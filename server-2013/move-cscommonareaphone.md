---
title: Move-CsCommonAreaPhone
TOCTitle: Move-CsCommonAreaPhone
ms:assetid: af5f832c-1be9-4495-ba1a-c10ca50d7b29
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg412837(v=OCS.15)
ms:contentKeyID: 49304727
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Move-CsCommonAreaPhone

 

_**마지막으로 수정된 항목:** 2015-04-02_

하나 이상의 공통 영역 전화를 새 등록자 풀로 이동합니다. 이 cmdlet은 Lync Server 2010에서 도입되었습니다.

## 구문

    Move-CsCommonAreaPhone -Identity <UserIdParameter> -Target <Fqdn> [-Confirm [<SwitchParameter>]] [-DomainController <Fqdn>] [-Force <SwitchParameter>] [-IgnoreBackendStoreException <SwitchParameter>] [-PassThru <SwitchParameter>] [-ProxyPool <Fqdn>] [-WhatIf [<SwitchParameter>]]

## 예제

## 예제 1

예제 1에 표시된 명령은 ID가 CN={ce84964a-c4da-4622-ad34-c54ff3ed361f},OU=Redmond,DC=Litwareinc,DC=com인 공통 영역 전화를 atl-cs-001.litwareinc.com 등록자 풀로 이동합니다.

    Move-CsCommonAreaPhone -Identity "CN={ce84964a-c4da-4622-ad34-c54ff3ed361f},OU=Redmond,DC=Litwareinc,DC=com" -Target atl-cs-001.litwareinc.com

## 예제 2

예제 2에서는 Active Directory 표시 이름이 "Building 31 Cafeteria"인 공통 영역 전화를 atl-cs-001.litwareinc.com 등록자 풀로 이동합니다. 이 작업을 수행하기 위해 먼저 매개 변수 없이 **Get-CsCommonAreaPhone** cmdlet을 호출하여 조직에서 현재 사용 중인 공통 영역 전화의 컬렉션을 반환합니다. 이 컬렉션은 DisplayName 속성이 "Building 31 Cafeteria"와 같은 전화만 선택하는 **Where-Object** cmdlet에 파이프됩니다. 그런 다음 필터링된 컬렉션은 컬렉션의 각 전화를 atl-cs-001.litwareinc.com으로 이동하는 **Move-CsCommonAreaPhone** cmdlet에 파이프됩니다.

    Get-CsCommonAreaPhone | Where-Object {$_.DisplayName -eq "Building 31 Cafeteria"} | Move-CsCommonAreaPhone -Target atl-cs-001.litwareinc.com

## 예제 3

예제 3에서는 등록자 풀 dublin-cs-001.litwareinc.com에 속해 있는 모든 공통 영역 전화를 atl-cs-001.litwareinc.com 등록자 풀로 이동합니다. 이 작업을 수행하기 위해 명령은 먼저 매개 변수 없이 **Get-CsCommonAreaPhone** cmdlet을 호출합니다. 그러면 조직에서 사용하도록 구성된 모든 공통 영역 전화의 컬렉션이 반환됩니다. 이 컬렉션은 등록자 풀이 dublin-cs-001.litwareinc.com과 같은 모든 공통 영역 전화를 선택하는 **Where-Object** cmdlet에 파이프됩니다. 그런 다음 이 컬렉션은 컬렉션의 각 전화를 새 등록자 풀 atl-cs-001.litwareinc.com으로 이동하는 **Move-CsCommonAreaPhone** cmdlet에 파이프됩니다.

    Get-CsCommonAreaPhone | Where-Object {$_.RegistrarPool -match "dublin-cs-001.litwareinc.com"} | Move-CsCommonAreaPhone -Target atl-cs-001.litwareinc.com

## 예제 4

예제 4는 예제 3에 표시된 명령의 변형입니다. 그러나 이 예제에서는 공통 영역 전화를 새 등록자 풀로 이동할 뿐만 아니라 사용자별 음성 정책을 할당합니다. 이 작업을 수행하기 위해 **Move-CsCommonAreaPhone** cmdlet을 호출할 때 PassThru 매개 변수를 포함합니다. 그러면 공통 영역 전화 개체가 파이프라인을 통해 전달됩니다. 기본적으로 **Move-CsCommonAreaPhone** cmdlet은 파이프라인을 통해 개체를 전달하지 않습니다. 전화가 이동된 후 전화 개체는 새로 이동된 각 전화에 음성 정책 AtlantaVoicePolicy를 할당하는 **Grant-CsVoicePolicy** cmdlet에 파이프됩니다.

    Get-CsCommonAreaPhone | Where-Object {$_.RegistrarPool -match "dublin-cs-001.litwareinc.com"} | Move-CsCommonAreaPhone -Target atl-cs-001.litwareinc.com -PassThru | Grant-CsVoicePolicy -PolicyName AtlantaVoicePolicy

## 자세한 정보

공통 영역 전화는 개별 사용자와 연결되지 않은 IP 전화입니다. 공통 영역 전화는 특정 사무실에 있는 것이 아니라 일반적으로 건물의 로비, 카페, 직원 라운지, 회의실 등 많은 사람이 모일 수 있는 장소에 있습니다. 따라서 관리자의 관리가 필요합니다. Lync Server를 통해 사용하는 전화는 일반적으로 개별 사용자에게 할당된 음성 정책 및 다이얼 플랜으로 유지 관리되는데, 공통 영역 전화에는 개별 사용자가 할당되지 않기 때문입니다.

이러한 문제를 해결하는 한 가지 방법은 모든 공통 영역 전화에 대해 Active Directory 연락처 개체를 만드는 방법이 있습니다. 연락처 개체는 **New-CsCommonAreaPhone** cmdlet을 사용하여 만들 수 있습니다. 이러한 연락처 개체에는 사용자 계정과 마찬가지로 정책 및 음성 계획을 할당할 수 있습니다. 따라서 공통 영역 전화가 개별 사용자와 연결되어 있지 않더라도 해당 전화에 대한 제어를 유지 관리할 수 있습니다. 예를 들어 사람들이 공통 영역 전화에서 통화를 전송하거나 대기할 수 없도록 하려면 통화 전송 및 통화 대기를 금지하는 음성 정책을 만들어 해당 정책을 공통 영역 전화에 할당하기만 하면 됩니다. 좀 더 정확하게 표현하자면 공통 영역 전화를 나타내는 연락처 개체에 할당하면 됩니다.

**Move-CsCommonAreaPhone** cmdlet을 사용하면 기존 공통 영역 전화를 새 등록자 풀로 이동할 수 있습니다.

이 cmdlet을 실행할 수 있는 사용자: 기본적으로 RTCUniversalServerAdmins 그룹의 구성원은 **Move-CsCommonAreaPhone** cmdlet을 로컬로 실행할 수 있습니다. 특정 사이트 또는 특정 Active Directory OU(조직 구성 단위)에 대해 이 cmdlet을 실행할 권한은 **Grant-CsOUPermission** cmdlet을 사용하여 할당할 수 있습니다. 사용자가 직접 만든 사용자 지정 RBAC(역할 기반 액세스 제어) 역할을 포함하여 이 cmdlet이 할당된 모든 RBAC 역할의 목록을 반환하려면 Windows PowerShell 프롬프트에서 다음 명령을 실행합니다.

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Move-CsCommonAreaPhone"}

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
<td><p>Microsoft.Rtc.Management.AD.UserIdParameter</p></td>
<td><p>공통 영역 전화의 고유 식별자입니다. 공통 영역 전화는 연결된 연락처 개체의 Active Directory 고유 이름을 사용하여 식별됩니다. 기본적으로 공통 영역 전화는 GUID(Globally Unique Identifier)를 공용 이름으로 사용합니다. 따라서 일반적으로 CN={ce84964a-c4da-4622-ad34-c54ff3ed361f},OU=Redmond,DC=Litwareinc,DC=com과 유사한 ID가 지정됩니다.</p></td>
</tr>
<tr class="even">
<td><p><em>Target</em></p></td>
<td><p>필수</p></td>
<td><p>Microsoft.Rtc.Management.Deploy.Fqdn</p></td>
<td><p>공통 영역 전화를 이동할 등록자 풀의 FQDN(정규화된 도메인 이름)입니다(예: atl-cs-001.litwareinc.com). 등록자 풀 이외에 호스팅 공급자의 FQDN도 대상이 될 수 있습니다.</p></td>
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
<td><p>공통 영역 전화를 이동하기 위해 지정된 도메인 컨트롤러에 연결하는 데 사용됩니다. 특정 도메인 컨트롤러에 연결하려면 DomainController 매개 변수 뒤에 컴퓨터 이름(예: atl-cs-001) 또는 FQDN(예: atl-cs-001.litwareinc.com)을 포함합니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>Force</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>이 매개 변수를 지정하면 관련 데이터(예: 장치에 할당된 정책)를 모두 삭제한 상태로 공통 영역 전화를 이동합니다. 그렇지 않으면 모든 관련 데이터와 함께 전화를 이동합니다.</p></td>
</tr>
<tr class="even">
<td><p><em>IgnoreBackendStoreException</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>이 매개 변수가 있으면 백 엔드 데이터베이스에서 발생했을 수 있는 모든 오류를 무시하고 오류가 발생했더라도 공통 영역 전화 이동을 시도하도록 컴퓨터에 명령합니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>PassThru</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>이동할 사용자 계정을 나타내는 사용자 개체를 파이프라인을 통해 전달하는 데 사용됩니다. 기본적으로 <strong>Move-CsCommonAreaPhone</strong> cmdlet은 파이프라인을 통해 개체를 전달하지 않습니다.</p></td>
</tr>
<tr class="even">
<td><p><em>ProxyPool</em></p></td>
<td><p>선택</p></td>
<td><p>Microsoft.Rtc.Management.Deploy.Fqdn</p></td>
<td><p>이 매개 변수는 Lync Online에만 사용됩니다. Lync Server의 온-프레미스 구현에 사용하면 안 됩니다.</p></td>
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

문자열. **Move-CsCommonAreaPhone** cmdlet은 공통 영역 전화의 ID를 나타내는 파이프라인된 문자열 값을 허용합니다.

## 반환 형식

기본적으로 **Move-CsCommonAreaPhone** cmdlet은 개체나 값을 반환하지 않습니다. 그러나 PassThru 매개 변수를 포함한 경우 이 cmdlet은 Microsoft.Rtc.Management.ADConnect.Schema.OCSADCommonAreaPhoneContact 개체의 인스턴스를 반환합니다.

## 참고 항목

#### 기타 리소스

[Get-CsCommonAreaPhone](get-cscommonareaphone.md)  
[New-CsCommonAreaPhone](new-cscommonareaphone.md)  
[Remove-CsCommonAreaPhone](remove-cscommonareaphone.md)  
[Set-CsCommonAreaPhone](set-cscommonareaphone.md)

