---
title: 응답 그룹 큐 삭제
TOCTitle: 응답 그룹 큐 삭제
ms:assetid: 67c7a489-8c5f-4c6b-9387-9d4c11d43695
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg521008(v=OCS.15)
ms:contentKeyID: 49303887
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# 응답 그룹 큐 삭제

 

_**마지막으로 수정된 항목:** 2012-11-01_

다음 절차 중 하나를 사용해서 큐를 삭제합니다.

## Lync Server 제어판을 사용하여 큐를 삭제하려면

1.  RTCUniversalServerAdmins 그룹의 구성원이나 응답 그룹을 지원하는 미리 정의된 관리 역할 중 하나의 구성원으로 로그온합니다.

2.  브라우저 창을 연 다음 Admin URL을 입력하여 Lync Server 제어판을 엽니다. Lync Server 제어판을 시작하는 데 사용할 수 있는 다양한 방법에 대한 자세한 내용은 [Lync Server 관리 도구 열기](lync-server-2013-open-lync-server-administrative-tools.md)를 참조하세요.

3.  왼쪽 탐색 모음에서 **응답 그룹**을 클릭하고 **큐**를 클릭합니다.

4.  검색 필드에 삭제할 큐의 이름을 일부분 또는 모두 입력합니다.

5.  큐 목록에서 삭제할 큐를 클릭하고 **편집**을 클릭한 다음 **삭제**를 클릭합니다.

6.  **확인**을 클릭합니다.

## cmdlet을 사용하여 큐를 삭제하려면

1.  RTCUniversalServerAdmins 그룹의 구성원이나 응답 그룹을 지원하는 미리 정의된 관리 역할 중 하나의 구성원으로 로그온합니다.

2.  Lync Server 관리 셸 시작: **시작**, **모든 프로그램**, **Microsoft Lync Server 2013**을 차례로 클릭한 다음 **Lync Server 관리 셸**을 클릭합니다.

3.  명령줄에서 다음을 실행합니다.
    
        Get-CsRgsQueue -Identity <Application Server service> -Name "<name of queue>" | Remove-CsRgsQueue
    
    예:
    
        Get-CsRgsQueue -Identity service:ApplicationServer:redmond.contoso.com -Name "Help Desk" | Remove-CsRgsQueue

