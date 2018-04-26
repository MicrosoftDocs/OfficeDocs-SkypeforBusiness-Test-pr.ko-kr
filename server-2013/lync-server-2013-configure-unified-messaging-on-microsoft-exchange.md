---
title: Microsoft Exchange에서 Lync Server 2013용 통합 메시징 구성
TOCTitle: Microsoft Exchange에서 Lync Server 2013용 통합 메시징 구성
ms:assetid: 07547968-c59b-4dde-ace4-9fd286933759
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg398129(v=OCS.15)
ms:contentKeyID: 49302704
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Microsoft Exchange에서 Lync Server 2013용 통합 메시징 구성

 

_**마지막으로 수정된 항목:** 2013-02-24_

이 항목에서는 Microsoft Exchange Server에서 Enterprise Voice와 함께 사용하도록 Exchange 통합 메시징(UM)을 구성하는 방법에 대해 설명합니다.


> [!NOTE]
> 이 항목의 cmdlet 예제에서는 Exchange 2007 버전의 Exchange 관리 셸용 구문을 제공합니다. Exchange 2010 또는 Exchange 2013을 실행하는 경우 참조된 해당 설명서를 참조하십시오.



## Exchange Server UM을 실행하는 서버를 구성하려면

1.  각 Enterprise Voice 위치 프로필에 대한 UM SIP(Session Initiation Protocol) URI(Uniform Resource Identifier) 다이얼 플랜을 만듭니다. Exchange 관리 콘솔을 사용하도록 선택하는 경우 **보안(기본 설정)** 보안 설정을 사용하여 새 다이얼 플랜을 만듭니다.
    

    > [!WARNING]
    > 보안 설정 값을 SIP 트래픽에 대해서만 암호화를 요구하는 <STRONG>SIP 보안</STRONG>으로 설정한 경우에는 이전에 권장한 대로 다이얼 플랜의 이 보안 설정은 프런트 엔드 풀이 암호화를 요구하도록 구성된 경우에 적합하지 않다는 점에 주의해야 합니다(풀이 SIP 트래픽과 RTP 트래픽 둘 다에 대해 암호화를 요구함). 다이얼 플랜과 풀 보안 설정이 호환되지 않으면 프런트 엔드 풀에서 Exchange UM으로 전달되는 모든 통화가 실패하고 "보안 설정이 호환되지 않습니다."라는 오류가 발생합니다.

    
    Exchange 관리 셸을 사용하는 경우에는 다음을 입력합니다.
    
        New-UMDialPlan -Name <dial plan name> -UriType "SipName" -VoipSecurity <SIPSecured|Unsecured|Secured> -NumberOfDigitsInExtension <number of digits> -AccessTelephoneNumbers <access number in E.164 format>
    
    참조 항목
    
      - Office Communications Server 2007의 경우 "통합 메시징 SIP URI 다이얼 플랜을 만드는 방법"([http://go.microsoft.com/fwlink/?linkid=268632\&clcid=0x412](http://go.microsoft.com/fwlink/?linkid=268632%26clcid=0x412)) 및 "New-UMDialplan: Exchange 2007 도움말"([http://go.microsoft.com/fwlink/?linkid=268666\&clcid=0x412](http://go.microsoft.com/fwlink/?linkid=268666%26clcid=0x412))을 참조하십시오.
    
      - Exchange 2010의 경우 "UM 다이얼 플랜 만들기"([http://go.microsoft.com/fwlink/?linkid=268674\&clcid=0x412](http://go.microsoft.com/fwlink/?linkid=268674%26clcid=0x412)) 및 "New-UMDialplan: Exchange 2010 도움말"([http://go.microsoft.com/fwlink/?linkid=268680\&clcid=0x412](http://go.microsoft.com/fwlink/?linkid=268680%26clcid=0x412))을 참조하십시오.
    
      - Exchange 2013의 경우 "통합 메시징"([http://go.microsoft.com/fwlink/?linkid=266579\&clcid=0x412](http://go.microsoft.com/fwlink/?linkid=266579%26clcid=0x412))을 참조하십시오.
    

    > [!NOTE]
    > <STRONG>SIPSecured</STRONG> 또는 <STRONG>Secured</STRONG> 보안 수준의 선택은 미디어 암호화에 대한 SRTP(Secure Real-time Transport Protocol)의 활성화 여부에 따라 결정됩니다. Lync Server 2010과 Exchange UM이 통합된 경우 이는 Lync Server 미디어 구성의 암호화 수준과 일치해야 합니다. Lync Server 미디어 구성은 <STRONG>Get-CsMediaConfiguration</STRONG> cmdlet을 실행하여 확인할 수 있습니다. 자세한 내용은 Lync Server 관리 셸 설명서에서 Get-CsMediaConfiguration을 참조하십시오.<BR>적절한 VoIP 보안 설정을 선택하는 방법에 대한 자세한 내용은 <A href="lync-server-2013-deployment-process-for-integrating-on-premises-unified-messaging.md">온-프레미스 통합 메시징과 Lync Server 2013의 통합을 위한 배포 프로세스</A>를 참조하십시오.



2.  다음 cmdlet을 실행하여 각 UM 다이얼 플랜의 FQDN(정규화된 도메인 이름)을 가져옵니다.
    
    ``` 
    (Get-UMDialPlan <dialplanname>).PhoneContext  
    ```
    
    참조 항목
    
      - Exchange 2007의 경우 "Get-UMDialplan: Exchange 2007 도움말"([http://go.microsoft.com/fwlink/?linkid=268678\&clcid=0x412](http://go.microsoft.com/fwlink/?linkid=268678%26clcid=0x412))을 참조하십시오.
    
      - Exchange 2010의 경우 "Get-UMDialplan: Exchange 2010 도움말"([http://go.microsoft.com/fwlink/?linkid=268679\&clcid=0x412](http://go.microsoft.com/fwlink/?linkid=268679%26clcid=0x412))을 참조하십시오.
    
      - Exchange 2013의 경우 "통합 메시징"([http://go.microsoft.com/fwlink/?linkid=266579\&clcid=0x412](http://go.microsoft.com/fwlink/?linkid=266579%26clcid=0x412))을 참조하십시오.

3.  각 UM 다이얼 플랜의 다이얼 플랜 이름을 기록합니다. Exchange Server 버전에 따라 다이얼 플랜 이름이 일치하도록 나중에 각 다이얼 플랜의 FQDN을 각 UM 다이얼 플랜의 해당 Lync Server 다이얼 플랜 이름으로 사용해야 할 수도 있습니다.
    

    > [!NOTE]
    > Lync Server 다이얼 플랜 이름은 UM 다이얼 플랜에서 Exchange 2010 SP1 <EM>이전</EM> 버전의 Exchange를 실행하는 경우에만 UM 다이얼 플랜 이름과 일치해야 합니다.



4.  Exchange UM을 실행하는 서버에 다음과 같이 다이얼 플랜을 추가합니다.
    
      - Exchange 관리 콘솔을 사용하도록 선택한 경우 서버에 대한 속성 시트에서 다이얼 플랜을 추가할 수 있습니다. 특정 지침은 Exchange Server 제품 설명서를 참조하십시오.
        
        Exchange 2007의 경우 "다이얼 플랜에 통합 메시징 서버를 추가하는 방법"([http://go.microsoft.com/fwlink/?linkid=268681\&clcid=0x412](http://go.microsoft.com/fwlink/?linkid=268681%26clcid=0x412))을 참조하십시오.
        
        Exchange 2010의 경우 "UM 서버 속성 보기 또는 구성"([http://go.microsoft.com/fwlink/?linkid=268682\&clcid=0x412](http://go.microsoft.com/fwlink/?linkid=268682%26clcid=0x412))을 참조하십시오.
        
        Exchange 2013의 경우 "통합 메시징"([http://go.microsoft.com/fwlink/?linkid=266579\&clcid=0x412](http://go.microsoft.com/fwlink/?linkid=266579%26clcid=0x412))을 참조하십시오.
    
      - Exchange 관리 셸을 사용하는 경우 각 Exchange UM 서버에 대해 다음을 실행합니다.
        
            $ums=get-umserver; 
            $dp=get-umdialplan -id <name of dial-plan created in step 1>; 
            $ums[0].DialPlans +=$dp.Identity; 
            set-umserver -instance $ums[0]
    

    > [!NOTE]
    > 다음 단계를 수행하기 전에 모든 Enterprise Voice 사용자가 Exchange Server 사서함에 구성되었는지 확인합니다.<BR>Exchange 2007의 경우 Exchange Server 2007 TechNet 라이브러리(<A class=uri href="http://go.microsoft.com/fwlink/?linkid=268685%26clcid=0x412">http://go.microsoft.com/fwlink/?linkid=268685&amp;clcid=0x412</A>)를 참조하십시오.<BR>Exchange 2010의 경우 Exchange Server 2010 TechNet 라이브러리(<A class=uri href="http://go.microsoft.com/fwlink/?linkid=268686%26clcid=0x412">http://go.microsoft.com/fwlink/?linkid=268686&amp;clcid=0x412</A>)를 참조하십시오.<BR>1단계에서 만든 각 다이얼 플랜에 대해 사서함 정책을 지정할 때 기본 정책 또는 사용자가 만든 정책을 선택할 수 있습니다.



5.  \<*Exchange 설치 디렉터리*\>\\Scripts로 이동한 다음 Exchange가 단일 포리스트에 배포된 경우 다음을 입력합니다.
    
        exchucutil.ps1
    
    또는 Exchange가 여러 포리스트에 배포된 경우 다음을 입력합니다.
    
        exchucutil.ps1 -Forest:"<forest FQDN>"
    
    여기서 *forest FQDN*은 Lync Server가 배포된 포리스트를 나타냅니다.
    
    여러 IP 게이트웨이와 연결된 UM 다이얼 플랜이 하나 이상 있는 경우 6단계를 계속 진행하고, 다이얼 플랜이 각각 하나의 IP 게이트웨이에만 연결된 경우 6단계를 건너뜁니다.
    

    > [!IMPORTANT]
    > exchucutil.ps1을 실행한 <EM>후</EM><STRONG>Lync Server 프런트 엔드</STRONG> 서비스(rtcsrv.exe)를 다시 시작해야 합니다. 그러지 않으면 Lync Server가 토폴로지에서 통합 메시징을 검색하지 않습니다.



6.  Exchange 관리 셸 또는 Exchange 관리 콘솔을 사용하여 각 다이얼 플랜과 연결된 IP 게이트웨이 중 하나를 제외하고 모든 IP 게이트웨이에 대해 아웃바운드 통화를 해제합니다.
    

    > [!NOTE]
    > 이 단계는 외부 사용자에 대한 Exchange Server Unified Messaging을 실행하는 서버의 아웃바운드 통화(예: 전화에서 재생 시나리오)가 회사 방화벽을 안정적으로 통과하도록 하는 데 필요합니다.

    

    > [!IMPORTANT]
    > 발신 전화를 허용할 UM IP 게이트웨이를 선택할 때는 가장 많은 트래픽을 처리할 수 있을 것으로 생각되는 게이트웨이를 선택합니다. Lync Server 디렉터 풀에 연결된 IP 게이트웨이를 통해 트래픽이 나가도록 허용해서는 안 됩니다. 또한 다른 중앙 사이트 또는 분기 사이트의 풀도 피해야 합니다. 다음 방법 중 하나를 사용하여 발신 전화가 IP 게이트웨이를 통과하지 못하도록 차단할 수 있습니다.

    
      - Exchange 관리 셸을 사용하는 경우 다음 명령을 실행하여 각 IP 게이트웨이를 해제합니다.
        
            Set-UMIPGateway <gatewayname> -OutcallsAllowed $false
        
        Exchange 2007의 경우 "Set-UMIPGateway: Exchange 2007 도움말"([http://go.microsoft.com/fwlink/?linkid=268687\&clcid=0x412](http://go.microsoft.com/fwlink/?linkid=268687%26clcid=0x412))을 참조하십시오.
        
        Exchange 2010의 경우 "Set-UMIPGateway: Exchange 2010 도움말"([http://go.microsoft.com/fwlink/?linkid=268688\&clcid=0x412](http://go.microsoft.com/fwlink/?linkid=268688%26clcid=0x412))을 참조하십시오.
    
      - Exchange 관리 콘솔을 사용하는 경우 **이 IP 게이트웨이를 통해 발신 전화 허용** 확인란의 선택을 취소합니다.
    

    > [!IMPORTANT]
    > UM SIP URI 다이얼 플랜과 연결된 IP 게이트웨이가 하나뿐인 경우에는 이 게이트웨이를 통한 발신 전화를 거부하지 마십시오.



7.  각 Lync Server 다이얼 플랜에 대한 UM 자동 전화 교환을 만듭니다.
    

    > [!IMPORTANT]
    > 자동 전화 교환 이름에 공백을 포함하지 마십시오.

    
        New-umautoattendant -name <auto attendant name> -umdialplan < name of dial plan created in step 1> -PilotIdentifierList <auto attendant phone number in E.164 format> -SpeechEnabled $true -Status Enabled
    
    참조 항목
    
      - Exchange 2007의 경우 "New-UMAutoAttendant: Exchange 2007 도움말"([http://go.microsoft.com/fwlink/?linkid=268689\&clcid=0x412](http://go.microsoft.com/fwlink/?linkid=268689%26clcid=0x412))을 참조하십시오.
    
      - Exchange 2010의 경우 "New-UMAutoAttendant: Exchange 2010 도움말"([http://go.microsoft.com/fwlink/?linkid=268690\&clcid=0x412](http://go.microsoft.com/fwlink/?linkid=268690%26clcid=0x412))을 참조하십시오.
    
    다음 단계는 Lync Server 사용자가 Enterprise Voice를 사용할 수 있도록 설정하고 사용자의 SIP URI를 알고 있는 경우에 각 사용자에 대해 수행해야 합니다.

8.  각각 Exchange 사서함에 대해 구성해야 하는 Exchange UM 사용자를 UM 다이얼 플랜과 연결하고 각 사용자에 대한 SIP-URI를 만듭니다.
    

    > [!NOTE]
    > 다음 예의 <STRONG>SIPResourceIdentifier</STRONG>는 Lync Server 사용자의 SIP 주소여야 합니다.

    
        enable-ummailbox -id <user name> -ummailboxpolicy <name of the mailbox policy for the dial plan created in step 1> -Extensions <extension> -SIPResourceIdentifier "<user name>@<full domain name>" -PIN <user pin>
    
    참조 항목
    
      - Exchange 2007의 경우 "Enable-UMMailbox: Exchange 2007 도움말"([http://go.microsoft.com/fwlink/?linkid=268691\&clcid=0x412](http://go.microsoft.com/fwlink/?linkid=268691%26clcid=0x412))을 참조하십시오.
    
      - Exchange 2010의 경우 "Enable-UMMailbox: Exchange 2010 도움말"([http://go.microsoft.com/fwlink/?linkid=268692\&clcid=0x412](http://go.microsoft.com/fwlink/?linkid=268692%26clcid=0x412))을 참조하십시오.

