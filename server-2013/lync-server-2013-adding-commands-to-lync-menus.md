---
title: Lync 메뉴에 명령 추가
TOCTitle: Lync 메뉴에 명령 추가
ms:assetid: a8443bc2-e234-4022-870a-00700f38b1ea
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg412788(v=OCS.15)
ms:contentKeyID: 52056912
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Lync 메뉴에 명령 추가

 

_**마지막으로 수정된 항목:** 2015-03-09_

Lync 2013 메뉴에 사용자 지정 명령을 추가하고 현재 사용자 및 선택한 대화 상대의 SIP URI(Uniform Resource Identifier)를 사용자 지정 명령이 시작되는 응용 프로그램에 전달할 수 있습니다.

추가할 수 있는 사용자 지정 명령은 다음 메뉴 중 하나 이상에 표시될 수 있습니다.

  - Lync 주 창에 있는 메뉴 표시줄의 도구 메뉴

  - 대화 상대 목록의 대화 상대에 대한 바로 가기 메뉴

  - 대화 창의 다른 옵션 메뉴

  - 대화 창의 참가자 목록에 나열된 사용자에 대한 바로 가기 메뉴

  - 대화 상대 카드의 옵션 메뉴

다음 중 하나를 수행하는 두 가지 유형의 응용 프로그램에 대한 사용자 지정 명령을 정의할 수 있습니다.

  - 현재 사용자에게만 적용되고 로컬 컴퓨터에서 시작됩니다.

  - 온라인 공동 작업 프로그램 등과 같은 추가 사용자를 포함하고 각 사용자의 컴퓨터에서 시작되어야 합니다.

다음과 같은 방법으로 사용자 지정 명령을 호출할 수 있습니다.

  - 한 명 이상의 사용자를 선택하고 사용자 지정 명령을 선택합니다.

  - 두 사용자 간 대화 또는 단체 간 대화를 시작하고 사용자 지정 명령을 선택합니다.

## 사용자 지정 명령을 추가하려면

다음 표의 레지스트리 설정을 사용하여 메뉴에 명령을 추가합니다. 이 항목은 다음 위치의 레지스트리에 보관됩니다.

HKEY\_LOCAL\_MACHINE\\SOFTWARE\\Microsoft\\Office\\15.0\\Lync\\CustomCommands

### 사용자 지정 명령 레지스트리 항목

<table>
<colgroup>
<col style="width: 33%" />
<col style="width: 33%" />
<col style="width: 33%" />
</colgroup>
<thead>
<tr class="header">
<th>이름</th>
<th>유형</th>
<th>데이터</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>이름</p></td>
<td><p>REG_SZ</p></td>
<td><p>메뉴에 표시되는 응용 프로그램 이름입니다.</p></td>
</tr>
<tr class="even">
<td><p>ApplicationType</p></td>
<td><p>DWORD</p></td>
<td><p>0 = 실행 파일(기본값)</p>


> [!NOTE]
> ApplicationInstallPath가 필요합니다.



<p>1 = 프로토콜</p></td>
</tr>
<tr class="odd">
<td><p>ApplicationInstallPath</p></td>
<td><p>REG_SZ</p></td>
<td><p>실행 파일의 전체 경로.</p>


> [!NOTE]
> ApplicationType이 0(실행 파일)일 경우 지정해야 합니다.


</td>
</tr>
<tr class="even">
<td><p>Path</p></td>
<td><p>REG_SZ</p></td>
<td><p><em>%user-id%</em> 및 <em>%contact-id%</em> 등 기본 매개 변수를 비롯한 매개 변수와 함께 시작될 전체 경로</p></td>
</tr>
<tr class="odd">
<td><p>SessionType</p></td>
<td><p>DWORD</p></td>
<td><p>0 = 로컬 세션. 응용 프로그램이 로컬 컴퓨터에서 시작됩니다.</p>
<p>1 = 양방향 세션(기본값). Lync 2013에서 응용 프로그램을 로컬로 시작한 다음 다른 사용자에게 바탕 화면 알림을 보냅니다. 상대방이 알림을 클릭하여 응용 프로그램을 자신의 컴퓨터에서 시작합니다.</p>
<p>2 = 단체 세션. Lync 2013에서 응용 프로그램을 로컬로 시작한 다음 다른 사용자에게 바탕 화면 알림을 보냅니다. 상대방이 알림을 클릭하여 지정된 응용 프로그램을 자신의 컴퓨터에서 시작합니다.</p></td>
</tr>
<tr class="even">
<td><p>ExtensibleMenu</p></td>
<td><p>REG_SZ</p></td>
<td><p>이 명령이 표시될 메뉴 목록입니다. 각 메뉴는 세미콜론으로 구분됩니다. 가능한 값은 다음과 같습니다.</p>
<p>MainWindowActions</p>
<p>MainWindowRightClick</p>
<p>ConversationWindowActions</p>
<p>ConversationWindowRightClick</p>
<p>ContactCardMenu</p>
<p>ExtensibleMenu가 정의되어 있지 않으면 MainWindowRightClick 및 ConversationWindowActions가 기본값으로 사용됩니다.</p></td>
</tr>
</tbody>
</table>


예를 들어 다음 레지스트리 편집기(.REG) 파일에는 Contoso Sales Contact Manager 메뉴 항목을 대화 창의 동작 메뉴에 추가한 결과가 표시됩니다.

    Windows Registry Editor Version 5.00
    [HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Office\15.0\Lync\CustomCommands\{1F9F07C6-7E0B-462B-AAD7-98C6DBEA8F69}]
    "Name"="Contoso Sales Contact Manager"
    "HelpMessage"="The Contoso Sales Contact Manager is not installed. Contact the Help Desk for more information."
    "ApplicationType"=dword:00000000
    "ApplicationInstallPath"="C:\\cscm.exe"
    "Path"="C:\\cscm.exe %user-id% %contact-id%"
    "SessionType"=dword:00000001
    "ExtensibleMenu"="ConversationWindowActions;MainWindowRightClick"

## 사용자 지정 명령에 액세스하려면

사용자 지정 명령을 추가한 후 이 명령에 액세스하려면 정의한 ExtensibleMenu 값에 따라 다음 중 하나를 수행합니다.

  - **MainWindowActions**   Lync 주 창에서 **도구**를 클릭한 다음 사용자 지정 명령을 클릭합니다.

  - MainWindowRightClick   Lync 주 창에서 대화 상대를 마우스 오른쪽 단추로 클릭한 다음 사용자 지정 명령을 클릭합니다.

  - **ConversationWindowActions**   대화 창에서 **다른 옵션** 아이콘을 클릭한 다음 사용자 지정 명령을 클릭합니다.

  - **ConversationWindowRightClick**   대화 창에서 대화 상대 이름을 마우스 오른쪽 단추로 클릭한 다음 사용자 지정 명령을 클릭합니다.

  - **ContactCardMenu**   개인의 대화 상대 카드에서 옵션 아이콘을 클릭한 다음 사용자 지정 명령을 클릭합니다.

