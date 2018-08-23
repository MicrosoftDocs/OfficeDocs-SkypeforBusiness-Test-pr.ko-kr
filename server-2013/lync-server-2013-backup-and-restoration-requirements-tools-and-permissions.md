---
title: '백업 및 복원 요구 사항: 도구 및 사용 권한'
TOCTitle: '백업 및 복원 요구 사항: 도구 및 사용 권한'
ms:assetid: 35ec2e33-f33e-4f84-9e64-6550fd78aa52
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Hh202171(v=OCS.15)
ms:contentKeyID: 52056820
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# 백업 및 복원 요구 사항: 도구 및 사용 권한

 

_**마지막으로 수정된 항목:** 2015-03-09_

이 항목에서는 Lync Server 2013을 백업 및 복원하기 위해 사용할 수 있는 도구, 필요한 권한 및 명령을 원격 또는 로컬로 실행할 수 있는지 여부에 대해 설명합니다. 구체적으로는 Lync Server에서 백업 및 복원용으로 제공되는 도구에 대해 중점적으로 설명합니다.

## 백업

Lync Server를 백업하려면 아래 표에 나와 있는 도구를 사용합니다. Lync Server를 백업하는 데 필요한 모든 명령은 스크립트로 지정하고 원격으로 실행할 수 있습니다.

### Lync Server 백업 도구

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th>백업할 항목:</th>
<th>사용할 도구 또는 cmdlet:</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>토폴로지 구성 데이터(Xds.mdf)</p></td>
<td><p>Export-CsConfiguration</p></td>
</tr>
<tr class="even">
<td><p>위치 정보 서비스(E9-1-1) 데이터(Lis.mdf)</p></td>
<td><p>Export-CsLisConfiguration</p></td>
</tr>
<tr class="odd">
<td><p>응답 그룹 구성 데이터(RgsConfig.mdf)</p></td>
<td><p>Export-CsRgsConfiguration</p></td>
</tr>
<tr class="even">
<td><p>영구 사용자 데이터(Rtcxds.mdf 데이터베이스)</p>
<p>전화 회의 ID</p></td>
<td><p>Export-CsUserData</p></td>
</tr>
<tr class="odd">
<td><ul>
<li><p>보관 데이터베이스(LcsLog.mdf)</p></li>
<li><p>통화 정보 기록 모니터링 데이터베이스(LcsCDR.mdf)</p></li>
<li><p>QoE 모니터링 데이터베이스(QoEMetrics.mdf)</p></li>
</ul></td>
<td><p>SQL Server 데이터베이스 도구(예: SQL Server Management Studio)</p></td>
</tr>
<tr class="even">
<td><p>영구 채팅 데이터베이스(Mgc.mdf)</p></td>
<td><p>SQL Server 백업 절차 또는 Export-CsPersistentChatData. Export-CsPersistentChatData를 사용하는 경우 영구 채팅 데이터를 파일로 내보냅니다.</p></td>
</tr>
<tr class="odd">
<td><p>모든 파일 저장소(Lync Server 파일 공유, 보관 파일 저장소)</p>


> [!NOTE]
> 이름이 <STRONG>Meeting.Active</STRONG>인 파일은 백업해서는 안됩니다. 이러한 파일은 사용 중이며 모임이 수행되는 동안 잠깁니다.


</td>
<td><p>표준 파일 시스템 관리 도구(예: Robocopy)</p></td>
</tr>
</tbody>
</table>


## 복원

Lync Server를 복원하려면 아래 표의 도구를 사용합니다. Lync Server를 복원하는 데 필요한 모든 명령은 스크립트로 지정할 수 있습니다. 일부 명령은 원격으로 실행할 수 있지만 아래 표에 지정된 것처럼 로컬로 실행해야 하는 명령도 있습니다.

### Lync Server 복원 도구

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th>수행할 작업:</th>
<th>사용할 도구 또는 cmdlet:</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>신규 또는 깨끗한 컴퓨터 구축</p></td>
<td><ul>
<li><p>Windows 운영 체제 설치 소프트웨어</p></li>
<li><p>SQL Server 설치 소프트웨어</p></li>
<li><p>내보낼 수 있는 개인 키를 사용하여 인증서를 복원할 경우 MMC(Microsoft Management Console) 스냅인 인증</p></li>
</ul></td>
</tr>
<tr class="even">
<td><p>파일 저장소 데이터 복원</p></td>
<td><p>표준 파일 시스템 관리 도구(예: Robocopy)</p></td>
</tr>
<tr class="odd">
<td><p>빈 데이터베이스를 다시 만들고 다음에 대한 권한을 설정합니다.</p>
<ul>
<li><p>중앙 관리 저장소</p></li>
<li><p>백 엔드 서버</p></li>
<li><p>모니터링 데이터베이스</p></li>
<li><p>보관 데이터베이스</p></li>
</ul></td>
<td><p>Install-CsDatabase</p></td>
</tr>
<tr class="even">
<td><p>Active Directory 도메인 서비스 포인터를 중앙 관리 저장소로 복원</p>


> [!NOTE]
> 언제라도 서비스 연결 지점이 손실될 경우 이 cmdlet을 다시 실행할 수 있습니다.


</td>
<td><p>Set-CsConfigurationStoreLocation</p></td>
</tr>
<tr class="odd">
<td><p>토폴로지, 정책 및 구성 설정을 중앙 관리 저장소(Xds.mdf)로 가져오기</p></td>
<td><p>Import-CsConfiguration</p></td>
</tr>
<tr class="even">
<td><p>토폴로지를 게시하고 사용하도록 설정</p></td>
<td><p>토폴로지 작성기</p>
<p>-또는-</p>
<p>Publish-CsTopology 및 Enable-CsTopology</p></td>
</tr>
<tr class="odd">
<td><p>마지막으로 게시된 토폴로지 사용</p></td>
<td><p>Enable-CsTopology</p></td>
</tr>
<tr class="even">
<td><p>Lync Server 구성 요소를 다시 설치</p></td>
<td><p>Lync Server 설치</p>


> [!NOTE]
> Lync Server 설치 폴더 또는 미디어에 있음(\setup\amd64\Setup.exe)


</td>
</tr>
<tr class="odd">
<td><p>위치 정보(E9-1-1) 데이터(Lis.mdf) 복원</p></td>
<td><p>Import-CsLisConfiguration</p></td>
</tr>
<tr class="even">
<td><p>영구 사용자 데이터(Rtcxds.mdf) 복원(Rtc.mdf)</p></td>
<td><p>Import-CsUserData</p></td>
</tr>
<tr class="odd">
<td><p>응답 그룹 구성 데이터 복원(RgsConfig.mdf)</p></td>
<td><p>Import-CsRgsConfiguration</p>


> [!NOTE]
> 데이터베이스에 응답 그룹 데이터가 없는 새로 배포한 풀에 구성을 복원하는 경우에는 -OverwriteOwner 옵션을 사용해야 합니다. 복원하는 데이터가 FQDN(정규화된 도메인 이름)이 같은 풀에 있더라도 이 옵션을 사용합니다. 그렇지 않으면 응답 그룹에 대한 대화 상대 개체가 Active Directory에 이미 있기 때문에 가져오기가 정상적으로 수행되지 않습니다.


</td>
</tr>
<tr class="even">
<td><p>다음 데이터베이스 복원:</p>
<ul>
<li><p>보관 데이터베이스(LcsLog.mdf)</p></li>
<li><p>모니터링 데이터베이스: 통화 정보 기록 데이터베이스(LcsCDR.mdf) 및 QoE 데이터베이스(QoEMetrics.mdf)</p></li>
</ul></td>
<td><p>SQL Server 데이터베이스 관리 도구</p></td>
</tr>
<tr class="odd">
<td><p>영구 채팅 데이터베이스(Mgs.mdf)</p></td>
<td><p>SQL Server 복원 절차 또는 Import-CsPersistentChatData. Export-CsPersistentChatData를 사용하여 만든 파일에 대해 Import-CsPersistentChatData를 사용할 수 있으며, 그러면 데이터가 영구 채팅 데이터베이스로 가져오기됩니다.</p></td>
</tr>
</tbody>
</table>


## 필요한 사용 권한

이 항목에서 설명하는 모든 명령을 수행하려면 사용자가 **RTCUniversalServerAdmins** 그룹의 구성원이어야 합니다. 대부분의 백업 및 복원 명령은 RBAC(역할 기반 액세스 제어)를 지원하지 않습니다. 단, 2개 영구 채팅 cmdlet(Export-CsPersistentChatData 및 Import-CsPersistentChatData)는 CsPersistentChatAdministrator 그룹 구성원인 사용자가 실행해야 합니다. 또한 Lync Server 배포 마법사를 실행하려면 사용자가 Local Administrators 그룹 구성원이어야 합니다.

