---
title: "Lync Server 2010/그룹 채팅/Communications Server 그룹채팅->Lync Server, 영구채팅서버 마이그레이션"
TOCTitle: "Lync Server 2010/그룹 채팅/Communications Server 그룹채팅->Lync Server, 영구채팅서버 마이그레이션"
ms:assetid: 5b4d3db1-6eba-4932-b49c-f60bcf9488f9
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg615442(v=OCS.15)
ms:contentKeyID: 49303749
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Lync Server 2010, 그룹 채팅 또는 Office Communications Server 2007 R2 그룹 채팅에서 Lync Server 2013, 영구 채팅 서버로 마이그레이션

 

_**마지막으로 수정된 항목:** 2012-10-06_

이 섹션의 항목에서는 Lync Server 2010, 그룹 채팅 또는 Office Communications Server 2007 R2그룹 채팅을 Lync Server 2013, 영구 채팅 서버로 마이그레이션하는 프로세스를 안내합니다. Lync Server 2013, 영구 채팅 서버 배포를 Lync Server 2010, 그룹 채팅 또는 Office Communications Server 2007 R2그룹 채팅 배포와 함께 사용하려는 경우, 이 설명서에는 이러한 혼합 환경에서 작업하기 위한 몇 가지 필수 정보가 포함되어 있습니다. 이 설명서에서는 주로 영구 채팅 서버에 대한 데이터 마이그레이션에 대해 자세히 설명합니다. Lync Server의 레거시 버전에서 Lync Server 2013으로 마이그레이션하는 사용자의 경우 [Lync Server 2010에서 Lync Server 2013으로 마이그레이션](migration-from-lync-server-2010-to-lync-server-2013.md) 및 [Office Communications Server 2007 R2에서 Lync Server 2013으로 마이그레이션](migration-from-office-communications-server-2007-r2-to-lync-server-2013.md)을 참조하십시오.


> [!IMPORTANT]
> 이 항목에서는 Lync Server 2010 또는 Office Communications Server 2007 R2와 함께 Lync Server 2013을 이미 설치했다고 가정합니다.




> [!IMPORTANT]
> 이 설명서에서는 각 마이그레이션 단계를 수행하는 데 일반적으로 필요한 단계에 대해 설명합니다. 모든 가능한 레거시 배포 토폴로지 또는 모든 가능한 마이그레이션 시나리오에 대해서는 여기에서 다루지 않습니다. 따라서 배포에 따라 설명된 모든 단계를 수행할 필요가 없거나 추가 단계를 수행해야 할 수도 있습니다. 이 설명서에서는 또한 확인 단계에 대한 예를 제공합니다. 이러한 확인 단계는 마이그레이션을 진행하면서 각 단계가 성공적으로 완료되었는지 보장하기 위해 조사해야 하는 항목을 확인할 수 있도록 돕기 위해 제공됩니다. 이러한 확인 단계를 사용자의 마이그레이션 프로세스에 맞게 수정할 수 있습니다.



이 설명서에서는 기존 배포 업그레이드와 관련된 정보를 제공하며 기존 토폴로지를 변경하는 방법이나 새 기능 구현은 다루지 않습니다. 단, 자세한 절차가 다른 문서에 설명되어 있는 경우 해당 문서 또는 문서 섹션으로 사용자를 안내합니다.

이 문서에서는 다음 목록에 지정된 용어를 정의합니다.

  - *마이그레이션*   
    배포를 이전 버전의 영구 채팅 서버(이전 이름은 그룹 채팅 서버)에서 Lync Server 2013, 영구 채팅 서버로 이동합니다.

<!-- end list -->

  - *업그레이드*   
    서버 또는 클라이언트 컴퓨터에 새 버전의 소프트웨어를 설치합니다.

<!-- end list -->

  - *동시 사용성*   
    마이그레이션 중에 일부 기능이 Lync Server 2013, 영구 채팅 서버로 마이그레이션되었고 다른 기능은 아직 이전 버전의 그룹 채팅 서버에 남아 있는 일시적인 환경입니다.

영구 채팅 서버는 Lync Server 2013 인프라의 확장 기능입니다. 토폴로지에 따라 Lync Server 2010, 그룹 채팅 또는 Office Communications Server 2007 R2그룹 채팅을 Lync Server 2013영구 채팅 서버로 마이그레이션할 수 있습니다. 그룹 채팅 서버를 마이그레이션하는 데 사용할 수 있는 토폴로지와 기술 및 소프트웨어 요구 사항에 대한 자세한 내용은 계획 설명서에서 [Lync Server 2013의 영구 채팅 서버 계획](lync-server-2013-planning-for-persistent-chat-server.md)을 참조하십시오.

이제는 조직에 준수 지원이 필요한 경우 각 영구 채팅 서버에 자동으로 설치됩니다. 준수를 위한 별도의 서버는 더 이상 필요하지 않습니다.


> [!IMPORTANT]
> 파일 시스템 보안을 강화하려면 영구 채팅 서버를 NTFS 파일 시스템에 설치해야 합니다. FAT32는 영구 채팅 서버용으로 지원되는 파일 시스템이 아닙니다.<BR>이제는 조직에 준수 지원이 필요한 경우 각 영구 채팅 서버에 자동으로 설치됩니다. 준수를 위한 별도의 서버는 더 이상 필요하지 않습니다. Lync Server 2013영구 채팅 서버의 변경 내용에 대한 자세한 내용은 시작 설명서에서 <A href="lync-server-2013-new-persistent-chat-server-features.md">Lync Server 2013의 새 영구 채팅 서버 기능</A>을 참조하십시오.



## 이 섹션의 내용

  - [표준 마이그레이션 시나리오 - 고급](standard-migration-scenario-high-level.md)

  - [마이그레이션 프로세스 - 세부 정보](migration-process-details.md)

  - [동시 사용 고려 사항](coexistence-considerations.md)

