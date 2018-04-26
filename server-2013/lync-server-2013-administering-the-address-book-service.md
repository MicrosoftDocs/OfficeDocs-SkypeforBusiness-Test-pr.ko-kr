---
title: Lync Server 2013에서 주소록 서비스 관리
TOCTitle: Lync Server 2013에서 주소록 서비스 관리
ms:assetid: 801e4243-9670-4477-aa2f-88b61ecf5351
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg429711(v=OCS.15)
ms:contentKeyID: 49304201
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Lync Server 2013에서 주소록 서비스 관리

 

_**마지막으로 수정된 항목:** 2015-03-09_

주소록 서비스는 Lync Server, Enterprise Edition 또는 Standard Edition 서버 배포의 일부로 기본적으로 설치됩니다. 주소록 서비스에 사용되는 데이터베이스(RTCab)는 SQL Server(Enterprise Edition의 경우 백 엔드 SQL Server, Standard Edition 서버의 경우 함께 배치된 SQL Server)에 생성됩니다.


> [!NOTE]
> <STRONG>ADSI 편집</STRONG>을 사용하여 Active Directory 도메인 서비스 개체 특성을 편집하는 방법에 대한 자세한 내용은 <A href="http://go.microsoft.com/fwlink/?linkid=330427">ADSI 편집</A>을 참고하세요. 특별히 주소록 서비스를 위한 리소스 키트 도구에 대한 자세한 내용은 <A href="http://go.microsoft.com/fwlink/?linkid=330429">Microsoft Lync Server 2013 Resource Kit Tools</A>를 참고하세요.



## 주소록 서버 전화 번호 정규화

Lync Server에는 표준화된 RFC 3966/E.164 전화 번호가 필요합니다. 구조화되지 않았거나 일관적이지 않은 형식의 전화 번호를 사용하기 위해 Lync Server는 주소록 서버를 기반으로 전화 번호를 정규화 규칙으로 전달하기 전에 사전 처리합니다. 주소록에서 가져온 전화 번호를 사용하고 정규화 규칙을 적용하는 경우 Lync Phone Edition 및 Lync Mobile과 같은 클라이언트에서는 이러한 정규화된 번호를 사용합니다.

이전 버전에서 사용된 정규화 규칙을 적용하려면 일부 설정을 조정해야 합니다. 공백 및 필수가 아닌 문자는 정규화 규칙이 적용되기 전에 제거되기 때문에 regex 식에서 특별히 대시 또는 제거된 다른 문자를 찾는 경우 정규화 규칙이 실패할 수 있습니다. 정규화 규칙을 검토하여 이러한 필수가 아닌 문자를 찾지 않는지 또는 규칙에서 예상하는 곳에 문자가 없는 경우 규칙이 정상적으로 실패하고 계속 적용될 수 있는지 확인해야 합니다.

## User Replicator와 주소록 서버

주소록 서버는 User Replicator에서 제공된 데이터를 사용하여 초기에 GAL(전체 주소 목록)에서 가져온 정보를 업데이트합니다. User Replicator는 각 사용자, 연락처 및 그룹에 대한 Active Directory 도메인 서비스 특성을 데이터베이스의 AbUserEntry 테이블에 기록하고, 주소록 서버는 데이터베이스의 사용자 데이터를 주소록 서버 파일 저장소 및 주소록 데이터베이스(RTCab 또는 RTCab1)에 동기화합니다. AbUserEntry 테이블의 스키마에는 **UserGuid**와 **UserData**라는 두 개의 열이 사용됩니다. **UserGuid**는 Active Directory 개체의 16바이트 GUID를 포함하는 인덱스 열이고, **UserData**는 위에 언급된 해당 연락처에 대한 모든 Active Directory 도메인 서비스 특성을 포함하는 이미지 열입니다.

User Replicator는 AbUserEntry 테이블과 동일한 SQL Server 기반 인스턴스에 있는 구성 테이블을 읽어 기록할 Active Directory 특성을 결정합니다. AbAttribute 테이블에는 **ID**, **이름**, **플래그** 및 **사용**이라는 세 개의 열이 있습니다. 이 테이블은 데이터베이스 설정 중에 만들어집니다. AbAttribute 테이블이 비어 있는 경우 User Replicator는 해당 AbUserEntry 테이블 처리 논리를 건너뜁니다. 주소록 서버 특성은 동적이며 주소록 서버가 활성화될 때 주소록 서버에서 처음으로 작성한 AbAttribute 테이블에서 검색됩니다.

주소록 서버 활성화 시 AbAttribute 테이블은 다음 표에 있는 값으로 채워집니다.


<table>
<colgroup>
<col style="width: 33%" />
<col style="width: 33%" />
<col style="width: 33%" />
</colgroup>
<thead>
<tr class="header">
<th>ID</th>
<th>이름</th>
<th>플래그</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>1</p></td>
<td><p>givenName</p></td>
<td><p>0x01400000</p></td>
</tr>
<tr class="even">
<td><p>2</p></td>
<td><p>Sn</p></td>
<td><p>0x02400000</p></td>
</tr>
<tr class="odd">
<td><p>3</p></td>
<td><p>displayName</p></td>
<td><p>0x03420000</p></td>
</tr>
<tr class="even">
<td><p>4</p></td>
<td><p>Title</p></td>
<td><p>0x04000000</p></td>
</tr>
<tr class="odd">
<td><p>5</p></td>
<td><p>mailNickname</p></td>
<td><p>0x05400000</p></td>
</tr>
<tr class="even">
<td><p>6</p></td>
<td><p>Company</p></td>
<td><p>0x06000000</p></td>
</tr>
<tr class="odd">
<td><p>7</p></td>
<td><p>physicalDeliveryOfficeName</p></td>
<td><p>0x07000000</p></td>
</tr>
<tr class="even">
<td><p>8</p></td>
<td><p>msRTCSIP-PrimaryUserAddress</p></td>
<td><p>0x08520C00</p></td>
</tr>
<tr class="odd">
<td><p>9</p></td>
<td><p>telephoneNumber</p></td>
<td><p>0x09022800</p></td>
</tr>
<tr class="even">
<td><p>10</p></td>
<td><p>homePhone</p></td>
<td><p>0x0A302800</p></td>
</tr>
<tr class="odd">
<td><p>11</p></td>
<td><p>Mobile</p></td>
<td><p>0x0B622800</p></td>
</tr>
<tr class="even">
<td><p>12</p></td>
<td><p>otherTelephone</p></td>
<td><p>0x0C302000</p></td>
</tr>
<tr class="odd">
<td><p>13</p></td>
<td><p>ipPhone</p></td>
<td><p>0x0D302000</p></td>
</tr>
<tr class="even">
<td><p>14</p></td>
<td><p>Mail</p></td>
<td><p>0x0E500000</p></td>
</tr>
<tr class="odd">
<td><p>15</p></td>
<td><p>groupType</p></td>
<td><p>0x0F010800</p></td>
</tr>
<tr class="even">
<td><p>16</p></td>
<td><p>Department</p></td>
<td><p>0x10000000</p></td>
</tr>
<tr class="odd">
<td><p>17</p></td>
<td><p>Description</p></td>
<td><p>0x11000100</p></td>
</tr>
<tr class="even">
<td><p>18</p></td>
<td><p>Manager</p></td>
<td><p>0x12040001</p></td>
</tr>
<tr class="odd">
<td><p>19</p></td>
<td><p>proxyAddress</p></td>
<td><p>0x00500105</p></td>
</tr>
<tr class="even">
<td><p>20</p></td>
<td><p>msExchHideFromAddressLists</p></td>
<td><p>0xFF000003</p></td>
</tr>
<tr class="odd">
<td><p>99</p></td>
<td><p>entryID</p></td>
<td><p>0x99000000</p></td>
</tr>
</tbody>
</table>


**ID** 열의 숫자는 고유해야 하며 재사용할 수 없습니다. 또한 ID 값을 256 미만으로 유지하면 주소록 서버에서 작성하는 출력 파일의 공간이 절약됩니다. 그러나 최대 ID 값은 65535입니다. **이름** 열은 User Replicator가 각 연락처의 AbUserEntry 테이블에 입력해야 하는 Active Directory 특성 이름에 해당합니다. **플래그** 열의 값은 특성 유형을 정의하는 데 사용됩니다. User Replicator에서 인식되는 주소록 서버 특성의 유형은 다음과 같으며, **플래그** 열 값의 낮은 바이트로 표시됩니다.


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
<td><p>0x0</p></td>
<td><p>문자열 특성입니다. User Replicator는 이 유형을 AbUserEntry 테이블에 저장하기 전에 UTF-8로 변환합니다.</p></td>
</tr>
<tr class="even">
<td><p>0x1</p></td>
<td><p>이진 특성입니다. User Replicator는 이 유형을 변환하지 않고 blob에 저장합니다.</p></td>
</tr>
<tr class="odd">
<td><p>0x2</p></td>
<td><p>특성 값이 &quot;tel:&quot;로 시작하는 경우에만 포함되는 문자열 특성입니다. 주로 다중값 문자열 특성(특히 <strong>proxyAddresses</strong>)에 사용됩니다. 이 경우 주소록 서버는 &quot;tel:&quot;로 시작하는 <strong>proxyAddresses</strong> 항목에만 관련이 있습니다. 따라서 공간을 절약하기 위해 User Replicator는 &quot;tel:&quot;로 시작하는 항목만 저장합니다.</p></td>
</tr>
<tr class="even">
<td><p>0x3</p></td>
<td><p>부울 문자열 특성입니다. TRUE로 설정하면 User Replicator가 AbUserEntry 테이블에 해당 연락처를 포함하지 않고, FALSE로 설정하면 User Replicator가 AbUserEntry 테이블에 해당 연락처의 특성을 포함합니다(이 플래그가 있는 특정 특성은 제외). 이는 주로 <strong>msExchHideFromAddressLists</strong> 특성에 사용되는 또 다른 특별한 유형입니다.</p></td>
</tr>
<tr class="odd">
<td><p>0x4</p></td>
<td><p>특성 값이 &quot;smtp:&quot;로 시작하고 &quot;@&quot; 기호를 포함하는 경우에만 포함되는 문자열 특성입니다.</p></td>
</tr>
<tr class="even">
<td><p>0x5</p></td>
<td><p>특성 값이 &quot;tel:&quot; 또는 &quot;smtp:&quot;로 시작하고 &quot;@&quot; 기호를 포함하는 경우에만 포함되는 문자열 특성입니다. 문자열 특성입니다.</p></td>
</tr>
<tr class="odd">
<td><p>0x100</p></td>
<td><p>이 유형은 설정된 경우 각 연락처에 대해 두 번 이상 표시될 수 있는 다중값 특성입니다.</p></td>
</tr>
<tr class="even">
<td><p>0x400</p></td>
<td><p>이 유형은 설정된 경우 연락처의 전자 메일 사용자 계정 이름 특성을 나타냅니다. 주소록 서버는 이 플래그를 사용하여 전화 정규화 이벤트 로그 항목에 표시할 특성 값을 확인합니다.</p></td>
</tr>
<tr class="odd">
<td><p>0x800</p></td>
<td><p>이 유형은 설정된 경우 연락처의 필수 특성을 나타냅니다. 주소록 서버는 Active Directory에 이 특성에 대한 값이 있는 경우에만 AbUserEntry 테이블에 사용자를 포함합니다. 둘 이상의 필수 특성이 있는 경우 둘 중 하나의 값만 있으면 AbUserEntry 테이블에 사용자를 포함합니다.</p></td>
</tr>
<tr class="even">
<td><p>0x1000</p></td>
<td><p>이 유형이 설정된 경우 주소록 서버에서 이 특성 값을 항상 정규화합니다.</p></td>
</tr>
<tr class="odd">
<td><p>0x2000</p></td>
<td><p>이 유형이 설정된 경우 주소록 서버에서 <strong>proxyAddresses</strong>의 정규화된 번호를 사용합니다. 단, <strong>UseNormalizationRules</strong> CMS 설정이 FALSE로 설정되어 있어야 하며, 그렇지 않은 경우 플래그 비트가 0x1000인 경우와 동일하게 작동합니다.</p></td>
</tr>
<tr class="even">
<td><p>0x4000</p></td>
<td><p>이 유형이 설정된 경우 주소록 서버에서 지정된 특성에 대해 이 값을 가진 개체를 AbUserEntry 테이블에 포함하지 않습니다. 예를 들어 <strong>msRTCSIP-PrimaryUserAddress</strong> 특성에 이 플래그 비트가 설정된 경우 이 특성을 가진 연락처가 데이터베이스에 기록되지 않습니다.</p></td>
</tr>
<tr class="odd">
<td><p>0x8000</p></td>
<td><p>이 유형이 설정된 경우 주소록 서버에서 지정된 특성에 대해 이 값을 가지지 않은 개체를 AbUserEntry 테이블에 포함하지 않습니다. 하나의 개체에 0x4000 및 0x8000 플래그 비트가 둘 다 설정된 경우에는 플래그 비트 값이 0x4000으로 설정된 특성이 우선적으로 적용되므로 개체가 AbUserEntry 테이블에서 제외됩니다.</p></td>
</tr>
<tr class="even">
<td><p>0x10000</p></td>
<td><p>이 유형은 설정된 경우 그룹 개체를 나타냅니다. User Replicator는 이 플래그 비트를 사용하여 현재 상태가 그룹(예: 메일 그룹 또는 보안 그룹)을 나타내는 <strong>groupType</strong> 특성을 가진 연락처를 포함합니다.</p></td>
</tr>
<tr class="odd">
<td><p>0x20000</p></td>
<td><p>이 유형이 설정된 경우 User Replicator는 이 플래그 비트를 사용하여 장치별 주소록 서버 파일(즉, 확장명이 .dabs인 파일)에 이 특성을 포함합니다.</p></td>
</tr>
</tbody>
</table>


이전 버전의 Lync Server에서 변경 내용을 Active Directory에 적용할 때는 관리자가 **Update -CSUserDatabase** 및 **Update –CSAddressBook**Windows PowerShell cmdlet을 실행하여 변경 내용을 Lync Server 사용자 데이터베이스 및 RTCab 데이터베이스에 즉시 저장해야 합니다. Lync Server 2013에서 Lync Server User Replicator는 Active Directory에서 변경 내용을 선택하고 구성된 간격에 따라 Lync Server 사용자 데이터베이스를 업데이트합니다. Lync Server User Replicator는 또한 관리자가 Update-CSAddressBook을 실행할 필요 없이 RTCab 데이터베이스에 변경 내용을 신속하게 전파합니다. 주소록 웹 쿼리가 설정된 경우, 변경 내용이 Lync 클라이언트의 검색 결과에 반영됩니다. 주소록 파일 다운로드가 설정된 경우 관리자는 Update -CSAddressBook만 실행하면 됩니다.


> [!NOTE]
> 기본적으로 Lync Server User Replicator는 5분마다 자동으로 실행됩니다. 이 간격은 Set -CSUserReplicatorConfiguration -ReplicationCycleInterval &lt;&gt;를 사용하여 구성할 수 있습니다.



## 주소록 필터링

AbAttribute 테이블에 나열된 특정 Active Directory 도메인 서비스 특성을 기반으로 주소록 서버 파일에 채워지는 사용자를 제어할 수 있습니다. 필터링에 사용되는 이러한 특성 중 하나는 **msExchangeHideFromAddressBook** 특성입니다. 이 특성은 Exchange 스키마에 의해 추가되는 사용자 특성으로서, 값이 TRUE인 경우 Exchange Server에서는 이 특성을 사용하여 연락처를 Outlook GAL(전체 주소 목록)에서 숨깁니다. 마찬가지로, 이 특성 값이 TRUE인 경우 User Replicator에서 AbUserEntry 테이블에 이 사용자를 포함하지 않으므로 주소록 서버 파일에는 이 사용자가 포함되지 않습니다.

일부 플래그 비트를 사용하여 주소록 서버 특성에 대해 사용할 필터를 정의할 수 있습니다. 예를 들어 특정 플래그 비트를 표시하여 특성을 포함 특성 또는 제외 특성으로 구분할 수 있습니다. User Replicator는 제외 특성이 포함된 연락처와 포함 특성이 포함되지 않은 연락처를 필터링합니다.


> [!WARNING]
> 주소록 필터링에 대한 자세한 내용은 <A href="lync-server-2013-address-book-server-cmdlets.md">주소록 서버 Cmdlet</A> 및 <A href="http://go.microsoft.com/fwlink/?linkid=330430">Lync 2013 주소록 필터링</A>을 참고하세요.



현재 세 가지 필터가 있으며, 아래 표에 이러한 필터가 나와 있습니다.


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
<td><p>0x800</p></td>
<td><p>이 유형은 설정된 경우 연락처의 필수 특성을 나타냅니다. User Replicator는 이 플래그 비트를 사용하여 하나 이상의 필수 특성이 포함되지 않은 연락처를 필터링합니다. OuPathId는 필수 특성이므로 항상 설정됩니다. 따라서 다른 필수 특성 중 하나 이상이 설정되어 있어야 합니다. 그렇지 않으면 연락처(즉, OuPathId 필수 특성 값이 있는 연락처)가 데이터베이스에 기록되지 않습니다. 예를 들어 <strong>telephoneNumber</strong> 및 <strong>homePhone</strong>이 필수 특성으로 정의된 경우 이러한 특성 중 하나 이상이 있는 연락처만 데이터베이스에 기록됩니다.</p></td>
</tr>
<tr class="even">
<td><p>0x4000</p></td>
<td><p>이 유형은 설정된 경우 제외 특성을 나타냅니다. User Replicator는 이 플래그 비트를 사용하여 이 특성이 포함된 연락처를 필터링합니다. 예를 들어 <strong>msRTCSIP-PrimaryUserAddress</strong>가 제외 특성으로 정의된 경우 이 특성을 가진 연락처가 데이터베이스에 기록되지 않습니다.</p></td>
</tr>
<tr class="odd">
<td><p>0x8000</p></td>
<td><p>이 유형은 설정된 경우 포함 특성을 나타냅니다. User Replicator는 이 플래그 비트를 사용하여 이 특성이 포함되지 않은 연락처를 필터링합니다. 예를 들어 <strong>msRTCSIP-PrimaryUserAddress</strong>가 포함 특성으로 정의된 경우 이 특성을 가진 연락처만 데이터베이스에 기록됩니다.</p></td>
</tr>
</tbody>
</table>



> [!NOTE]
> 0x4000(제외 특성) 및 0x8000(포함 특성) 플래그 비트가 둘 다 설정된 경우에는 0x4000 비트가 0x8000 비트에 우선하므로 연락처가 제외됩니다.



특정 사용자만 포함하도록 주소록을 필터링할 수 있지만 항목을 제한하면 다른 사용자가 필터링된 사용자에게 연결하거나 필터링된 사용자의 현재 상태를 볼 수 있는 기능이 제한됩니다. 사용자는 언제든지 전체 로그인 이름을 입력하여 주소록에 없는 사용자를 찾거나 수동으로 인스턴트 메시지를 보내거나 수동으로 전화를 걸 수 있습니다. 또한 사용자의 연락처 정보는 Outlook에서 찾을 수 있습니다.

전체 연락처 레코드를 주소록 파일에 유지하면 Lync Server를 사용하여 SIP(Session Initiation Protocol)에 대해 구성되지 않은 사용자와 전자 메일, 전화 또는 Enterprise Voice 통화(즉, Enterprise Voice가 서버에서 사용할 수 있도록 설정된 경우)를 통해 연락할 수 있지만 일부 조직에서는 주소록 서버 항목에 있는 SIP를 사용할 수 있는 사용자만 포함하는 것을 선호합니다. 필수 특성의 **플래그** 열에서 0x800 비트를 제거하여 SIP를 사용할 수 있는 사용자만 포함하도록 주소록을 필터링할 수 있습니다. 이러한 필수 특성은 **mailNickname**, **telephoneNumber**, **homePhone**, **mobile**입니다. 또한 **msRTCSIP-PrimaryUserAddress** 특성의 **플래그** 열에 0x8000(포함 특성)을 설정하여 SIP를 사용할 수 있는 사용자만 포함하도록 주소록을 필터링할 수 있습니다. 이는 주소록 파일에서 서비스 계정을 제외하는 데도 유용합니다.

AbAttribute 테이블을 수정한 후 **Update-CsUserDatabase** cmdlet 명령을 실행하여 AbUserEntry 테이블의 데이터를 새로 고칠 수 있습니다. UR 복제가 완료되면 **UpdateCsAddressBook** 명령을 수동으로 실행하여 주소록 서버 파일 저장소의 파일을 업데이트할 수 있습니다.


> [!NOTE]
> 주소록 서버가 배치된 프런트 엔드 서버는 관리적으로 구성할 수 없습니다. 프런트 엔드 서버는 배포 중에 선택되고 일반적으로 첫 번째 프런트 엔드 서버가 배포됩니다. 실패할 경우에는 주소록 서비스가 다른 프런트 엔드 서버로 이동되며, 관리 주의는 필요하지 않습니다.




> [!IMPORTANT]
> 다중 포리스트 배포 또는 상위/하위 배포에서 인프라를 통합하거나 다른 방식으로 수정한 경우(예: Lync Server으로 이동하기 전에 인프라를 통합한 경우)에는 일부 사용자에 대해 주소록 서비스 다운로드 및 주소록 웹 쿼리가 실패할 수 있습니다. 여러 도메인 또는 포리스트가 포함된 배포에서는 <STRONG>MsRTCSIP-OriginatorSid</STRONG> 특성이 채워진 사용자 개체에서 문제가 발생합니다. 문제를 해결하려면 이러한 개체에 대한 <STRONG>MsRTCSIP-OriginatorSid</STRONG> 특성을 NULL로 설정해야 합니다.


