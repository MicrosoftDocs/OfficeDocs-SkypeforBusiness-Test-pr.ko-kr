---
title: Lync Server 2013의 미디어 품질 메트릭 배포 보고서
TOCTitle: 미디어 품질 메트릭 배포 보고서
ms:assetid: d07996e6-b0a5-4ff8-9512-ab707762b4e2
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/JJ205262(v=OCS.15)
ms:contentKeyID: 49305103
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Lync Server 2013의 미디어 품질 메트릭 배포 보고서

 

_**마지막으로 수정된 항목:** 2015-03-09_

미디어 품질 메트릭 분포 보고서를 사용하면 지터, 패킷 손실 등 QoE(체감 품질)의 분포 값을 표시하는 그래프를 확인할 수 있습니다. 예를 들어 사용자가 총 10건의 전화 통화를 한 경우 해당 10건의 통화가 다음 왕복 시간을 보고합니다.


<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th>통화 횟수</th>
<th>왕복 시간(밀리초)</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>1</p></td>
<td><p>50</p></td>
</tr>
<tr class="even">
<td><p>2</p></td>
<td><p>50</p></td>
</tr>
<tr class="odd">
<td><p>3</p></td>
<td><p>50</p></td>
</tr>
<tr class="even">
<td><p>4</p></td>
<td><p>50</p></td>
</tr>
<tr class="odd">
<td><p>5</p></td>
<td><p>50</p></td>
</tr>
<tr class="even">
<td><p>6</p></td>
<td><p>50</p></td>
</tr>
<tr class="odd">
<td><p>7</p></td>
<td><p>50</p></td>
</tr>
<tr class="even">
<td><p>8</p></td>
<td><p>4550</p></td>
</tr>
<tr class="odd">
<td><p>9</p></td>
<td><p>50</p></td>
</tr>
<tr class="even">
<td><p>10</p></td>
<td><p>50</p></td>
</tr>
</tbody>
</table>


이러한 왕복 시간의 평균은 500밀리초(5000을 10으로 나눈 값)입니다. 500밀리초는 상당히 긴 왕복 시간이므로 심각한 네트워크 정체 문제가 있다고 생각할 것입니다. 왕복 시간이 길면 일번적으로 네트워크가 과부하 상태입니다.

물론, 실제로 통화의 90%에 대한 왕복 시간은 상당히 양호하며 단지 한 번의 불량 통화로 전체 결과가 왜곡되었습니다. 이처럼 평균 왕복 시간만 살펴본다면 아주 잘못된 결과에 도달할 수 있습니다.

미디어 품질 메트릭 분포 보고서를 사용하면 지정한 메트릭(예: 왕복 시간)에 대한 그래픽 분포를 볼 수 있으므로 잘못된 결론에 도달하는 것을 방지할 수 있습니다. 이러한 그래프를 살펴보면 9건은 매우 양호했고 1건만 매우 불량했다는 것을 쉽게 알 수 있습니다. 하지만 해당 1건의 통화를 더 심도 있게 조사하려 할 수 있습니다. 하지만 10건의 통화 중 9건은 매우 양호하므로 아직까지는 네트워크를 크게 변경할 이유가 없다는 것을 알 수 있습니다.

## 필터

필터를 사용하면 여러 방식으로 반환된 데이터를 보거나 보다 세부적으로 대상화된 데이터 집합을 반환할 수 있습니다. 다음 표에서는 미디어 품질 메트릭 분포 보고서에서 사용할 수 있는 필터를 보여 줍니다.

### 미디어 품질 메트릭 분포 보고서 필터

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th>이름</th>
<th>설명</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><strong>시작</strong></p></td>
<td><p>시간 범위의 시작 날짜/시간입니다. 시간별 데이터를 보려면 다음과 같이 시작 날짜 및 시간을 입력합니다.</p>
<p>7/7/2012 1:00 PM</p>
<p>시작 시간을 입력하지 않으면 보고서가 자동으로 지정된 날짜의 오전 12시부터 시작됩니다. 일별 데이터를 보려면 날짜만 입력합니다.</p>
<p>7/7/2012</p>
<p>주 또는 월별로 보려면 데이터를 보려는 해당 주 또는 월에 속하는 날짜를 입력합니다. 주 또는 월의 첫 번째 날짜를 입력할 필요가 없습니다.</p>
<p>7/3/2012</p>
<p>주는 항상 일요일부터 토요일까지로 실행됩니다.</p></td>
</tr>
<tr class="even">
<td><p><strong>종료</strong></p></td>
<td><p>시간 범위의 종료 날짜/시간입니다. 시간별 데이터를 보려면 다음과 같이 종료 날짜 및 시간을 입력합니다.</p>
<p>7/7/2012 1:00 PM</p>
<p>종료 시간을 입력하지 않으면 보고서가 자동으로 지정된 날짜의 오전 12시에 종료됩니다. 일별 데이터를 보려면 날짜만 입력합니다.</p>
<p>7/7/2012</p>
<p>주 또는 월별로 보려면 데이터를 보려는 해당 주 또는 월에 속하는 날짜를 입력합니다. 주 또는 월의 첫 번째 날짜를 입력할 필요가 없습니다.</p>
<p>7/3/2012</p>
<p>주는 항상 일요일부터 토요일까지로 실행됩니다.</p></td>
</tr>
<tr class="odd">
<td><p><strong>x축 최소값</strong></p></td>
<td><p>그래프의 X축에 표시할 최소값입니다.</p></td>
</tr>
<tr class="even">
<td><p><strong>x축 최대값</strong></p></td>
<td><p>그래프의 X축에 표시할 가장 높은 값입니다.</p></td>
</tr>
<tr class="odd">
<td><p><strong>액세스 유형</strong></p></td>
<td><p>통화가 시도되었을 때 클라이언트가 내부 네트워크 또는 외부 네트워크에 로그온되어 있는지를 나타냅니다. 다음 중 하나를 선택합니다.</p>
<ul>
<li><p>[모두]</p></li>
<li><p>내부</p></li>
<li><p>외부</p></li>
</ul></td>
</tr>
<tr class="even">
<td><p><strong>VPN</strong></p></td>
<td><p>통화가 시도되었을 때 외부 클라이언트가 VPN(가상 사설망) 연결을 사용 중이었는지를 나타냅니다. 다음 중 하나를 선택합니다.</p>
<ul>
<li><p>[모두]</p></li>
<li><p>VPN</p></li>
<li><p>VPN 외</p></li>
</ul></td>
</tr>
<tr class="odd">
<td><p><strong>네트워크 유형</strong></p></td>
<td><p>통화가 시도되었을 때 클라이언트가 연결된 네트워크의 유형을 나타냅니다. 다음 중 하나를 선택합니다.</p>
<ul>
<li><p>[모두]</p></li>
<li><p>유선</p></li>
<li><p>무선</p></li>
</ul></td>
</tr>
</tbody>
</table>

