---
title: Active Directory Federation Services(AD FS 2.0) 구성
TOCTitle: Active Directory Federation Services(AD FS 2.0) 구성
ms:assetid: 0ba8657f-55b8-41b3-960c-fdc5eeee6978
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Dn308561(v=OCS.15)
ms:contentKeyID: 56270213
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Active Directory Federation Services(AD FS 2.0) 구성

 

_**마지막으로 수정된 항목:** 2013-07-03_

다음 섹션에서는 다단계 인증을 지원하도록 AD FS 2.0(Active Directory Federation Services)을 구성하는 방법에 대해 설명합니다. AD FS 2.0을 설치하는 방법에 대한 자세한 내용은 [http://go.microsoft.com/fwlink/p/?LinkId=313374](http://go.microsoft.com/fwlink/p/?linkid=313374)에서 AD FS 2.0 단계 및 방법 가이드(영어)를 참고하세요.


> [!NOTE]
> AD FS 2.0을 설치할 때 Windows Server Manager를 사용하여 Active Directory Federation Services 역할을 추가하지 마세요. 대신 <A href="http://go.microsoft.com/fwlink/p/?linkid=313375">http://go.microsoft.com/fwlink/p/?LinkId=313375</A>에서 Active Directory Federation Services 2.0 RTW 패키지를 다운로드해 설치하세요.




**2단계 인증을 위해 AD FS를 구성하려면**

1.  도메인 관리자 계정을 사용하여 AD FS 2.0에 로그인합니다.

2.  Windows PowerShell을 시작합니다.

3.  Windows PowerShell 명령줄에서 다음 명령을 실행합니다.
    
        add-pssnapin Microsoft.Adfs.PowerShell

4.  다음 명령을 사용하여 수동 인증에 사용할 수 있는 Lync Server 2013용 누적 업데이트(2013년 7월)가 적용된 각 Lync Server 2013 디렉터, 엔터프라이즈 풀, Standard Edition 서버와의 파트너 관계를 설정하고 배포에 맞게 서버 이름을 바꿉니다.
    
        Add-ADFSRelyingPartyTrust -Name LyncPool01-PassiveAuth -MetadataURL https://lyncpool01.contoso.com/passiveauth/federationmetadata/2007-06/federationmetadata.xml

5.  관리 도구 메뉴에서 AD FS 2.0 관리 콘솔을 시작합니다.

6.  **트러스트 관계** \> **신뢰 당사자 트러스트**를 확장합니다.

7.  Lync Server 2013용 누적 업데이트(2013년 7월)가 적용된 Lync Server 2013 엔터프라이즈 풀 또는 Standard Edition 서버에 대해 새 트러스트를 만들었는지 확인합니다.

8.  다음 명령을 실행하여 Windows PowerShell을 사용하는 신뢰 당사자 트러스트에 대한 발급 권한 부여 규칙을 만들고 할당합니다.
    
        $IssuanceAuthorizationRules = '@RuleTemplate = "AllowAllAuthzRule" => issue(Type = "http://schemas.microsoft.com/authorization/claims/permit", Value = "true");'
    
        Set-ADFSRelyingPartyTrust -TargetName LyncPool01-PassiveAuth 
        -IssuanceAuthorizationRules $IssuanceAuthorizationRules

9.  다음 명령을 실행하여 Windows PowerShell을 사용하는 신뢰 당사자 트러스트에 대한 발급 변환 규칙을 만들고 할당합니다.
    
        $IssuanceTransformRules = '@RuleTemplate = "PassThroughClaims" @RuleName = "Sid" c:[Type == "http://schemas.microsoft.com/ws/2008/06/identity/claims/primarysid"]=> issue(claim = c);'
    
        Set-ADFSRelyingPartyTrust -TargetName LyncPool01-PassiveAuth -IssuanceTransformRules $IssuanceTransformRules

10. AD FS 2.0 관리 콘솔에서 신뢰 당사자 트러스트를 마우스 오른쪽 단추로 클릭하고 **클레임 규칙 편집**을 선택합니다.

11. **발급 인증 규칙** 탭을 선택하여 새 인증 규칙이 성공적으로 만들어졌는지 확인합니다.

12. **발급 변환 규칙** 탭을 선택하여 새 변환 규칙이 성공적으로 만들어졌는지 확인합니다.

