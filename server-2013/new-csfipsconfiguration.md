---
title: New-CsFIPSConfiguration
TOCTitle: New-CsFIPSConfiguration
ms:assetid: 9ce030fb-fb6b-47a2-9fb9-69e8369b43be
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/JJ205114(v=OCS.15)
ms:contentKeyID: 49304527
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# New-CsFIPSConfiguration

 

_**마지막으로 수정된 항목:** 2014-10-29_

FIPS(Federal Information Processing Standards) 구성 설정의 새 컬렉션을 만듭니다. FIPS 표준은 군 기관이 아닌 정부 기관과 군 수급자가 유지 관리하는 컴퓨터에서 사용해야 하는 미국 정부 보안 표준 집합입니다. 이 cmdlet은 Lync Server 2013에서 도입되었습니다.

## 구문

    New-CsFIPSConfiguration -Identity <XdsIdentity> [-Confirm [<SwitchParameter>]] [-Force <SwitchParameter>] [-InMemory <SwitchParameter>] [-RequireFIPSCompliantMedia <$true | $false>] [-Tenant <Guid>] [-WhatIf [<SwitchParameter>]]

## 예제

## 예제 1

예제 1에 표시된 명령은 메모리 내에만 있는 FIPS 구성 설정 집합을 새로 만든 다음 나중에 이러한 설정을 사용하여 FIPS 구성 설정의 전역 컬렉션을 업데이트합니다. 이 작업을 수행하기 위해 예제의 첫 번째 명령은 **New-CsFIPSConfiguration** cmdlet 및 InMemory 매개 변수를 사용하여 ID가 "global"인 FIPS 구성 설정의 새 컬렉션을 만듭니다. 이렇게 만들어진 설정 개체는 $x 변수에 저장됩니다.

두 번째 명령에서는 **Set-CsFIPSConfiguration** cmdlet 및 Instance 매개 변수를 사용하여 FIPS 설정의 기존 전역 컬렉션을 $x에 저장된 새 컬렉션으로 바꿉니다.

이 예제가 작동하기는 하지만 **Set-CsFIPSConfiguration** cmdlet을 사용하여 FIPS 구성 설정을 수정하는 것이 더 쉽습니다.

    $x = New-CsFIPSConfiguration -Identity "global" -RequireFIPSCompliantMedia $False -InMemory
    
    Set-CsFIPSConfiguration -Instance $x

## 자세한 정보

FIPS(Federal Information Processing Standards)는 미국 정부 관련 업무용 컴퓨터에서 사용되는 일련의 표준 및 지침입니다. 암호화 및 디지털 서명과 같은 기술 사용을 제어하는 FIPS 표준을 예로 들 수 있습니다. 자세한 내용은 <http://www.itl.nist.gov/fipspubs/by-num.htm>을 참조하십시오. Lync Server 2013에서는 FIPS 표준을 충족하는 알고리즘만 사용할 수 있도록 하는 옵션을 제공합니다. 미국 정부 또는 FIPS를 준수하는 기타 업체 관련 업무를 수행해야 하는 경우에는 Lync Server 2013에서 FIPS 준수를 사용하도록 설정할 수 있습니다.

그러나 온-프레미스 버전 Lync Server의 경우에는 FIPS 구성 설정의 전역 컬렉션을 하나만 사용할 수 있으며 전체 Lync Server 구현에 대해서만 FIPS 준수를 사용하거나 사용하지 않도록 설정할 수 있습니다. 즉, 개별 사이트나 개별 등록자 풀에 대해 FIPS 준수를 선택적으로 사용하거나 사용하지 않도록 설정할 수는 없습니다. FIPS 준수를 사용하도록 설정하는 경우에는 FIPS 표준을 완전하게 따르지 않는 조직과 통신할 때 문제가 발생할 수 있습니다. 즉, **New-CsFIPSConfiguration** cmdlet은 기본적으로 비즈니스용 Skype Online에 대한 FIPS 준수를 관리하는 데 사용됩니다.

기본적으로 Lync Server 2013에서는 FIPS 준수가 사용하지 않도록 설정됩니다.

사용자가 직접 만든 사용자 지정 RBAC(역할 기반 액세스 제어) 역할을 포함하여 이 cmdlet이 할당된 모든 RBAC 역할의 목록을 반환하려면 Windows PowerShell 명령줄 인터페이스 프롬프트에서 다음 명령을 실행합니다.

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "New-CsFIPSConfiguration"}

**Lync Server 제어판:** New-CsFIPSConfiguration cmdlet에 의해 수행되는 기능은 Lync Server 제어판에서는 사용할 수 없습니다.

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
<td><p>새 FIPS 구성 설정 컬렉션의 고유 식별자입니다. Lync Server 2013에서는 FIPS 설정의 전역 컬렉션을 하나만 지원하므로 이 매개 변수를 사용하려면 메모리에만 있는 &quot;새&quot; 전역 컬렉션을 만들어야 합니다. 이렇게 하려면 InMemory도 사용해야 합니다.</p></td>
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
<td><p><em>InMemory</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>개체를 실제로 영구 변경 내용으로 커밋하지 않고 개체 참조를 만듭니다. 이 매개 변수를 사용하여 호출된 이 cmdlet의 출력을 변수에 할당하면 개체 참조의 속성을 변경한 후 이 cmdlet과 일치하는 Set- cmdlet을 호출하여 해당 변경 내용을 커밋할 수 있습니다.</p></td>
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
<td><p>새 FIPS 구성 설정이 만들어지는 비즈니스용 Skype Online 테넌트 계정의 GUID(Globally unique identifier)입니다. 예를 들면 다음과 같습니다.</p>
<p>–Tenant &quot;38aad667-af54-4397-aaa7-e94c79ec2308&quot;</p>
<p>다음 명령을 실행하여 각 테넌트에 대한 테넌트 ID를 반환할 수 있습니다.</p>
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

없음. **New-CsFIPSConfiguration** cmdlet은 파이프라인된 입력을 허용하지 않습니다.

## 반환 형식

**New-CsFIPSConfiguration** cmdlet은 Microsoft.Rtc.Management.WritableConfig.Settings.FIPSConfiguration.FIPSConfiguration 개체의 새 인스턴스를 만듭니다.

## 참고 항목

#### 기타 리소스

[Get-CsFIPSConfiguration](get-csfipsconfiguration.md)  
[Remove-CsFIPSConfiguration](remove-csfipsconfiguration.md)  
[Set-CsFIPSConfiguration](set-csfipsconfiguration.md)

