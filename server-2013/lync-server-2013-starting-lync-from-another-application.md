---
title: 다른 응용 프로그램에서 Lync 시작
TOCTitle: 다른 응용 프로그램에서 Lync 시작
ms:assetid: 573b30b1-6590-4b24-8e96-a41be57cb0ef
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg398376(v=OCS.15)
ms:contentKeyID: 52056862
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# 다른 응용 프로그램에서 Lync 시작

 

_**마지막으로 수정된 항목:** 2015-03-09_

명령줄 매개 변수를 사용하여 Lync 2013을 빠르게 시작할 수 있습니다. 예를 들어 사용자가 다른 응용 프로그램에서 전화 번호를 클릭하면 해당 응용 프로그램에서 Lync 2013 인스턴스를 시작하고 해당 번호로 거는 통화를 시작할 수 있습니다.

또한 Lync 2013은 세미콜론으로 구분된 단체 회의용 연락처 이름 목록을 인식할 수 있습니다.

Lync 2013이 시작 시에 자동으로 로그인하도록 구성된 경우 명령줄 매개 변수를 사용하여 Lync 2013을 시작하면 Lync 주 창이 열립니다. Lync가 시작 시에 자동으로 로그인하도록 구성되지 않은 경우에는 로그인 창이 열립니다.

다음 표에는 사용 가능한 매개 변수가 나와 있습니다.

### Lync 2013 명령줄 매개 변수

<table>
<colgroup>
<col style="width: 33%" />
<col style="width: 33%" />
<col style="width: 33%" />
</colgroup>
<thead>
<tr class="header">
<th>확장</th>
<th>데이터 형식</th>
<th>동작</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>tel:</p></td>
<td><p>tel URI</p></td>
<td><p>음성 통화용 대화 창을 열지만 지정된 번호로 전화를 걸지는 않습니다.</p></td>
</tr>
<tr class="even">
<td><p>callto:</p></td>
<td><p>tel:, sip: 또는 입력 가능한 tel URI</p></td>
<td><p>음성 통화용 대화 창을 열지만 지정된 번호로 전화를 걸지는 않습니다.</p></td>
</tr>
<tr class="odd">
<td><p>sip:</p></td>
<td><p>SIP URI</p></td>
<td><p>참가자 목록에 지정된 SIP URI(Uniform Resource Identifier)가 포함된 대화 창을 엽니다.</p></td>
</tr>
<tr class="even">
<td><p>Sips:</p></td>
<td><p>SIP URI</p></td>
<td><p>Lync 2013이 TLS(전송 계층 보안) 프로토콜을 사용하도록 구성된 경우에는 sip:와 정확히 동일하게 작동합니다. TLS를 사용하지 않는 경우에는 더욱 높은 보안 수준이 필요함을 사용자에게 알리는 대화 상자를 표시합니다.</p></td>
</tr>
<tr class="odd">
<td><p>conf:</p></td>
<td><p>참가할 회의의 SIP URI</p></td>
<td><p>자체 URI의 경우 포커스를 인스턴스화하고 명단 전용 보기를 표시합니다. 그렇지 않은 경우에는 명단 보기를 표시하되 INVITE를 보내지는 않습니다.</p>
<p></p></td>
</tr>
<tr class="even">
<td><p>im:</p></td>
<td><p>SIP URI</p></td>
<td><p>SIP URI가 포함된 IM(인스턴트 메시징) 전용 대화 창을 표시합니다. 구분 기호 없이 꺾쇠 괄호(&lt;&gt;) 안에 지정된 여러 SIP URI를 허용합니다.</p>
<pre><code>im:&lt;sip:user1@host&gt;&lt;sip:user2@host&gt;</code></pre></td>
</tr>
</tbody>
</table>


다음 표에는 이러한 명령줄 매개 변수의 예제가 나와 있습니다.

### 명령줄 매개 변수 예제

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th>인스턴스</th>
<th>결과</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Tel:+14255550101</p></td>
<td><p>+14255550101이 포함된 전화 전용 보기를 엽니다.</p></td>
</tr>
<tr class="even">
<td><p>Callto:tel:+ 14255550101</p></td>
<td><p>+14255550101이 포함된 전화 전용 보기를 엽니다.</p></td>
</tr>
<tr class="odd">
<td><p>Callto:sip:kazuto@litwareinc.com</p></td>
<td><p>kazuto@litwareinc.com이 포함된 전화 전용 보기를 엽니다.</p></td>
</tr>
<tr class="even">
<td><p>sip:kazuto@litwareinc.com</p></td>
<td><p>kazuto@litwareinc.com이 포함된 대화 창을 엽니다.</p></td>
</tr>
<tr class="odd">
<td><p>conf:sip:https://meet.contoso.com/kazuto/7322994</p></td>
<td><p>대화 창을 열고 모임 오디오 참가 옵션을 표시합니다.</p></td>
</tr>
</tbody>
</table>

