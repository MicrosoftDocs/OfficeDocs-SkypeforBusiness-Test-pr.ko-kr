---
title: Get-CsNetworkInterface
TOCTitle: Get-CsNetworkInterface
ms:assetid: 06a5fedf-d87e-4469-9bd6-ad16c1f9a801
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg398121(v=OCS.15)
ms:contentKeyID: 49302695
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Get-CsNetworkInterface

 

_**마지막으로 수정된 항목:** 2015-03-09_

Lync Server 서비스 또는 서버 역할을 실행하는 컴퓨터에서 사용 중인 네트워크 인터페이스에 대한 정보를 반환합니다. 이 cmdlet은 Lync Server 2010에서 도입되었습니다.

## 구문

    Get-CsNetworkInterface [-Identity <NetworkInterfaceIdentity>] <COMMON PARAMETERS>

    Get-CsNetworkInterface [-Filter <String>] <COMMON PARAMETERS>

    COMMON PARAMETERS: [-ComputerFqdn <Fqdn>]

## 예제

## 예제 1

예제 1에서는 조직에서 사용하도록 구성된 모든 네트워크 인터페이스에 대한 정보를 반환합니다.

    Get-CsNetworkInterface

## 예제 2

예제 2에 표시된 명령은 ID가 atl-cs-001.litwareinc.com.com/Primary/1인 네트워크 인터페이스 하나에 대한 정보를 반환합니다.

    Get-CsNetworkInterface -Identity atl-cs-001.litwareinc.com/Primary/1

## 예제 3

예제 3에서는 litwareinc.com 도메인의 모든 네트워크 인터페이스에 대한 정보를 반환합니다. 이 작업을 수행하기 위해 필터 값 "\*.litwareinc.com\*"와 함께 Filter 매개 변수를 포함합니다. 이 필터 값은 Identity에 문자열 값 "litwareinc.com"이 포함된 인터페이스에 대한 데이터만 반환되도록 제한합니다.

    Get-CsNetworkInterface -Filter "*.litwareinc.com*"

## 예제 4

예제 4에서는 IP 주소 192.168.0.240에 대해 구성된 모든 네트워크 인터페이스에 대한 정보를 반환합니다. 이 작업을 수행하기 위해 먼저 매개 변수 없이 **Get-CsNetworkInterface** cmdlet을 호출합니다. 그러면 조직에서 사용하도록 구성된 모든 네트워크 인터페이스 컬렉션이 반환됩니다. 이 컬렉션은 IPAddress 속성이 192.168.0.240과 같은 인터페이스만 선택하는 **Where-Object** cmdlet에 파이프됩니다.

    Get-CsNetworkInterface | Where-Object {$_.IPAddress -eq "192.168.0.240"}

## 예제 5

예제 5에 표시된 명령은 예제 4에 표시된 명령의 변형입니다. 그러나 이 경우에는 서브넷 "192.168.0.\*"에 대해 구성된 모든 네트워크 인터페이스에 대한 정보가 반환됩니다. 이 작업을 수행하기 위해 모든 네트워크 인터페이스 컬렉션을 검색하고 해당 컬렉션을 **Where-Object** cmdlet에 파이프한 다음 IPAddress가 문자열 값 "192.168.0."으로 시작하는 인터페이스만 선택합니다.

    Get-CsNetworkInterface | Where-Object {$_.IPAddress -like "192.168.0.*"}

## 예제 6

예제 6에서는 외부 액세스에 대해 구성된 모든 네트워크 인터페이스를 반환합니다. 이 작업을 수행하기 위해 먼저 매개 변수 없이 **Get-CsNetworkInterface** cmdlet을 호출합니다. 그러면 현재 사용 중인 모든 네트워크 인터페이스 컬렉션이 반환됩니다. 이 컬렉션은 Interface 속성이 External과 같은 항목만 선택하는 **Where-Object** cmdlet에 파이프됩니다.

    Get-CsNetworkInterface | Where-Object {$_.Interface -eq "External"}

## 자세한 정보

한 컴퓨터에서 다른 컴퓨터로 정보를 전송하려면 컴퓨터에 네트워크 인터페이스, 즉 컴퓨터와 네트워크 간의 연결이 필요합니다. Lync Server 서비스 또는 서버 역할을 실행하는 컴퓨터에는 네트워크 인터페이스가 한 개 이상 있어야 합니다. 그렇지 않으면 다른 컴퓨터와 통신할 수 없습니다. 그러나 이러한 컴퓨터에 네트워크 인터페이스가 여러 개 있을 수도 있습니다. 예를 들어 에지 서버에 내부 네트워크 연결용 인터페이스 한 개와 인터넷 연결용 인터페이스 한 개가 있을 수 있습니다. **Get-CsNetworkInterface** cmdlet을 사용하면 관리자가 Lync Server 서비스 또는 서버 역할을 실행하는 컴퓨터에서 현재 사용 중인 네트워크 인터페이스에 대한 정보를 가져올 수 있습니다.

이 cmdlet을 실행할 수 있는 사용자: 기본적으로 RTCUniversalUserAdmins 및 RTCUniversalServerAdmins 그룹의 구성원은 **Get-CsNetworkInterface** cmdlet을 로컬로 실행할 수 있습니다. 사용자가 직접 만든 사용자 지정 RBAC(역할 기반 액세스 제어) 역할을 포함하여 이 cmdlet이 할당된 모든 RBAC 역할의 목록을 반환하려면 Windows PowerShell 프롬프트에서 다음 명령을 실행합니다.

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Get-CsNetworkInterface"}

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
<td><p><em>ComputerFqdn</em></p></td>
<td><p>선택</p></td>
<td><p>Microsoft.Rtc.Management.Deploy.Fqdn</p></td>
<td><p>네트워크 인터페이스 정보를 반환할 컴퓨터의 FQDN입니다. 예를 들어 atl-cs-001.litwareinc.com 컴퓨터에 대한 네트워크 인터페이스 정보만 반환하려면 -ComputerFqdn atl-cs-001.litwareinc.com 구문을 사용합니다.</p></td>
</tr>
<tr class="even">
<td><p><em>Filter</em></p></td>
<td><p>선택</p></td>
<td><p>System.String</p></td>
<td><p>반환할 네트워크 인터페이스를 지정할 때 와일드카드를 사용할 수 있습니다. 예를 들어 -Filter &quot;*/Primary/*&quot; 구문은 Lync Server 서비스 또는 서버 역할을 실행하는 모든 컴퓨터에서 사용된 기본 네트워크 인터페이스에 대한 정보를 반환합니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>Identity</em></p></td>
<td><p>선택</p></td>
<td><p>Microsoft.Rtc.Management.Xds.NetworkInterfaceIdentity</p></td>
<td><p>반환할 네트워크 인터페이스의 고유 식별자입니다. 네트워크 인터페이스 ID는 다음 세 부분으로 구성됩니다.</p>
<p>컴퓨터 자체의 FQDN(정규화된 도메인 이름)(예: atl-cs-001.litwareinc.com)입니다.</p>
<p>네트워크 인터페이스 &quot;쪽&quot;(기본, 내부, 외부, PSTN)입니다. 이 쪽은 포트가 사용되는 트래픽 유형을 나타냅니다.</p>
<p>특정 쪽의 네트워크 인터페이스 번호입니다.</p>
<p>예: -Identity &quot;atl-cs-001.litwareinc.com/Primary/1&quot;</p>
<p>Identity, ComputerFqdn 및 Filter 매개 변수를 개별적으로 사용해야 합니다. 예를 들어 ComputerFqdn 및 Identity를 둘 다 사용하는 명령은 실행할 수 없습니다. 또한 ID를 지정할 때는 와일드카드 문자를 사용할 수 없습니다. 와일드카드를 사용하려면 Filter 매개 변수를 사용합니다.</p>
<p>Identity, ComputerFqdn 또는 Filter 매개 변수를 아무 것도 사용하지 않은 경우 <strong>Get-CsNetworkInterface</strong> cmdlet은 Lync Server 서비스 또는 서버 역할을 실행하는 컴퓨터에서 현재 사용 중인 모든 네트워크 인터페이스에 대한 정보를 반환합니다.</p></td>
</tr>
</tbody>
</table>


## 입력 형식

없음. **Get-CsNetworkInterface** cmdlet은 파이프라인된 입력을 허용하지 않습니다.

## 반환 형식

**Get-CsNetworkInterface** cmdlet은 Microsoft.Rtc.Management.Xds.DisplayNetworkInterface 개체의 인스턴스를 반환합니다.

## 참고 항목

#### 기타 리소스

[Get-CsComputer](get-cscomputer.md)

