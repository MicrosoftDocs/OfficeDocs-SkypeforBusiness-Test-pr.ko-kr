---
title: Lync Server 2013에서 비디오 대역폭 구성
TOCTitle: Lync Server 2013에서 비디오 대역폭 구성
ms:assetid: 446bed91-b26f-4ab2-b2f5-36e6810b405b
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/JJ204842(v=OCS.15)
ms:contentKeyID: 49303478
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Lync Server 2013에서 비디오 대역폭 구성

 

_**마지막으로 수정된 항목:** 2012-10-02_

Lync Server 2013에는 두 사용자 간 통화 및 단체 회의에서 비디오를 관리하기 위한 몇 가지 설정이 포함됩니다. Lync Server 2013을 배포할 때는 자신의 조직에 기본 설정이 적합한지 여부를 평가하고 필요에 따라 수정해야 합니다.

이 섹션에 설명된 매개 변수는 두 사용자 간 통화 및 단체 회의 모두에 적용됩니다. 다음 cmdlet 중 하나를 사용하여 설정을 보거나 수정하십시오.

  - **Get-CsConferencingPolicy**

  - **Set-CsConferencingPolicy**

  - **New-CsConferencingPolicy**

회의 정책에서 다음 설정을 확인합니다.

  - **VideoBitRateKb**   이 설정은 사용자가 전송한 비디오에 사용되는 최대 비디오 비트 전송률(kbps)을 지정합니다. 기본값은 5000kbps입니다. 유효한 값은 0부터 5000까지입니다.
    
    이 설정은 기본 비디오 및 파노라마 비디오에 별개로 적용됩니다.
    
    예: 2000kbps를 지정한 경우 Lync Server는 기본 비디오 스트림을 2000kbps로 전송하고 파노라마 비디오 스트림을 2000kbps로 전송할 수 있습니다.
    

    > [!NOTE]
    > Lync 2013 끝점에 대한 최대 비디오 네트워크 대역폭은 기본 비디오의 경우 8000kbps이고 파노라마 비디오의 경우 2500kbps입니다. 이러한 최대값은 여러 개의 비디오를 수신하거나 전송하는 경우에만 도달합니다. 자세한 내용은 <A href="lync-server-2013-network-bandwidth-requirements-for-media-traffic.md">미디어 트래픽에 대한 네트워크 대역폭 요구 사항</A>의 "미디어 트래픽 네트워크 사용" 섹션을 참조하십시오. 이 섹션에는 지원되는 모든 해상도에 대한 최대 및 일반 비디오 스트림 대역폭이 표시되어 있습니다.



  - **TotalReceiveVideoBitRateKb**   Lync Server 2013에서 새롭게 제공되는 이 설정은 클라이언트가 수신할 수 있는 모든 비디오 스트림에 대해 허용되는 최대 비트 전송률(초당 킬로비트 수)을 지정합니다. 예를 들어 150kbps를 지정한 경우 클라이언트는 여러 개의 비디오 스트림을 수신하든 단일 비디오 스트림을 수신하든 간에 최대 1500kbs의 속도로 비디오를 수신할 수 있습니다. 이 설정은 Lync Server 2013 클라이언트에만 적용됩니다.
    
    **TotalReceiveVideoBitRateKb**의 기본값은 50000kbps입니다. 갤러리 보기에 대한 **EnableMultiviewJoin** 설정이 True인 경우, **TotalReceiveVideoBitRateKb**는 420kbps 아래로 설정되지 않아야 합니다. 갤러리 보기에 대한 **EnableMultiviewJoin** 설정이 False인 경우, **TotalReceiveVideoBitRateKb**는 100kbps 아래로 설정되지 않아야 합니다. **EnableMultiviewJoin**이 True로 설정되었고 값을 420kbps 아래로 설정하면 값이 기본적으로 임계값으로 설정됩니다. 이 임계값은 사용자 경험 품질이 저하될 수 있는 잘못된 구성을 실수로 설정하지 않도록 방지합니다.
    

    > [!NOTE]
    > <STRONG>EnableMultiviewJoin</STRONG> 설정에 대한 자세한 내용은 <A href="lync-server-2013-configuring-gallery-view.md">갤러리 보기 구성</A>을 참조하십시오.



  - **MaxVideoConferencingResolution**   이 매개 변수는 Lync Server 2013 회의의 Lync Server 2013 클라이언트에서 더 이상 사용되지 않습니다. Lync Server 2013 회의에는 이 섹션의 앞 부분에서 설명한 비트 전송률 컨트롤이 사용됩니다. 이 설정은 Lync Server 2013 회의에 참가하는 레거시 클라이언트에 대해 계속 사용됩니다. 이 매개 변수는 Lync Server 2013에 있는 사용자가 구성하는 회의에서 레거시 클라이언에 대해 허용되는 최대 해상도를 결정합니다. 즉, 레거시 클라이언트는 이전 버전의 Lync Server 또는 Office Communications Server에서와 동일하게 처리됩니다.

사용자에게 적용되는 회의 정책 설정 외에도 미디어 구성 설정을 평가하십시오. 다음 cmdlet 중 하나를 사용하여 설정을 보거나 수정합니다.

  - **Get-CsMediaConfiguration**

  - **Set- CsMediaConfiguration**

  - **New- CsMediaConfiguration**

다음 설정을 확인합니다.

  - **MaxVideoRateAllowed**   이 풀당 설정은 클라이언트 끝점에서 비디오 신호를 전송할 수 있는 최대 전송률을 지정합니다. 이 설정은 이전 버전의 Lync Server 클라이언트에도 적용됩니다.
    

    > [!NOTE]
    > Lync Server 2013 클라이언트는 이 설정을 무시하고 회의 정책의 TotalReceiveVideoBitRateKb 설정을 대신 사용합니다.

    
    기본값은 HD720P입니다. 유효 값은 HD720p15M, VGA600K 및 CIF250K입니다.
    
    예: 1500kbps를 지정한 경우 풀의 모든 레거시 클라이언트가 두 사람 간의 회의 또는 단체 회의에서 최대 1500kbps로 비디오를 수신할 수 있습니다.

다음 절차에서는 Lync Server 관리 셸을 사용하여 이 섹션에 설명된 설정을 수정하는 방법을 예로 보여줍니다.

## 비디오 설정에 대한 회의 정책을 수정하려면

1.  Lync Server 관리 셸 시작: **시작**, **모든 프로그램**, **Microsoft Lync Server 2013**을 차례로 클릭한 다음 **Lync Server 관리 셸**을 클릭합니다.

2.  명령줄에서 다음 cmdlet을 실행하여 회의 정책을 편집합니다.
    
        Set-CsConferencingPolicy -Identity Pool01ConferencingPolicy -VideoBitRateKb 2000 -TotalReceiveVideoBitRateKb 2000 

## 레거시 클라이언트에 대한 미디어 구성을 수정하려면

1.  Lync Server 관리 셸 시작: **시작**, **모든 프로그램**, **Microsoft Lync Server 2013**을 차례로 클릭한 다음 **Lync Server 관리 셸**을 클릭합니다.

2.  명령줄에서 다음 cmdlet을 실행하여 미디어 구성을 편집합니다.
    
        Set-CsMediaConfiguration -Identity site:Redmond01 -MaxVideoRateAllowed CIF250K

