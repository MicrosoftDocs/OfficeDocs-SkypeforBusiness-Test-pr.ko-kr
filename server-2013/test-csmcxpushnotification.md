---
title: Test-CsMcxPushNotification
TOCTitle: Test-CsMcxPushNotification
ms:assetid: db81339b-f79a-418a-b29d-8596dff7a210
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Hh690043(v=OCS.15)
ms:contentKeyID: 49305243
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Test-CsMcxPushNotification

 

_**마지막으로 수정된 항목:** 2015-03-09_

푸시 알림 서비스가 작동하는지 확인합니다. 푸시 알림 서비스(Apple 푸시 알림 서비스 및 Microsoft 푸시 알림 서비스)를 사용하면 새 메신저 대화 또는 새 음성 메일 같은 이벤트에 대한 알림을 iPhone 및 Windows Phone 등의 모바일 장치로 보낼 수 있습니다. 이는 이러한 장치에서 현재 Lync 응용 프로그램이 일시 중단되었거나 백그라운드에서 실행 중인 경우에도 마찬가지입니다. 이 cmdlet은 Lync Server 2010용 2011년 11월 누적 업데이트에서 도입되었습니다.

## 구문

    Test-CsMcxPushNotification -AccessEdgeFqdn <String> [-Certificate <X509Certificate2>] [-Force <SwitchParameter>] [-OutLoggerVariable <String>] [-OutVerboseVariable <String>]

## 예제

## 예제 1

예제 1에 표시된 명령에서는 에지 서버 atl-edge-001.litwareinc.com을 통해 액세스하는 푸시 알림 서비스를 테스트합니다.

    Test-CsMcxPushNotification -AccessEdgeFqdn "atl-edge-001.litwareinc.com"

## 자세한 정보

Apple 푸시 알림 서비스 및 Lync Server 푸시 알림 서비스는 자신의 Apple iPhone 또는 Windows Phone에서 Lync를 실행하는 사용자가 Lync가 일시 중단되었거나 백그라운드에서 실행 중이더라도 Lync Server 이벤트에 대한 알림을 수신할 수 있도록 합니다. 예를 들어 사용자는 다음에 대한 이벤트 알림을 수신할 수 있습니다.

\- 새 메신저 대화 세션 또는 전화 회의 초대

\- 새 메신저 대화

\- 새 음성 메일

푸시 알림 서비스를 사용하지 않는 사용자는 Lync Server가 포그라운드에서 활성 응용 프로그램으로 사용되는 경우에만 이러한 알림을 수신하게 됩니다.

관리자는 Test-CsMcxPushNotification cmdlet을 사용하여 푸시 알림 서비스가 작동 중인지 여부를 확인할 수 있습니다.

이 cmdlet을 실행할 수 있는 사용자: 기본적으로 RTCUniversalServerAdmins 그룹의 구성원은 **Test-CsMcxPushNotification** cmdlet을 로컬로 실행할 수 있습니다.

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
<th>형식</th>
<th>설명</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><em>AccessEdgeFqdn</em></p></td>
<td><p>필수</p></td>
<td><p>System.String</p></td>
<td><p>푸시 알림 서비스에 연결하는 데 사용되는 액세스 에지 서버의 정규화된 도메인 이름입니다.</p></td>
</tr>
<tr class="even">
<td><p><em>Certificate</em></p></td>
<td><p>선택</p></td>
<td><p>System.Security.Cryptography.X509Certificates.X509Certificate2</p></td>
<td><p>인증을 위해 사용할 X509 인증서를 지정하는 데 사용합니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>Force</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>명령을 실행할 때 발생할 수 있는 심각하지 않은 오류 메시지를 표시하지 않습니다.</p></td>
</tr>
<tr class="even">
<td><p><em>OutLoggerVariable</em></p></td>
<td><p>선택</p></td>
<td><p>System.String</p></td>
<td><p>이 매개 변수가 있으면 cmdlet을 실행하여 얻은 자세한 출력이 지정된 변수에 저장됩니다. 이 변수에 포함된 메서드 쌍(ToHTML 및 ToXML)은 이러한 출력을 HTML 또는 XML 파일에 저장하는 데 사용할 수 있습니다.</p>
<p>출력을 $TestOutput이라는 로거 변수에 저장하려면 다음과 같은 구문을 사용합니다.</p>
<p>-OutLoggerVariable TestOutput</p>
<p>참고: 변수 이름을 지정할 때 $ 문자를 추가해서는 안 됩니다.</p>
<p>로거 변수에 저장된 정보를 HTML 파일에 저장하려면 다음 명령을 사용합니다.</p>
<p>$TestOutput.ToHTML() &gt; C:\Logs\TestOutput.html</p>
<p>로거 변수에 저장된 정보를 XML 파일에 저장하려면 다음 명령을 사용합니다.</p>
<p>$TestOutput.ToXML() &gt; C:\Logs\TestOutput.xml</p></td>
</tr>
<tr class="odd">
<td><p><em>OutVerboseVariable</em></p></td>
<td><p>선택</p></td>
<td><p>System.String</p></td>
<td><p>이 매개 변수가 있으면 cmdlet을 실행하여 얻은 자세한 출력이 지정된 변수에 저장됩니다. 예를 들어 출력을 $TestOutput이라는 변수에 저장하려면 다음과 같은 구문을 사용합니다.</p>
<p>-OutVerboseVariable TestOutput</p>
<p>변수 이름을 지정할 때 $ 문자를 추가해서는 안 됩니다.</p></td>
</tr>
</tbody>
</table>


## 입력 형식

없음. **Test-CsMcxPushNotification** cmdlet은 파이프라인된 입력을 허용하지 않습니다.

## 반환 형식

**Test-CsMcxPushNotification** cmdlet은 Microsoft.Rtc.SyntheticTransactions.TaskOutput 개체의 인스턴스를 반환합니다.

