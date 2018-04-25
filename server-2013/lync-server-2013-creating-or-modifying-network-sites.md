---
title: 네트워크 사이트 만들기 또는 수정
TOCTitle: 네트워크 사이트 만들기 또는 수정
ms:assetid: 358aa08a-c5bc-45fc-8017-19e6202f88c5
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg520975(v=OCS.15)
ms:contentKeyID: 49303271
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# 네트워크 사이트 만들기 또는 수정

 

_**마지막으로 수정된 항목:** 2012-10-08_

네트워크 사이트는 CAC(통화 허용 제어) 또는 고급 9-1-1 배포의 각 지역 내에 구성된 사무실 또는 위치입니다. Microsoft Lync Server 2013 제어판을 사용하여 사이트를 구성하고 지역에 연결할 수 있습니다. 예를 들어 북미 지역의 네트워크 지역은 Chicago, Redmond 및 Vancouver와 같은 네트워크 사이트와 연결할 수 있습니다. 대역폭 제한이 없는 사이트를 포함하여 조직 내의 모든 사이트에는 CAC 네트워크 사이트를 만들어야 합니다. Lync Server 제어판에서 네트워크 사이트를 작성, 수정 또는 삭제할 수 있습니다. 다음 절차에 따라 네트워크 사이트를 만들거나 수정합니다. 기존 네트워크 사이트를 삭제하는 방법에 대한 자세한 내용은 [기존 네트워크 사이트 삭제](lync-server-2013-deleting-an-existing-network-site.md)를 참조하십시오.

## 네트워크 사이트를 만들려면

1.  RTCUniversalServerAdmins 그룹의 구성원(또는 이와 동일한 사용자 권한을 가진 사용자 계정) 또는 CsAdministrator 역할이 할당된 사용자 계정에서 내부 배포된 컴퓨터에 로그온합니다.

2.  브라우저 창을 연 다음 Admin URL을 입력하여 Lync Server 제어판을 엽니다. Lync Server 제어판을 시작하는 데 사용할 수 있는 다양한 방법에 대한 자세한 내용은 [Lync Server 관리 도구 열기](lync-server-2013-open-lync-server-administrative-tools.md)를 참조하세요.

3.  왼쪽 탐색 모음에서 **네트워크 구성**을 클릭하고 **사이트**를 클릭합니다.

4.  **사이트** 페이지에서 **다음**을 클릭합니다.

5.  **새 사이트**에서 **이름** 필드에 해당 사이트의 이름을 입력합니다.
    

    > [!NOTE]
    > 사이트 이름은 Lync Server 2013 배포 내에서 고유해야 합니다.



6.  **지역** 드롭다운 목록에서 이 사이트에 연결할 네트워크 지역을 선택합니다.

7.  (선택 사항) 이 사이트에 대한 오디오 또는 비디오 통화에 대역폭 제한을 적용하려면 **대역폭 정책** 드롭다운 목록에서 적절한 설정이 포함된 대역폭 정책 프로필을 선택합니다.
    

    > [!NOTE]
    > <STRONG>네트워크 구성</STRONG> 그룹의 <STRONG>정책 프로필</STRONG> 페이지에서 사용 가능한 대역폭 정책 프로필의 세부 정보를 보거나 새 대역폭 정책 프로필을 만들 수 있습니다. 자세한 내용은 <A href="lync-server-2013-creating-or-modifying-bandwidth-policy-profiles.md">대역폭 정책 프로필 만들기 또는 수정</A>을 참조하십시오.



8.  (선택 사항) 이 사이트에 대해 위치 설정을 제공하려면 **위치 정책** 드롭다운 목록에서 위치 정책을 선택합니다.
    

    > [!NOTE]
    > 위치 정책은 사이트에 특정 E9-1-1(고급 9-1-1) 및 클라이언트 위치 설정을 할당합니다. <STRONG>네트워크 구성</STRONG> 그룹의 <STRONG>위치 정책</STRONG> 페이지에서 사용 가능한 위치 정책의 세부 정보를 보거나 새 위치 정책을 만들 수 있습니다. 자세한 내용은 <A href="lync-server-2013-viewing-location-policy-information.md">위치 정책 정보 보기</A>을 참조하십시오.



9.  (선택 사항) 이름만으로는 표현할 수 없는 이 사이트에 대한 자세한 정보를 제공하려면 **설명** 필드에 값을 입력합니다.

10. **커밋**을 클릭합니다.
    

    > [!NOTE]
    > 새 네트워크 사이트를 만들 때는 <STRONG>연결된 서브넷</STRONG> 표를 사용하지 않습니다. 서브넷을 만들거나 수정할 때 서브넷을 사이트에 연결합니다. 자세한 내용은 <A href="lync-server-2013-create-or-modify-network-subnets.md">네트워크 서브넷 만들기 또는 수정</A>을 참조하십시오.



## 네트워크 사이트를 수정하려면

1.  RTCUniversalServerAdmins 그룹의 구성원(또는 이와 동일한 사용자 권한을 가진 사용자 계정) 또는 CsAdministrator 역할이 할당된 사용자 계정에서 내부 배포된 컴퓨터에 로그온합니다.

2.  브라우저 창을 연 다음 Admin URL을 입력하여 Lync Server 제어판을 엽니다. Lync Server 제어판을 시작하는 데 사용할 수 있는 다양한 방법에 대한 자세한 내용은 [Lync Server 관리 도구 열기](lync-server-2013-open-lync-server-administrative-tools.md)를 참조하세요.

3.  왼쪽 탐색 모음에서 **네트워크 구성**을 클릭하고 **사이트**를 클릭합니다.

4.  **사이트** 페이지에서 수정할 사이트를 클릭합니다.

5.  **편집** 메뉴에서 **자세한 정보 표시**를 클릭합니다.

6.  **사이트 편집** 페이지에서 사이트에 연결된 위치 정책, 대역폭 정책 프로필, 지역 및 설명을 수정할 수 있습니다. 자세한 내용은 이 항목의 앞부분에 나오는 "네트워크 사이트를 만들려면" 섹션을 참조하십시오.

7.  **커밋**을 클릭합니다.

이 페이지의 **연결된 서브넷** 표는 수정할 수 없습니다. 연결된 서브넷 목록은 사이트 설정 수정 시 영향을 받는 서브넷을 확인할 수 있도록 참조용으로 제공됩니다.

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



## 참고 항목

#### 작업

[기존 네트워크 사이트 삭제](lync-server-2013-deleting-an-existing-network-site.md)  

#### 기타 리소스

[New-CsNetworkSite](new-csnetworksite.md)  
[Set-CsNetworkSite](set-csnetworksite.md)  
[Remove-CsNetworkSite](remove-csnetworksite.md)  
[Get-CsNetworkSite](get-csnetworksite.md)

