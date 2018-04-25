---
title: Remove-CsConferencingConfiguration
TOCTitle: Remove-CsConferencingConfiguration
ms:assetid: a3dff4b0-100b-46fa-9078-d3b0d4914d87
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg412767(v=OCS.15)
ms:contentKeyID: 49304602
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Remove-CsConferencingConfiguration

 

_**마지막으로 수정된 항목:** 2015-03-09_

전화 회의 구성 설정의 지정된 컬렉션을 제거합니다. 전화 회의 설정은 전화 회의 콘텐츠 및 참고 파일의 허용되는 최대 크기, 콘텐츠 유예 기간, 지원되는 클라이언트의 내부 및 외부 다운로드 URL 등을 지정합니다. 이 cmdlet은 Lync Server 2010에서 도입되었습니다.

## 구문

    Remove-CsConferencingConfiguration -Identity <XdsIdentity> [-Confirm [<SwitchParameter>]] [-Force <SwitchParameter>] [-WhatIf [<SwitchParameter>]]

## 예제

## 예제 1

예제 1에서는 Redmond 사이트에 적용된 회의 구성 설정을 삭제합니다. 사이트 설정이 삭제될 경우 사이트의 사용자는 자동으로 전역 회의 구성 설정에서 발견된 설정을 상속하게 됩니다.

    Remove-CsConferencingConfiguration -Identity site:Redmond

## 예제 2

예제 2에서는 명령이 사이트 범위에 적용된 모든 회의 구성 설정을 삭제합니다. 이 작업을 수행하기 위해 먼저 Filter 매개 변수와 함께 **Get-CsConferencingConfiguration** cmdlet을 호출합니다. 필터 값 "site:"은 ID가 "site:" 문자로 시작하는 설정만 반환하도록 합니다. 그런 다음 필터링된 컬렉션은 컬렉션의 각 항목을 삭제하는 **Remove-CsConferencingConfiguration** cmdlet에 파이프됩니다.

    Get-CsConferencingConfiguration -Filter site:* | Remove-CsConferencingConfiguration

## 예제 3

예제 3에서는 조직이 Litwareinc로 설정되지 않은 모든 회의 구성 설정을 삭제합니다. 이 작업을 수행하기 위해 명령은 먼저 매개 변수 없이 **Get-CsConferencingConfiguration** cmdlet을 호출합니다. 그러면 조직에서 사용 중인 모든 회의 구성 설정 컬렉션이 반환됩니다. 이 컬렉션은 Organization 속성이 Litwareinc와 같지 않은 설정만 선택하는 **Where-Object** cmdlet에 파이프됩니다. 끝으로, 필터링된 컬렉션은 컬렉션의 모든 항목을 삭제하는 **Remove-CsConferencingConfiguration** cmdlet에 파이프됩니다.

    Get-CsConferencingConfiguration | Where-Object {$_.Organization -ne "Litwareinc"} | Remove-CsConferencingConfiguration

## 자세한 정보

전화 회의의 경우 두 개의 cmdlet 집합으로 관리가 분할됩니다. 예를 들어 전화 회의에 참가하도록 익명 참여자를 초대할 수 있는지, 전화 회의에서 응용 프로그램 공유를 제공할 수 있는지, 전화 회의 내에서 파일을 전송할 수 있는지 등, 사용자가 수행할 수 있는 작업과 수행할 수 없는 작업을 관리하려면 **CsConferencingPolicy** cmdlet을 사용해야 합니다.

사용자 작업 외에 관리자는 웹 회의 서비스를 관리해야 합니다. 예를 들어 관리자는 단일 전화 회의에 할당된 콘텐츠 저장소의 최대 크기를 지정하고 전화 회의 콘텐츠가 자동으로 삭제되기 전 유예 기간을 지정하는 등의 작업을 수행할 수 있어야 합니다. 또한 응용 프로그램 공유 및 파일 전송과 같은 작업에 사용되는 포트를 지정할 수 있어야 합니다.

포트 지정과 같은 작업은 **CsConferencingConfiguration** cmdlet을 사용하여 관리할 수 있습니다. 이러한 cmdlet을 사용하여 실제 서버 자체를 관리할 수 있습니다. 전역, 사이트 및 서비스 범위에 적용할 수 있는 **CsConferencingConfiguration** cmdlet은 사용자가 회의 중에 응용 프로그램을 공유할 수 있는지, 응용 프로그램 공유가 허용되는지를 지정하는 데 사용되지는 않지만 이러한 작업에 사용할 포트를 지정할 수는 있습니다. 마찬가지로 이 cmdlet을 사용하여 저장소 제한 및 만료 기간, 사용자가 회의 도움말 및 리소스를 가져올 수 있는 내부 및 외부 URL에 대한 포인터 등을 지정할 수도 있습니다.

**Remove-CsConferencingConfiguration** cmdlet은 조직에서 사용하기 위해 만든 회의 구성 설정의 사용자 지정 컬렉션을 삭제할 수 있는 방법을 제공합니다. 설정 컬렉션을 삭제하면 이전에 이러한 설정의 영향을 받은 모든 서버가 자동으로 계층(서비스 - 사이트 - 범위)에서 다음 컬렉션의 관리 범위로 들어갑니다. 삭제된 설정이 서비스 범위에서 적용된 경우 서버가 사이트 설정에 의해 관리됩니다. 사이트 범위에 설정이 없는 경우 서버가 전역 설정으로 관리됩니다. 마찬가지로 사이트 범위에서 설정을 삭제하면 이전에 이러한 사이트 설정으로 관리된 서버가 전역 설정으로 관리됩니다.

전역 설정에 대해 **Remove-CsConferencingConfiguration** cmdlet을 실행할 수도 있습니다. 단, Lync Server에서는 전역 설정을 제거하도록 허용하지 않으므로 이 경우 전역 설정이 제거되지 않습니다. 대신 전역 컬렉션의 모든 속성이 기본값으로 다시 설정됩니다. 예를 들어 이전에 최대 콘텐츠 저장소 값을 200MB로 변경한 경우 이 속성이 기본값 100MB로 돌아갑니다.

이 cmdlet을 실행할 수 있는 사용자: 기본적으로 RTCUniversalServerAdmins 그룹의 구성원은 **Remove-CsConferencingConfiguration** cmdlet을 로컬로 실행할 수 있습니다. 사용자가 직접 만든 사용자 지정 RBAC(역할 기반 액세스 제어) 역할을 포함하여 이 cmdlet이 할당된 모든 RBAC 역할의 목록을 반환하려면 Windows PowerShell 프롬프트에서 다음 명령을 실행합니다.

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Remove-CsConferencingConfiguration"}

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
<td><p><em>Identity</em></p></td>
<td><p>필수</p></td>
<td><p>Microsoft.Rtc.Management.Xds.XdsIdentity</p></td>
<td><p>제거할 회의 구성 설정 컬렉션의 고유 식별자입니다. 사이트 범위에서 구성된 설정을 제거하려면 -Identity &quot;site:Redmond&quot;와 유사한 구문을 사용합니다. 서비스 범위에서 구성된 설정을 제거하려면 -Identity &quot;service:ConferencingServer:atl-cs-001.litwareinc.com&quot;과 유사한 구문을 사용합니다.</p>
<p>전역 설정에 대해 <strong>Remove-CsConferencingConfiguration</strong> cmdlet을 실행할 수도 있습니다. 그러나 이 경우 설정이 제거되지 않으며 대신 모든 속성이 기본값으로 다시 설정됩니다.</p></td>
</tr>
<tr class="even">
<td><p><em>Confirm</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>명령을 실행하기 전에 확인 메시지를 표시합니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>Force</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>명령을 실행할 때 발생할 수 있는 심각하지 않은 오류 메시지를 표시하지 않습니다.</p></td>
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

Microsoft.Rtc.Management.WritableConfig.Settings.WebConf.ConfSettings 개체입니다. **Remove-CsConferencingConfiguration** cmdlet은 전화 회의 구성 개체의 파이프라인된 인스턴스를 허용합니다.

## 반환 형식

없음. 대신 **Remove-CsConferencingConfiguration** cmdlet은 Microsoft.Rtc.Management.WritableConfig.Settings.WebConf.ConfSettings 개체의 기존 인스턴스를 삭제합니다.

## 참고 항목

#### 기타 리소스

[Get-CsConferencingConfiguration](get-csconferencingconfiguration.md)  
[New-CsConferencingConfiguration](new-csconferencingconfiguration.md)  
[Set-CsConferencingConfiguration](set-csconferencingconfiguration.md)

