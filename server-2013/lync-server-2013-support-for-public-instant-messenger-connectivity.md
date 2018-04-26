---
title: Lync Server 2013의 공용 메신저 연결 지원
TOCTitle: Lync Server 2013의 공용 메신저 연결 지원
ms:assetid: 9c6eb500-647b-4ccd-a00e-2b8dd7c44a76
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Dn458579(v=OCS.15)
ms:contentKeyID: 59602778
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Lync Server 2013의 공용 메신저 연결 지원

 

_**마지막으로 수정된 항목:** 2015-03-09_

## 공용 인스턴트 메신저 연결 지원

이 문서에서는 PIC(공용 메신저 연결) 지원에 대한 정보를 제공합니다. PIC는 조직에서 Lync 사용자가 Lync 클라이언트 및 ID를 통해 공용 메신저(메신저) 서비스의 사용자와 연결할 수 있도록 해 주는 Microsoft Lync의 기능입니다.

최종 사용자의 경우 고객, 파트너, 공급업체와 원하는 방식대로 연결할 수 있다는 이점이 있습니다. IT의 경우 Lync의 제어, 규정 준수, 보관 기능을 유지하는 동시에 하나의 실시간 통신 클라이언트를 지원할 수 있어 유리합니다. [2013년 5월에 공개 출시된](http://blogs.technet.com/b/lync/archive/2013/05/23/lync-skype-connectivity-available-today.aspx) Lync-Skype 연결은 MSN/Windows Live, AOL, Yahoo에 연결할 때 처음 PIC가 설정된 Lync/OCS(Office Communications Server)/LCS(Live Communications Server)의 기존 데이터를 사용합니다. Lync-Skype 연결에 대한 자세한 내용은 [Lync-Skype 연결](http://office.microsoft.com/en-us/lync/lync-skype-connectivity-fx103789635.aspx)을 참고하세요. Windows Live, AOL, Yahoo와의 페더레이션은 각각 종료에 임박해 있으며 이 페이지에서는 각 서비스의 상태에 대해 설명합니다.

PIC를 사용하려면 고객은 각 공용 메신저 서비스 공급자에 대한 서비스를 활성화해야 합니다. 활성화하는 방법에 대한 요구 사항과 세부 정보는 메신저 서비스 공급자와 고객의 기본 라이선스 프로그램에 따라 다릅니다.

## Windows Live Messenger

Microsoft는 Windows Live Messenger와 Skype를 통합했습니다. 2013년 4월부터 Messenger 사용자가 로그인하면 Skype로 마이그레이션됩니다. Messenger와의 페더레이션을 사용하는 Lync 고객은 자신의 Messenger 대화 상대가 Skype로 업데이트된 이후에도 계속해서 통신할 수 있습니다, 서비스를 계속 이용하기 위해 Lync 관리자 또는 Lync 최종 사용자가 수행해야 할 일은 없으며, Messenger와 통신할 때와 같이 Lync에서 이 기능을 관리할 수 있습니다. 

Messenger 사용자가 Microsoft 계정(예: Messenger에 사용하는 동일한 자격 증명)을 사용하여 Skype에 로그인하면 페더레이션된 Lync 대화 상대를 비롯한 해당 사용자의 모든 Messenger 대화 상대가 Skype로 따라옵니다. 이러한 대화 상대는 Skype와 Lync 간에 현재 상태 공유 및 메신저 대화를 이용할 수 있습니다.

이제 모든 Lync 고객이 Lync와 Skype 사용자 간에 대화 상대 추가, 현재 상태 공유, 메신저 대화, 음성 통화를 제공하는 Lync-Skype 연결을 사용할 수 있습니다.

## Yahoo\! 및 AOL 인스턴트 메신저

Lync(및 Office Communications Server) 고객을 위한 Yahoo\! 및 AOL과의 페더레이션이 모두 서비스 종료에 임박해 있습니다. Microsoft는 Yahoo\! 및 AOL의 지원 여부에 따라 각각의 서비스를 제공해 왔지만 각 업체와 맺은 기본 계약의 종료 날짜가 가까워지고 있습니다. Yahoo\! 및 AOL 모두 2014년 6월까지 서비스가 지속됩니다.

  - **Yahoo** - 서비스가 2014년 6월까지 지속되며 고객은 이전과 마찬가지로 Microsoft Lync 공용 메신저 연결 사용자 구독 라이선스(“PIC USL”)를 사용해 사용 허가를 받아야 합니다.  2012년 9월 1일을 기준으로 신규 계약이나 갱신 계약의 경우 PIC USL이 더 이상 제공되지 않습니다.  이 날짜 전에 라이선스를 구입한 고객은 서비스 종료 또는 라이선스 만료 중 더 빠른 날짜까지 Yahoo\!와의 페더레이션을 계속할 수 있습니다. Lync 팀 블로그에서 [공지 사항](http://blogs.technet.com/b/lync/archive/2012/11/26/lync-and-yahoo-federation-end-of-life.aspx)을 읽어 보세요.  라이선스 계약이 2014년 6월 30일을 지나서도 유효한 고객에게는 2014년 6월 30일부터 해당되는 기간에 상응하는 금액을 계산해 크레딧을 지급해 드립니다.

  - **AOL** - 2014년 6월 30일에 Lync의 메신저 연결("PIC") 서비스 제공이 중단됩니다. 서비스가 종료될 때 고객의 불편을 최소화하기 위해 Microsoft는 추가 고객 도메인의 프로비저닝을 중단했습니다. 2014년 6월 30일까지 고객은 AIM과의 페더레이션된 통신을 계속해서 지원하기 위해 아무것도 하지 않아도 됩니다. 이 날짜 이후(또는 그 사이에 추가 도메인을 프로비저닝하려는 고객의 경우)에는 AOL에서 직접 대체 서비스를 제공합니다. AOL의 새로운 서비스에 대한 자세한 내용은 [AIM과 직접 페더레이션 설정](http://aimenterprise.aol.com/pic.php)(영문, AOL.com에서 새 페이지가 열림)을 참고하세요.

## 공용 메신저 공급자 요약

다음 표에서는 공용 메신저 서비스 공급자, Lync와의 페더레이션 기능, 라이선스 요구 사항에 대한 요약을 제공합니다.


<table>
<colgroup>
<col style="width: 33%" />
<col style="width: 33%" />
<col style="width: 33%" />
</colgroup>
<thead>
<tr class="header">
<th>공용 메신저 서비스 공급자</th>
<th>페더레이션 기능</th>
<th>라이선스 요구 사항</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Skype</p></td>
<td><p>메신저, 현재 상태, 오디오</p></td>
<td><p>Lync Server 클라이언트 액세스 라이선스, Lync Online 계획 1/2/3</p></td>
</tr>
<tr class="even">
<td><p>Windows Live Messenger</p></td>
<td><p>메신저, 현재 상태, 오디오/비디오</p></td>
<td><p>Lync Server 클라이언트 액세스 라이선스(WLM이 판매되는 한 지원됨)</p></td>
</tr>
<tr class="odd">
<td><p>AOL</p></td>
<td><p>메신저, 현재 상태</p></td>
<td><p>Lync Server 클라이언트 액세스 라이선스, 기존 고객의 경우 2014년 6월까지 지원됨</p></td>
</tr>
<tr class="even">
<td><p>Yahoo!</p></td>
<td><p>메신저, 현재 상태</p></td>
<td><p>추가 Microsoft Lync 공용 메신저 연결 사용자 구독 라이선스(“PIC USL”)와 더불어 Lync Server 클라이언트 액세스 라이선스가 필요합니다. 2012년 9월 가격표를 시작으로 PIC USL은 더 이상 구입할 수 없습니다. 활성 라이선스가 있는 고객은 2013년 6월 30일에 서비스가 종료될 때까지 계속해서 Yahoo! Messenger와 페더레이션할 수 있습니다.</p></td>
</tr>
</tbody>
</table>

