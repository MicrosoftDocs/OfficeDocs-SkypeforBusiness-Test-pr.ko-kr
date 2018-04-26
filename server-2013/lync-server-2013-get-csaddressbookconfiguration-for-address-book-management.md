---
title: 주소록 관리용 Get-CsAddressBookConfiguration
TOCTitle: 주소록 관리용 Get-CsAddressBookConfiguration
ms:assetid: bd62f916-caf3-4e10-ada4-631bbb331ef1
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg429721(v=OCS.15)
ms:contentKeyID: 49304877
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# 주소록 관리용 Get-CsAddressBookConfiguration

 

_**마지막으로 수정된 항목:** 2012-11-01_

이 cmdlet을 실행할 수 있는 사용자: 기본적으로 RTCUniversalServerAdmins 그룹의 구성원은 Get-CsAddressBookConfiguration cmdlet을 로컬로 실행할 수 있습니다. 사용자가 직접 만든 사용자 지정 RBAC(역할 기반 액세스 제어) 역할을 포함하여 이 cmdlet이 할당된 모든 RBAC 역할의 목록을 가져오려면 Windows PowerShell 프롬프트에서 다음 명령을 실행합니다.

    Get-CsAdminRole | Where-Object {$_.Cmdlets -match "Get-CsAddressBookConfiguration"}

Get-CsAddressBookConfiguration cmdlet은 이미 있는 구성에 대한 정보를 반환합니다.

예:

    Get-CsAddressBookConfiguration -Identity site:Redmond

Get-CsAddressBookConfiguration과 Set-CsAddressBookConfiguration 기능을 결합함으로써 관리자는 수정할 구성을 정의한 후 수정을 적용할 수 있습니다. 결합 예는 다음과 같습니다.

    Get-CsAddressBookConfiguration -Filter site:* | Set-CsAddressBookConfiguration -RunTimeOfDay 23:00

모든 사이트의 모든 구성을 반환하며 23:00시로 표시된 RunTimeOfDay를 구성에 적용합니다.

전체 명령에 대한 자세한 설명은 기본 PowerShell RTCCmdlets 참조에서 다음 항목을 참조하십시오.

## 참고 항목

#### 기타 리소스

[Get-CsAddressBookConfiguration](get-csaddressbookconfiguration.md)

