---
title: ID, 범위, 테넌트
TOCTitle: ID, 범위, 테넌트
ms:assetid: 7cfa194a-2d01-4370-9b48-ee13ff597fa5
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Dn362819(v=OCS.15)
ms:contentKeyID: 56270262
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# ID, 범위, 테넌트

 

_**마지막으로 수정된 항목:** 2015-06-22_

비즈니스용 Skype Online을 관리하는 데 사용되는 대부분의 Windows PowerShell cmdlet은 관리하려는 항목을 매우 구체적으로 지정해야 합니다. 예를 들어 [Set-CsUserAcp](set-csuseracp.md) cmdlet을 실행할 경우 어떤 사용자를 관리하려는 것인지 확실하게 나타내야 합니다. cmdlet에 어떤 사용자 계정을 관리할 것인지 알리지 않는다면 **Set-CsUserAcp** cmdlet에서 어떤 사용자의 오디오 회의 정보를 수정해야 하는지 알 수 없습니다. 이러한 이유로 **Set-CsUserAcp** cmdlet을 실행할 때마다 Identity 매개 변수를 포함하고 그 뒤에 수정할 사용자 계정의 ID를 넣어야 합니다.

    Set-CsUserAcp -Identity "Ken Myer" -TollNumber "14255551298" -ParticipantPassCode 13761 -Domain "fabrikam.com" -Name "Fabrikam ACP"

*ID*라는 용어가 항상 사용자 계정의 ID를 의미한다면 크게 혼동할 일이 없을 것입니다. 사람(사용자, 대화 상대 등)을 대상으로 하는 경우 ID는 각각의 개인 사용자를 나타냅니다. 하지만 사용자 계정 외의 항목에게도 ID가 있습니다. 비즈니스용 Skype Online 서비스의 구성 요소(정책, 구성 설정 등)를 대상으로 할 때에는 ID의 의미가 약간 다를 수 있습니다. 예를 들어 다음 명령을 살펴보겠습니다.

    Get-CsMeetingConfiguration -Identity "global"

이 경우 Identity "global"은 모임 구설 설정의 범위를 말합니다. *범위*는 비즈니스용 Skype Online(및 Lync Server)에서 관리 영역을 지정하기 위해 사용하는 용어입니다. 기본적으로 정책과 설정에는 항상 전역 범위가 있습니다. 비즈니스용 Skype Online 계정을 처음 설정할 때 기본적으로 전역 정책 및 설정 모음(전역 모임 구성 설정, 전역 외부 액세스 정책, 전역 다이얼 플랜 등)이 제공됩니다.

이러한 전역 정책 및 설정은 모든 사용자와 모든 구성 요소를 어떤 식으로든 항상 관리할 수 있도록 하기 위해 Microsoft Lync Server 2010에 도입되었습니다. Microsoft Office Communicator 2007 R2에서는 약간 달랐습니다. 시스템에 액세스하는 방법에 따라 일반적으로 사용자 계정에 그룹 정책을 적용할 수 없었기 때문에 잠재적으로 거의 관리되지 않은 상태가 지속될 수도 있었습니다. 반대로 Lync Server 및 비즈니스용 Skype Online에서는 더 이상 관리되지 않은 상태로 유지되지 않습니다. 다른 항목 대신 전역 정책 및 설정이 항상 적용되기 때문입니다.

여기서 "다른 항목 대신"이란 어떤 의미일까요? 비즈니스용 Skype Online의 경우 *태그 범위* 또는 관리 영역에서 정책을 만들 수 있습니다. 태그 범위(*사용자별 범위*라고도 함)에서 만든 정책은 전역 범위에서 만든 정책보다 우선 순위가 높습니다. 다시 말해 전역 정책보다 사용자별 정책이 항상 우선합니다. 예를 들어 두 개의 외부 사용자 액세스 정책이 있다고 가정해 보겠습니다. 전역 정책은 사용자가 Windows Live 같은 공용 메신저 공급자에 계정이 있는 사용자와 통신하지 못하도록 합니다. AllowPublicIMCommunication이라는 사용자별 정책은 공용 메신저 공급자와 통신을 허용합니다.

Ken Myer과 Pilar Ackerman이라는 두 명의 사용자가 있으며 Ken Myer에게는 사용자별 정책이 할당되었고, Pilar Ackerman에게는 사용자별 정책이 할당되지 않아 전역 외부 액세스 정책에 의해 관리됩니다. 다음 표는 어떤 사용자가 공용 메신저 공급자와 통신할 수 있는지 보여 줍니다.


<table>
<colgroup>
<col style="width: 33%" />
<col style="width: 33%" />
<col style="width: 33%" />
</colgroup>
<thead>
<tr class="header">
<th>정책 설정</th>
<th>Ken Myer</th>
<th>Pilar Ackerman</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>공용 메신저 공급자를 위한 전역 정책 설정</p></td>
<td><p>아니요</p></td>
<td><p>아니요</p></td>
</tr>
<tr class="even">
<td><p>공용 메신저 공급자를 위한 사용자별 정책 설정</p></td>
<td><p>예</p></td>
<td><p>아니요</p></td>
</tr>
<tr class="odd">
<td><p>사용자가 공용 메신저 공급자와 통신할 수 있음</p></td>
<td><p>예</p></td>
<td><p>아니요</p></td>
</tr>
</tbody>
</table>


보다시피 Ken Myer는 공용 메신저 공급자와 통신할 수 있습니다. 이 사용자에게 할당된 사용자별 정책이 전역 정책의 설정보다 우선하기 때문입니다. Pilar Ackerman은 공용 메신저 공급자와 통신할 수 없습니다. 이 사용자의 경우 전역 정책에 의해 관리되며 전역 정책이 이러한 통신을 금지하기 때문입니다.

사용자별 정책은 Office 365 지원에서 만들어야 합니다. 정책이 만들어지면 적절한 **Grant-Cs** cmdlet(예: [Grant-CsExternalAccessPolicy](grant-csexternalaccesspolicy.md))을 사용하여 사용자에게 할당할 수 있습니다. 사용자별 정책의 경우 정책 ID가 항상 태그 **접두사**로 시작되기 때문에 쉽게 구별할 수 있습니다. 예를 들면 다음과 같습니다.

    Identity : tag:AllowPublicIMCommunication


> [!NOTE]
> 태그 <STRONG>접두사</STRONG>는 Lync Server 2010의 초기 개발 시기에 생겨난 것으로, 당시에는 사용자별 정책을 <EM>태그 정책</EM>이라고 불렀으며 태그 <STRONG>접두사</STRONG>를 통해 구분했습니다. 이 정책은 이제 좀 더 정확한 명칭인 <EM>사용자별 정책</EM>이라고 불리며, 태그 범위는 보다 정확하게 <EM>사용자별 범위</EM>라고 불립니다. 그러나 기술적인 이유로 태그 <STRONG>접두사</STRONG>는 변경되지 않았습니다.



비즈니스용 Skype Online 및 Windows PowerShell에서 작업할 때 사용되는 또 다른 주요 용어로는 *테넌트*가 있습니다. 비즈니스용 Skype Online 계정을 설정하면 새 배포에 다음과 같은 GUID(Globally Unique Identifier)에 해당하는 테넌트 ID 번호가 할당됩니다.

    bf19b7db-6960-41e5-a139-2aa373474354

cmdlet을 실행할 때마다 테넌트 ID를 입력해야 하는 비즈니스용 Skype Online cmdlet은 많지 않습니다. 테넌트가 하나밖에 없어 이 테넌트에 로그온하는 경우에도 테넌트 ID를 입력해야 합니다. 그러나 테넌트 ID를 외울 필요는 없습니다. 다음 Windows PowerShell 명령을 실행하여 언제든지 테넌트 ID를 가져올 수 있기 때문입니다.

    Get-CsTenant | Select-Object TenantId

물론 전역 범위와 사용자별 범위(또는 태그 범위) 사이의 차이를 아는 것만으로는 부족합니다. 이러한 범위를 사용할 수 있는지 여부와 언제 사용할 수 있는지도 알고 있어야 합니다. Identity와 Tenant 매개 변수의 경우도 마찬가지입니다. 다음 항목은 다양한 비즈니스용 Skype Online cmdlet에서 Indentity, Scope, Tenant 매개 변수가 어떻게 사용되는지 설명합니다.

  - [전역 범위만 사용하는 cmdlet](cmdlets-in-skype-for-business-online-that-use-only-the-global-scope.md)

  - [전역 범위 및 태그 범위를 사용하는 cmdlet](cmdlets-in-skype-for-business-online-that-use-the-global-scope-and-the-tag-scope.md)

  - [사용자 ID를 사용하는 cmdlet](cmdlets-in-skype-for-business-online-that-use-a-user-identity.md)

  - [사용자 ID 및 태그 범위를 사용하는 cmdlet](cmdlets-in-skype-for-business-online-that-use-a-user-identity-and-the-tag-scope.md)

  - [Tenant 매개 변수를 사용하는 cmdlet](cmdlets-in-skype-for-business-online-that-use-the-tenant-parameter.md)

  - [회의 공급자 ID를 사용하는 cmdlet](cmdlets-in-skype-for-business-online-that-use-a-conferencing-provider-identity.md)

  - [범위 또는 ID를 사용하지 않는 cmdlet](cmdlets-in-skype-for-business-online-that-do-not-use-a-scope-or-an-identity.md)

