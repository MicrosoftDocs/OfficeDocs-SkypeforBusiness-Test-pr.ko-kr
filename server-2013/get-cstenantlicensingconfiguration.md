---
title: Get-CsTenantLicensingConfiguration
TOCTitle: Get-CsTenantLicensingConfiguration
ms:assetid: 0df23143-f1aa-4850-b0f7-750422762925
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Dn362770(v=OCS.15)
ms:contentKeyID: 56270214
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Get-CsTenantLicensingConfiguration

 

_**마지막으로 수정된 항목:** 2015-03-09_

Lync 관리 센터에서 특정 테넌트에 대한 라이선스 정보를 사용할 수 있는지 여부를 나타냅니다.

이 cmdlet은 Lync Online에서만 사용할 수 있습니다.

## 구문

    Get-CsTenantLicensingConfiguration [-Filter] <Object>] [-Identity] <Object>] [-Tenant] <Object>] [-LocalStore]

## 자세한 정보

Get-CsTenantLicensingConfiguration cmdlet은 Lync 관리 센터에서 특정 테넌트에 대한 라이선스 정보를 사용할 수 있는지 여부를 나타냅니다. 이 cmdlet은 다음과 비슷한 정보를 반환합니다.

Identity : Global  
Status : Enabled

Status가 Enabled인 경우 Lync 관리 센터에서 라이선스 정보를 사용할 수 있습니다. 그렇지 않은 경우에는 Lync 관리 센터에서 라이선스 정보를 사용할 수 없습니다.

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
<th>형식</th>
<th>설명</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><strong>Filter</strong></p></td>
<td><p>선택</p></td>
<td><p>System.String</p></td>
<td><p>테넌트 라이선스 구성 설정 컬렉션을 반환하기 위해 와일드카드 문자를 사용할 수 있습니다. 각 테넌트는 하나의 라이선스 구성 설정 전역 컬렉션으로 제한되므로 Filter 매개 변수를 사용하지 않아도 됩니다.</p></td>
</tr>
<tr class="even">
<td><p><strong>Identity</strong></p></td>
<td><p>선택</p></td>
<td><p>Microsoft.Rtc.Management.Xds.XdsIdentity</p></td>
<td><p>반환할 테넌트 라이선스 구성 설정 컬렉션을 지정합니다. 각 테넌트는 하나의 라이선스 설정 전역 컬렉션으로 제한되므로 Get-CsTenantLicensingConfiguration cmdlet을 호출할 때는 이 매개 변수를 포함하지 않아도 됩니다.</p></td>
</tr>
<tr class="odd">
<td><p><strong>LocalStore</strong></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>중앙 관리 저장소 자체가 아니라 중앙 관리 저장소의 로컬 복제본에서 테넌트 라이선스 구성 데이터를 검색합니다.</p></td>
</tr>
<tr class="even">
<td><p><strong>Tenant</strong></p></td>
<td><p>선택</p></td>
<td><p>System.Guid</p></td>
<td><p>라이선스 설정을 반환할 테넌트 계정의 GUID(Globally Unique Identifier)입니다. 예를 들면 다음과 같습니다.</p>
<p>-Tenant &quot;38aad667-af54-4397-aaa7-e94c79ec2308&quot;</p>
<p>다음 명령을 실행하여 각 테넌트에 대한 테넌트 ID를 반환할 수 있습니다.</p>
<p>Get-CsTenant | Select-Object DisplayName, TenantID</p></td>
</tr>
</tbody>
</table>


## 입력 형식

Get-CsTenantLicensingConfiguration cmdlet은 파이프라인된 입력을 허용하지 않습니다.

## 반환 형식

Get-CsTenantLicensingConfiguration cmdlet은 Deserialized.Microsoft.Rtc.Management.WritableConfig.Settings.TenantConfiguration.TenantLicensingConfiguration 개체의 인스턴스를 반환합니다.

## 예제

예제 1에 표시된 명령은 현재 테넌트에 대한 라이선스 구성 정보를 반환합니다.

    Get-CsTenantLicensingConfiguration

