---
title: Test-CsSetupPermission
TOCTitle: Test-CsSetupPermission
ms:assetid: 604ccb97-278a-4588-9ab8-991aaabae275
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg398428(v=OCS.15)
ms:contentKeyID: 49303795
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Test-CsSetupPermission

 

_**마지막으로 수정된 항목:** 2015-03-09_

Lync Server 또는 해당 구성 요소 중 하나를 설치하는 데 필요한 권한이 지정한 Active Directory 컨테이너에 구성되어 있는지 확인합니다. 이 cmdlet은 Lync Server 2010에서 도입되었습니다.

## 구문

    Test-CsSetupPermission -ComputerOU <String> [-Domain <Fqdn>] [-DomainController <Fqdn>] [-GlobalCatalog <Fqdn>] [-Report <String>]

## 예제

## 예제 1

예제 1에 표시된 명령은 필요한 설치 권한이 litwareinc.com 도메인의 CsServers OU에 적용되었는지 확인합니다.

    Test-CsSetupPermission -ComputerOU "ou=CsServers,dc=litwareinc,dc=com"

## 자세한 정보

Lync Server를 설치할 때 수행되는 도메인 준비에서는 RTCUniversalServerAdmins 그룹의 구성원이 **Enable-CsTopology** cmdlet을 실행할 수 있는 권한을 자동으로 추가하지 않습니다. 이는 기본적으로 토폴로지를 사용하려면 도메인 관리자여야 함을 의미합니다. RTCUniversalServerAdmins 그룹의 구성원에게 토폴로지를 사용할 수 있는 권한을 부여하려면 **Grant-CsSetupPermissions** cmdlet을 실행해야 합니다. 또한 Lync Server를 실행하는 컴퓨터가 속해 있는 각 Active Directory 컨테이너에 대해 이 cmdlet을 실행해야 합니다.

**Test-CsSetupPermission** cmdlet을 사용하면 필수 권한이 지정한 Active Directory 컨테이너(Lync Server를 실행하는 컴퓨터를 호스트하는 컨테이너)에 추가되었는지 여부를 확인할 수 있습니다. **Test-CsSetupPermission** cmdlet은 올바른 권한이 적용된 경우 True를 반환하고, 올바른 권한이 적용되지 않은 경우 False를 반환합니다. cmdlet이 False를 반환한 경우 Active Directory 컨테이너에 필요한 변경을 수행하려면 **Grant-CsSetupPermission** cmdlet을 실행해야 합니다.

이 cmdlet을 실행할 수 있는 사용자: 사용자가 직접 만든 사용자 지정 RBAC(역할 기반 액세스 제어) 역할을 포함하여 이 cmdlet이 할당된 모든 RBAC 역할의 목록을 반환하려면 Windows PowerShell 프롬프트에서 다음 명령을 실행합니다.

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Test-CsSetupPermission"}

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
<td><p><em>ComputerOU</em></p></td>
<td><p>필수</p></td>
<td><p>System.String</p></td>
<td><p>Lync Server를 실행하는 컴퓨터에 대한 계정이 있는 OU(조직 구성 단위)의 고유 이름입니다(예: &quot;ou=CsServers,dc=litwareinc,dc=com&quot;).</p></td>
</tr>
<tr class="even">
<td><p><em>Domain</em></p></td>
<td><p>선택</p></td>
<td><p>Microsoft.Rtc.Management.Deploy.Fqdn</p></td>
<td><p>확인할 OU가 있는 도메인의 이름입니다. 이 매개 변수가 포함되지 않은 경우 <strong>Test-CsSetupPermission</strong> cmdlet은 현재 도메인에서 OU를 찾습니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>DomainController</em></p></td>
<td><p>선택</p></td>
<td><p>Microsoft.Rtc.Management.Deploy.Fqdn</p></td>
<td><p>도메인에 있는 도메인 컨트롤러의 FQDN(정규화된 도메인 이름)입니다. 사용자 도메인 계정을 가진 컴퓨터에서 <strong>Test-CsSetupPermission</strong> cmdlet을 실행하는 경우에는 이 매개 변수가 필요하지 않습니다.</p></td>
</tr>
<tr class="even">
<td><p><em>GlobalCatalog</em></p></td>
<td><p>선택</p></td>
<td><p>Microsoft.Rtc.Management.Deploy.Fqdn</p></td>
<td><p>도메인에 있는 전역 카탈로그 서버의 FQDN입니다. 사용자 도메인 계정을 가진 컴퓨터에서 <strong>Test-CsSetupPermission</strong> cmdlet을 실행하는 경우에는 이 매개 변수가 필요하지 않습니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>Report</em></p></td>
<td><p>선택</p></td>
<td><p>System.String</p></td>
<td><p>cmdlet이 실행될 때 자세한 작업을 화면에 보고합니다.</p></td>
</tr>
</tbody>
</table>


## 입력 형식

없음. **Test-CsSetupPermission** cmdlet은 파이프라인된 입력을 허용하지 않습니다.

## 반환 형식

**Test-CsSetupPermission** cmdlet은 Microsoft.Rtc.SyntheticTransactions.TaskOutput 개체의 인스턴스를 반환합니다.

## 참고 항목

#### 기타 리소스

[Grant-CsSetupPermission](grant-cssetuppermission.md)  
[Revoke-CsSetupPermission](revoke-cssetuppermission.md)

