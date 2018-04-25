---
title: Get-CsSite
TOCTitle: Get-CsSite
ms:assetid: 0e5fd5b8-17aa-433d-9915-3b88281fa2c2
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg398185(v=OCS.15)
ms:contentKeyID: 49302809
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Get-CsSite

 

_**마지막으로 수정된 항목:** 2015-03-09_

Lync Server 인프라의 일부로 만들어진 사이트에 대한 정보를 반환합니다. 사이트는 Lync Server 풀의 컬렉션을 나타내며 일반적으로 지리적인 지역에 걸쳐 설계됩니다. Lync Server에는 데이터 센터 사이트와 원격 사이트(분기 사이트)의 두 가지 사이트가 있습니다. 이 cmdlet은 Lync Server 2010에서 도입되었습니다.

## 구문

    Get-CsSite [-Identity <XdsGlobalRelativeIdentity>] <COMMON PARAMETERS>

    Get-CsSite [-Filter <String>] <COMMON PARAMETERS>

    COMMON PARAMETERS:

## 예제

## 예제 1

예제 1에서는 모든 Lync Server 사이트에 대한 정보를 검색합니다.

    Get-CsSite

## 예제 2

예제 2에서는 ID가 Redmond인 단일 사이트에 대한 정보가 반환됩니다.

    Get-CsSite -Identity "Redmond"

## 예제 3

예제 3에 표시된 명령은 중앙 사이트에 대한 정보를 반환합니다. 이 작업을 수행하기 위해 이 명령은 먼저 **Get-CsSite** cmdlet을 호출하여 조직에서 사용하도록 구성된 모든 사이트 컬렉션을 반환합니다. 이 컬렉션은 SiteType 속성이 CentralSite와 같은 사이트 하나를 선택하는 **Where-Object** cmdlet에 파이프됩니다.

    Get-CsSite | Where-Object {$_.SiteType -eq "CentralSite"}

## 예제 4

예제 4에서는 Redmond 사이트에 있는 풀 목록을 표시합니다. 이 작업을 수행하기 위해 이 명령은 먼저 Redmond 사이트에 대한 전체 정보를 검색한 다음 해당 데이터를 **Select-Object** cmdlet에 파이프합니다. 그러면 **Select-Object** cmdlet에서 ExpandProperty 매개 변수를 사용하여 Pools 속성 값을 "확장"합니다. 속성 값을 확장하면 해당 속성에 저장된 모든 값이 읽기 쉬운 형식으로 화면에 표시됩니다.

    Get-CsSite -Identity "Redmond" | Select-Object -ExpandProperty Pools

## 자세한 정보

Lync Server 2010에는 Lync Server 토폴로지의 새로운 개념인 사이트라는 새 개념이 추가되었습니다. 사이트는 일반적으로 지리 및 네트워크 대역폭에 따라 조직된 Lync Server 풀 및 서버의 컬렉션이며 Active Directory 사이트 또는 Microsoft Exchange Server 사이트와 혼동해서는 안 됩니다. 예를 들어 Redmond의 모든 컴퓨터가 고속, 저지연 연결을 지원하는 동일한 로컬 영역 네트워크에 있는 경우 이러한 컴퓨터를 통칭하는 Redmond 사이트를 지정할 수 있습니다. Dublin의 컴퓨터가 해당 LAN(Local Area Network)에 있고 대기 시간이 짧은 고속 연결을 공유하는 경우 별도의 Dublin 사이트도 만들 수 있습니다. 사이트는 Lync Server 관리에서 중요한 역할을 합니다. 대부분의 정책 및 설정을 사이트 범위에 구성할 수 있으며, 이렇게 하면 Redmond의 사용자에게 특정 다이얼 플랜 집합을 적용하고 Dublin의 사용자에게는 완전히 다른 다이얼 플랜 집합을 적용하는 등의 작업을 쉽게 수행할 수 있습니다.

**Get-CsSite** cmdlet을 사용하면 이러한 각 사이트를 구성하는 풀에 대한 정보를 비롯하여 조직 내 모든 사이트에 대한 정보를 반환할 수 있습니다.

이 cmdlet을 실행할 수 있는 사용자: 기본적으로 RTCUniversalUserAdmins, RTCUniversalServerAdmins 및 RTCUniversalReadOnlyAdmins 그룹의 구성원은 **Get-CsSite** cmdlet을 로컬로 실행할 수 있습니다. 사용자가 직접 만든 사용자 지정 RBAC(역할 기반 액세스 제어) 역할을 포함하여 이 cmdlet이 할당된 모든 RBAC 역할의 목록을 반환하려면 Windows PowerShell 프롬프트에서 다음 명령을 실행합니다.

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Get-CsSite"}

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
<td><p>반환할 사이트의 ID를 지정할 때 와일드카드를 사용할 수 있습니다. 예를 들어 -Filter &quot;*Dublin*&quot; 구문은 Identity에 문자열 값 &quot;Dublin&quot;이 포함된 모든 풀을 반환합니다.</p>
<p>Filter 매개 변수와 Identity 매개 변수를 같은 명령에 함께 사용할 수 없습니다.</p>
<p></p></td>
</tr>
<tr class="even">
<td><p><em>Identity</em></p></td>
<td><p>선택</p></td>
<td><p>Microsoft.Rtc.Management.Xds.XdsGlobalRelativeIdentity</p></td>
<td><p>반환할 사이트의 이름입니다. 사이트 이름만 지정하면 됩니다(예: -Identity &quot;Redmond&quot;). ID를 지정할 때 &quot;site:Redmond&quot;와 같은 형식을 사용하지 마십시오.</p></td>
</tr>
</tbody>
</table>


## 입력 형식

없음. **Get-CsSite** cmdlet은 파이프라인된 입력을 허용하지 않습니다.

## 반환 형식

**Get-CsSite** cmdlet은 Microsoft.Rtc.Management.Deploy.Internal.Site+CentralSite 개체의 인스턴스를 반환합니다.

## 참고 항목

#### 기타 리소스

[Set-CsSite](set-cssite.md)

