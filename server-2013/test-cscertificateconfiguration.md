---
title: Test-CsCertificateConfiguration
TOCTitle: Test-CsCertificateConfiguration
ms:assetid: 8086bdf7-d283-4666-9f6c-0d5a3a31b3a6
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg398647(v=OCS.15)
ms:contentKeyID: 49304193
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Test-CsCertificateConfiguration

 

_**마지막으로 수정된 항목:** 2015-03-09_

로컬 컴퓨터에 사용되는 Lync Server 인증서에 대한 정보를 반환합니다. 이 cmdlet은 Lync Server 2010에서 도입되었습니다.

## 구문

    Test-CsCertificateConfiguration [-Report <String>]

## 예제

## 예제 1

예제 1에 표시된 명령은 로컬 컴퓨터의 Lync Server에서 현재 사용 중인 인증서에 대한 정보를 반환합니다.

    Test-CsCertificateConfiguration

## 예제 2

예제 2에 표시된 명령은 예제 1에 표시된 명령의 변형입니다. 단, 이 경우에는 **Test-CsCertificateConfiguration** cmdlet을 실행할 때 생성되는 출력 파일에 대한 파일 경로(C:\\Logs\\Certificates.xml)를 지정하는 데 Report 매개 변수가 사용됩니다.

    Test-CsCertificateConfiguration -Report "C:\Logs\Certificates.xml"

## 자세한 정보

**Test-CsCertificateConfiguration** cmdlet은 "가상 트랜잭션"의 한 예입니다. 가상 트랜잭션은 Lync Server에서 사용자가 시스템 로그온, 메신저 대화 교환 또는 PSTN(공중 전화망)의 전화로 전화 걸기와 같은 일반적인 작업을 성공적으로 수행할 수 있는지 확인하는 데 사용됩니다. 이러한 테스트는 관리자가 "수동으로" 수행하거나 Microsoft System Center Operations Manager(이전 Microsoft Operations Manager)와 같은 응용 프로그램에 의해 자동으로 실행될 수 있습니다.

**Test-CsCertificateConfiguration** cmdlet은 Lync Server에 사용되는 인증서에 대한 정보를 반환합니다. **Test-CsCertificateConfiguration** cmdlet은 주로 인증서 마법사에서 사용하도록 만들어졌습니다. 관리자는 인증서 정보를 검색할 때 **Get-CsCertificate** cmdlet을 사용하는 것이 좋습니다.

이 cmdlet을 실행할 수 있는 사용자: 사용자가 직접 만든 사용자 지정 RBAC(역할 기반 액세스 제어) 역할을 포함하여 이 cmdlet이 할당된 모든 RBAC 역할의 목록을 반환하려면 Windows PowerShell 프롬프트에서 다음 명령을 실행합니다.

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Test-CsCertificateConfiguration"}

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
<td><p>cmdlet이 실행될 때 만들어진 로그 파일에 대한 파일 경로를 지정할 수 있도록 합니다. 예를 들면 다음과 같습니다. -Report &quot;C:\Logs\Certificates.html&quot;. 이 파일이 이미 있는 경우 cmdlet을 실행할 때 덮어쓰게 됩니다.</p></td>
</tr>
</tbody>
</table>


## 입력 형식

없음. **Test-CsCertificateConfiguration** cmdlet은 파이프라인된 입력을 허용하지 않습니다.

## 반환 형식

**Test-CsCertificateConfiguration** cmdlet은 Microsoft.Rtc.Management.Deployment,CertificateExists 개체의 인스턴스를 반환합니다.

## 참고 항목

#### 기타 리소스

[Get-CsCertificate](get-cscertificate.md)

