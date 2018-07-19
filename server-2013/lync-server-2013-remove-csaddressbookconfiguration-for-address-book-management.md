---
title: 주소록 관리용 Remove-CsAddressBookConfiguration
TOCTitle: 주소록 관리용 Remove-CsAddressBookConfiguration
ms:assetid: 5d173ebe-ec4d-4640-8432-a25071ea9cc5
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg429705(v=OCS.15)
ms:contentKeyID: 49303770
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# 주소록 관리용 Remove-CsAddressBookConfiguration

 

_**마지막으로 수정된 항목:** 2012-11-01_

이 cmdlet을 실행할 수 있는 사용자: 기본적으로 RTCUniversalServerAdmins 그룹의 구성원은 Remove-CsAddressBookConfiguration cmdlet을 로컬로 실행할 수 있습니다. 사용자가 직접 만든 사용자 지정 RBAC(역할 기반 액세스 제어) 역할을 포함하여 이 cmdlet이 지정된 모든 RBAC 역할의 목록을 가져오려면 Windows PowerShell 프롬프트에서 다음 명령을 실행합니다.

    Get-CsAdminRole | Where-Object {$_.Cmdlets -match "Remove-CsAddressBookConfiguration"}

이름에서 확인할 수 있듯이, Remove-CsAddressBookConfiguration은 정의된 사이트 ID에 따라 구성을 제거합니다.

예:

    Remove-CsAddressBookConfiguration -Identity site:Redmond

전체 명령에 대한 자세한 설명은 기본 PowerShell RTCCmdlets 참조에서 다음 항목을 참조하십시오.

## 참고 항목

#### 기타 리소스

[Remove-CsAddressBookConfiguration](https://docs.microsoft.com/en-us/powershell/module/skype/Remove-CsAddressBookConfiguration)

