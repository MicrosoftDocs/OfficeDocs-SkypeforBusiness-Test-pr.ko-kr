---
title: 메시지 제거
TOCTitle: 메시지 제거
ms:assetid: 90fcb30d-4987-4e9c-afbc-4482644ce0e4
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/JJ205081(v=OCS.15)
ms:contentKeyID: 49304379
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# 메시지 제거

 

_**마지막으로 수정된 항목:** 2012-04-04_

메시지를 제거하려면

    Remove-CsPersistentChatMessage -Identity <string> [-UserUri <string>] [-StartDate <DateTime>] [-EndDate <DateTime>] [-Filter <string>] [-MatchClause <AndOr> {And | Or | Exact}] [-CaseSensitive <bool>] [-ReplaceMessage <string>] [-WhatIf] [-Confirm] [<CommonParameters>]

