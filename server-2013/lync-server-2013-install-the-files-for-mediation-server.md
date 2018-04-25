---
title: 'Lync Server 2013: 중재 서버용 파일 설치'
TOCTitle: 중재 서버용 파일 설치
ms:assetid: f0f7dd15-58e1-40fd-aa7e-6db50ceafacd
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg412998(v=OCS.15)
ms:contentKeyID: 49305482
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Lync Server 2013에서 중재 서버용 파일 설치

 

_**마지막으로 수정된 항목:** 2012-08-06_

이 절차를 성공적으로 완료하려면 최소한 RTCUniversalReadOnlyAdmins 그룹의 구성원인 로컬 관리자 및 도메인 사용자 이상의 권한으로 서버에 로그온해야 합니다.

이 항목의 단계에 따라 Lync Server 2013 배포 마법사를 실행하여 토폴로지 작성기를 통해 풀을 정의하고 게시할 때 중재 서버 풀에 추가한 컴퓨터에 중재 서버용 파일을 설치할 수 있습니다. 중재 서버용 파일을 설치할 때 중재 서버 풀의 각 컴퓨터에 필요한 인증서를 설치 및 할당해야 합니다.

이 사이트에 프런트 엔드 풀 또는 Standard Edition 서버에 배치된 중재 서버을 이미 배포한 경우 이 항목을 건너뛰고 대신 [Lync Server 2013에서 트렁크 구성](lync-server-2013-configuring-trunks.md)을 계속할 수 있습니다.


> [!NOTE]
> 이 항목에서는 배포 설명서의 <A href="lync-server-2013-define-a-mediation-server-in-topology-builder.md">Lync Server 2013의 토폴로지 작성기에서 중재 서버 정의</A> 및 <A href="lync-server-2013-publish-the-topology.md">Lync Server 2013에서 토폴로지 게시</A>에 설명된 대로 독립 실행형 중재 서버 풀을 이미 정의하고 게시했으며, 중재 서버 풀의 컴퓨터가 <A href="lync-server-2013-software-prerequisites-for-enterprise-voice.md">Lync Server 2013의 Enterprise Voice에 대한 소프트웨어 필수 구성 요소</A> 및 <A href="lync-server-2013-security-and-configuration-prerequisites-for-enterprise-voice.md">Lync Server 2013의 Enterprise Voice에 대한 보안 및 구성 필수 구성 요소</A>에 설명된 필수 구성 요소를 충족하는 것을 확인한 것으로 가정합니다.



## 독립 실행형 중재 서버 풀용 파일을 설치하려면

1.  설치 미디어에서 *\<설치 미디어\>* **\\Setup\\amd64\\Setup.exe** 를 마우스 오른쪽 단추로 클릭하고 **관리자 권한으로 실행** 을 클릭합니다.

2.  **설치 위치** 페이지에서 **확인** 을 클릭합니다.

3.  **최종 사용자 사용권 계약** 페이지에서 **동의함** 을 클릭한 다음 **확인** 을 클릭합니다. 계속하려면 반드시 클릭해야 합니다.

4.  **Lync Server 2010 배포 마법사** 페이지에서 **Lync Server 시스템 설치 또는 업데이트** 를 클릭합니다.

5.  **1단계: 로컬 구성 저장소 설치** 옆에 있는 **실행** 을 클릭한 다음 화면의 지시를 따릅니다.

6.  **중앙 관리 저장소의 로컬 복제본 구성** 페이지에서 기본값인 **중앙 관리 저장소에서 직접 검색** 을 적용하고 **다음** 을 클릭합니다.

7.  **명령 실행** 페이지에서 작업 상태가 **완료됨** 으로 표시되면 **마침** 을 클릭합니다.

8.  **2단계: Lync Server 구성 요소 설치 또는 제거** 옆에 있는 **실행** 을 클릭하고 **다음** 을 클릭합니다.

9.  **명령 실행** 페이지에서 작업 상태가 **완료됨** 으로 표시되면 **마침** 을 클릭합니다.

10. **3단계: 인증서 요청, 설치 또는 할당** 에서 **실행** 을 클릭합니다. 화면의 지시에 따라 기본 설정을 적용합니다. 중재 서버에는 하나의 인증서가 필요하므로 **3단계** 를 두 번 실행합니다. 즉, 한 번은 필요한 인증서를 발급하기 위해 실행하고, 또 한 번은 인증서를 할당하기 위해 실행합니다.

11. 인증서가 올바르게 발급 및 할당되면 **4단계: 서비스 시작** 옆에 있는 **실행** 을 클릭한 다음 화면의 지시를 따릅니다.

12. **4단계** 가 성공적으로 완료되면 서버를 다시 시작하고 DomainAdmins 그룹의 구성원으로 서버에 로그온합니다.

13. Lync Server 제어판을 실행하는 컴퓨터에서 Lync Server 제어판의 **토폴로지** 페이지에 중재 서버의 서비스 상태가 녹색 확인 표시로 표시되어 있는지 확인합니다. 빨간색 X가 표시된 경우에는 중재 서버를 선택합니다. **동작** 메뉴에서 **모든 서비스 시작** 을 클릭합니다.

중재 서버 풀에 둘 이상의 컴퓨터를 추가한 경우 중재 서버 풀의 다른 모든 컴퓨터에서 이 절차의 단계를 수행합니다. 중재 서버용 파일을 다른 컴퓨터에 설치할 필요가 없으면 [Lync Server 2013에서 트렁크 구성](lync-server-2013-configuring-trunks.md)의 절차에 따라 이 중재 서버 풀(또는 사이트의 모든 중재 서버)과 해당 피어 간의 트렁크 연결 설정을 구성합니다.

## 참고 항목

#### 개념

[Lync Server 2013의 내부 서버에 대한 인증서 요구 사항](lync-server-2013-certificate-requirements-for-internal-servers.md)

