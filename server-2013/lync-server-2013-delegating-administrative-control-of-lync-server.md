---
title: 'Lync Server 2013: Lync Server 관리 권한 위임'
TOCTitle: Lync Server 2013 관리 권한 위임
ms:assetid: 0f378eff-8ef4-4c60-9fd2-67d7ee259ef8
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg520951(v=OCS.15)
ms:contentKeyID: 49302817
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Lync Server 2013 관리 권한 위임

 

_**마지막으로 수정된 항목:** 2013-02-22_

Lync Server 2013에서는 새로운 RBAC(역할 기반 액세스 제어) 기능을 사용하여 관리 작업을 사용자에게 위임합니다. Lync Server를 설치하면 여러 RBAC 역할이 자동으로 만들어집니다. 이러한 역할은 Active Directory 도메인 서비스의 유니버설 보안 그룹에 해당합니다. 예를 들어 RBAC 역할 CsHelpDesk는 Active Directory 도메인 서비스의 Users 컨테이너에 있는 CsHelpDesk 그룹에 해당합니다. 또한 각 RBAC 역할은 Lync ServerWindows PowerShell cmdlet 집합과 연결됩니다. 이러한 cmdlet은 지정된 RBAC 역할이 할당된 사용자가 수행할 수 있는 작업을 나타냅니다. 예를 들어 CsHelpDesk 역할에는 Lock-CsClientPin 및 UnlockCsClientPin cmdlet이 할당됩니다. 즉, CsHelpDesk 역할이 할당된 사용자는 사용자 PIN 번호를 잠그고 잠금을 해제할 수 있습니다. 그러나 New-CsVoicePolicy cmdlet은 CsHelpDesk 역할에 할당되지 않습니다. 즉, CsHelpDesk 역할이 할당된 사용자가 새 음성 정책을 만들 수는 없습니다.

## RBAC 역할에 대한 정보 보기

Lync Server 관리 셸 내에서 다음 명령을 실행하여 RBAC 역할에 대한 기본 정보를 검색할 수 있습니다.

    Get-CsAdminRole

RBAC 역할(예: CsVoiceAdministrator)의 ID는 Active Directory 도메인 서비스의 Users 컨테이너에 있는 보안 그룹에 직접 매핑됩니다.

역할에 할당된 cmdlet 목록을 보려면 다음과 같은 명령을 사용합니다.

    Get-CsAdminRole -Identity "CsHelpDesk" | Select-Object -ExpandProperty Cmdlets

## 사용자에게 RBAC 역할 할당

사용자에게 RBAC 역할을 할당하려면 해당하는 Active Directory 보안 그룹에 해당 사용자를 추가해야 합니다. 예를 들어 사용자에게 CsLocationAdministrator 역할을 할당하려면 CsLocationAdministrator 그룹에 해당 사용자를 추가해야 합니다. 이렇게 하려면 다음 절차를 수행합니다.

**보안 그룹에 사용자를 할당하려면**

1.  Active Directory 그룹 구성원 수정 권한이 있는 계정을 사용하여 Active Directory 사용자 및 컴퓨터가 설치된 컴퓨터에 로그온합니다.

2.  **시작** 을 클릭하고 **모든 프로그램** 과 **관리 도구** 를 차례로 클릭한 다음 **Active Directory 사용자 및 컴퓨터** 를 클릭합니다.

3.  Active Directory 사용자 및 컴퓨터에서 도메인 이름을 확장하고 **Users** 컨테이너를 클릭합니다.

4.  **CsLocationAdministrator** 보안 그룹을 마우스 오른쪽 단추로 클릭하고 **속성** 을 클릭합니다.

5.  **속성** 대화 상자의 **구성원** 탭에서 **추가** 를 클릭합니다.

6.  **사용자, 컴퓨터, 연락처 또는 그룹 선택** 대화 상자에서 그룹에 추가할 사용자의 이름이나 표시 이름(예: **Ken Myer** )을 **선택할 개체 이름을 입력하십시오** 상자에 입력하고 **확인** 을 클릭합니다.

7.  **속성** 대화 상자에서 **확인** 을 클릭합니다.

RBAC 역할이 할당되었는지 확인하려면 [Get-CsAdminRoleAssignment](get-csadminroleassignment.md) cmdlet을 사용하고, 사용자의 SamAccountName(Active Directory 로그온 이름)을 cmdlet에 전달합니다. 예를 들어 Lync Server 관리 셸 내에서 아래 명령을 실행합니다.

    Get-CsAdminRoleAssignment  -Identity "kenmyer"

