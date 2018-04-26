---
title: Get-CsMediaConfiguration
TOCTitle: Get-CsMediaConfiguration
ms:assetid: 071c1733-07c3-4075-8745-367634e37941
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg398128(v=OCS.15)
ms:contentKeyID: 49302702
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Get-CsMediaConfiguration

 

_**마지막으로 수정된 항목:** 2015-03-09_

지원되는 암호화 수준, Lync Server 클라이언트와 상호 작용할 때 중재 서버에서 Siren을 음성 코덱으로 사용할 수 있는지 여부, 허용되는 최대 비디오 해상도를 포함하여 미디어 설정에 대한 정보를 반환합니다. 이 cmdlet은 Lync Server 2010에서 도입되었습니다.

## 구문

    Get-CsMediaConfiguration [-Identity <XdsIdentity>] <COMMON PARAMETERS>

    Get-CsMediaConfiguration [-Filter <String>] <COMMON PARAMETERS>

    COMMON PARAMETERS: [-LocalStore <SwitchParameter>]

## 예제

## 예제 1

예제 1에서는 추가 매개 변수 없이 **Get-CsMediaConfiguration** cmdlet을 호출하여 조직에서 사용 중인 모든 미디어 구성을 반환합니다.

    Get-CsMediaConfiguration

## 예제 2

예제 2에서는 ID가 site:Redmond1인 미디어 구성만 반환합니다. ID가 고유해야 하므로 ID를 지정하면 둘 이상의 항목이 검색되지 않습니다.

    Get-CsMediaConfiguration -Identity site:Redmond1

## 예제 3

예제 3에서는 사이트 범위의 모든 미디어 구성을 반환하기 위해 Filter 매개 변수를 사용합니다. 와일드카드 문자열 site:\*는 Windows PowerShell에서 문자열 값 site:로 시작하는 ID를 가진 미디어 구성만 반환하게 합니다.

    Get-CsMediaConfiguration -Filter site:*

## 예제 4

위 예제에서는 **Get-CsMediaConfiguration** cmdlet 및 **Where-Object** cmdlet을 사용하여 암호화를 지원하지만 요구하지는 않는 모든 미디어 구성을 반환합니다. 이를 수행하기 위해 먼저 **Get-CsMediaConfiguration** cmdlet을 사용하여 조직에서 사용할 모든 미디어 구성을 검색합니다. 그런 다음, 반환되는 데이터를 EncryptionLevel 속성이 SupportEncryption과 동일(-eq)한 구성으로 제한하는 필터가 적용되는 **Where-Object** cmdlet에 이 정보가 파이프됩니다.

    Get-CsMediaConfiguration | Where-Object {$_.EncryptionLevel -eq "SupportEncryption"}

## 예제 5

이 예제에서는 문자열 "med"가 이름에 포함된 사이트 및 서비스에 정의된 모든 미디어 구성을 검색합니다. 예를 들어 이 명령은 medford1 사이트, TwoMedfordPlace 사이트 및 MediationServer:redmond.litwareinc.com 서비스에 대해 정의된 미디어 구성 설정을 검색합니다.

    Get-CsMediaConfiguration -Filter *:*med*

## 자세한 정보

이 cmdlet은 미디어 상호 작용을 정의하는 설정 컬렉션을 하나 이상 검색합니다.

이 cmdlet을 실행할 수 있는 사용자: 기본적으로 RTCUniversalUserAdmins 및 RTCUniversalServerAdmins 그룹의 구성원은 **Get-CsMediaConfiguration** cmdlet을 로컬로 실행할 수 있습니다. 사용자가 직접 만든 사용자 지정 RBAC(역할 기반 액세스 제어) 역할을 포함하여 이 cmdlet이 할당된 모든 RBAC 역할의 목록을 반환하려면 Windows PowerShell 프롬프트에서 다음 명령을 실행합니다.

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Get-CsMediaConfiguration"}

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
<td><p><em>Filter</em></p></td>
<td><p>선택</p></td>
<td><p>System.String</p></td>
<td><p>이 매개 변수는 이 매개 변수에 전달된 와일드카드 값에 기초하여 Get 작업의 결과를 필터링합니다.</p></td>
</tr>
<tr class="even">
<td><p><em>Identity</em></p></td>
<td><p>선택</p></td>
<td><p>Microsoft.Rtc.Management.Xds.XdsIdentity</p></td>
<td><p>검색할 미디어 구성의 고유 식별자입니다. 이 식별자는 이 구성이 적용되는 범위(전역, 사이트 또는 서비스)를 지정합니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>LocalStore</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>중앙 관리 저장소 자체가 아니라 중앙 관리 저장소의 로컬 복제본에서 미디어 구성 정보를 검색합니다.</p></td>
</tr>
</tbody>
</table>


## 입력 형식

없음.

## 반환 형식

**Get-CsMediaConfiguration** cmdlet은 Microsoft.Rtc.Management.WritableConfig.Settings.Media.MediaSettings 개체의 인스턴스를 반환합니다.

## 참고 항목

#### 기타 리소스

[New-CsMediaConfiguration](new-csmediaconfiguration.md)  
[Remove-CsMediaConfiguration](remove-csmediaconfiguration.md)  
[Set-CsMediaConfiguration](set-csmediaconfiguration.md)

