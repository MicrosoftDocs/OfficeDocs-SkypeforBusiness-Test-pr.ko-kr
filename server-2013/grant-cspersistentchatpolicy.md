---
title: Grant-CsPersistentChatPolicy
TOCTitle: Grant-CsPersistentChatPolicy
ms:assetid: 58889550-167a-4267-9f3d-0f244e898599
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/JJ204907(v=OCS.15)
ms:contentKeyID: 49303706
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Grant-CsPersistentChatPolicy

 

_**마지막으로 수정된 항목:** 2015-03-09_

사용자에게 사용자별 영구적 채팅 정책을 반환합니다. 영구적 채팅 정책은 사용자의 영구 채팅방 액세스가 허용되는지 여부를 결정합니다. 이 cmdlet은 Lync Server 2013에서 도입되었습니다.

## 구문

    Grant-CsPersistentChatPolicy -Identity <UserIdParameter> -PolicyName <String> [-Confirm [<SwitchParameter>]] [-DomainController <Fqdn>] [-PassThru <SwitchParameter>] [-WhatIf [<SwitchParameter>]]

## 예제

## 예제 1

예제 1에 표시된 명령은 Active Directory 표시 이름이 "Ken Myer"인 사용자에게 사용자별 정책 RedmondUsersPersistentChatPolicy를 할당합니다.

    Grant-CsPersistentChatPolicy -Identity "Ken Myer" -PolicyName "RedmondUsersPersistentChatPolicy"

## 예제 2

예제 2에서는 IT 부서에 근무하는 모든 사용자에게 사용자별 정책 RedmondUsersPersistentChatPolicy를 할당합니다. 이 작업을 수행하기 위해 먼저 LdapFilter 속성과 함께 **Get-CsUser** cmdlet을 호출합니다. 필터 값 "Department=IT"는 반환되는 데이터를 IT 부서에 근무하는 사용자로 제한합니다. 그런 다음 해당 사용자 컬렉션은 컬렉션의 각 사용자에게 RedmondUsersPersistentChatPolicy 정책을 할당하는 **Grant-CsPersistentChatPolicy** cmdlet에 파이프됩니다.

    Get-CsUser -LdapFilter "Department=IT" | Grant-CsPersistentChatPolicy -PolicyName "RedmondUsersPersistentChatPolicy"

## 예제 3

예제 3에서는 현재 사용자별 영구적 채팅 정책이 할당되어 있지 않은 모든 사용자에게 사용자별 영구적 채팅 정책 RedmondUsersPersistentChatPolicy를 할당합니다. 이 작업을 수행하기 위해 먼저 **Get-CsUser** cmdlet 및 Filter 매개 변수를 사용합니다. 필터 값 {PersistentChatPolicy –eq $Null}는 반환되는 데이터를 PersistentChatPolicy 속성이 현재 null($Null)인 사용자 계정으로 제한합니다. 그런 다음 해당 사용자 컬렉션은 컬렉션의 각 사용자에게 RedmondUsersPersistentChatPolicy 정책을 할당하는 **Grant-CsPersistentChatPolicy** cmdlet에 파이프됩니다.

    Get-CsUser -Filter {PersistentChatPolicy -eq $Null} | Grant-CsPersistentChatPolicy -PolicyName "RedmondUsersPersistentChatPolicy"

## 예제 4

예제 4에 표시된 명령은 현재 사용자별 영구적 채팅 정책 RedmondUsersPersistentChatPolicy가 할당되어 있는 사용자로부터 해당 정책 할당을 취소합니다. 이 작업을 수행하기 위해 이 명령은 먼저 **Get-CsUser** cmdlet 및 Filter 매개 변수를 사용하여 현재 RedmondUsersPersistentChatPolicy 정책이 할당되어 있는 사용자의 컬렉션을 반환합니다. 필터 값 {PersistentChatPolicy –eq "RedmondUsersPersistentChatPolicy"}는 반환되는 항목을 PersistentChatPolicy 속성이 RedmondUsersPersistentChatPolicy와 같은 사용자 계정으로 제한합니다. 그런 다음 해당 컬렉션은 PersistentChatPolicy 속성을 null 값($Null)으로 설정하여 사용자별 정책 할당을 취소하는 **Grant-CsPersistentChatPolicy** cmdlet에 파이프됩니다.

사용자별 정책의 할당을 취소하고 나면 사용자의 영구 채팅 기능이 해당 영구 채팅 사이트 정책(있는 경우)에 의해 관리되며, 사이트 정책이 없으면 전역 영구적 채팅 정책에 의해 관리됩니다.

    Get-CsUser -Filter {PersistentChatPolicy -eq "RedmondUsersPersistentChatPolicy"} | Grant-CsPersistentChatPolicy -PolicyName $Null

## 자세한 정보

Microsoft Lync Server 2010에서 사용되었던 그룹 채팅 서비스 대신 제공되는 영구 채팅 서비스를 사용하는 조직에서는 인터넷 토론 포럼과 비슷한 메시징 및 공동 작업 기능을 사용할 수 있습니다. 사용자는 실시간으로 메시지를 교환하는 동시에 언제든지 대화를 다시 방문하여 다시 시작할 수 있습니다. 특정 주제에 대해 대화를 할 수 있으며, 해당 대화를 모든 사용자가 확인할 수 있도록 하거나 선택한 사용자 집합만 확인하도록 할 수 있습니다. 마찬가지로 개별 채팅방도 누구나 메시지를 게시할 수 있도록 구성하거나 지정된 발표자만 메시지를 게시하도록 구성할 수 있습니다.

기본적으로 사용자에게는 영구 채팅 서비스 액세스 권한이 부여되지 않습니다. 사용자의 서비스 사용을 허용하는 영구적 채팅 정책을 통해 사용자가 관리되는 경우에만 이 액세스 권한을 부여할 수 있습니다. Lync 2013를 설치하면 모든 사용자가 전역 영구적 채팅 정책을 통해 관리되며, 이 정책에서는 영구 채팅이 사용할 수 없도록 설정됩니다. 모든 사용자에게 서비스 액세스 권한을 제공하려면 전역 정책의 EnablePersistentChat 속성을 True로 설정하면 됩니다. 사이트 또는 사용자별 범위에서 추가 정책을 만들어 일부 사용자에게는 영구 채팅 액세스 권한을 제공하고 나머지 사용자에 대해서는 액세스를 거부할 수도 있습니다.

사용자가 직접 만든 사용자 지정 RBAC(역할 기반 액세스 제어) 역할을 포함하여 이 cmdlet이 할당된 모든 RBAC 역할의 목록을 반환하려면 Windows PowerShell 명령줄 인터페이스 프롬프트에서 다음 명령을 실행합니다.

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Grant-CsPersistentChatPolicy"}

**Lync Server 제어판:** Lync Server 제어판에서 사용자에게 영구적 채팅 정책을 할당하려면 해당하는 사용자 계정을 두 번 클릭하고, **Lync Server 사용자 편집** 대화 상자의 **영구적 채팅 정책** 드롭다운 목록에서 정책을 선택한 후에 **커밋** 을 클릭합니다.

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
<td><p><em>Identity</em></p></td>
<td><p>필수</p></td>
<td><p>Microsoft.Rtc.Management.AD.UserIdParameter</p></td>
<td><p>사용자별 영구적 채팅 정책을 할당할 사용자 계정의 ID를 나타냅니다. 사용자 ID는 보통 네 가지 형식 중 하나를 사용하여 지정할 수 있는데, 이러한 형식은 1) 사용자의 SIP 주소, 2) 사용자의 UPN(사용자 계정 이름), 3) 도메인\로그온 형태인 사용자의 도메인 이름 및 로그온 이름(예: litwareinc\kenmyer) 및 4) 사용자의 Active Directory 표시 이름(예: Ken Myer)입니다. 사용자의 Active Directory 고유 이름을 사용하여 사용자 ID를 지정할 수도 있습니다.</p>
<p>또한 표시 이름을 사용자 ID로 사용할 경우 별표(*) 와일드카드 문자를 사용할 수 있습니다. 예를 들어 &quot;* Smith&quot;라는 ID는 표시 이름이 &quot; Smith&quot; 문자열 값으로 끝나는 모든 사용자를 반환합니다.</p></td>
</tr>
<tr class="even">
<td><p><em>PolicyName</em></p></td>
<td><p>필수</p></td>
<td><p>System.String</p></td>
<td><p>할당할 정책의 &quot;이름&quot;입니다. PolicyName은 간단히 말해 정책 ID에서 정책 범위(&quot;tag:&quot; 접두사)를 뺀 것입니다. 예를 들어 ID가 tag:Redmond인 정책의 PolicyName은 Redmond와 같고, ID가 tag:RedmondUsersPersistentChatPolicy인 정책의 PolicyName은 RedmondUsersPersistentChatPolicy와 같습니다. 사용자에게 이전에 할당한 사용자별 정책을 할당 취소하려면 PolicyName을 null 값($Null)으로 설정합니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>Confirm</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>명령을 실행하기 전에 확인 메시지를 표시합니다.</p></td>
</tr>
<tr class="even">
<td><p><em>DomainController</em></p></td>
<td><p>선택</p></td>
<td><p>Microsoft.Rtc.Management.Deploy.Fqdn</p></td>
<td><p>새 정책을 할당할 때 연결할 도메인 컨트롤러의 정규화된 도메인 이름을 지정하는 데 사용됩니다. 이 매개 변수를 지정하지 않으면 <strong>Grant-CsPersistentChatPolicy</strong> cmdlet에서 사용 가능한 첫 번째 도메인 컨트롤러에 연결합니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>PassThru</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>정책을 할당할 사용자를 나타내는 사용자 개체를 파이프라인을 통해 전달하는 데 사용됩니다. 기본적으로 <strong>Grant-CsPersistentChatPolicy</strong> cmdlet은 파이프라인을 통해 개체를 전달하지 않습니다.</p></td>
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

문자열 값 또는 Microsoft.Rtc.Management.WritableConfig.Policy.PersistentChat.PersistentChatPolicy 개체입니다. **Grant-CsPersistentChatPolicy** cmdlet은 사용자 계정의 ID를 나타내는 파이프라인된 문자열 값 입력을 허용합니다. 또한 이 cmdlet은 사용자 개체의 파이프라인된 입력을 허용합니다.

## 반환 형식

기본적으로 **Grant-CsPersistentChatPolicy** cmdlet은 개체나 값을 반환하지 않습니다. 그러나 PassThru 매개 변수를 포함하는 경우 이 cmdlet은 Microsoft.Rtc.Management.ADConnect.Schema.OCSUserOrAppContact의 인스턴스를 반환합니다.

## 참고 항목

#### 기타 리소스

[Get-CsPersistentChatPolicy](get-cspersistentchatpolicy.md)  
[New-CsPersistentChatPolicy](new-cspersistentchatpolicy.md)  
[Remove-CsPersistentChatPolicy](remove-cspersistentchatpolicy.md)  
[Set-CsPersistentChatPolicy](set-cspersistentchatpolicy.md)

