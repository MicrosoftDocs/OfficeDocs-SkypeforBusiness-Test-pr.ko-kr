---
title: Import-CsCertificate
TOCTitle: Import-CsCertificate
ms:assetid: 87bdafce-f4b9-4c44-ad8f-86c2deb680a4
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg398688(v=OCS.15)
ms:contentKeyID: 49304286
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Import-CsCertificate

 

_**마지막으로 수정된 항목:** 2015-03-09_

Lync Server에서 사용하기 위한 인증서를 가져옵니다. **Request-CsCertificate** cmdlet을 사용하여 인증서를 얻지 못하는 경우 이 인증서를 Lync Server 서버 역할에 할당하려면 먼저 인증서를 가져와야 합니다. 이 cmdlet은 Lync Server 2010에서 도입되었습니다.

## 구문

    Import-CsCertificate -Identity <XdsIdentity> -Type <CertType[]> <COMMON PARAMETERS>

    Import-CsCertificate [-PrivateKeyExportable <$true | $false>] <COMMON PARAMETERS>

    COMMON PARAMETERS: -Path <String> [-Confirm [<SwitchParameter>]] [-EffectiveDate <DateTime>] [-Force <SwitchParameter>] [-Password <String>] [-Report <String>] [-Roll <SwitchParameter>] [-WhatIf [<SwitchParameter>]]

## 예제

## 예제 1

예제 1에 표시된 명령은 C:\\Certificates\\WebServer.pfx 인증서를 가져옵니다. 명령이 완료된 후 인증서를 서버 역할에 할당할 수 있습니다.

    Import-CsCertificate -Path "C:\Certificates\WebServer.pfx" -PrivateKeyExportable $True

## 자세한 정보

Lync Server에서는 서버 및 서버 역할의 ID를 확인하는 방법으로 인증서를 사용합니다. 예를 들어 에지 서버는 인증서를 사용하여 현재 통신 중인 컴퓨터가 실제 프런트 엔드 서버인지 확인하며, 그 반대의 경우도 마찬가지입니다. Lync Server를 완벽하게 구현하려면 적절한 서버 역할에 적절한 인증서를 할당해야 합니다.

인증서를 Lync Server 역할에 할당하려면 인증서를 Lync Server에 알려야 합니다. **Request-CsCertificate** cmdlet을 사용하면 새 인증서에 대한 온라인 및 오프라인 요청을 보낼 수 있습니다. 온라인 요청을 보낸 경우 인증서는 로컬 인증서 저장소에서 자동으로 다운로드되어 저장되며, Lync Server에서 즉시 사용할 수 있습니다. 오프라인 요청의 경우에는 인증서 파일이 전송됩니다. 이 경우 **Import-CsCertificate** cmdlet을 사용하여 인증서를 가져올 수 있습니다. 이 프로세스를 통해 Lync Server 서버 역할에 인증서를 할당할 수 있게 됩니다.

이 cmdlet을 실행할 수 있는 사용자: **Import-CsCertificate** cmdlet을 로컬로 실행하려면 로컬 관리자여야 합니다. 사용자가 직접 만든 사용자 지정 RBAC(역할 기반 액세스 제어) 역할을 포함하여 이 cmdlet이 할당된 모든 RBAC 역할의 목록을 반환하려면 Windows PowerShell 프롬프트에서 다음 명령을 실행합니다.

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Import-CsCertificate"}

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
<td><p>Global로 설정하면 인증서가 전역 범위에서 작동합니다. 전역 인증서는 자동으로 복사되어 해당 컴퓨터로 배포됩니다.</p></td>
</tr>
<tr class="even">
<td><p><em>Path</em></p></td>
<td><p>필수</p></td>
<td><p>System.String</p></td>
<td><p>가져올 인증서 파일의 전체 경로입니다(예: –Path &quot;C:\Certificates\WebServer.cer&quot;).</p></td>
</tr>
<tr class="odd">
<td><p><em>Type</em></p></td>
<td><p>필수</p></td>
<td><p>Microsoft.Rtc.Management.Deployment.CertType[]</p></td>
<td><p>요청할 인증서 유형입니다. 인증서 유형의 예를 들면 다음과 같습니다.</p>
<p>* AccessEdgeExternal</p>
<p>* AudioVideoAuthentication</p>
<p>* DataEdgeExternal</p>
<p>* Default</p>
<p>* External</p>
<p>* Internal</p>
<p>* iPadAPNService</p>
<p></p>
<p>* iPhoneAPNService</p>
<p>* LogRetentionService</p>
<p>* MPNService</p>
<p>* OAuthTokenIssuer</p>
<p>* PICWebService</p>
<p>* ProvisionService</p>
<p>* SMPDNSWebService</p>
<p>* TenantAdmin</p>
<p>* UpgradeEngineService</p>
<p>* WebServicesExternal</p>
<p>* WebServicesInternal</p>
<p>* WsFedTokenTransfer</p>
<p>* XMPPServer</p></td>
</tr>
<tr class="even">
<td><p><em>Confirm</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>명령을 실행하기 전에 확인 메시지를 표시합니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>EffectiveDate</em></p></td>
<td><p>선택</p></td>
<td><p>System.DateTime</p></td>
<td><p>인증서를 최초로 사용할 수 있는 날짜와 시간입니다. 예를 들어 2012년 7월 31일 오전 8시에 인증서를 최초로 사용 가능하도록 구성하려면 국가 및 언어 설정이 영어(미국)로 설정되어 실행 중인 서버에서 다음 구문을 사용합니다.</p>
<p>-EffectiveTime &quot;7/31/2012 8:00 AM&quot;</p></td>
</tr>
<tr class="even">
<td><p><em>Force</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>명령을 실행할 때 발생할 수 있는 심각하지 않은 오류 메시지를 표시하지 않습니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>Password</em></p></td>
<td><p>선택</p></td>
<td><p>System.String</p></td>
<td><p>인증서 파일과 연결된 암호입니다.</p></td>
</tr>
<tr class="even">
<td><p><em>PrivateKeyExportable</em></p></td>
<td><p>선택</p></td>
<td><p>System.Boolean</p></td>
<td><p>True로 설정된 경우 인증서의 개인 키 부분을 네트워크 서비스 계정에서 읽을 수 있어야 합니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>Report</em></p></td>
<td><p>선택</p></td>
<td><p>System.String</p></td>
<td><p>cmdlet을 실행할 때 만들어지는 로그 파일의 파일 경로를 지정할 수 있습니다(예: -Report &quot;C:\Logs\Certificates.html&quot;).</p></td>
</tr>
<tr class="even">
<td><p><em>Roll</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>EffectiveDate 매개 변수로 지정된 날짜와 시간에 지정한 인증서를 업데이트할 수 있습니다. 그러면 새 인증서가 주 인증서로 설정되는 날짜와 시간을 지정할 수 있습니다. EffectiveDate 매개 변수 없이 Roll 매개 변수를 지정하면 명령이 실패합니다.</p></td>
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

없음. **Import-CsCertificate** cmdlet은 파이프라인된 입력을 허용하지 않습니다.

## 반환 형식

없음.

## 참고 항목

#### 기타 리소스

[Get-CsCertificate](get-cscertificate.md)  
[Remove-CsCertificate](remove-cscertificate.md)  
[Request-CsCertificate](request-cscertificate.md)  
[Set-CsCertificate](set-cscertificate.md)

