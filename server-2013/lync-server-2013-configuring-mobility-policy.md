---
title: 'Lync Server 2013: 모바일 정책 구성'
TOCTitle: 모바일 정책 구성
ms:assetid: 595536e0-9bb3-49a3-8d13-1a77351ebc62
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Hh690018(v=OCS.15)
ms:contentKeyID: 49303723
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Lync Server 2013에서 모바일 정책 구성

 

_**마지막으로 수정된 항목:** 2013-02-13_

    Some information in this topic pertains to Cumulative Updates for Lync Server 2013: February 2013.

Lync Server 2013은 모바일 기능, 회사번호로 전화, VoIP(Voice over IP) 또는 비디오를 사용할 수 있는 사용자와 VoIP나 비디오에 대해 Wi-Fi가 필요한지 여부를 결정할 수 있는 새로운 모바일 기능 정책을 제공합니다. 모바일 사용자는 회사번호로 전화 기능을 통해 자신의 휴대폰 번호 대신 회사 전화 번호를 사용하여 휴대폰에서 전화를 걸고 받을 수 있습니다. 이 기능을 사용하면 수신자가 발신자의 휴대폰 번호를 볼 수 없으며 발신자에게는 발신 통화 요금이 부과되지 않습니다. VoIP 및 비디오를 구성하면 사용자가 VoIP 전화와 비디오 전화를 걸고 받을 수 있습니다. Wi-Fi 사용에 대한 설정은 사용자 장치에서 셀룰러 데이터 네트워크가 아닌 Wi-Fi 네트워크를 사용해야 하는지 여부를 정의합니다.

기본적으로는 모바일 기능, 회사번호로 전화, VoIP 및 비디오 기능을 모두 사용할 수 있습니다. VoIP 및 비디오에 대해 Wi-Fi를 필요로 하는 설정은 사용하지 않도록 설정됩니다. 관리자는 cmdlet을 실행하여 이러한 기능에 액세스할 수 있는 사용자를 결정할 수 있습니다. 옵션을 전역적으로 해제할 수도 있고 사이트나 사용자별로 해제할 수도 있습니다.

모바일 기능과 회사번호로 전화 기능을 사용하려면 사용자는 다음 필수 구성 요소를 충족해야 합니다.

  - 사용자가 Lync Server 2013를 사용할 수 있도록 설정되어야 합니다.

  - 사용자가 Enterprise Voice를 사용할 수 있도록 설정되어야 합니다.

  - **EnableMobility** 옵션이 True로 설정된 모바일 정책이 사용자에게 지정되어 있어야 합니다.

회사번호로 전화 기능을 사용하려는 사용자는 다음의 두 선행 조건을 추가로 충족해야 합니다.

  - **동시 전화 신호 울림 사용** 옵션이 선택된 음성 정책이 사용자에게 지정되어 있어야 합니다.

  - **EnableOutsideVoice** 옵션이 True로 설정된 모바일 정책이 사용자에게 지정되어 있어야 합니다.


> [!NOTE]
> Enterprise Voice를 사용할 수 없는 사용자의 경우 모바일 장치를 사용하여 Lync에서 Lync로의 VoIP(Voice over IP) 전화를 걸거나, 해당 사용자에게 적절한 음성 정책용 옵션을 할당하는 경우에는 모바일 장치에서 참가하려면 클릭 링크를 통해 회의에 참가할 수 있습니다. 자세한 내용은 <A href="lync-server-2013-defining-your-mobility-requirements.md">Lync Server 2013에 대한 모바일 기능 요구 사항 정의</A>를 참조하십시오.



사용자가 Lync Server 2013을 사용할 수 있도록 설정하는 방법에 대한 자세한 내용은 [사용자 계정에서 Lync Server를 사용하거나 사용하지 않도록 설정](lync-server-2013-disable-or-re-enable-user-account-for-lync-server.md)를 참조하십시오. 사용자가 Enterprise Voice를 사용할 수 있도록 설정하는 방법에 대한 자세한 내용은 [Lync Server 2013에서 사용자가 Enterprise Voice를 사용할 수 있도록 설정](lync-server-2013-enable-users-for-enterprise-voice.md)를 참조하십시오. 음성 정책 옵션을 설정하는 방법에 대한 자세한 내용은 [Lync Server 2013에서 음성 정책 수정 및 PSTN 사용 레코드 구성](lync-server-2013-modify-a-voice-policy-and-configure-pstn-usage-records.md)을 참조하십시오.

## 전역 모바일 정책을 수정하려면

1.  Lync Server 관리 셸 및 Ocscore가 설치되어 있는 컴퓨터에 CsAdministrator 역할의 구성원으로 로그온합니다.

2.  Lync Server 관리 셸 시작: **시작**, **모든 프로그램**, **Microsoft Lync Server 2013**을 차례로 클릭한 다음 **Lync Server 관리 셸**을 클릭합니다.

3.  명령줄에 다음을 입력하여 모바일 기능 및 회사번호로 전화 기능에 대한 액세스를 전역적으로 해제합니다.
    
        Set-CsMobilityPolicy -EnableMobility $False -EnableOutsideVoice $False
    

    > [!NOTE]
    > 모바일 기능 액세스는 해제하지 않고 회사번호로 전화 기능만 해제할 수는 있지만, 회사번호로 전화 기능은 해제하지 않고 모바일 기능만 해제할 수는 없습니다.



## 사이트별로 모바일 정책을 수정하려면

1.  Lync Server 관리 셸 및 Ocscore가 설치되어 있는 컴퓨터에 CsAdministrator 역할의 구성원으로 로그온합니다.

2.  Lync Server 관리 셸 시작: **시작**, **모든 프로그램**, **Microsoft Lync Server 2013**을 차례로 클릭한 다음 **Lync Server 관리 셸**을 클릭합니다.

3.  사이트 수준 정책을 만들고 VoIP 및 비디오를 해제한 후에 사이트별로 IP 오디오에 대해 Wi-Fi 필요 및 IP 비디오에 대해 Wi-Fi 필요를 사용하도록 설정합니다. 이렇게 하려면 명령줄에 다음을 입력합니다.
    
        New-CsMobilityPolicy -Identity site:<site identifier> -EnableIPAudioVideo $False -RequireWiFiForIPAudio $True -RequireWiFiForIPVideo $True

## 사용자별로 모바일 정책을 수정하려면

1.  Lync Server 관리 셸 및 Ocscore가 설치되어 있는 컴퓨터에 CsAdministrator 역할의 구성원으로 로그온합니다.

2.  Lync Server 관리 셸 시작: **시작**, **모든 프로그램**, **Microsoft Lync Server 2013**을 차례로 클릭한 다음 **Lync Server 관리 셸**을 클릭합니다.

3.  명령줄에 다음을 입력하여 사용자 수준 모바일 정책을 만들고 모바일 기능 및 회사번호로 전화 기능을 사용자별로 해제합니다.
    
        New-CsMobilityPolicy -Identity <policy name> -EnableMobility $False -EnableOutsideVoice $False
        Grant-CsMobilityPolicy -Identity <user identifier> -PolicyName <policy name>
    
    모바일 기능 액세스는 해제하지 않고 회사번호로 전화 기능만 해제할 수는 있지만, 회사번호로 전화 기능은 해제하지 않고 모바일 기능만 해제할 수는 없습니다.
    
    예를 들면 다음과 같습니다.
    
        New-CsMobilityPolicy "tag:disableOutsideVoice" -EnableOutsideVoice $False
        Grant-CsMobilityPolicy -Identity -MobileUser1@contoso.com -PolicyName Tag:disableOutsideVoice

## 참고 항목

#### 작업

[사용자 계정에서 Lync Server를 사용하거나 사용하지 않도록 설정](lync-server-2013-disable-or-re-enable-user-account-for-lync-server.md)  
[Lync Server 2013에서 사용자가 Enterprise Voice를 사용할 수 있도록 설정](lync-server-2013-enable-users-for-enterprise-voice.md)  
[Lync Server 2013에서 음성 정책 수정 및 PSTN 사용 레코드 구성](lync-server-2013-modify-a-voice-policy-and-configure-pstn-usage-records.md)  

#### 개념

[Lync Server 2013에 대한 모바일 기능 요구 사항 정의](lync-server-2013-defining-your-mobility-requirements.md)  

#### 기타 리소스

[New-CsMobilityPolicy](https://docs.microsoft.com/en-us/powershell/module/skype/New-CsMobilityPolicy)  
[Set-CsMobilityPolicy](https://docs.microsoft.com/en-us/powershell/module/skype/Set-CsMobilityPolicy)  
[Get-CsMobilityPolicy](https://docs.microsoft.com/en-us/powershell/module/skype/Get-CsMobilityPolicy)  
[Grant-CsMobilityPolicy](https://docs.microsoft.com/en-us/powershell/module/skype/Grant-CsMobilityPolicy)  
[Remove-CsMobilityPolicy](https://docs.microsoft.com/en-us/powershell/module/skype/Remove-CsMobilityPolicy)

