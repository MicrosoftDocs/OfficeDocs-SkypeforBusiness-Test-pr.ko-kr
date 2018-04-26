---
title: Lync Server 2013의 공용 메신저 연결 계획
TOCTitle: Lync Server 2013의 공용 메신저 연결 계획
ms:assetid: e75e8884-05c7-414a-8014-bc9aa8126fb7
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/JJ205349(v=OCS.15)
ms:contentKeyID: 49305369
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Lync Server 2013의 공용 메신저 연결 계획

 

_**마지막으로 수정된 항목:** 2013-10-07_

공용 메신저 연결은 페더레이션의 한 클래스이며 내부 및 외부 Lync Server 2013 사용자가 다음의 연락처를 추가할 수 있도록 구성됩니다.

  - Messenger 연락처

  - Yahoo\! 연락처

  - AOL(America Online) 연락처


> [!IMPORTANT]
> <UL>
> <LI>
> <P>2012년 9월 1일 현재 신규 또는 갱신 계약에 대해 Microsoft Lync PIC USL(공용 메신저 연결 사용자 구독 라이선스)을 더 이상 구입할 수 없습니다. 유효 라이선스를 보유한 고객은 서비스 종료 날짜까지 Yahoo! Messenger와 계속해서 페더레이션할 수 있습니다. AOL 및 Yahoo!는 서비스 종료 날짜를 2014년 6월로 발표했습니다. 자세한 내용은 <A href="lync-server-2013-support-for-public-instant-messenger-connectivity.md">Lync Server 2013의 공용 메신저 연결 지원</A>을 참고하세요.</P>
> <LI>
> <P>PIC USL은 Lync Server 또는 Office Communications Server가 Yahoo! Messenger와 페더레이션하는 데 필요한 월별 사용자 단위 구독 라이선스입니다. Microsoft는 Yahoo!의 지원 여부에 따라 이 서비스를 제공할 수 있었으며 해당 서비스의 기본 계약은 갱신되지 않을 예정입니다.</P>
> <LI>
> <P>Lync는 전 세계의 여러 조직과 개별 사용자를 연결해 주는 매우 효율적인 도구입니다. Lync Standard CAL 외의 추가 사용자/장치 라이선스가 없어도 Windows Live Messenger와의 페더레이션이 가능합니다. Skype 페더레이션도 이 목록에 추가될 예정이므로 Lync 사용자는 메신저 및 음성을 통해 수많은 사람들과 연결할 수 있습니다.</P></LI></UL>



이 클래스의 페더레이션을 사용하려면 계획 시 다음 사항을 고려해야 합니다.

  - Windows Live Messenger 사용자는 Lync Server 2013 사용자와 메신저 대화는 물론, 피어 투 피어 오디오/시각적 통신을 할 수 있습니다. 에지 서버에서 특정 포트 및 프로토콜 요구 사항을 충족해야 합니다. 자세한 내용은 [Lync Server 2013에 대한 외부 A/V 방화벽 및 포트 요구 사항 확인](lync-server-2013-determine-external-a-v-firewall-and-port-requirements.md)을 참고하세요.

  - Yahoo 메신저의 경우에는 페더레이션을 제공하는 기본 에지 서버의 계획 및 배포에 일반적으로 사용되는 것과 다른 고유 요구 사항이 없습니다.

  - AOL의 경우에는 액세스 에지 서비스에 할당된 에지 서버 인증서에 클라이언트 EKU(확장된 키 사용)가 있어야 합니다.

## 이 단원의 내용

  - [인증서 요약 - 공용 인스턴트 메시징 연결](lync-server-2013-certificate-summary-public-instant-messaging-connectivity.md)

  - [포트 요약 - 공용 인스턴트 메시징 연결](lync-server-2013-port-summary-public-instant-messaging-connectivity.md)

  - [DNS 요약 - 공용 인스턴트 메시징 연결](this-topic-is-no-longer-available.md)

