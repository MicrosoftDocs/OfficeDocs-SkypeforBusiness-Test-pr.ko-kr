---
title: Get-CsTrunk
TOCTitle: Get-CsTrunk
ms:assetid: c49407f2-2e03-4b8b-b51b-75b12ef87fd1
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/JJ205244(v=OCS.15)
ms:contentKeyID: 49304967
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Get-CsTrunk

 

_**마지막으로 수정된 항목:** 2015-03-09_

조직에서 사용되는 SIP 트렁크에 대한 정보를 반환합니다. SIP 트렁크는 Lync Server 2013 VoIP 전화 네트워크를 PSTN(공중 전화망)에 연결합니다. 이 cmdlet은 Lync Server 2013에서 도입되었습니다.

## 구문

    Get-CsTrunk [-Identity <XdsGlobalRelativeIdentity>] <COMMON PARAMETERS>

    Get-CsTrunk [-Filter <String>] <COMMON PARAMETERS>

    COMMON PARAMETERS: [-PoolFqdn <String>]

## 예제

## 예제 1

예제 1에 표시된 명령은 조직에서 사용하도록 구성된 모든 SIP 트렁크에 대한 정보를 반환합니다.

    Get-CsTrunk

## 예제 2

예제 2에서는 단일 SIP 트렁크, 즉 ID가 PstnGateway:192.168.0.240인 트렁크에 대한 정보를 반환합니다.

    Get-CsTrunk -Identity "PstnGateway:192.168.0.240"

## 예제 3

예제 3에서는 atl-cs-001.litwareinc.com 풀에 있는 모든 SIP 트렁크에 대한 정보를 반환합니다.

    Get-CsTrunk -PoolFqdn "atl-cs-001.litwareinc.com"

## 예제 4

예제 4에서는 라우팅 가능한 모든 SIP 트렁크에 대한 정보를 반환합니다. 이 작업을 수행하기 위해 명령은 먼저 매개 변수 없이 **Get-CsTrunk** cmdlet을 호출하여 사용 가능한 모든 SIP 트렁크의 컬렉션을 반환합니다. 이 컬렉션은 **Where-Object** cmdlet에 파이프되며, 해당 cmdlet은 Routable 속성이 True($True)와 같은(-eq) 트렁크만 선택합니다.

    Get-CsTrunk | Where-Object {$_.Routable -eq $True}

## 자세한 정보

Microsoft Lync Server 2010에서 트렁크는 아웃바운드 통화를 중재 서버에서 PSTN 게이트웨이로 라우팅하는 데 사용됩니다. 각 게이트웨이에서는 트렁크를 하나만 사용할 수 있으므로 관리자가 아웃바운드 통화에 대해 복원 기능을 제공하기가 어렵습니다. 그러나 트렁크와 PSTN 게이트웨이는 기본적으로 동일하기 때문에 다음 명령을 실행하면 모든 트렁크에 대한 정보를 검색할 수 있습니다.

Get-CsService -PstnGateway

Lync Server 2013에서는 PSTN 게이트웨이 하나에 여러 트렁크를 할당할 수 있습니다. 즉, 게이트웨이와 트렁크가 더 이상 동일하지 않습니다. 따라서 Lync Server 2013에서는 **Get-CsService** cmdlet을 사용하여 개별 트렁크에 대한 상세 정보를 검색할 수 없습니다. 대신 새롭게 제공되는 **Get-CsTrunk** cmdlet을 통해 개별 트렁크에 대한 상세 정보를 반환합니다.

Windows PowerShell 명령줄 인터페이스에서는 트렁크 정보가 읽기 전용입니다. 따라서 PowerShell을 사용하여 트렁크를 작성, 삭제 또는 수정할 수는 없습니다. 이러한 작업은 Lync Server 토폴로지 작성기를 통해서만 수행할 수 있습니다.

사용자가 직접 만든 사용자 지정 RBAC(역할 기반 액세스 제어) 역할을 포함하여 이 cmdlet이 할당된 모든 RBAC 역할의 목록을 반환하려면 Windows PowerShell 프롬프트에서 다음 명령을 실행합니다.

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Get-CsTrunk"}

**Lync Server 제어판:** **Get-CsTrunk** cmdlet에 의해 수행되는 기능은 Lync Server 제어판에서는 사용할 수 없습니다.

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
<td><p>SIP 트렁크 하나 또는 SIP 트렁크 컬렉션을 반환하기 위해 와일드카드 문자를 사용할 수 있습니다. 예를 들어 PSTN 게이트웨이 서비스의 일부분으로 구성된 모든 SIP 트렁크의 컬렉션을 반환하려면 다음 구문을 사용합니다.</p>
<p>-Filter &quot;PstnGateway:*&quot;</p></td>
</tr>
<tr class="even">
<td><p><em>Identity</em></p></td>
<td><p>선택</p></td>
<td><p>Microsoft.Rtc.Management.Xds.XdsGlobalRelativeIdentity</p></td>
<td><p>반환할 SIP 트렁크의 고유 식별자입니다. 예를 들면 다음과 같습니다.</p>
<p>–Identity &quot;PstnGateway:192.168.0.240&quot;</p>
<p>ID를 지정할 때는 와일드카드를 사용할 수 없습니다. 와일드카드를 사용해야 하는 경우 대신 Filter 매개 변수를 포함합니다.</p>
<p>이 매개 변수를 지정하지 않으면 <strong>Get-CsTrunk</strong> cmdlet이 조직에서 사용 중인 모든 SIP 트렁크 컬렉션을 반환합니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>PoolFqdn</em></p></td>
<td><p>선택</p></td>
<td><p>System.String</p></td>
<td><p>토폴로지에 정의된 트렁크 또는 PSTN 게이트웨이의 정규화된 도메인 이름입니다. 예를 들면 다음과 같습니다.</p>
<p>-PoolFqdn &quot;atl-trunk-001.litwareinc.com&quot;</p></td>
</tr>
</tbody>
</table>


## 입력 형식

없음. **Get-CsTrunk** cmdlet은 파이프라인된 입력을 허용하지 않습니다.

## 반환 형식

**Get-CsTrunk** cmdlet은 Microsoft.Rtc.Management.Xds.DisplayPstnGateway\#Decorated 개체의 인스턴스를 반환합니다.

## 참고 항목

#### 기타 리소스

[Get-CsTrunkConfiguration](get-cstrunkconfiguration.md)

