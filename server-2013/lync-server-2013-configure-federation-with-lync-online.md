---
title: 'Lync Server 2013: Lync Online과의 페더레이션 구성'
TOCTitle: Lync Online과의 페더레이션 구성
ms:assetid: a10bd1d5-c003-46db-9f57-7d55d3fa08da
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/JJ205126(v=OCS.15)
ms:contentKeyID: 49304569
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Lync Online과 Lync Server 2013의 페더레이션 구성

 

_**마지막으로 수정된 항목:** 2015-08-19_

이 섹션의 단계에 따라 온-프레미스 배포와 비즈니스용 Skype Online 간에 상호 운용성을 구성합니다.

## 비즈니스용 Skype Online과 페더레이션되도록 에지 서버 구성

페더레이션은 온-프레미스 배포의 사용자가 조직의 Office 365 사용자와 통신할 수 있도록 허용합니다. 페더레이션을 구성하려면 다음 cmdlet을 실행합니다.

```
    Set-CSAccessEdgeConfiguration -AllowOutsideUsers 1 -AllowFederatedUsers 1 -UseDnsSrvRouting
```
```
    New-CSHostingProvider -Identity LyncOnline -ProxyFqdn "sipfed.online.lync.com" -Enabled $true -EnabledSharedAddressSpace $true -HostsOCSUsers $true -VerificationLevel UseSourceVerification -IsLocal $false -AutodiscoverUrl https://webdir.online.lync.com/Autodiscover/AutodiscoverService.svc/root
```

## 공유 SIP 주소 공간에 대한 비즈니스용 Skype Online 테넌트 구성

SIP(Session Initiation Protocol) 주소는 네트워크에 있는 각 사용자의 고유 식별자로, 전화 번호나 전자 메일 주소와 비슷합니다. 온-프레미스에서 비즈니스용 Skype Online으로 Lync 사용자를 이동하기 전에 반드시 공유 SIP(Session Initiation Protocol) 주소 공간을 온-프레미스 배포와 공유하도록 Office 365 테넌트를 구성해야 합니다. 이와 같이 구성하지 않으면 다음 오류 메시지가 나타날 수 있습니다.

Move-CsUser : HostedMigration fault: Error=(510), Description=(이 사용자의 테넌트는 공유 SIP 주소 공간을 사용하도록 설정되지 않았습니다.)

공유 SIP 주소 공간을 구성하려면 원격 PowerShell 세션을 비즈니스용 Skype Online에 설정한 후 다음 cmdlet을 실행합니다.

    Set-CsTenantFederationConfiguration -SharedSipAddressSpace $true

원격 PowerShell 세션을 비즈니스용 Skype Online에 설정하려면 먼저 [http://go.microsoft.com/fwlink/p/?LinkId=391911](http://go.microsoft.com/fwlink/p/?linkid=391911)에서 제공되는 Windows PowerShell용 비즈니스용 Skype Online 모듈을 설치해야 합니다.

이 모듈을 설치한 후 다음 cmdlet으로 원격 세션을 설정할 수 있습니다.

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

## 참고 항목

#### 기타 리소스

[New-CsHostingProvider](https://docs.microsoft.com/en-us/powershell/module/skype/New-CsHostingProvider)

