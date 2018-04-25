---
title: Get-CsDeviceUpdateConfiguration
TOCTitle: Get-CsDeviceUpdateConfiguration
ms:assetid: e7adc8a7-616a-41b1-8f4b-5f8778e46f55
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg399030(v=OCS.15)
ms:contentKeyID: 49305368
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Get-CsDeviceUpdateConfiguration

 

_**마지막으로 수정된 항목:** 2015-03-09_

조직에 현재 배포된 장치 업데이트 구성 설정에 대한 정보를 반환합니다. 이러한 설정은 관리자가 전화기 및 Lync Server를 실행하는 기타 장치에 펌웨어 업데이트를 배포하는 데 사용할 수 있는 Lync Server 구성 요소인 장치 업데이트 웹 서비스를 관리하도록 도와줍니다. 이 cmdlet은 Lync Server 2010에서 도입되었습니다.

## 구문

    Get-CsDeviceUpdateConfiguration [-Identity <XdsIdentity>] <COMMON PARAMETERS>

    Get-CsDeviceUpdateConfiguration [-Filter <String>] <COMMON PARAMETERS>

    COMMON PARAMETERS: [-LocalStore <SwitchParameter>]

## 예제

## 예제 1

예제 1에 표시된 명령은 조직에서 현재 사용 중인 모든 장치 업데이트 구성 설정 컬렉션을 반환합니다. 추가 매개 변수를 지정하지 않고 **Get-CsDeviceUpdateConfiguration** cmdlet을 호출하면 현재 사용 중인 모든 장치 업데이트 설정이 반환됩니다.

    Get-CsDeviceUpdateConfiguration 

## 예제 2

예제 2에서는 전역 장치 업데이트 구성 설정에 대한 정보를 반환합니다.

    Get-CsDeviceUpdateConfiguration -Identity Global

## 예제 3

예제 3에서는 Filter 매개 변수 사용 방법을 보여 줍니다. 필터 값 "site:\*"는 사이트 범위에서 적용되는 모든 장치 업데이트 구성 설정 컬렉션을 반환합니다. 이러한 설정의 ID는 모두 문자열 값 "site:"으로 시작하기 때문입니다.

    Get-CsDeviceUpdateConfiguration -Filter site:*

## 예제 4

예제 4에서는 MaxLogFileSize 속성이 2048000바이트보다 큰 모든 장치 업데이트 구성 설정을 반환합니다. 이 작업을 수행하기 위해 **Get-CsDeviceUpdateConfiguration** cmdlet을 사용하여 현재 사용 중인 모든 장치 업데이트 구성 설정 컬렉션을 반환합니다. 이 컬렉션은 MaxLogFileSize 속성이 2048000보다 큰 설정만 선택하는 **Where-Object** cmdlet에 파이프됩니다.

    Get-CsDeviceUpdateConfiguration | Where-Object {$_.MaxLogFileSize -gt 2048000}

## 예제 5

예제 5에 표시된 명령은 유효한 로그 파일 형식으로 "Watson"을 포함하는 모든 장치 업데이트 구성 설정을 반환합니다. 이 작업을 수행하기 위해 **Get-CsDeviceUpdateConfiguration** cmdlet을 사용하여 모든 장치 업데이트 구성 설정 컬렉션을 반환합니다. 이 컬렉션은 유효한 로그 파일 형식 집합에 "Watson"이 포함된 장치 설정만 선택하는 **Where-Object** cmdlet에 파이프됩니다.

    Get-CsDeviceUpdateConfiguration | Where-Object {$_.ValidLogFileTypes -like "*Watson*"}

## 자세한 정보

장치 업데이트 웹 서비스를 사용하면 관리자가 Lync Server를 실행하는 장치에 펌웨어 업데이트를 배포할 수 있습니다. 관리자는 주기적으로 Lync Server에 장치 업데이트 규칙 집합을 업로드하면 됩니다. 이러한 규칙을 테스트하고 승인한 후에는 규칙이 해당 장치(시스템에 연결된 경우)에 적용됩니다. 장치는 장치를 켤 때 업데이트를 확인한 다음 사용자가 로그온하면 다시 확인합니다. 이후에는 24시간마다 업데이트를 확인합니다.

장치 업데이트 웹 서비스는 장치 구성 설정을 사용하여 관리할 수 있습니다. 이러한 설정은 전역 범위 또는 사이트 범위에 적용됩니다. **Get-CsDeviceUpdateConfiguration** cmdlet을 사용하여 조직에서 현재 사용 중인 장치 업데이트 구성 설정에 대한 정보를 반환할 수 있습니다.

이 cmdlet을 실행할 수 있는 사용자: 기본적으로 RTCUniversalUserAdmins 및 RTCUniversalServerAdmins 그룹의 구성원은 **Get-CsDeviceUpdateConfiguration** cmdlet을 로컬로 실행할 수 있습니다. 사용자가 직접 만든 사용자 지정 RBAC(역할 기반 액세스 제어) 역할을 포함하여 이 cmdlet이 할당된 모든 RBAC 역할의 목록을 반환하려면 Windows PowerShell 프롬프트에서 다음 명령을 실행합니다.

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Approve-CsDeviceUpdateRule"}

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
<td><p>장치 업데이트 구성 설정을 지정할 때 와일드카드 문자를 사용할 수 있는 방법을 제공합니다. 예를 들어 사이트 범위에서 적용된 모든 구성 설정의 컬렉션을 반환하려면 -Filter &quot;site:*&quot; 구문을 사용하고, ID에 &quot;EMEA&quot;라는 단어가 포함된 모든 설정을 반환하려면 -Filter &quot;*EMEA*&quot; 구문을 사용합니다. 설정 ID에는 Filter 매개 변수만 작동하며 다른 장치 업데이트 구성 속성을 필터링할 수 없습니다.</p></td>
</tr>
<tr class="even">
<td><p><em>Identity</em></p></td>
<td><p>선택</p></td>
<td><p>Microsoft.Rtc.Management.Xds.XdsIdentity</p></td>
<td><p>검색할 장치 업데이트 구성 설정의 ID를 나타냅니다. 전역 설정을 참조하려면 -Identity global 구문을 사용하고, 사이트 설정을 참조하려면 -Identity site:Redmond와 유사한 구문을 사용합니다. ID를 지정할 때는 와일드카드를 사용할 수 없습니다. 와일드카드를 사용해야 하는 경우 Filter 매개 변수를 대신 사용하십시오.</p></td>
</tr>
<tr class="odd">
<td><p><em>LocalStore</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>중앙 관리 저장소 자체가 아니라 중앙 관리 저장소의 로컬 복제본에서 장치 업데이트 구성 데이터를 검색합니다.</p></td>
</tr>
</tbody>
</table>


## 입력 형식

없음. **Get-CsDeviceUpdateConfiguration** cmdlet은 파이프라인된 입력을 허용하지 않습니다.

## 반환 형식

**Get-CsDeviceUpdateConfiguration** cmdlet은 Microsoft.Rtc.Management.WritableConfig.Settings.DeviceUpdate.DeviceUpdateConfiguration 개체의 인스턴스를 반환합니다.

## 참고 항목

#### 기타 리소스

[New-CsDeviceUpdateConfiguration](new-csdeviceupdateconfiguration.md)  
[Remove-CsDeviceUpdateConfiguration](remove-csdeviceupdateconfiguration.md)  
[Set-CsDeviceUpdateConfiguration](set-csdeviceupdateconfiguration.md)

