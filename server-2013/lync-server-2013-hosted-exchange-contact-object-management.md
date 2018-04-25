---
title: 'Lync Server 2013: 호스팅된 Exchange 연락처 개체 관리'
TOCTitle: 호스팅된 Exchange 연락처 개체 관리
ms:assetid: eead9d76-bc4f-4c1c-9779-683cb7a88410
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg412978(v=OCS.15)
ms:contentKeyID: 49305451
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Lync Server 2013의 호스팅된 Exchange 연락처 개체 관리

 

_**마지막으로 수정된 항목:** 2012-09-25_

교차 프레미스 배포에서 각 자동 전화 교환 번호 및 구독자 액세스 번호에 대해 대화 상대 개체를 구성해야 합니다.

호스팅된 Exchange UM과의 통합 시 Active Directory Exchange UM 설정에 따라 달라지므로 ocsumutil.exe를 사용하여 연락처 개체를 관리할 수 없습니다. 교차 프레미스 배포에서 Lync Server 2013 및 호스팅된 Exchange UM은 상호 신뢰 관계가 없는 별도의 포리스트에 설치됩니다. 보안상의 이유로 Lync Server 2013 관리자는 Exchange UM Active Directory 설정에 직접 액세스할 수 없습니다. 따라서 Lync Server 2013은 Lync Server 2013 서버와 호스팅된 UM 서비스에 모두 액세스할 수 있는 *공유 SIP 주소 공간* 에서 연락처 개체를 관리할 수 있도록 다른 모델을 제공합니다.

## 호스팅된 대화 상대 개체 워크플로

다음은 대화 상대 개체를 관리하기 위해 호스팅된 Exchange 테넌트 관리자가 수행하는 일반적인 단계입니다.

1.  Exchange 관리자가 Exchange UM 구독자 액세스 및 자동 전화 교환 대화 상대 개체에 대한 전화 번호를 요청합니다.

2.  Lync Server 2013 관리자가 각 전화 번호에 대한 연락처 개체를 만들고 호스팅된 음성 사서함 정책을 각 연락처 개체에 지정합니다.

3.  Lync Server 2013 관리자가 Exchange 관리자에게 전화 번호를 제공합니다.

4.  Exchange 관리자가 자동 전화 교환 및 구독자 액세스에 적합한 Exchange UM 다이얼 플랜에 전화 번호를 지정합니다.


> [!NOTE]
> 온-프레미스 배포에서 구성되었으므로 연락처 개체에 대해 Lync Server 2013 다이얼 플랜 설정을 별도로 구성하지 않아도 됩니다.



## 호스팅된 대화 상대 개체 구성


> [!NOTE]
> 호스팅된 Exchange UM에 대해 Lync Server 2013 연락처 개체를 사용하도록 설정하려면 이러한 개체에 적용할 호스팅된 음성 사서함 정책을 배포해야 합니다. 사용하도록 설정할 연락처 개체에 적용되는 경우에는 정책 범위를 전역, 사이트 수준 또는 사용자별로 지정할 수 있습니다. 자세한 내용은 <A href="lync-server-2013-hosted-voice-mail-policies.md">Lync Server 2013의 호스팅된 음성 메일 정책</A>을 참조하십시오.



교차 프레미스 배포에서 호스팅된 자동 전화 교환 및 구독자 액세스 대화 상대 개체를 구성하려면 다음 cmdlet를 사용해야 합니다.

  - **New-CsExUmContact** - 호스팅된 UM에 대해 새 대화 상대 개체를 만듭니다.

  - **Set-CsExUmContact** - 호스팅된 Exchange UM에 대해 기존의 대화 상대 개체를 수정합니다.

다음은 자동 전화 교환 대화 상대 개체를 만드는 예입니다.

    New-CsExUmContact -SipAddress sip:exumaa1@fabrikam.com -RegistrarPool RedmondPool.litwareinc.com -OU "OU=ExUmContacts,DC=litwareinc,DC=com" -DisplayNumber 2065559876 -AutoAttendant $True

이 예는 SIP 주소가 sip:exumaa1@fabrikam.com인 새 Exchange UM 연락처 개체를 만듭니다. Lync Server 2013 등록자 서비스가 실행되는 풀의 이름은 RedmondPool.litwareinc.com이며, 이 정보가 저장되는 Active Directory 조직 구성 단위는 OU=ExUmContacts,DC=litwareinc,DC=com입니다. 연락처 개체의 전화 번호는 2065554567이며, 선택적 -AutoAttendant $True 매개 변수는 이 개체가 자동 전화 교환 연락처 개체임을 지정합니다. -AutoAttendant 매개 변수를 False(기본값)로 설정하면 구독자 액세스 연락처 개체가 지정됩니다.

New-CsExUmContact 및 Set-CsExUmContact cmdlet에 대한 자세한 내용은 Lync Server 관리 셸 설명서를 참조하십시오.

