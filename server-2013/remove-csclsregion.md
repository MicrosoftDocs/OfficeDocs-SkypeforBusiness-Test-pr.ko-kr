---
title: Remove-CsClsRegion
TOCTitle: Remove-CsClsRegion
ms:assetid: 6ab1596e-0e27-44e7-8cbc-efd4064ba58b
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/JJ204971(v=OCS.15)
ms:contentKeyID: 49303936
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Remove-CsClsRegion

 

_**마지막으로 수정된 항목:** 2015-03-09_

하나 이상의 중앙 로깅 구성 영역을 제거합니다. 관리자는 중앙 로깅을 통해 여러 컴퓨터에서 이벤트 추적을 동시에 사용하거나 사용하지 않도록 설정할 수 있습니다. 중앙 로깅 영역은 비즈니스용 Skype Online용입니다.

이 cmdlet은 Lync Server 2013에서 도입되었습니다.

## 구문

    Remove-CsClsRegion -Identity <XdsIdentity> [-Confirm [<SwitchParameter>]] [-Force <SwitchParameter>] [-WhatIf [<SwitchParameter>]]

## 예제

## 예제 1

예제 1에 표시된 명령은 ID가 global/US인 중앙 로깅 영역을 제거합니다.

    Remove-CsClsRegion -Identity "global/US"

## 예제 2

예제 2에서는 전역 범위에서 구성된 모든 중앙 로깅 영역을 제거합니다. 이 작업을 수행하기 위해 명령은 먼저 Filter 매개 변수를 포함하여 **Get-CsClsRegion** cmdlet을 호출합니다. 필터 값 "global/\*"는 반환되는 데이터를 전역 범위에서 구성된 영역으로 제한합니다. 이러한 영역은 **Remove-CsClsRegion** cmdlet에 파이프되며 해당 cmdlet에 의해 삭제됩니다.

    Get-CsClsRegion -Filter "global/*" | Remove-CsClsRegion 

## 예제 3

예제 3에서는 보안 그룹 접미사 EMEA가 포함된 모든 중앙 로깅 영역을 삭제합니다. 이 작업을 수행하기 위해 명령은 먼저 매개 변수 없이 **Get-CsClsRegion** cmdlet을 호출합니다. 그러면 조직에서 사용하도록 구성된 모든 중앙 로깅 영역의 컬렉션이 반환됩니다. 이 컬렉션은 Where-Object cmdlet에 파이프되며, 해당 cmdlet은 SecurityGroupSuffix 속성이 EMEA와 같은(-eq) 영역만 선택합니다. 이 영역의 하위 컬렉션은 **Remove-CsClsRegion** cmdlet에 파이프되며, 해당 cmdlet은 하위 컬렉션의 각 영역을 삭제합니다.

    Get-CsClsRegion | Where-Object {$_.SecurityGroupSuffix -eq "EMEA" | Remove-CsClsRegion

## 자세한 정보

중앙 로깅 서비스( Microsoft Lync Server 2010에서 사용하는 OCSLogger 및 OCSTracer 도구를 대체함)는 관리자가 비즈니스용 Skype Online을 실행하는 모든 컴퓨터와 풀에 대한 로깅 및 추적을 관리할 수 있게 해 줍니다. 중앙 로깅을 사용하면 관리자가 단일 명령을 사용하여 하나 이상의 풀 및 컴퓨터에 대해 로깅을 시작, 중지 및 구성할 수 있습니다. 예를 들어 명령 하나를 사용하여 모든 주소록 서버에서 주소록 서비스 로깅을 사용하도록 설정할 수 있습니다. 이는 서버마다 개별적으로 관리해야 하는(개별적으로 시작하고 중지하는 것도 포함) OCSLogger 및 OCSTracer 도구와 다릅니다. 또한 중앙 로깅 서비스에서는 관리자가 Windows PowerShell 명령줄 인터페이스 및 [Search-CsClsLogging](search-csclslogging.md) cmdlet을 사용하여 명령에서 추적 로그를 검색하는 방법도 있습니다.

비즈니스용 Skype Online에서는 로그 파일에 기록되는 개인 식별이 가능한 정보에 액세스할 수 있는 사용자를 결정하는 데 영역이 사용됩니다. 영역은 [New-CsClsRegion](new-csclsregion.md) cmdlet을 사용하여 작성된 후 중앙 로깅 구성 설정의 컬렉션에 추가됩니다. 이러한 컬렉션 중 하나에 추가된 영역은 나중에 **Remove-CsClsRegion** cmdlet을 사용하여 제거할 수 있습니다.

사용자가 직접 만든 사용자 지정 RBAC(역할 기반 액세스 제어) 역할을 포함하여 이 cmdlet이 할당된 모든 RBAC 역할의 목록을 반환하려면 Windows PowerShell 프롬프트에서 다음 명령을 실행합니다.

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Remove-CsClsRegion"}

**Lync Server 제어판:** **Remove-CsClsRegion** cmdlet에 의해 수행되는 기능은 Lync Server 제어판에서는 사용할 수 없습니다.

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
<th>형식</th>
<th>설명</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><em>Identity</em></p></td>
<td><p>필수</p></td>
<td><p>Microsoft.Rtc.Management.Xds.XdsIdentity</p></td>
<td><p>제거할 중앙 로깅 영역의 고유 식별자입니다. 영역 ID는 영역이 만들어진 범위 뒤에 영역 이름이 붙는 형식으로 구성됩니다. 예를 들어 전역 범위에서 만들어진 US 영역을 삭제하려면 다음 구문을 사용합니다.</p>
<p>-Identity &quot;global/US&quot;</p></td>
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
<td><p><em>WhatIf</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>명령을 실제로 실행하지 않고도 명령이 실행될 경우 발생할 수 있는 현상을 설명합니다.</p></td>
</tr>
</tbody>
</table>


## 입력 형식

**Remove-CsClsRegion** cmdlet은 Microsoft.Rtc.Management.WritableConfig.Settings.CentralizedLogging.Region\#Decorated 개체의 파이프라인된 인스턴스를 허용합니다.

## 반환 형식

없음. 대신 **Remove-CsClsRegion** cmdlet은 Microsoft.Rtc.Management.WritableConfig.Settings.CentralizedLogging.Region\#Decorated 개체의 기존 인스턴스를 삭제합니다.

## 참고 항목

#### 기타 리소스

[Get-CsClsRegion](get-csclsregion.md)  
[New-CsClsRegion](new-csclsregion.md)  
[Set-CsClsRegion](set-csclsregion.md)

