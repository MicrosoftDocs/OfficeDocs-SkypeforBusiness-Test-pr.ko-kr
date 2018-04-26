---
title: 'Lync Server 2013: 분기 사이트 SIP 트렁크'
TOCTitle: 분기 사이트 SIP 트렁크
ms:assetid: c4d9dfcd-8baa-41ea-9677-48b0e429429d
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg412974(v=OCS.15)
ms:contentKeyID: 49304962
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Lync Server 2013의 분기 사이트 SIP 트렁크

 

_**마지막으로 수정된 항목:** 2012-09-21_

경우에 따라, 선택한 분기 사이트에서 분산된 SIP 트렁크를 구현해야 할 수 있습니다. 분기 사이트에 SIP 트렁크가 필요한지 여부를 확인하려면 [Lync Server 2013에서 SIP 트렁크를 구현하는 방법](lync-server-2013-how-do-i-implement-sip-trunking.md)의 내용을 참조하십시오.

분기 사이트에 SIP 트렁크를 배포할 때 지원되는 토폴로지 옵션에 대한 자세한 내용은 [Lync Server 2013의 분기 사이트 복구 솔루션](lync-server-2013-branch-site-resiliency-solutions.md)을 참조하십시오.

## 예 분기 사이트 SIP 트렁크 요구 사항 분석

분기 사이트 SIP 트렁크를 배포하도록 결정한 경우 사이트별 비용 분석을 수행해야 합니다. 예를 들어 레드몬드, 워싱턴에 중앙 사이트가 있고 뉴욕에 분기 사이트가 있는 기업은 뉴욕 사이트에서 로컬 서비스 공급자까지 SIP 트렁크를 구현할지 여부를 결정하기 위해 분석 작업을 수행해야 합니다.

뉴욕에서 분산된 SIP 트렁크가 비용 효율적인지 여부를 확인하려면 SIP 트렁크가 사용되는 DID(내선 직접 호출) 번호를 식별하고 뉴욕에서 레드몬드(425)가 아닌 지역으로 전화를 건 횟수를 분석합니다. 중앙 사이트에서 분기 사이트에 대해 DID 착신호가 발생할 수 있습니다. 예를 들어 레드몬드 중앙 사이트에서 뉴욕 분기 사이트에 대해 DID 번호를 호스팅할 수 있습니다. 분산된 SIP 트렁크 구현 비용이 이러한 통화 비용보다 적을 경우 뉴욕 분기 사이트에서 SIP 트렁크를 구현하는 것이 좋습니다.

## 기타 분기 사이트 SIP 트렁크 요구 사항

게이트웨이가 아닌 SIP 트렁크 배포 여부는 각 옵션에 대한 PSTN(공중 전화망) 장거리 전화 요금 간 차이에 기반하여 결정됩니다. 분기 사이트 SIP 트렁크를 배포할 경우 복구 및 대역폭 요구 사항도 확인해야 합니다. 분기 사이트와 중앙 사이트 간 링크가 복구 가능하고 대역폭이 충분한 경우 게이트웨이나 SIP 트렁크를 배포할 수 있습니다. SBA(Survivable Branch Appliance)에서는 분기 사이트를 배포하지 않아도 됩니다. 분기 사이트와 중앙 사이트 간 링크를 복구할 수 없는 경우 분기 사이트에서 게이트웨이나 SIP 트렁크와 함께 SBA(Survivable Branch Appliance) 또는 지속 가능 분기 서버를 배포합니다.

