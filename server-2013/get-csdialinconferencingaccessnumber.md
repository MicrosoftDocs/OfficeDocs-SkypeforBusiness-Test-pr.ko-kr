---
title: Get-CsDialInConferencingAccessNumber
TOCTitle: Get-CsDialInConferencingAccessNumber
ms:assetid: f2c78377-ad21-4a9f-bef9-e9ef97316c85
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg413015(v=OCS.15)
ms:contentKeyID: 49305507
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Get-CsDialInConferencingAccessNumber

 

_**마지막으로 수정된 항목:** 2015-03-09_

조직에서 사용하도록 구성된 모든 전화 접속 회의 액세스 번호에 대한 정보를 반환합니다. 전화 접속 회의는 사용자가 "일반" 전화, 휴대폰 또는 PSTN(공중 전화망)의 장치를 사용하여 온라인 회의의 오디오 부분에 참가할 수 있는 방법을 제공합니다. 이 cmdlet은 Lync Server 2010에서 도입되었습니다.

## 구문

    Get-CsDialInConferencingAccessNumber [-Region <String>] <COMMON PARAMETERS>

    Get-CsDialInConferencingAccessNumber -EmptyRegion <SwitchParameter> <COMMON PARAMETERS>

    Get-CsDialInConferencingAccessNumber [-Identity <UserIdParameter>] <COMMON PARAMETERS>

    COMMON PARAMETERS: [-Credential <PSCredential>] [-DomainController <Fqdn>] [-Filter <String>] [-OU <OUIdParameter>] [-ResultSize <Unlimited>]

## 예제

## 예제 1

예제 1에 표시된 명령은 조직에서 사용하도록 구성된 모든 전화 접속 회의 액세스 번호의 컬렉션을 반환합니다. 추가 매개 변수 없이 **Get-CsDialInConferencingAccessNumber** cmdlet을 호출하면 사용 가능한 모든 전화 접속 액세스 번호의 컬렉션이 항상 반환됩니다.

    Get-CsDialInConferencingAccessNumber

## 예제 2

예제 2에서는 ID가 sip:RedmondDialIn@litwareinc.com인 전화 접속 회의 액세스 번호가 반환됩니다. ID는 고유해야 하므로 이 명령은 둘 이상의 액세스 번호를 반환하지 않습니다.

    Get-CsDialInConferencingAccessNumber -Identity sip:RedmondDialIn@litwareinc.com

## 예제 3

예제 3에서는 Region 매개 변수를 사용하여 Redmond 지역과 연결된 모든 전화 접속 회의 액세스 번호를 반환합니다. 이 작업을 수행하기 위해 **Get-CsDialInConferencingAccessNumber** cmdlet이 Region 매개 변수와 함께 호출됩니다. "Redmond"를 매개 변수 값으로 지정하면 **Get-CsDialInConferencingAccessNumber** cmdlet은 연결된 지역 목록에 "Redmond"가 나타나는 모든 번호를 반환합니다. 예를 들어 지역으로 Redmond만 나열된 액세스 번호와 Redmond 및 Portland가 모두 나열된 액세스 번호가 반환됩니다.

    Get-CsDialInConferencingAccessNumber -Region "Redmond"

## 예제 4

예제 4에서는 지역과 연결되지 않은(즉, Regions 속성이 비어 있는) 모든 전화 접속 회의 액세스 번호를 반환합니다.

    Get-CsDialInConferencingAccessNumber -Region $Null

## 예제 5

예제 5에 표시된 명령은 USA 사이트(즉 SiteId가 site:USA인 사이트)로 범위가 지정된 Redmond 지역에 대한 전화 접속 회의 액세스 번호를 모두 반환합니다.

    Get-CsDialInConferencingAccessNumber -Region site:USA/Redmond

## 예제 6

예제 6에서는 Filter 매개 변수를 사용하여 DisplayName에 "Seattle"이라는 문자열 값이 포함된 모든 전화 접속 회의 액세스 번호의 컬렉션을 반환합니다. 필터 값 {DisplayName -like "\*Seattle\*"}은 반환되는 데이터를 DisplayName에 "Seattle"이라는 단어가 포함된 액세스 번호(예: Seattle Access Number, Dial-In Number for Seattle, Tacoma/Seattle Access Number 등)로 제한합니다.

    Get-CsDialInConferencingAccessNumber -Filter {DisplayName -like "*Seattle*"}

## 예제 7

예제 7에서는 줄 URI가 tel:+1425로 시작하는 모든 전화 접속 회의 액세스 번호를 반환합니다. 따라서 미국 지역 번호가 425인 모든 액세스 번호가 효과적으로 반환됩니다. 이 작업을 수행하기 위해 Filter 매개 변수와 함께 **Get-CsDialInConferencingAccessNumber** cmdlet이 호출됩니다. 필터 값 {LineUri -like "tel:+1425\*"}는 반환되는 데이터를 문자열 값 "tel:+1425"로 시작하는 줄 URI로 제한합니다. 지역 번호가 425인 전화 번호나 지역 번호가 206인 전화 번호를 모두 반환하려면 다음 필터 값을 사용합니다.

{LineUri -like "tel:+1425\*" -or LineUri -like "tel:+1206\*"}

    Get-CsDialInConferencingAccessNumber -Filter {LineUri -like "tel:+1425*"}

## 예제 8

예제 8에서는 기본 언어가 이탈리아어로 설정된 모든 전화 접속 회의 액세스 번호의 컬렉션을 반환합니다. 이 작업을 수행하기 위해 먼저 **Get-CsDialInConferencingAccessNumber** cmdlet을 호출하여 조직에서 사용하도록 구성된 모든 액세스 번호의 컬렉션을 반환합니다. 이 컬렉션은 PrimaryLanguage 속성이 Italian("it-It")과 같은 번호만 선택하는 **Where-Object** cmdlet에 파이프됩니다.

    Get-CsDialInConferencingAccessNumber | Where-Object {$_.PrimaryLanguage -eq "it-IT"}

## 예제 9

예제 9에 표시된 명령은 보조 언어 중 하나로 프랑스어가 나열된 모든 전화 접속 회의 액세스 번호를 반환합니다. 이 작업을 수행하기 위해 먼저 매개 변수 없이 **Get-CsDialInConferencingAccessNumber** cmdlet을 호출하여 조직에서 사용하도록 구성된 모든 액세스 번호의 컬렉션을 반환합니다. 이 컬렉션은 SecondaryLanguages 속성에 French(fr-FR) 목록이 포함된 번호만 선택하는 **Where-Object** cmdlet에 파이프됩니다.

    Get-CsDialInConferencingAccessNumber  | Where-Object {$_.SecondaryLanguages -contains "fr-FR"}

## 자세한 정보

전화 접속 회의를 사용하여 사용자는 모든 종류의 전화기(예: 표준 "유선전화", 휴대폰 또는 VoIP(Voice over Internet Protocol 전화)를 사용하여 온라인 회의의 오디오 부분에 참가할 수 있습니다. 그러면 컴퓨터나 인터넷 연결이 없어도 모임에 참가할 수 있습니다. 사용자는 모든 오디오 기능을 이용할 수 있습니다. 즉, 다른 참가자에게 말하고 모든 진행 상황을 들을 수 있습니다. 그러나 공유 슬라이드, 화상 공급 또는 기타 시각적 요소는 볼 수 없습니다.

사용자에게 전화 접속 회의 기능을 제공하려면 전화 접속 회의 액세스 번호를 만들어야 합니다. 이 번호는 사용자가 모임에 연결하기 위해 전화 걸 수 있는 전화 번호입니다. 전화 접속 회의 액세스 번호는 **New-CsDialInConferencingAccessNumber** cmdlet을 사용하여 만듭니다. 새 전화 접속 회의 액세스 번호를 만드는 작업은 실제로는 Active Directory 도메인 서비스에 새 대화 상대 개체를 만드는 작업입니다. 이 대화 상대 개체는 액세스 번호 및 모든 해당 특성을 나타내는 데 사용됩니다. 연락처 번호는 **Get-CsDialInConferencingAccessNumber** cmdlet을 사용하여 검색할 수 있습니다.

Microsoft Office Communications Server 2007에서 전화 접속 회의 액세스 번호를 가져온 경우 **Get-CsDialInConferencingAccessNumber** cmdlet을 실행하고 Region 매개 변수를 포함하여 이러한 번호를 검색할 수도 있습니다. 가져온 번호는 Region 매개 변수를 사용해야 표시됩니다. 그러나 가져온 번호의 URI(Uniform Resource Identifier) 외에 경고 메시지도 표시됩니다. 이는 cmdlet이 가져온 전화 접속 회의 액세스 번호를 처리하는 방식일 뿐입니다.

이 cmdlet을 실행할 수 있는 사용자: 기본적으로 RTCUniversalUserAdmins, RTCUniversalServerAdmins 및 RTCUniversalReadOnlyAdmins 그룹의 구성원은 **Get-CsDialInConferencingAccessNumber** cmdlet을 로컬로 실행할 수 있습니다. 사용자가 직접 만든 사용자 지정 RBAC(역할 기반 액세스 제어) 역할을 포함하여 이 cmdlet이 할당된 모든 RBAC 역할의 목록을 반환하려면 Windows PowerShell 프롬프트에서 다음 명령을 실행합니다.

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Get-CsDialInConferencingAccessNumber"}

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
<td><p><em>EmptyRegion</em></p></td>
<td><p>필수</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>하나 이상의 전화 접속 회의 액세스 번호와 연결되지 않은 지역과 연결된 다이얼 플랜에 대한 정보를 반환합니다. 그 예로 Bellevue 다이얼 플랜은 Bellevue 지역과 연결되어 있지만 Bellevue 지역에 액세스 번호가 구성되어 있지 않은 경우를 들 수 있습니다. 따라서 Bellevue 지역은 빈 지역으로 간주됩니다.</p>
<p>이 매개 변수는 다른 매개 변수와 함께 사용할 수 없습니다.</p></td>
</tr>
<tr class="even">
<td><p><em>Credential</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.PSCredential</p></td>
<td><p>대체 자격 증명으로 <strong>Get-CsDialInConferencingAccessNumber</strong> cmdlet을 실행하는 데 사용됩니다. Windows에 로그온하는 데 사용한 계정에 대화 상대 개체를 사용하는 데 필요한 권한이 없는 경우 이 기능이 필요할 수 있습니다.</p>
<p>Credential 매개 변수를 사용하려면 먼저 <strong>Get-Credential</strong> cmdlet을 사용하여 PSCredential 개체를 만들어야 합니다. 자세한 내용은 <strong>Get-Credential</strong> cmdlet 도움말 항목을 참조하십시오.</p></td>
</tr>
<tr class="odd">
<td><p><em>DomainController</em></p></td>
<td><p>선택</p></td>
<td><p>Microsoft.Rtc.Management.Deploy.Fqdn</p></td>
<td><p>대화 상대 정보를 검색하기 위해 지정된 도메인 컨트롤러에 연결하는 데 사용됩니다. 특정 도메인 컨트롤러에 연결하려면 DomainController 매개 변수 뒤에 컴퓨터 이름(예: atl-mcs-001) 또는 정규화된 도메인 이름(예: atl-mcs-001.litwareinc.com)을 포함합니다.</p></td>
</tr>
<tr class="even">
<td><p><em>Filter</em></p></td>
<td><p>선택</p></td>
<td><p>System.String</p></td>
<td><p>Lync Server 관련 특성을 필터링하여 반환된 데이터를 제한할 수 있도록 합니다. 예를 들어 반환되는 데이터를 표시 이름에 &quot;Redmond&quot;라는 문자열 값이 포함된 전화 접속 회의 번호로 제한하거나 1-800 접두사를 사용하는 무료 전화 접속 회의 번호로 제한할 수 있습니다.</p>
<p>Filter 매개 변수는 <strong>Where-Object</strong> cmdlet에 사용되는 구문과 동일한 Windows PowerShell 필터링 구문을 사용합니다. 예를 들어 1-800 접두사가 포함된 액세스 번호만 반환하는 필터는 {LineUri -like &quot;tel:+1800*&quot;}과 유사한 형태입니다. 여기서 LineUri는 Active Directory 특성을 나타내고, -like는 비교 연산자를 나타내며, &quot;tel:+1800*&quot;은 필터 값을 나타냅니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>Identity</em></p></td>
<td><p>선택</p></td>
<td><p>Microsoft.Rtc.Management.AD.UserIdParameter</p></td>
<td><p>검색할 전화 접속 회의 액세스 번호의 SIP 주소(즉, 해당 번호를 나타내는 연락처 개체)입니다. ID를 지정할 때는 &quot;sip:&quot; 접두사를 포함해야 합니다(예: -Identity sip:RedmondDialIn@litwareinc.com).</p>
<p>이 매개 변수를 지정하지 않으면 <strong>Get-CsDialInConferencingAccessNumber</strong> cmdlet이 조직에서 사용하도록 구성된 모든 전화 접속 회의 액세스 번호를 반환합니다.</p></td>
</tr>
<tr class="even">
<td><p><em>OU</em></p></td>
<td><p>선택</p></td>
<td><p>Microsoft.Rtc.Management.AD.OUIdParameter</p></td>
<td><p>특정 Active Directory OU(조직 구성 단위)에서 액세스 번호를 반환하는 데 사용됩니다. 여기에는 지정된 OU 및 모든 하위 OU의 데이터가 포함됩니다. 예를 들어 Finance OU에 두 개의 하위 OU인 AccountsPayable 및 AccountsReceivable이 있는 경우 이러한 세 개의 각 OU에서 액세스 번호 정보가 반환됩니다.</p>
<p>OU를 지정할 때 해당 컨테이너에 대한 고유 이름을 사용합니다(예: -OU &quot;OU=Finance,dc=litwareinc,dc=com&quot;).</p></td>
</tr>
<tr class="odd">
<td><p><em>Region</em></p></td>
<td><p>선택</p></td>
<td><p>System.String</p></td>
<td><p>지정된 다이얼 플랜 지역과 연결된 모든 전화 접속 회의 액세스 번호를 반환합니다. 예를 들어 Northwest 지역의 모든 전화 접속 번호를 반환하려면 -Region Northwest 구문을 사용하십시오.</p>
<p>또한 매개 변수 값에 범위를 포함하여 특정 사이트 또는 전역 범위로 범위가 지정된 액세스 번호를 반환할 수도 있습니다. 예를 들어 Northwest 지역을 사용하고 Redmond 사이트로 범위가 지정된 액세스 번호를 반환하려면 -Region site:Redmond/Northwest 구문을 사용합니다. 사이트 범위를 참조하는 경우 SiteId 속성을 사용해야 합니다. <strong>Get-CsSite</strong> cmdlet을 사용하여 SiteId 값을 검색할 수 있습니다.</p>
<p>다이얼 플랜과 연결되지 않은 액세스 번호 목록을 반환하려면 Region 매개 변수 값을 $Null: -Region $Null로 설정합니다.</p>
<p>이 매개 변수가 지정되면 전화 접속 회의 액세스 번호가 할당된 우선 순위대로만 반환됩니다. 우선 순위는 모임 초대 및 전화 접속 회의 웹 페이지에서 번호가 나타나는 순서와 동일한 순서입니다. 자세한 내용은 <a href="set-csdialinconferencingaccessnumber.md">Set-CsDialInConferencingAccessNumber</a> cmdlet 도움말 항목을 참조하십시오.</p></td>
</tr>
<tr class="even">
<td><p><em>ResultSize</em></p></td>
<td><p>선택</p></td>
<td><p>Microsoft.Rtc.Management.ADConnect.Core.Unlimited</p></td>
<td><p>명령에서 반환되는 레코드 수를 제한할 수 있게 합니다. 예를 들어, 포리스트에 있는 액세스 번호 수에 상관없이 7개의 액세스 번호만 반환하려면 ResultSize 매개 변수를 포함하고 매개 변수 값을 7로 설정합니다. 반환될 7개의 액세스 번호를 지정하는 방법은 없습니다. ResultSize를 7로 설정했지만 포리스트에 액세스 번호가 3개만 있는 경우 3개의 번호가 반환된 다음, 오류 없이 완료됩니다.</p>
<p>결과 크기는 0-2147483647(포함) 사이의 임의 정수로 설정할 수 있습니다. 0으로 설정할 경우 명령이 실행되지만 데이터가 반환되지 않습니다.</p></td>
</tr>
</tbody>
</table>


## 입력 형식

문자열. **Get-CsDialInConferencingAccessNumber** cmdlet은 액세스 번호의 ID를 나타내는 문자열 값을 허용합니다.

## 반환 형식

**Get-CsDialInConferencingAccessNumber** cmdlet은 Microsoft.Rtc.Management.Xds.AccessNumber 개체의 인스턴스를 반환합니다.

## 참고 항목

#### 기타 리소스

[New-CsDialInConferencingAccessNumber](new-csdialinconferencingaccessnumber.md)  
[Remove-CsDialInConferencingAccessNumber](remove-csdialinconferencingaccessnumber.md)  
[Set-CsDialInConferencingAccessNumber](set-csdialinconferencingaccessnumber.md)

