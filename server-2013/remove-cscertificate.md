---
title: Remove-CsCertificate
TOCTitle: Remove-CsCertificate
ms:assetid: b7a83a58-9d3f-458a-867e-44466c9817dc
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg412895(v=OCS.15)
ms:contentKeyID: 49304809
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Remove-CsCertificate

 

_**마지막으로 수정된 항목:** 2015-03-09_

이전에 Lync Server에서 사용할 수 있는 것으로 표시된 인증서를 제거합니다. 이 cmdlet은 Lync Server 2010에서 도입되었습니다.

## 구문

    Remove-CsCertificate -Type <CertType[]> [-Confirm [<SwitchParameter>]] [-Force <SwitchParameter>] [-Identity <XdsIdentity>] [-Previous <SwitchParameter>] [-Report <String>] [-WhatIf [<SwitchParameter>]]

## 예제

## 예제 1

예제 1에 표시된 명령은 Lync Server에 제공되는 모든 WebServicesExternal 인증서를 삭제합니다. 이러한 인증서가 현재 사용 중인 경우 **Remove-CsCertificate** cmdlet에서 인증서를 제거할지 묻고, 이 프롬프트에 응답해야만 명령이 완료됩니다. 확인 프롬프트를 무시하려면 Force 매개 변수를 사용합니다.

Remove-CsCertificate –Type WebServicesExternal -Force

    Remove-CsCertificate -Type WebServicesExternal

## 자세한 정보

Lync Server에서는 서버 및 서버 역할의 ID를 확인하는 방법으로 인증서를 사용합니다. 예를 들어 에지 서버는 인증서를 사용하여 현재 통신 중인 컴퓨터가 실제 프런트 엔드 서버인지 확인하며, 그 반대의 경우도 마찬가지입니다. Lync Server를 완전히 구현하려면 해당 인증서를 해당 서버 역할에 할당해야 합니다.

**Remove-CsCertificate** cmdlet을 사용하면 Lync Server에서 현재 사용 중인 인증서를 제거할 수 있습니다. **Remove-CsCertificate** cmdlet은 실제로 인증서 자체를 삭제하지 않습니다. 대신 Lync Server에서 더 이상 사용할 수 없는 것으로 인증서를 표시하고, 인증서 바인딩을 제거하며, 인증서에 대한 액세스 권한을 해지합니다(인증서를 사용 중인 다른 서비스가 없다고 가정할 경우). 예를 들어 **Get-CsCertificate** cmdlet을 실행하면 인증서가 더 이상 표시되지 않습니다.

Lync Server에서 인증서를 다시 사용하려면 **Set-CsCertificate** cmdlet을 사용하여 인증서를 Lync Server에 다시 할당해야 합니다.

현재 사용 중인 인증서를 제거하려고 하면 **Remove-CsCertificate** cmdlet에서 인증서를 제거할지 묻고, 이 프롬프트에 응답해야만 인증서가 제거됩니다. 이 프롬프트를 무시하고 현재 사용 중이더라도 인증서를 자동으로 삭제하려면 Force 매개 변수를 명령에 추가합니다.

Remove-CsCertificate –Type WebServicesExternal -Force

이 cmdlet을 실행할 수 있는 사용자: **Remove-CsCertificate** cmdlet을 로컬로 실행하려면 로컬 관리자 및 도메인 구성원이어야 합니다. 사용자가 직접 만든 사용자 지정 RBAC(역할 기반 액세스 제어) 역할을 포함하여 이 cmdlet이 할당된 모든 RBAC 역할의 목록을 반환하려면 Windows PowerShell 프롬프트에서 다음 명령을 실행합니다.

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Remove-CsCertificate"}

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
<td><p><em>Type</em></p></td>
<td><p>필수</p></td>
<td><p>Microsoft.Rtc.Management.Deployment.CertType[]</p></td>
<td><p>삭제할 인증서 유형입니다. 인증서 유형의 예를 들면 다음과 같습니다.</p>
<p>AccessEdgeExternal</p>
<p>AudioVideoAuthentication</p>
<p>DataEdgeExternal</p>
<p>Default</p>
<p>External</p>
<p>Internal</p>
<p>PICWebService(Microsoft Lync Online 2010에만 해당)</p>
<p>ProvisionService(Microsoft Lync Online 2010에만 해당)</p>
<p>WebServicesExternal</p>
<p>WebServicesInternal</p>
<p>WsFedTokenTransfer</p>
<p>예를 들어 이 구문은 기본 인증서 -Type Default를 삭제합니다.</p>
<p>인증서 유형을 쉼표로 구분하여 단일 명령으로 여러 유형을 삭제할 수 있습니다.</p>
<p>-Type Internal,External,Default</p></td>
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
<td><p>현재 사용 중인 인증서를 삭제하려고 하면 일반적으로 나타나는 확인 프롬프트를 무시합니다.</p></td>
</tr>
<tr class="even">
<td><p><em>Identity</em></p></td>
<td><p>선택</p></td>
<td><p>Microsoft.Rtc.Management.Xds.XdsIdentity</p></td>
<td><p>Global로 설정하면 인증서를 전역 범위에서 제거합니다. 지정하지 않으면 인증서를 로컬 컴퓨터에서 제거합니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>Previous</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>이 매개 변수를 지정하면 현재 할당되어 있는 인증서가 아닌 이전에 할당했던 인증서를 제거합니다.</p></td>
</tr>
<tr class="even">
<td><p><em>Report</em></p></td>
<td><p>선택</p></td>
<td><p>System.String</p></td>
<td><p><strong>Remove-CsCertificate</strong> cmdlet에서 수행하는 프로시저에 대한 자세한 정보를 기록하는 데 사용됩니다. 이 매개 변수 값은 생성할 HTML 파일의 전체 경로여야 합니다(예: -Report C:\Logs\Certificates.html). 지정된 파일이 이미 있는 경우에는 자동으로 새 정보로 덮어씁니다.</p></td>
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

없음. Remove-CsCertificate cmdlet은 파이프라인된 입력을 허용하지 않습니다.

## 반환 형식

없음. 대신에 **Remove-CsCertificate** cmdlet은 Microsoft.Rtc.Management.Deployment.CertificateReference 개체의 인스턴스를 삭제합니다.

## 참고 항목

#### 기타 리소스

[Get-CsCertificate](get-cscertificate.md)  
[Import-CsCertificate](import-cscertificate.md)  
[Request-CsCertificate](request-cscertificate.md)  
[Set-CsCertificate](set-cscertificate.md)

