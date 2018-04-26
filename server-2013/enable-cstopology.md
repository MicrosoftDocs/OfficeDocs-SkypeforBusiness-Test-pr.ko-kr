---
title: Enable-CsTopology
TOCTitle: Enable-CsTopology
ms:assetid: 5aedffa0-9ca1-4aec-b4ad-c3e409c0ffb2
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg398398(v=OCS.15)
ms:contentKeyID: 49303742
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Enable-CsTopology

 

_**마지막으로 수정된 항목:** 2015-03-09_

가장 최근에 게시된 Lync Server 토폴로지를 사용하도록 설정합니다. 토폴로지 내용을 변경한 후 변경 내용을 적용하려면 먼저 게시 및 활성화해야 합니다. 이 cmdlet은 Lync Server 2010에서 도입되었습니다.

## 구문

    Enable-CsTopology [-Confirm [<SwitchParameter>]] [-Force <SwitchParameter>] [-GlobalCatalog <Fqdn>] [-GlobalSettingsDomainController <Fqdn>] [-Report <String>] [-SkipPrepareCheck <$true | $false>] [-WhatIf [<SwitchParameter>]]

## 예제

## 예제 1

예제 1에 표시된 명령은 가장 최근 게시된 토폴로지를 활성화합니다.

    Enable-CsTopology

## 자세한 정보

Lync Server를 설치한 후에는 인프라를 변경해야 합니다. 예를 들어 새 사이트를 추가하거나 기존 등록자 풀을 삭제하거나 보관 서버를 추가해야 할 수 있습니다. 이러한 인프라 변경은 토폴로지 작성기를 사용하여 수행해야 합니다. 토폴로지 작성기에서 변경 내용을 적용한 후에는 이 도구를 사용하여 변경 내용을 게시하고 활성화할 수 있습니다. 후반의 이 두 단계는 매우 중요합니다. 토폴로지 작성기를 사용하여 원하는 만큼 수정할 수 있지만 이러한 수정 사항을 게시하고 새 토폴로지를 활성화할 때까지는 실제로 수정 사항이 적용되지 않고 인프라가 변경되지 않기 때문입니다.

변경 내용을 게시하면 새 정보(예: 새 사이트 또는 새 서버 역할)가 중앙 관리 저장소에 기록됩니다. 그러나 이러한 새 개체 또는 새로 수정한 개체가 토폴로지에 즉시 조인되는 것은 아닙니다. 이는 업데이트된 토폴로지가 활성화된 경우에만 실행됩니다. 토폴로지 작성기에서 게시 옵션을 선택한 경우 두 단계를 동시에 수행할 수 있습니다. 즉 변경 내용이 게시(중앙 관리 저장소에 기록)되는 동시에 새 토폴로지가 활성화됩니다.

그러나 변경 내용 게시와 토폴로지 활성화를 별도의 단계로 수행하고자 하는 경우도 있습니다. 이렇게 하면 새 개체를 토폴로지로 가져오기 전에 배포가 성공했는지 확인할 수 있습니다. 토폴로지 변경 내용을 별도로 게시한 후 활성화하려면 다음을 수행해야 합니다.

Topology Builder에서 수정된 토폴로지를 게시합니다. 이후의 제품 변경을 고려하여 항상 Topology Builder를 사용하여 게시하는 것이 좋습니다.

**Enable-CsTopology** cmdlet을 사용하여 게시된 변경 내용을 적용합니다.

간혹 Topology Builder 외부에서 변경된 내용을 사용하기 위해 **Enable-CsTopology** cmdlet을 호출해야 할 수도 있습니다. 예를 들어 CsKerberosAccountAssignment cmdlet을 사용하여 Kerberos 웹 인증을 수정한 후에 이 cmdlet을 실행해야 합니다.

이 cmdlet을 실행할 수 있는 사용자: 기본적으로 RTCUniversalServerAdmins 그룹의 구성원은 **Enable-CsTopology** cmdlet을 로컬로 실행할 수 있습니다. 그러나 설정 권한을 위임 받지 않은 경우에는 도메인 관리자여야 이 cmdlet을 실행할 수 있습니다. 실제로 **Enable-CsTopology** cmdlet을 사용할 수 있는 RTCUniversalServerAdmins 권한을 부여하려면 Lync Server 서비스를 실행하는 컴퓨터가 포함된 모든 Active Directory 컨테이너에 대해 **Grant-CsSetupPermission** cmdlet을 실행해야 합니다. 이 제한 사항은 토폴로지 작성기를 통해 토폴로지를 활성화하는 경우에도 적용됩니다. **Grant-CsSetupPermission** cmdlet을 통해 권한을 위임 받지 않은 경우에는 도메인 관리자만 토폴로지 작성기를 통해 토폴로지를 활성화할 수 있습니다.

또한 공유 폴더에 필요한 보안 권한을 설정하려면 Lync Server 파일 저장소가 만들어진 컴퓨터의 로컬 관리자여야 합니다. 파일 공유에 대한 모든 권한을 가진 경우 **Enable-CsTopology** cmdlet을 실행할 수도 있습니다. 그러면 cmdlet에서 공유 폴더를 만들고 공유 수준 보안 권한을 설정할 수 있습니다. 그러나 이 경우에는 이후에 로컬 관리자가 공유 수준 보안 권한을 추가해야 합니다.

설정 권한을 위임 받았는지 확인하려면 Lync Server 서비스를 실행하는 컴퓨터가 포함된 Active Directory 컨테이너에 대해 **Test-CsSetupPermission** cmdlet을 실행합니다.

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
<td><p><em>Confirm</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>명령을 실행하기 전에 확인 메시지를 표시합니다.</p></td>
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
<td><p>도메인에 있는 전역 카탈로그 서버의 FQDN(정규화된 도메인 이름)입니다. 사용자 도메인 계정을 가진 컴퓨터에서 <strong>Enable-CsTopology</strong> cmdlet을 실행하는 경우에는 이 매개 변수가 필요하지 않습니다.</p></td>
</tr>
<tr class="even">
<td><p><em>GlobalSettingsDomainController</em></p></td>
<td><p>선택</p></td>
<td><p>Microsoft.Rtc.Management.Deploy.Fqdn</p></td>
<td><p>전역 설정이 저장된 도메인 컨트롤러의 FQDN입니다. 전역 설정이 Active Directory 도메인 서비스의 시스템 컨테이너에 저장된 경우 이 매개 변수는 루트 도메인 컨트롤러를 가리켜야 합니다. 전역 설정이 구성 컨테이너에 저장된 경우 아무 도메인 컨트롤러나 사용할 수 있으며 이 매개 변수는 생략해도 됩니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>Report</em></p></td>
<td><p>선택</p></td>
<td><p>System.String</p></td>
<td><p>cmdlet이 실행될 때 만들어지는 로그 파일의 파일 경로를 지정하는 데 사용됩니다(예: -Report &quot;C:\Logs\Enable_Topology.html&quot;).</p></td>
</tr>
<tr class="even">
<td><p><em>SkipPrepareCheck</em></p></td>
<td><p>선택</p></td>
<td><p>System.Boolean</p></td>
<td><p>True($True)로 설정하면 <strong>Enable-CsTopology</strong> cmdlet에서 초기 준비 확인을 건너뜁니다.</p></td>
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

없음. **Enable-CsTopology** cmdlet은 파이프라인된 입력을 허용하지 않습니다.

## 반환 형식

없음. 대신 **Enable-CsTopology** cmdlet은 Microsoft.Rtc.Management.Deploy.Internal.DefaultTopology 개체의 인스턴스를 활성화합니다.

## 참고 항목

#### 기타 리소스

[Get-CsTopology](get-cstopology.md)  
[Grant-CsSetupPermission](grant-cssetuppermission.md)  
[Publish-CsTopology](publish-cstopology.md)  
[Test-CsSetupPermission](test-cssetuppermission.md)  
[Test-CsTopology](test-cstopology.md)

