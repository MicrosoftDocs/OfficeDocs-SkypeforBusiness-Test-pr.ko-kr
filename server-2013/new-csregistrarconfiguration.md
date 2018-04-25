---
title: New-CsRegistrarConfiguration
TOCTitle: New-CsRegistrarConfiguration
ms:assetid: 3cd02e36-629f-4ace-841a-1064fc423cfd
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg425893(v=OCS.15)
ms:contentKeyID: 49303382
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# New-CsRegistrarConfiguration

 

_**마지막으로 수정된 항목:** 2015-03-09_

새 등록자 구성 설정 컬렉션을 만듭니다. 등록자는 로그온 요청을 인증하고 사용자 상태에 대한 정보를 유지 관리하는 데 사용됩니다. 이 cmdlet은 Lync Server 2010에서 도입되었습니다.

## 구문

    New-CsRegistrarConfiguration -Identity <XdsIdentity> [-BackupStoreUnavailableThreshold <TimeSpan>] [-Confirm [<SwitchParameter>]] [-DefaultEndpointExpiration <Int32>] [-EnableDHCPServer <$true | $false>] [-Force <SwitchParameter>] [-InMemory <SwitchParameter>] [-MaxEndpointExpiration <Int32>] [-MaxEndpointsPerUser <UInt16>] [-MaxUserCount <UInt64>] [-MinEndpointExpiration <Int32>] [-PoolState <FailedOver | Active | FailingOver | FailingBack>] [-WhatIf [<SwitchParameter>]]

## 예제

## 예제 1

예제 1에서는 Redmond 사이트에 대한 새 등록자 구성 설정 컬렉션을 만듭니다(-Identity site:Redmond). 이 명령은 새 설정의 ID를 지정할 뿐 아니라 사용자당 최대 끝점 수를 4개로 설정하고(-MaxEndpointsPerUser 4) 클라이언트 등록에 DHCP 서버를 사용할 수 있도록 설정합니다(-EnableDHCPServer $True). Redmond 사이트에 등록자 구성 설정 컬렉션이 이미 할당된 경우 이 명령은 실패합니다.

    New-CsRegistrarConfiguration -Identity site:Redmond -MaxEndpointsPerUser 4 -EnableDHCPServer $True

## 예제 2

또한 예제 2에 표시된 명령은 Redmond 사이트(-Identity site:Redmond)에 대한 새 등록자 구성 설정 컬렉션을 만듭니다. 그러나 이 예제에서는 이러한 설정이 처음에 메모리에만 만들어지고 나중에 사이트 자체에 적용됩니다.

이 작업을 수행하기 위해 첫 번째 명령은 **New-CsRegistrarConfiguration** cmdlet을 사용하여 site:Redmond에 대한 새 설정 컬렉션을 만듭니다. 이러한 설정이 메모리에만 만들어지고 Redmond 사이트에 즉시 적용되지 않도록 InMemory 매개 변수를 명령 끝에 추가합니다. 이러한 설정은 메모리에만 존재하므로 변수에 저장해야 합니다. 이 예제에서는 $x라는 변수를 사용합니다.

두 번째 및 세 번째 명령은 새 가상 설정의 두 가지 속성(MaxEndpointsPerUser 및 EnableDHCPServer)을 수정합니다. 이 예제의 마지막 명령은 **Set-CsRegistrarConfiguration** cmdlet을 사용하여 $x에 저장된 가상 설정을 Redmond 사이트에 적용되는 실제 등록자 구성 설정 집합으로 변환합니다. **Set-CsRegistrarConfiguration** cmdlet을 호출하지 않으면 Redmond 사이트에 대한 새 설정이 만들어지지 않으며, Windows PowerShell 세션을 종료하거나 변수 $x를 삭제하는 즉시 가상 설정이 사라집니다.

    $x = New-CsRegistrarConfiguration -Identity site:Redmond -InMemory 
    $x.MaxEndpointsPerUser = 4 
    $x.EnableDHCPServer = $True
    Set-CsRegistrarConfiguration -Instance $x

## 자세한 정보

등록자는 Lync Server의 가장 중요한 구성 요소라고 할 수 있습니다. 등록자 없이는 사용자가 시스템에 로그온할 수 없으며 Lync Server에서 사용자와 사용자의 현재 상태를 추적할 수 없기 때문입니다. 사용자가 Lync Server에 로그온하면 로그온한 끝점에서 등록자에 REGISTER 요청을 보냅니다. 그러면 서버에서 클라이언트 장치의 인증 자격 증명을 요구하여 응답합니다. 클라이언트가 응답을 전달하는 경우(클라이언트가 유효한 자격 증명 집합을 제공하는 경우) 사용자가 인증되고 IP 주소, 포트 및 사용자 이름과 같은 끝점 정보가 등록 데이터베이스에 로깅됩니다. 사용자가 로그오프하면 이 정보가 데이터베이스에서 제거됩니다. 로그온한 시점부터 로그오프할 때까지 등록자는 상태 정보를 최신 상태로 유지하면서 사용자가 주고받는 메시지의 경로 지정을 지원합니다.

등록자 구성 설정은 끝점과 끝점 구독을 관리하는 데 사용됩니다. 이러한 설정은 전역, 사이트 또는 서비스 범위에서 적용할 수 있습니다. 서비스 범위 설정은 등록자 서비스에서만 사용할 수 있습니다.

**New-CsRegistrarConfiguration** cmdlet을 사용하면 사이트 또는 서비스 범위에서 새 등록자 구성 설정을 만들 수 있습니다. 지정된 사이트 또는 서비스에는 이러한 설정 컬렉션이 최대 한 개만 포함될 수 있습니다. 등록자 구성 설정 컬렉션이 이미 호스트되어 있는 사이트나 서비스에 새 컬렉션을 추가하려고 하면 명령이 실패합니다. 전역 범위에서 새 설정을 만들려고 하는 경우에도 명령이 실패합니다.

이 cmdlet을 실행할 수 있는 사용자: 기본적으로 RTCUniversalServerAdmins 그룹의 구성원은 **New-CsRegistrarConfiguration** cmdlet을 로컬로 실행할 수 있습니다. 사용자가 직접 만든 사용자 지정 RBAC(역할 기반 액세스 제어) 역할을 포함하여 이 cmdlet이 할당된 모든 RBAC 역할의 목록을 반환하려면 Windows PowerShell 프롬프트에서 다음 명령을 실행합니다.

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "New-CsRegistrarConfiguration"}

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
<td><p>만들려는 등록자 구성 설정의 고유 식별자입니다. 사이트 범위에서 구성된 설정을 만들려면 -Identity site:Redmond와 유사한 구문을 사용합니다. 서비스 수준에서 설정을 만들려면 -Identity service:Registrar:atl-cs-001.litwareinc.com과 유사한 구문을 사용합니다. 지정된 사이트 또는 서비스에는 등록자 설정 컬렉션이 최대 한 개만 포함될 수 있습니다. Identity가 site:Redmond인 새 컬렉션을 만들려고 하는데 Redmond 사이트에 등록자 설정 컬렉션이 이미 호스트되어 있으면 명령이 실패합니다.</p>
<p>또한 전역 범위에서는 새 등록자 설정을 만들 수 없습니다. 전역 범위에서 값을 변경하려면 <strong>Set-CsRegistrarConfiguration</strong> cmdlet을 사용합니다.</p></td>
</tr>
<tr class="even">
<td><p><em>BackupStoreUnavailableThreshold</em></p></td>
<td><p>선택</p></td>
<td><p>System.TimeSpan</p></td>
<td><p>시스템이 백업 저장소를 사용할 수 없다고 결정할 때까지 대기하는 시간을 지정합니다. 이 시간이 지나면 사용자가 지속 가능 모드로 전환됩니다. 기본값은 30분(00:30:00)입니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>Confirm</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>명령을 실행하기 전에 확인 메시지를 표시합니다.</p></td>
</tr>
<tr class="even">
<td><p><em>DefaultEndpointExpiration</em></p></td>
<td><p>선택</p></td>
<td><p>System.Int32</p></td>
<td><p>끝점은 로그온 시 만료 시간 제한을 요청할 수 있습니다. 이 옵션은 끝점이 서버에 연결하고 연장을 요청하기 전에 시스템에 로그온된 상태로 유지될 수 있는 시간 간격을 지정합니다. DefaultEndpointExpiration 속성은 특정 시간 제한 값을 요청하지 않는 클라이언트의 만료 시간 제한 간격을 나타냅니다.</p>
<p>DefaultEndpointExpiration은 300(5분)에서 900(15분) 사이여야 합니다. 기본값은 600(10분)입니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>EnableDHCPServer</em></p></td>
<td><p>선택</p></td>
<td><p>System.Boolean</p></td>
<td><p>끝점에서 DHCP 서버를 사용하여 등록자를 찾을 수 있는지 여부를 나타냅니다. True일 경우 클라이언트가 처음 시작할 때 DHCP 알림 메시지를 보내고, DHCP 서버가 사용자를 로그온시키는 데 사용할 수 있는 등록자의 FQDN(정규화된 도메인 이름)을 보내 응답합니다.</p></td>
</tr>
<tr class="even">
<td><p><em>Force</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>명령을 실행할 때 발생할 수 있는 심각하지 않은 오류 메시지를 표시하지 않습니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>InMemory</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>개체를 실제로 영구 변경 사항으로 커밋하지 않고 개체 참조를 만듭니다. 이 매개 변수와 함께 호출된 이 cmdlet의 결과를 변수로 할당하면 개체 참조의 속성을 변경한 후 이 cmdlet과 일치하는 Set- cmdlet을 호출하여 해당 변경 사항을 커밋할 수 있습니다.</p></td>
</tr>
<tr class="even">
<td><p><em>MaxEndpointExpiration</em></p></td>
<td><p>선택</p></td>
<td><p>System.Int32</p></td>
<td><p>끝점이 로그온하면 만료 시간 제한을 요청할 수 있습니다. 이는 끝점이 서버에 연결하여 연장을 요청하기 전까지 시스템에 로그온 상태로 있을 수 있는 시간 간격을 지정합니다. MaxEndpointExpiration 속성은 클라이언트에 부여할 수 있는 최대 시간을 나타냅니다. 예를 들어 최대 시간이 600초로 설정되고 클라이언트가 시간 제한 간격으로 800초를 요청하는 경우 클라이언트에 제공되는 최대 허용 만료 기간은 600초입니다.</p>
<p>MaxEndpointExpiration은 300(5분)에서 900(15분) 사이여야 합니다. 기본값은 900입니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>MaxEndpointsPerUser</em></p></td>
<td><p>선택</p></td>
<td><p>System.UInt16</p></td>
<td><p>사용자가 동시에 시스템에 연결할 수 있는 최대 끝점 수를 나타냅니다. 예를 들어 컴퓨터와 휴대폰을 동시에 사용하여 Lync Server에 로그온한 사용자는 2개의 끝점을 사용하는 것입니다. MaxEndpointsPerUser는 1에서 64(포함) 사이의 값으로 설정해야 합니다. 기본값은 8입니다.</p>
<p>사용자에게 끝점을 64개까지 허용할 수는 있지만 최대 끝점 수가 8을 초과하지 않는 것이 좋습니다. 9 이상의 값은 드물지만 Microsoft 지원 담당자가 제안한 경우 이전 버전과의 호환성을 위해 사용됩니다. 새 배포의 경우 최대 끝점 수가 8을 초과해서는 안 됩니다.</p>
<p>최대 끝점 수는 개별 사용자에게 여러 클라이언트에서 로그인을 제공하기 위한 것입니다. 따라서 이 설정은 전체 부서와 같은 사용자 그룹이 아닌 개별 사용자를 위해 만들어졌습니다.</p></td>
</tr>
<tr class="even">
<td><p><em>MaxUserCount</em></p></td>
<td><p>선택</p></td>
<td><p>System.UInt64</p></td>
<td><p>등록자에 동시에 로그온할 수 있는 최대 사용자 수를 나타냅니다. MaxUserCount는 2000에서 100000(포함) 사이의 정수 값으로 설정할 수 있습니다. 기본값은 12000입니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>MinEndpointExpiration</em></p></td>
<td><p>선택</p></td>
<td><p>System.Int32</p></td>
<td><p>끝점이 로그온하면 만료 시간 제한을 요청할 수 있습니다. 이는 끝점이 서버에 연결하여 연장을 요청하기 전까지 시스템에 로그온 상태로 있을 수 있는 시간 간격을 지정합니다. MinEndpointExpiration 속성은 클라이언트에 부여할 수 있는 최소 시간을 나타냅니다. 예를 들어 최소 시간이 600초로 설정되고 클라이언트가 시간 제한 간격으로 200초를 요청하는 경우 클라이언트에 제공되는 최소 허용 만료 기간은 600초입니다.</p>
<p>MinEndpointExpiration은 300(5분)에서 900(15분) 사이여야 합니다. 기본값은 300입니다.</p></td>
</tr>
<tr class="even">
<td><p><em>PoolState</em></p></td>
<td><p>선택</p></td>
<td><p>Microsoft.Rtc.Management.WritableConfig.Settings.Registrar.PoolState</p></td>
<td><p>등록자 풀의 현재 상태입니다. 사용 가능한 값은 다음과 같습니다.</p>
<p>* Active</p>
<p>* FailedOver</p>
<p>* FailingOver</p>
<p>* FailedBack</p>
<p>기본값은 Active입니다.</p></td>
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

없음. **New-CsRegistrarConfiguration** cmdlet은 파이프라인된 입력을 허용하지 않습니다.

## 반환 형식

**New-CsRegistrarConfiguration** cmdlet은 Microsoft.Rtc.Management.WritableConfig.Settings.Registrar.RegistrarSettings 개체의 새 인스턴스를 만듭니다.

## 참고 항목

#### 기타 리소스

[Get-CsRegistrarConfiguration](get-csregistrarconfiguration.md)  
[Remove-CsRegistrarConfiguration](remove-csregistrarconfiguration.md)  
[Set-CsRegistrarConfiguration](set-csregistrarconfiguration.md)

