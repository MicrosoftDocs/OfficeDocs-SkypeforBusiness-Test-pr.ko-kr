---
title: 'Lync Server 2013: 외부 사용자 액세스에 대한 시나리오'
TOCTitle: 외부 사용자 액세스에 대한 시나리오
ms:assetid: 25697446-b045-4d12-9b1c-47f694b4f224
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg425727(v=OCS.15)
ms:contentKeyID: 49303080
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Lync Server 2013의 외부 사용자 액세스에 대한 시나리오

 

_**마지막으로 수정된 항목:** 2015-03-09_

Lync Server 2013에 대해 외부 사용자 액세스 권한을 제공하려면 경계 네트워크에서 에지 서버 하나 이상과 역방향 프록시 하나를 배포해야 합니다. 또한 내부 네트워크에서 디렉터 또는 디렉터 풀을 배포해야 할 수 있습니다.

단일 에지 서버가 제공할 수 있는 것보다 많은 용량이 필요하거나, 에지 서버 배포의 가용성을 높여야 하는 경우에는 부하 분산을 구성하고 부하 분산된 풀에서 여러 에지 서버를 배포할 수 있습니다. 조직에 데이터 센터가 여러 개 있으면 여러 위치에서 에지 서버 또는 에지 풀을 배포할 수 있습니다. 그러나 에지 서버 배포 중 하나만 페더레이션 경로로 지정할 수 있습니다.

이 섹션에서는 에지 서버 배포용 시나리오를 정의하고 계획 섹션을 가능한 시나리오에 매핑합니다. 예를 들어 배포에 고가용성, XMPP(Extensible Messaging and Presence) 연락처와의 페더레이션 및 Lync 모바일 기능이 필요한 경우에는 다음 표에서 이러한 요구 사항을 충족하는 일치 항목을 선택하고 참조 항목으로 나와 있는 계획 섹션을 사용하여 다음 순서도에 나와 있는 대로 배포를 정의합니다.

**에지 서버 배포 시나리오 선택 프로세스**

![샘플 배포 순서도](images/Gg425727.007100b5-6923-4909-bfd7-897d8867205f(OCS.15).jpg "샘플 배포 순서도")

이 프로세스를 사용하면 사용자에게 배포하려는 모든 잠재적 기능의 구성을 계획 및 문서화할 수 있습니다. 그러나 에지 서버를 배포하고 정상적인 작동을 확인한 후 다른 기능을 추가하기 전에 페더레이션 및 모바일 서비스를 추가할 수 있습니다. 기존 에지 서버 배포에 기능을 추가하는 프로세스는 배포 섹션에서 다룹니다. 배포에 대한 자세한 내용은 [Lync Server 2013에서 외부 사용자 액세스 배포](lync-server-2013-deploying-external-user-access.md)를 참조하십시오. 초기 계획 프로세스 중에 이러한 기능에 대한 계획을 포함하면 추가되는 기능에 대해 DNS, 방화벽 및 인증서 요구 사항을 준비할 수 있으므로 인증서를 얻고 DNS 및 포트/프로토콜 요구 사항을 미리 구성할 수 있습니다.


> [!TIP]
> 에지 서버 및 역방향 프록시를 설치한 다음 페더레이션, 모바일 기능 등의 기능을 나중에 설치하려는 경우 배포 후 모든 서비스에 필요한 인증서를 확인합니다. 모든 기능에 대해 인증서를 미리 계획하고 얻으면(초기 배포 여부는 관계없음) 페더레이션( 에지 서버의 경우) 또는 역방향 프록시(모바일 서비스의 경우)의 요구 사항을 충족하도록 새 인증서를 요청하지 않아도 됩니다.




> [!NOTE]
> 모든 에지 서비스는 각 에지 서버에서 실행됩니다. 서로 다른 두 에지 서버 간에 서비스를 분할할 수는 없습니다. 확장성을 위해 에지 풀을 배포하는 경우 모든 에지 서비스는 풀의 각 에지 서버에 배포됩니다. XMPP 페더레이션, Office Communications Server 및 Lync Server 페더레이션, 공용 IM 연결 및 클라이언트 모바일 기능은 첫 번째 에지 서버 또는 에지 풀을 배포한 후 배포할 수 있는 추가 서비스입니다. 모바일 서비스는 역방향 프록시를 사용하는 기능입니다. 모바일 서비스를 설치해도 에지 서버에 기능이 추가되지는 않지만, 역방향 프록시는 다시 구성해야 합니다. 이러한 기능이 나열되어 있는 <STRONG>설치 목표</STRONG> 열의 <STRONG>에지 서버 계획 섹션</STRONG> 아래 관련 열에서는 에지 서버 설치 및 구성 시 이러한 기능을 동시에 배포하도록 계획하기 위한 계획 지침이 제공됩니다.



## 배포 목표 파악 및 매핑


<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th>설치 목표</th>
<th>에지 서버 계획 설명서</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>단일 서버로도 인프라에서 에지 서비스를 제공하는 데 충분하다는 결정을 내렸습니다. 또한 NAT를 포함하는 인터넷으로의 에지 서버 외부 인터페이스에 대해 개인 IP 주소를 사용하려고 합니다.</p>
<p>경계에서 단일 에지 서버를 배포하는 경우 이 계획 섹션을 사용합니다. 개인 IP 주소가 에지 서버에 할당된 상태로 에지 서버를 배포하며, NAT를 사용하여 인터넷의 외부 사용자에 대해 공용 IP 주소를 제공합니다.</p></td>
<td><p><a href="lync-server-2013-single-consolidated-edge-with-private-ip-addresses-and-nat.md">Lync Server 2013의 개인 IP 주소 및 NAT 사용 단일 통합 에지</a></p></td>
</tr>
<tr class="even">
<td><p>단일 서버로도 인프라에서 에지 서비스를 제공하는 데 충분하다는 결정을 내렸습니다. 또한 인터넷으로의 에지 서버 외부 인터페이스에 대해 공용 IP 주소를 사용하려고 합니다.</p>
<p>경계에서 단일 에지 서버를 배포하는 경우 이 계획 섹션을 사용합니다. 공용 IP 주소가 에지 서버에 할당된 상태로 에지 서버를 배포합니다. 이 시나리오에서는 NAT 대신 라우팅을 사용합니다. 에지 서버의 실제 공용 IP 주소는 외부 사용자 연결에 대해 제공됩니다.</p></td>
<td><p><a href="lync-server-2013-single-consolidated-edge-with-public-ip-addresses.md">Lync Server 2013의 공용 IP 주소의 단일 통합 에지</a></p></td>
</tr>
<tr class="odd">
<td><p>사용자에게 에지 서비스의 고가용성이 중요하다는 결정을 내렸으며, 이 풀에 에지 서버를 두 개 이상 배포할 예정입니다. 또한 NAT를 포함하는 인터넷으로의 에지 서버 외부 인터페이스에 대해 개인 IP 주소를 사용하려고 합니다.</p>
<p>경계에서 에지 서버 풀을 배포하는 경우 이 계획 섹션을 사용합니다. 개인 IP 주소가 에지 서버에 할당된 상태로 에지 서버를 배포하며, 풀 전체에서 DNS 부하 분산을 사용하여 통신을 배포합니다. 또한 NAT를 사용하여 인터넷의 외부 사용자에 대해 공용 IP 주소를 제공합니다.</p></td>
<td><p><a href="lync-server-2013-scaled-consolidated-edge-dns-load-balancing-with-private-ip-addresses-using-nat.md">Lync Server 2013의 조정된 통합 에지, NAT 사용 개인 IP 주소의 DNS 부하 분산</a></p></td>
</tr>
<tr class="even">
<td><p>사용자에게 에지 서비스의 고가용성이 중요하다는 결정을 내렸으며, 이 풀에 에지 서버를 두 개 이상 배포할 예정입니다. 또한 인터넷으로의 에지 서버 외부 인터페이스에 대해 공용 IP 주소를 사용하려고 합니다.</p>
<p>경계에서 에지 서버 풀을 배포하는 경우 이 계획 섹션을 사용합니다. 공용 IP 주소가 에지 서버에 할당된 상태로 에지 서버를 배포하며, 풀 전체에서 DNS 부하 분산을 사용하여 통신을 배포합니다. 이 시나리오에서는 NAT 대신 라우팅을 사용하여 인터넷의 외부 사용자에 대해 공용 IP 주소를 제공합니다.</p></td>
<td><p><a href="lync-server-2013-scaled-consolidated-edge-dns-load-balancing-with-public-ip-addresses.md">Lync Server 2013의 조정된 통합 에지, 공용 IP 주소의 DNS 부하 분산</a></p></td>
</tr>
<tr class="odd">
<td><p>사용자에게 에지 서비스의 고가용성이 중요하다는 결정을 내렸으며, 하드웨어 부하 분산 장치를 사용하여 이 풀에 에지 서버를 두 개 이상 배포할 예정입니다.</p>
<p>경계에서 에지 서버 풀을 배포하는 경우 이 계획 섹션을 사용합니다. 공용 IP 주소가 에지 서버에 할당된 상태로 에지 서버를 배포하며, 풀 전체에서 하드웨어 부하 분산 장치를 사용하여 통신을 배포합니다. 이 시나리오에서는 NAT 대신 라우팅을 사용하여 인터넷의 외부 사용자에 대해 공용 IP 주소를 제공합니다.</p></td>
<td><p><a href="lync-server-2013-scaled-consolidated-edge-with-hardware-load-balancers.md">Lync Server 2013의 하드웨어 부하 분산 장치를 사용하는 조정된 통합 에지</a></p></td>
</tr>
<tr class="even">
<td><p>페더레이션 시나리오에서는 사용자가 통신할 수 있는 파트너 유형을 확장하는 기능을 계획할 수 있습니다.</p>
<ul>
<li><p>Lync Server 페더레이션</p></li>
<li><p>Office Communications Server 페더레이션</p></li>
<li><p>공용 메신저 연결</p></li>
<li><p>XMPP 페더레이션</p></li>
</ul></td>
<td><p>페더레이션 시나리오 계획</p>
<ul>
<li><p><a href="lync-server-2013-planning-for-lync-server-and-office-communications-server-federation.md">Lync Server 및 Office Communications Server 페더레이션 계획</a></p></li>
<li><p><a href="lync-server-2013-planning-for-public-instant-messaging-connectivity.md">Lync Server 2013의 공용 메신저 연결 계획</a></p></li>
<li><p><a href="lync-server-2013-planning-for-extensible-messaging-and-presence-protocol-xmpp-federation.md">Lync Server 2013의 XMPP(Extensible Messaging and Presence Protocol) 페더레이션 계획</a></p></li>
</ul></td>
</tr>
<tr class="odd">
<td><p>모바일 서비스는 역방향 프록시를 통해 제공됩니다. 외부 사용자가 모바일 기능을 사용할 수 있도록 설정하는 서비스는 프런트 엔드 서버 또는 프런트 엔드 풀에 배포됩니다. 역방향 프록시에서 게시 규칙을 만들거나 기존 게시 규칙을 수정하여 외부 사용자가 모바일 서비스를 사용할 수 있도록 설정합니다.</p></td>
<td><p><a href="lync-server-2013-planning-for-mobility.md">Lync Server 2013의 모바일 기능 계획</a></p></td>
</tr>
</tbody>
</table>



> [!TIP]
> 다음 시나리오 섹션에는 참조 아키텍처, DNS 예, 포트/프로토콜 정의 및 인증서 요구 사항이 나와 있습니다. 또한 DNS, 포트/프로토콜 정의 및 인증서 요구 사항 다이어그램도 포함되어 있습니다. 이 다이어그램에서는 내용을 입력하여 다른 팀(예: 조직의 네트워크 팀, 공개 키 인프라 팀, 서버 배포 팀)에 배포할 수 있는 템플릿이 제공됩니다. 다이어그램을 참조하여 통신 기능을 개선하고 실제 구성 작업을 수행할 사용자에게 필수 에지 서버 구성 요소를 적절하게 전달할 수 있습니다. 다이어그램 및 관련 참조 아키텍처를 사용하여 배포를 계획하는 것이 좋습니다.


