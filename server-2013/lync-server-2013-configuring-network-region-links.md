---
title: 네트워크 지역 링크 구성
TOCTitle: 네트워크 지역 링크 구성
ms:assetid: 952bc93e-e6aa-4539-85c7-2b15f14eb382
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg182551(v=OCS.15)
ms:contentKeyID: 49304424
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# 네트워크 지역 링크 구성

 

_**마지막으로 수정된 항목:** 2012-11-01_

CAC(통화 허용 제어)의 일환으로 두 네트워크 지역 간의 링크를 구성할 수 있습니다. 네트워크 내의 지역은 실제 WAN(Wide Area Network) 연결을 통해 연결됩니다. Lync Server 제어판을 사용하여 두 네트워크 지역 간의 링크를 정의하고 이러한 지역 간의 오디오 및 비디오 연결에 대한 대역폭 제한을 설정할 수 있습니다. 기존 네트워크 지역 링크를 삭제하는 방법에 대한 자세한 내용은 [네트워크 지역 링크 삭제](lync-server-2013-deleting-network-region-links.md)를 참조하십시오.

## 네트워크 지역 링크를 만들려면

1.  RTCUniversalServerAdmins 그룹의 구성원(또는 이와 동일한 사용자 권한을 가진 사용자 계정) 또는 CsAdministrator 역할이 할당된 사용자 계정에서 내부 배포된 컴퓨터에 로그온합니다.

2.  브라우저 창을 연 다음 Admin URL을 입력하여 Lync Server 제어판을 엽니다. Lync Server 제어판을 시작하는 데 사용할 수 있는 다양한 방법에 대한 자세한 내용은 [Lync Server 관리 도구 열기](lync-server-2013-open-lync-server-administrative-tools.md)를 참조하세요.

3.  왼쪽 탐색 모음에서 **네트워크 구성**을 클릭한 다음 **지역 링크**를 클릭합니다.

4.  **지역 링크** 페이지에서 **새로 만들기**를 클릭합니다.

5.  **새 지역 링크**에서 **이름** 필드에 값을 입력합니다.
    

    > [!NOTE]
    > 이 값은 Lync Server 2013 배포 내에서 고유해야 합니다.



6.  **네트워크 지역 \#1** 드롭다운 목록에서 연결할 두 지역 중 하나를 선택합니다.

7.  **네트워크 지역 \#2** 드롭다운 목록에서 연결할 나머지 지역을 선택합니다. 이 지역은 네트워크 지역 \#1에 대해 선택한 지역과 달라야 합니다.

8.  (선택 사항) 이러한 지역 간의 음성 또는 화상 통화에 대역폭 제한을 설정하려면 **대역폭 정책** 드롭다운 목록에서 대역폭 정책 프로필을 선택합니다.

9.  **커밋**을 클릭합니다.

## 네트워크 지역 링크를 수정하려면

1.  RTCUniversalServerAdmins 그룹의 구성원(또는 이와 동일한 사용자 권한을 가진 사용자 계정) 또는 CsAdministrator 역할이 할당된 사용자 계정에서 내부 배포된 컴퓨터에 로그온합니다.

2.  브라우저 창을 연 다음 Admin URL을 입력하여 Lync Server 제어판을 엽니다. Lync Server 제어판을 시작하는 데 사용할 수 있는 다양한 방법에 대한 자세한 내용은 [Lync Server 관리 도구 열기](lync-server-2013-open-lync-server-administrative-tools.md)를 참조하세요.

3.  왼쪽 탐색 모음에서 **네트워크 구성**을 클릭한 다음 **지역 링크**를 클릭합니다.

4.  **지역 링크** 페이지에서 수정할 지역 링크를 클릭합니다.

5.  **편집** 메뉴에서 **자세한 정보 표시**를 클릭합니다.

6.  **지역 링크 편집**에서 연결된 지역 또는 이 링크에 대한 대역폭 정책 프로필을 수정할 수 있습니다.

7.  **커밋**을 클릭합니다.

## 참고 항목

#### 작업

[네트워크 지역 링크 삭제](lync-server-2013-deleting-network-region-links.md)  

#### 기타 리소스

[New-CsNetworkRegionLink](new-csnetworkregionlink.md)  
[Set-CsNetworkRegionLink](set-csnetworkregionlink.md)  
[Remove-CsNetworkRegionLink](remove-csnetworkregionlink.md)  
[Get-CsNetworkRegionLink](get-csnetworkregionlink.md)

