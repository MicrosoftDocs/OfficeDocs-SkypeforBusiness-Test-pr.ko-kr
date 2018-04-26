---
title: Test-CsExStorageConnectivity
TOCTitle: Test-CsExStorageConnectivity
ms:assetid: 20fda110-5e09-4453-bb7b-a062abaab87f
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/JJ204740(v=OCS.15)
ms:contentKeyID: 49303035
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Test-CsExStorageConnectivity

 

_**마지막으로 수정된 항목:** 2015-03-09_

Lync Server 저장소 서비스가 프런트 엔드 서버에서 작동 중인지를 확인합니다. 이 작업은 지정된 Exchange 사서함에서 테스트 전자 메일 메시지를 작성한 다음 원하는 경우 텍스트 종료 시 해당 메시지를 삭제하는 방법으로 수행합니다. **Test-CsExStorageConnectivity**는 Exchange 보관이 예상대로 작동하는지도 확인합니다. 이 cmdlet은 Lync Server 2013에서 도입되었습니다.

## 구문

    Test-CsExStorageConnectivity -SipUri <String> [-Binding <String>] [-DeleteItem <SwitchParameter>] [-Folder <ConversationHistory | Inbox | Dumpster>] [-Force <SwitchParameter>] [-HostNameStorageService <String>] [-UseCache <SwitchParameter>]

## 예제

## 예제 1

예제 1에 표시된 명령은 Lync Server 저장소 서비스가 사용자 sip:kenmyer@litwareinc.com의 Exchange 사서함에 연결할 수 있는지 확인합니다. 이 예제에서는 NetNamedPipe가 WCF 바인딩으로 사용됩니다.

    Test-CsExStorageConnectivity -SipUri "sip:kenmyer@litwareinc.com" -Binding "NetNamedPipe"

## 예제 2

예제 2에서는 Lync Server 저장소 서비스가 Exchange 2013의 보관 저장소에 연결할 수 있는지를 확인합니다. 지정된 사용자가 Exchange 보관을 사용하도록 설정되지 않은 경우 이 명령은 실패합니다. 이 예제에서는 휴지통 폴더에 대한 연결을 수행합니다. 복구 가능 항목 제거 폴더인 휴지통 폴더는 삭제된 항목을 저장하는 데 사용되는 폴더로, 최종 사용자에게는 표시되지 않습니다.

    Test-CsExStorageConnectivity -SipUri "sip:kenmyer@litwareinc.com" -Binding "NetNamedPipe" -Folder Dumpster

## 자세한 정보

**Test-CsExStorageConnectivity** cmdlet은 Lync Server 2013과 Exchange 2013 간의 서버 간 인증이 작동하는지 확인하는 데 사용됩니다. 서버 간 인증을 확인하기 위해 이 cmdlet은 Exchange 2013에 로그온하여 지정된 사서함의 대화 내용 폴더에 항목을 쓴 다음 해당 항목을 삭제합니다.

**Test-CsExStorageConnectivity** cmdlet을 사용하여 Exchange 2013의 보관 저장소에 연결할 수 있는지를 확인할 수도 있습니다.

이 cmdlet을 실행할 때 "액세스 거부" 메시지가 표시되면 RTC Local User Administrators 로컬 그룹의 구성원이 아닌 것입니다. **Test-CsExStorageConnectivity** cmdlet을 실행하는 데 필요한 권한을 얻으려면 이 그룹 또는 RTCUniversalUserAdmins Active Directory 그룹(RTC Local User Administrators의 구성원)에 추가하면 됩니다.

사용자가 직접 만든 사용자 지정 RBAC(역할 기반 액세스 제어) 역할을 포함하여 이 cmdlet이 할당된 모든 RBAC 역할의 목록을 반환하려면 Windows PowerShell 프롬프트에서 다음 명령을 실행합니다.

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Test-CsExStorageConnectivity"}

**Lync Server 제어판:** **Test-CsExStorageConnectivity** cmdlet에 의해 수행되는 기능은 Lync Server 제어판에서는 사용할 수 없습니다.

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
<td><p>테스트 항목을 만들 Exchange 2013 사서함의 SIP 주소입니다.</p></td>
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
<td><p>이 매개 변수가 있으면 텍스트 종료 시 테스트 항목이 Exchange 2013 사서함에서 삭제됩니다.</p></td>
</tr>
<tr class="even">
<td><p><em>Folder</em></p></td>
<td><p>선택</p></td>
<td><p>Microsoft.Rtc.Management.Lyss.Cmdlets.ExchFolder</p></td>
<td><p>cmdlet이 연결할 Exchange 2013 보관 폴더를 지정합니다. 사용 가능한 값은 다음과 같습니다.</p>
<p>* ConversationHistory</p>
<p>* Inbox</p>
<p>* Dumpster</p></td>
</tr>
<tr class="odd">
<td><p><em>Force</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>명령을 실행할 때 발생할 수 있는 심각하지 않은 오류 메시지를 표시하지 않습니다.</p></td>
</tr>
<tr class="even">
<td><p><em>HostNameStorageService</em></p></td>
<td><p>선택</p></td>
<td><p>System.String</p></td>
<td><p>Lync Server 저장소 서비스가 실행 중인 서버의 FQDN(정규화된 도메인 이름)입니다. Binding을 NetTCP로 설정하는 경우 이 매개 변수가 필요합니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>UseCache</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>이 매개 변수가 있으면 Exchange 연결 시 캐시된 자동 검색 결과를 사용하도록 cmdlet에 명령합니다.</p></td>
</tr>
</tbody>
</table>


## 입력 형식

없음. Test-CsExStorageConnectivity cmdlet은 파이프라인된 입력을 허용하지 않습니다.

## 반환 형식

**Test-CsExStorageConnectivity** cmdlet은 Microsoft.Rtc.Management.ResourceData 개체의 인스턴스를 반환합니다.

## 참고 항목

#### 기타 리소스

[Test-CsExStorageNotification](test-csexstoragenotification.md)

