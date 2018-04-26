---
title: 'Lync Server 2013: Lync Server용 Windows Update'
TOCTitle: Lync Server 2013용 Windows Update
ms:assetid: fe26ab32-b1a9-421d-9227-506703d4b834
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Dn518337(v=OCS.15)
ms:contentKeyID: 60504746
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Lync Server 2013용 Windows Update

 

_**마지막으로 수정된 항목:** 2013-12-05_

Windows Update Services를 통해 업데이트와 보안 업데이트를 자주 확인하고 적용합니다. 이렇게 하면 공격자가 관리자 권한을 사용하여 Microsoft Lync Server 2013 실행 서버에 액세스함으로써 Lync Server 2013을 손상시키는 데 사용할 수 있는 다른 시스템 구성 요소의 취약점을 없앨 수 있습니다.

Microsoft SQL Server 2008 Express(64비트 버전)용 업데이트는 이러한 데이터베이스를 SQL Server 2008 R2 Express로 업그레이드하지 않은 한 각 Lync Server 2013 Standard Edition 서버(백 엔드 데이터베이스용) 및 기타 모든 Lync Server 2013 서버 역할(로컬 구성 저장소용)에서 실행됩니다. 프런트 엔드 풀의 백 엔드 데이터베이스에 있는 SQL Server, 모니터링 데이터베이스 및 보관 데이터베이스와 같이 이러한 데이터베이스는 일상적인 보안 업데이트 유지 관리의 일부로 생각해야 합니다.

## 모범 사례

  - Windows Update를 통해 최신 상태를 유지합니다.

