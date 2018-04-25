---
title: Update-CsUserData
TOCTitle: Update-CsUserData
ms:assetid: e3cb48e9-9b5e-4c73-ab54-4aea16533ed8
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/JJ205358(v=OCS.15)
ms:contentKeyID: 49305317
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Update-CsUserData

 

_**마지막으로 수정된 항목:** 2015-03-09_

이전에 내보냈던 사용자 정보를 사용하여 Lync Server 사용자 데이터를 업데이트합니다. 이 cmdlet은 Lync Server 2013에서 도입되었습니다.

## 구문

    Update-CsUserData -FileName <String> [-Confirm [<SwitchParameter>]] [-DomainController <Fqdn>] [-Force <SwitchParameter>] [-RoutingGroupFilter <String>] [-UserFilter <String>] [-WhatIf [<SwitchParameter>]]

## 예제

## 예제 1

예제 1에 표시된 명령은 C:\\Logs\\ExportedUserData.zip 파일에 저장된 정보에 따라 Lync Server 사용자 데이터를 업데이트합니다.

    Update-CsUserData -Filename "C:\Logs\ExportedUserData.zip"

## 예제 2

예제 2에 표시된 명령은 단일 사용자, 즉 SIP 주소가 kenmyer@litwareinc.com인 사용자의 사용자 데이터를 업데이트합니다. 이 작업은 UserFilter 매개 변수와 사용자의 SIP 주소(sip: 접두사는 제외)를 차례로 포함하여 수행합니다.

    Update-CsUserData -Filename "C:\Logs\ExportedUserData.zip" -UserFilter "kenmyer@litwareinc.com"

## 자세한 정보

관리자는 **Update-CsUserData** cmdlet을 사용하여 지정된 사용자 또는 사용자 집합에 대한 사용자 데이터를 업데이트할 수 있습니다. 이 데이터는 [Export-CsUserData](export-csuserdata.md) cmdlet을 사용하여 이전에 내보낸 상태여야 합니다. 일반적으로는 로그온된 사용자에 대한 손실된 데이터를 복원하기 위해 이 업데이트 작업을 수행합니다.

사용자가 직접 만든 사용자 지정 RBAC(역할 기반 액세스 제어) 역할을 포함하여 이 cmdlet이 할당된 모든 RBAC 역할의 목록을 반환하려면 Windows PowerShell 명령줄 인터페이스 프롬프트에서 다음 명령을 실행합니다.

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Update-CsUserData"}

**Lync Server 제어판:** The functions carried out by the **Update-CsUserData** cmdlet are not available in the Lync Server 제어판.

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
<td><p><em>FileName</em></p></td>
<td><p>필수</p></td>
<td><p>System.String</p></td>
<td><p>업데이트할 사용자 데이터가 포함된 .ZIP 파일 또는 .XML 파일의 전체 경로입니다. 예를 들면 다음과 같습니다.</p>
<p>-FileName &quot;C:\Data\Lync2010.zip&quot;</p></td>
</tr>
<tr class="even">
<td><p><em>Confirm</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>명령을 실행하기 전에 확인 메시지를 표시합니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>DomainController</em></p></td>
<td><p>선택</p></td>
<td><p>Microsoft.Rtc.Management.Deploy.Fqdn</p></td>
<td><p>관리자가 <strong>Update-CsUserData</strong> cmdlet을 실행할 때 사용할 도메인 컨트롤러의 FQDN을 지정하는 데 사용됩니다. 이 매개 변수를 지정하지 않으면 cmdlet이 사용 가능한 첫 번째 도메인 컨트롤러를 사용하게 됩니다.</p></td>
</tr>
<tr class="even">
<td><p><em>Force</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>명령을 실행할 때 발생할 수 있는 심각하지 않은 오류 메시지를 표시하지 않습니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>RoutingGroupFilter</em></p></td>
<td><p>선택</p></td>
<td><p>System.String</p></td>
<td><p>지정된 라우팅 그룹에 대해서만 데이터를 업데이트할 수 있습니다. 라우팅 그룹은 사용자가 등록되어 있는 프런트 엔드 서버를 지정하는 데 사용됩니다.</p></td>
</tr>
<tr class="even">
<td><p><em>UserFilter</em></p></td>
<td><p>선택</p></td>
<td><p>System.String</p></td>
<td><p>단일 사용자에 대한 데이터를 업데이트할 수 있습니다. 특정 사용자를 지정하려면 다음과 같이 sip: 접두사를 포함하지 않고 해당 사용자의 SIP 주소를 사용합니다.</p>
<p>-UserFilter &quot;kenmyer@litwareinc.com&quot;</p></td>
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

없음. **Update-CsUserData** cmdlet은 파이프라인된 입력을 허용하지 않습니다.

## 반환 형식

**Update-CsUserData** cmdlet은 Lync Server 사용자 정보를 업데이트합니다.

## 참고 항목

#### 기타 리소스

[Convert-CsUserData](convert-csuserdata.md)  
[Export-CsUserData](export-csuserdata.md)  
[Import-CsUserData](import-csuserdata.md)  
[Sync-CsUserData](sync-csuserdata.md)

