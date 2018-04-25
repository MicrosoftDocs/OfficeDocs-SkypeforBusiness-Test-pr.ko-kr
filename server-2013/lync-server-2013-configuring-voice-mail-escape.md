---
title: Lync Server 2013에서 음성 사서함 이스케이프 구성
TOCTitle: Lync Server 2013에서 음성 사서함 이스케이프 구성
ms:assetid: a1d19e6c-82ff-4768-8ae5-da981368ce40
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/JJ688157(v=OCS.15)
ms:contentKeyID: 49885905
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Lync Server 2013에서 음성 사서함 이스케이프 구성

 

_**마지막으로 수정된 항목:** 2013-02-22_

사용자가 휴대폰에 대한 동시 전화 신호 울림 기능을 구성한 경우 휴대폰이 꺼져 있거나, 배터리가 방전되었거나, 망 범위를 벗어나 있는 경우 일반적으로 발신자가 사용자의 개인 음성 메일로 라우팅됩니다. Microsoft Lync Server 2013에서는 사용자가 업무 관련 전화를 회사 음성 메일 시스템으로 라우팅하도록 선택할 수 있습니다. 특히 타이머를 구성할 수 있어 전화가 정의된 시간 범위 내에 이동 통신 사업자의 음성 메일로 응답되는 경우 Lync Server 2013에서 이동 통신 사업자의 음성 메일 시스템(및 사용자의 개인 음성 메일)에서 연결을 끊으며 이와 동시에 회사 시스템에 있는 사용자의 나머지 끝점에서 계속 전화 신호가 울립니다. 이렇게 해서 발신자가 자동으로 사용자의 회사 음성 메일로 라우팅됩니다.

이 구성은 Lync Server 관리 셸 cmdlet인 Set-CsVoicePolicy를 사용하여 음성 정책 수준에서 다음 매개 변수를 사용하여 수행됩니다.

## 음성 메일 이스케이프 구성

1.  Lync Server 관리 셸 시작: **시작**, **모든 프로그램**, **Microsoft Lync Server 2013**을 차례로 클릭한 다음 **Lync Server 관리 셸**을 클릭합니다.

2.  **Set-CsVoicePolicy**에 다음 매개 변수를 지정합니다.
    
      - **EnableVoicemailEscapeTimer** - 이스케이프 타이머를 사용하거나 사용하지 않도록 설정합니다.
    
      - **PSTNVoicemailEscapeTimer** - 시간 제한 값을 밀리초 단위로 지정합니다. 기본값은 1500밀리초이며 0~8000밀리초 범위에서 값을 지정할 수 있습니다.

## 예제

    Set-CsVoicePolicy UserVoicePolicy -EnableVoiceMailEscapeTimer $true - PSTNVoicemailEscapeTimer 2000
    
    Set-CsVoicePolicy -Identity site:SitePolicy -EnableVoiceMailEscapeTimer $true -PSTNVoicemailEscapeTimer 1500

## 참고 항목

#### 기타 리소스

[Lync Server 2013에서 통화 기능 및 권한을 부여하도록 음성 정책 및 PSTN 사용 레코드 구성](lync-server-2013-configuring-voice-policies-and-pstn-usage-records-to-authorize-calling-features-and-privileges.md)

