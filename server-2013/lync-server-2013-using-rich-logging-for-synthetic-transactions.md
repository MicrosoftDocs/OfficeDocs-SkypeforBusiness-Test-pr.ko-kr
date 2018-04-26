---
title: 가상 트랜잭션에 고급 로깅 사용
TOCTitle: 가상 트랜잭션에 고급 로깅 사용
ms:assetid: 32714a71-9f42-4d5b-a508-e176d8f08bbf
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/JJ204798(v=OCS.15)
ms:contentKeyID: 49303243
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# 가상 트랜잭션에 고급 로깅 사용

 

_**마지막으로 수정된 항목:** 2012-10-22_

관리자는 Microsoft Lync Server 2010에서 도입된 가상 트랜잭션을 통해 사용자가 시스템 로그온, 인스턴트 메시지 교환, 공중 전화망(PSTN)의 전화로 전화 걸기 등의 일반적인 작업을 성공적으로 완료할 수 있는지 확인할 수 있습니다. 이러한 테스트는 Lync ServerWindows PowerShell cmdlet 집합으로 패키지되며, 관리자가 수동으로 수행하거나 System Center Operations Manager 등의 응용 프로그램에 의해 자동으로 실행될 수 있습니다.

Lync Server 2010에서 가상 트랜잭션은 관리자가 시스템의 문제를 쉽게 파악할 수 있도록 하는 데 매우 유용합니다. 예를 들어 **Test-CsRegistration** cmdlet은 일부 사용자의 Lync Server 등록에 문제가 있음을 관리자에게 알릴 수 있습니다. 그러나 이러한 사용자의 Lync Server 등록에 문제가 발생한 이유를 확인하려는 경우에는 가상 트랜잭션이 그다지 유용하지 않습니다. 가상 트랜잭션은 관리자가 Lync Server 관련 문제를 해결하는 데 도움이 되는 자세한 로깅 정보를 제공하지 않기 때문입니다. 가상 트랜잭션의 자세한 정보 출력에서 제공하는 단계별 정보를 통해 관리자가 문제 발생 위치를 어느 정도 근접하게 추측할 수는 있습니다.

Microsoft Lync Server 2013에서는 가상 트랜잭션이 새롭게 설계되어 향상된 로깅이 제공됩니다. "향상된 로깅"이란 가상 트랜잭션이 수행하는 각 활동에 대해 다음과 같은 정보가 기록된다는 의미입니다.

  - 활동이 시작된 시간

  - 활동이 완료된 시간

  - 수행된 작업(예: 회의 작성/참가/나가기, Lync Server 로그인, 인스턴트 메시지 보내기 등)

  - 활동 실행 시 생성된 정보, 자세한 정보, 경고 또는 오류 메시지

  - SIP 등록 메시지

  - 활동 실행 시 생성된 예외 레코드 또는 진단 코드

  - 활동 실행의 순수 결과

이 정보는 가상 트랜잭션을 실행할 때마다 자동으로 생성됩니다. 그러나 정보가 자동으로 표시되거나 로그 파일에 저장되는 것은 아닙니다. 대신 가상 트랜잭션을 수동으로 실행하는 관리자가 OutLoggerVariable 매개 변수를 사용하여 정보를 저장할 Windows PowerShell 변수를 지정할 수 있습니다. 그러면 관리자는 두 가지 방법을 통해 향상된 로그를 XML 또는 HTML 형식으로 저장 및/또는 표시할 수 있습니다.

예를 들어 Lync Server 2010 관리자는 다음과 같은 명령을 사용하여 **Test-CsRegistration** cmdlet을 실행할 수 있습니다.

    Test-CsRegistration -TargetFqdn atl-cs-001.litwareinc.com

관리자는 OutLoggerVariable 매개 변수 뒤에 선택한 변수 이름을 붙여 포함할 수 있습니다.

    Test-CsRegistration -TargetFqdn atl-cs-001.litwareinc.com -OutLoggerVariable RegistrationTest


> [!NOTE]
> 변수 이름 앞에 $ 문자를 붙이지 마십시오. 즉, $RegistrationTest가 아닌 RegistrationTest를 변수 이름으로 사용해야 합니다.



위의 명령은 다음과 같은 콘텐츠를 출력합니다.

    Target Fqdn   : atl-cs-001.litwareinc.com
    Result        : Failure
    Latency       : 00:00:00
    Error Message : This machine does not have any assigned certificates.
    Diagnosis     :

그러나 이 오류에 대해 위에 나와 있는 오류 메시지뿐만 아니라 훨씬 자세한 정보를 확인할 수 있습니다. HTML 형식의 해당 정보에 액세스하려면 다음과 같은 명령을 사용하여 RegistrationTest 변수에 저장된 정보를 HTML 파일에 저장합니다.

    $RegistrationTest.ToHTML() | Out-File C:\Logs\Registration.html

또는 ToXML() 메서드를 사용하여 데이터를 XML 파일에 저장할 수도 있습니다.

    $RegistrationTest.ToXML() | Out-File C:\Logs\Registration.xml

그러면 Internet Explorer, Visual Studio 또는 HTML/XML 파일을 열 수 있는 기타 응용 프로그램을 사용하여 이러한 파일을 볼 수 있습니다.

System Center Operations Manager 내에서 가상 트랜잭션을 실행하면 오류에 대해 이러한 로그 파일이 자동으로 생성됩니다. 그러나 Windows PowerShell에서 가상 트랜잭션을 로드 및 실행하기 전에 실행이 실패하면 이러한 로그가 생성되지 않습니다.


> [!IMPORTANT]
> 기본적으로 Lync Server 2013에서는 공유되지 않는 폴더에 로그 파일을 저장합니다. 이러한 로그에 쉽게 액세스하려면 이 폴더를 \\atl-watcher-001.litwareinc.com\WatcherNode와 같이 공유해야 합니다.


