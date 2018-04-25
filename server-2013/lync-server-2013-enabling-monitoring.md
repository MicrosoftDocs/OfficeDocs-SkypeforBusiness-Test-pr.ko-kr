---
title: Lync Server 2013에서 모니터링 사용
TOCTitle: Lync Server 2013에서 모니터링 사용
ms:assetid: 244df419-d0a8-4b1d-aedd-a92114172ab6
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/JJ687994(v=OCS.15)
ms:contentKeyID: 49885683
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Lync Server 2013에서 모니터링 사용

 

_**마지막으로 수정된 항목:** 2012-10-17_

통합 데이터 수집 에이전트는 각 프런트 엔드 서버에서 자동으로 설치 및 활성화되지만, Microsoft Lync Server 2013 설치를 완료하는 즉시 모니터링 데이터 수집이 시작되는 것은 아닙니다. 대신 두 가지 작업을 수행해야 합니다. 그 중 하나는 프런트 엔드 서버/프런트 엔드 풀을 모니터링 데이터베이스에 연결하는 것이고, 다른 하나는 전역 범위 및/또는 사이트 범위에서 CDR(통화 정보 기록) 및/또는 QoE(체감 품질) 모니터링을 사용하도록 설정하는 것입니다.

프런트 엔드 서버 또는 프런트 엔드 풀을 모니터링 데이터베이스와 연결하는 단계별 지침은 배포 설명서에서 [Lync Server 2013에서 프런트 엔드 풀과 모니터링 저장소 연결](lync-server-2013-associating-a-monitoring-store-with-a-front-end-pool.md) 항목을 참조하십시오. 이러한 연결을 설정하고 새 Lync Server 토폴로지를 게시한 후에도 모니터링 데이터를 수집할 수는 없습니다. Lync Server 2013 설치 시 기본적으로 CDR 및 QoE 데이터 수집은 사용하지 않도록 설정되기 때문입니다.

데이터 수집을 시작하려면 CDR 및/또는 QoE 모니터링을 사용하도록 설정해야 합니다. CDR 및 QoE 모니터링을 모두 사용하도록 설정할 필요는 없습니다. 원하는 경우 한 가지 모니터링 유형은 사용하도록 설정하고 나머지 유형은 사용하지 않도록 설정된 상태로 유지할 수 있습니다. 전역 범위에서 CDR 모니터링을 사용하도록 설정하려면 Lync Server 관리 셸 내에서 다음 명령을 실행합니다.

    Set-CsCdrConfiguration -Identity "global" -EnableCDR $True

Lync Server 2013 제어판 내에서 CDR 모니터링을 사용하도록 설정할 수도 있습니다. 이렇게 하려면 Lync Server 제어판 내에서 다음 절차를 완료합니다.

1.  **모니터링**을 클릭합니다.

2.  **통화 정보 기록** 탭에서 **전역** 설정을 두 번 클릭합니다.

3.  **CDR(통화 정보 기록) 설정 편집** 창에서 **CDR 모니터링 사용**을 선택하고 **커밋**을 클릭합니다.

전역 범위에서 QoE 모니터링을 사용하도록 설정하려면 Lync Server 관리 셸 내에서 다음 명령을 실행합니다.

    Set-CsQoEConfiguration -Identity "global" -EnableQoE $True

Lync Server 제어판 내에서 QoE 모니터링을 사용하도록 설정할 수도 있습니다. 이렇게 하려면 제어판 내에서 다음 절차를 완료합니다.

1.  **모니터링**을 클릭합니다.

2.  **체감 품질 데이터** 탭에서 **전역** 설정을 두 번 클릭합니다.

3.  **QoE(체감 품질) 설정 편집** 창에서 **QoE 데이터 모니터링 사용**을 선택하고 **커밋**을 클릭합니다.

앞에서 설명한 대로, 위의 예를 사용하면 전역 범위에서 모니터링이 사용하도록 설정됩니다. 즉, 조직 전체에서 CDR 및 QoE 모니터링이 사용하도록 설정됩니다. 사이트 범위에서 별도의 CDR 및 QoE 구성 설정을 만든 다음 각 사이트에 대해 모니터링을 선택적으로 사용하거나 사용하지 않도록 설정할 수도 있습니다. 예를 들어 CDR 모니터링을 Redmond 사이트에 대해서는 사용하도록 설정하고 Dublin 사이트에 대해서는 사용하지 않도록 설정할 수 있습니다. 모니터링 구성 설정을 관리하는 방법에 대한 자세한 내용은 배포 가이드 항목 [Lync Server 2013에서 통화 정보 기록 및 체감 품질 설정 구성](lync-server-2013-configuring-call-detail-recording-and-quality-of-experience-settings.md)을 참조하십시오.

