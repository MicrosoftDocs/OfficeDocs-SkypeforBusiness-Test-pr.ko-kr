---
title: Get-CsManagementConnection
TOCTitle: Get-CsManagementConnection
ms:assetid: b0e2377c-6aab-45d8-b71d-0d37c6f6dae3
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg412849(v=OCS.15)
ms:contentKeyID: 49304744
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Get-CsManagementConnection

 

_**마지막으로 수정된 항목:** 2015-03-09_

중앙 관리 저장소와의 관리 연결에 대한 정보를 반환합니다. 이 cmdlet은 Lync Server 2010에서 도입되었습니다.

## 구문

    Get-CsManagementConnection

## 예제

## 예제 1

예제 1의 명령은 중앙 관리 저장소와의 관리 연결에 대한 정보를 반환합니다.

    Get-CsManagementConnection

## 자세한 정보

Lync Server에 대한 구성 데이터는 중앙 관리 저장소에 저장됩니다. 따라서 Windows PowerShell 및 관리 복제 서비스가 이 데이터베이스를 찾을 수 있어야 합니다. Lync Server를 설치하면 이 데이터베이스의 위치 정보를 제공하는 서비스 제어 지점이 Active Directory 도메인 서비스에 만들어집니다. 일반적으로 컴퓨터는 이 서비스 제어 지점을 사용하여 중앙 관리 저장소에 연결합니다. 이러한 연결에 대한 자세한 정보가 필요한 경우, 즉 중앙 관리 저장소가 실행되는 컴퓨터 및 SQL Server와 중앙 관리 저장소 간의 연결 정보를 알아야 하는 경우 **Get-CsManagementConnection** cmdlet을 실행하기만 하면 됩니다.

**Set-CsManagementConnection** cmdlet을 사용하여 Windows PowerShell의 현재 인스턴스에 대한 임시 관리 연결을 설정한 경우(예를 들어 로컬 복제본에서 사용하기 위해) **Get-CsManagementConnection** cmdlet이 해당 임시 연결에 대한 정보를 보고하게 됩니다. 반대로, **Get-CsConfigurationStoreLocation** cmdlet은 항상 로컬 관리 연결이 지정된 위치에 관계없이 Active Directory의 서비스 제어 지점에 대한 정보를 반환합니다.

이 cmdlet을 실행할 수 있는 사용자: 기본적으로 RTCUniversalUserAdmins, RTCUniversalServerAdmins 및 RTCUniversalReadOnlyAdmins 그룹의 구성원은 **Get-CsManagementConnection** cmdlet을 로컬로 실행할 수 있습니다. 사용자가 직접 만든 사용자 지정 RBAC(역할 기반 액세스 제어) 역할을 포함하여 이 cmdlet이 할당된 모든 RBAC 역할의 목록을 반환하려면 Windows PowerShell 프롬프트에서 다음 명령을 실행합니다.

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Get-CsManagementConnection"}

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
<td><p></p></td>
<td><p></p></td>
<td><p></p></td>
<td><p></p></td>
</tr>
<tr class="even">
<td><p>이 cmdlet은 일반 Windows PowerShell 매개 변수만 제공합니다.</p></td>
<td> </td>
<td> </td>
<td> </td>
</tr>
</tbody>
</table>


## 입력 형식

없음. **Get-CsManagementConnection** cmdlet은 파이프라인된 입력을 허용하지 않습니다.

## 반환 형식

**Get-CsManagementConnection** cmdlet은 Microsoft.Rtc.Management.Xds.ManagementConnection 개체의 인스턴스를 반환합니다.

## 참고 항목

#### 기타 리소스

[Remove-CsManagementConnection](remove-csmanagementconnection.md)  
[Set-CsManagementConnection](set-csmanagementconnection.md)

