---
title: Import-CsDeviceUpdate
TOCTitle: Import-CsDeviceUpdate
ms:assetid: cc2e5fab-d978-4e7e-8fc6-d12a0172c07c
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg398861(v=OCS.15)
ms:contentKeyID: 49305052
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Import-CsDeviceUpdate

 

_**마지막으로 수정된 항목:** 2015-03-09_

Microsoft 웹 사이트에서 다운로드한 장치 업데이트 규칙 집합을 가져옵니다. 장치 업데이트 규칙은 펌웨어 버전 업데이트를 Lync Phone Edition을 실행하는 하드웨어 장치와 연결합니다. 이 cmdlet은 Lync Server 2010에서 도입되었습니다.

## 구문

    Import-CsDeviceUpdate -FileName <String> -Identity <XdsIdentity> [-Confirm [<SwitchParameter>]] [-Force <SwitchParameter>] [-WhatIf [<SwitchParameter>]]

## 예제

## 예제 1

예제 1에 표시된 명령은 C:\\Updates\\UCUpdates.cab 파일에서 장치 업데이트 규칙을 가져옵니다.

    Import-CsDeviceUpdate -Identity "service:WebServer:atl-cs-001.litwareinc.com" -FileName C:\Updates\UCUpdates.cab

## 예제 2

예제 2에 표시된 명령은 UNC 경로 \\\\atl-fs-001\\Updates\\UCUpdates.cab에서 장치 업데이트 규칙을 가져옵니다.

    Import-CsDeviceUpdate -Identity "service:WebServer:atl-cs-001.litwareinc.com" -FileName \\atl-fs-001\Updates\UCUpdates.cab

## 예제 3

예제 3에서는 단일 명령을 사용하여 웹 서비스를 실행 중인 모든 서버로 장치 업데이트 규칙을 가져올 수 있는 방법을 보여 줍니다. 이 작업을 수행하기 위해 명령은 먼저 WebServer 매개 변수와 함께 **Get-CsService** cmdlet을 호출하여 웹 서비스 서비스를 실행 중인 모든 서버 컬렉션을 반환합니다. 이 컬렉션은 컬렉션의 각 서버를 순환하면서 **Import-CsDeviceUpdate** cmdlet을 사용하여 이러한 서버에 최신 장치 업데이트 규칙을 업데이트하는 **ForEach-Object** cmdlet에 파이프됩니다. 이 명령은 UCUpdates.cab를 모든 서버의 동일한 위치(C:\\Updates)에 복사한 경우에만 작동합니다.

    Get-CsService -WebServer | ForEach-Object {Import-CsDeviceUpdate -Identity $_.Identity -FileName C:\Updates\UCUpdates.cab}

## 자세한 정보

Microsoft는 주기적으로 Lync Phone Edition에 대한 새 장치 업데이트 규칙 집합을 제공합니다. 이러한 규칙은 Lync Phone Edition을 실행하는 장치용 펌웨어 업데이트를 나타냅니다. 이러한 규칙을 가져온 후 관리자는 펌웨어 업데이트를 테스트한 다음 테스트에 성공하면 조직에서 사용 중인 모든 관련 장치에 업데이트를 적용할 수 있습니다.

새 업데이트 규칙을 만드는 유일한 방법은 Microsoft에서 업데이트 팩을 다운로드하는 것입니다. 사용자 고유의 장치 업데이트 규칙을 만들 수는 없습니다. 최신 장치 업데이트 규칙 집합을 가져오려면 Microsoft 웹 사이트의 도움말 및 지원 페이지로 이동하여 "Phone Edition"을 검색합니다. 업데이트 패키지를 다운로드하고, 업데이트를 업로드할 컴퓨터의 폴더에 파일을 추출합니다. 파일이 추출되면 **Import-CsDeviceUpdate** cmdlet을 사용하여 추출된 .CAB 파일(예: UCUpdates.cab)에 있는 장치 업데이트 규칙을 가져올 수 있습니다.

앞서 말했듯이 업데이트는 로컬에만 로드할 수 있습니다. 장치 업데이트 규칙을 호스트해야 하는 웹 서비스 서비스를 실행 중인 컴퓨터에 UCUpdates.cab를 복사해야 합니다. 또한 장치 업데이트 규칙은 서버에서 서버로 복제할 수 없습니다. 모든 장치 업데이트 규칙이 조직 전체에서 동기화 상태를 유지하도록 하려면 이러한 규칙을 호스트하는 각 서버에서 동일한 작업을 수행해야 합니다. 예를 들어 한 웹 서비스 서버에서 규칙을 제거하려면 다른 웹 서비스 서버에서도 동일한 규칙을 제거해야 합니다. 그렇지 않으면 장치 업데이트 규칙이 더 이상 동기화 상태를 유지하지 않게 됩니다.

업데이트 규칙은 서비스로만 가져올 수 있으며 전역, 사이트 또는 사용자별 범위에서 적용할 수 없습니다. 그러나 **Import-CsDeviceUpdate** cmdlet은 사이트의 각 서비스에 자동으로 규칙 및 업데이트를 추가하지 않으며, 대신 지정된 서비스에만 이러한 규칙 및 업데이트를 로드합니다. 예를 들어 사이트에 웹 서비스를 실행 중인 서버가 3대 있는 경우 웹 서비스의 각 인스턴스에 대해 **Import-CsDeviceUpdate** cmdlet을 한 번씩, 총 세 번 실행해야 합니다. 또는 예제 3에 표시된 것과 같은 명령을 사용할 수 있습니다. 이 명령은 모든 서버 웹 서비스의 ID를 검색한 다음 이러한 각 서버에 대해 **Import-CsDeviceUpdate** cmdlet을 실행합니다.

이 cmdlet을 실행할 수 있는 사용자: 기본적으로 RTCUniversalServerAdmins 그룹의 구성원은 **Import-CsDeviceUpdate** cmdlet을 로컬로 실행할 수 있습니다. 사용자가 직접 만든 사용자 지정 RBAC(역할 기반 액세스 제어) 역할을 포함하여 이 cmdlet이 할당된 모든 RBAC 역할의 목록을 반환하려면 Windows PowerShell 프롬프트에서 다음 명령을 실행합니다.

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Import-CsDeviceUpdate"}

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
<td><p>업데이트 파일의 경로입니다(예: C:\Updates\UCUpdates.cab).</p></td>
</tr>
<tr class="even">
<td><p><em>Identity</em></p></td>
<td><p>필수</p></td>
<td><p>Microsoft.Rtc.Management.Xds.XdsIdentity</p></td>
<td><p>새 업데이트 규칙을 적용할 서비스 인스턴스를 나타냅니다 (예: -Identity &quot;service:WebServer:atl-cs-001.litwareinc.com&quot; 구문은 풀 atl-cs-001.litwareinc.com에 대한 웹 서버에서 장치 업데이트 로그 파일을 지웁니다.</p>
<p>ID는 웹 서버가 설치된 프런트 엔드 풀의 정규화된 도메인 이름이어야 합니다.</p></td>
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

없음. **Import-CsDeviceUpdate** cmdlet은 파이프라인된 입력을 허용하지 않습니다.

## 반환 형식

**Import-CsDeviceUpdate** cmdlet은 Microsoft.Rtc.Management.WritableConfig.Settings.DeviceUpdate.Rule 클래스의 인스턴스를 가져옵니다.

## 참고 항목

#### 기타 리소스

[Get-CsDeviceUpdateRule](get-csdeviceupdaterule.md)

