---
title: Microsoft Lync Phone Edition 장치의 서비스 품질 구성
TOCTitle: Microsoft Lync Phone Edition 장치의 서비스 품질 구성
ms:assetid: a6eb2620-a512-4ab6-bdfd-eb76be43bbfe
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/JJ205137(v=OCS.15)
ms:contentKeyID: 49304630
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Microsoft Lync Phone Edition 장치의 서비스 품질 구성

 

_**마지막으로 수정된 항목:** 2012-11-01_

QoS(서비스 품질)는 iPhone과 같은 장치에서는 기본적으로 사용하지 않도록 설정되어 있지만 Lync Phone Edition을 실행하는 장치에서는 기본적으로 사용하도록 설정되어 있습니다. 이러한 장치를 일반적으로 UC(통합 통신) 전화라고 합니다. 이것을 확인하려면 Lync Server 관리 셸 내에서 다음 Windows PowerShell 명령을 실행합니다.

    Get-CsUCPhoneConfiguration

UC 전화 구성 설정을 변경하지 않은 경우 다음과 같은 정보가 반환됩니다.

    Identity             : Global
    CalendarPollInterval : 00:03:00
    EnforcePhoneLock     : True
    PhoneLockTimeout     : 00:10:00
    MinPhonePinLength    : 6
    SIPSecurityMode      : High
    VoiceDiffServTag     : 40
    Voice8021p           : 0
    LoggingLevel         : Off

QoS 용도로는 이러한 속성 중 VoiceDiffServTag 하나만 고려됩니다. VoiceDiffServTag는 Lync Phone Edition 장치에서 나오는 음성 트래픽에 할당된 DSCP 값을 나타냅니다.


> [!NOTE]
> Voice8021p 매개 변수는 Lync Server 2013에서 더 이상 지원되지 않습니다. 이 매개 변수는 이전 버전인 Microsoft Lync Server 2010과의 호환성을 위해 여전히 유효하지만 Lync Server 2013을 사용하는 장치에서는 유효하지 않습니다.



대부분의 네트워크에서 Lync Phone Edition 패킷을 VoiceDiffServTag 40으로 표시할 경우 아무 문제도 발생하지 않습니다. 그러나 40은 일반적으로 오디오 트래픽에 사용되는 값이 아닙니다. 오디오 트래픽은 거의 항상 DSCP 코드 46으로 표시됩니다. 네트워크 전반에서 일관성을 유지하기 위해 UC 전화의 VoiceDiffServTag 속성을 46으로 변경하는 것이 좋을 수 있습니다.

이를 위해 Windows PowerShell 또는 Lync Server 제어판을 사용할 수 있습니다. Windows PowerShell을 사용하여 VoiceDiffServTag 값을 수정하려면 Lync Server 관리 셸 내에서 다음 명령을 실행합니다.

    Set-CsUCPhoneConfiguration -VoiceDiffServTag 46

위의 명령은 UC 전화 구성 설정의 전역 컬렉션을 수정합니다. 그러나 UC 전화 설정을 사이트 범위에 할당할 수도 있습니다. 사이트 범위에서 UC 전화 구성 설정을 수정하려면 사이트 ID를 지정해야 합니다. 예를 들면 다음과 같습니다.

    Set-CsUCPhoneConfiguration -Identity "site:Redmond" -VoiceDiffServTag 46

또한 다음 명령을 사용하여 모든 UC 전화 구성 설정을 동시에 수정할 수도 있습니다.

    Get-CsUCPhoneConfiguration | Set-CsUCPhoneConfiguration -VoiceDiffServTag 46

Lync Server 제어판을 사용하여 이 변경을 수행하려면 제어판을 시작하고 다음 절차를 완료합니다.

1.  **클라이언트**를 클릭하고 **장치 구성**을 클릭합니다.

2.  **장치 구성** 탭에서 수정할 설정 컬렉션(예: **전역**)을 두 번 클릭합니다.

3.  **장치 구성 편집** 대화 상자에서 **음성 QoS(Quality of Service)** 상자의 값을 **46**으로 설정한 다음 **커밋**을 클릭합니다.

여러 컬렉션이 있는 경우 각 UC 전화 설정 컬렉션에 대해 이 프로세스를 반복해야 합니다. Lync Server 제어판에서는 여러 설정 컬렉션을 동시에 수정할 수 없습니다.

Windows 운영 체제 기반이 아닌 장치(예: iPhone)가 조직에 있는 경우 이러한 장치는 VoiceDiffServTag 설정 변경의 영향을 받지 않습니다. 이러한 장치에서 DSCP 값을 변경하려면 각 장치 유형에 대한 관리 설명서를 참조해야 합니다.

