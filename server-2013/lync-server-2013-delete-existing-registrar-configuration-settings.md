---
title: 기존 고급 등록자 구성 설정 삭제
TOCTitle: 기존 고급 등록자 구성 설정 삭제
ms:assetid: ae43cd75-cae4-4f78-b037-779a2cdb583b
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg182571(v=OCS.15)
ms:contentKeyID: 49304724
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# 기존 고급 등록자 구성 설정 삭제

 

_**마지막으로 수정된 항목:** 2013-02-23_

다음 단계에 따라 등록자를 삭제할 수 있습니다.

## 등록자를 삭제하려면

1.  RTCUniversalServerAdmins 그룹의 구성원인 사용자 계정(또는 이와 동일한 사용자 권한을 가진 사용자 계정)이나 CsServerAdministrator 또는 CsAdministrator 역할이 할당된 사용자 계정에서 Lync Server 2013을 배포한 네트워크에 있는 컴퓨터에 로그온합니다.

2.  브라우저 창을 연 다음 Admin URL을 입력하여 Lync Server 제어판을 엽니다. Lync Server 제어판을 시작하는 데 사용할 수 있는 다양한 방법에 대한 자세한 내용은 [Lync Server 관리 도구 열기](lync-server-2013-open-lync-server-administrative-tools.md)를 참조하세요.

3.  왼쪽 탐색 표시줄에서 **보안**, **등록자**를 차례로 클릭합니다.

4.  **등록자** 페이지의 검색 필드에 삭제할 등록자의 이름 일부나 전체를 입력합니다.

5.  목록에서 삭제할 등록자를 클릭하고 **편집**, **삭제**를 차례로 클릭합니다.

6.  **확인**을 클릭합니다.

## Lync Server 관리 셸 cmdlet을 사용하여 등록자 구성 설정 제거

또한 Lync Server 관리 셸 및 **Remove-CsProxyConfiguration** cmdlet을 사용하여 등록자 구성을 삭제할 수 있습니다. 이 cmdlet은 Lync Server 2013 관리 셸 또는 Windows PowerShell의 원격 세션에서 실행할 수 있습니다. 원격 Windows PowerShell을 사용하여 Lync Server에 연결하는 방법에 대한 자세한 내용은 Lync Server Windows PowerShell 블로그 문서인 "빠른 시작: 원격 PowerShell을 사용하여 Microsoft Lync Server 2010 관리"([http://go.microsoft.com/fwlink/p/?linkId=255876](http://go.microsoft.com/fwlink/p/?linkid=255876))를 참조하세요.

## 특정 등록자 보안 설정 집합을 제거하려면

  - 다음 명령은 에지 서버 atl-edge-011.litwareinc.com에 적용된 등록자 보안 설정을 제거합니다.
    
        Remove-CsProxyConfiguration -Identity service:EdgeServer:atl-edge-011.litwareinc.com

## 사이트 범위에 적용된 모든 등록자 보안 설정을 제거하려면

  - 다음 명령은 등록자 서비스에 적용된 모든 등록자 보안 설정을 제거합니다.
    
        Get-CsProxyConfiguration -Filter "service:Registrar:*" | Remove-CsProxyConfiguration

## NTLM 인증을 허용하는 모든 등록자 보안 설정을 제거하려면

  - 다음 명령은 클라이언트 인증에 NTLM을 사용할 수 있도록 허용하는 모든 등록자 보안 설정을 삭제합니다.
    
        Get-CsProxyConfiguration | Where-Object {$_.UseNtlmForClientToProxyAuth -eq $True}| Remove-CsProxyConfiguration

자세한 내용은 [Remove-CsProxyConfiguration](https://docs.microsoft.com/en-us/powershell/module/skype/Remove-CsProxyConfiguration)을 참조하십시오.

