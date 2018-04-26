---
title: Set-CsConferencingConfiguration
TOCTitle: Set-CsConferencingConfiguration
ms:assetid: c468d7fd-fb2c-469c-85fb-58e0834aac36
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg412969(v=OCS.15)
ms:contentKeyID: 49304956
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Set-CsConferencingConfiguration

 

_**마지막으로 수정된 항목:** 2015-03-09_

전화 회의 구성 설정의 기존 컬렉션을 수정합니다. 전화 회의 설정은 모임 콘텐츠 및 유인물에 허용되는 최대 크기, 콘텐츠 유예 기간(즉, 콘텐츠를 삭제하기 전까지 보관할 시간) 및 지원되는 클라이언트의 내부 및 외부 다운로드 URL 등과 같은 사항을 결정합니다. 이 cmdlet은 Lync Server 2010에서 도입되었습니다.

## 구문

    Set-CsConferencingConfiguration [-Identity <XdsIdentity>] <COMMON PARAMETERS>

    Set-CsConferencingConfiguration [-Instance <PSObject>] <COMMON PARAMETERS>

    COMMON PARAMETERS: [-ClientAppSharingPort <UInt16>] [-ClientAppSharingPortRange <UInt32>] [-ClientAudioPort <UInt16>] [-ClientAudioPortRange <UInt32>] [-ClientFileTransferPort <UInt16>] [-ClientFileTransferPortRange <UInt32>] [-ClientMediaPort <UInt16>] [-ClientMediaPortRange <UInt32>] [-ClientMediaPortRangeEnabled <$true | $false>] [-ClientSipDynamicPort <UInt16>] [-ClientSipDynamicPortRange <UInt32>] [-ClientVideoPort <UInt16>] [-ClientVideoPortRange <UInt32>] [-Confirm [<SwitchParameter>]] [-ConsoleDownloadExternalUrl <String>] [-ConsoleDownloadInternalUrl <String>] [-ContentGracePeriod <TimeSpan>] [-Force <SwitchParameter>] [-HelpdeskExternalUrl <String>] [-HelpdeskInternalUrl <String>] [-MaxBandwidthPerAppSharingServiceMb <UInt64>] [-MaxContentStorageMb <UInt16>] [-MaxUploadFileSizeMb <UInt16>] [-Organization <String>] [-WhatIf [<SwitchParameter>]]

## 예제

## 예제 1

예제 1에서는 **Set-CsConferencingConfiguration** cmdlet이 전화 회의 구성 설정의 전역 인스턴스를 수정합니다. 이 경우 이 명령은 Organization 속성 값을 Litwareinc로 설정합니다. 이 작업을 수행하기 위해 Organization 매개 변수에 조직 이름 Litwareinc를 포함합니다.

    Set-CsConferencingConfiguration -Identity global -Organization Litwareinc

## 예제 2

예제 2는 예제 1을 확장한 것입니다. 이 예제의 명령은 현재 사용 중인 전화 회의 구성 설정의 각 컬렉션에 대한 Organization 속성 값을 수정합니다. 이 작업을 수행하기 위해 명령은 먼저 **Get-CsConferencingConfiguration** cmdlet을 사용하여 모든 전화 회의 구성 설정 컬렉션을 검색합니다. 이 컬렉션은 컬렉션의 각 항목을 가져와 Organization 속성 값을 Litwareinc로 변경하는 **Set-CsConferencingConfiguration** cmdlet에 파이프됩니다.

    Get-CsConferencingConfiguration | Set-CsConferencingConfiguration -Organization Litwareinc

## 예제 3

예제 3에 표시된 명령은 사이트 범위에 적용된 모든 전화 회의 구성 설정의 MaxContentStorageMb 속성 값을 변경합니다. 이 작업을 수행하기 위해 명령은 먼저 **Get-CsConferencingConfiguration** cmdlet을 Filter 매개 변수와 함께 호출합니다. 필터 값 "site:\*"는 ID가 "site:" 문자로 시작하는 설정만 반환되도록 합니다. 필터링된 컬렉션은 컬렉션의 각 항목에 대한 MaxContentStorageMB 속성 값을 50으로 변경하는 **Set-CsConferencingConfiguration** cmdlet에 파이프됩니다.

    Get-CsConferencingConfiguration -Filter site:* | Set-CsConferencingConfiguration -MaxContentStorageMb 50 

## 예제 4

예제 4에서는 100MB 이상의 콘텐츠 저장을 허용하는 모든 전화 회의 구성 설정을 허용되는 최대 콘텐츠 저장을 100MB로 설정하도록 수정됩니다. 이 작업을 수행하기 위해 명령은 먼저 매개 변수 없이 **Get-CsConferencingConfiguration** cmdlet을 호출하여 현재 사용 중인 모든 전화 회의 구성 설정 컬렉션을 반환합니다. 이 컬렉션은 MaxContentStorageMb 속성이 100보다 큰 설정을 선택하는 **Where-Object** cmdlet에 파이프됩니다. 그런 다음 필터링된 컬렉션은 컬렉션의 각 항목을 가져와 MaxContentStorageMb 속성 값을 100으로 설정하는 **Set-CsConferencingConfiguration** cmdlet에 파이프됩니다.

    Get-CsConferencingConfiguration | Where-Object {$_.MaxContentStorageMb -gt 100} | Set-CsConferencingConfiguration -MaxContentStorageMB 100

## 예제 5

예제 5에서는 Redmond 사이트(-Identity site:Redmond)에 대한 전화 회의 구성 설정을 검색하고 ContentGracePeriod 속성 값을 수정하여 유예 기간을 22시간(22시간: 00분: 00초)으로 설정합니다.

    Set-CsConferencingConfiguration -Identity site:Redmond -ContentGracePeriod "22:00:00"

## 예제 6

예제 6에서는 Fabrikam이 조직 목록에 포함되지 않은 모든 전화 회의 구성 설정을 수정합니다. 특히 이러한 설정에는 모두 Litwareinc가 새 조직으로 할당됩니다. 이 작업을 수행하기 위해 명령은 먼저 매개 변수 없이 **Get-CsConferencingConfiguration** cmdlet을 호출합니다. 그러면 조직에서 현재 사용 중인 모든 전화 회의 구성 설정 컬렉션이 반환됩니다. 이 컬렉션은 Organization 속성이 Fabrikam과 같지 않은(-ne) 모든 설정을 선택하는 **Where-Object** cmdlet에 파이프됩니다. 그런 다음 필터링된 컬렉션은 **Set-CsConferencingConfiguration** cmdlet에 파이프됩니다. **Set-CsConferencingConfiguration** cmdlet은 컬렉션의 각 항목을 가져와 Organization 속성 값을 Litwareinc로 변경합니다.

    Get-CsConferencingConfiguration | Where-Object {$_.Organization -ne "Fabrikam"} | Set-CsConferencingConfiguration -Organization Litwareinc

## 자세한 정보

전화 회의의 경우 두 개의 cmdlet 집합으로 관리가 분할됩니다. 예를 들어 전화 회의에 참가하도록 익명 참여자를 초대할 수 있는지, 전화 회의에서 응용 프로그램 공유를 제공할 수 있는지, 전화 회의 내에서 파일을 전송할 수 있는지 등, 사용자가 수행할 수 있는 작업과 수행할 수 없는 작업을 관리하려면 **CsConferencingPolicy** cmdlet을 사용해야 합니다.

관리자는 사용자 작업 관리뿐만 아니라 웹 회의 서비스도 관리해야 합니다. 예를 들어 관리자는 단일 전화 회의에 할당된 콘텐츠 저장소의 최대 크기를 지정하고 전화 회의 콘텐츠가 자동으로 삭제되기 전 유예 기간을 지정하는 등의 작업을 수행할 수 있어야 합니다. 또한 응용 프로그램 공유 및 파일 전송과 같은 작업에 사용할 포트도 지정할 수 있어야 합니다.

포트 지정과 같은 작업은 **CsConferencingConfiguration** cmdlet을 사용하여 관리할 수 있습니다. 이러한 cmdlet을 사용하여 실제 서버 자체를 관리할 수 있습니다. 전역, 사이트 및 서비스 범위에 적용할 수 있는 **CsConferencingConfiguration** cmdlet은 사용자가 전화 회의 중에 응용 프로그램을 공유할 수 있는지, 응용 프로그램 공유가 허용되는지를 지정하는 데 사용되지는 않지만 이러한 작업에 사용할 포트를 지정할 수는 있습니다. 마찬가지로 이 cmdlet을 사용하여 저장소 제한 및 만료 기간, 사용자가 전화 회의 도움말 및 리소스를 가져올 수 있는 내부 및 외부 URL에 대한 포인터 등을 지정할 수도 있습니다.

Lync Server를 설치하면 시스템에서 한 가지 전화 회의 구성 설정 컬렉션(전역 컬렉션)을 제공합니다. 사이트 또는 서비스의 사용자 지정 설정을 만들어야 하는 경우 **New-CsConferencingConfiguration** cmdlet을 사용하면 됩니다. 이러한 사용자 지정 설정을 만든 후에는 **Set-CsConferencingConfiguration** cmdlet을 사용하여 해당 설정과 전역 컬렉션을 수정할 수 있습니다.

이 cmdlet을 실행할 수 있는 사용자: 기본적으로 RTCUniversalServerAdmins 그룹의 구성원은 **Set-CsConferencingConfiguration** cmdlet을 로컬로 실행할 수 있습니다. 사용자가 직접 만든 사용자 지정 RBAC(역할 기반 액세스 제어) 역할을 포함하여 이 cmdlet이 할당된 모든 RBAC 역할의 목록을 반환하려면 Windows PowerShell 프롬프트에서 다음 명령을 실행합니다.

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Set-CsConferencingConfiguration"}

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
<td><p><em>ClientAppSharingPort</em></p></td>
<td><p>선택</p></td>
<td><p>System.UInt16</p></td>
<td><p>응용 프로그램 공유에 사용되는 시작 포트 번호를 나타냅니다. ClientAppSharingPort는 1024-65535(포함)의 값 포트 번호여야 합니다. 기본값은 5350입니다.</p></td>
</tr>
<tr class="even">
<td><p><em>ClientAppSharingPortRange</em></p></td>
<td><p>선택</p></td>
<td><p>System.UInt32</p></td>
<td><p>응용 프로그램 공유에 사용할 수 있는 총 포트 수를 나타냅니다. 기본값은 40입니다. 응용 프로그램 공유에 사용되는 실제 포트를 확인하려면 이 값 및 ClientAppSharingPort 값을 사용하십시오. 예를 들어 ClientAppSharingPort를 5350으로 설정하고 ClientAppSharingPortRange를 3으로 설정하면 응용 프로그램 공유에 다음 세 개의 포트를 사용할 수 있습니다. 5350; 5351; 5352.</p></td>
</tr>
<tr class="odd">
<td><p><em>ClientAudioPort</em></p></td>
<td><p>선택</p></td>
<td><p>System.UInt16</p></td>
<td><p>클라이언트 오디오에 사용되는 시작 포트 번호를 나타냅니다. ClientAudioPort는 1024-65535(포함)의 값 포트 번호여야 합니다. 기본값은 5350입니다.</p></td>
</tr>
<tr class="even">
<td><p><em>ClientAudioPortRange</em></p></td>
<td><p>선택</p></td>
<td><p>System.UInt32</p></td>
<td><p>클라이언트 오디오에 사용할 수 있는 총 포트 수를 나타냅니다. 기본값은 40입니다. 클라이언트 오디오에 사용되는 실제 포트를 확인하려면 이 값 및 ClientAudioPort 값을 사용하십시오. 예를 들어 ClientAudioPort를 5350으로 설정하고 ClientAudioPortRange를 3으로 설정하면 클라이언트 오디오에 다음 세 개의 포트를 사용할 수 있습니다. 5350; 5351; 5352.</p></td>
</tr>
<tr class="odd">
<td><p><em>ClientFileTransferPort</em></p></td>
<td><p>선택</p></td>
<td><p>System.UInt16</p></td>
<td><p>파일 전송에 사용되는 시작 포트 번호를 나타냅니다. ClientFileTransferPort는 1024-65535(포함)의 값 포트 번호여야 합니다. 기본값은 5350입니다.</p></td>
</tr>
<tr class="even">
<td><p><em>ClientFileTransferPortRange</em></p></td>
<td><p>선택</p></td>
<td><p>System.UInt32</p></td>
<td><p>파일 전송에 사용할 수 있는 총 포트 수를 나타냅니다. 기본값은 40입니다. 파일 전송에 사용되는 실제 포트를 확인하려면 이 값 및 ClientFileTransferPort 값을 사용하십시오. 예를 들어 ClientFileTransferPort를 5350으로 설정하고 ClientFileTransferPortRange를 3으로 설정하면 파일 전송에 다음 세 개의 포트를 사용할 수 있습니다. 5350; 5351; 5352.</p></td>
</tr>
<tr class="odd">
<td><p><em>ClientMediaPort</em></p></td>
<td><p>선택</p></td>
<td><p>System.UInt16</p></td>
<td><p>클라이언트 미디어에 사용되는 시작 포트 번호를 나타냅니다. Microsoft Office Communicator 2007 R2 클라이언트에 대해 이 매개 변수를 사용합니다. ClientMediaPort는 1024-65535(포함)의 값 포트 번호여야 합니다. 기본값은 5350입니다.</p></td>
</tr>
<tr class="even">
<td><p><em>ClientMediaPortRange</em></p></td>
<td><p>선택</p></td>
<td><p>System.UInt32</p></td>
<td><p>클라이언트 미디어에 사용할 수 있는 총 포트 수를 나타냅니다. 기본값은 40입니다. Office Communicator 2007 R2 클라이언트에 대해 이 매개 변수를 사용합니다. 클라이언트 미디어에 사용되는 실제 포트를 확인하려면 이 값 및 ClientMediaPort 값을 사용하십시오. 예를 들어 ClientMediaPort를 5350으로 설정하고 ClientMediaPortRange를 3으로 설정하면 클라이언트 미디어에 5350, 5351, 5352의 세 개 포트를 사용할 수 있습니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>ClientMediaPortRangeEnabled</em></p></td>
<td><p>선택</p></td>
<td><p>System.Boolean</p></td>
<td><p>True로 설정하면 클라이언트가 미디어 트래픽에 지정된 포트 범위를 사용합니다. False(기본값)로 설정하면 사용 가능한 모든 포트(포트 1024-포트 65535)를 사용하여 미디어 트래픽을 수용합니다.</p></td>
</tr>
<tr class="even">
<td><p><em>ClientSipDynamicPort</em></p></td>
<td><p>선택</p></td>
<td><p>System.UInt16</p></td>
<td><p>SIP 트래픽에 사용되는 시작 포트 번호를 나타냅니다. ClientSipDynamicPort는 1024-65535(포함)의 값 포트 번호여야 합니다. 기본값은 7100입니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>ClientSipDynamicPortRange</em></p></td>
<td><p>선택</p></td>
<td><p>System.UInt32</p></td>
<td><p>SIP 트래픽에 사용할 수 있는 총 포트 수를 나타냅니다. 기본값은 3입니다. SIP 트래픽에 사용되는 실제 포트를 확인하려면 이 값 및 ClientSipDynamicPort 값을 사용하십시오. 예를 들어 ClientSipDynamicPort를 7100으로 설정하고 ClientSipDynamicPortRange를 3으로 설정하면 클라이언트 미디어에 다음 세 개의 포트를 사용할 수 있습니다. 7100; 7101; 7102.</p></td>
</tr>
<tr class="even">
<td><p><em>ClientVideoPort</em></p></td>
<td><p>선택</p></td>
<td><p>System.UInt16</p></td>
<td><p>클라이언트 비디오에 사용되는 시작 포트 번호를 나타냅니다. ClientVideoPort는 1024-65535(포함)의 값 포트 번호여야 합니다. 기본값은 5350입니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>ClientVideoPortRange</em></p></td>
<td><p>선택</p></td>
<td><p>System.UInt32</p></td>
<td><p>클라이언트 비디오에 사용할 수 있는 총 포트 수를 나타냅니다. 기본값은 40입니다. 클라이언트 비디오에 사용되는 실제 포트를 확인하려면 이 값 및 ClientVideoPort 값을 사용하십시오. 예를 들어 ClientVideoPort를 5350으로 설정하고 ClientVideoPortRange를 3으로 설정하면 클라이언트 비디오에 다음 세 개의 포트를 사용할 수 있습니다. 5350; 5351; 5352.</p></td>
</tr>
<tr class="even">
<td><p><em>Confirm</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>명령을 실행하기 전에 확인 메시지를 표시합니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>ConsoleDownloadExternalUrl</em></p></td>
<td><p>선택</p></td>
<td><p>System.String</p></td>
<td><p>외부 사용자가 지원되는 클라이언트(예: Lync 2013)를 다운로드할 수 있는 URL입니다. 이 설정은 Lync Server 풀에 로그인 중인 레거시 클라이언트(예: Microsoft Office Communicator 2007 R2)에만 적용됩니다.</p></td>
</tr>
<tr class="even">
<td><p><em>ConsoleDownloadInternalUrl</em></p></td>
<td><p>선택</p></td>
<td><p>System.String</p></td>
<td><p>내부 사용자가 지원되는 클라이언트(예: Lync 2013)를 다운로드할 수 있는 URL입니다. 이 설정은 Lync Server 풀에 로그인 중인 레거시 클라이언트(예: Microsoft Office Communicator 2007 R2)에만 적용됩니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>ContentGracePeriod</em></p></td>
<td><p>선택</p></td>
<td><p>System.TimeSpan</p></td>
<td><p>전화 회의가 끝난 후에 전화 회의 콘텐츠가 서버에 남아 있게 될 시간을 나타냅니다. ContentGracePeriod는 일.시간:분:초 형식을 사용하여 지정해야 합니다. 예를 들어 콘텐츠 유예 기간을 30일로 설정하려면 -ContentGracePeriod 30.00:00:00 구문을 사용하십시오.</p>
<p>콘텐츠 유예 기간은 30분(00:30:00)에서 180일(180.00:00:00)의 값으로 설정할 수 있습니다. 기본값은 15일(15.00:00:00)입니다.</p></td>
</tr>
<tr class="even">
<td><p><em>Force</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>명령을 실행할 때 발생할 수 있는 심각하지 않은 오류 메시지를 표시하지 않습니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>HelpdeskExternalUrl</em></p></td>
<td><p>선택</p></td>
<td><p>System.String</p></td>
<td><p>전화 회의 중에 도움말을 클릭하는 외부 사용자에게 표시할 URL입니다.</p></td>
</tr>
<tr class="even">
<td><p><em>HelpdeskInternalUrl</em></p></td>
<td><p>선택</p></td>
<td><p>System.String</p></td>
<td><p>전화 회의 중에 도움말을 클릭하는 내부 사용자에게 표시할 URL입니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>Identity</em></p></td>
<td><p>선택</p></td>
<td><p>Microsoft.Rtc.Management.Xds.XdsIdentity</p></td>
<td><p>수정할 전화 회의 구성 설정 컬렉션의 고유 식별자입니다. 전역 컬렉션을 참조하려면 -Identity global 구문을 사용합니다. 사이트 범위에서 구성된 컬렉션을 참조하려면 -Identity &quot;site:Redmond&quot;와 유사한 구문을 사용합니다. 서비스 범위에서 컬렉션을 참조하려면 -Identity &quot;service:ConferencingServer:atl-cs-001.litwareinc.com&quot;과 유사한 구문을 사용합니다. 이러한 구성 설정을 호스트할 수 있는 서비스는 웹 회의 서비스뿐입니다.</p>
<p>이 매개 변수를 지정하지 않으면 <strong>Set-CsConferencingConfiguration</strong> cmdlet이 전역 설정을 자동으로 수정합니다.</p></td>
</tr>
<tr class="even">
<td><p><em>Instance</em></p></td>
<td><p>선택</p></td>
<td><p>전화 회의 설정 개체</p></td>
<td><p>개별 매개 변수 값을 설정하는 대신 cmdlet에 개체에 대한 참조를 전달할 수 있습니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>MaxBandwidthPerAppSharingServiceMb</em></p></td>
<td><p>선택</p></td>
<td><p>System.UInt64</p></td>
<td><p>응용 프로그램 공유 회의 서비스에 대해 별도로 설정하는 대역폭의 최대 크기(MB)입니다. MaxBandwidthPerAppSharingServiceMb는 50-100000(포함)의 모든 정수 값으로 설정할 수 있습니다. 기본값은 375MB입니다.</p></td>
</tr>
<tr class="even">
<td><p><em>MaxContentStorageMb</em></p></td>
<td><p>선택</p></td>
<td><p>System.UInt16</p></td>
<td><p>모임 콘텐츠 저장소에 허용되는 파일 공간의 최대 크기(MB)입니다. MaxContentStorageMb는 50-1024(1GB)(포함)의 정수 값으로 설정할 수 있습니다. 기본값은 500MB입니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>MaxUploadFileSizeMb</em></p></td>
<td><p>선택</p></td>
<td><p>System.UInt16</p></td>
<td><p>지정된 전화 회의에서 사용할 수 있는 파일의 최대 총 크기(유인물 및 PowerPoint 슬라이드 포함)입니다. 이 설정은 대개 Microsoft Exchange Server에서 전화 회의 콘텐츠를 보관하는 경우에 사용됩니다. 최대 업로드 파일 크기를 설정하면 전화 회의에서 사용되는 콘텐츠, 즉 보관해야 하는 콘텐츠가 Microsoft Exchange에 대해 구성된 최대 파일 크기를 초과하지 않도록 할 수 있습니다. 기본값은 500MB입니다.</p></td>
</tr>
<tr class="even">
<td><p><em>Organization</em></p></td>
<td><p>선택</p></td>
<td><p>System.String</p></td>
<td><p>전화 회의를 호스트하는 조직의 이름입니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>WhatIf</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>명령을 실제로 실행하지 않고도 명령이 실행될 경우 발생할 수 있는 현상을 설명합니다.</p></td>
</tr>
</tbody>
</table>


## 입력 형식

Microsoft.Rtc.Management.WritableConfig.Settings.WebConf.ConfSettings 개체입니다. **Set-CsConferencingConfiguration** cmdlet은 전화 회의 구성 개체의 파이프라인된 인스턴스를 허용합니다.

## 반환 형식

**Set-CsConferencingConfiguration** cmdlet은 값이나 개체를 반환하지 않습니다. 대신 이 cmdlet은 Microsoft.Rtc.Management.WritableConfig.Settings.WebConf.ConfSettings 개체의 인스턴스를 구성합니다.

## 참고 항목

#### 기타 리소스

[Get-CsConferencingConfiguration](get-csconferencingconfiguration.md)  
[New-CsConferencingConfiguration](new-csconferencingconfiguration.md)  
[Remove-CsConferencingConfiguration](remove-csconferencingconfiguration.md)

