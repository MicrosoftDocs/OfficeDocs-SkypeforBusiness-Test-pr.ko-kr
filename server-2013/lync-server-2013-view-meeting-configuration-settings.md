---
title: 모임 구성 설정 보기
TOCTitle: 모임 구성 설정 보기
ms:assetid: d03a4684-9d8b-4728-917d-5b5c91511e2c
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/JJ721894(v=OCS.15)
ms:contentKeyID: 49885997
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# 모임 구성 설정 보기

 

_**마지막으로 수정된 항목:** 2013-02-23_

Lync Server 2013 제어판에서 모임 구성 설정을 사용하여 모임이 배포에 구현되는 방식을 제어할 수 있습니다. 여기에는 다음 모임 구성이 포함됩니다.

  - Lync Server 2013을 배포할 때 기본적으로 만들어지는 전역 구성

  - 모임이 특정 사이트 또는 사용자에 구현되는 방식을 지정하는 데 사용하도록 만들 수 있는 사이트 수준 및 사이트 수준 구성(선택 사항)

## 모임 구성 설정을 보려면

1.  CsUserAdministrator 역할 또는 CsAdministrator 역할에 할당된 사용자 계정에서 내부 배포된 컴퓨터에 로그온합니다.

2.  브라우저 창을 연 다음 Admin URL을 입력하여 Lync Server 제어판을 엽니다. Lync Server 제어판을 시작하는 데 사용할 수 있는 다양한 방법에 대한 자세한 내용은 [Lync Server 관리 도구 열기](lync-server-2013-open-lync-server-administrative-tools.md)를 참조하세요.

3.  왼쪽 탐색 표시줄에서 **회의**, **모임 구성**을 차례로 클릭합니다.

4.  **모임 구성** 페이지에서 보려는 모임 구성을 클릭합니다.

5.  **파일 필터 편집**에서 **자세한 정보 표시** 확인란을 선택합니다.
    
    **모임 구성 편집 - \<정책\>**이 열리고 선택한 정책의 설정이 표시됩니다. 설정을 구성하는 방법에 대한 자세한 내용은 [모임 구성 설정 모음 만들기 또는 수정](lync-server-2013-create-or-modify-a-collection-of-meeting-configuration-settings.md)을 참조하십시오.

## Lync Server PowerShell Cmdlet을 사용하여 모임 구성 정보 보기

모임 구성 설정은 또한 Lync Server PowerShell 및 Get-CsMeetingConfiguration cmdlet을 사용하여 볼 수 있습니다. 이 cmdlet은 Lync Server 2013 관리 셸 또는 원격 세션의 Windows PowerShell에서 실행할 수 있습니다. 원격 Windows PowerShell을 사용하여 Lync Server에 연결하는 방법에 대한 자세한 내용은 Lync Server Windows PowerShell 블로그 문서인 "빠른 시작: 원격 PowerShell을 사용하여 Microsoft Lync Server 2010 관리"([http://go.microsoft.com/fwlink/p/?linkId=255876](http://go.microsoft.com/fwlink/p/?linkid=255876))를 참조하세요.

## 모임 구성 정보 보기

  - 모든 모임 구성 설정에 대한 정보를 보려면 Lync Server 관리 셸에서 다음 명령을 입력하고 Enter 키를 누릅니다.
    
        Get-CsMeetingConfiguration
    
    그러면 다음과 유사한 정보가 반환됩니다.
    
        Identity                        : Global
        PstnCallersBypassLobby          : True
        EnableAssignedConferenceType    : True
        DesignateAsPresenter            : Company
        AssignedConferenceTypeByDefault : True
        AdmitAnonymousUsersByDefault    : True
        RequireRoomSystemsAuthorization : False
        LogoURL                         :
        LegalURL                        :
        HelpURL                         :
        CustomFooterText                :
        AllowConferenceRecording        : True

자세한 내용은 [Get-CsMeetingConfiguration](https://docs.microsoft.com/en-us/powershell/module/skype/Get-CsMeetingConfiguration) cmdlet에 대한 도움말 항목을 참조하십시오.

