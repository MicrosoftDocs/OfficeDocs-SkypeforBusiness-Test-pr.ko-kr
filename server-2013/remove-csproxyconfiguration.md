---
title: Remove-CsProxyConfiguration
TOCTitle: Remove-CsProxyConfiguration
ms:assetid: 738f731c-4d62-4395-bdc3-3f5e5738f443
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg398553(v=OCS.15)
ms:contentKeyID: 49304031
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Remove-CsProxyConfiguration

 

_**마지막으로 수정된 항목:** 2015-03-09_

기존 프록시 서버 구성 설정 컬렉션을 제거합니다. 이 cmdlet은 Lync Server 2010에서 도입되었습니다.

## 구문

    Remove-CsProxyConfiguration -Identity <XdsIdentity> [-Confirm [<SwitchParameter>]] [-Force <SwitchParameter>] [-WhatIf [<SwitchParameter>]]

## 예제

## 예제 1

예제 1에 표시된 명령은 ID가 service:EdgeServer:atl-edge-litwareinc.com인 프록시 구성 설정을 삭제합니다.

    Remove-CsProxyConfiguration -Identity service:EdgeServer:atl-edge-011.litwareinc.com 

## 예제 2

예제 2에서는 서비스 범위에 적용된 모든 프록시 구성 설정이 삭제됩니다. 이 작업을 수행하기 위해 명령은 먼저 **Get-CsProxyConfiguration** cmdlet을 Filter 매개 변수와 함께 호출합니다. 필터 값 "service:\*"는 ID가 문자열 값 "service:"으로 시작하는 프록시 설정만 반환되도록 합니다. 그런 다음 필터링된 컬렉션은 컬렉션의 각 항목을 삭제하는 **Remove-CsProxyConfiguration** cmdlet에 파이프됩니다.

    Get-CsProxyConfiguration -Filter "service:*" | Remove-CsProxyConfiguration

## 예제 3

예제 3에서는 모든 클라이언트를 원격 클라이언트로 취급하는 프록시 구성 설정을 삭제합니다. 이 작업을 수행하기 위해 먼저 **Get-CsProxyConfiguration** cmdlet을 매개 변수 없이 호출하여 현재 사용 중인 모든 프록시 서버 구성 설정의 컬렉션을 반환합니다. 이 컬렉션은 TreatAllClientsAsRemote 속성이 True와 같은 설정만 선택하는 **Where-Object** cmdlet에 파이프됩니다. 그런 다음 이 프록시 구성 설정의 하위 집합은 컬렉션의 모든 설정을 제거하는 **Remove-CsProxyConfiguration** cmdlet에 파이프됩니다.

    Get-CsProxyConfiguration | Where-Object {$_.TreatAllClientsAsRemote -eq $True} | Remove-CsProxyConfiguration

## 자세한 정보

Lync Server에서는 프록시 서버 구성 설정을 통해 프록시 서버를 관리할 수 있습니다. 전역 범위 및 서비스 범위( 에지 서버 및 등록자 서비스에만 해당)에서 적용할 수 있는 이러한 설정을 통해 클라이언트 끝점에서 사용할 수 있는 인증 프로토콜, 보내고 받는 프록시 서버 연결에 압축을 사용할지 여부 등을 제어할 수 있습니다. Lync Server를 설치하면 전역 프록시 서버 구성 설정 컬렉션이 자동으로 만들어집니다. 앞서 언급했듯이 서비스 범위에 추가 컬렉션을 만들 수도 있습니다.

만들어진 새 프록시 서버 설정은 나중에 **Remove-CsProxyConfiguration** cmdlet을 사용하여 제거할 수 있습니다. **Remove-CsProxyConfiguration** cmdlet을 전역 컬렉션에 대해 실행할 수도 있습니다. 단, Lync Server에서는 전역 설정을 제거하도록 허용하지 않으므로 이 경우 전역 설정이 제거되지 않습니다. 대신 전역 컬렉션 내의 모든 속성이 기본값으로 다시 설정됩니다. 예를 들어 기본적으로 프록시 서버 설정에서는 클라이언트가 인증에 Kerberos 프로토콜을 사용하도록 허용합니다. Kerberos를 사용할 수 없도록 전역 설정을 변경할 수 있습니다. 그러나 전역 컬렉션에 대해 **Remove-CsProxyConfiguration** cmdlet을 실행할 경우 해당 속성(UseKerberosForClientToProxyAuth)은 기본값으로 다시 설정되고, Kerberos는 다시 인증 프로토콜로 사용할 수 있게 됩니다.

이 cmdlet을 실행할 수 있는 사용자: 기본적으로 RTCUniversalServerAdmins 그룹의 구성원은 **Remove-CsProxyConfiguration** cmdlet을 로컬로 실행할 수 있습니다. 사용자가 직접 만든 사용자 지정 RBAC(역할 기반 액세스 제어) 역할을 포함하여 이 cmdlet이 할당된 모든 RBAC 역할의 목록을 반환하려면 Windows PowerShell 프롬프트에서 다음 명령을 실행합니다.

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Remove-CsProxyConfiguration"}

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
<td><p>제거할 프록시 서버 구성 설정의 고유 식별자입니다(예: -Identity &quot;service:Registrar:atl-cs-001.litwareinc.com&quot;).</p>
<p><strong>Remove-CsProxyConfiguration</strong> cmdlet은 전역 설정에 대해서도 실행할 수 있습니다. 단, 이 경우 설정이 제거되지 않습니다. 대신 해당 전역 컬렉션 내의 속성이 기본값으로 다시 설정됩니다.</p></td>
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

Microsoft.Rtc.Management.WritableConfig.Settings.SipProxy.ProxySettings 개체입니다. **Remove-CsProxyConfiguration** cmdlet은 프록시 설정 개체의 파이프라인된 인스턴스를 허용합니다.

## 반환 형식

없음. 대신 **Remove-CsProxyConfiguration** cmdlet은 Microsoft.Rtc.Management.WritableConfig.Settings.SipProxy.ProxySettings 개체의 기존 인스턴스를 삭제합니다.

## 참고 항목

#### 기타 리소스

[Get-CsProxyConfiguration](get-csproxyconfiguration.md)  
[New-CsProxyConfiguration](new-csproxyconfiguration.md)  
[Set-CsProxyConfiguration](set-csproxyconfiguration.md)

