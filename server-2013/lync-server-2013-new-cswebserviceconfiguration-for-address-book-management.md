---
title: 주소록용 New-CsWebServiceConfiguration
TOCTitle: 주소록용 New-CsWebServiceConfiguration
ms:assetid: 49e4ecc5-aa3e-4dd4-a32c-b0dea3758fab
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg429703(v=OCS.15)
ms:contentKeyID: 49303537
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# 주소록용 New-CsWebServiceConfiguration

 

_**마지막으로 수정된 항목:** 2012-11-01_

이 cmdlet을 실행할 수 있는 사용자: 기본적으로 RTCUniversalServerAdmins 그룹의 구성원은 New-CsWebServiceConfiguration cmdlet을 로컬로 실행할 수 있습니다. 사용자가 직접 만든 사용자 지정 RBAC(역할 기반 액세스 제어) 역할을 포함하여 이 cmdlet이 지정된 모든 RBAC 역할의 목록을 가져오려면 Windows PowerShell 프롬프트에서 다음 명령을 실행합니다.

    Get-CsAdminRole | Where-Object {$_.Cmdlets -match "New-CsWebServiceConfiguration"}

New-CsWebServiceConfiguration cmdlet은 조직의 웹 서비스에 대해 새 구성을 정의합니다. 웹 서비스 구성의 범위는 사이트 또는 서비스 수준이어야 하며, 전역 수준에서 새 웹 서비스 구성을 만들 수는 없습니다. 주소록에서 주의해야 하는 특성은 EnableGroupExansion입니다. 이 특성을 True로 설정하는 경우 웹 서비스가 그룹 확장 요청에 응답할 수 있습니다.

예:

    New-CsWebServiceConfiguration -Identity site:Redmond -EnableGroupExpansion $False -UseCertificateAuth $True

전체 명령에 대한 자세한 설명은 기본 PowerShell RTCCmdlets 참조에서 다음 항목을 참조하십시오.

## 참고 항목

#### 기타 리소스

[New-CsWebServiceConfiguration](new-cswebserviceconfiguration.md)

