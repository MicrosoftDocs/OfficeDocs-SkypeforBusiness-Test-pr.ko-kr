---
title: Lync Server 2013용 RBAC(역할 기반 액세스 제어)
TOCTitle: Lync Server 2013용 RBAC(역할 기반 액세스 제어)
ms:assetid: d01fba36-eb7e-4de9-9bba-5102ae157820
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Dn481134(v=OCS.15)
ms:contentKeyID: 59679297
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Lync Server 2013용 RBAC(역할 기반 액세스 제어)

 

_**마지막으로 수정된 항목:** 2013-11-07_

Microsoft Lync Server 2013에는 RBAC(역할 기반 액세스 제어) 그룹이 포함되어 있어 사용자가 보안을 위한 높은 기준을 유지하면서 관리 작업을 위임할 수 있습니다. 이 그룹은 포리스트 준비 중에 만들어집니다. 포리스트 준비에 대한 자세한 내용은 [Lync Server 2013용 Active Directory 도메인 서비스](lync-server-2013-active-directory-domain-services-for-lync-server.md)를 참고하세요. 포리스트 준비를 통해 만든 특정 그룹에 대한 자세한 내용은 배포 설명서의 [Lync Server 2013에서 포리스트 준비로 인한 변경](lync-server-2013-changes-made-by-forest-preparation.md)을 참고하세요.

RBAC가 있으면 다수의 일반적인 관리 작업을 아우르는 미리 정의된 역할 11개를 포함하여 미리 정의된 관리 역할에 사용자를 지정하는 방식으로 관리 권한이 부여됩니다. 각 역할은 해당 역할의 사용자가 실행할 수 있는 Lync Server 관리 셸 cmdlet의 특정 목록과 연결됩니다. RBAC를 사용하여 사용자에게 작업에 필요한 관리 능력만 부여되는 "최소 권한"의 원칙을 따를 수 있습니다. 자세한 내용은 준비 설명서의 [Lync Server 2013의 역할 기반 액세스 제어 계획](lync-server-2013-planning-for-role-based-access-control.md)을 참고하세요.

