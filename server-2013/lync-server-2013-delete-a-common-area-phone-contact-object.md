---
title: 공통 영역 전화 대화 상대 개체 삭제
TOCTitle: 공통 영역 전화 대화 상대 개체 삭제
ms:assetid: f4c139dc-f07c-4c75-9345-e291aea41173
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/JJ994087(v=OCS.15)
ms:contentKeyID: 52056991
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# 공통 영역 전화 대화 상대 개체 삭제

 

_**마지막으로 수정된 항목:** 2013-02-20_

공통 영역 전화와 연결된 대화 상대 개체를 삭제하려는 경우가 있습니다. 예를 들어 직원 휴게실에서 전화를 제거하는 경우 해당 전화와 연결된 대화 상대 개체가 없어도 됩니다. **Remove-CsCommonAreaPhone** cmdlet을 사용하면 공통 영역 전화 계정을 삭제할 수 있습니다. 이 cmdlet을 실행하면 **Get-CsCommonAreaPhone**에 의해 반환된 공통 영역 전화 목록에서 전화가 삭제됩니다. 또한 해당 전화와 연결된 대화 상대 개체가 Active Directory 도메인 서비스에서 삭제됩니다.

공통 영역 전화 하나 또는 공통되는 요소(예: 표시 이름 또는 국가/지역 번호)를 포함하는 모든 공통 영역 전화를 제거하려면 **Remove-CsCommonAreaPhone**을 사용합니다. 이 cmdlet은 Lync Server 2013 관리 셸 또는 Windows PowerShell의 원격 세션에서 실행할 수 있습니다. 원격 Windows PowerShell을 사용하여 Lync Server에 연결하는 방법에 대한 자세한 내용은 Lync Server Windows PowerShell 블로그 문서인 "빠른 시작: 원격 PowerShell을 사용하여 Microsoft Lync Server 2010 관리"([http://go.microsoft.com/fwlink/p/?linkId=255876](http://go.microsoft.com/fwlink/p/?linkid=255876))를 참조하세요.


## 지정한 공통 영역 전화 제거

  - 다음 명령은 SIP 주소가 sip:mainlobby@litwareinc.com인 공통 영역 전화를 제거합니다.
    
        Remove-CsCommonAreaPhone -Identity "sip:mainlobby@litwareinc.com"

## 표시 이름을 기준으로 공통 영역 전화 제거

  - 다음 명령은 표시 이름에 문자열 값 "Building 14"가 포함된 모든 공통 영역 전화를 제거합니다.
    
        Get-CsCommonAreaPhone | Where-Object {$_.DisplayName -match "Building 14"} | Remove-CsCommonAreaPhone

## 국가 및 지역 번호를 기준으로 공통 영역 전화 제거

  - 다음 명령은 미국(국가 번호 1)의 지역 번호가 425인 모든 공통 영역 전화를 제거합니다.
    
        Get-CsCommonAreaPhone | Where-Object {$_.LineUri  -match "^tel:\+1425"} | Remove-CsCommonAreaPhone

자세한 내용은 [Remove-CsCommonAreaPhone](remove-cscommonareaphone.md) cmdlet의 도움말 항목을 참조하십시오.

## 참고 항목

#### 기타 리소스

[Get-CsCommonAreaPhone](get-cscommonareaphone.md)

