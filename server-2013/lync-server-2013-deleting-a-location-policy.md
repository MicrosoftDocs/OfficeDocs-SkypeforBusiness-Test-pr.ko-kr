---
title: 위치 정책 삭제
TOCTitle: 위치 정책 삭제
ms:assetid: 8ca9ba10-f45f-435a-b39c-519d251e9085
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/JJ688125(v=OCS.15)
ms:contentKeyID: 49885859
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# 위치 정책 삭제

 

_**마지막으로 수정된 항목:** 2012-10-10_

Lync Server 2013에서는 위치 정책을 사용해서 E9-1-1(Enhanced 9-1-1) 기능 및 사용자 또는 대화 상대의 위치 설정과 관련된 설정을 적용할 수 있습니다. 위치 정책은 사용자가 E9-1-1을 사용하도록 설정되어 있는지 여부를 확인하고, 설정된 경우 긴급 통화에 대한 동작을 결정합니다. 예를 들어 위치 정책을 사용하여 긴급 통화 번호(한국의 경우 119), 회사 보안 부서에 자동으로 알림을 제공할지 여부 및 통화를 라우팅할 방법을 정의할 수 있습니다.

위치 정책은 Lync Server 2013 제어판의 **네트워크 구성** 그룹에서 구성할 수 있습니다. Lync Server 제어판에서는 위치 정책을 보거나, 만들거나, 수정하거나, 삭제할 수 있습니다. 위치 정책을 삭제하려면 다음 절차를 따릅니다. 위치 정책 만들기 또는 수정에 대한 자세한 내용은 [위치 정책 만들기 또는 수정](lync-server-2013-creating-or-modifying-a-location-policy.md)을 참조하십시오.

## 위치 정책을 삭제하려면

1.  RTCUniversalServerAdmins 그룹의 구성원(또는 이와 동일한 사용자 권한을 가진 사용자 계정) 또는 CsAdministrator 역할이 할당된 사용자 계정에서 내부 배포된 컴퓨터에 로그온합니다.

2.  브라우저 창을 연 다음 Admin URL을 입력하여 Lync Server 제어판을 엽니다. Lync Server 제어판을 시작하는 데 사용할 수 있는 다양한 방법에 대한 자세한 내용은 [Lync Server 관리 도구 열기](lync-server-2013-open-lync-server-administrative-tools.md)를 참조하세요.

3.  왼쪽 탐색 모음에서 **네트워크 구성**을 클릭한 다음 **위치 정책**을 클릭합니다.

4.  **위치 정책** 페이지에서 삭제할 위치 정책을 선택합니다.
    

    > [!NOTE]
    > 한 번에 둘 이상의 위치 정책을 삭제할 수 있습니다. 이렇게 하려면 Ctrl 키를 누른 채 여러 정책을 선택합니다. 또는 모든 정책을 선택하려면 <STRONG>편집</STRONG> 메뉴에서 <STRONG>모두 선택</STRONG>을 클릭합니다.



5.  **편집** 메뉴에서 **삭제**를 클릭합니다.

6.  **확인**을 클릭합니다.
    

    > [!IMPORTANT]
    > 전역 위치 정책은 삭제할 수 없습니다. 글로벌 정책을 삭제하려고 하면 경고 메시지가 나타나고 해당 정책이 기본값으로 다시 설정됩니다.



## 참고 항목

#### 작업

[위치 정책 만들기 또는 수정](lync-server-2013-creating-or-modifying-a-location-policy.md)  
[위치 정책 정보 보기](lync-server-2013-viewing-location-policy-information.md)

