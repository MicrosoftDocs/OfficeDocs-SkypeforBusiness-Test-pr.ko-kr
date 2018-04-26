---
title: Export-CsRgsConfiguration
TOCTitle: Export-CsRgsConfiguration
ms:assetid: 754513a4-0b46-44b7-8910-f865b1e0f037
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/JJ205011(v=OCS.15)
ms:contentKeyID: 49304053
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Export-CsRgsConfiguration

 

_**마지막으로 수정된 항목:** 2015-03-09_

기존 응답 그룹 응용 프로그램 구성에서 데이터를 내보냅니다. 이 데이터는 .ZIP 파일로 저장되며 나중에 **Import-CsRgsConfiguration** cmdlet을 사용하여 가져올 수 있습니다. 응답 그룹 구성 데이터를 내보내고 가져오는 기능은 재해 복구 시나리오에서 특히 유용합니다. 이 cmdlet은 Lync Server 2013에 도입되었습니다.

## 구문

    Export-CsRgsConfiguration -FileName <String> -Source <RgsIdentity> [-Force <SwitchParameter>] [-Owner <RgsIdentity>] [-RemoveExportedConfiguration <SwitchParameter>]

## 예제

## 예제 1

예제 1에 표시된 명령은 atl-rgs-001.litwareinc.com 풀에서 경로가 C:\\Exports\\Rgs.zip인 파일로 응답 그룹 구성 설정을 내보냅니다.

    Export-CsRgsConfiguration -Source "ApplicationServer:atl-rgs-001.litwareinc.com" -FileName "C:\Exports\Rgs.zip"

## 자세한 정보

**Export-CsRgsConfiguration** cmdlet 및 [Import-CsRgsConfiguration](import-csrgsconfiguration.md) cmdlet을 사용하면 워크플로, 큐, 에이전트 그룹, 휴일 집합, 근무 시간 등의 항목과 오디오 파일 및 서비스 구성 설정을 포함한 응답 그룹 응용 프로그램의 현재 구현에 대한 데이터를 내보낸 다음 나중에 해당 정보를 가져오거나 다시 가져올 수 있습니다. 따라서 재해 복구 시나리오(예: 응답 그룹 응용 프로그램을 호스트하는 서버에 장애가 발생한 경우)나 단순히 응답 그룹 응용 프로그램을 다른 풀로 전송해야 하는 경우에 매우 유용할 수 있습니다.

**Export-CsRgsConfiguration** cmdlet 및 **Import-CsRgsConfiguration** cmdlet은 Lync Server 2013에서만 작동합니다. 응답 그룹 데이터를 Microsoft Lync Server 2010에서 Lync Server 2013으로 마이그레이션하려면 대신 [Move-CsRgsConfiguration](move-csrgsconfiguration.md) cmdlet을 사용해야 합니다.

사용자가 직접 만든 사용자 지정 RBAC(역할 기반 액세스 제어) 역할을 포함하여 이 cmdlet이 할당된 모든 RBAC 역할의 목록을 반환하려면 Windows PowerShell 명령줄 인터페이스 프롬프트에서 다음 명령을 실행합니다.

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Export-CsRgsConfiguration"}

**Lync Server 제어판:** **Export-CsRgsConfiguration** cmdlet에 의해 수행되는 기능은 Lync Server 제어판에서는 사용할 수 없습니다.

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
<td><p><strong>Export-CsRgsConfiguration</strong> cmdlet을 실행할 때 생성되는 .ZIP 파일의 경로입니다. 예를 들면 다음과 같습니다.</p>
<p>-FileName &quot;C:\Exports\RgsConfig.zip&quot;</p>
<p>이 파일이 이미 있는 경우에는 명령이 실패합니다.</p></td>
</tr>
<tr class="even">
<td><p><em>Source</em></p></td>
<td><p>필수</p></td>
<td><p>Microsoft.Rtc.Rgs.Management.RgsIdentity</p></td>
<td><p>해당 구성 설정을 내보내는 응답 그룹 인스턴스의 ID입니다. 예를 들면 다음과 같습니다.</p>
<p>-Source &quot;ApplicationServer:atl-rgs-001.litwareinc.com&quot;</p></td>
</tr>
<tr class="odd">
<td><p><em>Force</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>명령을 실행할 때 발생할 수 있는 심각하지 않은 오류 메시지를 표시하지 않습니다.</p></td>
</tr>
<tr class="even">
<td><p><em>Owner</em></p></td>
<td><p>선택</p></td>
<td><p>Microsoft.Rtc.Rgs.Management.RgsIdentity</p></td>
<td><p>지정하는 경우 지정된 풀에 있는 모든 응답 그룹 인스턴스에 대한 구성 정보를 내보냅니다. 예를 들면 다음과 같습니다.</p>
<p>-Owner &quot;atl-rgs-001.litwareinc.com&quot;</p></td>
</tr>
<tr class="odd">
<td><p><em>RemoveExportedConfiguration</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>지정하는 경우 구성 정보를 내보낸 후 응답 그룹 인스턴스를 삭제합니다.</p></td>
</tr>
</tbody>
</table>


## 입력 형식

없음. **Export-CsRgsConfiguration** cmdlet은 파이프라인된 입력을 허용하지 않습니다.

## 반환 형식

**Export-CsRgsConfiguration** cmdlet은 파일 확장명이 .ZIP인 압축 파일을 만듭니다.

## 참고 항목

#### 기타 리소스

[Import-CsRgsConfiguration](import-csrgsconfiguration.md)

