---
title: SQL Server Reporting Services 설치
TOCTitle: SQL Server Reporting Services 설치
ms:assetid: 638a1d0c-1ac7-4735-83f2-4df3d03c7cf9
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/JJ204957(v=OCS.15)
ms:contentKeyID: 49303830
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# SQL Server Reporting Services 설치

 

_**마지막으로 수정된 항목:** 2012-06-20_

Microsoft Lync Server 2013 모니터링 보고서(자세한 내용은 이 설명서의 다음 섹션 참조)를 사용하려면 먼저 SQL Server Reporting Services를 설치해야 합니다. Reporting Services는 Microsoft SQL Server를 설치할 때 동시에 설치하거나 SQL Server를 설치한 후 나중에 설치할 수 있습니다. SQL Server를 설치하지 않았으면 이 설명서의 앞 부분에 제공된 지침을 따릅니다. SQL Server를 설치할 때는 기능 선택 페이지에서 Reporting Services를 선택합니다. 그러면 SQL Server Reporting Services가 설치됩니다.

이미 SQL Server를 설치했지만 아직 SQL Server Reporting Services를 설치하지 않은 경우 필요에 따라 SQL Server 2008 R2 또는 SQL Server 2012의 적합한 지침에 따라 해당 기능을 추가할 수 있습니다.

Reporting Services가 성공적으로 설치되었는지 확인하려면 다음 단계를 수행합니다.

1.  Microsoft SQL Server 2008 R2를 실행하는 경우 **시작**, **모든 프로그램**, **Microsoft SQL Server 2008 R2**, **구성 도구**를 차례로 클릭한 후 **Reporting Services 구성 관리자**를 클릭합니다.
    
    Microsoft SQL Server 2012를 실행하는 경우 **시작**, **모든 프로그램**, **Microsoft SQL Server 2012**, **구성 도구**를 차례로 클릭한 후 **Reporting Services 구성 관리자**를 클릭합니다.

2.  **Reporting Services 구성 연결** 대화 상자의 **서버 이름** 상자에 해당 서버 이름이 표시되었는지 확인하고 모니터링 데이터가 저장되는 SQL Server 인스턴스 이름이 **보고서 서버 인스턴스** 상자에 표시되는지 확인합니다. **연결**을 클릭합니다.

Reporting Services 연결 관리자에서 보고서 서버 상태 창에는 SQL Server Reporting Services가 설치되었고 Reporting Services가 현재 실행되고 있음이 표시됩니다. 보고서 서버 상태는 **시작됨**으로 표시되어야 하며, **시작** 단추가 회색으로 표시되어 사용할 수 없는 상태여야 합니다. Reporting Service가 실행 중이 아니면 **시작**을 클릭하여 서비스를 시작합니다.

보고서 서버 데이터베이스 이름 레이블 옆에 데이터베이스가 나열되어 있지 않으면 다음을 수행합니다.

1.  Reporting Services 구성 관리자에서 **데이터베이스**를 클릭합니다.

2.  보고서 서버 데이터베이스 창에서 **데이터베이스 변경**을 클릭합니다.

3.  보고서 서버 데이터베이스 연결 마법사의 작업 창에서 **새 보고서 서버 데이터베이스 만들기**를 선택한 후 **다음**을 클릭합니다.

4.  보고서 서버 데이터베이스 구성 마법사의 데이터베이스 서버 창에서 **서버 이름**, **인증 유형** 및 **사용자 이름** 상자에 나열된 정보가 올바른지 확인합니다. **연결 테스트**를 클릭하여 데이터베이스 서버에 연결할 수 있는지 확인한 후 **다음**을 클릭합니다.

5.  보고서 서버 데이터베이스 구성 마법사의 데이터베이스 창에서 **데이터베이스 이름**, **언어** 및 **보고서 서버 모드**의 기본값을 사용하고 **다음**을 클릭합니다.

6.  보고서 서버 데이터베이스 구성 마법사의 자격 증명 창에서 **인증 유형** 드롭다운 목록 및 **사용자 이름** 및 **암호** 상자에 올바른 정보가 나열되었는지 확인한 후 **다음**을 클릭합니다.

7.  보고서 서버 데이터베이스 구성 마법사의 요약 창에서 **다음**을 클릭합니다.

8.  보고서 서버 데이터베이스 구성 마법사의 진행률 및 마침 요약 창에서 **마침**을 클릭합니다.

Reporting Services URL이 구성되었는지 확인하려면 **웹 서비스 URL**을 클릭합니다. **보고서 서버 웹 서비스 URL** 제목 아래에 하나 이상의 URL이 나열되어 있습니다. 이러한 URL을 각각 클릭하여 SQL Server Reporting Services의 로컬 설치에 대한 홈 페이지에 연결할 수 있는지 확인합니다.

