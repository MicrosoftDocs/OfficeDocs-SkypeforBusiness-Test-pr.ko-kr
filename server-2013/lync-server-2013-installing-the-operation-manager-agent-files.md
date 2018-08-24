---
title: Operation Manager Agent 파일 설치
TOCTitle: Operation Manager Agent 파일 설치
ms:assetid: e2246c44-0c75-43fc-8b04-26e53c5dd572
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/JJ205345(v=OCS.15)
ms:contentKeyID: 49305308
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Operation Manager Agent 파일 설치

 

_**마지막으로 수정된 항목:** 2012-10-20_

컴퓨터에 Operations Manager 에이전트 파일을 설치하려면 다음 단계를 수행하십시오.

1.  System Center 설치 미디어에서 **SetupOM.exe**를 두 번 클릭합니다.

2.  System Center Operation Manager 설치 프로그램에서 <strong>Operations Manager 에이전트 설치(Install Operations Manager Agent)</strong>를 클릭합니다.

3.  System Center 설치 마법사의 **System Center Operations Manager 설치 시작(Welcome to the System Center Operations Manager Setup)** 마법사 페이지에서 **다음**을 클릭합니다.

4.  **대상 폴더** 페이지에서 Operations Manager 에이전트 파일이 설치될 폴더를 선택하고 **다음**을 클릭합니다.

5.  **관리 그룹 구성** 페이지에서 **관리 그룹 정보 지정**을 선택하고 **다음**을 클릭합니다.

6.  **관리 그룹 구성** 페이지의 **관리 그룹 이름** 상자에 Operations Manager 관리 그룹의 이름을 입력하고 **관리 서버** 상자에 Operations Manager 서버의 이름(예: atl-scom-001)을 입력합니다. Operations Manager에 사용되는 포트 번호를 변경한 경우 관리 서버 포트 상자에 새 포트 번호를 입력합니다. 그렇지 않으면 기본값인 5723을 포트로 그대로 사용하고 **다음**을 클릭합니다.

7.  **에이전트 작업 계정** 페이지에서 **로컬 시스템**을 선택하고 **다음**을 선택합니다.

8.  **Microsoft Update** 페이지에서 <strong>Microsoft Update 사용 안 함(I don't want to use Microsoft Update)</strong>을 선택하고 **다음**을 클릭합니다.

9.  **설치 준비 완료** 페이지에서 **설치**를 클릭합니다.

10. **System Center Operations Manager 설치 마법사 완료 중(Completing the System Center Operations Manager Setup wizard)** 페이지에서 **마침**을 클릭합니다.

11. **끝내기**를 클릭합니다.

System Center 2007 R2를 사용하는 경우 **시작**, **모든 프로그램**, **System Center Operations Manager 2007 R2** 및 **Operations Manager Shell**을 차례대로 클릭하여 에이전트가 만들어졌는지 확인할 수 있습니다. Operations Manager Shell에서 다음 Windows PowerShell 명령을 입력하고 Enter 키를 누릅니다.

    Get-Agent 

모든 Operations Manager 에이전트 목록이 화면에 나타납니다.

System Center 2012를 사용하는 경우 Operations 2012 Manager Shell에서 다음 명령을 실행합니다.

    Get-SCOMAgent

