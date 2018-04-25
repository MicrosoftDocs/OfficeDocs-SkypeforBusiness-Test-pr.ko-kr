---
title: New-CsPresenceProvider
TOCTitle: New-CsPresenceProvider
ms:assetid: 55110f49-f8d5-4287-89d3-ae069d8090d3
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/JJ204895(v=OCS.15)
ms:contentKeyID: 49303665
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# New-CsPresenceProvider

 

_**마지막으로 수정된 항목:** 2015-03-09_

조직에서 사용할 새 현재 상태 공급자의 권한을 부여합니다. 현재 상태 공급자는 사용자 서비스 구성 설정 컬렉션의 PresenceProviders 속성을 나타냅니다. 이 cmdlet은 Lync Server 2013에서 도입되었습니다.

## 구문

    New-CsPresenceProvider -Fqdn <String> -Parent <String> <COMMON PARAMETERS>

    New-CsPresenceProvider -Identity <XdsIdentity> <COMMON PARAMETERS>

    COMMON PARAMETERS: [-Confirm [<SwitchParameter>]] [-Force <SwitchParameter>] [-InMemory <SwitchParameter>] [-WhatIf [<SwitchParameter>]]

## 예제

## 예제 1

예제 1에 표시된 명령은 정규화된 도메인 이름이 "fabrikam.com"인 새 현재 상태 공급자를 만듭니다. 이 공급자는 사용자 서비스 구성 설정의 전역 컬렉션에 추가됩니다.

    New-CsPresenceProvider -Parent "global" -Fqdn "fabrikam.com"

## 예제 2

예제 2에서는 Fqdn이 "fabrikam.com"인 현재 상태 공급자를 조직의 모든 사용자 서비스 구성 컬렉션에 추가합니다. 이 작업을 수행하기 위해 먼저 **Get-CsUserServicesConfiguration** cmdlet을 사용하여 모든 사용자 서비스 설정의 컬렉션을 반환합니다. 해당 설정은 컬렉션의 각 항목을 가져온 다음 해당 컬렉션에 대해 새 현재 상태 공급자를 만드는 ForEach-Object에 파이프됩니다. 이때 "fabrikam.com"을 현재 상태 공급자 Fqdn으로, 사용자 서비스 컬렉션의 Identity를 현재 상태 공급자 Parent로 사용합니다.

    Get-CsUserServicesConfiguration | ForEach-Object {New-CsPresenceProvider -Parent $_.Identity -Fqdn "fabrikam.com"}

## 자세한 정보

**CsPresenceProvider** cmdlet은 사용자 서비스 구성 설정에 포함된 PresenceProviders 속성을 관리하는 데 사용됩니다. 이 설정의 가장 중요한 용도는 권한이 부여된 현재 상태 공급자 컬렉션을 비롯하여 현재 상태 정보를 유지 관리하는 것입니다. 해당 컬렉션은 PresenceProviders 속성에 저장됩니다. **New-CsPresenceProvider** cmdlet을 사용하면 권한이 부여된 현재 상태 공급자를 사용자 서비스 구성 설정의 컬렉션에 추가할 수 있습니다.

사용자가 직접 만든 사용자 지정 RBAC(역할 기반 액세스 제어) 역할을 포함하여 이 cmdlet이 할당된 모든 RBAC 역할의 목록을 반환하려면 Windows PowerShell 명령줄 인터페이스 프롬프트에서 다음 명령을 실행합니다.

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "New-CsPresenceProvider"}

**Lync Server 제어판:** **New-CsPresenceProvider** cmdlet에 의해 수행되는 기능은 Lync Server 제어판에서는 사용할 수 없습니다.

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
<th>형식</th>
<th>설명</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><em>Fqdn</em></p></td>
<td><p>필수</p></td>
<td><p>System.String</p></td>
<td><p>현재 상태 공급자의 정규화된 도메인 이름입니다. 예를 들면 다음과 같습니다.</p>
<p>-Fqdn &quot;fabrikam.com&quot;</p>
<p>Fqdn 매개 변수를 사용하는 경우에는 Parent 매개 변수도 사용해야 합니다. 그러나 Fqdn 매개 변수를 Identity 매개 변수와 같은 명령에서 사용할 수는 없습니다.</p>
<p>FQDN은 지정된 범위에서 고유해야 합니다.</p></td>
</tr>
<tr class="even">
<td><p><em>Identity</em></p></td>
<td><p>필수</p></td>
<td><p>Microsoft.Rtc.Management.Xds.XdsIdentity</p></td>
<td><p>새 현재 상태 공급자의 고유 식별자입니다. 현재 상태 공급자의 ID는 두 부분, 즉 service:UserServer:atl-cs-001.litwareinc.com과 같은 규칙이 적용된 범위(상위 항목)와 공급자의 정규화된 도메인 이름으로 구성됩니다. 전역 범위에서 새 공급자를 만들려면 다음과 같은 구문을 사용합니다.</p>
<p>-Identity &quot;global/fabrikam.com&quot;</p>
<p>사이트 범위에서 공급자를 만들려면 다음과 같은 구문을 사용합니다.</p>
<p>-Identity &quot;site:Redmond/fabrikam.com&quot;</p>
<p>UserServer 서비스에 한해 서비스 범위에서 공급자를 만들려면 다음과 같은 구문을 사용합니다.</p>
<p>-Parent &quot;UserServer:atl-cs-001.litwareinc.com&quot;</p>
<p>Fqdn 또는 Parent 매개 변수와 같은 명령에서 Identity 매개 변수를 사용할 수는 없습니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>Parent</em></p></td>
<td><p>필수</p></td>
<td><p>System.String</p></td>
<td><p>새 현재 상태 공급자를 만들 범위입니다. 전역 범위에서 새 현재 상태 공급자를 만들려면 다음과 같은 구문을 사용합니다.</p>
<p>-Parent &quot;global&quot;</p>
<p>사이트 범위에서 새 공급자를 만들려면 다음과 같은 구문을 사용합니다.</p>
<p>-Parent &quot;site:Redmond&quot;</p>
<p>UserServer 서비스에 한해 서비스 범위에서 공급자를 만들려면 다음과 같은 구문을 사용합니다.</p>
<p>-Parent &quot;UserServer:atl-cs-001.litwareinc.com&quot;</p>
<p>Parent 매개 변수를 사용하는 경우에는 Fqdn 매개 변수도 포함해야 합니다. 그러나 Parent 매개 변수를 Identity 매개 변수와 함께 사용할 수는 없습니다.</p></td>
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
<td><p><em>WhatIf</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>명령을 실제로 실행하지 않고도 명령이 실행될 경우 발생할 수 있는 현상을 설명합니다.</p></td>
</tr>
</tbody>
</table>


## 입력 형식

없음. **New-CsPresenceProvider** cmdlet은 파이프라인된 입력을 허용하지 않습니다.

## 반환 형식

**New-CsPresenceProvider** cmdlet은 Microsoft.Rtc.Management.WritableConfig.Settings.UserServices.PresenceProvider\#Decorated 개체의 새 인스턴스를 만듭니다.

## 참고 항목

#### 기타 리소스

[Get-CsPresenceProvider](get-cspresenceprovider.md)  
[Get-CsUserServicesConfiguration](get-csuserservicesconfiguration.md)  
[Remove-CsPresenceProvider](remove-cspresenceprovider.md)  
[Set-CsPresenceProvider](set-cspresenceprovider.md)

