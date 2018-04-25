---
title: Windows 기반이 아닌 장치에 QoS 사용
TOCTitle: Windows 기반이 아닌 장치에 QoS 사용
ms:assetid: 26f793df-aef8-4028-9e3b-6c2c37ea61b9
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/JJ204750(v=OCS.15)
ms:contentKeyID: 49303107
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Windows 기반이 아닌 장치에 QoS 사용

 

_**마지막으로 수정된 항목:** 2012-11-01_

Microsoft Lync Server 2013을 설치할 때 QoS(서비스 품질)는 조직에서 사용되는 장치 중에서 Windows 이외의 운영 체제를 사용하는 장치에 대해 사용하도록 설정되지 않습니다. Lync Server 2013 관리 셸 내에서 다음 명령을 실행하면 이를 확인할 수 있습니다.

    Get-CsMediaConfiguration

미디어 구성 설정을 변경하지 않았다고 가정할 때 다음과 같은 정보가 반환됩니다.

    Identity                          : Global
    EnableQoS                         : False
    EncryptionLevel                   : RequireEncryption
    EnableSiren                       : False
    MaxVideoRateAllowed               : VGA600K
    EnableG722StereoCodec             : True
    EnableH264Codec                   : True
    EnableAdaptiveBandwidthEstimation : True

위의 출력에서와 같이 EnableQoS 속성이 False로 설정되어 있으면 Windows 이외의 운영 체제를 사용하는 컴퓨터 및 장치에 대해 서비스 품질이 사용하도록 설정되지 않은 것입니다. QoS는 Lync Phone Edition 장치에 대해 기본적으로 사용하도록 설정되지만, Lync Phone Edition에 대해 서비스 품질을 사용하지 않도록 설정할 수 있습니다.

전역 범위에서 서비스 품질을 사용하도록 설정하려면 Lync Server 관리 셸 내에서 다음 명령을 실행합니다.

    Set-CsMediaConfiguration -EnableQoS $True

위의 명령은 전역 범위에서 QoS를 사용하도록 설정합니다. 그러나 미디어 구성 설정은 사이트 범위에도 적용될 수 있습니다. 사이트에 대해 서비스 품질을 사용하도록 설정해야 하는 경우에는 Set-CsMediaConfiguration을 호출할 때 구성 설정의 Identity도 포함해야 합니다. 예를 들어 다음 명령은 Redmond 사이트에 대해 QoS를 사용하도록 설정합니다.

    Set-CsMediaConfiguration -Identity site:Redmond -EnableQoS $True


> [!NOTE]
> 사이트 범위에서 QoS를 사용하도록 설정해야 하는지 여부는 경우에 따라 다릅니다. 사이트 범위에 할당된 설정은 전역 범위에 할당된 설정보다 우선합니다. QoS를 전역 범위에서는 사용하도록 설정하고 사이트 범위(Redmond 사이트의 경우)에서는 사용하지 않도록 설정했다고 가정하겠습니다. 이 경우 사이트 설정이 우선하기 때문에 Redmond 사이트에 대해서는 서비스 품질이 사용하지 않도록 설정됩니다. Redmond 사이트에 대해 QoS를 사용하도록 설정하려면 해당 사이트에 적용된 미디어 구성 설정을 사용하여 해당 작업을 수행해야 합니다.



범위에 관계없이 모든 미디어 구성 설정에 대해 QoS를 동시에 사용하도록 설정하려면 Lync Server 관리 셸 내에서 다음 명령을 실행합니다.

    Get-CsMediaConfiguration | Set-CsMediaConfiguration -EnableQoS $True

EnableQoS 속성의 값을 False로 설정하면 Windows 이외의 운영 체제를 사용하는 장치에 대해 QoS를 사용하지 않도록 설정할 수 있습니다. 예를 들면 다음과 같습니다.

    Set-CsMediaConfiguration -Identity site:Redmond -EnableQoS $False

이렇게 하면 네트워크의 일부분에서는 서비스 품질을 사용하지 않도록 설정한 상태를 유지하면서 Redmond 사이트에서와 같이 다른 네트워크 부분에는 QoS를 구현할 수 있습니다.

QoS는 Lync Server 관리 셸을 통해서만 사용 및 사용하지 않도록 설정할 수 있습니다. Lync Server 제어판에서는 이러한 옵션을 사용할 수 없습니다.

