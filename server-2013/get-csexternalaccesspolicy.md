---
title: Get-CsExternalAccessPolicy
TOCTitle: Get-CsExternalAccessPolicy
ms:assetid: 301403c8-aeb2-4501-a2ae-96eaa6ad68a4
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg425805(v=OCS.15)
ms:contentKeyID: 49303206
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Get-CsExternalAccessPolicy

 

_**마지막으로 수정된 항목:** 2015-03-09_

조직에서 사용하도록 구성된 외부 액세스 정책에 대한 정보를 반환합니다. 외부 액세스 정책은 사용자가 1) 페더레이션 조직의 SIP(Session Initiation Protocol) 계정을 가진 사용자와 통신할 수 있는지 여부, 2) Windows Live와 같은 공용 메신저 공급자의 SIP 계정을 가진 사용자와 통신할 수 있는지 여부 및 3) 내부 네트워크에 로그온하지 않고도 인터넷을 통해 Lync Server에 액세스할 수 있는지 여부를 결정합니다. 이 cmdlet은 Lync Server 2010에서 도입되었습니다.

## 구문

    Get-CsExternalAccessPolicy [-Identity <XdsIdentity>] [[-ApplicableTo] <Object>] <COMMON PARAMETERS>

    Get-CsExternalAccessPolicy [-Filter <String>] [[-ApplicableTo] <Object>] <COMMON PARAMETERS>

    COMMON PARAMETERS: [-LocalStore <SwitchParameter>]

## 예제

## 예제 1

예제 1에서는 조직에서 사용하도록 구성된 모든 외부 액세스 정책의 컬렉션을 반환합니다. **Get-CsExternalAccessPolicy** cmdlet을 추가 매개 변수 없이 호출하면 항상 외부 액세스 정책의 전체 컬렉션이 반환됩니다.

    Get-CsExternalAccessPolicy

## 예제 2

예제 2는 Identity 매개 변수를 사용하여 ID가 site:Redmond인 외부 액세스 정책을 반환합니다. 액세스 정책 ID는 고유해야 하므로 이 명령은 둘 이상의 항목을 반환하지 않습니다.

    Get-CsExternalAccessPolicy -Identity site:Redmond

## 예제 3

예제 3에 표시된 명령은 Filter 매개 변수를 사용하여 사용자별 범위에 구성된 모든 외부 액세스 정책을 반환합니다. 매개 변수 값 "tag:\*"는 문자열 값 "tag:"으로 시작하는 ID가 있는 정책에 대한 데이터만 반환하도록 제한합니다. 정의에 따르면 "tag:"으로 시작하는 ID가 있는 모든 정책은 사용자별 범위에 구성된 정책입니다.

    Get-CsExternalAccessPolicy -Filter tag:*

## 예제 4

예제 4에서는 **Get-CsExternalAccessPolicy** cmdlet 및 **Where-Object** cmdlet을 사용하여 사용자에게 페더레이션 액세스 권한을 부여하는 모든 외부 액세스 정책을 반환합니다. 이 작업을 수행하기 위해 먼저 **Get-CsExternalAccessPolicy** cmdlet을 사용하여 조직에서 현재 사용 중인 모든 외부 액세스 정책의 컬렉션을 반환합니다. 이 컬렉션은 EnableFederationAccess 속성이 True와 같은 정책만 선택하는 **Where-Object** cmdlet에 파이프됩니다.

    Get-CsExternalAccessPolicy | Where-Object {$_.EnableFederationAccess -eq $True}

## 예제 5

예제 5에 표시된 명령은 페더레이션 액세스 및 공용 클라우드 액세스가 모두 허용되어야 한다는 두 가지 기준을 충족하는 외부 액세스 정책을 반환합니다. 이 작업을 수행하기 위해 이 명령은 먼저 **Get-CsExternalAccessPolicy** cmdlet을 사용하여 조직에서 사용 중인 모든 액세스 정책의 컬렉션을 반환합니다. 이 컬렉션은 EnableFederationAccess 속성이 True와 같고 EnablePublicCloudAccess 속성도 True와 같은 정책만 선택하는 **Where-Object** cmdlet에 파이프됩니다. EnableFederationAccess와 EnablePublicCloudAccess가 모두 True인 정책만 반환되어 화면에 표시됩니다.

EnableFederationAccess 또는 EnablePublicCloudAccess 중 하나가 True인 정책의 목록을 반환하려면 –or 연산자를 사용합니다.

Where-Object {$\_.EnableFederationAccess -eq $True -or $\_.EnablePublicCloudAccess -eq $True}

    Get-CsExternalAccessPolicy | Where-Object {$_.EnableFederationAccess -eq $True -and $_.EnablePublicCloudAccess -eq $True} 

## 자세한 정보

Lync Server를 설치하면 내부 사용자들만 서로 메신저 대화 및 현재 상태 정보를 교환할 수 있습니다. 기본적으로 Active Directory 도메인 서비스에 SIP 계정이 있는 다른 사용자와만 통신할 수 있습니다. 또한 인터넷을 통해 Lync Server에 액세스할 수 없습니다. 대신 Lync Server에 로그온하려면 먼저 내부 네트워크에 로그온해야 합니다.

이것만으로도 통신 요구를 충분히 만족시킬 수 있을 것입니다. 그러나 이 정도로 부족한 경우 외부 액세스 정책을 사용하여 통신 및 공동 작업 기능을 확장할 수 있습니다. 외부 액세스 정책은 사용자에게 다음과 같은 작업의 일부 또는 전부를 수행할 수 있는 권한을 부여하거나 이러한 권한을 해지할 수 있습니다.

1\. 페더레이션 조직의 SIP 계정을 가진 사용자와 통신 - 페더레이션을 사용하도록 설정하는 것만으로는 이러한 기능이 제공되지 않습니다. 대신 페더레이션을 사용하도록 설정한 다음, 사용자에게 페더레이션 사용자와 통신할 권한을 제공하는 외부 액세스 정책을 할당해야 합니다.

2\. Windows Live와 같은 공용 메시지 서비스의 SIP 계정을 가진 사용자와 통신

3\. 내부 네트워크에 로그온하지 않고도 인터넷을 통해 Lync Server에 액세스 - 이 경우 사용자는 인터넷 카페 또는 기타 원격 위치에서 Lync를 사용하고 Lync Server에 로그온할 수 있습니다.

**Get-CsExternalAccessPolicy** cmdlet은 조직에서 사용하도록 구성된 모든 외부 액세스 정책에 대한 정보를 반환할 수 있는 방법을 제공합니다.

이 cmdlet을 실행할 수 있는 사용자: 기본적으로 RTCUniversalUserAdmins 및 RTCUniversalServerAdmins 그룹의 구성원은 **Get-CsExternalAccessPolicy** cmdlet을 로컬로 실행할 수 있습니다. 사용자가 직접 만든 사용자 지정 RBAC(역할 기반 액세스 제어) 역할을 포함하여 이 cmdlet이 할당된 모든 RBAC 역할의 목록을 반환하려면 Windows PowerShell 프롬프트에서 다음 명령을 실행합니다.

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Get-CsExternalAccessPolicy"}

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
<td><p>외부 액세스 정책에 대해 와일드카드 검색을 수행할 수 있습니다. 예를 들어 사이트 범위에 구성된 모든 정책을 찾아보려면 site:* 필터를 사용합니다. 사용자별 정책 Seattle, Seville 및 Saskatoon(모두 &quot;S&quot;로 시작)을 찾아보려면 &quot;S*&quot; 필터를 사용합니다. Filter 매개 변수는 정책 ID에만 적용할 수 있습니다.</p></td>
</tr>
<tr class="even">
<td><p><em>Identity</em></p></td>
<td><p>선택</p></td>
<td><p>Microsoft.Rtc.Management.Xds.XdsIdentity</p></td>
<td><p>정책이 만들어질 때 정책에 할당된 고유 ID입니다. 외부 액세스 정책은 전역, 사이트 또는 사용자별 범위에 할당할 수 있습니다. 전역 인스턴스를 참조하려면 -Identity global 구문을 사용합니다. 사이트 범위의 정책을 참조하려면 -Identity site:Redmond 구문을 사용합니다. 사용자별 범위의 정책을 참조하려면 -Identity RedmondPolicy와 유사한 구문을 사용합니다.</p>
<p>별표(*)와 같은 와일드카드 문자는 Identity 매개 변수에 사용할 수 없습니다. 정책에 대해 와일드카드 검색을 수행하려면 Filter 매개 변수를 대신 사용합니다.</p>
<p>Identity 또는 Filter 매개 변수가 둘 다 지정되지 않은 경우 <strong>Get-CsExternalAccessPolicy</strong> cmdlet에서 조직에서 사용하도록 구성된 모든 외부 액세스 정책 컬렉션을 가져옵니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>LocalStore</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>중앙 관리 저장소 자체가 아니라 중앙 관리 저장소의 로컬 복제본에서 외부 액세스 정책 데이터를 검색합니다.</p></td>
</tr>
</tbody>
</table>


## 입력 형식

없음. **Get-CsExternalAccessPolicy** cmdlet은 파이프라인된 입력을 허용하지 않습니다.

## 반환 형식

Microsoft.Rtc.Management.WritableConfig.Policy.ExternalAccess.ExternalAccessPolicy 개체의 인스턴스를 반환합니다.

## 참고 항목

#### 기타 리소스

[Grant-CsExternalAccessPolicy](grant-csexternalaccesspolicy.md)  
[New-CsExternalAccessPolicy](new-csexternalaccesspolicy.md)  
[Remove-CsExternalAccessPolicy](remove-csexternalaccesspolicy.md)  
[Set-CsExternalAccessPolicy](set-csexternalaccesspolicy.md)

