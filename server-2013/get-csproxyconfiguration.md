---
title: Get-CsProxyConfiguration
TOCTitle: Get-CsProxyConfiguration
ms:assetid: e4836619-026f-4df0-adbd-aa5216e36368
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg399011(v=OCS.15)
ms:contentKeyID: 49305326
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Get-CsProxyConfiguration

 

_**마지막으로 수정된 항목:** 2015-03-09_

조직에서 현재 사용 중인 프록시 서버 구성 설정에 대한 정보를 반환합니다. 이 cmdlet은 Lync Server 2010에서 도입되었습니다.

## 구문

    Get-CsProxyConfiguration [-Identity <XdsIdentity>] <COMMON PARAMETERS>

    Get-CsProxyConfiguration [-Filter <String>] <COMMON PARAMETERS>

    COMMON PARAMETERS: [-LocalStore <SwitchParameter>]

## 예제

## 예제 1

예제 1에 표시된 명령은 조직에서 현재 사용 중인 모든 프록시 구성 설정 컬렉션을 반환합니다. 이 작업을 수행하기 위해 매개 변수 없이 **Get-CsProxyConfiguration** cmdlet을 호출합니다.

    Get-CsProxyConfiguration

## 예제 2

예제 2에서는 ID가 service:EdgeServer:atl-cs-001.litwareinc.com인 프록시 구성 설정에 대한 정보가 반환됩니다. ID는 고유해야 하므로 이 명령은 두 개 이상의 설정 컬렉션을 반환하지 않습니다.

    Get-CsProxyConfiguration -Identity "service:EdgeServer:atl-cs-001.litwareinc.com"

## 예제 3

예제 3에서는 서비스 범위에서 구성된 모든 프록시 설정에 대한 정보를 반환합니다. 이 작업을 수행하기 위해 명령은 Filter 매개 변수와 함께 **Get-CsProxyConfiguration** cmdlet을 호출합니다. 필터 값 "service:\*"는 ID가 문자열 값 "service:"으로 시작하는 설정만 반환되도록 합니다.

    Get-CsProxyConfiguration -Filter "service:*"

## 예제 4

예제 4에서는 클라이언트 인증서를 인증 메커니즘으로 사용하지 못하도록 하는 프록시 구성 설정에 대한 정보를 반환합니다. 이 작업을 수행하기 위해 명령은 먼저 **Get-CsProxyConfiguration** cmdlet을 사용하여 현재 사용 중인 모든 프록시 구성 설정 컬렉션을 반환합니다. 이 컬렉션은 UseCertificateForClientToProxyAuth 속성이 False와 같은 설정만 선택하는 **Where-Object** cmdlet에 파이프됩니다.

    Get-CsProxyConfiguration | Where-Object {$_.UseCertificateForClientToProxyAuth -eq $False}

## 예제 5

예제 5에서는 클라이언트 메시지의 최대 본문 크기가 5000KB보다 작은 모든 프록시 구성 설정을 반환합니다. 이 작업을 수행하기 위해 명령은 먼저 매개 변수 없이 **Get-CsProxyConfiguration** cmdlet을 호출합니다. 그러면 현재 사용 중인 모든 프록시 구성 설정 컬렉션이 반환됩니다. 이 컬렉션은 MaxClientMessageBodySizeKb 속성이 5000KB보다 작은 설정을 선택하는 **Where-Object** cmdlet에 파이프됩니다.

    Get-CsProxyConfiguration | Where-Object {$_.MaxClientMessageBodySizeKb -lt 5000}

## 자세한 정보

Lync Server에서는 프록시 서버 구성 설정을 통해 프록시 서버를 관리할 수 있습니다. 전역 범위 및 서비스 범위(에지 서버 및 등록자 서비스에만 해당)에서 적용할 수 있는 이러한 설정을 통해 클라이언트 끝점에서 사용할 수 있는 인증 프로토콜, 보내고 받는 프록시 서버 연결에 압축을 사용할지 여부 등을 제어할 수 있습니다. Lync Server를 설치하면 전역 프록시 서버 구성 설정 컬렉션이 자동으로 만들어집니다. 앞서 언급했듯이 서비스 범위에 추가 컬렉션을 만들 수도 있습니다.

**Get-CsProxyConfiguration** cmdlet을 사용하면 조직에서 현재 사용 중인 프록시 서버 구성 설정에 대한 정보를 반환할 수 있습니다.

이 cmdlet을 실행할 수 있는 사용자: 기본적으로 RTCUniversalUserAdmins, RTCUniversalServerAdmins 그룹의 구성원은 **Get-CsProxyConfiguration** cmdlet을 로컬로 실행할 수 있습니다. 사용자가 직접 만든 사용자 지정 RBAC(역할 기반 액세스 제어) 역할을 포함하여 이 cmdlet이 할당된 모든 RBAC 역할의 목록을 반환하려면 Windows PowerShell 프롬프트에서 다음 명령을 실행합니다.

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Get-CsProxyConfiguration"}

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
<td><p>와일드카드를 사용하여 반환할 프록시 구성 설정을 지정하는 데 사용됩니다. 예를 들어 -Filter &quot;site:*&quot; 구문은 서비스 범위에서 구성된 모든 설정을 반환합니다.</p>
<p>Filter 매개 변수와 Identity 매개 변수를 같은 명령에 함께 사용할 수 없습니다.</p></td>
</tr>
<tr class="even">
<td><p><em>Identity</em></p></td>
<td><p>선택</p></td>
<td><p>Microsoft.Rtc.Management.Xds.XdsIdentity</p></td>
<td><p>반환할 프록시 서버 구성 설정의 고유 식별자입니다. 전역 설정을 반환하려면 -Identity global 구문을 사용하고, 서비스 범위에서 구성된 설정을 반환하려면 -Identity &quot;service:EdgeServer:atl-cs-001.litwareinc.com&quot;과 유사한 구문을 사용합니다. ID를 지정할 때는 와일드카드를 사용할 수 없습니다. 와일드카드를 사용하려고 하거나 사용해야 하는 경우에는 대신 Filter 매개 변수를 사용합니다.</p>
<p>이 매개 변수를 포함하지 않으면 <strong>Get-CsProxyConfiguration</strong> cmdlet이 조직에서 현재 사용 중인 모든 프록시 서버 설정을 반환합니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>LocalStore</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>중앙 관리 저장소 자체가 아니라 중앙 관리 저장소의 로컬 복제본에서 프록시 구성 데이터를 검색합니다.</p></td>
</tr>
</tbody>
</table>


## 입력 형식

없음. **Get-CsProxyConfiguration** cmdlet은 파이프라인된 입력을 허용하지 않습니다.

## 반환 형식

**Get-CsProxyConfiguration** cmdlet은 Microsoft.Rtc.Management.WritableConfig.Settings.SipProxy.ProxySettings 개체의 인스턴스를 반환합니다.

## 참고 항목

#### 기타 리소스

[New-CsProxyConfiguration](new-csproxyconfiguration.md)  
[Remove-CsProxyConfiguration](remove-csproxyconfiguration.md)  
[Set-CsProxyConfiguration](set-csproxyconfiguration.md)

