---
title: Set-CsTestDevice
TOCTitle: Set-CsTestDevice
ms:assetid: 0a9fabfc-b0d3-4c94-ae04-0a87f0886db8
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg398156(v=OCS.15)
ms:contentKeyID: 49302753
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Set-CsTestDevice

 

_**마지막으로 수정된 항목:** 2015-03-09_

조직에서 사용하도록 구성된 장치 업데이트 관리 테스트 장치를 하나 이상 수정합니다. 관리자는 테스트 장치를 통해 펌웨어 업데이트를 조직의 모든 장치에 배포하기 전에 테스트할 수 있습니다. 이 cmdlet은 Lync Server 2010에서 도입되었습니다.

## 구문

    Set-CsTestDevice [-Identity <XdsIdentity>] <COMMON PARAMETERS>

    Set-CsTestDevice [-Instance <PSObject>] <COMMON PARAMETERS>

    COMMON PARAMETERS: [-Confirm [<SwitchParameter>]] [-Force <SwitchParameter>] [-Identifier <String>] [-IdentifierType <MACAddress | SerialNumber>] [-WhatIf [<SwitchParameter>]]

## 예제

## 예제 1

예제 1에서는 Redmond 사이트에 할당된 UCPhone이라는 테스트 장치의 Identifier 속성을 수정합니다.

    Set-CsTestDevice -Identity site:Redmond/UCPhone -Identifier "09768-ABDR-83295"

## 예제 2

예제 2에 표시된 명령도 Redmond 사이트에 할당된 UCPhone이라는 테스트 장치를 수정합니다. 그러나 이 경우에는 명령이 새 Identifier를 지정할 뿐 아니라 새 IdentifierType인 SerialNumber도 할당합니다.

    Set-CsTestDevice -Identity site:Redmond/UCPhone -IdentifierType SerialNumber -Identifier "09768-ABDR-83295"

## 자세한 정보

관리자는 Lync Phone Edition을 실행하는 특정 전화 또는 기타 장치를 테스트 장치로 식별하여 펌웨어 업데이트를 조직의 모든 관련 장치에 적용하기 전에 이러한 업데이트를 확인 및 승인할 수 있습니다. 장치 업데이트 규칙을 Lync Server로 가져올 때 이러한 규칙은 "대기 중"으로 표시됩니다. 이는 대상 장치에서 이러한 규칙에 해당하는 업데이트를 자동으로 다운로드 및 설치하지 않음을 의미합니다.

대신 이러한 대기 중인 규칙은 관련 테스트 장치에서 다운로드하여 설치합니다. 테스트 장치의 기본 개념이 바로 이것입니다. 즉, 새 장치 업데이트 규칙은 테스트 장치에 자동으로 적용되므로 관리자는 펌웨어 업데이트가 예상대로 작동하는지 여부를 확인할 수 있습니다. 예상대로 작동할 경우 관리자는 규칙을 승인된 것으로 표시할 수 있습니다. 그러면 승인된 규칙은 조직의 모든 관련 장치에 다운로드 및 설치됩니다.

테스트 장치는 **New-CsTestDevice** cmdlet을 사용하여 만듭니다. 테스트 장치가 만들어진 후 **Set-CsTestDevice** cmdlet을 사용하여 해당 장치 또는 다른 테스트 장치의 Identifier 및/또는 IdentifierType을 변경할 수 있습니다.

이 cmdlet을 실행할 수 있는 사용자: 기본적으로 RTCUniversalServerAdmins 그룹의 구성원은 **Set-CsTestDevice** cmdlet을 로컬로 실행할 수 있습니다. 사용자가 직접 만든 사용자 지정 RBAC(역할 기반 액세스 제어) 역할을 포함하여 이 cmdlet이 할당된 모든 RBAC 역할의 목록을 반환하려면 Windows PowerShell 프롬프트에서 다음 명령을 실행합니다.

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Set-CsTestDevice"}

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
<td><p><em>Force</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>명령을 실행할 때 발생할 수 있는 심각하지 않은 오류 메시지를 표시하지 않습니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>Identifier</em></p></td>
<td><p>선택</p></td>
<td><p>System.String</p></td>
<td><p>IdentifierType을 기준으로 새 테스트 장치의 MAC(Media Access Control) 주소 또는 일련 번호를 나타냅니다. 일련 번호는 숫자, 문자, 하이픈 및 밑줄을 사용하여 지정할 수 있습니다. 예를 들면 다음과 같습니다.</p>
<p>-Identifier &quot;AB37_679e&quot;</p>
<p>MAC 주소는 6개 이상의 두 문자 쌍으로 지정해야 합니다. 이러한 쌍은 MAC 주소에 따라 단일 문자열 값이거나 하이픈 또는 콜론으로 구분된 값일 수 있습니다. MAC 주소는 문자 및/또는 숫자를 포함할 수 있습니다. 유효한 MAC 주소의 예를 들면 다음과 같습니다.</p>
<p>010203040506</p>
<p>01-02-03-04-05-06</p>
<p>01:02:03:04:05:06</p>
<p>01-02-03-04-05와 같은 MAC 주소는 두 문자 쌍이 6개 미만이므로 허용되지 않습니다.</p></td>
</tr>
<tr class="even">
<td><p><em>IdentifierType</em></p></td>
<td><p>선택</p></td>
<td><p>Microsoft.Rtc.Management.WritableConfig.Settings.DeviceUpdate.IdentifierType</p></td>
<td><p>테스트 장치가 해당 MAC 주소 또는 일련 번호로 고유하게 식별되는지를 나타냅니다. 장치를 해당 MAC 주소로 식별하려면 IdentifierType을 MACAddress로 설정합니다. 장치를 해당 일련 번호로 식별하려면 IdentifierType을 SerialNumber로 설정합니다. MACAddress 및 SerialNumber 값만 사용할 수 있습니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>Identity</em></p></td>
<td><p>선택</p></td>
<td><p>Microsoft.Rtc.Management.Xds.XdsIdentity</p></td>
<td><p>수정할 테스트 장치의 ID를 나타냅니다(예: -Identity site:Redmond/UCPhoneTestDevice). ID를 지정할 때는 와일드카드를 사용할 수 없습니다.</p></td>
</tr>
<tr class="even">
<td><p><em>Instance</em></p></td>
<td><p>선택</p></td>
<td><p>테스트 장치 개체</p></td>
<td><p>개별 매개 변수 값을 설정하는 대신 cmdlet에 개체에 대한 참조를 전달할 수 있습니다.</p></td>
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

Microsoft.Rtc.Management.WritableConfig.Settings.DeviceUpdate.TestDevice 개체입니다. **Set-CsTestDevice** cmdlet은 테스트 장치 개체의 파이프라인된 입력을 허용합니다.

## 반환 형식

**Set-CsTestDevice** cmdlet은 값이나 개체를 반환하지 않습니다. 대신 이 cmdlet은 Microsoft.Rtc.Management.WritableConfig.Settings.DeviceUpdate.TestDevice 개체의 인스턴스를 구성합니다.

## 참고 항목

#### 기타 리소스

[Get-CsTestDevice](get-cstestdevice.md)  
[New-CsTestDevice](new-cstestdevice.md)  
[Remove-CsTestDevice](remove-cstestdevice.md)

