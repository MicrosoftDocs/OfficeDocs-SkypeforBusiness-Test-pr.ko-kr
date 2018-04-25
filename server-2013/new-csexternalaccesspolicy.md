---
title: New-CsExternalAccessPolicy
TOCTitle: New-CsExternalAccessPolicy
ms:assetid: 624a878e-6bbf-4e8b-9a5e-e7b5521fa4c1
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg398441(v=OCS.15)
ms:contentKeyID: 49303829
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# New-CsExternalAccessPolicy

 

_**마지막으로 수정된 항목:** 2015-03-09_

새 외부 액세스 정책을 만들 수 있습니다. 외부 액세스 정책은 사용자가 1) 페더레이션 조직의 SIP(Session Initiation Protocol) 계정을 가진 사용자와 통신할 수 있는지 여부, 2) MSN과 같은 공용 메신저 공급자의 SIP 계정을 가진 사용자와 통신할 수 있는지 여부 및 3) 내부 네트워크에 로그온하지 않고도 인터넷을 통해 Lync Server에 액세스할 수 있는지 여부를 결정합니다. 이 cmdlet은 Lync Server 2010에서 도입되었습니다.

## 구문

    New-CsExternalAccessPolicy -Identity <XdsIdentity> [-Confirm [<SwitchParameter>]] [-Description <String>] [-EnableFederationAccess <$true | $false>] [-EnableOutsideAccess <$true | $false>] [-EnablePublicCloudAccess <$true | $false>] [-EnablePublicCloudAudioVideoAccess <$true | $false>] [-EnableXmppAccess <$true | $false>] [-Force <SwitchParameter>] [-InMemory <SwitchParameter>] [-WhatIf [<SwitchParameter>]]

## 예제

## 예제 1

예제 1에 표시된 명령은 ID가 site:Redmond인 새 외부 액세스 정책을 만듭니다. 이 정책은 생성되는 즉시 Redmond 사이트에 자동으로 할당됩니다. 이 새 정책은 EnableFederationAccess 및 EnableOutsideAccess 속성을 모두 True로 설정합니다.

    New-CsExternalAccessPolicy -Identity site:Redmond -EnableFederationAccess $True -EnableOutsideAccess $True

## 예제 2

예제 2에서는 InMemory 매개 변수의 사용법을 보여 줍니다. 이 매개 변수를 사용하여 외부 액세스 정책의 메모리 내부 전용 인스턴스를 만들 수 있습니다. 메모리 내부 전용 인스턴스가 생성되면 이 인스턴스를 수정한 다음 **Set-CsExternalAccessPolicy** cmdlet을 사용하여 가상 정책을 실제 외부 액세스 정책으로 변환할 수 있습니다.

이 작업을 수행하기 위해 예제의 첫 번째 명령은 **New-CsExternalAccessPolicy** cmdlet 및 InMemory 매개 변수를 호출하여 ID가 RedmondAccessPolicy인 가상 정책을 만듭니다. 이 가상 정책은 $x라는 변수에 저장됩니다. 이 명령 다음에 나오는 EnableFederationAccess, EnablePublicCloudAccess 및 EnableOutsideAccess 세 명령은 가상 정책의 세 가지 속성을 수정하는 데 사용됩니다. 마지막 명령은 **Set-CsExternalAccessPolicy** cmdlet을 사용하여 ID가 RedmondAccessPolicy인 실제 사용자별 외부 액세스 정책을 만듭니다. **Set-CsExternalAccessPolicy** cmdlet을 호출하지 않으면 Windows PowerShell 세션을 종료하거나 변수 $x를 삭제하는 즉시 가상 정책이 사라집니다. 이 경우 ID가 RedmondAccessPolicy인 외부 액세스 정책이 만들어지지 않습니다.

``` 
$x = New-CsExternalAccessPolicy -Identity RedmondAccessPolicy -InMemory
$x.EnableFederationAccess = $True
$x.EnablePublicCloudAccess = $True
$x.EnableOutsideAccess = $True
Set-CsExternalAccessPolicy -Instance $x  
```

## 자세한 정보

Lync Server를 설치하면 내부 사용자들만 서로 메신저 대화 및 현재 상태 정보를 교환할 수 있습니다. 기본적으로 Active Directory 도메인 서비스에 SIP 계정이 있는 다른 사용자와만 통신할 수 있습니다. 또한 인터넷을 통해 Lync Server에 액세스할 수 없습니다. 대신 Lync Server에 로그온하려면 먼저 내부 네트워크에 로그온해야 합니다.

대부분의 사용자는 이것만으로 통신 요구 사항이 충족됩니다. 요구 사항이 충족되지 않는 경우 외부 액세스 정책을 사용하여 사용자가 통신하고 공동 작업할 수 있는 권한을 확장할 수 있습니다. 외부 액세스 정책은 사용자에게 다음 중 일부 또는 전부를 수행할 수 있는 권한을 부여하거나 해지할 수 있습니다.

1\. 페더레이션 조직의 SIP 계정을 가진 사용자와 통신 - 페더레이션을 사용하도록 설정하는 것만으로는 이러한 기능이 제공되지 않습니다. 대신 페더레이션을 사용하도록 설정한 다음, 사용자에게 페더레이션 사용자와 통신할 권한을 제공하는 외부 액세스 정책을 할당해야 합니다.

2\. MSN과 같은 공용 메시지 서비스의 SIP 계정을 가진 사용자와 통신합니다.

3\. 내부 네트워크에 로그온하지 않고도 인터넷을 통해 Lync Server에 액세스 - 이 경우 사용자는 인터넷 카페 또는 기타 원격 위치에서 Lync Server를 사용하고 Lync Server에 로그온할 수 있습니다.

Lync Server를 설치하면 전역 외부 액세스 정책이 자동으로 만들어집니다. 전역 정책 외에도 사이트 또는 사용자별 범위에 사용자 지정 외부 액세스 정책을 만들 수도 있습니다. 사이트 범위에 외부 액세스 정책을 만들면 해당 정책이 생성되는 즉시 사이트에 자동으로 할당됩니다. 사용자별 범위에 외부 액세스 정책을 만들면 해당 정책이 생성되지만 어느 사용자에게도 할당되지 않습니다. 사용자 또는 사용자 그룹에 정책을 할당하려면 **Grant-CsExternalAccessPolicy** cmdlet을 사용합니다.

새 외부 액세스 정책은 **New-CsExternalAccessPolicy** cmdlet을 사용하여 만들 수 있습니다. 이러한 정책은 사이트 또는 사용자별 범위에서만 만들 수 있습니다. 전역 범위에서는 새 정책을 만들 수 없습니다. 또한 사이트당 하나의 외부 액세스 정책만 유지할 수 있습니다. Redmond 사이트에 외부 액세스 정책이 이미 할당되어 있으면 이 사이트에 대한 두 번째 정책을 만들 수 없습니다.

이 cmdlet을 실행할 수 있는 사용자: 기본적으로 RTCUniversalServerAdmins 그룹의 구성원은 **New-CsExternalAccessPolicy** cmdlet을 로컬로 실행할 수 있습니다. 사용자가 직접 만든 사용자 지정 RBAC(역할 기반 액세스 제어) 역할을 포함하여 이 cmdlet이 할당된 모든 RBAC 역할의 목록을 반환하려면 Windows PowerShell 프롬프트에서 다음 명령을 실행합니다.

    Get-CsAdminRole | Where-Object  {$_.Cmdlets -match "New-CsExternalAccessPolicy"}

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
<td><p>정책에 할당할 고유 ID입니다. 새 외부 액세스 정책은 사이트 또는 사용자별 범위에 만들 수 있습니다. 새 사이트 정책을 만들려면 &quot;site:&quot; 접두사와 사이트 이름을 ID로 사용합니다. 예를 들어 Redmond 사이트에 대한 새 정책을 만들려면 -Identity site:Redmond 구문을 사용합니다. 새 사용자별 정책을 만들려면 -Identity SalesAccessPolicy와 유사한 ID를 사용합니다.</p>
<p>전역 정책은 새로 만들 수 없습니다. 대신 <strong>Set-CsExternalAccessPolicy</strong> cmdlet을 사용하여 전역 정책을 변경할 수는 있습니다. 마찬가지로 ID가 이미 존재하는 새 사이트 또는 사용자별 정책은 만들 수 없습니다. 기존 정책을 변경해야 하는 경우 <strong>Set-CsExternalAccessPolicy</strong> cmdlet을 사용합니다.</p></td>
</tr>
<tr class="even">
<td><p><em>Confirm</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>명령을 실행하기 전에 확인 메시지를 표시합니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>Description</em></p></td>
<td><p>선택</p></td>
<td><p>System.String</p></td>
<td><p>관리자가 정책과 함께 표시할 설명 텍스트를 제공할 수 있습니다. 예를 들어 정책을 할당할 사용자에 대한 정보를 설명에 포함할 수 있습니다.</p></td>
</tr>
<tr class="even">
<td><p><em>EnableFederationAccess</em></p></td>
<td><p>선택</p></td>
<td><p>System.Boolean</p></td>
<td><p>사용자가 페더레이션 조직의 SIP 계정을 가진 다른 사용자와 통신할 수 있는지 여부를 나타냅니다. 기본값은 False입니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>EnableOutsideAccess</em></p></td>
<td><p>선택</p></td>
<td><p>System.Boolean</p></td>
<td><p>사용자가 조직의 내부 네트워크에 로그온하지 않고 인터넷을 통해 Lync Server에 연결할 수 있는지 여부를 나타냅니다. 기본값은 False입니다.</p></td>
</tr>
<tr class="even">
<td><p><em>EnablePublicCloudAccess</em></p></td>
<td><p>선택</p></td>
<td><p>System.Boolean</p></td>
<td><p>사용자가 MSN과 같은 공용 인터넷 연결 공급자의 SIP 계정을 가진 다른 사용자와 통신할 수 있는지 여부를 나타냅니다. 기본값은 False입니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>EnablePublicCloudAudioVideoAccess</em></p></td>
<td><p>선택</p></td>
<td><p>System.Boolean</p></td>
<td><p>사용자가 MSN과 같은 공용 인터넷 연결 공급자의 SIP 계정을 가진 다른 사용자와 음성/화상 채팅을 할 수 있는지 여부를 나타냅니다. False로 설정하면 사용자가 공용 인터넷 연결 대화 상대와 통신할 때마다 Lync Server의 오디오 및 비디오 옵션이 표시됩니다.</p></td>
</tr>
<tr class="even">
<td><p><em>EnableXmppAccess</em></p></td>
<td><p>선택</p></td>
<td><p>System.Boolean</p></td>
<td><p>사용자가 페더레이션 XMPP(Extensible Messaging and Presence Protocol) 파트너의 SIP 계정을 가진 사용자와 통신할 수 있는지 여부를 나타냅니다. 기본값은 False입니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>Force</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>명령을 실행할 때 발생할 수 있는 심각하지 않은 오류 메시지를 표시하지 않습니다.</p></td>
</tr>
<tr class="even">
<td><p><em>InMemory</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>개체를 실제로 영구 변경 사항으로 커밋하지 않고 개체 참조를 만듭니다. 이 매개 변수와 함께 호출된 이 cmdlet의 결과를 변수로 할당하면 개체 참조의 속성을 변경한 후 이 cmdlet과 일치하는 Set- cmdlet을 호출하여 해당 변경 사항을 커밋할 수 있습니다.</p></td>
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

없음. **New-CsExternalAccessPolicy** cmdlet은 파이프라인된 입력을 허용하지 않습니다.

## 반환 형식

Microsoft.Rtc.Management.WritableConfig.Policy.ExternalAccess.ExternalAccessPolicy 개체의 새 인스턴스를 만듭니다.

## 참고 항목

#### 기타 리소스

[Get-CsExternalAccessPolicy](get-csexternalaccesspolicy.md)  
[Grant-CsExternalAccessPolicy](grant-csexternalaccesspolicy.md)  
[Remove-CsExternalAccessPolicy](remove-csexternalaccesspolicy.md)  
[Set-CsExternalAccessPolicy](set-csexternalaccesspolicy.md)

