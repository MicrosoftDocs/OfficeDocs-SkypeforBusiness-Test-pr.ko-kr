---
title: Get-CsAudioTestServiceApplication
TOCTitle: Get-CsAudioTestServiceApplication
ms:assetid: ef36a059-bf9b-4066-a817-db8d82c41e49
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg412984(v=OCS.15)
ms:contentKeyID: 49305459
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Get-CsAudioTestServiceApplication

 

_**마지막으로 수정된 항목:** 2015-03-09_

조직에서 사용 중인 오디오 테스트 서비스 응용 프로그램에 대한 정보를 반환할 수 있습니다. 이 cmdlet은 Lync Server 2010에서 도입되었습니다.

## 구문

    Get-CsAudioTestServiceApplication [-Identity <UserIdParameter>] [-Credential <PSCredential>] [-DomainController <Fqdn>] [-Filter <String>] [-OU <OUIdParameter>] [-ResultSize <Unlimited>]

## 예제

## 예제 1

예제 1에서는 **Get-CsAudioTestServiceApplication** cmdlet을 추가 매개 변수 없이 호출하여 조직에서 현재 사용되고 있는 모든 오디오 테스트 서비스 연락처의 컬렉션을 반환합니다.

    Get-CsAudioTestServiceApplication

## 예제 2

예제 2에서는 ID sip:RedmondAudioTest@litwareinc.com이 포함된 단일 오디오 테스트 서비스 연락처를 반환합니다.

    Get-CsAudioTestServiceApplication -Identity "sip:RedmondAudioTest@litwareinc.com"

## 예제 3

예제 3은 표시 이름에 문자열 값 "Redmond"가 포함된 모든 오디오 테스트 서비스 연락처를 반환합니다. 이 작업을 수행하기 위해 명령은 Filter 매개 변수 및 필터 값 {DisplayName –like "\*Redmond\*"}를 사용합니다. 해당 필터 값은 반환되는 데이터를 표시 이름에 문자열 값 "Redmond"가 포함된 연락처로 제한합니다. 이 명령은 표시 이름이 "Redmond Audio Test Service Contact", "Redmond Audio Bot" 및 "Test Contact for Redmond"와 같은 연락처를 반환합니다.

    Get-CsAudioTestServiceApplication -Filter {DisplayName -like "*Redmond*"}

## 자세한 정보

Lync Server 사용자는 오디오 테스트 서비스를 사용하여 음성 통화를 시작하기 전에 음성 연결을 테스트할 수 있습니다. 이렇게 하려면 Lync Server 옵션 대화 상자의 오디오 장치 탭에 있는 통화 품질 확인 단추를 클릭합니다. 사용자가 이 단추를 클릭하면 자동화된 오디오 테스트 서비스와 통화가 이루어집니다. 통화에 대한 응답이 제공되고 간단한 안내 메시지가 재생된 후 발신자에게 간단한 메시지를 녹음하라는 안내가 나옵니다. 메시지를 녹음하고 나면 발신자가 현재 연결을 통해 해당 메시지를 들을 수 있도록 녹음된 메시지가 재생됩니다.

오디오 테스트 서비스는 Active Directory 연락처 개체에 부분적으로 의존합니다. 이러한 개체는 Audio Bot를 설치하면 자동으로 만들어집니다. 이러한 개체를 수동으로 만들 수 있는 방법은 없습니다. 그러나 관리자는 **Get-CsAudioTestServiceApplication** cmdlet을 사용하여 조직에서 현재 사용되고 있는 다양한 테스트 서비스 연락처에 대한 정보를 검색할 수 있습니다. 관리자는 또한 **Set-CsAudioTestServiceApplication**을 사용하여 이러한 연락처의 속성을 수정할 수 있습니다.

이 cmdlet을 실행할 수 있는 사용자: 기본적으로 RTCUniversalUserAdmins, RTCUniversalServerAdmins, RTCUniversalReadOnlyAdmins 그룹의 구성원은 **Get-CsAudioTestServiceApplication** cmdlet을 로컬로 실행할 수 있습니다. 사용자가 직접 만든 사용자 지정 RBAC(역할 기반 액세스 제어) 역할을 포함하여 이 cmdlet이 할당된 모든 RBAC 역할의 목록을 반환하려면 Windows PowerShell 프롬프트에서 다음 명령을 실행합니다.

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Get-CsAudioTestServiceApplication"}

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
<td><p>대체 자격 증명으로 cmdlet을 실행할 수 있습니다. Windows에 로그온하는 데 사용한 계정에 연락처 개체를 사용하는 데 필요한 권한이 없는 경우 이 기능이 필요할 수 있습니다.</p>
<p>Credential 매개 변수를 사용하려면 먼저 <strong>Get-Credential</strong> cmdlet을 사용하여 PSCredential 개체를 만들어야 합니다. 자세한 내용은 <strong>Get-Credential</strong> cmdlet 도움말 항목을 참조하십시오.</p></td>
</tr>
<tr class="even">
<td><p><em>DomainController</em></p></td>
<td><p>선택</p></td>
<td><p>Microsoft.Rtc.Management.Deploy.Fqdn</p></td>
<td><p>대화 상대 정보를 검색하기 위해 지정된 도메인 컨트롤러에 연결하는 데 사용됩니다. 특정 도메인 컨트롤러에 연결하려면 DomainController 매개 변수 뒤에 컴퓨터 이름(예: atl-cs-001) 또는 FQDN(정규화된 도메인 이름)(예: atl-cs-001.litwareinc.com)을 포함합니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>Filter</em></p></td>
<td><p>선택</p></td>
<td><p>System.String</p></td>
<td><p>Lync Server 관련 특성을 필터링하여 반환되는 데이터를 제한할 수 있습니다. 예를 들어 반환된 데이터를 특정 표시 이름이 있거나 특정 언어를 사용하는 오디오 테스트 연락처 개체로 제한할 수 있습니다.</p>
<p>Filter 매개 변수는 <strong>Where-Object</strong> cmdlet에 사용되는 것과 동일한 Windows PowerShell 필터링 구문을 사용합니다. 예를 들어 표시 이름이 Audio Test Service Contacts인 연락처만 반환하는 필터는 다음과 유사한 형태입니다.여기서 -eq는 비교 연산자(같음)를 나타내고 &quot;Audio Test Service Contact&quot;는 필터 값을 나타냅니다.</p>
<p>-Filter {DisplayName -eq &quot;Audio Test Service Contact&quot;}</p>
<p>Filter 매개 변수와 Identity 매개 변수를 같은 명령에 함께 사용할 수 없습니다.</p></td>
</tr>
<tr class="even">
<td><p><em>Identity</em></p></td>
<td><p>선택</p></td>
<td><p>Microsoft.Rtc.Management.AD.UserIdParameter</p></td>
<td><p>오디오 테스트 서비스 연락처의 SIP 주소입니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>OU</em></p></td>
<td><p>선택</p></td>
<td><p>Microsoft.Rtc.Management.AD.OUIdParameter</p></td>
<td><p>특정 Active Directory OU(조직 구성 단위)에서 연락처를 반환하는 데 사용됩니다. OU 매개 변수는 지정한 OU 및 모든 하위 OU의 데이터를 반환합니다. 예를 들어, Finance OU에 두 개의 하위 OU인 AccountsPayable 및 AccountsReceivable이 있는 경우 이러한 세 개의 각 OU에서 사용자가 반환됩니다.</p>
<p>OU를 지정할 때는 해당 컨테이너에 대한 DN(고유 이름)을 사용합니다(예: -OU &quot;OU=Finance,dc=litwareinc,dc=com&quot;).</p></td>
</tr>
<tr class="even">
<td><p><em>ResultSize</em></p></td>
<td><p>선택</p></td>
<td><p>Microsoft.Rtc.Management.ADConnect.Core.Unlimited</p></td>
<td><p>명령에서 반환되는 레코드 수를 제한할 수 있게 합니다. 예를 들어, 포리스트에 있는 사용자 수에 상관없이 7명의 사용자만 반환하려면 ResultSize 매개 변수를 포함하고 매개 변수 값을 7로 설정합니다. 반환될 7명의 사용자를 지정하는 방법은 없습니다. ResultSize를 7로 설정했지만 포리스트에 사용자가 3명만 있는 경우 3명의 사용자가 반환된 다음, 오류 없이 완료됩니다.</p>
<p>결과 크기는 0-2147483647(포함) 사이의 임의 정수로 설정할 수 있습니다. 0으로 설정할 경우 명령이 실행되지만 데이터가 반환되지 않습니다.</p></td>
</tr>
</tbody>
</table>


## 입력 형식

없음.

## 반환 형식

**Get-CsAudioTestServiceApplication** cmdlet은 Microsoft.Rtc.Management.ADConnect.Schema.OCSADApplicationContact 개체의 인스턴스를 반환합니다.

## 참고 항목

#### 기타 리소스

[Set-CsAudioTestServiceApplication](set-csaudiotestserviceapplication.md)

