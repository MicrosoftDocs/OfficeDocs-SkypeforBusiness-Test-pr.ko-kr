---
title: 기존 네트워크 지역 삭제
TOCTitle: 기존 네트워크 지역 삭제
ms:assetid: c7293a2f-2b49-4c4a-903f-f7edcea2bc5f
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/JJ721882(v=OCS.15)
ms:contentKeyID: 49885976
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# 기존 네트워크 지역 삭제

 

_**마지막으로 수정된 항목:** 2013-02-21_

네트워크 지역은 여러 지리적 영역의 다양한 네트워크 부분을 상호 연결합니다. 모든 네트워크 지역은 중앙 사이트와 연결되어 있어야 합니다. 중앙 사이트는 CAC(통화 허용 제어) 대역폭 정책 서비스가 실행되는 데이터 센터 사이트입니다. Lync Server 제어판을 사용하여 네트워크 지역을 구성할 수 있습니다. 네트워크 지역에는 오디오 및 비디오 연결에 대해 인터넷을 통한 대체 경로가 허용되는지 여부를 결정하는 설정이 포함됩니다. Lync Server 제어판에서 네트워크 지역을 만들고 수정하거나 삭제할 수 있습니다. 이 항목을 참조하여 기존 네트워크 지역을 삭제하십시오. 기존 네트워크 지역을 만들거나 수정하는 방법에 대한 자세한 내용은 [네트워크 영역 만들기 또는 수정](lync-server-2013-creating-or-modifying-network-regions.md) 섹션을 참조하십시오.

## 네트워크 지역을 삭제하려면

1.  RTCUniversalServerAdmins 그룹의 구성원(또는 이와 동일한 사용자 권한을 가진 사용자 계정) 또는 CsAdministrator 역할이 할당된 사용자 계정에서 내부 배포된 컴퓨터에 로그온합니다.

2.  브라우저 창을 연 다음 Admin URL을 입력하여 Lync Server 제어판을 엽니다. Lync Server 제어판을 시작하는 데 사용할 수 있는 다양한 방법에 대한 자세한 내용은 [Lync Server 관리 도구 열기](lync-server-2013-open-lync-server-administrative-tools.md)를 참조하세요.

3.  왼쪽 탐색 표시줄에서 **네트워크 구성**을 클릭한 다음 **지역**을 클릭합니다.

4.  **지역** 페이지에서 삭제하려는 지역을 클릭합니다.
    

    > [!NOTE]
    > 한 번에 둘 이상의 지역을 삭제할 수 있습니다. 이렇게 하려면 Ctrl 키를 누른 상태에서 여러 지역을 선택합니다. 또는 지역을 모두 선택하려면 <STRONG>편집</STRONG> 메뉴에서 <STRONG>모두 선택</STRONG>을 클릭합니다.



5.  **편집** 메뉴에서 **삭제**를 클릭합니다.

6.  **확인**을 클릭합니다.
    

    > [!WARNING]
    > 네트워크 사이트와 연결된 네트워크 지역은 제거할 수 없습니다. 사이트와 연결된 지역을 제거하려고 시도하면 오류 메시지가 표시됩니다. 지역이 사이트와 연결되어 있는지 확인하려면 지역을 선택하고 <STRONG>편집</STRONG> 메뉴에서 <STRONG>자세한 정보 표시</STRONG>를 클릭합니다.



## 참고 항목

#### 작업

[네트워크 영역 만들기 또는 수정](lync-server-2013-creating-or-modifying-network-regions.md)

