---
title: 주소록 관리용 Get-CsWebServiceConfiguration
TOCTitle: 주소록 관리용 Get-CsWebServiceConfiguration
ms:assetid: 0b223733-5224-47d1-9b47-2109e6f135c9
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg429692(v=OCS.15)
ms:contentKeyID: 49302763
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# 주소록 관리용 Get-CsWebServiceConfiguration

 

_**마지막으로 수정된 항목:** 2012-11-01_

이 cmdlet을 실행할 수 있는 사용자: 기본적으로 RTCUniversalUserAdmins 및 RTCUniversalServerAdmins 그룹의 구성원은 Get-CsWebServiceConfiguration cmdlet을 로컬로 실행할 수 있습니다. 사용자가 직접 만든 사용자 지정 RBAC(역할 기반 액세스 제어) 역할을 포함하여 이 cmdlet이 할당된 모든 RBAC 역할의 목록을 가져오려면 Windows PowerShell 프롬프트에서 다음 명령을 실행합니다.

    Get-CsAdminRole | Where-Object {$_.Cmdlets -match "Get-CsWebServiceConfiguration"}

Get-CsWebServiceConfiguration은 현재 조직에서 사용 중인 웹 서비스 구성 정보를 반환합니다. 메일 그룹 확장 기능의 상태는 주소록 서비스와 관련이 있습니다. EnableGroupExpansion 특성이 True이면 조직에서 현재 그룹 확장을 허용하는 것입니다.

예:

    Get-CsWebServiceConfiguration -Identity site:Redmond

전체 명령에 대한 자세한 설명은 기본 PowerShell RTCCmdlets 참조에서 다음 항목을 참조하십시오.

## 참고 항목

#### 기타 리소스

[Get-CsWebServiceConfiguration](get-cswebserviceconfiguration.md)

