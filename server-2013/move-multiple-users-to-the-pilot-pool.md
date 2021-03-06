﻿---
title: 파일럿 풀로 여러 사용자 이동
TOCTitle: 파일럿 풀로 여러 사용자 이동
ms:assetid: 90d0590c-922c-4933-b778-9dd850b59310
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/JJ205096(v=OCS.15)
ms:contentKeyID: 49304381
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# 파일럿 풀로 여러 사용자 이동

 

_**마지막으로 수정된 항목:** 2012-10-02_

Lync Server 2013 제어판 또는 Lync Server 2013 관리 셸을 사용하여 Lync Server 2010 풀의 여러 사용자를 Lync Server 2013 파일럿 풀로 이동할 수 있습니다.

## Lync Server 2013 제어판을 사용하여 여러 사용자를 이동하려면

1.  **Lync Server 제어판** 을 엽니다.

2.  **사용자** , 검색, **찾기** 를 차례로 클릭합니다.

3.  Lync Server 2013 풀로 이동할 사용자 두 명을 선택합니다. 이 예에서는 사용자 Chen Yang과 Claus Hansen을 이동하겠습니다.
    
    ![사용자를 특정 등록 풀로 이동](images/JJ205096.70d510e1-8e6b-40a5-a80b-27cbc63fc337(OCS.15).jpg "사용자를 특정 등록 풀로 이동")  

4.  **동작** 메뉴에서 **선택한 사용자를 풀로 이동** 을 선택합니다.

5.  드롭다운 목록에서 Lync Server 2013 풀을 선택합니다.

6.  **동작** , **선택한 사용자를 풀로 이동** , 확인을 차례로 클릭합니다.
    
    ![사용자 이동, 대상 등록자 풀 대화 상자](images/JJ205401.8a375003-dc00-4541-b578-4d88f2010601(OCS.15).png "사용자 이동, 대상 등록자 풀 대화 상자")  

7.  사용자의 **등록자 풀** 열에 이제 Lync Server 2013 풀이 포함되어 있는지 확인합니다. 포함되어 있으면 사용자가 성공적으로 이동된 것입니다.

## Lync Server 2013 관리 셸을 사용하여 여러 사용자를 이동하려면

1.  Lync Server 2013 관리 셸를 엽니다.

2.  명령줄에 다음을 입력하고 **User1** 및 **User2**를 이동하려는 특정 사용자 이름으로 바꾸고 **pool\_FQDN**을 대상 풀의 이름으로 바꿉니다. 이 예에서는 Hao Chen과 Katie Jordan을 이동하겠습니다.
    
        Get-CsUser -Filter {DisplayName -eq "User1" -or DisplayName - eq "User2"} | Move-CsUser -Target "pool_FQDN"
    
    ![PowerShell Get-CsUser cmdlet의 예제](images/JJ205096.767ff9fc-755d-4a80-a710-5b1367aecbe0(OCS.15).jpg "PowerShell Get-CsUser cmdlet의 예제")  

3.  명령줄에 다음을 입력합니다.
    
        Get-CsUser -Identity "User1"

4.  **등록자 풀** ID는 이제 사용자가 이전 단계에서 **pool\_FQDN**으로 지정한 풀을 가리킵니다.이 ID가 있으면 사용자가 성공적으로 이동된 것입니다. 이 단계를 반복하여 **User2**가 이동되었는지 확인합니다.
    
    ![PowerShell Get-UsUser -Identity cmdlet의 출력](images/JJ205096.8ff04c67-37a0-4156-bfbc-28f9f7b137c8(OCS.15).jpg "PowerShell Get-UsUser -Identity cmdlet의 출력")  

## Lync Server 2013 관리 셸을 사용하여 모든 사용자를 동시에 이동하려면

이 예에서는 모든 사용자가 Lync Server 2010 풀(pool01.contoso.net)로 복귀되었습니다. Lync Server 2013 관리 셸을 사용하여 모든 사용자를 동시에 Lync Server 2013 풀(pool02.contoso.net)로 이동하겠습니다.

1.  **Lync Server 2013 관리 셸**을 엽니다.

2.  명령줄에 다음을 입력합니다.
    
        Get-CsUser -OnLyncServer | Move-CsUser -Target "pool_FQDN"
    
    ![PowerShell cmdlet 및 관리 셸의 결과](images/JJ205096.1e57ccb1-9378-4dc7-82b7-dcaa63a285c6(OCS.15).png "PowerShell cmdlet 및 관리 셸의 결과")  

3.  그런 다음 파일럿 사용자 한 명에 대해 **Get-CsUser**를 실행합니다.
    
        Get-CsUser -Identity "Hao Chen"

4.  각 사용자의 **등록자 풀** ID는 이제 사용자가 이전 단계에서 "pool\_FQDN"으로 지정한 풀을 가리킵니다. 이 ID가 있으면 사용자가 성공적으로 이동된 것입니다.

5.  또한 Lync Server 2013 제어판에서 사용자 목록을 보고 등록자 풀 값이 이제 Lync Server 2013 풀을 가리키는지 확인할 수도 있습니다.
    
    ![Lync Server 2013 제어판 사용자 목록](images/JJ205096.3f2e87a7-ec59-43c5-82cb-e770108bfb04(OCS.15).jpg "Lync Server 2013 제어판 사용자 목록")

