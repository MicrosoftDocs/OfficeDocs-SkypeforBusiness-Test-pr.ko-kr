---
title: 'Lync Server 2013: 에지 및 디렉터 토폴로지 구성'
TOCTitle: 에지 및 디렉터 토폴로지 구성
ms:assetid: 11e5759e-d69f-4c39-8994-f467c279c558
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg398202(v=OCS.15)
ms:contentKeyID: 49302860
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Lync Server 2013에서 에지 및 디렉터 토폴로지 구성

 

_**마지막으로 수정된 항목:** 2012-09-08_

토폴로지를 작성할 때는 다음과 같은 계획 및 배포 작업을 수행합니다.

  - **계획**   조직에 적합한 토폴로지를 정의하고 해당 토폴로지를 배포하는 데 필요한 구성 요소를 파악해야 합니다. 이러한 작업은 계획 프로세스의 표준 단계입니다. Lync Server 2013에서 제공되는 Microsoft Lync Server 2013계획 도구를 사용하면 계획 프로세스를 쉽게 시작할 수 있을 뿐 아니라, 요구 사항 및 계획을 확정한 후에도 쉽게 변경할 수 있습니다.

  - **배포**    토폴로지 작성기를 사용하여 정의하는 토폴로지는 Lync Server 2013 서버 배포에 필수적인 항목입니다. 계획 작업의 일부분으로 토폴로지 작성기를 사용한 토폴로지 정의 및 게시를 완료하지 않는 경우에는 에지 서버를 배포하기 전에 해당 작업을 완료하고 토폴로지를 게시해야 합니다.

내부 풀을 하나 이상 배포하기 전에는 에지 서버 구성 요소를 배포할 수 없으며, 내부 서버를 배포하려면 토폴로지 작성기를 설치해야 합니다. 이 섹션에서는 토폴로지 작성기 설치에 대해서는 설명하지 않습니다. 이 작업은 내부 풀 설치 프로세스의 일부분이기 때문입니다.

이러한 도구에 대한 자세한 내용은 [Lync Server 2013의 외부 사용자 액세스를 위한 배포 검사 목록](lync-server-2013-deployment-checklist-for-external-user-access.md)을 참조하십시오.


> [!NOTE]
> 이전에 토폴로지 작성기를 사용하여 에지 토폴로지를 비롯한 전체 토폴로지를 정의한 경우에는 이 섹션의 <A href="lync-server-2013-define-your-edge-topology.md">Lync Server 2013에서 에지 토폴로지 정의</A> 및 <A href="lync-server-2013-publish-your-topology.md">Lync Server 2013에서 토폴로지 게시</A> 작업을 건너뛰어도 됩니다. 그러나 <A href="lync-server-2013-export-your-topology-and-copy-it-to-external-media-for-edge-installation.md">Lync Server 2013 토폴로지 내보내기 및 에지 설치용 외부 미디어에 토폴로지 복사</A> 작업은 완료해야 합니다.



## 이 단원의 내용

  - [Lync Server 2013에서 에지 토폴로지 정의](lync-server-2013-define-your-edge-topology.md)

  - [Lync Server 2013에 대한 토폴로지에서 선택적 디렉터 토폴로지 정의](lync-server-2013-define-optional-director-topologies-in-your-topology.md)

  - [Lync Server 2013에서 토폴로지 게시](lync-server-2013-publish-your-topology.md)

  - [Lync Server 2013 토폴로지 내보내기 및 에지 설치용 외부 미디어에 토폴로지 복사](lync-server-2013-export-your-topology-and-copy-it-to-external-media-for-edge-installation.md)

