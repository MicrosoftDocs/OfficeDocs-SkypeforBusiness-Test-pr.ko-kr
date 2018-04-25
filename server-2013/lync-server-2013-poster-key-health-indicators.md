---
title: Lync Server 2013의 주요 상태 표시기
TOCTitle: '포스터: 주요 상태 표시기'
ms:assetid: 8367dccf-adaa-4a0b-a4ed-bc9570cc5e24
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Dn593599(v=OCS.15)
ms:contentKeyID: 61084848
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Lync Server 2013의 주요 상태 표시기

 

_**마지막으로 수정된 항목:** 2015-03-09_

이 문서는 다운로드 센터에서 다운로드할 수 있는 [주요 상태 표시기: 정상적인 Lync Server 유지 관리를 위한 기본 사항](http://go.microsoft.com/fwlink/?linkid=391838) 포스터와 함께 제공됩니다.

![KHI 데이터를 사용하는 문제 해결에 대해 설명하는 포스터](images/Dn594589.b6fe82bd-d70f-4c1f-a812-b615ac5fa7d7(OCS.15).jpg "KHI 데이터를 사용하는 문제 해결에 대해 설명하는 포스터")

이 포스터를 통해 사용자 환경 문제를 표시하기 위한 임계값이 사용된 성능 카운터인 KHI(주요 상태 표시기)에 대해 알아볼 수 있습니다. Lync 사용자의 우수한 오디오 환경을 보장하는 데 중점을 둔 CQM(통화 품질 방법론)을 구현하는 단계는 일반적으로 KHI 데이터를 수집하는 것으로 시작됩니다.

CQM을 사용하는 방법에 대한 질문 사항은 cqmfeedback@microsoft.com으로 제출하면 됩니다.

이 포스터에서는 다음 사항에 대해 설명합니다.

  - 주요 상태 표시기란?

  - KHI 데이터를 수집하는 방법

  - 모든 서버 역할에 대한 문제 해결 순서

  - 용어집

  - 프런트 엔드 서버

  - 백엔드 SQL Server

  - 중재 서버

  - 에지 서버

## 주요 상태 표시기란?

주요 상태 표시기는 사용자 환경 문제를 표시하기 위한 임계값이 사용된 성능 카운터입니다. Lync 사용자의 우수한 오디오 환경을 보장하는 데 중점을 두는 CQM(통화 품질 방법론)을 구현하는 단계는 주로 KHI 데이터를 수집하는 것으로 시작됩니다.

KHI는 표준 Lync 모니터링 솔루션(예: System Center Operations Manager, 가상 트랜잭션, 모니터링 서버)을 대신하는 것이 아니라, 이러한 솔루션에 추가적으로 사용됩니다.

KHI 성능 카운터를 수집하고 네트워킹 가이드와 함께 제공되는 KHI 스프레드시트를 채워 Lync 배포의 서버 상태를 확인하는 데 도움이 되는 성과 기록표를 생성합니다. 스프레드시트가 채워지고 나면 환경 문제를 해결하기 위한 지침이 제공되고 다른 관계자에게는 추가 정보가 제공됩니다. KHI를 매월 평가하고 모든 배포의 진행 중인 작업 프로세스에 통합합니다.

[Lync Server 네트워킹 가이드](http://go.microsoft.com/fwlink/p/?linkid=390677)를 다운로드하여 KHI의 전체 목록을 확인하고 관련 스프레드시트를 가져오세요.

## KHI 데이터를 수집하는 방법

1.  각 Lync Server의 Lync Server 네트워킹 가이드와 함께 포함된 KHI 스크립트를 실행합니다. 그러면 성능 모니터 내부에 데이터 수집기가 만들어지고 KHI로 이름이 지정됩니다. 기본적으로 데이터는 15초마다 폴링됩니다.

2.  회사의 영업일이 시작되기 전에 각 Lync Server로 이동하여 KHI 데이터 수집기를 시작합니다.

3.  해당 날짜가 끝날 때 KHI 데이터 수집기를 중지하고 데이터를 중앙 위치에 복사합니다.

4.  성능 모니터를 사용하여 Lync Server 네트워킹 가이드 다운로드에 포함된 KHI 스프레드시트를 채운 후 권장 목표와 결과를 대조합니다.

## 모든 서버 역할에 대한 문제 해결 순서

Lync 구현의 각 서버에 대해 먼저 서버의 구성 요소 상태와 시스템 성능이 적절한 수준 이상인지 확인합니다. 이 과정을 거친 후에 전체 Lync 구현의 서버 역할에 관한 표시기를 확인해야 합니다.

먼저 모든 서버에 대한 KHI 성능 데이터를 수집합니다. 각 서버 역할(이 문서의 뒷부분에서 자세히 다룸)에 대해 기본 시스템 구성 요소가 권장 목표를 충족하는지 확인합니다. 권장 목표를 충족하지 않을 경우 Lync 구현의 서버 역할에 관한 메트릭을 확인하기 전에 시스템 성능 문제를 해결한 다음 KHI 데이터를 다시 수집하고 시스템 상태를 확인합니다. 모든 역할에 대한 구성 요소 상태는 다음과 같이 정의됩니다.

  - CPU 사용률 \< 80%

  - 평균 디스크 쓰기 속도 \< 10ms

  - 평균 디스크 읽기 속도 \< 10ms

  - 사용 가능한 메모리 \> 시스템 총 MB의 20%

  - 네트워크 큐 길이 \< 2

  - 삭제된 패킷 수(입력/출력) = 0

## 용어집

다음은 이 포스터에서 사용되는 용어 및 머리글자어입니다.

AS MCU = 응용 프로그램 공유 Multi-point Control Unit

AV MCU = 오디오/비디오 MCU

IM MCU = 메신저 대화 MCU

UCWA = 통합 통신 웹 API

AV 에지 = 에지를 통한 오디오/비디오 통과

AV Auth = 오디오/비디오 인증

SIP 스택 = Lync의 핵심 SIP 구현

데이터 프록시 = 에지 회의에 사용됨

LySS = Lync 저장소 서비스

## 프런트 엔드 서버

다음은 기본 구성 요소 상태에 추가적으로 프런트 엔드 서버에 대해 권장되는 KHI 목표입니다.


<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th>기능 영역</th>
<th>목표 메트릭</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>AS/AV/IM MCU</p></td>
<td><p>MCU 성능 상태 &lt; 2</p></td>
</tr>
<tr class="even">
<td><p>웹 구성 요소</p></td>
<td><p>메일 그룹 확장 AD 시간 초과 &lt; 0</p>
<p>ABWQ 오류 수 = 0</p>
<p>LIS 오류 수 = 0</p>
<p>인증 오류 수 &lt; 1/초</p>
<p>거부된 ASP.NET v4 요청 수 = 0</p></td>
</tr>
<tr class="odd">
<td><p>SIP 스택</p></td>
<td><p>들어오는 메시지 평균 처리 시간 &lt; 1초</p>
<p>손실된 들어오는 응답 수 &lt; 1/초, 손실된 들어오는 요청 수 &lt; 1/초</p>
<p>큐 대기 시간 &lt; 100ms</p>
<p>Sproc 대기 시간 &lt; 100ms</p>
<p>제한된 요청 수 = 0</p>
<p>인증 오류 수 &lt; 1/초</p>
<p>시간 초과된 들어오는 메시지 수 &lt; 2</p>
<p>평균 들어오는 메시지 보류 &lt; 1초</p>
<p>흐름 제어된 연결 수 &lt; 2</p>
<p>평균 나가는 큐 지연 &lt; 2초</p></td>
</tr>
<tr class="even">
<td><p>LySS</p></td>
<td><p>저장소 서비스 DB에서 사용되는 공간의 비율(%) &lt; 80</p>
<p>복제본 복제 오류 수 = 0</p>
<p>데이터 손실 이벤트 수 = 0</p></td>
</tr>
<tr class="odd">
<td><p>SQL</p></td>
<td><p>페이지 수명 예상 &gt; 300초</p>
<p>일괄 처리 요청/초 &lt; 2500</p></td>
</tr>
</tbody>
</table>


## 백엔드 SQL Server

다음은 기본 구성 요소 상태에 추가적으로 SQL Server에 대해 권장되는 KHI 목표입니다.


<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th>기능 영역</th>
<th>목표 메트릭</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>SQL</p></td>
<td><p>페이지 수명 예상 &gt; 300초</p>
<p>일괄 처리 요청/초 &lt; 2500</p></td>
</tr>
</tbody>
</table>


## 중재 서버

다음은 기본 구성 요소 상태에 추가적으로 중재 서버에 대해 권장되는 KHI 목표입니다.


<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th>기능 영역</th>
<th>목표 메트릭</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>중재 서버 서비스</p></td>
<td><p>통화 실패 로드 인덱스 = 0</p>
<p>프록시로 인해 실패한 통화 수 &lt; 10</p>
<p>게이트웨이로 인해 실패한 통화 수 &lt; 10</p>
<p>거부된 받거나 건 통화 수 = 0</p>
<p>누락된 미디어 후보 수 = 0</p>
<p>미디어 연결 확인 오류 수 = 0</p></td>
</tr>
</tbody>
</table>


## 에지 서버

다음은 기본 구성 요소 상태에 추가적으로 에지 서버에 대해 권장되는 KHI 목표입니다.


<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th>기능 영역</th>
<th>목표 메트릭</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>AV Auth</p></td>
<td><p>잘못된 요청 수 &lt; 20/초</p></td>
</tr>
<tr class="even">
<td><p>AV 에지</p></td>
<td><p>인증 오류 수 &lt; 20/초</p>
<p>할당 오류 수 &lt; 20/초</p>
<p>손실된 패킷 수 &lt; 300/초</p></td>
</tr>
<tr class="odd">
<td><p>데이터 프록시</p></td>
<td><p>제한된 서버 연결 수 &lt; 3</p>
<p>제한된 시스템 수 &lt; 1</p></td>
</tr>
<tr class="even">
<td><p>SIP 스택</p></td>
<td><p>손실된 제한을 초과하는 연결 수 &lt; 1</p>
<p>시간 초과된 전송 수 &lt; 10</p>
<p>흐름 제어된 연결 수 &lt; 100</p>
<p>손실된 들어오는 요청 수 &lt; 1/초</p>
<p>평균 메시지 처리 &lt; 3초</p></td>
</tr>
</tbody>
</table>


## 참고 항목

#### 기타 리소스

[Lync Server 네트워킹 가이드](http://go.microsoft.com/fwlink/p/?linkid=390677)  
[주요 상태 표시기: 정상적인 Lync Server 유지 관리를 위한 기본 사항](http://go.microsoft.com/fwlink/?linkid=391838)  
[Lync 통화 품질 방법론](http://go.microsoft.com/fwlink/?linkid=391841)

