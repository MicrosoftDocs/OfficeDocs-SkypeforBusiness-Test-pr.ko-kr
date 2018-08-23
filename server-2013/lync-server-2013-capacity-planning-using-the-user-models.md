---
title: Lync Server 2013 사용자 모델을 사용한 용량 계획
TOCTitle: 사용자 모델을 사용한 용량 계획
ms:assetid: 902ab23e-94d6-482a-9d6e-c0b28dc3e03d
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg615015(v=OCS.15)
ms:contentKeyID: 49885874
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Lync Server 2013의 사용자 모델을 사용한 용량 계획

 

_**마지막으로 수정된 항목:** 2015-03-09_

이 섹션에서는 [Lync Server 2013의 사용자 모델](lync-server-2013-user-models.md)에 설명된 방법으로 사용할 경우 사이트의 사용자 수를 고려하여 사이트에 필요한 서버 수를 결정하는 방법에 대한 지침을 제공합니다.

## 테스트된 하드웨어 플랫폼

이 섹션에 나온 모든 성능 결과와 배포 권장 사항은 아래 표에 정리된 하드웨어를 실행하는 서버에 대한 성능 테스트를 기준으로 한 것입니다. 이와 유사한 하드웨어를 사용하는 것이 좋으며, 이보다 낮은 사양의 하드웨어를 사용할 경우 기능 문제나 성능 저하를 경험할 수 있습니다. 이러한 하드웨어 권장 사양은 이전 버전의 Lync Server보다 높습니다.

### 성능 테스트에 사용된 하드웨어

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th>하드웨어 구성 요소</th>
<th>권장</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>CPU</p></td>
<td><p>64비트 듀얼 프로세서, 헥사 코어, 2.26GHz 이상</p>
<p>Intel Itanium 프로세서는 Lync Server 역할에 지원되지 않습니다.</p></td>
</tr>
<tr class="even">
<td><p>메모리</p></td>
<td><p>32GB</p></td>
</tr>
<tr class="odd">
<td><p>디스크</p></td>
<td><ul>
<li><p>72GB 이상의 사용 가능한 디스크 공간이 있는 10,000RPM 하드 디스크 드라이브 8개 이상</p>
<p>이 중 두 개는 RAID 1을 사용하고 6개는 RAID 10을 사용합니다.</p>
<p>-또는-</p></li>
<li><p>8개의 10,000 RPM 기계식 디스크 드라이브와 유사한 성능을 제공하는 SDD(반도체 드라이브)</p></li>
</ul></td>
</tr>
<tr class="even">
<td><p>네트워크</p></td>
<td><ul>
<li><p>1개의 이중 포트 네트워크 어댑터, 1Gbps 이상(2개 권장, 단일 MAC 주소와 단일 IP 주소를 사용하여 팀으로 구성해야 함)</p></li>
</ul></td>
</tr>
</tbody>
</table>


## 결과 요약

다음 표는 서버 테스트 결과에 따른 권장 사항을 요약한 것입니다.


<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th>서버 역할</th>
<th>지원되는 최대 사용자 수</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>12개의 프런트 엔드 서버와 1개의 백 엔드 서버 또는 미러링된 한 쌍의 백 엔드 서버로 구성된 프런트 엔드 풀</p></td>
<td><p>동시에 로그인된 80,000명의 고유 사용자 + 비모바일 인스턴스를 나타내는 MPOP(Multiple Point of Presence) 50% +총 152,000개의 끝점에 대한 모바일 기능을 사용하도록 설정된 사용자 40%</p></td>
</tr>
<tr class="even">
<td><p>A/V 회의</p></td>
<td><p>프런트 엔드 풀에서 제공하는 A/V 회의 서비스의 지원되는 최대 회의 규모는 사용자 250명이며, 이러한 대규모 회의는 한 번에 하나만 실행할 수 있습니다.</p>


> [!NOTE]
> 또한 대규모 회의를 호스트하는 2개의 프런트 엔드 서버로 구성된 별도의 프런트 엔드 풀을 배포하여 250명~1,000명의 사용자가 참여하는 보다 큰 규모의 회의를 지원할 수 있습니다. 자세한 내용은 <A href="lync-server-2013-supporting-large-meetings.md">Lync Server 2013으로 대규모 모임 지원</A>을 참고하세요.


</td>
</tr>
<tr class="odd">
<td><p>1개의 에지 서버</p></td>
<td><p>12,000명의 동시 원격 사용자</p></td>
</tr>
<tr class="even">
<td><p>1개의 디렉터</p></td>
<td><p>12,000명의 동시 원격 사용자</p></td>
</tr>
<tr class="odd">
<td><p>모니터링 및 보관</p></td>
<td><p>Lync Server 2013에서는 이제 모니터링 및 보관 프런트 엔드 서비스가 별도의 서버 역할이 아닌 각 프런트 엔드 서버에서 실행됩니다.</p>
<p>모니터링과 보관에는 각각 자체 데이터베이스 저장소가 여전히 필요합니다. Exchange 2013도 실행하는 경우 보관 데이터를 전용 SQL 데이터베이스가 아닌 Exchange에 유지할 수 있습니다.</p></td>
</tr>
<tr class="even">
<td><p>1개의 중재 서버</p></td>
<td><p>프런트 엔드 서버와 함께 배치된 중재 서버는 풀의 모든 프런트 엔드 서버에서 실행되며 풀의 사용자를 위한 충분한 용량을 제공합니다. 독립 실행형 중재 서버에 대한 자세한 내용은 이 항목의 뒷부분에 나오는 “중재 서버” 섹션을 참고하세요.</p></td>
</tr>
<tr class="odd">
<td><p>단일 Standard Edition 서버</p></td>
<td><p>Standard Edition 서버를 사용해 사용자를 호스팅하는 경우 <a href="lync-server-2013-planning-for-high-availability-and-disaster-recovery.md">Lync Server 2013의 고가용성 및 재해 복구 계획</a>의 권장 사항에 따라 항상 2개의 서버를 쌍으로 묶어 사용하는 것이 좋습니다. 이 쌍의 각 서버는 최대 2,500명의 사용자를 호스팅할 수 있으며, 서버 하나에서 오류가 발생하면 남은 서버가 장애 조치(failover) 시나리오에서 5천 명의 사용자를 지원할 수 있습니다.</p>
<p>배포에 많은 양의 오디오 또는 비디오 트래픽이 포함된 경우 서버당 사용자가 2,500명 이상인 경우에는 서버 성능이 저하될 수 있습니다. 이 경우 Standard Edition 서버를 더 추가하거나 Lync ServerEnterprise Edition으로 전환해야 할 수 있습니다.</p></td>
</tr>
</tbody>
</table>


## 프런트 엔드 서버


> [!NOTE]
> 확장된 풀은 이 서버 역할에는 지원되지 않습니다.



풀의 모든 서버에서 하이퍼 스레딩을 사용하고 서버 하드웨어가 [Lync Server 2013의 서버 하드웨어 플랫폼](lync-server-2013-server-hardware-platforms.md)의 권장 사양을 충족한다고 했을 때 프런트 엔드 풀에는 풀에 소속된 6,660명의 사용자당 1개의 프런트 엔드 서버가 있어야 합니다. 풀의 모든 서버에서 하이퍼 스레딩을 사용할 경우 하나의 프런트 엔드 풀에서 지원하는 최대 사용자 수는 80,000명입니다. 사이트 사용자 수가 80,000명을 넘는 경우 둘 이상의 프런트 엔드 풀을 배포할 수 있습니다.

프런트 엔드 풀의 사용자 수를 계산할 때는 이 프런트 엔드 풀과 연결된 지점의 SBA(Survivable Branch Appliance) 및 지속 가능 분기 서버에 있는 사용자를 포함시킵니다.

활성 서버를 사용할 수 없는 경우 해당 연결이 풀의 다른 서버에 자동으로 전송됩니다. 예를 들어 사용자 수가 30,000명이고 5개의 프런트 엔드 서버가 있는 경우 하나의 서버를 사용할 수 없으면 6,000명의 사용자 연결을 다른 네 서버에 전송해야 합니다. 이 경우 네 서버의 사용자 수가 각각 7,500명이 되므로 권장치를 초과하게 됩니다.

그러나 사용자 수가 30,000명일 때 6개의 프런트 엔드 서버로 시작하면 하나의 서버를 사용할 수 없는 경우 총 5,000명의 사용자가 다른 다섯 서버로 이동하므로 다섯 서버가 각각 6,000명의 사용자를 호스트하여 사용자 수가 권장 범위 내로 유지됩니다.

프런트 엔드 풀의 최대 사용자 수는 80,000명이고, 풀의 최대 프런트 엔드 서버 수는 12개입니다.

프런트 엔드 풀의 사용자 수가 80,000명인 경우 [Lync Server 2013의 사용자 모델](lync-server-2013-user-models.md)에 따른 일반적인 배포에서는 12개의 프런트 엔드 서버로 성능을 충분히 유지할 수 있습니다. 재해 복구 장애 조치(failover)를 지원하도록 설계된 배포에서는 한 쌍을 이루는 두 프런트 엔드 풀에 각각 최대 40,000명의 사용자를 호스트할 수 있으며, 하나의 풀을 다른 풀로 장애 조치해야 할 경우를 위해 각 풀이 두 풀의 사용자를 모두 수용할 수 있는 충분한 프런트 엔드 서버를 갖습니다.

그러나 다음과 같은 경우에는 특정 프런트 엔드 풀에서 적정 성능을 유지하며 지원되는 사용자 수가 이와 달라질 수 있습니다.

  - 프런트 엔드 서버의 하드웨어가 [Lync Server 2013의 서버 하드웨어 플랫폼](lync-server-2013-server-hardware-platforms.md)에 나온 권장 사양을 충족하지 않는 경우

  - 조직의 사용법이 사용자 모델과 크게 다른 경우(예: 회의 트래픽이 훨씬 큰 경우)


> [!IMPORTANT]
> Lync Server 2010에서는 현재 상태 데이터베이스가 백 엔드 서버에서 호스트된 반면, Lync Server 2013에서는 이제 현재 상태 데이터베이스가 프런트 엔드 서버에서 호스트됩니다. 따라서 프런트 엔드 서버에서 호스트하는 사용자 수에 관계없이 프런트 엔드 서버의 디스크 성능 및 용량이 이 섹션 앞부분과 <A href="lync-server-2013-server-hardware-platforms.md">Lync Server 2013의 서버 하드웨어 플랫폼</A>에 나온 권장 사양을 반드시 따라야 합니다.



다음 표에서는 [Lync Server 2013의 사용자 모델](lync-server-2013-user-models.md)에 정의된 대로 특정 사용자 모델에서 IM 및 현재 상태에 대한 평균 대역폭을 보여줍니다.


<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th>사용자당 평균 대역폭</th>
<th>사용자 수가 6,600명인 경우의 프런트 엔드 서버당 대역폭 요구 사항</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>1.3Kpbs</p></td>
<td><p>13Mbps</p></td>
</tr>
</tbody>
</table>



> [!NOTE]
> 프런트 엔드 서버에 함께 배치된 A/V 회의 및 중재 서버 기능의 미디어 성능을 향상시키려면 프런트 엔드 서버에서 네트워크 어댑터의 RSS(수신측 배율)를 활성화해야 합니다. 자세한 내용은 "Windows Server 2008의 향상된 RSS(수신측 배율) 기능"( <A class=uri href="http://go.microsoft.com/fwlink/?linkid=268731">http://go.microsoft.com/fwlink/?linkid=268731</A>)을 참고하세요. RSS를 사용하도록 설정하는 방법에 대한 자세한 내용은 네트워크 어댑터 설명서를 참고하세요.



## 회의 최대값

풀 사용자의 5%가 동시에 전화 회의에 참가할 수 있는 사용자 모델의 경우 사용자 수가 80,000명인 풀에서는 약 4,000명의 사용자가 동시에 전화 회의에 참가할 수 있습니다. 이러한 전화 회의에서는 참가자 수가 다양하고 여러 가지 미디어(예: IM 전용, IM과 오디오, 오디오/비디오 등의 혼합)가 사용될 수 있습니다. 허용되는 실제 전화 회의 수에는 명확한 제한이 없지만 실제 사용법에 따라 실제 성능이 달라집니다. 예를 들어 조직에 사용자 모델에 예상된 것보다 많은 수의 혼합 모드 회의가 포함된 경우 이 문서의 권장 사항보다 많은 프런트 엔드 서버 또는 A/V 회의 서버를 배포해야 할 수 있습니다. 사용자 모델의 가정에 대한 자세한 내용은 [Lync Server 2013의 사용자 모델](lync-server-2013-user-models.md)을 참고하세요.

일반적인 Lync Server 2013프런트 엔드 풀에서 호스트하는 전화 회의의 지원되는 최대 규모는 참가자 250명입니다. 250명 규모의 전화 회의가 진행되는 동안 풀에서는 다른 전화 회의를 계속 지원할 수 있습니다. 이때 풀에서 지원하는 동시 전화 회의 참가자 수는 풀 사용자의 총 5%입니다. 예를 들어 사용자 수가 80,000명이고 12개의 프런트 엔드 서버로 구성된 풀에서 250명 규모의 전화 회의가 진행되는 동안 Lync Server에서는 이보다 작은 규모의 전화 회의에 참가하는 3,750명의 다른 사용자를 지원합니다.

프런트 엔드 풀 또는 Standard Edition Server에 있는 사용자 수에 관계없이 Lync Server는 250명 규모의 전화 회의를 호스트하는 풀 또는 서버에서 125명 이상의 다른 사용자가 이보다 작은 규모의 전화 회의에 참가할 수 있도록 지원합니다.

250명~1,000명의 사용자가 참여하는 전화 회의를 진행할 수 있도록 하려면 이러한 전화 회의만 호스트하는 프런트 엔드 풀을 설정하면 됩니다. 이 프런트 엔드 풀에는 사용자가 호스트되지 않습니다. 자세한 내용은 [Lync Server 2013으로 대규모 모임 지원](lync-server-2013-supporting-large-meetings.md)을 참고하세요.

조직에 사용자 모델에 예상된 것보다 많은 수의 혼합 모드 회의가 포함된 경우 이 문서의 권장 사항보다 많은 프런트 엔드 서버(최대 12개의 프런트 엔드 서버)를 배포해야 할 수 있습니다. 사용자 모델의 가정에 대한 자세한 내용은 [Lync Server 2013의 사용자 모델](lync-server-2013-user-models.md)을 참고하세요.

## 에지 서버


> [!NOTE]
> 확장된 풀은 이 서버 역할에는 지원되지 않습니다.



사이트에 동시에 액세스하는 원격 사용자 12,000명당 하나의 에지 서버를 배포해야 하며, 고가용성을 유지하려면 최소한 두 개의 에지 서버를 사용하는 것이 좋습니다. 이러한 권장 사항은 에지 서버의 하드웨어가 [Lync Server 2013의 서버 하드웨어 플랫폼](lync-server-2013-server-hardware-platforms.md)에 나온 권장 사양을 충족하는 것으로 가정합니다.

에지 서버의 사용자 수를 계산할 때는 이 사이트의 프런트 엔드 풀과 연결된 지점의 SBA(Survivable Branch Appliance) 및 지속 가능 분기 서버에 있는 사용자를 포함시킵니다.


> [!NOTE]
> 에지 서버의 A/V 회의 에지 서비스 성능을 향상시키려면 에지 서버에서 네트워크 어댑터의 RSS(수신측 배율)를 활성화해야 합니다. RSS는 수신 패킷을 서버의 여러 프로세서에서 병렬로 처리하도록 합니다. 자세한 내용은 "Windows Server 2008의 향상된 RSS(수신측 배율) 기능"( <A class=uri href="http://go.microsoft.com/fwlink/?linkid=268731">http://go.microsoft.com/fwlink/?linkid=268731</A>)을 참고하세요. RSS를 사용하도록 설정하는 방법에 대한 자세한 내용은 네트워크 어댑터 설명서를 참고하세요.



## 디렉터


> [!NOTE]
> 확장된 풀은 이 서버 역할에는 지원되지 않습니다.



디렉터 서버 역할을 배포하는 경우 사이트에 동시에 액세스하는 원격 사용자 12,000명당 하나의 디렉터를 배포하는 것이 좋으며, 고가용성을 유지하려면 최소한 두 개의 디렉터를 사용하는 것이 좋습니다. 이러한 권장 사항은 에지 서버의 하드웨어가 [Lync Server 2013의 서버 하드웨어 플랫폼](lync-server-2013-server-hardware-platforms.md)에 나온 권장 사양을 충족하는 것으로 가정합니다.

디렉터의 사용자 수를 계산할 때는 이 사이트의 프런트 엔드 풀과 연결된 지점의 SBA(Survivable Branch Appliance) 및 지속 가능 분기 서버에 있는 사용자를 포함시킵니다.

## 중재 서버


> [!NOTE]
> 확장된 풀은 이 서버 역할에는 지원되지 않습니다.



프런트 엔드 서버와 함께 중재 서버를 배치하는 경우 중재 서버는 풀의 모든 프런트 엔드 서버에서 실행되며 풀의 사용자를 위한 충분한 용량을 제공합니다.

독립 실행형 중재 서버 풀을 배포하는 경우, 배포할 중재 서버 수는 중재 서버에 사용되는 하드웨어, VoIP 사용자 수, 각 중재 서버 풀 풀에서 제어하는 게이트웨이 피어 수, 네트워크 사용량이 많은 시간에 이러한 게이트웨이를 통과하는 트래픽, 중재 서버를 바이패스하는 통화 비율 등 여러 요소에 따라 결정됩니다.

다음 표에서는 중재 서버에서 처리할 수 있는 동시 통화 수에 대한 지침을 제공합니다. 이 지침은 중재 서버의 하드웨어가 [Lync Server 2013의 서버 하드웨어 플랫폼](lync-server-2013-server-hardware-platforms.md)에 나온 요구 사항을 충족하고 하이퍼 스레딩을 사용하는 것으로 가정합니다. 중재 서버 확장성에 대한 자세한 내용은 [Lync Server 2013의 음성 사용량 및 트래픽 예상](lync-server-2013-estimating-voice-usage-and-traffic.md) 및 [Lync Server 2013의 중재 서버 배포 지침](lync-server-2013-deployment-guidelines-for-mediation-server.md)을 참고하세요.

아래에 나오는 모든 표에서는 [Lync Server 2013의 사용자 모델](lync-server-2013-user-models.md)에 요약된 사용법을 따르는 것으로 가정합니다.

### 독립 실행형 중재 서버 용량: 내부 사용자 70%, 바이패스가 없는 통화 용량을 갖는 외부 사용자 30%( 중재 서버에서 미디어 코드 변환)

<table>
<colgroup>
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
</colgroup>
<thead>
<tr class="header">
<th>서버 하드웨어</th>
<th>최대 통화 수</th>
<th>최대 T1 회선 수</th>
<th>최대 E1 회선 수</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>듀얼 프로세서, 헥사 코어, 2.26GHz 하이퍼 스레드 CPU( <strong>하이퍼 스레딩 사용 안 함</strong>), 32GB 메모리 및 1개의 이중 포트 네트워크 어댑터 카드</p></td>
<td><p>1100</p></td>
<td><p>46</p></td>
<td><p>35</p></td>
</tr>
<tr class="even">
<td><p>듀얼 프로세서, 헥사 코어, 2.26GHz 하이퍼 스레드 CPU, 32GB 메모리 및 1개의 이중 포트 네트워크 어댑터 카드</p></td>
<td><p>1500</p></td>
<td><p>63</p></td>
<td><p>47</p></td>
</tr>
</tbody>
</table>



> [!NOTE]
> 성능 테스트를 위해서는 32GB 메모리의 서버가 사용되었지만 독립 실행형 중재 서버에서는 16GB 메모리의 서버가 지원되며 이 표에 표시된 성능을 충분히 제공할 수 있습니다.



### 중재 서버 용량( 프런트 엔드 서버와 함께 배치된 중재 서버) 내부 사용자 70%, 바이패스가 없는 통화 용량을 갖는 외부 사용자 30%( 중재 서버에서 미디어 코드 변환)

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th>서버 하드웨어</th>
<th>최대 통화 수</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>듀얼 프로세서, 헥사 코어, 2.26GHz 하이퍼 스레드 CPU, 32GB 메모리 및 2개의 1GB 네트워크 어댑터 카드</p></td>
<td><p>150</p></td>
</tr>
</tbody>
</table>



> [!NOTE]
> 이 수치는 독립 실행형 중재 서버에 비해 훨씬 작습니다. 그 이유는 프런트 엔드 서버에서 음성 통화에 필요한 코드 변환은 물론 소속된 사용자 6,600명에 대한 기타 기능을 처리해야 하기 때문입니다.




> [!NOTE]
> 중재 서버의 성능을 향상시키려면 중재 서버에서 네트워크 어댑터의 RSS(수신측 배율)를 활성화해야 합니다. RSS는 수신 패킷을 서버의 여러 프로세서에서 병렬로 처리하도록 합니다. 자세한 내용은 "Windows Server 2008의 향상된 RSS(수신측 배율) 기능"( <A class=uri href="http://go.microsoft.com/fwlink/?linkid=268731">http://go.microsoft.com/fwlink/?linkid=268731</A>)을 참고하세요. RSS를 사용하도록 설정하는 방법에 대한 자세한 내용은 네트워크 어댑터 설명서를 참고하세요.



## 백 엔드 서버

Lync Server 2013에서는 현재 상태 데이터베이스가 백 엔드 서버이 아닌 프런트 엔드 서버에 있습니다. 이에 따라 Lync Server 2013의 각 백 엔드 서버에 대한 요구 사항이 프런트 엔드 서버의 하드웨어 요구 사항과 동등한 수준으로 훨씬 단순해졌습니다. 이에 비해 Lync Server 2010에서는 백 엔드 서버가 25개의 디스크를 갖춘 훨씬 높은 등급의 서버여야 했습니다. 하지만 백 엔드 서버의 작업 특성상 여전히 이 섹션 앞부분과 [Lync Server 2013의 서버 하드웨어 플랫폼](lync-server-2013-server-hardware-platforms.md)에 나온 하드웨어 권장 사양을 충족해야 합니다.

백 엔드 서버의 고가용성을 제공하려면 서버 미러링을 배포하는 것이 좋습니다. 자세한 내용은 [Lync Server 2013의 백 엔드 서버 고가용성](lync-server-2013-back-end-server-high-availability.md)을 참고하세요.

## 모니터링 및 보관

Lync Server 2013에서는 모니터링 또는 보관을 배포하는 경우 이러한 서비스의 프런트 엔드 기능이 별도의 서버 역할이 아닌 프런트 엔드 서버에서 실행됩니다. 모니터링과 보관은 여전히 각각 백 엔드 저장소와 별도의 자체 데이터베이스 저장소를 사용합니다. Exchange 2013이 배포되어 있는 경우 메신저 대화 보관 데이터를 전용 SQL 저장소 대신 Exchange에 저장할 수 있습니다.

다음 표에는 사용자당 일일 모니터링 및 보관 데이터에 필요한 대략적인 데이터베이스 저장소 용량이 나와 있습니다.


<table>
<colgroup>
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p></p></td>
<td><p><strong>CDR(모니터링)</strong></p></td>
<td><p><strong>QoE(모니터링)</strong></p></td>
<td><p><strong>보관</strong></p></td>
</tr>
<tr class="even">
<td><p>사용자당 일일 데이터에 필요한 디스크 공간</p></td>
<td><p>49 KB</p></td>
<td><p>28 KB</p></td>
<td><p>57KB</p></td>
</tr>
</tbody>
</table>


Microsoft에서는 성능 테스트 시 모니터링 및 보관용 데이터베이스 서버에 다음 표의 하드웨어를 사용했습니다. 성능 테스트를 통해 각각 80,000명의 사용자가 포함된 두 프런트 엔드 풀의 데이터를 수집했습니다.

### 모니터링 및 보관 성능 테스트에 사용된 하드웨어

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th>하드웨어 구성 요소</th>
<th>권장</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>CPU</p></td>
<td><p>64비트 듀얼 프로세서, 헥사 코어, 2.26GHz 이상</p></td>
</tr>
<tr class="even">
<td><p>메모리</p></td>
<td><p>48GB</p></td>
</tr>
<tr class="odd">
<td><p>디스크</p></td>
<td><p>다음과 같이 구성된 10,000RPM 하드 디스크 드라이브 25개(각각 300GB 용량)</p>
<h3 id="section-3"> </h3>
<div>
<table>
<colgroup>
<col style="width: 33%" />
<col style="width: 33%" />
<col style="width: 33%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p><strong>드라이브</strong></p></td>
<td><p><strong>RAID 구성</strong></p></td>
<td><p><strong>디스크 수</strong></p></td>
</tr>
<tr class="even">
<td><p>단일 드라이브에 CDR, QoE 및 보관 데이터베이스 데이터 파일 저장</p></td>
<td><p>1+0</p></td>
<td><p>16</p></td>
</tr>
<tr class="odd">
<td><p>CDR 데이터베이스 로그 파일</p></td>
<td><p>1</p></td>
<td><p>2</p></td>
</tr>
<tr class="even">
<td><p>QoE 데이터베이스 로그 파일</p></td>
<td><p>1</p></td>
<td><p>2</p></td>
</tr>
<tr class="odd">
<td><p>보관 데이터베이스 로그 파일</p></td>
<td><p>1</p></td>
<td><p>2</p></td>
</tr>
</tbody>
</table>

</div></td>
</tr>
<tr class="even">
<td><p>네트워크</p></td>
<td><ul>
<li><p>1개의 이중 포트 네트워크 어댑터, 1Gbps 이상(2개 권장, 단일 MAC 주소와 단일 IP 주소를 사용하여 팀으로 구성해야 함)</p></li>
</ul></td>
</tr>
</tbody>
</table>


## 이 섹션의 내용

  - [Lync Server 2013의 음성 사용량 및 트래픽 예상](lync-server-2013-estimating-voice-usage-and-traffic.md)

  - [Lync Server 2013의 중재 서버 배포 지침](lync-server-2013-deployment-guidelines-for-mediation-server.md)

