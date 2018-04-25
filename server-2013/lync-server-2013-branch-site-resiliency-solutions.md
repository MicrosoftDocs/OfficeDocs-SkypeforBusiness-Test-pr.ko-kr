---
title: 'Lync Server 2013: 분기 사이트 복구 솔루션'
TOCTitle: 분기 사이트 복구 솔루션
ms:assetid: 1700f99b-709c-4e47-88eb-c0a5490e26e2
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg398234(v=OCS.15)
ms:contentKeyID: 49302928
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Lync Server 2013의 분기 사이트 복구 솔루션

 

_**마지막으로 수정된 항목:** 2015-03-09_

조직에 분기 사이트 탄성을 제공할 경우 확실한 이점이 있습니다. 구체적으로 설명하자면, 중앙 사이트에 대한 연결이 해제되어도 분기 사이트 사용자는 Enterprise Voice 서비스와 음성 메일(음성 메일 다시 라우팅 설정이 구성된 경우. 자세한 내용은 [Lync Server 2013에 대한 분기 사이트 복구 요구 사항](lync-server-2013-branch-site-resiliency-requirements.md) 참조)을 계속 이용할 수 있습니다. 그러나 사용자 수가 25명 미만인 사이트의 경우에는 탄성 솔루션으로부터 충분한 투자 수익을 내지 못할 수도 있습니다.

분기 사이트 탄성을 제공하려는 경우 세 가지 방법 중 하나를 사용할 수 있습니다. 다음 표를 사용하면 조직에 가장 적합한 옵션을 선택하는 데 도움이 될 수 있습니다.



<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th>상황</th>
<th>권장 방법</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>분기 사이트에서 25~1000명의 사용자를 호스팅하려는 경우(ROI(투자 수익률)가 전체 배포를 지원하지 않거나 로컬 관리 지원을 사용할 수 없음)</p></td>
<td><p>SBA(Survivable Branch Appliance)</p>
<p>SBA(Survivable Branch Appliance)는 Windows Server 2008 R2에서 실행되는 Lync Server 등록자 및 중재 서버가 포함된 업계 표준 블레이드 서버입니다. SBA(Survivable Branch Appliance)에는 공중 전화망(PSTN) 게이트웨이도 포함되어 있습니다. SBA(Survivable Branch Appliance) 자격 검증/인증 프로그램에서 Microsoft 파트너가 개발한 적격 타사 장치는 WAN 오류 시에도 지속적인 PSTN 연결을 제공하지만, 이러한 기능은 중앙 사이트의 프런트 엔드 서버를 기반으로 하기 때문에 이 접근 방식이 탄력적인 현재 상태 및 회의 기능을 제공하지는 못합니다.</p>
<p>SBA(Survivable Branch Appliance)에 대한 자세한 내용은 이 항목 뒷부분의 &quot; SBA(Survivable Branch Appliance) 세부 정보&quot;를 참조하십시오.</p>
<p><strong>참고:</strong> SBA(Survivable Branch Appliance)에서 SIP 트렁크도 사용하려는 경우에는 조직에 가장 적합한 서비스 공급자를 SBA(Survivable Branch Appliance) 공급업체에 문의하십시오.</p></td>
</tr>
<tr class="even">
<td><p>분기 사이트에서 1000~2000명의 사용자를 호스팅하려는 경우(숙련된 Lync Server 관리자는 있지만 복구 가능한 WAN 연결이 없음)</p></td>
<td><p>지속 가능 분기 서버 또는 SBA(Survivable Branch Appliance) 두 개</p>
<p>지속 가능 분기 서버는 Lync Server 등록자 및 중재 서버 소프트웨어가 설치되어 있으며 지정된 하드웨어 요구 사항을 충족하는 Windows Server입니다. 이 서버는 전화 서비스 공급자에 대한 SIP 트렁크 또는 PSTN 게이트웨이에 연결되어야 합니다.</p>
<p>지속 가능 분기 서버에 대한 자세한 내용은 이 항목 뒷부분의 &quot;지속 가능 분기 서버 세부 정보&quot;를 참고하세요.</p></td>
</tr>
<tr class="odd">
<td><p>최대 5000명의 사용자를 지원하는 음성 기능 외에 현재 상태 및 회의 기능이 필요한 경우(숙련된 Lync Server 관리자가 있음)</p></td>
<td><p>Standard Edition 서버를 분기 사이트가 아니라 중앙 사이트로 배포합니다.</p>
<p>전체 Lync Server 배포는 WAN 오류 시 지속적인 PSTN 연결과 탄력적인 현재 상태 및 회의 기능을 제공합니다.</p>
<p>이 솔루션을 준비하는 방법에 대한 자세한 내용은 <a href="lync-server-2013-planning-for-your-organization.md">Lync Server 2013에 대한 조직 계획</a>, <a href="lync-server-2013-determining-your-system-requirements.md">Lync Server 2013의 시스템 요구 사항 확인</a>, <a href="lync-server-2013-determining-your-infrastructure-requirements.md">Lync Server 2013에 대한 인프라 요구 사항 확인</a> 및 계획 설명서의 기타 관련 섹션을 참조하십시오.</p></td>
</tr>
</tbody>
</table>


## 복구 토폴로지

다음 그림에서는 분기 사이트 복구를 지원하는 권장 토폴로지를 보여 줍니다.

**분기 사이트 복구 옵션**

![음성 분기 복구 옵션](images/Gg398234.47eecd19-08ae-4d82-acbe-61f0de760306(OCS.15).jpg "음성 분기 복구 옵션")

## SBA(Survivable Branch Appliance) 세부 정보

Lync Server SBA(Survivable Branch Appliance)에는 다음 구성 요소가 포함됩니다.

  - 사용자 인증, 등록 및 통화 라우팅을 수행하는 등록자

  - 등록자와 PSTN 게이트웨이 간의 신호를 처리하는 중재 서버

  - WAN 중단 시 PSTN 통화를 대체 전송으로 라우팅하는 PSTN 게이트웨이

  - 로컬 사용자 데이터를 저장하는 SQL Server Express

또한 SBA(Survivable Branch Appliance)에는 PSTN 트렁크, 아날로그 포트 및 이더넷 어댑터가 포함되어 있습니다.

분기 사이트에서 WAN을 통해 중앙 사이트에 연결할 수 없는 경우 내부 분기 사용자는 SBA(Survivable Branch Appliance) 등록자에 등록한 후 SBA(Survivable Branch Appliance)와 PSTN 간의 연결을 사용하여 중단되지 않은 음성 서비스를 계속 사용할 수 있습니다. 홈 또는 다른 원격 위치에서 연결하는 분기 사이트 사용자는 분기 사이트의 WAN 링크를 사용할 수 없어도 중앙 사이트의 등록자 서버에 등록할 수 있습니다. 이러한 사용자는 분기 사이트로의 인바운드 통화가 음성 메일로 이동하는 것을 제외하고는 전체 통합 통신 기능을 사용할 수 있습니다. WAN 연결이 복구되면 분기 사이트 사용자를 위한 전체 기능이 복원됩니다. IT 관리자가 없어도 SBA(Survivable Branch Appliance)로의 장애 조치(failover) 및 서비스 복원은 수행됩니다.

Lync Server는 분기 사이트에서 최대 2개의 SBA(Survivable Branch Appliance)를 지원합니다.

## SBA(Survivable Branch Appliance) 배포 개요

SBA(Survivable Branch Appliance)는 Microsoft 파트너인 OEM(Original Equipment Manufacturer)에서 제조하고 VAR(Value Added Retailer)이 이들을 대신해 배포합니다. 이러한 배포는 중앙 사이트에 Lync Server가 배포되고 분기 사이트와의 WAN 연결이 설정되고 분기 사이트 사용자가 Enterprise Voice를 사용하도록 설정된 경우에만 가능합니다.

이러한 단계에 대한 자세한 내용은 배포 설명서의 [Lync Server 2013을 통해 SBA(Survivable Branch Appliance) 또는 지속 가능 분기 서버 배포](lync-server-2013-deploying-a-survivable-branch-appliance-or-server.md)를 참조하십시오.


<table>
<colgroup>
<col style="width: 33%" />
<col style="width: 33%" />
<col style="width: 33%" />
</colgroup>
<thead>
<tr class="header">
<th>단계</th>
<th>절차</th>
<th>사용자 권한</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>SBA(Survivable Branch Appliance)에 대한 Active Directory 도메인 서비스를 설정합니다.</p></td>
<td><p><strong>중앙 사이트에서 다음을 수행합니다.</strong></p>
<ol>
<li><p>분기 사이트에서 SBA(Survivable Branch Appliance)를 설치하고 활성화할 기술자의 도메인 사용자 계정(또는 엔터프라이즈 ID)을 만듭니다.</p></li>
<li><p>Active Directory 도메인 서비스에서 SBA(Survivable Branch Appliance)에 대한 컴퓨터 계정(해당 FQDN(정규화된 도메인 이름) 포함)을 만듭니다.</p></li>
<li><p>토폴로지 작성기에서 SBA(Survivable Branch Appliance)를 만들고 게시합니다.</p></li>
</ol></td>
<td><p>기술자 사용자 계정은 RTCUniversalSBATechnicians의 구성원이어야 합니다. SBA(Survivable Branch Appliance)는 RTCSBAUniversalServices 그룹에 속해야 하며, 이는 Topology Builder를 사용할 때 자동으로 적용됩니다.</p></td>
</tr>
<tr class="even">
<td><p>SBA(Survivable Branch Appliance)를 설치 및 활성화합니다.</p></td>
<td><p><strong>분기 사이트에서 다음을 수행합니다.</strong></p>
<ol>
<li><p>SBA(Survivable Branch Appliance)를 이더넷 포트 및 PSTN 포트에 연결합니다.</p></li>
<li><p>SBA(Survivable Branch Appliance)를 시작합니다.</p></li>
<li><p>중앙 사이트의 SBA(Survivable Branch Appliance)에 대해 만든 도메인 사용자 계정을 사용하여 SBA(Survivable Branch Appliance)를 도메인 가입시킵니다. FQDN 및 IP 주소를 컴퓨터 계정에 만든 FQDN과 일치하도록 설정합니다.</p></li>
<li><p>OEM 사용자 인터페이스를 사용하여 SBA(Survivable Branch Appliance)를 구성합니다.</p></li>
<li><p>PSTN 연결을 테스트합니다.</p></li>
</ol></td>
<td><p>기술자 사용자 계정은 RTCUniversalSBATechnicians의 구성원이어야 합니다.</p></td>
</tr>
</tbody>
</table>


## 지속 가능 분기 서버 세부 정보

토폴로지 작성기에서 분기 사이트를 만들고 이 사이트에 지속 가능 분기 서버를 추가한 다음 이 역할을 설치할 컴퓨터에서 Lync Server 배포 마법사를 실행할 수 있습니다.

## 참고 항목

#### 기타 리소스

[Lync Server 2013 배포](lync-server-2013-deploying-lync-server.md)

