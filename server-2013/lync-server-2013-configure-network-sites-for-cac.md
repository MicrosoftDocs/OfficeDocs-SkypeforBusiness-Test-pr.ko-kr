---
title: Lync Server 2013에서 CAC에 대한 네트워크 사이트 구성
TOCTitle: Lync Server 2013에서 CAC에 대한 네트워크 사이트 구성
ms:assetid: afcea38f-5789-45ec-97af-c6e38364950c
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg412840(v=OCS.15)
ms:contentKeyID: 49304728
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Lync Server 2013에서 CAC에 대한 네트워크 사이트 구성

 

_**마지막으로 수정된 항목:** 2012-09-05_


> [!IMPORTANT]  
> E9-1-1 또는 미디어 바이패스에 대해 네트워크 사이트를 이미 만든 경우 <STRONG>Set-CsNetworkSite</STRONG> cmdlet을 사용하여 대역폭 정책 프로필을 적용할 기존 네트워크 사이트를 수정합니다. 네트워크 사이트를 수정하는 방법에 대한 예는 <A href="lync-server-2013-create-or-modify-a-network-site.md">Lync Server 2013에서 네트워크 사이트 만들기 또는 수정</A>을 참조하십시오.



*네트워크 사이트*는 CAC(통화 허용 제어), E9-1-1 및 미디어 바이패스 배포에 대한 각 네트워크 지역 내에 있는 사무실이나 위치입니다. 다음 절차를 사용하여 CAC에 대한 네트워크 토폴로지 예의 네트워크 사이트에 따라 조정된 네트워크 사이트를 만듭니다. 이러한 절차에는 WAN 대역폭에서 제한하는 네트워크 사이트를 만들고 수정하는 방법이 나와 있으며, 따라서 실시간 오디오 또는 비디오 트래픽 흐름을 제한하는 대역폭 정책이 필요합니다.

CAC 배포 예에서 북미 지역에는 6개의 사이트가 있습니다. 이 사이트 중 세 개는 WAN 대역폭에서 제한하며, 해당 사이트는 Reno, Portland, 및 Albuquerque입니다. WAN 대역폭에서 제한하지 *않는* 나머지 세 개 사이트는 사이트(뉴욕, 시카고 및 디트로이트)를 보여 줍니다. 이러한 네트워크 사이트를 만들거나 수정하는 방법에 대한 예는 [Lync Server 2013에서 네트워크 사이트 만들기 또는 수정](lync-server-2013-create-or-modify-a-network-site.md)을 참조하십시오.

네트워크 토폴로지 예를 보려면 [예: Lync Server 2013에서 통화 허용 제어 서비스에 대한 요구 사항 수집](lync-server-2013-example-of-gathering-your-requirements-for-call-admission-control.md)을 참조하십시오.


> [!NOTE]  
> 다음 절차에서는 Lync Server 관리 셸을 사용하여 네트워크 사이트를 만듭니다. Lync Server 제어판을 사용하여 네트워크 사이트를 만드는 방법에 대한 자세한 내용은 <A href="lync-server-2013-create-or-modify-a-network-site.md">Lync Server 2013에서 네트워크 사이트 만들기 또는 수정</A>을 참조하십시오.



## 통화 허용 제어에 대한 네트워크 사이트를 만들려면

1.  Lync Server 관리 셸 시작: **시작**, **모든 프로그램**, **Microsoft Lync Server 2013**을 차례로 클릭한 다음 **Lync Server 관리 셸**을 클릭합니다.

2.  **New-CsNetworkSite** cmdlet을 실행하여 네트워크 사이트를 만들고 각 사이트에 적합한 대역폭 정책 프로필을 적용합니다. 예를 들어 다음을 실행합니다.
    
```
                New-CsNetworkSite -NetworkSiteID Reno -Description "NA:Branch office for sales force" -NetworkRegionID NorthAmerica -BWPolicyProfileID 10MB_Link
```
```    
        New-CsNetworkSite -NetworkSiteID Portland -Description "NA:Branch office for marketing force" -NetworkRegionID NorthAmerica -BWPolicyProfileID 5MB_Link
```
```    
        New-CsNetworkSite -NetworkSiteID Albuquerque -Description "NA:Branch office for SouthWest sales" -NetworkRegionID EMEA -BWPolicyProfileID 10MB_Link
```

3.  전체 토폴로지 예에 대한 네트워크 사이트 만들기를 종료하려면 EMEA 및 APAC 지역의 대역폭 제한 네트워크 사이트에 대해 2단계를 반복합니다.

