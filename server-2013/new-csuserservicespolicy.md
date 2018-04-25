---
title: New-CsUserServicesPolicy
TOCTitle: New-CsUserServicesPolicy
ms:assetid: 8d7b7f79-f72e-4057-a0d1-188a87af5023
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/JJ205072(v=OCS.15)
ms:contentKeyID: 49304334
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# New-CsUserServicesPolicy

 

_**마지막으로 수정된 항목:** 2015-03-09_

새 사용자 서비스 정책을 만듭니다. 사용자 서비스 정책은 사용자의 연락처가 Lync Server 2013에 저장되는지 아니면 통합 연락처 저장소에 저장되는지를 결정합니다. 사용자는 통합 연락처 저장소를 통해 Lync 2013, Microsoft Outlook 및/또는 Microsoft Outlook Web Access를 사용하여 액세스할 수 있는 단일 연락처 집합을 유지 관리할 수 있습니다. 이 cmdlet은 Lync Server 2013에서 도입되었습니다.

## 구문

    New-CsUserServicesPolicy -Identity <XdsIdentity> [-Confirm [<SwitchParameter>]] [-Force <SwitchParameter>] [-InMemory <SwitchParameter>] [-Tenant <Guid>] [-UcsAllowed <$true | $false>] [-WhatIf [<SwitchParameter>]]

## 예제

## 예제 1

예제 1에 표시된 명령은 Redmond 사이트에 대해 새 사용자 서비스 정책을 만듭니다. UcsAllowed 매개 변수가 False($False)로 설정되었으므로 이 정책을 통해 관리되는 사용자의 연락처는 통합 연락처 저장소로 이동되지 않습니다.

    New-CsUserServicesPolicy -Identity "site:Redmond" -UcsAllowed $False

## 자세한 정보

Lync Server 2013에서 도입된 통합 연락처 저장소를 통해 관리자는 Lync Server가 아닌 Microsoft Exchange Server 2013에서 사용자 연락처를 저장할 수 있습니다. 그러면 사용자가 Lync 2013에서는 물론 Microsoft Outlook과 Outlook Web Access에서도 같은 연락처 집합에 액세스할 수 있습니다. 계속 Lync Server 2013에서 연락처를 저장할 수도 있는데, 이 경우 사용자는 서로 다른 두 연락처 집합(Outlook 및 Outlook Web Access에서 사용할 연락처 집합과 Lync 2013에서 사용할 연락처 집합)을 유지 관리해야 합니다.

통합 연락처 저장소를 활용하려면 우선 통합 연락처 저장소를 사용할 수 있도록 설정하는 사용자 서비스 정책을 사용자에게 할당해야 합니다. 전역, 사이트 또는 사용자별 범위에서 구성할 수 있는 사용자 서비스 정책은 하나의 속성, 즉 UcsAllowed만 포함합니다. 이 속성을 True로 설정하는 경우 기타 모든 전제 조건이 충족되었다고 가정할 때 다음 번에 사용자가 Lync Server 2013에 로그온하면 사용자의 연락처가 통합 연락처 저장소로 자동 마이그레이션됩니다.

이 속성을 False로 설정하면 이와 같은 자동 마이그레이션이 수행되지 않습니다. 그러나 UcsAllowed만 설정한다고 해서 사용자 연락처가 통합 연락처 저장소에서 Lync Server로 다시 이동되지는 않습니다. 이러한 이동을 수행하려면 먼저 통합 연락처 저장소 사용을 허용하지 않는 사용자 서비스 정책을 사용자에게 할당해야 합니다. 그 후에는 **Invoke-UcsRollback** cmdlet을 사용하여 연락처를 통합 연락처 저장소에서 Lync Server로 다시 "수동으로" 마이그레이션해야 합니다.

사용자가 직접 만든 사용자 지정 RBAC(역할 기반 액세스 제어) 역할을 포함하여 이 cmdlet이 할당된 모든 RBAC 역할의 목록을 반환하려면 Windows PowerShell 명령줄 인터페이스 프롬프트에서 다음 명령을 실행합니다.

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "New-CsUserServicesPolicy"}

**Lync Server 제어판:** **New-CsUserServicesPolicy** cmdlet에 의해 수행되는 기능은 Lync Server 제어판에서는 사용할 수 없습니다.

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
<td><p>만들 정책의 고유 식별자입니다. 사이트 범위에서 정책을 만들려면 다음과 같은 구문을 사용합니다.</p>
<p>-Identity &quot;site:Redmond&quot;</p>
<p>서비스 범위에서 정책을 생성하려면 -Identity &quot;UserServer:atl-cs-001.litwareinc.com&quot;과 같은 구문을 사용합니다.</p>
<p>사용자 서비스 정책을 호스트할 수 있는 서비스는 사용자 서버 서비스뿐입니다.</p>
<p>사용자별 범위에서 정책을 만들 수도 있습니다. 사용자별 정책을 만들려면 다음과 같은 구문을 사용합니다.</p>
<p>-Identity &quot;RedmondUserServicesPolicy&quot;</p></td>
</tr>
<tr class="even">
<td><p><em>Confirm</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>명령을 실행하기 전에 확인 메시지를 표시합니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>Force</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>명령을 실행할 때 발생할 수 있는 심각하지 않은 오류 메시지를 표시하지 않습니다.</p></td>
</tr>
<tr class="even">
<td><p><em>InMemory</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>개체를 실제로 영구 변경 사항으로 커밋하지 않고 개체 참조를 만듭니다. 이 매개 변수와 함께 호출된 이 cmdlet의 결과를 변수로 할당하면 개체 참조의 속성을 변경한 후 이 cmdlet과 일치하는 Set- cmdlet을 호출하여 해당 변경 사항을 커밋할 수 있습니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>Tenant</em></p></td>
<td><p>선택</p></td>
<td><p>System.Guid</p></td>
<td><p>새 사용자 서비스 정책이 만들어지는 비즈니스용 Skype Online 테넌트 계정의 GUID(Globally unique identifier)입니다. 예를 들면 다음과 같습니다.</p>
<p>-Tenant &quot;38aad667-af54-4397-aaa7-e94c79ec2308&quot;</p>
<p>다음 명령을 실행하여 각 테넌트에 대해 테넌트 ID를 반환할 수 있습니다.</p>
<p>Get-CsTenant | Select-Object DisplayName, TenantID</p></td>
</tr>
<tr class="even">
<td><p><em>UcsAllowed</em></p></td>
<td><p>선택</p></td>
<td><p>System.Boolean</p></td>
<td><p>기본값인 True로 설정하면 정책이 적용되는 사용자가 통합 연락처 저장소로 자동 마이그레이션됩니다(사용자가 Microsoft Exchange Server 2013에서 계정을 소유하고 있으며 Lync 2013을 사용하여 로그온한다고 가정함). False로 설정하면 사용자를 통합 연락처 저장소에서 제거할 수 있지만 이 경우 <strong>Invoke-CsUcsRollback</strong> cmdlet을 통해 사용자를 &quot;수동으로&quot; 제거해야 합니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>WhatIf</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>명령을 실제로 실행하지 않고도 명령이 실행될 경우 발생할 수 있는 현상을 설명합니다.</p></td>
</tr>
</tbody>
</table>


## 입력 형식

없음. **New-CsUserServicesPolicy** cmdlet은 파이프라인된 입력을 허용하지 않습니다.

## 반환 형식

**New-CsUserServicesPolicy** cmdlet은 Microsoft.Rtc.Management.WritableConfig.Policy.UserServices.UserServicesPolicy 개체의 새 인스턴스를 만듭니다.

## 참고 항목

#### 기타 리소스

[Get-CsUserServicesPolicy](get-csuserservicespolicy.md)  
[Grant-CsUserServicesPolicy](grant-csuserservicespolicy.md)  
[Remove-CsUserServicesPolicy](remove-csuserservicespolicy.md)  
[Set-CsUserServicesPolicy](set-csuserservicespolicy.md)

