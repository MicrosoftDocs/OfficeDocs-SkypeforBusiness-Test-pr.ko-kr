---
title: 파일럿 풀로 단일 사용자 이동
TOCTitle: 파일럿 풀로 단일 사용자 이동
ms:assetid: 80d5b365-f153-4c61-a148-f9e18ce6e027
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/JJ688109(v=OCS.15)
ms:contentKeyID: 49885843
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# 파일럿 풀로 단일 사용자 이동

 

_**마지막으로 수정된 항목:** 2012-09-28_

Lync Server 2013 제어판 또는 Lync Server 2013 관리 셸을 사용하면 Office Communications Server 2007 R2 풀에서 Lync Server 2013 파일럿 풀로 사용자를 이동할 수 있습니다. 아래 예의 등록자 풀 열에서 **\<Office Communications Server\>**는 Office Communications Server 2007 R2 풀이고 6명의 사용자가 모두 이 풀에 연결되어 있습니다. 다음 절차에 따라 Lync Server 2013 제어판 및 Lync Server 관리 셸을 사용해서 사용자를 Lync Server 2013으로 이동합니다.

![Lync Server 제어판에서 OCS 사용자 검색](images/JJ688109.d2008fd6-868b-4f26-84cf-57bb69e073d3(OCS.15).jpg "Lync Server 제어판에서 OCS 사용자 검색")

## Lync Server 2013 제어판을 사용하여 사용자를 이동하려면

1.  RTCUniversalServerAdmins 그룹의 구성원이거나 CsAdministrator 또는 CsUserAdministrator 관리 역할의 구성원인 계정으로 프런트 엔드 서버에 로그온합니다.

2.  Lync Server 제어판을 엽니다.

3.  **사용자**를 클릭합니다.

4.  **사용자 검색** 탭에서 **검색** 단추를 클릭합니다.

5.  그런 다음 **필터 추가**를 클릭합니다.

6.  **Office Communications Server 사용자**가 **True**와 같은 필터를 만듭니다.

7.  **찾기**를 클릭하여 기존 Office Communications Server 2007 R2 사용자를 검색합니다.
    
    ![Lync Server 제어판에서 OCS 사용자 검색](images/JJ688109.09528349-7915-41e1-91b4-6ab5c12b1b38(OCS.15).jpg "Lync Server 제어판에서 OCS 사용자 검색")  

8.  Lync Server 2013 풀로 이동할 사용자를 선택합니다. 이 예제에서는 Sara Davis를 이동합니다.

9.  **동작** 메뉴에서 **선택한 사용자를 풀로 이동**을 선택합니다.

10. 드롭다운 목록에서 Lync Server 2013 풀을 선택합니다.

11. **동작**, **선택한 사용자를 풀로 이동**, **확인**을 차례로 클릭합니다.
    
    ![사용자 이동의 대상 풀 설정 대화 상자](images/JJ688109.d7dc0759-87c5-4c23-938f-361576621504(OCS.15).jpg "사용자 이동의 대상 풀 설정 대화 상자")  

12. 이제 새 사용자에 대한 **등록자 풀** 열에 해당 사용자가 성공적으로 이동되었음을 나타내는 Lync Server 2013 풀이 포함되는지 확인합니다.

## Lync Server 2013 관리 셸을 사용하여 사용자를 이동하려면

1.  Lync Server 관리 셸을 엽니다.

2.  명령줄에 다음을 입력합니다.
    
        Move-CsLegacyUser -Identity "David Pelton" -Target "pool02.contoso.net"

3.  다음에는 명령줄에 다음을 입력합니다.
    
        Get-CsUser -Identity "David Pelton"

4.  **RegistrarPool** ID가 이제 Lync Server 2013 풀을 가리킵니다. 이 ID가 있으면 사용자가 성공적으로 이동된 것입니다.
    
    ![ID 필터가 사용된 Get-CsUser cmdlet의 출력](images/JJ205401.bc5d4672-8068-4475-b882-dbd305c801a9(OCS.15).jpg "ID 필터가 사용된 Get-CsUser cmdlet의 출력")  
    

    > [!NOTE]
    > <STRONG>Get-CsUser</STRONG> cmdlet에 대한 자세한 내용을 보려면 <STRONG>Get-Help Get-CsUser –Detailed</STRONG>를 실행합니다.


