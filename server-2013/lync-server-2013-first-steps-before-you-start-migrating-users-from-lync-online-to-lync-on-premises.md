---
title: Lync Online에서 Lync 온-프레미스로 사용자를 마이그레이션하기 전 첫 단계
TOCTitle: Lync Online에서 Lync 온-프레미스로 사용자를 마이그레이션하기 전 첫 단계
ms:assetid: 98245b04-ded4-4186-8da3-ba1c554b5c39
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Dn689118(v=OCS.15)
ms:contentKeyID: 62247351
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Lync Online에서 Lync 온-프레미스로 사용자를 마이그레이션하기 전 첫 단계

 

_**마지막으로 수정된 항목:** 2014-05-08_

Lync Online 사용자를 온-프레미스 환경으로 이동하기 전에 다음 내용이 모두 맞는지 확인하세요.

  - Lync Server 온-프레미스 환경을 완전하게 배포하고 유효성을 검사해야 합니다. 자세한 내용은 [Lync Server 2013 배포](lync-server-2013-deploying-lync-server.md)를 참고하세요.

  - Lync Online 테넌트를 원격 PowerShell 액세스에 맞게 구성해야 합니다.
    
    이렇게 하려면 먼저 Windows PowerShell용 비즈니스용 Skype Online 모듈을 설치합니다. 이 모듈은 [http://go.microsoft.com/fwlink/p/?LinkId=391911](http://go.microsoft.com/fwlink/p/?linkid=391911)에서 찾을 수 있습니다.
    
    모듈을 설치한 후에는 다음 cmdlet을 Lync Server 관리 셸에 입력해 원격 세션을 설정할 수 있습니다.
    
    ```
        Import-Module LyncOnlineConnector
    ```
    ```    
        $cred = Get-Credential
    ```
    ``` 
        $CSSession = New-CsOnlineSession -Credential $cred
    ```    
    ```
        Import-PSSession $CSSession -AllowClobber
    ```

원격 PowerShell 세션을 비즈니스용 Skype Online에 설정하는 방법에 대한 자세한 내용은 [Windows PowerShell을 사용하여 Lync Online에 연결](https://docs.microsoft.com/en-us/SkypeForBusiness/set-up-your-computer-for-windows-powershell/set-up-your-computer-for-windows-powershell)을 참고하세요.

비즈니스용 Skype Online PowerShell 모듈 사용에 대한 자세한 내용은 [Windows PowerShell을 사용하여 Lync Online 관리](https://docs.microsoft.com/en-us/SkypeForBusiness/set-up-your-computer-for-windows-powershell/set-up-your-computer-for-windows-powershell)를 참고하세요.

  - Lync Online을 공유 SIP 주소 공간에 맞게 구성해야 합니다. 이렇게 하려면 먼저 Lync Online을 사용해 원격 Powershell 세션을 시작합니다. 그리고 나서 다음 cmdlet을 실행합니다.
    
        Set-CsTenantFederationConfiguration -SharedSipAddressSpace $True

이 단계를 마친 후에는 [Lync Online 사용자를 Lync 온-프레미스로 마이그레이션](lync-server-2013-migrating-lync-online-users-to-lync-on-premises.md)으로 이동할 수 있습니다.

