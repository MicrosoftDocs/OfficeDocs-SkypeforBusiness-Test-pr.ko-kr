---
title: Debug-CsLisConfiguration
TOCTitle: Debug-CsLisConfiguration
ms:assetid: 8cc718d6-52ec-4ff3-a77e-8d6df1725fb0
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg398710(v=OCS.15)
ms:contentKeyID: 49304327
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Debug-CsLisConfiguration

 

_**마지막으로 수정된 항목:** 2015-03-09_

E9-1-1(Enhanced 9-1-1) LIS(위치 정보 서비스) 구성을 XML 형식으로 표시합니다. 이 cmdlet은 Lync Server 2010에서 도입되었습니다.

## 구문

    Debug-CsLisConfiguration [-Force <SwitchParameter>] [-LocalStore <SwitchParameter>]

## 예제

## 예제 1

이 명령을 실행하면 전체 LIS 구성이 Lync Server 관리 셸 창에 XML 형식으로 표시됩니다. 기본적으로 **Debug-CsLisConfiguration** cmdlet의 출력은 한 줄에 표시되며, 데이터가 두 줄 이상 있음을 나타내는 줄임표(...)가 줄 끝에 포함됩니다. 따라서 이 예제에서는 Wrap 매개 변수가 지정된 **Format-Table** cmdlet에 출력을 파이프하여 표시 창에 맞게 줄바꿈된 형식으로 전체 출력을 표시합니다.

    Debug-CsLisConfiguration | Format-Table -Wrap

## 자세한 정보

Enterprise Voice E9-1-1 구현에 대한 LIS 구성은 압축 형식으로 저장됩니다. 이 cmdlet은 구성을 압축 해제하고 XML 형식으로 표시합니다. 이 작업을 통해 구성 관련 문제를 더 빠르게 디버그할 수 있습니다.

이 cmdlet은 중앙 관리 저장소에서 위치 정보를 검색합니다. 이와 같이 생성된 정보는 위치 데이터베이스에 저장됩니다. 그러나 **Publish-CsLisConfiguration** cmdlet을 통해 게시될 때까지는 중앙 관리 저장소로 이동되지 않습니다. 위치 정보가 게시되지 않았거나 **Unpublish-CsLisConfiguration** cmdlet을 통해 게시가 취소된 경우에는 **Debug-CsLisConfiguration** cmdlet에서 아무 항목도 반환하지 않습니다.

이 cmdlet을 실행할 수 있는 사용자: 기본적으로 RTCUniversalServerAdmins 그룹의 구성원은 **Debug-CsLisConfiguration** cmdlet을 로컬로 실행할 수 있습니다. 사용자가 직접 만든 사용자 지정 RBAC(역할 기반 액세스 제어) 역할을 포함하여 이 cmdlet이 할당된 모든 RBAC 역할의 목록을 반환하려면 Windows PowerShell 프롬프트에서 다음 명령을 실행합니다.

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Debug-CsLisConfiguration"}

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
<td><p>변경하기 전에 표시되는 확인 메시지를 표시하지 않습니다.</p></td>
</tr>
<tr class="even">
<td><p><em>LocalStore</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>도메인 컨트롤러를 지정하는 데 사용됩니다. 도메인 컨트롤러가 지정되지 않은 경우 사용 가능한 첫 번째 도메인 컨트롤러가 사용됩니다.</p></td>
</tr>
</tbody>
</table>


## 입력 형식

없음.

## 반환 형식

System.Management.Automation.PSCustomObject 유형의 개체를 반환합니다.

## 참고 항목

#### 기타 리소스

[Publish-CsLisConfiguration](publish-cslisconfiguration.md)  
[Unpublish-CsLisConfiguration](unpublish-cslisconfiguration.md)  
[Import-CsLisConfiguration](import-cslisconfiguration.md)  
[Export-CsLisConfiguration](export-cslisconfiguration.md)  
[Test-CsLisConfiguration](test-cslisconfiguration.md)

