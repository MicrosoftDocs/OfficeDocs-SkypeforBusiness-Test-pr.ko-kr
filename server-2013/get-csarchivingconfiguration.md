---
title: Get-CsArchivingConfiguration
TOCTitle: Get-CsArchivingConfiguration
ms:assetid: e4951b81-2738-4cc2-87be-f8ee79da6c09
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg399012(v=OCS.15)
ms:contentKeyID: 49305327
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Get-CsArchivingConfiguration

 

_**마지막으로 수정된 항목:** 2015-03-09_

조직에서 메신저 대화 세션을 보관하는 경우 또는 보관하는 방법에 대한 정보를 반환합니다. 이 cmdlet은 Lync Server 2010에서 도입되었습니다.

## 구문

    Get-CsArchivingConfiguration [-Identity <XdsIdentity>] <COMMON PARAMETERS>

    Get-CsArchivingConfiguration [-Filter <String>] <COMMON PARAMETERS>

    COMMON PARAMETERS: [-LocalStore <SwitchParameter>]

## 예제

## 예제 1

예제 1에 표시된 명령은 조직에서 사용 중인 모든 보관 구성 설정 컬렉션을 반환합니다.

    Get-CsArchivingConfiguration

## 예제 2

예제 2에서는 Identity 매개 변수를 사용하여 반환되는 보관 구성 설정 컬렉션을 ID가 site:Redmond인 설정으로 제한합니다.

    Get-CsArchivingConfiguration -Identity site:Redmond

## 예제 3

예제 3에서는 Filter 매개 변수를 사용하여 반환되는 보관 구성 설정 컬렉션을 사이트 범위에서 구성된 설정으로 제한합니다. 매개 변수 값 "site:\*"는 반환되는 항목을 ID가 문자열 값 "site:"으로 시작하는 항목으로 제한합니다.

    Get-CsArchivingConfiguration -Filter site:*

## 예제 4

이 예제에서는 **Get-CsArchivingConfiguration** cmdlet을 사용하여 조직에서 사용하도록 설정된 모든 보관 구성 설정 컬렉션을 반환합니다. 이 작업을 수행하기 위해 명령은 먼저 매개 변수 없이 **Get-CsArchivingConfiguration** cmdlet을 호출하여 모든 보관 구성 설정 컬렉션을 반환합니다. 이 컬렉션은 반환되는 데이터를 EnableArchiving 속성이 "None"과 같지 않은 컬렉션으로 제한하는 필터가 적용되는 **Where-Object** cmdlet에 파이프됩니다. EnableArchiving이 "None"으로 설정되어 있으면 보관을 사용하지 않는 것이고, 이 속성이 다른 값("IMOnly" 또는 "ImAndWebConf")으로 설정되어 있으면 보관을 사용하는 것입니다.

    Get-CsArchivingConfiguration | Where-Object {$_.EnableArchiving -ne "None"}

## 자세한 정보

대부분의 조직에서는 조직의 사용자 또는 선택된 사용자의 하위 집합이 수행하는 모든 메신저 세션의 대화 내용을 보관하여 유용하게 활용하고 있습니다. 그러한 대화 내용을 의무적으로 보관해야 하는 조직도 있습니다. 예를 들어 법에 따라 모든 전자 통신의 복사본을 보관해야 하는 금융 분야의 조직 대부분이 이에 해당합니다.

Lync Server에서는 메신저 및 웹 회의 세션 보관과 관련된 유동적인 기능을 제공합니다. 보관 서버를 배포한 경우 여러 가지 **CsArchivingConfiguration** cmdlet을 사용하여 메신저 대화 보관을 설정 및 해제하고 보관 데이터베이스를 관리할 수 있습니다. 또한 보관에 실패한 경우 메신저를 일시 중단하여 모든 전자 통신의 레코드를 유지할 수 있습니다.

메신저 대화 세션을 보관하려면 적어도 하나의 보관 서버를 설정해야 합니다. 보관 서버를 설정한 후에는 다음 두 단계를 추가로 수행해야 합니다. 먼저, 적절한 범위에서 보관을 사용하도록 설정해야 합니다. 자세한 내용은 **Set-CsArchivingConfiguration** cmdlet 도움말 항목을 참조하십시오. 전역 범위가 적절한 범위일 수 있지만 다른 사이트의 사용자 지정 보관 설정을 구성할 수도 있습니다.

둘째, 어떤 사용자의 메신저 대화 세션을 보관할지 나타내는 보관 정책을 사용해야 합니다. 보관을 사용하도록 설정하지만 사용자에게 메신저 대화 세션을 보관하도록 지정하는 정책을 할당하지 않을 경우 어떻게 되겠습니까? 문자 그대로 아무 일도 발생하지 않습니다. 메신저 대화 세션을 보관하도록 지정된 정책을 적용하지 않으면 메신저 대화 세션이 보관되지 않습니다.

**Get-CsArchivingConfiguration** cmdlet을 사용하면 조직에서 메신저 대화 세션 보관이 구성된 방식을 확인할 수 있습니다.

이 cmdlet을 실행할 수 있는 사용자: 기본적으로 RTCUniversalUserAdmins, RTCUniversalServerAdmins 그룹의 구성원은 **Get-CsArchivingConfiguration** cmdlet을 로컬로 실행할 수 있습니다. 사용자가 직접 만든 사용자 지정 RBAC(역할 기반 액세스 제어) 역할을 포함하여 이 cmdlet이 할당된 모든 RBAC 역할의 목록을 반환하려면 Windows PowerShell 프롬프트에서 다음 명령을 실행합니다.

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Get-CsArchivingConfiguration"}

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
<td><p>와일드카드 문자를 사용하여 하나 이상의 보관 구성 설정 컬렉션을 반환하는 데 사용됩니다. 사이트 범위에서 구성된 모든 설정 컬렉션을 반환하려면 -Filter site:* 구문을 사용하고, ID(필터링할 수 있는 유일한 속성)에 문자열 값 &quot;Canada&quot;가 포함된 모든 설정 컬렉션을 반환하려면 -Filter &quot;*Canada*&quot; 구문을 사용합니다.</p></td>
</tr>
<tr class="even">
<td><p><em>Identity</em></p></td>
<td><p>선택</p></td>
<td><p>Microsoft.Rtc.Management.Xds.XdsIdentity</p></td>
<td><p>반환할 보관 설정의 컬렉션에 대한 고유 식별자를 나타냅니다. 전역 설정을 참조하려면 -Identity global 구문을 사용하고, 사이트 범위에서 구성된 컬렉션을 참조하려면 -Identity site:Redmond와 같은 구문을 사용합니다. 개별 등록자 풀에 할당된 설정에 대한 정보를 반환하려면 다음과 같은 구문을 사용합니다.</p>
<p>-Identity &quot;service:Registrar:atl-cs-001.litwareinc.com&quot;</p>
<p>풀 수준 설정은 Lync Server 2013에서만 사용할 수 있습니다.</p>
<p>ID를 지정할 때는 와일드카드를 사용할 수 없습니다. 와일드카드를 사용해야 하는 경우 대신 Filter 매개 변수를 포함합니다.</p>
<p>이 매개 변수를 지정하지 않으면 <strong>Get-CsArchivingConfiguration</strong> cmdlet이 조직에서 사용 중인 모든 보관 구성 설정 컬렉션을 반환합니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>LocalStore</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>중앙 관리 저장소 자체가 아니라 중앙 관리 저장소의 로컬 복제본에서 보관 구성 데이터를 검색합니다.</p></td>
</tr>
</tbody>
</table>


## 입력 형식

없음. **Get-CsArchivingConfiguration** cmdlet은 파이프라인된 입력을 허용하지 않습니다.

## 반환 형식

**Get-CsArchivingConfiguration** cmdlet은 Microsoft.Rtc.Management.WritableConfig.Settings.Archiving.ArchivingSettings 개체의 인스턴스를 반환합니다.

## 참고 항목

#### 기타 리소스

[New-CsArchivingConfiguration](new-csarchivingconfiguration.md)  
[Remove-CsArchivingConfiguration](remove-csarchivingconfiguration.md)  
[Set-CsArchivingConfiguration](set-csarchivingconfiguration.md)  
[Set-CsArchivingServer](set-csarchivingserver.md)

