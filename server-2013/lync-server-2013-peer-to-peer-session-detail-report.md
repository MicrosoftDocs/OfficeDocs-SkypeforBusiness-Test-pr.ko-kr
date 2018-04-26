---
title: 'Lync Server 2013: 피어 투 피어 세션 정보 보고서'
TOCTitle: 피어 투 피어 세션 정보 보고서
ms:assetid: 6be1d676-68f7-4a53-a72a-de73296c5571
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg558659(v=OCS.15)
ms:contentKeyID: 49303938
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Lync Server 2013의 피어 투 피어 세션 정보 보고서

 

_**마지막으로 수정된 항목:** 2015-03-09_

피어 투 피어 세션 세부 정보 보고서는 피어 투 피어 세션에 대한 세부 정보를 반환합니다. 예를 들어 인스턴트 메시징 세션을 선택한 경우에는 보고서가 세션에서 두 사용자가 각각 전송한 메시지 수를 알려줍니다.

## 피어 투 피어 세션 세부 정보 보고서 액세스

피어 투 피어 세션 세부 정보 보고서는 다음과 같은 보고서에서 액세스할 수 있습니다(이러한 모든 보고서는 모니터링 보고서 홈 페이지에서 모두 액세스할 수 있음).

  - IP 전화 인벤토리 보고서

  - 사용자 작업 보고서

  - 통화 허용 제어 보고서

  - 오류 목록 보고서

피어 투 피어 세션 세부 정보 보고서에서는 진단 보고서(세부 정보) 메트릭을 클릭하여 [Lync Server 2013의 진단 보고서](lync-server-2013-diagnostic-report.md)에 액세스할 수 있습니다. 또한 다음 두 메트릭 중 하나를 클릭하여 최상위 오류 보고서에 액세스할 수도 있습니다.

  - 응답

  - 진단 ID

## 피어 투 피어 세션 세부 정보 보고서 활용

피어 투 피어 세션 세부 정보 보고서에는 대부분 시스템 관리자에게 익숙하지 않을 수 있는 여러 개의 메트릭이 포함됩니다. 하지만 메트릭 레이블 위로 마우스를 가져가면 해당 메트릭에 대한 간단한 설명을 제공하는 도구 설명을 볼 수 있습니다.

특정 보고서에 표시되는 실제 메트릭은 선택한 피어 투 피어 세션의 유형에 따라 달라집니다. 오디오/비디오 세션은 인스턴트 메시징 세션과 다른 메트릭 집합을 보고합니다.

또한 응답 코드 및 진단 ID 메트릭 위로 마우스를 가져가면 해당 값에 대한 설명을 볼 수 있습니다.

## 필터

없음. 피어 투 피어 세션 세부 정보 보고서는 필터링할 수 없습니다.

## 세션 정보 메트릭

다음 표에서는 각 세션에 대해 피어 투 피어 세션 정보 보고서에 제공되는 정보를 보여 줍니다.

### 세션 정보 메트릭

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
<td><p><strong>풀 FQDN</strong></p></td>
<td><p>세션에 포함된 등록자 풀 또는 에지 서버의 FQDN(정규화된 도메인 이름)입니다.</p></td>
</tr>
<tr class="even">
<td><p><strong>초대 시간</strong></p></td>
<td><p>세션 초대가 원래 전송된 날짜 및 시간입니다.</p></td>
</tr>
<tr class="odd">
<td><p><strong>응답 시간</strong></p></td>
<td><p>초대 수락이 수신된 날짜 및 시간입니다.</p></td>
</tr>
<tr class="even">
<td><p><strong>시작 사용자</strong></p></td>
<td><p>세션을 시작한 사용자의 SIP 주소입니다.</p></td>
</tr>
<tr class="odd">
<td><p><strong>출처 사용자 에이전트</strong></p></td>
<td><p>세션을 시작한 사용자의 끝점에 사용된 소프트웨어입니다.</p></td>
</tr>
<tr class="even">
<td><p><strong>출처는 내부 사용자입니다.</strong></p></td>
<td><p>세션을 시작한 사용자가 내부 네트워크에 로그온되었는지 여부를 나타냅니다.</p></td>
</tr>
<tr class="odd">
<td><p><strong>출처는 일반 전화기와 통합된 사용자임</strong></p></td>
<td><p>세션을 시작한 사용자가 사용한 끝점이 해당 사용자의 데스크톱 전화와 통합되어 있는지를 나타냅니다.</p></td>
</tr>
<tr class="even">
<td><p><strong>세션 우선 순위</strong></p></td>
<td><p>세션에 지정된 우선 순위입니다. 유효한 우선 순위는 알 수 없음, 일반, 보통, 긴급 및 응급의 순서입니다.</p></td>
</tr>
<tr class="odd">
<td><p><strong>응답 코드</strong></p></td>
<td><p>세션이 실패했을 때 전송된 SIP 응답 코드입니다.</p></td>
</tr>
<tr class="even">
<td><p><strong>프런트 엔드</strong></p></td>
<td><p>회의에 사용된 프런트 엔드 서버의 이름입니다.</p></td>
</tr>
<tr class="odd">
<td><p><strong>캡처 시간</strong></p></td>
<td><p>세션 정보가 기록된 날짜 및 시간입니다.</p></td>
</tr>
<tr class="even">
<td><p><strong>종료 시간</strong></p></td>
<td><p>세션이 종료된 날짜 및 시간입니다.</p></td>
</tr>
<tr class="odd">
<td><p><strong>대상 사용자</strong></p></td>
<td><p>세션에 초대된 사용자의 SIP 주소입니다.</p></td>
</tr>
<tr class="even">
<td><p><strong>대상 사용자 에이전트</strong></p></td>
<td><p>세션에 초대된 사용자의 끝점에 사용된 소프트웨어입니다.</p></td>
</tr>
<tr class="odd">
<td><p><strong>대상은 내부 사용자임</strong></p></td>
<td><p>세션에 초대된 사용자가 내부 네트워크에 로그온되었는지 여부를 나타냅니다.</p></td>
</tr>
<tr class="even">
<td><p><strong>대상은 일반 전화기와 통합된 사용자임</strong></p></td>
<td><p>세션에 초대된 사용자가 사용한 끝점이 해당 사용자의 데스크톱 전화와 통합되어 있는지를 나타냅니다.</p></td>
</tr>
<tr class="odd">
<td><p><strong>다시 시도된 세션임</strong></p></td>
<td><p>세션이 이전에 실패한 세션에 대한 다시 시도인지 여부를 나타냅니다.</p></td>
</tr>
<tr class="even">
<td><p><strong>진단 ID</strong></p></td>
<td><p>오류 문제를 해결할 때 종종 유용한 정보를 제공하는 SIP 메시지에 연결된 고유 식별자(ms-diagnostics 헤더 형식)입니다. 해당 ID에 대한 추가 정보를 보려면 ID 번호 위에 마우스를 둡니다.</p></td>
</tr>
</tbody>
</table>


## 형식에 대한 메트릭

다음 표에서는 각 세션 형식에 대해 피어 투 피어 세션 정보 보고서에 제공되는 정보를 보여 줍니다.

### 형식에 대한 메트릭

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
<td><p><strong>형식</strong></p></td>
<td><p>아니요</p></td>
<td><p>세션에 사용된 형식입니다. 예: IM(인스턴트 메시징) 또는 파일 전송</p></td>
</tr>
<tr class="even">
<td><p><strong>보낸 사용자 메시지</strong></p></td>
<td><p>아니요</p></td>
<td><p>세션을 시작한 사용자가 보낸 메시지 수입니다.</p></td>
</tr>
<tr class="odd">
<td><p><strong>대상 사용자 메시지</strong></p></td>
<td><p>아니요</p></td>
<td><p>세션에 참가하도록 초대된 사용자가 보낸 메시지 수입니다.</p></td>
</tr>
</tbody>
</table>


## 미디어 보고서에 대한 메트릭

다음 표에서는 각 진단 보고서에 대해 피어 투 피어 세션 정보 보고서에 제공되는 정보를 보여 줍니다.

### 미디어 보고서에 대한 메트릭

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
<td><p>이 항목을 클릭하면 보고서에 세션에 대한 진단 보고서가 표시됩니다.</p></td>
</tr>
<tr class="even">
<td><p><strong>보고 시간</strong></p></td>
<td><p>아니요</p></td>
<td><p>보고서가 기록된 날짜 및 시간입니다.</p></td>
</tr>
<tr class="odd">
<td><p><strong>요청</strong></p></td>
<td><p>아니요</p></td>
<td><p>SIP 요청 유형입니다. 예: INVITE 또는 BYE</p></td>
</tr>
<tr class="even">
<td><p><strong>진단 ID</strong></p></td>
<td><p>아니요</p></td>
<td><p>오류 문제를 해결할 때 종종 유용한 정보를 제공하는 SIP 메시지에 연결된 고유 식별자(ms-diagnostics 헤더 형식)입니다.</p></td>
</tr>
<tr class="odd">
<td><p><strong>콘텐츠 형식</strong></p></td>
<td><p>아니요</p></td>
<td><p>회의에 사용된 미디어 콘텐츠 형식입니다. 예를 들어 공통 콘텐츠 형식은 Application/sdp입니다. SDP(Session Description Protocol)는 세션 알림, 세션 초대 및 멀티 미디어 세션 초대의 다른 형식에 사용된 표준 인터넷 프로토콜입니다.</p></td>
</tr>
<tr class="even">
<td><p><strong>보고서 작성자</strong></p></td>
<td><p>아니요</p></td>
<td><p>문제를 보고한 컴퓨터(즉, 클라이언트 또는 서버)입니다.</p></td>
</tr>
</tbody>
</table>

