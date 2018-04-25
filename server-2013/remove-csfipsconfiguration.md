---
title: Remove-CsFIPSConfiguration
TOCTitle: Remove-CsFIPSConfiguration
ms:assetid: b7e43419-0154-4fed-bfc6-9053335ce5d8
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/JJ205201(v=OCS.15)
ms:contentKeyID: 49304819
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Remove-CsFIPSConfiguration

 

_**마지막으로 수정된 항목:** 2015-03-09_

하나 이상의 FIPS(Federal Information Processing Standards) 구성 설정 컬렉션을 제거합니다. FIPS 표준은 군 기관이 아닌 정부 기관과 군 수급자가 유지 관리하는 컴퓨터에서 사용해야 하는 미국 정보 보안 표준 집합입니다. 이 cmdlet은 Lync Server 2013에서 도입되었습니다.

## 구문

    Remove-CsFIPSConfiguration -Identity <XdsIdentity> [-Confirm [<SwitchParameter>]] [-Force <SwitchParameter>] [-Tenant <Guid>] [-WhatIf [<SwitchParameter>]]

## 예제

## 예제 1

예제 1에서는 FIPS 구성 설정의 전역 컬렉션에 포함된 속성을 기본값으로 다시 설정합니다.

    Remove-CsFIPSConfiguration -Identity "Global"

## 자세한 정보

FIPS(Federal Information Processing Standards)는 미국 정부 관련 업무용 컴퓨터에서 사용되는 일련의 표준 및 지침입니다. 암호화 및 디지털 서명과 같은 기술 사용을 제어하는 FIPS 표준을 예로 들 수 있습니다. 자세한 내용은 <http://www.itl.nist.gov/fipspubs/by-num.htm>을 참조하십시오. Lync Server 2013에서는 FIPS 표준을 충족하는 알고리즘만 사용할 수 있도록 하는 옵션을 제공합니다. 미국 정부 또는 FIPS를 준수하는 기타 업체 관련 업무를 수행해야 하는 경우에는 Lync Server 2013에서 FIPS 준수를 사용하도록 설정할 수 있습니다.

그러나 온-프레미스 버전 Lync Server의 경우에는 FIPS 구성 설정의 전역 컬렉션을 하나만 사용할 수 있으며 전체 Lync Server 구현에 대해서만 FIPS 준수를 사용하거나 사용하지 않도록 설정할 수 있습니다. 즉, 개별 사이트나 개별 등록자 풀에 대해 FIPS 준수를 선택적으로 사용하거나 사용하지 않도록 설정할 수는 없습니다. FIPS 준수를 사용하도록 설정하는 경우에는 FIPS 표준을 완전하게 따르지 않는 조직과 통신할 때 문제가 발생할 수 있습니다.

기본적으로 Lync Server 2013에서는 FIPS 준수가 사용하지 않도록 설정됩니다.

사용자가 직접 만든 사용자 지정 RBAC(역할 기반 액세스 제어) 역할을 포함하여 이 cmdlet이 할당된 모든 RBAC 역할의 목록을 반환하려면 Windows PowerShell 명령줄 인터페이스 프롬프트에서 다음 명령을 실행합니다.

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Remove-CsFIPSConfiguration

**Lync Server 제어판:** Remove-CsFIPSConfiguration cmdlet에 의해 수행되는 기능은 Lync Server 제어판에서는 사용할 수 없습니다.

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
<td><p>Microsoft.Rtc.Management.Xds.XdsIdentity</p></td>
<td><p>제거할 FIPS 구성 설정의 고유 ID입니다. Lync Server 2013에서는 FIPS 설정의 전역 컬렉션을 하나만 지원하므로 삭제할 수 있는 컬렉션은 전역 컬렉션뿐입니다.</p>
<p>-Identity global</p>
<p>이 경우 전역 컬렉션이 시스템에서 실제로 제거되는 것은 아닙니다. Lync Server 2013에서는 전역 설정의 삭제를 지원하지 않습니다. 대신 해당 컬렉션의 lone 속성인 RequireFIPSCompliantMedia가 기본값인 False로 다시 설정됩니다.</p></td>
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
<td><p><em>Tenant</em></p></td>
<td><p>선택</p></td>
<td><p>System.Guid</p></td>
<td><p>삭제할 FIPS 구성 설정에 대한 비즈니스용 Skype Online 테넌트 계정의 GUID(Globally Unique Identifier)입니다. 예를 들면 다음과 같습니다.</p>
<p>–Tenant &quot;38aad667-af54-4397-aaa7-e94c79ec2308&quot;</p>
<p>다음 명령을 실행하여 각 테넌트에 대해 테넌트 ID를 반환할 수 있습니다.</p>
<p>Get-CsTenant | Select-Object DisplayName, TenantID</p></td>
</tr>
<tr class="odd">
<td><p><em>WhatIf</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>실제로 명령을 수행하지는 않고 명령을 실행했을 때 발생할 결과에 대해 설명합니다.</p></td>
</tr>
</tbody>
</table>


## 입력 형식

**Remove-CsFIPSConfiguration** cmdlet은 Microsoft.Rtc.Management.WritableConfig.Settings.FIPSConfiguration.FIPSConfiguration 개체의 파이프라인된 인스턴스를 허용합니다.

## 반환 형식

없음. 대신 **Remove-CsFIPSConfiguration** cmdlet은 Microsoft.Rtc.Management.WritableConfig.Settings.FIPSConfiguration.FIPSConfiguration 개체의 기존 인스턴스를 삭제합니다.

## 참고 항목

#### 기타 리소스

[Get-CsFIPSConfiguration](get-csfipsconfiguration.md)  
[New-CsFIPSConfiguration](new-csfipsconfiguration.md)  
[Set-CsFIPSConfiguration](set-csfipsconfiguration.md)

