---
title: 'Lync Server 2013: 보관 개요'
TOCTitle: 보관 개요
ms:assetid: 1e3c2ef1-f561-4f57-8b6a-7d78addc1ed1
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/JJ204729(v=OCS.15)
ms:contentKeyID: 49302999
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Lync Server 2013의 보관 개요

 

_**마지막으로 수정된 항목:** 2013-09-30_

Lync Server 2013에서 보관을 사용하면 Lync Server 2013을 통해 전송되는 통신 내용을 보관할 수 있습니다.

보관은 초기 Lync Server 2013 배포의 일부분으로 구현할 수도 있고 기존 배포에 추가할 수도 있습니다. 보관 데이터 저장소로 Lync Server 2013 보관 데이터베이스( SQL Server 데이터베이스)를 사용하려면 토폴로지 작성기를 사용하여 토폴로지에 데이터베이스를 추가한 다음 토폴로지를 다시 게시합니다. 모든 사용자가 Exchange 2013에 있고 해당 사서함이 원본 위치 유지 상태인 경우에는 토폴로지를 업데이트할 필요가 없으며, 보관된 데이터를 Exchange 2013에 저장하기 위해 Microsoft Exchange 통합을 사용하도록 설정하기만 하면 됩니다.

보관을 구현할 때는 보관을 구성하여 보관되는 항목을 지정합니다. 기본적으로는 아무런 항목도 보관되지 않습니다. Lync Server 2013 제어판을 사용하여 보관을 구성하고 관리합니다. 내부 통신이나 외부 통신 또는 둘 다에 대해 보관을 구현할 수 있습니다. 전체 조직에 대한 보관 설정을 구성할 수 있으며, 원하는 경우 특정 사이트/풀/사용자 및 사용자 그룹에 대해 보관 설정을 구성할 수도 있습니다. 조직에 적합한 옵션을 확인하는 방법에 대한 자세한 내용은 계획 설명서에서 [Lync Server 2013에서 보관에 대한 요구 사항 정의](lync-server-2013-defining-your-requirements-for-archiving.md)를 참고하세요. 보관 정책 및 구성이 구현되는 방법과 보관할 수 있거나 보관할 수 없는 정보의 종류에 대한 자세한 내용은 계획 설명서, 배포 설명서 또는 작업 설명서에서 [Lync Server 2013의 보관 작동 방식](lync-server-2013-how-archiving-works.md)을 참고하세요.

