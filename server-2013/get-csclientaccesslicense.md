---
title: Get-CsClientAccessLicense
TOCTitle: Get-CsClientAccessLicense
ms:assetid: 435062d3-b7f9-400c-9ce7-fb6b6ffce44a
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/JJ204853(v=OCS.15)
ms:contentKeyID: 49303464
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Get-CsClientAccessLicense

 

_**마지막으로 수정된 항목:** 2015-03-09_

조직의 클라이언트 라이선스 사용에 대한 정보를 반환합니다. 이 cmdlet은 Lync Server 2013에서 도입되었습니다.

## 구문

    Get-CsClientAccessLicense -LicenseBasedType <String> -LicenseName <String> -MonitoringDatabase <String> -StartDate <DateTime> [-DailyUsage <SwitchParameter>] [-EndDate <DateTime>] <COMMON PARAMETERS>

    Get-CsClientAccessLicense -License <SwitchParameter> <COMMON PARAMETERS>

    COMMON PARAMETERS:

## 예제

## 예제 1

예제 1에 표시된 명령은 모니터링 데이터베이스 atl-sql-001\\Archinst에 기록된 사용자 기반 라이선스에 대한 표준 라이선스 사용을 반환합니다. 2012년 6월 1일(6/1/2012)에서 현재 날짜까지의 기간에 대한 라이선스 사용 정보가 반환됩니다.

    Get-CsClientAccessLicense -MonitoringDatabase "atl-sql-001\Archinst" -LicenseName "Standard" -LicenseBasedType "UserBased" -StartDate "6/1/2012"

## 자세한 정보

관리자는 **Get-CsClientAccessLicense** cmdlet을 사용하여 Lync 클라이언트 라이선스 사용을 모니터링할 수 있습니다. 이 작업은 사용자 등록을 기준으로 지정된 기간 동안의 클라이언트 라이선스 사용을 표시하여 수행합니다. 이 cmdlet이 클라이언트 라이선스를 자동으로 관리하지는 않습니다. 예를 들어 cmdlet을 실행해도 추가 라이선스가 필요하다는 메시지가 표시되지는 않습니다. 대신 이 cmdlet은 지정된 기간 동안 사용된 라이선스 수에 대한 정보만 반환합니다.

모니터링 서비스와 통화 정보 기록을 사용하도록 설정한 경우에만 **Get-CsClientAccessLicense** cmdlet을 사용할 수 있습니다. 이는 등록 정보가 통화 정보 기록 데이터베이스에 저장되기 때문입니다. 이름에서 알 수 있듯이 **Get-CsClientAccessLicense** cmdlet은 클라이언트 라이선스에 대한 정보만 반환합니다. 서버 라이선스에 대한 정보가 필요할 경우 [Get-CsService](get-csservice.md) cmdlet을 사용하여 모든Lync Server 2013 데이터베이스의 FQDN(정규화된 도메인 이름)을 반환할 수 있습니다. 프런트 엔드 서버의 FQDN이 백 엔드 서버의 FQDN과 일치할 경우 표준 라이선스를 갖고 있는 것입니다. 두 FQDN이 일치하지 않으면 엔터프라이즈 라이선스를 갖고 있는 것입니다.

**Get-CsClientAccessLicense** cmdlet이 잘못된 라이선스 수를 반환하는 경우도 있습니다. 예를 들면 다음과 같습니다.

\* 모바일 사용자가 데스크톱 클라이언트를 사용하여 여러 위치에서 로그인하는 경우 라이선스가 과다하게 계산될 수 있습니다.

\* 사용자가 모바일 클라이언트와 연결할 경우 장치의 IP 주소를 확인할 수 없기 때문에 라이선스 수가 실제보다 적게 계산될 수 있습니다. 또한 모바일 장치에서 세션 중에 해당 IP 주소가 변경될 경우 라이선스 수가 실제보다 과다하게 계산될 수 있습니다.

\*Lync 클라이언트로의 PSTN 호출 또는 Lync 클라이언트에서 PSTN 전화로의 호출 시 라이선스가 두 번 계산될 수 있습니다. 이는 세션에 이용되는 라이선스 수를 결정할 때Lync 사용자 계정과 PSTN 전화 번호가 모두 사용되기 때문입니다.

\* 라이선스 사용 쿼리를 실행하기 전에 Lync 전화가 시스템에 로그온되는 경우 전화에 대한 라이선스가 계산되지 않을 수 있습니다.

\* 사용자가 PSTN 전화를 사용하여 회의에 참가할 경우 해당 통화에 대해 단일 라이선스 사용이 기록됩니다. 그러나 PSTN 전화를 사용하여 회의에 참가하는 데는 실제로 라이선스가 필요하지 않습니다.


> [!NOTE]
> 자세한 내용과 이러한 문제를 해결하는 방법은 <A href="lync-server-2013-release-notes.md">Lync Server 2013 릴리스 정보</A>를 참고하세요.



사용자가 직접 만든 사용자 지정 RBAC(역할 기반 액세스 제어) 역할을 포함하여 이 cmdlet이 할당된 모든 RBAC 역할의 목록을 반환하려면 Windows PowerShell 명령줄 인터페이스 프롬프트에서 다음 명령을 실행합니다.

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Get-CsClientAccessLicense"}

**Lync Server 제어판:** **Get-CsClientAccessLicense** cmdlet에 의해 수행되는 기능은 Lync Server 제어판에서는 사용할 수 없습니다.

## 매개 변수


<table>
<colgroup>
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
</colgroup>
<thead>
<tr class="header">
<th>매개 변수</th>
<th>필수</th>
<th>유형</th>
<th>설명</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><em>License</em></p></td>
<td><p>필수</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>사용 가능한 라이선스 이름을 반환합니다. 이 매개 변수는 다른 매개 변수와 함께 사용할 수 없으며, 사용 가능한 구문은 다음 구문뿐입니다.</p>
<p>Get-CsClientAccessLicense -License</p></td>
</tr>
<tr class="even">
<td><p><em>LicenseBasedType</em></p></td>
<td><p>필수</p></td>
<td><p>System.String</p></td>
<td><p>라이선스가 UserBased인지 아니면 DeviceBased인지를 나타냅니다. UserBased 라이선스의 경우 Lync Server에 액세스하는 각 사용자가 Lync Server에 액세스하는 데 사용하는 장치의 수에 관계없이 클라이언트 액세스 라이선스를 소유하고 있어야 합니다. DeviceBased 라이선스의 경우에는 Lync Server에 액세스하는 데 사용되는 각 장치에서 별도의 라이선스가 필요합니다.</p>
<p>사이트를 항상 사용하지는 않으며 여러 장치를 통해 Lync Server에 액세스하는 사용자의 경우에는 대개 사용자 기반 라이선스를 사용하는 것이 좋습니다. 장치 기반 라이선스는 일반적으로 데스크톱 컴퓨터와 같은 공유 장치를 통해서만 Lync Server에 액세스하는 온사이트 사용자용입니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>LicenseName</em></p></td>
<td><p>필수</p></td>
<td><p>System.String</p></td>
<td><p>검색할 라이선스의 종류를 나타냅니다. 사용 가능한 값은 다음과 같습니다.</p>
<p>* Standard</p>
<p>* Enterprise</p>
<p>* Plus</p></td>
</tr>
<tr class="even">
<td><p><em>MonitoringDatabase</em></p></td>
<td><p>필수</p></td>
<td><p>System.String</p></td>
<td><p>모니터링 데이터베이스용 SQL Server 인스턴스입니다. 일반적으로 SQL Server 컴퓨터의 정규화된 도메인 이름과 모니터링 데이터베이스의 SQL Server 인스턴스를 사용하여 지정합니다. 예를 들면 다음과 같습니다.</p>
<p>-MonitoringDatabase &quot;atl-sql-001.litwareinc.com\archinst&quot;</p>
<p>모니터링 데이터베이스가 기본 SQL Server 인스턴스인 경우에는 SQL Server를 실행하는 컴퓨터의 FQDN만 지정하면 됩니다.</p>
<p>-MonitoringDatabase &quot;atl-sql-001.litwareinc.com&quot;</p></td>
</tr>
<tr class="odd">
<td><p><em>StartDate</em></p></td>
<td><p>필수</p></td>
<td><p>System.DateTime</p></td>
<td><p>클라이언트 라이선스 사용을 확인할 기간의 시작 날짜입니다. 예를 들어 영어(미국) 형식을 사용하는 경우 StartDate 매개 변수는 다음과 같습니다.</p>
<p>-StartDate &quot;1/1/2012&quot;</p>
<p>StartDate는 EndDate 이전이어야 합니다.</p></td>
</tr>
<tr class="even">
<td><p><em>DailyUsage</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>지정하는 경우 지정된 기간에 대해 라이선스 사용이 일별로 구분됩니다. 지정하지 않는 경우에는 지정된 기간에 대해 라이선스 사용의 요약이 표시됩니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>EndDate</em></p></td>
<td><p>선택</p></td>
<td><p>System.DateTime</p></td>
<td><p>클라이언트 라이선스 사용을 확인할 기간의 종료 날짜입니다. 예를 들면 다음과 같습니다.</p>
<p>-EndDate &quot;2/1/2012&quot;</p>
<p>EndDate는 StartDate 이후여야 합니다. <strong>Get-CsClientAccessLicense</strong> cmdlet을 호출할 때는 출력에 종료 날짜가 나타나지 않습니다.</p></td>
</tr>
</tbody>
</table>


## 입력 형식

없음. **Get-CsClientAccessLicense** cmdlet은 파이프라인된 입력을 허용하지 않습니다.

## 반환 형식

**Get-CsClientAccessLicense** cmdlet은 라이선스 정보를 반환합니다.

## 참고 항목

#### 기타 리소스

[Get-CsUser](get-csuser.md)

