---
title: Revoke-CsClientCertificate
TOCTitle: Revoke-CsClientCertificate
ms:assetid: 27d6d4d9-f8ed-4942-b7cf-dd308dafb5bc
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg425748(v=OCS.15)
ms:contentKeyID: 49303115
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Revoke-CsClientCertificate

 

_**마지막으로 수정된 항목:** 2015-03-09_

클라이언트 인증서를 사용하면 Lync Server에 로그온할 때 인증받을 수 있습니다. 인증서는 전화나 기타 Lync Mobile 실행 장치와 같이 사용자 이름 및/또는 암호를 입력하기 어려운 경우에 특히 유용합니다. 관리자는 **Revoke-CsClientCertificate** cmdlet을 통해 사용자에게 발급된 클라이언트 인증서를 해지할 수 있습니다. 이 cmdlet은 Lync Server 2010에서 도입되었습니다.

## 구문

    Revoke-CsClientCertificate -Identity <UserIdParameter> [-Confirm [<SwitchParameter>]] [-Force <SwitchParameter>] [-WhatIf [<SwitchParameter>]]

## 예제

## 예제 1

예제 1에 표시된 명령은 현재 Ken Myer에 할당된 모든 클라이언트 인증서를 해지합니다. 이 작업을 수행하기 위해 뒤에 인증서를 해지할 사용자의 ID를 포함하여 **Revoke-CsClientCertificate** cmdlet을 호출합니다.

    Revoke-CsClientCertificate -Identity "Ken Myer"

## 예제 2

예제 2에서는 조직에서 발급된 모든 클라이언트 인증서를 해지합니다. 이 작업을 수행하기 위해 먼저 **Get-CsUser** cmdlet을 호출하여 조직에서 Lync Server를 사용하도록 설정된 모든 사용자 컬렉션을 반환합니다. 이 컬렉션은 컬렉션의 각 사용자에 대한 인증서를 삭제하는 **Revoke-CsClientCertificate** cmdlet에 파이프됩니다.

    Get-CsUser | Revoke-CsClientCertificate

## 자세한 정보

클라이언트 인증서는 Lync Server에서 사용자를 인증하는 대체 방법을 제공합니다. 사용자는 사용자 이름 및 암호를 제공하는 대신 X.509 인증서를 시스템에 제공합니다. 이 인증서에는 사용자를 식별하는 주체 이름 또는 주체 대체 이름이 있어야 합니다. 사용자가 인증을 받으려면 개인식별번호(PIN)만 입력하면 됩니다. 일반적으로 휴대폰 사용자에게는 영숫자 사용자 이름 및/또는 암호를 입력하는 것보다는 PIN을 입력하는 것이 더 쉽습니다.

관리자는 **Revoke-CsClientCertificate** cmdlet을 사용하여 언제든지 사용자에게 발급된 클라이언트 인증서를 해지할 수 있습니다. **Revoke-CsClientCertificate** cmdlet은 해당 사용자에게 발급된 모든 클라이언트 인증서를 서버에서 해지합니다.

**Revoke-CsClientCertificate** cmdlet은 클라이언트 장치 자체에서 인증서를 삭제하지 않습니다. 대신, 서버에서만 인증서를 삭제합니다. 그러나 이렇게만 해도 클라이언트에서 인증을 위해 인증서를 사용할 수 없습니다. 서버에서 인증서를 찾을 수 없으면 인증 요청이 거부됩니다.

Lync Server Standard Edition을 설치한 경우에는 기본적으로 SQL Server Express에 대한 방화벽 예외가 활성화되지 않습니다. 따라서 Windows PowerShell의 원격 인스턴스에서 **Revoke-CsClientCertificate** cmdlet을 실행할 수 없습니다. 이는 명령이 방화벽을 통과하여 SQL Server Express 데이터베이스에 액세스할 수 없기 때문입니다. 그러나 로컬로, 즉 Standard Edition 서버 자체에서 cmdlet을 실행할 수는 있습니다. Standard Edition을 사용하는 경우 **Revoke-CsClientCertificate** cmdlet을 원격으로 실행하려면 SQL Server Express에 대한 방화벽 예외를 수동으로 활성화해야 합니다.

이 cmdlet을 실행할 수 있는 사용자: 기본적으로 RTCUniversalServerAdmins 그룹의 구성원은 **Revoke-CsClientCertificate** cmdlet을 로컬로 실행할 수 있습니다. 사용자가 직접 만든 사용자 지정 RBAC(역할 기반 액세스 제어) 역할을 포함하여 이 cmdlet이 할당된 모든 RBAC 역할의 목록을 반환하려면 Windows PowerShell 프롬프트에서 다음 명령을 실행합니다.

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Revoke-CsClientCertificate"}

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
<td><p>인증서를 해지할 사용자 계정의 ID를 나타냅니다. 사용자 ID는 네 가지 형식 중 하나를 사용하여 지정할 수 있는데, 이러한 형식은 1) 사용자의 SIP(Session Initiation Protocol) 주소, 2) 사용자의 UPN(사용자 계정 이름), 3) 도메인\로그온 형태인 사용자의 도메인 이름 및 로그온 이름(예: litwareinc\kenmyer) 및 4) 사용자의 Active Directory 표시 이름(예: Ken Myer)입니다. 또한 사용자의 Active Directory 고유 이름을 사용하여 사용자 ID를 참조할 수도 있습니다.</p>
<p></p></td>
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
<td><p>명령을 실행할 때 발생할 수 있는 심각하지 않은 오류 메시지를 표시하지 않습니다.</p></td>
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

문자열 값 또는 Microsoft.Rtc.Management.ADConnect.Schema.ADUser 개체입니다. **Revoke-CsClientCertificate** cmdlet은 사용자 계정의 ID를 나타내는 파이프라인된 문자열 값 입력을 허용합니다. 또한 이 cmdlet은 사용자 개체의 파이프라인된 입력을 허용합니다.

## 반환 형식

없음. 대신 **Revoke-CsClientCertificate** cmdlet은 Microsoft.Rtc.Management.UserPinService.CertInfoDetails 개체의 인스턴스를 해지합니다.

## 참고 항목

#### 기타 리소스

[Get-CsClientCertificate](get-csclientcertificate.md)

