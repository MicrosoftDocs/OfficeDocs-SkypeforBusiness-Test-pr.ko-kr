---
title: Get-CsTenantPublicProvider
TOCTitle: Get-CsTenantPublicProvider
ms:assetid: 0d949ec2-206d-4979-a3be-a5578ae93ed3
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/JJ994016(v=OCS.15)
ms:contentKeyID: 52056785
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Get-CsTenantPublicProvider

 

_**마지막으로 수정된 항목:** 2015-03-09_

Microsoft Lync Online 사용자가 타사 메신저 및 현재 상태 공급자 Windows Live, AOL, Yahoo에 계정이 있는 다른 사용자와 통신할 수 있는지 여부를 나타내는 정보를 반환합니다.

이 cmdlet은 비즈니스용 Skype Online에서만 사용할 수 있습니다.

## 구문

    Get-CsTenantPublicProvider -Tenant <String> [-Verbose]

## 예제

## 예제 1

예제 1에 표시된 명령은 테넌트 ID가 "bf19b7db-6960-41e5-a139-2aa373474354"인 테넌트의 공용 공급자 정보를 반환합니다.

    Get-CsTenantPublicProvider -Tenant "bf19b7db-6960-41e5-a139-2aa373474354"

Tenant 매개 변수는 선택 사항입니다. 다음 구문을 사용하여 Get-CsTenantPublicProvider를 호출할 수도 있습니다.

    Get-CsTenantPublicProvider

## 예제 2

위 명령은 bf19b7db-6960-41e5-a139-2aa373474354 테넌트에 할당된 모든 공용 공급자의 상태에 대한 자세한 정보를 반환합니다. 이를 수행하기 위해 이 명령은 먼저 **Get-CsTenantPublicProvider** cmdlet을 사용하여 지정된 테넌트에 대한 공용 공급자 정보를 반환합니다. 해당 정보는 **Select-Object** cmdlet에 파이프되며, 이 cmdlet은 ExpandProperty 매개 변수를 사용하여 DomainPICStatus 속성의 값을 "확장"합니다. 속성을 확장한다는 것은 간단히 말해 해당 속성 화면에 저장된 모든 값을 읽기 쉬운 형식으로 표시하는 것을 의미합니다.

    Get-CsTenantPublicProvider -Tenant "bf19b7db-6960-41e5-a139-2aa373474354" | Select-Object -ExpandProperty DomainPICStatus

이와 같은 명령은 Lync Server 2013의 하이브리드 배포에 사용됩니다.

## 예제 3

예제 3의 명령은 예제 2에 나와 있는 명령의 변형입니다. 그러나 예제 3에서는 DomainPICStatus 속성 값을 "확장"하여 반환된 공용 공급자 정보가 **Where-Object** cmdlet에 파이프됩니다. 그러면 **Where-Object** cmdlet을 통해 Status 속성이 Enabled로 설정된 공급자만 선택됩니다. 따라서 사용하도록 설정된 공용 공급자만 표시됩니다.

    Get-CsTenantPublicProvider -Tenant "bf19b7db-6960-41e5-a139-2aa373474354" | Select-Object -ExpandProperty DomainPICStatus | Where-Object {$_.Status -eq "Enabled"}

## 자세한 정보

공용 공급자는 일반 대중에게 SIP 통신 서비스를 제공하는 조직입니다. 공용 공급자와의 페더레이션 관계를 설정하면 해당 공급자가 호스트하는 계정을 가진 사용자와의 페더레이션을 효과적으로 설정할 수 있습니다. 예를 들어 Windows Live와 페더레이션할 경우 사용자가 Windows Live 메신저 계정을 가진 다른 사용자와 메신저 및 현재 상태 정보를 교환할 수 있습니다.

Lync Online에서는 관리자가 다음 중 하나 이상의 공용 메신저 및 현재 상태 공급자와의 페더레이션을 구성할 수 있습니다.

  - Windows Live

  - AOL

  - Yahoo\!

관리자는 **Get-CsTenantPublicProvider** cmdlet을 사용하여 페더레이션에 사용하도록 설정된 공급자(있는 경우)를 확인할 수 있습니다. **Get-CsTenantPublicProvider** cmdlet을 호출하면 다음과 유사한 정보가 반환됩니다.

    PublicProviderSet     DomainPicStatus
    ------------------    ------------------------
    True                  {Microsoft.Rtc.Management.Hosted.DomainPICStatus}

PublicProviderSet 속성은 하나 이상의 공급자에 대해 페더레이션을 사용하도록 설정되었는지 여부를 나타냅니다. PublicProviderSet가 True이면 하나 이상의 공급자에 대해 페더레이션을 사용하도록 설정된 것이고 PublicProviderSet가 False이면 세 가지 공용 공급자(Windows Live, AOL, Yahoo) 모두에 대해 페더레이션을 사용하지 않도록 설정된 것입니다. 각 공급자의 실제 상태를 확인하려면 다음 명령을 사용합니다.

    Get-CsTenantPublicProvider -Tenant "bf19b7db-6960-41e5-a139-2aa373474354" | Select-Object -ExpandProperty DomainPICStatus

단순히 공용 공급자 상태를 사용하도록 설정한다고 해서 사용자가 해당 공급자의 계정이 있는 사용자와 메신저 및 현재 상태 정보를 교환할 수 있는 것은 아닙니다. 해당 공급자와 페더레이션을 사용하도록 설정하는 것 외에도 관리자가 페더레이션 구성 설정의 AllowPublicUsers 속성을 True로 설정해야 합니다. 이 속성이 False로 설정될 경우에는 공용 공급자 구성 설정과 상관없이 모든 공용 공급자와의 통신이 허용되지 않습니다.

자세한 내용은 **Set-CsTenantFederationConfiguration** cmdlet 관련 도움말 항목을 참고하세요.

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
<td><p><em>Tenant</em></p></td>
<td><p>필수</p></td>
<td><p>System.String</p></td>
<td><p>공용 공급자 설정을 반환하는 테넌트 계정의 GUID(Globally Unique Identifier)입니다. 예를 들면 다음과 같습니다.</p>
<p>–Tenant &quot;38aad667-af54-4397-aaa7-e94c79ec2308&quot;</p>
<p>다음 명령을 실행하여 각 테넌트에 대해 테넌트 ID를 반환할 수 있습니다.</p>
<p>Get-CsTenant | Select-Object DisplayName, TenantID</p>
<p>Windows PowerShell 원격 세션을 사용 중이며 비즈니스용 Skype Online에만 연결되어 있는 경우에는 Tenant 매개 변수를 포함하지 않아도 됩니다. 대신, 연결 정보를 기반으로 테넌트 ID가 자동으로 채워집니다. Tenant 매개 변수는 하이브리드 배포에서 주로 사용됩니다.</p></td>
</tr>
</tbody>
</table>


## 입력 형식

없음. **Get-CsTenantPublicProvider** cmdlet은 파이프라인된 입력을 허용하지 않습니다.

## 반환 형식

**Get-CsTenantPublicProvider** cmdlet은 Microsoft.Rtc.Management.Hosted.TenantPICStatus 개체의 인스턴스를 반환합니다.

## 참고 항목

#### 기타 리소스

[Set-CsTenantPublicProvider](set-cstenantpublicprovider.md)

