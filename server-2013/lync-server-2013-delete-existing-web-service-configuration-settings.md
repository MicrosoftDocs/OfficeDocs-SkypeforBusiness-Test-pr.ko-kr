---
title: 기존 웹 서비스 구성 설정 삭제
TOCTitle: 기존 웹 서비스 구성 설정 삭제
ms:assetid: c2b96f4c-4b07-48e6-9ca6-55bc0e0cf5a1
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg182582(v=OCS.15)
ms:contentKeyID: 49304941
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# 기존 웹 서비스 구성 설정 삭제

 

_**마지막으로 수정된 항목:** 2013-02-23_

다음 단계에 따라 웹 서비스 정책을 삭제할 수 있습니다.

## 웹 서비스 정책을 삭제하려면

1.  RTCUniversalServerAdmins 그룹의 구성원인 사용자 계정(또는 이와 동일한 사용자 권한을 가진 사용자 계정)이나 CsServerAdministrator 또는 CsAdministrator 역할이 할당된 사용자 계정에서 Lync Server 2013을 배포한 네트워크에 있는 컴퓨터에 로그온합니다.

2.  브라우저 창을 연 다음 Admin URL을 입력하여 Lync Server 제어판을 엽니다. Lync Server 제어판을 시작하는 데 사용할 수 있는 다양한 방법에 대한 자세한 내용은 [Lync Server 관리 도구 열기](lync-server-2013-open-lync-server-administrative-tools.md)를 참조하세요.

3.  왼쪽 탐색 표시줄에서 **보안**, **웹 서비스**를 차례로 클릭합니다.

4.  **웹 서비스** 페이지의 검색 필드에 삭제할 정책의 이름 일부나 전체를 입력합니다.

5.  정책 목록에서 원하는 정책을 클릭하고 **편집**을 클릭한 다음 **삭제**를 클릭합니다.

6.  **확인**을 클릭합니다.

## Lync Server 관리 셸 cmdlet을 사용하여 새 웹 서비스 구성 설정 삭제

또한 Lync Server 관리 셸 및 **Remove-CsWebServiceConfiguration** cmdlet을 사용하여 웹 서비스 구성을 삭제할 수 있습니다. 이 cmdlet은 Lync Server 2013 관리 셸 또는 Windows PowerShell의 원격 세션에서 실행할 수 있습니다. 원격 Windows PowerShell을 사용하여 Lync Server에 연결하는 방법에 대한 자세한 내용은 Lync Server Windows PowerShell 블로그 문서인 "빠른 시작: 원격 PowerShell을 사용하여 Microsoft Lync Server 2010 관리"([http://go.microsoft.com/fwlink/p/?linkId=255876](http://go.microsoft.com/fwlink/p/?linkid=255876))를 참조하세요.

## 웹 서비스 구성 설정의 특정 컬렉션을 삭제하려면

  - 다음 명령은 Redmond 사이트에 적용된 웹 서비스 보안 설정을 제거합니다.
    
        Remove-CsWebServiceConfiguration -Identity "site:Redmond"

## 사이트 범위에 적용된 모든 웹 서비스 구성 설정을 삭제하려면

  - 다음 명령은 서비스 범위에 적용된 모든 웹 서비스 보안 설정을 제거합니다.
    
        Get-CsWebServiceConfiguration -Filter "service:*" | Remove-CsWebServiceConfiguration

## 인증서 인증을 허용하는 모든 웹 서비스 구성 설정을 삭제하려면

  - 다음 명령은 인증서 인증을 사용할 수 있도록 허용하는 모든 웹 서비스 보안 설정을 제거합니다.
    
        Get-CsWebServiceConfiguration | Where-Object {$_.UseCertificateAuth -eq $True} | Remove-CsWebServiceConfiguration

자세한 내용은 [Remove-CsWebServiceConfiguration](https://docs.microsoft.com/en-us/powershell/module/skype/Remove-CsWebServiceConfiguration)을 참조하십시오.

## 참고 항목

#### 기타 리소스

[Lync Server 2013 제어판에서 보안 구성](lync-server-2013-configuring-authentication-in-the-lync-server-control-panel.md)

