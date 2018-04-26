---
title: Move-CsExUmContact
TOCTitle: Move-CsExUmContact
ms:assetid: 35ed6bdc-95ea-4bf8-84ce-c4256dc2c4e5
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg425842(v=OCS.15)
ms:contentKeyID: 49303284
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Move-CsExUmContact

 

_**마지막으로 수정된 항목:** 2015-03-09_

하나 이상의 Exchange 통합 메시징(UM) 대화 상대를 새 등록자 풀로 이동합니다. 이 cmdlet은 Lync Server 2010에서 도입되었습니다.

## 구문

    Move-CsExUmContact -Identity <UserIdParameter> -Target <Fqdn> [-Confirm [<SwitchParameter>]] [-DomainController <Fqdn>] [-Force <SwitchParameter>] [-IgnoreBackendStoreException <SwitchParameter>] [-PassThru <SwitchParameter>] [-ProxyPool <Fqdn>] [-WhatIf [<SwitchParameter>]]

## 예제

## 예제 1

예제 1에서는 SIP 주소가 exum1@fabrikam.com인 Exchange UM 대화 상대 개체를 FQDN이 atl-cs-001.litwareinc.com인 등록자 풀로 이동합니다. 이 명령을 실행하면 Confirm 매개 변수를 포함하지 않은 경우도 확인 메시지가 표시됩니다. 이 메시지는 Force 매개 변수를 포함한 경우에도 나타납니다.

    Move-CsExUmContact -Identity "sip:exum1@fabrikam.com" -Target atl-cs-001.litwareinc.com

## 예제 2

이 예제에서는 자동 전화 교환인 모든 Exchange UM 대화 상대 개체를 FQDN이 atl-cs-001.litwareinc.com인 등록자 풀로 이동합니다. 먼저 **Get-CsExUmContact** cmdlet을 호출하여 정의된 모든 Exchange UM 대화 상대를 검색합니다. 이 대화 상대 컬렉션은 컬렉션에서 AutoAttendant 속성 값이 True($True), 즉 대화 상대가 자동 전화 교환인 모든 대화 상대를 찾는 **Where-Object** cmdlet에 파이프됩니다.

그런 다음 AutoAttendant가 True인 대화 상대 컬렉션은 이러한 대화 상대를 Target 매개 변수에 지정된 등록자 풀로 이동하는 **Move-CsExUmContact** cmdlet에 파이프됩니다.

예제 1와 마찬가지로 이 명령을 실행하면 확인 메시지가 나타납니다.

    Get-CsExUmContact | Where-Object {$_.AutoAttendant -eq $True} | Move-CsExUmContact -Target atl-cs-001.litwareinc.com

## 자세한 정보

Lync Server는 Exchange UM과 함께 작동하여 자동 전화 교환 및 구독자 액세스와 같은 여러 가지 음성 관련 기능을 제공합니다. **Move-CsExUmContact** cmdlet을 사용하면 기존 Exchange UM 대화 상대 개체를 새 등록자 풀로 이동할 수 있습니다.

Exchange UM 대화 상대 개체를 이동하면 해당 개체의 OtherIpPhone 속성 값을 기반으로 AutoAttendant 및 IsSubscriberAccess 속성이 적절하게 설정됩니다.

이 cmdlet을 실행할 수 있는 사용자: 기본적으로 RTCUniversalUserAdmins 그룹의 구성원은 **Move-CsExUmContact** cmdlet을 로컬로 실행할 수 있습니다. 사용자가 직접 만든 사용자 지정 RBAC(역할 기반 액세스 제어) 역할을 포함하여 이 cmdlet이 할당된 모든 RBAC 역할의 목록을 반환하려면 Windows PowerShell 프롬프트에서 다음 명령을 실행합니다.

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Move-CsExUmContact"}

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
<td><p>이동할 연락처 개체의 고유한 식별자입니다. 연락처 ID는 네 가지 형식 중 하나를 사용하여 지정할 수 있는데, 이러한 형식은 1) 연락처의 SIP 주소, 2) 연락처의 UPN(사용자 계정 이름), 3) 도메인\로그온 형태인 연락처의 도메인 이름 및 로그온 이름(예: litwareinc\exum1) 및 4) 연락처의 Active Directory 표시 이름(예: Team Auto Attendant)입니다.</p></td>
</tr>
<tr class="even">
<td><p><em>Target</em></p></td>
<td><p>필수</p></td>
<td><p>Microsoft.Rtc.Management.Deploy.Fqdn</p></td>
<td><p>대화 상대를 이동할 등록자 풀의 FQDN(정규화된 도메인 이름)입니다.</p></td>
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
<td><p>지정된 도메인 컨트롤러에 연결하는 데 사용됩니다. 특정 도메인 컨트롤러에 연결하려면 DomainController 매개 변수 뒤에 컴퓨터 이름(예: atl-mcs-001) 또는 FQDN(예: atl-mcs-001.litwareinc.com)을 포함합니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>Force</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>변경하기 전에 표시되는 확인 메시지를 표시하지 않습니다.</p></td>
</tr>
<tr class="even">
<td><p><em>IgnoreBackendStoreException</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>이 매개 변수가 있으면 백 엔드 데이터베이스에서 발생했을 수 있는 모든 오류를 무시하고 오류가 발생했더라도 연락처 이동을 시도하도록 컴퓨터에 명령합니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>PassThru</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>이동할 대화 상대 계정을 나타내는 대화 상대 개체를 파이프라인을 통해 전달하는 데 사용됩니다. 기본적으로 <strong>Move-CsExUmContact</strong> cmdlet은 파이프라인을 통해 개체를 전달하지 않습니다.</p></td>
</tr>
<tr class="even">
<td><p><em>ProxyPool</em></p></td>
<td><p>선택</p></td>
<td><p>Microsoft.Rtc.Management.Deploy.Fqdn</p></td>
<td><p>이 매개 변수는 Lync Server의 호스트된 인스턴스에만 사용됩니다. Lync Server의 온-프레미스 구현에 사용하면 안 됩니다.</p></td>
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

문자열. 이동할 Exchange UM 개체의 ID를 나타내는 파이프라인된 문자열 값을 허용합니다.

## 반환 형식

PassThru 매개 변수와 함께 호출한 경우 Microsoft.Rtc.Management.ADConnect.Schema.OCSADExUmContact 유형의 개체를 반환합니다.

## 참고 항목

#### 기타 리소스

[New-CsExUmContact](new-csexumcontact.md)  
[Remove-CsExUmContact](remove-csexumcontact.md)  
[Set-CsExUmContact](set-csexumcontact.md)  
[Get-CsExUmContact](get-csexumcontact.md)

