---
title: Set-CsExternalAccessPolicy
TOCTitle: Set-CsExternalAccessPolicy
ms:assetid: d3e45fbb-357f-4ff2-b52d-58b94e8f2241
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg398916(v=OCS.15)
ms:contentKeyID: 49305146
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Set-CsExternalAccessPolicy

 

_**마지막으로 수정된 항목:** 2015-03-09_

기존 외부 액세스 정책의 속성을 수정하는 데 사용됩니다. 외부 액세스 정책은 사용자가 1) 페더레이션 조직의 SIP(Session Initiation Protocol) 계정을 가진 사용자와 통신할 수 있는지 여부, 2) MSN과 같은 공용 메신저 공급자의 SIP 계정을 가진 사용자와 통신할 수 있는지 여부 및 3) 내부 네트워크에 로그온하지 않고도 인터넷을 통해 Lync Server에 액세스할 수 있는지 여부를 결정합니다. 이 cmdlet은 Lync Server 2010에서 도입되었습니다.

## 구문

    Set-CsExternalAccessPolicy [-Identity <XdsIdentity>] <COMMON PARAMETERS>

    Set-CsExternalAccessPolicy [-Instance <PSObject>] <COMMON PARAMETERS>

    COMMON PARAMETERS: [-Confirm [<SwitchParameter>]] [-Description <String>] [-EnableFederationAccess <$true | $false>] [-EnableOutsideAccess <$true | $false>] [-EnablePublicCloudAccess <$true | $false>] [-EnablePublicCloudAudioVideoAccess <$true | $false>] [-EnableXmppAccess <$true | $false>] [-Force <SwitchParameter>] [-WhatIf [<SwitchParameter>]]

## 예제

## 예제 1

예제 1에 표시된 명령은 ID가 RedmondExternalAccessPolicy인 사용자별 외부 액세스 정책을 수정합니다. 이 예제의 명령은 EnableFederationAccess 속성 값을 True로 변경합니다.

    Set-CsExternalAccessPolicy -Identity RedmondExternalAccessPolicy -EnableFederationAccess $True

## 예제 2

예제 2에서는 조직에서 사용하도록 구성된 모든 외부 액세스 정책에 대해 페더레이션 액세스를 사용하도록 설정합니다. 이 작업을 수행하기 위해 명령은 먼저 매개 변수 없이 **Get-CsExternalAccessPolicy** cmdlet을 호출하여 현재 사용하도록 구성된 모든 외부 정책 컬렉션을 반환합니다. 이 컬렉션은 컬렉션의 각 정책에 대한 EnableFederationAccess 속성 값을 변경하는 **Set-CsExternalAccessPolicy** cmdlet에 파이프됩니다.

    Get-CsExternalAccessPolicy | Set-CsExternalAccessPolicy -EnableFederationAccess $True

## 예제 3

예제 3에서는 사용자별 범위에서 구성된 모든 외부 액세스 정책에 대해 페더레이션 액세스를 사용하도록 설정합니다. 이 작업을 수행하기 위해 명령은 먼저 **Get-CsExternalAcessPolicy** cmdlet 및 Filter 매개 변수를 사용하여 사용자별 범위에서 구성된 모든 정책 컬렉션을 반환합니다. 필터 값 "tag:\*"는 반환되는 데이터를 ID가 문자열 값 "tag:"으로 시작하는 정책으로 제한합니다. ID가 "tag:"으로 시작하는 정책은 사용자별 범위에서 구성된 정책입니다. 그런 다음 필터링된 컬렉션은 컬렉션의 각 정책에 대한 EnableFederationAccess 속성을 수정하는 **Set-CsExternalAccessPolicy** cmdlet에 파이프됩니다.

    Get-CsExternalAccessPolicy -Filter tag:* | Set-CsExternalAccessPolicy -EnableFederationAccess $True

## 예제 4

예제 4에서는 공용 클라우드 액세스를 허용하는 모든 외부 액세스 정책에 대해 페더레이션 액세스를 사용하도록 설정합니다. 이 작업을 수행하기 위해 명령은 먼저 **Get-CsExternalAccessPolicy** cmdlet을 사용하여 조직에서 현재 사용하도록 구성된 모든 외부 액세스 정책 컬렉션을 반환합니다. 이 컬렉션은 EnablePublicCloudAccess 속성이 True와 같은 정책만 선택하는 **Where-Object** cmdlet에 파이프됩니다. 그런 다음 필터링된 컬렉션은 각 정책을 가져와 EnableFederationAccess 속성을 True로 설정하는 **Set-CsExternalAccessPolicy** cmdlet에 파이프됩니다. 그러면 공용 클라우드 액세스를 허용하는 모든 외부 액세스 정책에서 페더레이션 액세스도 허용하게 됩니다.

    Get-CsExternalAccessPolicy | Where-Object {$_.EnablePublicCloudAccess -eq $True} | Set-CsExternalAccessPolicy -EnableFederationAccess $True

## 자세한 정보

Lync Server를 설치하면 내부 사용자들만 서로 메신저 대화 및 현재 상태 정보를 교환할 수 있습니다. 기본적으로 Active Directory 도메인 서비스에 SIP 계정이 있는 사용자와만 통신할 수 있습니다. 또한 인터넷을 통해 Lync Server에 액세스할 수 없습니다. 대신 Lync Server에 로그온하려면 먼저 내부 네트워크에 로그온해야 합니다.

이것만으로도 통신 요구를 충분히 만족시킬 수 있을 것입니다. 그러나 이 정도로 부족한 경우 외부 액세스 정책을 사용하여 통신 및 공동 작업 기능을 확장할 수 있습니다. 외부 액세스 정책은 사용자에게 다음과 같은 작업의 일부 또는 전부를 수행할 수 있는 권한을 부여하거나 이러한 권한을 해지할 수 있습니다.

1\. 페더레이션 조직의 SIP 계정을 가진 사용자와 통신 - 페더레이션을 사용하도록 설정하는 것만으로는 이러한 기능이 제공되지 않습니다. 대신 페더레이션을 사용하도록 설정한 다음, 사용자에게 페더레이션 사용자와 통신할 권한을 제공하는 외부 액세스 정책을 할당해야 합니다.

2\. MSN과 같은 공용 메시지 서비스의 SIP 계정을 가진 사용자와 통신합니다.

3\. 내부 네트워크에 로그온하지 않고도 인터넷을 통해 Lync Server에 액세스 - 이 경우 사용자는 인터넷 카페 또는 기타 원격 위치에서 Lync를 사용하고 Lync Server에 로그온할 수 있습니다.

외부 액세스 정책을 만든 후에는 **Set-CsExternalAccessPolicy** cmdlet을 사용하여 해당 정책의 속성 값을 변경할 수 있습니다. 예를 들어 기본적으로 전역 정책은 사용자가 페더레이션 조직의 계정을 가진 다른 사용자와 통신하는 것을 허용하지 않습니다. 이 기능을 모든 사용자에게 부여하려면 **Set-CsExternalAccessPolicy** cmdlet을 호출하고 전역 정책의 EnableFederationAccess 속성 값을 True로 설정하면 됩니다.

이 cmdlet을 실행할 수 있는 사용자: 기본적으로 RTCUniversalServerAdmins 그룹의 구성원은 **Set-CsExternalAccessPolicy** cmdlet을 로컬로 실행할 수 있습니다. 사용자가 직접 만든 사용자 지정 RBAC(역할 기반 액세스 제어) 역할을 포함하여 이 cmdlet이 할당된 모든 RBAC 역할의 목록을 반환하려면 Windows PowerShell 프롬프트에서 다음 명령을 실행합니다.

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Set-CsExternalAccessPolicy"}

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
<td><p><em>Confirm</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>명령을 실행하기 전에 확인 메시지를 표시합니다.</p></td>
</tr>
<tr class="even">
<td><p><em>Description</em></p></td>
<td><p>선택</p></td>
<td><p>System.String</p></td>
<td><p>관리자가 정책과 함께 표시할 추가 텍스트를 제공할 수 있습니다. 예를 들어 정책을 할당할 사용자에 대한 정보를 설명에 포함할 수 있습니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>EnableFederationAccess</em></p></td>
<td><p>선택</p></td>
<td><p>System.Boolean</p></td>
<td><p>사용자가 페더레이션 조직의 SIP 계정을 가진 다른 사용자와 통신할 수 있는지 여부를 나타냅니다. 기본값은 False입니다.</p></td>
</tr>
<tr class="even">
<td><p><em>EnableOutsideAccess</em></p></td>
<td><p>선택</p></td>
<td><p>System.Boolean</p></td>
<td><p>사용자가 조직의 내부 네트워크에 로그온하지 않고 인터넷을 통해 Lync Server에 연결할 수 있는지 여부를 나타냅니다. 기본값은 False입니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>EnablePublicCloudAccess</em></p></td>
<td><p>선택</p></td>
<td><p>System.Boolean</p></td>
<td><p>사용자가 MSN과 같은 공용 인터넷 연결 공급자의 SIP 계정을 가진 다른 사용자와 통신할 수 있는지 여부를 나타냅니다. 기본값은 False입니다.</p></td>
</tr>
<tr class="even">
<td><p><em>EnablePublicCloudAudioVideoAccess</em></p></td>
<td><p>선택</p></td>
<td><p>System.Boolean</p></td>
<td><p>사용자가 MSN과 같은 공용 인터넷 연결 공급자의 SIP 계정을 가진 다른 사용자와 음성/화상 채팅을 할 수 있는지 여부를 나타냅니다. False로 설정하면 사용자가 공용 인터넷 연결 대화 상대와 통신할 때마다 Lync의 오디오 및 비디오 옵션이 표시됩니다. 기본값은 False입니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>EnableXmppAccess</em></p></td>
<td><p>선택</p></td>
<td><p>System.Boolean</p></td>
<td><p>사용자가 페더레이션 XMPP(Extensible Messaging and Presence Protocol) 파트너의 SIP 계정을 가진 사용자와 통신할 수 있는지 여부를 나타냅니다. 기본값은 False입니다.</p></td>
</tr>
<tr class="even">
<td><p><em>Force</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>명령을 실행할 때 발생할 수 있는 심각하지 않은 오류 메시지를 표시하지 않습니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>Identity</em></p></td>
<td><p>선택</p></td>
<td><p>Microsoft.Rtc.Management.Xds.XdsIdentity</p></td>
<td><p>수정할 외부 액세스 정책의 고유 식별자입니다. 외부 액세스 정책은 전역 범위, 사이트 범위 또는 사용자별 범위에서 구성할 수 있습니다. 전역 정책을 수정하려면 -Identity global 구문을 사용하고, 사이트 정책을 수정하려면 -Identity site:Redmond와 유사한 구문을 사용하십시오. 또한 사용자별 정책을 수정하려면 -Identity SalesAccessPolicy 구문을 사용하십시오. 이 매개 변수를 지정하지 않으면 전역 정책이 수정됩니다.</p>
<p>ID를 지정할 때는 와일드카드를 사용할 수 없습니다.</p></td>
</tr>
<tr class="even">
<td><p><em>Instance</em></p></td>
<td><p>선택</p></td>
<td><p>외부 액세스 정책 개체</p></td>
<td><p>개별 매개 변수 값을 설정하는 대신 cmdlet에 개체에 대한 참조를 전달할 수 있습니다.</p></td>
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

Microsoft.Rtc.Management.WritableConfig.Policy.ExternalAccess.ExternalAccessPolicy 개체입니다. **Set-CsExternalAccessPolicy** cmdlet은 외부 액세스 정책 개체의 파이프라인된 입력을 허용합니다.

## 반환 형식

**Set-CsExternalAccessPolicy** cmdlet은 값이나 개체를 반환하지 않습니다. 대신에 이 cmdlet은 Microsoft.Rtc.Management.WritableConfig.Policy.ExternalAccess.ExternalAccessPolicy 개체의 인스턴스를 구성합니다.

## 참고 항목

#### 기타 리소스

[Get-CsExternalAccessPolicy](get-csexternalaccesspolicy.md)  
[Grant-CsExternalAccessPolicy](grant-csexternalaccesspolicy.md)  
[New-CsExternalAccessPolicy](new-csexternalaccesspolicy.md)  
[Remove-CsExternalAccessPolicy](remove-csexternalaccesspolicy.md)

