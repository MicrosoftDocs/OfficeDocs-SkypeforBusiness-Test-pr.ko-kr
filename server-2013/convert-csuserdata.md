---
title: Convert-CsUserData
TOCTitle: Convert-CsUserData
ms:assetid: e52f8037-19f3-49c9-8dfc-79b0c27d8b94
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/JJ205337(v=OCS.15)
ms:contentKeyID: 49305335
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Convert-CsUserData

 

_**마지막으로 수정된 항목:** 2015-03-09_

내보낸 사용자 데이터를 Microsoft Lync Server 2010 또는 Lync Server 2013에서 사용하는 데이터 형식으로 변환합니다. 이 cmdlet은 Lync Server 2013에서 도입되었습니다.

## 구문

    Convert-CsUserData -InputFile <String> -OutputFile <String> -TargetVersion <Lync2010 | Current> [-ConfDirectoryFilter <String>] [-Force <SwitchParameter>] [-UserFilter <String>]

## 예제

## 예제 1

예제 1에 표시된 명령은 C:\\Logs\\Lync2013Data.zip 파일에 저장된 사용자 데이터를 Lync Server 2010에서 사용되는 사용자 데이터 형식으로 변환합니다. 변환된 데이터는 XML 파일 C:\\Logs\\Lync2010Data.xml에 저장됩니다.

    Convert-CsUserData -InputFile "C:\Logs\Lync2013Data.Zip" -OutputFile "C:\Logs\Lync2010Data.xml" -TargetVersion Lync2010

## 예제 2

예제 2에서는 단일 사용자(이 예제에서는 SIP 주소가 kenmyer@litwareinc.com인 사용자)의 데이터를 변환하는 방법을 보여 줍니다. 이 작업은 UserFilter 매개 변수와 사용자의 SIP 주소(sip: 접두사는 제외)를 차례로 포함하여 수행합니다.

    Convert-CsUserData -InputFile "C:\Logs\Lync2013Data.Zip" -OutputFile "C:\Logs\Lync2010data.xml" -TargetVersion Lync2010 -UserFilter "kenmyer@litwareinc.com"

## 자세한 정보

**Convert-CsUserData** cmdlet은 [Export-CsUserData](export-csuserdata.md) cmdlet을 사용하여 내보낸 데이터를 가져온 다음 Microsoft Lync Server 2010 또는 Lync Server 2013에서 사용되는 사용자 데이터 형식으로 변환합니다. 그러면 **Import-CsUserData** cmdlet이 해당 데이터를 적절한 Lync Server 버전으로 가져올 수 있습니다.

사용자가 직접 만든 사용자 지정 RBAC(역할 기반 액세스 제어) 역할을 포함하여 이 cmdlet이 할당된 모든 RBAC 역할의 목록을 반환하려면 Windows PowerShell 명령줄 인터페이스 프롬프트에서 다음 명령을 실행합니다.

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Convert-CsUserData"}

**Lync Server 제어판:** **Convert-CsUserData** cmdlet에 의해 수행되는 기능은 Lync Server 제어판에서는 사용할 수 없습니다.

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
<td><p><em>InputFile</em></p></td>
<td><p>필수</p></td>
<td><p>System.String</p></td>
<td><p>변환할 사용자 데이터가 포함된 .ZIP 파일 또는 .XML 파일의 전체 경로입니다. 예를 들면 다음과 같습니다.</p>
<p>-InputFile “C:\Data\Lync2010.zip&quot;</p></td>
</tr>
<tr class="even">
<td><p><em>OutputFile</em></p></td>
<td><p>필수</p></td>
<td><p>System.String</p></td>
<td><p>변환된 데이터를 저장할 파일의 전체 경로입니다. Microsoft Lync Server 2010 형식을 사용하여 데이터를 출력하는 경우에는 출력 파일이 다음과 같이 .XML 파일 확장명을 사용해야 합니다.</p>
<p>-OutputFile &quot;C:\Data\ConvertedLync2010Data.xml&quot;</p>
<p>Lync Server 2013 형식을 사용하는 경우에는 출력 파일이 .ZIP 파일 확장명을 사용해야 합니다.</p>
<p>-OutputFile &quot;C:\Data\ConvertedLyncData.zip&quot;</p></td>
</tr>
<tr class="odd">
<td><p><em>TargetVersion</em></p></td>
<td><p>필수</p></td>
<td><p>Microsoft.Rtc.Management.BlobStore.Cmdlets.ConvertTarget</p></td>
<td><p>변환된 데이터의 형식을 나타냅니다. 허용되는 값은 다음과 같습니다.</p>
<p>Lync2010</p>
<p>Current</p></td>
</tr>
<tr class="even">
<td><p><em>ConfDirectoryFilter</em></p></td>
<td><p>선택</p></td>
<td><p>System.String</p></td>
<td><p>전화 회의 디렉터리 데이터를 변환할 수 있습니다. 이 작업을 수행하려면 ConfDirectoryFilter 매개 변수를 포함하고 전화 회의 디렉터리의 ID를 지정합니다.</p>
<p>-ConfDirectoryFilter 13</p>
<p>다음 명령을 사용하면 전화 회의 디렉터리 ID를 검색할 수 있습니다.</p>
<p>Get-CsConferenceDirectory | Select-Object Identity, ServiceId</p></td>
</tr>
<tr class="odd">
<td><p><em>Force</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>명령을 실행할 때 발생할 수 있는 심각하지 않은 오류 메시지를 표시하지 않습니다.</p></td>
</tr>
<tr class="even">
<td><p><em>UserFilter</em></p></td>
<td><p>선택</p></td>
<td><p>System.String</p></td>
<td><p>단일 사용자에 대한 데이터를 변환할 수 있습니다. 특정 사용자를 지정하려면 다음과 같이 sip: 접두사를 포함하지 않고 해당 사용자의 SIP 주소를 사용합니다.</p>
<p>-UserFilter &quot;kenmyer@litwareinc.com&quot;</p></td>
</tr>
</tbody>
</table>


## 입력 형식

없음. **Convert-CsUserData** cmdlet은 파이프라인된 입력을 허용하지 않습니다.

## 반환 형식

**Convert-CsUserData** cmdlet은 변환된 데이터를 Lync Server 2010에서 사용할지 Lync Server 2013에서 사용할지에 따라 XML 또는 ZIP 파일을 만듭니다.

## 참고 항목

#### 기타 리소스

[Export-CsUserData](export-csuserdata.md)  
[Import-CsUserData](import-csuserdata.md)  
[Sync-CsUserData](sync-csuserdata.md)  
[Update-CsUserData](update-csuserdata.md)

