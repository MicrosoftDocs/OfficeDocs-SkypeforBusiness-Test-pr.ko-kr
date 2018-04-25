---
title: Get-CsAdForest
TOCTitle: Get-CsAdForest
ms:assetid: f063df2f-fdb2-4599-bfb0-fb4ba3584e3b
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg412995(v=OCS.15)
ms:contentKeyID: 49305477
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Get-CsAdForest

 

_**마지막으로 수정된 항목:** 2015-03-09_

Active Directory 포리스트가 Lync Server를 설치할 수 있도록 올바르게 구성되었는지 여부를 나타내는 정보를 반환합니다. 이 cmdlet은 Lync Server 2010에서 도입되었습니다.

## 구문

    Get-CsAdForest [-GlobalCatalog <Fqdn>] [-GlobalSettingsDomainController <Fqdn>] [-Report <String>] [-RootDomainController <Fqdn>] [-SkipPrepareCheck <$true | $false>]

## 예제

## 예제 1

예제 1에서는 Active Directory 포리스트가 Lync Server를 설치할 수 있도록 올바르게 구성되었는지 여부를 나타내는 정보를 반환합니다.

    Get-CsAdForest

## 예제 2

예제 2에서는 포리스트 상태 정보를 반환하고 포리스트 준비 상태를 화면에 표시합니다. 또한 포리스트 상태를 확인하기 위해 수행해야 하는 단계에 대한 자세한 정보를 C:\\Logs\\ForestState.html이라는 파일에 기록합니다. 이 파일은 권한이 확인된 모든 Active Directory 그룹 및 Active Directory 컨테이너의 자세한 목록 등을 포함합니다.

    Get-CsAdForest -Report C:\Logs\ForestState.html

## 자세한 정보

Lync Server를 설치하려면 Active Directory 도메인 서비스에서 몇 가지 포리스트 수준을 변경해야 합니다. 여기에는 Lync Server 관련 표시 지정자 및 개체를 만들고, Lync Server를 관리하는 데 필요한 유니버설 보안 그룹을 만들고, 전역 설정 개체에 이러한 그룹에 대한 액세스 권한을 부여하는 과정이 포함됩니다. **Get-CsAdForest** cmdlet은 포리스트에 Lync Server를 설치할 수 있는지 여부를 나타내는 단일 값을 반환합니다. **Get-CsAdForest**cmdlet이 LC\_FORESTSETTINGS\_STATE\_READY 값을 반환하는 경우 Lync Server를 포리스트에 설치할 수 있습니다. cmdlet이 LC\_FORESTSETTINGS\_STATE\_NOT\_READY를 반환하는 경우 Lync Server를 설치하려고 시도하기 전에 포리스트를 올바르게 준비해야 합니다.

**Get-CsAdForest** cmdlet은 설치 마법사의 일부로 실행됩니다. 마법사에서 해당 포리스트가 올바르게 준비되지 않았다고 판단하는 경우 오류 메시지가 나타나고 설치가 중지됩니다. 그러나 Lync Server 설치를 시도하기 전에 설치 마법사와는 별도로 **Get-CsAdForest** cmdlet을 실행하여 포리스트 상태를 확인할 수 있습니다.

**Get-CsAdForest**cmdlet은 다음 Microsoft Office Communications Server 2007 R2 명령과 동일한 기능을 수행합니다.

Lcscmd.exe /forest /action:CheckForestPrepState

이 cmdlet을 실행할 수 있는 사용자: 기본적으로 Active Directory에 대한 읽기 권한을 가진 사용자는 누구나 **Get-CsAdForest** cmdlet을 로컬로 실행할 수 있습니다. 일반적으로 모든 도메인 구성원은 이 권한이 있습니다.

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Get-CsAdForest"}

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
<td><p><em>GlobalCatalog</em></p></td>
<td><p>선택</p></td>
<td><p>Microsoft.Rtc.Management.Deploy.Fqdn</p></td>
<td><p>도메인에 있는 전역 카탈로그 서버의 FQDN(정규화된 도메인 이름)입니다. 사용자 도메인의 계정을 가진 컴퓨터에서 <strong>Get-CsAdForest</strong> cmdlet을 실행하는 경우 이 매개 변수가 필요하지 않습니다.</p></td>
</tr>
<tr class="even">
<td><p><em>GlobalSettingsDomainController</em></p></td>
<td><p>선택</p></td>
<td><p>Microsoft.Rtc.Management.Deploy.Fqdn</p></td>
<td><p>전역 설정이 저장된 도메인 컨트롤러의 FQDN입니다. 전역 설정이 AD DS의 시스템 컨테이너에 저장된 경우 이 매개 변수는 루트 도메인 컨트롤러를 가리켜야 합니다. 전역 설정이 구성 컨테이너에 저장된 경우 아무 도메인 컨트롤러나 사용할 수 있으며 이 매개 변수는 생략해도 됩니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>Report</em></p></td>
<td><p>선택</p></td>
<td><p>System.String</p></td>
<td><p>cmdlet이 실행될 때 만들어지는 로그 파일의 파일 경로를 지정하는 데 사용됩니다(예: -Report &quot;C:\Logs\ForestPrep.html&quot;).</p></td>
</tr>
<tr class="even">
<td><p><em>RootDomainController</em></p></td>
<td><p>선택</p></td>
<td><p>Microsoft.Rtc.Management.Deploy.Fqdn</p></td>
<td><p>외부 도메인의 리소스에 액세스해야 하는 클라이언트를 위해 신뢰 경로를 만드는 데 사용되는 루트 도메인 컨트롤러의 FQDN입니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>SkipPrepareCheck</em></p></td>
<td><p>선택</p></td>
<td><p>System.Boolean</p></td>
<td><p>True($True)로 설정하면 Get-CsAdForest가 초기 준비 검사를 수행하지 않고 실행됩니다.</p></td>
</tr>
</tbody>
</table>


## 입력 형식

없음.

## 반환 형식

**Get-CsAdForest**cmdlet은 Microsoft.Rtc.Management.Deployment.LcForestSettingsState 개체의 인스턴스를 반환합니다.

