---
title: Get-CsAdServerSchema
TOCTitle: Get-CsAdServerSchema
ms:assetid: fba777e5-886c-4914-a492-f2237721c57c
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg413070(v=OCS.15)
ms:contentKeyID: 49305612
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Get-CsAdServerSchema

 

_**마지막으로 수정된 항목:** 2015-03-09_

Active Directory 스키마가 Lync Server를 설치할 수 있도록 올바르게 구성되었는지 여부를 나타내는 정보를 반환합니다. 이 cmdlet은 Lync Server 2010에서 도입되었습니다.

## 구문

    Get-CsAdServerSchema [-Report <String>]

## 예제

## 예제 1

예제 1에 표시된 명령은 Active Directory 서버 스키마의 현재 상태를 반환합니다. 스키마가 최신 상태인 경우 명령은 SCHEMA\_VERSION\_STATE\_CURRENT 값을 반환합니다.

    Get-CsAdServerSchema

## 예제 2

예제 2에서도 Active Directory 서버 스키마의 현재 상태를 반환합니다. 뿐만 아니라 이 명령은 해당 스키마에 대한 보다 자세한 정보를C:\\Logs\\Server\_Schema.html 파일에 기록합니다. 여기에는 스키마의 주 버전 및 부 버전과 같은 정보가 포함됩니다.

    Get-CsAdServerSchema -Report C:\Logs\Server_Schema.html

## 자세한 정보

Active Directory 스키마를 제대로 확장하지 않으면 Lync Server를 설치할 수 없습니다. 즉, 설치를 실행하려면 먼저 Lync Server 관련 개체 및 특성을 Active Directory 도메인 서비스에 추가해야 합니다. 예를 들어 사용자에게 할당된 음성 정책을 나타내거나 사용자 계정이 Enterprise Voice를 사용하도록 설정되어 있는지 여부를 보고하는 등의 작업을 수행하는 특성을 허용하도록 사용자 계정 개체를 수정해야 합니다.

**Get-CsAdServerSchema** cmdlet은 Active Directory가 확장되고 Lync Server를 설치할 준비가 되었는지 여부를 알려 주는 단일 값을 반환합니다. **Get-CsAdServerSchema** cmdlet에서 SCHEMA\_VERSION\_STATE\_CURRENT 값을 반환하면 스키마가 확장된 것이고, 이 cmdlet에서 다른 값을 반환하면 스키마가 확장되지 않은 것입니다.

**Get-CsAdServerSchema** cmdlet은 일반적으로 설치 마법사의 일부로 실행됩니다. 설치 프로그램에서 이 스키마가 제대로 준비되지 않은 것으로 인식하면 오류 메시지가 나타나고 설치가 중지됩니다. 그러나 설치 마법사와 독립적으로 **Get-CsAdServerSchema** cmdlet을 실행할 수도 있습니다. 이를 통해 Lync Server를 설치하기 전에 스키마 상태를 확인할 수 있습니다.

**Get-CsAdServerSchema** cmdlet은 Microsoft Office Communications Server 2007 R2 명령 Lcscmd.exe /domain /action:CheckSchemaPrepState와 동일한 기능을 수행합니다.

이 cmdlet을 실행할 수 있는 사용자: 기본적으로 Active Directory에 대한 읽기 권한을 가진 사용자는 누구나 **Get-CsAdServerSchema** cmdlet을 로컬로 실행할 수 있습니다. 일반적으로 모든 도메인 구성원은 이 권한이 있습니다.

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
<td><p><em>Report</em></p></td>
<td><p>선택</p></td>
<td><p>System.String</p></td>
<td><p>cmdlet이 실행될 때 만들어지는 로그 파일의 파일 경로를 지정하는 데 사용됩니다(예: -Report &quot;C:\Logs\SchemaPrep.html&quot;).</p></td>
</tr>
</tbody>
</table>


## 입력 형식

없음. **Get-CsAdServerSchema** cmdlet은 파이프라인된 입력을 허용하지 않습니다.

## 반환 형식

**Get-CsAdServerSchema** cmdlet은 Microsoft.Rtc.Management.Deployment.SchemaVersionState 개체의 인스턴스를 반환합니다.

## 참고 항목

#### 기타 리소스

[Install-CsAdServerSchema](install-csadserverschema.md)

