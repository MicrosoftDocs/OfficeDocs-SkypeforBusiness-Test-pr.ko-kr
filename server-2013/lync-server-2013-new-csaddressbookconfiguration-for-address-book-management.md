---
title: 주소록 관리용 new-csaddressbookconfiguration
TOCTitle: 주소록 관리용 new-csaddressbookconfiguration
ms:assetid: a58ddc8c-ae04-4141-b69e-e45374a67d72
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg429718(v=OCS.15)
ms:contentKeyID: 49304621
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# 주소록 관리용 new-csaddressbookconfiguration

 

_**마지막으로 수정된 항목:** 2012-11-01_

이 cmdlet을 실행할 수 있는 사용자: 기본적으로 RTCUniversalServerAdmins 그룹에 속한 구성원은 new-csaddressbookconfiguration cmdlet을 로컬로 실행할 수 있습니다. 사용자가 직접 만든 사용자 지정 RBAC(역할 기반 액세스 제어) 역할을 포함하여 이 cmdlet이 할당된 모든 RBAC 역할의 목록을 가져오려면 Windows PowerShell 프롬프트에서 다음 명령을 실행합니다.

    Get-CsAdminRole | Where-Object {$_.Cmdlets -match "new-csaddressbookconfiguration"}

new-csaddressbookconfiguration cmdlet은 새 구성을 만들어 주소록의 동작을 관리합니다. 이 cmdlet은 주소록 서비스에서 클라이언트 다운로드 파일을 만들지 여부, 정규화 규칙 사용 여부, 델타 및 컴팩트 델타 파일 보존 기간, 전체 새 파일 만들기를 통합하기 전 델타 파일 크기, 전체 파일 주소록이 만들어지는 시기 및 사용자 데이터베이스에서 정보 동기화를 위한 내부 상태 등을 정의합니다.

예:

    new-csaddressbookconfiguration -Identity site:Redmond -KeepDuration 15 -SynchronizePollingInterval 00:10:00

전체 명령에 대한 자세한 설명은 기본 PowerShell RTCCmdlets 참조에서 다음 항목을 참조하십시오.

## 참고 항목

#### 기타 리소스

[new-csaddressbookconfiguration](https://docs.microsoft.com/en-us/powershell/module/skype/New-CsAddressBookConfiguration)

