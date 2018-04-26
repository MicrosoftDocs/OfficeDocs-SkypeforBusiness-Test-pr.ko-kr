---
title: Set-CsExUmContact
TOCTitle: Set-CsExUmContact
ms:assetid: c0fe0fdc-6fea-4334-8645-24ffd494db07
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg412944(v=OCS.15)
ms:contentKeyID: 49304914
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Set-CsExUmContact

 

_**마지막으로 수정된 항목:** 2015-03-09_

호스트된 Exchange 통합 메시징(UM)에 대한 기존 자동 전화 교환 또는 구독자 액세스 연락처 개체를 수정합니다. 이 cmdlet은 Lync Server 2010에서 도입되었습니다.

## 구문

    Set-CsExUmContact -Identity <UserIdParameter> [-AutoAttendant <$true | $false>] [-Confirm [<SwitchParameter>]] [-Description <String>] [-DisplayNumber <String>] [-DomainController <Fqdn>] [-Enabled <$true | $false>] [-EnterpriseVoiceEnabled <$true | $false>] [-ExchangeArchivingPolicy <Uninitialized | UseLyncArchivingPolicy | NoArchiving | ArchivingToExchange>] [-PassThru <SwitchParameter>] [-SipAddress <String>] [-WhatIf [<SwitchParameter>]]

## 예제

## 예제 1

이 예제에서는 SIP 주소가 exumsa4@fabrikam.com인 Exchange UM 연락처의 AutoAttendant 속성을 True로 설정합니다. 먼저 **Get-CsExUmContact** cmdlet을 호출하여 연락처 개체를 검색합니다. 연락처의 Active Directory 표시 이름, 연락처의 사용자 계정 이름 또는 연락처의 로그온 이름을 사용할 수도 있습니다. 이 명령은 제공된 ID를 가진 하나의 연락처를 검색합니다. 이 연락처는 **Set-CsExUmContact** cmdlet에 전달되며, 여기서 해당 AutoAttendant 매개 변수를 True로 설정합니다.

    Get-CsExUmContact -Identity sip:exumsa4@fabrikam.com | Set-CsExUmContact -AutoAttendant $True

## 예제 2

이 예제는 예제 1과 동일하지만 **Get-CsExUmContact** cmdlet을 호출하고 해당 개체를 **Set-CsExUmContact** cmdlet에 파이프하여 연락처를 검색하는 대신 수정할 연락처의 ID를 **Set-CsExUmContact** cmdlet에 제공합니다. 여기서 ID 형식에 주의해야 합니다. 이 예제에서는 연락처를 만들 때 자동으로 생성된 GUID를 포함하는 연락처 개체의 전체 고유 이름을 사용합니다. 그런 다음 연락처의 AutoAttendant 매개 변수를 True로 설정합니다.

    Set-CsExUmContact -Identity "CN={1bf6208d-2847-45d0-828f-636f14da858b},OU=ExUmContacts,DC=litwareinc,DC=com" -AutoAttendant $True

## 자세한 정보

Lync Server는 Exchange UM과 함께 작동하여 자동 전화 교환 및 구독자 액세스와 같은 여러 가지의 음성 관련 기능을 제공합니다. Exchange UM이 온-프레미스가 아니라 호스트된 서비스로 제공되는 경우 자동 전화 교환 및 구독자 액세스 기능을 적용하려면 Windows PowerShell을 사용하여 연락처 개체를 만들어야 합니다. 이러한 개체는 **New-CsExUmContact** cmdlet을 호출하여 만들고 나중에 **Set-CsExUmContact** cmdlet을 사용하여 수정할 수 있습니다.

일반적으로 이 cmdlet을 사용하려면 먼저 **Get-CsExUmContact** cmdlet을 호출하여 수정할 연락처 개체의 인스턴스를 검색하는 것이 가장 편리합니다. **Get-CsExUmContact** cmdlet 명령의 출력을 **Set-CsExUmContact** cmdlet에 파이프하고 변경할 속성의 매개 변수에 값을 할당하기만 하면 됩니다. 자세한 내용은 이 항목의 예제 섹션을 참조하십시오. 또는 **Set-CsExUmContact** cmdlet을 호출하여 수정할 연락처 개체의 ID를 전달할 수 있습니다.

이 cmdlet을 실행할 수 있는 사용자: 기본적으로 RTCUniversalUserAdmins 그룹의 구성원은 **Set-CsExUmContact** cmdlet을 로컬로 실행할 수 있습니다. 사용자가 직접 만든 사용자 지정 RBAC(역할 기반 액세스 제어) 역할을 포함하여 이 cmdlet이 할당된 모든 RBAC 역할의 목록을 반환하려면 Windows PowerShell 프롬프트에서 다음 명령을 실행합니다.

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Set-CsExUmContact"}

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
<td><p>사용자 ID 매개 변수</p></td>
<td><p>수정할 연락처 개체의 고유 식별자입니다. 연락처 ID는 네 가지 형식 중 하나를 사용하여 지정할 수 있는데, 이러한 형식은 1) 연락처의 SIP 주소, 2) 연락처의 UPN(사용자 계정 이름), 3) 도메인\로그온 형태인 연락처의 도메인 이름 및 로그인 이름(예: litwareinc\exum1) 및 4) 연락처의 Active Directory 표시 이름(예: Team Auto Attendant)입니다.</p>
<p>전체 데이터 형식: Microsoft.Rtc.Management.AD.UserIdParameter</p></td>
</tr>
<tr class="even">
<td><p><em>AutoAttendant</em></p></td>
<td><p>선택</p></td>
<td><p>부울</p></td>
<td><p>연락처 개체가 자동 전화 교환인 경우 이 매개 변수를 True로 설정합니다. 기본적으로 이 매개 변수는 False입니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>Confirm</em></p></td>
<td><p>선택</p></td>
<td><p>스위치 매개 변수</p></td>
<td><p>명령을 실행하기 전에 확인 메시지를 표시합니다.</p></td>
</tr>
<tr class="even">
<td><p><em>Description</em></p></td>
<td><p>선택</p></td>
<td><p>문자열</p></td>
<td><p>이 연락처에 대한 설명입니다. 연락처 유형(자동 전화 교환 또는 구독자 액세스), 위치, 공급자 또는 각 Exchange UM 연락처의 목적을 식별하는 기타 정보를 식별하기 위해 관리자가 사용할 설명입니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>DisplayNumber</em></p></td>
<td><p>선택</p></td>
<td><p>문자열</p></td>
<td><p>연락처의 전화 번호입니다. 각 연락처에 대한 표시 번호는 고유해야 합니다. 예를 들어 두 개의 Exchange UM 연락처가 동일한 표시 번호를 가질 수 없습니다. 이 값을 변경하면 LineURI 속성 값도 변경됩니다.</p>
<p>이 값은 더하기 기호(+)로 시작하고 임의의 숫자가 포함될 수 있습니다. 첫 번째 숫자는 0이 아니어야 합니다.</p></td>
</tr>
<tr class="even">
<td><p><em>DomainController</em></p></td>
<td><p>선택</p></td>
<td><p>FQDN</p></td>
<td><p>도메인 컨트롤러를 지정하는 데 사용됩니다. 도메인 컨트롤러가 지정되지 않은 경우 사용 가능한 첫 번째 도메인 컨트롤러가 사용됩니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>Enabled</em></p></td>
<td><p>선택</p></td>
<td><p>부울</p></td>
<td><p>연락처가 Lync Server에 대해 활성화되었는지 여부를 나타냅니다. 이 매개 변수를 False로 설정하면 연락처가 비활성화되고 이 연락처와 연관된 자동 전화 교환 또는 구독자 액세스가 더 이상 작동하지 않습니다.</p>
<p>Enabled 매개 변수를 사용하여 계정을 비활성화한 경우 해당 계정과 연관된 정보(할당한 호스트된 음성 메일 정책 포함)는 유지됩니다. 나중에 Enable 매개 변수를 사용하여 계정을 다시 활성화할 경우 연관된 계정 정보가 복원됩니다.</p></td>
</tr>
<tr class="even">
<td><p><em>EnterpriseVoiceEnabled</em></p></td>
<td><p>선택</p></td>
<td><p>부울</p></td>
<td><p>연락처가 Enterprise Voice에 대해 활성화되었는지 여부를 나타냅니다. 이 값이 False로 설정된 경우 이 연락처와 연관된 자동 전화 교환 또는 구독자 액세스 기능을 더 이상 사용할 수 없습니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>ExchangeArchivingPolicy</em></p></td>
<td><p>선택</p></td>
<td><p>Exchange 보관 정책 옵션 열거</p></td>
<td><p>연락처의 메신저 대화 세션이 보관되는 위치를 나타냅니다. 사용 가능한 값은 다음과 같습니다.</p>
<p>* Uninitialized</p>
<p>* UseLyncArchivingPolicy</p>
<p>* ArchivingToExchange</p>
<p>* NoArchiving</p></td>
</tr>
<tr class="even">
<td><p><em>PassThru</em></p></td>
<td><p>선택</p></td>
<td><p>스위치 매개 변수</p></td>
<td><p>명령 결과를 반환합니다. 기본적으로 이 cmdlet에서는 출력을 생성하지 않습니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>SipAddress</em></p></td>
<td><p>선택</p></td>
<td><p>문자열</p></td>
<td><p>연락처의 SIP 주소입니다. 이 주소는 Active Directory 도메인 서비스에서 사용자 또는 연락처로 이미 존재하지 않는 새 주소여야 합니다.</p>
<p>이 값을 변경하면 OtherIpPhone 속성에 저장된 SIP 주소도 변경됩니다.</p>
<p>SipAddress를 <strong>Get-CsExUmContact</strong> cmdlet 명령에 대한 Identity 값으로 사용하여 특정 연락처를 검색할 수 있습니다. 해당 cmdlet을 호출할 경우 새 SipAddress가 사용됩니다. 이전 SIP 주소에 대한 쿼리는 개체를 반환하지 않습니다.</p></td>
</tr>
<tr class="even">
<td><p><em>WhatIf</em></p></td>
<td><p>선택</p></td>
<td><p>스위치 매개 변수</p></td>
<td><p>명령을 실제로 실행하지 않고도 명령이 실행될 경우 발생할 수 있는 현상을 설명합니다.</p></td>
</tr>
</tbody>
</table>


## 입력 형식

Microsoft.Rtc.Management.ADConnect.Schema.OCSADExUmContact 개체입니다. Exchange UM 연락처 개체의 파이프라인된 입력을 허용합니다.

## 반환 형식

이 cmdlet은 Microsoft.Rtc.Management.ADConnect.Schema.OCSADExUmContact 유형의 개체를 수정합니다. PassThru 매개 변수가 사용될 경우 이러한 유형의 개체도 반환합니다.

## 참고 항목

#### 기타 리소스

[New-CsExUmContact](new-csexumcontact.md)  
[Remove-CsExUmContact](remove-csexumcontact.md)  
[Get-CsExUmContact](get-csexumcontact.md)  
[Move-CsExUmContact](move-csexumcontact.md)

