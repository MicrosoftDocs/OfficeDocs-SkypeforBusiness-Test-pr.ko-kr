---
title: Remove-CsPublicProvider
TOCTitle: Remove-CsPublicProvider
ms:assetid: b9eec2f4-cf36-41b7-8023-67790cc8d4cd
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg412906(v=OCS.15)
ms:contentKeyID: 49304840
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Remove-CsPublicProvider

 

_**마지막으로 수정된 항목:** 2015-03-09_

조직에서 사용하도록 구성된 공용 공급자를 제거합니다. 공용 공급자는 메신저, 현재 상태 및 관련 서비스를 일반 대중에 제공하는 조직입니다. Lync Server에는 Yahoo\!, AIM(AOL) 및 Messenger(MSN)가 함께 제공되는데, 이러한 공용 공급자는 구성되어 있지만 사용하도록 설정되어 있지는 않습니다. 이 cmdlet은 Lync Server 2010에서 도입되었습니다.

## 구문

    Remove-CsPublicProvider -Identity <XdsGlobalRelativeIdentity> [-Confirm [<SwitchParameter>]] [-Force <SwitchParameter>] [-WhatIf [<SwitchParameter>]]

## 예제

## 예제 1

예제 1에서는 ID가 Messenger인 공용 공급자를 삭제합니다. 이 명령이 완료된 후에는 구성된 공용 공급자 목록에 Messenger가 더 이상 표시되지 않습니다. 이 경우 Messenger와의 페더레이션을 다시 설정하려면 해당 공급자를 다시 만드는 방법밖에 없습니다.

    Remove-CsPublicProvider -Identity "Messenger"

## 예제 2

예제 2에서는 조직에서 사용하도록 구성된 모든 공용 공급자를 삭제합니다. 이 작업을 수행하기 위해 명령은 먼저 **Get-CsPublicProvider** cmdlet을 사용하여 현재 사용하도록 구성된 모든 공용 공급자 컬렉션을 반환합니다. 이 컬렉션은 컬렉션의 각 공급자를 삭제하는 **Remove-CsPublicProvider** cmdlet에 파이프됩니다.

    Get-CsPublicProvider | Remove-CsPublicProvider

## 예제 3

예제 3에서는 현재 사용하지 않도록 설정된 모든 공용 공급자를 구성된 공용 공급자 집합에서 제거합니다. 이 작업을 수행하기 위해 명령은 먼저 **Get-CsPublicProvider** cmdlet을 사용하여 현재 사용 중인 모든 RBAC 역할의 컬렉션을 반환합니다. 이 컬렉션은 Enabled 속성이 False와 같은 공급자만 선택하는 **Where-Object** cmdlet에 파이프됩니다. 그런 다음 필터링된 컬렉션은 컬렉션의 모든 항목을 삭제하는 **Remove-CsPublicProvider** cmdlet에 파이프됩니다.

    Get-CsPublicProvider | Where-Object {$_.Enabled -eq $False} | Remove-CsPublicProvider

## 자세한 정보

페더레이션은 두 조직에서 두 그룹 간의 통신을 용이하게 하는 트러스트 관계를 설정할 수 있는 수단입니다. 페더레이션이 설정되면 두 조직의 사용자가 서로 인스턴스 메시지를 보내고, 현재 상태 알림에 가입하고, Lync 2013과 같은 SIP 응용 프로그램을 사용하여 통신할 수 있습니다. Lync Server를 사용하면 1) 사용자 조직과 다른 조직 간의 직접 페더레이션, 2) 사용자 조직과 공용 공급자 간의 페더레이션 및 3) 사용자 조직과 타사 호스팅 공급자 간의 페더레이션이라는 세 가지 유형의 페더레이션을 설정할 수 있습니다.

공용 공급자는 일반인에게 SIP 통신 서비스를 제공하는 조직입니다. 공용 공급자와의 페더레이션 관계를 설정하면 해당 공급자가 호스트하는 계정을 가진 사용자와의 페더레이션을 효과적으로 설정할 수 있습니다. 예를 들어 Messenger(MSN)와 페더레이션한 경우 사용자가 Messenger 계정을 가진 다른 사용자와 메신저 대화 및 현재 상태 정보를 교환할 수 있습니다.

공용 공급자와 페더레이션하려면 새 공용 공급자를 만들고 사용하도록 설정해야 합니다. 또한 해당 공용 공급자가 사용자와 페더레이션 관계를 만들어야 합니다. 나중에 이 관계를 종료하기로 결정한 경우 **Remove-CsPublicProvider** cmdlet을 사용하여 공용 공급자를 삭제할 수 있습니다. 공용 공급자를 삭제하면 페더레이션 파트너 목록에서 해당 공급자가 제거됩니다. 이 경우 관계를 다시 설정하려면 공급자를 다시 만드는 방법밖에 없습니다. 일시적으로 관계를 중단하려면 대신 **Disable-CsPublicProvider** cmdlet을 사용합니다. 공용 공급자를 사용하지 않도록 설정하면 해당 공급자가 페더레이션 파트너 목록에서 삭제되지 않고 대신 사용하지 않도록 설정된 것으로 표시되며 사용자 조직과 해당 공급자 간의 통신이 일시 중단됩니다. 관계를 다시 설정하려면 **Enable-CsPublicProvider** cmdlet을 사용하여 해당 공급자를 다시 설정하기만 하면 됩니다.

이 cmdlet을 실행할 수 있는 사용자: 기본적으로 RTCUniversalServerAdmins 그룹의 구성원은 **Remove-CsPublicProvider** cmdlet을 로컬로 실행할 수 있습니다. 사용자가 직접 만든 사용자 지정 RBAC(역할 기반 액세스 제어) 역할을 포함하여 이 cmdlet이 할당된 모든 RBAC 역할의 목록을 반환하려면 Windows PowerShell 프롬프트에서 다음 명령을 실행합니다.

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Remove-CsPublicProvider"}

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
<td><p>Microsoft.Rtc.Management.Xds.XdsGlobalRelativeIdentity</p></td>
<td><p>제거할 공용 공급자의 고유 식별자입니다. Identity는 일반적으로 서비스를 제공하는 웹 사이트(예: Yahoo!, AOL, MSN 등)의 이름입니다.</p></td>
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

Microsoft.Rtc.Management.WritableConfig.Settings.Edge.DisplayPublicProvider 개체입니다. **Remove-CsPublicProvider** cmdlet은 공용 공급자 개체의 파이프라인된 인스턴스를 허용합니다.

## 반환 형식

없음. 대신 이 cmdlet은 Microsoft.Rtc.Management.WritableConfig.Settings.Edge.DisplayPublicProvider 개체의 인스턴스를 삭제합니다.

## 참고 항목

#### 기타 리소스

[Disable-CsPublicProvider](disable-cspublicprovider.md)  
[Enable-CsPublicProvider](enable-cspublicprovider.md)  
[Get-CsPublicProvider](get-cspublicprovider.md)  
[New-CsPublicProvider](new-cspublicprovider.md)  
[Set-CsPublicProvider](set-cspublicprovider.md)

