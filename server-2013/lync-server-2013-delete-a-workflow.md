---
title: 워크플로 삭제
TOCTitle: 워크플로 삭제
ms:assetid: 0469a6b8-ce1e-459b-bc3d-4c8adf2d97d5
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg520944(v=OCS.15)
ms:contentKeyID: 49302662
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# 워크플로 삭제

 

_**마지막으로 수정된 항목:** 2012-11-01_

다음 절차 중 하나를 수행하여 워크플로를 삭제합니다.

## Lync Server 제어판을 사용하여 워크플로를 삭제하려면

1.  RTCUniversalServerAdmins 그룹의 구성원이나 응답 그룹을 지원하는 미리 정의된 관리 역할 중 하나의 구성원으로 로그온합니다.

2.  브라우저 창을 연 다음 Admin URL을 입력하여 Lync Server 제어판을 엽니다. Lync Server 제어판을 시작하는 데 사용할 수 있는 다양한 방법에 대한 자세한 내용은 [Lync Server 관리 도구 열기](lync-server-2013-open-lync-server-administrative-tools.md)를 참조하세요.

3.  왼쪽 탐색 모음에서 **응답 그룹**을 클릭하고 **워크플로**를 클릭합니다.

4.  **워크플로** 페이지에서 **워크플로 만들기 또는 편집**을 클릭합니다.

5.  **서비스 선택** 검색 필드에 삭제할 워크플로를 호스팅하는 **ApplicationServer** 서비스의 이름을 일부분 또는 모두 입력합니다.

6.  서비스 목록에서 원하는 서비스를 클릭하고 **확인**을 클릭합니다.
    

    > [!NOTE]
    > 응답 그룹 구성 도구 웹 페이지가 열립니다. 웹 브라우저에서 <STRONG>https://<EM>&lt;webPoolFQDN&gt;</EM>/RgsConfig</STRONG>에 연결하여 응답 그룹 구성 도구 웹 페이지를 직접 열 수도 있습니다.



7.  **기존 워크플로 관리**에서 삭제할 워크플로를 찾은 다음 **동작**에서 **삭제**를 클릭합니다.

8.  **예**를 클릭합니다.

## cmdlet을 사용하여 워크플로를 삭제하려면

1.  RTCUniversalServerAdmins 그룹의 구성원이나 응답 그룹을 지원하는 미리 정의된 관리 역할 중 하나의 구성원으로 로그온합니다.

2.  Lync Server 관리 셸 시작: **시작**, **모든 프로그램**, **Microsoft Lync Server 2013**을 차례로 클릭한 다음 **Lync Server 관리 셸**을 클릭합니다.

3.  명령줄에서 다음을 실행합니다.
    
        Get-CsRgsWorkflow -Identity <Application Server service> -Name "<name of workflow>" | Remove-CsRgsWorkflow
    
    예를 들면 다음과 같습니다.
    
        Get-CsRgsWorkflow -Identity service:ApplicationServer:redmond.contoso.com -Name "Help Desk" | Remove-CsRgsWorkflow

