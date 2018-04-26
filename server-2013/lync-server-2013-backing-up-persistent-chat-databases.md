---
title: 영구 채팅 데이터베이스 백업
TOCTitle: 영구 채팅 데이터베이스 백업
ms:assetid: b99ebdc0-a025-44d7-9d74-37a7365f330d
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/JJ945646(v=OCS.15)
ms:contentKeyID: 52056929
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# 영구 채팅 데이터베이스 백업

 

_**마지막으로 수정된 항목:** 2013-02-17_

영구 채팅 대화방 콘텐츠는 영구 채팅 데이터베이스(Mgc.mdf)에 저장됩니다. 이 콘텐츠는 정기적으로 백업해야 하는 업무상 중요한 데이터입니다. 대화방 콘텐츠 외에 영구 채팅 데이터베이스에는 계정(예: 사용자, 사용자 그룹 등) 및 이러한 계정이 대화방에 대해 가지는 역할 및 액세스 권한에 대한 정보도 저장됩니다.

영구 채팅 데이터는 두 가지 방법으로 백업할 수 있습니다.

  - SQL Server 백업

  - 영구 채팅 데이터를 파일로 내보내는 `Export-CsPersistentChatData` cmdlet

SQL Server 백업을 통해 만들어지는 데이터의 경우 `Export-CsPersistentChatData`를 통해 만들어지는 데이터보다 훨씬 더 많은 디스크 공간(약 20배 이상)이 필요하지만 관리자는 대개 SQL Server 백업 절차에 익숙합니다.

