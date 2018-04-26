---
title: 'Lync Server 2013: 통화 허용 제어 보고서'
TOCTitle: 통화 허용 제어 보고서
ms:assetid: ea4b0c9f-7f93-4b8a-b901-01e1636c44fb
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg615043(v=OCS.15)
ms:contentKeyID: 49305406
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Lync Server 2013의 통화 허용 제어 보고서

 

_**마지막으로 수정된 항목:** 2015-03-09_

통화 허용 제어 서비스 보고서는 통화 허용 제어 서비스에 의해 제한이 설정된 상태에서 수행된 피어 투 피어 및 회의 세션에 대한 정보를 제공합니다. Microsoft Lync Server 2010에 새로 도입된 통화 허용 제어 서비스는 관리자가 대역폭 제약 조건에 따라 통신 세션을 허용하거나 거부할 수 있는 방법을 제공합니다. 예를 들어 관리자는 음성 및 비디오 통화에 사용할 수 있는 대역폭 양에 대한 제한을 설정하는 정책을 만들 수 있습니다. 해당 대역폭 제한에 도달하면 동시 통화 중 하나가 종료되고 네트워크 리소스가 사용 가능 공간으로 확보될 때까지 새로운 음성 또는 비디오 전화를 걸 수 없습니다.

## 통화 허용 제어 서비스 보고서 액세스

통화 허용 제어 서비스 보고서는 모니터링 보고서 홈 페이지에서 액세스합니다. 통화 허용 제어 서비스 보고서에서 다음 보고서 중 하나로 드릴다운할 수 있습니다.

  - 전화 회의 정보 보고서 ? 이 보고서에 액세스하려면 전화 회의 세션에서 정보 메트릭을 클릭합니다.

  - 피어 투 피어 세션 정보 보고서 - 이 보고서에 액세스하려면 피어 투 피어 세션에 대한 정보 메트릭을 클릭합니다.

## 통화 허용 제어 서비스 보고서의 최적 사용

부족한 대역폭으로 인해 실패한 통화 목록을 가져오려면 통화 범주 드롭다운 목록에서 통화 허용 제어 서비스로 인해 거부된 통화를 선택합니다. 반환된 통화 중 대부분은 진단 ID가 5일 가능성이 높습니다.

대역폭이 부족하여 세션을 설정할 수 없습니다. PSTN 다시 라우팅을 시도하십시오.

이는 통화 허용 제어 서비스 제한으로 인해 VoIP 네트워크에서 통화할 수 없음을 나타냅니다.

## 필터

필터를 사용하면 여러 방식으로 반환된 데이터를 보거나 보다 세부적으로 대상화된 데이터 집합을 반환할 수 있습니다. 예를 들어 통화 허용 제어 보고서에서는 통화를 시작한 사용자 또는 통화를 받은 사용자에 따라 통화를 필터링할 수 있습니다. 또한 데이터의 그룹 지정 방식도 선택할 수 있습니다. 이 경우 통화는 시간, 일, 주 및 월별로 그룹이 지정됩니다.

다음 표에서는 통화 허용 제어 보고서에서 사용할 수 있는 필터를 보여 줍니다.

### 통화 허용 제어 보고서 필터

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
<p>2012/7/17 오후 1:00</p>
<p>시작 시간을 입력하지 않으면 보고서가 자동으로 지정된 날짜의 오전 12시부터 시작됩니다. 일별 데이터를 보려면 날짜만 입력합니다.</p>
<p>2012/7/17</p>
<p>주 또는 월별로 보려면 데이터를 보려는 해당 주 또는 월에 속하는 날짜를 입력합니다. 주 또는 월의 첫 번째 날짜를 입력할 필요가 없습니다.</p>
<p>13.07.12</p>
<p>주는 항상 일요일부터 토요일까지로 실행됩니다.</p></td>
</tr>
<tr class="even">
<td><p><strong>종료</strong></p></td>
<td><p>시간 범위의 종료 날짜/시간입니다. 시간별 데이터를 보려면 다음과 같이 종료 날짜 및 시간을 입력합니다.</p>
<p>2012/7/17 오후 1:00</p>
<p>종료 시간을 입력하지 않으면 보고서가 자동으로 지정된 날짜의 오전 12시에 종료됩니다. 일별 데이터를 보려면 날짜만 입력합니다.</p>
<p>2012/7/17</p>
<p>주 또는 월별로 보려면 데이터를 보려는 해당 주 또는 월에 속하는 날짜를 입력합니다. 주 또는 월의 첫 번째 날짜를 입력할 필요가 없습니다.</p>
<p>13.07.12</p>
<p>주는 항상 일요일부터 토요일까지로 실행됩니다.</p></td>
</tr>
<tr class="odd">
<td><p><strong>풀</strong></p></td>
<td><p>등록자 풀 또는 에지 서버의 FQDN(정규화된 도메인 이름)입니다. 개별 풀을 선택하거나 <strong>[모두]</strong> 를 클릭하여 모든 풀에 대한 데이터를 봅니다. 이 드롭다운 목록은 데이터베이스의 레코드에 따라 자동으로 채워집니다.</p></td>
</tr>
<tr class="even">
<td><p><strong>활동 유형</strong></p></td>
<td><p>활동 유형입니다. 다음 활동 중 하나를 선택합니다.</p>
<ul>
<li><p>[모두]</p></li>
<li><p>피어 투 피어</p></li>
<li><p>전화 회의</p></li>
</ul></td>
</tr>
<tr class="odd">
<td><p><strong>통화 범주</strong></p></td>
<td><p>통화에 CAC가 사용된 이유를 나타냅니다. 다음 중 하나를 선택합니다.</p>
<ul>
<li><p>[모두]</p></li>
<li><p>통화 허용 제어로 인해 거부된 통화</p></li>
<li><p>통화 허용 제어로 인해 PSTN을 통해 라우팅된 통화</p></li>
</ul></td>
</tr>
</tbody>
</table>


## 피어 투 피어 세션에 대한 메트릭

다음 표에서는 피어 투 피어 세션(즉, 참가자가 두 명뿐인 세션)에 대해 통화 허용 제어 보고서에 제공되는 정보를 보여 줍니다.

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
<td><p><strong>세부 정보</strong></p></td>
<td><p>아니요</p></td>
<td><p>이 항목을 클릭하면 보고서에 지정된 세션에 대한 피어 투 피어 세션 세부 정보 보고서가 표시됩니다.</p></td>
</tr>
<tr class="even">
<td><p><strong>시작 사용자</strong></p></td>
<td><p>예</p></td>
<td><p>세션을 시작한 사용자의 SIP 주소입니다.</p></td>
</tr>
<tr class="odd">
<td><p><strong>대상 사용자</strong></p></td>
<td><p>예</p></td>
<td><p>세션에 참가하도록 초대된 사용자의 SIP 주소입니다.</p></td>
</tr>
<tr class="even">
<td><p><strong>형식</strong></p></td>
<td><p>예</p></td>
<td><p>세션 중 사용된 통신 형식(예: 오디오 및 비디오)입니다.</p></td>
</tr>
<tr class="odd">
<td><p><strong>초대 시간</strong></p></td>
<td><p>예</p></td>
<td><p>보낸 사용자에게 최초 세션 초대가 전송된 날짜 및 시간입니다.</p></td>
</tr>
<tr class="even">
<td><p><strong>응답 시간</strong></p></td>
<td><p>예</p></td>
<td><p>초대 수락이 수신된 날짜 및 시간입니다.</p></td>
</tr>
<tr class="odd">
<td><p><strong>종료 시간</strong></p></td>
<td><p>예</p></td>
<td><p>세션이 종료된 날짜 및 시간입니다.</p></td>
</tr>
<tr class="even">
<td><p><strong>진단 ID</strong></p></td>
<td><p>예</p></td>
<td><p>오류 문제를 해결할 때 종종 유용한 정보를 제공하는 SIP 메시지에 연결된 고유 식별자(ms-diagnostics 헤더 형식)입니다. 진단 헤더는 선택 사항이며(이러한 헤더를 포함하지 않는 SIP 세션도 가능함) 진단 ID는 일부 유형의 문제가 발생한 세션에 대해서만 보고됩니다.</p></td>
</tr>
</tbody>
</table>


## 회의 세션에 대한 메트릭

다음 표에서는 회의 세션(즉, 참가자가 세 명 이상인 세션)에 대해 통화 허용 제어 보고서에 제공되는 정보를 보여 줍니다.

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
<td><p><strong>전화 회의 URI</strong></p></td>
<td><p>예</p></td>
<td><p>회의의 고유 식별자입니다. 이 항목을 클릭하면 보고서에 개별 회의 참가자가 표시됩니다.</p></td>
</tr>
<tr class="even">
<td><p><strong>이끌이</strong></p></td>
<td><p>예</p></td>
<td><p>회의를 구성한 사용자의 SIP 주소입니다.</p></td>
</tr>
<tr class="odd">
<td><p><strong>풀</strong></p></td>
<td><p>예</p></td>
<td><p>회의에 사용된 에지 서버입니다.</p></td>
</tr>
<tr class="even">
<td><p><strong>시작 시간</strong></p></td>
<td><p>예</p></td>
<td><p>회의가 시작된 날짜 및 시간입니다.</p></td>
</tr>
<tr class="odd">
<td><p><strong>종료 시간</strong></p></td>
<td><p>예</p></td>
<td><p>회의가 종료된 날짜 및 시간입니다.</p></td>
</tr>
</tbody>
</table>


## 개별 회의 참가자에 대한 메트릭

다음 표에서는 개별 회의 참가자에 대해 통화 허용 제어 보고서에 제공된 정보를 보여 줍니다.

### 개별 회의 참가자에 대한 메트릭

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
<td><p><strong>역할</strong></p></td>
<td><p>아니요</p></td>
<td><p>회의 참가자가 수행하는 역할(예: 발표자)입니다.</p></td>
</tr>
<tr class="even">
<td><p><strong>참가자</strong></p></td>
<td><p>아니요</p></td>
<td><p>회의 참가자의 SIP 주소입니다.</p></td>
</tr>
<tr class="odd">
<td><p><strong>연결</strong></p></td>
<td><p>아니요</p></td>
<td><p>참가자의 네트워크 연결(일반적으로 내부 발신 또는 외부 발신)입니다.</p></td>
</tr>
<tr class="even">
<td><p><strong>형식</strong></p></td>
<td><p>아니요</p></td>
<td><p>회의 유형(예: A/V 회의)입니다.</p></td>
</tr>
<tr class="odd">
<td><p><strong>참가 시간</strong></p></td>
<td><p>아니요</p></td>
<td><p>참가자가 회의에 참가한 날짜 및 시간입니다.</p></td>
</tr>
<tr class="even">
<td><p><strong>나간 시간</strong></p></td>
<td><p>아니요</p></td>
<td><p>참가자가 회의에서 나간 날짜 및 시간입니다.</p></td>
</tr>
<tr class="odd">
<td><p><strong>진단 ID</strong></p></td>
<td><p>아니요</p></td>
<td><p>오류 문제를 해결할 때 종종 유용한 정보를 제공하는 SIP 메시지에 연결된 고유 식별자(ms-diagnostics 헤더 형식)입니다. 진단 헤더는 선택 사항이며(이러한 헤더를 포함하지 않는 SIP 세션도 가능함) 진단 ID는 일부 유형의 문제가 발생한 세션에 대해서만 보고됩니다.</p></td>
</tr>
</tbody>
</table>

