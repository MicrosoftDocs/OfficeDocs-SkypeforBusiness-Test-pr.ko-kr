﻿---
title: Microsoft Lync 클라이언트에 대한 포트 범위 구성
TOCTitle: Microsoft Lync 클라이언트에 대한 포트 범위 구성
ms:assetid: 287d5cea-7ada-461c-9b4a-9da2af315e71
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/JJ204760(v=OCS.15)
ms:contentKeyID: 49303121
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Microsoft Lync 클라이언트에 대한 포트 범위 구성

 

_**마지막으로 수정된 항목:** 2015-03-09_

기본적으로 Lync 클라이언트 응용 프로그램은 통신 세션을 수행할 때 포트 1024에서 65535 사이의 어떤 포트나 사용할 수 있습니다. 클라이언트에 대해 특정 포트 범위가 자동으로 사용하도록 설정되지 않기 때문입니다. 그러나 서비스 품질을 사용하려면 오디오, 비디오, 미디어, 응용 프로그램, 공유, 파일 전송 등의 여러 트래픽 유형을 일련의 고유한 포트 범위에 다시 할당해야 합니다. 이 작업은 Set-CsConferencingConfiguration cmdlet을 사용하여 수행할 수 있습니다.

Microsoft Lync Server 2013 관리 셸 내에서 다음 명령을 실행하면 현재 통신 세션에 사용되는 포트 범위를 확인할 수 있습니다.

    Get-CsConferencingConfiguration

Lync Server 2013 설치 후 회의 설정을 변경하지 않았다고 가정할 때 다음과 같은 속성 값을 포함하는 정보가 반환됩니다.

    ClientMediaPortRangeEnabled : False
    ClientAudioPort             : 5350
    ClientAudioPortRange        : 40
    ClientVideoPort             : 5350
    ClientVideoPortRange        : 40
    ClientAppSharingPort        : 5350
    ClientAppSharingPortRange   : 40
    ClientFileTransferPort      : 5350
    ClientTransferPortRange     : 40

위의 출력을 자세히 보면 두 가지 중요한 사항을 확인할 수 있습니다. 먼저, ClientMediaPortRangeEnabled 속성이 False로 설정되어 있습니다.

    ClientMediaPortRangeEnabled : False

이 사항이 중요한 이유는, 이 속성이 False로 설정되어 있으면 Lync 클라이언트가 통신 세션을 수행할 때 포트 1024에서 65535 사이에서 사용 가능한 임의의 포트를 사용하기 때문입니다. ClientMediaPort 또는 ClientVideoPort 등의 다른 포트 설정을 사용하는 경우에도 마찬가지입니다. 지정된 포트 집합만 사용하도록 제한하려면(서비스 품질 구현을 계획하는 경우 이처럼 포트 사용을 제한해야 함) 먼저 클라이언트 미디어 포트 범위를 사용하도록 설정해야 합니다. 이렇게 하려면 다음 Windows PowerShell 명령을 사용하면 됩니다.

    Set-CsConferencingConfiguration -ClientMediaPortRangeEnabled $True

위의 명령은 회의 구성 설정의 전역 컬렉션에 대해 클라이언트 미디어 포트 범위를 사용하도록 설정합니다. 그러나 이러한 설정은 사이트 범위 및/또는 서비스 범위(회의 서버 서비스에 한함)에도 적용할 수 있습니다. 특정 사이트 또는 서버에 대해 클라이언트 미디어 포트 범위를 사용하도록 설정하려면 Set-CsConferencingConfiguration을 호출할 때 해당 사이트 또는 서버의 Identity를 지정합니다.

    Set-CsConferencingConfiguration -Identity "site:Redmond" -ClientMediaPortRangeEnabled $True

또는 이 명령을 사용하여 모든 회의 구성 설정에 대해 포트 범위를 동시에 사용하도록 설정할 수도 있습니다.

    Get-CsConferencingConfiguration | Set-CsConferencingConfiguration  -ClientMediaPortRangeEnabled $True

위의 출력에서 두 번째로 중요한 사항은 예제 출력에서 기본적으로 각 네트워크 트래픽 유형에 대해 설정된 미디어 포트 범위가 동일하다는 점입니다.

    ClientAudioPort             : 5350
    ClientVideoPort             : 5350
    ClientAppSharingPort        : 5350
    ClientFileTransferPort      : 5350

QoS를 구현하려면 이러한 각 포트 범위가 고유해야 합니다. 예를 들어 포트 범위를 다음과 같이 구성할 수 있습니다.


<table>
<colgroup>
<col style="width: 33%" />
<col style="width: 33%" />
<col style="width: 33%" />
</colgroup>
<thead>
<tr class="header">
<th>클라이언트 트래픽 유형</th>
<th>포트 시작</th>
<th>포트 범위</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>오디오</p></td>
<td><p>50020</p></td>
<td><p>20</p></td>
</tr>
<tr class="even">
<td><p>비디오</p></td>
<td><p>58000</p></td>
<td><p>20</p></td>
</tr>
<tr class="odd">
<td><p>응용 프로그램 공유</p></td>
<td><p>42000</p></td>
<td><p>20</p></td>
</tr>
<tr class="even">
<td><p>파일 전송</p></td>
<td><p>42020</p></td>
<td><p>20</p></td>
</tr>
</tbody>
</table>


위의 표에서 클라이언트 포트 범위는 서버에 대해 구성된 포트 범위의 하위 집합을 나타냅니다. 예를 들어 서버에서 응용 프로그램 공유는 포트 40803~49151을 사용하도록 구성되었습니다. 반면 클라이언트 컴퓨터에서는 응용 프로그램 공유가 포트 42000~42019를 사용하도록 구성되었습니다. 이러한 구성 역시 기본적으로 QoS를 보다 쉽게 관리하기 위한 것입니다. 클라이언트 포트는 서버에서 사용되는 포트의 하위 집합이 아니어도 됩니다. 예를 들어 클라이언트 컴퓨터에서는 응용 프로그램 공유가 포트 10000~10019를 사용하도록 구성할 수도 있습니다. 그러나 클라이언트 포트 범위를 서버 포트 범위의 하위 집합으로 지정하는 것이 좋습니다.

또한 서버에서는 응용 프로그램 공유용으로 포트 8348개가 설정되었는데 클라이언트에서는 응용 프로그램 공유용으로 포트가 20개만 설정되었음을 확인할 수 있습니다. 이러한 구성 역시 사용하는 것이 좋기는 하지만 반드시 지켜야 하는 규칙은 아닙니다. 일반적으로 사용 가능한 각 포트는 단일 통신 세션을 나타낸다고 간주할 수 있습니다. 포트 범위에서 포트 100개를 사용할 수 있으면 해당하는 컴퓨터가 지정된 시간에 최대 100개의 통신 세션에 참가할 수 있다는 의미입니다. 서버는 클라이언트보다 훨씬 많은 대화에 참가하므로 클라이언트보다 서버에 더 많은 수의 포트를 열어 두는 것이 적절합니다. 클라이언트에서 응용 프로그램 공유용으로 포트 20개를 설정하면 사용자가 지정된 장치에서 동시에 20개의 응용 프로그램 공유 세션에 참가할 수 있습니다. 대부분의 사용자에게는 해당 값이면 충분합니다.

위의 포트 범위를 회의 구성 설정의 전역 컬렉션에 할당하려면 다음 Lync Server 관리 셸 명령을 사용하면 됩니다.

    Set-CsConferencingConfiguration -Identity global -ClientAudioPort 50020 -ClientAudioPortRange 20 -ClientVideoPort 58000 -ClientVideoPortRange 20 -ClientAppSharingPort 42000 -ClientAppSharingPortRange 20 - ClientFileTransferPort 42020 -ClientFileTransferPortRange 20

또는 다음 명령을 사용하여 모든 회의 구성 설정에 대해 동일한 포트 범위를 할당합니다.

    Get-CsConferencingConfiguration | Set-CsConferencingConfiguration -ClientAudioPort 50020 -ClientAudioPortRange 20 -ClientVideoPort 58000 -ClientVideoPortRange 20 -ClientAppSharingPort 42000 -ClientAppSharingPortRange 20 - ClientFileTransferPort 42020 -ClientFileTransferPortRange 20

개별 사용자는 Lync에서 로그오프했다가 다시 로그온해야 이러한 변경 내용이 적용됩니다.


> [!NOTE]
> 명령 하나를 사용하여 클라이언트 미디어 포트 범위를 사용하도록 설정한 다음 해당 포트 범위를 할당할 수도 있습니다. 예를 들면 다음과 같습니다.<BR><CODE>Set-CsConferencingConfiguration -ClientMediaPortRangeEnabled $True -ClientAudioPort 50020 -ClientAudioPortRange 20 -ClientVideoPort 58000 -ClientVideoPortRange 20 -ClientAppSharingPort 42000 -ClientAppSharingPortRange 20 -ClientFileTransferPort 42020 -ClientFileTransferPortRange 20</CODE>


