---
title: Remove-CsFileTransferFilterConfiguration
TOCTitle: Remove-CsFileTransferFilterConfiguration
ms:assetid: faae4d4b-ea8b-4d50-9c46-16a075476642
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg413064(v=OCS.15)
ms:contentKeyID: 49305615
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Remove-CsFileTransferFilterConfiguration

 

_**마지막으로 수정된 항목:** 2015-03-09_

지정된 메신저 대화 파일 전송 필터 구성을 제거합니다. 메신저 대화 파일 전송 필터 설정은 사용자가 메신저 대화 내에서 특정 파일 유형을 전송하지 못하도록 차단하는 데 사용됩니다. 이 cmdlet은 Lync Server 2010에서 도입되었습니다.

## 구문

    Remove-CsFileTransferFilterConfiguration -Identity <XdsIdentity> [-Confirm [<SwitchParameter>]] [-Force <SwitchParameter>] [-WhatIf [<SwitchParameter>]]

## 예제

## 예제 1

예제 1에서는 **Remove-CsFileTransferFilterConfiguration** cmdlet을 사용하여 ID가 site:Redmond인 파일 전송 필터 구성을 제거합니다.

    Remove-CsFileTransferFilterConfiguration -Identity site:Redmond

## 예제 2

예제 2에서는 사이트 범위의 모든 파일 전송 필터 구성을 제거합니다. 이 작업을 수행하기 위해 명령은 먼저 **Get-CsFileTransferFilterConfiguration** cmdlet 및 Filter 매개 변수를 사용하여 사이트 범위의 모든 구성을 반환합니다. 필터 값 "site:\*"는 **Get-CsFileTransferFilterConfiguration** cmdlet이 문자열 값 "site:"으로 시작하는 ID를 가진 구성만 반환하도록 지시합니다. 필터링된 구성 컬렉션은 컬렉션의 각 항목을 삭제하는 **Remove-CsFileTransferFilterConfiguration** cmdlet에 파이프됩니다.

    Get-CsFileTransferFilterConfiguration -Filter site:* | Remove-CsFileTransferFilterConfiguration

## 예제 3

예제 3에서는 현재 사용하지 않도록 설정된 모든 파일 전송 필터 구성을 제거하는 방법을 보여 줍니다. 이 작업을 수행하기 위해 명령은 먼저 **Get-CsFileTransferFilterConfiguration** cmdlet을 사용하여 조직에서 현재 사용 중인 모든 파일 전송 필터 구성의 컬렉션을 반환합니다. 이 정보는 Enabled 속성이 False($False)와 같은(-eq) 파일 전송 필터 구성만 선택하는 **Where-Object** cmdlet에 파이프됩니다. 그런 다음 필터링된 컬렉션은 계속해서 해당 컬렉션의 각 항목을 제거하는 **Remove-CsFileTransferFilterConfiguration** cmdlet에 파이프됩니다.

    Get-CsFileTransferFilterConfiguration | Where-Object {$_.Enabled -eq $False} | Remove-CsFileTransferFilterConfiguration

## 자세한 정보

메신저 대화를 보낼 때 사용자는 파일을 첨부하여 다른 대화 참가자에게 보낼 수 있습니다. 특정 확장명(보통 잠재적으로 유해한 파일 형식의 확장명)을 가진 파일이 Lync Server 클라이언트를 사용하여 전송되지 않도록 Lync Server를 구성할 수 있습니다.

**Remove-CsFileTransferFilterConfiguration** cmdlet을 사용하면 파일 전송 필터 구성을 삭제할 수 있습니다. 사이트 범위 구성의 경우 **Remove-CsFileTransferFilterConfiguration** cmdlet이 구성을 제거하면 해당 사이트의 사용자가 자동으로 전역 파일 전송 필터 구성을 상속하게 됩니다. **Remove-CsFileTransferFilterConfiguration** cmdlet은 전역 구성에 대해 실행할 수도 있습니다. 그러나 이 경우 전역 구성이 제거되는 것이 아니라 해당 구성의 모든 속성 값이 기본값으로 다시 설정됩니다.

이 cmdlet을 실행할 수 있는 사용자: 기본적으로 RTCUniversalServerAdmins 그룹의 구성원은 **Remove-CsFileTransferFilterConfiguration** cmdlet을 로컬로 실행할 수 있습니다. 사용자가 직접 만든 사용자 지정 RBAC(역할 기반 액세스 제어) 역할을 포함하여 이 cmdlet이 할당된 모든 RBAC 역할의 목록을 반환하려면 Windows PowerShell 프롬프트에서 다음 명령을 실행합니다.

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Remove-CsFileTransferFilterConfiguration"}

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
<td><p>제거할 파일 전송 구성에 대한 고유 식별자입니다. 전역 구성을 참조하려면 -Identity global 구문을 사용합니다. 사이트 범위에서 구성을 참조하려면 -Identity site:Redmond와 유사한 구문을 사용합니다. ID를 지정할 때 와일드카드 값을 사용할 수 없습니다.</p></td>
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
<td><p>변경하기 전에 표시되는 확인 메시지를 표시하지 않습니다.</p></td>
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

Microsoft.Rtc.Management.WritableConfig.Settings.ImFilter.FileTransferFilterConfiguration 개체입니다. 파일 전송 필터 구성 개체의 파이프라인된 입력을 허용합니다.

## 반환 형식

이 cmdlet은 값이나 개체를 반환하지 않습니다. 대신 이 cmdlet은 Microsoft.Rtc.Management.WritableConfig.Settings.ImFilter.FileTransferFilterConfiguration 개체의 인스턴스를 구성합니다.

## 참고 항목

#### 기타 리소스

[New-CsFileTransferFilterConfiguration](new-csfiletransferfilterconfiguration.md)  
[Set-CsFileTransferFilterConfiguration](set-csfiletransferfilterconfiguration.md)  
[Get-CsFileTransferFilterConfiguration](get-csfiletransferfilterconfiguration.md)

