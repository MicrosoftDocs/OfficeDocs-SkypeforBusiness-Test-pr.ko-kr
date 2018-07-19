---
title: Lync Server 2013에서 에이전트 그룹 삭제
TOCTitle: Lync Server 2013에서 에이전트 그룹 삭제
ms:assetid: df385fd1-62f4-42b7-a349-4eb38dea50c8
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg182597(v=OCS.15)
ms:contentKeyID: 49305270
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Lync Server 2013에서 에이전트 그룹 삭제

 

_**마지막으로 수정된 항목:** 2012-11-01_

다음 절차 중 하나를 사용하여 에이전트 그룹을 삭제합니다.

## Lync Server 제어판을 사용하여 에이전트 그룹을 삭제하려면

1.  RTCUniversalServerAdmins 그룹의 구성원이나 응답 그룹을 지원하는 미리 정의된 관리 역할 중 하나의 구성원으로 로그온합니다.

2.  브라우저 창을 연 다음 Admin URL을 입력하여 Lync Server 제어판을 엽니다. Lync Server 제어판을 시작하는 데 사용할 수 있는 다양한 방법에 대한 자세한 내용은 [Lync Server 관리 도구 열기](lync-server-2013-open-lync-server-administrative-tools.md)를 참조하세요.

3.  왼쪽 탐색 모음에서 **응답 그룹**을 클릭한 다음 **그룹**을 클릭합니다.

4.  **리소스 그룹** 페이지의 검색 필드에 삭제할 에이전트 그룹의 이름 일부나 전체를 입력합니다.

5.  결과 목록에서 삭제할 그룹을 클릭하고 **편집**, **삭제**를 차례로 클릭합니다.

6.  **확인**을 클릭합니다.

## cmdlet을 사용하여 에이전트 그룹을 삭제하려면

1.  RTCUniversalServerAdmins 그룹의 구성원이나 응답 그룹을 지원하는 미리 정의된 관리 역할 중 하나의 구성원으로 로그온합니다.

2.  Lync Server 관리 셸 시작: **시작**, **모든 프로그램**, **Microsoft Lync Server 2013**을 차례로 클릭한 다음 **Lync Server 관리 셸**을 클릭합니다.

3.  명령줄에서 다음을 실행합니다.
    
        Get-CsRgsAgentGroup -Identity <Application Server service> -Name "<name of agent group>" | Remove-CsRgsAgentGroup
    
    예를 들면 다음과 같습니다.
    
        Get-CsRgsAgentGroup -Identity service:ApplicationServer:redmond.contoso.com -Name "Human Resources" | Remove-CsRgsAgentGroup

## 참고 항목

#### 작업

[Lync Server 2013에서 에이전트 그룹 만들기 또는 수정](lync-server-2013-create-or-modify-an-agent-group.md)  

#### 기타 리소스

[Remove-CsRgsAgentGroup](https://docs.microsoft.com/en-us/powershell/module/skype/Remove-CsRgsAgentGroup)  
[Get-CsRgsAgentGroup](https://docs.microsoft.com/en-us/powershell/module/skype/Get-CsRgsAgentGroup)

