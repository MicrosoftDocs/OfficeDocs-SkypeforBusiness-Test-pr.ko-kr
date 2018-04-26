---
title: Get-CsFIPSConfiguration
TOCTitle: Get-CsFIPSConfiguration
ms:assetid: 56d29011-187f-4034-a5ed-71625087bf36
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/JJ204904(v=OCS.15)
ms:contentKeyID: 49303691
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Get-CsFIPSConfiguration

 

_**마지막으로 수정된 항목:** 2015-03-09_

조직에서 현재 사용되고 있는 FIPS(Federal Information Processing Standards) 구성 설정에 대한 정보를 반환합니다. FIPS 표준은 군 기관이 아닌 정부 기관과 군 수급자가 유지 관리하는 컴퓨터에서 사용해야 하는 미국 정보 보안 표준 집합입니다. 이 cmdlet은 Lync Server 2013에서 도입되었습니다.

## 구문

    Get-CsFIPSConfiguration [-Identity <XdsIdentity>] <COMMON PARAMETERS>

    Get-CsFIPSConfiguration [-Filter <String>] <COMMON PARAMETERS>

    COMMON PARAMETERS: [-LocalStore <SwitchParameter>] [-Tenant <Guid>]

## 예제

## 예제 1

예제 1에 표시된 명령은 조직에서 현재 사용 중인 모든 FIPS 구성 설정에 대한 정보를 반환합니다. FIPS 구성 설정의 인스턴스는 전역 인스턴스 하나뿐입니다.

    Get-CsFIPSConfiguration

## 자세한 정보

FIPS(Federal Information Processing Standards)는 미국 정부 관련 업무용 컴퓨터에서 사용되는 일련의 표준 및 지침입니다. 암호화 및 디지털 서명과 같은 기술 사용을 제어하는 FIPS 표준을 예로 들 수 있습니다. 자세한 내용은 <http://www.itl.nist.gov/fipspubs/by-num.htm>을 참조하십시오. Lync Server 2013에서는 FIPS 표준을 충족하는 알고리즘만 사용할 수 있도록 하는 옵션을 제공합니다. 미국 정부 또는 FIPS를 준수하는 기타 업체 관련 업무를 수행해야 하는 경우에는 Lync Server 2013에서 FIPS 준수를 사용하도록 설정할 수 있습니다.

그러나 온-프레미스 버전 Lync Server의 경우에는 FIPS 구성 설정의 전역 컬렉션을 하나만 사용할 수 있으며 전체 Lync Server 구현에 대해서만 FIPS 준수를 사용하거나 사용하지 않도록 설정할 수 있습니다. 즉, 개별 사이트나 개별 등록자 풀에 대해 FIPS 준수를 선택적으로 사용하거나 사용하지 않도록 설정할 수는 없습니다. FIPS 준수를 사용하도록 설정하는 경우에는 FIPS 표준을 완전하게 따르지 않는 조직과 통신할 때 문제가 발생할 수 있습니다.

기본적으로 Lync Server 2013에서는 FIPS 준수가 사용하지 않도록 설정됩니다.

사용자가 직접 만든 사용자 지정 RBAC(역할 기반 액세스 제어) 역할을 포함하여 이 cmdlet이 할당된 모든 RBAC 역할의 목록을 반환하려면 Windows PowerShell 명령줄 인터페이스 프롬프트에서 다음 명령을 실행합니다.

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Get-CsFIPSConfiguration"}

**Lync Server 제어판:** Get-CsFIPSConfiguration cmdlet에 의해 수행되는 기능은 Lync Server 제어판에서는 사용할 수 없습니다.

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
<td><p><em>Filter</em></p></td>
<td><p>선택</p></td>
<td><p>System.String</p></td>
<td><p>FIPS 구성 설정의 컬렉션을 참조할 때 와일드카드 값을 사용할 수 있습니다. 이러한 설정에 대해서는 전역 인스턴스를 하나만 사용할 수 있으므로 Filter 매개 변수는 사용할 필요가 없습니다. 그러나 원하는 경우 다음 구문을 사용하여 전역 설정을 참조할 수 있습니다.</p>
<p>-Filter &quot;g*&quot;</p>
<p>이 구문은 ID가 &quot;g&quot; 문자로 시작되는 모든 FIPS 구성 설정을 가져옵니다.</p></td>
</tr>
<tr class="even">
<td><p><em>Identity</em></p></td>
<td><p>선택</p></td>
<td><p>Microsoft.Rtc.Management.Xds.XdsIdentity</p></td>
<td><p>FIPS 구성 설정의 고유 ID입니다. 이러한 설정에 대해서는 전역 인스턴스를 하나만 사용할 수 있으므로 <strong>Get-CsFIPSConfiguration</strong> cmdlet을 호출할 때 Identity를 지정할 필요가 없습니다. 그러나 원하는 경우에는 다음 구문을 사용하여 전역 설정을 참조할 수 있습니다.</p>
<p>-Identity global</p></td>
</tr>
<tr class="odd">
<td><p><em>LocalStore</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>중앙 관리 저장소 자체가 아니라 중앙 관리 저장소의 로컬 복제본에서 FIPS 구성 데이터를 검색합니다.</p></td>
</tr>
<tr class="even">
<td><p><em>Tenant</em></p></td>
<td><p>선택</p></td>
<td><p>System.Guid</p></td>
<td><p>해당 FIPS 구성 설정을 검색할 비즈니스용 Skype Online 테넌트 계정의 GUID(Globally Unique Identifier)입니다.</p>
<p>예를 들면 다음과 같습니다.</p>
<p>–Tenant &quot;38aad667-af54-4397-aaa7-e94c79ec2308&quot;</p>
<p>다음 명령을 실행하여 각 테넌트에 대해 테넌트 ID를 반환할 수 있습니다.</p>
<p>Get-CsTenant | Select-Object DisplayName, TenantID</p></td>
</tr>
</tbody>
</table>


## 입력 형식

없음. **Get-CsFIPSConfiguration** cmdlet은 파이프라인된 입력을 허용하지 않습니다.

## 반환 형식

**Get-CsFIPSConfiguration** cmdlet은 Microsoft.Rtc.Management.WritableConfig.Settings.FIPSConfiguration.FIPSConfiguration 개체의 인스턴스를 반환합니다.

## 참고 항목

#### 기타 리소스

[New-CsFIPSConfiguration](new-csfipsconfiguration.md)  
[Remove-CsFIPSConfiguration](remove-csfipsconfiguration.md)  
[Set-CsFIPSConfiguration](set-csfipsconfiguration.md)

