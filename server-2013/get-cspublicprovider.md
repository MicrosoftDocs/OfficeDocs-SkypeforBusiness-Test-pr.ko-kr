---
title: Get-CsPublicProvider
TOCTitle: Get-CsPublicProvider
ms:assetid: c122505d-7209-4dcb-a888-5c73f58fa68a
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg412945(v=OCS.15)
ms:contentKeyID: 49304918
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Get-CsPublicProvider

 

_**마지막으로 수정된 항목:** 2015-03-09_

조직에서 사용하도록 구성된 공용 공급자에 대한 정보를 반환합니다. 공용 공급자는 메신저, 현재 상태 및 관련 서비스를 일반 대중에 제공하는 조직입니다. Lync Server에는 Yahoo\!, AIM(AOL) 및 Messenger(MSN)가 함께 제공되는데, 이러한 공용 공급자는 구성되어 있지만 사용하도록 설정되어 있지는 않습니다. 이 cmdlet은 Lync Server 2010에서 도입되었습니다.

## 구문

    Get-CsPublicProvider [-Identity <XdsGlobalRelativeIdentity>] <COMMON PARAMETERS>

    Get-CsPublicProvider [-Filter <String>] <COMMON PARAMETERS>

    COMMON PARAMETERS: [-LocalStore <SwitchParameter>]

## 예제

## 예제 1

예제 1에 표시된 명령은 조직에서 사용하도록 구성된 모든 공용 공급자 컬렉션을 반환합니다. **Get-CsPublicProvider** cmdlet을 추가 매개 변수 없이 호출하면 항상 공용 공급자의 전체 컬렉션이 반환됩니다.

    Get-CsPublicProvider

## 예제 2

예제 2에서는 ID가 Messenger인 모든 공용 공급자를 반환합니다. ID는 공용 공급자 및 호스팅 공급자 간에 고유해야 하므로 이 명령은 항상 단일 항목만 반환합니다.

    Get-CsPublicProvider -Identity "Messenger"

## 예제 3

예제 3에서는 ID가 W 문자로 시작하는 모든 공용 공급자를 반환합니다. 이 작업을 수행하기 위해 Filter 매개 변수 및 필터 값 "W\*"를 포함합니다.

    Get-CsPublicProvider -Filter W*

## 예제 4

예제 4에 표시된 명령은 현재 사용하지 않도록 설정된 모든 공용 공급자 컬렉션을 반환합니다. 이 작업을 수행하기 위해 명령은 먼저 **Get-CsPublicProvider** cmdlet을 호출하여 조직에서 사용하도록 구성된 모든 공용 공급자 컬렉션을 반환합니다. 이 컬렉션은 Enabled 속성이 False와 같은 공급자만 선택하는 **Where-Object** cmdlet에 파이프됩니다.

    Get-CsPublicProvider | Where-Object {$_.Enabled -eq $False}

## 예제 5

예제 5에서는 VerificationLevel 속성이 AlwaysUnverifiable 또는 UseSourceVerification으로 설정된 모든 공용 공급자를 반환합니다. 확인 수준은 AlwaysUnverifiable, UseSourceVerification 또는 AlwaysVerifiable로 설정할 수 있습니다. 이 작업을 수행하기 위해 명령은 먼저 **Get-CsPublicProvider** cmdlet을 호출하여 조직에서 사용하도록 구성된 모든 공용 공급자 컬렉션을 반환합니다. 이 컬렉션은 VerificationLevel 속성이 AlwaysVerifiable과 같지 않은 공급자만 선택하는 **Where-Object** cmdlet에 파이프됩니다. 그러면 VerificationLevel 속성이 AlwaysUnverifiable 또는 UseSourceVerification으로 설정된 공급자만 선택됩니다.

    Get-CsPublicProvider | Where-Object {$_.VerificationLevel -ne "AlwaysVerifiable"}

## 자세한 정보

페더레이션은 두 조직에서 두 그룹 간의 통신을 용이하게 하는 트러스트 관계를 설정할 수 있는 수단입니다. 페더레이션이 설정되면 두 조직의 사용자가 서로 인스턴스 메시지를 보내고, 현재 상태 알림에 가입하고, Lync 2013과 같은 SIP 응용 프로그램을 사용하여 통신할 수 있습니다. Lync Server를 사용하면 1) 사용자 조직과 다른 조직 간의 직접 페더레이션, 2) 사용자 조직과 공용 공급자 간의 페더레이션 및 3) 사용자 조직과 타사 호스팅 공급자 간의 페더레이션이라는 세 가지 유형의 페더레이션을 설정할 수 있습니다.

공용 공급자는 일반인에게 SIP 통신 서비스를 제공하는 조직입니다. 공용 공급자와의 페더레이션 관계를 설정하면 해당 공급자가 호스트하는 계정을 가진 사용자와의 페더레이션을 효과적으로 설정할 수 있습니다. 예를 들어 Messenger(MSN)와 페더레이션한 경우 사용자가 Messenger 계정을 가진 다른 사용자와 메신저 대화 및 현재 상태 정보를 교환할 수 있습니다.

공용 공급자와 페더레이션하려면 새 공용 공급자를 만들고 사용하도록 설정해야 합니다. 또한 해당 공용 공급자가 사용자와 페더레이션 관계를 만들어야 합니다. **Get-CsPublicProvider** cmdlet을 사용하면 조직에서 사용하도록 구성된 공용 공급자에 대한 정보를 반환할 수 있습니다.

이 cmdlet을 실행할 수 있는 사용자: 기본적으로 RTCUniversalUserAdmins 및 RTCUniversalServerAdmins 그룹의 구성원은 **Get-CsPublicProvider** cmdlet을 로컬로 실행할 수 있습니다. 사용자가 직접 만든 사용자 지정 RBAC(역할 기반 액세스 제어) 역할을 포함하여 이 cmdlet이 할당된 모든 RBAC 역할의 목록을 반환하려면 Windows PowerShell 프롬프트에서 다음 명령을 실행합니다.

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Get-CsPublicProvider"}

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
<td><p>와일드카드 값을 사용하여 하나 이상의 공용 공급자를 반환하는 데 사용됩니다. 예를 들어 ID가 Y 문자로 시작하는 모든 공용 공급자 컬렉션을 반환하려면 -Filter &quot;Y*&quot; 구문을 사용하고, Identity에 &quot;Windows&quot; 문자열 값이 포함된 모든 공용 공급자 컬렉션을 반환하려면 -Filter &quot;*Windows*&quot; 구문을 사용하십시오.</p></td>
</tr>
<tr class="even">
<td><p><em>Identity</em></p></td>
<td><p>선택</p></td>
<td><p>Microsoft.Rtc.Management.Xds.XdsGlobalRelativeIdentity</p></td>
<td><p>반환할 공용 공급자의 고유 식별자입니다. Identity는 일반적으로 서비스를 제공하는 웹 사이트(예: Yahoo!, AOL, MSN 등)의 이름입니다.</p>
<p>ID를 지정할 때는 와일드카드를 사용할 수 없습니다. 와일드카드를 사용하여 하나 이상의 공용 공급자를 반환하려면 대신 Filter 매개 변수를 사용합니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>LocalStore</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>중앙 관리 저장소 자체가 아니라 중앙 관리 저장소의 로컬 복제본에서 공용 공급자 데이터를 검색합니다.</p></td>
</tr>
</tbody>
</table>


## 입력 형식

없음. **Get-CsPublicProvider** cmdlet은 파이프라인된 입력을 허용하지 않습니다.

## 반환 형식

Microsoft.Rtc.Management.WritableConfig.Settings.Edge.DisplayPublicProvider 개체의 인스턴스를 반환합니다.

## 참고 항목

#### 기타 리소스

[Disable-CsPublicProvider](disable-cspublicprovider.md)  
[Enable-CsPublicProvider](enable-cspublicprovider.md)  
[New-CsPublicProvider](new-cspublicprovider.md)  
[Remove-CsPublicProvider](remove-cspublicprovider.md)  
[Set-CsPublicProvider](set-cspublicprovider.md)

