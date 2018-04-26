---
title: New-CsClsRegion
TOCTitle: New-CsClsRegion
ms:assetid: 09396d6e-e7ec-43b8-9f5b-d9cac30348f6
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/JJ204658(v=OCS.15)
ms:contentKeyID: 49302733
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# New-CsClsRegion

 

_**마지막으로 수정된 항목:** 2015-03-09_

새 중앙 로깅 구성 영역을 만듭니다. 관리자는 중앙 로깅을 통해 여러 컴퓨터에서 이벤트 추적을 동시에 사용하거나 사용하지 않도록 설정할 수 있습니다. 중앙 로깅 영역은 비즈니스용 Skype Online용입니다.

이 cmdlet은 Lync Server 2013에서 도입되었습니다.

## 구문

    New-CsClsRegion -Name <String> -Parent <String> <COMMON PARAMETERS>

    New-CsClsRegion -Identity <XdsIdentity> <COMMON PARAMETERS>

    COMMON PARAMETERS: -OtherRegionAccess <String> -SecurityGroupSuffix <String> [-Confirm [<SwitchParameter>]] [-Force <SwitchParameter>] [-InMemory <SwitchParameter>] [-Sites <String>] [-WhatIf [<SwitchParameter>]]

## 예제

## 예제 1

예제에 표시된 명령은 Europe이라는 새 전역 영역을 만듭니다. 새 영역은 보안 그룹 접미사 EMEA를 사용하며 global/US 영역의 액세스도 허용합니다.

    New-CsClsRegion -Identity "global/Europe" -SecurityGroupSuffix "EMEA" -OtherRegionAccess "global/US"

## 자세한 정보

중앙 로깅 서비스( Microsoft Lync Server 2010에서 사용하는 OCSLogger 및 OCSTracer 도구를 대체함)는 관리자가 Lync Server 2013을 실행하는 모든 컴퓨터와 풀에 대한 로깅 및 추적을 관리할 수 있게 해 줍니다. 중앙 로깅을 사용하면 관리자가 단일 명령을 사용하여 하나 이상의 풀 및 컴퓨터에 대해 로깅을 시작, 중지 및 구성할 수 있습니다. 예를 들어 명령 하나를 사용하여 모든 주소록 서버에서 주소록 서비스 로깅을 사용하도록 설정할 수 있습니다. 이는 서버마다 개별적으로 관리해야 하는(개별적으로 시작하고 중지하는 것도 포함) OCSLogger 및 OCSTracer 도구와 다릅니다. 또한 중앙 로깅 서비스에서는 관리자가 Windows PowerShell 명령줄 인터페이스 및 [Search-CsClsLogging](search-csclslogging.md) cmdlet을 사용하여 명령에서 추적 로그를 검색하는 방법도 있습니다.

Office 365 버전 Lync Server에서는 로그 파일에 기록되는 개인 식별이 가능한 정보에 액세스할 수 있는 사용자를 결정하는 데 영역이 사용됩니다. 영역은 [New-CsClsRegion](new-csclsregion.md) cmdlet을 사용하여 작성된 다음 중앙 로깅 구성 설정의 컬렉션에 추가됩니다.

사용자가 직접 만든 사용자 지정 RBAC(역할 기반 액세스 제어) 역할을 포함하여 이 cmdlet이 할당된 모든 RBAC 역할의 목록을 반환하려면 Windows PowerShell 프롬프트에서 다음 명령을 실행합니다.

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "New-CsClsRegion"}

**Lync Server 제어판:** **New-CsClsRegion** cmdlet에 의해 수행되는 기능은 Lync Server 제어판에서는 사용할 수 없습니다.

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
<td><p>새 영역의 고유 식별자입니다. 영역 ID는 영역을 만들 중앙 로깅 구성 범위와 고유 영역 이름으로 구성됩니다. 예를 들어 Redmond라는 전역 영역을 만들려면 다음 구문을 사용합니다.</p>
<p>-Identity &quot;global/Redmond&quot;</p>
<p>Identity 매개 변수를 사용하는 경우에는 Name 매개 변수 또는 Parent 매개 변수를 같은 명령에서 사용할 수 없습니다.</p></td>
</tr>
<tr class="even">
<td><p><em>Name</em></p></td>
<td><p>필수</p></td>
<td><p>System.String</p></td>
<td><p>새 영역의 고유한 이름입니다. 예를 들면 다음과 같습니다.</p>
<p>-Name &quot;Redmond&quot;</p>
<p>Name 매개 변수를 사용하는 경우 Parent 매개 변수도 사용해야 합니다. 그러나 Name 및 Parent 매개 변수와 같은 명령에서 Identity 매개 변수를 사용해서는 안 됩니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>OtherRegionAccess</em></p></td>
<td><p>필수</p></td>
<td><p>System.String</p></td>
<td><p>이 영역에 대해 권한이 부여된 사용자가 액세스할 수 있는 추가 영역의 이름입니다.</p></td>
</tr>
<tr class="even">
<td><p><em>Parent</em></p></td>
<td><p>필수</p></td>
<td><p>System.String</p></td>
<td><p>새 영역을 배치할 중앙 로깅 구성 설정의 범위입니다. 예를 들어 전역 설정에 새 영역을 추가하려면 다음 구문을 사용합니다.</p>
<p>-Parent &quot;global&quot;</p>
<p>다음 명령을 사용하면 모든 중앙 로깅 상위 항목에 대해 ID를 반환할 수 있습니다.</p>
<p>Get-CsCentralizedLoggingConfiguration | Select-Object Identity</p>
<p>Name 매개 변수를 사용하는 경우 Parent 매개 변수도 사용해야 합니다. 그러나 Name 및 Parent 매개 변수와 같은 명령에서 Identity 매개 변수를 사용해서는 안 됩니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>SecurityGroupSuffix</em></p></td>
<td><p>필수</p></td>
<td><p>System.String</p></td>
<td><p>이 영역에 대해 권한을 부여할 보안 그룹의 이름 끝에 추가할 접미사입니다.</p></td>
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
<td><p><em>Sites</em></p></td>
<td><p>선택</p></td>
<td><p>System.String</p></td>
<td><p>이 지역 내에 포함된 사이트로서 토폴로지 문서의 SideId 특성 값에 해당합니다.</p></td>
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

없음. New-CsClsRegion cmdlet은 파이프라인된 입력을 허용하지 않습니다.

## 반환 형식

New-CsClsRegion cmdlet은 Microsoft.Rtc.Management.WritableConfig.Settings.CentralizedLogging.Region\#Decorated 개체의 새 인스턴스를 만듭니다.

## 참고 항목

#### 기타 리소스

[Get-CsClsRegion](get-csclsregion.md)  
[Remove-CsClsRegion](remove-csclsregion.md)  
[Set-CsClsRegion](set-csclsregion.md)

