---
title: Lync Server 2013에서 CAC에 대한 네트워크 지역 구성
TOCTitle: Lync Server 2013에서 CAC에 대한 네트워크 지역 구성
ms:assetid: ea3ff988-dd5a-4bc4-bec5-39a0fb09793a
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg399051(v=OCS.15)
ms:contentKeyID: 49305410
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Lync Server 2013에서 CAC에 대한 네트워크 지역 구성

 

_**마지막으로 수정된 항목:** 2012-09-21_


> [!IMPORTANT]
> E9-1-1 또는 미디어 바이패스에 대해 네트워크 영역을 이미 만든 경우 <STRONG>Set-CsNetworkRegion</STRONG> cmdlet을 사용하여 CAC(통화 허용 제어 서비스) 관련 설정을 추가하여 기존 네트워크 영역을 수정할 수 있습니다. 네트워크 영역을 수정하는 방법에 대한 예제를 보려면 <A href="lync-server-2013-create-or-modify-a-network-region.md">Lync Server 2013에서 네트워크 지역 만들기 또는 수정</A>을 참조하십시오.



*네트워크 지역*은 CAC, E9-1-1 및 미디어 바이패스를 구성하는 데 사용되는 네트워크 허브나 백본입니다. 다음 절차를 사용하여 CAC에 대한 네트워크 토폴로지 예의 네트워크 지역에 따라 조정된 네트워크 지역을 만듭니다. 네트워크 토폴로지 예를 보려면 계획 설명서에서 [예: Lync Server 2013에서 통화 허용 제어 서비스에 대한 요구 사항 수집](lync-server-2013-example-of-gathering-your-requirements-for-call-admission-control.md)을 참조하십시오.

CAC에 대한 네트워크 토폴로지의 예에는 다음과 같은 세 개의 지역이 포함됩니다. 북미, EMEA, APAC 이렇게 세 개의 네트워크 지역이 있습니다. 지역마다 중앙 사이트가 지정되어 있습니다. 북미 지역의 경우 지정된 중앙 사이트 이름은 CHICAGO입니다. 다음 절차에는 **New-CsNetworkRegion** cmdlet을 사용하여 북미 지역을 만드는 방법에 대한 예가 나와 있습니다.


> [!NOTE]
> 다음 절차에서는 Lync Server 관리 셸을 사용하여 네트워크 지역을 만듭니다. Lync Server 제어판 사용에 대한 자세한 내용은 <A href="lync-server-2013-create-or-modify-a-network-region.md">Lync Server 2013에서 네트워크 지역 만들기 또는 수정</A>을 참조하십시오.



## 통화 허용 제어에 대한 네트워크 지역을 만들려면

1.  Lync Server 관리 셸 시작: **시작**, **모든 프로그램**, **Microsoft Lync Server 2013**을 차례로 클릭한 다음 **Lync Server 관리 셸**을 클릭합니다.

2.  만들어야 하는 각 지역에 대해 **New-CsNetworkRegion** cmdlet을 실행합니다. 예를 들어 북미 지역을 만들려면 다음을 실행합니다.
    
        New-CsNetworkRegion -Identity NorthAmerica -CentralSite CHICAGO -Description "All North America Locations"

3.  2단계를 반복하여 네트워크 지역 EMEA 및 APAC을 만듭니다.

