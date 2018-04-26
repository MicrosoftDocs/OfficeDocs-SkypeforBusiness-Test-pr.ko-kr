---
title: Lync Server 2013용 Active Directory 도메인 서비스
TOCTitle: Lync Server 2013용 Active Directory 도메인 서비스
ms:assetid: 5483afd5-d8af-4825-ae95-a82dbe941dbf
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Dn481129(v=OCS.15)
ms:contentKeyID: 59679292
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Lync Server 2013용 Active Directory 도메인 서비스

 

_**마지막으로 수정된 항목:** 2015-03-09_

Active Directory 도메인 서비스는 Windows Server 2003, Windows Server 2008, Windows Server 2012, Windows Server 2012 R2 디렉터리 서비스로서의 기능을 합니다. 또한 Active Directory 도메인 서비스는 Microsoft Lync Server 2013 보안 인프라를 구축할 수 있는 토대가 됩니다. 이 섹션에서는 Lync Server 2013에서 Active Directory 도메인 서비스를 사용하여 메신저 대화, 웹 회의, 미디어, 음성에 적합한 신뢰할 수 있는 환경을 만드는 방법을 설명합니다. Active Directory 도메인 서비스에 대한 Lync Server 확장 및 Active Directory 도메인 서비스를 위한 환경 준비에 대한 자세한 내용은 배포 설명서의 [Lync Server 2013에 대한 Active Directory 도메인 서비스 준비](lync-server-2013-preparing-active-directory-domain-services.md)를 참고하세요. Windows Server 네트워크에서 Active Directory 도메인 서비스의 역할에 대한 자세한 내용은 사용 중인 운영 체제의 버전에 대한 설명서를 참고하세요.

Lync Server 2013은 Active Directory 도메인 서비스를 사용하여 다음을 저장합니다.

  - 포리스트에 있는 Lync Server 2013을 실행하는 모든 서버에 필요한 전역 설정

  - 포리스트에 있는 Lync Server 2013을 실행하는 모든 서버의 역할을 식별하는 서비스 정보

  - 일부 사용자 설정

## Active Directory 인프라

Active Directory의 인프라 요구 사항에는 다음이 포함됩니다.

  - 도메인 컨트롤러의 운영 체제 요구 사항

  - 도메인 및 포리스트 기능 수준 요구 사항

  - 글로벌 카탈로그 도메인 요구 사항

자세한 내용은 배포 설명서의 [Lync Server 2013에 대한 Active Directory 인프라 요구 사항](lync-server-2013-active-directory-infrastructure-requirements.md)을 참고하세요.

## Active Directory 도메인 서비스 준비


> [!NOTE]
> System 컨테이너 대신 Configuration 컨테이너에 전역 설정을 배포하는 것이 좋습니다. 이렇게 해서 보안이 향상되는 것은 아니지만 일부 Active Directory 도메인 서비스 토폴로지의 확장성이 개선될 수 있습니다. Microsoft Office Communications Server 2007에서 마이그레이션 중이고 System 컨테이너를 사용했지만 Configuration 컨테이너를 사용할 계획이라면 업그레이드 준비 전에 반드시 System 컨테이너의 설정을 이동해야 합니다. System 컨테이너 설정을 Configuration 컨테이너로 마이그레이션하려면 Office Communications Server 2007 전역 설정 마이그레이션 도구(<A href="http://go.microsoft.com/fwlink/p/?linkid=145236">http://go.microsoft.com/fwlink/p/?LinkId=145236</A>)를 참고하세요.



Lync Server 2013을 배포할 때 가장 먼저 Active Directory 도메인 서비스를 준비합니다. Lync Server 2013용 Active Directory 도메인 서비스 준비에는 다음 세 가지 단계가 포함됩니다.

  - **스키마 준비**. Lync Server 2013에 해당하는 클래스 및 특성을 포함하도록 Active Directory 도메인 서비스의 스키마를 확장합니다. 스키마 준비에 대한 자세한 내용은 배포 설명서의 [Lync Server 2013에서 Active Directory 스키마 준비 실행](lync-server-2013-running-schema-preparation.md)을 참고하세요. 자세한 내용은 [Office Communications Server 2007 R2에서 Lync Server 2013으로 마이그레이션](migration-from-office-communications-server-2007-r2-to-lync-server-2013.md)을 참고하세요.

  - **포리스트 준비**. 포리스트 루트 도메인에 전역 설정 및 개체, 그리고 이러한 설정 및 개체에 대한 액세스를 제어하는 유니버설 그룹 및 관리 그룹을 만듭니다. 포리스트 준비에 대한 자세한 내용은 배포 설명서의 [Lync Server 2013에 대한 포리스트 준비 실행](lync-server-2013-running-forest-preparation.md)을 참고하세요.

  - **도메인 준비**. 호스트에 권한을 부여하고 도메인 내 사용자를 관리하는 유니버설 그룹에 필요한 ACE(액세스 제어 항목)를 추가합니다. Lync Server 2013 실행 서버를 배포할 모든 도메인 및 Lync Server 사용자가 속한 모든 도메인에서 이 작업을 마쳐야 합니다. 도메인 준비에 대한 자세한 내용은 배포 설명서의 [Lync Server 2013에 대한 도메인 준비 실행](lync-server-2013-running-domain-preparation.md)을 참고하세요.

Active Directory 준비의 전체 프로세스 개요 및 각 단계를 수행하는 데 필요한 권한 및 사용 권한은 배포 설명서의 [Lync Server 2013에 대한 Active Directory 인프라 요구 사항](lync-server-2013-active-directory-infrastructure-requirements.md)을 참고하세요.

## 유니버설 그룹

포리스트를 준비하는 동안 Lync Server 2013은 전역 설정 및 서비스에 액세스 및 이를 관리하는 권한을 가진 다양한 유니버설 그룹을 Active Directory 도메인 서비스 내에 만듭니다. 이러한 유니버설 그룹에는 다음이 포함됩니다.

  - **관리 그룹**. 이 그룹은 Lync Serever 네트워크에 대한 기본 관리자 역할을 정의합니다. 포리스트를 준비하는 동안 이 관리자 그룹이 Lync Server 인프라 그룹에 추가됩니다.

  - **서비스 그룹**. 이 그룹은 Lync Server에서 제공한 다양한 서비스에 액세스하는 데 필요한 서비스 계정입니다.

  - **인프라 그룹**. 이 그룹은 Lync Server 인프라의 특정 영역에 대한 액세스 권한을 제공합니다. 인프라 그룹은 관리 그룹의 구성 요소로 작동하며, 이 그룹을 직접 수정하거나 이 그룹에 사용자를 직접 추가해서는 안 됩니다. 포리스트를 준비하는 동안 특정 서비스 및 관리 그룹이 적절한 인프라 그룹에 추가됩니다.

Lync Server용 AD를 준비할 때 만들어지는 특정 유니버설 그룹 및 인프라 그룹에 추가되는 서비스 및 관리 그룹에 대한 자세한 내용은 배포 설명서의 [Lync Server 2013에서 포리스트 준비로 인한 변경](lync-server-2013-changes-made-by-forest-preparation.md)을 참고하세요.


> [!NOTE]
> Lync Server 2013은 Lync Server 2013을 실행하는 Windows Server 2012 및 도메인 컨트롤러용 Windows Server 2003 운영 체제에 있는 유니버설 그룹을 지원합니다. 유니버설 그룹의 구성원은 도메인 트리 또는 포리스트에 있는 도메인의 다른 그룹 및 계정을 포함할 수 있고, 도메인 트리 또는 포리스트에 있는 도메인의 사용 권한을 할당받을 수 있습니다. 유니버설 그룹 지원과 관리자 위임이 결합되어 Lync Server 배포 관리가 단순화됩니다. 예를 들어 한 도메인을 다른 도메인에 추가하지 않아도 관리자가 두 개 모두 관리할 수 있습니다.



## 역할 기반 액세스 제어

포리스트 준비를 통해 유니버설 서비스 및 관리 그룹이 만들어지고 적절한 유니버설 그룹에 서비스 및 관리 그룹이 추가될 뿐 아니라 RBAC(역할 기반 액세스 제어) 그룹도 만들어집니다. 포리스트 준비를 통해 만들어진 특정 RBAC 그룹에 대한 자세한 내용은 배포 설명서의 [Lync Server 2013에서 포리스트 준비로 인한 변경](lync-server-2013-changes-made-by-forest-preparation.md)을 참고하세요. RBAC 그룹에 대한 자세한 내용은 [Lync Server 2013용 RBAC(역할 기반 액세스 제어)](lync-server-2013-role-based-access-control-rbac.md)를 참고하세요.

## ACE(액세스 제어 항목) 및 상속

포리스트 준비를 통해 만들어진 유니버설 그룹에 대한 ACE가 추가되면서 개인 ACE 및 공개 ACE가 만들어집니다. 개인 ACE는 Lync Server에 사용되는 전역 설정 컨테이너에 만들어집니다. 이 컨테이너는 Lync Server에만 사용되고, 전역 설정을 저장하는 위치에 따라 루트 도메인의 System 컨테이너나 Configuration 컨테이너에 위치합니다.

도메인 준비 단계에서는 호스트에 권한을 부여하고 도메인 내의 사용자를 관리하는 유니버설 그룹에 필요한 ACE(액세스 제어 항목)를 추가합니다. 도메인 준비는 도메인 루트와 세 개의 기본 제공 컨테이너인 사용자, 컴퓨터 및 도메인 컨트롤러에 ACE를 만듭니다.

포리스트 준비 및 도메인 준비 단계에서 만들어지고 추가된 공개 ACE에 대한 자세한 내용은 배포 설명서의 [Lync Server 2013에서 포리스트 준비로 인한 변경](lync-server-2013-changes-made-by-forest-preparation.md) 및 [Lync Server 2013에서 도메인 준비로 인한 변경](lync-server-2013-changes-made-by-domain-preparation.md)을 참고하세요.

조직에서는 보안 위험을 완화하기 위해 AD DS(Active Directory 도메인 서비스)를 잠그는 경우가 많습니다. 그러나 잠긴 Active Directory 환경으로 인해 Lync Server 2013에 필요한 사용 권한이 제한될 수 있습니다. 컨테이너와 OU에서 ACE가 제거 및 User, Contact, InetOrgPerson 또는 Computer 개체에 대한 사용 권한 상속 해제가 포함될 수 있습니다. 잠긴 Active Directory 환경에서 사용 권한을 필요로 하는 컨테이너 및 OU에 대해 수동으로 설정해야 합니다. 자세한 내용은 배포 설명서의 [Lync Server 2013에서 잠긴 Active Directory 도메인 서비스 준비](lync-server-2013-preparing-a-locked-down-active-directory-domain-services.md)를 참고하세요.

## 서버 정보

정품 인증 과정에서 Lync Server 2013은 Active Directory 도메인 서비스의 다음 세 위치에 서버 정보를 게시합니다.

  - Lync Server 2013이 설치된 물리적 컴퓨터에 해당하는 각 Active Directory 컴퓨터 개체의 SCP(서비스 연결 지점)

  - **msRTCSIP-Pools** 클래스의 컨테이너에 만들어진 서버 개체

  - 토폴로지 작성기에 지정된 트러스트된 서버

## 서비스 연결 지점

Active Directory 도메인 서비스의 각 Lync Server 2013 개체에는 RTC 서비스라는 SCP가 있으며 여기에는 각 컴퓨터를 식별하고 이것이 제공하는 서비스를 지정하는 많은 특성이 포함됩니다. 더욱 중요한 SCP 특성에는 *serviceDNSName*, *serviceDNSNameType*, *serviceClassname*, *serviceBindingInformation*이 포함됩니다. 타사 자산 관리 응용 프로그램을 사용하면 이러한 특성 및 다른 SCP 특성을 쿼리하여 배포 간 서버 정보를 검색할 수 있습니다.

## Active Directory 서버 개체

각 Lync Server 2013 서버 역할에는 해당 Active Directory 개체가 있고, 개체의 특성은 그러한 역할에서 제공하는 서비스를 정의합니다. 또한 Standard Edition 서버가 인증되거나 Enterprise Edition 풀이 만들어질 때 Lync Server 2013은 **msRTCSIP-Pools** 컨테이너에 새 **msRTCSIP-Pool** 개체를 만듭니다. **msRTCSIP-Pool** 클래스는 풀의 FQDN(정규화된 도메인 이름)과 풀의 프런트 엔드 및 백 엔드 구성 요소 간 연결을 지정합니다. Standard Edition 서버는 프런트 엔드 및 백 엔드가 단일 컴퓨터에 배치된 논리 풀로 간주됩니다.

## 트러스트된 서버

Lync Server 2013에서 트러스트된 서버는 토폴로지 작성기를 실행하고 토폴로지를 게시할 때 지정되는 서버입니다. 게시된 토폴로지는 모든 서버 정보를 포함하여 중앙 관리 저장소에 저장됩니다. 중앙 관리 저장소에 정의된 전용 서버는 신뢰할 수 있습니다. Lync Server 2013에서 트러스트된 서버는 다음 조건을 충족해야 합니다.

  - 서버의 FQDN은 중앙 관리 저장소에 저장된 토폴로지에서 만들어집니다.

  - 서버는 트러스트된 CA에서 발급한 올바른 인증서를 제공합니다. 자세한 내용은 [Lync Server 2013에 대한 인증서 인프라 요구 사항](lync-server-2013-certificate-infrastructure-requirements.md)을 참고하세요.

이 조건 중 하나라도 충족하지 못할 경우 서버를 신뢰할 수 없으며 서버와의 연결이 거부됩니다. 이러한 두 가지 요구 사항을 통해 Rogue 서버가 올바른 서버의 FQDN을 가져오려는 잠재적인 공격을 방지할 수 있습니다.

또한 Microsoft Office Communications Server 2007 R2 및 Microsoft Office Communications Server 2007 배포를 사용하여 Lync Server 2013 서버와 통신하기 위해, Lync Server 2013은 포리스트를 준비하는 동안 이전 릴리스에 대한 트러스트된 서버 목록을 보유하기 위해 컨테이너를 만듭니다. 다음 표에는 이전 배포와의 호환성을 위해 만들어진 컨테이너가 나와 있습니다.

### 트러스트된 서버 목록 및 이전 릴리스와의 호환성을 위한 Active Directory 컨테이너

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th>트러스트된 서버 목록</th>
<th>Active Directory 컨테이너</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Standard Edition 서버 및 엔터프라이즈 풀 프런트 엔드 서버</p></td>
<td><p>RTC 서비스/전역 설정</p></td>
</tr>
<tr class="even">
<td><p>회의 서버</p></td>
<td><p>RTC 서비스/신뢰할 수 있는 MCU</p></td>
</tr>
<tr class="odd">
<td><p>웹 구성 요소 서버</p></td>
<td><p>RTC 서비스/TrustedWebComponentsServers</p></td>
</tr>
<tr class="even">
<td><p>중재 서버 및 Communicator Web Access Server, 응용 프로그램 서버, QoE 등록자, A/V 회의 서비스(타사 SIP 서버라고도 함)</p></td>
<td><p>RTC 서비스/신뢰할 수 있는 서비스</p></td>
</tr>
<tr class="odd">
<td><p>프록시 서버</p></td>
<td><p>Lync Server 2013은 프록시 서버에 대해 이전 버전과의 호환성을 지원하지 않습니다.</p></td>
</tr>
</tbody>
</table>


이전 릴리스의 트러스트된 서버를 지원하려면 모범 사례 분석기 도구를 실행해야 합니다. 모범 사례 분석기를 실행하는 방법에 대한 자세한 내용은 [http://go.microsoft.com/fwlink/p/?LinkId=330633](http://go.microsoft.com/fwlink/p/?linkid=330633)을 참고하세요.

