---
title: 'Lync Server 2013: IP 전화 인벤토리 보고서'
TOCTitle: IP 전화 인벤토리 보고서
ms:assetid: aa7d6b31-cb09-4e68-b020-aa5dd0081c20
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg615027(v=OCS.15)
ms:contentKeyID: 49304673
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Lync Server 2013의 IP 전화 인벤토리 보고서

 

_**마지막으로 수정된 항목:** 2015-03-09_

IP 전화 인벤토리 보고서에서는 조직에서 현재 사용 중인 IP 전화에 대한 정보를 보고합니다. 이 보고서는 지정된 보고 기간 동안 실제로 사용된 IP 전화의 목록을 제공합니다. 무엇보다도 관리자는 이 보고서를 통해 오래되어 교체해야 하는 전화가 아직 사용되고 있는지를 파악할 수 있습니다. 또한 조직에 있는 값비싼 전화가 좀처럼 사용되지 않는 경우에도 이 보고서를 통해 확인할 수 있습니다. 새로운 전화를 구매해야 하거나 기존 전화를 다시 배포해야 하는 경우 이러한 정보는 매우 유용할 수 있습니다. 예를 들어 값비싼 전화를 좀처럼 사용하지 않는 사용자에게 전화를 훨씬 더 자주 사용하는 사용자와 전화를 바꾸도록 요청할 수 있습니다.

이 보고서는 진정한 인벤토리 보고서로 사용하기에 몇 가지 제한 사항이 있습니다. 첫째, IP 전화 보고서는 단지 지정된 기간 동안 Lync Server에 로그온한 모든 전화를 마지막 로그온 시간을 기준으로 정렬하여 나열합니다. 지정된 기간 동안 로그온하지 않은 전화는 인벤토리 보고서에 나열되지 않습니다. 여기에는 지정된 기간이 시작되기 전에 로그온하여 지정된 기간 중 계속 로그온되어 있던 전화도 포함됩니다. 예를 들어 2012년 7월의 모든 전화 인벤토리를 확인하면서 2012년 6월 30일에 Lync Server에 로그온하여 7월 1일에 계속 로그온되어 있는 전화도 함께 확인하려고 합니다. 그러나 이러한 전화는 7월 1일 날짜의 인벤토리 보고서에 표시되지 않습니다.

또한 인벤토리 보고서에는 조직에서 더 이상 사용하지 않는 전화가 포함될 수 있습니다. 예를 들어 2012년 7월 1일에 여러 Fabrikam 전화가 시스템에 로그온한 경우 5일 후에 조직에서 모든 Fabrikam 전화를 제거하고 최신 Contoso 모델로 교체한 경우에도 Fabrikam 전화가 7월 중에 시스템에 로그온했다는 이유만으로 "인벤토리" 보고서에 표시됩니다.

또한 IP 전화 인벤토리 보고서는 여러 종류의 전화에 대한 요약 합계를 보고하지 않습니다. 예를 들어 105개의 Polycom CX600 전화가 있다고 할 경우 이 보고서에는 이러한 전화가 105개 있다는 것은 나타나지 않으며 Polycom Cx600에 대한 별도의 항목 105개가 표시되기만 합니다. Cx600 항목이 105개 있다는 것을 파악하려면 수동으로 이러한 각 항목의 개수를 세야 합니다.


> [!WARNING]
> 아니면 데이터를 내보내어 Microsoft Excel 또는 Windows PowerShell을 사용하여 자동으로 개수를 계산할 수도 있습니다.



## IP 전화 인벤토리 보고서 액세스

IP 전화 인벤토리 보고서는 모니터링 보고서 홈 페이지에서 액세스됩니다. 사용자 URI 메트릭을 클릭하면 해당 사용자에 대한 사용자 활동 보고서에 액세스할 수 있습니다. 피어 투 피어 통화에 대한 마지막 활동 메트릭을 클릭하면 피어 투 피어 세션 세부 정보 보고서가 표시되며 전화 회의에 대해 동일한 메트릭을 클릭하면 전화 회의 정보 보고서가 표시됩니다.

## IP 전화 인벤토리 보고서의 효과적인 활용

특정 종류의 전화에 대한 사용 정보(예: "사용자들이 Polycom CX600 전화를 얼마나 자주 사용하는가?")만 알아보고 싶은 경우 IP 전화 인벤토리 보고서에서 바로 해당 종류의 전화로 필터링하여 정보를 얻을 수 있습니다. 한편 모든 전화에 대한 요약 정보(예: Polycom CX600을 사용하는 사용자 수, LG-Nortel IP8540을 사용하는 사용자 수 등)를 알아보려는 경우 해당 데이터를 내보내어 다른 응용 프로그램(예: Windows PowerShell)을 사용하여 관련 분석을 할 수 있습니다. 예를 들어 데이터를 쉼표로 구분된 값 파일(C:\\Data\\IP\_Phone\_Inventory\_Report.csv)로 내보내는 경우 다음과 같은 두 명령을 사용하여 모든 전화에 대한 요약 데이터를 얻을 수 있습니다.

    $phones = Import-Csv "C:\Data\IP_Phone_Inventory_Report.csv"
    $phones |Group-Object Manufacturer, "Hardware version" | Select-Object Count, Name | Sort-Object Count -Descending

그러면 다음과 같은 데이터가 반환됩니다.

    Count    Name
    -----    ----
      267    POLYCOM, CX700
      267    POLYCOM, CX600
      166    POLYCOM, C
       68    Microsoft, CPE
       64    LG-Nortel, IP8540
       59    Aastra, 6725ip
       37    LG-Nortel, IP
       22    POLYCOM, CX3000
       11    Microsoft, CPE_A
        9    POLYCOM, CX500
        7    Aastra, 6721ip

또한 다음과 같은 두 명령을 통해, 시스템에 로그온했지만 실제로 통화하는 데 사용되지 않은 전화를 파악할 수 있습니다. Last activity 메트릭 값이 비어 있으면 마지막 활동이 없었음을 나타냅니다.

    $phones = Import-Csv "C:\Data\IP_Phone_Inventory_Report.csv"
    $phones | Where-Object {$_."Last activity" -eq ""}

그러면 사용되지 않은 각 전화에 대해 다음과 같은 데이터가 반환됩니다.

    Manufacturer     : POLYCOM
    Hardware version : CX600
    MAC address      : 00-04-F2-00-01-76
    User URI         : 422
    User agent       : CPE/4.0.7423.1 OCPhone/4.0.7423.1 (Microsoft Lync 2010 (Beta) Phone Edition)
    Last logon time  : 8/30/2010 4:44:48 PM
    Last logoff time : 8/30/2010 5:59:07 PM
    Last activity    :

또한 IP 전화 인벤토리 보고서를 다음과 같은 흥미로운 방식으로 사용할 수 있습니다. IP 전화의 MAC 주소를 아는 경우 MAC 주소 텍스트 상자에 MAC 주소를 입력하여 해당 전화를 마지막으로 사용한 사용자를 확인할 수 있습니다. IP 전화 인벤토리 보고서는 해당 전화에 마지막으로 로그온한 사용자의 SIP 주소와 기타 여러 값을 보고합니다. 또는 사용자 URI 접두사 상자에 사용자 SIP 주소를 입력하여 해당 사용자가 사용한 모든 전화를 확인할 수도 있습니다.

## 필터

필터를 사용하면 여러 방식으로 반환된 데이터를 보거나 보다 세부적으로 대상화된 데이터 집합을 반환할 수 있습니다. 예를 들어 IP 전화 인벤토리를 사용하면 특정 회사에서 제작한 전화 또는 이러한 전화 중 특정 버전만 볼 수 있습니다. 또한 데이터의 그룹 지정 방식도 선택할 수 있습니다. 이 경우 등록은 시간, 일, 주 및 월별로 그룹이 지정됩니다.

다음 표에서는 IP 전화 인벤토리 보고서에서 사용할 수 있는 필터를 보여 줍니다.

### IP 전화 인벤토리 보고서 필터

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
<td><p><strong>제조업체</strong></p></td>
<td><p>IP 전화를 제작한 회사의 이름입니다. 이 필터의 값은 데이터베이스에 현재 있는 IP 전화에 따라 자동으로 채워집니다.</p></td>
</tr>
<tr class="even">
<td><p><strong>하드웨어 버전</strong></p></td>
<td><p>IP 전화의 버전 번호입니다. 제조업체 및 하드웨어 버전 필터를 사용하면 특정 유형의 전화를 고유하게 식별할 수 있습니다. 이 필터의 값은 데이터베이스에 현재 있는 IP 전화에 따라 자동으로 채워집니다.</p></td>
</tr>
<tr class="odd">
<td><p><strong>사용자 에이전트</strong></p></td>
<td><p>IP 전화에 사용된 소프트웨어의 식별자입니다. 이 필터의 값은 데이터베이스에 현재 있는 IP 전화에 따라 자동으로 채워집니다.</p></td>
</tr>
<tr class="even">
<td><p><strong>MAC 주소</strong></p></td>
<td><p>IP 전화의 네트워크 인터페이스에 대한 고유 식별자입니다. MAC(미디어 액세스 제어) 주소는 일반적으로 해당 전화를 제작할 당시에 지정되며 장치 하드웨어에 직접 연결되어 있습니다.</p>
<p>특정 MAC 주소와 관련된 레코드를 검색하려면 해당 주소만 입력하면 됩니다. 예:</p>
<p>00-08-5D-16-16-48</p>
<p>전체 주소를 입력해야 합니다. 부분 주소(예: 00-08-5D)만 사용하면 데이터가 반환되지 않습니다.</p></td>
</tr>
<tr class="odd">
<td><p><strong>다음 일 이전의 마지막 활동</strong></p></td>
<td><p>다음 값 중 하나를 선택합니다.</p>
<ul>
<li><p>[모두]</p></li>
<li><p>10</p></li>
<li><p>20</p></li>
<li><p>30</p></li>
</ul></td>
</tr>
<tr class="even">
<td><p><strong>다음 일 이전의 마지막 로그오프 시간</strong></p></td>
<td><p>다음 값 중 하나를 선택합니다.</p>
<ul>
<li><p>[모두]</p></li>
<li><p>10</p></li>
<li><p>20</p></li>
<li><p>30</p></li>
</ul></td>
</tr>
<tr class="odd">
<td><p><strong>사용자 URI 접두사</strong></p></td>
<td><p>IP 전화를 사용한 사용자의 SIP 주소입니다.</p></td>
</tr>
</tbody>
</table>


## 메트릭

다음 표에서는 IP 전화 인벤토리 보고서에서 제공되는 정보를 보여 줍니다.

### IP 전화 인벤토리 보고서 메트릭

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
<td><p><strong>제조업체</strong></p></td>
<td><p>예</p></td>
<td><p>IP 전화를 제작한 회사의 이름입니다.</p></td>
</tr>
<tr class="even">
<td><p><strong>하드웨어 버전</strong></p></td>
<td><p>예</p></td>
<td><p>IP 전화의 버전 번호입니다.</p></td>
</tr>
<tr class="odd">
<td><p><strong>MAC 주소</strong></p></td>
<td><p>예</p></td>
<td><p>IP 전화의 네트워크 인터페이스에 대한 고유 식별자입니다. MAC 주소는 일반적으로 해당 전화를 제작할 당시에 지정되며 장치 하드웨어에 직접 연결되어 있습니다.</p></td>
</tr>
<tr class="even">
<td><p><strong>사용자 URI</strong></p></td>
<td><p>예</p></td>
<td><p>IP 전화를 사용한 사용자의 SIP 주소입니다.</p></td>
</tr>
<tr class="odd">
<td><p><strong>사용자 에이전트</strong></p></td>
<td><p>예</p></td>
<td><p>IP 전화에 사용된 소프트웨어의 식별자입니다.</p></td>
</tr>
<tr class="even">
<td><p><strong>마지막 로그온 시간</strong></p></td>
<td><p>예</p></td>
<td><p>IP 전화로 Lync Server에 마지막으로 로그온한 날짜 및 시간입니다.</p></td>
</tr>
<tr class="odd">
<td><p><strong>마지막 로그오프 시간</strong></p></td>
<td><p>예</p></td>
<td><p>IP 전화로 Lync Server에서 마지막으로 로그오프한 날짜 및 시간입니다.</p></td>
</tr>
<tr class="even">
<td><p><strong>마지막 활동</strong></p></td>
<td><p>예</p></td>
<td><p>IP 전화를 마지막으로 사용한 날짜 및 시간입니다.</p></td>
</tr>
</tbody>
</table>

