---
title: Get-CsConferencingConfiguration
TOCTitle: Get-CsConferencingConfiguration
ms:assetid: db4ab3bc-071c-4f73-a3a0-62dc8aed48a1
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg398965(v=OCS.15)
ms:contentKeyID: 49305240
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Get-CsConferencingConfiguration

 

_**마지막으로 수정된 항목:** 2015-03-09_

조직의 전화 회의 구성 설정에 대한 정보를 반환합니다. 전화 회의 설정은 전화 회의 콘텐츠 및 유인물에 허용되는 최대 크기, 콘텐츠 유예 기간(즉, 콘텐츠를 삭제하기 전까지 보관할 시간) 및 지원되는 클라이언트의 내부 및 외부 다운로드 URL 등과 같은 사항을 결정합니다. 이 cmdlet은 Lync Server 2010에서 도입되었습니다.

## 구문

    Get-CsConferencingConfiguration [-Identity <XdsIdentity>] <COMMON PARAMETERS>

    Get-CsConferencingConfiguration [-Filter <String>] <COMMON PARAMETERS>

    COMMON PARAMETERS: [-LocalStore <SwitchParameter>]

## 예제

## 예제 1

예제 1에서는 조직에서 현재 사용 중인 모든 전화 회의 구성 설정에 대한 정보를 반환합니다. 이 작업을 수행하기 위해 매개 변수 없이 **Get-CsConferencingConfiguration** cmdlet을 호출합니다.

    Get-CsConferencingConfiguration

## 예제 2

예제 2에서는 Redmond 사이트(-Identity site:Redmond)에 대한 전화 회의 구성 정보를 반환합니다. ID는 고유해야 하므로 이 명령은 항상 최대 하나의 전화 회의 구성 설정 컬렉션을 반환합니다.

    Get-CsConferencingConfiguration -Identity site:Redmond

## 예제 3

예제 3에 표시된 명령은 사이트 범위에서 적용된 모든 전화 회의 구성 설정에 대한 정보를 반환합니다. 이 작업을 수행하기 위해 Filter 매개 변수와 함께 **Get-CsConferencingConfiguration** cmdlet을 호출합니다. 필터 값 "site:\*"는 ID가 문자열 값 "site:"으로 시작하는 설정만 반환되도록 합니다.

    Get-CsConferencingConfiguration -Filter "site:*"

## 예제 4

예제 4에서는 조직이 Litwareinc로 설정되지 않은 모든 전화 회의 구성 설정에 대한 정보를 반환합니다. 이 작업을 수행하기 위해 명령은 먼저 매개 변수 없이 **Get-CsConferencingConfiguration** cmdlet을 호출합니다. 그러면 조직에서 사용 중인 모든 전화 회의 구성 설정 컬렉션이 반환됩니다. 결과 컬렉션은 Organization 속성이 Litwareinc와 같지 않은 설정만 선택하는 **Where-Object** cmdlet에 파이프됩니다.

    Get-CsConferencingConfiguration | Where-Object {$_.Organization -ne "Litwareinc"}

## 예제 5

예제 5에서는 최대 콘텐츠 저장 공간이 100MB보다 큰 전화 회의 구성 설정에 대한 정보만 반환합니다. 이 작업을 수행하기 위해 명령은 먼저 매개 변수 없이 **Get-CsConferencingConfiguration** cmdlet을 호출하여 모든 전화 회의 구성 설정 컬렉션을 반환합니다. 이 컬렉션은 콘텐츠 저장 공간이 100MB보다 큰 설정을 선택하는 **Where-Object** cmdlet에 파이프됩니다.

    Get-CsConferencingConfiguration | Where-Object {$_.MaxContentStorageMB -gt 100}

## 자세한 정보

전화 회의의 경우 두 개의 cmdlet 집합으로 관리가 분할됩니다. 예를 들어 전화 회의에 참가하도록 익명 참여자를 초대할 수 있는지, 전화 회의에서 응용 프로그램 공유를 제공할 수 있는지, 전화 회의 내에서 파일을 전송할 수 있는지 등, 사용자가 수행할 수 있는 작업과 수행할 수 없는 작업을 관리하려면 **CsConferencingPolicy** cmdlet을 사용해야 합니다.

사용자 작업 외에 관리자는 Lync Server 웹 회의 서비스를 관리해야 합니다. 예를 들어 관리자는 단일 전화 회의에 할당된 콘텐츠 저장소의 최대 크기를 지정하고 전화 회의 콘텐츠가 자동으로 삭제되기 전 유예 기간을 지정하는 등의 작업을 수행할 수 있어야 합니다. 또한 응용 프로그램 공유 및 파일 전송과 같은 작업에 사용되는 포트를 지정할 수 있어야 합니다.

포트 지정과 같은 작업은 **CsConferencingConfiguration** cmdlet을 사용하여 관리할 수 있습니다. 이러한 cmdlet을 사용하여 실제 서버 자체를 관리할 수 있습니다. 전역, 사이트 및 서비스 범위에 적용할 수 있는 **CsConferencingConfiguration** cmdlet은 사용자가 전화 회의 중에 응용 프로그램을 공유할 수 있는지, 응용 프로그램 공유가 허용되는지를 지정하는 데 사용되지는 않지만 이러한 작업에 사용할 포트를 지정할 수는 있습니다. 마찬가지로 이 cmdlet을 사용하여 저장소 제한 및 만료 기간, 사용자가 전화 회의 도움말 및 리소스를 가져올 수 있는 내부 및 외부 URL에 대한 포인터 등을 지정할 수도 있습니다.

**Get-CsConferencingConfiguration** cmdlet을 사용하면 관리자가 조직에서 현재 사용 중인 모든 전화 회의 구성 설정에 대한 정보를 반환할 수 있습니다.

이 cmdlet을 실행할 수 있는 사용자: 기본적으로 RTCUniversalUserAdmins 및 RTCUniversalServerAdmins 그룹의 구성원은 **Get-CsConferencingConfiguration** cmdlet을 로컬로 실행할 수 있습니다. 사용자가 직접 만든 사용자 지정 RBAC(역할 기반 액세스 제어) 역할을 포함하여 이 cmdlet이 할당된 모든 RBAC 역할의 목록을 반환하려면 Windows PowerShell 프롬프트에서 다음 명령을 실행합니다.

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Get-CsConferencingConfiguration"}

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
<td><p>반환할 전화 회의 구성 설정의 ID를 지정할 때 와일드카드를 활용하는 데 사용됩니다. 예를 들어 -Filter &quot;site:*&quot; 구문은 사이트 범위에서 구성된 모든 설정을 반환하고, -Filter &quot;service:*&quot; 구문은 서비스 범위에서 구성된 모든 설정을 반환합니다.</p>
<p>Filter 매개 변수와 Identity 매개 변수를 같은 명령에 함께 사용할 수 없습니다.</p></td>
</tr>
<tr class="even">
<td><p><em>Identity</em></p></td>
<td><p>선택</p></td>
<td><p>Microsoft.Rtc.Management.Xds.XdsIdentity</p></td>
<td><p>검색할 전화 회의 구성 설정 컬렉션의 고유 식별자입니다. 전역 설정을 검색하려면 -Identity global 구문을 사용하고, 사이트 범위에서 구성된 설정을 검색하려면 -Identity &quot;site:Redmond&quot;와 유사한 구문을 사용하고, 서비스 범위에서 구성된 설정을 검색하려면 -Identity &quot;service:ConferencingServer:atl-cs-001.litwareinc.com&quot;과 유사한 구문을 사용합니다.</p>
<p>이 매개 변수를 포함하지 않으면 <strong>Get-CsConferencingConfiguration</strong> cmdlet이 조직에서 현재 사용 중인 모든 전화 회의 구성 설정을 반환합니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>LocalStore</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>중앙 관리 저장소 자체가 아니라 중앙 관리 저장소의 로컬 복제본에서 전화 전화 회의 구성 데이터를 검색합니다.</p></td>
</tr>
</tbody>
</table>


## 입력 형식

없음. **Get-CsConferencingConfiguration** cmdlet은 파이프라인된 입력을 허용하지 않습니다.

## 반환 형식

**Get-CsConferencingConfiguration** cmdlet은 Microsoft.Rtc.Management.WritableConfig.Settings.WebConf.ConfSettings 개체의 인스턴스를 반환합니다.

## 참고 항목

#### 기타 리소스

[New-CsConferencingConfiguration](new-csconferencingconfiguration.md)  
[Remove-CsConferencingConfiguration](remove-csconferencingconfiguration.md)  
[Set-CsConferencingConfiguration](set-csconferencingconfiguration.md)

