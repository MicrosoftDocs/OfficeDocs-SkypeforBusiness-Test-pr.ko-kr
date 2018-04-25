---
title: 모임 참가 페이지 구성
TOCTitle: 모임 참가 페이지 구성
ms:assetid: 036c9d03-ad95-4d63-a3d8-6cae1a8ad530
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/JJ204635(v=OCS.15)
ms:contentKeyID: 49302645
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# 모임 참가 페이지 구성

 

_**마지막으로 수정된 항목:** 2015-03-09_

사용자가 모임 요청에서 모임 링크를 클릭하면 모임 참가 페이지에서 Lync 2013 클라이언트가 사용자의 컴퓨터에 이미 설치되어 있는지 확인합니다. 클라이언트가 이미 설치되어 있으면 클라이언트가 열리고 모임에 참가합니다. 클라이언트가 설치되어 있지 않은 경우 기본적으로 2013 버전의 Lync Web App이 열립니다.

사용자가 Office Communicator 2007 R2 또는 Lync 2010 Attendant를 사용하여 모임에 참가할 수 있도록 하려는 경우 모임 참가 페이지의 동작을 수정할 수 있습니다. 이러한 구성 옵션은 Lync Server 2013 제어판에서 제거되었지만 CsWebServiceConfiguration cmdlet을 사용하여 구성할 수 있습니다.

### 모임 참가 페이지 CsWebServiceConfiguration 매개 변수

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th>CsWebServiceConfiguration 매개 변수</th>
<th>설명</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>ShowJoinUsingLegacyClientLink</p></td>
<td><p>True로 설정하면 Lync 이외의 클라이언트 응용 프로그램을 사용하여 모임에 참가하는 사용자가 Office Communicator 2007 R2를 사용하여 모임에 참가할 수 있게 됩니다. 기본값은 False입니다.</p></td>
</tr>
<tr class="even">
<td><p>ShowAlternateJoinOptionsExpanded</p></td>
<td><p>True로 설정하면 Office Communicator 2007 R2 등 온라인 전화 회의 참가를 위한 대체 옵션이 자동으로 확장되어 사용자에게 표시됩니다. 기본값인 False로 설정하면 해당 옵션을 사용할 수는 있지만 사용자가 옵션 목록을 직접 표시해야 합니다.</p></td>
</tr>
</tbody>
</table>


## Lync Server 2013 관리 셸을 사용하여 모임 참가 페이지를 구성하려면

1.  Lync Server 2013 관리 셸을 시작합니다. **시작** , **모든 프로그램** , **Microsoft Lync Server 2013**, **Lync Server 관리 셸**을 차례로 클릭합니다.

2.  다음 cmdlet을 실행합니다.
    
        Get-CsWebServiceConfiguration
    
    이 cmdlet은 웹 서비스 구성 설정을 반환합니다.

3.  필요에 따라 매개 변수를 True 또는 False로 설정하여 다음 명령을 실행합니다. 이 cmdlet의 매개 변수에 대한 자세한 내용은 Lync Server 2013 관리 셸 설명서를 참고하세요.
    
        Set-CsWebServiceConfiguration -Identity global -ShowJoinUsingLegacyClientLink $True

