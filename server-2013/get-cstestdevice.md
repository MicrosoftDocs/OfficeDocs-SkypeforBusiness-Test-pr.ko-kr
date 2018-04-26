---
title: Get-CsTestDevice
TOCTitle: Get-CsTestDevice
ms:assetid: 4c88d448-4130-40de-b7e9-7389922322f4
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg398304(v=OCS.15)
ms:contentKeyID: 49303565
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Get-CsTestDevice

 

_**마지막으로 수정된 항목:** 2015-03-09_

조직에서 사용하도록 구성된 장치 업데이트 관리 테스트 장치에 대한 정보를 검색합니다. 테스트 장치를 통해 관리자는 조직 내 모든 장치에 펌웨어 업데이트를 배포하기 전에 업데이트 내용을 테스트할 수 있습니다. 이 cmdlet은 Lync Server 2010에서 도입되었습니다.

## 구문

    Get-CsTestDevice [-Identity <XdsIdentity>] <COMMON PARAMETERS>

    Get-CsTestDevice [-Filter <String>] <COMMON PARAMETERS>

    COMMON PARAMETERS: [-LocalStore <SwitchParameter>]

## 예제

## 예제 1

예제 1에서는 조직의 모든 테스트 장치를 반환합니다. 추가 매개 변수 없이 **Get-CsTestDevice** cmdlet을 호출하면 현재 사용 중인 모든 테스트 장치가 반환됩니다.

    Get-CsTestDevice

## 예제 2

이 예제에서는 Redmond 사이트에 할당된 UCPhone이라는 테스트 장치를 반환합니다.

    Get-CsTestDevice -Identity site:Redmond/UCPhone

## 예제 3

예제 3에서는 Redmond 사이트에 대해 구성된 모든 테스트 장치가 반환됩니다.

``` 
Get-CsTestDevice -Identity site:Redmond  
```

## 예제 4

예제 4에서는 사이트 범위에서 구성된 모든 테스트 장치를 반환합니다. 이 작업을 수행하기 위해 Filter 매개 변수를 사용합니다. 필터 값 "site:\*"는 ID가 문자열 값 "site:"으로 시작하는 테스트 장치에 대한 데이터만 반환되도록 제한합니다.

    Get-CsTestDevice -Filter site:*

## 자세한 정보

관리자는 특정 Lync Phone Edition 호환 전화 또는 기타 장치를 테스트 장치로 식별하여 펌웨어 업데이트를 조직의 모든 관련 장치에 적용하기 전에 이러한 업데이트를 확인 및 승인할 수 있습니다. 장치 업데이트 규칙을 Lync Server로 가져올 때 이러한 규칙은 "대기 중"으로 표시됩니다. 이는 대상 장치에서 이러한 규칙에 해당하는 업데이트를 자동으로 다운로드 및 설치하지 않음을 의미합니다.

대신 관련 테스트 장치가 보류 중인 이 규칙을 다운로드 및 설치합니다. 테스트 장치의 용도가 바로 이것입니다. 즉, 새 장치 업데이트 규칙은 테스트 장치에 자동으로 적용되므로 관리자는 펌웨어 업데이트가 예상대로 작동하는지 여부를 확인할 수 있습니다. 예상대로 작동하는 경우 관리자는 규칙을 승인된 것으로 표시할 수 있습니다. 그런 다음 조직 내 모든 관련 장치가 승인된 규칙을 다운로드 및 설치합니다.

테스트 장치는 전역 범위 또는 사이트 범위에 할당할 수 있습니다. **Get-CsTestDevice** cmdlet을 사용하여 조직에서 사용하도록 현재 구성된 테스트 장치에 대한 정보를 검색할 수 있습니다.

이 cmdlet을 실행할 수 있는 사용자: 기본적으로 RTCUniversalUserAdmins 및 RTCUniversalServerAdmins 그룹의 구성원은 **Get-CsTestDevice** cmdlet을 로컬로 실행할 수 있습니다. 사용자가 직접 만든 사용자 지정 RBAC(역할 기반 액세스 제어) 역할을 포함하여 이 cmdlet이 할당된 모든 RBAC 역할의 목록을 반환하려면 Windows PowerShell 프롬프트에서 다음 명령을 실행합니다.

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Get-CsTestDevice"}

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
<td><p><em>Filter</em></p></td>
<td><p>선택</p></td>
<td><p>System.String</p></td>
<td><p>반환할 테스트 장치를 지정할 때 와일드카드 문자를 사용할 수 있습니다. 예를 들어 사이트 범위에서 구성된 모든 테스트 장치 컬렉션을 반환하려면 -Filter &quot;site:*&quot; 구문을 사용합니다. Identity에 &quot;EMEA&quot;라는 용어가 포함된 모든 장치를 반환하려면 -Filter &quot;*EMEA*&quot; 구문을 사용합니다. Filter는 테스트 장치 컬렉션의 ID에만 적용됩니다. 다른 컬렉션 속성은 필터링할 수 없습니다.</p></td>
</tr>
<tr class="even">
<td><p><em>Identity</em></p></td>
<td><p>선택</p></td>
<td><p>Microsoft.Rtc.Management.Xds.XdsIdentity</p></td>
<td><p>반환할 테스트 장치의 ID를 나타냅니다. 전역 컬렉션에 저장된 UCPhone이라는 개별 장치를 나타내려면 -Identity global/UCPhone 구문을 사용합니다. 사이트 컬렉션에 있는 장치를 나타내려면 -Identity site:Redmond/UCPhone과 유사한 구문을 사용합니다. 전체 컬렉션을 나타내려면 장치 이름을 생략합니다. 예를 들어 -Identity site:Redmond 구문은 Redmond 사이트에 대해 구성된 모든 테스트 장치를 반환합니다.</p>
<p>ID를 지정할 때는 와일드카드를 사용할 수 없습니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>LocalStore</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>중앙 관리 저장소 자체가 아니라 중앙 관리 저장소의 로컬 복제본에서 테스트 장치 데이터를 검색합니다.</p></td>
</tr>
</tbody>
</table>


## 입력 형식

없음. **Get-CsTestDevice** cmdlet은 파이프라인된 입력을 허용하지 않습니다.

## 반환 형식

**Get-CsTestDevice** cmdlet은 Microsoft.Rtc.Management.WritableConfig.Settings.DeviceUpdate.TestDevice 개체의 인스턴스를 하나 이상 반환합니다.

## 참고 항목

#### 기타 리소스

[New-CsTestDevice](new-cstestdevice.md)  
[Remove-CsTestDevice](remove-cstestdevice.md)  
[Set-CsTestDevice](set-cstestdevice.md)

