---
title: 기존 네트워크 사이트 삭제
TOCTitle: 기존 네트워크 사이트 삭제
ms:assetid: 2762149b-3572-4513-b838-beda7fa9e81e
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/JJ688001(v=OCS.15)
ms:contentKeyID: 49885690
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# 기존 네트워크 사이트 삭제

 

_**마지막으로 수정된 항목:** 2012-11-01_

네트워크 사이트는 CAC(통화 허용 제어) 또는 고급 9-1-1 배포의 각 지역 내에 구성된 사무실 또는 위치입니다. Lync Server 2013 제어판을 사용하여 사이트를 구성하고 지역에 연결할 수 있습니다. 예를 들어 북미 지역의 네트워크 지역은 Chicago, Redmond 및 Vancouver와 같은 네트워크 사이트와 연결할 수 있습니다. 조직 내의 모든 사이트에는 해당 사이트에 대역폭 제한이 없더라도 CAC 네트워크 사이트를 만들어야 합니다. Lync Server 제어판에서 네트워크 사이트를 작성, 수정 또는 삭제할 수 있습니다. 다음 절차에 따라 기존 네트워크 사이트를 삭제합니다. 네트워크 사이트를 만들거나 수정하는 방법에 대한 자세한 내용은 [네트워크 사이트 만들기 또는 수정](lync-server-2013-creating-or-modifying-network-sites.md)을 참조하십시오.

## 네트워크 사이트를 삭제하려면

1.  RTCUniversalServerAdmins 그룹의 구성원(또는 이와 동일한 사용자 권한을 가진 사용자 계정) 또는 CsAdministrator 역할이 할당된 사용자 계정에서 내부 배포된 컴퓨터에 로그온합니다.

2.  브라우저 창을 연 다음 Admin URL을 입력하여 Lync Server 제어판을 엽니다. Lync Server 제어판을 시작하는 데 사용할 수 있는 다양한 방법에 대한 자세한 내용은 [Lync Server 관리 도구 열기](lync-server-2013-open-lync-server-administrative-tools.md)를 참조하세요.

3.  왼쪽 탐색 모음에서 **네트워크 구성**을 클릭하고 **사이트**를 클릭합니다.

4.  **사이트** 페이지에서 삭제할 사이트를 클릭합니다.
    

    > [!NOTE]
    > 한 번에 둘 이상의 사이트를 삭제할 수 있습니다. 이렇게 하려면 Ctrl 키를 누른 상태에서 여러 사이트를 선택합니다. 또는 모든 사이트를 선택하려면 <STRONG>편집</STRONG> 메뉴에서 <STRONG>모두 선택</STRONG>을 클릭합니다.



5.  **편집** 메뉴에서 **삭제**를 클릭합니다.

6.  **확인**을 클릭합니다.
    

    > [!WARNING]
    > 네트워크 서브넷과 연결된 네트워크 사이트는 제거할 수 없습니다. 서브넷과 연결된 사이트를 제거하려고 시도하면 오류 메시지가 표시됩니다. 사이트가 서브넷에 연결되어 있는지 확인하려면 <STRONG>편집</STRONG> 메뉴에서 <STRONG>자세한 정보 표시</STRONG>를 클릭합니다.


