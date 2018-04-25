---
title: New-CsTestDevice
TOCTitle: New-CsTestDevice
ms:assetid: 3d223c5e-b987-4353-9bf7-b247a2bdfa25
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg425899(v=OCS.15)
ms:contentKeyID: 49303383
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# New-CsTestDevice

 

_**마지막으로 수정된 항목:** 2015-03-09_

새 장치 업데이트 관리 테스트 장치를 만듭니다. 테스트 장치를 통해 관리자는 조직 내 모든 장치에 펌웨어 업데이트를 배포하기 전에 업데이트 내용을 테스트할 수 있습니다. 이 cmdlet은 Lync Server 2010에서 도입되었습니다.

## 구문

    New-CsTestDevice -Name <String> -Parent <String> <COMMON PARAMETERS>

    New-CsTestDevice -Identity <XdsIdentity> <COMMON PARAMETERS>

    COMMON PARAMETERS: -Identifier <String> -IdentifierType <MACAddress | SerialNumber> [-Confirm [<SwitchParameter>]] [-Force <SwitchParameter>] [-InMemory <SwitchParameter>] [-WhatIf [<SwitchParameter>]]

## 예제

## 예제 1

예제 1에서는 Redmond 사이트에 대한 새 테스트 장치(UCPhone)를 만듭니다. 장치 ID를 지정하는 데 사용되는 구문은 장치 범위(site:Redmond) 뒤에 / 문자와 장치 이름(UCPhone)을 포함합니다. 이 장치는 일련 번호를 IdentifierType으로 사용하며 일련 번호 07823-A345가 지정됩니다.

    New-CsTestDevice -Identity site:Redmond/UCPhone -IdentifierType SerialNumber -Identifier "07823-A345"

## 예제 2

예제 2에 표시된 명령은 예제 1에 표시된 명령의 변형이지만 예제 2에서는 Identity 매개 변수를 사용하지 않습니다. 대신, Parent 매개 변수를 사용하여 새 테스트 장치의 범위(site:Redmond)를 지정하고 Name 매개 변수를 사용하여 새 장치의 이름(UCPhone)을 나타냅니다. **New-CsTestDevice** cmdlet은 두 매개 변수 값을 사용하여 자동으로 테스트 장치 ID(site:Redmond/UCPhone)를 생성합니다.

    New-CsTestDevice -Parent "site:Redmond" -Name UCPhone -IdentifierType SerialNumber -Identifier "07823-A345"

## 자세한 정보

관리자는 Lync Phone Edition 또는 기타 장치와 호환되는 특정 전화를 테스트 장치로 식별하여 펌웨어 업데이트를 조직의 관련 장치에 적용하기 전에 이러한 업데이트를 확인 및 승인할 수 있습니다. 장치 업데이트 규칙을 Lync Server로 가져올 때 이러한 규칙은 "대기 중"으로 표시됩니다. 이는 대상 장치에서 이러한 규칙에 해당하는 업데이트를 자동으로 다운로드 및 설치하지 않음을 의미합니다.

대신 관련 테스트 장치가 보류 중인 이 규칙을 다운로드 및 설치합니다. 테스트 장치의 기본 개념이 바로 이것입니다. 즉, 새 장치 업데이트 규칙은 테스트 장치에 자동으로 적용되므로 관리자는 펌웨어 업데이트가 예상대로 작동하는지 여부를 확인할 수 있습니다. 예상대로 작동하는 경우 관리자는 규칙을 승인된 것으로 표시할 수 있습니다. 그런 다음 조직 내 모든 관련 장치가 승인된 규칙을 다운로드 및 설치합니다.

테스트 장치는 **New-CsTestDevice** cmdlet을 사용하여 만듭니다. 전역 범위 또는 사이트 범위에서 이러한 장치를 구성할 수 있습니다.

이 cmdlet을 실행할 수 있는 사용자: 기본적으로 RTCUniversalServerAdmins 그룹의 구성원은 **New-CsTestDevice** cmdlet을 로컬로 실행할 수 있습니다. 사용자가 직접 만든 사용자 지정 RBAC(역할 기반 액세스 제어) 역할을 포함하여 이 cmdlet이 할당된 모든 RBAC 역할의 목록을 반환하려면 Windows PowerShell 프롬프트에서 다음 명령을 실행합니다.

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "New-CsTestDevice"}

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
<td><p><em>Identifier</em></p></td>
<td><p>필수</p></td>
<td><p>System.String</p></td>
<td><p>IdentifierType을 기준으로 새 테스트 장치의 MAC(Media Access Control) 주소 또는 일련 번호를 나타냅니다. 일련 번호는 숫자, 문자, 하이픈 및 밑줄을 사용하여 지정할 수 있습니다. 예를 들면 다음과 같습니다.</p>
<p>-Identifier &quot;AB37_679e&quot;</p>
<p>MAC 주소는 6개 이상의 두 문자 쌍으로 지정해야 합니다. 이러한 쌍은 MAC 주소에 따라 단일 문자열로 결합되거나 하이픈 또는 콜론으로 구분될 수 있습니다. MAC 주소는 문자 및/또는 숫자를 포함할 수 있습니다. 유효한 MAC 주소의 예를 들면 다음과 같습니다.</p>
<p>010203040506</p>
<p>01-02-03-04-05-06</p>
<p>01:02:03:04:05:06</p>
<p>01-02-03-04-05와 같은 MAC 주소는 두 문자 쌍이 6개 미만이므로 허용되지 않습니다.</p></td>
</tr>
<tr class="even">
<td><p><em>IdentifierType</em></p></td>
<td><p>필수</p></td>
<td><p>Microsoft.Rtc.Management.WritableConfig.Settings.DeviceUpdate.IdentifierType</p></td>
<td><p>테스트 장치가 해당 MAC 주소 또는 일련 번호로 고유하게 식별되는지를 나타냅니다. 장치를 해당 MAC 주소로 식별하려면 IdentifierType을 MACAddress로 설정합니다. 장치를 해당 일련 번호로 식별하려면 IdentifierType을 SerialNumber로 설정합니다. MACAddress 및 SerialNumber 값만 사용할 수 있습니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>Identity</em></p></td>
<td><p>필수</p></td>
<td><p>Microsoft.Rtc.Management.Xds.XdsIdentity</p></td>
<td><p>새 테스트 장치의 ID를 나타냅니다. ID는 테스트 장치를 할당할 범위(예: site:Redmond) 및 새 장치의 이름(예: UCPhone)으로 구성됩니다. UCPhone이라는 테스트 장치를 Redmond 사이트에 할당하려면 Identity 매개 변수가 -Identity &quot;site:Redmond/UCPhone&quot;과 유사해야 합니다.</p></td>
</tr>
<tr class="even">
<td><p><em>Name</em></p></td>
<td><p>필수</p></td>
<td><p>System.String</p></td>
<td><p>새 테스트 장치의 이름입니다. 이름은 지정된 범위 내에서 고유해야 합니다. Name 매개 변수는 Parent 매개 변수를 사용하는 경우에만 사용해야 합니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>Parent</em></p></td>
<td><p>필수</p></td>
<td><p>System.String</p></td>
<td><p>새 테스트 장치를 할당할 범위의 이름(예: site:Redmond)입니다. Parent 매개 변수를 사용하는 경우 Name 매개 변수도 사용해야 합니다(예: -Parent site:Redmond -Name UCPhone). Parent를 사용하는 경우에는 Identity를 사용하지 않아야 하고 그 반대의 경우도 마찬가지입니다.</p></td>
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
<td><p><em>InMemory</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>개체를 실제로 영구 변경 사항으로 커밋하지 않고 개체 참조를 만듭니다. 이 매개 변수와 함께 호출된 이 cmdlet의 결과를 변수로 할당하면 개체 참조의 속성을 변경한 후 이 cmdlet과 일치하는 Set- cmdlet을 호출하여 해당 변경 사항을 커밋할 수 있습니다.</p></td>
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

없음. **New-CsTestDevice** cmdlet은 파이프라인된 입력을 허용하지 않습니다.

## 반환 형식

Microsoft.Rtc.Management.WritableConfig.Settings.DeviceUpdate.TestDevice 개체의 새 인스턴스를 만듭니다.

## 참고 항목

#### 기타 리소스

[Get-CsTestDevice](get-cstestdevice.md)  
[Remove-CsTestDevice](remove-cstestdevice.md)  
[Set-CsTestDevice](set-cstestdevice.md)

