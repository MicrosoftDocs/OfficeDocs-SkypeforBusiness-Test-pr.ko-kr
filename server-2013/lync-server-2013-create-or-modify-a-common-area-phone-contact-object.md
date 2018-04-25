---
title: 공통 영역 전화 대화 상대 개체 만들기 또는 수정
TOCTitle: 공통 영역 전화 대화 상대 개체 만들기 또는 수정
ms:assetid: eec33ad1-e4f2-49b2-91d6-d5a9d2e1714b
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/JJ994083(v=OCS.15)
ms:contentKeyID: 52056982
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# 공통 영역 전화 대화 상대 개체 만들기 또는 수정

 

_**마지막으로 수정된 항목:** 2013-02-20_

모든 공통 영역 전화에 대해 Active Directory 도메인 서비스 대화 상대 개체를 만들려면**New-CsCommonAreaPhone** cmdlet을 사용합니다. 이 cmdlet은 공통 영역 전화에 사용할 새 대화 상대 개체를 만들거나, 기존 대화 상대 개체를 새 공통 영역 전화에 연결할 수 있습니다. 공통 영역 전화와 연결된 대화 상대 개체의 속성을 수정하려면**Set-CsCommonAreaPhone** cmdlet을 사용합니다. **Set-CsCommonAreaPhone**에 대해 선택적 매개 변수를 사용하면 대화 상대의 Active Directory 표시 이름이나 전화와 연결된 줄 URI(Uniform Resource Identifier)와 같은 항목을 변경할 수 있으며 Lync Server에서 계정을 사용하거나 사용하지 않도록 설정할 수 있습니다. 수정할 수 있는 모든 항목에 대한 자세한 내용은 [Set-CsCommonAreaPhone](set-cscommonareaphone.md)의 매개 변수 섹션을 참조하십시오. **New-CsCommonAreaPhone** 매개 변수에 대한 자세한 내용은 [New-CsCommonAreaPhone](new-cscommonareaphone.md)을 참조하십시오.

이 두 cmdlet은 Lync Server 2013 관리 셸 또는 Windows PowerShell의 원격 세션에서 실행할 수 있습니다. 원격 Windows PowerShell을 사용하여 Lync Server에 연결하는 방법에 대한 자세한 내용은 Lync Server Windows PowerShell 블로그 문서인 "빠른 시작: 원격 PowerShell을 사용하여 Microsoft Lync Server 2010 관리"([http://go.microsoft.com/fwlink/p/?linkId=255876](http://go.microsoft.com/fwlink/p/?linkid=255876))를 참조하세요.


## 공통 영역 전화 대화 상대 개체 만들기

  - 새 공통 영역 전화 대화 상대 개체를 만들려면 **New-CsCommonAreaPhone** cmdlet을 사용합니다. 대화 상대 개체를 만들 때는 최소한 다음 정보를 제공해야 합니다.
    
      - **LineUri**: 공통 영역 전화에 할당된 전화 번호입니다. 전화 번호를 지정할 때는 E.164 형식을 사용해야 합니다.
    
      - **RegistrarPool**: 대화 상대 개체를 호스트할 등록자 풀의 FQDN(정규화된 도메인 이름)입니다.
    
      - **OU**: 대화 상대 개체를 만들 Active Directory 컨테이너의 고유 이름입니다.
    
    Active Directory 도메인 서비스 표시 이름도 지정하는 것이 좋습니다. 그렇지 않으면 GUID를 사용하여 전화 ID를 지정해야 합니다. 예를 들면 다음과 같습니다.
    
        New-CsCommonAreaPhone -LineUri "tel:+12065551219" -RegistrarPool "atl-cs-001.litwareinc.com" -OU "OU=Phones,dc=litwareinc,dc=com" -DisplayName "Lobby"

## 공통 영역 전화 대화 상대 개체 수정

  - 기존 공통 영역 전화 대화 상대 개체의 속성을 수정하려면 **Set-CsCommonAreaPhone** cmdlet을 사용합니다. 예를 들어 이 명령은 DisplayName이 Lobby인 공통 영역 전화에 대해 SIP 주소를 구성합니다.
    
        Set-CsCommonAreaPhone -Identity "Lobby" -SipAddress "sip:lobby@litwareinc.com"

자세한 내용은 [New-CsCommonAreaPhone](new-cscommonareaphone.md) cmdlet 및 [Set-CsCommonAreaPhone](set-cscommonareaphone.md) cmdlet의 도움말 항목을 참조하십시오.

