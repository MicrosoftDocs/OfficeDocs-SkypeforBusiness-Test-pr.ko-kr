---
title: 'Lync Server 2013: Standard Edition 서버 데이터베이스 설치'
TOCTitle: Standard Edition 서버 데이터베이스 설치
ms:assetid: 0bd3a804-aad6-48cb-981b-54725af032db
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg398167(v=OCS.15)
ms:contentKeyID: 49302782
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Lync Server 2013에 대한 Standard Edition 서버 데이터베이스 설치

 

_**마지막으로 수정된 항목:** 2012-10-01_

Standard Edition 서버를 인프라에서 사용자의 홈 위치가 되는 유일한 서버로 설정하는 것은 **배포 마법사** 에서 특별히 초기 서버 설치 전용 선택 항목이 제공된다는 점에서 다른 서버 설치와 다릅니다.

## Standard Edition 서버를 설치하려면

1.  Standard Edition 서버를 설치할 서버에 로컬 관리자 또는 그에 해당하는 도메인 사용자로 로그온합니다.

2.  Active Directory 도메인 서비스를 준비하지 않은 경우 먼저 해당 절차를 수행합니다. 자세한 내용은 [Lync Server 2013에 대한 Active Directory 도메인 서비스 준비](lync-server-2013-preparing-active-directory-domain-services.md)를 참조하십시오.

3.  Lync Server 배포 마법사에서 **첫 번째 Standard Edition 서버 준비** 를 클릭합니다.

4.  **단일 Standard Edition Server 준비** 페이지에서 **다음** 을 클릭합니다.

5.  **명령 실행** 페이지에서 SQL Server 2012 Express가 중앙 관리 저장소로 설치됩니다. 또한 필요한 방화벽 규칙이 만들어집니다. 데이터베이스 및 필수 구성 요소 소프트웨어 설치가 완료되면 **마침** 을 클릭합니다.
    

    > [!NOTE]
    > 초기 설치는 시간이 오래 걸릴 수 있으며 명령 출력 요약 화면에 업데이트가 표시되지 않을 수 있습니다. 이는 SQL Server Express가 설치되기 때문입니다. 데이터베이스 설치를 모니터링해야 하는 경우 작업 관리자를 사용하여 설치를 모니터링합니다.



6.  이전에 관리 도구를 설치하지 않은 경우 Lync Server 배포 마법사 페이지에서 **토폴로지 작성기 설치** 를 클릭합니다. 자세한 내용은 [Lync Server 2013 관리 도구 설치](lync-server-2013-install-lync-server-administrative-tools.md)를 참조하십시오.

7.  "Active Directory 준비", "첫 번째 Standard Edition 서버 준비" 및 "토폴로지 작성기 설치" 옆에 녹색 확인 표시가 있는지 확인합니다.

