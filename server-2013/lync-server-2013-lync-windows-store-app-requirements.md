---
title: Lync Server 2013용 Lync Windows 스토어 앱 요구 사항
TOCTitle: Lync Server 2013용 Lync Windows 스토어 앱 요구 사항
ms:assetid: 5f2e0a40-8450-4f61-b6f6-913fc1906020
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/JJ823129(v=OCS.15)
ms:contentKeyID: 52056864
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Lync Server 2013용 Lync Windows 스토어 앱 요구 사항

 

_**마지막으로 수정된 항목:** 2013-12-03_

Lync Server의 온-프레미스 배포를 사용하는 조직에서는 Lync Windows 스토어 앱을 지원하기 위해 다음 요구 사항을 충족해야 합니다.


> [!NOTE]
> Lync Server 2010의 경우 모든 서버에서 Lync Server 2010용 누적 업데이트(2012년 2월)(<A class=uri href="http://go.microsoft.com/fwlink/?linkid=3052%26kbid=2670352">http://go.microsoft.com/fwlink/?linkid=3052&amp;kbid=2670352</A>에 제공됨) 이상을 실행해야 합니다. 사용자가 모임에 참가할 수 있도록 설정하려면 모든 서버에서 Lync Server 2010: 2012년 10월 누적 업데이트(<A class=uri href="http://go.microsoft.com/fwlink/?linkid=3052%26kbid=2737915">http://go.microsoft.com/fwlink/?linkid=3052&amp;kbid=2737915</A>에 제공됨)를 실행해야 합니다.



  - 서버에 자동 검색, Lync Web App 및 웹 티켓 서비스를 설정합니다.

  - 프런트 엔드 서버 또는 프런트 엔드 풀에서 인증서 인증을 설정합니다(프런트 엔드 서버 또는 프런트 엔드 풀에서 사용자 등록 과정을 등록 기관이라고 함). 자세한 내용은 [고급 등록자 구성 설정 만들기](lync-server-2013-create-registrar-configuration-settings.md)를 참고하세요.

  - 자동 검색 서비스에 대한 DNS 별칭(CNAME) 리소스 레코드를 게시합니다.

  - Lync Server에 발급된 인증서의 CDP(CRL(인증서 해지 목록) 배포 지점)가 LDAP 리소스가 아닌 HTTP 리소스를 가리키는지 확인하지 않아도 됩니다. 하지만 클라이언트 컴퓨터에 최신 Windows 업데이트 버전이 설치되어 있는지 확인해야 합니다.

  - Lync Server 관련 HTTP 트래픽을 허용하도록 기업의 HTTP 프록시를 구성합니다. 필요한 경우 자동 검색, Lync Web App, 웹 티켓 서비스에 대한 예외를 추가합니다.

  - 클라이언트에서 Windows 8.1 및 Lync Windows 스토어 앱의 최신 버전을 설치하여 여러 도메인을 사용하는 경우 일반적으로 발생하는 로그인 문제를 해결합니다(예: SIP URI가 **userA@domainZ.com**이지만 에지 서버가 **sip.domainX.com**인 경우).

조직이 Lync Online 또는 Office 365에 등록하고 사용자가 자신의 도메인 이름을 사용하고 있는 경우 Lync Server의 자동 검색에 대한 네트워크를 설정하기 위해 추가 단계를 수행해야 합니다. 네트워크 구성 요구 사항은 Lync Windows 스토어 앱 및 모바일 장치의 Lync와 동일합니다. [http://go.microsoft.com/fwlink/?LinkId=271822](http://go.microsoft.com/fwlink/?linkid=271822)에 제공되는 Office 365 위키 문서 “Lync 모바일 장치 설정(영어)”의 "네트워크 설정" 지침을 참고하세요.

## 참고 항목

#### 개념

[Lync Windows 스토어 앱 배포](lync-server-2013-deploying-lync-windows-store-app.md)

