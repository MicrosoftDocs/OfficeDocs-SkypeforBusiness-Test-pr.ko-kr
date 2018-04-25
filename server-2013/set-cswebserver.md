---
title: Set-CsWebServer
TOCTitle: Set-CsWebServer
ms:assetid: 95a7be5b-9e53-40b9-b7b8-3a4bae9c946c
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg398759(v=OCS.15)
ms:contentKeyID: 49304437
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Set-CsWebServer

 

_**마지막으로 수정된 항목:** 2015-03-09_

Lync Server에서 사용하는 하나 이상의 웹 서버 서비스를 수정합니다. 이 cmdlet은 Lync Server 2010에서 도입되었습니다.

## 구문

    Set-CsWebServer [-Identity <XdsGlobalRelativeIdentity>] [-AppSharingPortCount <UInt16>] [-AppSharingPortStart <UInt16>] [-Confirm [<SwitchParameter>]] [-ExternalFqdn <Fqdn>] [-ExternalHttpPort <UInt16>] [-ExternalHttpsPort <UInt16>] [-Force <SwitchParameter>] [-InternalFqdn <Fqdn>] [-McxSipExternalListeningPort <UInt16>] [-McxSipPrimaryListeningPort <UInt16>] [-MeetingRoomAdminPortalExternalListeningPort <UInt16>] [-MeetingRoomAdminPortalInternalListeningPort <UInt16>] [-PrimaryHttpPort <UInt16>] [-PrimaryHttpsPort <UInt16>] [-PublishedExternalHttpPort <UInt16>] [-PublishedExternalHttpsPort <UInt16>] [-PublishedPrimaryHttpPort <UInt16>] [-PublishedPrimaryHttpsPort <UInt16>] [-ReachExternalPsomServerPort <UInt16>] [-ReachPrimaryPsomServerPort <UInt16>] [-RmWebSipExternalListeningPort <UInt16>] [-RmWebSipPrimaryListeningPort <UInt16>] [-SupportConferenceConsoleSipExternalListeningPort <UInt16>] [-SupportConferenceConsoleSipPrimaryListeningPort <UInt16>] [-UcwaSipExternalListeningPort <UInt16>] [-UcwaSipPrimaryListeningPort <UInt16>] [-UserServer <String>] [-WhatIf [<SwitchParameter>]]

## 예제

## 예제 1

예제 1의 명령은 단일 웹 서비스 풀에 대한 PrimaryHttpPort를 변경합니다. 이 풀은 Identity가 WebServer:atl-cs-001.litwareinc.com입니다. 이 예제에서 포트는 번호는 89로 변경됩니다.

    Set-CsWebServer -Identity "WebServer:atl-cs-001.litwareinc.com" -PrimaryHttpPort 89

## 예제 2

예제 2의 명령은 예제 1에 나온 명령의 변형입니다. 이 경우에는 PrimaryHttpPort가 조직의 모든 웹 서비스 풀에 대해 수정됩니다. 이 작업을 수행하기 위해 명령은 먼저 **Get-CsService** cmdlet 및 WebServer 매개 변수를 사용하여 현재 사용 중인 모든 웹 서비스 풀의 컬렉션을 반환합니다. 이 컬렉션은 컬렉션의 각 풀에서 PrimaryHttpPort를 포트 89로 설정하는 **ForEach-Object** cmdlet에 파이프됩니다. **Set-CsWebServer** cmdlet은 파이프라인된 데이터 자체를 받을 수 없으므로 데이터는 **ForEach-Object** cmdlet에 파이프되어야 합니다.

    Get-CsService -WebServer | ForEach-Object {Set-CsWebServer -Identity $_.Identity -PrimaryHttpPort 89}

## 자세한 정보

Lync Server는 웹 서버 및 웹 서비스의 사용을 확장합니다. 예를 들어 웹 서비스를 사용하여 주소록 쿼리를 수행할 수 있습니다(주소록 쿼리 웹 서비스). 또한 Lync Server는 사용자가 전화 접속 회의 개인식별번호(PIN)를 구성할 때 이러한 작업을 수행할 수 있는 웹 페이지를 호스트합니다. 웹 서버 및 웹 서비스가 수행하는 중요한 역할을 감안하면 관리자는 이러한 서버 및 서비스의 구성 방법을 반드시 알아야 합니다. 이 정보는 다음 명령을 사용하여 반환할 수 있습니다.

Get-CsService –WebServer

관리자가 웹 서버 구성 방식을 변경할 수 있다는 점도 중요합니다. 예를 들어 외부 HTTP 또는 HTTPS 연결에 사용되는 포트를 수정해야 하는 경우가 있을 수 있습니다. 이와 같은 포트 변경 및 기타 수정 작업은 **Set-CsWebServer** cmdlet을 사용하여 수행할 수 있습니다.

이 cmdlet을 실행할 수 있는 사용자: 기본적으로 RTCUniversalServerAdmins 그룹의 구성원은 **Set-CsWebServer** cmdlet을 로컬로 실행할 수 있습니다. 사용자가 직접 만든 사용자 지정 RBAC(역할 기반 액세스 제어) 역할을 포함하여 이 cmdlet이 할당된 모든 RBAC 역할의 목록을 반환하려면 Windows PowerShell 프롬프트에서 다음 명령을 실행합니다.

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Set-CsWebServer"}

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
<td><p><em>AppSharingPortCount</em></p></td>
<td><p>선택</p></td>
<td><p>System.UInt16</p></td>
<td><p>응용 프로그램 공유를 위해 할당된 전체 포트 수입니다. 포트는 AppSharingPortStart에 구성된 값부터 시작하여 AppSharingPortCount에 지정된 포트 수만큼 열립니다. 예를 들어 AppSharingPortStart가 60000으로 설정되고 AppSharingPortCount가 100으로 설정된 경우 포트 60000부터 60099까지 응용 프로그램 공유에 사용됩니다. 기본값은 16383입니다.</p></td>
</tr>
<tr class="even">
<td><p><em>AppSharingPortStart</em></p></td>
<td><p>선택</p></td>
<td><p>System.UInt16</p></td>
<td><p>응용 프로그램 공유를 위해 할당된 포트 범위의 첫 번째 포트입니다 기본값은 49152입니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>Confirm</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>명령을 실행하기 전에 확인 메시지를 표시합니다.</p></td>
</tr>
<tr class="even">
<td><p><em>ExternalFqdn</em></p></td>
<td><p>선택</p></td>
<td><p>Microsoft.Rtc.Management.Deploy.Fqdn</p></td>
<td><p>내부 네트워크 외부에서 웹 서비스 풀에 연결하는 사용자가 사용하는 FQDN(정규화된 도메인 이름)입니다(예: -ExternalFqdn &quot;www.litwareinc.com&quot;).</p></td>
</tr>
<tr class="odd">
<td><p><em>ExternalHttpPort</em></p></td>
<td><p>선택</p></td>
<td><p>System.UInt16</p></td>
<td><p>HTTP 프로토콜을 사용하여 설정되는 외부 웹 연결의 포트 번호입니다. 기본값은 포트 8080입니다.</p></td>
</tr>
<tr class="even">
<td><p><em>ExternalHttpsPort</em></p></td>
<td><p>선택</p></td>
<td><p>System.UInt16</p></td>
<td><p>HTTPS 프로토콜을 사용하여 설정되는 외부 웹 연결의 포트 번호입니다. 기본값은 포트 4443입니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>Force</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>명령을 실행할 때 발생할 수 있는 심각하지 않은 오류 메시지를 표시하지 않습니다.</p></td>
</tr>
<tr class="even">
<td><p><em>Identity</em></p></td>
<td><p>선택</p></td>
<td><p>Microsoft.Rtc.Management.Xds.XdsGlobalRelativeIdentity</p></td>
<td><p>웹 서비스 풀의 고유 식별자입니다(예: -Identity &quot;WebServer:atl-cs-001.litwareinc.com&quot;).</p>
<p>웹 서버를 지정할 때 접두사 &quot;WebServer:&quot;를 생략할 수 있습니다(예: -Identity &quot;atl-cs-001.litwareinc.com&quot;).</p></td>
</tr>
<tr class="odd">
<td><p><em>InternalFqdn</em></p></td>
<td><p>선택</p></td>
<td><p>Microsoft.Rtc.Management.Deploy.Fqdn</p></td>
<td><p>Mobility Service의 정규화된 도메인 이름입니다. InternalFqdn은 조직의 방화벽 내에서만 액세스할 수 있어야 합니다.</p></td>
</tr>
<tr class="even">
<td><p><em>McxSipExternalListeningPort</em></p></td>
<td><p>선택</p></td>
<td><p>System.UInt16</p></td>
<td><p>Mobility Service의 외부 수신 대기 포트입니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>McxSipPrimaryListeningPort</em></p></td>
<td><p>선택</p></td>
<td><p>System.UInt16</p></td>
<td><p>Mobility Service의 내부 수신 대기 포트입니다.</p></td>
</tr>
<tr class="even">
<td><p><em>MeetingRoomAdminPortalExternalListeningPort</em></p></td>
<td><p>선택</p></td>
<td><p>System.UInt16</p></td>
<td><p>Lync 회의실 관리 포털의 외부 수신 대기 포트입니다. 관리 포털은 관리자가 회의실을 관리하는 데 사용하는 웹 기반 유틸리티입니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>MeetingRoomAdminPortalInternalListeningPort</em></p></td>
<td><p>선택</p></td>
<td><p>System.UInt16</p></td>
<td><p>Lync 회의실 관리 포털의 내부 수신 대기 포트입니다. 관리 포털은 관리자가 회의실을 관리하는 데 사용하는 웹 기반 유틸리티입니다.</p></td>
</tr>
<tr class="even">
<td><p><em>PrimaryHttpPort</em></p></td>
<td><p>선택</p></td>
<td><p>System.UInt16</p></td>
<td><p>HTTP 프로토콜을 사용하여 설정되는 내부 웹 연결의 포트 번호입니다. 기본값은 포트 80입니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>PrimaryHttpsPort</em></p></td>
<td><p>선택</p></td>
<td><p>System.UInt16</p></td>
<td><p>HTTPS 프로토콜을 사용하여 설정되는 내부 웹 연결의 포트 번호입니다. 기본값은 포트 443입니다.</p></td>
</tr>
<tr class="even">
<td><p><em>PublishedExternalHttpPort</em></p></td>
<td><p>선택</p></td>
<td><p>System.UInt16</p></td>
<td><p>게시된 외부 HTTP 포트의 포트 번호입니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>PublishedExternalHttpsPort</em></p></td>
<td><p>선택</p></td>
<td><p>System.UInt16</p></td>
<td><p>Mobility Service의 외부 포트입니다.</p></td>
</tr>
<tr class="even">
<td><p><em>PublishedPrimaryHttpPort</em></p></td>
<td><p>선택</p></td>
<td><p>System.UInt16</p></td>
<td><p>게시된 기본 HTTP 포트의 포트 번호입니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>PublishedPrimaryHttpsPort</em></p></td>
<td><p>선택</p></td>
<td><p>System.UInt16</p></td>
<td><p>Mobility Service의 내부 포트입니다.</p></td>
</tr>
<tr class="even">
<td><p><em>ReachExternalPsomServerPort</em></p></td>
<td><p>선택</p></td>
<td><p>System.UInt16</p></td>
<td><p>Microsoft의 전화 회의용 프로토콜인 영구적 공유 개체 모델 프로토콜에 대한 외부 포트 번호입니다. 기본 포트 번호는 8061입니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>ReachPrimaryPsomServerPort</em></p></td>
<td><p>선택</p></td>
<td><p>System.UInt16</p></td>
<td><p>Microsoft의 전화 회의용 프로토콜인 PSOM(영구적 공유 개체 모델) 프로토콜에 대한 주 포트 번호입니다. 기본 포트 번호는 8060입니다.</p></td>
</tr>
<tr class="even">
<td><p><em>RmWebSipExternalListeningPort</em></p></td>
<td><p>선택</p></td>
<td><p>System.UInt16</p></td>
<td><p>영구 채팅방 관리 웹 앱용 외부 수신 대기 포트입니다. 이 응용 프로그램은 영구 채팅을 설치 및 구성한 경우에만 사용 가능합니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>RmWebSipPrimaryListeningPort</em></p></td>
<td><p>선택</p></td>
<td><p>System.UInt16</p></td>
<td><p>영구 채팅방 관리 웹 앱용 기본 수신 대기 포트입니다. 이 응용 프로그램은 영구 채팅을 설치 및 구성한 경우에만 사용 가능합니다.</p></td>
</tr>
<tr class="even">
<td><p><em>SupportConferenceConsoleSipExternalListeningPort</em></p></td>
<td><p>선택</p></td>
<td><p>System.UInt16</p></td>
<td><p>지원 회의 콘솔용 수신 대기 포트입니다. 기본값은 6007입니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>SupportConferenceConsoleSipPrimaryListeningPort</em></p></td>
<td><p>선택</p></td>
<td><p>System.UInt16</p></td>
<td><p>Office 365 지원 전화 회의 콘솔에서 사용하는 포트입니다. 이 콘솔은 지원 담당자가 전화 회의 및 온라인 모임의 문제를 해결하는 데 사용됩니다.</p></td>
</tr>
<tr class="even">
<td><p><em>UcwaSipExternalListeningPort</em></p></td>
<td><p>선택</p></td>
<td><p>System.UInt16</p></td>
<td><p>UCWA(통합 통신 웹 API)용 외부 SIP 수신 대기 포트입니다. 기본값은 5088입니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>UcwaSipPrimaryListeningPort</em></p></td>
<td><p>선택</p></td>
<td><p>System.UInt16</p></td>
<td><p>UCWA(통합 통신 웹 API)용 내부 SIP 수신 대기 포트입니다. 기본값은 5089입니다.</p></td>
</tr>
<tr class="even">
<td><p><em>UserServer</em></p></td>
<td><p>선택</p></td>
<td><p>System.String</p></td>
<td><p>웹 서비스 풀과 연결된 사용자 서비스 풀의 서비스 ID입니다(예: -UserServer &quot;UserServer:atl-cs-001.litwareinc.com&quot;).</p></td>
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

없음. **Set-CsWebServer** cmdlet은 파이프라인된 입력을 허용하지 않습니다.

## 반환 형식

없음. 대신 **Set-CsWebServer** cmdlet은 Microsoft.Rtc.Management.Xds.DisplayWebServer 개체의 인스턴스를 수정합니다.

## 참고 항목

#### 기타 리소스

[Get-CsService](get-csservice.md)

