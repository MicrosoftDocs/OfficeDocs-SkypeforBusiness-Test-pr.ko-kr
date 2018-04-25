---
title: Revoke-CsOUPermission
TOCTitle: Revoke-CsOUPermission
ms:assetid: de0542c9-6d11-4038-9b4a-757338d61fae
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg398977(v=OCS.15)
ms:contentKeyID: 49305256
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Revoke-CsOUPermission

 

_**마지막으로 수정된 항목:** 2015-03-09_

Active Directory OU(조직 구성 단위)에 부여된 Lync Server 관리 권한을 해지합니다. 이 cmdlet은 Lync Server 2010에서 도입되었습니다.

## 구문

    Revoke-CsOUPermission -ObjectType <User | Computer | InetOrgPerson | Contact | AppContact | Device> -OU <String> [-Confirm [<SwitchParameter>]] [-Domain <Fqdn>] [-DomainController <Fqdn>] [-Force <SwitchParameter>] [-GlobalCatalog <Fqdn>] [-Report <String>] [-WhatIf [<SwitchParameter>]]

## 예제

## 예제 1

예제 1에 표시된 명령은 litwareinc.com 도메인에서 Redmond OU의 사용자 관리 권한(-ObjectType "user")을 해지합니다.

    Revoke-CsOUPermission -OU "ou=Redmond,dc=litwareinc,dc=com" -ObjectType "user"

## 예제 2

예제 2에서는 litwareinc.com 도메인에서 Redmond OU의 세 가지 다른 관리 권한(user, contact 및 inetOrgPerson 개체)을 제거합니다.

    Revoke-CsOUPermission -OU "ou=Redmond,dc=litwareinc,dc=com" -ObjectType "user","contact","inetOrgPerson"

## 자세한 정보

Active Directory 도메인을 잠근 경우(즉, 권한 상속을 비활성화한 경우) Lync Server를 설치할 때 수행되는 도메인 준비에서 사용자, 컴퓨터, 대화 상대, 응용 프로그램 대화 상대 및 InetOrg 사람을 관리하는 데 필요한 사용 권한을 추가할 수 없게 됩니다. 엔터프라이즈 관리자 및 도메인 관리자는 이러한 개체를 관리할 수 있지만 RTCUniversalServerAdmins 그룹의 구성원을 비롯한 다른 사용자에게는 관리 권한이 없습니다. 이 경우 **Grant-CsOUPermission** cmdlet을 사용하여 필요한 보안 그룹에 필요한 사용 권한을 부여해야 합니다. 이 작업은 Lync Server 사용자 계정이 포함된 각 Active Directory 컨테이너에 대해 컨테이너 단위로 수행해야 합니다.

**Grant-CsOUPermission** cmdlet을 사용하여 부여한 권한은 나중에 **Revoke-CsOUPermission**을 사용하여 제거할 수 있습니다. OU에 대해 **Revoke-CsOUPermission** cmdlet을 실행하는 경우 해당 OU의 Lync Server 사용자를 관리하려면 엔터프라이즈 관리자 또는 도메인 관리자여야 합니다.

이 cmdlet을 실행할 수 있는 사용자: **Revoke-CsOUPermission** cmdlet을 로컬로 실행하려면 도메인 관리자여야 합니다. 사용자가 직접 만든 사용자 지정 RBAC(역할 기반 액세스 제어) 역할을 포함하여 이 cmdlet이 할당된 모든 RBAC 역할의 목록을 반환하려면 Windows PowerShell 프롬프트에서 다음 명령을 실행합니다.

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Revoke-CsOUPermission"}

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
<td><p><em>ObjectType</em></p></td>
<td><p>필수</p></td>
<td><p>Microsoft.Rtc.Management.Deployment.ObjectType</p></td>
<td><p>이러한 권한이 적용되는 개체의 유형입니다. 사용할 수 있는 값은 다음과 같습니다.</p>
<p>User</p>
<p>Computer</p>
<p>Contact</p>
<p>AppContact</p>
<p>InetOrgPerson</p>
<p>동일한 명령에서 여러 개체 유형에 대한 권한을 해지하려면 개체 유형을 쉼표로 구분하십시오(예: -ObjectType &quot;user&quot;,&quot;computer&quot;,&quot;contact&quot;).</p></td>
</tr>
<tr class="even">
<td><p><em>OU</em></p></td>
<td><p>필수</p></td>
<td><p>System.String</p></td>
<td><p>권한을 제거할 OU의 고유 이름입니다 (예: -OU &quot;ou=Redmond,dc=litwareinc,dc=com&quot;). 명령당 하나의 OU에서만 권한을 제거할 수 있습니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>Confirm</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>명령을 실행하기 전에 확인 메시지를 표시합니다.</p></td>
</tr>
<tr class="even">
<td><p><em>Domain</em></p></td>
<td><p>선택</p></td>
<td><p>Microsoft.Rtc.Management.Deploy.Fqdn</p></td>
<td><p>OU가 있는 도메인의 이름입니다. 이 매개 변수를 포함하지 않으면 <strong>Revoke-CsOUPermission</strong> cmdlet이 현재 도메인에서 OU를 찾습니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>DomainController</em></p></td>
<td><p>선택</p></td>
<td><p>Microsoft.Rtc.Management.Deploy.Fqdn</p></td>
<td><p>관리자가 <strong>Revoke-CsOUPermission</strong> cmdlet을 실행할 때 사용할 도메인 컨트롤러의 FQDN(정규화된 도메인 이름)을 지정할 수 있습니다. 이 매개 변수를 지정하지 않으면 cmdlet이 사용 가능한 첫 번째 도메인 컨트롤러를 사용하게 됩니다.</p></td>
</tr>
<tr class="even">
<td><p><em>Force</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>명령을 실행할 때 발생할 수 있는 심각하지 않은 오류 메시지를 표시하지 않습니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>GlobalCatalog</em></p></td>
<td><p>선택</p></td>
<td><p>Microsoft.Rtc.Management.Deploy.Fqdn</p></td>
<td><p>도메인에 있는 전역 카탈로그 서버의 정규화된 도메인 이름입니다. 사용자 도메인의 계정으로 컴퓨터에서 <strong>Revoke-CsOUPermission</strong> cmdlet을 실행하는 경우에는 이 매개 변수가 필요하지 않습니다.</p></td>
</tr>
<tr class="even">
<td><p><em>Report</em></p></td>
<td><p>선택</p></td>
<td><p>System.String</p></td>
<td><p>cmdlet이 실행될 때 만들어지는 로그 파일의 파일 경로를 지정하는 데 사용됩니다(예: -Report &quot;C:\Logs\OUPermissions.html&quot;).</p></td>
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

없음. **Revoke-CsOUPermission** cmdlet은 파이프라인된 입력을 허용하지 않습니다.

## 반환 형식

**Revoke-CsOUPermission** cmdlet은 개체나 값을 반환하지 않습니다.

## 참고 항목

#### 기타 리소스

[Grant-CsOUPermission](grant-csoupermission.md)  
[Test-CsOUPermission](test-csoupermission.md)

