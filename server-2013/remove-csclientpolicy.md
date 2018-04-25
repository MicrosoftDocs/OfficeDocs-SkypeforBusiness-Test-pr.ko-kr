---
title: Remove-CsClientPolicy
TOCTitle: Remove-CsClientPolicy
ms:assetid: 2beb1557-8397-493e-be87-910ce01ba8f5
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg425772(v=OCS.15)
ms:contentKeyID: 49303151
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Remove-CsClientPolicy

 

_**마지막으로 수정된 항목:** 2015-03-09_

기존 클라이언트 정책을 제거합니다. 특히 클라이언트 정책은 사용자가 사용할 수 있는 Lync 기능을 결정하는 데 도움이 됩니다. 예를 들어 일부 사용자에게는 파일 전송 권한을 부여하고 다른 사용자에 대해서는 이 권한을 거부할 수 있습니다. 이 cmdlet은 Lync Server 2010에서 도입되었습니다.

## 구문

    Remove-CsClientPolicy -Identity <XdsIdentity> [-Confirm [<SwitchParameter>]] [-Force <SwitchParameter>] [-WhatIf [<SwitchParameter>]]

## 예제

## 예제 1

예제 1에서는 **Remove-CsClientPolicy** cmdlet을 사용하여 Identity가 SalesPolicy인 클라이언트 정책을 삭제합니다.

    Remove-CsClientPolicy -Identity SalesPolicy

## 예제 2

예제 2에서는 **Get-CsClientPolicy** cmdlet 및 **Remove-CsClientPolicy** cmdlet을 사용하여 사용자별 범위에서 구성된 모든 클라이언트 정책을 삭제합니다. 이 명령은 **Get-CsClientPolicy** cmdlet 및 Filter 매개 변수를 사용하여 사용자별 범위에서 구성된 모든 클라이언트 정책 컬렉션을 반환합니다. 필터 값 "tag:\*"는 Identity가 문자열 값 "tag:"으로 시작하는 클라이언트 정책에 대한 데이터만 검색하게 제한하도록 **Get-CsClientPolicy** cmdlet에 지시합니다. 그런 다음 필터링된 컬렉션은 컬렉션의 각 정책을 제거하는 **Remove-CsClientPolicy** cmdlet에 파이프됩니다.

    Get-CsClientPolicy -Filter "tag:*" | Remove-CsClientPolicy

## 예제 3

예제 3에서는 EnableAppearOffline 속성이 True로 설정된 모든 클라이언트 정책을 삭제합니다. 이 작업을 수행하기 위해 먼저 추가 매개 변수 없이 **Get-CsClientPolicy** cmdlet을 호출합니다. 그러면 조직에서 사용하도록 구성된 모든 클라이언트 정책 컬렉션이 반환됩니다. 이 컬렉션은 EnableAppearOffline 속성이 True와 같은 정책만 선택하는 **Where-Object** cmdlet에 파이프됩니다. 그런 다음 필터링된 컬렉션은 컬렉션의 각 정책을 삭제하는 **Remove-CsClientPolicy** cmdlet에 파이프됩니다.

    Get-CsClientPolicy | Where-Object {$_.EnableAppearOffline -eq $True} | Remove-CsClientPolicy

## 자세한 정보

Lync Server에서는 이전 버전의 제품에서 사용된 그룹 정책 설정 대신 클라이언트 정책을 사용합니다. Microsoft Office Communicator 2007 및 Microsoft Office Communicator 2007 R2에서는 Communicator 및 기타 클라이언트로 사용자가 수행할 수 있는 작업을 결정할 때 그룹 정책을 사용했습니다. 예를 들어 사용자가 메신저 대화 세션의 대화 내용을 저장할 수 있는지 여부, Microsoft Outlook의 정보를 상태 정보로 통합할지 여부, 사용자가 메신저 대화에 이모티콘이나 서식 있는 텍스트를 포함할 수 있는지 여부 등을 결정하는 그룹 정책 설정이 있었습니다.

그룹 정책은 유용하지만 Lync Server에 적용할 때 몇 가지 기술적인 제한이 있습니다. 우선, 그룹 정책은 도메인별 또는 OU(조직 구성 단위)별로 적용하도록 설계되었기 때문에 보다 선별적인 사용자 그룹(예: 특정 부서에서 근무하는 모든 사용자나 특정 직책의 모든 사용자)에 적용하기 어렵습니다. 또한 그룹 정책은 도메인에 로그온하거나 컴퓨터를 사용하여 로그온한 사용자에게만 적용됩니다. 인터넷을 통해 Lync Server에 액세스하거나 휴대폰을 사용하여 시스템에 액세스한 사용자에게는 적용되지 않습니다. 따라서 로그온하는 데 사용한 장치 및 로그온한 위치에 따라 동일한 사용자에게 다른 환경이 제공될 수 있습니다.

이러한 불일치를 해결하기 위해 Lync Server에서는 그룹 정책 대신 클라이언트 정책을 사용합니다. 클라이언트 정책은 로그온한 위치 및 로그온하는 데 사용한 장치 유형에 관계없이 사용자가 시스템에 액세스할 때마다 적용됩니다. 또한 다른 Lync Server 정책과 마찬가지로 클라이언트 정책을 언제든지 선택한 사용자 그룹으로 지정할 수 있을 뿐만 아니라 단일 사용자에게 할당되는 사용자 지정 정책을 만들 수도 있습니다.

클라이언트 정책은 전역, 사이트 및 사용자별 범위에서 구성할 수 있습니다. 사이트 또는 사용자별 범위에서 구성된 정책은 나중에 **Remove-CsClientPolicy** cmdlet을 사용하여 삭제할 수 있습니다. 전역 정책에 대해 **Remove-CsClientPolicy** cmdlet을 실행할 수도 있습니다. 전역 정책은 삭제할 수 없으므로 이 경우에는 전역 정책이 제거되지 않습니다. 그러나 전역 정책의 모든 속성이 기본값으로 다시 설정됩니다.

이 cmdlet을 실행할 수 있는 사용자: 기본적으로 RTCUniversalServerAdmins 그룹의 구성원은 **Remove-CsClientPolicy** cmdlet을 로컬로 실행할 수 있습니다. 사용자가 직접 만든 사용자 지정 RBAC(역할 기반 액세스 제어) 역할을 포함하여 이 cmdlet이 할당된 모든 RBAC 역할의 목록을 반환하려면 Windows PowerShell 프롬프트에서 다음 명령을 실행합니다.

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Remove-CsClientPolicy"}

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
<td><p><em>Identity</em></p></td>
<td><p>필수</p></td>
<td><p>Microsoft.Rtc.Management.Xds.XdsIdentity</p></td>
<td><p>제거할 클라이언트 정책의 고유 식별자입니다. 전역 정책을 &quot;제거&quot;하려면 -Identity global 구문을 사용합니다. 전역 정책은 실제로 제거할 수 없습니다. 대신 해당 정책의 모든 속성이 기본값으로 다시 설정됩니다. 사이트 정책을 제거하려면 -Identity &quot;site:Redmond&quot;와 유사한 구문을 사용합니다. 사용자별 정책을 제거하려면 -Identity &quot;SalesDepartmentPolicy&quot;와 유사한 구문을 사용합니다. 정책 ID를 지정할 때는 와일드카드를 사용할 수 없습니다.</p></td>
</tr>
<tr class="even">
<td><p><em>Confirm</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>명령을 실행하기 전에 확인 메시지를 표시합니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>Force</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>이 매개 변수가 있으면 현재 하나 이상의 사용자에게 할당된 경우에도 정책이 자동으로 제거됩니다. 이 매개 변수가 없으면 <strong>Remove-CsClientPolicy</strong> cmdlet에서 하나 이상의 사용자에 할당된 사용자별 정책을 자동으로 제거하지 않습니다. 대신 정책을 제거할 것인지 확인하는 확인 메시지가 표시됩니다. Y 키를 눌러 예라고 응답해야 명령이 계속되고 정책이 제거됩니다.</p></td>
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

Microsoft.Rtc.Management.WritableConfig.Policy.Client.ClientPolicy 개체입니다. **Remove-CsClientPolicy** cmdlet은 클라이언트 정책 개체의 파이프라인된 인스턴스를 허용합니다.

## 반환 형식

**Remove-CsClientPolicy** cmdlet은 값을 반환하지 않습니다. 대신 이 cmdlet은 Microsoft.Rtc.Management.WritableConfig.Policy.Client.ClientPolicy 개체의 인스턴스를 삭제합니다.

## 참고 항목

#### 기타 리소스

[Get-CsClientPolicy](get-csclientpolicy.md)  
[Grant-CsClientPolicy](grant-csclientpolicy.md)  
[New-CsClientPolicy](new-csclientpolicy.md)  
[Set-CsClientPolicy](set-csclientpolicy.md)

