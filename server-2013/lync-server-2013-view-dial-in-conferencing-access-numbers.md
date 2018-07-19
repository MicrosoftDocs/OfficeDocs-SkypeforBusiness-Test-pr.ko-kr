---
title: 전화 접속 회의 액세스 번호 보기
TOCTitle: 전화 접속 회의 액세스 번호 보기
ms:assetid: 41a7dfb4-0c89-4650-b61b-0e1bf875c62b
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/JJ688037(v=OCS.15)
ms:contentKeyID: 49885739
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# 전화 접속 회의 액세스 번호 보기

 

_**마지막으로 수정된 항목:** 2013-02-23_

Lync Server 2013 제어판에서는 사용자가 외부에서 모임에 참가할 수 있도록 사용자에게 전화 접속 액세스 번호를 제공합니다.

## 전화 접속 액세스 번호를 보려면

1.  CsUserAdministrator 역할 또는 CsAdministrator 역할에 할당된 사용자 계정에서 내부 배포된 컴퓨터에 로그온합니다.

2.  브라우저 창을 연 다음 Admin URL을 입력하여 Lync Server 제어판을 엽니다. Lync Server 제어판을 시작하는 데 사용할 수 있는 다양한 방법에 대한 자세한 내용은 [Lync Server 관리 도구 열기](lync-server-2013-open-lync-server-administrative-tools.md)를 참조하세요.

3.  왼쪽 탐색 모음에서 **회의**를 클릭한 다음 **전화 접속 액세스 번호**를 클릭합니다.

4.  **전화 접속 액세스 번호** 페이지에서 보려는 액세스 번호를 클릭합니다.

5.  **편집**에서 **세부 정보 표시...** 확인란을 선택합니다.

## Lync Server PowerShell Cmdlet을 사용하여 전화 접속 회의 액세스 번호 보기

전화 접속 회의 액세스 번호는 Lync Server PowerShell 및 Get-CsDialInConferencingAccessNumber cmdlet을 사용하여 볼 수 있습니다. 이 cmdlet은 Lync Server 2013 관리 셸에서 실행하거나 Windows PowerShell의 원격 세션에서 실행할 수 있습니다. 원격 Windows PowerShell을 사용하여 Lync Server에 연결하는 방법에 대한 자세한 내용은 Lync Server Windows PowerShell 블로그 문서인 "빠른 시작: 원격 PowerShell을 사용하여 Microsoft Lync Server 2010 관리"([http://go.microsoft.com/fwlink/p/?linkId=255876](http://go.microsoft.com/fwlink/p/?linkid=255876))를 참조하세요.

## SIP 트렁크 구성 정보 보기

  - 모든 전화 접속 회의 액세스 번호에 대한 정보를 보려면 Lync Server 관리 셸에 다음 명령을 입력한 후 Enter 키를 누릅니다.
    
        Get-CsDialInConferencingAccessNumber
    
    그러면 다음과 비슷한 정보가 표시됩니다.
    
        Identity           : CN={20ca8dc8-5ff8-41f4-b5bb-22ba9972ae2e},
                             CN=Application Contacts,CN=RTCService=Services,
                             CN=Configuration,DC=litwareinc,DC=com
        PrimaryUri         : sip:testnumber@litwareinc.com
        DisplayName        : Test
        DisplayNumber      : 1-425-555-1019
        LineUri            : tel:+14255551019
        PrimaryLanguage    : en-US
        SecondaryLanguages : {}
        Pool               : atl-cs-001.litwareinc.com
        HostingProvider    :
        Regions            : {US}

자세한 내용은 [Get-CsDialInConferencingAccessNumber](https://docs.microsoft.com/en-us/powershell/module/skype/Get-CsDialInConferencingAccessNumber) cmdlet의 도움말 항목을 참조하십시오.

