---
title: Lync Server 2013에서 네트워크 사이트에 위치 정책 추가
TOCTitle: Lync Server 2013에서 네트워크 사이트에 위치 정책 추가
ms:assetid: 43bfab8a-3d6b-4ca4-8425-879fd910502e
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg425936(v=OCS.15)
ms:contentKeyID: 49303470
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Lync Server 2013에서 네트워크 사이트에 위치 정책 추가

 

_**마지막으로 수정된 항목:** 2013-02-24_

다음 예제에서는 [Lync Server 2013에서 위치 정책 만들기](lync-server-2013-create-location-policies.md)에 정의된 **Redmond** 위치 정책을 기존 네트워크 사이트에 추가하는 방법과 **Redmond** 위치 정책을 사용하는 새 네트워크 사이트를 만드는 방법을 보여줍니다.

네트워크 사이트 작업에 대한 자세한 내용은 다음 cmdlet에 대한 Lync Server 관리 셸 설명서를 참조하십시오.

  - **New-CsNetworkSite**

  - **Get-CsNetworkSite**

  - **Set-CsNetworkSite**

  - **Remove-CsNetworkSite**

## 기존 네트워크 사이트에 위치 정책을 지정하려면

1.  Lync Server 관리 셸 시작: **시작**, **모든 프로그램**, **Microsoft Lync Server 2013**을 차례로 클릭한 다음 **Lync Server 관리 셸**을 클릭합니다.

2.  다음 cmdlet을 실행하여 기존 네트워크 사이트를 수정합니다.
    
    태그가 지정된 **Redmond** 위치 정책을 **Redmond**라는 기존 네트워크 사이트에 지정합니다.
    
        Set-CsNetworkSite -Identity "Redmond" -NetworkRegionID "NorthAmerica" -LocationPolicy "Redmond"

## 새 네트워크 사이트에 위치 정책을 지정하려면

1.  Lync Server 관리 셸 시작: **시작**, **모든 프로그램**, **Microsoft Lync Server 2013**을 차례로 클릭한 다음 **Lync Server 관리 셸**을 클릭합니다.

2.  다음 cmdlet을 실행하여 새 네트워크 사이트를 만듭니다.
    
    네트워크 지역에 새 네트워크 사이트를 만들어 태그가 지정된 **Redmond** 위치 정책을 지정합니다.
    
        New-CsNetworkSite -Identity "Redmond" -NetworkRegionID "NorthAmerica" -LocationPolicy "Redmond"

