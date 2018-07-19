---
title: 'Lync Server 2013: 에지 서버 인증서 계획'
TOCTitle: 에지 서버 인증서 계획
ms:assetid: f1dfe220-2398-4ac8-ba4c-206c8c0cbc50
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg413010(v=OCS.15)
ms:contentKeyID: 49305502
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Lync Server 2013의 에지 서버 인증서 계획

 

_**마지막으로 수정된 항목:** 2012-11-05_

Lync Server 2013에서는 에지에 대한 인증서를 만드는 과정이 단순화되었습니다.

**에지 서버에 대한 인증서 순서도**

![인증서 순서도](images/Gg413010.a5fc20db-7ced-4364-b577-6a709a8367cd(OCS.15).jpg "인증서 순서도")

하나의 공용 인증서를 만들고 인증서에 대해 내보낼 수 있는 개인 키를 정의했는지 확인한 후 인증서 마법사를 사용하여 다음 에지 서버 외부 인터페이스에 할당합니다.


> [!IMPORTANT]
> 와일드카드 인증서는 역방향 프록시를 통해 단순 URL을 요약하는 데 사용되는 경우를 제외하면 Lync Server에서 지원되지 않습니다. 따라서 배포에서 제공되는 각 SIP 도메인 이름, 웹 회의 에지 서비스, A/V 에지 서비스 및 XMPP 도메인에 대해 고유한 SAN(주체 대체 이름)을 정의해야 합니다.




> [!NOTE]
> Lync Server 2013에 도입된 현재 인증서의 만료 시간 전 오디오/비디오 인증 인증서 준비에는 추가 계획이 필요합니다. 외부 에지 인터페이스용으로 다용도의 단일 인증서 대신에 두 개 인증서가 필요합니다. 하나는 액세스 에지 서비스 및 웹 회의 에지 서비스에 할당되고, 다른 하나는 A/V 에지 서비스용 인증서입니다. 자세한 내용은 <A href="lync-server-2013-staging-av-and-oauth-certificates-using-roll-in-https://docs.microsoft.com/en-us/powershell/module/skype/Set-CsCertificate">Set-CsCertificate에 -Roll을 사용하여 Lync Server 2013에서 AV 및 OAuth 인증서 준비</A>를 참조하십시오.




> [!IMPORTANT]
> 에지 서버 풀 이벤트에서 각 에지 서버로 개인 키와 함께 인증서를 내보내고 이 인증서를 에지 서버 서비스에 할당할 수 있습니다. 내부 에지 서버 인증서에 대해서도 개인 키와 함께 인증서를 내보내고 각 내부 에지 인터페이스에 할당하는 동일한 단계를 수행합니다.



  - 인증서에 내보낼 수 있는 개인 키가 할당되었는지 확인합니다.

  - 액세스 에지 서비스(인증서 마법사에서는 **SIP 액세스 에지 외부** 라고 함)

  - 웹 회의 에지 서비스(인증서 마법사에서는 **웹 회의 에지 외부** 라고 함)

  - A/V 인증 서비스(인증서 마법사에서 **A/V 에지 외부** 라고 함)

내보낼 수 있는 개인 키가 할당된 하나의 내부 인증서를 만든 후 복사하여 각각의 에지 서버 내부 인터페이스에 할당합니다.

  - 에지 서버(인증서 마법사에서 **에지 내부** 라고 함)


> [!IMPORTANT]
> 각 에지 서버 서비스에 대해 별도의 고유한 인증서를 사용할 수 있습니다. A/V 에지 서비스 인증서에 대한 새로운 롤링 인증서 기능을 사용하려는 경우에는 개별 인증서를 선택하는 것이 좋습니다. 이 기능의 경우 A/V 에지 서비스 인증서를 액세스 에지 서비스 및 웹 회의 에지 서비스와 분리하는 것이 좋습니다. 각 서비스마다 인증서를 요청, 획득 및 할당하도록 선택하는 경우 개인 키를 A/V 에지 서비스(앞에서 설명했듯이 이 서비스는 사실상 A/V 인증 서비스에 있음)에 대해 내보낼 수 있도록 요청하고 동일한 인증서를 각 에지 서버의 A/V 애지 외부 인터페이스에 할당해야 합니다.



## 참고 항목

#### 작업

[Set-CsCertificate에 -Roll을 사용하여 Lync Server 2013에서 AV 및 OAuth 인증서 준비](lync-server-2013-staging-av-and-oauth-certificates-using-roll-in-https://docs.microsoft.com/en-us/powershell/module/skype/Set-CsCertificate)  

#### 개념

[에지 서버 계획에 영향을 주는 Lync Server 2013의 변경 사항](lync-server-2013-changes-in-lync-server-that-affect-edge-server-planning.md)

