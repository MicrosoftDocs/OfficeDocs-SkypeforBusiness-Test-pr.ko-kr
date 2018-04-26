---
title: Get-CsConferencingPolicy
TOCTitle: Get-CsConferencingPolicy
ms:assetid: 21dc4774-2306-4425-a561-71e0b293f8df
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg398293(v=OCS.15)
ms:contentKeyID: 49303041
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Get-CsConferencingPolicy

 

_**마지막으로 수정된 항목:** 2015-03-09_

조직에서 사용하도록 구성된 전화 회의 정책에 대한 정보를 반환합니다. 전화 회의 정책은 전화 회의에서 사용할 수 있는 기능을 결정합니다. 여기에는 전화 회의에 IP 오디오 및 비디오를 포함할 수 있는지 여부에서 모임에 참석할 수 있는 최대 사용자 수에 이르기까지 모든 기능이 포함됩니다. 이 cmdlet은 Lync Server 2010에서 도입되었습니다.

## 구문

    Get-CsConferencingPolicy [-Identity <XdsIdentity>] [[-ApplicableTo] <Object>] <COMMON PARAMETERS>

    Get-CsConferencingPolicy [-Filter <String>] [[-ApplicableTo] <Object>] <COMMON PARAMETERS>

    COMMON PARAMETERS: [-LocalStore <SwitchParameter>]

## 예제

## 예제 1

예제 1에서는 조직에서 사용하도록 구성된 모든 전화 회의 정책의 컬렉션을 반환합니다.

    Get-CsConferencingPolicy

## 예제 2

예제 2에서는 Identity 매개 변수를 사용하여 Identity가 Global인 전화 회의 정책만 검색되도록 제한합니다. 정책 ID는 고유해야 하므로 이 명령은 Global 전화 회의 정책이라는 단일 정책을 반환합니다.

    Get-CsConferencingPolicy -Identity Global

## 예제 3

예제 3에서는 Filter 매개 변수를 사용하여 사용자별 범위에서 구성된 모든 전화 회의 정책 컬렉션을 반환합니다. 와일드카드 값 "tag:\*"를 사용하면 Windows PowerShell에서 ID가 문자열 값 tag:으로 시작하는 전화 회의 정책에 대한 데이터만 반환되도록 제한합니다.

    Get-CsConferencingPolicy -Filter tag:*

## 예제 4

예제 4에서는 MaxMeetingSize 속성이 100보다 큰 모든 전화 회의 정책 컬렉션을 반환합니다. 먼저 조직에서 사용하도록 구성된 모든 전화 회의 정책 컬렉션을 반환하기 위해 **Get-CsConferencingPolicy** cmdlet이 사용됩니다. 이 컬렉션은 MaxMeetingSize 속성이 100보다 큰 정책에 대한 데이터만 반환되도록 제한하는 필터가 적용된 **Where-Object** cmdlet에 파이프됩니다.

    Get-CsConferencingPolicy | Where-Object {$_.MaxMeetingSize -gt 100}

## 예제 5

예제 5에서는 AllowExternalUsersToSaveContent 속성이 True이고 AllowExternalUserControl 속성도 True인 조건을 충족하는 모든 전화 회의 정책을 반환합니다. 이 작업을 수행하기 위해 추가 매개 변수 없이 **Get-CsConferencingPolicy** cmdlet을 호출합니다. 이렇게 하면 조직에서 사용하도록 구성된 모든 전화 회의 정책 컬렉션이 반환됩니다. 이 컬렉션은 AllowExternalUsersToSaveContent 및 AllowExternalUserControl이 모두 True인 정책만 선택하는 **Where-Object** cmdlet에 파이프됩니다. -and 연산자는 개체가 지정한 조건을 모두 충족해야 반환되도록 **Where-Object** cmdlet에 지시합니다.

    Get-CsConferencingPolicy | Where-Object {$_.AllowExternalUsersToSaveContent -eq $True -and $_.AllowExternalUserControl -eq $True}

## 예제 6

예제 6은 예제 5에 표시된 명령의 변형입니다. 이 경우에는 명령에서 AllowExternalUsersToSaveContent 속성이 True와 같거나 그리고/또는 AllowExternalUserControl 속성이 True와 같은 조건을 충족하는(둘 다 충족하지 않아도 됨) 모든 정책을 반환합니다. 이 작업을 수행하기 위해 추가 매개 변수 없이 **Get-CsConferencingPolicy** cmdlet을 호출합니다. 이렇게 하면 조직에서 사용하도록 구성된 모든 전화 회의 정책 컬렉션이 반환됩니다. 이 컬렉션은 AllowExternalUsersToSaveContent 및/또는 AllowExternalUserControl이 True인 정책만 선택하는 **Where-Object** cmdlet에 파이프됩니다. -or 연산자는 개체가 지정한 조건 중 한 개만 충족하면 반환되도록 **Where-Object** cmdlet에 지시합니다.

    Get-CsConferencingPolicy | Where-Object {$_.AllowExternalUsersToSaveContent -eq $True -or $_.AllowExternalUserControl -eq $True}

## 자세한 정보

전화 회의는 Lync Server의 중요한 부분입니다. 전화 회의 기능을 사용하면 사용자 그룹이 온라인으로 모여 슬라이드 및 비디오 보기, 응용 프로그램 공유, 파일 교환, 기타 통신 및 공동 작업 등을 수행할 수 있기 때문입니다.

관리자가 전화 회의 및 전화 회의 설정에 대한 제어를 유지 관리하는 기능도 중요합니다. 경우에 따라 보안 문제가 발생할 수 있습니다. 기본적으로 인증되지 않은 사용자를 비롯한 모든 사용자가 모임에 참가하고 모임 중에 배포된 슬라이드나 유인물을 저장할 수 있습니다. 대역폭 문제가 발생하는 경우도 있습니다. 예를 들어 동시 모임 수가 많은 경우, 각 모임에 수백 명의 참가자가 있는 경우 및 각 모임에서 화상 공급 및 파일 공유를 사용하는 경우에 네트워크에 문제가 발생할 수 있습니다. 또한 법적인 문제가 발생할 수 있습니다. 예를 들어 모임 참가자는 기본적으로 공유 콘텐츠에 주석을 추가할 수 있지만 이러한 주석은 모임을 보관할 때 저장되지 않습니다. 조직에서 모든 전자 통신의 기록을 보관해야 하는 경우 주석을 사용하지 않도록 설정할 수 있습니다.

물론 전화 회의 설정을 관리해야 하는 것도 중요한 사항입니다. 실제로 이러한 설정을 관리하는 것은 또 다른 문제입니다. Lync Server에서는 전화 회의 정책을 사용하여 전화 회의를 관리합니다. 이전 버전의 소프트웨어에서는 이러한 정책을 모임 정책이라고 했습니다. 앞서 언급한 것처럼 전화 회의 정책은 전화 회의에서 사용할 수 있는 기능을 결정하며, 여기에는 전화 회의에 IP 오디오 및 비디오를 포함할 수 있는지 여부부터 모임에 참가할 수 있는 최대 사용자 수에 이르기까지 모든 기능이 포함됩니다. 전화 회의 정책은 전역 범위, 사이트 범위 또는 사용자별 범위에서 구성할 수 있습니다. 따라서 각 사용자가 사용할 수 있는 기능을 관리자가 유동적으로 결정할 수 있습니다.

**Get-CsConferencingPolicy** cmdlet을 통해 조직에서 사용하도록 구성된 모든 전화 회의 정책에 대한 정보를 가져올 수 있습니다.

이 cmdlet을 실행할 수 있는 사용자: 기본적으로 RTCUniversalUserAdmins 및 RTCUniversalServerAdmins 그룹의 구성원은 **Get-CsConferencingPolicy** cmdlet을 로컬로 실행할 수 있습니다. 사용자가 직접 만든 사용자 지정 RBAC(역할 기반 액세스 제어) 역할을 포함하여 이 cmdlet이 할당된 모든 RBAC 역할의 목록을 반환하려면 Windows PowerShell 프롬프트에서 다음 명령을 실행합니다.

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Get-CsConferencingPolicy"}

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
<td><p>반환할 전화 회의 정책을 지정할 때 와일드카드 문자를 사용할 수 있습니다. 예를 들어 사이트 범위에서 구성된 모든 정책을 반환하려면 -Filter &quot;site:*&quot; 구문을 사용합니다. 사용자별 범위에서 구성된 모든 정책 컬렉션을 반환하려면 -Filter tag:* 구문을 사용합니다.</p></td>
</tr>
<tr class="even">
<td><p><em>Identity</em></p></td>
<td><p>선택</p></td>
<td><p>Microsoft.Rtc.Management.Xds.XdsIdentity</p></td>
<td><p>검색할 전화 회의 정책의 고유 식별자입니다. 전화 회의 정책은 전역, 사이트 또는 사용자별 범위에서 구성할 수 있습니다. 전역 정책을 검색하려면 -Identity global 구문을 사용합니다. 사이트 정책을 검색하려면 -Identity site:Redmond와 유사한 구문을 사용합니다. 사용자별 정책을 검색하려면 -Identity SalesConferencingPolicy와 유사한 구문을 사용합니다.</p>
<p>이 매개 변수를 포함하지 않으면 <strong>Get-CsConferencingPolicy</strong> cmdlet은 조직에서 사용하도록 구성된 모든 전화 회의 정책 컬렉션을 반환합니다.</p>
<p>ID를 지정할 때는 와일드카드를 사용할 수 없습니다. 전화 회의 정책을 지정할 때 와일드카드를 사용하려면 -Filter 매개 변수를 사용합니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>LocalStore</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>중앙 관리 저장소 자체가 아니라 중앙 관리 저장소의 로컬 복제본에서 전화 회의 정책 데이터를 검색합니다.</p></td>
</tr>
</tbody>
</table>


## 입력 형식

없음. **Get-CsConferencingPolicy** cmdlet은 파이프라인된 입력을 허용하지 않습니다.

## 반환 형식

**Get-CsConferencingPolicy** cmdlet은 Microsoft.Rtc.Management.WritableConfig.Settings.Meeting.MeetingPolicy 개체의 인스턴스를 반환합니다.

## 참고 항목

#### 기타 리소스

[Grant-CsConferencingPolicy](grant-csconferencingpolicy.md)  
[New-CsConferencingPolicy](new-csconferencingpolicy.md)  
[Remove-CsConferencingPolicy](remove-csconferencingpolicy.md)  
[Set-CsConferencingPolicy](set-csconferencingpolicy.md)

