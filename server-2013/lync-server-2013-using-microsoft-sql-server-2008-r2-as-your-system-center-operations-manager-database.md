---
title: Microsoft SQL Server 2008 R2를 System Center Operations Manager 데이터베이스로 사용
TOCTitle: Microsoft SQL Server 2008 R2를 System Center Operations Manager 데이터베이스로 사용
ms:assetid: 0efe76da-8854-499e-bdc7-3623244a8e85
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/JJ687969(v=OCS.15)
ms:contentKeyID: 49885648
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Microsoft SQL Server 2008 R2를 System Center Operations Manager 데이터베이스로 사용

 

_**마지막으로 수정된 항목:** 2013-07-29_

SQL Server 2008 R2를 백 엔드 데이터베이스로 사용하려면 이 항목에서 설명하는 단계를 완료합니다.

## SQL Server 2008 R2 및 SQL Server Reporting Services 구성

System Center Operations Manager 설치를 시작하기 전에 SQL Server 2008 R2 및 SQL Server Reporting Services 구성에서 두 가지 항목을 변경해야 합니다. 이러한 변경은 SQL Server 2008 R2를 Operations Manager 데이터베이스로 사용하는 경우에만 수행하면 됩니다. 먼저 Operations Manager 데이터베이스를 호스팅할 컴퓨터에서 다음을 수행합니다.

1.  **시작**을 클릭한 다음 **실행**을 클릭합니다.

2.  **실행** 대화 상자에 **C:\\Program Files\\Microsoft SQL Server\\ MSRS10\_50.ARCHINST\\Reporting Services\\ReportServer**를 입력하고 Enter 키를 누릅니다.

3.  **ReportServer** 폴더에서 **rsreportserver.config** 파일을 메모장 또는 기타 텍스트 편집기에서 엽니다.

4.  파일 시작 부분에 일련의 "Add Key" 노드가 표시됩니다. **\<Add Key="SecureConnectionLevel"**로 시작하는 항목을 찾아서 값을 **0**으로 설정합니다.
    
        <Add Key="SecureConnectionLevel" Value="0"/>

5.  **rsreportserver.config** 파일을 저장하고 텍스트 편집기를 닫습니다.

보고서 서버 구성 파일을 업데이트한 후에는 올바른 인증서를 SQL Server Reporting Services에 할당해야 합니다. 이렇게 하려면 다음을 수행합니다.

1.  **시작**, **모든 프로그램**, **Microsoft SQL Server 2008 R2**, **구성 도구**, **Reporting Services 구성 관리자**를 차례로 클릭합니다.

2.  **Reporting Services 구성 연결** 대화 상자의 **서버 이름** 상자에 서버의 이름이 나타나는지 확인합니다. Operations Manager 데이터베이스를 호스팅할 SQL Server 인스턴스(예: **ARCHINST**)를 **보고서 서버 인스턴스** 드롭다운 목록에서 선택하고 **연결**을 클릭합니다.

3.  Reporting Services 구성 관리자에서 **웹 서비스 URL**을 클릭합니다.

4.  **웹 서비스 URL** 페이지의 **SSL 인증서** 드롭다운 목록에서 Reporting Services에 사용할 인증서를 선택하고 **적용**을 클릭합니다. 그러면 몇 초 후에 **보고서 서버 웹 서비스 URL** 아래에 URL 한 쌍이 나열됩니다.

5.  두 URL을 모두 클릭하여 SQL Server Reporting Services에 액세스할 수 있는지 확인합니다.

6.  Reporting Services 구성 관리자를 닫습니다.

## SQL Server 2008 R2에 사용할 System Center Operations Manager 데이터베이스 만들기

SQL Server 2008 R2 데이터베이스를 사용하도록 System Center Operations Manager를 구성하려면 SQL Server 2008 R2를 실행하는 컴퓨터에서 Operations Manager 데이터베이스를 "수동으로" 만들어야 합니다. 여기서도 마찬가지로 SQL Server 2005 또는 SQL Server 2008을 백 엔드 데이터베이스로 사용하는 경우에는 이러한 단계를 수행할 필요가 없습니다.

Operations Manager 데이터베이스를 수동으로 만들려면 다음을 수행합니다.

1.  System Center Operations Manager 2007 R2 설치 미디어의 SupportTools\\AMD64 폴더에서 **DBCreateWizard.exe**를 두 번 클릭합니다.

2.  데이터베이스 구성 마법사의 **데이터베이스 구성 마법사 시작** 페이지에서 **다음**을 클릭합니다.

3.  **데이터베이스 정보** 페이지에서 모든 설정을 그대로 두고 **다음**을 클릭합니다.

4.  **관리 그룹 구성** 페이지의 **관리 그룹 이름** 상자에 관리 그룹의 이름을 **Lync Server 모니터링**과 같이 입력하고 **다음**을 클릭합니다.

5.  **Operations Manager 오류 보고서** 페이지에서 **다음**을 클릭합니다.

6.  **요약** 페이지에서 **마침**을 클릭합니다.

## SQL Server 2008 R2에 사용할 System Center Operations Manager 데이터 웨어하우스 만들기

Microsoft Lync Server 2013에서는 새로운 System Center Operations Manager 보고서 3개가 제공됩니다.

  - **종단 간 시나리오 가용성 보고서**   이 보고서에서는 등록, 현재 상태 등의 주요 Lync Server 서비스에 대한 가용성/가동률 정보를 자세하게 제공합니다.

  - **용량 보고서**   이 보고서에서는 성능 카운터 정보를 사용하여 메모리 가용성, 프로세서 사용량 등의 시스템 구성 요소 추세를 보여 줍니다.

  - **구성 요소 보고서**   이 보고서에서는 Lync Server 구성 요소별로 그룹화된 상위 경고 생성 요소의 목록을 제공합니다.

이러한 새 보고서를 사용하려면 System Center Operations Manager 데이터 웨어하우스를 설치해야 합니다. 데이터 웨어하우스는 작업 데이터에 대한 장기적인 저장소를 제공합니다. SQL Server 2008 R2에서 데이터 웨어하우스를 사용하려면 SQL Server 데이터베이스를 호스팅하는 컴퓨터에서 다음 단계를 수행해야 합니다.

1.  System Center Operations Manager 설치 미디어의 Setup\\SupportTools\\AMD64 폴더에서 **DBCreateWizard.exe**를 두 번 클릭합니다.

2.  데이터베이스 구성 마법사의 **데이터베이스 구성 마법사 시작** 페이지에서 **다음**을 클릭합니다.

3.  **데이터베이스 정보** 페이지의 **데이터베이스 유형** 드롭다운 목록에서 **Operations Manager 데이터 웨어하우스 데이터베이스**를 선택하고 **다음**을 클릭합니다.

4.  **요약** 페이지에서 **마침**을 클릭합니다.

## System Center Operations Manager 콘솔 설치

Operations Manager 콘솔은 System Center Operations Manager를 관리하는 데 기본적으로 사용되는 도구입니다. Operations Manager 콘솔을 설치하기 전에 SQL Server Reporting Services와 함께 지원되는 SQL Server 버전을 설치했는지 확인하세요. 또한 SQL Server의 Reporting Services 구성 관리자를 실행하여 Reporting Services가 올바르게 설치 및 구성되었는지를 확인하는 것이 좋습니다.

System Center Operations Manager 콘솔을 설치하려면

1.  System Center Operations Manager 설치 미디어에서 **SetupOM.exe**를 두 번 클릭합니다.

2.  System Center Operations Manager 2007 R2 설치 프로그램에서 **필수 구성 요소 검사**를 클릭합니다.

3.  System Center Operations Manager 필수 뷰어에서 설치할 System Center 구성 요소(**서버**, **콘솔**, **PowerShell**)를 선택한 후에 **검사**를 클릭합니다. 설치를 차단하는 문제가 보고되지 않았는지 확인하고 **닫기**를 클릭합니다. 설치를 차단하는 문제가 보고된 경우 문제를 해결하고 **검사**를 클릭하여 필수 구성 요소 테스트를 다시 실행합니다.

4.  System Center Operations Manager 설치 프로그램에서 **Operations Manager 설치**를 클릭합니다.

5.  System Center Operations Manager 설치 마법사의 **System Center Operations Manager 설치 마법사 시작** 페이지에서 **다음**을 클릭합니다.

6.  **최종 사용자 사용권 계약** 페이지에서 **동의함**을 선택하고 **다음**을 클릭합니다.

7.  **제품 등록** 페이지의 **사용자 이름** 상자에는 자신의 이름을, **조직** 상자에는 조직의 이름을 입력합니다. **25자리 CD 키 입력** 상자에는 System Center Operations Manager 제품 키를 입력하고 **다음**을 클릭합니다.

8.  **사용자 지정 설치** 페이지에서 설치할 System Center 옵션을 선택하고 **다음**을 클릭합니다. **관리 서버**, **사용자 인터페이스** 및 **웹 콘솔**을 설치하도록 선택해야 합니다. **데이터베이스**는 선택 및 설치하면 안 됩니다.

9.  **SC 데이터베이스 서버 인스턴스** 페이지에서 Operations Manager 데이터베이스가 설치되어 있는 컴퓨터의 이름이 **System Center 데이터베이스 서버** 상자에 나타나는지 확인합니다. **다음**을 클릭합니다.

10. **관리 서버 작업 계정** 페이지에서 **도메인 또는 로컬 컴퓨터 계정**을 선택하고 **사용자 계정**, **암호** 및 **도메인 또는 로컬 컴퓨터** 상자에 적절한 값을 입력합니다. **다음**을 클릭합니다.

11. **SDK 및 구성 서비스 계정** 페이지에서 **도메인 또는 로컬 컴퓨터 계정**을 선택하고 **사용자 계정**, **암호** 및 **도메인 또는 로컬 컴퓨터** 상자에 적절한 값을 입력합니다. **다음**을 클릭합니다.

12. **Operations Manager 오류 보고서** 페이지에서 **다음**을 클릭합니다.

13. **사용자 환경 개선 프로그램** 페이지에서 **다음**을 클릭합니다.

14. **프로그램을 설치할 준비가 되었습니다.** 페이지에서 **설치**를 클릭합니다.

15. **System Center Operations Manager 설치 완료** 페이지에서 **암호화 키 백업** 및 **콘솔 시작** 확인란 선택을 취소하고 **마침**을 클릭합니다.

16. System Center Operations Manager 설치 프로그램에서 **끝내기**를 클릭합니다.

## System Center Reporting Services 설치

System Center Operations Manager 콘솔을 설치 및 구성한 후에는 System Center Reporting Services를 설치해야 합니다. SQL Server 2008 R2를 Operations Manager 백 엔드 데이터베이스로 사용하는 경우에는 먼저 SQL Server Reporting Services와 연결된 보안 그룹을 임시로 변경해야 합니다. SQL Server 2008 R2를 사용하는 경우 다음을 수행해야 합니다.

1.  **시작**을 클릭하고 **관리 도구**를 가리킨 다음 **서버 관리자**를 클릭합니다.

2.  서버 관리자에서 **구성**, **로컬 사용자 및 그룹**을 차례로 확장한 다음 **그룹**을 클릭합니다.

3.  **SQLServerReportServerUser$atl-sc-001$MSRS10\_50.ARCHINST** 그룹을 찾습니다(atl-sc-001은 컴퓨터의 이름을, ARCHINST는 System Center 데이터베이스의 SQL Server 인스턴스를 나타냄).

4.  그룹을 마우스 오른쪽 단추로 클릭하고 **이름 바꾸기**를 클릭합니다. 그런 다음 그룹 이름에서 **\_50**을 삭제하여 그룹 이름을 바꿉니다. 예를 들어 이름을 **SQLServerReportServerUser$atl-sc-001$MSRS10.ARCHINST**와 같이 바꿉니다.

5.  서버 관리자를 닫습니다.

이제 System Center Reporting Services를 설치할 수 있습니다. 설치하려면 다음을 수행합니다.

1.  System Center Operations Manager 2007 R2 설치 미디어에서 **SetupOM.exe**를 두 번 클릭합니다.

2.  System Center Operations Manager 2007 R2 설치 프로그램에서 **Operations Manager Reporting 설치**를 클릭합니다.

3.  System Center Operations Manager 2007 R2 Reporting 설치 마법사의 **Operations Manager Reporting 설치 시작** 페이지에서 **다음**을 클릭합니다.

4.  **최종 사용자 사용권 계약** 페이지에서 **동의함**을 선택하고 **다음**을 클릭합니다.

5.  **제품 등록** 페이지의 **사용자 이름** 및 **조직** 상자에 자신의 이름과 조직의 이름이 각각 나타나는지 확인하고 **다음**을 클릭합니다.

6.  **사용자 지정 설치** 페이지에서 **보고 서버**를 클릭하고 **이 구성 요소와 모든 종속 구성 요소는 로컬 디스크 드라이브에 설치됩니다.**를 선택합니다. **데이터 웨어하우스**를 클릭하고 **이 구성 요소를 사용할 수 없게 됩니다.**를 선택한 후에 **다음**을 클릭합니다.

7.  **루트 관리 서버에 연결** 페이지의 **루트 관리 서버** 상자에 Operations Manager 루트 관리 서버의 이름을 입력하고 **다음**을 클릭합니다.

8.  **Operations Manager 데이터 웨어하우스에 연결** 페이지의 **SQL Server 인스턴스** 상자에 데이터 웨어하우스가 있는 SQL Server 인스턴스를 입력합니다. 데이터 웨어하우스가 기본 인스턴스에 있는 경우에는 atl-sql-001과 같이 서버 이름만 입력합니다. 데이터베이스 이름 **OperationsManagerDW**가 **이름** 상자에, 포트 **1433**이 **SQL Server 포트** 상자에 나타나는지 확인합니다. **다음**을 클릭합니다.

9.  **SQL Server Reporting 인스턴스** 페이지의 **SQL Server Reporting Services 서버 입력** 드롭다운 목록에서 SQL Server 보고 서버를 선택하고 **다음**을 클릭합니다.

10. **데이터 웨어하우스 쓰기 계정** 페이지의 **사용자 계정** 및 **암호** 상자에 데이터 웨어하우스 쓰기 권한을 처음 할당할 사용자의 이름과 암호를 입력합니다. **도메인** 드롭다운 목록에서 사용자 도메인을 선택하고 **다음**을 클릭합니다.

11. **데이터 판독기 계정** 페이지의 **사용자 계정** 및 **암호** 상자에 SQL Reporting Services에서 데이터 웨어하우스를 쿼리할 때 사용할 사용자 계정의 이름과 암호를 입력합니다. **도메인** 드롭다운 목록에서 계정 도메인을 선택하고 **다음**을 클릭합니다.

12. **운영 데이터 보고서** 페이지에서 **다음**을 클릭합니다.

13. **Microsoft 업데이트** 페이지에서 **다음**을 클릭합니다.

14. **프로그램을 설치할 준비가 되었습니다.** 페이지에서 **설치**를 클릭합니다.

15. **Operations Manager Reporting Components 설치 마법사 완료** 페이지에서 **마침**을 클릭합니다.

16. System Center Operations Manager 2007 R2 설치 프로그램에서 **끝내기**를 클릭합니다.

System Center 보고를 설치한 후에는 다음 절차에 따라 SQL Server 보고와 연결된 보안 그룹의 이름을 다시 설정합니다. 이 절차 역시 SQL Server를 사용하는 경우에만 수행하면 됩니다.

1.  **시작**을 클릭하고 **관리 도구**를 가리킨 다음 **서버 관리자**를 클릭합니다.

2.  서버 관리자에서 **구성**, **로컬 사용자 및 그룹**을 차례로 확장한 다음 **그룹**을 클릭합니다.

3.  **SQLServerReportServerUser$atl-sc-001$MSRS10\_50.ARCHINST** 그룹을 찾습니다(atl-sc-001은 컴퓨터의 이름을, ARCHINST는 보관 및 모니터링 데이터베이스의 SQL Server 인스턴스를 나타냄).

4.  그룹을 마우스 오른쪽 단추로 클릭하고 **이름 바꾸기**를 클릭합니다. 그런 다음 그룹 이름 끝의 SQL Server 인스턴스 이름 바로 앞에 **\_50**을 추가하여 그룹 이름을 바꿉니다. 예를 들어 이름을 **SQLServerReportServerUser$atl-sc-001$MSRS10\_50.ARCHINST**와 같이 바꿉니다.

5.  서버 관리자를 닫습니다.

System Center 운영 콘솔이 열려 있으면 응용 프로그램을 닫았다가 다시 시작해야 하며, 이렇게 하지 않으면 운영 콘솔 사용자 인터페이스에 **보고** 탭이 나타나지 않습니다. 운영 콘솔을 처음으로 다시 시작하면 모든 모니터링 보고서가 **보고** 탭에 표시될 때까지 몇 분 정도 걸릴 수 있습니다.

