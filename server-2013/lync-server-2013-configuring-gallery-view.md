---
title: 갤러리 보기 구성
TOCTitle: 갤러리 보기 구성
ms:assetid: 4a609178-47d8-4682-ac8d-29f882801924
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/JJ204871(v=OCS.15)
ms:contentKeyID: 49303543
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# 갤러리 보기 구성

 

_**마지막으로 수정된 항목:** 2012-10-30_

Lync Server 2013에서는 회의 정책에서 갤러리 보기 비디오 회의를 구성합니다. 갤러리 보기는 기본적으로 설정되어 있습니다. 갤러리 보기를 허용하지 않거나 일부 사용자에게만 허용하려는 경우 회의 정책에서 이 기능을 해제해야 합니다.

회의 참가자의 비디오를 사용할 수 없는 경우, Lync Server 2013의 새로운 기능인 고해상도 사진을 배포하면 사용자의 갤러리 보기 경험을 개선할 수 있습니다. 고해상도 사진은 Active Directory 도메인 서비스에 저장되는 더 작고 제한된 해상도의 대화 상대 사진에 대한 대안을 제공합니다. 고해상도 사진은 사용자의 Exchange 2013 사서함에 저장되므로 Lync Server 2013을 Exchange 2013과 통합해야 합니다. 자세한 내용은 [http://go.microsoft.com/fwlink/?linkid=260987\&clcid=0x412](http://go.microsoft.com/fwlink/?linkid=260987%26clcid=0x412)의 NextHop 블로그 문서, "Integrating Exchange 2013 and Lync Server 2013"()을 참조하십시오.


> [!NOTE]
> 각 블로그의 콘텐츠와 해당 URL은 공지 없이 변경될 수 있습니다.



Lync Server 2013 제어판을 사용하거나 다음 cmdlet 중 하나를 사용하여 갤러리 보기 매개 변수를 보거나 수정할 수 있습니다.

  - **Get-CsConferencingPolicy**

  - **Set-CsConferencingPolicy**

  - **New-CsConferencingPolicy**

다음 회의 정책 설정으로 갤러리 보기를 구성합니다.

  - **AllowMultiview**   이 매개 변수는 사용자가 갤러리 보기 비디오 회의를 구성하도록 허용할지 여부를 제어합니다. 이 매개 변수는 사용자가 만드는 예약 모임 및 임시 모임에 적용됩니다.
    
    예:
    
      - 이 매개 변수는 Lync Server 2013 풀에 있는 사용자 A에 대해 True로 설정되었습니다. 사용자 A가 구성하는 모임에서는 사용자가 모임에 참가하고 여러 비디오 스트림을 수신할 수 있습니다.
    
      - 이 매개 변수는 Lync Server 2013 풀에 있는 사용자 B에 대해 False로 설정되었습니다. 사용자 B가 구성하는 모임에는 Lync Server 2010에서 제공하는 비디오 회의 경험과 비슷한 단일 비디오 스트림이 포함됩니다.
    
    이 매개 변수는 여러 비디오 스트림을 허용하는 모임을 구성할 수 있는 사용자를 결정합니다. 여러 비디오 스트림을 허용하는 모임의 참가자는 개별 권한에 따라 여러 비디오 스트림을 수신하도록 허용되거나 허용되지 않을 수 있습니다(EnableMultiviewJoin 매개 변수 설명 참조).

  - **EnableMultiviewJoin**   이 매개 변수는 모임 참가자가 갤러리 보기를 허용하는 모임에서 갤러리 보기 비디오 경험을 수신할지 여부를 제어합니다. 이 매개 변수는 사용자가 참가하는 모임에서 사용자의 경험을 제어합니다.
    
    예:
    
      - 이 매개 변수는 사용자 C에 대해 True로 설정되었습니다. 사용자 C는 사용자 A가 구성하거나 시작한 모임에 참가할 때 여러 비디오 스트림을 수신할 수 있습니다. 사용자 C는 사용자 B가 구성하거나 시작한 모임에 참가할 때 Lync Server 2010에서 제공되는 비디오 회의 경험과 비슷한 단일 비디오 스트림을 수신합니다.
    
      - 이 매개 변수는 사용자 D에 대해 False로 설정되었습니다. 사용자 D는 사용자 A 또는 사용자 B가 구성한 모임에 참가할 때 Lync Server 2010에서 제공된 비디오 회의 경험과 비슷한 단일 비디오 스트림을 수신합니다.

다음 절차는 Lync Server 관리 셸을 사용하여 갤러리 보기 비디오 회의를 설정하는 예입니다.

## 갤러리 보기 비디오 회의에 대한 회의 정책을 수정하려면

1.  Lync Server 관리 셸 시작: **시작**, **모든 프로그램**, **Microsoft Lync Server 2013**을 차례로 클릭한 다음 **Lync Server 관리 셸**을 클릭합니다.

2.  명령줄에서 다음 cmdlet을 실행하여 회의 정책을 편집합니다.
    
        Set-CsConferencingPolicy -Identity Pool01ConferencingPolicy -AllowMultiview $true -EnableMultiviewJoin $true

