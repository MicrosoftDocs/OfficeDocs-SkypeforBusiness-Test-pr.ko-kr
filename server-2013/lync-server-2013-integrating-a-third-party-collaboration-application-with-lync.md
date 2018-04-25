---
title: Lync와 타사 공동 작업 응용 프로그램 통합
TOCTitle: Lync와 타사 공동 작업 응용 프로그램 통합
ms:assetid: 00b9312c-b0c8-4f79-8b76-05b2d820e197
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg398068(v=OCS.15)
ms:contentKeyID: 52056774
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Lync와 타사 공동 작업 응용 프로그램 통합

 

_**마지막으로 수정된 항목:** 2015-03-09_

타사 온라인 공동 작업 응용 프로그램에 대한 정보를 레지스트리에 추가하여 Lync 2013을 해당 응용 프로그램과 통합할 수 있습니다. Lync 2013을 사용하면 내부 서버, 인터넷 기반 서비스 또는 둘 모두에서 호스트되는 데이터 회의 세션을 시작할 수 있습니다. 대화 상대 목록 또는 기존의 인스턴트 메시징, 음성 및 화상 세션에서 공동 작업(또는 데이터 회의) 세션을 시작할 수 있습니다. Lync 2013은 응용 프로그램을 시작하기 위한 용도로만 사용됩니다. 온라인 공동 작업 세션이 시작된 후에도 기존의 Lync 2013 대화는 활성 상태로 유지됩니다.

다음 섹션에서는 Lync 2013을 인터넷 기반 공동 작업 응용 프로그램 및 서버 기반 공동 작업 응용 프로그램과 통합하는 방법에 대해 설명합니다.

## Lync 2013에 인터넷 기반 공동 작업 응용 프로그램 통합

타사 공동 작업 응용 프로그램을 통합하는 일반적인 단계는 다음과 같습니다.

1.  응용 프로그램에 대한 정보를 레지스트리에 추가합니다.

2.  이끌이가 Lync 2013에 로그인한 다음 데이터를 공유하고 공동 작업을 할 대화 상대를 선택합니다. 또는 이끌이가 대화 중에 데이터 회의를 추가할 수도 있습니다.

3.  Lync 2013에서 레지스트리를 읽고 공동 작업 응용 프로그램을 시작한 다음 선택된 참가자에게 사용자 지정 SIP 메시지(appINVITE)를 보냅니다.

4.  참가자가 초대를 수락하면 각 참가자의 컴퓨터에서 공동 작업 응용 프로그램이 시작됩니다. Lync 2013에서는 사용할 공동 작업 응용 프로그램을 레지스트리를 통해 결정한 다음 appINVITE 메시지에 포함된 매개 변수를 사용하여 해당 응용 프로그램을 시작합니다.

아래 표에는 인터넷 기반 공동 작업 응용 프로그램을 Lync 2013에 통합하는 데 필요한 레지스트리 항목에 대한 설명이 나와 있습니다. 이러한 항목은 레지스트리에서 다음 위치에 있습니다.

  - HKEY\_LOCAL\_MACHINE\\Software\\Microsoft\\Office\\15.0\\Lync\\SessionManager\\Apps\\Parameters

### 인터넷 기반 공동 작업 응용 프로그램의 레지스트리 항목

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
<td><p>Lync 2013 메뉴의 응용 프로그램 이름입니다.</p></td>
</tr>
<tr class="even">
<td><p>SmallIcon</p></td>
<td><p>REG_SZ</p></td>
<td><p>16 x 16픽셀 아이콘(BMP 또는 PNG)의 경로입니다.</p></td>
</tr>
<tr class="odd">
<td><p>Path</p></td>
<td><p>REG_SZ</p></td>
<td><p>온라인 공동 작업 응용 프로그램을 시작할 참가자의 경로입니다.</p></td>
</tr>
<tr class="even">
<td><p>OriginatorPath</p></td>
<td><p>REG_SZ</p></td>
<td><p>온라인 공동 작업 응용 프로그램을 시작할 이끌이의 경로입니다. 이 경로에는 Parameters 하위 키에 정의된 사용자 지정 매개 변수가 하나 이상 포함될 수 있습니다. 예를 들면 <code>https://meetserv.adatum.com/cc/%param1%/join?id=%param2%&amp;role=present&amp;pw=%param3%</code>와 같습니다.</p></td>
</tr>
<tr class="odd">
<td><p>SessionType</p></td>
<td><p>DWORD</p></td>
<td><p>0 = 로컬 세션. 응용 프로그램이 로컬 컴퓨터에서 시작됩니다.</p>
<p>1 = 두 그룹 세션(기본값). Lync 2013에서 응용 프로그램을 로컬로 시작한 후에 다른 사용자에게 시스템 알림을 보냅니다. 다른 사용자는 알림을 클릭하여 지정된 응용 프로그램을 자신의 컴퓨터에서 시작합니다.</p>
<p>2 = 단체 세션. Lync 2013에서 응용 프로그램을 로컬로 시작한 다음 각자의 컴퓨터에서 지정된 응용 프로그램을 시작하도록 메시지를 표시하는 시스템 알림을 다른 사용자에게 보냅니다.</p></td>
</tr>
<tr class="even">
<td><p>ExensibleMenu</p></td>
<td><p>REG_SZ</p></td>
<td><p>이 명령이 표시될 메뉴 목록입니다. 각 메뉴는 세미콜론으로 구분됩니다. 가능한 값은 다음과 같습니다.</p>
<ul>
<li><p>MainWindowActions</p></li>
<li><p>MainWindowRightClick</p></li>
<li><p>ConversationWindowActions</p></li>
<li><p>ConversationWindowButton</p></li>
<li><p>ConversationWindowRightClick</p></li>
</ul>
<p>ExtensibleMenu가 정의되어 있지 않으면 MainWindowRightClick 및 ConversationWindowActions가 기본값으로 사용됩니다.</p></td>
</tr>
</tbody>
</table>


다음 표에 매개 변수의 레지스트리 항목에 대한 설명이 나와 있습니다. 이러한 항목은 HKEY\_CURRENT\_USER\\Software\\Microsoft\\Office\\15.0\\Lync\\SessionManager\\Apps\\Parameters에 있습니다.

### 인터넷 기반 공동 작업 응용 프로그램의 레지스트리 항목

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
<td><p>Param1</p></td>
<td><p>REG_SZ</p></td>
<td><p>OriginatorPath 레지스트리 키에 사용자별 값을 추가하기 위해 토큰 형식(<code>%Parm1%</code>)으로 사용됩니다.</p></td>
</tr>
<tr class="even">
<td><p>Param2</p></td>
<td><p>REG_SZ</p></td>
<td><p>Param1을 참조하십시오.</p></td>
</tr>
<tr class="odd">
<td><p>Param3</p></td>
<td><p>REG_SZ</p></td>
<td><p>Param1을 참조하십시오.</p></td>
</tr>
</tbody>
</table>


다음 레지스트리 설정 예제에서는 Lync 2013에 ADatum Collaboration Client를 통합합니다.

    Windows Registry Editor Version 5.00
    [HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Office\15.0\Lync\SessionManager]
    [HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Office\15.0\Lync\SessionManager\Apps]
    [HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Office\15.0\Lync\SessionManager\Apps\{C3F6E17A-855F-44a0-B90D-C0B92D38E5F1}]
    "Path"="https://meetingservice.adatum.com/cc/%param1%/meet/%param2%"
    "OriginatorPath"="https://meetserv.adatum.com/cc/%param1%/join?id=%param2%&role=present&pw=%param3%"
    "SessionType"=dword:00000002
    "ApplicationType"=dword:00000001
    "LiveServerIntegration"=dword:00000000
    "Name"="ADatum Online Collaboration Service"
    "Extensiblemenu"="MainWindowActions;MainWindowRightClick;ConversationWindowActions;ConversationWindowRightClick"
    
    [HKEY_CURRENT_USER\Software\Microsoft\Office\15.0\Lync\SessionManager]
    [HKEY_CURRENT_USER\Software\Microsoft\Office\15.0\Lync\SessionManager\Apps]
    [HKEY_CURRENT_USER\Software\Microsoft\Office\15.0\Lync\SessionManager\Apps\Parameters]
    [HKEY_CURRENT_USER\Software\Microsoft\Office\15.0\Lync\SessionManager\Apps\Parameters\{C3F6E17A-855F-44a0-B90D-C0B92D38E5F1}]
    "Param1"="meetserv"
    "Param2"="admin"
    "Param3"="abcdefg123"

## Lync 2013에 서버 기반 공동 작업 응용 프로그램 통합

Lync 2013 내에서 서버 기반 공동 작업 응용 프로그램을 시작하기 위한 명령을 추가하는 설정은 이전 섹션인 Lync 2013에 인터넷 기반 공동 작업 응용 프로그램 통합에서 설명한 설정과 비슷합니다. 그러나 이번에는 OriginatorPath가 필요하지 않으며 일부 값이 다릅니다. 레지스트리 항목은 다음 위치에 있습니다.

  - HKEY\_LOCAL\_MACHINE\\Software\\Microsoft\\Office\\15.0\\Lync\\SessionManager\\Apps\\Parameters

### 서버 기반 공동 작업 응용 프로그램의 레지스트리 항목

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
<td><p>값 = 1. 응용 프로그램 유형을 프로토콜로 설정합니다. 이 경우에는 다른 값이 적용되지 않습니다. 값이 없는 경우 ApplicationType이 0(실행 파일)으로 설정됩니다.</p></td>
</tr>
<tr class="odd">
<td><p>Path</p></td>
<td><p>REG_SZ</p></td>
<td><p>공동 작업 응용 프로그램을 시작하는 데 사용되는 프로토콜입니다. Live Meeting 2007의 경우 Path의 값은 <code>meet:%conf-uri%</code>로 설정됩니다.</p></td>
</tr>
<tr class="even">
<td><p>SessionType</p></td>
<td><p>DWORD</p></td>
<td><p>0 = 로컬 세션. 응용 프로그램이 로컬 컴퓨터에서 시작됩니다.</p>
<p>1 = 두 그룹 세션(기본값). Lync 2013에서 응용 프로그램을 로컬로 시작한 후에 다른 사용자에게 시스템 알림을 보냅니다. 다른 사용자는 알림을 클릭하여 지정된 응용 프로그램을 자신의 컴퓨터에서 시작합니다.</p>
<p>2 = 단체 세션. Lync 2013에서 응용 프로그램을 로컬로 시작한 다음 각자의 컴퓨터에서 지정된 응용 프로그램을 시작하도록 메시지를 표시하는 시스템 알림을 다른 사용자에게 보냅니다.</p></td>
</tr>
<tr class="odd">
<td><p>MCUType</p></td>
<td><p>REG_SZ</p></td>
<td><p>DATA = 서버 유형입니다.</p></td>
</tr>
<tr class="even">
<td><p>ExtensibleMenu</p></td>
<td><p>REG_SZ</p></td>
<td><p>이 명령이 표시될 메뉴 목록입니다. 각 메뉴는 세미콜론으로 구분됩니다. 가능한 값은 다음과 같습니다.</p>
<ul>
<li><p>MainWindowActions</p></li>
<li><p>MainWindowRightClick</p></li>
<li><p>ConversationWindowActions</p></li>
<li><p>ConversationWindowButton</p></li>
<li><p>ConversationWindowRightClick</p></li>
</ul>
<p>ExtensibleMenu가 정의되어 있지 않으면 MainWindowRightClick 및 ConversationWindowActions가 기본값으로 사용됩니다.</p></td>
</tr>
</tbody>
</table>


다음 예제에서는 Lync 2013에서 ADatum Collaboration Client를 시작하는 명령을 추가합니다.

    Windows Registry Editor Version 5.00
    [HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Office\15.0\Lync\SessionManager]
    [HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Office\15.0\Lync\SessionManager\Apps]
    [HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Office\15.0\Lync\SessionManager\Apps\{27877e66-615c-4582-ab88-0cb2ca05d951}]
    "Path"="meet:%conf-uri%"
    "SessionType"=dword:00000002
    "LiveServerIntegration"=dword:00000001
    "ApplicationType"=dword:00000001
    "Name"="ADatum Collaboration Client"
    "MCUType"="Data"
    "Extensiblemenu"="MainWindowActions;MainWindowRightClick;ConversationWindowActions;ConversationWindowRightClick"

