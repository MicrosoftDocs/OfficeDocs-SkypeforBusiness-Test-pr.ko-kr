---
title: 'Lync Server 2013: Active Directory 도메인 서비스 준비 개요'
TOCTitle: Active Directory 도메인 서비스 준비 개요
ms:assetid: cdd2a652-6a0d-4728-9950-3fcaa7a80066
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg398869(v=OCS.15)
ms:contentKeyID: 49305063
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Lync Server 2013의 Active Directory 도메인 서비스 준비 개요

 

_**마지막으로 수정된 항목:** 2015-03-09_

Lync Server 2013 배포를 위해 Active Directory 도메인 서비스를 준비하려면 다음과 같은 지정된 순서로 세 단계를 수행해야 합니다.

다음 표에는 Lync Server에 대해 AD DS를 준비하는 데 필요한 단계가 나와 있습니다.

### Active Directory 준비 단계

<table>
<colgroup>
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
</colgroup>
<thead>
<tr class="header">
<th></th>
<th>단계</th>
<th>설명</th>
<th>실행 위치</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>1.</p></td>
<td><p><a href="lync-server-2013-preparing-the-active-directory-schema.md">Lync Server 2013에서 Active Directory 스키마 준비</a></p></td>
<td><p>Lync Server에서 사용되는 새 클래스 및 특성을 추가하여 Active Directory 스키마를 확장합니다.</p>
<p>Lync Server가 배포된 배포에서 각 포리스트에 대해 한 번씩 실행합니다.</p></td>
<td><p>Lync Server를 배포할 각 포리스트의 루트 도메인에 있는 스키마 마스터에 대해 실행합니다.</p>


> [!NOTE]
> 스키마 마스터에 대한 사용 권한이 있는 경우 루트 도메인에서 이 단계를 실행할 필요가 없습니다. 단, 루트 도메인에서 Schema Admins 그룹의 구성원이어야 하며 스키마 마스터에서 Enterprise Admins 그룹의 구성원이어야 합니다. 리소스 포리스트 토폴로지에서는 사용자 포리스트가 아니라 리소스 포리스트에서만 이 단계를 실행합니다. 중앙 포리스트 토폴로지에서는 사용자 포리스트가 아니라 중앙 포리스트에서만 이 단계를 실행합니다.


</td>
</tr>
<tr class="even">
<td><p>2.</p></td>
<td><p><a href="lync-server-2013-preparing-the-forest.md">Lync Server 2013에 대한 포리스트 준비</a></p></td>
<td><p>Lync Server에 사용되는 전역 설정과 유니버설 그룹을 만듭니다.</p>
<p>Lync Server가 배포된 배포에서 각 포리스트에 대해 한 번씩 실행합니다.</p></td>
<td><p>Lync Server를 배포할 각 포리스트의 루트 도메인에서 실행합니다. 이 단계를 실행하려면 Enterprise Admins 그룹의 구성원이어야 합니다.</p>


> [!NOTE]
> 리소스 포리스트 토폴로지에서는 사용자 포리스트가 아니라 리소스 포리스트에서만 이 단계를 실행합니다. 중앙 포리스트 토폴로지에서는 사용자 포리스트가 아니라 중앙 포리스트에서만 이 단계를 실행합니다.


</td>
</tr>
<tr class="odd">
<td><p>3.</p></td>
<td><p><a href="lync-server-2013-preparing-domains.md">Lync Server 2013에 대한 도메인 준비</a></p></td>
<td><p>유니버설 그룹의 구성원으로 사용할 개체에 대한 사용 권한을 추가합니다.</p>
<p>사용자 도메인이나 서버 도메인당 한 번씩 실행합니다.</p>


> [!NOTE]
> Lync Server 2010에서 Lync Server 2013으로 마이그레이션한 경우 배포 마법사에 도메인 준비가 이미 완료되었다고 표시될 수 있습니다. 도메인 준비를 다시 실행할 필요는 없습니다. 권한은 Lync Server 2010에서 Lync Server 2013으로 변경되지 않습니다.


</td>
<td><p>Lync Server가 배포된 각 도메인의 구성원 서버에서 실행합니다. 이 단계를 실행하려면 Domain Admins 그룹의 구성원이어야 합니다.</p></td>
</tr>
</tbody>
</table>


대부분의 구성 정보가 AD DS에 저장되던 Office Communications Server 2007 R2와 달리, Lync Server 2013은 Lync Server 2010과 마찬가지로 대부분의 구성 정보를 중앙 관리 저장소에 저장합니다. 하지만 다음과 같은 정보는 계속해서 AD DS에 저장됩니다.

  - **스키마 확장**:
    
      - 사용자 개체 확장
    
      - 이전 버전과의 호환성을 유지 관리하기 위한 Office Communications Server 2007 R2 클래스에 대한 확장

<!-- end list -->

  - **데이터**( Lync Server 확장 스키마 및 기존 스키마 클래스에 저장됨):
    
      - 사용자 SIP URI(Uniform Resource Identifier) 및 기타 사용자 설정
    
      - 응답 그룹 및 회의 길잡이 등과 같은 응용 프로그램에 대한 대화 상대 개체
    
      - 중앙 관리 저장소에 대한 포인터
    
      - Kerberos 인증 계정(선택적 컴퓨터 개체)

Lync Server 2013에서는 RTCUniversalServerAdmins 유니버설 그룹에 설치 권한을 부여하여 설치 및 관리를 위임하므로 서버가 토폴로지에 추가되고 게시 및 사용 가능하도록 설정된 후 해당 그룹의 구성원이 로컬 서버에서 Lync Server 2013 을 설치하고 활성화할 수 있습니다. 위임된 사용자는 Lync Server 2013을 설치하고 활성화하는 컴퓨터의 로컬 관리자여야 하며, Domain Admins 그룹의 구성원일 필요는 없습니다. 지정된 OU(조직 구성 단위)의 개체에 대해 사용 권한을 부여하여 Domain Admins 그룹의 구성원 자격 없이 포리스트를 준비하는 동안 만들어진 유니버설 그룹의 구성원이 해당 개체에 액세스할 수 있습니다.

Lync Server 2013을 새로 배포하려면 전역 설정이 구성 컨테이너에 저장되어 있어야 합니다. 조직이 이전 버전에서 업그레이드하고 있지만 시스템 컨테이너에 전역 설정이 계속 있는 경우 시스템 컨테이너가 계속해서 지원됩니다.

## 참고 항목

#### 개념

[Lync Server 2013에서 Active Directory 스키마 준비](lync-server-2013-preparing-the-active-directory-schema.md)  
[Lync Server 2013에서 사용하는 Active Directory 스키마 확장, 클래스 및 속성](lync-server-2013-active-directory-schema-extensions-classes-and-attributes-used-by-lync-server.md)  

#### 기타 리소스

[Lync Server 2013에 대한 포리스트 준비](lync-server-2013-preparing-the-forest.md)  
[Lync Server 2013에 대한 도메인 준비](lync-server-2013-preparing-domains.md)

