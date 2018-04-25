---
title: Update-CsUserDatabase
TOCTitle: Update-CsUserDatabase
ms:assetid: 86ed4291-70cc-4c41-ab2a-e5f7546a0f1f
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg398682(v=OCS.15)
ms:contentKeyID: 49304275
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Update-CsUserDatabase

 

_**마지막으로 수정된 항목:** 2015-03-09_

백 엔드 데이터베이스에서 Active Directory와의 복제 상태를 강제로 지우도록 합니다. 이렇게 하면 데이터베이스가 Active Directory 도메인 서비스에 저장된 모든 사용자 관련 정보를 다시 읽습니다. 이 cmdlet은 Lync Server 2010에서 도입되었습니다.

## 구문

    Update-CsUserDatabase [-Force <SwitchParameter>] [-Fqdn <Fqdn>]

## 예제

## 예제 1

예제 1에 표시된 명령은 로컬 컴퓨터가 있는 풀에 대한 사용자 데이터베이스를 찾은 다음 해당 데이터베이스를 강제로 연결하여 Active Directory에서 전체 사용자 정보를 반환하게 합니다.

    Update-CsUserDatabase

## 예제 2

예제 2에서는 특정 사용자 데이터베이스가 강제로 Active Directory의 데이터를 다시 읽게 하는 방법을 보여 줍니다. 이 예제에서는 atl-cs-001.litwareinc.com 풀의 사용자 데이터베이스를 사용합니다.

    Update-CsUserDatabase -Fqdn atl-cs-001.litwareinc.com

## 자세한 정보

Lync Server 사용자 데이터베이스에는 연락처, 그룹 및 액세스 권한 등에 대한 세부적인 정보가 저장됩니다. 따라서 이 데이터베이스는 Active Directory에 저장된 정보와 데이터베이스의 내용을 정기적으로 동기화해야 합니다.

대부분 사용자 데이터베이스와 Active Directory 간의 자동 동기화를 통해 사용자 데이터베이스의 정보는 최신 상태로 유지됩니다. 그러나 문제가 발생하여 이 자동 동기화가 수행되지 못하는 경우가 있습니다. 이 경우 **Update-CsUserDatabase** cmdlet을 사용하여 사용자 데이터베이스에서 Active Directory에 저장된 사용자 정보를 다시 읽어 데이터베이스의 내용을 새로 고치도록 강제할 수 있습니다. 제품 업데이트에 User Replicator 서비스에 대한 변경 내용이 포함된 경우에도 이 cmdlet을 실행해야 할 수 있습니다.

이 cmdlet을 실행할 수 있는 사용자: 기본적으로 RTCUniversalUserAdmins 및 RTCUniversalServerAdmins 그룹의 구성원은 **Update-CsUserDatabase** cmdlet을 로컬로 실행할 수 있습니다. 사용자가 직접 만든 사용자 지정 RBAC(역할 기반 액세스 제어) 역할을 포함하여 이 cmdlet이 할당된 모든 RBAC 역할의 목록을 반환하려면 Windows PowerShell 프롬프트에서 다음 명령을 실행합니다.

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Update-CsUserDatabase"}

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
<td><p><em>Force</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>명령을 실행할 때 발생할 수 있는 심각하지 않은 오류 메시지를 표시하지 않습니다.</p></td>
</tr>
<tr class="even">
<td><p><em>Fqdn</em></p></td>
<td><p>선택</p></td>
<td><p>Microsoft.Rtc.Management.Deploy.Fqdn</p></td>
<td><p>사용자 데이터베이스를 호스트하는 컴퓨터의 FQDN(정규화된 도메인 이름)입니다. 이 매개 변수를 지정하지 않으면 <strong>Update-CsUserDatabase</strong> cmdlet은 로컬 컴퓨터가 속한 풀에 대해 사용자 데이터베이스를 업데이트합니다.</p></td>
</tr>
</tbody>
</table>


## 입력 형식

없음. **Update-CsUserDatabase** cmdlet은 파이프라인된 입력을 허용하지 않습니다.

## 반환 형식

없음. 대신 **Update-CsUserDatabase** cmdlet은 Microsoft.Rtc.Management.Xds.DisplayuserDatabase 개체의 인스턴스를 업데이트합니다.

## 참고 항목

#### 기타 리소스

[Get-CsUserDatabaseState](get-csuserdatabasestate.md)  
[Set-CsUserDatabaseState](set-csuserdatabasestate.md)

