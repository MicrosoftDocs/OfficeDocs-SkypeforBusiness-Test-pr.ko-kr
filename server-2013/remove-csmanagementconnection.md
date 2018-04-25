---
title: Remove-CsManagementConnection
TOCTitle: Remove-CsManagementConnection
ms:assetid: 2fe69a3d-0154-418f-b6ee-99a88e5a9c7d
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg425803(v=OCS.15)
ms:contentKeyID: 49303200
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Remove-CsManagementConnection

 

_**마지막으로 수정된 항목:** 2015-03-09_

중앙 관리 저장소의 Active Directory 서비스 제어 지점에 대한 관리 연결을 다시 설정합니다. 이 cmdlet은 Lync Server 2010에서 도입되었습니다.

## 구문

    Remove-CsManagementConnection [-Confirm [<SwitchParameter>]] [-WhatIf [<SwitchParameter>]]

## 예제

## 예제 1

예제 1에 표시된 명령은 기존 관리 연결 정보를 제거하고 Active Directory에 저장된 기본 연결 정보로 바꿉니다.

    Remove-CsManagementConnection

## 자세한 정보

Lync Server의 구성 데이터는 중앙 관리 저장소에 저장되므로 Windows PowerShell과 관리 복제 서비스 둘 다 이 데이터베이스를 찾을 수 있어야 합니다. Lync Server를 설치하면 이 데이터베이스의 위치 정보를 제공하는 서비스 제어 지점이 Active Directory 도메인 서비스에 만들어집니다. 일반적으로 컴퓨터는 이 서비스 제어 지점을 사용하여 중앙 관리 저장소에 연결합니다. 이 연결에 대한 세부 정보를 보려면, 즉 중앙 관리 저장소를 실행 중인 컴퓨터 및 해당 중앙 관리 저장소와의 SQL Server 연결 정보를 확인하려면 **Get-CsManagementConnection** cmdlet을 실행하면 됩니다.

일반적으로 관리 연결을 변경할 필요는 없습니다. 그러나 일시적으로 새 관리 연결을 사용해야 할 수도 있습니다. 기본 연결로 다시 전환할 준비가 되면 **Remove-CsManagementConnection** cmdlet을 실행하기만 하면 됩니다. 이 cmdlet은 현재 연결 정보를 지우고 Active Directory 서비스 제어 지점에 저장된 연결 정보로 바꿉니다. 즉, 원본 연결 정보를 다시 만들 필요가 없으며 **Remove-CsManagementConnection** cmdlet에서 자동으로 이 작업을 수행합니다.

기본 연결을 사용하는 동안 이 cmdlet을 호출해도 아무 문제가 발생하지 않습니다. 이렇게 하면 Active Directory에 저장된 기본 연결 정보를 계속 사용하게 됩니다. 이 cmdlet은 현재 Windows PowerShell 세션의 관리 연결 정보에만 영향을 줍니다. 관리 연결에 대한 변경은 로컬 컴퓨터 및 로컬 Windows PowerShell 인스턴스로 제한됩니다.

이 cmdlet을 실행할 수 있는 사용자: 기본적으로 RTCUniversalUserAdmins, RTCUniversalServerAdmins 및 RTCUniversalReadOnlyAdmins 그룹의 구성원은 **Remove-CsManagementConnection** cmdlet을 로컬로 실행할 수 있습니다. 사용자가 직접 만든 사용자 지정 RBAC(역할 기반 액세스 제어) 역할을 포함하여 이 cmdlet이 할당된 모든 RBAC 역할의 목록을 반환하려면 Windows PowerShell 프롬프트에서 다음 명령을 실행합니다.

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Remove-CsManagementConnection"}

## 매개 변수


<table>
<colgroup>
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
</colgroup>
<thead>
<tr class="header">
<th>매개 변수</th>
<th>필수</th>
<th>유형</th>
<th>설명</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><em>Confirm</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>명령을 실행하기 전에 확인 메시지를 표시합니다.</p></td>
</tr>
<tr class="even">
<td><p><em>WhatIf</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>명령을 실제로 실행하지 않고도 명령이 실행될 경우 발생할 수 있는 현상을 설명합니다.</p></td>
</tr>
</tbody>
</table>


## 입력 형식

없음. **Remove-CsManagementConnection** cmdlet은 파이프라인된 입력을 허용하지 않습니다.

## 반환 형식

없음. 대신 **Remove-CsManagementConnection** cmdlet은 Microsoft.Rtc.Management.Xds.ManagementConnection 개체의 인스턴스를 삭제합니다.

## 참고 항목

#### 기타 리소스

[Get-CsManagementConnection](get-csmanagementconnection.md)  
[Remove-CsConfigurationStoreLocation](remove-csconfigurationstorelocation.md)  
[Set-CsManagementConnection](set-csmanagementconnection.md)

