---
title: 주소록 관리용 Update-CsAddressBook
TOCTitle: 주소록 관리용 Update-CsAddressBook
ms:assetid: 0ffd2ef8-201c-44aa-8c64-1c7b0eaa7d48
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg429695(v=OCS.15)
ms:contentKeyID: 49302832
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# 주소록 관리용 Update-CsAddressBook

 

_**마지막으로 수정된 항목:** 2012-11-01_

이 cmdlet을 실행할 수 있는 사용자: 기본적으로 RTCUniversalUserAdmins 및 RTCUniversalServerAdmins 그룹의 구성원은 Update-CsAddressBook cmdlet을 로컬로 실행할 수 있습니다. 사용자가 직접 만든 사용자 지정 RBAC(역할 기반 액세스 제어) 역할을 포함하여 이 cmdlet이 할당된 모든 RBAC 역할의 목록을 가져오려면 Windows PowerShell 프롬프트에서 다음 명령을 실행합니다.

    Get-CsAdminRole | Where-Object {$_.Cmdlets -match "Update-CsAddressBook"}

Update-CsAddressBook cmdlet은 Office Communications Server의 **abserver.exe –syncNow** 명령을 대체합니다. 이 cmdlet은 예약된 시간을 기다리지 않고 동기화를 즉시 시작하는 데 사용됩니다. 첫 번째 예제 명령에서는 조직의 모든 주소록을 업데이트합니다. 두 번째 예제 명령에서는 정의된 서버에 연결된 주소록만 업데이트합니다.


> [!NOTE]
> Lync Server 2013에서 Lync Server User Replicator는 Active Directory의 변경 내용을 가져와서 구성된 간격에 따라 Lync Server 사용자 데이터베이스를 업데이트합니다. 또한 관리자가 Update-CSAddressBook을 실행하지 않아도 Lync Server User Replicator가 RTCab 데이터베이스에 대한 변경 내용을 빠르게 전파합니다. 관리자는 주소록 파일 다운로드가 사용하도록 설정된 경우에만 Update-CSAddressBook을 실행하면 됩니다.



예:

    Update-CsAddressBook

    Update-CsAddressBook -Fqdn atl-abs-001.contoso.com

전체 명령에 대한 자세한 설명은 기본 PowerShell RTCCmdlets 참조에서 다음 항목을 참조하십시오.

## 참고 항목

#### 기타 리소스

[Update-CsAddressBook](update-csaddressbook.md)

