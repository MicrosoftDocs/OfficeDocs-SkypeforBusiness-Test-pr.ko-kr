---
title: Set-CsLisServiceProvider
TOCTitle: Set-CsLisServiceProvider
ms:assetid: 3fe2878c-6ad2-4b7f-a844-e978c263163f
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg425911(v=OCS.15)
ms:contentKeyID: 49303423
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Set-CsLisServiceProvider

 

_**마지막으로 수정된 항목:** 2015-03-09_

위치를 확인하기 위해 E9-1-1(Enhanced 9-1-1) 네트워크 경로 지정 공급자가 제공한 웹 서비스에 대한 정보를 만들거나 수정합니다. 이 cmdlet은 Lync Server 2010에서 도입되었습니다.

## 구문

    Set-CsLisServiceProvider -CertFileName <String> -Password <SecureString> -ServiceProviderName <String> -ValidationServiceUrl <String> [-Confirm [<SwitchParameter>]] [-WhatIf [<SwitchParameter>]]

## 예제

## 예제 1

E9-1-1 네트워크 경로 지정 공급자 웹 서비스에 대한 항목을 만드는 데 필요한 매개 변수 중 하나는 인증서 파일에 액세스하기 위한 암호가 포함된 보안 문자열입니다. 이런 이유로 이 예제의 첫째 줄에서는 **Read-Host** cmdlet을 호출합니다. **Read-Host** cmdlet은 사용자 입력을 확인합니다. 입력 시 해당 입력을 별표(\*)로 표시하는 AsSecureString 매개 변수를 지정합니다. 이 명령의 결과를 $p 변수에 할당했습니다. 그 결과, 사용자 입력의 암호화된 버전인 보안 문자열이 만들어집니다. 즉, 이 명령을 실행하면 웹 서비스의 암호를 묻는 메시지가 표시되고 해당 암호가 $p 변수에 저장됩니다.

이제 암호가 있으므로 웹 서비스에 액세스할 개체를 만들 수 있습니다. 이 작업을 수행하려면 **Set-CsLisServiceProvider** cmdlet을 호출합니다. 이 cmdlet에 여러 개의 매개 변수를 전달합니다. 첫 번째 매개 변수는 공급자 이름(이 경우 E911Provider)입니다. 그런 다음 ValidationServiceUrl에 대해 값 https://www.911contoso.com/validation/을 제공합니다. 이 사이트는 http 대신 접두사 https를 사용하는 "보안 사이트"여야 합니다. 끝으로, 이 웹 서비스에 액세스하는 데 사용되는 인증서가 포함된 파일의 이름(C:\\MS-Contoso-Cert.pfx)을 입력한 후 웹 서비스 암호가 포함된 보안 문자열이 들어 있는 변수 $p를 Password 매개 변수에 전달합니다.

    $p = Read-Host -AsSecureString
    Set-CsLisServiceProvider -ServiceProviderName E911Provider -ValidationServiceUrl https://www.911contoso.com/validation/ -CertFileName C:\MS-Contoso-Cert.pfx -Password $p

## 자세한 정보

E9-1-1을 사용하는 Enterprise Voice 구현에서는 적절한 PSAP(Public Safety Answering Point)로 통화가 경로 지정되도록 먼저 E9-1-1 네트워크 경로 지정 공급자를 통해 응급 통화가 경로 지정되어야 합니다. PSAP는 경찰서, 소방서, 응급 구조대 등 가장 가까운 응급 서비스로 통화를 전달하는 미국의 기관입니다. 이를 위해 공급자는 마스터 주소 가이드와 대조하여 모든 위치가 유효한지 확인할 수 있는 위치 목록을 조직으로부터 제공 받아야 합니다. 이 cmdlet은 공급자 이름, 조직에서 위치를 보내는 데 사용할 웹 서비스의 URL, 보안 웹 서비스의 인증서와 암호 등 공급자에 대한 정보를 만들거나 수정합니다.

지정된 E9-1-1 구현에 대해 둘 이상의 서비스 공급자를 정의할 수 없습니다. 웹 서비스의 URL 및 보안 정보를 확인할 수 없는 경우 이 cmdlet이 실패합니다.

이 cmdlet을 실행할 수 있는 사용자: 기본적으로 RTCUniversalServerAdmins 그룹의 구성원은 **Set-CsLisServiceProvider** cmdlet을 로컬로 실행할 수 있습니다. 사용자가 직접 만든 사용자 지정 RBAC(역할 기반 액세스 제어) 역할을 포함하여 이 cmdlet이 할당된 모든 RBAC 역할의 목록을 반환하려면 Windows PowerShell 프롬프트에서 다음 명령을 실행합니다.

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Set-CsLisServiceProvider"}

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
<td><p><em>CertFileName</em></p></td>
<td><p>필수</p></td>
<td><p>System.String</p></td>
<td><p>인증서 파일의 이름과 전체 경로입니다. 이 파일에는 PFX 파일 확장명이 있어야 합니다.</p></td>
</tr>
<tr class="even">
<td><p><em>Password</em></p></td>
<td><p>필수</p></td>
<td><p>System.Security.SecureString</p></td>
<td><p>암호로 보호된 파일의 인증서에 액세스하는 데 필요한 암호가 포함된 보안 문자열입니다. 보안 문자열은 <strong>ConvertTo-SecureString</strong> cmdlet 또는 <strong>Read-Host</strong> cmdlet을 AsSecureString 매개 변수와 함께 사용하여 만들 수 있습니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>ServiceProviderName</em></p></td>
<td><p>필수</p></td>
<td><p>System.String</p></td>
<td><p>E9-1-1 네트워크 경로 지정 공급자의 이름입니다.</p></td>
</tr>
<tr class="even">
<td><p><em>ValidationServiceUrl</em></p></td>
<td><p>필수</p></td>
<td><p>System.String</p></td>
<td><p>웹 서비스의 URL입니다. 이 URL은 https:// 접두사로 시작하는 보안 URL이어야 합니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>Confirm</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>명령을 실행하기 전에 확인 메시지를 표시합니다.</p></td>
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

LIS(위치 정보 서버) 서비스 공급자 개체의 파이프라인된 입력을 허용합니다.

## 반환 형식

이 cmdlet은 System.Management.Automation.PSCustomObject 유형의 개체를 만들거나 수정합니다.

## 참고 항목

#### 기타 리소스

[Remove-CsLisServiceProvider](remove-cslisserviceprovider.md)  
[Get-CsLisServiceProvider](get-cslisserviceprovider.md)

