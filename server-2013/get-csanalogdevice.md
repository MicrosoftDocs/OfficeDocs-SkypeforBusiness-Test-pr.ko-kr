---
title: Get-CsAnalogDevice
TOCTitle: Get-CsAnalogDevice
ms:assetid: 92f56039-f112-45bb-8340-109b0837f828
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg398748(v=OCS.15)
ms:contentKeyID: 49304400
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Get-CsAnalogDevice

 

_**마지막으로 수정된 항목:** 2015-03-09_

Lync Server를 사용하여 관리할 수 있는 아날로그 장치에 대한 정보를 반환합니다. 아날로그 장치는 PSTN(공중 전화망)에 연결된 전화(또는 팩스)입니다. 이 cmdlet은 Lync Server 2010에서 도입되었습니다.

## 구문

    Get-CsAnalogDevice [-Identity <UserIdParameter>] [-Credential <PSCredential>] [-DomainController <Fqdn>] [-Filter <String>] [-LdapFilter <String>] [-OU <OUIdParameter>] [-ResultSize <Unlimited>]

## 예제

## 예제 1

예제 1에 표시된 명령은 현재 조직에 사용하도록 구성된 모든 아날로그 장치 컬렉션을 반환합니다. 이 작업을 수행하기 위해 매개 변수 없이 **Get-CsAnalogDevice** cmdlet을 호출합니다.

    Get-CsAnalogDevice

## 예제 2

예제 2에서는 조직의 모든 아날로그 장치에 대해 DisplayName과 LineUri의 두 가지 속성 값만 반환합니다. 이 작업을 수행하기 위해 명령은 먼저 매개 변수 없이 **Get-CsAnalogDevice** cmdlet을 호출합니다. 이렇게 하면 조직의 모든 아날로그 장치에 대한 모든 속성 값이 반환됩니다. 이 컬렉션은 DisplayName 및 LineUri 속성에 대한 값만 선택하여 화면에 표시하는 **Select-Object** cmdlet에 파이프됩니다.

    Get-CsAnalogDevice | Select-Object DisplayName, LineUri

## 예제 3

예제 3은 Active Directory 표시 이름이 "Building 14 Receptionist"인 아날로그 장치에 대한 정보를 반환합니다. 이를 수행하기 위해 명령은 **Get-CsAnalogDevice** 및 Filter 매개 변수를 호출합니다. 필터 값 {DisplayName -eq "Building 14 Receptionist"}는 DisplayName 속성이 "Building 14 Receptionist"와 같은 아날로그 장치 항목만 반환하도록 제한합니다.

    Get-CsAnalogDevice -Filter {DisplayName -eq "Building 14 Receptionist"}

## 예제 4

예제 4에서는 게이트웨이 192.168.0.240을 사용하도록 구성된 모든 아날로그 장치를 반환합니다. 이를 수행하기 위해 **Get-CsAnalogDevice** cmdlet을 호출하고 Filter 매개 변수를 포함합니다. 필터 값 "192.168.0.240"은 Gateway 속성 값이 192.168.0.240과 같은 아날로그 장치 개체만 반환되도록 합니다.

    Get-CsAnalogDevice -Filter {Gateway -eq "192.168.0.240"}

## 예제 5

예제 5에 표시된 명령은 조직의 모든 아날로그 팩스에 대한 정보를 반환합니다. 이 작업을 수행하기 위해 Filter 매개 변수를 사용하여 **Get-CsAnalogDevice** cmdlet을 호출합니다. 필터 값 {AnalogFax -eq $True}는 AnalogFax 속성이 True와 같은 아날로그 장치인 팩스 개체만 반환하도록 제한합니다.

    Get-CsAnalogDevice -Filter {AnalogFax -eq $True}

## 예제 6

예제 6에서는 단일 아날로그 장치를 반환합니다. 이 장치는 LineUri(전화 번호)가 tel:+14255556001과 같습니다.

    Get-CsAnalogDevice -Filter {LineUri -eq "tel:+14255556001"}

## 예제 7

예제 7은 지역 번호가 425이고 전화 접두사가 555인 모든 아날로그 장치를 반환합니다. 이 작업을 수행하기 위해 **Get-CsAnalogDevice** cmdlet에 Filter 매개 변수가 사용됩니다. 필터 값 {LineUri -like "tel:+1425555\*"}는 LineUri 속성이 문자 "tel:+1425555"로 시작하는 장치에 대한 데이터만 반환하도록 제한합니다. 이는 1425555와 같은 문자로 시작하는 전화 번호와 같습니다(예: 1-425-555-1298).

    Get-CsAnalogDevice -Filter {LineUri -like "tel:+1425555*"}

## 예제 8

예제 8에서는 Active Directory 도메인 서비스의 Telecommunications OU에 연락처 개체가 있는 모든 아날로그 장치 컬렉션을 반환합니다. 이 작업을 수행하기 위해 OU 매개 변수를 사용하여 **Get-CsAnalogDevice** cmdlet을 호출합니다. 매개 변수 값은 OU에 고유 이름이 ou=Telecommunications,dc=litwareinc,dc=com인 연락처 개체가 있는 아날로그 장치에 대한 개체만 반환하도록 제한합니다.

    Get-CsAnalogDevice -OU "ou=Telecommunications,dc=litwareinc,dc=com"

## 예제 9

예제 9에 표시된 명령은 아날로그 장치 컬렉션을 검색한 다음 컬렉션의 각 장치에 음성 정책을 할당하는 방법을 보여 줍니다. 이 작업을 수행하기 위해 먼저 **Get-CsAnalogDevice** cmdlet을 매개 변수 없이 호출합니다. 그러면 조직에서 사용하도록 구성된 모든 아날로그 장치 컬렉션이 반환됩니다. 이 컬렉션은 컬렉션의 각 장치에 AnalogVoicePolicy 음성 정책을 할당하는 **Grant-CsVoicePolicy** cmdlet에 파이프됩니다.

    Get-CsAnalogDevice | Grant-CsVoicePolicy -PolicyName "AnalogVoicePolicy"

## 자세한 정보

아날로그 장치에는 PSTN(공중 전화망)에 연결된 전화, 팩스, 모뎀 및 TTY/TTD(텔레타이프/청각 장애자용 통신 장치) 장치가 포함됩니다. 아날로그 장치는 Enterprise Voice(Microsoft에서 제공하는 VoIP(Voice over Internet Protocol) 솔루션)를 활용하는 장치와 달리 디지털 패킷을 사용하여 정보를 전송하지 않습니다. 대신에 정보가 연속 신호를 사용하여 전송됩니다. 이 신호를 일반적으로 아날로그 신호라고 하며, 그래서 "아날로그 장치"라고 합니다.

아날로그 전화 및 Enterprise Voice를 사용하는 전화 외에 IP가 아닌 디지털 전화도 있습니다. 이러한 전화는 함께 구매한 PBX(Private Branch Exchange) 시스템에 속하므로 Lync Server cmdlet을 사용하여 관리할 수 없습니다.

Lync Server는 관리자가 아날로그 장치와 Active Directory 연락처 개체를 연결하여 조직의 아날로그 장치를 관리할 수 있도록 지원합니다. 장치가 연락처 개체에 연결되면 연락처에 정책 및 다이얼 플랜을 할당하는 등의 작업을 수행하여 아날로그 장치를 관리할 수 있습니다.

**Get-CsAnalogDevice** cmdlet을 사용하면 조직에서 사용하도록 구성된 아날로그 장치에 대한 정보를 검색할 수 있습니다. 매개 변수 없이 **Get-CsAnalogDevice** cmdlet을 호출하면 모든 아날로그 장치에 대한 정보가 반환됩니다. 선택적 매개 변수는 지정된 OU에 연락처 개체가 있는 모든 장치를 검색하거나 지정된 건물에 있는 모든 아날로그 장치를 검색하는 등 정보를 필터링할 수 있는 다양한 방법을 제공합니다.

이 cmdlet을 실행할 수 있는 사용자: 기본적으로 RTCUniversalUserAdmins, RTCUniversalServerAdmins 및 RTCUniversalReadOnlyAdmins 그룹의 구성원은 **Get-CsAnalogDevice** cmdlet을 로컬로 실행할 수 있습니다. 특정 사이트 또는 특정 Active Directory OU에 대해 이 cmdlet을 실행할 권한은 **Grant-CsOUPermission** cmdlet을 사용하여 할당할 수 있습니다. 사용자가 직접 만든 사용자 지정 RBAC(역할 기반 액세스 제어) 역할을 포함하여 이 cmdlet이 할당된 모든 RBAC 역할의 목록을 반환하려면 Windows PowerShell 프롬프트에서 다음 명령을 실행합니다.

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Get-CsAnalogDevice"}

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
<td><p><em>Credential</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.PSCredential</p></td>
<td><p>대체 자격 증명으로 <strong>Get-CsAnalogDevice</strong> cmdlet을 실행하는 데 사용됩니다. Windows에 로그온하는 데 사용한 계정에 연락처 개체를 사용하는 데 필요한 권한이 없는 경우 이 기능이 필요할 수 있습니다.</p>
<p>Credential 매개 변수를 사용하려면 먼저 <strong>Get-Credential</strong> cmdlet을 사용하여 PSCredential 개체를 만들어야 합니다. 자세한 내용은 <strong>Get-Credential</strong> cmdlet 도움말 항목을 참조하십시오.</p></td>
</tr>
<tr class="even">
<td><p><em>DomainController</em></p></td>
<td><p>선택</p></td>
<td><p>Microsoft.Rtc.Management.Deploy.Fqdn</p></td>
<td><p>대화 상대 정보를 검색하기 위해 지정된 도메인 컨트롤러에 연결하는 데 사용됩니다. 특정 도메인 컨트롤러에 연결하려면 DomainController 매개 변수 뒤에 컴퓨터의 FQDN(정규화된 도메인 이름)을 포함합니다(예: atl-cs-001.litwareinc.com).</p></td>
</tr>
<tr class="odd">
<td><p><em>Filter</em></p></td>
<td><p>선택</p></td>
<td><p>System.String</p></td>
<td><p>Lync Server 관련 특성을 필터링하여 반환되는 데이터를 제한할 수 있습니다. 예를 들어 특성 음성 정책이 할당된 아날로그 장치 연락처 개체 또는 특정 음성 정책이 할당되지 않은 연락처에 대해 반환되는 데이터를 제한할 수 있습니다.</p>
<p>Filter 매개 변수는 <strong>Where-Object</strong> cmdlet에 사용되는 구문과 동일한 Windows PowerShell 필터링 구문을 사용합니다. 예를 들어 팩스만 반환하는 필터는 Active Directory 특성을 나타내는 AnalogFax, 비교 연산자(같음)를 나타내는 -eq 및 필터 값을 나타내는 $True(기본 제공 Windows PowerShell 변수)를 사용하여 다음과 같이 나타납니다.</p>
<p>-Filter {AnalogFax -eq $True}</p></td>
</tr>
<tr class="even">
<td><p><em>Identity</em></p></td>
<td><p>선택</p></td>
<td><p>Microsoft.Rtc.Management.AD.UserIdParameter</p></td>
<td><p>아날로그 장치의 고유한 식별자입니다. 아날로그 장치는 연결된 연락처 개체의 Active Directory 고유 이름을 사용하여 식별됩니다. 아날로그 장치는 기본적으로 공용 이름으로 GUID(Globally Unique Identifier)를 사용합니다. 따라서 일반적으로 CN={ce84964a-c4da-4622-ad34-c54ff3ed361f},OU=Redmond,DC=Litwareinc,DC=com과 유사한 ID가 지정됩니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>LdapFilter</em></p></td>
<td><p>선택</p></td>
<td><p>System.String</p></td>
<td><p>일반 Active Directory 특성(즉, Lync Server와 관련되지 않은 특성)을 필터링하여 반환되는 데이터를 제한할 수 있습니다. 예를 들어 특정 부서에 할당되거나 특정 건물에 있는 대화 상대 개체에 대한 데이터만 반환하도록 제한할 수 있습니다.</p>
<p>필터를 만들 때 LdapFilter 매개 변수는 LDAP 쿼리 언어를 사용합니다. 예를 들어 레드몬드 시에 있는 아날로그 장치를 나타내는 연락처 개체만 반환하는 필터는</p>
<p>-LDAPFilter &quot;l=Redmond&quot;와 같습니다.</p>
<p>이 필터에서 &quot;l&quot;는 Active Directory 특성(구/군/시)을 나타내고 &quot;=&quot;는 비교 연산자(같음)를 나타내며 &quot;Redmond&quot;는 필터 값을 나타냅니다.</p></td>
</tr>
<tr class="even">
<td><p><em>OU</em></p></td>
<td><p>선택</p></td>
<td><p>Microsoft.Rtc.Management.AD.OUIdParameter</p></td>
<td><p>특정 Active Directory OU(조직 구성 단위)에서대화 상대 개체를 반환하는 데 사용됩니다. 이 경우 지정된 OU 및 모든 하위 OU에서 데이터가 반환됩니다. 예를 들어 Finance OU에 두 개의 하위 OU인 AccountsPayable 및 AccountsReceivable이 있는 경우 이러한 각 OU에서 아날로그 장치 정보가 반환됩니다.</p>
<p>OU를 지정할 때 해당 컨테이너에 대한 고유 이름을 사용합니다(예: -OU &quot;OU=Finance,dc=litwareinc,dc=com&quot;).</p></td>
</tr>
<tr class="odd">
<td><p><em>ResultSize</em></p></td>
<td><p>선택</p></td>
<td><p>Microsoft.Rtc.Management.ADConnect.Core.Unlimited</p></td>
<td><p>명령에서 반환되는 레코드 수를 제한할 수 있게 합니다. 예를 들어 포리스트에 있는 아날로그 장치 수에 상관없이 7개의 아날로그 장치만 반환하려면 -ResultSize 매개 변수를 포함하고 매개 변수 값을 7로 설정합니다. 반환될 7개의 전화를 지정하는 방법은 없습니다. ResultSize를 7로 설정했지만 포리스트에 아날로그 장치가 3개만 있는 경우 3개의 장치가 반환된 다음 오류 없이 완료됩니다.</p>
<p>결과 크기는 0-2147483647(포함) 사이의 임의 정수로 설정할 수 있습니다. 0으로 설정할 경우 명령이 실행되지만 데이터가 반환되지 않습니다.</p></td>
</tr>
</tbody>
</table>


## 입력 형식

문자열. **Get-CsAnalogDevice** cmdlet은 아날로그 장치의 ID를 나타내는 파이프라인된 문자열 값을 허용합니다.

## 반환 형식

**Get-CsAnalogDevice** cmdlet은 Microsoft.Rtc.Management.ADConnect.Schema.OCSADAnalogDeviceContact 개체의 인스턴스를 반환합니다.

## 참고 항목

#### 기타 리소스

[Move-CsAnalogDevice](move-csanalogdevice.md)  
[New-CsAnalogDevice](new-csanalogdevice.md)  
[Remove-CsAnalogDevice](remove-csanalogdevice.md)  
[Set-CsAnalogDevice](set-csanalogdevice.md)

