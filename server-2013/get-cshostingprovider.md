---
title: Get-CsHostingProvider
TOCTitle: Get-CsHostingProvider
ms:assetid: fd493022-eb53-4084-aa81-213cb5e959fc
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg413078(v=OCS.15)
ms:contentKeyID: 49305626
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Get-CsHostingProvider

 

_**마지막으로 수정된 항목:** 2015-03-09_

조직에서 사용하도록 구성된 호스팅 공급자에 대한 정보를 반환합니다. 호스팅 공급자는 페더레이션하려는 도메인에 메신저, 현재 상태 및 관련 서비스를 제공하는 타사 조직입니다. Microsoft Lync Online 2010과 같은 호스팅 공급자는 일반인에게 서비스를 제공하지 않는다는 점에서 Yahoo\!, MSN 및 AOL 등의 공용 공급자와 다릅니다. 이 cmdlet은 Lync Server 2010에서 도입되었습니다.

## 구문

    Get-CsHostingProvider [-Identity <XdsGlobalRelativeIdentity>] <COMMON PARAMETERS>

    Get-CsHostingProvider [-Filter <String>] <COMMON PARAMETERS>

    COMMON PARAMETERS: [-LocalStore <SwitchParameter>]

## 예제

## 예제 1

예제 1에서는 조직에서 사용하도록 구성된 모든 호스팅 공급자 컬렉션을 반환합니다. **Get-CsHostingProvider** cmdlet을 추가 매개 변수 없이 호출하면 호스팅 공급자의 전체 컬렉션이 반환됩니다.

    Get-CsHostingProvider

## 예제 2

예제 2에서는 ID가 Fabrikam.com인 호스팅 공급자를 반환합니다. ID는 호스팅 공급자 간에 고유해야 하므로 이 명령은 두 개 이상의 항목을 반환하지 않습니다.

    Get-CsHostingProvider -Identity Fabrikam.com

## 예제 3

예제 3에 표시된 명령은 ID가 문자열 값 ".org"로 끝나는(예: fabrikam.org 및 contoso.org) 모든 호스팅 공급자 컬렉션을 반환합니다.

    Get-CsHostingProvider -Filter *.org

## 예제 4

예제 4에서는 현재 사용하도록 설정된 모든 호스팅 공급자를 반환합니다. 이 작업을 수행하기 위해 먼저 **Get-CsHostingProvider** cmdlet을 호출하여 조직에서 현재 사용하도록 구성된 모든 호스팅 공급자 컬렉션을 반환합니다. 이 컬렉션은 Enabled 속성이 True와 같은 공급자만 선택하는 **Where-Object** cmdlet에 파이프됩니다.

    Get-CsHostingProvider | Where-Object {$_.Enabled -eq $True}

## 예제 5

예제 5에서는 공유 주소 공간이 있고 Lync Server 사용자를 호스트하는 모든 호스팅 공급자를 반환합니다. 즉, 정의에 따라 이 명령은 "분할 도메인" 설정의 일부인 모든 호스팅 공급자를 반환합니다. 분할 도메인은 일부 Lync Server 계정은 온-프레미스에서 유지 관리되고 다른 계정은 호스팅 공급자가 유지 관리하는 환경을 의미합니다. 이 작업을 수행하기 위해 명령은 먼저 **Get-CsHostingProvider** cmdlet을 사용하여 현재 구성된 모든 호스팅 공급자 컬렉션을 반환합니다. 이 컬렉션은 **Where-Object** cmdlet에 파이프됩니다. 이 cmdlet은 1) Enabled 속성이 True와 같고 2) EnabledSharedAddressSpace 속성이 True와 같다는 2가지 조건을 충족하는 공급자만 선택합니다.

    Get-CsHostingProvider | Where-Object {$_.Enabled -eq $True -and $_.EnabledSharedAddressSpace -eq $True}

## 예제 6

예제 6에 표시된 명령은 조직에서 사용하도록 구성된 모든 호스팅 공급자의 모든 속성 값을 표시합니다. 기본적으로 **Get-CsHostingProvider** cmdlet을 실행하면 EnabledSharedAddressSpace 및 HostsOCSUsers의 속성 값이 표시되지 않습니다. 이러한 속성 값을 확인하기 위해 **Get-CsHostingProvider** cmdlet에 의해 반환된 정보가 **Select-Object** cmdlet에 파이프됩니다. 와일드카드 문자(\*)는 **Select-Object** cmdlet에 반환된 항목의 모든 속성 및 속성 값을 표시하도록 지시합니다.

    Get-CsHostingProvider | Select-Object *

## 자세한 정보

페더레이션은 두 조직에서 두 그룹 간의 통신을 용이하게 하는 트러스트 관계를 설정할 수 있는 수단입니다. 페더레이션이 설정되면 두 조직의 사용자가 서로 메신저 대화를 보내고, 현재 상태 알림에 가입하고, Lync와 같은 SIP 응용 프로그램을 사용하여 통신할 수 있습니다. Lync Server를 사용하면 1) 사용자 조직과 다른 조직 간의 직접 페더레이션, 2) 사용자 조직과 공용 공급자 간의 페더레이션 및 3) 사용자 조직과 타사 호스팅 공급자 간의 페더레이션이라는 세 가지 유형의 페더레이션을 설정할 수 있습니다.

호스팅 공급자는 다른 조직에 SIP 통신 서비스를 제공하는 조직입니다. 예를 들어 Fabrikam, Inc.는 Contoso, Northwind Traders, Wingtip Toys 등의 사용자를 호스트할 수 있습니다. 호스팅 공급자와의 페더레이션 관계를 설정하면 해당 공급자가 호스트하는 조직과 효과적으로 페더레이션을 설정할 수 있습니다. 예를 들어 Fabrikam과 페더레이션한 경우 Contoso, Northwind Traders 및 Wingtip Toys의 사용자와 메신저 대화 및 현재 상태 정보를 교환할 수 있습니다.

분할 도메인 시나리오에서 호스팅 공급자를 사용할 수도 있습니다. 분할 도메인 시나리오에서 일부 Lync Server 사용자는 온-프레미스에서 호스트되는 계정, 즉 Lync Server의 로컬 구현에서 호스트되는 계정을 가지고 있고, 다른 사용자는 호스팅 공급자가 오프-프레미스에서 유지 관리하는 계정을 가지고 있습니다. 호스팅 공급자와 페더레이션하면 온-프레미스 사용자와 오프-프레미스 사용자가 서로 통신할 수 있습니다.

**Get-CsHostingProvider** cmdlet을 사용하면 조직에서 사용하도록 구성된 모든 호스팅 공급자에 대한 정보를 반환할 수 있습니다.

에지 서버가 DNS(Domain Name System) 서버 라우팅이 아닌 기본 라우팅을 사용하도록 구성된 경우 호스팅 공급자와 페더레이션할 수 없습니다.

이 cmdlet을 실행할 수 있는 사용자: 기본적으로 RTCUniversalUserAdmins 및 RTCUniversalServerAdmins 그룹의 구성원은 **Get-CsHostingProvider** cmdlet을 로컬로 실행할 수 있습니다. 사용자가 직접 만든 사용자 지정 RBAC(역할 기반 액세스 제어) 역할을 포함하여 이 cmdlet이 할당된 모든 RBAC 역할의 목록을 반환하려면 Windows PowerShell 프롬프트에서 다음 명령을 실행합니다.

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Get-CsHostingProvider"}

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
<td><p>와일드카드 값을 사용하여 하나 이상의 호스팅 공급자를 반환하는 데 사용됩니다. 예를 들어 ID가 문자열 값 &quot;com&quot;으로 끝나는 모든 호스팅 공급자를 반환하려면 -Filter &quot;*.com&quot; 구문을 사용하고, ID가 문자열 값 &quot;Fabri&quot;로 시작하는 모든 호스팅 공급자를 반환하려면 -Filter &quot;Fabri*&quot; 구문을 사용합니다.</p></td>
</tr>
<tr class="even">
<td><p><em>Identity</em></p></td>
<td><p>선택</p></td>
<td><p>Microsoft.Rtc.Management.Xds.XdsGlobalRelativeIdentity</p></td>
<td><p>반환할 호스팅 공급자의 고유 식별자입니다. Identity는 호스팅 공급자의 FQDN(정규화된 도메인 이름)(예: fabrikam.com)일 수도 있고, 서비스를 제공하는 회사의 이름(Fabrikam, Inc.)일 수도 있습니다.</p>
<p>이 매개 변수를 지정하지 않으면 <strong>Get-CsHostingProvider</strong> cmdlet이 조직에서 사용하도록 구성된 모든 호스팅 공급자 컬렉션을 반환합니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>LocalStore</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>중앙 관리 저장소 자체가 아니라 중앙 관리 저장소의 로컬 복제본에서 호스팅 공급자 데이터를 검색합니다.</p></td>
</tr>
</tbody>
</table>


## 입력 형식

없음. **Get-CsHostingProvider** cmdlet은 파이프라인된 입력을 허용하지 않습니다.

## 반환 형식

Microsoft.Rtc.Management.WritableConfig.Settings.Edge.DisplayHostingProvider 개체의 인스턴스를 반환합니다.

## 참고 항목

#### 기타 리소스

[Disable-CsHostingProvider](disable-cshostingprovider.md)  
[Enable-CsHostingProvider](enable-cshostingprovider.md)  
[New-CsHostingProvider](new-cshostingprovider.md)  
[Remove-CsHostingProvider](remove-cshostingprovider.md)  
[Set-CsHostingProvider](set-cshostingprovider.md)

