---
title: 'Lync Server 2013: 토폴로지 선택'
TOCTitle: 토폴로지 선택
ms:assetid: 23f2aeb6-fed9-4349-8fba-dcbf18ee4b04
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg425716(v=OCS.15)
ms:contentKeyID: 49303065
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Lync Server 2013에서 토폴로지 선택

 

_**마지막으로 수정된 항목:** 2015-03-09_

토폴로지를 선택한 경우 다음과 같은 지원되는 토폴로지 옵션 중 하나를 사용할 수 있습니다.


> [!NOTE]
> 별도의 언급이 없는 경우 Microsoft Lync Server 2010을 사용해 본 적이 있다면 여기서 제공되는 지침도 크게 다르지 않습니다.



  - [Lync Server 2013의 개인 IP 주소 및 NAT 사용 단일 통합 에지](lync-server-2013-single-consolidated-edge-with-private-ip-addresses-and-nat.md)

  - [Lync Server 2013의 공용 IP 주소의 단일 통합 에지](lync-server-2013-single-consolidated-edge-with-public-ip-addresses.md)

  - [Lync Server 2013의 조정된 통합 에지, NAT 사용 개인 IP 주소의 DNS 부하 분산](lync-server-2013-scaled-consolidated-edge-dns-load-balancing-with-private-ip-addresses-using-nat.md)

  - [Lync Server 2013의 조정된 통합 에지, 공용 IP 주소의 DNS 부하 분산](lync-server-2013-scaled-consolidated-edge-dns-load-balancing-with-public-ip-addresses.md)

  - [Lync Server 2013의 하드웨어 부하 분산 장치를 사용하는 조정된 통합 에지](lync-server-2013-scaled-consolidated-edge-with-hardware-load-balancers.md)


> [!IMPORTANT]
> 내부 에지 인터페이스와 외부 에지 인터페이스는 같은 유형의 부하 분산을 사용해야 합니다. 즉, 한 에지 인터페이스에서는 DNS 부하 분산을 사용하고 다른 에지 인터페이스에서는 하드웨어 부하 분산을 사용할 수는 없습니다.



다음 표에는 지원되는 Microsoft Lync Server 2013 토폴로지에서 사용할 수 있는 기능이 요약되어 있습니다. 열 머리글은 지정된 에지 구성 옵션에 사용할 수 있는 기능을 나타냅니다. 확장된 에지(DNS 부하 분산됨) 옵션을 예로 들어 보면, 이 옵션은 고가용성을 지원하고, 에지 외부 인터페이스에 할당된 라우팅할 수 없는 개인 IP 주소(NAT 사용) 또는 라우팅 가능한 공용 IP 주소를 사용하고, 하드웨어 부하 분산 장치가 필요하지 않으므로 비용을 줄일 수 있음을 알 수 있습니다.

DNS 부하 분산을 통해 지원되는 에지 장애 조치(failover) 시나리오는 Lync- Lync 지점 간 세션, Lync 회의 세션, Lync-PSTN 세션 및 Office 365입니다. DNS 부하 분산을 활용하지 않는 에지 장애 조치(failover) 시나리오로는 원격 사용자 Exchange 통합 메시징(UM)( Exchange 2010 SP1 이전)에 대한 장애 조치(failover), 공용 IM(인스턴트 메시징) 연결 및 Office Communications Server 실행 서버와의 페더레이션이 있습니다.

### 에지 서버 토폴로지 옵션 요약

<table>
<colgroup>
<col style="width: 20%" />
<col style="width: 20%" />
<col style="width: 20%" />
<col style="width: 20%" />
<col style="width: 20%" />
</colgroup>
<thead>
<tr class="header">
<th>토폴로지</th>
<th>고가용성</th>
<th>에지 풀의 외부 에지 서버에 추가 DNS A 레코드 필요</th>
<th>Lync-- Lync 세션에 대한 에지 장애 조치(failover)</th>
<th>Lync-- Lync EUM/PIC/OCS 페더레이션 세션에 대한 에지 장애 조치(failover)</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>NAT를 사용하는 단일 에지</p></td>
<td><p>아니요</p></td>
<td><p>아니요</p></td>
<td><p>아니요</p></td>
<td><p>아니요</p></td>
</tr>
<tr class="even">
<td><p>공용 IP를 사용하는 단일 에지</p></td>
<td><p>아니요</p></td>
<td><p>아니요</p></td>
<td><p>아니요</p></td>
<td><p>아니요</p></td>
</tr>
<tr class="odd">
<td><p>NAT를 사용하는 확장된 에지(DNS 부하 분산됨)</p></td>
<td><p>예</p></td>
<td><p>예</p></td>
<td><p>예</p></td>
<td><p>*</p></td>
</tr>
<tr class="even">
<td><p>공용 IP를 사용하는 확장된 에지(DNS 부하 분산됨)</p></td>
<td><p>예</p></td>
<td><p>예</p></td>
<td><p>예</p></td>
<td><p>*</p></td>
</tr>
<tr class="odd">
<td><p>확장된 에지(하드웨어 부하 분산됨)</p></td>
<td><p>예</p></td>
<td><p>아니요(VIP당 DNS A 레코드 하나)</p></td>
<td><p>예</p></td>
<td><p>예</p></td>
</tr>
</tbody>
</table>


**\*** 공용 IM(인스턴트 메시징) 연결 및 Office Communications Server 실행 서버와의 페더레이션에 대한 장애 조치(failover)는 DNS 부하 분산을 통해 제공되지 않습니다. DNS 부하 분산을 사용하는 Exchange UM(원격 사용자) 장애 조치(failover)에는 Exchange Server 2010 SP1 이상 버전이 필요합니다.


> [!NOTE]  
> 단일 에지 및 확장된 에지(DNS 부하 분산) 토폴로지는 다음을 사용할 수 있습니다.
> 
> <ul><li><p>라우팅 가능한 공용 IP 주소</p></li>
> <li><p>대칭 NAT(Network Address Translation)를 사용하는 경우 라우팅할 수 없는 개인 IP 주소</p></li></ul>
>  
> NAT와 함께 공용 IP 주소 또는 개인 IP 주소를 사용하는 경우에도 토폴로지 작성기에서 선택한 구성에 따라 같은 수의 IP 주소를 사용합니다. 서비스별로 고유 포트가 지정된 IP 주소 하나를 사용하거나, 서비스별로 다른 IP 주소를 사용하되 같은 포트(기본적으로 포트 443)를 사용하도록 에지 서버를 구성할 수 있습니다.
> 
> NAT와 함께 라우팅할 수 없는 개인 IP 주소를 사용하려는 경우 다음을 수행해야 합니다.
> 
> <ul><li><p>3개 외부 인터페이스 모두에 대해 라우팅 가능한 개인 IP 주소를 사용해야 합니다.</p></li>
> <li><p>들어오는 트래픽과 나가는 트래픽에 대해 대칭 NAT를 구성해야 합니다.</p></li></ul>
> 
> 확장된 에지(하드웨어 부하 분산됨) 토폴로지는 공용 IP 주소를 사용해야 합니다.


Lync Server 2013에서는 단일 통합 에지 서버 토폴로지 및 확장 통합 에지 서버 토폴로지 모두에 대해 NAT(Network Address Translation)를 수행하는 방화벽이나 라우터 뒤에 액세스, 웹 회의 및 A/V 에지 외부 인터페이스를 배치할 수 있습니다.

모든 에지 외부 인터페이스에 대해 NAT를 사용하려면 DNS 부하 분산을 사용해야 합니다. 하드웨어 부하 분산 장치를 사용하는 경우에 비해 NAT를 사용하지 않고 DNS 부하 분산을 사용하면 다음 목록에서 설명하는 것과 같이 에지 풀에서 에지 서버당 공용 IP 주소 수를 줄일 수 있습니다.

  - Lync Server 2013 확장 통합 에지(DNS 부하 분산됨): 에지 풀에서 각 에지 서버에 대해 세 개의 공용 IP 주소가 필요합니다.

  - Lync Server 2013 확장 통합 에지(하드웨어 부하 분산됨): 부하 분산 장치 가상 IP 주소에 대해 세 개의 공용 IP 주소가 필요하며(추가 에지 서버가 풀에 추가되므로 일회성 요구 사항은 늘어나지 않음) 풀에서 에지 서버당 세 개의 공용 IP 주소가 필요합니다.

### 확장 통합 에지에 대한 IP 주소 요구 사항(역할당 IP 주소)

<table>
<colgroup>
<col style="width: 33%" />
<col style="width: 33%" />
<col style="width: 33%" />
</colgroup>
<thead>
<tr class="header">
<th>풀당 에지 서버 수</th>
<th>Lync Server 2013(DNS 부하 분산됨)에 필요한 IP 주소 수</th>
<th>Lync Server 2013(하드웨어 부하 분산됨)에 필요한 IP 주소 수</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>2</p></td>
<td><p>6</p></td>
<td><p>3개(VIP당 1개) + 6개</p></td>
</tr>
<tr class="even">
<td><p>3</p></td>
<td><p>9</p></td>
<td><p>3개(VIP당 1개) + 9개</p></td>
</tr>
<tr class="odd">
<td><p>4</p></td>
<td><p>12</p></td>
<td><p>3개(VIP당 1개) + 12개</p></td>
</tr>
<tr class="even">
<td><p>5</p></td>
<td><p>15</p></td>
<td><p>3개(VIP당 1개) + 15개</p></td>
</tr>
</tbody>
</table>


### 확장 통합 에지에 대한 IP 주소 요구 사항(모든 역할에 대해 단일 IP 주소)

<table>
<colgroup>
<col style="width: 33%" />
<col style="width: 33%" />
<col style="width: 33%" />
</colgroup>
<thead>
<tr class="header">
<th>풀당 에지 서버 수</th>
<th>Lync Server 2013(DNS 부하 분산됨)에 필요한 IP 주소 수</th>
<th>Lync Server 2013(하드웨어 부하 분산됨)에 필요한 IP 주소 수</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>2</p></td>
<td><p>2</p></td>
<td><p>1개(VIP당 1개) + 2개</p></td>
</tr>
<tr class="even">
<td><p>3</p></td>
<td><p>3</p></td>
<td><p>1개(VIP당 1개) + 3개</p></td>
</tr>
<tr class="odd">
<td><p>4</p></td>
<td><p>4</p></td>
<td><p>1개(VIP당 1개) + 4개</p></td>
</tr>
<tr class="even">
<td><p>5</p></td>
<td><p>5</p></td>
<td><p>1개(VIP당 1개) + 5개</p></td>
</tr>
</tbody>
</table>


토폴로지 선택에서 중요한 사항은 고가용성과 부하 분산입니다. 고가용성에 대한 요구 사항은 부하 분산 결정에 영향을 줄 수 있습니다.

  - **고가용성**   고가용성이 필요한 경우에는 두 개 이상의 에지 서버를 풀에 배포해야 합니다. 하나의 에지 풀은 최대 12개의 에지 서버를 지원합니다. 더 많은 용량이 필요한 경우 여러 에지 풀을 배포할 수 있습니다. 대체로 지정된 사용자층의 10%는 외부 액세스가 필요합니다.
    

    > [!IMPORTANT]
    > 토폴로지 작성기에서는 단일 에지 풀에 에지 서버를 20개까지 구성할 수 있습니다. 풀에 포함 가능한 것으로 테스트되었으며 지원이 가능한 최대 에지 서버 수는 12개이며, 토폴로지 작성기에서 12개보다 많은 에지 서버가 허용된다고 해서 단일 에지 풀에서 12개보다 많은 에지 서버가 지원됨을 암시적으로 의미한다고 간주해서는 안 됩니다.



  - **하드웨어 부하 분산**   하드웨어 부하 분산은 에지 외부 인터페이스에 공개적으로 라우팅 가능한 IP 주소를 사용할 때 Lync Server 2013에지 서버의 부하 분산에 지원됩니다. 예를 들어 다음과 같은 응용 프로그램에 장애 조치(failover)가 필요한 경우 이 접근 방법을 사용합니다.
    
      - 공용 메신저 연결
    
      - Microsoft Office Communications Server 2007 또는 Microsoft Office Communications Server 2007 R2를 실행하는 회사와의 페더레이션
    
      - Exchange 2007 UM(통합 메시징) 또는 Exchange 2010 UM에 대한 외부 액세스
        

        > [!IMPORTANT]
        > Exchange UM에서는 Exchange 2010 SP1 이상 버전에 대한 DNS 부하 분산이 지원됩니다.

    
    이 세 가지 응용 프로그램은 계속 작동하지만 DNS 부하 분산을 인식하지 않으므로 풀의 첫 번째 에지 서버에만 연결됩니다. 따라서 이 서버를 사용할 수 없는 경우 연결에 실패합니다. 예를 들어 페더레이션 트래픽 부하를 처리하기 위해 풀에 여러 에지 서버를 배포한 경우 실제로는 하나의 액세스 프록시에서만 트래픽을 수신하고 다른 프록시는 유휴 상태로 유지됩니다.


> [!IMPORTANT]
> DNS 부하 분산은 Lync Server 2010 및 Microsoft Office 365를 사용하는 회사와 페더레이션하는 경우에 사용하는 것이 좋습니다. 대부분의 페더레이션 파트너가 Office Communications Server 2007 또는 Office Communications Server 2007 R2를 사용하면 성능에 큰 영향을 주게 됩니다.


