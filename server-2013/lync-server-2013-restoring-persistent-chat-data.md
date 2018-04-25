---
title: 영구 채팅 데이터 복원
TOCTitle: 영구 채팅 데이터 복원
ms:assetid: c251a7fa-50da-434b-b39a-17f5978ce736
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/JJ945649(v=OCS.15)
ms:contentKeyID: 52056953
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# 영구 채팅 데이터 복원

 

_**마지막으로 수정된 항목:** 2013-02-18_

영구 채팅 대화방 콘텐츠는 영구 채팅 데이터베이스(mgc.mdf)에 저장됩니다. 이 콘텐츠는 정기적으로 백업해야 하는 업무상 중요한 데이터입니다. 대화방 콘텐츠 외에 영구 채팅 데이터베이스에는 계정(예: 사용자, 그룹 등) 및 이러한 계정이 대화방 및 대화방 콘텐츠에 대해 가지는 역할 및 액세스 권한에 대한 정보도 저장됩니다.

영구 채팅 데이터를 복원하는 방법은 해당 데이터를 백업할 때 사용한 방법에 따라 달라집니다.

  - SQL Server 백업 절차를 사용했다면 SQL Server 복원 절차를 사용해야 합니다.

  - **Export-CsPersistentChatData** cmdlet을 사용하여 영구 채팅 데이터를 백업했다면 **Import-CsPersistentChatData** cmdlet을 사용하여 데이터를 복원해야 합니다.

