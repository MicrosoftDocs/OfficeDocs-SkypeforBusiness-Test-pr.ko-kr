---
title: Get-CsFileTransferFilterConfiguration
TOCTitle: Get-CsFileTransferFilterConfiguration
ms:assetid: 6f43c203-acd6-4dbf-a071-752bf0c1727c
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg398527(v=OCS.15)
ms:contentKeyID: 49303982
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Get-CsFileTransferFilterConfiguration

 

_**마지막으로 수정된 항목:** 2015-03-09_

조직의 파일 전송 필터 구성을 반환합니다. 이러한 구성은 Lync Server 클라이언트를 사용하여 특정 형식의 파일(예: .vbs 또는 .ps1 파일 확장명을 사용하는 파일)을 전송하는 사용자 기능을 차단하는 데 사용됩니다. 이 cmdlet은 Lync Server 2010에서 도입되었습니다.

## 구문

    Get-CsFileTransferFilterConfiguration [-Identity <XdsIdentity>] <COMMON PARAMETERS>

    Get-CsFileTransferFilterConfiguration [-Filter <String>] <COMMON PARAMETERS>

    COMMON PARAMETERS: [-LocalStore <SwitchParameter>]

## 예제

## 예제 1

예제 1에 표시된 명령은 조직에서 사용 중인 모든 파일 전송 필터 구성의 컬렉션을 반환합니다. 이는 추가 매개 변수 없이 **Get-CsFileTransferFilterConfiguration** cmdlet을 호출할 때마다 실행되는 기본 동작입니다.

    Get-CsFileTransferFilterConfiguration

## 예제 2

예제 2에서는 ID가 site:Redmond인 단일 파일 전송 필터 구성을 반환합니다. ID는 고유해야 하므로 이 명령은 두 개 이상의 구성을 반환할 수 없습니다.

    Get-CsFileTransferFilterConfiguration -Identity site:Redmond

## 예제 3

예제 3에서는 Filter 매개 변수를 사용하여 사이트 수준의 모든 파일 전송 필터 구성 컬렉션을 반환합니다. 필터 값 "site:\*"는 ID가 문자열 값 "site:"으로 시작하는 구성만 반환하도록 **Get-CsFileTransferFilterConfiguration** cmdlet에 지시합니다.

    Get-CsFileTransferFilterConfiguration -Filter site:*

## 예제 4

예제 4에 표시된 명령은 금지된 파일 확장명 목록에서 .xls가 포함된 파일 전송 필터 구성만 반환합니다. 이 작업을 수행하기 위해 먼저 **Get-CsFileTransferFilterConfiguration** cmdlet을 사용하여 조직에서 사용하도록 구성된 모든 정책의 컬렉션을 반환합니다. 이 컬렉션은 Extensions 속성에 문자열 값 ".xls"가 포함된(-contains) 구성 데이터만 반환되도록 제한하는 필터를 적용하는 **Where-Object** cmdlet에 파이프됩니다.

    Get-CsFileTransferFilterConfiguration | Where-Object {$_.Extensions -contains ".xls"}

## 예제 5

예제 5에서는 현재 사용하지 않도록 설정된 모든 파일 전송 필터 구성을 반환합니다. 이 작업을 수행하기 위해 **Get-CsFileTransferFilterConfiguration** cmdlet을 사용하여 조직에서 사용하도록 구성된 모든 정책의 컬렉션을 반환합니다. 이 컬렉션은 Enabled 속성이 False($False)와 같은(-eq) 구성만 선택하는 **Where-Object** cmdlet에 파이프됩니다.

    Get-CsFileTransferFilterConfiguration | Where-Object {$_.Enabled -eq $False}

## 예제 6

예제 6에서는 전역 파일 전송 필터 구성에서 금지하는 전체 파일 확장명 목록을 표시합니다. 먼저 **Get-CsFileTransferFilterConfiguration** cmdlet을 호출하여 Global 구성을 지정합니다. 반환된 정보는 ExpandProperty 매개 변수를 사용하여 Extensions 속성 값을 "확장"하는 **Select-Object** cmdlet에 파이프됩니다. 그런 다음 줄당 파일 확장명 하나씩, 전체 파일 확장명 목록이 화면에 표시됩니다.

    Get-CsFileTransferFilterConfiguration -Identity Global | Select-Object -ExpandProperty Extensions

## 자세한 정보

메신저 대화를 보낼 때 사용자는 파일을 첨부하여 다른 대화 참가자에게 보낼 수 있습니다. 특정 확장명(보통 잠재적으로 유해한 파일 형식의 확장명)을 가진 파일이 Lync 클라이언트를 사용하여 전송되지 않도록 Lync Server를 구성할 수 있습니다.

**Get-CsFileTransferFilterConfiguration** cmdlet을 사용하면 특정 설정 컬렉션을 검색할 수 있습니다. 이러한 설정은 전역 범위 또는 사이트 범위에서 구성될 수 있습니다. 파일 전송 필터 구성에는 전송에서 차단되는 파일 확장명 목록, 필터링이 사용되는 정도(모든 파일 전송이 차단되거나 지정된 확장명을 사용하는 파일만 차단) 및 파일 전송 필터링 사용 여부가 포함됩니다.

이 cmdlet을 실행할 수 있는 사용자: 기본적으로 RTCUniversalUserAdmins 및 RTCUniversalServerAdmins 그룹의 구성원은 **Get-CsFileTransferFilterConfiguration** cmdlet을 로컬로 실행할 수 있습니다. 사용자가 직접 만든 사용자 지정 RBAC(역할 기반 액세스 제어) 역할을 포함하여 이 cmdlet이 할당된 모든 RBAC 역할의 목록을 반환하려면 Windows PowerShell 프롬프트에서 다음 명령을 실행합니다.

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Get-CsFileTransferFilterConfiguration"}

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
<td><p><em>Filter</em></p></td>
<td><p>선택</p></td>
<td><p>System.String</p></td>
<td><p>반환할 파일 전송 필터 구성을 지정할 때 와일드카드를 사용하는 데 사용됩니다. 예를 들어 사이트 범위의 모든 파일 전송 필터 구성을 반환하려면 -Filter &quot;site:*&quot; 구문을 사용합니다. 기본적으로 ID(필터링할 수 있는 유일한 속성)가 문자열 값 &quot;site:&quot;으로 시작하는 파일 전송 필터 구성은 사이트 범위에 구성되어 있습니다.</p></td>
</tr>
<tr class="even">
<td><p><em>Identity</em></p></td>
<td><p>선택</p></td>
<td><p>Microsoft.Rtc.Management.Xds.XdsIdentity</p></td>
<td><p>검색할 파일 전송 필터 구성의 고유 식별자입니다. 전역 설정을 참조하려면 -Identity global 구문을 사용합니다. 사이트 범위에 구성된 설정을 참조하려면 -Identity site:Redmond와 유사한 구문을 사용합니다. ID를 지정할 때 와일드카드 값을 사용할 수 없습니다. 와일드카드를 사용하려면 Filter 매개 변수를 대신 사용합니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>LocalStore</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>중앙 관리 저장소 자체가 아니라 중앙 관리 저장소의 로컬 복제본에서 파일 전송 필터 구성을 검색합니다.</p></td>
</tr>
</tbody>
</table>


## 입력 형식

없음.

## 반환 형식

**Get-CsFileTransferFilterConfiguration** cmdlet은 Microsoft.Rtc.Management.WritableConfig.Settings.ImFilter.FileTransferFilterConfiguration 개체의 인스턴스를 반환합니다.

## 참고 항목

#### 기타 리소스

[New-CsFileTransferFilterConfiguration](new-csfiletransferfilterconfiguration.md)  
[Remove-CsFileTransferFilterConfiguration](remove-csfiletransferfilterconfiguration.md)  
[Set-CsFileTransferFilterConfiguration](set-csfiletransferfilterconfiguration.md)

