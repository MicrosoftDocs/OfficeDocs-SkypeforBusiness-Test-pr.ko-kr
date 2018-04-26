---
title: 주소록 관리용 Set-CsWebServiceConfiguration
TOCTitle: 주소록 관리용 Set-CsWebServiceConfiguration
ms:assetid: 79d0edf5-23f3-4845-a7b7-e11b5a928bab
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg429709(v=OCS.15)
ms:contentKeyID: 49304119
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# 주소록 관리용 Set-CsWebServiceConfiguration

 

_**마지막으로 수정된 항목:** 2012-11-01_

이 cmdlet을 실행할 수 있는 사용자: 기본적으로 RTCUniversalServerAdmins 그룹의 구성원은 Set-CsWebServiceConfiguration cmdlet을 로컬로 실행할 수 있습니다. 사용자가 직접 만든 사용자 지정 RBAC(역할 기반 액세스 제어) 역할을 포함하여 이 cmdlet이 지정된 모든 RBAC 역할의 목록을 가져오려면 Windows PowerShell 프롬프트에서 다음 명령을 실행합니다.

    Get-CsAdminRole | Where-Object {$_.Cmdlets -match "Set-CsWebServiceConfiguration"}

관리자는 Set-CsWebServiceConfiguration cmdlet을 사용하여 웹 서비스 구성의 기존 특성을 다시 정의할 수 있습니다.

예:

    Set-CsWebServiceConfiguration -Identity site:Redmond -EnableGroupExpansion $True

전체 명령에 대한 자세한 설명은 기본 PowerShell RTCCmdlets 참조에서 다음 항목을 참조하십시오.

## 참고 항목

#### 기타 리소스

[Set-CsWebServiceConfiguration](set-cswebserviceconfiguration.md)

