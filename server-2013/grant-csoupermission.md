---
title: Grant-CsOUPermission
TOCTitle: Grant-CsOUPermission
ms:assetid: 26d8bdbf-abf0-4ca3-b9ab-fbb355fbcca1
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg425739(v=OCS.15)
ms:contentKeyID: 49303100
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Grant-CsOUPermission

 

_**마지막으로 수정된 항목:** 2015-03-09_

Active Directory OU(조직 구성 단위)에 Lync Server 관리 권한을 부여합니다. 이 cmdlet은 Lync Server 2010에서 도입되었습니다.

## 구문

    Grant-CsOUPermission -ObjectType <User | Computer | InetOrgPerson | Contact | AppContact | Device> -OU <String> [-Confirm [<SwitchParameter>]] [-Domain <Fqdn>] [-DomainController <Fqdn>] [-Force <SwitchParameter>] [-GlobalCatalog <Fqdn>] [-Report <String>] [-WhatIf [<SwitchParameter>]]

## 예제

## 예제 1

예제 1에 표시된 명령은 litwareinc.com 도메인의 Redmond OU에 대한 사용자 관리 권한(-ObjectType "user")을 부여합니다.

    Grant-CsOUPermission -OU "ou=Redmond,dc=litwareinc,dc=com" -ObjectType "user"

## 예제 2

예제 2에서는 litwareinc.com 도메인에 있는 Redmond OU의 세 가지 개체(user, contact, inetOrgPerson)에 대한 관리 권한이 부여됩니다.

    Grant-CsOUPermission -OU "ou=Redmond,dc=litwareinc,dc=com" -ObjectType "user","contact","inetOrgPerson"

## 예제 3

예제 3에서는 Redmond, Dublin 및 Tokyo의 세 가지 OU에 대한 사용자 관리 권한이 동시에 부여됩니다. 이 작업을 수행하기 위해 예제의 첫 번째 명령은 $x라는 배열 변수를 만듭니다. 이 변수는 권한이 부여될 세 가지 Active Directory OU의 고유 이름을 포함합니다. 두 번째 명령에서는 배열에 저장된 각 OU를 가져오고 해당 조직 구성 단위에 대해 **Grant-CsOUPermission** cmdlet을 실행하는 foreach 루프가 만들어집니다. 이 명령은 사용자에게 배열의 각 OU에 대한 관리 권한을 부여합니다.

    $x = "ou=Redmond,dc=litwareinc,dc=com", "ou=Dublin,dc=litwareinc,dc=com", "ou=Tokyo,dc=litwareinc,dc=com"
    
    foreach ($i in $x) {Grant-CsOUPermission -OU $i -ObjectType "user"}

## 자세한 정보

Active Directory 도메인을 잠근 경우(즉, 권한 상속을 비활성화한 경우) Lync Server를 설치할 때 수행되는 도메인 준비에서 사용자, 컴퓨터, 대화 상대, 응용 프로그램 대화 상대 및 InetOrg 사람을 관리하는 데 필요한 권한을 추가할 수 없게 됩니다. 도메인 관리자는 이러한 개체를 관리할 수 있지만 RTCUniversalUserAdmins 그룹의 구성원을 비롯한 다른 사용자에게는 관리 권한이 없습니다. 이 경우 **Grant-CsOUPermission** cmdlet을 사용하여 필요한 보안 그룹에 필요한 권한을 제공해야 합니다. 이 작업은 컨테이너 단위로 수행해야 합니다.

이 cmdlet은 미리 정의된 보안 그룹에만 권한을 부여합니다. 따라서 임의의 보안 그룹 또는 개별 사용자에게 권한을 부여하는 데는 사용할 수 없습니다.

**Grant-CsOUPermission** cmdlet을 사용하여 부여한 권한은 나중에 **Revoke-CsOUPermission** cmdlet을 사용하여 제거할 수 있습니다. 이 cmdlet을 실행하면 초기에 OU 권한이 부여된 그룹이 지정된 Active Directory 컨테이너에 대한 Lync Server 관리 권한을 더 이상 가지지 못하게 됩니다. 이 경우 엔터프라이즈 관리자나 도메인 관리자만 Lync Server 또는 해당 구성 요소 중 하나를 관리할 수 있습니다.

이 cmdlet을 실행할 수 있는 사용자: **Grant-CsOUPermission** cmdlet을 로컬로 실행하려면 도메인 관리자여야 합니다. 사용자가 직접 만든 사용자 지정 RBAC(역할 기반 액세스 제어) 역할을 포함하여 이 cmdlet이 할당된 모든 RBAC 역할의 목록을 반환하려면 Windows PowerShell 프롬프트에서 다음 명령을 실행합니다.

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Grant-CsOUPermission"}

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
<p>Device(공통 영역 전화를 만드는 데 필요)</p>
<p>같은 명령에서 여러 개의 개체 유형을 할당하려면 각 개체 유형을 쉼표로 구분합니다(예: -ObjectType &quot;user&quot;,&quot;computer&quot;,&quot;contact&quot;). 명령당 개체 유형을 최대 3개까지만 지정할 수 있습니다.</p></td>
</tr>
<tr class="even">
<td><p><em>OU</em></p></td>
<td><p>필수</p></td>
<td><p>System.String</p></td>
<td><p>권한을 부여할 OU의 고유 이름입니다(예: -OU &quot;ou=Redmond,dc=litwareinc,dc=com&quot;). 명령당 한 개의 OU에만 권한을 부여할 수 있습니다.</p></td>
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
<td><p>OU가 있는 도메인의 이름입니다. 이 매개 변수를 포함하지 않으면 <strong>Grant-CsOUPermission</strong> cmdlet은 현재 도메인의 OU를 찾습니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>DomainController</em></p></td>
<td><p>선택</p></td>
<td><p>Microsoft.Rtc.Management.Deploy.Fqdn</p></td>
<td><p>관리자가 <strong>Grant-CsOUPermission</strong> cmdlet을 실행할 때 사용할 도메인 컨트롤러의 FQDN(정규화된 도메인 이름)을 지정할 수 있습니다. 이 매개 변수를 지정하지 않으면 cmdlet은 사용 가능한 첫 번째 도메인 컨트롤러를 사용합니다.</p></td>
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
<td><p>도메인에 있는 전역 카탈로그 서버의 FQDN입니다. 사용자 도메인의 계정으로 컴퓨터에서 <strong>Grant-CsOUPermission</strong> cmdlet을 실행하는 경우에는 이 매개 변수가 필요하지 않습니다.</p></td>
</tr>
<tr class="even">
<td><p><em>Report</em></p></td>
<td><p>선택</p></td>
<td><p>System.String</p></td>
<td><p>cmdlet을 실행할 때 만들어지는 로그 파일의 파일 경로를 지정할 수 있습니다(예: -Report &quot;C:\Logs\OUPermissions.html&quot;).</p></td>
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

없음. **Grant-CsOUPermission** cmdlet은 파이프라인된 입력을 허용하지 않습니다.

## 반환 형식

**Grant-CsOUPermission** cmdlet은 개체나 값을 반환하지 않습니다.

## 참고 항목

#### 기타 리소스

[Revoke-CsOUPermission](revoke-csoupermission.md)  
[Test-CsOUPermission](test-csoupermission.md)

