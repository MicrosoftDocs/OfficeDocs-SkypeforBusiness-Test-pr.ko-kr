---
title: Test-CsOUPermission
TOCTitle: Test-CsOUPermission
ms:assetid: 9908eac9-765e-4406-bb6b-0e4dd07f85f8
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg398787(v=OCS.15)
ms:contentKeyID: 49304479
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Test-CsOUPermission

 

_**마지막으로 수정된 항목:** 2015-03-09_

사용자, 컴퓨터 및 기타 개체를 관리하는 데 필요한 사용 권한이 지정된 Active Directory 컨테이너에 설정되었는지 확인합니다. 이 cmdlet은 Lync Server 2010에서 도입되었습니다.

## 구문

    Test-CsOUPermission -ObjectType <User | Computer | InetOrgPerson | Contact | AppContact | Device> -OU <String> [-Domain <Fqdn>] [-DomainController <Fqdn>] [-GlobalCatalog <Fqdn>] [-Report <String>]

## 예제

## 예제 1

예제 1의 명령은 litwareinc.com 도메인의 Redmond OU에 사용자 권한이 설정되었는지 확인합니다.

    Test-CsOUPermission -OU "ou=Redmond,dc=litwareinc,dc=com" -ObjectType "user"

## 자세한 정보

Active Directory 도메인을 잠근 경우(즉, 권한 상속을 비활성화한 경우) Lync Server를 설치할 때 수행되는 도메인 준비에서 사용자, 컴퓨터, 대화 상대, 응용 프로그램 대화 상대 및 InetOrg 사람을 관리하는 데 필요한 사용 권한을 추가할 수 없게 됩니다. 도메인 관리자는 이러한 개체를 관리할 수 있지만 RTCUniversalServerAdmins 그룹의 구성원을 비롯한 다른 사용자에게는 관리 권한이 없습니다. 이 경우 [Grant-CsOUPermission](grant-csoupermission.md) cmdlet을 사용하여 RTCUniversalServerAdmins 그룹에 적절한 사용 권한을 부여해야 합니다. 또한 이 작업은 컨테이너별로 수행해야 합니다.

**Test-CsOUPermission** cmdlet을 사용하면 지정된 Active Directory 컨테이너에 필수 사용 권한이 추가되었는지 여부를 확인할 수 있습니다. **Test-CsOUPermission** cmdlet은 적절한 사용 권한이 적용된 경우 True를 반환하고, 적절한 사용 권한이 적용되지 않은 경우 False를 반환합니다. False가 반환되는 경우 [Grant-CsOUPermission](grant-csoupermission.md) cmdlet을 실행하여 필요한 변경 작업을 수행해야 합니다.

이 cmdlet을 실행할 수 있는 사용자: 사용자가 직접 만든 사용자 지정 RBAC(역할 기반 액세스 제어) 역할을 포함하여 이 cmdlet이 할당된 모든 RBAC 역할의 목록을 반환하려면 Windows PowerShell 프롬프트에서 다음 명령을 실행합니다.

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Test-CsOUPermission"}

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
<td><p>확인할 개체 유형입니다. 사용할 수 있는 값은 다음과 같습니다.</p>
<p>User</p>
<p>Computer</p>
<p>Contact</p>
<p>AppContact</p>
<p>InetOrgPerson</p>
<p>같은 종류의 여러 개체를 확인하려면 쉼표를 사용하여 개체 유형을 구분합니다(예: -ObjectType &quot;user&quot;,&quot;computer&quot;,&quot;contact&quot;).</p></td>
</tr>
<tr class="even">
<td><p><em>OU</em></p></td>
<td><p>필수</p></td>
<td><p>System.String</p></td>
<td><p>확인할 OU(조직 구성 단위)의 고유 이름입니다. 예를 들면 다음과 같습니다. -OU &quot;ou=Redmond,dc=litwareinc,dc=com&quot;.</p>
<p>명령당 하나의 OU만 확인할 수 있습니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>Domain</em></p></td>
<td><p>선택</p></td>
<td><p>Microsoft.Rtc.Management.Deploy.Fqdn</p></td>
<td><p>확인할 OU가 위치한 도메인의 이름입니다. 이 매개 변수를 포함하지 않으면 <strong>Test-CsOUPermission</strong> cmdlet은 현재 도메인의 OU를 찾습니다.</p></td>
</tr>
<tr class="even">
<td><p><em>DomainController</em></p></td>
<td><p>선택</p></td>
<td><p>Microsoft.Rtc.Management.Deploy.Fqdn</p></td>
<td><p>도메인에 있는 도메인 컨트롤러의 FQDN(정규화된 도메인 이름)입니다. 사용자 도메인의 계정으로 컴퓨터에서 <strong>Test-CsOUPermission</strong> cmdlet을 실행하는 경우에는 이 매개 변수가 필요하지 않습니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>GlobalCatalog</em></p></td>
<td><p>선택</p></td>
<td><p>Microsoft.Rtc.Management.Deploy.Fqdn</p></td>
<td><p>도메인에 있는 전역 카탈로그 서버의 FQDN입니다. 사용자 도메인의 계정으로 컴퓨터에서 <strong>Test-CsOUPermission</strong> cmdlet을 실행하는 경우에는 이 매개 변수가 필요하지 않습니다.</p></td>
</tr>
<tr class="even">
<td><p><em>Report</em></p></td>
<td><p>선택</p></td>
<td><p>System.String</p></td>
<td><p>cmdlet이 실행될 때 만들어진 로그 파일에 대한 파일 경로를 지정할 수 있도록 합니다. 예를 들면 다음과 같습니다. -Report &quot;C:\Logs\OUPermissions.html&quot;. 이 파일이 이미 있는 경우 cmdlet을 실행할 때 덮어쓰게 됩니다.</p></td>
</tr>
</tbody>
</table>


## 입력 형식

없음. **Test-CsOUPermission** cmdlet은 파이프라인된 입력을 허용하지 않습니다.

## 반환 형식

**Test-CsOUPermission** cmdlet은 Microsoft.Rtc.SyntheticTransactions.TaskOutput 개체의 인스턴스를 반환합니다.

## 참고 항목

#### 기타 리소스

[Grant-CsOUPermission](grant-csoupermission.md)  
[Revoke-CsOUPermission](revoke-csoupermission.md)

