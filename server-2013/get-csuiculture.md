---
title: Get-CsUICulture
TOCTitle: Get-CsUICulture
ms:assetid: b8df7083-068b-4d5e-a9b4-448602de6586
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg412900(v=OCS.15)
ms:contentKeyID: 49304828
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Get-CsUICulture

 

_**마지막으로 수정된 항목:** 2015-03-09_

Lync Server 관리 셸에서 사용하는 문화권(즉, 언어 및 지역 설정)에 대한 정보를 반환합니다. 이 cmdlet은 Lync Server 2010에서 도입되었습니다.

## 구문

    Get-CsUICulture

## 예제

## 예제 1

예제 1에 표시된 명령은 Lync Server 관리 셸에서 현재 사용 중인 문화권에 대한 기본 정보를 반환합니다.

    Get-CsUICulture

## 자세한 정보

Lync Server를 여러 언어로 사용할 수 있지만 이 소프트웨어는 실제로 MUI(다국어 사용자 인터페이스) 응용 프로그램이 아닙니다. 특히 이는 운영 체제 언어를 변경할 때 Lync Server 관리 셸의 사용자 인터페이스 언어가 변경되지 않음을 의미합니다. 예를 들어 영어(미국) 버전의 Lync Server를 설치하고 영어(미국) Windows 운영 체제를 실행하는 경우 운영 체제 문화권(즉, 언어 및 지역 설정)을 한국어로 변경하면 Lync Server 관리 셸이 그에 맞게 자동으로 변경되지 않고 대신 오류 메시지 및 도움말 텍스트를 비롯한 Lync Server 관리 셸 사용자 인터페이스가 영어(미국)로 그대로 유지됩니다. Lync Server 관리 셸의 문화권을 변경해야 하는 경우 **Set-CsUICulture** cmdlet을 실행해야 합니다.

**Get-CsUICulture** cmdlet을 사용하면 Lync Server 관리 셸에서 현재 사용 중인 문화권을 확인할 수 있습니다.

이 cmdlet을 실행할 수 있는 사용자: 기본적으로 RTCUniversalUserAdmins, RTCUniversalServerAdmins 및 RTCUniversalReadOnlyAdmins 그룹의 구성원은 **Get-CsUICulture** cmdlet을 로컬로 실행할 수 있습니다.

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
<td><p></p></td>
<td><p></p></td>
<td><p></p></td>
<td><p></p></td>
</tr>
<tr class="even">
<td><p>이 cmdlet은 일반 Windows PowerShell 매개 변수만 제공합니다.</p></td>
<td><p></p></td>
<td><p></p></td>
<td><p></p></td>
</tr>
</tbody>
</table>


## 입력 형식

없음. **Get-CsUICulture** cmdlet은 파이프라인된 입력을 허용하지 않습니다.

## 반환 형식

**Get-CsUICulture** cmdlet은 System.Globalization.CultureInfo 클래스의 인스턴스를 반환합니다.

## 참고 항목

#### 기타 리소스

[Set-CsUICulture](set-csuiculture.md)

