---
title: Lync Server 2013에서 네트워크 지역 간 경로 만들기
TOCTitle: Lync Server 2013에서 네트워크 지역 간 경로 만들기
ms:assetid: 5555262a-a502-4b01-9593-836dd30064f5
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg398368(v=OCS.15)
ms:contentKeyID: 49303670
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Lync Server 2013에서 네트워크 지역 간 경로 만들기

 

_**마지막으로 수정된 항목:** 2012-10-20_

*네트워크 지역 간 경로*는 네트워크 지역 쌍 간의 경로를 정의합니다. 통화 허용 제어 배포의 각 네트워크 지역 쌍에는 네트워크 지역 간 경로가 필요합니다. 따라서 배포 내의 모든 네트워크 지역이 다른 모든 지역에 액세스할 수 있습니다.

지역 링크는 지역 간 연결에 대한 대역폭 제한을 설정하는 반면, 지역 간 경로는 연결이 지역 간에 이어지는 링크된 경로를 결정합니다.

네트워크 지역 간 경로를 사용하는 방법에 대한 자세한 내용은 Lync Server 관리 셸 설명서에서 다음 cmdlet을 참조하십시오.

  - [New-CsNetworkInterRegionRoute](https://docs.microsoft.com/en-us/powershell/module/skype/New-CsNetworkInterRegionRoute)

  - [Get-CsNetworkInterRegionRoute](https://docs.microsoft.com/en-us/powershell/module/skype/Get-CsNetworkInterRegionRoute)

  - [Set-CsNetworkInterRegionRoute](https://docs.microsoft.com/en-us/powershell/module/skype/Set-CsNetworkInterRegionRoute)

  - [Remove-CsNetworkInterRegionRoute](https://docs.microsoft.com/en-us/powershell/module/skype/Remove-CsNetworkInterRegionRoute)

예제 토폴로지에서는 각각의 세 지역 쌍, 즉 North America/EMEA, EMEA/APAC, North America/APAC에 대해 네트워크 지역 간 경로를 정의해야 합니다.

## Lync Server 관리 셸을 사용하여 네트워크 지역 간 경로를 만들려면

1.  Lync Server 관리 셸 시작: **시작**, **모든 프로그램**, **Microsoft Lync Server 2013**을 차례로 클릭한 다음 **Lync Server 관리 셸**을 클릭합니다.

2.  **New-CsNetworkInterRegionRoute** cmdlet을 사용하여 필요한 경로를 정의합니다. 예를 들어 다음을 실행합니다.
    
        New-CsNetworkInterRegionRoute -Identity NorthAmerica_EMEA_Route -NetworkRegionID1 NorthAmerica -NetworkRegionID2 EMEA -NetworkRegionLinkIDs "NA-EMEA-LINK"
    
        New-CsNetworkInterRegionRoute -Identity NorthAmerica_APAC_Route -NetworkRegionID1 NorthAmerica -NetworkRegionID2 APAC -NetworkRegionLinkIDs "NA-EMEA-LINK, EMEA-APAC-LINK"
    
        New-CsNetworkInterRegionRoute -Identity EMEA_APAC_Route -NetworkRegionID1 EMEA -NetworkRegionID2 APAC -NetworkRegionLinkIDs "EMEA-APAC-LINK"
    

    > [!NOTE]
    > North America/APAC 네트워크 지역 간 경로의 경우, 지역 간에 직접 네트워크 지역 링크가 없으므로 네트워크 지역 링크가 두 개 필요합니다.



## Lync Server 제어판을 사용하여 네트워크 지역 간 경로를 만들려면

1.  브라우저 창을 연 다음 Admin URL을 입력하여 Lync Server 제어판을 엽니다. Lync Server 제어판을 시작하는 데 사용할 수 있는 다양한 방법에 대한 자세한 내용은 [Lync Server 관리 도구 열기](lync-server-2013-open-lync-server-administrative-tools.md)를 참조하세요.

2.  왼쪽 탐색 모음에서 **네트워크 구성**을 클릭합니다.

3.  **지역 경로** 탐색 단추를 클릭합니다.

4.  **새로 만들기**를 클릭합니다.

5.  **새 지역 경로** 페이지에서 **이름**을 클릭하고 네트워크 지역 간 경로의 이름을 입력합니다.

6.  **네트워크 지역 \#1**을 클릭하고 목록에서 네트워크 지역 \#2로 라우팅할 네트워크 지역을 클릭합니다.

7.  **네트워크 지역 \#2**를 클릭하고 목록에서 네트워크 지역 \#1로 라우팅할 네트워크 지역을 클릭합니다.

8.  **네트워크 지역 링크** 필드 옆의 **추가**를 클릭한 다음, 네트워크 지역 간 경로에 사용할 네트워크 지역 링크를 추가합니다.
    

    > [!NOTE]
    > 두 네트워크 지역에 대한 경로를 만드는데 해당 지역 사이에 직접 네트워크 지역 링크가 없는 경우, 경로를 완료하려면 필요한 모든 링크를 추가해야 합니다. 예를 들어 North America/APAC 네트워크 지역 간 경로의 경우, 지역 간에 직접 네트워크 지역 링크가 없으므로 네트워크 지역 링크가 두 개 필요합니다.



9.  **커밋**을 클릭합니다.

10. 토롤로지에 대해 네트워크 지역 간 경로 만들기를 완료하려면 다른 네트워크 지역 간 경로에 대한 설정을 사용하여 4-9단계를 반복합니다.

