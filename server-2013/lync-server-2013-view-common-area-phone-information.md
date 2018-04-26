---
title: 공통 영역 전화 정보 보기
TOCTitle: 공통 영역 전화 정보 보기
ms:assetid: e652240c-6a3f-4be7-a083-32f24c08e655
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/JJ994081(v=OCS.15)
ms:contentKeyID: 52056977
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# 공통 영역 전화 정보 보기

 

_**마지막으로 수정된 항목:** 2013-02-20_

**Get-CsCommonAreaPhone** cmdlet을 사용하면 조직에서 사용하도록 구성된 공통 영역 전화에 대한 정보를 볼 수 있습니다. 매개 변수 없이 사용하는 경우 이 cmdlet은 모든 공통 영역 전화에 대한 정보를 반환합니다. 선택적 매개 변수를 포함하면 다른 방식으로 정보를 필터링할 수 있습니다. 예를 들어 지정된 OU(조직 구성 단위)에 대화 상대 개체가 있거나 모든 대화 상대 개체가 지정된 건물에 있는 모든 공통 영역 전화를 반환할 수 있습니다. **Get-CsCommonAreaPhone** 매개 변수에 대한 자세한 내용은 [Get-CsCommonAreaPhone](get-cscommonareaphone.md)을 참조하십시오.

**Get-CsCommonAreaPhone**은 Lync Server 2013 관리 셸 또는 Windows PowerShell의 원격 세션에서 실행합니다.


## 모든 공통 영역 전화에 대한 정보 보기

  - 모든 공통 영역 전화에 대한 정보를 보려면 Lync Server 관리 셸에서 다음 명령을 입력하고 Enter 키를 누릅니다.
    
        Get-CsCommonAreaPhone
    
    그러면 다음과 같은 정보가 표시됩니다.
    
        Identity           : CN=Building 14 Lobby,OU=Redmond,
                             DC=litwareinc,DC=com
        RegistrarPool      : atl-cs-001.litwareinc.com
        Enabled            : True
        SipAddress         : sip:4714e34b-9781-421d-b07a-
                             52056b5b4a56@litwareinc.com
        ClientPolicy       :
        PinPolicy          :
        VoicePolicy        :
        MobilityPolicy     :
        GroupChatPolicy    :
        ConferencingPolicy :
        LineURI            : tel:+14255550712
        DisplayNumber      : 1-425-555-0712
        DisplayName        : Building 14 Lobby
        Description        :
        ExUmEnabled        : False

자세한 내용은 [Get-CsCommonAreaPhone](get-cscommonareaphone.md) cmdlet의 도움말 항목을 참조하십시오.

