---
title: MSPL(Microsoft SIP Processing Language) 응용 프로그램을 중요 또는 중요하지 않음으로 표시
TOCTitle: MSPL(Microsoft SIP Processing Language) 응용 프로그램을 중요 또는 중요하지 않음으로 표시
ms:assetid: df68fdc6-b7e6-4f07-acdc-0cd4c2c888a1
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg182598(v=OCS.15)
ms:contentKeyID: 49305278
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# MSPL(Microsoft SIP Processing Language) 응용 프로그램을 중요 또는 중요하지 않음으로 표시

 

_**마지막으로 수정된 항목:** 2012-11-01_

MSPL(Microsoft SIP Processing Language) 서버 응용 프로그램은 Microsoft Lync 2010 API가 아닌 MSPL 스크립팅 언어를 사용하는 스크립트 전용 응용 프로그램이며, 일부 MSPL 서버 응용 프로그램은 중요 응용 프로그램으로 지정됩니다. 스크립트가 중요 스크립트일 경우 Lync Server 2013을 시작하려면 시스템을 시작하는 동안 스크립트를 시작해야 합니다. Lync Server가 실행되는 동안 스크립트가 실패한 경우 서버가 종료되지는 않지만 스크립트로 트래픽이 전송되지 않으며 이벤트 로그에 오류가 작성됩니다.

Lync Server 제어판을 사용하여 MSPL(Microsoft SIP Processing Language) 서버 응용 프로그램을 중요 응용 프로그램으로 표시하거나 표시를 해제할 수 있습니다.

일부 스크립트에서는 이 옵션이 지원되지 않습니다. 예를 들어 DefaultRouting 스크립트가 중요 스크립트로 표시되었으며, DefaultRouting에 대해 이 옵션을 변경할 수 없습니다.

## MSPL 서버 응용 프로그램을 중요 응용 프로그램으로 표시하거나 표시 해제하려면

1.  RTCUniversalServerAdmins 그룹의 구성원인 사용자 계정(또는 이와 동일한 사용자 권한을 가진 사용자 계정)이나 CsServerAdministrator 또는 CsAdministrator 역할이 할당된 사용자 계정에서 Lync Server 2013을 배포한 네트워크에 있는 컴퓨터에 로그온합니다.

2.  브라우저 창을 연 다음 Admin URL을 입력하여 Lync Server 제어판을 엽니다. Lync Server 제어판을 시작하는 데 사용할 수 있는 다양한 방법에 대한 자세한 내용은 [Lync Server 관리 도구 열기](lync-server-2013-open-lync-server-administrative-tools.md)를 참조하세요.

3.  왼쪽 탐색 표시줄에서 **토폴로지**를 클릭한 다음 **서버 응용 프로그램**을 클릭합니다.

4.  **서버 응용 프로그램** 페이지에서 필요한 경우 열 머리글을 클릭하여 응용 프로그램을 정렬한 다음 수정할 서버 응용 프로그램을 클릭합니다.

5.  **동작**을 클릭합니다.

6.  **중요로 표시** 또는 **중요로 선택 해제**를 클릭합니다(즉 스크립트에서 이 옵션이 지원되는 경우).

## 참고 항목

#### 작업

[MSPL(Microsoft SIP Processing Language) 서버 응용 프로그램을 사용하거나 사용하지 않도록 설정](lync-server-2013-enable-or-disable-a-microsoft-sip-processing-language-mspl-server-application.md)  

#### 개념

[Lync Server 2013에서 MSPL(Microsoft SIP Processing Language) 서버 응용 프로그램 보기](lync-server-2013-view-microsoft-sip-processing-language-mspl-server-applications.md)  

#### 기타 리소스

[Lync Server 2013 토폴로지 관리](lync-server-2013-managing-the-lync-server-topology.md)

