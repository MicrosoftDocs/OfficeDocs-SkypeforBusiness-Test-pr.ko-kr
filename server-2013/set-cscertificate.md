---
title: Set-CsCertificate
TOCTitle: Set-CsCertificate
ms:assetid: 6da0be05-b257-4258-9d6d-7ddf283f1038
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg398518(v=OCS.15)
ms:contentKeyID: 49303965
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Set-CsCertificate

 

_**마지막으로 수정된 항목:** 2015-03-09_

Lync Server 서버 또는 서버 역할에 인증서를 할당할 수 있습니다. 이 cmdlet은 Lync Server 2010에서 도입되었습니다.

## 구문

    Set-CsCertificate -Reference <CertificateReference> -Type <CertType[]> [-Identity <XdsIdentity>] <COMMON PARAMETERS>

    Set-CsCertificate -Identity <XdsIdentity> -Path <String> -Type <CertType[]> [-Password <String>] <COMMON PARAMETERS>

    Set-CsCertificate -Thumbprint <String> -Type <CertType[]> [-Identity <XdsIdentity>] <COMMON PARAMETERS>

    COMMON PARAMETERS: [-Confirm [<SwitchParameter>]] [-EffectiveDate <DateTime>] [-Force <SwitchParameter>] [-Report <String>] [-Roll <SwitchParameter>] [-WhatIf [<SwitchParameter>]]

## 예제

## 예제 1

예제 1에 표시된 명령은 지문이 B142918E463981A76503828BB1278391B716280987B인 인증서를 로컬 컴퓨터의 WebServicesExternal 역할에 할당합니다.

    Set-CsCertificate -Type WebServicesExternal -Thumbprint "B142918E463981A76503828BB1278391B716280987B"

## 예제 2

예제 2에서는 지문이 B142918E463981A76503828BB1278391B716280987B인 인증서를 로컬 컴퓨터의 세 가지 역할인 기본값, WebServicesInternal 및 WebServicesExternal에 할당합니다.

    Set-CsCertificate -Type Default, WebServicesInternal, WebServicesExternal -Thumbprint "B142918E463981A76503828BB1278391B716280987B"

## 자세한 정보

Lync Server에서는 서버 및 서버 역할의 ID를 확인하는 방법으로 인증서를 사용합니다. 예를 들어 에지 서버는 인증서를 사용하여 현재 통신 중인 컴퓨터가 실제 프런트 엔드 서버인지 확인하며, 그 반대의 경우도 마찬가지입니다. Lync Server를 완전히 구현하려면 해당 인증서를 해당 서버 역할에 할당해야 합니다.

관리자는 **Set-CsCertificate** cmdlet을 사용하여 인증서를 서버 또는 서버 역할에 할당할 수 있습니다. Lync Server와 함께 사용하도록 이미 구성된 인증서만 할당할 수 있습니다. 할당할 수 있는 인증서를 식별하려면 **Get-CsCertificate** cmdlet을 사용합니다.

이 cmdlet을 실행할 수 있는 사용자: **Set-CsCertificate** cmdlet을 로컬로 실행하려면 로컬 관리자여야 합니다. 사용자가 직접 만든 사용자 지정 RBAC(역할 기반 액세스 제어) 역할을 포함하여 이 cmdlet이 할당된 모든 RBAC 역할의 목록을 반환하려면 Windows PowerShell 프롬프트에서 다음 명령을 실행합니다.

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Set-CsCertificate"}

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
<td><p>.PFX 인증서 파일의 전체 경로입니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>Reference</em></p></td>
<td><p>필수</p></td>
<td><p>Microsoft.Rtc.Management.Deployment.CertificateReference</p></td>
<td><p>Lync Server와 함께 사용하도록 구성된 인증서에 대한 개체 참조입니다. 다음 명령은 지문 B142918E463981A76503828BB1278391B716280987B가 포함된 인증서를 나타내는 개체 참조(변수 $x)를 반환합니다.</p>
<p>$x = Get-CsCertificate | Where-Object {$_.Thumbprint –eq &quot;B142918E463981A76503828BB1278391B716280987B&quot;.</p></td>
</tr>
<tr class="even">
<td><p><em>Thumbprint</em></p></td>
<td><p>필수</p></td>
<td><p>System.String</p></td>
<td><p>인증서의 고유한 식별자입니다. 인증서 Thumbprint 표시 예: B142918E463981A76503828BB1278391B716280987B.</p></td>
</tr>
<tr class="odd">
<td><p><em>Type</em></p></td>
<td><p>필수</p></td>
<td><p>Microsoft.Rtc.Management.Deployment.CertType[]</p></td>
<td><p>할당할 인증서 유형입니다. 인증서 유형의 예를 들면 다음과 같습니다.</p>
<p>AccessEdgeExternal</p>
<p>AudioVideoAuthentication</p>
<p>DataEdgeExternal</p>
<p>Default</p>
<p>External</p>
<p>Internal</p>
<p>iPhoneAPNService</p>
<p>iPadAPNService</p>
<p>MPNService</p>
<p>PICWebService(Microsoft Lync Online 2010에만 해당)</p>
<p>ProvisionService(Microsoft Lync Online 2010에만 해당)</p>
<p>WebServicesExternal</p>
<p>WebServicesInternal</p>
<p>WsFedTokenTransfer</p>
<p>예를 들어 -Type Default 구문은 기본 인증서를 할당합니다.</p>
<p>다음과 같이 인증서 유형을 쉼표로 구분하여 단일 명령에 여러 유형을 지정할 수 있습니다.</p>
<p>-Type Internal,External,Default</p></td>
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
<td><p>인증서를 최초로 사용할 수 있는 날짜와 시간입니다. 예를 들어 국가 및 언어 설정이 영어(미국)로 설정되어 실행 중인 서버에서 2012년 7월 31일 오전 8시에 인증서를 최초로 사용 가능하도록 구성하려면 다음 구문을 사용합니다.</p>
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
<td><p>인증서의 암호입니다.</p></td>
</tr>
<tr class="even">
<td><p><em>Report</em></p></td>
<td><p>선택</p></td>
<td><p>System.String</p></td>
<td><p><strong>Set-CsCertificate</strong> cmdlet이 수행하는 절차에 대한 세부 정보를 기록할 수 있습니다. 이 매개 변수 값은 생성할 HTML 파일의 전체 경로여야 합니다(예: -Report C:\Logs\Certificates.html). 지정된 파일이 이미 있는 경우에는 자동으로 새 정보로 덮어씁니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>Roll</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>EffectiveDate 매개 변수로 지정된 날짜와 시간에 지정한 인증서를 업데이트할 수 있습니다. 그러면 새 인증서가 주 인증서로 설정되는 날짜와 시간을 지정할 수 있습니다. EffectiveDate 매개 변수 없이 Roll 매개 변수를 지정하면 명령이 실패합니다.</p></td>
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

Microsoft.Rtc.Management.Deployment.CertificateReference 개체입니다.

## 반환 형식

**Set-CsCertificate** cmdlet은 값이나 개체를 반환하지 않습니다.

## 참고 항목

#### 기타 리소스

[Get-CsCertificate](get-cscertificate.md)  
[Import-CsCertificate](import-cscertificate.md)  
[Remove-CsCertificate](remove-cscertificate.md)  
[Request-CsCertificate](request-cscertificate.md)

