---
title: 'Lync Server 2013: 토폴로지 작성기로 재해 복구 및 고가용성 구성'
TOCTitle: 토폴로지 작성기로 재해 복구 및 고가용성 구성
ms:assetid: abc1a25d-1f5e-46ef-91d2-0144fc847206
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/JJ205172(v=OCS.15)
ms:contentKeyID: 49304682
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Lync Server 2013에서 토폴로지 작성기로 재해 복구 및 고가용성 구성

 

_**마지막으로 수정된 항목:** 2012-10-06_

영구 채팅 서버에 대한 고가용성과 재해 복구를 구성하려면 토폴로지 작성기 내에서 다음 단계를 수행하십시오.

1.  미러 데이터베이스 및 로그 전달 보조 데이터베이스 SQL Server 저장소를 추가합니다.

2.  영구 채팅 서버 서비스 속성을 다음과 같이 편집합니다.
    
    1.  주 데이터베이스에 대한 미러링을 사용하도록 설정합니다.
    
    2.  주 미러 SQL Server 저장소를 추가합니다.
    
    3.  SQL Server 로그 전달 데이터베이스를 사용하도록 설정합니다.
    
    4.  SQL Server 로그 전달 보조 SQL Server 저장소를 추가합니다.
    
    5.  보조 데이터베이스에 대한 SQL Server 저장소 미러를 추가합니다.
    
    6.  토폴로지를 게시합니다.

