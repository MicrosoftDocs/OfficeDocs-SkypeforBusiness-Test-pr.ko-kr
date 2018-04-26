---
title: 'Lync Server 2013: 프런트 엔드 서버, 메신저 및 현재 상태에 대한 요구 사항 정의'
TOCTitle: 프런트 엔드 서버, 메신저 및 현재 상태에 대한 요구 사항 정의
ms:assetid: c21198bc-520c-4d17-8b84-7ff1475b9b0a
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg412956(v=OCS.15)
ms:contentKeyID: 49304931
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Lync Server 2013에서 프런트 엔드 서버, 메신저 및 현재 상태에 대한 요구 사항 정의

 

_**마지막으로 수정된 항목:** 2013-10-07_

IM(인스턴트 메시징) 및 현재 상태를 계획하는 데 수행되는 작업 중 주요 작업은 사용자를 위해 충분한 프런트 엔드 서버를 제공하는 것입니다.

## 외부 사용자와 통신 사용

사용자가 외부 사용자와 통신할 수 있도록 설정하면 Lync Server에 대한 투자 이익을 크게 증가시킬 수 있습니다. 외부 사용자에는 다음이 포함될 수 있습니다.

  - **원격 사용자**   방화벽 외부에서 랩톱 또는 다른 Lync Server 장치를 사용하여 작업하는 조직의 사용자

  - **페더레이션 사용자**    Lync Server를 실행하여 함께 작업하는 회사의 사용자. 조직의 사용자가 이러한 사용자에게 쉽게 연결할 수 있도록 하려면 이러한 회사와 페더레이션 관계를 만들면 됩니다.

  - **공용 사용자**   Windows Live 인터넷 서비스 네트워크에서 제공한 IM 서비스, Yahoo\!, AOL 등과 같은 공용 IM 서비스 사용자 및 Google Talk 등과 같은 XMPP(eXtensible Messaging and Presence Protocol)를 사용하는 공급자 및 서버 사용자
    

    > [!NOTE]
    > Windows Live, AOL, Yahoo! 등의 공용 IM 연결에는 별도의 라이선스가 필요할 수도 있습니다.

    

    > [!IMPORTANT]
    > <UL>
    > <LI>
    > <P>2012년 9월 1일 현재 신규 또는 갱신 계약에 대해 Microsoft Lync "PIC USL"(공용 메신저 연결 사용자 구독 라이선스)을 더 이상 구입할 수 없습니다. 유효 라이선스를 보유한 고객은 서비스 종료 날짜까지 Yahoo! Messenger와 계속 페더레이션할 수 있습니다. AOL 및 Yahoo!는 서비스 종료 날짜를 2014년 6월로 발표했습니다. 자세한 내용은 <A href="lync-server-2013-support-for-public-instant-messenger-connectivity.md">Lync Server 2013의 공용 메신저 연결 지원</A>을 참고하세요.</P>
    > <LI>
    > <P>PIC USL은 Lync Server 또는 Office Communications Server가 Yahoo! Messenger와 페더레이션하는 데 필요한 월별 사용자 단위 구독 라이선스입니다. Microsoft는 Yahoo!의 지원 여부에 따라 이 서비스를 제공할 수 있었으며 해당 서비스의 기본 계약은 곧 종료될 예정입니다.</P>
    > <LI>
    > <P>Lync는 전 세계의 여러 조직과 개별 사용자를 연결해 주는 매우 효율적인 도구입니다. Lync Standard CAL 외의 추가 사용자/장치 라이선스가 없어도 Windows Live Messenger와의 페더레이션이 가능합니다. Skype 페더레이션도 이 목록에 추가될 예정이므로 Lync 사용자는 메신저 및 음성을 통해 수많은 사람들과 연결할 수 있습니다.</P></LI></UL>



이러한 시나리오의 전부 또는 일부를 적용하려면 에지 서버를 배포하여 Lync Server 배포와 외부 사용자 간 보안 통신을 설정해야 합니다. 조직의 원격 사용자와 페더레이션 조직의 사용자는 IM을 사용하여 서로의 현재 상태를 확인하고 통신할 수 있습니다. 외부 사용자와의 통신을 사용하는 방법에 대한 자세한 내용은 계획 설명서에서 [Lync Server 2013의 외부 사용자 액세스 계획](lync-server-2013-planning-for-external-user-access.md)를 참조하십시오.

## IM 콘텐츠 보관

Lync Server에서는 조직이 준수 규정을 따라야 하는 경우 사용할 수 있는 기능을 제공합니다. 보관을 사용하여 조직의 모든 사용자 및 지정한 특정 사용자에 대한 IM 메시지 콘텐츠를 보관할 수 있습니다. 자세한 내용은 계획 설명서에서 [Lync Server 2013의 보관 계획](lync-server-2013-planning-for-archiving.md)을 참조하십시오.

Microsoft Exchange Server 2013이 배포된 경우 Exchange 데이터의 보관을 Lync Server 데이터의 보관과 통합하고 하나의 도구를 사용하여 이 두 유형의 보관된 데이터를 모두 검색할 수 있습니다. 자세한 내용은 [Microsoft Exchange Server 2013 보관을 사용하도록 Microsoft Lync Server 2013 구성](configuring-lync-server-2013-to-use-microsoft-exchange-server-2013-archiving.md)을 참조하십시오.

