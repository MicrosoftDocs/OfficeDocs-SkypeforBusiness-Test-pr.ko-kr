---
title: MSPL(Microsoft SIP Processing Language) 서버 응용 프로그램을 사용하거나 사용하지 않도록 설정
TOCTitle: MSPL(Microsoft SIP Processing Language) 서버 응용 프로그램을 사용하거나 사용하지 않도록 설정
ms:assetid: b20af38d-224a-4459-991d-0b7eabb3ca7c
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg182573(v=OCS.15)
ms:contentKeyID: 49304754
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# MSPL(Microsoft SIP Processing Language) 서버 응용 프로그램을 사용하거나 사용하지 않도록 설정

 

_**마지막으로 수정된 항목:** 2012-09-21_

Lync Server 제어판을 사용하여 Lync Server 2013 환경에서 실행하는 MSPL(Microsoft SIP Processing Language) 서버 응용 프로그램을 사용하거나 사용하지 않도록 설정할 수 있습니다. 이러한 응용 프로그램은 Microsoft Lync 2013 Preview API가 아닌 스크립팅 언어를 사용하는 스크립트 전용 응용 프로그램입니다.

일부 스크립트는 사용하거나 사용하지 않도록 설정할 수 없습니다. 예를 들어 DefaultRouting 스크립트는 사용할 수 있도록 설정되며 DefaultRouting에 대한 이 옵션은 변경할 수 없습니다.

## MSPL 서버 응용 프로그램을 사용하거나 사용하지 않도록 설정하려면

1.  RTCUniversalServerAdmins 그룹의 구성원인 사용자 계정(또는 이와 동일한 사용자 권한을 가진 사용자 계정)이나 CsServerAdministrator 또는 CsAdministrator 역할이 할당된 사용자 계정에서 Lync Server 2013을 배포한 네트워크에 있는 컴퓨터에 로그온합니다.

2.  브라우저 창을 연 다음 Admin URL을 입력하여 Lync Server 제어판을 엽니다. Lync Server 제어판을 시작하는 데 사용할 수 있는 다양한 방법에 대한 자세한 내용은 [Lync Server 관리 도구 열기](lync-server-2013-open-lync-server-administrative-tools.md)를 참조하세요.

3.  왼쪽 탐색 표시줄에서 **토폴로지**를 클릭한 다음 **서버 응용 프로그램**을 클릭합니다.

4.  **서버 응용 프로그램** 페이지에서 필요한 경우 열 머리글을 클릭하여 응용 프로그램을 정렬한 다음 수정할 서버 응용 프로그램을 클릭합니다.

5.  **동작**을 클릭합니다.

6.  **응용 프로그램 사용** 또는 **응용 프로그램 사용 안 함**(스크립트에서 이 옵션을 지원하는 경우)을 클릭합니다.

## 참고 항목

#### 작업

[MSPL(Microsoft SIP Processing Language) 응용 프로그램을 중요 또는 중요하지 않음으로 표시](lync-server-2013-mark-a-microsoft-sip-processing-language-mspl-application-as-critical-or-not-critical.md)  

#### 개념

[Lync Server 2013에서 MSPL(Microsoft SIP Processing Language) 서버 응용 프로그램 보기](lync-server-2013-view-microsoft-sip-processing-language-mspl-server-applications.md)  

#### 기타 리소스

[Lync Server 2013 토폴로지 관리](lync-server-2013-managing-the-lync-server-topology.md)

