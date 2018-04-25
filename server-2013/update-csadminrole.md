---
title: Update-CsAdminRole
TOCTitle: Update-CsAdminRole
ms:assetid: 42cc9cc2-c408-4d0c-814a-6c6367cba834
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/JJ204851(v=OCS.15)
ms:contentKeyID: 49303458
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Update-CsAdminRole

 

_**마지막으로 수정된 항목:** 2015-03-09_

다른 데이터베이스 테이블에는 영향을 주지 않고 중앙 관리 데이터베이스에 저장된 RBAC(역할 기반 액세스 제어) 정의를 업데이트합니다. 이 cmdlet은 Lync Server 2013에서 도입되었습니다.

## 구문

    Update-CsAdminRole [-Confirm [<SwitchParameter>]] [-Force <SwitchParameter>] [-WhatIf [<SwitchParameter>]]

## 예제

## 예제 1

예제 1에 표시된 명령은 중앙 관리 데이터베이스에 저장된 RBAC 정의를 업데이트합니다.

    Update-CsAdminRole

## 자세한 정보

**Update-CsAdminRole** cmdlet을 사용하면 중앙 관리 데이터베이스에 저장된 RBAC 역할 정의를 업데이트할 수 있습니다. 이 cmdlet은 보통 중앙 관리 데이터베이스가 현재 Microsoft Lync Server 2010 풀에 있는 공존성/마이그레이션 시나리오에서 사용됩니다.

사용자가 직접 만든 사용자 지정 RBAC(역할 기반 액세스 제어) 역할을 포함하여 이 cmdlet이 할당된 모든 RBAC 역할의 목록을 반환하려면 Windows PowerShell 명령줄 인터페이스 프롬프트에서 다음 명령을 실행합니다.

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Update-CsAdminRole"}

**Lync Server 제어판:** **Update-CsAdminRole** cmdlet에 의해 수행되는 기능은 Lync Server 제어판에서는 사용할 수 없습니다.

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
<td><p><em>WhatIf</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>명령을 실제로 실행하지 않고도 명령이 실행될 경우 발생할 수 있는 현상을 설명합니다.</p></td>
</tr>
</tbody>
</table>


## 입력 형식

없음. **Update-CsAdminRole** cmdlet은 파이프라인된 입력을 허용하지 않습니다.

## 반환 형식

없음. **Update-CsAdminRole** cmdlet은 데이터나 개체를 반환하지 않습니다.

