---
title: New-CsPublicProvider
TOCTitle: New-CsPublicProvider
ms:assetid: 0b2dcb40-13f8-4ce6-b537-527d34895ceb
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg398161(v=OCS.15)
ms:contentKeyID: 49302767
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# New-CsPublicProvider

 

_**마지막으로 수정된 항목:** 2015-03-09_

새 공용 공급자와 페더레이션 관계를 만듭니다. 공용 공급자는 일반 대중에게 메신저, 현재 상태 및 관련 서비스를 제공하는 조직입니다. Lync Server에는 Yahoo, AIM(AOL) 및 Messenger(MSN)가 함께 제공되는데, 이 3개 공용 공급자는 구성되어 있지만 사용하도록 설정되어 있지는 않습니다. 이 cmdlet은 Lync Server 2010에서 도입되었습니다.

## 구문

    New-CsPublicProvider -Identity <XdsGlobalRelativeIdentity> -Enabled <$true | $false> -ProxyFqdn <String> [-Confirm [<SwitchParameter>]] [-Force <SwitchParameter>] [-IconUrl <String>] [-InMemory <SwitchParameter>] [-VerificationLevel <AlwaysVerifiable | AlwaysUnverifiable | UseSourceVerification>] [-WhatIf [<SwitchParameter>]]

## 예제

## 예제 1

예제 1에 표시된 명령은 ID가 Fabrikam인 공용 공급자와 새 페더레이션 관계를 만듭니다. Identity를 지정할 뿐 아니라 ProxyFQDN(proxyserver.fabrikam.com으로 설정됨) 및 Enabled(이 경우 True로 설정됨) 속성 값(및 해당 매개 변수)도 설정해야 합니다.

    New-CsPublicProvider -Identity "Fabrikam" -ProxyFqdn "proxyserver.fabrikam.com" -Enabled $True

## 예제 2

예제 2에서는 새 공용 공급자를 메모리에만 만들고 해당 공급자의 속성을 수정한 다음 가상 공급자를 조직에서 사용할 수 있는 실제 공급자로 전환하는 방법을 보여 줍니다. 이 작업을 위해 예제의 첫 번째 명령은 ID가 Fabrikam인 공용 공급자를 만듭니다. 이 명령은 필요한 매개 변수(Identity, ProxyFQDN 및 Enabled)를 포함할 뿐 아니라 InMemory 매개 변수를 추가합니다. 이렇게 하면 변수 $x에 저장된 공급자의 메모리 전용 인스턴스가 만들어집니다.

공급자의 메모리 내부 인스턴스가 만들어지면 이 예제의 두 번째 명령이 가상 공급자의 VerificationLevel을 수정합니다. 마지막 명령은 **Set-CsPublicProvider** cmdlet을 사용하여 $x에 저장된 가상 공급자를 실제 공용 공급자로 전환합니다. **Set-CsPublicProvider** cmdlet을 호출하지 않으면 실제 공급자가 만들어지지 않습니다. 또한 Windows PowerShell 세션을 종료하거나 변수 $x를 삭제하는 즉시 가상 공급자가 사라집니다.

    $x = New-CsPublicProvider -Identity "Fabrikam" -ProxyFqdn "proxyserver.fabrikam.com" -Enabled $True -InMemory
    $x.VerificationLevel = "AlwaysUnverifiable"
    Set-CsPublicProvider -Instance $x

## 자세한 정보

페더레이션은 두 조직에서 두 그룹 간의 통신을 용이하게 하는 트러스트 관계를 설정할 수 있는 수단입니다. 페더레이션이 설정되면 두 조직의 사용자가 서로 메신저 대화를 보내고, 현재 상태 알림에 가입하고, Lync 2013과 같은 SIP 응용 프로그램을 사용하여 통신할 수 있습니다. Lync Server를 사용하면 1) 사용자 조직과 다른 조직 간의 직접 페더레이션, 2) 사용자 조직과 공용 공급자 간의 페더레이션 및 3) 사용자 조직과 타사 호스팅 공급자 간의 페더레이션이라는 세 가지 유형의 페더레이션을 설정할 수 있습니다.

공용 공급자는 일반인에게 SIP 통신 서비스를 제공하는 조직입니다. 공용 공급자와의 페더레이션 관계를 설정하면 해당 공급자가 호스트하는 계정을 가진 사용자와의 페더레이션을 효과적으로 설정할 수 있습니다. 예를 들어 Messenger(MSN)와 페더레이션한 경우 사용자가 Messenger 계정을 가진 다른 사용자와 메신저 대화 및 현재 상태 정보를 교환할 수 있습니다.

공용 공급자와 페더레이션하려면 새 공용 공급자를 만들고 사용하도록 설정해야 합니다. 또한 해당 공용 공급자가 사용자와 페더레이션 관계를 만들어야 합니다. **Set-CsPublicProvider**를 통해 조직에서 사용하도록 구성된 공용 공급자의 속성 값을 수정할 수 있습니다.

에지 서버가 DNS 서버 경로 지정 대신 기본 경로 지정을 사용하도록 구성된 경우에는 공용 공급자와 페더레이션할 수 없습니다.

이 cmdlet을 실행할 수 있는 사용자: 기본적으로 RTCUniversalServerAdmins 그룹의 구성원은 **New-CsPublicProvider** cmdlet을 실행할 수 있습니다. 사용자가 직접 만든 사용자 지정 RBAC(역할 기반 액세스 제어) 역할을 포함하여 이 cmdlet이 할당된 모든 RBAC 역할의 목록을 반환하려면 Windows PowerShell 프롬프트에서 다음 명령을 실행합니다.

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "New-CsPublicProvider"}

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
<td><p><em>Enabled</em></p></td>
<td><p>필수</p></td>
<td><p>System.Boolean</p></td>
<td><p>조직과 공용 공급자 간의 페더레이션 관계가 활성 상태인지 여부를 나타냅니다. True로 설정하면 조직의 사용자가 공용 공급자 호스트된 계정을 가진 사용자와 메신저 대화 및 현재 상태 정보를 교환할 수 있고, False로 설정하면 조직의 사용자가 공용 공급자 호스트된 계정을 가진 사용자와 메신저 대화 및 현재 상태 정보를 교환할 수 없습니다. 언제든지 <strong>Enable-CsPublicProvider</strong> cmdlet 및 <strong>Disable-CsPublicProvider</strong> cmdlet을 각각 사용하여 페더레이션 관계를 설정하고 해제할 수 있습니다.</p></td>
</tr>
<tr class="even">
<td><p><em>Identity</em></p></td>
<td><p>필수</p></td>
<td><p>Microsoft.Rtc.Management.Xds.XdsGlobalRelativeIdentity</p></td>
<td><p>만들려는 공용 공급자의 고유 식별자입니다. Identity는 일반적으로 서비스를 제공하는 웹 사이트(예: Yahoo!, AOL, MSN 등)의 이름입니다.</p>
<p>Identity는 공용 공급자뿐 아니라 호스팅 공급자에서도 고유해야 합니다. ID가 Fabrikam인 새 공용 공급자를 만든다고 가정해 보십시오. 해당 Identity를 가진 공용 공급자 또는 호스팅 공급자가 이미 있는 경우 명령이 실패합니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>ProxyFqdn</em></p></td>
<td><p>필수</p></td>
<td><p>System.String</p></td>
<td><p>공용 공급자가 사용하는 프록시 서버의 FQDN(정규화된 도메인 이름)(예: proxyserver.fabrikam.com)을 지정합니다.</p>
<p>프록시 FQDN은 공용 공급자뿐만 아니라 호스팅 공급자 사이에서도 고유해야 합니다. 예를 들어 프록시 FQDN이 proxyserver.fabrikam.com인 새 공용 공급자를 만들려는 경우 이 프록시 FQDN을 가진 공용 공급자 또는 호스팅 공급자가 이미 있으면 이 명령이 실패합니다.</p></td>
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
<td><p><em>IconUrl</em></p></td>
<td><p>선택</p></td>
<td><p>System.String</p></td>
<td><p>Microsoft Skype 연락처를 나타내는 데 사용되는 아이콘의 URL입니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>InMemory</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>개체를 실제로 영구 변경 사항으로 커밋하지 않고 개체 참조를 만듭니다. 이 매개 변수와 함께 호출된 이 cmdlet의 결과를 변수로 할당하면 개체 참조의 속성을 변경한 후 이 cmdlet과 일치하는 Set- cmdlet을 호출하여 해당 변경 사항을 커밋할 수 있습니다.</p></td>
</tr>
<tr class="even">
<td><p><em>VerificationLevel</em></p></td>
<td><p>선택</p></td>
<td><p>Microsoft.Rtc.Management.WritableConfig.Settings.Edge.VerificationLevelType</p></td>
<td><p>공용 공급자가 보낸 메시지가 해당 공급자로부터 전송되었는지 확인하는 방법 또는 여부를 나타냅니다. VerificationLevel은 다음 값 중 하나로 설정되어야 합니다.</p>
<p>AlwaysVerifiable. 이 공급자가 보낸 모든 메시지가 수락됩니다. 메시지에 확인 헤더가 없는 경우 Lync Server에서 확인 헤더를 추가합니다. 이 값은 기본값입니다.</p>
<p>AlwaysUnverifiable. 공용 공급자가 보낸 모든 메시지가 확인되지 않은 것으로 간주됩니다. 받는 사람의 대화 상대 목록에 있는 사람이 보낸 메시지만 배달됩니다. 예를 들어 Ken Myer가 대화 상대 목록에 있으면 이 사용자가 보낸 메시지를 받을 수 있습니다. 대화 상대 목록에 없는 Pilar Ackerman이 보낸 메시지는 받을 수 없습니다. Lync 2013 사용자는 이 설정을 수동으로 재정의하여 대화 상대 목록에 없는 사용자의 메시지를 받을 수 있습니다.</p>
<p>UseSourceVerification. 공용 공급자가 메시지에 추가한 확인 헤더를 사용합니다. 확인 정보가 누락된 경우 메시지가 거부됩니다. 이 값은 Lync Server 2013에서는 더 이상 사용되지 않습니다.</p></td>
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

없음. **New-CsPublicProvider** cmdlet은 파이프라인된 입력을 허용하지 않습니다.

## 반환 형식

Microsoft.Rtc.Management.WritableConfig.Settings.Edge.DisplayPublicProvider 개체의 새 인스턴스를 만듭니다.

## 참고 항목

#### 기타 리소스

[Disable-CsPublicProvider](disable-cspublicprovider.md)  
[Enable-CsPublicProvider](enable-cspublicprovider.md)  
[Get-CsPublicProvider](get-cspublicprovider.md)  
[Remove-CsPublicProvider](remove-cspublicprovider.md)  
[Set-CsPublicProvider](set-cspublicprovider.md)

