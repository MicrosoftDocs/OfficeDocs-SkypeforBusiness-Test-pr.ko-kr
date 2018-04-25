---
title: 'Lync Server 2013: SIP 트렁크에 대한 통화 허용 제어 서비스'
TOCTitle: SIP 트렁크에 대한 통화 허용 제어 서비스
ms:assetid: 7eada098-3d47-4be2-839f-8f87d582efe8
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg398632(v=OCS.15)
ms:contentKeyID: 49304175
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Lync Server 2013의 SIP 트렁크에 대한 통화 허용 제어 서비스

 

_**마지막으로 수정된 항목:** 2012-09-22_

SIP 트렁크에 CAC(통화 허용 제어)를 배포하려면 ITSP(인터넷 전화 통신 서비스 공급자)를 나타내는 네트워크 사이트를 만듭니다. SIP 트렁크에 대역폭 정책 값을 적용하려면 엔터프라이즈의 네트워크 사이트와 ITSP를 나타내기 위해 만든 네트워크 사이트 간의 사이트 간 정책을 만듭니다.

다음 그림에서는 SIP 트렁크에 대한 예제 CAC 배포를 보여 줍니다.

**SIP 트렁크에 대한 CAC 구성**

![통화 허용 제어 SIP 트렁크 다이어그램](images/Gg398632.276c0d8f-1dd5-4883-8499-c202399ddbe9(OCS.15).jpg "통화 허용 제어 SIP 트렁크 다이어그램")

SIP 트렁크에 CAC를 구성하려면 CAC 배포 중에 다음 작업을 수행해야 합니다.

1.  ITSP를 나타내는 네트워크 사이트를 만듭니다. 네트워크 사이트를 적절한 네트워크 지역에 연결하고 이 네트워크 사이트에 오디오 및 비디오 대역폭으로 0을 할당합니다. 자세한 내용은 배포 설명서의 [Lync Server 2013에서 CAC에 대한 네트워크 사이트 구성](lync-server-2013-configure-network-sites-for-cac.md)을 참조하십시오.
    

    > [!NOTE]
    > ITSP에 대해서는 이 네트워크 사이트 구성이 작동하지 않습니다. 대역폭 정책 값은 2단계에서 실제로 적용됩니다.



2.  1단계에서 만든 사이트에 대한 관련 매개 변수 값을 사용하여 SIP 트렁크에 대한 사이트 간 링크를 만듭니다. 예를 들어 엔터프라이즈의 네트워크 사이트 이름을 NetworkSiteID1 매개 변수 값으로 사용하고 ITSP 네트워크 사이트를 NetworkSiteID2 매개 변수 값으로 사용합니다. 자세한 내용은 배포 설명서의 [Lync Server 2013에서 새 네트워크 사이트 간 정책 만들기](lync-server-2013-create-network-intersite-policies.md)를 참조하십시오. 또한 New-CsNetworkInterSitePolicy cmdlet에 대한 Lync Server 관리 셸 설명서를 참조하십시오.

3.  ITSP로부터 SCB(세션 경계 컨트롤러) 미디어 종료 지점의 IP 주소를 얻습니다. 해당 IP 주소(서브넷 마스크 32 포함)를 ITSP를 나타내는 네트워크 사이트에 추가합니다. 자세한 내용은 [Lync Server 2013 에서 네트워크 사이트에 서브넷 연결](lync-server-2013-associate-a-subnet-with-a-network-site.md)을 참조하십시오.

