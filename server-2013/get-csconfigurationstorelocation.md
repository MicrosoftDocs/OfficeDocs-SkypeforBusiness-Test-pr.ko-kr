---
title: Get-CsConfigurationStoreLocation
TOCTitle: Get-CsConfigurationStoreLocation
ms:assetid: abfda147-02fa-46a5-a988-d83daf4cc455
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg412814(v=OCS.15)
ms:contentKeyID: 49304687
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Get-CsConfigurationStoreLocation

 

_**마지막으로 수정된 항목:** 2015-03-09_

중앙 관리 저장소의 Active Directory 서비스 제어 지점 위치를 다시 보고합니다. 이 cmdlet은 Lync Server 2010에서 도입되었습니다.

## 구문

    Get-CsConfigurationStoreLocation [-GlobalSettingsDomainController <Fqdn>] [-Report <String>]

## 예제

## 예제 1

예제 1에 표시된 명령은 중앙 관리 저장소를 호스트하는 컴퓨터 또는 풀에 SQL Server 경로를 반환합니다.

    Get-CsConfigurationStoreLocation

## 예제 2

예제 2는 예제 1에 표시된 명령의 변형입니다. 그러나 이 예제에서는 Report 매개 변수를 포함하여 **Get-CsConfigurationStoreLocation** cmdlet을 실행할 때 생성되는 보고서의 경로를 지정합니다.

    Get-CsConfigurationStoreLocation -Report "C:\Logs\ConfigurationStore.html"

## 자세한 정보

Active Directory 도메인 서비스는 SCP(서비스 제어 지점)를 사용하여 컴퓨터가 서비스를 찾을 수 있도록 도와줍니다. 예를 들어 Lync Server를 설치하면 Lync Server 데이터를 유지 관리하는 데 사용되는 위치 정보를 중앙 관리 저장소에 제공하는 서비스 제어 지점이 만들어집니다. 데이터베이스에 액세스해야 하는 컴퓨터는 Active Directory에 연결하고 SCP에 포함된 정보를 사용하여 올바른 컴퓨터와 올바른 SQL Server 인스턴스를 찾습니다.

**Get-CsConfigurationStoreLocation** cmdlet은 중앙 관리 저장소를 실행하는 컴퓨터에 SQL Server 경로(예: atl-sql-001.litwareinc.com/rtc)를 다시 보고하는 데 사용됩니다.

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
<td><p><em>GlobalSettingsDomainController</em></p></td>
<td><p>선택</p></td>
<td><p>Microsoft.Rtc.Management.Deploy.Fqdn</p></td>
<td><p>전역 설정이 저장되는 도메인 컨트롤러의 FQDN(정규화된 도메인 이름)입니다. 전역 설정이 Active Directory 시스템 컨테이너에 저장된 경우 이 매개 변수는 루트 도메인 컨트롤러를 가리켜야 합니다. 전역 설정이 구성 컨테이너에 저장된 경우 아무 도메인 컨트롤러나 사용할 수 있으며 이 매개 변수는 생략해도 됩니다.</p></td>
</tr>
<tr class="even">
<td><p><em>Report</em></p></td>
<td><p>선택</p></td>
<td><p>System.String</p></td>
<td><p>cmdlet이 실행될 때 만들어지는 로그 파일의 파일 경로를 지정하는 데 사용됩니다(예: -Report &quot;C:\Logs\ConfigurationStore.html&quot;).</p></td>
</tr>
</tbody>
</table>


## 입력 형식

없음. **Get-CsConfigurationStoreLocation** cmdlet은 파이프라인된 입력을 허용하지 않습니다.

## 반환 형식

문자열. **Get-CsConfigurationStoreLocation** cmdlet은 구성 저장소의 위치를 다시 보고합니다.

## 참고 항목

#### 기타 리소스

[Remove-CsConfigurationStoreLocation](remove-csconfigurationstorelocation.md)  
[Set-CsConfigurationStoreLocation](set-csconfigurationstorelocation.md)

