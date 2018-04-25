---
title: Lync Server 2013의 공통 영역 전화
TOCTitle: Lync Server 2013의 공통 영역 전화
ms:assetid: d63bb3de-154e-4347-9251-9fa94e7d593a
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/JJ994076(v=OCS.15)
ms:contentKeyID: 52056963
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Lync Server 2013의 공통 영역 전화

 

_**마지막으로 수정된 항목:** 2013-02-20_

공통 영역 전화는 개별 사용자와 연결되지 않은 IP 전화입니다. 공통 영역 전화는 특정 사무실에 있는 것이 아니라 일반적으로 건물의 로비, 카페, 직원 라운지, 회의실 등 많은 사람이 모일 수 있는 장소에 있습니다. Lync Server에서 일반적으로 개별 사용자에게 할당된 음성 정책 및 다이얼 플랜으로 유지 관리되는 다른 전화와는 달리 공통 영역 전화에는 개별 사용자가 할당되지 않습니다. 즉, 공통 영역 전화는 기타 전화와는 다른 방식으로 관리해야 합니다.

공통 영역 전화를 관리하려면 사용자 계정처럼 정책과 음성 계획을 할당할 수 있는 Active Directory 도메인 서비스 대화 상대 개체를 모든 공통 영역 전화에 대해 만듭니다. 이 방식을 사용하면 공통 영역 전화가 개별 사용자와 연결되어 있지 않더라도 해당 전화에 대한 제어를 유지 관리할 수 있습니다.

이 섹션의 항목을 통해 공통 영역 전화용으로 개체를 만들고 수정 및 삭제하는 방법과, 배포의 공통 영역 전화에 대한 구성 정보를 구성하고 보는 방법을 파악할 수 있습니다.


> [!NOTE]
> 공통 영역 전화로 사용 가능한 옵션은 Aastra 6721ip 공통 영역 전화, HP 4110 IP 전화 및 Polycom CX500 IP 공통 영역 전화의 세 가지입니다. Polycom CX3000 IP 회의용 전화도 공통 영역 전화의 한 형태입니다. 그러나 이 전화는 회의실 전용으로 사용됩니다. 공통 영역 전화에 대한 자세한 내용은 <A href="http://technet.microsoft.com/ko-kr/library/gg398958(v=ocs.14).aspx">새 장치 선택</A>의 공통 영역 전화 섹션을 참조하십시오.



## 이 단원의 내용

  - [공통 영역 전화 정보 보기](lync-server-2013-view-common-area-phone-information.md)

  - [공통 영역 전화 대화 상대 개체 만들기 또는 수정](lync-server-2013-create-or-modify-a-common-area-phone-contact-object.md)

  - [hot-desk를 사용하거나 사용하지 않도록 설정](lync-server-2013-enable-or-disable-hot-desking.md)

  - [공통 영역 전화 대화 상대 개체 삭제](lync-server-2013-delete-a-common-area-phone-contact-object.md)

  - [공통 영역 전화에 정책 할당](lync-server-2013-assign-policies-to-a-common-area-phone.md)

