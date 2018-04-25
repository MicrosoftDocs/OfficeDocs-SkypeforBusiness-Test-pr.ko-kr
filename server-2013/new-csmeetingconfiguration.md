---
title: New-CsMeetingConfiguration
TOCTitle: New-CsMeetingConfiguration
ms:assetid: 0043c9e7-83c6-4f07-88d2-7018c65c1654
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg398065(v=OCS.15)
ms:contentKeyID: 49302604
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# New-CsMeetingConfiguration

 

_**마지막으로 수정된 항목:** 2015-03-09_

사이트 또는 서비스 범위에서 새 전화 회의 구성 컬렉션을 만듭니다. 모임 구성 설정은 사용자가 만들 수 있는 모임(또는 "회의"라고도 함) 유형을 지정할 뿐만 아니라 익명 사용자 및 전화 접속 회의 사용자가 이러한 모임에 참가하는 방법(또는 심지어 참가 여부)까지도 제어하도록 지원합니다. 이러한 설정은 예약된 모임에만 영향을 주며, Lync에서 모임 시작 옵션을 클릭하여 만든 임시 모임에는 영향을 주지 않습니다. 이 cmdlet은 Lync Server 2010에서 도입되었습니다.

## 구문

    New-CsMeetingConfiguration -Identity <XdsIdentity> [-AdmitAnonymousUsersByDefault <$true | $false>] [-AssignedConferenceTypeByDefault <$true | $false>] [-Confirm [<SwitchParameter>]] [-CustomFooterText <String>] [-DesignateAsPresenter <None | Company | Everyone>] [-EnableAssignedConferenceType <$true | $false>] [-Force <SwitchParameter>] [-HelpURL <String>] [-InMemory <SwitchParameter>] [-LegalURL <String>] [-LogoURL <String>] [-PstnCallersBypassLobby <$true | $false>] [-RequireRoomSystemsAuthorization <$true | $false>] [-Tenant <Guid>] [-WhatIf [<SwitchParameter>]]

## 예제

## 예제 1

예제 1에서는 Redmond 사이트에 대한 새 모임 구성 설정 컬렉션을 만듭니다(-Identity site:Redmond). ID를 지정할 뿐 아니라 이 명령에는 EnableAssignedConferenceType, AssignedConferenceTypeByDefault 및 AdmitAnonymousUsersByDefault라는 세 개의 선택적 매개 변수도 포함됩니다. 세 경우에서 모두, 이러한 매개 변수는 False로 설정됩니다. 따라서 공개 모임 유형이 해제되고, 기본 모임 유형이 공개 모임으로 설정되지 않으며, 익명 사용자의 모임 참석이 기본적으로 허용되지 않습니다.

ID가 site:Redmond인 모임 구성 설정 컬렉션이 이미 있는 경우 이 명령은 실패합니다. 이것은 지정된 사이트에 모임 구성 설정 컬렉션을 한 개만 적용할 수 있기 때문입니다.

    New-CsMeetingConfiguration -Identity site:Redmond -EnableAssignedConferenceType $False -AssignedConferenceTypeByDefault $False -AdmitAnonymousUsersByDefault $False

## 예제 2

예제 2에서는 Redmond 사이트에 대한 새 모임 구성 설정 컬렉션을 만드는 대체 방법을 보여 줍니다. 이 경우 설정이 초기에 메모리에만 만들어지고 나중에 사이트에 적용됩니다. 이 작업을 수행하기 위해 이 예제의 첫 번째 명령은 **New-CsMeetingConfiguration** cmdlet을 사용하여 Redmond 사이트에 대한 새 모임 설정을 만듭니다. InMemory 매개 변수를 명령 끝에 추가하여 이러한 설정이 메모리에서만 만들어지고 Redmond 사이트에 즉시 적용되지 않도록 합니다. 설정이 메모리에만 있기 때문에 설정을 변수에 저장해야 합니다. 이 예제에서는 $x라는 변수에 저장합니다.

두 번째, 세 번째 및 네 번째 명령은 가상 모임 설정이 만들어진 후 이러한 설정(EnableAssignedConferenceType, AssignedConferenceTypeByDefault 및 AdmitAnonymousUsersByDefault)의 다양한 속성을 수정하는 데 사용됩니다. 첫 번째 명령에서 **Set-CsMeetingConfiguration** cmdlet 및 Instance 매개 변수는 실제로 Redmond 사이트에 가상 설정을 적용하는 데 사용됩니다. 이 최종 단계는 매우 중요합니다. **Set-CsMeetingConfiguration** cmdlet을 호출하지 않으면 새 모임 구성 설정이 Redmond 사이트에 적용되지 않습니다. 대신, Windows PowerShell 세션을 종료하거나 변수 $x를 삭제하는 즉시 가상 설정이 사라집니다.

    $x = New-CsMeetingConfiguration -Identity site:Redmond -InMemory
    $x.EnableAssignedConferenceType = $False 
    $x.AssignedConferenceTypeByDefault = $False 
    $x.AdmitAnonymousUsersByDefault = $False
    Set-CsMeetingConfiguration -Instance $x

## 자세한 정보

모임("전화 회의"라고도 함)은 Lync Server의 필수적인 부분입니다. **CsMeetingConfiguration** cmdlet을 통해 관리자는 사용자가 만들 수 있는 모임 유형을 제어할 뿐만 아니라 모임에서 익명 사용자 및 전화 접속 회의 사용자를 처리하는 방법도 결정할 수 있습니다. 예를 들어 PSTN(공중 전화망)을 통해 전화 접속한 사용자가 모임에 자동으로 입장하도록 모임을 구성할 수 있습니다. 또는 전화 접속 사용자가 모임에 자동으로 입장하지는 않지만 대신 모임 대기실로 경로 지정되도록 모임을 구성할 수 있습니다. 이러한 전화 접속 사용자는 발표자가 모임에 입장하도록 허용할 때까지 대기실에서 대기 상태로 유지됩니다.

앞에서 설명한 것처럼 이러한 설정은 예약된 모임에만 영향을 주며 Microsoft Lync에서 모임 시작을 클릭하여 만든 임시 모임에는 영향을 주지 않습니다. 모임 시작을 클릭하여 모임을 만들 때는 참가자 액세스 권한이 자동으로 모든 사용자에게 제공되며, 익명 사용자가 대기실에서 기다릴 필요 없이 모임에 참가할 수 있습니다. 이 동작은 CsMeetingConfiguration cmdlet을 사용하여 모임 설정을 구성한 방법에 관계없이 수행됩니다.

**New-CsMeetingConfiguration** cmdlet을 사용하면 사이트 또는 서비스 범위(User Services서비스에만 해당)에서 새 모임 구성 컬렉션을 만들 수 있습니다. 전역 범위에서는 모임 설정을 만들 수 없습니다. 이것은 전역 모임 설정 컬렉션이 이미 있기 때문입니다.

각 사이트 또는 서비스에는 모임 구성 설정 컬렉션이 최대 한 개만 포함될 수 있습니다. Redmond 사이트에 대한 새 설정을 만들려고 하는데 Redmond 사이트에 모임 구성 설정 컬렉션이 이미 있으면 명령이 실패합니다.

이 cmdlet을 실행할 수 있는 사용자: 기본적으로 RTCUniversalServerAdmins 그룹의 구성원은 **New-CsMeetingConfiguration** cmdlet을 로컬로 실행할 수 있습니다. 사용자가 직접 만든 사용자 지정 RBAC(역할 기반 액세스 제어) 역할을 포함하여 이 cmdlet이 할당된 모든 RBAC 역할의 목록을 반환하려면 Windows PowerShell 프롬프트에서 다음 명령을 실행합니다.

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "New-CsMeetingConfiguration"}

## 매개 변수


<table>
<colgroup>
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
</colgroup>
<thead>
<tr class="header">
<th>매개 변수</th>
<th>필수</th>
<th>유형</th>
<th>설명</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><em>Identity</em></p></td>
<td><p>필수</p></td>
<td><p>Microsoft.Rtc.Management.Xds.XdsIdentity</p></td>
<td><p>새 모임 구성 설정 컬렉션의 고유 식별자입니다. 모임 구성 설정은 사이트 또는 서비스 범위에서만 만들 수 있습니다. 사이트 범위에서 새 설정을 만들려면 -Identity &quot;site:Redmond&quot;와 유사한 구문을 사용합니다. 서비스 범위에서 새 설정을 만들려면 -Identity &quot;service:UserServer:atl-cs-001.litwareinc.com&quot;과 유사한 구문을 사용합니다.</p>
<p>지정한 사이트 또는 서비스에 모임 구성 설정 컬렉션이 이미 있으면 <strong>New-CsMeetingConfiguration</strong> cmdlet 호출이 실패합니다.</p></td>
</tr>
<tr class="even">
<td><p><em>AdmitAnonymousUsersByDefault</em></p></td>
<td><p>선택</p></td>
<td><p>System.Boolean</p></td>
<td><p>모임에서 기본적으로 익명 사용자(인증되지 않은 사용자)의 참석을 허용할지 여부를 결정합니다. 새 모임에서 기본적으로 익명 사용자의 참석을 허용하려면 이 값을 True로 설정합니다. 새 모임에서 기본적으로 익명 사용자의 참석을 허용하지 않으려면 이 값을 False로 설정합니다. 기본값은 True입니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>AssignedConferenceTypeByDefault</em></p></td>
<td><p>선택</p></td>
<td><p>System.Boolean</p></td>
<td><p>새 모임이 기본적으로 공개 모임으로 구성되는지 여부를 결정합니다. 기본적으로 공개 모임을 사용하려면 이 값을 True로 설정하고 기본적으로 비공개 모임을 사용하려면 False로 설정합니다. 기본값은 True입니다.</p></td>
</tr>
<tr class="even">
<td><p><em>Confirm</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>명령을 실행하기 전에 확인 메시지를 표시합니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>CustomFooterText</em></p></td>
<td><p>선택</p></td>
<td><p>System.String</p></td>
<td><p>사용자 지정 모임 초대에 사용할 텍스트입니다.</p></td>
</tr>
<tr class="even">
<td><p><em>DesignateAsPresenter</em></p></td>
<td><p>선택</p></td>
<td><p>Microsoft.Rtc.Management.WritableConfig.Settings.UserServices.DesignateAsPresenter</p></td>
<td><p>모임 주최자 외에 모임에 참가할 경우 자동으로 발표자로 지정되는 사용자를 나타냅니다. 사용할 수 있는 값은 None, Company 및 Everyone입니다. 기본적으로 DesignateAsPresenter는 Company로 설정됩니다. 따라서 조직의 모든 구성원이 모임에 참가하는 순간 발표자 권한을 가지게 됩니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>EnableAssignedConferenceType</em></p></td>
<td><p>선택</p></td>
<td><p>System.Boolean</p></td>
<td><p>사용자가 공개 모임을 예약하도록 허용되는지 여부를 나타냅니다. 공개 모임에서는 전화 회의 ID와 모임 링크가 모임을 가질 때마다 일관된 상태로 유지되고, 비공개 모임에서는 전화 회의 ID와 모임 링크가 모임마다 변경됩니다.</p></td>
</tr>
<tr class="even">
<td><p><em>Force</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>명령을 실행할 때 발생할 수 있는 심각하지 않은 오류 메시지를 표시하지 않습니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>HelpURL</em></p></td>
<td><p>선택</p></td>
<td><p>System.String</p></td>
<td><p>사용자가 모임 참가를 위한 지원을 받을 수 있는 웹 사이트의 URL입니다.</p></td>
</tr>
<tr class="even">
<td><p><em>InMemory</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>개체를 실제로 영구 변경 사항으로 커밋하지 않고 개체 참조를 만듭니다. 이 매개 변수와 함께 호출된 이 cmdlet의 결과를 변수로 할당하면 개체 참조의 속성을 변경한 후 이 cmdlet과 일치하는 Set- cmdlet을 호출하여 해당 변경 사항을 커밋할 수 있습니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>LegalURL</em></p></td>
<td><p>선택</p></td>
<td><p>System.String</p></td>
<td><p>법적 정보 및 모임 고지 사항이 나와 있는 웹 사이트의 URL입니다.</p></td>
</tr>
<tr class="even">
<td><p><em>LogoURL</em></p></td>
<td><p>선택</p></td>
<td><p>System.String</p></td>
<td><p>사용자 지정 모임 초대에 사용할 이미지의 URL입니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>PstnCallersBypassLobby</em></p></td>
<td><p>선택</p></td>
<td><p>System.Boolean</p></td>
<td><p>PSTN(공중 전화망) 전화 회선에서 전화를 거는 사용자의 모임 참가를 자동으로 허용할지 여부를 나타냅니다. True로 설정하면 PSTN 호출자의 모임 참가가 자동으로 허용됩니다. False로 설정하면 PSTN 호출자는 우선 전화 회의 대기실로 경로 지정됩니다. 여기서 전화 회의 발표자가 모임 액세스 권한을 부여할 때까지 대기해야 합니다. 기본값은 True입니다.</p></td>
</tr>
<tr class="even">
<td><p><em>RequireRoomSystemsAuthorization</em></p></td>
<td><p>선택</p></td>
<td><p>System.Boolean</p></td>
<td><p>True($True)로 설정하면 Lync 채팅방 시스템을 사용하여 모임에 참가하려는 모든 사용자는 인증을 해야 합니다. 기본값은 False($False)입니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>Tenant</em></p></td>
<td><p>선택</p></td>
<td><p>System.Guid</p></td>
<td><p>새 모임 구성 설정이 만들어지는 비즈니스용 Skype Online 테넌트 계정의 GUID(Globally Unique Identification)입니다. 예를 들면 다음과 같습니다.</p>
<p>-Tenant &quot;38aad667-af54-4397-aaa7-e94c79ec2308&quot;</p>
<p>다음 명령을 실행하여 각 테넌트에 대해 테넌트 ID를 반환할 수 있습니다.</p>
<p>Get-CsTenant | Select-Object DisplayName, TenantID</p></td>
</tr>
<tr class="even">
<td><p><em>WhatIf</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>명령을 실제로 실행하지 않고도 명령이 실행될 경우 발생할 수 있는 현상을 설명합니다.</p></td>
</tr>
</tbody>
</table>


## 입력 형식

없음. **New-CsMeetingConfiguration** cmdlet은 파이프라인된 데이터를 허용하지 않습니다.

## 반환 형식

**New-CsMeetingConfiguration** cmdlet은 Microsoft.Rtc.Management.WritableConfig.Settings.UserServices.MeetingConfiguration 개체의 새 인스턴스를 만듭니다.

## 참고 항목

#### 기타 리소스

[Get-CsMeetingConfiguration](get-csmeetingconfiguration.md)  
[Remove-CsMeetingConfiguration](remove-csmeetingconfiguration.md)  
[Set-CsMeetingConfiguration](set-csmeetingconfiguration.md)

