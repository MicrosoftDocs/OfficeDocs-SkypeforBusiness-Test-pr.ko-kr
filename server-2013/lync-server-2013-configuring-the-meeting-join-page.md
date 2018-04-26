---
title: 'Lync Server 2013: 모임 참가 페이지 구성'
TOCTitle: 모임 참가 페이지 구성
ms:assetid: 45880423-47f4-49af-b825-cbd8e3fc1046
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/JJ204861(v=OCS.15)
ms:contentKeyID: 49303489
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Lync Server 2013에서 모임 참가 페이지 구성

 

_**마지막으로 수정된 항목:** 2015-03-09_

사용자가 모임 요청에서 모임 링크를 클릭하면 모임 참가 페이지가 사용자의 컴퓨터에 Lync 2013 클라이언트가 이미 설치되었는지 여부를 감지합니다. 클라이언트가 이미 설치된 경우 클라이언트가 열리고 모임에 참가합니다. 클라이언트가 설치되지 않았으면 기본적으로 Lync Web App의 2013 버전이 열립니다.

사용자가 Office Communicator 2007 R2 또는 Lync 2010 Attendant를 사용해서 모임에 참가하도록 허용하려면 모임 참가 페이지의 동작을 수정할 수 있습니다. 이러한 구성 옵션은 Lync Server 2013 제어판에서 제거되었지만 Set-CsWebServiceConfiguration cmdlet을 사용하여 구성할 수 있습니다.

### 모임 참가 페이지 Set-CsWebServiceConfiguration 매개 변수

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th>Set-CsWebServiceConfiguration 매개 변수</th>
<th>설명</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>ShowJoinUsingLegacyClientLink</p></td>
<td><p>True로 설정하면 Lync 이외의 클라이언트 응용 프로그램을 사용하여 모임에 참가하는 사용자에게 Office Communicator 2007 R2를 사용하여 모임에 참가할 수 있는 기회가 제공됩니다. 기본값은 False입니다.</p></td>
</tr>
<tr class="even">
<td><p>ShowAlternateJoinOptionsExpanded</p></td>
<td><p>True로 설정하면 Office Communicator 2007 R2 등 온라인 전화 회의 참가를 위한 대체 옵션이 자동으로 확장되어 사용자에게 표시됩니다. 기본값인 False로 설정하면 해당 옵션을 사용할 수는 있지만 사용자가 옵션 목록을 직접 표시해야 합니다.</p></td>
</tr>
</tbody>
</table>


## Lync Server 2013 관리 셸을 사용하여 모임 참가 페이지를 구성하려면

1.  Lync Server 2013 관리 셸을 시작합니다. **시작** , **모든 프로그램** , **Microsoft Lync Server 2013**, **Lync Server 관리 셸**을 차례로 클릭합니다.

2.  웹 서비스 구성 설정을 보려면 다음 cmdlet을 실행합니다.
    
        Get-CsWebServiceConfiguration

3.  필요에 따라 매개 변수를 True 또는 False로 설정하여 다음 명령을 실행합니다. 이 cmdlet의 매개 변수에 대한 자세한 내용은 Lync Server 2013 관리 셸 설명서의 [Set-CsWebServiceConfiguration](set-cswebserviceconfiguration.md)을 참고하세요.
    
        Set-CsWebServiceConfiguration -Identity global -ShowJoinUsingLegacyClientLink $True

## 참고 항목

#### 기타 리소스

[Set-CsWebServiceConfiguration](set-cswebserviceconfiguration.md)

