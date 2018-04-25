---
title: Lync Server 2013의 스키마 변경 사항
TOCTitle: Lync Server 2013의 스키마 변경 사항
ms:assetid: d760cb93-77d4-4d64-adb7-416b808f36f8
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg398944(v=OCS.15)
ms:contentKeyID: 49305187
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Lync Server 2013의 스키마 변경 사항

 

_**마지막으로 수정된 항목:** 2015-03-09_

Lync Server 2013을 배포 및 작동하려면 스키마를 확장하여 Active Directory 도메인 서비스를 준비해야 합니다. 스키마 확장은 Lync Server 2013에 필요한 클래스 및 특성을 추가합니다.

Lync Server 2013은 몇 개의 새 클래스 및 특성을 필요로 하며, 기존의 일부 클래스와 특성을 수정합니다. 또한 Lync Server 2013에서는 대부분의 구성 정보가 이전 버전에서 AD DS에 저장된 것과 달리 중앙 관리 저장소에 저장됩니다. 단, 다음 정보는 Lync Server 2013에서 계속해서 AD DS에 저장됩니다.

  - **스키마 확장**:
    
      - 사용자 개체 확장
    
      - 지원되는 이전 버전과의 호환성을 유지 관리하기 위한 Office Communications Server 2007 및 Office Communications Server 2007 R2 클래스에 대한 확장

<!-- end list -->

  - **데이터**(Lync Server 확장 스키마 및 기존 스키마 클래스에 저장됨):
    
      - 사용자 SIP URI(Uniform Resource Identifier) 및 기타 사용자 설정
    
      - 응답 그룹 및 회의 길잡이 등과 같은 응용 프로그램에 대한 대화 상대 개체
    
      - 중앙 관리 저장소에 대한 포인터
    
      - Kerberos 인증 계정(선택적 컴퓨터 개체)

이 항목에서는 Lync Server 2013에 필요한 Active Directory 스키마 변경 내용에 대해 설명하며, 이전 버전의 Office Communications Server에서 소개된 스키마 변경 내용에 대해서는 설명하지 않습니다. 클래스 목록 및 해당 설명을 보려면 [Lync Server 2013의 스키마 클래스 및 설명](lync-server-2013-schema-classes-and-descriptions.md)을 참조하십시오. 특성 목록 및 해당 설명을 보려면 [Lync Server 2013의 스키마 특성 및 설명](lync-server-2013-schema-attributes-and-descriptions.md)을 참조하십시오. 클래스가 포함될 수 있는 특성이 있는 클래스 목록을 보려면 [Lync Server 2013의 클래스별 스키마 특성](lync-server-2013-schema-attributes-by-class.md)을 참조하십시오.

msRTCSIP 접두사는 Lync Server 관련 클래스 및 특성을 식별합니다.

## 새 Active Directory 특성

다음 표에는 Lync Server 2013에서 추가된 Active Directory 클래스가 나와 있습니다.

### Lync Server 2013에서 추가된 특성

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th>특성</th>
<th>설명</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>msExchUserHoldPolicies</p></td>
<td><p>이 다중값 특성은 사용자에 적용되는 유지 정책의 ID를 보유합니다. 유지 정책은 유지 기간 동안 사용자의 사서함 항목을 보존합니다. 이 특성은 Exchange 2013과 공유됩니다.</p></td>
</tr>
<tr class="even">
<td><p>msRTCSIP-UserRoutingGroupId</p></td>
<td><p>이는 SIP 라우팅 그룹 ID입니다. 동일한 그룹의 사용자는 동일한 프런트 엔드 서버에 등록됩니다.</p></td>
</tr>
<tr class="odd">
<td><p>msRTCSIP-MirrorBackEndServer</p></td>
<td><p>이 특성은 프런트 엔드 풀에 사용되는 SQL Server 백 엔드 미러를 저장하는 데 사용됩니다.</p></td>
</tr>
</tbody>
</table>


## 수정된 Active Directory 클래스

다음 표에는 Lync Server 2013에서 수정된 Active Directory 클래스가 나와 있습니다.

### Lync Server 2013에서 수정된 클래스

<table>
<colgroup>
<col style="width: 33%" />
<col style="width: 33%" />
<col style="width: 33%" />
</colgroup>
<thead>
<tr class="header">
<th>클래스</th>
<th>변경</th>
<th>클래스 또는 특성</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>User</p></td>
<td><p>추가: mayContain</p>
<p>추가: mayContain</p></td>
<td><p>ProxyAddresses</p>
<p>msRTCSIP-UserRoutingGroupId</p></td>
</tr>
<tr class="even">
<td><p>Contact</p></td>
<td><p>추가: mayContain</p>
<p>추가: mayContain</p></td>
<td><p>ProxyAddresses</p>
<p>msRTCSIP-UserRoutingGroupId</p></td>
</tr>
<tr class="odd">
<td><p>Mail-Recipient</p></td>
<td><p>추가: mayContain</p></td>
<td><p>msExchUserHoldPolicies</p></td>
</tr>
<tr class="even">
<td><p>msRTCSIP-GlobalTopologySetting</p></td>
<td><p>추가: mayContain</p></td>
<td><p>msRTCSIP-MirrorBackEndServer</p></td>
</tr>
</tbody>
</table>

