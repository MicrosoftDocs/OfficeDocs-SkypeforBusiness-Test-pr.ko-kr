---
title: Lync Server 2013에서 네트워크 지역 링크 만들기
TOCTitle: Lync Server 2013에서 네트워크 지역 링크 만들기
ms:assetid: f8163910-8935-475d-88a2-3aa44feb9dbe
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg413047(v=OCS.15)
ms:contentKeyID: 49305576
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Lync Server 2013에서 네트워크 지역 링크 만들기

 

_**마지막으로 수정된 항목:** 2012-10-19_

네트워크 내의 지역은 실제 WAN 연결을 통해 연결됩니다. *네트워크 지역 링크*는 CAC(통화 허용 제어)에 대해 구성된 두 개의 지역 간 링크를 만들며, 이 지역 간 오디오 및 비디오 트래픽에 대한 대역폭 제한을 설정합니다.

네트워크 지역 링크를 사용하는 방법에 대한 자세한 내용은 다음 cmdlet에 대한 Lync Server 관리 셸 설명서를 참조하십시오.

  - [New-CsNetworkRegionLink](new-csnetworkregionlink.md)

  - [Get-CsNetworkRegionLink](get-csnetworkregionlink.md)

  - [Set-CsNetworkRegionLink](set-csnetworkregionlink.md)

  - [Remove-CsNetworkRegionLink](remove-csnetworkregionlink.md)

이 토폴로지 예에는 북미와 APAC 지역 간 링크 및 EMEA와 APAC 지역 간 링크가 포함됩니다. 이 지역의 각 링크는 계획 설명서의 [예: Lync Server 2013에서 통화 허용 제어 서비스에 대한 요구 사항 수집](lync-server-2013-example-of-gathering-your-requirements-for-call-admission-control.md) 섹션에서 설명한 대로 WAN 대역폭에서 제한합니다.

## Lync Server 관리 셸을 사용하여 네트워크 지역 링크를 만들려면

1.  Lync Server 관리 셸 시작: **시작**, **모든 프로그램**, **Microsoft Lync Server 2013**을 차례로 클릭한 다음 **Lync Server 관리 셸**을 클릭합니다.

2.  New-CsNetworkRegionLink cmdlet를 실행하여 지역 링크를 만들고 적합한 대역폭 정책 프로필을 적용합니다. 예를 들어 다음을 실행합니다.
    
        New-CsNetworkRegionLink -NetworkRegionLinkID NA-EMEA-LINK -NetworkRegionID1 NorthAmerica -NetworkRegionID2 EMEA -BWPolicyProfileID 50Mb_Link
    
        New-CsNetworkRegionLink -NetworkRegionLinkID EMEA-APAC-LINK -NetworkRegionID1 EMEA -NetworkRegionID2 APAC -BWPolicyProfileID 25Mb_Link

## Lync Server 제어판을 사용하여 네트워크 지역 링크를 만들려면

1.  브라우저 창을 연 다음 Admin URL을 입력하여 Lync Server 제어판을 엽니다. Lync Server 제어판을 시작하는 데 사용할 수 있는 다양한 방법에 대한 자세한 내용은 [Lync Server 관리 도구 열기](lync-server-2013-open-lync-server-administrative-tools.md)를 참조하세요.

2.  왼쪽 탐색 모음에서 **네트워크 구성**을 클릭합니다.

3.  **지역 링크** 탐색 단추를 클릭합니다.

4.  **새로 만들기**를 클릭합니다.

5.  **새 지역 링크** 페이지에서 **이름**을 클릭하고 네트워크 지역 링크에 대한 이름을 입력합니다.

6.  **네트워크 지역 \#1**을 클릭하고 목록에서 네트워크 지역 \#2에 연결할 네트워크 지역을 클릭합니다.

7.  **네트워크 지역 \#2**를 클릭하고 목록에서 네트워크 지역 \#1에 연결할 네트워크 지역을 클릭합니다.

8.  (선택 사항) **대역폭 정책**을 클릭하고 네트워크 지역 링크에 적용할 대역폭 정책 프로필을 선택합니다.
    

    > [!NOTE]
    > 네트워크 지역 링크에 대역폭 제한이 있고 CAC를 사용하여 해당 링크에 대해 미디어 트래픽을 제어할 경우에만 대역폭 정책을 적용합니다.



9.  **커밋**을 클릭합니다.

10. 토폴로지에 대한 네트워크 지역 링크 만들기를 종료하려면 다른 지역에 대한 설정을 사용하여 4-9단계를 반복합니다.

