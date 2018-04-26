---
title: 'Lync Server 2013: 영구 채팅 서버 배포'
TOCTitle: 영구 채팅 서버 배포
ms:assetid: e3b930fb-6855-47f0-b6b3-7dfae386540d
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/JJ205357(v=OCS.15)
ms:contentKeyID: 49305316
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Lync Server 2013에서 영구 채팅 서버 배포

 

_**마지막으로 수정된 항목:** 2014-03-31_

Lync Server 2013의 영구 채팅 서버는 Lync Server 2013 인프라의 일부입니다.

영구 채팅 서버를 배포하려면 다음을 실행해야 합니다.

  - 토폴로지 작성기를 사용하여 배포할 토폴로지 및 구성 요소를 정의하거나 가져온 후 게시합니다.

  - 영구 채팅 서버 구성 요소 배포를 위한 환경을 준비합니다.

  - 배포할 영구 채팅 서버 구성 요소를 설치하고 구성합니다.

영구 채팅 서버는 개별 서버( Enterprise Edition프런트 엔드 서버와는 다른 위치에 있음)로서 Lync Server 2013Enterprise Edition과 함께 사용할 수 있습니다. 영구 채팅 서버에서 대화방 콘텐츠 및 기타 관련 메타데이터를 저장하려면 Enterprise Edition 풀에 SQL Server백 엔드 서버가 있어야 합니다. 동일한 SQL Server 인스턴스에 Lync Server 2013백 엔드 서버 및 **PersistentChatStore**를 함께 배치할 수는 있지만 전용 SQL Server백 엔드 서버에 **PersistentChatStore**를 설치하는 것이 좋습니다.

영구 채팅 서버를 Lync Server 2013Standard Edition과 함께 배포할 수도 있습니다. 이 경우 **PersistentChatService**프런트 엔드 서버가 Standard Edition 컴퓨터에 함께 배치되며, **PersistentChatStore**백 엔드 서버를 로컬 SQL Server Express 인스턴스에 배포할 수 있습니다.

지원되는 배치 구성에 대한 자세한 내용은 [Lync Server 2013의 지원되는 서버 배치](lync-server-2013-supported-server-collocation.md)를 참고하세요.


> [!IMPORTANT]
> 영구 채팅 서버Standard Edition에 대한 고가용성은 지원되지 않으며 성능과 확장성도 제한됩니다. 또한 새로운 영구 채팅 서버Standard Edition 서버만 지원됩니다. Lync Server 2010, 그룹 채팅 서버에서 Lync Server 2013영구 채팅 서버Standard Edition으로는 업그레이드할 수 없습니다.



조직에 준수 지원이 필요할 경우 영구 채팅 서버 준수 서비스를 영구 채팅 서버프런트 엔드 서버에 설치할 수 있습니다. 준수용으로 별도의 데이터베이스가 필요합니다.

최소한 각 토폴로지에 Lync Server 2013이 설치된 서버와 SQL Server 데이터베이스 소프트웨어가 설치된 서버가 한 대씩 있어야 합니다.

토폴로지 작성기를 사용하여 영구 채팅 서버를 Lync Server 2013 배포에 추가합니다. 토폴로지 작성기를 사용하여 하나 이상의 영구 채팅 서버 풀을 추가할 수 있습니다. 다른 모든 풀과 마찬가지로 동일한 배포 지침에 따라 여러 영구 채팅 서버 풀을 배포합니다. 자세한 내용은 배포 설명서의 [Lync Server 2013 배포](lync-server-2013-deploying-lync-server.md)를 참조하십시오.

사용 가능한 토폴로지와 영구 채팅 서버 설치를 위한 기술 및 소프트웨어 요구 사항에 대한 자세한 내용은 계획 설명서의 [Lync Server 2013의 영구 채팅 서버 계획](lync-server-2013-planning-for-persistent-chat-server.md)과 [Lync Server 2013에서 영구 채팅 서버의 작동 방법](lync-server-2013-how-persistent-chat-server-works.md), 배포 설명서 또는 운영 설명서 및 지원 가능성 설명서의 [Lync Server 2013에서 지원되는 하드웨어](lync-server-2013-supported-hardware.md)를 참조하십시오.

인증서 얻기, SQL Server 데이터베이스 만들기, 파일 저장소 만들기에 대한 자세한 내용은 배포 설명서의 [Lync Server 2013 배포](lync-server-2013-deploying-lync-server.md)를 참고하세요.

단일 영구 채팅 서버프런트 엔드 서버에서는 20,000명의 활성 사용자를 지원할 수 있습니다. 최대 4개의 활성 프런트 엔드 서버와 영구 채팅 서버 풀이 있을 경우 총 80,000명의 동시 사용자를 지원할 수 있습니다.

영구 채팅 서버도 가상 서버에서 지원됩니다. 가상 서버는 실제 서버의 사양과 일치할 경우 최대 20,000명의 동시 사용자를 지원할 수 있습니다.


> [!IMPORTANT]
> 파일 시스템 보안을 강화하려면 영구 채팅 서버를 NTFS 파일 시스템에 설치해야 합니다. FAT32는 영구 채팅 서버용으로 지원되는 파일 시스템이 아닙니다.



## 이 섹션의 내용

  - [Lync Server 2013에서 영구 채팅 서버의 작동 방법](lync-server-2013-how-persistent-chat-server-works.md)

  - [Lync Server 2013의 영구 채팅 서버용 배포 검사 목록](lync-server-2013-deployment-checklist-for-persistent-chat-server.md)

  - [Lync Server 2013의 영구 채팅 서버에 대한 기술 요구 사항](lync-server-2013-technical-requirements-for-persistent-chat-server.md)

  - [Lync Server 2013에서 영구 채팅 서버에 대한 시스템 및 인프라 설정](lync-server-2013-setting-up-systems-and-infrastructure-for-persistent-chat-server.md)

  - [Lync Server 2013에서 배포에 영구 채팅 서버 추가](lync-server-2013-adding-persistent-chat-server-to-your-deployment.md)

  - [Lync Server 2013에서 영구 채팅 서버 설치](lync-server-2013-installing-persistent-chat-server.md)

  - [Lync Server 2013에서 영구 채팅 관리자 추가](lync-server-2013-adding-a-persistent-chat-administrator.md)

  - [Lync Server 2013에서 영구 채팅 서버 구성](lync-server-2013-configuring-persistent-chat-server.md)

  - [Windows PowerShell cmdlet으로 영구 채팅 서버 구성](configuring-persistent-chat-server-by-using-windows-powershell-cmdlets.md)

  - [Lync Server 2013에서 Windows PowerShell cmdlet으로 영구 채팅 서버 구성 문제 해결](lync-server-2013-troubleshooting-persistent-chat-server-configuration-using-windows-powershell-cmdlets.md)

  - [Lync Server 2013에서 고가용성 및 재해 복구를 위한 영구 채팅 서버 구성](lync-server-2013-configuring-persistent-chat-server-for-high-availability-and-disaster-recovery.md)

  - [Lync Server 2013의 영구 채팅 서버 장애 조치(failover) 및 장애 복구(failback)](lync-server-2013-failing-over-and-failing-back-persistent-chat-server.md)

