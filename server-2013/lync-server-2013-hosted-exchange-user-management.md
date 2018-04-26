---
title: 'Lync Server 2013: 호스팅된 Exchange 사용자 관리'
TOCTitle: 호스팅된 Exchange 사용자 관리
ms:assetid: e8723af5-0604-4d7d-bad2-463a9832efb4
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg399037(v=OCS.15)
ms:contentKeyID: 49305387
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Lync Server 2013의 호스팅된 Exchange 사용자 관리

 

_**마지막으로 수정된 항목:** 2015-03-09_

사서함이 호스팅된 Exchange 서비스에 있는 Lync Server 2013 사용자에게 음성 사서함 서비스를 제공하려면 사용자 계정이 호스팅된 음성 사서함을 사용할 수 있도록 설정해야 합니다.


> [!NOTE]
> Lync Server 2013 사용자가 호스팅된 음성 사서함을 사용할 수 있도록 설정하려면 해당 사용자 계정에 적용할 호스팅된 음성 사서함 정책을 배포해야 합니다. 호스팅된 음성 사서함을 사용할 수 있도록 설정할 사용자에게 적용되는 경우에는 정책 범위를 전역, 사이트 또는 사용자별로 지정할 수 있습니다. 자세한 내용은 <A href="lync-server-2013-hosted-voice-mail-policies.md">Lync Server 2013의 호스팅된 음성 메일 정책</A>을 참조하십시오.



## msExchUCVoiceMailSettings 특성

Lync Server 2013에는 **msExchUCVoiceMailSettings**라는 새로운 사용자 특성이 도입되었으며, 이 특성은 Lync Server 2013 Active Directory 스키마 준비의 일부로 만들어집니다. 이 다중값 특성에는 Lync Server 2013 및 호스팅된 Exchange 서비스에서 공유된 음성 사서함 설정이 포함됩니다.

경우에 따라 호스팅된 Exchange 서비스는 Exchange UM을 사용하도록 설정하는 프로세스나 사서함을 호스팅된 Exchange Server로 전송하는 프로세스 동안 msExchUCVoiceMailSettings 특성의 값을 설정하기도 합니다. 이 특성이 Exchange에서 설정되지 않는 경우 Lync Server 2013 관리자는 이 항목 앞부분에서 설명한 대로 Set-CsUser cmdlet를 실행하여 이 특성을 설정해야 합니다.

다음 표에 특성의 키/값 쌍 및 저자가 나와 있습니다.

### msExchUCVoiceMailSettings 특성 키/값 쌍

<table>
<colgroup>
<col style="width: 33%" />
<col style="width: 33%" />
<col style="width: 33%" />
</colgroup>
<thead>
<tr class="header">
<th>값</th>
<th>저자</th>
<th>의미</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>ExchangeHostedVoiceMail=1</p></td>
<td><p>Exchange</p></td>
<td><p>사용자가 Exchange Server에서 호스팅된 UM 액세스를 사용할 수 있습니다. Exchange UM 라우팅 응용 프로그램에서 사용자의 호스팅된 음성 사서함 정책을 확인하여 라우팅 세부 정보를 검토합니다.</p></td>
</tr>
<tr class="even">
<td><p>ExchangeHostedVoiceMail=0</p></td>
<td><p>Exchange</p></td>
<td><p>사용자가 Exchange Serve에서 액세스된 호스팅된 UM을 사용할 수 없습니다.</p></td>
</tr>
<tr class="odd">
<td><p>CsHostedVoiceMail=1</p></td>
<td><p>Lync Server</p></td>
<td><p>사용자가 Lync Server 2013에서 호스팅된 UM 액세스를 사용할 수 있습니다. Lync Server 2013 ExUM 라우팅 응용 프로그램에서 사용자의 호스팅된 음성 사서함 정책을 확인하여 라우팅 세부 정보를 검토합니다.</p></td>
</tr>
<tr class="even">
<td><p>CsHostedVoiceMail=0</p></td>
<td><p>Lync Server</p></td>
<td><p>사용자가 Lync Server 2013에서 호스팅된 UM 액세스를 사용할 수 없습니다.</p></td>
</tr>
</tbody>
</table>



> [!NOTE]
> 특성에 이미 Lync Server 2013 키/값 쌍(CSHostedVoiceMail=0 또는 CSHostedVoiceMail=1) 중 하나가 아닌 다른 값이 있는 경우 특성이 다른 응용 프로그램에서 관리될 수 있다는 경고가 표시됩니다. 예를 들어 키/값 쌍 ExchangeHostedVoiceMail=0 또는 ExchangeHostedVoiceMail=1이 이미 있는 경우 경고가 표시됩니다. 이 경우 Active Directory에서 편집하여 값을 변경하거나 다음 cmdlet를 실행하여 값을 null로 설정합니다.<BR>Set-CsUser –identity user –HostedVoicemail $null



## 사용자가 호스팅된 음성 메일을 사용할 수 있도록 설정

사용자의 음성 사서함 통화가 호스팅된 Exchange UM으로 라우팅되도록 하려면 Set-CsUser cmdlet를 실행하여 *HostedVoiceMail* 매개 변수의 값을 설정해야 합니다. 이 매개 변수는 "음성 사서함 호출" 표시기를 켜도록 Lync Server 2013에 신호를 보내기도 합니다.

  - 다음 예는 Pilar Ackerman의 사용자 계정이 호스팅된 음성 메일을 사용하도록 설정합니다.
    
        Set-CsUser -Identity "Pilar Ackerman" -HostedVoiceMail $True
    
    cmdlet가 호스팅된 음성 메일 정책(전역, 사이트 수준 또는 사용자별)이 이 사용자에게 적용되는지 확인합니다. 정책이 적용되지 않으면 cmdlet가 실패합니다.

  - 다음 예는 Pilar Ackerman의 사용자 계정이 호스팅된 음성 메일을 사용할 수 없도록 설정합니다.
    
        Set-CsUser -Identity "Pilar Ackerman" -HostedVoiceMail $False
    
    cmdlet가 호스팅된 음성 메일 정책(전역, 사이트 수준 또는 사용자별)이 이 사용자에게 적용되지 않는지 확인합니다. 정책이 적용되면 cmdlet가 실패합니다.

Set-CsUser cmdlet를 사용하는 방법에 대한 자세한 내용은 Lync Server 관리 셸 설명서를 참조하십시오.

