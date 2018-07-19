---
title: Lync Server 2013에서 응용 프로그램 수준 응답 그룹 설정 관리
TOCTitle: Lync Server 2013에서 응용 프로그램 수준 응답 그룹 설정 관리
ms:assetid: aab749a1-fa2d-4ce8-a6c6-ebcfa37ce02a
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/JJ721843(v=OCS.15)
ms:contentKeyID: 49885921
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Lync Server 2013에서 응용 프로그램 수준 응답 그룹 설정 관리

 

_**마지막으로 수정된 항목:** 2012-11-01_

응답 그룹 응용 프로그램에 대한 응용 프로그램 수준 설정에는 기본 대기 음악 구성, 기본 대기 음악 오디오 파일, 에이전트 되걸기 유예 기간 및 통화 컨텍스트 구성이 포함됩니다. 풀당 응용 프로그램 수준 설정 집합을 하나만 정의할 수 있습니다. 응용 프로그램 수준 설정을 보려면 **Get-CsRgsConfiguration** cmdlet을 사용하고, 응용 프로그램 수준 설정을 수정하려면 **Set-CsRgsConfiguration** cmdlet을 사용합니다.

기본 대기 음악은 사용자 지정 대기 음악이 정의되지 않은 경우에만 통화 대기 시 재생됩니다. 통화 컨텍스트는 대화형 워크플로에 할당된 큐에만 제공됩니다. 통화 컨텍스트를 사용하도록 설정된 경우 에이전트가 전화를 받을 때 발신자 대기 시간 또는 워크플로 질문 및 대답과 같은 정보를 볼 수 있습니다.

## 응답 그룹 응용 프로그램 수준 설정을 수정하려면

1.  RTCUniversalServerAdmins 그룹의 구성원이나 응답 그룹을 지원하는 미리 정의된 관리 역할 중 하나의 구성원으로 로그온합니다.

2.  Lync Server 관리 셸 시작: **시작**, **모든 프로그램**, **Microsoft Lync Server 2013**을 차례로 클릭한 다음 **Lync Server 관리 셸**을 클릭합니다.

3.  명령줄에서 다음을 실행합니다.
    
        Set-CsRgsConfiguration -Identity <name of service hosting Response Group> [-AgentRingbackGracePeriod <# seconds until call returns to agent after declined>] [-DefaultMusicOnHoldFile <audio file>] [-DisableCallContext <$true | $false>]
    
    예를 들면 다음과 같습니다.
    
        Set-CsRgsConfiguration -Identity "service:ApplicationServer:redmond.contoso.com" -AgentRingbackGracePeriod 30 -DisableCallContext $false
    
    기본 대기 음악으로 사용할 오디오 파일을 지정하려면 먼저 오디오 파일을 가져와야 합니다. 예를 들면 다음과 같습니다.
    
        $x = Import-CsRgsAudioFile -Identity "service:ApplicationServer:redmond.contoso.com" -FileName "MusicWhileYouWait.wav" -Content (Get-Content C:\Media\ MusicWhileYouWait.wav -Encoding byte -ReadCount 0)
        Set-CsRgsConfiguration -Identity "service:ApplicationServer:redmond.contoso.com" -DefaultMusicOnHoldFile <$x>

## 참고 항목

#### 기타 리소스

[Get-CsRgsConfiguration](https://docs.microsoft.com/powershell/module/skype/Get-CsRgsConfiguration)  
[Set-CsRgsConfiguration](https://docs.microsoft.com/en-us/powershell/module/skype/Set-CsRgsConfiguration)  
[Import-CsRgsAudioFile](https://docs.microsoft.com/powershell/module/skype/Import-CsRgsAudioFile)

