---
title: Set-CsManagementConnection
TOCTitle: Set-CsManagementConnection
ms:assetid: f7cf19ba-6c56-4f74-9757-843e1ca0c9a1
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg413045(v=OCS.15)
ms:contentKeyID: 49305567
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Set-CsManagementConnection

 

_**마지막으로 수정된 항목:** 2015-03-09_

중앙 관리 저장소에 대한 관리 연결을 수정합니다. 이 cmdlet은 Lync Server 2010에서 도입되었습니다.

## 구문

    Set-CsManagementConnection -Connection <String> -StoreProvider <FileSystem | Sql | Memory> [-Confirm [<SwitchParameter>]] [-EnableCaching <$true | $false>] [-WhatIf [<SwitchParameter>]]

## 예제

## 예제 1

예제 1에 표시된 명령은 atl-sql-001.litwareinc.com 컴퓨터의 rtcbackup이라는 SQL Server 인스턴스에 대한 관리 연결을 변경합니다.

    Set-CsManagementConnection -StoreProvider Sql -Connection "atl-sql-001.litwareinc.com\rtcbackup"

## 예제 2

예제 2에서는 파일 시스템, 더 구체적으로 말해 로컬 컴퓨터의 C:\\TestTopology 폴더에 대한 관리 연결을 설정합니다.

    Set-CsManagementConnection -StoreProvider FileSystem -Connection "C:\TestTopology"

## 자세한 정보

Lync Server에 대한 구성 데이터는 중앙 관리 저장소에 저장됩니다. 따라서 Windows PowerShell 및 관리 복제 서비스가 이 데이터베이스를 찾을 수 있어야 합니다. Lync Server를 설치하면 이 데이터베이스의 위치 정보를 제공하는 서비스 제어 지점이 Active Directory 도메인 서비스에 만들어집니다. 일반적으로 컴퓨터는 이 서비스 제어 지점을 사용하여 중앙 관리 저장소에 연결합니다. 이러한 연결에 대한 자세한 정보가 필요한 경우, 즉 중앙 관리 저장소가 실행되는 컴퓨터 및 SQL Server와 중앙 관리 저장소 간의 연결 정보를 알아야 하는 경우 **Get-CsManagementConnection** cmdlet을 실행하기만 하면 됩니다.

대부분의 경우 관리 연결이 설정된 후에는 이를 변경할 필요가 없습니다. 그러나 하드웨어 또는 소프트웨어 오류가 발생할 경우 임시 연결을 사용해야 할 수 있습니다. 예를 들어 로컬 복제본에서 작동하도록 컴퓨터를 구성할 수 있습니다. **Set-CsManagementConnection** cmdlet을 사용하면 중앙 관리 저장소의 새 위치를 제공할 수 있습니다.

임시 관리 연결을 사용할 때 Lync Server에 대해 변경한 내용은 원래 연결로 다시 전환할 때까지 지속되지 않습니다. 다시 전환하려면 **Remove-CsManagementConnection** cmdlet을 실행하면 됩니다. 예를 들어 파일 시스템을 임시로 저장소 공급자로 사용하기로 했다고 가정하겠습니다. 이 경우 관리 연결을 변경한 다음 각각 XML 파일로 인스턴스화되는 여러 개의 새 음성 정책을 만듭니다. 다시 원래 관리 연결로 전환하면 이러한 새 음성 정책은 원래 중앙 관리 저장소에 기록된 적이 없으므로 사라지게 됩니다.

또한 이 cmdlet을 실행하여 변경한 사항은 로컬 컴퓨터에만 적용됩니다. **Set-CsManagementConnection** cmdlet을 사용하여 다른 컴퓨터의 관리 연결을 변경할 수는 없습니다.

이 cmdlet을 실행할 수 있는 사용자: 기본적으로 RTCUniversalUserAdmins, RTCUniversalServerAdmins 및 RTCUniversalReadOnlyAdmins 그룹의 구성원은 **Set-CsManagementConnection** cmdlet을 로컬로 실행할 수 있습니다.

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
<td><p><em>Connection</em></p></td>
<td><p>필수</p></td>
<td><p>System.String</p></td>
<td><p>관리 연결로 사용할 SQL Server 인스턴스 또는 파일 시스템 폴더의 위치 정보입니다.</p>
<p>예를 들어 atl-sql-001.litwareinc.com 컴퓨터에 있는 rtcbackup이라는 SQL Server 인스턴스에 대한 새 관리 연결을 설정하는 경우 -Connection &quot;atl-sql-001.litwareinc.com\rtcbackup&quot; 구문을 사용합니다.</p>
<p>C:\TestTopology 폴더에 대한 관리 연결을 만들려면 -Connection &quot;C:\TestTopology&quot; 구문을 사용합니다. 폴더가 없는 경우에는 <strong>Set-CsManagementConnection</strong> cmdlet이 새 폴더를 만듭니다.</p></td>
</tr>
<tr class="even">
<td><p><em>StoreProvider</em></p></td>
<td><p>필수</p></td>
<td><p>Microsoft.Rtc.Management.Store.StoreProvider</p></td>
<td><p>구성 정보에 사용할 백 엔드 저장소 유형을 지정합니다. 구성 데이터를 SQL Server에 저장하려면 StoreProvider를 -StoreProvider Sql과 같이 설정합니다. 파일 시스템에 구성 데이터를 저장하려면 -StoreProvider FileSystem 구문을 사용합니다. Microsoft 지원 담당자가 지시하지 않은 경우 StoreProvider 속성을 수정하지 않는 것이 좋습니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>Confirm</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>명령을 실행하기 전에 확인 메시지를 표시합니다.</p></td>
</tr>
<tr class="even">
<td><p><em>EnableCaching</em></p></td>
<td><p>선택</p></td>
<td><p>System.Boolean</p></td>
<td><p>True($True)로 설정하면 관리 연결에 대해 캐싱을 사용하도록 설정합니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>WhatIf</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>명령을 실제로 실행하지 않고도 명령이 실행될 경우 발생할 수 있는 현상을 설명합니다.</p></td>
</tr>
</tbody>
</table>


## 입력 형식

없음. **Set-CsManagementConnection** cmdlet은 파이프라인된 입력을 허용하지 않습니다.

## 반환 형식

**Set-CsManagementConnection** cmdlet은 값이나 개체를 반환하지 않습니다. 대신에 이 cmdlet은 Microsoft.Rtc.Management.Store.StoreProvider 개체의 인스턴스를 구성합니다.

## 참고 항목

#### 기타 리소스

[Get-CsManagementConnection](get-csmanagementconnection.md)  
[Remove-CsManagementConnection](remove-csmanagementconnection.md)  
[Set-CsConfigurationStoreLocation](set-csconfigurationstorelocation.md)

