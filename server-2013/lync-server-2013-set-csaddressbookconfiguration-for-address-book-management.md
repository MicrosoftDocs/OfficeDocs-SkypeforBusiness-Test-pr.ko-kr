---
title: 주소록 관리용 Set-CsAddressBookConfiguration
TOCTitle: 주소록 관리용 Set-CsAddressBookConfiguration
ms:assetid: 3a64ceb1-9f79-4f3b-bf33-eaf346dbd60d
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg429700(v=OCS.15)
ms:contentKeyID: 49303352
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# 주소록 관리용 Set-CsAddressBookConfiguration

 

_**마지막으로 수정된 항목:** 2012-11-01_

이 cmdlet을 실행할 수 있는 사용자: 기본적으로 RTCUniversalServerAdmins 그룹의 구성원은 Set-CsAddressBookConfiguration cmdlet을 로컬로 실행할 수 있습니다. 사용자가 직접 만든 사용자 지정 RBAC(역할 기반 액세스 제어) 역할을 포함하여 이 cmdlet이 할당된 모든 RBAC 역할의 목록을 가져오려면 Windows PowerShell 프롬프트에서 다음 명령을 실행합니다.

    Get-CsAdminRole | Where-Object {$_.Cmdlets -match "Set-CsAddressBookConfiguration"}

Set-CsAddressBookConfiguration은 기존 구성을 수정하는 데 사용된다는 점을 제외하면 New-CsAddressBookConfiguration cmdlet와 비슷합니다.

예:

    Set-CsAddressBookConfiguration -identity site:Redmond -RunTimeOfDay 23:00

전체 명령에 대한 자세한 설명은 기본 PowerShell RTCCmdlets 참조에서 다음 항목을 참조하십시오.

## 참고 항목

#### 기타 리소스

[Set-CsAddressBookConfiguration](set-csaddressbookconfiguration.md)

