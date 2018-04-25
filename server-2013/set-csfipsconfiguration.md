---
title: Set-CsFIPSConfiguration
TOCTitle: Set-CsFIPSConfiguration
ms:assetid: 920f58ce-e175-41ac-b681-5ac873091593
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/JJ205084(v=OCS.15)
ms:contentKeyID: 49304394
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Set-CsFIPSConfiguration

 

_**마지막으로 수정된 항목:** 2015-03-09_

FIPS(Federal Information Processing Standards) 구성 설정의 기존 컬렉션을 수정합니다. FIPS 표준은 군 기관이 아닌 정부 기관과 군 수급자가 유지 관리하는 컴퓨터에서 사용해야 하는 미국 정보 보안 표준 집합입니다. 이 cmdlet은 Lync Server 2013에서 도입되었습니다.

## 구문

    Set-CsFIPSConfiguration [-Identity <XdsIdentity>] <COMMON PARAMETERS>

    Set-CsFIPSConfiguration [-Instance <PSObject>] <COMMON PARAMETERS>

    COMMON PARAMETERS: [-Confirm [<SwitchParameter>]] [-Force <SwitchParameter>] [-RequireFIPSCompliantMedia <$true | $false>] [-Tenant <Guid>] [-WhatIf [<SwitchParameter>]]

## 예제

## 예제 1

예제 1에서는 전역 FIPS 구성 설정의 RequireFIPSCompliantMedia 속성을 True($True)로 설정합니다.

    Set-CsFIPSConfiguration -Identity "global" -RequireFIPSCompliantMedia $True

## 자세한 정보

FIPS(Federal Information Processing Standards)는 미국 정부 관련 업무용 컴퓨터에서 사용되는 일련의 표준 및 지침입니다. 암호화 및 디지털 서명과 같은 기술 사용을 제어하는 FIPS 표준을 예로 들 수 있습니다. 자세한 내용은 <http://www.itl.nist.gov/fipspubs/by-num.htm>을 참조하십시오. Lync Server 2013에서는 FIPS 표준을 충족하는 알고리즘만 사용할 수 있도록 하는 옵션을 제공합니다. 미국 정부 또는 FIPS를 준수하는 기타 업체 관련 업무를 수행해야 하는 경우에는 Lync Server 2013에서 FIPS 준수를 사용하도록 설정할 수 있습니다.

그러나 온-프레미스 버전 Lync Server의 경우에는 FIPS 구성 설정의 전역 컬렉션을 하나만 사용할 수 있으며 전체 Lync Server 구현에 대해서만 FIPS 준수를 사용하거나 사용하지 않도록 설정할 수 있습니다. 즉, 개별 사이트나 개별 등록자 풀에 대해 FIPS 준수를 선택적으로 사용하거나 사용하지 않도록 설정할 수는 없습니다. FIPS 준수를 사용하도록 설정하는 경우에는 FIPS 표준을 완전하게 따르지 않는 조직과 통신할 때 문제가 발생할 수 있습니다.

기본적으로 Lync Server 2013에서는 FIPS 준수가 사용하지 않도록 설정됩니다.

**Set-CsFIPSConfiguration** cmdlet을 사용하여 FIPS 준수를 사용하거나 사용하지 않도록 설정합니다.

사용자가 직접 만든 사용자 지정 RBAC(역할 기반 액세스 제어) 역할을 포함하여 이 cmdlet이 할당된 모든 RBAC 역할의 목록을 반환하려면 Windows PowerShell 명령줄 인터페이스 프롬프트에서 다음 명령을 실행합니다.

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Set-CsFIPSConfiguration"}

**Lync Server 제어판:** **Set-CsFIPSConfiguration** cmdlet에 의해 수행되는 기능은 Lync Server 제어판에서는 사용할 수 없습니다.

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
<td><p><em>Identity</em></p></td>
<td><p>선택</p></td>
<td><p>Microsoft.Rtc.Management.Xds.XdsIdentity</p></td>
<td><p>수정할 FIPS 구성 설정의 고유 ID입니다. Lync Server 2013에서는 FIPS 설정의 전역 컬렉션을 하나만 지원하므로 수정할 수 있는 컬렉션은 전역 컬렉션뿐입니다.</p>
<p>-Identity global</p>
<p>이 매개 변수를 포함하지 않으면 <strong>Set-CsFIPSConfiguration</strong> cmdlet은 전역 컬렉션을 수정합니다.</p></td>
</tr>
<tr class="even">
<td><p><em>Instance</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.PSObject</p></td>
<td><p>개별 매개 변수 값을 설정하는 대신 cmdlet에 개체에 대한 참조를 전달할 수 있습니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>RequireFIPSCompliantMedia</em></p></td>
<td><p>선택</p></td>
<td><p>System.Boolean</p></td>
<td><p>True로 설정하면 Lync Server 2013에서는 인증 및 권한 부여에 FIPS 호환 알고리즘을 사용하는 엔터티와의 미디어 세션만 허용합니다.</p>
<p>FIPS를 준수해야 하는 경우 사용자들이 더 이상 Microsoft Lync Server 2010 A/V 에지 서버를 사용하여 시스템에 연결할 수 없으며, 모든 에지 서버를 Lync 2013로 업그레이드해야 합니다.</p>
<p>기본값은 False입니다.</p></td>
</tr>
<tr class="even">
<td><p><em>Tenant</em></p></td>
<td><p>선택</p></td>
<td><p>System.Guid</p></td>
<td><p>FIPS 구성 설정을 수정할 비즈니스용 Skype Online 테넌트 계정의 GUID(Globally Unique Identifier)입니다. 예를 들면 다음과 같습니다.</p>
<p>–Tenant &quot;38aad667-af54-4397-aaa7-e94c79ec2308&quot;</p>
<p>다음 명령을 실행하여 각 테넌트에 대해 테넌트 ID를 반환할 수 있습니다.</p>
<p>Get-CsTenant | Select-Object DisplayName, TenantID</p></td>
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

**Set-CsFIPSConfiguration** cmdlet은 Microsoft.Rtc.Management.WritableConfig.Settings.FIPSConfiguration.FIPSConfiguration 개체의 파이프라인된 인스턴스를 허용합니다.

## 반환 형식

없음. 대신 **Set-CsFIPSConfiguration** cmdlet은 Microsoft.Rtc.Management.WritableConfig.Settings.FIPSConfiguration.FIPSConfiguration 개체의 기존 인스턴스를 수정합니다.

## 참고 항목

#### 기타 리소스

[Get-CsFIPSConfiguration](get-csfipsconfiguration.md)  
[New-CsFIPSConfiguration](new-csfipsconfiguration.md)  
[Remove-CsFIPSConfiguration](remove-csfipsconfiguration.md)

