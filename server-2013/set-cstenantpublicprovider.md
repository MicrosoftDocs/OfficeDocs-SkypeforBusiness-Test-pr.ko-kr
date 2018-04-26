---
title: Set-CsTenantPublicProvider
TOCTitle: Set-CsTenantPublicProvider
ms:assetid: 8341d801-bfa1-4c5b-9b80-5d503deebaf7
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/JJ994047(v=OCS.15)
ms:contentKeyID: 52056882
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Set-CsTenantPublicProvider

 

_**마지막으로 수정된 항목:** 2015-03-09_

타사 메신저 및 현재 상태 공급자(예: Windows Live, AOL, Yahoo)와의 통신을 사용하도록/사용하지 않도록 설정합니다. 사용하도록 설정할 경우 Microsoft Lync Online 사용자가 지정된 공용 공급자의 계정이 있는 사용자와 메신저 및 현재 상태 정보를 교환할 수 있습니다.

**Set-CsTenantPublicProvider** cmdlet은 비즈니스용 Skype Online에서만 사용할 수 있습니다.

## 구문

    Set-CsTenantPublicProvider -Tenant <String> [-Provider <String[]>] [-Verbose] [-WhatIf] [-Confirm]

## 예제

## 예제 1

예제 1에 표시된 명령은 테넌트 ID가 bf19b7db-6960-41e5-a139-2aa373474354인 테넌트에 대해 Windows Live와 페더레이션을 사용하도록 설정합니다. Windows Live가 지정된 유일한 공급자이므로 명령이 실행된 후에는 AOL 및 Yahoo 공급자가 모두 사용하지 않도록 설정됩니다.

    Set-CsTenantPublicProvider -Tenant "bf19b7db-6960-41e5-a139-2aa373474354" -Provider "WindowsLive"

## 예제 2

예제 2에서는 두 개의 공용 공급자(Windows Live 및 AOL)를 사용하도록 설정합니다. 즉, 지정된 테넌트에 대해 Yahoo 공용 공급자만 사용하지 않도록 설정합니다.

    Set-CsTenantPublicProvider -Tenant "bf19b7db-6960-41e5-a139-2aa373474354" -Provider "WindowsLive","AOL"

## 예제 3

예제 3에서는 지정된 테넌트에 대해 모든 공용 공급자를 사용하지 않도록 설정하는 방법을 보여줍니다. 이 명령은 Provider 속성을 빈 문자열("")로 설정하여 수행됩니다.

    Set-CsTenantPublicProvider -Tenant "bf19b7db-6960-41e5-a139-2aa373474354" -Provider ""

## 예제 4

예제 4에 표시된 명령은 모든 Lync Online 테넌트에 대해 모든 공용 공급자를 사용하지 않도록 설정합니다. 이 작업을 수행하기 위해 명령은 먼저 **Get-CsTenant** cmdlet을 사용하여 모든 테넌트 컬렉션을 반환합니다. 그런 다음 이 컬렉션은 **ForEach-Object** cmdlet에 파이프됩니다. 이 cmdlet은 컬렉션의 각 테넌트를 가져온 다음 각각의 해당 테넌트에 대해 **Set-CsTenantPublicProvider** cmdlet을 호출하여 공용 공급자를 사용하지 않도록 설정합니다. 마지막 작업은 Provider 속성을 빈 문자열("")로 설정하여 수행됩니다.

    Get-CsTenant | ForEach-Object {Set-CsTenantPublicProvider -Tenant $_.TenantId -Provider ""}

## 자세한 정보

공용 공급자는 일반 대중에게 SIP 통신 서비스를 제공하는 조직입니다. 공용 공급자와의 페더레이션 관계를 설정하면 해당 공급자가 호스트하는 계정을 가진 사용자와의 페더레이션을 효과적으로 설정할 수 있습니다. 예를 들어 Windows Live와 페더레이션할 경우 사용자가 Windows Live 메신저 계정을 가진 다른 사용자와 메신저 및 현재 상태 정보를 교환할 수 있습니다.

Lync Online에서는 관리자가 다음 중 하나 이상의 공용 메신저 및 현재 상태 공급자와의 페더레이션을 구성할 수 있습니다.

  -   
    Windows Live

  -   
    AOL

  -   
    Yahoo\!

**Set-CsTenantPublicProvider** cmdlet을 사용하면 이러한 공용 공급자와의 페더레이션을 설정하거나 해제할 수 있습니다. 이 cmdlet을 사용하는 경우 **Set-CsTenantPublicProvider** cmdlet을 실행할 때마다 사용하도록 설정해야 하는 모든 공급자를 지정해야 합니다. 예를 들어 세 공급자를 모두 사용하지 않도록 설정할 경우에는 다음 명령을 실행합니다.

    Set-CsTenantPublicProvider -Tenant "bf19b7db-6960-41e5-a139-2aa373474354" -Provider "WindowsLive"

예상대로 Windows Live는 사용하도록 설정되고 AOL 및 Yahoo는 계속 사용하지 않도록 설정됩니다.

이제 다음 명령을 이후에 실행한다고 가정해 보겠습니다.

    Set-CsTenantPublicProvider -Tenant "bf19b7db-6960-41e5-a139-2aa373474354" -Provider "AOL"

이 명령은 AOL을 사용하도록 설정합니다. 하지만 Windows Live는 사용하지 않도록 설정합니다. Windows Live가 Provider 매개 변수에 제공된 매개 변수 값의 일부로 지정되지 않았기 때문입니다. AOL을 사용하도록 설정하고 Windows Live도 계속 사용하도록 설정하려면 Set-CsTenantPublicProvider를 호출할 때 AOL과 Windows Live를 모두 지정해야 합니다.

    Set-CsTenantPublicProvider -Tenant "bf19b7db-6960-41e5-a139-2aa373474354" -Provider "AOL","WindowsLive"

세 공급자 모두에 대해 페더레이션을 사용하지 않도록 설정하려면 Provider 속성을 빈 문자열("")로 설정합니다.

    Set-CsTenantPublicProvider -Tenant "bf19b7db-6960-41e5-a139-2aa373474354" -Provider ""

단순히 공용 공급자 상태를 사용하도록 설정한다고 해서 사용자가 해당 공급자의 계정이 있는 사용자와 메신저 및 현재 상태 정보를 교환할 수 있는 것은 아닙니다. 해당 공급자와 페더레이션을 사용하도록 설정하는 것 외에도 관리자가 페더레이션 구성 설정의 AllowPublicUsers 속성을 True로 설정해야 합니다. 이 속성이 False로 설정될 경우에는 공용 공급자 구성 설정과 상관없이 모든 공용 공급자와의 통신이 허용되지 않습니다.

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
<td><p>System.Guid</p></td>
<td><p>공용 공급자 설정이 수정되는 테넌트 계정의 GUID(Globally Unique Identifier)입니다. 예를 들면 다음과 같습니다.</p>
<p>–Tenant &quot;38aad667-af54-4397-aaa7-e94c79ec2308&quot;</p>
<p>다음 명령을 실행하여 각 테넌트에 대해 테넌트 ID를 반환할 수 있습니다.</p>
<pre><code>Get-CsTenant | Select-Object DisplayName, TenantID</code></pre>
<p>Get-CsTenant | Select-Object DisplayName, TenantID</p></td>
</tr>
<tr class="even">
<td><p><em>Confirm</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>명령을 실행하기 전에 확인 메시지를 표시합니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>Provider</em></p></td>
<td><p>선택</p></td>
<td><p>System.String[]</p></td>
<td><p>사용자가 통신하도록 허용할 공용 공급자를 나타냅니다. 사용할 수 있는 값은 다음과 같습니다.</p>
<p>* AOL</p>
<p>* WindowsLive</p>
<p>* Yahoo</p>
<p>공용 공급자를 구성하는 경우에는 Provider 매개 변수 값에 포함된 모든 공급자가 사용하도록 설정되지만 이 매개 변수 값에 포함되지 않은 공급자는 모두 사용하지 않도록 설정됩니다. 예를 들어 다음 구문은 Yahoo만 사용하도록 설정하고 Windows Live와 AOL은 사용하지 않도록 설정합니다.</p>
<p>-Provider &quot;AOL&quot;</p>
<p>다음과 같이 공급자 이름을 쉼표로 구분하여 여러 공급자를 사용하도록 설정할 수 있습니다.</p>
<p>-Provider &quot;AOL&quot;,&quot;WindowsLive&quot;</p></td>
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

**Set-CsTenantPublicProvider** cmdlet은 Microsoft.Rtc.Management.Hosted.TenantPICStatus 개체의 파이프라인된 인스턴스를 허용합니다.

## 반환 형식

없음. 대신 **Set-CsTenantPublicProvider** cmdlet은 Microsoft.Rtc.Management.Hosted.TenantPICStatus 개체의 기존 인스턴스를 수정합니다.

## 참고 항목

#### 기타 리소스

[Get-CsTenantPublicProvider](get-cstenantpublicprovider.md)

