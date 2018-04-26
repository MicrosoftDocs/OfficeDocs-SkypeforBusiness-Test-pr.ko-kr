---
title: 'Lync Server 2013: SQL Server에 대한 시스템 요구 사항'
TOCTitle: SQL Server에 대한 시스템 요구 사항
ms:assetid: 9c235085-cbfa-4e9e-9cec-3f5749039a6b
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/JJ205112(v=OCS.15)
ms:contentKeyID: 49304515
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Lync Server 2013의 SQL Server에 대한 시스템 요구 사항

 

_**마지막으로 수정된 항목:** 2013-10-25_

Enterprise Edition 서버를 배포하기 전에 하드웨어 요구 사항을 충족하는 전용 컴퓨터에 Microsoft SQL Server 2008 R2 또는 Microsoft SQL Server 2012를 설치합니다. 하드웨어 요구 사항에 대한 자세한 내용은 지원 가능성 설명서에서 [Lync Server 2013의 서버 하드웨어 플랫폼](lync-server-2013-server-hardware-platforms.md)을 참고하세요. 소프트웨어 요구 사항에 대한 자세한 내용은 지원 가능성 설명서에서 [Lync Server 2013의 데이터베이스 소프트웨어 지원](lync-server-2013-database-software-support.md)을 참고하세요. 배포에 필요한 사용 권한에 대한 자세한 내용은 [Lync Server 2013의 SQL Server에 대한 배포 권한](lync-server-2013-deployment-permissions-for-sql-server.md)을 참고하세요.

또한 프런트 엔드 풀을 만들기 전에 Lync Server 2013이 특정 포트를 통해 SQL Server에 액세스할 수 있도록 Windows 방화벽을 구성해야 합니다. 이렇게 하려면 SQL Server 구성 관리자를 사용하여 서버에 대해 포트를 정의하고 고급 보안이 포함된 Windows 방화벽에서 포트를 엽니다.

