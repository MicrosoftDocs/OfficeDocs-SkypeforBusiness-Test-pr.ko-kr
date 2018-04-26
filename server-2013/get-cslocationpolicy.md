---
title: Get-CsLocationPolicy
TOCTitle: Get-CsLocationPolicy
ms:assetid: d338af1b-3865-4010-a7fc-d5841c515ae6
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg398911(v=OCS.15)
ms:contentKeyID: 49305134
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Get-CsLocationPolicy

 

_**마지막으로 수정된 항목:** 2015-03-09_

E9-1-1(Enhanced 9-1-1) 위치 정보 서비스가 구성된 방식 또는 구성되었는지 여부에 대한 정보를 반환합니다. E9-1-1 서비스를 사용하면 긴급 통화 응답자가 발신자의 지리적 위치를 확인할 수 있습니다. 이 cmdlet은 Lync Server 2010에서 도입되었습니다.

## 구문

    Get-CsLocationPolicy [-Identity <XdsIdentity>] <COMMON PARAMETERS>

    Get-CsLocationPolicy [-Filter <String>] <COMMON PARAMETERS>

    COMMON PARAMETERS: [-LocalStore <SwitchParameter>]

## 예제

## 예제 1

예제 1에서는 조직에서 현재 사용 중인 모든 위치 정책 컬렉션을 반환합니다. 이 작업을 수행하기 위해 매개 변수 없이 **Get-CsLocationPolicy** cmdlet을 호출합니다.

    Get-CsLocationPolicy

## 예제 2

예제 2에 표시된 명령은 ID가 Reno와 같은 위치 정책만 반환합니다. ID는 고유해야 하므로 이 명령은 최대 하나의 위치 정책만 반환합니다.

    Get-CsLocationPolicy -Identity Reno

## 예제 3

예제 3에서는 Filter 매개 변수를 사용하여 사용자별 범위에서 구성된 모든 위치 정책을 반환합니다. 사용자별 범위에서 구성된 정책은 사용자 및 네트워크 사이트에 직접 할당할 수 있습니다. tag:\* 와일드카드는 반환되는 데이터를 ID가 문자열 값 tag:으로 시작하는 위치 정책으로 제한하도록 **Get-CsLocationPolicy** cmdlet에 지시합니다. 개별 정책을 검색할 때는 tag: 접두사를 지정할 필요가 없지만 이 접두사를 사용하면 모든 사용자별 정책을 필터링할 수 있습니다.

    Get-CsLocationPolicy -Filter tag:*

## 예제 4

예제 4는 고급 응급 서비스가 비활성화된 모든 위치 정책 컬렉션을 반환합니다. 이 작업을 수행하기 위해 명령은 먼저 **Get-CsLocationPolicy** cmdlet을 사용하여 조직에서 현재 사용 중인 모든 위치 정책 컬렉션을 반환합니다. 이 컬렉션은 **Where-Object** cmdlet에 파이프되며, **Where-Object** cmdlet은 반환되는 데이터를 EnhancedEmergencyServicesEnabled 속성이 False($False)와 같은(-eq) 정책으로 제한하는 필터를 적용합니다.

    Get-CsLocationPolicy | Where-Object {$_.EnhancedEmergencyServicesEnabled -eq $False}

## 자세한 정보

위치 정책은 E9-1-1 기능과 관련된 설정을 적용하는 데 사용되며, 사용자가 E9-1-1을 사용하도록 설정되어 있는지 여부를 확인하고, 설정된 경우 응급 통화에 대한 행동을 결정합니다. 예를 들어 위치 정책을 사용하여 응급 통화 번호(한국의 경우 119)를 정의하고, 회사 보안 부서에 자동으로 알림을 제공할지 여부, 통화를 경로 지정할 방법 등을 지정할 수 있습니다. 이 cmdlet은 하나 이상의 위치 정책을 검색합니다.

이 cmdlet을 실행할 수 있는 사용자: 기본적으로 RTCUniversalUserAdmins 및 RTCUniversalServerAdmins 그룹의 구성원은 **Get-CsLocationPolicy** cmdlet을 로컬로 실행할 수 있습니다. 사용자가 직접 만든 사용자 지정 RBAC(역할 기반 액세스 제어) 역할을 포함하여 이 cmdlet이 할당된 모든 RBAC 역할의 목록을 반환하려면 Windows PowerShell 프롬프트에서 다음 명령을 실행합니다.

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Get-CsLocationPolicy"}

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
<td><p>와일드카드 문자열과 일치하는 정책 ID 값을 기준으로 위치 정책을 검색할 와일드카드 문자가 포함된 문자열입니다.</p></td>
</tr>
<tr class="even">
<td><p><em>Identity</em></p></td>
<td><p>선택</p></td>
<td><p>Microsoft.Rtc.Management.Xds.XdsIdentity</p></td>
<td><p>검색할 위치 정책의 고유 식별자입니다. 전역 위치 정책을 검색하려면 Global 값을 사용하십시오. 사이트 범위에서 만들어진 정책의 경우 이 값은 site:&lt;사이트 이름&gt; 형식으로 지정됩니다. 여기서 사이트 이름은 Lync Server 배포에 정의된 사이트 이름입니다(예: site:Redmond). 사용자별 범위에서 만들어진 정책의 경우 이 값은 단순히 해당 정책의 이름(예: Reno)입니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>LocalStore</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>중앙 관리 저장소 자체가 아니라 중앙 관리 저장소의 로컬 복제본에서 위치 정책 정보를 검색합니다.</p></td>
</tr>
</tbody>
</table>


## 입력 형식

없음.

## 반환 형식

**Get-CsLocationPolicy** cmdlet은 Microsoft.Rtc.Management.WritableConfig.Policy.Location.LocationPolicy 개체의 인스턴스를 반환합니다.

## 참고 항목

#### 기타 리소스

[New-CsLocationPolicy](new-cslocationpolicy.md)  
[Remove-CsLocationPolicy](remove-cslocationpolicy.md)  
[Set-CsLocationPolicy](set-cslocationpolicy.md)  
[Grant-CsLocationPolicy](grant-cslocationpolicy.md)  
[Test-CsLocationPolicy](test-cslocationpolicy.md)

