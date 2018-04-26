---
title: Lync for Windows Phone 설치
TOCTitle: Lync for Windows Phone 설치
ms:assetid: bf502546-ff69-489f-a92e-a78b58803d53
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Hh690996(v=OCS.15)
ms:contentKeyID: 52056951
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Lync for Windows Phone 설치

 

_**마지막으로 수정된 항목:** 2014-02-03_

Lync 2013 for Windows Phone은 사용자가 설치할 수 있는 응용 프로그램으로, Windows Phone 마켓플레이스에서 제공됩니다.

## Lync for Windows Mobile 설치

사용자에게 Windows Phone 마켓플레이스(<http://go.microsoft.com/fwlink/?linkid=231901>)를 안내하여 장치에 Lync 2013 for Windows Phone을 설치하도록 할 수 있습니다.

## DNS SRV 레코드를 사용하여 Exchange 웹 서비스를 게시하는 경우

Lync 클라이언트에 대해 Exchange 통합을 사용하도록 설정하려면 일부 조직에서 DNS SRV 레코드를 사용하여 Exchange 웹 서비스 URL을 게시해야 합니다. Microsoft 다운로드 센터([http://go.microsoft.com/fwlink/?LinkID=391095](http://go.microsoft.com/fwlink/?linkid=391095))에서 제공하는 "Exchange 통합 이해 및 문제 해결" 문서에 이러한 작업이 필요한 시나리오에 대해 설명되어 있습니다. 하지만 Windows Phone 플랫폼에서는 SRV 조회가 지원되지 않으므로 Windows Phone 사용자의 Exchange 통합은 이 시나리오에 해당되지 않습니다. Windows Phone 사용자는 휴대폰에서 자동으로 서버를 검색하도록 허용하는 대신 Exchange 웹 서비스 URL을 지정하도록 안내해야 합니다.

사용자가 다음과 같이 해당 Windows Phone에서 Lync 설정을 구성하도록 안내합니다.

1.  Windows Phone의 Lync 설정에서 **Exchange** 화면을 선택합니다.

2.  **서버 자동 검색**을 **꺼짐**으로 이동합니다.

3.  비어 있는 필드를 탭하고 FQDN(정규화된 도메인 이름) 또는 Exchange 웹 서비스의 URL을 입력합니다.
    

    > [!NOTE]
    > FQDN(정규화된 도메인 이름)이나 Exchange 웹 서비스 서버의 전체 URL을 지정할 수 있습니다. FQDN을 지정하는 경우 프로토콜(https://)과 Exchange 웹 서비스 경로(/ews/exchange.asmx)가 자동으로 추가됩니다. Exchange 웹 서비스 경로가 다른 경우에는 전체 URL을 지정할 수 있습니다.



4.  화면을 닫습니다.

## 모바일 클라이언트 설치 확인

정상적으로 클라이언트를 구성하여 로그인한 후에는 다음 테스트를 통해 설치한 Lync 2013이 모바일 장치에서 올바르게 작동하는지 확인합니다.

**회사 디렉터리에서 대화 상대 검색**

1.  대화 상대 목록에서 아래쪽의 **검색**을 누릅니다.

2.  전체 주소 목록에만 있는 대화 상대를 검색합니다.

3.  대화 상대 이름이 검색 결과에 나타나는지 확인합니다.

**인스턴트 메시징 및 현재 상태 테스트**

1.  대화 상대 목록에서 대화 상대를 누릅니다.

2.  대화 상대 카드에서 **IM** 아이콘을 누릅니다.

3.  IM(인스턴트 메시징) 창이 나타나고 IM을 입력해 보낼 수 있는지 확인합니다.

**전화 접속 회의 테스트**

1.  Outlook에서 Lync 모임을 예약합니다.

2.  모바일 장치에서 모임 초대를 엽니다.

3.  참가할 모임의 링크를 클릭합니다.

4.  회의 서비스에서 걸려 오는 전화를 받아 모임 오디오에 연결되는지 확인합니다.

**푸시 알림 테스트**

1.  사용자 A의 모바일 장치에서 사용자 A의 계정으로 Lync에 로그인합니다.

2.  모바일 장치에서 다른 응용 프로그램을 엽니다.

3.  다른 클라이언트에서 사용자 B의 계정으로 Lync에 로그인합니다.

4.  사용자 B로부터 사용자 A에게 IM을 보냅니다.

5.  IM 알림이 사용자 A의 모바일 장치에 나타나는지 확인합니다.

