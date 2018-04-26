---
title: 'Lync Server 2013: 호스팅된 Exchange UM에 대한 대화 상대 개체 만들기'
TOCTitle: 호스팅된 Exchange UM에 대한 대화 상대 개체 만들기
ms:assetid: a39be52f-488a-4523-ad5f-ce1f0d681959
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg412765(v=OCS.15)
ms:contentKeyID: 49304595
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Lync Server 2013에서 호스팅된 Exchange UM에 대한 대화 상대 개체 만들기

 

_**마지막으로 수정된 항목:** 2012-09-24_

다음 절차는 호스팅된 Exchange UM(통합 메시징)에 대한 AA(자동 전화 교환), SA(구독자 액세스) 연락처 개체를 만드는 방법에 대해 설명합니다.

자세한 내용은 계획 설명서에서 [Lync Server 2013의 호스팅된 Exchange 연락처 개체 관리](lync-server-2013-hosted-exchange-contact-object-management.md)을 참고하세요.

연락처 개체를 구성하는 방법에 대한 자세한 내용은 다음 cmdlet에 대한 Lync Server 관리 셸 설명서를 참조하십시오.

  - [New-CsExUmContact](new-csexumcontact.md)

  - [Set-CsExUmContact](set-csexumcontact.md)


> [!IMPORTANT]
> 호스팅된 Exchange UM에 대해 Lync Server 2013 연락처 개체를 사용하도록 설정하려면 이러한 개체에 적용할 호스팅된 음성 메일 정책을 배포해야 합니다. 자세한 내용은 <A href="lync-server-2013-hosted-voice-mail-policies.md">Lync Server 2013의 호스팅된 음성 메일 정책</A>을 참조하십시오.



## 호스팅된 Exchange UM에 대한 AA 또는 SA 연락처 개체를 만들려면

1.  Lync Server 관리 셸 시작: **시작**, **모든 프로그램**, **Microsoft Lync Server 2013**을 차례로 클릭한 다음 **Lync Server 관리 셸**을 클릭합니다.

2.  New-CsExUmContact cmdlet을 실행하여 배포에 필요한 연락처 개체를 만듭니다. 예를 들어 다음을 실행하여 AA 및 SA 연락처 개체를 만듭니다.
    
        New-CsExUmContact -SipAddress "sip:exumaa1@fabrikam.com" -RegistrarPool "RedmondPool.litwareinc.com" -OU "HostedExUM Integration" -DisplayNumber "+14255550101" -AutoAttendant $True
    
        New-CsExUmContact -SipAddress "sip:exumsa1@fabrikam.com" -RegistrarPool "RedmondPool.litwareinc.com" -OU "HostedExUM Integration" -DisplayNumber "+14255550101"
    
    이러한 예는 다음 매개 변수를 설정합니다.
    
      - **SipAddress**는 연락처 개체의 SIP 주소를 지정하며, Active Directory 도메인 서비스에서 사용자나 연락처 개체를 구성하는 데 사용되지 않은 주소여야 합니다. 이 값은 이전 예에 표시된 바와 같이 “sip:\< *SIP 주소* \>“ 형식이어야 합니다.
    
      - **RegistrarPool**은 등록자 서비스가 실행되고 있는 풀의 FQDN(정규화된 도메인 이름)을 지정합니다.
        

        > [!NOTE]
        > Exchange UM 연락처 개체는 Lync Server 2013 이전의 Lync Server 2013 배포의 일부인 풀로 이동할 수 없습니다.

    
      - **OU**는 이 연락처 개체가 위치할 Active Directory 조직 구성 단위를 지정합니다.
    
      - **DisplayNumber**는 연락처 개체의 전화 번호를 지정합니다. 각 연락처 개체의 전화 번호는 고유해야 합니다.
    
      - **AutoAttendant**는 연락처 개체가 자동 전화 교환인지 여부를 지정합니다. 자동 전화 교환은 발신자가 전화 시스템을 탐색하여 연결할 상대방을 찾을 수 있게 하는 음성 안내 집합을 제공합니다. 이 매개 변수의 값이 **False** (기본값)일 경우 연락처 개체는 구독자 액세스 연락처 개체입니다.

