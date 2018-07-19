---
title: 네트워크 대역폭 정책 프로필 삭제
TOCTitle: 네트워크 대역폭 정책 프로필 삭제
ms:assetid: 4d6beda8-6aa5-4d5e-8a07-363598f0e0c8
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/JJ688050(v=OCS.15)
ms:contentKeyID: 49885758
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# 네트워크 대역폭 정책 프로필 삭제

 

_**마지막으로 수정된 항목:** 2012-11-01_

대역폭 정책은 CAC(통화 허용 제어)의 일부로 특정 형식에 대한 대역폭 제한을 정의하는 데 사용됩니다. Microsoft Lync Server 2013에서는 오디오 및 비디오 형식에만 대역폭 제한을 지정할 수 있습니다. 전체 대역폭 제한 및 세션 제한을 설정할 수 있습니다. Lync Server 제어판을 사용하여 이러한 정책에 대한 프로필을 만들거나, 수정 또는 삭제할 수 있습니다. 다음 절차에 따라 네트워크 대역폭 정책 프로필을 삭제하십시오. 네트워크 대역폭 정책 프로필을 만들거나 수정하는 방법에 대한 자세한 내용은 [대역폭 정책 프로필 만들기 또는 수정](lync-server-2013-creating-or-modifying-bandwidth-policy-profiles.md)을 참조하십시오.

## 대역폭 정책 프로필을 삭제하려면

1.  RTCUniversalServerAdmins 그룹의 구성원(또는 이와 동일한 사용자 권한을 가진 사용자 계정) 또는 CsAdministrator 역할이 할당된 사용자 계정에서 내부 배포된 컴퓨터에 로그온합니다.

2.  브라우저 창을 연 다음 Admin URL을 입력하여 Lync Server 제어판을 엽니다. Lync Server 제어판을 시작하는 데 사용할 수 있는 다양한 방법에 대한 자세한 내용은 [Lync Server 관리 도구 열기](lync-server-2013-open-lync-server-administrative-tools.md)를 참조하세요.

3.  왼쪽 탐색 모음에서 **네트워크 구성**을 클릭한 후 **대역폭 정책**을 클릭합니다.

4.  **대역폭 정책** 페이지에서 삭제하려는 대역폭 정책 프로필을 클릭합니다.
    

    > [!NOTE]
    > 한 번에 둘 이상의 프로필을 삭제할 수 있습니다. 이렇게 하려면 Ctrl 키를 누른 상태에서 여러 프로필을 선택합니다. 또는 모든 프로필을 선택하려면 <STRONG>편집</STRONG> 메뉴에서 <STRONG>모두 선택</STRONG>을 클릭합니다.



5.  **편집** 메뉴에서 **삭제**를 클릭합니다.
    

    > [!WARNING]
    > 네트워크 사이트에 연결된 대역폭 정책 프로필은 삭제할 수 없습니다. 프로필을 삭제하려면 먼저 네트워크 사이트와의 연결을 제거해야 합니다. 네트워크 사이트 수정 방법에 대한 자세한 내용은 <A href="lync-server-2013-creating-or-modifying-network-sites.md">네트워크 사이트 만들기 또는 수정</A>을 참조하십시오.



## 참고 항목

#### 작업

[대역폭 정책 프로필 만들기 또는 수정](lync-server-2013-creating-or-modifying-bandwidth-policy-profiles.md)  
[네트워크 대역폭 정책 프로필 정보 보기](lync-server-2013-viewing-network-bandwidth-policy-profile-information.md)  

#### 기타 리소스

[Lync Server 2013에서 통화 허용 제어 서비스 구성](lync-server-2013-configure-call-admission-control.md)  
[Remove-CsNetworkBandwidthPolicyProfile](https://docs.microsoft.com/en-us/powershell/module/skype/Remove-CsNetworkBandwidthPolicyProfile)

