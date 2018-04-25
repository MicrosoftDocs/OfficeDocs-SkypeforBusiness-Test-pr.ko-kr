---
title: 주소록용 New-CsClientPolicy
TOCTitle: 주소록용 New-CsClientPolicy
ms:assetid: ef4415fc-82c4-4dc8-97d1-37a084553343
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg429726(v=OCS.15)
ms:contentKeyID: 49305455
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# 주소록용 New-CsClientPolicy

 

_**마지막으로 수정된 항목:** 2012-11-01_

이 cmdlet을 실행할 수 있는 사용자: 기본적으로 RTCUniversalServerAdmins 그룹의 구성원은 New-CsClientPolicy cmdlet을 실행할 수 있습니다. 사용자가 직접 만든 사용자 지정 RBAC(역할 기반 액세스 제어) 역할을 포함하여 이 cmdlet이 할당된 모든 RBAC 역할의 목록을 반환하려면 Windows PowerShell 프롬프트에서 다음 명령을 실행합니다.

    Get-CsAdminRole | Where-Object {$_.Cmdlets -match "New-CsClientPolicy"}

New-CsClientPolicy cmdlet은 Lync Server 2013에서 사용할 수 있는 기능에 대해 클라이언트를 프로비전하는 여러 설정을 정의합니다. 주소록 서비스의 경우 AddressBookAvailability 매개 변수가 고려됩니다. 클라이언트에서 사용할 수 있는 옵션에 직접 영향을 주는 이 매개 변수에는 다음과 같은 세 가지 옵션이 있습니다.

  - WebSearchAndFileDownload

  - WebSearchOnly

  - FileDownloadOnly

이 매개 변수가 정의된 경우 클라이언트에서 주소록에 액세스하는 방법이 결정됩니다. 이 매개 변수를 정의할 경우 옵션 중 하나를 정의해야 합니다. 이 설정을 수정하지 않으면 기본 WebSearchAndFileDownload가 적용됩니다.

예:

    New-CsClientPolicy -Identity RedmondClientPolicy -DisableCalendarPresence $True -DisablePhonePresence $True -DisplayPhoto "PhotosFromADOnly" -AddressBookAvailability "WebSearchOnly"

## 참고 항목

#### 기타 리소스

[New-CsClientPolicy](new-csclientpolicy.md)

