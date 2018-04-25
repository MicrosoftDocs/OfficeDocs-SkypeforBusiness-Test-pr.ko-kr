---
title: Set-CsConfigurationStoreLocation
TOCTitle: Set-CsConfigurationStoreLocation
ms:assetid: 1c69a872-8e78-4c78-ba27-f20f04dce59f
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg398258(v=OCS.15)
ms:contentKeyID: 49302982
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Set-CsConfigurationStoreLocation

 

_**마지막으로 수정된 항목:** 2015-03-09_

중앙 관리 저장소의 Active Directory 서비스 제어 지점을 설정합니다. 이 cmdlet은 Lync Server 2010에서 도입되었습니다.

## 구문

    Set-CsConfigurationStoreLocation -SqlServerFqdn <Fqdn> [-Confirm [<SwitchParameter>]] [-Force <SwitchParameter>] [-GlobalSettingsDomainController <Fqdn>] [-MirrorSqlInstanceName <String>] [-MirrorSqlServerFqdn <Fqdn>] [-Report <String>] [-SkipLookup <SwitchParameter>] [-SqlInstanceName <String>] [-WhatIf [<SwitchParameter>]]

## 예제

## 예제 1

예제 1에 표시된 명령은 Lync Server 중앙 관리 저장소에 대한 Active Directory 서비스 제어 지점을 설정합니다. 이 예제에서 SCP는 atl-sql-001.litwareinc.com 컴퓨터와 SQL Server 인스턴스 Rtc를 가리킵니다.

    Set-CsConfigurationStoreLocation -SqlServerFqdn atl-sql-001.litwareinc.com -SqlInstanceName Rtc

## 예제 2

예제 2에 표시된 명령은 예제 1에 표시된 명령의 변형입니다. 이 명령도 Lync Server 중앙 관리 저장소에 대한 Active Directory SCP를 설정합니다. 또한 이 작업의 성공(또는 실패)에 관한 정보가 C:\\Logs\\Store\_Location.html 파일에 기록됩니다. 이 로그는 Report 매개 변수 뒤에 로그 파일의 전체 경로를 포함하면 생성됩니다.

    Set-CsConfigurationStoreLocation -SqlServerFqdn atl-sql-001.litwareinc.com -SqlInstanceName Rtc -Report C:\Logs\Store_Location.html

## 자세한 정보

Active Directory 도메인 서비스는 SCP(서비스 제어 지점)를 사용하여 컴퓨터가 서비스를 찾을 수 있도록 도와줍니다. 예를 들어 Lync Server를 설치하면 Lync Server 데이터를 유지 관리하는 데 사용되는 위치 정보를 중앙 관리 저장소에 제공하는 서비스 제어 지점이 만들어집니다. 데이터베이스에 액세스해야 하는 컴퓨터는 Active Directory에 연결하고 SCP에 포함된 정보를 사용하여 올바른 컴퓨터와 올바른 SQL Server 인스턴스를 찾습니다.

앞에서 설명한 대로 Lync Server를 설치하면 중앙 관리 저장소에 대한 SCP가 자동으로 만들어집니다. 데이터베이스를 다른 컴퓨터로 이동해야 하거나 데이터베이스를 다른 SQL Server 인스턴스로 이동해야 하는 경우 해당 서비스 제어 지점을 업데이트해야 합니다. 이 작업은 **Set-CsConfigurationStoreLocation** cmdlet을 사용하여 수행할 수 있습니다. 이 cmdlet을 실행하면 **Set-CsConfigurationStoreLocation** cmdlet이 Active Directory에서 SqlServer 매개 변수로 지정된 컴퓨터를 검색합니다. 그런 다음 저장소 위치를 해당 컴퓨터의 FQDN으로 설정합니다.

이 cmdlet을 실행할 수 있는 사용자: 기본적으로 RTCUniversalServerAdmins 그룹의 구성원은 **Set-CsConfigurationStoreLocation** cmdlet을 실행할 수 있습니다.

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
<td><p><em>SqlServerFqdn</em></p></td>
<td><p>필수</p></td>
<td><p>Microsoft.Rtc.Management.Deploy.Fqdn</p></td>
<td><p>중앙 관리 저장소가 설치된 컴퓨터의 FQDN(정규화된 도메인 이름)입니다(예: -SqlServer atl-sql-001.litwareinc.com).</p></td>
</tr>
<tr class="even">
<td><p><em>Confirm</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>명령을 실행하기 전에 확인 메시지를 표시합니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>Force</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>명령을 실행할 때 발생할 수 있는 심각하지 않은 오류 메시지를 표시하지 않습니다.</p></td>
</tr>
<tr class="even">
<td><p><em>GlobalSettingsDomainController</em></p></td>
<td><p>선택</p></td>
<td><p>Microsoft.Rtc.Management.Deploy.Fqdn</p></td>
<td><p>전역 설정이 저장된 도메인 컨트롤러의 FQDN입니다. 전역 설정이 Active Directory 시스템 컨테이너에 저장된 경우 이 매개 변수는 루트 도메인 컨트롤러를 가리켜야 합니다. 전역 설정이 구성 컨테이너에 저장된 경우 아무 도메인 컨트롤러나 사용할 수 있으며 이 매개 변수는 생략해도 됩니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>MirrorSqlInstanceName</em></p></td>
<td><p>선택</p></td>
<td><p>System.String</p></td>
<td><p>Lync Server 미러 데이터베이스 테이블 및 데이터가 포함된 SQL Server 인스턴스의 이름입니다(예: -SqlInstanceName &quot;rtc&quot;).</p></td>
</tr>
<tr class="even">
<td><p><em>MirrorSqlServerFqdn</em></p></td>
<td><p>선택</p></td>
<td><p>Microsoft.Rtc.Management.Deploy.Fqdn</p></td>
<td><p>중앙 관리 저장소 미러 데이터베이스가 설치된 컴퓨터의 FQDN(정규화된 도메인 이름)입니다(예: -SqlServer atl-mirror-001.litwareinc.com).</p></td>
</tr>
<tr class="odd">
<td><p><em>Report</em></p></td>
<td><p>선택</p></td>
<td><p>System.String</p></td>
<td><p>cmdlet이 실행될 때 만들어지는 로그 파일의 파일 경로를 지정하는 데 사용됩니다(예: -Report &quot;C:\Logs\ConfigurationStore.html&quot;).</p></td>
</tr>
<tr class="even">
<td><p><em>SkipLookup</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>이 매개 변수를 포함하면 <strong>Set-CsConfigurationStoreLocation</strong> cmdlet에서 지정된 컴퓨터와 지정된 SQL Server 인스턴스를 사용할 수 있는지 확인하지 않고 단순히 서비스 제어 지점을 변경합니다.</p>
<p>이 매개 변수를 포함하지 않으면 지정한 컴퓨터와 지정한 SQL Server 인스턴스를 모두 사용할 수 있어야 SCP가 변경됩니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>SqlInstanceName</em></p></td>
<td><p>선택</p></td>
<td><p>System.String</p></td>
<td><p>Lync Server 테이블 및 데이터가 포함된 SQL Server 인스턴스의 이름입니다. 예: -SqlInstanceName &quot;rtc&quot;</p></td>
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

없음. **Set-CsConfigurationStoreLocation** cmdlet은 파이프라인된 입력을 허용하지 않습니다.

## 반환 형식

**Set-CsConfigurationStoreLocation** cmdlet은 개체나 값을 반환하지 않습니다.

## 참고 항목

#### 기타 리소스

[Get-CsConfigurationStoreLocation](get-csconfigurationstorelocation.md)  
[Remove-CsConfigurationStoreLocation](remove-csconfigurationstorelocation.md)

