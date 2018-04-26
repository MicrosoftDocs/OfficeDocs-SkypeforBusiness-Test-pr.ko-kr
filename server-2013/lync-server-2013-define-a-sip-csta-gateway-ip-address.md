---
title: 'Lync Server 2013: SIP/CSTA 게이트웨이 IP 주소 정의'
TOCTitle: SIP/CSTA 게이트웨이 IP 주소 정의
ms:assetid: ae944057-3ad6-4474-a09b-81a3d27bd50f
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg602125(v=OCS.15)
ms:contentKeyID: 49304716
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Lync Server 2013에서 SIP/CSTA 게이트웨이 IP 주소 정의

 

_**마지막으로 수정된 항목:** 2012-09-21_

Lync Server가 TCP(전송 제어 프로토콜) 연결을 사용하여 원격 통화 제어를 위한 배포된 SIP/CSTA 게이트웨이에 연결된 경우 토폴로지 작성기에서 게이트웨이의 IP 주소를 정의해야 합니다. TLS(전송 계층 보안) 연결을 지원하는 게이트웨이에는 이 단계가 필요하지 않습니다. TLS 연결을 지원하는 모든 게이트웨이에 대해서는 이 절차를 건너뛰고 [Lync Server 2013에서 Lync 사용자가 원격 통화 제어를 사용하도록 설정](lync-server-2013-enable-lync-users-for-remote-call-control.md)의 단계를 수행하여 원격 통화 제어를 계속 배포할 수 있습니다.

## 토폴로지 작성기를 사용하여 SIP/CSTA 게이트웨이 IP 주소를 정의하려면

1.  토폴로지 작성기가 Domain Admins 그룹 및 RTCUniversalServerAdmins 그룹의 구성원으로 설치되어 있는 컴퓨터에 로그온합니다.

2.  토폴로지 작성기 시작: **시작**, **모든 프로그램**, **Microsoft Lync Server 2013**을 차례로 클릭한 다음 **Lync Server 토폴로지 작성기**를 클릭합니다.

3.  기존 토폴로지를 다운로드하도록 옵션을 선택합니다.

4.  **신뢰할 수 있는 응용 프로그램 서버** 노드를 확장합니다.

5.  [Lync Server 2013에서 원격 통화 제어를 위한 신뢰할 수 있는 응용 프로그램 항목 구성](lync-server-2013-configure-a-trusted-application-entry-for-remote-call-control.md)에서 설명한 대로 만든 신뢰할 수 있는 응용 프로그램 풀을 마우스 오른쪽 단추로 클릭한 다음 **속성 편집** 을 클릭합니다.

6.  **이 풀에 대한 구성 데이터 복제 사용** 확인란의 선택을 취소합니다.

7.  **선택한 IP 주소로 서비스 사용 제한** 을 클릭합니다. 기본 설정은 **구성된 모든 IP 주소 사용** 입니다.

8.  **기본 IP 주소** 텍스트 상자에 SIP/CSTA 게이트웨이의 IP 주소를 입력합니다.

9.  중앙 관리 저장소에서 토폴로지를 업데이트하려면 콘솔 트리에서 **Lync Server** 를 클릭하고 **동작** 창에서 **게시** 를 클릭합니다.

## 참고 항목

#### 작업

[Lync Server 2013에서 원격 통화 제어에 대한 고정 경로 구성](lync-server-2013-configure-a-static-route-for-remote-call-control.md)  
[Lync Server 2013에서 원격 통화 제어를 위한 신뢰할 수 있는 응용 프로그램 항목 구성](lync-server-2013-configure-a-trusted-application-entry-for-remote-call-control.md)

