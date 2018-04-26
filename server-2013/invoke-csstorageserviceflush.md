---
title: Invoke-CsStorageServiceFlush
TOCTitle: Invoke-CsStorageServiceFlush
ms:assetid: 3f88a70d-79b0-4614-8604-660bac35a86f
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/JJ619175(v=OCS.15)
ms:contentKeyID: 49303420
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Invoke-CsStorageServiceFlush

 

_**마지막으로 수정된 항목:** 2015-03-09_

풀의 각 프런트 엔드 서버에서 Lync Server 저장소 서비스 데이터베이스를 플러시합니다. 데이터베이스 플러시는 대기 중인 모든 데이터를 디스크에 쓴 다음 데이터베이스 큐를 지우는 작업입니다. 이 cmdlet은 Lync Server 2013에서 도입되었습니다.

## 구문

    Invoke-CsStorageServiceFlush -FlushType <FullFlush | SteadyStateFlush> -PoolFqdn <Fqdn> [-Binding <String>] [-Force <SwitchParameter>] [-HostNameStorageService <String>] [-WaitTime <TimeSpan>]

## 예제

## 예제 1

예제 1의 명령은 풀 atl-cs-011.litwareinc.com에 있는 저장소 서비스 데이터베이스에 대해 안정 상태 플러시를 수행합니다. 안정 상태 플러시에서는 데이터를 제거할 때 데이터베이스 작업에 영향을 주지 않는 데이터만 큐에서 제거하여 디스크에 씁니다.

    Invoke-CsStorageServiceFlush -PoolFqdn "atl-cs-001.litwareinc.com" -FlushType "SteadyState"

## 자세한 정보

Lync Server 저장소 서비스는 모니터링하고 보관할 세션 데이터 및 대화 내용을 포함한 Lync Server 데이터의 관리는 물론, Microsoft Exchange Server 2013 저장소 시스템과의 통합에 필요한 공통의 인터페이스와 인프라를 제공합니다. 다른 데이터베이스와 마찬가지로 저장소 서비스도 데이터를 메모리에 캐시한 다음 시스템 리소스가 허용하는 범위 내에서 주기적으로 해당 데이터를 디스크에 씁니다.

일반적으로 관리자가 이처럼 대기 중인 데이터와 상호 작용할 필요는 없습니다. 하지만 큐가 너무 커지거나 데이터베이스에 연결된 고급 등록자 풀에 장애 조치가 발생하는 경우가 있을 수 있습니다. 이 경우 **Invoke-CsStorageServiceFlush** cmdlet을 호출하여 대기 중인 모든 데이터를 디스크에 쓴 다음 데이터베이스 캐시를 삭제할 수 있습니다.

**Invoke-CsStorageServiceFlush** cmdlet은 소프트웨어 업그레이드 등을 위해 여러 프런트 엔드 서버를 동시에 종료해야 할 때도 유용합니다. 원래 풀의 프런트 엔드 서버를 하나씩 종료하고 다시 시작해야 합니다. 이는 라우팅 그룹 재분산으로 인해 발생할 수 있는 데이터 손실을 예방하는 데 도움이 됩니다. 그러나 여러 서버를 동시에 종료해야 할 경우가 있습니다. 이러한 경우 손실이 발생하지 않도록 컴퓨터 종료 전에 **Invoke-CsStorageServiceFlush** cmdlet을 실행합니다. 이렇게 하면 서버가 실제로 종료되기 전에 풀을 위해 큐가 플러시되고 모든 데이터가 디스크에 작성됩니다.

사용자가 직접 만든 사용자 지정 RBAC(역할 기반 액세스 제어) 역할을 포함하여 이 cmdlet이 할당된 모든 RBAC 역할의 목록을 반환하려면 Windows PowerShell 명령줄 인터페이스 프롬프트에서 다음 명령을 실행합니다.

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Invoke-CsStorageServiceFlush"}

**Lync Server 제어판:** **Invoke-CsStorageServiceFlush** cmdlet에 의해 수행되는 기능은 Lync Server 제어판에서는 사용할 수 없습니다.

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
<td><p><em>FlushType</em></p></td>
<td><p>필수</p></td>
<td><p>Microsoft.Rtc.Management.Hadr.FlushType</p></td>
<td><p>수행할 저장소 플러시의 유형을 지정합니다. 허용되는 값은 다음과 같습니다.</p>
<p>* SteadyState – 큐에서 제거할 때 저장소 서비스의 정상적인 작동에 영향을 주지 않는 데이터만 플러시합니다. 이 플러시는 보통 큐에서 오래된 데이터를 제거할 때 수행합니다.</p>
<p>* FullFlush – 큐에서 모든 데이터를 플러시합니다. 이는 풀에 장애 조치가 발생할 때 및 큐에 새 데이터가 들어올 가능성이 없을 때 사용됩니다.</p></td>
</tr>
<tr class="even">
<td><p><em>PoolFqdn</em></p></td>
<td><p>필수</p></td>
<td><p>Microsoft.Rtc.Management.Deploy.Fqdn</p></td>
<td><p>플러시할 저장소 서비스가 있는 풀의 정규화된 도메인 이름입니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>Binding</em></p></td>
<td><p>선택</p></td>
<td><p>System.String</p></td>
<td><p>WCF(Windows Communication Foundation) 바인딩입니다. WCF 바인딩은 클라이언트와 서비스가 서로 통신하는 데 필요한 전송, 인코딩 및 프로토콜 세부 정보를 결정합니다. 유효한 값은 다음과 같습니다.</p>
<p>* NetNamedPipe</p>
<p>* NetTCP</p></td>
</tr>
<tr class="even">
<td><p><em>Force</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>명령 실행 중 오류가 발생할 경우 치명적인 오류를 제외하고 오류 메시지를 표시하지 않습니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>HostNameStorageService</em></p></td>
<td><p>선택</p></td>
<td><p>System.String</p></td>
<td><p>Lync Server 저장소 서비스가 실행 중인 서버의 정규화된 도메인 이름입니다. Binding을 NetTCP로 설정하는 경우 이 매개 변수가 필요합니다.</p></td>
</tr>
<tr class="even">
<td><p><em>WaitTime</em></p></td>
<td><p>선택</p></td>
<td><p>System.TimeSpan</p></td>
<td><p>플러시가 시작된 것으로 판단하고 플러시 프로세스의 다음 단계로 넘어가기 전까지 cmdlet이 대기하는 최대 시간을 지정합니다.</p></td>
</tr>
</tbody>
</table>


## 입력 형식

없음. **Invoke-CsStorageServiceFlush** cmdlet은 파이프라인된 데이터를 허용하지 않습니다.

## 반환 형식

문자열 값

## 참고 항목

#### 기타 리소스

[Invoke-CsPoolFailOver](invoke-cspoolfailover.md)

