---
title: 공통 영역 전화에 정책 할당
TOCTitle: 공통 영역 전화에 정책 할당
ms:assetid: f0554fd1-b237-49b3-9eb4-26f4b91f5604
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/JJ994082(v=OCS.15)
ms:contentKeyID: 52056984
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# 공통 영역 전화에 정책 할당

 

_**마지막으로 수정된 항목:** 2013-02-20_

공통 영역 전화용으로 정책을 만든 후(자세한 내용은 [Lync Server 2013에서 음성 정책 수정 및 PSTN 사용 레코드 만들기](lync-server-2013-create-a-voice-policy-and-configure-pstn-usage-records.md) 참조) Windows PowerShell 및 적절한 **Grant-Cs** cmdlet을 사용하여 해당 정책을 공통 영역 전화에 할당할 수 있습니다. 이러한 cmdlet은 Lync Server 2013 관리 셸Windows PowerShell 또는 원격 Windows PowerShell을 사용하여 Lync Server에 연결하는 방법에 대한 자세한 내용은 Lync Server Windows PowerShell 블로그 문서인 "빠른 시작: 원격 PowerShell을 사용하여 Microsoft Lync Server 2010 관리"([http://go.microsoft.com/fwlink/p/?linkId=255876](http://go.microsoft.com/fwlink/p/?linkid=255876))를 참조하세요.의 원격 세션에서 실행할 수 있습니다.


## 단일 공통 영역 전화에 정책 할당

  - 다음 명령은 Identity가 Building 14 Lobby인 공통 영역 전화에 사용자별 음성 정책 RedmondVoice를 할당합니다.
    
        Grant-CsVoicePolicy -Identity "Building 14 Lobby" -PolicyName "RedmondVoicePolicy"

## 여러 공통 영역 전화에 정책 할당

  - 이 예제에서는 조직에서 사용하도록 구성된 모든 공통 영역 전화에 사용자별 음성 정책 RedmondVoice를 할당합니다.
    
        Get-CsCommonAreaPhone | Grant-CsVoicePolicy  -PolicyName "RedmondVoicePolicy"

자세한 내용은 [Grant-CsVoicePolicy](https://docs.microsoft.com/en-us/powershell/module/skype/Grant-CsVoicePolicy) cmdlet의 도움말 항목을 참조하십시오.

## 참고 항목

#### 기타 리소스

[Get-CsCommonAreaPhone](https://docs.microsoft.com/en-us/powershell/module/skype/Get-CsCommonAreaPhone)

