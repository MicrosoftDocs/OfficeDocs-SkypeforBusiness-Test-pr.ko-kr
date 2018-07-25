---
title: SCOM 모니터링 구성
TOCTitle: SCOM 모니터링 구성
ms:assetid: 4003d225-2a33-448c-abd9-571750661140
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/JJ688033(v=OCS.15)
ms:contentKeyID: 49885736
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# SCOM 모니터링 구성

 

_**마지막으로 수정된 항목:** 2012-10-04_

Microsoft Lync Server 2013으로 마이그레이션한 후 System Center Operations Manager에서 작동하도록 몇 가지 Lync Server 2013 구성 작업을 완료해야 합니다.

  - 중앙 검색 논리를 관리하도록 선택된 서버에 Lync Server 2010 업데이트를 적용합니다.

  - 중앙 검색 후보 서버 레지스트리 키를 업데이트합니다.

  - 후보 중앙 검색 노드를 무시하도록 기본 System Center Operations Manager 관리 서버를 구성합니다.

이러한 각 작업의 수행 지침은 아래에 제공되어 있습니다.

**중앙 검색 논리를 관리하도록 선택된 서버에 Lync Server 2010 업데이트를 적용합니다.**

1.  System Center Operations Manager 에이전트 파일을 설치하고 후보 검색 노드로 구성할 서버를 선택합니다.

2.  이 서버에 Lync Server 2010 업데이트를 적용합니다. [Lync Server 2010 업데이트 적용](apply-lync-server-2010-updates.md) 항목을 참조하십시오.

**중앙 검색 후보 서버 레지스트리 키를 업데이트합니다.**

1.  중앙 검색 논리를 관리하도록 선택한 서버에서 Windows PowerShell 명령 창을 엽니다.

2.  명령줄에 다음을 입력합니다.
    
  ```
          New-Item -Path "HKLM:\Software\Microsoft\Real-Time Communications\Health"
  ```
  ```  
        New-Item -Path "HKLM:\Software\Microsoft\Real-Time Communications\Health\CentralDiscoveryCandidate"
  ```    

  > [!NOTE]  
  > 레지스트리를 편집할 때마다 레지스트리 키가 이미 있으면 명령이 실패했다는 오류가 발생할 수 있습니다. 이 문제가 발생할 경우 오류를 무시해도 됩니다.



**후보 중앙 검색 감시자 노드를 무시하도록 기본 System Center Operations Manager 관리 서버를 구성합니다.**

1.  System Center Operations Manager 콘솔이 설치된 컴퓨터에서 **관리 팩 개체**를 확장한 후 **개체 검색**을 선택합니다.

2.  **범위 변경...**을 클릭합니다.

3.  **관리 팩 개체 범위 지정** 페이지에서 **LS 검색 후보**를 선택합니다.

4.  **LS 검색 후보 유효 값**을 이전 절차에서 선택한 후보 서버의 이름으로 바꿉니다.

마지막으로 변경 내용을 마무리하기 위해 System Center Operations Manager 루트 관리 서버에서 상태 관리 서비스를 다시 시작합니다.

