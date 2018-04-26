---
title: Lync Server 2013 하드웨어 부하 분산 장치 요구 사항
TOCTitle: 하드웨어 부하 분산 장치 요구 사항
ms:assetid: 32891268-2059-43d0-adf4-af4ff1e9ce66
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/JJ656815(v=OCS.15)
ms:contentKeyID: 49885718
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Lync Server 2013에 대한 하드웨어 부하 분산 장치 요구 사항

 

_**마지막으로 수정된 항목:** 2015-05-11_

Lync Server 2013 확장된 통합 에지 토폴로지는 주로 Lync Server를 사용하는 다른 조직과 페더레이션하는 새 배포의 DNS 부하 분산에 최적화되어 있습니다. 다음과 같은 시나리오에 고가용성이 필요한 경우에는 에지 서버 풀에서 다음에 대해 하드웨어 부하 분산 장치를 사용해야 합니다.

  - Office Communications Server 2007 R2 또는 Office Communications Server 2007을 사용하는 조직과의 페더레이션

  - Exchange 2010 SP1 이전 Exchange UM을 사용하는 원격 사용자용 Exchange UM

  - 공용 IM 사용자 연결


> [!IMPORTANT]
> DNS 부하 분산과 하드웨어 부하 분산을 서로 다른 인터페이스에서 사용할 수 없습니다. 두 인터페이스에서 모두 하드웨어 부하 분산 또는 DNS 부하 분산을 사용해야 합니다.




> [!NOTE]
> 하드웨어 부하 분산 장치를 사용하는 경우, 내부 네트워크와의 연결을 위해 배포된 부하 분산 장치는 액세스 에지 서비스와 A/V 에지 서비스를 실행 중인 서버의 트래픽 부하만 분산하도록 구성해야 합니다. 즉, 이 부하 분산 장치를 사용하여 내부 웹 회의 에지 서비스 또는 내부 XMPP 프록시 서비스에 대한 트래픽 부하 분산을 수행할 수는 없습니다.




> [!NOTE]
> DSR(직접 서버 반환) NAT는 Lync Server 2013에서 지원되지 않습니다.



하드웨어 부하 분산 장치가 Lync Server 2013에 필요한 기능을 지원하는지 확인하려면 [http://go.microsoft.com/fwlink/?linkid=202452\&clcid=0x412](http://go.microsoft.com/fwlink/?linkid=202452%26clcid=0x412)에서 " Lync Server 2010 부하 분산 장치 파트너"를 참조하십시오.

## A/V 에지 서비스를 실행하는 에지 서버에 대한 하드웨어 부하 분산 장치 요구 사항

다음은 A/V 에지 서비스를 실행하는 에지 서버에 대한 하드웨어 부하 분산 장치 요구 사항입니다.

  - 내부 및 외부 포트 443에 대해 TCP Nagling을 해제합니다. Nagling은 보다 효율적인 전송을 위해 여러 개의 작은 패킷을 하나의 큰 패킷으로 결합하는 프로세스입니다.

  - 외부 포트 범위 50,000~59,999에 대해 TCP Nagling을 해제합니다.

  - 내부 또는 외부 방화벽에 NAT를 사용하지 않습니다.

  - 에지 내부 인터페이스는 에지 서버 외부 인터페이스와 다른 네트워크에 있어야 하며 두 인터페이스 간의 라우팅은 사용할 수 없도록 설정되어야 합니다.

  - A/V 에지 서비스를 실행하는 에지 서버의 외부 인터페이스는 에지 외부 IP 주소의 NAT 또는 포트 변환이 아니라 공개적으로 라우팅 가능한 IP 주소를 사용해야 합니다.

## 하드웨어 부하 분산 장치 요구 사항

Lync Server 2013에서는 웹 서비스에 대한 쿠키 기반 선호도 요구 사항이 크게 감소했습니다. Lync Server 2013을 배포하며 Lync Server 2010프런트 엔드 서버 또는 프런트 엔드 풀을 보존하지 않으려는 경우 쿠키 기반 지속성이 필요하지 않습니다. 그러나 Lync Server 2010프런트 엔드 서버 또는 프런트 엔드 풀을 일시적으로 또는 영구적으로 보존하려는 경우에는 Lync Server 2010용으로 배포 및 구성된 쿠키 기반 지속성을 계속 사용해야 합니다.


> [!NOTE]
> <STRONG>배포에서 필요하지 않은 경우에도 쿠키 기반 선호도를 사용하려는 경우</STRONG> 부정적인 영향은 없습니다.



쿠키 기반 선호도를 **사용하지 않는** 배포에는 다음이 적용됩니다.

  - 포트 4443에 대한 역방향 프록시 게시 규칙에 대해 **호스트 헤더 전달** 을 True로 설정합니다. 그러면 원래 URL이 전달됩니다.

쿠키 기반 선호도를 **사용하는** 배포에는 다음이 적용됩니다.

  - 포트 4443에 대한 역방향 프록시 게시 규칙에 대해 **호스트 헤더 전달** 을 True로 설정합니다. 그러면 원래 URL이 전달됩니다.

  - 하드웨어 부하 분산 장치 쿠키는 httpOnly로 표시해서는 안 됩니다.

  - 하드웨어 부하 분산 장치 쿠키에 만료 시간이 있어서는 안 됩니다.

  - 하드웨어 부하 분산 장치 쿠키 이름은 **MS-WSMAN**(웹 서비스에 필요한 값이며 변경할 수 없음)으로 지정해야 합니다.

  - 동일한 TCP 연결의 이전 HTTP 응답에서 이미 쿠키를 가져왔는지 여부에 관계없이, 들어오는 HTTP 요청에 쿠키가 없었던 모든 HTTP 응답에서 하드웨어 부하 분산 장치 쿠키를 설정해야 합니다. 부하 분산 장치에서 TCP 연결당 한 번만 쿠키 삽입이 수행되도록 최적화하는 경우에는 해당 최적화를 사용하면 안 됩니다.


> [!NOTE]
> 일반적인 하드웨어 부하 분산 장치 구성에서는 원본 주소 선호도와 TCP 세션 수명 20분을 사용하며, 이 경우 세션 상태가 클라이언트 사용 및/또는 응용 프로그램 상호 작용 전체에서 유지되므로 해당 구성은 Lync Server 및 Lync 2013 클라이언트에 적합합니다.



모바일 장치를 배포하는 경우 하드웨어 부하 분산 장치는 TCP 세션 내의 개별 요청 부하를 분산할 수 있어야 합니다(대상 IP 주소를 기준으로 개별 요청 부하를 분산할 수 있어야 함).


> [!WARNING]
> F5 하드웨어 부하 분산 장치에는 TCP 연결 내의 각 요청이 개별적으로 부하 분산되도록 하는 OneConnect라는 기능이 있습니다. 모바일 장치를 배포하는 경우 하드웨어 부하 분산 장치 공급업체에서 이와 동일한 기능을 지원하는지 확인하십시오. 최신 Apple iOS 모바일 앱의 경우 TLS(전송 계층 보안) 버전 1.2가 필요합니다. F5는 이 버전을 위한 특정 설정을 제공합니다.<BR>타사 하드웨어 부하 분산 장치에 대한 자세한 내용은 <A class=uri href="http://go.microsoft.com/fwlink/?linkid=230700%26clcid=0x412">http://go.microsoft.com/fwlink/?linkid=230700&amp;clcid=0x412</A>를 참조하십시오.



다음은 디렉터 및 프런트 엔드 풀 웹 서비스에 대한 하드웨어 부하 분산 장치 요구 사항입니다.

  - 내부 웹 서비스 VIP의 경우 하드웨어 부하 분산 장치에 Source\_addr 지속성(내부 포트 80, 443)을 설정합니다. Lync Server 2013의 경우 Source\_addr 지속성은 세션 상태를 유지하기 위해 단일 IP 주소의 여러 연결이 항상 하나의 서버로 전송됨을 의미합니다.

  - 1800초의 TCP 유휴 시간 제한을 사용합니다.

  - 역방향 프록시와 다음 홉 풀의 하드웨어 부하 분산 장치 사이에 있는 방화벽에 역방향 프록시에서 하드웨어 부하 분산 장치로 전송되는 https: 트래픽(포트 4443)을 허용하는 규칙을 만듭니다. 하드웨어 부하 분산 장치는 포트 80, 443 및 4443에서 수신 대기하도록 구성되어야 합니다.

## 하드웨어 부하 분산 장치 선호도 요구 사항 요약


<table>
<colgroup>
<col style="width: 33%" />
<col style="width: 33%" />
<col style="width: 33%" />
</colgroup>
<thead>
<tr class="header">
<th>클라이언트/사용자 위치</th>
<th>외부 웹 서비스 FQDN 선호도 요구 사항</th>
<th>내부 웹 서비스 FQDN 선호도 요구 사항</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Lync Web App(내부 및 외부 사용자)</p>
<p>모바일 장치(내부 및 외부 사용자)</p></td>
<td><p>선호도 없음</p></td>
<td><p>원본 주소 선호도</p></td>
</tr>
<tr class="even">
<td><p>Lync Web App(외부 사용자 전용)</p>
<p>모바일 장치(내부 및 외부 사용자)</p></td>
<td><p>선호도 없음</p></td>
<td><p>원본 주소 선호도</p></td>
</tr>
<tr class="odd">
<td><p>Lync Web App(내부 사용자 전용)</p>
<p>모바일 장치(배포되지 않음)</p></td>
<td><p>선호도 없음</p></td>
<td><p>원본 주소 선호도</p></td>
</tr>
</tbody>
</table>


## 하드웨어 부하 분산 장치용 포트 모니터링

하드웨어 부하 분산 장치에 대해 포트 모니터링을 정의하여 하드웨어 또는 통신 오류로 인해 특정 서비스를 더 이상 사용할 수 없는 시기를 확인합니다. 예를 들어 프런트 엔드 서버 또는 프런트 엔드 풀에 오류가 발생하여 프런트 엔드 서버 서비스(RTCSRV)가 중지되면 HLB 모니터링은 웹 서비스에서 트래픽 수신도 중지해야 합니다. HLB에 대해 포트 모니터링을 구현하여 다음 항목을 모니터링합니다.

### 프런트 엔드 서버 사용자 풀 - HLB 내부 인터페이스

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
<th>가상 IP/포트</th>
<th>노드 포트</th>
<th>노드 컴퓨터/모니터</th>
<th>지속성 프로필</th>
<th>참고</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>&lt;풀&gt;web-int_mco_443_vs</p>
<p>443</p></td>
<td><p>443</p></td>
<td><p>프런트 엔드</p>
<p>5061</p></td>
<td><p>원본</p></td>
<td><p>HTTPS</p></td>
</tr>
<tr class="even">
<td><p>&lt;풀&gt;web-int_mco_80_vs</p>
<p>80</p></td>
<td><p>80</p></td>
<td><p>프런트 엔드</p>
<p>5061</p></td>
<td><p>원본</p></td>
<td><p>HTTP</p></td>
</tr>
</tbody>
</table>


### 프런트 엔드 서버 사용자 풀 - HLB 외부 인터페이스

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
<th>가상 IP/포트</th>
<th>노드 포트</th>
<th>노드 컴퓨터/모니터</th>
<th>지속성 프로필</th>
<th>참고</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>&lt;풀&gt;web_mco_443_vs</p>
<p>443</p></td>
<td><p>4443</p></td>
<td><p>프런트 엔드</p>
<p>5061</p></td>
<td><p>없음</p></td>
<td><p>HTTPS</p></td>
</tr>
<tr class="even">
<td><p>&lt;풀&gt;web_mco_80_vs</p>
<p>80</p></td>
<td><p>8080</p></td>
<td><p>프런트 엔드</p>
<p>5061</p></td>
<td><p>없음</p></td>
<td><p>HTTP</p></td>
</tr>
</tbody>
</table>

