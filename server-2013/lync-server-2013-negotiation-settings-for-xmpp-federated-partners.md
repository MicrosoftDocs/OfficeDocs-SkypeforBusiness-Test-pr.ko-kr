---
title: 'Lync Server 2013: XMPP 페더레이션 파트너의 협상 설정'
TOCTitle: XMPP 페더레이션 파트너의 협상 설정
ms:assetid: ef773942-ef92-4f71-85a1-738dfebdfa00
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/JJ552456(v=OCS.15)
ms:contentKeyID: 49305464
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Lync Server 2013의 XMPP 페더레이션 파트너의 협상 설정

 

_**마지막으로 수정된 항목:** 2015-03-09_

XMPP 파트너의 구성에서 협상 유형에 대한 다양한 조합의 설정이 있을 수 있습니다. 이러한 조합 중에는 유효하지 않은 것도 있습니다. 이 항목에 자세히 설명된 표에서는 유효한 설정과 유효하지 않은 설정을 정의합니다. 일반 구성은 첫 번째 표에 나와 있으며 두 번째 표에는 가능한 모든 조합이 나와 있습니다. *TLS(전송 계층 보안)* 를 사용할 수 **없으면***SASL(Simple Authentication and Security Layer)* 도 사용할 수 없습니다. SASL은 암호화되지 않은(읽을 수 있는) 형식으로 전송되므로 TLS와 같은 다른 수단을 통해 보호되지 않을 경우 전송하면 안 됩니다.

### 일반 XMPP 페더레이션 협상 방법

<table>
<colgroup>
<col style="width: 20%" />
<col style="width: 20%" />
<col style="width: 20%" />
<col style="width: 20%" />
<col style="width: 20%" />
</colgroup>
<thead>
<tr class="header">
<th>TLS(전송 계층 보안)</th>
<th>SASL(Simple Authentication and Security Layer)</th>
<th>Dialback 인증</th>
<th>예상 인증 방법</th>
<th>참고</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>필수</p></td>
<td><p>필수</p></td>
<td><p>False</p></td>
<td><p>SASL over TLS</p></td>
<td><p>필수 TLS와 SASL은 SASL 메시지 스트림에 대한 보안을 유지하는 데 도움이 됩니다. XMPP 페더레이션 파트너가 TLS를 필수 또는 선택 사항으로 설정하지 않은 경우 Dialback을 대체 방법으로 사용할 수 없습니다.</p></td>
</tr>
<tr class="even">
<td><p>필수</p></td>
<td><p>선택</p></td>
<td><p>True</p></td>
<td><p>SASL over TLS, TLS Dialback, TCP Dialback</p></td>
<td><p>XMPP 페더레이션 파트너가 TLS를 요구하여 SASL을 선택 또는 필수로 설정한 경우 SASL이 사용됩니다. SASL을 사용할 수 없으면 Dialback over TLS가 사용됩니다.</p></td>
</tr>
<tr class="odd">
<td><p>선택</p></td>
<td><p>선택</p></td>
<td><p>True</p></td>
<td><p>SASL over TLS, TLS Dialback, TCP Dialback</p></td>
<td><p>매우 유연한 협상 방법이 제공되는 반면, 이러한 설정은 XMPP 페더레이션 파트너의 설정에 의존합니다. 파트너가 TLS를 선택 또는 필수로 설정했지만 SASL을 지원하지 않을 경우 TLS Dialback을 사용할 수 있습니다. 파트너가 TLS 및 SASL을 선택 또는 필수로 설정한 경우 TLS over SASL이 최적 설정으로 사용됩니다.</p></td>
</tr>
<tr class="even">
<td><p>지원 안 됨</p></td>
<td><p>지원 안 됨</p></td>
<td><p>True</p></td>
<td><p>TCP Dialback</p></td>
<td><p>대부분의 경우 TCP Dialback만이 사용 가능한 유일한 솔루션입니다. 다른 옵션보다는 덜 바람직하지만, 어느 정도의 신뢰성을 제공합니다.</p></td>
</tr>
</tbody>
</table>


### XMPP 페더레이션 협상 방법 매트릭스 - 전체

<table>
<colgroup>
<col style="width: 20%" />
<col style="width: 20%" />
<col style="width: 20%" />
<col style="width: 20%" />
<col style="width: 20%" />
</colgroup>
<thead>
<tr class="header">
<th>TLS(전송 계층 보안)</th>
<th>SASL(Simple Authentication and Security Layer)</th>
<th>Dialback 인증</th>
<th>예상 인증 방법</th>
<th>유효하지 않은 구성에 대한 설명, 경고 또는 오류</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>필수</p></td>
<td><p>필수</p></td>
<td><p>True</p></td>
<td><p>SASL over TLS</p></td>
<td>

> [!WARNING]
> SASL 및 TLS가 필수인 경우 Dialback이 작동되지 않습니다.


</td>
</tr>
<tr class="even">
<td><p>필수</p></td>
<td><p>필수</p></td>
<td><p>False</p></td>
<td><p>SASL over TLS</p></td>
<td><p></p></td>
</tr>
<tr class="odd">
<td><p>선택</p></td>
<td><p>필수</p></td>
<td><p>True</p></td>
<td><p>SASL over TLS, TLS Dialback, TCP Dialback</p></td>
<td>

> [!WARNING]
> SASL에 TLS가 필요합니다. TLS를 선택 항목으로 설정하면 세션 협상에 실패할 수 있습니다.


</td>
</tr>
<tr class="even">
<td><p>선택</p></td>
<td><p>필수</p></td>
<td><p>False</p></td>
<td><p>SASL over TLS</p></td>
<td>

> [!WARNING]
> SASL에 TLS가 필요합니다. TLS를 선택 항목으로 설정하면 세션 협상에 실패할 수 있습니다.


</td>
</tr>
<tr class="odd">
<td><p>지원 안 됨</p></td>
<td><p>필수</p></td>
<td><p>True</p></td>
<td><p>TCP Dialback</p></td>
<td>

> [!WARNING]
> SASL에 TLS가 필요합니다. TLS를 선택 항목으로 설정하면 세션 협상에 실패할 수 있습니다.


</td>
</tr>
<tr class="even">
<td><p>지원 안 됨</p></td>
<td><p>필수</p></td>
<td><p>False</p></td>
<td>

> [!WARNING]
> 유효하지 않은 구성


</td>
<td>

> [!WARNING]
> SASL에 TLS가 필요하지만 TLS를 사용할 수 없으므로 SASL/TLS가 성공할 수 없습니다. TCP Dialback이 False로 설정되고 사용할 수 없습니다.


</td>
</tr>
<tr class="odd">
<td><p>필수</p></td>
<td><p>선택</p></td>
<td><p>True</p></td>
<td><p>SASL over TLS, TLS Dialback</p></td>
<td><p></p></td>
</tr>
<tr class="even">
<td><p>필수</p></td>
<td><p>선택</p></td>
<td><p>False</p></td>
<td><p>SASL over TLS</p></td>
<td><p></p></td>
</tr>
<tr class="odd">
<td><p>선택</p></td>
<td><p>선택</p></td>
<td><p>True</p></td>
<td><p>SASL over TLS, TLS Dialback, TCP Dialback</p></td>
<td>

> [!WARNING]
> SASL에 TLS가 필요합니다. TLS를 선택 항목으로 설정하면 세션 협상에 실패할 수 있습니다.


</td>
</tr>
<tr class="even">
<td><p>선택</p></td>
<td><p>선택</p></td>
<td><p>False</p></td>
<td><p>SASL over TLS</p></td>
<td>

> [!WARNING]
> SASL에 TLS가 필요합니다. TLS를 선택 항목으로 설정하면 세션 협상에 실패할 수 있습니다.


</td>
</tr>
<tr class="odd">
<td><p>지원 안 됨</p></td>
<td><p>선택</p></td>
<td><p>True</p></td>
<td><p>TCP Dialback</p></td>
<td>

> [!WARNING]
> SASL에 TLS가 필요합니다. TLS를 선택 항목으로 설정하면 세션 협상에 실패할 수 있습니다.


</td>
</tr>
<tr class="even">
<td><p>지원 안 됨</p></td>
<td><p>선택</p></td>
<td><p>False</p></td>
<td>

> [!WARNING]
> 유효하지 않은 구성


</td>
<td>

> [!WARNING]
> SASL에 TLS가 필요합니다. TLS를 선택 항목으로 설정하면 세션 협상에 실패할 수 있습니다.


</td>
</tr>
<tr class="odd">
<td><p>필수</p></td>
<td><p>지원 안 됨</p></td>
<td><p>True</p></td>
<td><p>TLS Dialback</p></td>
<td><p>구성에서 TLS Dialback을 허용합니다.</p></td>
</tr>
<tr class="even">
<td><p>필수</p></td>
<td><p>지원 안 됨</p></td>
<td><p>False</p></td>
<td><p>유효하지 않은 구성</p></td>
<td>

> [!WARNING]
> SASL 또는 Dialback을 사용하도록 설정해야 합니다.


</td>
</tr>
<tr class="odd">
<td><p>선택</p></td>
<td><p>지원 안 됨</p></td>
<td><p>True</p></td>
<td><p>TLS Dialback, TCP Dialback</p></td>
<td><p>다른 끝점의 협상 선택에 따라 TCP 또는 TLS Dialback이 허용됩니다.</p></td>
</tr>
<tr class="even">
<td><p>선택</p></td>
<td><p>지원 안 됨</p></td>
<td><p>False</p></td>
<td><p>유효하지 않은 구성</p></td>
<td>

> [!WARNING]
> SASL 또는 Dialback을 사용하도록 설정해야 합니다.


</td>
</tr>
<tr class="odd">
<td><p>지원 안 됨</p></td>
<td><p>지원 안 됨</p></td>
<td><p>True</p></td>
<td><p>TCP Dialback</p></td>
<td><p>TCP Dialback이 사용 가능한 유일한 협상입니다.</p></td>
</tr>
<tr class="even">
<td><p>지원 안 됨</p></td>
<td><p>지원 안 됨</p></td>
<td><p>False</p></td>
<td><p>유효하지 않은 구성</p></td>
<td>

> [!WARNING]
> SASL 또는 Dialback을 사용하도록 설정해야 합니다.


</td>
</tr>
</tbody>
</table>

