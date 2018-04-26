---
title: Lync Server 2013에서 사용자별 호스팅된 음성 메일 정책 할당
TOCTitle: Lync Server 2013에서 사용자별 호스팅된 음성 메일 정책 할당
ms:assetid: d44c71a0-4407-4ab4-b7e0-d671dde3425f
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg398919(v=OCS.15)
ms:contentKeyID: 49305138
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Lync Server 2013에서 사용자별 호스팅된 음성 메일 정책 할당

 

_**마지막으로 수정된 항목:** 2010-11-07_

사용자별로 하나 이상의 호스팅된 음성 메일 정책을 배포하는 것은 선택 사항입니다. 사용자별 정책을 배포하려면 이 정책을 사용자, 개체 또는 대화 상대 개체에 명시적으로 할당해야 합니다.

사용자별 호스팅된 음성 메일 정책 할당을 할당하거나 제거하는 방법에 대한 자세한 내용은 다음 cmdlet에 대한 Lync Server 관리 셸 설명서를 참조하십시오.

  - Grant-CsHostedVoicemailPolicy

  - Remove-CsHostedVoicemailPolicy

## 사용자별 호스팅된 음성 메일 정책을 할당하려면

1.  Lync Server 관리 셸 시작: **시작**, **모든 프로그램**, **Microsoft Lync Server 2013**을 차례로 클릭한 다음 **Lync Server 관리 셸**을 클릭합니다.

2.  Grant-CsHostedVoicemailPolicy cmdlet를 실행하여 개별 사용자, 그룹 및 대화 상대 개체에 사용자별 호스팅된 음성 메일 정책을 할당합니다. 예를 들어 다음을 실행합니다.
    
        Grant-CsHostedVoicemailPolicy -Identity "Ken Myer" -PolicyName ExRedmond
    
    이 예에서는 ExRedmond hosted 음성 메일 정책이 Ken Myer라는 사용자에게 할당되었습니다.
    
    **Identity**는 수정할 사용자 계정을 지정합니다. Identity 값은 다음 형식 중 하나를 사용하여 지정할 수 있습니다.
    
      - 사용자의 SIP 주소
    
      - 사용자의 Active Directory 사용자 계정 이름
    
      - 사용자의 도메인\\로그온 이름(예: contoso\\kenmyer)
    
      - 사용자의 Active Directory 도메인 서비스 표시 이름(예: Ken Myer). Identity 값으로 표시 이름을 사용하는 경우 별표(\*) 와일드카드 문자를 사용할 수 있습니다. 예를 들어 Identity 값이 "\* Smith"일 경우 표시 이름이 "Smith" 문자열 값으로 끝나는 모든 사용자를 반환합니다.
    

    > [!NOTE]
    > SAM 계정 이름은 포리스트에서 고유하지 않아도 되므로 사용자의 Active Directory SAM 계정 이름을 Identity 값으로 사용할 수 없습니다.


