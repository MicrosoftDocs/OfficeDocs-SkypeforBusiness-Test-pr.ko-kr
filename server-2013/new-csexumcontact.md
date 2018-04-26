---
title: New-CsExUmContact
TOCTitle: New-CsExUmContact
ms:assetid: 085d0a0f-0efb-4c65-b742-2c1cb7a5ae8f
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg398139(v=OCS.15)
ms:contentKeyID: 49302723
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# New-CsExUmContact

 

_**마지막으로 수정된 항목:** 2015-03-09_

호스트된 Exchange 통합 메시징(UM)에 대한 새 자동 전화 교환 또는 구독자 액세스 연락처 개체를 만듭니다. 이 cmdlet은 Lync Server 2010에서 도입되었습니다.

## 구문

    New-CsExUmContact -DisplayNumber <String> -OU <OUIdParameter> -RegistrarPool <Fqdn> -SipAddress <String> [-AutoAttendant <$true | $false>] [-Confirm [<SwitchParameter>]] [-Description <String>] [-PassThru <SwitchParameter>] [-WhatIf [<SwitchParameter>]]

## 예제

## 예제 1

이 예제에서는 **New-CsExUmContact** cmdlet을 호출하여 새 Exchange UM Active Directory 연락처 개체를 만듭니다. 새 연락처를 만들려면 자동 전화 교환 또는 구독자 액세스의 SIP 주소(이 예제에서는 sip:exumsa1@fabrikam.com)를 제공해야 합니다. 또한 Lync Server 등록자 서비스가 실행되고 있는 풀의 이름(RedmondPool.litwareinc.com), 이 정보가 저장될 OU(OU=ExUmContacts,DC=litwareinc,DC=com) 및 자동 전화 교환이나 구독자 액세스의 전화 번호(2065554567)를 제공해야 합니다. AutoAttendant 매개 변수를 명확하게 설정하지 않았으므로 기본값 False가 적용되며 이 연락처 개체는 구독자 액세스 개체로 간주됩니다.

    New-CsExUmContact -SipAddress sip:exumsa1@fabrikam.com -RegistrarPool RedmondPool.litwareinc.com -OU "OU=ExUmContacts,DC=litwareinc,DC=com" -DisplayNumber 2065554567

## 예제 2

이 예제는 **New-CsExUmContact** cmdlet을 호출하여 새 Exchange UM 연락처를 만든다는 점에서 예제 1과 비슷합니다. 마찬가지로 새 자동 전화 교환 또는 구독자 액세스 연락처를 만들지만 이번에는 SIP 주소 sip:exumaa1@fabrikam.com을 사용합니다. 그런 다음, Lync Server 등록자 서비스가 실행되고 있는 풀의 이름(RedmondPool.litwareinc.com), 이 정보가 저장될 OU(OU=ExUmContacts,DC=litwareinc,DC=com) 및 자동 전화 교환이나 구독자 액세스의 전화 번호(2065554567)를 제공합니다. 이 예제에서는 선택적 매개 변수 AutoAttendant를 True($True)로 설정하여 이 개체가 자동 전화 교환 연락처라는 것을 보여 준다는 차이점이 있습니다.

    New-CsExUmContact -SipAddress sip:exumaa1@fabrikam.com -RegistrarPool RedmondPool.litwareinc.com -OU "OU=ExUmContacts,DC=litwareinc,DC=com" -DisplayNumber 2065559876 -AutoAttendant $True

## 자세한 정보

Lync Server는 Exchange UM과 함께 작동하여 자동 전화 교환 및 구독자 액세스와 같은 여러 가지의 음성 관련 기능을 제공합니다. Exchange UM이 온-프레미스가 아니라 호스트된 서비스로 제공될 경우 자동 전화 교환 및 구독자 액세스 기능을 적용하려면 이 cmdlet으로 연락처 개체를 만들어야 합니다. 이러한 개체는 **New-CsExUmContact** cmdlet을 호출하여 만듭니다.

이 cmdlet을 사용하여 만든 연락처 개체는 연락처에 대한 경로 지정을 구성하는 호스트된 음성 메일 정책을 적용해야만 시스템 내에서 사용할 수 있습니다. **Get-CsHostedVoicemailPolicy** cmdlet을 호출하여 호스트된 음성 메일 정책을 검색할 수 있습니다. 검색된 정책에서 해당 전역 또는 사이트 정책이 있는지 여부 또는 이 연락처에 부여해야 하는 사용자별 정책이 있는지 여부를 확인할 수 있습니다.

이 cmdlet을 실행할 수 있는 사용자: 기본적으로 RTCUniversalServerAdmins 그룹의 구성원은 **New-CsExUmContact** cmdlet을 로컬로 실행할 수 있습니다. 사용자가 직접 만든 사용자 지정 RBAC(역할 기반 액세스 제어) 역할을 포함하여 이 cmdlet이 할당된 모든 RBAC 역할의 목록을 반환하려면 Windows PowerShell 프롬프트에서 다음 명령을 실행합니다.

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "New-CsExUmContact"}

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
<td><p><em>DisplayNumber</em></p></td>
<td><p>필수</p></td>
<td><p>System.String</p></td>
<td><p>연락처의 전화 번호입니다. 각 연락처에 대한 표시 번호는 고유해야 합니다. 예를 들어 두 개의 Exchange UM 연락처가 동일한 표시 번호를 가질 수 없습니다.</p>
<p>이 값은 더하기 기호(+)로 시작하고 임의의 숫자가 포함될 수 있습니다. 첫 번째 숫자는 0이 아니어야 합니다.</p></td>
</tr>
<tr class="even">
<td><p><em>OU</em></p></td>
<td><p>필수</p></td>
<td><p>Microsoft.Rtc.Management.AD.OUIdParameter</p></td>
<td><p>Active Directory에서 이 연락처가 위치할 OU(조직 구성 단위)입니다.</p>
<p>전체 데이터 형식: Microsoft.Rtc.Management.AD.OUIdParameter</p></td>
</tr>
<tr class="odd">
<td><p><em>RegistrarPool</em></p></td>
<td><p>필수</p></td>
<td><p>Microsoft.Rtc.Management.Deploy.Fqdn</p></td>
<td><p>등록자 서비스가 실행되고 있는 풀의 FQDN(정규화된 도메인 이름)입니다.</p>
<p>Lync Server의 Exchange UM 연락처는 Microsoft Office Communications Server 2007 또는 Microsoft Office Communications Server 2007 R2 배포에 속한 풀로 이동할 수 없습니다.</p>
<p>전체 데이터 형식: Microsoft.Rtc.Management.Deploy.Fqdn</p></td>
</tr>
<tr class="even">
<td><p><em>SipAddress</em></p></td>
<td><p>필수</p></td>
<td><p>System.String</p></td>
<td><p>연락처의 SIP 주소입니다. 이 주소는 Active Directory 도메인 서비스에서 사용자 또는 연락처로 이미 존재하지 않는 새 주소여야 합니다. 이 값은 문자열 sip:로 시작하고 그 뒤에 SIP 주소가 와야 합니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>AutoAttendant</em></p></td>
<td><p>선택</p></td>
<td><p>System.Boolean</p></td>
<td><p>이 연락처 개체가 자동 전화 교환인지 여부를 지정합니다. 자동 전화 교환은 전화를 건 사람이 전화 시스템을 탐색하여 원하는 상대방을 찾을 수 있게 하는 음성 프롬프트 집합을 제공합니다.</p>
<p>기본값: False</p></td>
</tr>
<tr class="even">
<td><p><em>Confirm</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>명령을 실행하기 전에 확인 메시지를 표시합니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>Description</em></p></td>
<td><p>선택</p></td>
<td><p>System.String</p></td>
<td><p>이 연락처에 대한 설명입니다. 연락처 유형(자동 전화 교환 또는 구독자 액세스), 위치, 공급자 또는 각 Exchange UM 연락처의 목적을 식별하는 기타 정보를 식별하기 위해 관리자가 사용할 설명입니다.</p></td>
</tr>
<tr class="even">
<td><p><em>PassThru</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>이 명령의 결과를 반환합니다. 이 cmdlet을 실행하면 새로 만든 개체가 표시됩니다. 단순히 이 매개 변수를 포함하면 해당 출력이 반복되므로 매개 변수를 중복하여 사용하는 것이 됩니다.</p></td>
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

없음.

## 반환 형식

Microsoft.Rtc.Management.ADConnect.Schema.OCSADExUmContact 유형의 개체를 만듭니다.

## 참고 항목

#### 기타 리소스

[Remove-CsExUmContact](remove-csexumcontact.md)  
[Set-CsExUmContact](set-csexumcontact.md)  
[Get-CsExUmContact](get-csexumcontact.md)  
[Move-CsExUmContact](move-csexumcontact.md)  
[Get-CsHostedVoicemailPolicy](get-cshostedvoicemailpolicy.md)

