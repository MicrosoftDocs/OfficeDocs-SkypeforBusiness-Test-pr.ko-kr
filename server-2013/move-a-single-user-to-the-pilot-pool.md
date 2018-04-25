---
title: 파일럿 풀로 단일 사용자 이동
TOCTitle: 파일럿 풀로 단일 사용자 이동
ms:assetid: e9de81a8-40dd-4446-81e7-a2b810eaea50
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/JJ205401(v=OCS.15)
ms:contentKeyID: 49305402
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# 파일럿 풀로 단일 사용자 이동

 

_**마지막으로 수정된 항목:** 2012-09-26_

Lync Server 2013 제어판 또는 Lync Server 2013 관리 셸을 사용하여 Lync Server 2010 풀에서 Lync Server 2013 파일럿 풀로 사용자를 이동할 수 있습니다. 아래 예의 등록자 풀 열에서 **pool01.contoso.net**은 Lync Server 2010 풀이며, 이 사용자 6명 모두가 이 풀에 연결됩니다. 다음 절차에 따라 사용자를 Lync Server 2013 제어판 및 Lync Server 관리 셸을 사용하여 Lync Server 2013 풀로 이동합니다.

## Lync Server 2013 제어판을 사용하여 사용자를 이동하려면

**Lync Server 2013 제어판의 사용자 목록**

![Lync Server 제어판, 사용자 이동 대화 상자](images/JJ205401.a2bce284-0392-4db3-9bb2-9f12699738e7(OCS.15).jpg "Lync Server 제어판, 사용자 이동 대화 상자")

1.  RTCUniversalServerAdmins 그룹의 구성원이거나 CsAdministrator 또는 CsUserAdministrator 관리 역할의 구성원인 계정으로 프런트 엔드 서버에 로그온합니다.

2.  **Lync Server 제어판**을 엽니다.

3.  **사용자**, 검색, **찾기**를 차례로 클릭합니다.

4.  Lync Server 2013 풀로 이동할 사용자를 선택합니다. 이 예제에서는 손영숙을 이동합니다.

5.  **동작** 메뉴에서 **선택한 사용자를 풀로 이동**을 선택합니다.

6.  드롭다운 목록에서 Lync Server 2013 풀을 선택합니다.

7.  **동작**, **선택한 사용자를 풀로 이동**, **확인**을 차례로 클릭합니다.
    
    ![사용자 이동, 대상 등록자 풀 대화 상자](images/JJ205401.8a375003-dc00-4541-b578-4d88f2010601(OCS.15).png "사용자 이동, 대상 등록자 풀 대화 상자")  

8.  이제 사용자에 대한 **등록자 풀** 열에 해당 사용자가 성공적으로 이동되었음을 나타내는 Lync Server 2013 풀이 포함되는지 확인합니다.

## Lync Server 2013 관리 셸을 사용하여 사용자를 이동하려면

1.  Lync Server 관리 셸를 엽니다.

2.  명령줄에 다음을 입력합니다.
    
        Move-CsUser -Identity "David Pelton" -Target "pool02.contoso.net"

3.  다음에는 명령줄에 다음을 입력합니다.
    
        Get-CsUser -Identity "David Pelton"

4.  **RegistrarPool** ID가 이제 Lync Server 2013 풀을 가리킵니다. 이 ID가 있으면 사용자가 성공적으로 이동된 것입니다.
    
    ![ID 필터가 사용된 Get-CsUser cmdlet의 출력](images/JJ205401.bc5d4672-8068-4475-b882-dbd305c801a9(OCS.15).jpg "ID 필터가 사용된 Get-CsUser cmdlet의 출력")  
    

    > [!NOTE]
    > <STRONG>Get-CsUser</STRONG> cmdlet에 대한 자세한 내용을 보려면 <STRONG>Get-Help Get-CsUser -Detailed</STRONG>를 실행합니다.


