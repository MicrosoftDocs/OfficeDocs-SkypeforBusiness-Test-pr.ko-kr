---
title: 'Lync Server 2013: 역할 기반 액세스 제어 계획'
TOCTitle: RBAC(역할 기반 액세스 제어) 계획
ms:assetid: 41204ba3-ce5b-41a8-a6c3-b444468fa328
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg425917(v=OCS.15)
ms:contentKeyID: 49303431
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Lync Server 2013의 역할 기반 액세스 제어 계획

 

_**마지막으로 수정된 항목:** 2015-03-09_

높은 보안 표준을 유지하면서 관리 작업을 위임할 수 있도록 Lync Server 2013은 RBAC(역할 기반 액세스 제어)를 제공합니다. RBAC를 사용하면 사용자를 관리 역할에 지정하여 관리 권한을 부여할 수 있습니다. Lync Server 2013에는 다양한 기본 제공 관리 역할이 포함되며, 사용자가 새로운 역할을 만들고 각 역할에 대해 사용자 지정 cmdlet 목록을 지정할 수도 있습니다. 또한 미리 정의된 RBAC 역할 및 사용자 지정 RBAC 역할 모두의 허용된 작업에 cmdlet 스크립트를 추가할 수도 있습니다.

## 향상된 서버 보안 및 중앙 집중화

RBAC에서는 액세스 및 권한 부여가 정확히 사용자의 Lync Server 역할을 기반으로 적용됩니다. 따라서 "최소 권한"의 보안 원칙을 적용하고 관리자 및 사용자에게 해당 작업을 수행하는 데 필요한 권한만 부여할 수 있습니다.


> [!IMPORTANT]
> RBAC 제한은 Lync Server 제어판 또는 Lync Server 관리 셸을 사용하여 원격으로 작업하는 관리자에게만 적용됩니다. Lync Server를 실행하는 서버에서 작업하는 사용자는 RBAC의 제한을 받지 않습니다. 따라서 Lync Server의 실제 보안이 RBAC 제한을 유지하는 데 중요합니다.



## 역할 및 범위

RBAC에서 *역할* 은 특정 유형의 관리자 또는 기술자에게 유용하도록 디자인된 cmdlet 목록을 사용하도록 설정됩니다. *범위* 는 역할에 정의된 cmdlet이 작업을 수행할 수 있는 개체 집합입니다. 이 범위의 영향을 받는 개체는 사용자 계정(조직 구성 단위별로 그룹화) 또는 서버(사이트별로 그룹화)일 수 있습니다.

다음 표에서는 Lync Server에서 미리 정의된 역할을 보여주고 각 작업이 수행할 수 있는 작업 유형에 대한 일반적인 개요를 제공합니다. 4번째 열에는 각 Lync Server 역할에 대해 비슷한 Microsoft Exchange Server 역할(있는 경우)을 보여줍니다.

### 미리 정의된 관리 역할

<table>
<colgroup>
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
</colgroup>
<thead>
<tr class="header">
<th>역할</th>
<th>허용되는 작업</th>
<th>기본 Active Directory 그룹</th>
<th>해당 Exchange 역할</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>CsAdministrator</p></td>
<td><p>모든 관리 작업을 수행하고 역할 만들기, 역할에 사용자 지정 등의 모든 설정을 수정할 수 있습니다. 새 사이트, 풀 및 서비스를 추가하여 배포를 확장할 수 있습니다.</p></td>
<td><p>CSAdministrator</p></td>
<td><p>조직 관리</p></td>
</tr>
<tr class="even">
<td><p>CsUserAdministrator</p></td>
<td><p>사용자가 Lync Server를 사용하거나 사용하지 못하도록 설정하고, 사용자를 이동하고, 사용자에게 기존 정책을 지정할 수 있습니다. 정책을 수정할 수는 없습니다.</p></td>
<td><p>CSUserAdministrator</p></td>
<td><p>메일 받는 사람</p></td>
</tr>
<tr class="odd">
<td><p>CsVoiceAdministrator</p></td>
<td><p>음성 관련 설정 및 정책을 만들고 구성하고 관리할 수 있습니다.</p></td>
<td><p>CSVoiceAdministrator</p></td>
<td><p>해당 없음</p></td>
</tr>
<tr class="even">
<td><p>CsServerAdministrator</p></td>
<td><p>서버 및 서비스를 관리 및 모니터링하고 관련 문제를 해결할 수 있습니다. 서버에 대한 새 연결을 방지하고, 서비스를 시작하거나 중지하고, 소프트웨어 업데이트를 적용할 수 있습니다. 전역 구성에 영향을 주는 변경 작업은 수행할 수 없습니다.</p></td>
<td><p>CSServerAdministrator</p></td>
<td><p>서버 관리</p></td>
</tr>
<tr class="odd">
<td><p>CsViewOnlyAdministrator</p></td>
<td><p>사용자 및 서버 정보를 포함하여 배포를 보고 배포 상태를 모니터링할 수 있습니다.</p></td>
<td><p>CSViewOnlyAdministrator</p></td>
<td><p>보기 전용 조직 관리</p></td>
</tr>
<tr class="even">
<td><p>CsHelpDesk</p></td>
<td><p>사용자의 속성 및 정책을 포함하여 배포를 볼 수 있으며, 특정 문제 해결 작업을 실행할 수 있습니다. 사용자 속성 또는 정책, 서버 구성 또는 서비스를 변경할 수는 없습니다.</p></td>
<td><p>CSHelpDesk</p></td>
<td><p>지원 센터</p></td>
</tr>
<tr class="odd">
<td><p>CsArchivingAdministrator</p></td>
<td><p>보관 구성 및 정책을 수정할 수 있습니다.</p></td>
<td><p>CSArchivingAdministrator</p></td>
<td><p>보유 관리, 법적 보유</p></td>
</tr>
<tr class="even">
<td><p>CsResponseGroupAdministrator</p></td>
<td><p>사이트 내에서 응답 그룹 응용 프로그램 구성을 관리할 수 있습니다.</p></td>
<td><p>CSResponseGroupAdministrator</p></td>
<td><p>해당 없음</p></td>
</tr>
<tr class="odd">
<td><p>CsLocationAdministrator</p></td>
<td><p>E9-1-1(Enhanced 9-1-1) 위치 및 네트워크 식별자를 만들고 서로 연결하는 등 E9-1-1 관리에 대한 최하위 수준의 권한을 가집니다. 이 역할은 항상 전역 범위로 지정됩니다.</p></td>
<td><p>CSLocationAdministrator</p></td>
<td><p>해당 없음</p></td>
</tr>
<tr class="even">
<td><p>CsResponseGroupManager</p></td>
<td><p>특정 응답 그룹을 관리할 수 있습니다.</p></td>
<td><p>CSResponseGroupManager</p></td>
<td><p>해당 없음</p></td>
</tr>
<tr class="odd">
<td><p>CsPersistentChatAdministrator</p></td>
<td><p>영구 채팅 기능 및 특정 영구 채팅방을 관리할 수 있습니다.</p></td>
<td><p>CSPersistentChatAdministrator</p></td>
<td><p>해당 없음</p></td>
</tr>
<tr class="even">
<td><p>CsAdministrator</p></td>
<td><p>모든 관리 작업을 수행하고 역할 만들기, 역할에 사용자 지정 등의 모든 설정을 수정할 수 있습니다. 새 사이트, 풀 및 서비스를 추가하여 배포를 확장할 수 있습니다.</p></td>
<td><p>CSAdministrator</p></td>
<td><p>조직 관리</p></td>
</tr>
<tr class="odd">
<td><p>CsUserAdministrator</p></td>
<td><p>사용자가 Lync Server를 사용하거나 사용하지 못하도록 설정하고, 사용자를 이동하고, 사용자에게 기존 정책을 지정할 수 있습니다. 정책을 수정할 수는 없습니다.</p></td>
<td><p>CSUserAdministrator</p></td>
<td><p>메일 받는 사람</p></td>
</tr>
<tr class="even">
<td><p>CsVoiceAdministrator</p></td>
<td><p>음성 관련 설정 및 정책을 만들고 구성하고 관리할 수 있습니다.</p></td>
<td><p>CSVoiceAdministrator</p></td>
<td><p>해당 없음</p></td>
</tr>
<tr class="odd">
<td><p>CsServerAdministrator</p></td>
<td><p>서버 및 서비스를 관리 및 모니터링하고 관련 문제를 해결할 수 있습니다. 서버에 대한 새 연결을 방지하고, 서비스를 시작하거나 중지하고, 소프트웨어 업데이트를 적용할 수 있습니다. 전역 구성에 영향을 주는 변경 작업은 수행할 수 없습니다.</p></td>
<td><p>CSServerAdministrator</p></td>
<td><p>서버 관리</p></td>
</tr>
<tr class="even">
<td><p>CsViewOnlyAdministrator</p></td>
<td><p>사용자 및 서버 정보를 포함하여 배포를 보고 배포 상태를 모니터링할 수 있습니다.</p></td>
<td><p>CSViewOnlyAdministrator</p></td>
<td><p>보기 전용 조직 관리</p></td>
</tr>
<tr class="odd">
<td><p>CsHelpDesk</p></td>
<td><p>사용자의 속성 및 정책을 포함하여 배포를 볼 수 있으며, 특정 문제 해결 작업을 실행할 수 있습니다. 사용자 속성 또는 정책, 서버 구성 또는 서비스를 변경할 수는 없습니다.</p></td>
<td><p>CSHelpDesk</p></td>
<td><p>지원 센터</p></td>
</tr>
<tr class="even">
<td><p>CsArchivingAdministrator</p></td>
<td><p>보관 구성 및 정책을 수정할 수 있습니다.</p></td>
<td><p>CSArchivingAdministrator</p></td>
<td><p>보유 관리, 법적 보유</p></td>
</tr>
<tr class="odd">
<td><p>CsResponseGroupAdministrator</p></td>
<td><p>사이트 내에서 응답 그룹 응용 프로그램 구성을 관리할 수 있습니다.</p></td>
<td><p>CSResponseGroupAdministrator</p></td>
<td><p>해당 없음</p></td>
</tr>
<tr class="even">
<td><p>CsLocationAdministrator</p></td>
<td><p>E9-1-1(Enhanced 9-1-1) 위치 및 네트워크 식별자를 만들고 서로 연결하는 등 E9-1-1 관리에 대한 최하위 수준의 권한을 가집니다. 이 역할은 항상 전역 범위로 지정됩니다.</p></td>
<td><p>CSLocationAdministrator</p></td>
<td><p>해당 없음</p></td>
</tr>
<tr class="odd">
<td><p>CsResponseGroupManager</p></td>
<td><p>특정 응답 그룹을 관리할 수 있습니다.</p></td>
<td><p>CSResponseGroupManager</p></td>
<td><p>해당 없음</p></td>
</tr>
<tr class="even">
<td><p>CsPersistentChatAdministrator</p></td>
<td><p>영구 채팅 기능 및 특정 영구 채팅방을 관리할 수 있습니다.</p></td>
<td><p>CSPersistentChatAdministrator</p></td>
<td><p>해당 없음</p></td>
</tr>
</tbody>
</table>


Lync Server에서 제공되는 모든 미리 정의된 역할은 전역 범위를 갖습니다. 최소 권한 원칙을 따르기 위해서는 제한된 서버 또는 사용자 집합만 관리하려는 경우 전체 범위로 설정된 역할에 사용자를 지정해서는 안됩니다. 이를 위해서는 기존 역할을 기반으로 하지만 보다 제한된 범위를 갖는 역할을 만들 수 있습니다.

## 범위가 지정된 역할 만들기

제한된 범위를 갖는 역할(범위가 지정된 역할)을 만들 때는 역할의 기반이 되는 기존 역할 및 역할에 지정할 Active Directory 그룹과 함께 범위를 지정합니다. 지정하는 Active Directory 그룹은 이미 만들어져 있어야 합니다. 다음 cmdlet은 미리 정의된 관리 역할 중 하나의 권한을 갖지만 범위가 제한된 역할을 만드는 예를 보여줍니다. 여기에서는 `Site01 Server Administrators`라는 새로운 역할을 만듭니다. 이 역할은 미리 정의된 CsServerAdministrator 역할의 기능을 갖지만 Site01 사이트에 있는 서버로만 범위가 제한됩니다. 이 cmdlet이 작동하기 위해서는 Site01 사이트가 이미 정의되어 있어야 하고 `Site01 Server Administrators`라는 유니버설 보안 그룹이 이미 있어야 합니다.

    New-CsAdminRole -Identity "Site01 Server Administrators" -Template CsServerAdministrator -ConfigScopes "site:Site01"

이 cmdlet을 실행하면 `Site01 Server Administrators` 그룹의 구성원인 모든 사용자에게 Site01의 서버에 대한 서버 관리자 권한이 부여됩니다. 또한 이 유니버설 보안 그룹에 나중에 추가된 사용자에게도 이 역할의 권한이 부여됩니다. 역할 자체와 해당 역할이 지정된 유니버설 보안 그룹 둘 다 `Site01 Server Administrators`라고 합니다.

다음 예에서는 서버 범위 대신 사용자 범위를 제한합니다. 이 예에서는 Sales 조직 단위의 사용자 계정을 관리할 `Sales Users Administrator` 역할을 만듭니다. 이 cmdlet이 작동하려면 SalesUsersAdministrator 유니버설 보안 그룹이 이미 만들어져 있어야 합니다.

    New-CsAdminRole -Identity "Sales Users Administrator " -Template CsUserAdministrator -UserScopes "OU:OU=Sales, OU=Lync Tenants, DC=Domain, DC=com"

## 새 역할 만들기

미리 정의된 역할 중에서 찾을 수 없는 cmdlet 집합에 액세스하거나 스크립트 또는 모듈 집합에 액세스하는 역할을 만들려는 경우에도 미리 정의된 역할 중 하나를 템플릿으로 사용해서 작업을 시작합니다. 역할이 실행할 수 있어야 하는 스크립트 및 모듈은 다음 위치에 저장되어 있어야 합니다.

  - Lync 모듈 경로(기본값: C:\\Program Files\\Common Files\\Microsoft Lync Server 2013\\Modules\\Lync)

  - 사용자 스크립트 경로(기본값: C:\\Program Files\\Common Files\\Microsoft Lync Server 2013\\AdminScripts)

새 역할을 만들려면 **New-CsAdminRole** cmdlet을 사용합니다. **New-CsAdminRole** 을 실행하기 전에 먼저 이 역할과 연결할 기본 유니버설 보안 그룹을 만들어야 합니다.

다음 cmdlet은 새 역할을 만드는 예를 보여줍니다. 이러한 cmdlet은 `MyHelpDeskScriptRole`이라는 새로운 역할 유형을 만듭니다. 이 새 역할은 미리 정의된 CsHelpDesk 역할의 기능을 포함하며 추가적으로 “testscript”라는 스크립트의 기능을 실행할 수 있습니다.

    New-CsAdminRole -Identity "MyHelpDeskScriptRole" -Template CsHelpDesk -ScriptModules @{Add="testScript.ps1"}

이 cmdlet이 작동할 수 있으려면 먼저 MyHelpDeskScriptRole이라는 유니버설 보안 그룹을 만들어야 합니다.

이 cmdlet이 실행된 후에는 이 역할에 사용자를 직접 지정하거나(전역 범주를 갖는 경우), 이 문서의 앞 부분에 있는 범위가 지정된 역할 만들기에서 설명한 대로 이 역할을 기반으로 범위가 지정된 역할을 만들 수 있습니다.

## 사용자에게 역할 지정

각 Lync Server 역할은 기본 Active Directory 유니버설 보안 그룹과 연결됩니다. 기본 그룹에 추가하는 모든 사용자는 해당 역할의 기능을 갖습니다.

이전 섹션의 예에서는 새 역할을 만들고 새 역할에 기존 유니버설 보안 그룹을 지정했습니다. 한 명 이상의 사용자에게 기존 역할을 지정하려면 해당 역할과 연결된 그룹에 사용자를 추가합니다. 이러한 그룹에는 개별 사용자 및 유니버설 보안 그룹을 모두 추가할 수 있습니다.

예를 들어 **CsAdministrator** 역할은 Active Directory의 **CS Administrators** 유니버설 보안 그룹에 자동으로 부여됩니다. 이 유니버설 보안 그룹은 Lync Server를 배포할 때 Active Directory에 만들어집니다. 사용자 또는 그룹에 이 권한을 부여하려면 해당 사용자 또는 그룹을 **CS Administrators** 그룹에 추가하기만 하면 됩니다.

각 역할에 해당하는 기본 Active Directory 그룹에 사용자를 추가하여 사용자에게 여러 RBAC 역할을 부여할 수 있습니다.

역할을 만든 경우 기본 Active Directory 그룹에 나중에 추가되는 사용자에게도 해당 역할의 권한이 부여됩니다.

## 역할의 기능 수정

역할이 실행할 수 있는 cmdlet 및 스크립트 목록을 수정할 수 있습니다. 사용자 지정 역할이 실행할 수 있는 cmdlet 및 스크립트를 모두 수정할 수 있지만 미리 정의된 역할의 경우 스크립트만 수정할 수 있습니다. 입력하는 각 cmdlet은 cmdlet 또는 스크립트를 추가, 제거 또는 대체할 수 있습니다.

역할을 수정하려면 **Set-CsAdminRole** cmdlet을 사용합니다. 다음 cmdlet은 역할에서 스크립트를 하나 제거합니다.

    Set-CsAdminRole -Identity "MyHelpDeskScriptRole" -ScriptModules @{Remove="testScript.ps1"}

## RBAC 계획

Lync Server 배포에 대해 어떠한 종류든 관리 권한을 부여하려는 각 사용자에 대해 해당 사용자가 수행할 작업을 정확하게 고려해서, 해당 작업에 필요한 최소 권한 및 범위를 갖는 역할에 사용자를 지정하세요. 필요에 따라 **Set-CsAdminRole** cmdlet을 사용해서 이 사용자의 작업에 필요한 cmdlet만 포함된 새 역할을 만들 수 있습니다.

CsAdministrator 역할을 가진 사용자는 CsAdministrator를 기반으로 하는 역할을 포함하여 모든 유형의 역할을 만들고 각 역할에 사용자를 지정할 수 있습니다. 따라서 신뢰할 수 있는 소수의 사용자에게만 CsAdministrator 역할을 지정하는 것이 좋습니다.

