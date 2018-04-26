---
title: 'Lync Server 2013: 공용 메신저 지원'
TOCTitle: 공용 메신저 지원
ms:assetid: 1f45163b-52c6-4a78-b9c8-dfe3abe4e5eb
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/JJ204732(v=OCS.15)
ms:contentKeyID: 49303011
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Lync Server 2013의 공용 메신저 지원

 

_**마지막으로 수정된 항목:** 2013-10-07_

Lync Server 2013에서는 사용이 허가된 공용 IM(인스턴트 메시징) 연결 공급자를 사용할 수 있을 뿐 아니라 XMPP(Extensible Messaging and Presence Protocol)를 사용하여 특수한 유형의 페더레이션( Lync Server에서 Lync 2013 클라이언트를 사용해 구성된 XMPP 도메인 파트너에 액세스할 수 있도록 함)을 구현할 수 있습니다.

## 공용 IM 연결 공급자 지원

현재 지원되는 공용 인스턴트 메시징 연결 파트너는 다음과 같습니다.

  - America Online

  - Windows Live

  - Yahoo\!

Windows Live 사용자와의 통신을 위해 Lync Server 2013에서는 피어 투 피어 IM 및 오디오/비디오 통화를 지원합니다. AOL 및 Yahoo\!와의 통신을 위해 Lync Server 2013에서는 피어 투 피어 IM을 지원합니다. 별도의 라이선스가 필요할 수 있습니다.


> [!IMPORTANT]
> <UL>
> <LI>
> <P>2012년 9월 1일 현재 신규 또는 갱신 계약에 대해 Microsoft Lync "PIC USL"(공용 메신저 연결 사용자 구독 라이선스)을 더 이상 구입할 수 없습니다. 유효 라이선스를 보유한 고객은 서비스 종료 날짜까지 Yahoo! Messenger와 계속 페더레이션할 수 있습니다. AOL 및 Yahoo!는 서비스 종료 날짜를 2014년 6월로 발표했습니다. 자세한 내용은 <A href="lync-server-2013-support-for-public-instant-messenger-connectivity.md">Lync Server 2013의 공용 메신저 연결 지원</A>을 참고하세요.</P>
> <LI>
> <P>PIC USL은 Lync Server 또는 Office Communications Server가 Yahoo! Messenger와 페더레이션하는 데 필요한 월별 사용자 단위 구독 라이선스입니다. Microsoft는 Yahoo!의 지원 여부에 따라 이 서비스를 제공할 수 있었으며 해당 서비스의 기본 계약은 곧 종료될 예정입니다.</P>
> <LI>
> <P>Lync는 전 세계의 여러 조직과 개별 사용자를 연결해 주는 매우 효율적인 도구입니다. Lync Standard CAL 외의 추가 사용자/장치 라이선스가 없어도 Windows Live Messenger와의 페더레이션이 가능합니다. Skype 페더레이션도 이 목록에 추가될 예정이므로 Lync 사용자는 메신저 및 음성을 통해 수많은 사람들과 연결할 수 있습니다.</P></LI></UL>



## XMPP 페더레이션 지원

XMPP 페더레이션은 GTalk 등의 공용 공급자를 사용하는 구성된 XMPP 도메인 사용자와 Lync 사용자의 통신을 지원합니다. 이러한 사용자와의 통신

  - 피어 투 피어 IM 및 현재 상태

  - Lync 클라이언트에서 XMPP 페더레이션 연락처 만들기

