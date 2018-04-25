---
title: UCWA 이벤트
TOCTitle: UCWA 이벤트
ms:assetid: 26cb409d-f4e4-43c7-873f-b694702d491d
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/JJ945621(v=OCS.15)
ms:contentKeyID: 52056813
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# UCWA 이벤트

 

_**마지막으로 수정된 항목:** 2015-03-09_

    The information in this topic pertains to Cumulative Updates for Lync Server 2013: February 2013.

Lync Server 2013에서는 연락처 검색을 위한 Microsoft Exchange 액세스에서 모바일 클라이언트에 대한 현재 상태 업데이트에 이르기까지 다양한 용도로 UCWA(통합 통신 웹 API)를 사용합니다.

UCWA는 정보/경고/오류 이벤트 유형으로 작동 동작 레코드를 기록합니다. 아래 표에는 UCWA 구성 요소가 기록할 수 있는 이벤트에 대한 설명이 나와 있습니다.


<table>
<colgroup>
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
</colgroup>
<thead>
<tr class="header">
<th>이벤트 ID</th>
<th>이벤트 유형</th>
<th>요약</th>
<th>원인 및 해결 방법</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>20001</p></td>
<td><p>정보</p></td>
<td><p>UCWA 초기화됨</p></td>
<td><p>해당 없음</p>
<p>해당 없음</p></td>
</tr>
<tr class="even">
<td><p>20002</p></td>
<td><p>오류</p></td>
<td><p>초기화 중 UCWA에서 예기치 않은 예외가 발생함</p></td>
<td><p>초기화 중 예기치 않은 오류가 발생했습니다.</p>
<p>관련 이벤트 로그 항목에서 예외 세부 정보를 확인하여 가능한 원인을 파악합니다.</p></td>
</tr>
<tr class="odd">
<td><p>20003</p></td>
<td><p>오류</p></td>
<td><p>UCWA에서 처리되지 않은 예외가 발생함</p></td>
<td><p>처리되지 않은 예외가 발생했습니다.</p>
<p>서버를 다시 시작합니다. 문제가 계속되면 기술 지원에 문의합니다.</p></td>
</tr>
<tr class="even">
<td><p>20004</p></td>
<td><p>오류</p></td>
<td><p>HD 사진을 사용하기 위해 Exchange에 액세스할 수 없음</p></td>
<td><p>Exchange에 연결할 수 없습니다.</p>
<p>Exchange에 연결할 수 있는지 확인합니다.</p></td>
</tr>
<tr class="odd">
<td><p>20005</p></td>
<td><p>정보</p></td>
<td><p>HD 사진을 사용하기 위한 Exchange 액세스 오류에서 복구됨</p></td>
<td><p>해당 없음</p></td>
</tr>
<tr class="even">
<td><p>20006</p></td>
<td><p>오류</p></td>
<td><p>연락처 검색을 위해 Exchange에 액세스할 수 없음</p></td>
<td><p>Exchange에 연결할 수 없습니다.</p>
<p>Exchange에 연결할 수 있는지 확인합니다.</p></td>
</tr>
<tr class="odd">
<td><p>20007</p></td>
<td><p>정보</p></td>
<td><p>Exchange의 연락처 검색 오류에서 복구됨</p></td>
<td><p>해당 없음</p></td>
</tr>
<tr class="even">
<td><p>20008</p></td>
<td><p>경고</p></td>
<td><p>응용 프로그램당 허용되는 현재 상태 구독 수를 초과하여 구독 시도</p></td>
<td><p>응용 프로그램당 허용되는 현재 상태 구독 수를 초과하여 구독을 시도했습니다.</p>
<p>클라이언트에서 불필요한 구독을 확인합니다.</p></td>
</tr>
<tr class="odd">
<td><p>20009</p></td>
<td><p>경고</p></td>
<td><p>배치당 허용되는 현재 상태 구독 수를 초과하여 구독 시도</p></td>
<td><p>배치당 허용되는 현재 상태 구독 수를 초과하여 구독을 시도했습니다.</p>
<p>클라이언트에서 불필요한 구독을 확인합니다.</p></td>
</tr>
<tr class="even">
<td><p>20010</p></td>
<td><p>오류</p></td>
<td><p>인밴드 데이터를 검색할 수 없음</p></td>
<td><p>인밴드 데이터를 검색할 수 없습니다.</p>
<p>문제가 계속되면 기술 지원에 문의합니다.</p></td>
</tr>
<tr class="odd">
<td><p>20011</p></td>
<td><p>오류</p></td>
<td><p>현재 상태를 구독할 수 없음</p></td>
<td><p>현재 상태를 구독할 수 없습니다.</p>
<p>문제가 계속되면 기술 지원에 문의합니다.</p></td>
</tr>
<tr class="even">
<td><p>20012</p></td>
<td><p>오류</p></td>
<td><p>끝점을 등록하지 못함</p></td>
<td><p>끝점을 등록하지 못했습니다.</p>
<p>문제가 계속되면 기술 지원에 문의합니다.</p></td>
</tr>
<tr class="odd">
<td><p>20013</p></td>
<td><p>오류</p></td>
<td><p>IM MCU를 사용할 수 없음</p></td>
<td><p>IM MCU를 사용할 수 없습니다.</p>
<p>IM MCU가 실행 중인지 확인합니다.</p></td>
</tr>
<tr class="even">
<td><p>20014</p></td>
<td><p>정보</p></td>
<td><p>IM MCU 연결 오류에서 복구됨</p></td>
<td><p>해당 없음</p></td>
</tr>
<tr class="odd">
<td><p>20015</p></td>
<td><p>오류</p></td>
<td><p>AV MCU를 사용할 수 없음</p></td>
<td><p>AV MCU를 사용할 수 없습니다.</p>
<p>AV MCU가 실행 중인지 확인합니다.</p></td>
</tr>
<tr class="even">
<td><p>20016</p></td>
<td><p>정보</p></td>
<td><p>AV MCU 연결 오류에서 복구됨</p></td>
<td><p>해당 없음</p></td>
</tr>
<tr class="odd">
<td><p>20017</p></td>
<td><p>오류</p></td>
<td><p>AS MCU를 사용할 수 없음</p></td>
<td><p>AS MCU를 사용할 수 없습니다.</p>
<p>AS MCU가 실행 중인지 확인합니다.</p></td>
</tr>
<tr class="even">
<td><p>20018</p></td>
<td><p>정보</p></td>
<td><p>AS MCU 연결 오류에서 복구됨</p></td>
<td><p>해당 없음</p></td>
</tr>
<tr class="odd">
<td><p>20019</p></td>
<td><p>오류</p></td>
<td><p>데이터 MCU를 사용할 수 없음</p></td>
<td><p>데이터 MCU를 사용할 수 없습니다.</p>
<p>데이터 MCU가 실행 중인지 확인합니다.</p></td>
</tr>
<tr class="even">
<td><p>20020</p></td>
<td><p>정보</p></td>
<td><p>데이터 MCU 연결 오류에서 복구됨</p></td>
<td><p>해당 없음</p></td>
</tr>
<tr class="odd">
<td><p>20021</p></td>
<td><p>오류</p></td>
<td><p>IM MCU에 참가할 수 없음</p></td>
<td><p>IM MCU에 참가할 수 없습니다.</p>
<p>IM MCU가 실행 중인지 확인합니다.</p></td>
</tr>
<tr class="even">
<td><p>20022</p></td>
<td><p>오류</p></td>
<td><p>AV MCU에 참가할 수 없음</p></td>
<td><p>AV MCU에 참가할 수 없습니다.</p>
<p>AV MCU가 실행 중인지 확인합니다.</p></td>
</tr>
<tr class="odd">
<td><p>20023</p></td>
<td><p>오류</p></td>
<td><p>AS MCU에 참가할 수 없음</p></td>
<td><p>AS MCU에 참가할 수 없습니다.</p>
<p>AS MCU가 실행 중인지 확인합니다.</p></td>
</tr>
<tr class="even">
<td><p>20024</p></td>
<td><p>오류</p></td>
<td><p>데이터 MCU에 참가할 수 없음</p></td>
<td><p>데이터 MCU에 참가할 수 없습니다.</p>
<p>데이터 MCU가 실행 중인지 확인합니다.</p></td>
</tr>
<tr class="odd">
<td><p>20025</p></td>
<td><p>오류</p></td>
<td><p>사진을 사용하기 위해 활성 디렉터리에 액세스할 수 없음</p></td>
<td><p>활성 디렉터리에 연결할 수 없습니다.</p>
<p>활성 디렉터리에 연결할 수 있는지 확인합니다.</p></td>
</tr>
<tr class="even">
<td><p>20026</p></td>
<td><p>정보</p></td>
<td><p>사진을 사용하기 위한 활성 디렉터리 액세스 오류에서 복구됨</p></td>
<td><p>해당 없음</p></td>
</tr>
<tr class="odd">
<td><p>20027</p></td>
<td><p>경고</p></td>
<td><p>역직렬화할 수 없음</p></td>
<td><p>역직렬화할 수 없습니다.</p>
<p>문제가 계속되면 기술 지원에 문의합니다.</p></td>
</tr>
</tbody>
</table>

