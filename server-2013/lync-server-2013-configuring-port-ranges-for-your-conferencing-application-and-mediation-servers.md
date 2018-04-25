---
title: 회의, 응용 프로그램 및 중재 서버에 대한 포트 범위 구성
TOCTitle: 회의, 응용 프로그램 및 중재 서버에 대한 포트 범위 구성
ms:assetid: 4d6eaa5d-0127-453f-be6a-e55384772d83
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/JJ204872(v=OCS.15)
ms:contentKeyID: 49303592
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# 회의, 응용 프로그램 및 중재 서버에 대한 포트 범위 구성

 

_**마지막으로 수정된 항목:** 2015-04-30_

QoS(서비스 품질)를 구현하기 위해서는 회의, 응용 프로그램 및 중재 서버에서 오디오, 비디오 및 응용 프로그램 공유에 대한 동일한 포트 범위를 구성해야 합니다. 또한 이러한 포트 범위는 어떠한 방식으로든 서로 겹쳐서는 안됩니다. 간단한 예로, 회의 서버에서 비디오를 위해 10000~10999 포트를 사용한다고 가정해보십시오. 이 경우에는 응용 프로그램 및 중재 서버에서도 10000~10999 포트를 비디오용으로 예약해야 합니다. 그렇지 않으면 QoS가 예상한 대로 작동하지 않습니다.

이와 비슷하게, 10000~10999 포트를 비디오용으로 예약하지만 10500~11999 포트는 오디오용으로 예약한다고 가정해보십시오. 이 경우에는 포트 범위가 겹치기 때문에 QoS(서비스 품질) 문제가 발생할 수 있습니다. QoS에서는 각 형식이 고유한 포트 집합을 가져야 합니다. 10000~10999 포트를 비디오용으로 사용한다면 다른 범위를 사용해야 합니다(예: 오디오에 11000~11999 사용).

기본적으로 오디오 및 비디오 포트 범위는 Microsoft Lync Server 2013에서 서로 겹쳐지지 않습니다. 하지만 응용 프로그램 공유에 지정된 포트 범위는 오디오 및 비디오 포트 범위와 겹쳐집니다. 즉, 이러한 범위 중 고유한 범위는 없습니다. Lync Server 2013 관리 셸 내에서 다음 3개 명령을 실행하면 회의, 응용 프로그램 및 중재 서버에서 기존 포트 범위를 확인할 수 있습니다.

    Get-CsService -ConferencingServer | Select-Object Identity, AudioPortStart, AudioPortCount, VideoPortStart, VideoPortCount, AppSharingPortStart, AppSharingPortCount
    
    Get-CsService -ApplicationServer | Select-Object Identity, AudioPortStart, AudioPortCount
    
    Get-CsService -MediationServer | Select-Object Identity, AudioPortStart, AudioPortCount


> [!WARNING]
> 앞의 명령에서 볼 수 있듯이, 각 포트 유형(오디오, 비디오 및 응용 프로그램 공유)에는 두 개의 개별 속성 값인 포트 시작 및 포트 개수 값이 지정됩니다. 포트 시작은 해당 형식에 사용되는 첫 번째 포트를 나타냅니다. 예를 들어 오디오 포트 시작이 50000이면 오디오 트래픽에 사용되는 첫 번째 포트가 포트 50000입니다. 오디오 포트 개수가 2(올바른 값은 아니지만 설명을 위해 사용됨)이면 오디오에 2개의 포트만 지정됩니다. 첫 번째 포트가 포트 50000이고 총 2개의 포트만 있으므로 두 번째 포트는 포트 50001이어야 합니다(포트 범위는 연속되어야 함). 따라서 오디오에 대한 포트 범위는 50000~50001까지입니다.<BR>응용 프로그램 서버 및 중재 서버는 오디오에 대해서만 QoS를 지원합니다. 응용 프로그램 서버 또는 중재 서버에서는 비디오 또는 응용 프로그램 공유 포트를 변경할 필요가 없습니다.



앞의 세 명령을 실행하면 Lync Server 2013에 대한 기본 포트 값이 다음과 같이 구성된다는 것을 알 수 있습니다.


<table>
<colgroup>
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
</colgroup>
<thead>
<tr class="header">
<th>속성</th>
<th>회의 서버</th>
<th>응용 프로그램 서버</th>
<th>중재 서버</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>AudioPortStart</p></td>
<td><p>49152</p></td>
<td><p>49152</p></td>
<td><p>49152</p></td>
</tr>
<tr class="even">
<td><p>AudioPortCount</p></td>
<td><p>8348</p></td>
<td><p>8348</p></td>
<td><p>8348</p></td>
</tr>
<tr class="odd">
<td><p>VideoPortStart</p></td>
<td><p>57501</p></td>
<td><p>--</p></td>
<td><p>--</p></td>
</tr>
<tr class="even">
<td><p>VideoPortCount</p></td>
<td><p>8034</p></td>
<td><p>--</p></td>
<td><p>--</p></td>
</tr>
<tr class="odd">
<td><p>ApplicationSharingPortStart</p></td>
<td><p>49152</p></td>
<td><p>--</p></td>
<td><p>--</p></td>
</tr>
<tr class="even">
<td><p>ApplicationSharingPortCount</p></td>
<td><p>16383</p></td>
<td><p>--</p></td>
<td><p>--</p></td>
</tr>
</tbody>
</table>


앞에서 설명한 것처럼 QoS에 대한 Lync Server 포트를 구성할 때는 다음 사항을 확인해야 합니다. 1) 오디오 포트 설정이 회의, 응용 프로그램 및 중재 서버 간에 동일해야 합니다. 2) 포트 범위가 겹치지 않습니다. 앞의 표를 자세히 살펴보면 3개의 서버 유형 모두 포트 범위가 동일한 것을 알 수 있습니다. 예를 들어 시작 오디오 포트는 각 서버 유형 모두 포트 49152로 설정되었고 각 서버에서 오디오용으로 예약된 총 포트 수도 동일하게 8348입니다. 포트 범위가 겹치고 오디오 포트가 모드 포트 49152에서 시작합니다. 하지만 응용 프로그램 공유에 대해서는 포트를 별도로 설정합니다. QoS(서비스 품질)를 올바르게 사용하기 위해서는 고유한 포트 범위를 사용하도록 응용 프로그램 공유를 다시 구성해야 합니다. 예를 들어 포트 40803에서 시작하고 8348개의 포트를 사용하도록 응용 프로그램 공유를 구성할 수 있습니다. (왜 8348개의 포트일까요? 40803 + 8348로 해당 숫자를 합하면 응용 프로그램 공유에 40803~49151 포트가 사용됩니다. 오디오 포트는 포트 49152 전까지는 시작하지 않으므로 더 이상 아무 포트 범위도 겹치지 않습니다.)

응용 프로그램 공유에 대해 새 포트 범위를 선택한 후에는 Set-CsConferencingServer cmdlet을 사용하여 항목을 변경할 수 있습니다. 이러한 서버에서 응용 프로그램 공유 트래픽이 처리되지 않기 때문에 이러한 항목은 응용 프로그램 서버 또는 중재 서버에서 변경할 필요가 없습니다. 오디오 트래픽에 사용되는 포트를 다시 지정할 경우에만 해당 서버에서 포트 값을 변경해야 합니다.

단일 회의 서버에서 응용 프로그램 공유에 대한 포트 값을 수정하려면 Lync Server 관리 셸 내에서 다음과 비슷한 형식의 명령을 실행합니다.

    Set-CsConferenceServer -Identity ConferencingServer:atl-cs-001.litwareinc.com -AppSharingPortStart 40803 -AppSharingPortCount 8348

모든 회의 서버에서 이러한 항목을 변경하려는 경우 대신 다음 명령을 실행할 수 있습니다.

    Get-CsService -ConferencingServer | ForEach-Object {Set-CsConferenceServer -Identity $_.Identity -AppSharingPortStart 40803 -AppSharingPortCount 8348}

포트 설정을 변경한 후에는 변경 내용의 영향을 받는 각 서비스를 중지하고 다시 시작해야 합니다.

회의 서버, 응용 프로그램 서버 및 중재 서버가 정확히 동일한 포트 범위를 공유할 필요는 없으며, 모든 서버에서 고유한 포트 범위를 별도로 설정하기만 하면 됩니다. 하지만 관리 측면에서는 모든 서버에서 동일한 포트 집합을 사용하는 것이 더 쉬울 것입니다.

