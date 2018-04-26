---
title: 'Lync Server 2013: 시스템 플랫폼 설정'
TOCTitle: 시스템 플랫폼 설정
ms:assetid: 2e72e49d-2737-4b5b-8c0a-60f6ecb15bf1
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/JJ204783(v=OCS.15)
ms:contentKeyID: 49303186
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Lync Server 2013에서 시스템 플랫폼 설정

 

_**마지막으로 수정된 항목:** 2013-02-21_

영구 채팅 서버 배포를 시작하기 전에 서버의 시스템 요구 사항을 충족하는 하드웨어에 필요한 운영 체제를 설치해야 합니다.

Lync Server 2013 실행 서버, 데이터베이스 서버 및 파일 서버에 지원되는 하드웨어에 대한 자세한 내용은 지원 가능성 설명서에서 [Lync Server 2013에서 지원되는 하드웨어](lync-server-2013-supported-hardware.md)를 참조하십시오. 지원되는 운영 체제 및 데이터베이스 소프트웨어에 대한 자세한 내용은 지원 가능성 설명서에서 [Lync Server 2013의 서버 소프트웨어 및 인프라 지원](lync-server-2013-server-software-and-infrastructure-support.md)을 참조하십시오. Windows 업데이트 요구 사항에 대한 자세한 내용은 지원 가능성 설명서에서 [Lync Server 2013의 추가 서버 지원 및 요구 사항](lync-server-2013-additional-server-support-and-requirements.md)을 참조하십시오.

영구 채팅 서버프런트 엔드 서버, **PersistentChatService**는 Lync Server 2013Enterprise Edition 풀에 포함된 하나 이상의 독립 실행형 컴퓨터에 배포할 수 있습니다. 그러나 Lync ServerEnterprise Edition프런트 엔드 서버에 배치할 수는 없습니다. 영구 채팅 서버는 다른 Lync Server 역할과 마찬가지로 부트스트래퍼를 통해 배포할 수 있습니다. **파일 업로드/다운로드용 영구 채팅 웹 서비스** 및 **채팅방 관리용 영구 채팅 웹 서비스**는 Lync Server 2013프런트 엔드 서버에 배포되는 웹 구성 요소입니다.

단일 영구 채팅 서버프런트 엔드 서버는 활성 사용자 2만 명을 지원할 수 있습니다. 영구 채팅 서버 풀에는 활성 프런트 엔드를 4개까지 포함할 수 있으므로 지원 가능한 동시 사용자 수는 총 8만 명입니다. 영구 채팅백 엔드 서버, **PersistentChatStore**는 채팅방 및 범주를 저장합니다. **PersistentChatStore**는 Enterprise Edition 풀의 전용 SQL Server백 엔드 서버에 설치하는 것이 좋지만, Lync Server 2013백 엔드 서버 및 **PersistentChatStore**를 같은 SQL Server 인스턴스에 배치하는 방식도 지원되기는 합니다.

조직에서 준수를 지원해야 하는 경우에는 토폴로지 작성기를 사용하여 준수를 설치할 수 있습니다. 영구 채팅 서버 준수 서비스는 영구 채팅 서버프런트 엔드 서버와 같은 컴퓨터에 설치됩니다. 준수용으로 별도의 데이터베이스가 필요합니다. 영구 채팅 서버의 준수 요구 사항에 대한 자세한 내용은 계획 설명서에서 [Lync Server 2013의 영구 채팅 서버 계획](lync-server-2013-planning-for-persistent-chat-server.md)을 참조하십시오.

각 토폴로지에는 최소한 Lync Server 2013이 설치된 서버와 SQL Server 데이터베이스 소프트웨어가 설치된 서버가 필요합니다. 토폴로지 작성기에서는 여러 영구 채팅 서버 풀을 지원합니다. 여러 영구 채팅 서버 풀을 배포할 때도 배포 설명서의 [Lync Server 2013 배포](lync-server-2013-deploying-lync-server.md)에 나와 있는 일반적인 풀 배포 지침을 따릅니다.

영구 채팅 서버를 Lync Server 2013Standard Edition과 함께 배포할 수도 있습니다. 이 경우 **PersistentChatService**프런트 엔드 서버는 Standard Edition 서버에 배치되며, **PersistentChatStore**백 엔드 서버를 로컬 SQL Server Express 인스턴스에 배포할 수 있습니다.


> [!IMPORTANT]
> 영구 채팅 서버Standard Edition에서는 고가용성이 지원되지 않습니다. 성능 및 확장 기능은 제한됩니다. 또한 새로운 영구 채팅 서버&nbsp; Standard Edition 서버 배포만 지원됩니다. 즉, Lync Server 2010, 그룹 채팅 서버에서 Lync Server 2013영구 채팅 서버Standard Edition으로의 업그레이드는 지원되지 않습니다.



## 참고 항목

#### 개념

[Lync Server 2013의 추가 서버 지원 및 요구 사항](lync-server-2013-additional-server-support-and-requirements.md)  

#### 기타 리소스

[Lync Server 2013에서 지원되는 하드웨어](lync-server-2013-supported-hardware.md)  
[Lync Server 2013의 서버 소프트웨어 및 인프라 지원](lync-server-2013-server-software-and-infrastructure-support.md)  
[Lync Server 2013의 영구 채팅 서버 계획](lync-server-2013-planning-for-persistent-chat-server.md)  
[Lync Server 2013 배포](lync-server-2013-deploying-lync-server.md)

