---
title: PIN 정책 정보 보기
TOCTitle: PIN 정책 정보 보기
ms:assetid: 1d48b060-d77f-44ee-b70f-3ce128aedac4
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/JJ687985(v=OCS.15)
ms:contentKeyID: 49885671
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# PIN 정책 정보 보기

 

_**마지막으로 수정된 항목:** 2013-02-23_

**PIN 정책** 탭을 사용하면 IP 전화를 사용하여 Lync 2013에 연결하는 사용자의 개인 ID 번호(PIN) 인증을 확인합니다. PIN 인증을 사용하려면 웹 서비스 설정에서 **PIN 인증 사용**이 선택되어 있는지 확인합니다. 자세한 내용은 [기존 웹 서비스 구성 설정 수정](lync-server-2013-modify-existing-web-service-configuration-settings.md)을 참조하십시오.

사용자 수준 또는 사이트 수준 PIN 정책을 수정하려면 다음 단계를 수행합니다.

## Lync Server 제어판에서 PIN 정책에 대한 정보를 보려면

1.  RTCUniversalServerAdmins 그룹의 구성원인 사용자 계정(또는 이와 동일한 사용자 권한을 가진 사용자 계정)이나 CsServerAdministrator 또는 CsAdministrator 역할이 할당된 사용자 계정에서 Lync Server 2013을 배포한 네트워크에 있는 컴퓨터에 로그온합니다.

2.  브라우저 창을 연 다음 Admin URL을 입력하여 Lync Server 제어판을 엽니다. Lync Server 제어판을 시작하는 데 사용할 수 있는 다양한 방법에 대한 자세한 내용은 [Lync Server 관리 도구 열기](lync-server-2013-open-lync-server-administrative-tools.md)를 참조하세요.

3.  왼쪽 탐색 모음에서 **보안**을 클릭하고 **PIN 정책**을 클릭합니다.

4.  **PIN 정책** 페이지에서 정책을 클릭하고 **편집**을 클릭한 후에 **자세한 정보 표시**를 클릭합니다.

## Lync Server PowerShell cmdlet을 사용하여 PIN 정책 확인

Windows PowerShell 및 Get-CsPinPolicy cmdlet을 사용하여 PIN 정책을 확인할 수도 있습니다. 이 cmdlet은 Lync Server 2013 관리 셸 또는 Windows PowerShell의 원격 세션에서 실행할 수 있습니다. 원격 Windows PowerShell을 사용하여 Lync Server에 연결하는 방법에 대한 자세한 내용은 Lync Server Windows PowerShell 블로그 문서인 "빠른 시작: 원격 PowerShell을 사용하여 Microsoft Lync Server 2010 관리"([http://go.microsoft.com/fwlink/p/?linkId=255876](http://go.microsoft.com/fwlink/p/?linkid=255876))를 참조하세요.

## PIN 정책 확인

  - 모든 PIN 정책에 대한 정보를 보려면 Lync Server 관리 셸에서 다음 명령을 입력하고 Enter 키를 누릅니다.
    
        Get-CsPinPolicy
    
    그러면 다음과 같은 정보가 반환됩니다.
    
        Identity             : Global
        Description          :
        MinPasswordLength    : 5
        PINHistoryCount      : 0
        AllowCommonPatterns  : False
        PINLifetime          : 0
        MaximumLogonAttempts :

자세한 내용은 [Get-CsPinPolicy](https://docs.microsoft.com/en-us/powershell/module/skype/Get-CsPinPolicy) cmdlet에 대한 도움말 항목을 참조하십시오.

## 참고 항목

#### 작업

[기존 웹 서비스 구성 설정 수정](lync-server-2013-modify-existing-web-service-configuration-settings.md)  
[새 PIN 정책 만들기](lync-server-2013-create-a-new-pin-policy.md)

