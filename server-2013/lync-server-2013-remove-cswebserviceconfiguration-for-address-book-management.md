---
title: 주소록용 Remove-CsWebServiceConfiguration
TOCTitle: 주소록용 Remove-CsWebServiceConfiguration
ms:assetid: 91947cad-5cdd-41b9-83e1-650703c55879
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg429713(v=OCS.15)
ms:contentKeyID: 49304389
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# 주소록용 Remove-CsWebServiceConfiguration

 

_**마지막으로 수정된 항목:** 2012-11-01_

이 cmdlet을 실행할 수 있는 사용자: 기본적으로 RTCUniversalServerAdmins 그룹의 구성원은 Remove-CsWebServiceConfiguration cmdlet을 로컬로 실행할 수 있습니다. 사용자가 직접 만든 사용자 지정 RBAC(역할 기반 액세스 제어) 역할을 포함하여 이 cmdlet이 할당된 모든 RBAC 역할의 목록을 가져오려면 Windows PowerShell 프롬프트에서 다음 명령을 실행합니다.

    Get-CsAdminRole | Where-Object {$_.Cmdlets -match "Remove-CsWebServiceConfiguration"}

관리자는 이전에 만든 웹 서비스 구성을 Remove-CsWebServiceConfiguration cmdlet로 제거할 수 있습니다. 이 cmdlet은 전역 웹 서비스 구성을 제거하지는 못합니다.

예:

    Remove-CsWebServiceConfiguration -Identity site:Redmond

전체 명령에 대한 자세한 설명은 기본 PowerShell RTCCmdlets 참조에서 다음 항목을 참조하십시오.

## 참고 항목

#### 기타 리소스

[Remove-CsWebServiceConfiguration](https://docs.microsoft.com/en-us/powershell/module/skype/Remove-CsWebServiceConfiguration)

