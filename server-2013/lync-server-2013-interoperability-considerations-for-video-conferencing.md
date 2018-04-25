---
title: 비디오 회의를 위한 상호 운용성 고려 사항
TOCTitle: 비디오 회의를 위한 상호 운용성 고려 사항
ms:assetid: 31ead3b5-ed95-42d4-96e2-7d9403d5c026
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/JJ204790(v=OCS.15)
ms:contentKeyID: 49303230
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# 비디오 회의를 위한 상호 운용성 고려 사항

 

_**마지막으로 수정된 항목:** 2012-10-02_

이 섹션에서는 마이그레이션의 동시 사용 단계 중(레거시 클라이언트 및 Lync Server 2013 풀 또는 Lync Server 2013 클라이언트와 레거시 풀이 상호 운용되는 경우) 사용자 환경에 대해 설명합니다.

## Lync Server 2013 풀

Lync Server 2013 풀에서 레거시 클라이언트를 사용하는 경우 다음과 같은 동작이 수행됩니다.

  - 두 사용자 간의 통화에서는 비디오 해상도가 레거시 풀과 동일하게 설정됩니다.

  - 단체 전화 회의에서는 비디오 해상도 및 비디오 회의 기능이 레거시 풀과 동일하게 설정됩니다. 갤러리 보기 및 고해상도는 사용할 수 없습니다.

## 레거시 풀

레거시 풀에서 Lync Server 2013 클라이언트를 사용하는 경우 다음과 같은 동작이 수행됩니다.

  - 두 사용자 간의 통화에서는 Lync Server 2013 클라이언트가 다음과 같은 새 기능을 사용할 수 있습니다.
    
      - 두 참가자가 모두 Lync Server 2013 클라이언트를 사용하는 경우 H.264를 사용할 수 있습니다.
    
      - Lync Server 2013 클라이언트는 TotalReceiveVideoBitRateKb에 대해 기본값을 사용하는데, 이는 레거시 서버가 인밴드 프로비전을 통해 이 정보를 보내지 않기 때문입니다.

  - 단체 전화 회의에서는 비디오 해상도 및 비디오 회의 기능이 레거시 풀의 레거시 클라이언트에 사용되는 것과 동일하게 설정됩니다.


> [!NOTE]
> 레거시 서버에서 Lync Server 2013 클라이언트를 호스팅할 때는 풀의 모든 사용자가 저해상도 비디오만 받고 고해상도 비디오를 보내도록 비디오 회의 대역폭을 구성할 수 있습니다. 미디어 구성에서는 MaxVideoRateAllowed를 CIF-250K로 설정하고 회의 정책에서는 VideoBitRateKb를 2000kbps로 설정하는 경우를 한 가지 예로 들 수 있습니다. 이러한 상황에서는 풀의 사용자에 대해 고해상도를 사용할 수 없게 됩니다.<BR>MaxVideoRateAllowed는 Lync Server 2013 클라이언트에 대해 더 이상 사용되지 않으므로 Lync Server 2013 클라이언트의 고해상도 비디오 요청을 차단할 수 없습니다. 대신 풀의 모든 사용자에 대해 회의 정책의 VideoBitRateKb를 MaxVideoRateAllowed와 같은 값으로 설정하십시오(CIF를 250kbps로 설정하거나, VGA를 600kbps로 설정하거나, HD를 1500kbps로 설정함).


