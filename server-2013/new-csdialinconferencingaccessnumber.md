---
title: New-CsDialInConferencingAccessNumber
TOCTitle: New-CsDialInConferencingAccessNumber
ms:assetid: c6d0536c-0ba3-45e0-affe-7ee00a070435
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg398818(v=OCS.15)
ms:contentKeyID: 49304990
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# New-CsDialInConferencingAccessNumber

 

_**마지막으로 수정된 항목:** 2015-03-09_

새 전화 접속 회의 액세스 번호를 만듭니다. 전화 접속 회의는 사용자가 "일반" 전화, 휴대폰 또는 PSTN(공중 전화망)의 기타 장치를 사용하여 전화 회의의 오디오 부분에 참가할 수 있는 방법을 제공합니다. 이 cmdlet은 Lync Server 2010에서 도입되었습니다.

## 구문

    New-CsDialInConferencingAccessNumber -Pool <Fqdn> -Regions <MultiValuedProperty> <COMMON PARAMETERS>

    New-CsDialInConferencingAccessNumber -HostingProviderProxyFqdn <Fqdn> <COMMON PARAMETERS>

    COMMON PARAMETERS: -DisplayNumber <String> -LineURI <String> -PrimaryLanguage <String> -PrimaryUri <String> [-Confirm [<SwitchParameter>]] [-DisplayName <String>] [-PassThru <SwitchParameter>] [-ScopeToSite <SwitchParameter>] [-SecondaryLanguages <MultiValuedProperty>] [-Tenant <Guid>] [-WhatIf [<SwitchParameter>]]

## 예제

## 예제 1

예제 1에서는 기본 URI가 sip:RedmondDialIn@litwareinc.com인 새 전화 접속 회의 액세스 번호를 만듭니다. 이 명령에는 PrimaryUri 매개 변수 외에 Lync에 표시되는 전화 번호(DisplayNumber), E.164 형식의 전화 번호(LineUri), 새 번호를 할당할 등록자 풀(-Pool), 전화 번호의 기본 언어(PrimaryLanguage) 및 새 번호가 할당되는 지역(Region)을 구성하는 매개 변수도 포함됩니다.

    New-CsDialInConferencingAccessNumber -PrimaryUri "sip:RedmondDialIn@litwareinc.com" -DisplayNumber "1-800-555-1234" -LineUri "tel:+18005551234" -Pool atl-cs-001.litwareinc.com -PrimaryLanguage "en-US" -Regions "Redmond"

## 예제 2

예제 2에 표시된 명령은 예제 1에 표시된 명령의 변형입니다. 새 전화 접속 회의 액세스 번호에 두 개의 보조 언어(프랑스어(캐나다) 및 프랑스어)를 할당한다는 점만 다릅니다. 이러한 보조 언어를 할당하기 위해 할당할 언어(fr-CA 및 fr-FR)의 쉼표로 구분된 목록과 함께 SecondaryLanguages 매개 변수를 포함합니다.

    New-CsDialInConferencingAccessNumber -PrimaryUri "sip:RedmondDialIn@litwareinc.com" -DisplayNumber "1-800-555-1234" -LineUri "tel:+18005551234" -Pool atl-cs-001.litwareinc.com -PrimaryLanguage "en-US" -Regions "Redmond" -SecondaryLanguages "fr-CA", "fr-FR"

## 예제 3

예제 3에서는 대화 상대 개체의 홈 풀이 있는 사이트로 범위가 지정된 새 전화 접속 회의 액세스 번호를 만듭니다. 이 작업을 수행하기 위해 명령은 ScopeToSite 매개 변수를 포함합니다.

    New-CsDialInConferencingAccessNumber -PrimaryUri "sip:RedmondDialIn@litwareinc.com" -DisplayNumber "1-800-555-1234" -LineUri "tel:+18005551234" -Pool atl-cs-001.litwareinc.com -PrimaryLanguage "en-US" -Regions "Redmond" -ScopeToSite

## 자세한 정보

전화 접속 회의를 사용하여 사용자는 모든 종류의 전화기(예: 표준 "유선전화", 휴대폰 또는 VoIP(Voice over Internet Protocol 전화)를 사용하여 온라인 회의의 오디오 부분에 참가할 수 있습니다. 그러면 컴퓨터나 인터넷 연결이 없어도 모임에 참가할 수 있습니다. 사용자는 모든 오디오 기능을 이용할 수 있습니다. 즉, 다른 참가자에게 말하고 모든 진행 상황을 들을 수 있습니다. 하지만 공유 슬라이드, 비디오 대화 또는 기타 시각적 요소는 볼 수 없습니다.

사용자에게 전화 접속 회의 기능을 제공하려면 전화 접속 회의 액세스 번호를 만들어야 합니다. 사용자가 모임에 연결하기 위해 전화를 걸어야 하는 전화 번호입니다. 전화 접속 회의 액세스 번호는 **New-CsDialInConferencingAccessNumber** cmdlet을 사용하여 만듭니다. 새 전화 접속 회의 액세스 번호를 만드는 작업은 실제로는 Active Directory 도메인 서비스에 새 대화 상대 개체를 만드는 작업입니다. 이 대화 상대 개체는 액세스 번호 및 모든 해당 특성을 나타내는 데 사용됩니다.

새 전화 접속 번호를 만들 때 PrimaryUri, LineURI, Pool, DisplayNumber, PrimaryLanguage 및 Regions 매개 변수를 포함해야 합니다. 이러한 매개 변수 및 매개 변수 값은 Regions을 제외하고는 모두 단순합니다. 새 액세스 번호를 만들면 하나 이상의 지역과 연결해야 합니다. 그리고 지역이 하나 이상의 다이얼 플랜에 나타나지 않으면 전화 접속 회의 번호에 지역을 연결할 수 없습니다. 지역이 하나 이상 다이얼 플랜의 DialInConferencingRegion 속성에 표시되면 액세스 번호에 연결할 수 있고, 그렇지 않으면 액세스 번호에 연결할 수 없습니다. 따라서 전화 접속 회의 액세스 번호를 만들려면 먼저 다이얼 플랜을 만들고 해당 다이얼 플랜의 지역을 지정해야 합니다.

이 cmdlet을 실행할 수 있는 사용자: 기본적으로 RTCUniversalServerAdmins 그룹의 구성원은 **New-CsDialInConferencingAccessNumber** cmdlet을 로컬로 실행할 수 있습니다. 사용자가 직접 만든 사용자 지정 RBAC(역할 기반 액세스 제어) 역할을 포함하여 이 cmdlet이 할당된 모든 RBAC 역할의 목록을 반환하려면 Windows PowerShell 프롬프트에서 다음 명령을 실행합니다.

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "New-CsDialInConferencingAccessNumber"}

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
<td><p>모임 초대 및 전화 접속 회의 웹 페이지에 표시되는 전화 번호입니다. DisplayNumber는 원하는 형식으로 지정할 수 있습니다. 예를 들어 1-800-555-1234, 1-(800)-555-1234, 1.800.555.1234 등으로 지정할 수 있습니다.</p></td>
</tr>
<tr class="even">
<td><p><em>HostingProviderProxyFqdn</em></p></td>
<td><p>필수</p></td>
<td><p>Microsoft.Rtc.Management.Deploy.Fqdn</p></td>
<td><p>전화 접속 회의 서비스를 호스트하는 호스팅 공급자의 정규화된 도메인 이름입니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>LineURI</em></p></td>
<td><p>필수</p></td>
<td><p>System.String</p></td>
<td><p>실제 전화 접속 회의 전화 번호입니다. LineURI는 tel: 접두사를 시작으로 더하기(+) 기호, 국가 번호, 지역 번호 및 전화 번호가 차례로 뒤에 오는 구문을 사용하여 지정해야 합니다(예: tel:+18005551234). 공백, 하이픈, 괄호 및 기타 문자는 허용되지 않습니다.</p>
<p>LineURI는 Active Directory 전체에서 고유해야 합니다.</p></td>
</tr>
<tr class="even">
<td><p><em>Pool</em></p></td>
<td><p>필수</p></td>
<td><p>Microsoft.Rtc.Management.Deploy.Fqdn</p></td>
<td><p>새 대화 상대 개체의 홈 풀입니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>PrimaryLanguage</em></p></td>
<td><p>필수</p></td>
<td><p>System.String</p></td>
<td><p>전화 접속 회의 알림을 만드는 데 사용되는 기본 언어입니다. 이 언어는 사용 가능한 전화 접속 회의 언어 코드 중 하나를 사용하여 구성해야 합니다(예: 미국 영어의 경우 en-US, 프랑스어의 경우 fr-FR 등). 사용 가능한 언어 코드 목록을 반환하려면 Windows PowerShell 프롬프트에 다음 명령을 입력합니다.</p>
<p>Get-CsDialInConferencingLanguageList | Select-Object -ExpandProperty Languages</p></td>
</tr>
<tr class="even">
<td><p><em>PrimaryUri</em></p></td>
<td><p>필수</p></td>
<td><p>System.String</p></td>
<td><p>새 대화 상대 개체에 할당할 고유 SIP 주소입니다. PrimaryUri를 지정할 때는 &quot;sip:&quot; 접두사가 앞에 와야 합니다(예: -PrimaryUri &quot; sip:RedmondDialIn@litwareinc.com&quot;). sip: 접두사는 모두 소문자로 입력해야 합니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>Regions</em></p></td>
<td><p>필수</p></td>
<td><p>Microsoft.Rtc.Management.ADConnect.Core.MultiValuedProperty</p></td>
<td><p>전화 접속 번호와 연결된 다이얼 플랜 지역입니다. 지역이 하나 이상의 다이얼 플랜에 포함되지 않은 경우에는 전화 접속 회의 액세스 번호에 연결할 수 없습니다. 여러 지역을 사용하려면 쉼표로 구분된 목록을 사용하십시오(예: -Regions &quot;Northwest&quot;, &quot;Southwest&quot;).</p></td>
</tr>
<tr class="even">
<td><p><em>Confirm</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>명령을 실행하기 전에 확인 메시지를 표시합니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>DisplayName</em></p></td>
<td><p>선택</p></td>
<td><p>System.String</p></td>
<td><p>새 연락처 개체의 Active Directory 표시 이름입니다. 또한 이 이름은 Lync에 나타납니다.</p></td>
</tr>
<tr class="even">
<td><p><em>PassThru</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>새 전화 접속 회의 액세스 번호를 나타내는 파이프라인을 통해 대화 상대 개체를 전달하는 데 사용됩니다. 기본적으로 <strong>New-CsDialInConferencingAccessNumber</strong> cmdlet은 파이프라인을 통해 개체를 전달하지 않습니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>ScopeToSite</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>이 매개 변수가 있으면 새 번호의 범위가 대화 상대 개체의 홈 풀과 동일한 사이트에 지정됩니다. ScopeToSite 매개 변수를 포함하지 않으면 새 번호가 전역 범위에 할당됩니다.</p></td>
</tr>
<tr class="even">
<td><p><em>SecondaryLanguages</em></p></td>
<td><p>선택</p></td>
<td><p>Microsoft.Rtc.Management.ADConnect.Core.MultiValuedProperty</p></td>
<td><p>전화 접속 회의 알림을 만드는 데 사용할 수 있는 선택적 언어 컬렉션입니다. 보조 언어는 쉼표로 구분된 언어 코드 목록으로 구성해야 합니다. 예를 들어 -SecondaryLanguages &quot;fr-CA&quot;, &quot;fr-FR&quot; 구문은 프랑스어(캐나다) 및 프랑스어를 보조 언어로 설정합니다.</p>
<p>단일 액세스 번호에 최대 4개의 보조 언어를 사용할 수 있습니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>Tenant</em></p></td>
<td><p>선택</p></td>
<td><p>System.Guid</p></td>
<td><p>새 전화 접속 회의 액세스 번호가 만들어지는 비즈니스용 Skype Online 테넌트 계정의 GUID(Globally unique identifier)입니다. 예를 들면 다음과 같습니다.</p>
<p>–Tenant &quot;38aad667-af54-4397-aaa7-e94c79ec2308&quot;</p>
<p>다음 명령을 실행하여 각 테넌트에 대한 테넌트 ID를 반환할 수 있습니다.</p>
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

없음. **New-CsDialInConferencingAccessNumber** cmdlet은 파이프라인된 입력을 허용하지 않습니다.

## 반환 형식

**New-CsDialInConferencingAccessNumber** cmdlet은 Microsoft.Rtc.Management.Xds.AccessNumber 개체의 새 인스턴스를 만듭니다.

## 참고 항목

#### 기타 리소스

[Get-CsDialInConferencingAccessNumber](get-csdialinconferencingaccessnumber.md)  
[Remove-CsDialInConferencingAccessNumber](remove-csdialinconferencingaccessnumber.md)  
[Set-CsDialInConferencingAccessNumber](set-csdialinconferencingaccessnumber.md)

