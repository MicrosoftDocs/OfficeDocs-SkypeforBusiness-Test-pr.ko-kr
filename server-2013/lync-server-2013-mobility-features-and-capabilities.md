---
title: 'Lync Server 2013: 모바일 기능'
TOCTitle: 모바일 기능
ms:assetid: 12517a88-2531-44a5-bea5-d8884aff53eb
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Hh689983(v=OCS.15)
ms:contentKeyID: 49302865
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Lync Server 2013의 모바일 기능

 

_**마지막으로 수정된 항목:** 2013-02-19_

    The information in this topic pertains to Cumulative Updates for Lync Server 2013: February 2013.

Lync Server 2013용 누적 업데이트(2013년 2월)에 도입된 모바일 기능은 Lync 2010 Mobile 및 Lync 2013 모바일 클라이언트 기능을 지원합니다. Lync Server 2013 Mobility Service를 배포하면 사용자가 지원되는 Apple iOS, Android 및 Windows Phone 또는 Nokia Symbian 모바일 장치를 통해 인스턴트 메시지 보내기/받기, 대화 상대 보기, 현재 상태 보기 등의 작업을 수행할 수 있습니다. 또한 모바일 장치에서는 클릭하여 회의 참가, 회사번호로 전화, 단일 번호 연결, 음성 사서함, 부재 중 통화 등의 일부 Enterprise Voice 기능도 지원됩니다. Lync Server 2013용 누적 업데이트(2013년 2월)에 도입된 새로운 기능으로는 VoIP(Voice over IP) 기능 및 모임 참가자를 위한 비디오(H.264) 등이 있습니다.

Lync Server 2013용 누적 업데이트(2013년 2월)에 도입된 모바일 기능은 Lync 2013 모바일 클라이언트 기능을 지원합니다. Lync Server 2013용 누적 업데이트(2013년 2월)는 UCWA(통합 통신 웹 API)를 설치합니다. UCWA는 Lync 2013 모바일 클라이언트에 사용되는 구성 요소입니다. Lync Server 2013에서는 Mcx가 Lync 2010 Mobile 클라이언트에 사용됩니다. Lync Server 2013용 누적 업데이트(2013년 2월)에는 모바일 서비스의 새 진입점으로 UCWA가 도입되었습니다. Lync Server 2013은 Lync Server 2010용 누적 업데이트(2011년 11월)에 도입된 Mobility Service(Mcx)를 동시에 구현하며 Lync 2010 Mobile을 지원합니다. Lync Server 2013용 누적 업데이트(2013년 2월)를 배포하면 사용자가 지원되는 Apple iOS, Android 및 Windows Phone 모바일 장치를 사용하여 다음과 같은 작업을 수행할 수 있습니다.


> [!IMPORTANT]
> Lync Server 2010용 누적 업데이트(2011년 11월)의 Mobility Service가 지원하는 기능에는 (Mcx)가 표시되어 있습니다. 아래 목록의 모든 기능은 Lync Server 2013용 누적 업데이트(2013년 2월)에서 도입된 UCWA를 통해 지원됩니다.



  - 인스턴트 메시지 보내기/받기(Mcx)

  - 현재 상태 보기(Mcx)

  - 대화 상대 보기(Mcx)

  - 클릭하여 회의 참가(Mcx)

  - 회사번호로 전화(Mcx)

  - 단일 번호 연결(Mcx)

  - 음성 사서함(Mcx)

  - 부재 중 통화 알림(Mcx)

  - VoIP(Voice over IP)

  - 참가자 비디오(H.264)


> [!NOTE]
> Lync 2010 Mobile에서는 Nokia Symbian 장치용 클라이언트가 제공되었습니다. Lync 2013 Mobile에는 Nokia Symbian 기반 장치용 클라이언트가 포함되지 않습니다.



Apple iPad 사용자는 향상된 기능에 액세스할 수 있습니다. iPad 사용자는 오디오 호출을 사용하여 모임에 참가한 후 모임 내에서 업로드된 Microsoft PowerPoint 프레젠테이션을 확인하고, 응용 프로그램과 데스크톱을 공유하고, 모임 참가자 목록을 보고, 모임 내에서 공유되는 기타 콘텐츠 형식에 대한 알림을 받을 수 있습니다.


> [!TIP]
> 단일 번호 연결을 사용하는 경우 회사 번호로 걸려온 전화를 휴대폰에서 받을 수 있습니다. 회사번호로 전화 기능을 사용하는 경우에는 휴대폰 번호가 아닌 회사 전화 번호를 사용하여 Lync Mobile 클라이언트에서 발신 전화를 걸 수 있습니다. 클라이언트는 전화 걸기 기능을 사용하여 Lync Mobile 버전에 따라 Mcx 또는 UCWA로 전화 걸기 요청을 보냅니다. 그러면 서버에서는 통화를 시작한 다음 사용자의 휴대폰으로 다시 전화를 겁니다. 사용자가 전화를 받으면 서버에서 상대방에 전화를 걸어 통화를 완료합니다. 회사번호로 전화 기능을 사용하면 통화 중에 회사 번호가 표시되도록 할 수 있으므로 통화 수신자가 발신자의 휴대폰 번호를 볼 수 없으며, 발신자에게 발신 통화 요금이 부과되지 않습니다.




> [!NOTE]
> 모든 기능이 모든 모바일 장치에서 정확히 동일하게 작동하는 것은 아닙니다. 모바일 장치에서 지원되는 기능에 대한 자세한 내용은 모바일 클라이언트 비교 표( <A class=uri href="http://go.microsoft.com/fwlink/?linkid=234777">http://go.microsoft.com/fwlink/?linkid=234777</A>)를 참조하십시오. 지원되는 장치 및 운영 체제에 대한 자세한 내용은 <A href="lync-server-2013-planning-for-mobile-clients.md">Lync Server 2013의 모바일 클라이언트 계획</A>의 요구 사항 항목을 참조하십시오.



Lync Server 2013 자동 검색 기능을 사용하는 경우 모바일 응용 프로그램이 Lync Server 2013 웹 서비스를 자동으로 찾을 수 있으므로 사용자가 장치 설정에서 URL을 직접 입력할 필요가 없습니다. 그러나 모바일 장치 설정에서 URL을 수동으로 입력할 수도 있으며, 이 기능은 주로 문제 해결을 위해 사용됩니다.


> [!IMPORTANT]
> Mcx 및 UCWA는 보완 서비스이며 둘 다 Lync 2010 Mobile 및 Lync 2013 모바일 클라이언트를 지원하기 위해 배포됩니다. Lync 2013 Mobile에서는 Lync Server 2010 배포에 로그인할 수 없습니다. Lync 2010 Mobile 및 Lync 2013 Mobile에서는 Lync Server 2013용 누적 업데이트(2013년 2월)가 적용된 Lync Server 2013 배포를 사용할 수 있습니다.



모바일 기능에는 또한 백그라운드에서 실행 중인 응용 프로그램을 지원하지 않는 모바일 장치를 위한 *푸시 알림* 도 지원합니다. 푸시 알림은 모바일 응용 프로그램이 비활성화된 동안 발생하는 이벤트에 대해 모바일 장치로 발송되는 알림입니다. 예를 들어 확인하지 않은 IM(인스턴트 메시징) 초대가 있으면 푸시 알림이 발송될 수 있습니다.

Mcx, UCWA, 자동 검색 서비스 및 푸시 알림 지원은 Lync Server 2013에서 제공됩니다. 업데이트된 클라이언트 기능과 모바일 진입점으로 UCWA를 사용하는 기능은 Lync Server 2013용 누적 업데이트(2013년 2월)에 도입되었습니다.

