---
title: Move-CsRgsConfiguration
TOCTitle: Move-CsRgsConfiguration
ms:assetid: 983eadb8-baee-41ba-bba4-2f2b01471250
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg398782(v=OCS.15)
ms:contentKeyID: 49304472
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Move-CsRgsConfiguration

 

_**마지막으로 수정된 항목:** 2015-03-09_

Microsoft Office Communications Server 2007 R2 또는 Microsoft Lync Server 2010에서 Microsoft Lync Server 2013로 응답 그룹 구성 설정을 마이그레이션하는 데 사용됩니다. 이 cmdlet은 Lync Server 2010에서 도입되었습니다.

## 구문

    Move-CsRgsConfiguration -Destination <String> -Source <String> [-Force <SwitchParameter>]

## 예제

## 예제 1

예제 1에 표시된 명령은 응답 그룹 응용 프로그램을 atl-ocsrgs-001.litwareinc.com에서 redmond-lyncrgs-001.litwareinc.com으로 마이그레이션합니다.

    Move-CsRgsConfiguration -Source atl-ocsrgs-001.litwareinc.com -Destination redmond-lyncrgs-001.litwareinc.com 

## 자세한 정보

응답 그룹 응용 프로그램에서는 지원 센터 또는 고객 지원과 같은 엔터티로 전화 통화를 자동으로 경로 지정하는 기능을 제공합니다. 발신자가 지정된 전화 번호로 전화를 걸면 이 전화를 적절한 응답 그룹 에이전트 집합으로 자동으로 경로 지정할 수 있습니다. 또는 IVR(대화형 음성 응답) 큐로 전화를 경로 지정할 수도 있습니다. 이 큐에서는 발신자에게 일련의 질문(예: "기존 주문과 관련하여 전화하셨습니까?")을 제공한 다음, 해당 답변에 따라 요청한 정보를 제공하거나 응답 그룹 에이전트로 통화를 경로 지정합니다.

현재 Office Communications Server 2007 R2 또는 Lync Server 2010에서 응답 그룹 응용 프로그램을 실행 중인 경우 **Move-CsRgsConfiguration** cmdlet을 사용하면 이 서비스를 Lync Server 2013로 마이그레이션할 수 있습니다. 서비스를 마이그레이션하려면 **Move-CsRgsConfiguration** cmdlet을 호출하고 1) 기존 버전의 응답 그룹 응용 프로그램(원본)에 대한 FQDN(정규화된 도메인 이름) 및 2) 새 Lync Server 2013 버전의 서비스(대상)에 대한 FQDN을 지정해야 합니다. 그러면 **Move-CsRgsConfiguration**에서 모든 구성 설정, 오디오 파일 및 연락처 개체를 기존 버전(Office Communications Server 2007 R2 또는 Lync Server 2010)에서 Lync Server 2013로 이동합니다. 서비스가 마이그레이션된 후에는 응답 그룹 전화 번호로 걸려 오는 모든 전화가 Lync Server 2013에 의해 처리됩니다. 이전 버전의 서비스에서는 더 이상 통화를 처리하지 않습니다.

**Move-CsRgsConfiguration**을 실행하려면 먼저 WMI(Windows Management Instrumentation) Backward Compatibility 인터페이스 패키지를 설치해야 합니다. 설치 DVD의 설치(Setup) 폴더에 있는 OCSWMIBC.msi 파일을 실행하면 이 응용 프로그램이 설치됩니다.

Office Communications Server 2007에서 Microsoft SQL Server 2005를 실행하는 경우에는 응답 그룹 응용 프로그램을 마이그레이션하기 전에 **Move-CsRgsConfiguration** cmdlet을 실행할 컴퓨터에 Microsoft SQL Server 2005 Native Client를 설치해야 합니다. Native Client가 설치되어 있지 않으면 **Move-CsRgsConfiguration**을 호출할 때 "WMI 설정에 액세스할 수 없습니다"라는 오류 메시지가 나타납니다.

**Move-CsRgsConfiguration** cmdlet은 Office Communications Server 2007 R2 또는 Lync Server 2010에서 Lync Server 2013로 마이그레이션하는 데만 사용됩니다. 이 cmdlet을 사용하여 Lync Server 2013의 특정 인스턴스에서 Lync Server 2013의 새 인스턴스로 마이그레이션할 수는 없습니다. 이 유형의 마이그레이션을 수행하는 방법은 새로운 **Import-CsRgsConfiguration** 및 **Export-CsRgsConfiguration** cmdlet을 사용하는 것뿐입니다.

이 cmdlet을 실행할 수 있는 사용자: 기본적으로 RTCUniversalServerAdmins 그룹의 구성원은 **Move-CsRgsConfiguration** cmdlet을 로컬로 실행할 수 있습니다. 사용자가 직접 만든 사용자 지정 RBAC(역할 기반 액세스 제어) 역할을 포함하여 이 cmdlet이 할당된 모든 RBAC 역할의 목록을 반환하려면 Windows PowerShell 프롬프트에서 다음 명령을 실행합니다.

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Move-CsRgsConfiguration"}

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
<td><p><em>Destination</em></p></td>
<td><p>필수</p></td>
<td><p>System.String</p></td>
<td><p>Lync Server 2013 응답 그룹 응용 프로그램을 호스트할 컴퓨터(&quot;복사 대상&quot; 위치)의 FQDN입니다.</p></td>
</tr>
<tr class="even">
<td><p><em>Source</em></p></td>
<td><p>필수</p></td>
<td><p>System.String</p></td>
<td><p>Office Communications Server 2007 R2 또는 Lync Server 2010 응답 그룹 응용 프로그램이 현재 호스트된 풀(&quot;복사 원본&quot; 위치)의 FQDN입니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>Force</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>명령을 실행할 때 발생할 수 있는 심각하지 않은 오류 메시지를 표시하지 않습니다.</p></td>
</tr>
</tbody>
</table>


## 입력 형식

없음. **Move-CsRgsConfiguration**은 파이프라인된 입력을 허용하지 않습니다.

## 반환 형식

**Move-CsRgsConfiguration**은 Microsoft.Rtc.Management.WriteableSettings.ServiceSettings 인스턴스를 서비스 간에 이동합니다.

## 참고 항목

#### 기타 리소스

[Get-CsRgsConfiguration](get-csrgsconfiguration.md)  
[Move-CsRgsConfiguration](move-csrgsconfiguration.md)

