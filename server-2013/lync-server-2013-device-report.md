---
title: 'Lync Server 2013: 장치 보고서'
TOCTitle: 장치 보고서
ms:assetid: f42e4d60-699b-4870-8bb5-13b51bb6eb2b
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg615049(v=OCS.15)
ms:contentKeyID: 49305524
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Lync Server 2013의 장치 보고서

 

_**마지막으로 수정된 항목:** 2015-03-09_

마이크 및 스피커 보고서라는 제목보다 장치 보고서가 더 나을 수 있습니다. 그 이유는 장치 보고서가 통화에 사용된 마이크와 스피커로 그룹화된 통화 관련 메트릭(예: 불량 통화율, 에코 및 음성 스위치 시간)을 가져오기 때문입니다. IP 전화(일반적으로 "장치"라고 함)에 관심이 있는 경우 이 제목 대신에 [Lync Server 2013의 IP 전화 인벤토리 보고서](lync-server-2013-ip-phone-inventory-report.md)를 사용하십시오.

장치 보고서는 관리자가 특정 종류의 장치에서 다른 장치보다 더 많은 양의 불량 통화가 발생하는지 여부를 확인하는 데 매우 유용합니다. 따라서 새 장치를 구입해야 하거나 기존 장치를 교체해야 할 시점에 내려야 하는 결정에 영향을 줄 수 있습니다.

기본적으로 장치 보고서에 표시된 정보는 통화에 사용된 마이크(캡처 장치)와 스피커/헤드셋(렌더링 장치)을 기반으로 합니다. 예를 들어 다음과 같은 캡처 장치와 렌더링 장치를 사용하는 여러 사용자가 있다고 가정해 보겠습니다.

  - 캡처 장치 -- 마이크(SoundMAX Integrated Digital HD Audio)

  - 렌더링 장치 -- 헤드셋 이어폰(Microsoft LifeChat LX-3000)

이들 사용자가 전화를 건 통화 수가 총 254통이었다면 보고서에는 다음과 같이 항목이 표시됩니다.


<table>
<colgroup>
<col style="width: 33%" />
<col style="width: 33%" />
<col style="width: 33%" />
</colgroup>
<thead>
<tr class="header">
<th>캡처 장치</th>
<th>렌더링 장치</th>
<th>통화량</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>마이크(SoundMAX Integrated Digital HD Audio)</p></td>
<td><p>헤드셋 이어폰(Microsoft LifeChat LX-3000)</p></td>
<td><p>254</p></td>
</tr>
</tbody>
</table>


이번에는 동일한 캡처 장치와 서로 다른 렌더링 장치를 사용하는 여러 사용자가 있다고 가정해 보겠습니다. 이 경우 보고서에 두 번째 줄에 고유한 캡처 장치 및 렌더링 장치 조합에 대한 정보가 표시됩니다.


<table>
<colgroup>
<col style="width: 33%" />
<col style="width: 33%" />
<col style="width: 33%" />
</colgroup>
<thead>
<tr class="header">
<th>캡처 장치</th>
<th>렌더링 장치</th>
<th>통화량</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>마이크(SoundMAX Integrated Digital HD Audio)</p></td>
<td><p>헤드셋 이어폰(Microsoft LifeChat LX-3000)</p></td>
<td><p>254</p></td>
</tr>
<tr class="even">
<td><p>마이크(SoundMAX Integrated Digital HD Audio)</p></td>
<td><p>스피커(SoundMAX Integrated Digital HD Audio)</p></td>
<td><p>319</p></td>
</tr>
</tbody>
</table>


지정된 장치에 대한 총 합계를 볼 경우(예: 사용된 렌더링 장치와 상관없이 SoundMAX 캡처 장치에 대해) 장치 유형 드롭다운 목록에서 해당 옵션(캡처 장치 또는 렌더링 장치)을 선택합니다. 이 예제에서 캡처 장치를 선택할 다음과 같은 출력에 제공됩니다.


<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th>캡처 장치</th>
<th>통화량</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>마이크(SoundMAX Integrated Digital HD Audio)</p></td>
<td><p>573</p></td>
</tr>
</tbody>
</table>


## 장치 보고서 액세스

장치 보고서는 일반적으로 모니터링 보고서 홈 페이지에서 액세스합니다. 하지만 [Lync Server 2013의 통화 정보 보고서](lync-server-2013-call-detail-report.md)를 보고 있는 경우에는 다음 메트릭 중 하나를 클릭하여 특정 장치에 대한 장치 보고서로 드릴다운할 수 있습니다.

  - 캡처 장치

  - 렌더링 장치

장치 보고서에서 다음 메트릭 중 하나를 클릭하여 [Lync Server 2013의 통화 목록 보고서](lync-server-2013-call-list-report.md)로 드릴다운할 수 있습니다.

  - 통화량

  - 불량 통화율

## 장치 보고서의 효과적인 사용

장치 이름에는 장치 보고서에 대한 자세한 설명이 있습니다. 예를 들어 다음 캡처 장치가 있다고 가정하겠습니다.

  - Aastra 3002 마이크(2- Aastra 3002)

  - Aastra 3002 마이크(3- Aastra 3002)

  - Aastra 3002 마이크(Aastra 3002)

  - Aastra 6725ip

  - Aastra 6725ip 마이크(10- Aastra 6725ip)

  - Aastra 6725ip 마이크(10- Aastra 6725ip)-V0

  - Aastra 6725ip 마이크(2- Aastra 6725ip)

  - Aastra 6725ip 마이크(3- Aastra 6725ip)

  - Aastra 6725ip 마이크(4- Aastra 6725ip)

  - Aastra 6725ip 마이크(5- Aastra 6725ip)

  - Aastra 6725ip 마이크(6- Aastra 6725ip)

  - Aastra 6725ip 마이크(7- Aastra 6725ip)

  - Aastra 6725ip 마이크(9- Aastra 6725ip)

  - Aastra 6725ip 마이크(9- Aastra 6725ip)-V0

  - Aastra 6725ip 마이크(Aastra 6725ip)

  - Aastra 6725ip 마이크(Aastra 6725ip)-V0

  - Aastra 6725ip 마이크(USB 오디오 장치)

  - Aastra 6725ip 마이크(USB 오디오 장치)-V0


> [!NOTE]
> Lync Server 2013의 지역화 버전을 실행 중인 경우 캡처 장치 이름이 동일하지 않을 수 있습니다. Aastra 6725ip 마이크(Aastra 6725ip)-V0라는 한국어 이름은 프랑스어나 스페인으로는 다른 이름일 수 있습니다.



때로는 이러한 상세 설명이 필요하겠지만, 그 밖의 경우에는 모델 번호와 상관없이 Aastra 마이크를 사용하는 통화 수에만 관심이 있을 수 있습니다. 이와 같은 정보를 얻는 한 가지 방법은 장치 보고서 데이터를 Microsoft Excel로 내보내고 나서 이 데이터를 쉼표로 구분된 값 파일(예: C:\\Data\\Devices\_Report.csv)로 저장하는 것입니다. 그러면 이와 비슷한 명령 집합을 사용하여 .CSV 파일을 Windows PowerShell로 가져오고 Aastra 캡처 장치를 사용하여 전화를 건 총 통화 수를 보고할 수 있습니다.

    $devices = Import-Csv "C:\Data\Device_Report.csv
    $sum = $devices | Where-Object {$_."Capture device" -match "Aastra"}
    $sum | foreach-object {[Int]$x = [Int]$x + [Int]$_."call volume"}
    $x

그러면 Aastra 캡처 장치를 사용하여 전화를 건 총 통화 수를 나타내는 단일 값이 반환됩니다. 예를 들면 다음과 같습니다.

    384

## 필터

필터를 사용하면 여러 방식으로 반환된 데이터를 보거나 보다 세부적으로 대상화된 데이터 집합을 반환할 수 있습니다. 예를 들어 장치 보고서에서는 통화 유형(즉 클라이언트 연결 통화), 전화 회의 또는 PSTN(공중 전화망 통화)와 같은 항목에 대해 필터링을 수행할 수 있습니다. 또한 데이터의 그룹 지정 방식도 선택할 수 있습니다. 이 경우 장치는 시간, 일, 주 또는 월별로 그룹화됩니다.

다음 표에서는 장치 보고서에 사용할 수 있는 필터를 보여 줍니다.

### 장치 보고서 필터

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
<p>07.07.12</p>
<p>주 또는 월별로 보려면 데이터를 보려는 해당 주 또는 월에 속하는 날짜를 입력합니다. 주 또는 월의 첫 번째 날짜를 입력할 필요가 없습니다.</p>
<p>03.07.12</p>
<p>주는 항상 일요일부터 토요일까지로 실행됩니다.</p></td>
</tr>
<tr class="even">
<td><p><strong>종료</strong></p></td>
<td><p>시간 범위의 종료 날짜/시간입니다. 시간별 데이터를 보려면 다음과 같이 종료 날짜 및 시간을 입력합니다.</p>
<p>7/7/2012 1:00 PM</p>
<p>종료 시간을 입력하지 않으면 보고서가 자동으로 지정된 날짜의 오전 12시에 종료됩니다. 일별 데이터를 보려면 날짜만 입력합니다.</p>
<p>07.07.12</p>
<p>주 또는 월별로 보려면 데이터를 보려는 해당 주 또는 월에 속하는 날짜를 입력합니다. 주 또는 월의 첫 번째 날짜를 입력할 필요가 없습니다.</p>
<p>03.07.12</p>
<p>주는 항상 일요일부터 토요일까지로 실행됩니다.</p></td>
</tr>
<tr class="odd">
<td><p><strong>음성 스위치 원인</strong></p></td>
<td><p>소리 울림 방지를 위해 반이중 모드로 통화를 설정해야 하는 이유입니다. 반이중 모드에서 통신은 무전기를 이용한 통신에서와 마찬가지로 한 번에 한쪽 방향으로만 전달됩니다. 다음 중 하나를 선택합니다.</p>
<dl>
<dt><span></span></dt>
<dd><p>[모두]</p>
</dd>
<dt><span></span></dt>
<dd><p>없음</p>
</dd>
<dt><span></span></dt>
<dd><p>잘못된 타임스탬프</p>
</dd>
<dt><span></span></dt>
<dd><p>에코</p>
</dd>
<dt><span></span></dt>
<dd><p>DNLP(dynamic nonlinear processor)</p>
</dd>
<dt><span></span></dt>
<dd><p>낮은 복잡성</p>
</dd>
<dt><span></span></dt>
<dd><p>잘못된 장치 상태</p>
</dd>
<dt><span></span></dt>
<dd><p>Post-AEC 에코(음향 반향 취소)</p>
</dd>
</dl></td>
</tr>
<tr class="even">
<td><p><strong>에코 원인</strong></p></td>
<td><p>통화에서 적정 수준 이상의 에코가 발견되는 이유입니다. 원격 통신에서 에코는 우물 아래쪽으로 큰 소리를 냈을 때 다시 들려오는 것과 동일한 현상인 소리의 반향을 의미합니다. 다음 중 하나를 선택합니다.</p>
<dl>
<dt><span></span></dt>
<dd><p>[모두]</p>
</dd>
<dt><span></span></dt>
<dd><p>없음</p>
</dd>
<dt><span></span></dt>
<dd><p>잘못된 타임스탬프</p>
</dd>
<dt><span></span></dt>
<dd><p>Post-AEC 에코(음향 반향 취소)</p>
</dd>
<dt><span></span></dt>
<dd><p>ANLP(adaptive nonlinear processor)</p>
</dd>
<dt><span></span></dt>
<dd><p>DNLP(dynamic nonlinear processor)</p>
</dd>
<dt><span></span></dt>
<dd><p>마이크 클리핑</p>
</dd>
</dl></td>
</tr>
<tr class="odd">
<td><p><strong>통화 유형</strong></p></td>
<td><p>수행된 통화의 유형을 나타냅니다. 다음 중 하나를 선택합니다.</p>
<dl>
<dt><span></span></dt>
<dd><p>[모두]</p>
</dd>
<dt><span></span></dt>
<dd><p>클라이언트 통화</p>
</dd>
<dt><span></span></dt>
<dd><p>PSTN 통화</p>
</dd>
<dt><span></span></dt>
<dd><p>전화 회의</p>
</dd>
</dl></td>
</tr>
<tr class="even">
<td><p><strong>액세스 유형</strong></p></td>
<td><p>통화가 시도되었을 때 클라이언트가 내부 네트워크 또는 외부 네트워크에 로그온되어 있는지를 나타냅니다. 다음 중 하나를 선택합니다.</p>
<dl>
<dt><span></span></dt>
<dd><p>[모두]</p>
</dd>
<dt><span></span></dt>
<dd><p>내부</p>
</dd>
<dt><span></span></dt>
<dd><p>외부</p>
</dd>
</dl></td>
</tr>
<tr class="odd">
<td><p><strong>네트워크 유형</strong></p></td>
<td><p>통화가 시도되었을 때 클라이언트가 연결된 네트워크의 유형을 나타냅니다. 다음 중 하나를 선택합니다.</p>
<dl>
<dt><span></span></dt>
<dd><p>[모두]</p>
</dd>
<dt><span></span></dt>
<dd><p>유선</p>
</dd>
<dt><span></span></dt>
<dd><p>무선</p>
</dd>
</dl></td>
</tr>
<tr class="even">
<td><p><strong>VPN</strong></p></td>
<td><p>통화가 시도되었을 때 외부 클라이언트가 VPN(가상 사설망) 연결을 사용 중이었는지를 나타냅니다. 다음 중 하나를 선택합니다.</p>
<dl>
<dt><span></span></dt>
<dd><p>[모두]</p>
</dd>
<dt><span></span></dt>
<dd><p>VPN</p>
</dd>
<dt><span></span></dt>
<dd><p>VPN 외</p>
</dd>
</dl></td>
</tr>
<tr class="odd">
<td><p><strong>장치 유형</strong></p></td>
<td><p>장치 유형을 나타냅니다. 다음 중 하나를 선택합니다.</p>
<dl>
<dt><span></span></dt>
<dd><p>캡처 장치</p>
</dd>
<dt><span></span></dt>
<dd><p>렌더링 장치</p>
</dd>
<dt><span></span></dt>
<dd><p>캡처/렌더링 장치 쌍</p>
</dd>
</dl></td>
</tr>
<tr class="even">
<td><p><strong>장치 이름</strong></p></td>
<td><p>캡처 또는 렌더링 장치의 이름입니다. 전체 장치 이름 또는 장치 이름 중 일부를 입력할 수 있습니다. 예를 들어 마이크 장치(Microsoft LifeCam VX-1000.)를 찾으려면 다음과 같이 전체 장치 이름을 입력할 수 있습니다.</p>
<p>Microphone(Microsoft LifeCam VX-1000.)</p>
<p>또는 이름 중 일부만 입력할 수도 있습니다. 예:</p>
<p>LifeCam</p>
<p>위의 필터를 사용하면 해당 이름에 &quot;LifeCam&quot; 문자열이 포함된 모든 장치가 반환됩니다.</p></td>
</tr>
</tbody>
</table>


## 메트릭

다음 표에서는 장치 보고서에서 제공되는 정보를 보여 줍니다.

### 장치 보고서 메트릭

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
<td><p><strong>캡처 장치</strong></p></td>
<td><p>예</p></td>
<td><p>오디오 전송에 사용되는 장치(예: 마이크 또는 웹캠)입니다.</p></td>
</tr>
<tr class="even">
<td><p><strong>렌더링 장치</strong></p></td>
<td><p>예</p></td>
<td><p>오디오 수신에 사용되는 장치(예: 헤드셋 또는 스피커)입니다.</p></td>
</tr>
<tr class="odd">
<td><p><strong>통화량</strong></p></td>
<td><p>예</p></td>
<td><p>수행된 총 통화 수입니다.</p></td>
</tr>
<tr class="even">
<td><p><strong>불량 통화율</strong></p></td>
<td><p>예</p></td>
<td><p>&quot;불량&quot;으로 분류된 통화 비율입니다. 불량 통화는 측정된 메트릭 중 적어도 하나 이상이 허용 값을 초과하는 모든 통화입니다(예: 지터가 과도하게 발생한 통화).</p></td>
</tr>
<tr class="odd">
<td><p><strong>고유 사용자</strong></p></td>
<td><p>예</p></td>
<td><p>장치를 사용한 고유 사용자입니다. 장치를 13회 사용한 사용자나 장치를 한 번만 사용한 사용자 모두 한 명의 고유한 사용자로 계산됩니다.</p></td>
</tr>
<tr class="even">
<td><p><strong>음성 스위치 시간 비율</strong></p></td>
<td><p>예</p></td>
<td><p>에코 방지를 위해 반이중 모드로 설정해야 한 통화 비율입니다. 반이중 모드에서 통신은 무전기를 이용한 통신에서와 마찬가지로 한 번에 한쪽 방향으로만 전달됩니다.</p></td>
</tr>
<tr class="odd">
<td><p><strong>마이크 작동 안 함 비율</strong></p></td>
<td><p>예</p></td>
<td><p>캡처 장치가 적정 수준으로 작동하지 않은 통화 비율입니다. 높은 값은 통화 품질 문제가 주로 올바르게 작동하지 않은 캡처 장치 때문인 것을 나타냅니다.</p></td>
</tr>
<tr class="even">
<td><p><strong>스피커 작동 안 함 비율</strong></p></td>
<td><p>예</p></td>
<td><p>렌더링 장치가 적정 수준으로 작동하지 않은 통화 비율입니다. 높은 값은 통화 품질 문제가 주로 올바르게 작동하지 않은 렌더링 장치 때문인 것을 나타냅니다.</p></td>
</tr>
<tr class="odd">
<td><p><strong>음성 스위치를 사용한 통화(%)</strong></p></td>
<td><p>예</p></td>
<td><p>반이중 모드로 설정해야 했던 총 통화 비율입니다. 반이중 모드에서 통신은 무전기를 이용한 통신에서와 마찬가지로 한 번에 한쪽 방향으로만 전달됩니다.</p></td>
</tr>
<tr class="even">
<td><p><strong>마이크 입력 에코(%)</strong></p></td>
<td><p>예</p></td>
<td><p>마이크 캡처 스트림에서 에코가 감지되는 시간의 비율입니다. 일반적으로 헤드셋이나 핸드셋에 대한 값은 낮으며, 스피커폰이나 독립 실행형 스피커에 대한 값은 이보다 높습니다. 온보드 음향 반향 취소를 지원하는 장치의 경우 값이 높으면 에코 누출을 나타냅니다. 기타 장치의 경우 장치 품질을 평가하기 위해 이 메트릭을 사용해서는 안 됩니다.</p></td>
</tr>
<tr class="odd">
<td><p><strong>송신 에코(%)</strong></p></td>
<td><p>예</p></td>
<td><p>다른 사용자에게 전송된 에코 비율입니다.</p></td>
</tr>
<tr class="even">
<td><p><strong>에코가 있는 통화(%)</strong></p></td>
<td><p>예</p></td>
<td><p>에코가 적정 수준을 초과한 총 통화 비율입니다.</p>
<p></p></td>
</tr>
</tbody>
</table>

