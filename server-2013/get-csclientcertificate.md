---
title: Get-CsClientCertificate
TOCTitle: Get-CsClientCertificate
ms:assetid: 0949288e-9df2-42c4-8297-0dc4cb40d544
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg398143(v=OCS.15)
ms:contentKeyID: 49302742
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Get-CsClientCertificate

 

_**마지막으로 수정된 항목:** 2015-03-09_

사용자에게 발급된 클라이언트 인증서에 대한 정보를 반환합니다. 이 cmdlet은 Lync Server 2010에서 도입되었습니다.

## 구문

    Get-CsClientCertificate -Identity <UserIdParameter> [-Confirm [<SwitchParameter>]] [-WhatIf [<SwitchParameter>]]

## 예제

## 예제 1

예제 1에 표시된 명령은 Ken Myer에게 발급된 모든 클라이언트 인증서를 반환합니다.

    Get-CsClientCertificate -Identity "Ken Myer"

## 예제 2

예제 2에서는 2011년 9월 1일 전에 만료되도록 설정되고 Ken Myer에게 발급된 모든 클라이언트 인증서를 반환합니다. 이 작업을 수행하기 위해 명령은 먼저 **Get-CsClientCertificate** cmdlet을 사용하여 Ken Myer에게 발급된 모든 클라이언트 인증서의 컬렉션을 반환합니다. 이 컬렉션은 ExpirationTime 속성이 2011년 9월 1일(9/1/2011) 이전인 인증서만 선택하는 **Where-Object** cmdlet에 파이프됩니다. 이 예제(9/1/2011)에 지정된 날짜는 날짜-시간 값에 대해 영어(미국) 형식을 사용합니다. 날짜는 사용자의 국가 및 언어 옵션과 호환되는 형식을 사용하여 지정해야 합니다.

    Get-CsClientCertificate -Identity "Ken Myer" | Where-Object {$_.ExpirationTime -lt "9/1/2011"}

## 예제 3

예제 3에서는 2010년 1월 1일 이후로 Ken Myer에게 발급된 모든 클라이언트 인증서를 반환합니다. 이 작업을 수행하기 위해 명령은 먼저 **Get-CsClientCertificate** cmdlet을 호출하여 Ken Myer에게 발급된 모든 클라이언트 인증서의 컬렉션을 반환합니다. 이 컬렉션은 PublicationTime 속성이 2010년 1월 1일(1/1/2010) 이후인 인증서만 선택하는 **Where-Object** cmdlet에 파이프됩니다.

    Get-CsClientCertificate -Identity "Ken Myer" | Where-Object {$_.PublicationTime -gt "1/1/2010"}

## 예제 4

예제 4에 표시된 명령은 Lync Server를 사용할 수 있고 등록자 풀에 할당된 모든 사용자의 클라이언트 인증서를 반환합니다. 등록자 풀에 할당되지 않은 사용자에 대한 인증서 정보를 검색하려고 하면 오류가 반환됩니다. 이 작업을 수행하기 위해 명령은 먼저 매개 변수 없이 **Get-CsUser** cmdlet을 호출합니다. 이 컬렉션은 RegistrarPool 속성이 null 값과 다른 사용자만 선택하는 **Where-Object** cmdlet에 파이프됩니다. 그런 다음 이 필터링된 컬렉션은 컬렉션의 각 사용자에게 할당된 인증서를 반환하는 **Get-CsClientCertificate** cmdlet에 파이프됩니다.

    Get-CsUser | Where-Object {$_.RegistrarPool -ne $Null} | Get-CsClientCertificate

## 자세한 정보

클라이언트 인증서는 Lync Server에서 사용자를 인증하는 대체 방법을 제공합니다. 사용자는 사용자 이름 및 암호를 제공하는 대신 X.509 인증서를 시스템에 제공합니다. 이 인증서에는 사용자를 식별하는 주체 이름 또는 주체 대체 이름이 있어야 합니다. 사용자가 인증을 받으려면 개인식별번호(PIN)만 입력하면 됩니다. 일반적으로 휴대폰 사용자에게는 영숫자 사용자 이름 및/또는 암호를 입력하는 것보다는 PIN을 입력하는 것이 더 쉽습니다.

**Get-CsClientCertificate** cmdlet을 통해 관리자는 사용자에게 발급된 Lync Server 클라이언트 인증서에 대한 정보를 검색할 수 있습니다. 이 정보에는 인증서가 발급된 날짜와 시간, 그리고 인증서가 만료될 날짜와 시간이 포함됩니다.

Lync Server Standard Edition을 설치한 경우에는 기본적으로 SQL Server Express에 대한 방화벽 예외가 활성화되지 않습니다. 따라서 Windows PowerShell의 원격 인스턴스에서 **Get-CsClientCertificate** cmdlet을 실행할 수 없습니다. 이는 명령이 방화벽을 통과하여 SQL Server Express 데이터베이스에 액세스할 수 없기 때문입니다. 그러나 cmdlet을 Standard Edition 서버 자체에서 로컬로 실행할 수는 있습니다. Standard Edition 서버에 대해 원격으로 **Get-CsClientCertificate** cmdlet을 실행하려면 SQL Server Express의 방화벽 예외를 수동으로 활성화해야 합니다.

이 cmdlet을 실행할 수 있는 사용자: 기본적으로 RTCUniversalServerAdmins 그룹의 구성원은 **Get-CsClientCertificate** cmdlet을 로컬로 실행할 수 있습니다. 사용자가 직접 만든 사용자 지정 RBAC(역할 기반 액세스 제어) 역할을 포함하여 이 cmdlet이 할당된 모든 RBAC 역할의 목록을 반환하려면 Windows PowerShell 프롬프트에서 다음 명령을 실행합니다.

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Get-CsClientCertificate"}

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
<td><p>Microsoft.Rtc.Management.AD.UserIdParameter</p></td>
<td><p>인증서 정보를 검색할 사용자 계정의 ID를 나타냅니다. 사용자 ID는 네 가지 형식 중 하나를 사용하여 지정할 수 있는데, 이러한 형식은 1) 사용자의 SIP(Session Initiation Protocol) 주소, 2) 사용자의 UPN(사용자 계정 이름), 3) 도메인\로그온 형태인 사용자의 도메인 이름 및 로그온 이름(예: litwareinc\kenmyer) 및 4) 사용자의 Active Directory 표시 이름(예: Ken Myer)입니다. 또한 사용자의 Active Directory 고유 이름을 사용하여 사용자 계정을 참조할 수도 있습니다.</p>
<p>사용자 ID를 지정할 때는 와일드카드를 사용할 수 없습니다.</p>
<p></p></td>
</tr>
<tr class="even">
<td><p><em>Confirm</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>명령을 실행하기 전에 확인 메시지를 표시합니다.</p></td>
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

문자열 값 또는 Microsoft.Rtc.Management.ADConnect.Schema.ADUser 개체입니다. **Get-CsClientCertificate** cmdlet은 사용자 계정의 ID를 나타내는 파이프라인된 문자 열 값 입력을 허용합니다. 또한 이 cmdlet은 사용자 개체의 파이프라인된 입력을 허용합니다.

## 반환 형식

**Get-CsClientCertificate** cmdlet은 Microsoft.Rtc.Management.UserPinService.CertInfoDetails 개체의 인스턴스를 반환합니다.

## 참고 항목

#### 기타 리소스

[Revoke-CsClientCertificate](revoke-csclientcertificate.md)

