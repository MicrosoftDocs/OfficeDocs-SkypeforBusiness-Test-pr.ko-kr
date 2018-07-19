---
title: 중앙화된 로깅 서비스에 시작을 사용하여 로그 캡처
TOCTitle: 중앙화된 로깅 서비스에 시작을 사용하여 로그 캡처
ms:assetid: 0512b9ce-7f5b-48eb-a79e-f3498bacf2de
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/JJ687958(v=OCS.15)
ms:contentKeyID: 49885634
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# 중앙화된 로깅 서비스에 시작을 사용하여 로그 캡처

 

_**마지막으로 수정된 항목:** 2013-02-21_

중앙 로깅 서비스를 사용하여 추적 로그를 캡처하려면 하나 이상의 컴퓨터 및 풀에 대한 로깅을 시작하는 명령을 실행합니다. 또한 컴퓨터 또는 풀, 실행할 시나리오(예: AlwaysOn, 미리 정의된 다른 시나리오 또는 직접 만든 시나리오), 추적할 Lync Server 구성 요소(예: S4, SipStack)를 정의하는 매개 변수도 실행합니다.

적절한 정보를 캡처하려면 올바른 시나리오를 사용하여 문제와 관련된 정보를 수집해야 합니다. 중앙 로깅 서비스에서 시나리오는 서버 구성 요소, 로깅 수준 및 플래그 모음을 기준으로 로깅을 설정하는 개념인데, 이는 서버별로 이러한 요소를 정의하는 것보다 훨씬 효율적이고 유용합니다. 시나리오를 정의 및 지정하면 인프라 범위 내의 모든 서버 및 풀에서 시나리오가 일관성 있게 실행됩니다.

기본 시나리오는 **AlwaysOn**입니다. AlwaysOn은 이름에서 짐작할 수 있듯이 시나리오를 지속적으로 실행하기 위한 용도로 사용됩니다. AlwaysOn 시나리오는 가장 일반적인 대부분의 서버 구성 요소에 대해 정보 수준의 정보를 수집합니다(정보 로깅 수준에는 정보 메시지 외에 심각, 오류 및 경고도 포함됨). AlwaysOn은 문제 발생 전/중/후에 정보를 수집합니다. 이는 OCSLogger와 같은 이전 로깅 도구의 일반적인 동작과는 크게 다릅니다. OCSLogger는 문제가 이미 발생한 후에 실행하는 방식이었으며, 수집되는 데이터가 사전 예방 방식이 아닌 사후 대응 방식이므로 문제를 해결하기가 보다 어려웠습니다. 문제 구성 요소를 파악하고 해당 문제를 해결하기 위한 일련의 동작을 나타내기 위해 확인해야 하는 정보가 AlwaysOn에 포함되어 있지 않은 경우(AlwaysOn에는 매우 다양하고 폭넓은 공급자가 포함되므로 그럴 가능성은 거의 없음), AlwaysOn은 새 시나리오 만들기, 다른 정보 수집, 다른 검색을 실행하여 보다 세부적인 정보 수집 등 수행해야 하는 다른 작업을 결정하기 위한 적절한 정보 수준을 지시합니다.

중앙 로깅 서비스에서는 두 가지 방법으로 명령을 실행할 수 있습니다. 대부분의 항목에서는 Lync Server 관리 셸을 통해 Windows PowerShell을 사용하는 방법에 대해 주로 설명합니다. 여러 가지 복잡한 구성과 명령을 사용하는 기능이 필요한 경우 Windows PowerShell에서 중앙 로깅 서비스를 사용하는 것이 좋습니다. Lync Server 관리 셸을 통해 Windows PowerShell을 사용하는 방식은 Lync Server의 거의 모든 기능에 대해 사용되므로 Windows PowerShell 명령에 대해서만 설명합니다.


> [!NOTE]
> 명령줄에서 제공되는 제한적인 명령 집합을 사용하려는 경우에는 <CODE>ClsController.exe</CODE>를 입력하여 CLSController.exe의 도움말을 확인할 수 있습니다. <STRONG>ClsController.exe</STRONG>는 기본적으로 C:\Program Files\Microsoft Lync Server 2013\ClsAgent디렉터리에 설치됩니다.



## 기본 명령을 사용하여 Windows PowerShell에서 Start-CsClsLogging을 실행하려면

1.  Lync Server 관리 셸 시작: **시작**, **모든 프로그램**, **Microsoft Lync Server 2013**을 차례로 클릭한 다음 **Lync Server 관리 셸**을 클릭합니다.

2.  다음을 입력하여 중앙 로깅 서비스에서 로깅 시나리오를 시작합니다.
    
        Start-CsClsLogging -Scenario <name of scenario>
    
    예를 들어 **AlwaysOn** 시나리오를 시작하려면 다음을 입력합니다.
    
        Start-CsClsLogging -Scenario AlwaysOn
    

    > [!NOTE]
    > AlwaysOn 시나리오에는 기본 기간이 없습니다. 즉, 이 시나리오는 <STRONG>Stop-CsClsLogging</STRONG> cmdlet을 사용하여 명시적으로 중지할 때까지 실행됩니다. 자세한 내용은 <A href="https://docs.microsoft.com/en-us/powershell/module/skype/Stop-CsClsLogging">Stop-CsClsLogging</A>을 참조하십시오. 다른 모든 시나리오의 경우 기본 기간은 4시간입니다.



3.  Enter 키를 눌러 명령을 실행합니다.
    

    > [!NOTE]
    > 명령이 실행되어 배포의 컴퓨터로부터 상태를 받을 때가지 시간이 약간 걸릴 수 있습니다(30~60초).

    
    ![Start-CsClsLogging 실행.](images/JJ687958.c5be7413-8cef-4de7-9712-944d20cc2fa4(OCS.15).jpg "Start-CsClsLogging 실행.")

4.  다른 시나리오를 시작하려면 실행하려는 추가 시나리오 이름(예: **Authentication** 시나리오)을 포함하여 **Start-CsClsLogging** cmdlet을 사용합니다.
    
        Start-CsClsLogging -Scenario Authentication
    

    > [!IMPORTANT]
    > 지정된 컴퓨터에서 항상 총 2개의 시나리오를 실행할 수 있습니다. 명령의 범위가 전역인 경우에는 배포의 모든 컴퓨터에서 시나리오를 실행합니다. 세 번째 시나리오를 시작하려면 새 시나리오를 실행할 컴퓨터, 풀, 사이트 또는 전역 범위에서 로깅을 중지해야 합니다. 전역 범위를 시작한 경우에는 하나 이상의 컴퓨터 및 풀에서 시나리오 하나 또는 둘 다에 대해 로깅을 중지하면 됩니다. 실행되는 시나리오를 관리하는 방법에 대한 자세한 내용은 <A href="lync-server-2013-using-stop-for-the-centralized-logging-service.md">중앙화된 로깅 서비스에 중지 사용</A> 및 <A href="https://docs.microsoft.com/en-us/powershell/module/skype/Stop-CsClsLogging">Stop-CsClsLogging</A>을 참조하십시오.



## 고급 명령을 사용하여 Windows PowerShell에서 Start-CsClsLogging을 실행하려면

1.  Lync Server 관리 셸 시작: **시작**, **모든 프로그램**, **Microsoft Lync Server 2013**을 차례로 클릭한 다음 **Lync Server 관리 셸**을 클릭합니다.

2.  추가 매개 변수를 사용하여 로깅 명령을 관리할 수 있습니다. –Duration을 사용하여 시나리오를 실행할 기간을 조정할 수 있습니다. 또한 –Computers(쉼표로 구분된 컴퓨터 FQDN(정규화된 도메인 이름) 목록) 또는 –Pools(로깅을 실행할 풀의 쉼표로 구분된 FQDN 목록)를 정의할 수도 있습니다.
    
    "pool01.contoso.net" 풀에서 *UserReplicator* 시나리오에 대해 로깅 세션을 시작합니다. 또한 로깅 세션 기간을 8시간으로 정의합니다. 이렇게 하려면 다음을 입력합니다.
    
        Start-CsClsLogging -Scenario UserReplicator -Duration 8:00 -Pools "pool01.contoso.net"
    
    이 시나리오가 정상적으로 실행되면 다음과 같은 결과가 반환됩니다.
    
    ![Start-CsClsLogging 실행.](images/JJ687958.399f0c2e-c08c-40ab-b6c6-381dddc12fe9(OCS.15).jpg "Start-CsClsLogging 실행.")
    
    이 예제에서는 AlwaysOn 시나리오와 UserReplicator 시나리오가 실행됩니다.

## 참고 항목

#### 개념

[중앙화된 로깅 서비스 개요](lync-server-2013-overview-of-the-centralized-logging-service.md)

