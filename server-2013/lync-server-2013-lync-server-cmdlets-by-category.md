---
title: 범주별 Lync Server 2013 Cmdlet
TOCTitle: 범주별 Lync Server 2013 Cmdlet
ms:assetid: 4ce274d7-b0ec-40b8-b85e-9a0613916ffb
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg398306(v=OCS.15)
ms:contentKeyID: 49303570
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# 범주별 Lync Server 2013 Cmdlet

 

_**마지막으로 수정된 항목:** 2015-03-09_

Microsoft Lync Server 2013에는 관리자가 명령줄에서 Lync Server을 관리할 수 있도록 설계된 550개의 cmdlet이 포함되어 있습니다. Lync Server 관리 셸에서 cmdlet에 액세스합니다. 다음과 같은 명령을 입력하여 명령줄에서 직접 cmdlet에 대한 도움말을 검색할 수 있습니다.

    Get-Help New-CsVoicePolicy -Full

위의 명령은 **New-CsVoicePolicy** cmdlet에 대해 사용 가능한 모든 도움말을 검색합니다. **New-CsVoicePolicy**에 대한 참조를, 도움말을 검색할 cmdlet의 이름으로 바꿉니다.

Microsoft Lync Server 2013를 관리하는 데 사용할 수 있는 전체 cmdlet 목록을 검색하려면 Lync Server 관리 셸 명령 프롬프트에 다음을 입력합니다.

    Get-Command * -Module Lync -CommandType cmdlet

필요한 cmdlet을 모르는 경우를 위해 분류된 cmdlet 목록 및 해당 도움말 항목도 제공됩니다. 여러 범주에 나오는 cmdlet도 있습니다. 이러한 cmdlet은 제품의 여러 영역에 적용되므로 의도적으로 여러 번 표시된 것입니다. 범주 목록은 다음과 같습니다.

## 이 단원의 내용


<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p><a href="lync-server-2013-user-management-cmdlets.md">사용자 관리 Cmdlet</a></p></td>
<td><p><a href="lync-server-2013-voice-application-cmdlets.md">음성 응용 프로그램 Cmdlet</a></p></td>
</tr>
<tr class="even">
<td><p><a href="lync-server-2013-client-management-cmdlets.md">클라이언트 관리 Cmdlet</a></p></td>
<td><p><a href="lync-server-2013-advanced-enterprise-voice-cmdlets.md">고급 Enterprise Voice Cmdlet</a></p></td>
</tr>
<tr class="odd">
<td><p><a href="lync-server-2013-im-and-presence-cmdlets.md">IM 및 현재 상태 Cmdlet</a></p></td>
<td><p><a href="lync-server-2013-pstn-connectivity-cmdlets.md">PSTN 연결 Cmdlet</a></p></td>
</tr>
<tr class="even">
<td><p><a href="lync-server-2013-conferencing-cmdlets.md">회의 Cmdlet</a></p></td>
<td><p><a href="lync-server-2013-phones-and-devices-cmdlets.md">전화 및 장치 Cmdlet</a></p></td>
</tr>
<tr class="odd">
<td><p><a href="lync-server-2013-infrastructure-and-deployment-cmdlets.md">인프라 및 배포 Cmdlet</a></p></td>
<td><p><a href="lync-server-2013-migration-and-coexistence-cmdlets.md">마이그레이션 및 동시 사용 Cmdlet</a></p></td>
</tr>
<tr class="even">
<td><p><a href="lync-server-2013-security-cmdlets.md">보안 Cmdlet</a></p></td>
<td><p><a href="lync-server-2013-lync-server-management-shell-configuration-cmdlets.md">Lync Server 관리 셸 구성 Cmdlet</a></p></td>
</tr>
<tr class="odd">
<td><p><a href="lync-server-2013-server-roles-and-services-cmdlets.md">서버 역할 및 서비스 Cmdlet</a></p></td>
<td><p><a href="lync-server-2013-mobility-cmdlets.md">모바일 기능 cmdlet</a></p></td>
</tr>
<tr class="even">
<td><p><a href="lync-server-2013-application-management-cmdlets.md">응용 프로그램 관리 Cmdlet</a></p></td>
<td><p><a href="lync-server-2013-persistent-chat-server-cmdlets.md">영구 채팅 서버 Cmdlet</a></p></td>
</tr>
<tr class="odd">
<td><p><a href="lync-server-2013-federation-and-external-access-cmdlets.md">Lync Server 2013의 페더레이션 및 외부 액세스 Cmdlet</a></p></td>
<td><p><a href="lync-server-2013-centralized-logging-cmdlets.md">중앙화된 로깅 Cmdlet</a></p></td>
</tr>
<tr class="even">
<td><p><a href="lync-server-2013-enterprise-voice-cmdlets.md">Enterprise Voice Cmdlet</a></p></td>
<td><p></p></td>
</tr>
</tbody>
</table>


## 참고 항목

#### 기타 리소스

[Lync Server PowerShell 블로그](http://go.microsoft.com/fwlink/?linkid=203150%26clcid=0x412)

