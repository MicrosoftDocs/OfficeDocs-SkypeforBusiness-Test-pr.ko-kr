---
title: Get-CsClsRegion
TOCTitle: Get-CsClsRegion
ms:assetid: 4f38e966-8e92-4549-8124-097c236c0165
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/JJ204879(v=OCS.15)
ms:contentKeyID: 49303601
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Get-CsClsRegion

 

_**마지막으로 수정된 항목:** 2015-03-09_

조직에서 사용 중인 중앙 로깅 구성 영역에 대한 정보를 반환합니다. 관리자는 중앙 로깅을 통해 여러 컴퓨터에서 이벤트 추적을 동시에 사용하거나 사용하지 않도록 설정할 수 있습니다. 중앙 로깅 영역은 비즈니스용 Skype Online용입니다.

이 cmdlet은 Lync Server 2013에서 도입되었습니다.

## 구문

    Get-CsClsRegion [-Identity <XdsIdentity>] <COMMON PARAMETERS>

    Get-CsClsRegion [-Filter <String>] <COMMON PARAMETERS>

    COMMON PARAMETERS: [-LocalStore <SwitchParameter>]

## 예제

## 예제 1

예제 1에 표시된 명령은 조직에서 사용하도록 구성된 모든 중앙 로깅 영역에 대한 정보를 반환합니다.

    Get-CsClsRegion

## 예제 2

예제 2에서는 ID가 global/US인 중앙 로깅 영역에 대한 정보만 반환합니다.

    Get-CsClsRegion -Identity "global/US"

## 예제 3

예제 3에서는 전역 범위에서 구성된 모든 중앙 로깅 영역에 대한 정보를 반환합니다. 이 작업을 수행하기 위해 Filter 매개 변수를 포함하여 **Get-CsClsRegion** cmdlet을 호출합니다. 필터 값 "global/\*"는 반환되는 데이터를 전역 범위에서 구성된 영역으로 제한합니다.

    Get-CsClsRegion -Filter "global/*"

## 예제 4

예제 4에 표시된 명령은 Europe 영역의 액세스를 허용하는 모든 중앙 로깅 영역에 대한 정보를 반환합니다. 이 작업을 수행하기 위해 이 명령은 먼저 **Get-CsClsRegion** cmdlet을 사용하여 현재 사용 중인 모든 중앙 로깅 영역의 컬렉션을 반환합니다. 이 컬렉션은 OtherRegionAccess 속성에 문자열 값 "Europe"이 포함된 영역만 선택하는 **Where-Object** cmdlet에 파이프됩니다.

    Get-CsClsRegion | Where-Object {$_.OtherRegionAccess -match "Europe"}

## 자세한 정보

중앙 로깅 서비스( Microsoft Lync Server 2010에서 사용하는 OCSLogger 및 OCSTracer 도구를 대체함)는 관리자가 Lync Server 2013을 실행하는 모든 컴퓨터와 풀에 대한 로깅 및 추적을 관리할 수 있게 해 줍니다. 중앙 로깅을 사용하면 관리자가 단일 명령을 사용하여 하나 이상의 풀 및 컴퓨터에 대해 로깅을 시작, 중지 및 구성할 수 있습니다. 예를 들어 명령 하나를 사용하여 모든 주소록 서버에서 주소록 서비스 로깅을 사용하도록 설정할 수 있습니다. 이는 서버마다 개별적으로 관리해야 하는(개별적으로 시작하고 중지하는 것도 포함) OCSLogger 및 OCSTracer 도구와 다릅니다. 또한 중앙 로깅 서비스에서는 관리자가 Windows PowerShell 명령줄 인터페이스 및 [Search-CsClsLogging](search-csclslogging.md) cmdlet을 사용하여 명령에서 추적 로그를 검색하는 방법도 있습니다.

Office 365 버전 Lync Server에서는 로그 파일에 기록되는 개인 식별이 가능한 정보에 액세스할 수 있는 사용자를 결정하는 데 영역이 사용됩니다. 영역은 [New-CsClsRegion](new-csclsregion.md) cmdlet을 사용하여 작성된 다음 중앙 로깅 구성 설정의 컬렉션에 추가됩니다. **Get-CsClsRegion** cmdlet을 사용하여 중앙 로깅 영역에 대한 정보를 반환할 수 있습니다.

사용자가 직접 만든 사용자 지정 RBAC(역할 기반 액세스 제어) 역할을 포함하여 이 cmdlet이 할당된 모든 RBAC 역할의 목록을 반환하려면 Windows PowerShell 프롬프트에서 다음 명령을 실행합니다.

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Get-CsClsRegion"}

**Lync Server 제어판:** **Get-CsClsRegion** cmdlet에 의해 수행되는 기능은 Lync Server 제어판에서는 사용할 수 없습니다.

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
<td><p><em>Filter</em></p></td>
<td><p>선택</p></td>
<td><p>System.String</p></td>
<td><p>하나 이상의 중앙 로깅 영역을 반환하기 위해 와일드카드 문자를 사용할 수 있습니다. 예를 들어 전역 범위에서 구성된 모든 설정 컬렉션을 반환하려면 다음 구문을 사용합니다.</p>
<p>-Filter &quot;global/*&quot;</p></td>
</tr>
<tr class="even">
<td><p><em>Identity</em></p></td>
<td><p>선택</p></td>
<td><p>Microsoft.Rtc.Management.Xds.XdsIdentity</p></td>
<td><p>반환할 중앙 로깅 영역의 고유 식별자입니다. 영역 ID는 영역이 작성된 범위 뒤에 영역 이름이 붙는 형식으로 구성됩니다. 예를 들어 전역 범위에서 작성된 US 영역을 반환하려면 다음 구문을 사용합니다.</p>
<p>-Identity &quot;global/US&quot;</p>
<p>이 매개 변수를 지정하지 않으면 <strong>Get-CsClsRegion</strong> cmdlet은 모든 중앙 로깅 영역에 대한 정보를 반환합니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>LocalStore</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>중앙 관리 저장소 자체가 아니라 중앙 관리 저장소의 로컬 복제본에서 중앙 로깅 구성 데이터를 검색합니다.</p></td>
</tr>
</tbody>
</table>


## 입력 형식

없음. **Get-CsClsRegion** cmdlet은 파이프라인된 입력을 허용하지 않습니다.

## 반환 형식

**Get-CsClsRegion** cmdlet은 Microsoft.Rtc.Management.WritableConfig.Settings.CentralizedLogging.Region\#Decorated 개체의 인스턴스를 반환합니다.

## 참고 항목

#### 기타 리소스

[New-CsClsRegion](new-csclsregion.md)  
[Remove-CsClsRegion](remove-csclsregion.md)  
[Set-CsClsRegion](set-csclsregion.md)

