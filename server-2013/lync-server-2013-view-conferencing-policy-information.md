---
title: 회의 정책 정보 보기
TOCTitle: 회의 정책 정보 보기
ms:assetid: e99fdc4d-926a-4e36-ac99-ab5035568847
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/JJ721918(v=OCS.15)
ms:contentKeyID: 49886035
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# 회의 정책 정보 보기

 

_**마지막으로 수정된 항목:** 2013-02-23_

Lync Server 2013 제어판에서는 회의 정책을 사용하여 배포에서 회의를 구현하는 방식을 제어할 수 있습니다. 여기에는 다음 회의 정책이 포함됩니다.

  - Lync Server 2013을 배포할 때 기본적으로 만들어지는 글로벌 정책

  - 특정 사이트나 사용자에 대해 회의가 어떻게 구현되는지를 지정하기 위해 만들고 사용할 수 있는 사이트 수준 및 사용자 수준의 정책(선택 사항)

## 회의 정책 설정을 보려면

1.  CsUserAdministrator 역할 또는 CsAdministrator 역할에 할당된 사용자 계정에서 내부 배포된 컴퓨터에 로그온합니다.

2.  브라우저 창을 연 다음 Admin URL을 입력하여 Lync Server 제어판을 엽니다. Lync Server 제어판을 시작하는 데 사용할 수 있는 다양한 방법에 대한 자세한 내용은 [Lync Server 관리 도구 열기](lync-server-2013-open-lync-server-administrative-tools.md)를 참조하세요.

3.  왼쪽 탐색 모음에서 **회의**를 클릭하고 **회의 정책**을 클릭합니다.

4.  **회의 정책** 페이지에서 표시할 회의 정책을 두 번 클릭합니다.

5.  **파일 필터 편집**에서 **세부 정보 표시…** 확인란을 선택합니다.
    
    **회의 정책 편집 - \<정책\>**이 열리고 선택한 정책에 대한 설정이 표시됩니다. 설정 구성에 대한 자세한 내용은 [회의 정책 만들기 또는 수정](lync-server-2013-create-or-modify-a-conferencing-policy.md)을 참조하십시오.

## Lync Server PowerShell Cmdlet을 사용하여 회의 정책 보기

회의 정책은 Lync Server PowerShell 및 Get-CsConferencingPolicy cmdlet을 사용하여 볼 수도 있습니다. 이 cmdlet은 Lync Server 2013 관리 셸 또는 Windows PowerShell의 원격 세션(원격 Windows PowerShell을 사용하여 Lync Server에 연결하는 방법에 대한 자세한 내용은 Lync Server Windows PowerShell 블로그 문서인 "빠른 시작: 원격 PowerShell을 사용하여 Microsoft Lync Server 2010 관리"([http://go.microsoft.com/fwlink/p/?linkId=255876](http://go.microsoft.com/fwlink/p/?linkid=255876))를 참조하세요.)에서 실행할 수 있습니다.

## 회의 정책 보기

  - 모든 회의 정책에 대한 정보를 보려면 Lync Server 관리 셸에서 다음 명령을 입력하고 Enter 키를 누릅니다.
    
        Get-CsConferencingPolicy
    
    그러면 다음과 같은 정보가 반환됩니다.
    
        Identity                                  : Global
        AllowIPAudio                              : True
        AllowIPVideo                              : True
        AllowMultiView                            : True
        Description                               :
        AllowParticipantControl                   : True
        AllowAnnotations                          : True
        DisablePowerPointAnnotations              : False
        AllowUserToScheduleMeetingsWithAppSharing : True
        AllowNonEnterpriseVoiceUsersToDialOut     : False
        AllowAnonymousUsersToDialOut              : False
        AllowAnonymousParticipantsInMeetings      : True
        AllowExternalUsersToSaveContent           : True
        AllowExternalUserControl                  : False
        AllowExternalUsersToRecordMeeting         : False
        AllowPolls                                : True
        AllowSharedNotes                          : True
        EnableDialInConferencing                  : True
        EnableAppDesktopSharing                   : Desktop
        AllowConferenceRecording                  : False
        EnableP2PRecording                        : False
        EnableFileTransfer                        : True
        EnableP2PFileTransfer                     : True
        EnableP2PVideo                            : True
        AllowLargeMeetings                        : False
        EnableDataCollaboration                   : True
        MaxVideoConferenceResolution              : VGA
        MaxMeetingSize                            : 250
        AudioBitRateKb                            : 200
        VideoBitRateKb                            : 50000
        AppSharingBitRateKb                       : 50000
        FileTransferBitRateKb                     : 50000
        TotalReceiveVideoBitRateKb                : 6000
        EnableMultiViewJoin                       : True

자세한 내용은 [Get-CsConferencingPolicy](https://docs.microsoft.com/en-us/powershell/module/skype/Get-CsConferencingPolicy) cmdlet에 대한 도움말 항목을 참조하십시오.

