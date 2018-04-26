---
title: Get-CsHostedVoicemailPolicy
TOCTitle: Get-CsHostedVoicemailPolicy
ms:assetid: 52dd4397-b1c5-44a5-a744-75d715a4511b
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg398348(v=OCS.15)
ms:contentKeyID: 49303639
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Get-CsHostedVoicemailPolicy

 

_**마지막으로 수정된 항목:** 2015-03-09_

호스트된 음성 메일 정책을 검색합니다. 이 cmdlet은 Lync Server 2010에서 도입되었습니다.

## 구문

    Get-CsHostedVoicemailPolicy [-Identity <XdsIdentity>] <COMMON PARAMETERS>

    Get-CsHostedVoicemailPolicy [-Filter <String>] <COMMON PARAMETERS>

    COMMON PARAMETERS: [-LocalStore <SwitchParameter>] [-Tenant <Guid>]

## 예제

## 예제 1

이 명령은 Lync Server 구현에 정의된 모든 호스트된 음성 메일 정책을 반환합니다.

    Get-CsHostedVoicemailPolicy

## 예제 2

이 명령은 사용자별 호스트된 음성 메일 정책 ExRedmond에 대한 정책 설정을 반환합니다.

    Get-CsHostedVoicemailPolicy -Identity ExRedmond

## 예제 3

이 명령은 모든 사용자별 호스트된 음성 메일 정책(태그 범위로 시작하는 정책)에 대한 정책 설정을 반환합니다.

    Get-CsHostedVoicemailPolicy -Filter tag:*

## 예제 4

이 명령은 테넌트 ID 73d355dd-ce5d-4ab9-bf49-7b822c18dd98의 Lync Online 테넌트에 대해 호스트된 음성 사서함 정책을 반환합니다.

    Get-CsHostedVoicemailPolicy -Tenant "73d355dd-ce5d-4ab9-bf49-7b822c18dd98"

## 자세한 정보

이 cmdlet은 사용자에 대한 응답하지 않은 통화를 호스트된 Exchange 통합 메시징(UM) 서비스에 경로 지정하는 방법을 지정하는 정책을 검색합니다.

이 정책을 적용하려면 사용자는 Exchange UM 호스트된 음성 메일에 대해 활성화되어야 합니다. **Get-CsUser** cmdlet을 호출하고 HostedVoiceMail 속성을 검사하여 사용자가 호스트된 음성 메일에 대해 활성화되었는지 여부를 확인할 수 있습니다. (True 값은 사용자가 활성화되었다는 것을 의미합니다.)

이 cmdlet을 실행할 수 있는 사용자: 기본적으로 RTCUniversalUserAdmins 및 RTCUniversalServerAdmins 그룹의 구성원은 **Get-CsHostedVoicemailPolicy** cmdlet을 로컬로 실행할 수 있습니다. 사용자가 직접 만든 사용자 지정 RBAC(역할 기반 액세스 제어) 역할을 포함하여 이 cmdlet이 할당된 모든 RBAC 역할의 목록을 반환하려면 Windows PowerShell 프롬프트에서 다음 명령을 실행합니다.

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Get-CsHostedVoicemailPolicy"}

``` 
```

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
<td><p>이 매개 변수를 사용하면 호스트된 음성 메일 정책의 ID에 대한 와일드카드 검색을 수행할 수 있습니다. 이 경우 ID가 Filter 값에 지정된 와일드카드 패턴과 일치하는 호스트된 음성 메일 정책의 모든 인스턴스가 검색됩니다.</p></td>
</tr>
<tr class="even">
<td><p><em>Identity</em></p></td>
<td><p>선택</p></td>
<td><p>Microsoft.Rtc.Management.Xds.XdsIdentity</p></td>
<td><p>검색할 호스트된 음성 메일 정책에 대한 고유한 식별자입니다. 이 ID는 범위(전역의 경우), 범위 및 사이트(사이트 정책의 경우, 예: site:Redmond) 또는 정책 이름(사용자별 정책의 경우, 예: HVUserPolicy)을 포함합니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>LocalStore</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>중앙 관리 저장소 자체가 아니라 중앙 관리 저장소의 로컬 복제본에서 호스트된 음성 메일 정책을 검색합니다.</p></td>
</tr>
<tr class="even">
<td><p><em>Tenant</em></p></td>
<td><p>선택</p></td>
<td><p>System.Guid</p></td>
<td><p>해당 음성 메일 정책을 검색할 비즈니스용 Skype Online 테넌트 계정의 GUID(Globally Unique Identifier)입니다.</p>
<p>예를 들면 다음과 같습니다.</p>
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

이 cmdlet은 Microsoft.Rtc.Management.WritableConfig.Policy.Voice.HostedVoicemailPolicy 유형의 개체를 반환합니다.

## 참고 항목

#### 기타 리소스

[New-CsHostedVoicemailPolicy](new-cshostedvoicemailpolicy.md)  
[Remove-CsHostedVoicemailPolicy](remove-cshostedvoicemailpolicy.md)  
[Set-CsHostedVoicemailPolicy](set-cshostedvoicemailpolicy.md)  
[Grant-CsHostedVoicemailPolicy](grant-cshostedvoicemailpolicy.md)

