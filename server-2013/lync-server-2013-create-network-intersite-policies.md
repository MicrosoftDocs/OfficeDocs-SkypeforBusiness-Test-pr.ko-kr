---
title: Lync Server 2013에서 새 네트워크 사이트 간 정책 만들기
TOCTitle: Lync Server 2013에서 새 네트워크 사이트 간 정책 만들기
ms:assetid: b0714aae-55dc-4587-b718-34a03f596b22
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg412844(v=OCS.15)
ms:contentKeyID: 49304739
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Lync Server 2013에서 새 네트워크 사이트 간 정책 만들기

 

_**마지막으로 수정된 항목:** 2012-10-19_

*네트워크 사이트 간 정책*은 사이트 간 직접 WAN 링크가 있는 사이트 간 대역폭 제한을 정의합니다.

자세한 내용은 다음 cmdlet에 대한 Lync Server 관리 셸 설명서를 참조하십시오.

  - [New-CsNetworkInterSitePolicy](new-csnetworkintersitepolicy.md)

  - [Get-CsNetworkInterSitePolicy](get-csnetworkintersitepolicy.md)

  - [Set-CsNetworkInterSitePolicy](set-csnetworkintersitepolicy.md)

  - [Remove-CsNetworkInterSitePolicy](remove-csnetworkintersitepolicy.md)


> [!IMPORTANT]
> 네트워크 사이트 간 정책은 두 개의 네트워크 사이트 간 직접 상호 링크가 있는 <EM>경우에만</EM> 필요합니다.



북미 지역 예 토포롤지에서 Reno 및 Albuquerque 사이트 간 직접 연결이 제공됩니다. 이러한 두 사이트에는 적합한 대역폭 정책 프로필이 적용되는 사이트 간 정책이 필요합니다. 다음 예에는 20Mb\_Link 프로필이 적용됩니다.

## 네트워크 사이트 간 정책을 만들려면

1.  Lync Server 관리 셸 시작: **시작**, **모든 프로그램**, **Microsoft Lync Server 2013**을 차례로 클릭한 다음 **Lync Server 관리 셸**을 클릭합니다.

2.  New-CsNetworkInterSitePolicy cmdlet을 실행하여 네트워크 사이트 간 정책을 만들고 직접 상호 연결이 있는 두 개의 사이트에 대해 적합한 대역폭 정책 프로필을 적용합니다. 예를 들어 다음을 실행합니다.
    
        New-CsNetworkInterSitePolicy -InterNetworkSitePolicyID Reno_Albuquerque -NetworkSiteID1 Reno -NetworkSiteID2 Albuquerque -BWPolicyProfileID 20Mb_Link

3.  필요한 경우 직접 상호 연결이 있는 모든 네트워크 사이트 쌍에 대해 네트워크 사이트 간 정책을 만들려면 2단계를 반복합니다.

