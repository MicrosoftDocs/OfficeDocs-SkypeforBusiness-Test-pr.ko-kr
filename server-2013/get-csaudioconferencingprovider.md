---
title: Get-CsAudioConferencingProvider
TOCTitle: Get-CsAudioConferencingProvider
ms:assetid: 4632e9d0-aa87-459f-ad7e-27125c11da5b
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/JJ994030(v=OCS.15)
ms:contentKeyID: 52056828
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Get-CsAudioConferencingProvider

 

_**마지막으로 수정된 항목:** 2015-03-09_

조직에서 사용하도록 허가된 오디오 회의 공급자에 대한 정보를 반환합니다. 오디오 회의 공급자는 조직에 회의 서비스를 제공하는 타회사입니다.

**Get-CsAudioConferencingProvider** cmdlet은 Microsoft Lync Online에서만 사용할 수 있습니다.

## 구문

    Get-CsAudioConferencingProvider [[-Identity] <XdsGlobalRelativeIdentity>] [-LocalStore][<CommonParameters>]Get-CsAudioConferencingProvider [-Filter <string>] [-LocalStore] [<CommonParameters>]

## 예제

## 예제 1

예제 1에 표시된 명령은 조직에서 사용할 수 있는 모든 오디오 회의 공급자에 대한 정보를 반환합니다.

    Get-CsAudioConferencingProvider

## 예제 2

예제 2에서는 ID가 Fabrikam Telecom인 단일 오디오 회의 공급자에 대한 정보를 반환합니다.

    Get-CsAudioConferencingProvider -Identity "Fabrikam Telecom"

## 예제 3

예제 3에서는 와일드카드 값(및 Filter 매개 변수)을 사용하여 오디오 회의 공급자에 대한 정보를 반환할 수 있는 방법을 보여줍니다. 이 예제에서 필터 값 "\*Fabrikam\*"는 ID의 어느 위치에든 문자열 값 "Fabrikam"이 있는 모든 오디오 회의 공급자를 반환합니다.

    Get-CsAudioConferencingProvider -Filter "*Fabrikam*"

## 자세한 정보

오디오 회의 공급자는 조직에 회의 서비스를 제공하는 타회사입니다. 특히, 외부에 있거나 회사 네트워크 또는 인터넷에 연결되지 않은 사용자는 오디오 회의 공급자를 통해 회의 또는 모임의 오디오 부분에 참여할 수 있습니다. 오디오 회의 공급자는 실시간 번역, 기록 및 회의별 실시간 운영자 지원과 같은 최고의 서비스를 제공합니다.

조직이 오디오 회의 공급자와 계약을 맺은 후에는 **Set-CsUserAcp** cmdlet을 사용하여 사용자를 해당 공급자에 할당할 수 있습니다. 관리자는 **Get-CsAudioConferencingProvider** cmdlet을 사용하여 사용 가능한 오디오 회의 공급자에 대한 정보를 검색할 수 있습니다.

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
<td><p>반환할 하나 이상의 오디오 회의 공급자를 나타낼 때 와일드카드 문자를 사용할 수 있도록 합니다. 예를 들어 다음 구문은 ID의 어느 위치에든 문자열 값 &quot;fabrikam&quot;이 있는 모든 오디오 회의 공급자에 대한 정보를 반환합니다.</p>
<p>-Filter &quot;*fabrikam*&quot;</p>
<p>Filter 매개 변수와 Identity 매개 변수를 같은 명령에 함께 사용할 수 없습니다.</p></td>
</tr>
<tr class="even">
<td><p><em>Identity</em></p></td>
<td><p>선택</p></td>
<td><p>Microsoft.Rtc.Management.Xds.XdsGlobalRelativeIdentity</p></td>
<td><p>반환할 오디오 회의 공급자의 고유 식별자입니다. 예를 들면 다음과 같습니다.</p>
<p>-Identity &quot;Fabrikam Telecom&quot;</p>
<p>Identity 매개 변수와 Filter 매개 변수를 모두 명령에 포함하지 않으면 <strong>Get-CsAudioConferencingProvider</strong> cmdlet은 사용 가능한 모든 공급자에 대한 정보를 반환합니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>LocalStore</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>중앙 관리 저장소 자체가 아니라 중앙 관리 저장소의 로컬 복제본에서 오디오 회의 공급자 데이터를 검색합니다.</p></td>
</tr>
</tbody>
</table>


## 입력 형식

없음. **Get-CsAudioConferencingProvider** cmdlet은 파이프라인된 입력을 허용하지 않습니다.

## 반환 형식

**Get-CsAudioConferencingProvider** cmdlet은 Microsoft.Rtc.Management.WritableConfig.Settings.AudioConferencingProvider.AudioConferencingProvider\#Decorated 개체의 인스턴스를 반환합니다.

## 참고 항목

#### 기타 리소스

[Get-CsUserAcp](get-csuseracp.md)  
[Remove-CsUserAcp](remove-csuseracp.md)  
[Set-CsUserAcp](set-csuseracp.md)

