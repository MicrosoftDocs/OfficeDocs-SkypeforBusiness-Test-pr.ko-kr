---
title: 구성 설정 확인
TOCTitle: 구성 설정 확인
ms:assetid: 41dbf91c-f2e1-4b9a-88cf-959575558cf2
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/JJ204848(v=OCS.15)
ms:contentKeyID: 49303443
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# 구성 설정 확인

 

_**마지막으로 수정된 항목:** 2015-03-09_

토폴로지를 병합하고 **Import-CsLegacyConfiguration** cmdlet을 실행한 후, Office Communications Server 2007 R2 정책 및 설정을 Lync Server 2013으로 가져왔는지 확인하십시오. 다음 표에서는 확인해야 하는 정책 및 설정을 나열합니다.

## 마이그레이션 이후 확인할 정책 및 설정


<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th>이 작업을 사용하는 경우:</th>
<th>정책 및 설정 확인:</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>IM(인스턴트 메시징) 및 회의</p></td>
<td><p>현재 상태 정책</p>
<p>회의 정책</p></td>
</tr>
<tr class="even">
<td><p>전화 접속 회의 구성</p></td>
<td><p>전화 접속 액세스 번호</p>
<p>다이얼 플랜</p></td>
</tr>
<tr class="odd">
<td><p>Enterprise Voice</p></td>
<td><p>음성 정책</p>
<p>음성 경로</p>
<p>다이얼 플랜</p>
<p>PSTN 사용 설정</p></td>
</tr>
<tr class="even">
<td><p>Communicator Web Access</p></td>
<td><p>단순 URL</p></td>
</tr>
<tr class="odd">
<td><p>외부 사용자</p></td>
<td><p>외부 액세스 정책</p></td>
</tr>
<tr class="even">
<td><p>보관</p></td>
<td><p>보관 정책</p></td>
</tr>
</tbody>
</table>


## 정책 및 설정을 확인하려면

1.  Office Communications Server 2007 R2 환경에서 Communicator Web Access에 사용된 URL 외에도 다이얼 플랜의 이름(이전의 위치 프로필), 전화 접속 액세스 번호(회의 길잡이 액세스 전화 번호 및 영역), 음성 경로 및 이전 테이블에 나열된 정책을 기록합니다.

2.  Lync Server 2013 프런트 엔드 서버에서 Lync Server 제어판을 엽니다.

3.  가져온 회의 정책을 확인하려면 왼쪽 창에서 **회의** , **회의 정책** 을 차례로 클릭한 후 Office Communications Server 2007 R2 환경의 모든 회의 정책이 목록에 포함되었는지 확인합니다.
    

    > [!NOTE]
    > 이전 버전의 Office Communications Server의 <STRONG>모임</STRONG> 정책은 이제 Lync Server 2013에서 회의 정책이라고 합니다. 또한 이전 버전의 Office Communications Server의 <STRONG>익명 참가자</STRONG> 설정은 이제 Lync Server 2013 회의 정책의 설정입니다.

    

    > [!NOTE]
    > Office Communications Server 2007 R2에서 회의 정책이 <STRONG>사용자당 사용</STRONG> 이면 전역 정책 설정만 가져옵니다. 이 경우에 다른 회의 정책은 가져오지 않습니다.

    

    > [!NOTE]
    > Office Communications Server 2007 R2 회의 정책에서 <STRONG>익명 참가자</STRONG> 가 <STRONG>사용자당 적용</STRONG> 으로 설정된 경우, 마이그레이션 중에 두 개의 회의 정책이 만들어지며, 이 중에서 하나에는 <STRONG>AllowAnonymousParticipantsInMeetings</STRONG> 가 <STRONG>True</STRONG> 로 설정되고 다른 하나에는 <STRONG>AllowAnonymousParticipantsInMeetings</STRONG> 가 <STRONG>False</STRONG> 로 설정됩니다.



4.  가져온 다이얼 플랜을 확인하려면 **음성 라우팅** , **다이얼 플랜** 을 차례로 클릭한 후 Office Communicator 2007 R2 환경의 모든 다이얼 플랜이 목록에 포함되었는지 확인합니다.
    

    > [!NOTE]
    > Lync Server 2013에서 <STRONG>위치 프로필</STRONG> 은 이제 <STRONG>다이얼 플랜</STRONG> 이라고 부릅니다.



5.  가져온 음성 정책을 확인하려면 **음성 라우팅** , **음성 정책** 을 차례로 클릭한 후 Office Communicator 2007 R2 환경의 모든 음성 정책이 목록에 포함되었는지 확인합니다.
    

    > [!NOTE]
    > Office Communications Server 2007 R2 환경에서 음성 정책이 <STRONG>사용자당 사용</STRONG> 으로 설정되지 않은 경우 전역 정책 설정만 가져옵니다. 이 경우에 다른 음성 정책은 가져오지 않습니다.



6.  가져온 음성 경로를 확인하려면 **음성 라우팅** , **경로** 를 차례로 클릭한 후 Office Communicator 2007 R2 환경의 모든 음성 경로가 목록에 포함되었는지 확인합니다.

7.  가져온 PSTN 사용 설정을 확인하려면 **음성 라우팅** , **PSTN 사용** 을 차례로 클릭한 후 Office Communicator 2007 R2 환경의 PSTN 사용 설정이 목록에 포함되었는지 확인합니다.

8.  가져온 외부 액세스 정책을 확인하려면 **페더레이션 및 외부 액세스** , **외부 액세스 정책** 을 차례로 클릭한 후 Office Communicator 2007 R2 환경의 모든 외부 액세스 정책이 목록에 포함되었는지 확인합니다.

9.  보관 정책을 확인하려면 **모니터링 및 보관** , **보관 정책** 을 차례로 클릭한 후 Office Communications Server 2007 R2 환경의 모든 보관 정책이 목록에 포함되었는지 확인합니다.

10. Lync Server 관리 셸를 엽니다.

11. 현재 상태 정책을 확인하려면 명령줄에 다음을 입력합니다.
    
        Get-CsPresencePolicy
    
    **Identity** 매개 변수에서 이름을 보고 Office Communications Server 2007 R2 환경의 모든 현재 상태 정책을 가져왔는지 확인합니다.

## cmdlet을 사용하여 정책 및 설정을 확인하려면

1.  Lync Server 관리 셸를 엽니다.

2.  다음 표의 cmdlet을 실행하여 정책 및 설정을 확인합니다.
    
    이러한 cmdlet의 구문은 다음 예와 같습니다.
    
        Get-CsConferencingPolicy
    
    이러한 cmdlet에 대한 자세한 내용을 보려면 다음을 실행합니다.
    
        Get-Help <cmdlet name> -Detailed


<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th>이 정책 또는 설정에 대해:</th>
<th>이 cmdlet 사용:</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>현재 상태 정책</p></td>
<td><p><strong>Get-CsPresencePolicy</strong></p></td>
</tr>
<tr class="even">
<td><p>회의 정책</p></td>
<td><p><strong>Get-CsConferencingPolicy</strong></p></td>
</tr>
<tr class="odd">
<td><p>전화 접속 액세스 번호</p></td>
<td><p><strong>Get-CsDialInConferencingAccessNumber</strong></p></td>
</tr>
<tr class="even">
<td><p>다이얼 플랜</p></td>
<td><p><strong>Get-CsDialPlan</strong></p></td>
</tr>
<tr class="odd">
<td><p>음성 정책</p></td>
<td><p><strong>Get-CsVoicePolicy</strong></p></td>
</tr>
<tr class="even">
<td><p>음성 경로</p></td>
<td><p><strong>Get-CsVoiceRoute</strong></p></td>
</tr>
<tr class="odd">
<td><p>PSTN 사용</p></td>
<td><p><strong>Get-CsPstnUsage</strong></p></td>
</tr>
<tr class="even">
<td><p>URL</p></td>
<td><p><strong>Get-CsSimpleUrlConfiguration</strong></p></td>
</tr>
<tr class="odd">
<td><p>외부 액세스 정책</p></td>
<td><p><strong>Get-CsExternalAccessPolicy</strong></p></td>
</tr>
<tr class="even">
<td><p>보관 정책</p></td>
<td><p><strong>Get-CsArchivingPolicy</strong></p></td>
</tr>
</tbody>
</table>

