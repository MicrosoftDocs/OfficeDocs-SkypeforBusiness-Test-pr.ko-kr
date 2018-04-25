---
title: Lync Web App 배포
TOCTitle: Lync Web App 배포
ms:assetid: b6301e98-051c-4e4b-8e10-ec922a8f508a
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/JJ205190(v=OCS.15)
ms:contentKeyID: 49304797
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Lync Web App 배포

 

_**마지막으로 수정된 항목:** 2013-07-18_

Lync Web App은 Lync Server 2013 과 함께 설치되고 기본적으로 사용하도록 설정되는 IIS(인터넷 정보 서비스) 웹 클라이언트입니다. 서버에서 Lync Web App을 사용하도록 설정하거나 사용자에게 웹 클라이언트를 배포하기 위한 별도의 단계가 필요 없습니다. 사용자가 모임 URL을 클릭할 때 Lync 2013 클라이언트가 설치되지 않은 경우 최신 버전의 Lync Web App을 사용하여 모임에 참가하는 옵션이 사용자에게 표시됩니다.

Lync Web App의 음성, 비디오 및 공유 기능에는 Microsoft ActiveX 컨트롤이 필요합니다. 관리자가 ActiveX 컨트롤을 미리 설치하거나 사용자로 하여금 관련 메시지가 나타날 때 설치하도록 할 수 있습니다. ActiveX 컨트롤을 설치하라는 메시지는 사용자가 Lync Web App을 처음으로 사용할 때 또는 ActiveX 컨트롤이 필요한 기능에 처음으로 액세스할 때 표시됩니다.


> [!NOTE]
> Lync Server 2013 에지 서버 배포에서는 Lync Web App 클라이언트 액세스를 위해 경계 네트워크의 HTTPS 역방향 프록시가 필요합니다. 또한 단순 URL을 게시해야 합니다. 자세한 내용은 <A href="lync-server-2013-setting-up-reverse-proxy-servers.md">Lync Server 2013에 대한 역방향 프록시 서버 설치</A> 및 <A href="lync-server-2013-planning-for-simple-urls.md">Lync Server 2013의 단순 URL 계획</A>을 참고하세요.



## Lync Web App에 다단계 인증을 사용하도록 설정

Lync Server 2013 버전의 Lync Web App은 다단계 인증을 지원합니다. 외부 네트워크에서 참가하는 사용자가 Lync 모임에 로그인할 때 이 사용자를 인증하기 위해 사용자 이름과 암호 이외에 스마트 카드 또는 PIN과 같은 추가 인증 방법을 요구할 수 있습니다. AD DS(Active Directory Federation Service) 페더레이션 서버를 배포하고 Lync Server 2013에서 수동 인증을 사용하도록 설정하여 다단계 인증을 사용하도록 설정할 수 있습니다. AD FS가 구성된 후에는 Lync 모임에 참가하려는 외부 사용자에게 사용자 이름 및 암호 질문과 함께 관리자가 구성한 추가 인증 방법이 포함된 AD FS 다단계 인증 웹 페이지가 표시됩니다.


> [!IMPORTANT]
> 다단계 인증을 사용하도록 AD FS를 구성하려는 경우 고려해야 하는 중요 사항은 다음과 같습니다. 
> <UL>
> <LI>
> <P>다단계 ADFS 인증은 모임 참가자와 이끌이가 둘 다 같은 조직에 있거나 AD FS 페더레이션 조직에 속해 있는 경우에 사용할 수 있습니다. 현재 Lync 서버 웹 인프라에서 이를 지원하지 않으므로 Lync 페더레이션 사용자는 다단계 ADFS 인증을 사용할 수 없습니다.</P>
> <LI>
> <P>하드웨어 부하 분산 장치를 사용하는 경우 Lync Web App 클라이언트의 모든 요청이 동일한 프런트 엔드 서버에서 처리되도록 부하 분산 장치에 쿠키 지속성을 사용하도록 설정합니다.</P>
> <LI>
> <P>Lync Server와 AD FS 서버 간에 신뢰 당사자 트러스트를 설정하는 경우 최대 Lync 모임 시간 동안 지속될 만큼 충분히 긴 토큰 수명을 할당합니다. 일반적으로 240분의 토큰 수명이면 충분합니다.</P>
> <LI>
> <P>이 구성은 Lync 모바일 클라이언트에 적용되지 않습니다.</P></LI></UL>



**다단계 인증을 구성하려면**

1.  AD FS 페더레이션 서버 역할을 설치합니다. 자세한 내용은 Active Directory Federation Services 2.0 배포 가이드([http://go.microsoft.com/fwlink/?linkid=267511\&clcid=0x412](http://go.microsoft.com/fwlink/?linkid=267511%26clcid=0x412))를 참고하세요.

2.  AD FS용 인증서를 만듭니다. 자세한 내용은 Single Sign-On에 사용할 AD FS 계획 및 배포 항목([http://go.microsoft.com/fwlink/p/?LinkId=285376](http://go.microsoft.com/fwlink/p/?linkid=285376))에서 "페더레이션 서버 인증서" 섹션을 참고하세요.

3.  Windows PowerShell 명령줄 인터페이스에서 다음 명령을 실행합니다.
    
        add-pssnapin Microsoft.Adfs.powershell

4.  다음 명령을 실행하여 파트너 관계를 설정합니다.
    
        Add-ADFSRelyingPartyTrust -Name ContosoApp -MetadataURL https://lyncpool.contoso.com/passiveauth/federationmetadata/2007-06/federationmetadata.xml

5.  다음과 같은 신뢰 당사자 규칙을 설정합니다.
    
        $IssuanceAuthorizationRules = '@RuleTemplate = "AllowAllAuthzRule" => issue(Type = "http://schemas.contoso.com/authorization/claims/permit", Value = "true");'
        $IssuanceTransformRules = '@RuleTemplate = "PassThroughClaims" @RuleName = "Sid" c:[Type == "http://schemas.contoso.com/ws/2008/06/identity/claims/primarysid"]=> issue(claim = c);'
    
        Set-ADFSRelyingPartyTrust -TargetName ContosoApp -IssuanceAuthorizationRules $IssuanceAuthorizationRules -IssuanceTransformRules $IssuanceTransformRules
    
        Set-CsWebServiceConfiguration -UseWsFedPassiveAuth $true -WsFedPassiveMetadataUri https://dc.contoso.com/federationmetadata/2007-06/federationmetadata.xml

## BranchCache 구성

Windows 7과 Windows Server 2008 R2의 BranchCache 기능은 Lync Web App 웹 구성 요소에 방해가 될 수 있습니다. Lync Web App 사용자에게 문제가 발생하지 않게 BranchCache를 사용하지 않도록 설정합니다.

BranchCache를 사용하지 않도록 설정하는 방법에 대한 자세한 내용은 Microsoft 다운로드 센터([http://go.microsoft.com/fwlink/?linkid=268788\&clcid=0x412](http://go.microsoft.com/fwlink/?linkid=268788%26clcid=0x412))에서 Word 형식으로 제공되고 Windows Server 2008 R2 기술 라이브러리([http://go.microsoft.com/fwlink/?linkid=268789\&clcid=0x412](http://go.microsoft.com/fwlink/?linkid=268789%26clcid=0x412))에서 HTML 형식으로 제공되는 BranchCache 배포 가이드를 참고하세요.

## Lync Web App 배포 확인

Test-CsUcwaConference cmdlet을 사용하여 한 쌍의 테스트 사용자가 UCWA(Unified Communications Web API)를 사용해서 회의에 참가할 수 있는지 확인합니다. 이 cmdlet에 대한 자세한 내용은 Lync Server 관리 셸 설명서에서 [Test-CsUcwaConference](test-csucwaconference.md)를 참고하세요.

## Windows Server 2008 R2에서 플러그인 설치 문제 해결

Windows Server 2008 R2를 실행하는 컴퓨터에서 플러그인 설치가 실패할 경우 Internet Explorer 보안 설정 또는 DisableMSI 레지스트리 키 설정을 수정해야 할 수 있습니다.

**Internet Explorer에서 보안 설정을 수정하려면**

1.  Internet Explorer를 엽니다.

2.  **도구**, **인터넷 옵션**을 클릭한 다음 **고급**을 클릭합니다.

3.  아래로 스크롤하여 **보안** 섹션으로 이동합니다.

4.  **암호화된 페이지를 디스크에 저장 안 함**의 선택을 취소한 다음 **확인**을 클릭합니다.
    

    > [!NOTE]
    > 이 설정을 선택할 경우 Lync Web App에서 첨부 파일을 다운로드할 때 오류가 발생합니다.



5.  모임에 다시 참가합니다. 이제 플러그인이 오류 없이 다운로드될 것입니다.

**DisableMSI 레지스트리 설정을 수정하려면**

1.  **시작**을 클릭한 다음 **실행**을 클릭합니다.

2.  **regedit**를 입력하여 레지스트리 편집기에 액세스합니다.

3.  HKEY\_LOCAL\_MACHINE\\Software\\Policies\\Microsoft\\Windows\\Installer로 이동합니다.

4.  REG\_DWORD 유형의 DisableMSI 레지스트리 키를 편집하거나 추가하고 0으로 설정합니다.

5.  모임에 다시 참가합니다.

## 참고 항목

#### 개념

[Lync Server 2013에서 모임 참가 페이지 구성](lync-server-2013-configuring-the-meeting-join-page.md)  
[Lync Server 2013의 Lync Web App 지원 플랫폼](lync-server-2013-lync-web-app-supported-platforms.md)

