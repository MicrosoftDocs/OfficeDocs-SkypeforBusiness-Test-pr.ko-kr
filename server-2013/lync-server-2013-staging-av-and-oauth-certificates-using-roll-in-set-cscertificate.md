---
title: Set-CsCertificate에 -Roll을 사용하여 Lync Server 2013에서 AV 및 OAuth 인증서 준비
TOCTitle: Set-CsCertificate에 -Roll을 사용하여 Lync Server 2013에서 AV 및 OAuth 인증서 준비
ms:assetid: 22dec3cc-4b6b-4df2-b269-5b35df4731a7
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/JJ660292(v=OCS.15)
ms:contentKeyID: 49885681
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Set-CsCertificate에 -Roll을 사용하여 Lync Server 2013에서 AV 및 OAuth 인증서 준비

 

_**마지막으로 수정된 항목:** 2012-11-13_

A/V(오디오/비디오) 통신은 Microsoft Lync Server 2013의 핵심 구성 요소입니다. 응용 프로그램 공유, 오디오 및 비디오 회의 등의 기능은 A/V 에지 서비스(구체적으로는 A/V 인증 서비스)에 할당된 인증서를 사용합니다.


> [!IMPORTANT]
> <OL>
> <LI>
> <P>이 새로운 기능은 A/V 에지 서비스 및 <EM>OAuthTokenIssuer</EM> 인증서에 대해 작동하도록 디자인되었습니다. A/V 에지 서비스 및 OAuth 인증서 유형과 함께 다른 인증서 유형도 프로비저닝할 수 있지만, A/V 에지 서비스 인증서의 동시 사용 동작으로 인해 제공되는 이점은 없습니다.</P>
> <LI>
> <P>Microsoft Lync Server 2013 인증서를 관리하는 데 사용되는 Lync Server 관리 셸 PowerShell cmdlet은 A/V 에지 서비스 인증서를 <EM>AudioVideoAuthentication</EM> 인증서 유형으로, OAuthServer 인증서를 <EM>OAuthTokenIssuer</EM> 유형으로 참조합니다. 인증서를 고유하게 식별할 수 있도록 이 항목의 나머지 부분에서는 이러한 인증서를 동일한 식별자 유형인 <EM>AudioVideoAuthentication</EM> 및 <EM>OAuthTokenIssuer</EM>로 지칭합니다.</P></LI></OL>



A/V 인증 서비스는 클라이언트 및 기타 A/V 소비자가 사용하는 토큰을 발급합니다. 이러한 토큰은 인증서의 특성에서 생성되며, 인증서가 만료되면 연결이 끊어지고 새 인증서에 의해 생성되는 새 토큰에 다시 연결해야 합니다. Lync Server 2013의 새로운 기능, 즉 이전 인증서가 만료되기 전에 새 인증서를 미리 준비하고 두 인증서가 일정 기간 동안 계속 작동하도록 하는 기능을 사용하면 이 문제를 해결할 수 있습니다. 이 기능은 Set-CsCertificate Lync Server 관리 셸 cmdlet의 업데이트된 기능을 사용합니다. 새로운 매개 변수인 -Roll과 기존 매개 변수인 -EffectiveDate를 함께 사용하면 새 AudioVideoAuthentication 인증서가 인증서 저장소에 저장됩니다. 이전 AudioVideoAuthentication 인증서는 발급된 토큰의 유효성 검사에 사용하기 위해 계속 유지됩니다. 새 AudioVideoAuthentication 인증서가 저장되고 나면 다음과 같은 일련의 이벤트가 발생합니다.


> [!TIP]
> Lync Server 관리 셸 cmdlet을 사용하여 인증서를 관리하면 에지 서버에서 각 용도를 위해 고유한 별도의 인증서를 요청할 수 있습니다. Lync Server 배포 마법사에서 인증서 마법사를 사용하면 인증서를 쉽게 만들 수 있지만, 이러한 인증서는 보통 에지 서버에서 인증서를 사용해야 하는 모든 경우에 하나의 인증서를 사용하도록 하는 <STRONG>기본</STRONG> 유형입니다. 롤링 인증서 기능을 사용하려는 경우에는 AudioVideoAuthentication 인증서를 사용하는 경우와 다른 인증서를 사용하는 경우를 구분하는 것이 좋습니다. Default 유형 인증서를 프로비저닝 및 준비할 수는 있지만, 준비를 통한 이점은 결합된 인증서의 AudioVideoAuthentication 부분에만 적용됩니다. 예를 들어 인증서 만료 시에 인스턴트 메시징 대화를 하고 있는 사용자는 로그아웃했다가 다시 로그인하여 액세스 에지 서비스에 연결된 새 인증서를 사용해야 합니다. 웹 회의 에지 서비스를 사용하여 웹 회의에 참가 중인 사용자의 경우에도 마찬가지입니다. 모든 서버에서 공유되는 특정 인증서 유형으로 OAuthTokenIssuer 인증서가 있습니다. 이 인증서는 한 곳에서 만들어서 관리하면 다른 모든 서버의 중앙 관리 저장소에도 저장됩니다.



Set-CsCertificate cmdlet을 사용할 때와 현재 인증서 만료 전에 해당 cmdlet을 사용하여 인증서를 준비할 때의 옵션 및 요구 사항을 완전하게 파악하려면 추가 세부 정보를 확인해야 합니다. -Roll 매개 변수는 중요한 항목이기는 하지만 기본적으로 한 가지 용도로만 사용됩니다. -Roll을 매개 변수로 정의하는 경우, -EffectiveDate로 정의된 인증서가 유효 상태가 될 때 -Type에 의해 정의되며 영향을 받는 인증서(예: AudioVideoAuthentication 및 OAuthTokenIssuer)에 대한 정보를 제공하도록 Set-CsCertificate에 지시하게 됩니다.

**-Roll:** -Roll 매개 변수는 필수 항목이며 함께 제공해야 하는 종속성을 포함합니다. 영향을 받는 인증서 및 이러한 인증서를 적용하는 방법을 완전하게 정의하는 데 필요한 매개 변수는 다음과 같습니다.

**-EffectiveDate:** -EffectiveDate 매개 변수는 새 인증서를 현재 인증서와 함께 활성화 상태로 설정할 시간을 정의합니다. -EffectiveDate는 현재 인증서의 만료 시간과 가깝게 지정할 수도 있고 좀 더 긴 시간으로 설정할 수도 있습니다. AudioVideoAuthentication 인증서의 경우 권장 최소 -EffectiveDate는 8시간(AudioVideoAuthentication 인증서를 사용하여 발급한 A/V 에지 서비스 토큰의 기본 토큰 수명)입니다.

OAuthTokenIssuer 인증서를 준비할 때는 서로 다른 지연 시간 요구 사항을 충족해야 인증서를 적용할 수 있습니다. OAuthTokenIssuer 인증서에 대해 적용해야 하는 최소 지연 시간은 현재 인증서 만료 시간 전 24시간입니다. 동시 사용의 경우 지연 시간이 길어지는 것은, OAuthTokenIssuer 인증서에 종속되는 다른 서버 역할(예: Exchange Server)의 인증서 작성 인증 및 암호화 주요 자료 보존 시간이 더 길기 때문입니다.

**-Thumbprint:** thumbprint는 인증서에 대해 고유한 해당 인증서의 특성입니다. -Thumbprint 매개 변수는 Set-CsCertificate cmdlet의 동작에 영향을 받는 인증서를 식별하는 데 사용됩니다.

**-Type:** -Type 매개 변수는 단일 인증서 사용 유형 또는 쉼표로 구분된 인증서 사용 유형 목록을 허용할 수 있습니다 .인증서 유형은 해당 cmdlet 및 인증서 사용 대상 서버로 식별되는 유형입니다. 예를 들어 AudioVideoAuthentication 유형은 A/V 에지 서비스 및 A/V 인증 서비스에 사용됩니다. 서로 다른 유형의 인증서를 동시에 준비 및 프로비저닝하려는 경우에는 인증서에 필요한 가장 긴 최소 유효 지연 시간을 고려해야 합니다. AudioVideoAuthentication 및 OAuthTokenIssuer 유형 인증서를 준비해야 하는 경우를 예로 들어 보겠습니다. 이 경우 최소 -EffectiveDate는 두 인증서 중 더 긴 쪽(이 경우 최소 지연 시간이 24시간인 OAuthTokenIssuer)이어야 합니다. 지연 시간을 24시간으로 지정하여 AudioVideoAuthentication 인증서를 준비하지 않으려는 경우 요구 사항에 보다 적합한 EffectiveDate를 적용하여 해당 인증서를 별도로 준비하십시오.

## \-Roll 및 -EffectiveDate 매개 변수를 사용하여 A/V 에지 서비스 인증서를 업데이트하거나 갱신하려면

1.  Administrators 그룹의 구성원으로 로컬 컴퓨터에 로그온합니다.

2.  A/V 에지 서비스의 기존 인증서에 대해 내보내기 가능한 개인 키를 사용하여 갱신 또는 새 AudioVideoAuthentication 인증서를 요청합니다.

3.  풀을 배포한 경우 풀의 에지 서버 및 기타 모든 에지 서버로 새 AudioVideoAuthentication 인증서를 가져옵니다.

4.  Set-CsCertificate cmdlet에서 -Roll 매개 변수와 -EffectiveDate 매개 변수를 사용하여 가져온 인증서를 구성합니다. 유효 날짜는 현재 인증서 만료 시간(14:00:00 또는 오후 2:00:00)에 토큰 수명(기본적으로 8시간)을 뺀 시간으로 정의해야 합니다. 그러면 인증서를 활성 상태로 설정해야 하는 시간(-EffectiveDate \<문자열\>: “7/22/2012 6:00:00 AM”)을 확인할 수 있습니다.
    

    > [!IMPORTANT]
    > 에지 풀의 경우에는 모든 클라이언트 및 소비자 토큰이 새 인증서를 사용하여 갱신되기 전에 이전 인증서가 만료됨으로 인해 발생할 수 있는 A/V 통신 중단을 방지하기 위해, 첫 번째 인증서의 -EffectiveDate 매개 변수로 정의되는 날짜와 시간으로 모든 AudioVideoAuthentication 인증서를 배포 및 프로비저닝해야 합니다.

    
    \-Roll 및 -EffectiveTime 매개 변수를 포함한 Set-CsCertificate 명령은 다음과 같습니다.
    
        Set-CsCertificate -Type AudioVideoAuthentication -Thumbprint <thumb print of new certificate> -Roll -EffectiveDate <date and time for certificate to become active>
    
    Set-CsCertificate 명령의 예는 다음과 같습니다.
    
        Set-CsCertificate -Type AudioVideoAuthentication -Thumbprint "B142918E463981A76503828BB1278391B716280987B" -Roll -EffectiveDate "7/22/2012 6:00:00 AM"
    

    > [!IMPORTANT]
    > EffectiveDate는 서버의 국가 및 언어 설정과 일치하도록 서식을 지정해야 합니다. 위의 예에서는 영어(미국) 국가 및 언어 설정을 사용합니다.



Set-CsCertificate, -Roll 및 -EffectiveDate가 이전 인증서를 계속 사용하여 소비자들이 사용 중인 AudioVideoAuthentication의 유효성을 검사하는 동시에 새 AudioVideoAuthentication 토큰 발급용으로 새 인증서를 준비하는 프로세스를 보다 자세하게 파악하려는 경우 시간 표시줄 그림을 활용하면 유용합니다.

다음 예에서는 관리자가 A/V 에지 서비스 인증서의 만료 시간을 2012/07/22 오후 2:00:00으로 결정합니다. 관리자는 새 인증서를 요청 및 수신하여 풀의 각 에지 서버로 가져옵니다. 2012/07/22 오전 2시가 되면 관리자는 -Roll, -Thumbprint(새 인증서의 thumbprint 문자열과 같음) 및 -EffectiveTime(2012/07/22 오전 6:00:00으로 설정)을 포함하여 Get-CsCertificate 실행을 시작합니다. 각 에지 서버에서 이 명령을 실행합니다.

![Roll 및 EffectiveDate 매개 변수 사용.](images/JJ660292.21d51a76-0d03-4ed7-a37e-a7c14940265f(OCS.15).jpg "Roll 및 EffectiveDate 매개 변수 사용.")

유효 시간(2012/7/22 오전 6:00:00)이 되면 새 인증서를 통해 새 토큰이 모두 발급됩니다. 토큰의 유효성을 검사할 때는 먼저 새 인증서에 대해 토큰 유효성을 검사합니다. 유효성 검사가 실패하면 이전 인증서에 대한 유효성 검사를 시도합니다. 이처럼 새 인증서에 대한 유효성 검사를 시도하고 실패 시 이전 인증서로 대체하는 과정은 이전 인증서의 만료 시간까지 계속됩니다. 이전 인증서가 만료되면(2012/7/22 오후 2:00:00) 새 인증서에 대해서만 토큰의 유효성을 검사합니다. 이 시점에는 -Previous 매개 변수를 포함한 Remove-CsCertificate cmdlet을 사용하여 인증서를 안전하게 제거할 수 있습니다.

    Remove-CsCertificate -Type AudioVideoAuthentication -Previous

## \-Roll 및 -EffectiveDate 매개 변수를 사용하여 OAuthTokenIssuer 인증서를 업데이트하거나 갱신하려면

1.  Administrators 그룹의 구성원으로 로컬 컴퓨터에 로그온합니다.

2.  A/V 에지 서비스의 기존 인증서에 대해 내보내기 가능한 개인 키를 사용하여 갱신 또는 새 OAuthTokenIssuer 인증서를 요청합니다.

3.  풀을 배포한 경우 풀의 프런트 엔드 서버로 새 OAuthTokenIssuer 인증서를 가져옵니다. OAuthTokenIssuer 인증서는 전역적으로 복제되며 배포의 모든 서버에서 업데이트 및 갱신하면 됩니다. 여기서는 예로 프런트 엔드 서버가 사용됩니다.

4.  Set-CsCertificate cmdlet에서 -Roll 매개 변수와 -EffectiveDate 매개 변수를 사용하여 가져온 인증서를 구성합니다. 유효 날짜는 현재 인증서 만료 시간(14:00:00 또는 오후 2:00:00)에 최소 24시간을 뺀 시간으로 정의해야 합니다.
    
    \-Roll 및 -EffectiveTime 매개 변수를 포함한 Set-CsCertificate 명령은 다음과 같습니다.
    
        Set-CsCertificate -Type OAuthTokenIssuer -Thumbprint <thumb print of new certificate> -Roll -EffectiveDate <date and time for certificate to become active>
    
    Set-CsCertificate 명령의 예는 다음과 같습니다.
    
        Set-CsCertificate -Type OAuthTokenIssuer -Thumbprint "B142918E463981A76503828BB1278391B716280987B" -Roll -EffectiveDate "7/21/2012 1:00:00 PM"
    

    > [!IMPORTANT]
    > EffectiveDate는 서버의 국가 및 언어 설정과 일치하도록 서식을 지정해야 합니다. 위의 예에서는 영어(미국) 국가 및 언어 설정을 사용합니다.



유효 시간(2012/7/21 오전 1:00:00)이 되면 새 인증서를 통해 새 토큰이 모두 발급됩니다. 토큰의 유효성을 검사할 때는 먼저 새 인증서에 대해 토큰 유효성을 검사합니다. 유효성 검사가 실패하면 이전 인증서에 대한 유효성 검사를 시도합니다. 이처럼 새 인증서에 대한 유효성 검사를 시도하고 실패 시 이전 인증서로 대체하는 과정은 이전 인증서의 만료 시간까지 계속됩니다. 이전 인증서가 만료되면(2012/7/22 오후 2:00:00) 새 인증서에 대해서만 토큰의 유효성을 검사합니다. 이 시점에는 -Previous 매개 변수를 포함한 Remove-CsCertificate cmdlet을 사용하여 인증서를 안전하게 제거할 수 있습니다.

    Remove-CsCertificate -Type OAuthTokenIssuer -Previous

## 참고 항목

#### 개념

[Lync Server 2013의 에지 서버 인증서 계획](lync-server-2013-plan-for-edge-server-certificates.md)  
[Lync Server 2013에서 서버 간 인증(Oauth) 및 파트너 응용 프로그램 관리](lync-server-2013-managing-server-to-server-authentication-oauth-and-partner-applications.md)  

#### 기타 리소스

[Lync Server 2013의 에지 인증서 설정](lync-server-2013-set-up-edge-certificates.md)  
[Set-CsCertificate](https://docs.microsoft.com/en-us/powershell/module/skype/Set-CsCertificate)  
[Remove-CsCertificate](https://docs.microsoft.com/en-us/powershell/module/skype/Remove-CsCertificate)

