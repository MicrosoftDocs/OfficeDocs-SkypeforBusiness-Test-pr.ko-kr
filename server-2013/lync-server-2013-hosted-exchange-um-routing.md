---
title: 'Lync Server 2013: 호스팅된 Exchange UM 라우팅'
TOCTitle: 호스팅된 Exchange UM 라우팅
ms:assetid: 6c90dc8b-6aef-4ce8-b483-37c7b5a553c2
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg398512(v=OCS.15)
ms:contentKeyID: 49303949
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Lync Server 2013의 호스팅된 Exchange UM 라우팅

 

_**마지막으로 수정된 항목:** 2012-10-01_

Exchange UM 라우팅 응용 프로그램은 프런트 엔드 서버에서 실행되어 통화를 온-프레미스 Microsoft Exchange Server UM(통합 메시징) 배포 또는 호스팅된 Exchange UM 서비스로 라우팅합니다.

## ExUM 라우팅 응용 프로그램

다음 다이어그램에 나와 있는 것처럼 Lync Server 2013Exchange UM 라우팅 응용 프로그램에서는 사용자 계정 설정 및 호스팅된 음성 메일 정책 매개 변수의 정보를 사용하여 호스팅된 음성 메시징에 대한 통화를 라우팅하는 방법을 결정합니다.

**혼합 배포 Exchange UM 라우팅 예제**

![온-프레미스 Lync Server Exchange UM 배포](images/Gg398512.75258286-1f23-487b-bf46-d8538e7d540e(OCS.15).jpg "온-프레미스 Lync Server Exchange UM 배포")

Exchange UM 라우팅은 온-프레미스 Exchange UM에 대해 사용하도록 설정된 사용자, 호스팅된 Exchange UM에 대해 사용하도록 설정된 사용자 또는 이러한 두 사용자의 결합으로 통화를 라우팅하도록 구성될 수 있습니다.

예를 들어 Roy의 사서함 및 Exchange UM 서비스가 온-프레미스 Exchange 배포에 속한다고 가정해 보겠습니다.

  - Roy의 사용자 계정 프록시 주소 정보는 ExUM 라우팅 응용 프로그램에서 Roy의 통화를 온-프레미스 Exchange UM 서버로 라우팅하는 데 사용하는 정보를 제공합니다.

Alice의 사서함 및 Exchange UM 서비스는 호스팅된 Exchange 서비스 공급자의 데이터 센터에 위치해 있습니다. Alice의 Exchange UM 통화에 대한 라우팅은 다음과 같이 구성됩니다.

  - Alice의 사용자 계정 msExchUCVoiceMailSettings 특성에 설정된 값은 호스팅된 음성 메일 정책의 라우팅 세부 정보를 확인하도록 ExUM 라우팅 응용 프로그램에 알립니다.
    

    > [!NOTE]
    > msExchUCVoiceMailSettings 특성의 값은 Exchange 서비스 공급자 또는 Lync Server 2013 관리자가 설정할 수 있습니다. 이전 다이어그램에 표시된 예에서는 Lync Server 2013 관리자가 Alice에 대해 호스팅된 음성 메일을 사용하도록 설정하기 위해 값(CsHostedVoiceMail=1)을 설정했습니다. 이 특성에 대한 자세한 내용은 <A href="lync-server-2013-hosted-exchange-user-management.md">Lync Server 2013의 호스팅된 Exchange 사용자 관리</A>를 참조하십시오.



  - Alice의 사용자 계정에 지정된 호스팅된 음성 메일 정책은 다음과 같은 라우팅 세부 정보를 제공합니다.
    
      - 대상은 호스팅된 Exchange UM 서비스 공급자(이 예제에서 ls.ExUm. *\<hostedExchangeServer\>* .com)입니다.
    
      - 조직은 ls.ExUm. *\<hostedExchangeServer\>* .com(이 예제에서 corp.contoso.com 및 corp.litwareinc.com)에 위치해 있는 Exchange Server 테넌트에 대한 SIP 메시지의 라우팅 FQDN인 테넌트 ID로 식별됩니다.
        

        > [!NOTE]
        > Exchange Online의 FQDN은 exap.um.outlook.com입니다.

        
        자세한 내용은 [Lync Server 2013의 호스팅된 음성 메일 정책](lync-server-2013-hosted-voice-mail-policies.md)을 참고하세요.


> [!NOTE]
> 사용자 계정에 msExchUCVoiceMailSettings 특성과 UM 프록시 주소 설정이 둘 다 있는 경우 msExchUCVoiceMailSettings 특성이 우선합니다.


