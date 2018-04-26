---
title: Remove-CsXmppAllowedPartner
TOCTitle: Remove-CsXmppAllowedPartner
ms:assetid: 858a07a3-891e-4678-b989-6339b0978427
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/JJ205055(v=OCS.15)
ms:contentKeyID: 49304269
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Remove-CsXmppAllowedPartner

 

_**마지막으로 수정된 항목:** 2015-03-09_

기존 XMPP 허용 파트너를 제거합니다. XMPP(Extensible Messaging and Presence Protocol)는 XML을 사용하여 메시지를 교환하기 위한 개방형 표준 통신 프로토콜입니다. 허용 파트너는 해당 사용자가 Lync Server 2013 사용자와 메신저 대화 및 현재 상태 정보를 교환할 수 있는 메신저 및 현재 상태 공급자입니다. 이 cmdlet은 Lync Server 2013에서 도입되었습니다.

## 구문

    Remove-CsXmppAllowedPartner -Identity <XdsGlobalRelativeIdentity> [-Confirm [<SwitchParameter>]] [-Force <SwitchParameter>] [-WhatIf [<SwitchParameter>]]

## 예제

## 예제 1

예제 1에서는 ID가 "contoso.com"인 XMPP 허용 파트너를 삭제합니다.

    Remove-CsXmppAllowedPartner -Identity "contoso.com"

## 예제 2

예제 2에 표시된 명령은 모든 XMPP 허용 파트너를 삭제합니다. 이 작업을 수행하기 위해 명령은 먼저 **Get-CsXmppAllowedPartner** cmdlet을 호출하여 조직에서 현재 사용 중인 모든 XMPP 허용 파트너의 컬렉션을 반환합니다. 이 컬렉션은 **Remove-CsXmppAllowedPartner** cmdlet에 파이프되며, 해당 cmdlet은 컬렉션의 각 파트너를 제거합니다.

    Get-CsXmppAllowedPartner | Remove-CsXmppAllowedPartner

## 예제 3

예제 3에서는 파트너 유형이 PublicUnverified인 모든 XMPP 허용 파트너를 삭제합니다. 이 작업을 수행하기 위해 명령은 먼저 **Get-CsXmppAllowedPartner** cmdlet을 사용하여 모든 허용 파트너의 컬렉션을 반환합니다. 이 컬렉션은 **Where-Object** cmdlet에 파이프되며, 해당 cmdlet은 PartnerType 속성이 "PublicUnverified"인 파트너만 선택합니다. 해당 조건을 충족하는 파트너는 **Remove-CsXmppAllowedPartner** cmdlet에 파이프되며 해당 cmdlet에 의해 삭제됩니다.

    Get-CsXmppAllowedPartner | Where-Object {$_.PartnerType -eq "PublicUnverified"} | Remove-CsXmppAllowedPartner

## 자세한 정보

XMPP(Extensible Messaging and Presence Protocol)는 인터넷에서 메시지를 보내는 데 사용되는 XML 기반 표준 통신 프로토콜입니다. XMPP(이전 이름은 Jabber)는 Google Talk, Facebook 채팅을 비롯한 여러 인터넷 메시징 및 통신 응용 프로그램에서 지원됩니다.

사용자가 XMPP 네트워크의 사용자와 메신저 대화 및 현재 상태 정보를 교환할 수 있도록 하려면 해당 네트워크가 XMPP 허용 파트너로 구성되어 있어야 합니다. 또한 XMPP 액세스를 허용하는 외부 액세스 정책을 사용자에게 할당해야 합니다. 기본적으로 사용자는 허용 파트너 목록에 있는 모든 XMPP 네트워크의 사용자와 통신하도록 허용됩니다. 사용자가 지정된 네트워크의 사용자와 통신하지 못하도록 하려면 허용 파트너 목록에서 해당 네트워크를 삭제해야 합니다.

사용자가 직접 만든 사용자 지정 RBAC(역할 기반 액세스 제어) 역할을 포함하여 이 cmdlet이 할당된 모든 RBAC 역할의 목록을 반환하려면 Windows PowerShell 명령줄 인터페이스 프롬프트에서 다음 명령을 실행합니다.

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Remove-CsXmppAllowedPartner"}

**Lync Server 제어판:**Lync Server 제어판을 사용하여 XMPP 허용 파트너를 제거하려면 외부 사용자 액세스, XMPP 페더레이션 파트너를 차례로 클릭하고 제거할 파트너를 선택한 후에 편집, 삭제를 차례로 클릭합니다.

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
<td><p>삭제할 XMPP 허용 파트너의 FQDN(정규화된 도메인 이름)입니다. 예를 들면 다음과 같습니다.</p>
<p>-Identity &quot;fabrikam.com&quot;</p></td>
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
<td><p>실제로 명령을 수행하지는 않고 명령을 실행했을 때 발생할 결과에 대해 설명합니다.</p></td>
</tr>
</tbody>
</table>


## 입력 형식

**Remove-CsXmppAllowedPartner** cmdlet은 Microsoft.Rtc.Management.WritableConfig.Settings.XmppFederation.XmppAllowedPartner\#Decorated 개체의 파이프라인된 인스턴스를 허용합니다.

## 반환 형식

없음. 대신 **Remove-CsXmppAllowedPartner** cmdlet은 Microsoft.Rtc.Management.WritableConfig.Settings.XmppFederation.XmppAllowedPartner\#Decorated 개체의 기존 인스턴스를 삭제합니다.

## 참고 항목

#### 기타 리소스

[Get-CsXmppAllowedPartner](get-csxmppallowedpartner.md)  
[New-CsXmppAllowedPartner](new-csxmppallowedpartner.md)  
[Set-CsXmppAllowedPartner](set-csxmppallowedpartner.md)

