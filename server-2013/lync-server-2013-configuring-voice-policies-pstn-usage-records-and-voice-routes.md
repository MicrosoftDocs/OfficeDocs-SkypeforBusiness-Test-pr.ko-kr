---
title: 'Lync Server 2013: 음성 정책, PSTN 사용 레코드 및 음성 경로 구성'
TOCTitle: 음성 정책, PSTN 사용 레코드 및 음성 경로 구성
ms:assetid: 1e5a15f9-6f42-4dc6-baaa-24daf54afc4d
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg398272(v=OCS.15)
ms:contentKeyID: 49303002
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Lync Server 2013에서 음성 정책, PSTN 사용 레코드 및 음성 경로 구성

 

_**마지막으로 수정된 항목:** 2012-10-10_

음성 정책, PSTN 사용 레코드 및 음성 경로는 완전하게 관련되어 있습니다. 음성 정책을 구성하려면 전화 걸기 기능 집합을 선택한 다음, PSTN 사용 현황 레코드 집합을 정책에 할당합니다. 그러면 음성 정책이 할당되는 사용자 또는 그룹에 대해 부여되는 권한을 지정합니다. 또한 음성 경로에도 PSTN 사용 레코드가 할당됩니다. 이 레코드는 경로 사용 권한이 부여된 사용자와 경로를 일치시키는 데 사용됩니다. 즉, 사용자는 일치하는 PSTN 사용 레코드를 가진 경로를 사용하는 전화만 걸 수 있습니다.

새 Enterprise Voice 배포에 권장되는 워크플로는, 먼저 해당하는 PSTN 사용 레코드를 포함하는 음성 정책을 구성한 다음 각 PSTN 사용 레코드에 적절한 경로를 연결하는 것입니다.


> [!NOTE]
> <EM>사용자</EM> 범위를 사용하여 음성 정책을 만든 다음 개별 사용자 또는 그룹에 정책을 할당할 수도 있습니다.



이러한 각 작업을 수행하는 자세한 단계는 이 섹션의 절차를 참조하십시오.

## 이 단원의 내용

  - [Lync Server 2013에서 통화 기능 및 권한을 부여하도록 음성 정책 및 PSTN 사용 레코드 구성](lync-server-2013-configuring-voice-policies-and-pstn-usage-records-to-authorize-calling-features-and-privileges.md)

  - [Lync Server 2013에서 PSTN 사용 레코드 보기](lync-server-2013-view-pstn-usage-records.md)

  - [Lync Server 2013에서 아웃바운드 통화에 대한 음성 경로 구성](lync-server-2013-configuring-voice-routes-for-outbound-calls.md)

  - [Lync Server 2013에서 음성 라우팅 구성 내보내기 및 가져오기](lync-server-2013-exporting-and-importing-voice-routing-configuration.md)

  - [Lync Server 2013에서 음성 라우팅 구성에 보류 중인 변경 사항 게시](lync-server-2013-publish-pending-changes-to-the-voice-routing-configuration.md)

  - [Lync Server 2013에서 음성 라우팅 테스트](lync-server-2013-test-voice-routing.md)

