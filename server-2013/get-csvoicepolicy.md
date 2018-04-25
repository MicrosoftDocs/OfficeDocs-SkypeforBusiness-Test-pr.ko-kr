---
title: Get-CsVoicePolicy
TOCTitle: Get-CsVoicePolicy
ms:assetid: 05096aec-321c-4a50-99be-6e9fbbbe17fa
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg398101(v=OCS.15)
ms:contentKeyID: 49302670
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Get-CsVoicePolicy

 

_**마지막으로 수정된 항목:** 2015-03-09_

조직에 대해 구성된 하나 이상의 음성 정책에 대한 정보를 반환합니다. 이 cmdlet은 Lync Server 2010에서 도입되었습니다.

## 구문

    Get-CsVoicePolicy [-Identity <XdsIdentity>] <COMMON PARAMETERS>

    Get-CsVoicePolicy [-Filter <String>] <COMMON PARAMETERS>

    COMMON PARAMETERS: [-LocalStore <SwitchParameter>] [-Tenant <Guid>]

## 예제

## 예제 1

이 예제에서는 조직에 대해 정의된 모든 음성 정책을 각각에 대한 설정과 함께 표시합니다.

    Get-CsVoicePolicy

## 예제 2

이 예제에서는 Identity 매개 변수를 사용하여 UserPolicy1이라는 사용자별 정책에 대한 음성 정책 설정을 검색합니다.

    Get-CsVoicePolicy -Identity UserPolicy1

## 예제 3

이 예제에서는 Filter 매개 변수를 사용하여 사용자에게 할당할 수 있는 모든 음성 정책 설정을 검색합니다. 모든 사용자별 음성 정책은 **tag:\<UserVoicePolicy\>** 형식의 Identity를 가지므로 태그를 필터링하여 모든 사용자 음성 정책을 검색합니다.

    Get-CsVoicePolicy -Filter tag*

## 자세한 정보

이 cmdlet은 음성 정책 정보를 검색합니다. 음성 정책은 동시 벨 울림(누군가가 사무실 전화에 전화를 걸 때마다 또 다른 전화에서 벨이 울리는 기능) 및 착신 전환과 같은 Enterprise Voice 관련 기능을 관리하는 데 사용됩니다. 이 cmdlet을 사용하여 이러한 대부분의 기능을 활성화 및 비활성화하는 설정을 검색합니다.

이 cmdlet을 실행할 수 있는 사용자: 기본적으로 RTCUniversalUserAdmins 및 RTCUniversalServerAdmins 그룹의 구성원은 **Get-CsVoicePolicy** cmdlet을 로컬로 실행할 수 있습니다. 사용자가 직접 만든 사용자 지정 RBAC(역할 기반 액세스 제어) 역할을 포함하여 이 cmdlet이 할당된 모든 RBAC 역할의 목록을 반환하려면 Windows PowerShell 프롬프트에서 다음 명령을 실행합니다.

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Get-CsVoicePolicy"}

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
<td><p>이 매개 변수에는 와일드카드 문자열이 허용되며 해당 문자열과 일치하는 ID를 가진 모든 음성 정책이 반환됩니다. 예를 들어, Filter 값 site:*는 사이트 수준에서 정의된 모든 음성 정책을 반환합니다.</p></td>
</tr>
<tr class="even">
<td><p><em>Identity</em></p></td>
<td><p>선택</p></td>
<td><p>Microsoft.Rtc.Management.Xds.XdsIdentity</p></td>
<td><p>정책의 범위나 경우에 따라서는 이름을 지정하는 고유한 식별자입니다. 이 매개 변수가 생략된 경우 조직의 모든 음성 정책이 반환됩니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>LocalStore</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>중앙 관리 저장소 자체가 아니라 중앙 관리 저장소의 로컬 복제본에서 음성 정책을 검색합니다.</p></td>
</tr>
<tr class="even">
<td><p><em>Tenant</em></p></td>
<td><p>선택</p></td>
<td><p>System.Guid</p></td>
<td><p>해당 음성 정책을 검색할 비즈니스용 Skype Online 테넌트 계정의 GUID(Globally Unique Identifier)입니다. 예를 들면 다음과 같습니다.</p>
<p>–Tenant &quot;38aad667-af54-4397-aaa7-e94c79ec2308&quot;</p>
<p>다음 명령을 실행하여 각 테넌트에 대해 테넌트 ID를 반환할 수 있습니다.</p>
<p>Get-CsTenant | Select-Object DisplayName, TenantID</p>
<p>Windows PowerShell의 원격 세션을 사용 중이고 비즈니스용 Skype Online에만 연결되는 경우 Tenant 매개 변수를 포함하지 않아도 됩니다. 대신, 연결 정보에 따라 테넌트 ID가 자동으로 채워집니다. Tenant 매개 변수는 하이브리드 배포에서 주로 사용됩니다.</p></td>
</tr>
</tbody>
</table>


## 입력 형식

없음.

## 반환 형식

이 cmdlet은 Microsoft.Rtc.Management.WritableConfig.Policy.Voice.VoicePolicy 개체의 인스턴스를 반환합니다.

## 참고 항목

#### 기타 리소스

[New-CsVoicePolicy](new-csvoicepolicy.md)  
[Remove-CsVoicePolicy](remove-csvoicepolicy.md)  
[Set-CsVoicePolicy](set-csvoicepolicy.md)  
[Grant-CsVoicePolicy](grant-csvoicepolicy.md)  
[Test-CsVoicePolicy](test-csvoicepolicy.md)

