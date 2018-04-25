---
title: Clear-CsDeviceUpdateLog
TOCTitle: Clear-CsDeviceUpdateLog
ms:assetid: 9e549484-b79b-47ef-b83b-13a6e20b0c80
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg412738(v=OCS.15)
ms:contentKeyID: 49304541
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Clear-CsDeviceUpdateLog

 

_**마지막으로 수정된 항목:** 2015-03-09_

지정된 일 수보다 오래된 모든 장치 업데이트 웹 서비스 로그 및 감사 파일을 삭제합니다. 이 cmdlet은 Lync Server 2010에서 도입되었습니다.

## 구문

    Clear-CsDeviceUpdateLog -DaysBack <Int32> -Identity <XdsIdentity> [-Confirm [<SwitchParameter>]] [-Force <SwitchParameter>] [-WhatIf [<SwitchParameter>]]

## 예제

## 예제 1

예제 1에 표시된 명령은 Identity가 "service:WebServer:atl-cs-001.litwareinc.com"인 장치 업데이트 웹 서비스에 연결된 후 10일보다 오래된 모든 장치 및 감사 로그를 삭제합니다.

    Clear-CsDeviceUpdateLog -Identity "service:WebServer:atl-cs-001.litwareinc.com" -DaysBack 10

## 자세한 정보

장치 업데이트 웹 서비스는 로그 파일의 확장 컬렉션을 유지합니다. 이 컬렉션에는 휴대폰 등의 클라이언트 장치에서 업데이트되는 로그 파일 및 서비스 자체에 의해 수행되는 감사 로그가 모두 포함됩니다. 장치 업데이트 작업 양과 조직에서 사용되는 클라이언트 장치 수에 따라 서버가 곧 장치 업데이트 웹 서비스 로그로 인해 "복잡"해질 수 있습니다. **Clear-CsDeviceUpdateLog** cmdlet은 서버에 저장된 로그 파일 수를 줄일 수 있는 방법을 제공합니다. cmdlet을 호출한 다음 삭제해야 하는 파일의 최대 사용 기간(일)을 지정하기만 하면 됩니다. 해당 최대 사용 기간보다 오래된 로그 파일은 시스템에서 제거됩니다.

이 cmdlet을 실행할 수 있는 사용자: 기본적으로 RTCUniversalServerAdmins 그룹의 구성원은 **Clear-CsDeviceUpdateLog** cmdlet을 로컬로 실행할 수 있습니다. 사용자가 직접 만든 사용자 지정 RBAC(역할 기반 액세스 제어) 역할을 포함하여 이 cmdlet이 할당된 모든 RBAC 역할의 목록을 반환하려면 Windows PowerShell 프롬프트에서 다음 명령을 실행합니다.

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Clear-CsDeviceUpdateLog"}

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
<td><p><em>DaysBack</em></p></td>
<td><p>필수</p></td>
<td><p>System.Int32</p></td>
<td><p>로그 파일을 유지할 최대 기간(일 수)입니다. DaysBack 매개 변수를 사용하여 지정한 값보다 오래된 로그 파일은 모두 삭제됩니다. 예를 들어 DaysBack을 7로 설정하면 7일보다 오래된 모든 로그 파일이 제거됩니다.</p>
<p>이 매개 변수는 1-30(포함) 사이의 정수 값으로 설정할 수 있습니다.</p></td>
</tr>
<tr class="even">
<td><p><em>Identity</em></p></td>
<td><p>필수</p></td>
<td><p>Microsoft.Rtc.Management.Xds.XdsIdentity</p></td>
<td><p>장치 업데이트 웹 서비스 로그 파일을 호스트하는 서비스의 고유한 식별자입니다. 예를 들어 -Identity &quot;service:WebServer:atl-cs-001.litwareinc.com&quot; 구문은 풀 atl-cs-001.litwareinc.com에 대한 웹 서비스에서 장치 업데이트 웹 서비스 로그 파일을 지웁니다.</p></td>
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
<td><p>명령을 실행할 때 발생할 수 있는 심각하지 않은 오류 메시지를 표시하지 않습니다.</p></td>
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

없음. **Clear-CsDeviceUpdateLog** cmdlet은 파이프라인된 입력을 허용하지 않습니다.

## 반환 형식

없음. **Clear-CsDeviceUpdateLog** cmdlet은 값을 반환하지 않습니다.

## 참고 항목

#### 기타 리소스

[Clear-CsDeviceUpdateFile](clear-csdeviceupdatefile.md)  
[Get-CsDeviceUpdateConfiguration](get-csdeviceupdateconfiguration.md)

