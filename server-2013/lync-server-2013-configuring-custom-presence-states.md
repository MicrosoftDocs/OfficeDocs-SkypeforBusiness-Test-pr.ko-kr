---
title: 사용자 지정 현재 상태 구성
TOCTitle: 사용자 지정 현재 상태 구성
ms:assetid: e17364a8-8b93-45fc-a614-c80e45435d42
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg398997(v=OCS.15)
ms:contentKeyID: 52056974
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# 사용자 지정 현재 상태 구성

 

_**마지막으로 수정된 항목:** 2013-01-10_

Lync 2013에서 사용자 지정 현재 상태를 정의하려면 XML 사용자 지정 현재 상태 구성 파일을 만든 다음 CustomStateURL 매개 변수와 함께 Lync Server 관리 셸의 **New-CSClientPolicy** 또는 **Set-CSClientPolicy** cmdlet을 사용하여 위치를 지정합니다.

구성 파일에는 다음과 같은 속성이 포함됩니다.

  - 사용자 지정 현재 상태는 대화 가능, 다른 용무 중 및 방해 금지 중 하나의 현재 상태 표시기로 구성될 수 있습니다.

  - 상태 특성은 사용자 지정 상태의 상태 텍스트와 연관된 현재 상태 표시기를 결정합니다. 이 항목의 뒷부분에 나오는 예에서는 녹색(대화 가능) 현재 상태 표시기 오른쪽에 '재택 근무 중' 상태 텍스트가 표시됩니다.

  - 최대 상태 텍스트 길이는 64자입니다.

  - 사용자 지정 현재 상태는 4개까지 추가할 수 있습니다.

  - CustomStateURL 매개 변수는 구성 파일의 위치를 지정합니다. Lync 2013에서는 SIP 높은 수준의 보안 모드가 기본적으로 사용하도록 설정되므로 HTTPS가 사용하도록 설정된 웹 서버에 사용자 지정 현재 상태 구성 파일을 저장해야 합니다. 그렇지 않으면 Lync 2013 클라이언트가 해당 파일에 연결할 수 없습니다. 유효한 주소의 예는 `https://lspool.corp.contoso.com/ClientConfigFolder/CustomPresence.xml`과 같습니다.


> [!NOTE]
> 프로덕션 환경에서는 권장되지 않지만, EnableSIPHighSecurityMode 레지스트리 설정을 사용해 클라이언트에서 SIP 높은 수준의 보안 모드를 사용하지 않도록 설정함으로써 HTTPS가 아닌 파일 공유에 있는 구성 파일을 테스트할 수 있습니다. 그런 후에 CustomStateURL 레지스트리 설정을 사용하여 구성 파일에 대해 HTTPS가 아닌 위치를 지정할 수 있습니다. Lync 2013은 Lync 2010 레지스트리 설정을 다루지만 레지스트리 하이브가 업데이트되었습니다. 레지스트리 설정은 다음과 같이 만듭니다. 
> <UL>
> <LI>
> <P>HKEY_LOCAL_MACHINE\SOFTWARE\Policies\Microsoft\Office\15.0\Lync\EnableSIPHighSecurityMode</P>
> <P>유형: DWORD</P>
> <P>값 데이터: 0</P>
> <LI>
> <P>HKEY_LOCAL_MACHINE\SOFTWARE\Policies\Microsoft\Office\15.0\Lync\CustomStateURL</P>
> <P>유형: 문자열(REG_SZ)</P>
> <P>값 데이터(예제): file://\\lspool.corp.contoso.com\LSFileShare\ClientConfigFolder\Presence.xml 또는 file:///c:/LSFileShare/ClientConfigFolder/Group_1_Pres.xml</P></LI></UL>



XML 구성 파일에서 하나 이상의 LCID(로캘 ID) 스키마를 지정하여 사용자 지정 현재 상태를 지역화합니다. 이 항목의 뒷부분에 나오는 예에서는 영어 - 미국(1033), 노르웨이어 - 복말(1044), 프랑스어 - 프랑스(1036) 및 터키(1055)로의 지역화가 나와 있습니다. LCID 목록을 보려면 <http://go.microsoft.com/fwlink/?linkid=157331>의 Microsoft에서 할당한 로캘 ID를 참조하십시오.

## Lync 2013에 사용자 지정 현재 상태를 추가하려면

1.  다음 예 형식을 사용하는 XML 구성 파일을 만듭니다.
    
        <?xml version="1.0"?>
        <customStates xmlns="http://schemas.microsoft.com/09/2009/communicator/customStates">
          <customState ID="1" availability="online">
            <activity LCID="1033">Working from Home</activity>
            <activity LCID="1044">activity 2 for 1044</activity>
            <activity LCID="1055">activity 3 for 1055</activity>
          </customState>
          <customState ID="2" availability="busy">
            <activity LCID="1033">In a Live Meeting</activity>
            <activity LCID="1036">Equivalent French String for - In a Live Meeting </activity>
          </customState>
          <customState ID="3" availability="busy">
            <activity LCID="1033">Meeting with Customer</activity>
            <activity LCID="1055">meeting with client</activity>
            <activity LCID="1036">Equivalent French String for - Meeting with Customer</activity>
          </customState>
          <customState ID="4" availability="do-not-disturb">
            <activity LCID="1033">Interviewing</activity>
          </customState>
        </customStates>

2.  HTTPS가 사용하도록 설정된 웹 서버에 XML 구성 파일을 저장합니다. 이 예제에서 파일 이름은 Presence.xml이며 https://lspool.corp.contoso.com/ClientConfigFolder/CustomPresence.xml 위치에 저장됩니다.

3.  Lync Server 관리 셸 시작: **시작**, **모든 프로그램**, **Microsoft Lync Server 2013**을 차례로 클릭한 다음 **Lync Server 관리 셸**을 클릭합니다.

4.  Lync Server 관리 셸에서 다음과 유사한 명령을 사용하여 XML 구성 파일의 위치를 정의합니다.
    
        New-CsClientPolicy -Identity ContosoCustomStates 
        -CustomStateURL "https://lspool.corp.contoso.com/ClientConfigFolder/CustomPresence.xml"

5.  **Grant-CSClientPolicy** cmdlet를 사용하여 새로운 이 정책을 사용자에게 할당합니다.

자세한 내용은 Lync Server 관리 셸 설명서에서 [New-CsClientPolicy](https://docs.microsoft.com/en-us/powershell/module/skype/New-CsClientPolicy) 및 [Grant-CsClientPolicy](https://docs.microsoft.com/en-us/powershell/module/skype/Grant-CsClientPolicy)를 참조하십시오.


> [!NOTE]
> <UL>
> <LI>
> <P>기본적으로 Lync Server 2013은 3시간마다 클라이언트 정책과 설정을 업데이트합니다.</P>
> <LI>
> <P>CustomStateURL과 같이 이전 릴리스의 그룹 정책 설정을 계속 사용하려는 경우 Lync 2013에서는 해당 설정이 새 정책 레지스트리 하이브(HKEY_LOCAL_MACHINE\SOFTWARE\Policies\Microsoft\Office\15.0\Lync)에 있으면 설정을 인식합니다. 그러나 서버 기반 클라이언트 정책이 우선적으로 사용됩니다.</P></LI></UL>


