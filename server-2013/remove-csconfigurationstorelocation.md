---
title: Remove-CsConfigurationStoreLocation
TOCTitle: Remove-CsConfigurationStoreLocation
ms:assetid: 141be225-c6e4-4377-913b-ba61528929d4
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg398214(v=OCS.15)
ms:contentKeyID: 49302887
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Remove-CsConfigurationStoreLocation

 

_**마지막으로 수정된 항목:** 2015-03-09_

중앙 관리 저장소의 Active Directory 서비스 제어 지점을 제거합니다. 이 cmdlet은 Lync Server 2010에서 도입되었습니다.

## 구문

    Remove-CsConfigurationStoreLocation [-Confirm [<SwitchParameter>]] [-Force <SwitchParameter>] [-GlobalSettingsDomainController <Fqdn>] [-Report <String>] [-WhatIf [<SwitchParameter>]]

## 예제

## 예제 1

예제 1에 표시된 명령은 중앙 관리 저장소에 대한 Active Directory 서비스 제어 지점을 제거합니다. 이 SCP를 복원하거나 새 SCP를 만들려면 **Set-CsConfigurationStoreLocation** cmdlet을 실행해야 합니다.

    Remove-CsConfigurationStoreLocation

## 예제 2

예제 2에서도 중앙 관리 저장소의 Active Directory 서비스 제어 지점을 제거합니다. 하지만 이 예제의 명령은 SCP를 삭제할 뿐만 아니라 작업 성공 여부에 대한 정보를 C:\\Logs\\Store\_Location.html 로그 파일에 기록합니다. 이 로그 파일을 만들기 위해 Report 매개 변수를 사용하고 그 뒤에 정보를 기록할 로그 파일의 경로를 포함합니다. 이 파일이 이미 존재하는 경우 명령을 실행할 때 내용이 덮어써집니다. 파일이 존재하지 않으면 명령을 실행할 때 파일이 만들어집니다.

    Remove-CsConfigurationStoreLocation -Report C:\Logs\Store_Location.html

## 자세한 정보

Active Directory 도메인 서비스는 SCP(서비스 제어 지점)를 사용하여 컴퓨터가 서비스를 찾을 수 있도록 도와줍니다. 예를 들어 Lync Server를 설치하면 Lync Server 데이터를 유지 관리하는 데 사용되는 위치 정보를 중앙 관리 저장소에 제공하는 SCP가 만들어집니다. 데이터베이스에 액세스해야 하는 컴퓨터는 Active Directory에 연결하고 SCP에 포함된 정보를 사용하여 올바른 컴퓨터와 올바른 SQL Server 인스턴스를 찾습니다.

앞에서 설명한 대로 Lync Server를 설치하면 중앙 관리 저장소에 대한 SCP가 자동으로 만들어집니다. 일반적으로 SCP는 삭제하지 않습니다. SCP를 삭제하면 컴퓨터에서 데이터베이스를 찾을 수 없게 됩니다. 그러나 문제를 해결할 때와 같이 SCP를 삭제해야 하는 경우가 있을 수 있습니다. 이 경우 **Remove-CsConfigurationStoreLocation** cmdlet을 사용합니다. SCP가 삭제된 다음에는 **Set-CsConfigurationStoreLocation** cmdlet을 사용하여 다시 만들거나 새 서비스 제어 지점을 만들 수 있습니다.

이 cmdlet을 실행할 수 있는 사용자: 기본적으로 RTCUniversalServerAdmins 그룹의 구성원은 **Remove-CsConfigurationStoreLocation** cmdlet을 실행할 수 있습니다.

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
<td><p><em>GlobalSettingsDomainController</em></p></td>
<td><p>선택</p></td>
<td><p>Microsoft.Rtc.Management.Deploy.Fqdn</p></td>
<td><p>전역 설정이 저장되는 도메인 컨트롤러의 FQDN(정규화된 도메인 이름)입니다. 전역 설정이 Active Directory 시스템 컨테이너에 저장된 경우 이 매개 변수는 루트 도메인 컨트롤러를 가리켜야 합니다. 전역 설정이 구성 컨테이너에 저장된 경우 아무 도메인 컨트롤러나 사용할 수 있으며 이 매개 변수는 생략해도 됩니다.</p></td>
</tr>
<tr class="even">
<td><p><em>Report</em></p></td>
<td><p>선택</p></td>
<td><p>System.String</p></td>
<td><p>cmdlet을 실행할 때 만들어지는 로그 파일의 파일 경로를 지정할 수 있습니다. (예: -Report &quot;C:\Logs\ConfigurationStore.html&quot;).</p></td>
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

없음. **Remove-CsConfigurationStoreLocation** cmdlet은 파이프라인된 입력을 허용하지 않습니다.

## 반환 형식

**Remove-CsConfigurationStoreLocation** cmdlet은 개체나 값을 반환하지 않습니다.

## 참고 항목

#### 기타 리소스

[Get-CsConfigurationStoreLocation](get-csconfigurationstorelocation.md)  
[Set-CsConfigurationStoreLocation](set-csconfigurationstorelocation.md)

