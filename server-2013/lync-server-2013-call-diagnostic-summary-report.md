---
title: 'Lync Server 2013: 통화 진단 요약 보고서'
TOCTitle: 통화 진단 요약 보고서
ms:assetid: 9091de56-13e6-440e-9353-f57c10c906fe
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg615016(v=OCS.15)
ms:contentKeyID: 49304374
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Lync Server 2013의 통화 진단 요약 보고서

 

_**마지막으로 수정된 항목:** 2015-03-09_

통화 진단 요약 보고서에서는 실패한 피어 투 피어 세션 및 전화 회의 세션에 대한 전체 요약 정보를 제공합니다. 두 세션 유형 모두의 전체 실패율과 다음과 같은 세션 형식별 실패 정보가 표시됩니다.

  - 메신저 대화

  - 응용 프로그램 공유

  - 파일 전송

  - 오디오

  - 비디오

## 통화 진단 요약 보고서 액세스

통화 진단 요약 보고서는 모니터링 보고서 홈 페이지에서 액세스됩니다. 통화 진단 요약 보고서에서 피어 투 피어 세션 요약 섹션 아래에 있는 실패율 메트릭을 클릭하여 [Lync Server 2013의 피어 투 피어 활동 진단 보고서](lync-server-2013-peer-to-peer-activity-diagnostic-report.md)에 액세스할 수 있습니다. 또한 다음과 같은 전화 회의 메트릭을 클릭하여 [Lync Server 2013의 회의 진단 보고서](lync-server-2013-conference-diagnostic-report.md)에 액세스할 수 있습니다.

  - 전체 세션 실패율

  - 회의 센터 실패율

  - MCU 실패율

## 통화 진단 요약 보고서의 효과적인 활용

통화 진단 요약 보고서에는 Microsoft Lync Server 2013에 사용되는 다양한 형식의 실패율을 비교하는 그래프가 포함됩니다. 이러한 그래프의 열은 실제로 핫링크입니다. 예를 들어 피어 투 피어 세션의 인스턴트 메시징 열을 클릭하면 통화 진단 요약 보고서에 포함된 모든 인스턴트 메시징 세션에 대한 자세한 정보를 제공하는 보고서인 [Lync Server 2013의 피어 투 피어 활동 진단 보고서](lync-server-2013-peer-to-peer-activity-diagnostic-report.md)로 드릴다운됩니다.

## 필터

필터를 사용하면 여러 방식으로 반환된 데이터를 보거나 보다 세부적으로 대상화된 데이터 집합을 반환할 수 있습니다. 예를 들어 통화 진단 요약 보고서에서는 세션에 사용된 등록자 풀 또는 에지 서버와 같은 항목에 필터를 적용할 수 있습니다. 또한 데이터의 그룹 지정 방식도 선택할 수 있습니다. 이 경우 통화는 시간, 일, 주 및 월별로 그룹이 지정됩니다.

다음 표에서는 통화 진단 요약 보고서에서 사용할 수 있는 필터를 보여 줍니다.

### 통화 진단 요약 보고서 필터

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
<p>7/7/12</p>
<p>주 또는 월별로 보려면 데이터를 보려는 해당 주 또는 월에 속하는 날짜를 입력합니다. 주 또는 월의 첫 번째 날짜를 입력할 필요가 없습니다.</p>
<p>3/7/12</p>
<p>주는 항상 일요일부터 토요일까지로 실행됩니다.</p></td>
</tr>
<tr class="even">
<td><p><strong>종료</strong></p></td>
<td><p>시간 범위의 종료 날짜/시간입니다. 시간별 데이터를 보려면 다음과 같이 종료 날짜 및 시간을 입력합니다.</p>
<p>7/7/2012 1:00 PM</p>
<p>종료 시간을 입력하지 않으면 보고서가 자동으로 지정된 날짜의 오전 12시에 종료됩니다. 일별 데이터를 보려면 날짜만 입력합니다.</p>
<p>7/7/12</p>
<p>주 또는 월별로 보려면 데이터를 보려는 해당 주 또는 월에 속하는 날짜를 입력합니다. 주 또는 월의 첫 번째 날짜를 입력할 필요가 없습니다.</p>
<p>3/7/12</p>
<p>주는 항상 일요일부터 토요일까지로 실행됩니다.</p></td>
</tr>
<tr class="odd">
<td><p><strong>간격</strong></p></td>
<td><p>시간 간격입니다. 다음 중 하나를 선택합니다.</p>
<ul>
<li><p>시간별(최대 25시간 표시 가능)</p></li>
<li><p>일별(최대 31일 표시 가능)</p></li>
<li><p>주별(최대 12주 표시 가능)</p></li>
<li><p>월별(최대 12개월 표시 가능)</p></li>
</ul>
<p>시작 및 종료 날짜가 선택한 간격에 허용되는 최대 값 수를 초과하면 시작 날짜로부터 최대 값 수만 표시됩니다. 예를 들어 일별 간격을 선택하는 경우 시작 날짜가 2012/8/7이고 종료 날짜가 2012/9/28이면 2012/8/7 오전 12:00부터 2012/9/7 오전 12:00까지 총 31일의 데이터만 표시됩니다.</p></td>
</tr>
<tr class="even">
<td><p><strong>풀</strong></p></td>
<td><p>등록자 풀 또는 에지 서버의 FQDN(정규화된 도메인 이름)입니다. 개별 풀을 선택하거나 <strong>[모두]</strong> 를 클릭하여 모든 풀에 대한 데이터를 봅니다. 이 드롭다운 목록은 데이터베이스의 레코드에 따라 자동으로 채워집니다.</p></td>
</tr>
</tbody>
</table>


## 피어 투 피어 세션에 대한 메트릭

다음 표에서는 피어 투 피어 세션(즉, 참가자가 두 명뿐인 세션)에 대해 통화 진단 요약 보고서에 제공되는 정보를 보여 줍니다.

### 피어 투 피어 세션에 대한 메트릭

<table>
<colgroup>
<col style="width: 33%" />
<col style="width: 33%" />
<col style="width: 33%" />
</colgroup>
<thead>
<tr class="header">
<th>이름</th>
<th>이 항목에 대한 정렬 가능 여부</th>
<th>설명</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><strong>총 세션</strong></p></td>
<td><p>아니요</p></td>
<td><p>수행된 총 피어 투 피어 세션 수입니다.</p></td>
</tr>
<tr class="even">
<td><p><strong>실패율</strong></p></td>
<td><p>아니요</p></td>
<td><p>실패한 피어 투 피어 세션의 비율입니다. 이 항목을 클릭하면 보고서에 실패한 피어 투 피어 세션에 대한 보다 자세한 정보가 표시되는 피어 투 피어 활동 진단 보고서가 표시됩니다.</p></td>
</tr>
</tbody>
</table>


## 회의 세션에 대한 메트릭

다음 표에서는 회의 세션(즉, 참가자가 세 명 이상인 세션)에 대해 통화 진단 보고서에 제공되는 정보를 보여 줍니다.

### 회의 세션에 대한 메트릭

<table>
<colgroup>
<col style="width: 33%" />
<col style="width: 33%" />
<col style="width: 33%" />
</colgroup>
<thead>
<tr class="header">
<th>이름</th>
<th>이 항목에 대한 정렬 가능 여부</th>
<th>설명</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><strong>총 전화 회의</strong></p></td>
<td><p>아니요</p></td>
<td><p>수행된 총 회의 수입니다.</p></td>
</tr>
<tr class="even">
<td><p><strong>총 전화 회의 세션</strong></p></td>
<td><p>아니요</p></td>
<td><p>수행된 총 전화 회의 수입니다.</p></td>
</tr>
<tr class="odd">
<td><p><strong>전체 세션 실패율</strong></p></td>
<td><p>아니요</p></td>
<td><p>실패한 총 전화 회의 세션의 비율입니다.</p></td>
</tr>
<tr class="even">
<td><p><strong>회의 센터 세션</strong></p></td>
<td><p>아니요</p></td>
<td><p>실패한 총 회의 센터 기반 전화 회의 세션 수입니다.</p></td>
</tr>
<tr class="odd">
<td><p><strong>회의 센터 실패율</strong></p></td>
<td><p>아니요</p></td>
<td><p>실패한 총 회의 센터 기반 전화 회의 세션의 비율입니다.</p></td>
</tr>
<tr class="even">
<td><p><strong>MCU 세션</strong></p></td>
<td><p>아니요</p></td>
<td><p>실패한 총 회의 서버 기반(이전의 MCU(Multipoint Control Unit)) 전화 회의 수입니다.</p></td>
</tr>
<tr class="odd">
<td><p><strong>MCU 실패율</strong></p></td>
<td><p>아니요</p></td>
<td><p>실패한 회의 서버 기반(이전의 MCU(Multipoint Control Unit)) 전화 회의 비율입니다.</p></td>
</tr>
</tbody>
</table>

