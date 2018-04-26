---
title: 'Lync Server 2013의 백업 및 복원 요구 사항: 데이터'
TOCTitle: 'Lync Server 2013의 백업 및 복원 요구 사항: 데이터'
ms:assetid: ecfb8e4d-cb4f-476d-9772-4486bd683c04
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Hh202194(v=OCS.15)
ms:contentKeyID: 52056981
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Lync Server 2013의 백업 및 복원 요구 사항: 데이터

 

_**마지막으로 수정된 항목:** 2013-03-26_

Lync Server에서는 데이터베이스에 저장된 설정 및 구성 정보와 데이터베이스 및 파일 저장소에 저장된 데이터를 사용합니다. 이 항목에서는 조직에서 오류 또는 중단이 발생할 경우 서비스를 복원할 수 있도록 백업해야 하는 데이터에 대해 설명하고 개별적으로 백업해야 하는 Lync Server에서 사용되는 데이터 및 구성 요소를 소개합니다.

## 설정 및 구성 요구 사항

이 항목에는 Lync Server 서비스 복구에 필요한 설정 및 구성 정보를 백업하고 복원하기 위한 절차가 포함되어 있습니다. 구성 정보는 중앙 관리 저장소 또는 다른 백 엔드 데이터베이스나 Standard Edition 서버에 있습니다.

다음 표에서는 백업 및 복원해야 하는 설정 및 구성 정보가 나와 있습니다.

### 설정 및 구성 데이터

<table>
<colgroup>
<col style="width: 33%" />
<col style="width: 33%" />
<col style="width: 33%" />
</colgroup>
<thead>
<tr class="header">
<th>데이터 형식</th>
<th>저장된 위치</th>
<th>설명/백업할 시기</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>토폴로지 구성 정보</p></td>
<td><p>중앙 관리 저장소(데이터베이스: Xds.mdf)</p></td>
<td><p>토폴로지, 정책 및 구성 설정입니다.</p>
<p>정기 백업 중 및 Lync Server 제어판 또는 cmdlet을 사용하여 구성 또는 정책을 수정한 후 백업합니다.</p></td>
</tr>
<tr class="even">
<td><p>위치 정보</p></td>
<td><p>중앙 관리 저장소(데이터베이스: Lis.mdf)</p></td>
<td><p>Enterprise Voice E9-1-1(고급 9-1-1) 구성 정보입니다. 이 정보는 일반적으로 정적입니다.</p>
<p>정기 백업 중 백업합니다.</p></td>
</tr>
<tr class="odd">
<td><p>응답 그룹 구성 정보</p></td>
<td><p>백 엔드 서버 또는 Standard Edition 서버(데이터베이스: RgsConfig.mdf)</p></td>
<td><p>응답 그룹 에이전트 그룹, 큐 및 워크플로입니다.</p>
<p>정기 백업 중 및 에이전트 그룹, 큐 또는 워크플로를 추가하거나 변경한 후 백업합니다.</p></td>
</tr>
</tbody>
</table>


## 데이터 요구 사항

아래에는 오류 발생 시 Lync Server 서비스를 복원할 수 있도록 백업해야 하는 Lync Server 데이터의 목록이 나와 있습니다.

일부 데이터 형식은 복구에 필요하지 않습니다. 이 항목에는 이와 같은 데이터 형식을 백업하는 절차는 포함되어 있지 않으며, 해당 형식은 다음과 같습니다.

  - 끝점과 구독, 활성 회의 서버 및 임시 회의 상태와 같은 임시 사용자 데이터(데이터베이스: RtcDyn.mdf)

  - 주소록 데이터(데이터베이스: Rtcab.mdf 및 Rtcab1.mdf). 주소록 데이터베이스는 Active Directory 도메인 서비스에서 자동으로 다시 생성됩니다.

  - 통화 대기 응용 프로그램에 대한 동적 정보(데이터베이스: CpsDyn.mdf)

  - 에이전트 로그인 상태 및 통화 대기 정보와 같은 임시 응답 그룹 데이터(데이터베이스: RgsDyn.mdf)

  - 영구 채팅용 준수 데이터베이스(데이터베이스: MgcComp.mdf). 영구 채팅 준수를 사용하도록 설정한 경우 데이터베이스에서 정보를 읽은 다음 대체 형식으로 변환하도록 어댑터가 구성되어 있으면 영구 채팅 준수 데이터베이스의 정보는 임시로 보관됩니다. 따라서 영구 채팅용 준수 데이터베이스도 임시 데이터베이스로 간주됩니다.
    
    Lync Server 2013 영구 채팅 서버에서는 XML 어댑터가 제공됩니다. 이 데이터를 가져와서 Exchange 호스트된 보관과 같은 기타 원본으로 이동하는 사용자 지정 어댑터를 설치할 수도 있습니다.

다음 표에는 백업 및 복원해야 하는 데이터가 나와 있습니다.

### 데이터베이스에 저장된 데이터

<table>
<colgroup>
<col style="width: 33%" />
<col style="width: 33%" />
<col style="width: 33%" />
</colgroup>
<thead>
<tr class="header">
<th>데이터 형식</th>
<th>저장된 위치</th>
<th>설명/백업할 시기</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>영구 사용자 데이터</p></td>
<td><p>백 엔드 서버 또는 Standard Edition 서버(데이터베이스: RTCXDS.mdf)</p></td>
<td><p>사용자 권한, 사용자 대화 상대 목록, 서버 또는 풀 데이터, 예약된 회의 등입니다. 회의에 업로드된 콘텐츠는 이 사용자 데이터에 포함되지 않습니다.</p>
<p>정기 백업 중 백업합니다. 이 정보는 동적이지만 업데이트가 손실되더라도 마지막 정기 백업으로 복원해야 할 경우 Lync Server에 영향을 주지 않습니다. 대화 상대 목록이 조직에 중요한 경우 이 데이터를 보다 자주 백업할 수 있습니다.</p></td>
</tr>
<tr class="even">
<td><p>보관 데이터</p></td>
<td><p>보관 데이터베이스(데이터베이스: LcsLog.mdf)</p>
<p>Microsoft Exchange 통합 옵션을 사용하도록 설정한 경우 이 데이터는 Exchange 2013에 저장될 수 있습니다. 그렇지 않으면 이 데이터는 Lync Server 보관 데이터베이스에 저장되는데, 이 데이터베이스는 다른 Lync Server 데이터베이스와 함께 배치될 수도 있고 별도의 데이터베이스 서버에 독립 실행형으로 포함될 수도 있습니다.</p></td>
<td><p>IM(인스턴트 메시징) 및 모임 콘텐츠입니다.</p>
<p>이 데이터는 Lync Server에는 중요하지 않지만 조직에서 규정상 중요할 수도 있습니다. 상황에 맞게 적절한 백업 일정을 결정하십시오.</p>
<p>Lync Server는 보관 데이터베이스에 대해 단순 복구 모델만 지원합니다. 단순 복구 모델에서는 데이터베이스가 마지막 전체 백업 지점까지 복구되므로, 장애 지점이나 특정 시점까지 데이터베이스를 복원할 수는 없습니다.</p></td>
</tr>
<tr class="odd">
<td><p>데이터 모니터링</p></td>
<td><p>모니터링 데이터베이스(LcsCDR.mdf 및 QoeMetrics.mdf)</p>
<p>이러한 데이터베이스는 다른 Lync Server 데이터베이스와 함께 배치될 수도 있고 별도의 데이터베이스 서버에 독립 실행형으로 포함될 수도 있습니다.</p></td>
<td><p>통화 정보 기록(LcsCDR.mdf) 및 QoE(체감 품질) 메트릭(QoeMetrics.mdf)</p>
<p>통화 정보 기록은 동적이며 업무에 중요할 수 있습니다. 규제 이유에 따라 이러한 레코드가 필요한지 여부를 고려하여 백업 일정을 결정하십시오.</p>
<p>체감 품질 정보는 동적입니다. QoE 데이터 손실은 Lync Server 작업에 중요하지 않지만 업무에 중요할 수 있습니다. 조직에서 이 정보가 중요한 정도에 따라 백업 일정을 결정하십시오.</p>
<p>Lync Server는 모니터링 데이터베이스에 대해 단순 복구 모델만 지원합니다. 단순 복구 모델에서는 데이터베이스가 마지막 전체 백업 지점까지 복구되므로, 장애 지점이나 특정 시점까지 데이터베이스를 복원할 수는 없습니다.</p></td>
</tr>
<tr class="even">
<td><p>영구 채팅 데이터</p></td>
<td><p>영구 채팅 데이터베이스(mgd.mdf)</p>
<p>이 데이터베이스는 다른 Lync Server 데이터베이스와 함께 배치될 수도 있고 별도의 데이터베이스 서버에 독립 실행형으로 포함될 수도 있습니다.</p></td>
<td><p>영구 채팅 데이터는 채팅방에서 게시되는 실제 채팅 내용입니다. 이 데이터는 업무상 중요한 경우가 많습니다.</p>
<p>SQL Server 백업을 사용할 수도 있고 Lync Server에서 제공되는 <strong>Export-CsPersistentChatData</strong> cmdlet을 사용하여 데이터베이스를 내보낼 수도 있습니다. 데이터를 복구하려는 경우 데이터베이스를 가져와서 마지막 전체 백업 시점까지 복원할 수 있습니다(장애 지점까지 데이터베이스를 복원할 수는 없음).</p></td>
</tr>
</tbody>
</table>


## 파일 저장소 데이터 요구 사항

Enterprise Edition 배포에서 Lync Server 파일 저장소는 대개 파일 서버에 있습니다. Standard Edition 배포에서는 Lync Server 파일 저장소가 기본적으로 Standard Edition 서버에 있습니다. 보통 하나의 Lync Server 파일 저장소가 사이트에 대해 공유됩니다. 영구 채팅 파일 저장소는 Lync Server 파일 저장소와 같은 파일 공유를 사용합니다.

파일 저장소 위치는 \\\\서버\\공유 이름으로 식별됩니다. 파일 저장소의 특정 위치를 찾으려면 토폴로지 작성기를 열고 **파일 저장소** 노드에서 찾습니다.

다음 표에서는 백업 및 복원하는 데 필요한 파일 저장소가 나와 있습니다.

### 파일 저장소

<table>
<colgroup>
<col style="width: 33%" />
<col style="width: 33%" />
<col style="width: 33%" />
</colgroup>
<thead>
<tr class="header">
<th>데이터 형식</th>
<th>저장된 위치</th>
<th>설명/백업할 시기</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Lync Server 파일 저장소</p></td>
<td><p>일반적으로 파일 서버, 파일 클러스터 또는 Standard Edition 서버에 있음</p></td>
<td><p>모임 콘텐츠, 모임 콘텐츠 메타데이터, 모임 준수 로그, 응용 프로그램 데이터 파일, 장치 업데이트를 위한 업데이트 파일, 응답 그룹, 통화 대기 및 알림 응용 프로그램용 오디오 파일, 영구 채팅방에서 게시되는 파일</p>
<p>정기 백업 중 백업합니다.</p></td>
</tr>
</tbody>
</table>


## 추가 백업 요구 사항

장애 시 Lync Server 서비스를 복원하려면 Lync Server 자체에 포함되지 않는 몇 가지 필요한 구성 요소를 백업해야 합니다. 다음 구성 요소는 이 문서에서 설명하는 Lync Server 백업 및 복원 프로세스의 일부분으로 백업되거나 복원되지 않습니다.

  - **Active Directory 도메인 서비스**   Lync Server 백업과 동시에 Active Directory 도구를 사용하여 AD DS를 백업해야 합니다. AD DS에 포함된 것과 일치하지 않는 대화 상대 개체가 Lync Server에 필요한 경우 발생할 수 있는 문제를 방지하려면 AD DS를 Lync Server와 동기화된 상태로 유지해야 합니다. AD DS에는 Lync Server에서 사용하는 다음과 같은 설정이 저장됩니다.
    
      - 사용자 SIP URI 및 기타 사용자 설정
    
      - 응답 그룹, 회의 길잡이 등의 응용 프로그램용 대화 상대 개체
    
      - 중앙 관리 저장소에 대한 포인터
    
      - Kerberos 인증 계정(선택적 컴퓨터 개체) 및 Lync Server 보안 그룹
    
    Windows Server 2008에서 AD DS를 백업 및 복원하는 방법에 대한 자세한 내용은 "AD DS 백업 및 복구 단계별 가이드"(<http://go.microsoft.com/fwlink/?linkid=209105>)를 참조하십시오.

  - **인증 기관 및 인증서**   CA(인증 기관) 및 인증서 백업을 위한 조직 정책을 사용합니다. 내보낼 수 있는 개인 키를 사용하는 경우 인증서 및 개인 키를 백업하고 이 문서의 절차에 따라 Lync Server를 복원할 때 이를 내보낼 수 있습니다. 내부 CA를 사용하는 경우 Lync Server를 복원해야 할 때 다시 등록할 수 있습니다. 개인 키는 컴퓨터에 문제가 발생했을 때 사용할 수 있도록 안전한 위치에 보관해야 합니다.

  - **System Center Operations Manager**   Microsoft System Center Operations Manager(이전 Microsoft Operations Manager)를 사용하여 Lync Server 배포를 모니터링할 경우 Lync Server를 모니터링하는 동안 선택적으로 시스템에서 만드는 데이터를 백업할 수 있습니다. 표준 SQL Server 백업 프로세스를 사용하여 System Center Operations Manager 파일을 백업합니다. 복구 중에는 이러한 파일이 복원되지 않습니다.

  - **PSTN(공중 전화망) 게이트웨이 구성**   Enterprise Voice 또는 Survivable Branch Appliance를 사용하는 경우 PSTN 게이트웨이 구성을 백업해야 합니다. PSTN 게이트웨이 구성의 백업 및 복원에 대한 자세한 내용은 공급업체에 문의하십시오.

  - **Lync Server 또는 Office Communications Server의 여러 버전 동시 사용**   Lync Server 2013 배포가 Lync Server 2010 이하 버전의 Office Communications Server와 동시에 사용될 경우 이 문서의 절차에 따라 이전 버전을 백업하거나 복원할 수 없습니다. 대신 이전 버전에 대해 설명된 백업 및 복원 절차를 따라야 합니다. Lync Server 2010을 백업 및 복원하는 방법에 대한 자세한 내용은 <http://go.microsoft.com/fwlink/?linkid=265417>를 참조하십시오. Microsoft Office Communications Server 2007 R2를 백업 및 복원하는 방법에 대한 자세한 내용은 <http://go.microsoft.com/fwlink/?linkid=168162>를 참조하십시오.

  - **인프라 정보**   방화벽 구성, 부하 분산 구성, IIS(인터넷 정보 서비스) 구성, DNS(Domain Name System) 레코드 및 IP 주소, DHCP(Dynamic Host Configuraton Protocol) 구성과 같은 인프라 정보를 백업해야 합니다. 이러한 구성 요소의 백업에 대한 자세한 내용은 해당 공급업체에 문의하십시오.

  - **Microsoft Exchange 및 Exchange UM(통합 메시징)**   Microsoft Exchange 설명서의 설명에 따라 Microsoft Exchange 및 Exchange UM을 백업하고 복원합니다. Exchange Server 2013을 백업 및 복원하는 방법에 대한 자세한 내용은 <http://go.microsoft.com/fwlink/?linkid=285384>를 참조하십시오. Exchange Server 2010을 백업 및 복원하는 방법에 대한 자세한 내용은 <http://go.microsoft.com/fwlink/?linkid=209179>를 참조하십시오.
    
    Lync Server 2013에는 보관 데이터, 고화질 사용자 사진 및 사용자 대화 상대 목록을 Exchange 2013에 저장하는 기능이 도입되었습니다. 이러한 데이터 형식을 백업하는 방법은 다음 목록을 참조하십시오.
    
      - **고화질 사진**은 Exchange Server 백업의 일부분으로 백업됩니다.
    
      - **통합 연락처 저장소**는 Lync Server 2013에서 도입되었습니다. 사용자는 통합 연락처 저장소에 Exchange 2013의 모든 연락처 정보를 보관할 수 있습니다.
        
        사용자 대화 상대가 저장되는 위치(통합 연락처 저장소 또는 Lync 백 엔드 서버)와 관련하여 사용자의 백업이 최신 상태인지를 확인해야 합니다. 다음 시나리오에서는 통합 연락처 저장소로 사용자 대화 상대를 마이그레이션하는 경우 백업 및 복원 프로세스에서 문제가 발생할 수 있는 상황에 대해 설명합니다.
        
        **시나리오 1:** 사용자 대화 상대를 통합 연락처 저장소로 마이그레이션하고 사용자 대화 상대 마이그레이션 이전에 작성한 Lync Server 백업에서 복원을 수행하는 경우. 이 시나리오에서는 Lync Server 마이그레이션 작업에서 Exchange로 사용자 대화 상대 마이그레이션을 시작할 때까지 최대 1일 동안 사용자의 대화 상대가 오래된 상태일 수 있습니다. 사용자 대화 상대는 이전에 통합 연락처 저장소로 마이그레이션되었으므로 Exchange 연락처 정보가 사용됩니다. 이 시나리오에서는 관리자가 개입할 필요가 없습니다.
        
        **시나리오 2:** 사용자 대화 상대가 이전에 통합 연락처 저장소에 저장되었다가 롤백된 경우. 사용자 대화 상대가 통합 연락처 저장소에 저장될 때 작성된 Lync Server 백업에서 복원이 수행됩니다. 이 시나리오에서는 클라이언트 또는 Lync 서버 로그에 `Error: Incorrect Exchange Version`이라는 오류 메시지가 나타나 이 상태를 문제로 지정할 수 있습니다. 사용자는 Exchange에서 Lync 2013의 대화 상대 목록에 직접 액세스할 수 있지만 클라이언트 상태는 Lync Server 상태와 일치하지 않습니다. 이 문제를 해결하려면 관리자가 영향을 받는 사용자에 대해 **Invoke-CsUCSRollback** cmdlet을 실행해야 합니다.
    
      - **보관 데이터**는 Exchange 2013에 저장될 수 있습니다. 이 데이터는 Lync Server에는 중요하지 않지만 조직에서 규정상 중요할 수도 있습니다. 보관 데이터가 Exchange에 저장되며 조직에서 중요한 경우에는 Exchange 백업 및 복원 절차를 따르십시오. Exchange에 저장된 보관 데이터를 Lync Server로 다시 이동할 수는 없습니다. 또한 Lync 보관 데이터베이스에 이미 저장된 데이터를 Exchange로 이동할 수도 없습니다.

