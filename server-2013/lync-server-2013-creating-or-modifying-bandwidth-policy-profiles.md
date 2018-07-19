---
title: 대역폭 정책 프로필 만들기 또는 수정
TOCTitle: 대역폭 정책 프로필 만들기 또는 수정
ms:assetid: 08a2e18f-9b0d-4a2f-aa14-13bbf79ec745
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg520945(v=OCS.15)
ms:contentKeyID: 49302730
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# 대역폭 정책 프로필 만들기 또는 수정

 

_**마지막으로 수정된 항목:** 2012-10-15_

대역폭 정책은 CAC(통화 허용 제어)의 일부로 특정 형식에 대한 대역폭 제한을 정의하는 데 사용됩니다. Microsoft Lync Server 2013에서는 오디오 및 비디오 형식에만 대역폭 제한이 할당될 수 있습니다. 전체 대역폭 제한 및 세션 제한을 설정할 수 있습니다. Lync Server 제어판을 사용하여 이러한 정책에 대해 컨테이너 프로필을 작성, 수정 또는 삭제할 수 있습니다. 각 대역폭 정책 프로필은 하나 이상의 네트워크 사이트에 연결할 수 있습니다. 다음 절차에 따라 대역폭 정책 프로필을 만들거나 수정합니다. 대역폭 정책 프로필을 삭제하려면 [네트워크 대역폭 정책 프로필 삭제](lync-server-2013-deleting-network-bandwidth-policy-profiles.md)를 참조하십시오.

## 새 대역폭 정책 프로필을 만들려면

1.  RTCUniversalServerAdmins 그룹의 구성원(또는 이와 동일한 사용자 권한을 가진 사용자 계정) 또는 CsAdministrator 역할이 할당된 사용자 계정에서 내부 배포된 컴퓨터에 로그온합니다.

2.  브라우저 창을 연 다음 Admin URL을 입력하여 Lync Server 제어판을 엽니다. Lync Server 제어판을 시작하는 데 사용할 수 있는 다양한 방법에 대한 자세한 내용은 [Lync Server 관리 도구 열기](lync-server-2013-open-lync-server-administrative-tools.md)를 참조하세요.

3.  왼쪽 탐색 모음에서 **네트워크 구성**을 클릭한 다음 **대역폭 정책**을 클릭합니다.

4.  **대역폭 정책** 페이지에서 **다음**을 클릭합니다.

5.  **새 대역폭 정책 프로필**에서 **이름** 필드에 이름을 입력합니다. 이 이름은 모든 대역폭 정책 프로필에서 고유해야 합니다.

6.  **오디오 제한** 필드에 숫자 값을 입력합니다. 이 값은 모든 오디오 연결에 대해 할당할 최대 대역폭 크기(kbps 단위)입니다.

7.  **오디오 세션 제한** 필드에 숫자 값을 입력합니다. 이 값은 개별 오디오 연결에 대해 할당할 최대 대역폭 크기(kbps 단위)입니다. 이 값은 40 이상이어야 합니다.

8.  **비디오 제한** 필드에 숫자 값을 입력합니다. 이 값은 모든 비디오 연결에 대해 할당할 최대 대역폭 크기(kbps 단위)입니다.

9.  **비디오 세션 제한** 필드에 숫자 값을 입력합니다. 이 값은 개별 비디오 연결에 대해 할당할 최대 대역폭 크기(kbps 단위)입니다. 이 값은 100 이상이어야 합니다.

10. (선택 사항) 이름만으로는 표현할 수 없는 이 대역폭 정책 프로필에 대한 자세한 정보를 제공하려면 **설명** 필드에 값을 입력합니다.

11. **커밋**을 클릭합니다.
    

    > [!NOTE]
    > 새 대역폭 정책 프로필을 만들어도 대역폭 제한이 자동으로 적용되지는 않습니다. 이렇게 하려면 먼저 정책 프로필을 사이트에 연결해야 합니다. 프로필 정책을 사이트에 연결하는 방법에 대한 자세한 내용은 <A href="lync-server-2013-creating-or-modifying-network-sites.md">네트워크 사이트 만들기 또는 수정</A>을 참조하십시오.



## 대역폭 정책 프로필을 수정하려면

1.  RTCUniversalServerAdmins 그룹의 구성원(또는 이와 동일한 사용자 권한을 가진 사용자 계정) 또는 CsAdministrator 역할이 할당된 사용자 계정에서 내부 배포된 컴퓨터에 로그온합니다.

2.  브라우저 창을 연 다음 Admin URL을 입력하여 Lync Server 제어판을 엽니다. Lync Server 제어판을 시작하는 데 사용할 수 있는 다양한 방법에 대한 자세한 내용은 [Lync Server 관리 도구 열기](lync-server-2013-open-lync-server-administrative-tools.md)를 참조하세요.

3.  왼쪽 탐색 모음에서 **네트워크 구성**을 클릭한 다음 **대역폭 정책**을 클릭합니다.

4.  **대역폭 정책** 페이지에서 수정할 대역폭 정책 프로필을 클릭합니다.

5.  **편집** 메뉴에서 **자세한 정보 표시**를 클릭합니다.

6.  **대역폭 정책 프로필 편집** 페이지에서 필드의 값을 필요한 대로 수정합니다. 자세한 내용은 이 항목 앞부분의 "대역폭 정책 프로필을 만들려면" 섹션을 참조하십시오.

7.  **커밋**을 클릭합니다.
    

    > [!NOTE]
    > 대역폭 정책 프로필을 수정하면 해당 대역폭 정책 프로필과 연결된 모든 네트워크 사이트의 대역폭 제한이 즉시 업데이트됩니다.



## 참고 항목

#### 작업

[네트워크 대역폭 정책 프로필 삭제](lync-server-2013-deleting-network-bandwidth-policy-profiles.md)  

#### 기타 리소스

[Lync Server 2013에서 통화 허용 제어 서비스 구성](lync-server-2013-configure-call-admission-control.md)  
[New-CsNetworkBandwidthPolicyProfile](https://docs.microsoft.com/en-us/powershell/module/skype/New-CsNetworkBandwidthPolicyProfile)  
[Set-CsNetworkBandwidthPolicyProfile](https://docs.microsoft.com/en-us/powershell/module/skype/Set-CsNetworkBandwidthPolicyProfile)  
[Get-CsNetworkBandwidthPolicyProfile](https://docs.microsoft.com/en-us/powershell/module/skype/Get-CsNetworkBandwidthPolicyProfile)

