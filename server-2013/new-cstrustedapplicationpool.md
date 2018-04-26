---
title: New-CsTrustedApplicationPool
TOCTitle: New-CsTrustedApplicationPool
ms:assetid: 30117225-d82b-494b-8bc2-da5d539bdd6b
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg425804(v=OCS.15)
ms:contentKeyID: 49303201
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# New-CsTrustedApplicationPool

 

_**마지막으로 수정된 항목:** 2015-03-09_

신뢰할 수 있는 응용 프로그램을 호스트하는 컴퓨터를 포함할 새 풀을 만듭니다. 이 cmdlet은 Lync Server 2010에서 도입되었습니다.

## 구문

    New-CsTrustedApplicationPool -Identity <XdsGlobalRelativeIdentity> [-AppSharingPortCount <UInt16>] [-AppSharingPortStart <UInt16>] [-AudioPortCount <UInt16>] [-AudioPortStart <UInt16>] [-ComputerFqdn <Fqdn>] [-Confirm [<SwitchParameter>]] [-Force <SwitchParameter>] [-OutboundOnly <$true | $false>] [-Registrar <String>] [-RequiresReplication <$true | $false>] [-Site <String>] [-ThrottleAsServer <$true | $false>] [-TreatAsAuthenticated <$true | $false>] [-VideoPortCount <UInt16>] [-VideoPortStart <UInt16>] [-WhatIf [<SwitchParameter>]]

## 예제

## 예제 1

이 예제는 TrustPool.litwareinc.com이라는 FQDN을 사용하여 새 풀을 만듭니다. 새 FQDN을 지정하기 위해 Identity 매개 변수를 사용합니다. 해당 FQDN의 등록자 서비스와 새 풀을 연결하기 위해 Registrar 매개 변수에 pool0.litwareinc.com 값을 사용합니다. 마지막으로 이 풀을 레드몬드 사이트에 포함하도록 지정하려면 Site 매개 변수에 Redmond 값을 사용합니다.

Site 값은 SiteId이며, 이는 **Get-CsSite** cmdlet을 호출하여 검색할 수 있습니다. 그러나 사이트의 Identity는 신뢰할 수 있는 새 응용 프로그램 풀에 저장됩니다. 예를 들어 사이트 Identity가 site:Redmond1이고 SiteId가 NA인 경우 **New-CsTrustedApplicationPool** cmdlet에 대한 호출에 NA를 Site 매개 변수 값으로 사용해야 합니다. 그러나 나중에 모든 신뢰할 수 있는 응용 프로그램 풀에서 NA 사이트를 찾아볼 때는 다음과 같이 Where 절에 Identity 값을 사용합니다.

Get-CsTrustedApplicationPool | Where-Object {$\_.SiteId –eq "site:Redmond1"}

    New-CsTrustedApplicationPool -Identity TrustPool.litwareinc.com -Registrar pool0.litwareinc.com -Site Redmond

## 예제 2

예제 2는 등록자 서비스의 FQDN을 지정하는 대신 서비스 ID Registrar:redmond.litwareinc.com을 사용한 점을 제외하고 예제 1과 동일합니다. 또한 ComputerFqdn 매개 변수에 값을 지정했습니다. 풀이 생성되면 해당 풀 내에 컴퓨터도 생성됩니다. 기본적으로 컴퓨터는 풀과 동일한 FQDN을 갖게 됩니다. 이 풀에 있는 컴퓨터에 대해 다른 FQDN인 AppServer.litwareinc.com을 지정했습니다.

    New-CsTrustedApplicationPool -Identity TrustPool.litwareinc.com -Registrar Registrar:redmond.litwareinc.com -Site Redmond -ComputerFqdn AppServer.litwareinc.com

## 자세한 정보

Lync Server 배포 내에서 신뢰할 수 있는 응용 프로그램을 실행하는 컴퓨터는 신뢰할 수 있는 응용 프로그램 전용으로 사용되는 별도의 풀에 추가하는 것이 좋습니다. 그러나 다용도로 사용되는 기존 풀에 신뢰할 수 있는 응용 프로그램 컴퓨터를 추가할 수도 있습니다. 풀이 토폴로지의 일부로 이미 존재하는 경우 이 cmdlet은 ExternalServer 서비스 역할을 사용하여 해당 풀과 연결된 외부 서비스를 만듭니다. 풀이 존재하지 않는 경우에는 풀과 해당 서비스를 만듭니다. **Get-CsPool** cmdlet을 호출하여 기존의 모든 풀 목록을 찾아볼 수 있습니다.

신뢰할 수 있는 새 응용 프로그램 풀(새 외부 서비스)을 만들면 해당 풀에 할당된 신뢰할 수 있는 새 응용 프로그램 컴퓨터도 생성됩니다. 기본적으로 이 컴퓨터에는 풀과 동일한 FQDN(정규화된 도메인 이름)이 할당됩니다. 그러나 이 cmdlet에 ComputerFqdn 매개 변수를 사용하여 사용자 지정 FQDN 값을 지정할 수 있습니다. 풀에 컴퓨터를 더 추가하려면 ComputerFqdn 값을 풀의 FQDN과 다르게 지정해야 합니다. 풀에 컴퓨터를 더 추가하려면 **New-CsTrustedApplicationComputer** cmdlet을 호출합니다.

이 cmdlet을 실행할 수 있는 사용자: 기본적으로 RTCUniversalServerAdmins 그룹의 구성원은 **New-CsTrustedApplicationPool** cmdlet을 로컬로 실행할 수 있습니다. 사용자가 직접 만든 사용자 지정 RBAC(역할 기반 액세스 제어) 역할을 포함하여 이 cmdlet이 할당된 모든 RBAC 역할의 목록을 반환하려면 Windows PowerShell 프롬프트에서 다음 명령을 실행합니다.

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "New-CsTrustedApplicationPool"}

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
<td><p>새 풀의 FQDN입니다. 풀을 만들 때 Identity 값은 풀의 FQDN이지만 실제로 새 풀의 Identity로 저장되는 값은 자동으로 생성된 풀의 서비스 ID입니다. 여기에 입력한 ID는 PoolFqdn으로 저장됩니다.</p></td>
</tr>
<tr class="even">
<td><p><em>AppSharingPortCount</em></p></td>
<td><p>선택</p></td>
<td><p>System.UInt16</p></td>
<td><p>응용 프로그램 공유 연결의 포트 범위에서 사용할 수 있는 포트의 개수입니다.</p>
<p>기본값: 0</p></td>
</tr>
<tr class="odd">
<td><p><em>AppSharingPortStart</em></p></td>
<td><p>선택</p></td>
<td><p>System.UInt16</p></td>
<td><p>응용 프로그램 공유 연결에 사용할 수 있는 포트 범위에서 첫 번째 포트의 번호입니다.</p></td>
</tr>
<tr class="even">
<td><p><em>AudioPortCount</em></p></td>
<td><p>선택</p></td>
<td><p>System.UInt16</p></td>
<td><p>오디오 연결의 포트 범위에서 사용할 수 있는 포트의 개수입니다.</p>
<p>기본값: 0</p></td>
</tr>
<tr class="odd">
<td><p><em>AudioPortStart</em></p></td>
<td><p>선택</p></td>
<td><p>System.UInt16</p></td>
<td><p>오디오 연결에 사용할 수 있는 포트 범위에서 첫 번째 포트의 번호입니다.</p></td>
</tr>
<tr class="even">
<td><p><em>ComputerFqdn</em></p></td>
<td><p>선택</p></td>
<td><p>Microsoft.Rtc.Management.Deploy.Fqdn</p></td>
<td><p>신뢰할 수 있는 응용 프로그램 풀을 만들면 해당 풀에 속하는 신뢰할 수 있는 응용 프로그램 컴퓨터가 자동으로 생성됩니다. 기본적으로 이 컴퓨터는 풀과 동일한 FQDN을 수신하게 됩니다. 컴퓨터의 FQDN을 풀 FQDN과 다르게 지정하려면 이 매개 변수에 값을 입력합니다. 풀에 컴퓨터를 더 추가하려면 이 매개 변수의 값을 풀의 FQDN과 다르게 입력해야 합니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>Confirm</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>명령을 실행하기 전에 확인 메시지를 표시합니다.</p></td>
</tr>
<tr class="even">
<td><p><em>Force</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>변경 작업을 수행하기 전에 표시되는 모든 확인 프롬프트를 표시하지 않습니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>OutboundOnly</em></p></td>
<td><p>선택</p></td>
<td><p>System.Boolean</p></td>
<td><p>신뢰할 수 있는 응용 프로그램이 풀의 서버에 대해 연결을 시작할 수 있는지 지정합니다. 모든 연결을 응용 프로그램이 아닌 서버에서 시작하려면 이 값을 True로 설정합니다.</p>
<p>기본값: False</p></td>
</tr>
<tr class="even">
<td><p><em>Registrar</em></p></td>
<td><p>선택</p></td>
<td><p>System.String</p></td>
<td><p>풀 등록자 서비스의 서비스 ID 또는 FQDN입니다.</p>
<p>이 매개 변수는 선택 사항이지만 <strong>New-CsTrustedApplicationEndpoint</strong> cmdlet을 사용하여 신뢰할 수 있는 새 응용 프로그램 끝점을 만들고 등록자 종속성이 없는 풀에 끝점을 할당하려고 하면 오류가 수신되고 끝점이 생성되지 않습니다. 또한 등록자와 연결되지 않은 신뢰할 수 있는 응용 프로그램 풀은 제거할 수 없습니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>RequiresReplication</em></p></td>
<td><p>선택</p></td>
<td><p>System.Boolean</p></td>
<td><p>이 풀에 복제가 필요한지 여부를 지정합니다. 복제가 필요하지 않은 경우 이 값을 False로 설정합니다. 일반적으로 Microsoft Outlook Web Access 및 수동으로 프로비전되는 응용 프로그램의 경우 이 매개 변수를 False로 설정합니다.</p>
<p>기본값: True</p></td>
</tr>
<tr class="even">
<td><p><em>Site</em></p></td>
<td><p>선택</p></td>
<td><p>System.String</p></td>
<td><p>이 풀이 있는 사이트의 사이트 ID입니다. 사이트의 SiteId 속성을 검색하려면 <strong>Get-CsSite</strong> cmdlet을 호출합니다. 사이트의 Identity가 아닌 SiteId 속성을 사용해야 합니다. 또한 SiteId 앞에 “site:” 문자열을 입력하지 말고 SiteId만 입력해야 합니다. 또한 <strong>Get-CsSite</strong> cmdlet을 통해 검색한 SiteId를 입력하더라도 신뢰할 수 있는 새 응용 프로그램 풀의 SiteId 속성에 사이트의 Identity가 포함됩니다. 예를 들어 사이트의 SiteId가 Main이고 사이트의 Identity가 site:Redmond1인 경우 <strong>New-CsTrustedApplicationPool</strong> cmdlet에 대한 호출에 -Site Main을 입력해야 하지만 이후의 <strong>Get-CsTrustedApplicationPool</strong> cmdlet 호출에서는 SiteId가 site:Redmond1로 표시됩니다.</p>
<p>Identity에 지정한 풀이 이미 존재하는 경우 Site를 지정할 필요가 없습니다. 풀이 존재하지 않는 경우 이 매개 변수가 필요합니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>ThrottleAsServer</em></p></td>
<td><p>선택</p></td>
<td><p>System.Boolean</p></td>
<td><p>풀의 서버와 신뢰할 수 있는 응용 프로그램 간의 연결을 클라이언트로 제한하려면 이 매개 변수를 false로 설정합니다. 이렇게 하면 연결을 서버로 제한하는 기본값 True보다 연결에 더 많은 제한이 적용됩니다. 연결을 제한하면 한 번에 발생할 수 있는 트랜잭션 수에 대해 제한이 적용됩니다.</p>
<p>기본값: True</p></td>
</tr>
<tr class="even">
<td><p><em>TreatAsAuthenticated</em></p></td>
<td><p>선택</p></td>
<td><p>System.Boolean</p></td>
<td><p>풀의 서버에 연결하는 신뢰할 수 있는 응용 프로그램에 인증을 요구할지 여부를 지정합니다. 신뢰할 수 있는 응용 프로그램에 인증을 요구하려면 이 매개 변수를 False로 설정합니다. 기본값 True는 신뢰할 수 있는 응용 프로그램이 이미 인증되었다는 가정하에 연결을 허용합니다.</p>
<p>기본값: True</p></td>
</tr>
<tr class="odd">
<td><p><em>VideoPortCount</em></p></td>
<td><p>선택</p></td>
<td><p>System.UInt16</p></td>
<td><p>비디오 연결의 포트 범위에서 사용할 수 있는 포트의 개수입니다.</p>
<p>기본값: 0</p></td>
</tr>
<tr class="even">
<td><p><em>VideoPortStart</em></p></td>
<td><p>선택</p></td>
<td><p>System.UInt16</p></td>
<td><p>비디오 연결에 사용할 수 있는 포트 범위에서 첫 번째 포트의 번호입니다.</p></td>
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

없음.

## 반환 형식

Microsoft.Rtc.Management.Xds.DisplayExternalServer 유형의 개체를 만듭니다.

## 참고 항목

#### 기타 리소스

[Remove-CsTrustedApplicationPool](remove-cstrustedapplicationpool.md)  
[Set-CsTrustedApplicationPool](set-cstrustedapplicationpool.md)  
[Get-CsTrustedApplicationPool](get-cstrustedapplicationpool.md)  
[New-CsTrustedApplicationComputer](new-cstrustedapplicationcomputer.md)  
[Get-CsSite](get-cssite.md)

