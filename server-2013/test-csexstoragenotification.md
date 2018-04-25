---
title: Test-CsExStorageNotification
TOCTitle: Test-CsExStorageNotification
ms:assetid: d8fe3b22-7a76-4d70-9bc1-b54b37f68449
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/JJ205331(v=OCS.15)
ms:contentKeyID: 49305218
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Test-CsExStorageNotification

 

_**마지막으로 수정된 항목:** 2015-03-09_

프런트 엔드 서버에서 실행 중인 Lync Server 저장소 서비스가 Microsoft Exchange Server 2013 사서함 알림 서비스를 구독할 수 있는지 확인합니다. 이 작업은 cmdlet이 서비스를 구독하도록 하고 항목을 만든 다음 새 항목 알림이 수신되는지 확인하고 원하는 경우 해당 항목을 삭제하여 서비스에서 항목 구독을 취소하는 방식으로 수행합니다. 이 cmdlet은 Lync Server 2013에서 도입되었습니다.

## 구문

    Test-CsExStorageNotification -SipUri <String> [-Binding <String>] [-DeleteItem <SwitchParameter>] [-Force <SwitchParameter>] [-HostNameStorageService <String>]

## 예제

## 예제 1

예제 1에 표시된 명령은 Lync Server 저장소 서비스가 사용자 sip:kenmyer@litwareinc.com의 Exchange Server 사서함 알림 서비스에 연결할 수 있는지 확인합니다. 이 예제에서는 NetNamedPipe가 WCF 바인딩으로 사용됩니다.

    Test-CsExStorageNotification -SipUri "sip:kenmyer@litwareinc.com" -Binding "NetNamedPipe"

## 자세한 정보

**Test-CsExStorageNotification** cmdlet은 사용자의 대화 상대 목록이 업데이트될 때마다 Microsoft Exchange Server 2013 알림 서비스가 Lync Server 2013에 알림을 제공할 수 있는지를 확인하는 데 사용됩니다. 이 cmdlet은 통합 연락처 저장소를 사용 중인 경우에만 유효합니다.

사용자가 직접 만든 사용자 지정 RBAC(역할 기반 액세스 제어) 역할을 포함하여 이 cmdlet이 할당된 모든 RBAC 역할의 목록을 반환하려면 Windows PowerShell 명령줄 인터페이스 프롬프트에서 다음 명령을 실행합니다.

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Test-CsExStorageNotification"}

**Lync Server 제어판:** **Test-CsExStorageNotification** cmdlet에 의해 수행되는 기능은 Lync Server 제어판에서는 사용할 수 없습니다.

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
<td><p><em>SipUri</em></p></td>
<td><p>필수</p></td>
<td><p>System.String</p></td>
<td><p>테스트 항목을 만들 Exchange Server 사서함의 SIP 주소입니다.</p></td>
</tr>
<tr class="even">
<td><p><em>Binding</em></p></td>
<td><p>선택</p></td>
<td><p>System.String</p></td>
<td><p>WCF(Windows Communication Foundation) 바인딩입니다. WCF 바인딩은 클라이언트와 서비스가 서로 통신하는 데 필요한 전송, 인코딩 및 프로토콜 세부 정보를 결정합니다. 사용 가능한 값은 다음과 같습니다.</p>
<p>* NetNamedPipe</p>
<p>* NetTCP</p></td>
</tr>
<tr class="odd">
<td><p><em>DeleteItem</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>이 매개 변수가 있으면 텍스트 종료 시 테스트 항목이 Exchange 사서함에서 삭제됩니다.</p></td>
</tr>
<tr class="even">
<td><p><em>Force</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>명령을 실행할 때 발생할 수 있는 심각하지 않은 오류 메시지를 표시하지 않습니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>HostNameStorageService</em></p></td>
<td><p>선택</p></td>
<td><p>System.String</p></td>
<td><p>Lync Server 저장소 서비스가 실행 중인 서버의 정규화된 도메인 이름입니다. Binding을 NetTCP로 설정하는 경우 이 매개 변수가 필요합니다.</p></td>
</tr>
</tbody>
</table>


## 입력 형식

없음. **Test-CsExStorageNotification** cmdlet은 파이프라인된 입력을 허용하지 않습니다.

## 반환 형식

**Test-CsExStorageNotification** cmdlet은 Microsoft.Rtc.Management.ResourceData 개체의 인스턴스를 반환합니다.

## 참고 항목

#### 기타 리소스

[Test-CsExStorageConnectivity](test-csexstorageconnectivity.md)

