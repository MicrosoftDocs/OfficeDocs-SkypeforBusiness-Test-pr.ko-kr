---
title: Clear-CsDeviceUpdateFile
TOCTitle: Clear-CsDeviceUpdateFile
ms:assetid: 34c5bb61-fcba-4e93-bb21-83b9611f3045
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg425835(v=OCS.15)
ms:contentKeyID: 49303264
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Clear-CsDeviceUpdateFile

 

_**마지막으로 수정된 항목:** 2015-03-09_

장치와 더 이상 연결되지 않는 거부된 장치 업데이트를 삭제합니다. 이 cmdlet은 Lync Server 2010에서 도입되었습니다.

## 구문

    Clear-CsDeviceUpdateFile -Identity <XdsIdentity> [-Confirm [<SwitchParameter>]] [-Force <SwitchParameter>] [-WhatIf [<SwitchParameter>]]

## 예제

## 예제 1

예제 1에 표시된 명령은 WebServer:atl-cs-001.litwareinc.com 서비스에서 장치와 더 이상 연결되지 않은 장치 업데이트 파일을 모두 삭제합니다.

    Clear-CsDeviceUpdateFile -Identity "service:WebServer:atl-cs-001.litwareinc.com"

## 자세한 정보

시스템에 새 장치 업데이트를 업로드할 때마다 해당 장치 업데이트 규칙이 만들어집니다. 기본적으로 새 장치 업데이트 규칙은 보류 중 상태에 할당됩니다. 따라서 테스트 장치에서는 규칙을 다운로드 및 설치할 수 있지만 프로덕션 장치에서는 이러한 작업을 수행할 수 없습니다. 이렇게 하면 사용자에게 업데이트를 제공하기 전에 업데이트를 테스트할 수 있습니다. 테스트에 성공하면 **Approve-CsDeviceUpdateRule** cmdlet을 실행하여 사용자에게 이러한 장치 업데이트를 제공할 수 있습니다.

테스트에 실패하면 **Reset-CsDeviceUpdateRule** cmdlet 또는 **Restore-CsDeviceUpdateRule** cmdlet을 사용하여 업데이트를 거부할 수 있습니다. 이러한 cmdlet을 실행하면 장치 업데이트가 장치 업데이트 규칙에서 분리됩니다. 이때 관리자가 **Clear-CsDeviceUpdateFile** cmdlet을 사용하여 분리된 업데이트를 서버에서 제거할 수 있습니다.

이 cmdlet을 실행할 수 있는 사용자: 기본적으로 RTCUniversalServerAdmins 그룹의 구성원은 **Clear-CsDeviceUpdateFile** cmdlet을 로컬로 실행할 수 있습니다. 사용자가 직접 만든 사용자 지정 RBAC(역할 기반 액세스 제어) 역할을 포함하여 이 cmdlet이 할당된 모든 RBAC 역할의 목록을 반환하려면 Windows PowerShell 프롬프트에서 다음 명령을 실행합니다.

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Clear-CsDeviceUpdateFile"}

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
<td><p>장치 업데이트 파일을 호스트하는 서비스의 고유 식별자입니다. 예를 들어 -Identity &quot;service:WebServer:atl-cs-001.litwareinc.com&quot; 구문은 atl-cs-001.litwareinc.com 풀에 대한 웹 서비스 서비스에서 장치 업데이트 파일을 지웁니다.</p></td>
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

없음. **Clear-CsDeviceUpdateFile** cmdlet은 파이프라인된 입력을 허용하지 않습니다.

## 반환 형식

없음. **Clear-CsDeviceUpdateFile** cmdlet은 값을 반환하지 않습니다.

## 참고 항목

#### 기타 리소스

[Clear-CsDeviceUpdateLog](clear-csdeviceupdatelog.md)  
[Get-CsDeviceUpdateConfiguration](get-csdeviceupdateconfiguration.md)

