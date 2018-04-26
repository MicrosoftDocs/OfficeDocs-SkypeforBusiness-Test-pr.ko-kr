---
title: 백업 및 복원 워크시트
TOCTitle: 백업 및 복원 워크시트
ms:assetid: 26c78155-0306-41ac-845b-7ad58000a1d6
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Hh202169(v=OCS.15)
ms:contentKeyID: 52056809
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# 백업 및 복원 워크시트

 

_**마지막으로 수정된 항목:** 2015-03-09_

조직의 백업 및 복원 계획에는 데이터 및 설정을 백업하는 방법 및 시간에 대한 세부 정보가 포함됩니다. 여기서 제공되는 워크시트를 사용하여 특정 배포 및 조직의 백업과 복원 요구 사항에 맞게 이 정보를 문서화할 수 있습니다.

다음 워크시트를 사용하여 데이터베이스를 백업 및 복원하는 데 필요한 정보, 파일 저장소, 그리고 Lync Server 풀 또는 Standard Edition 서버에 대한 설정 정보를 기록합니다. Lync Server를 복원해야 할 때 즉시 사용할 수 있도록 이러한 워크시트의 복사본을 하나 이상 안전한 위치에 보관하십시오.


> [!NOTE]
> 이 섹션의 워크시트에는 Lync Server 데이터베이스 및 서버의 데이터 및 설정을 복원하는 데 필요한 정보만 포함됩니다. 운영 체제 및 기타 소프트웨어 다시 설치를 위한 정보와 같은 다른 복원 정보를 문서화해야 할 경우 조직의 배포 계획과 백업 및 복원 계획을 사용하여 이러한 요구 사항을 해결합니다.



## 데이터베이스 백업 및 복원 워크시트

다음 표를 사용하여 Lync Server 데이터베이스를 백업 및 복원하는 데 필요한 정보를 기록합니다.

### 백업 및 복원에 대한 데이터베이스 정보

<table style="width:100%;">
<colgroup>
<col style="width: 14%" />
<col style="width: 14%" />
<col style="width: 14%" />
<col style="width: 14%" />
<col style="width: 14%" />
<col style="width: 14%" />
<col style="width: 14%" />
</colgroup>
<thead>
<tr class="header">
<th>데이터베이스</th>
<th>서버 이름(FQDN)</th>
<th>백업 일정</th>
<th>데이터베이스 백업 도구</th>
<th>백업 집합</th>
<th>백업 대상</th>
<th>참고</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>사용자 데이터에 대한 백 엔드 서버의 RTC 데이터베이스</p></td>
<td><p>                    </p></td>
<td><p>                    </p></td>
<td><p><strong>Export-CsUserData</strong> cmdlet</p></td>
<td><p>이름:</p>
<p>만료:</p>
<p>                   </p></td>
<td><p>                    </p></td>
<td><p>                    </p></td>
</tr>
<tr class="even">
<td><p>보관 데이터베이스 서버의 LcsLog(기본 이름) 데이터베이스</p></td>
<td><p> </p></td>
<td><p> </p></td>
<td><p>SQL Server 관리 도구</p></td>
<td><p>이름:</p>
<p>만료:</p></td>
<td><p> </p></td>
<td><p> </p></td>
</tr>
<tr class="odd">
<td><p>CDR(통화 정보 기록)에 대한 모니터링 데이터베이스 서버의 LcsCdr 데이터베이스</p></td>
<td><p> </p></td>
<td><p> </p></td>
<td><p>SQL Server 관리 도구</p></td>
<td><p>이름:</p>
<p>만료:</p></td>
<td><p> </p></td>
<td><p> </p></td>
</tr>
<tr class="even">
<td><p>QoE(체감 품질) 데이터에 대한 모니터링 데이터베이스 서버의 QoEMetrics 데이터베이스</p></td>
<td><p> </p></td>
<td><p> </p></td>
<td><p>SQL Server 관리 도구</p></td>
<td><p>이름:</p>
<p>만료:</p></td>
<td><p> </p></td>
<td><p> </p></td>
</tr>
<tr class="odd">
<td><p>영구 채팅 데이터베이스</p></td>
<td><p></p></td>
<td><p></p></td>
<td><p>SQL Server 관리 도구 또는 <strong>Export-CsPersistentChatData</strong> cmdlet</p></td>
<td><p>이름:</p>
<p>만료:</p></td>
<td><p></p></td>
<td><p></p></td>
</tr>
</tbody>
</table>


다음 데이터베이스에는 백업 또는 복원이 필요하지 않습니다.

  - Rtcdyn. 이 데이터베이스에서 임시 사용자 데이터는 서비스를 복원하는 데 필요하지 않습니다.

  - Rtcab. 주소록 데이터베이스는 Active Directory 도메인 서비스의 GAL(전체 주소 목록)에서 자동으로 다시 만들어집니다.

  - Rgsdyn. 이 데이터베이스에서 임시 응답 그룹 서비스 데이터는 서비스를 복원하는 데 필요하지 않습니다.

  - Cpsdyn. 통화 대기 응용 프로그램에 대한 동적 정보는 서비스를 복원하는 데 필요하지 않습니다.

  - MgcComp. 영구 채팅용 복원 데이터베이스는 서비스를 복원하는 데 필요하지 않습니다.

## 파일 저장소 백업 및 복원 워크시트

다음 표를 사용하여 파일 저장소를 백업 및 복원하는 데 필요한 정보를 기록합니다. 파일 저장소에는 모임 콘텐츠 메타데이터, 모임 준수 로그, 장치 업데이트에 대한 업데이트 로그, 응답 그룹에 대한 오디오 파일, 통화 대기, 알림 응용 프로그램과 같은 데이터가 포함됩니다.

### 백업 및 복원에 대한 파일 저장소 정보

<table style="width:100%;">
<colgroup>
<col style="width: 14%" />
<col style="width: 14%" />
<col style="width: 14%" />
<col style="width: 14%" />
<col style="width: 14%" />
<col style="width: 14%" />
<col style="width: 14%" />
</colgroup>
<thead>
<tr class="header">
<th>콘텐츠</th>
<th>서버 이름(FQDN)</th>
<th>백업 일정</th>
<th>파일 시스템 백업 도구</th>
<th>백업할 파일 공유*</th>
<th>백업 대상</th>
<th>참고</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Lync Server 파일 저장소</p></td>
<td><p></p></td>
<td><p></p></td>
<td><p>표준 백업 도구(예: Robocopy)</p></td>
<td><p>Enterprise Edition에 대한 파일 서버에 있습니다. 기본적으로는 Standard Edition 배포에 대한 Standard Edition에 있습니다. 일반적으로 사이트당 하나입니다.</p></td>
<td><p></p></td>
<td><p>이름이 <strong>Meeting.Active</strong>인 파일은 백업해서는 안됩니다. 이러한 파일은 사용 중이며 모임이 수행되는 동안 잠깁니다.</p></td>
</tr>
</tbody>
</table>


## 설정 백업 및 복원 워크시트

다음 표를 사용하여 설정을 백업 및 복원하는 데 필요한 정보를 기록합니다.

### 백업 및 복원에 대한 설정 정보

<table style="width:100%;">
<colgroup>
<col style="width: 14%" />
<col style="width: 14%" />
<col style="width: 14%" />
<col style="width: 14%" />
<col style="width: 14%" />
<col style="width: 14%" />
<col style="width: 14%" />
</colgroup>
<thead>
<tr class="header">
<th>데이터베이스</th>
<th>서버 이름(FQDN)</th>
<th>백업 일정</th>
<th>백업 도구</th>
<th>구성 파일(.xml) 이름</th>
<th>백업 위치</th>
<th>참고</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>토폴로지 구성에 대한 중앙 관리 저장소의 Xds 데이터베이스(전역)</p></td>
<td><p>                    </p></td>
<td><p>                    </p></td>
<td><p><strong>Export-CsConfiguration</strong> cmdlet</p></td>
<td><p>                   </p></td>
<td><p>                    </p></td>
<td><p>                   </p></td>
</tr>
<tr class="even">
<td><p>E9-1-1 위치 정보에 대한 중앙 관리 저장소의 Lis 데이터베이스(전역)</p></td>
<td><p> </p></td>
<td><p> </p></td>
<td><p><strong>Export-CsLisConfiguration</strong> cmdlet</p></td>
<td><p></p></td>
<td><p> </p></td>
<td><p>                    </p></td>
</tr>
<tr class="odd">
<td><p>응답 그룹 구성에 대한 백 엔드 서버의 RgsConfig 데이터베이스(풀)</p></td>
<td><p> </p></td>
<td><p> </p></td>
<td><p><strong>Export-CsRgsConfiguration</strong> cmdlet</p></td>
<td><p></p></td>
<td><p> </p></td>
<td><p>                    </p></td>
</tr>
</tbody>
</table>

