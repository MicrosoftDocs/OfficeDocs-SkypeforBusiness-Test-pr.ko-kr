---
title: Tenant 매개 변수를 사용하는 cmdlet
TOCTitle: Tenant 매개 변수를 사용하는 cmdlet
ms:assetid: e7fe7c12-fbe0-49c1-9e8c-eef6958f27d0
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Dn362850(v=OCS.15)
ms:contentKeyID: 56270305
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Tenant 매개 변수를 사용하는 cmdlet

 

_**마지막으로 수정된 항목:** 2015-06-22_

공용 공급자 설정을 수정할 때 항상 테넌트 ID를 제공해야 합니다. 테넌트가 하나만 있는 경우에도 마찬가지입니다. 예를 들어 다음 명령은 Windows Live를 사용자가 통신할 수 있는 유일한 공용 공급자로 설정합니다.

    Set-CsTenantPublicProvider -Tenant "bf19b7db-6960-41e5-a139-2aa373474354" -Provider "WindowsLive"

이러한 cmdlet 중 하나를 실행할 때마다 테넌트 ID(예: bf19b7db-6960-41e5-a139-2aa373474354)를 입력할 필요는 없습니다. 대신 [Get-CsTenant](https://docs.microsoft.com/en-us/powershell/module/skype/Get-CsTenant) cmdlet을 실행하여 테넌트 ID를 변수에 저장한 다음 다른 cmdlet 중 하나를 호출할 때 해당 변수를 사용하여 테넌트 ID를 검색할 수 있습니다. 예를 들면 다음과 같습니다.

    $x = (Get-CsTenant).TenantId
    Set-CsTenantPublicProvider -Tenant $x -Provider "WindowsLive"

또는 테넌트 ID를 검색한 다음 해당 값을 Set-CsTenantPublicProvider cmdlet으로 파이프하여 하나의 명령으로 이 작업을 완료할 수 있습니다.

    Get-CsTenant | Select-Object TenantId | ForEach-Object {Set-CsTenantPublicProvider -Tenant $_.TenantId -Provider "WindowsLive"}

**Get-CsTenant** cmdlet을 호출할 때에는 테넌트 ID를 지정하지 않아도 됩니다. 이 명령은 테넌트에 대한 정보를 반환합니다.

    Get-CsTenant

다음 cmdlet는 테넌트 ID를 허용하지만 이 경우 매개 변수는 선택 사항이며 cmdlet을 호출할 때 입력하지 않아도 됩니다. Windows PowerShell이 현재 사용자가 연결되어 있는 비즈니스용 Skype Online 테넌트를 기준으로 테넌트 ID를 대신 입력합니다.

  - [Get-CsTenant](https://docs.microsoft.com/en-us/powershell/module/skype/Get-CsTenant)

  - [Set-CsTenantFederationConfiguration](https://docs.microsoft.com/powershell/module/skype/Set-CsTenantFederationConfiguration)

  - [Set-CsTenantHybridConfiguration](https://docs.microsoft.com/en-us/powershell/module/skype/Set-CsTenantHybridConfiguration)

  - [Get-CsTenantFederationConfiguration](https://docs.microsoft.com/powershell/module/skype/Get-CsTenantFederationConfiguration)

  - [Get-CsTenantHybridConfiguration](https://docs.microsoft.com/en-us/powershell/module/skype/Get-CsTenantHybridConfiguration)

  - [Get-CsTenantLicensingConfiguration](https://docs.microsoft.com/en-us/powershell/module/skype/Get-CsTenantLicensingConfiguration)

예를 들어 다음 명령을 사용하여 **Get-CsTenantFederationConfiguration** cmdlet을 호출할 수 있습니다.

    Get-CsTenantFederationConfiguration

필수는 아니지만 Get-CsTenantFederationConfiguration을 호출할 때 Tenant 매개 변수를 포함할 수 있습니다.

    Get-CsTenantFederationConfiguration -Tenant "bf19b7db-6960-41e5-a139-2aa373474354"

## 참고 항목

#### 개념

[ID, 범위, 테넌트](identities-scopes-and-tenants-in-skype-for-business-online.md)  
[Lync Online Cmdlet](https://docs.microsoft.com/en-us/SkypeForBusiness/set-up-your-computer-for-windows-powershell/set-up-your-computer-for-windows-powershell)

