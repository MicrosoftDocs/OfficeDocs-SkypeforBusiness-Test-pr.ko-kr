---
title: 'Lync Server 2013: Lync Server 서버 구성 요소 설치'
TOCTitle: Lync Server 서버 구성 요소 설치
ms:assetid: 186aed6e-7adf-4a92-9f2e-f9a4de5ff202
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg398239(v=OCS.15)
ms:contentKeyID: 49302943
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Lync Server 2013의 서버 구성 요소 설치

 

_**마지막으로 수정된 항목:** 2014-05-05_

다음 단계를 따르기 전에 Active Directory에 있는 RTCUniversalReadOnlyAdmins 그룹의 로컬 관리자 및 구성원 도메인 사용자 계정으로 서버에 로그온했는지 확인하세요.

Lync Server 배포 마법사는 각 Lync Server 역할에 필요한 구성 요소를 설치하고 서버를 활성화하는 데 사용됩니다. 이 문서에서는 Lync 인프라에서 Standard Edition 서버 또는 프런트 엔드 서버를 배포하는 단계를 안내합니다.

## Lync Server 구성 요소를 설치하려면

1.  Lync Server 배포 마법사를 실행하고 있지 않은 경우 Lync를 설치하려는 서버에서 시작합니다.

2.  **Lync Server 시스템 설치 또는 업데이트**를 클릭합니다.

3.  배포 마법사에서 **1단계: 로컬 구성 저장소 설치**에 녹색 확인 표시가 있는지 확인합니다. 이 표시는 이 서버에 저장소의 로컬 복사본이 성공적으로 설치되었음을 의미합니다. 이 표시가 없으면 서버에 로컬 구성 저장소를 설치해야 합니다. [Lync Server 2013에서 로컬 구성 저장소 설치](lync-server-2013-install-the-local-configuration-store.md)의 단계를 따른 다음 여기로 다시 돌아옵니다.

4.  서버에 Lync Server 2013 구성 요소를 설치할 준비가 되었으면 **2단계: Lync Server 구성 요소 설치 또는 제거** 옆의 **실행**을 클릭합니다.

5.  **Lync Server 구성 요소 설치** 페이지에서 **다음**을 클릭하여 게시된 토폴로지에 정의된 대로 구성 요소를 설치합니다.

6.  설치가 진행되면서 **명령 실행** 페이지에 설치 진행 정보 및 명령 요약이 표시됩니다. 설치가 완료되면 목록을 통해 보려는 로그를 선택하고 **로그 보기**를 클릭하면 됩니다.

7.  Lync Server 2013 구성 요소 설치가 완료되고 필요한 대로 로그 검토를 마쳤으면 **마침**을 클릭하여 설치의 이 단계를 완료합니다.
    

    > [!NOTE]
    > 서버를 다시 시작하라는 메시지가 표시되면(Windows Desktop Experience를 설치해야 하는 경우 다시 시작해야 할 수 있음) 반드시 다시 시작합니다. 컴퓨터가 다시 시작되고 실행되면 이 절차를 3단계부터 반복합니다(배포 마법사의 2단계 다시 실행).


