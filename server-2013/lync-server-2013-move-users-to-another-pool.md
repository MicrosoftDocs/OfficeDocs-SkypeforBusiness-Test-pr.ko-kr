---
title: 다른 풀로 사용자 이동
TOCTitle: 다른 풀로 사용자 이동
ms:assetid: e7b4968c-0e9d-4d56-b5f1-9edf0f7206f8
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg182600(v=OCS.15)
ms:contentKeyID: 49305373
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# 다른 풀로 사용자 이동

 

_**마지막으로 수정된 항목:** 2013-03-11_

Lync Server 제어판을 사용하여 특정 서버나 풀에 사용자를 할당할 수 있습니다.


> [!TIP]
> 복합 Active Directory 환경에서 Microsoft Office Communications Server 2007 R2 및 이전 버전을 실행하는 원본 풀에서 기존의 모든 사용자를 Lync Server 2013 대상 풀로 이동하면 Active Directory 복제 속도가 느려질 수 있습니다. 이러한 문제를 방지하려면 검색 필터를 사용하여 Microsoft Office Communications Server 2007 R2 또는 이전 버전을 실행하는 풀에서 사용자를 별도로 이동하거나 Lync Server 관리 셸을 사용하여 cmdlet으로 사용자를 이동할 수 있습니다. 또한 필터 기능은 Lync Server 2013 사용자에서 작동합니다.



## 선택한 사용자를 다른 서버나 풀로 이동하려면

1.  CsUserAdministrator 역할 또는 CsAdministrator 역할에 할당된 사용자 계정에서 내부 배포된 컴퓨터에 로그온합니다.

2.  브라우저 창을 연 다음 Admin URL을 입력하여 Lync Server 제어판을 엽니다. Lync Server 제어판을 시작하는 데 사용할 수 있는 다양한 방법에 대한 자세한 내용은 [Lync Server 관리 도구 열기](lync-server-2013-open-lync-server-administrative-tools.md)를 참조하세요.

3.  왼쪽 탐색 모음에서 **사용자**를 클릭합니다.

4.  **사용자 검색** 상자에 원하는 사용자 계정의 표시 이름, 이름, 성, SAM(보안 계정 관리자) 계정 이름, SIP 주소 또는 줄 URI(Uniform Resource Identifier)를 모두 또는 첫부분을 입력하고 **찾기**를 클릭합니다.

5.  테이블의 목록에서 특정 사용자나 여러 사용자를 선택합니다.

6.  **동작** 메뉴에서 **선택한 사용자를 풀로 이동**을 클릭합니다.

7.  **사용자 이동**의 **대상 등록자 풀**에서 사용자를 이동할 풀을 선택합니다.

8.  (선택 사항) 대상 서버나 풀을 사용할 수 없는 경우 **강제 적용** 확인란을 선택합니다.
    

    > [!WARNING]
    > <STRONG>강제 적용</STRONG>을 선택하면 사용자 계정이 이동되지만 연결된 사용자 데이터가 삭제됩니다(예: 사용자가 예약한 회의). 이 확인란을 선택하지 않으면 계정 및 연결된 데이터가 둘 다 이동됩니다.



## 특정 서버나 풀의 모든 사용자를 다른 서버나 풀로 이동하려면

1.  CsUserAdministrator 역할 또는 CsAdministrator 역할에 할당된 사용자 계정에서 내부 배포된 컴퓨터에 로그온합니다.

2.  브라우저 창을 연 다음 Admin URL을 입력하여 Lync Server 제어판을 엽니다. Lync Server 제어판을 시작하는 데 사용할 수 있는 다양한 방법에 대한 자세한 내용은 [Lync Server 관리 도구 열기](lync-server-2013-open-lync-server-administrative-tools.md)를 참조하세요.

3.  왼쪽 탐색 모음에서 **사용자**를 클릭합니다.

4.  **동작** 메뉴에서 **모든 사용자를 풀로 이동**을 클릭합니다.

5.  **사용자 이동**의 **원본 등록자 풀**에서 이동할 사용자 계정이 있는 풀을 선택합니다.

6.  **대상 등록자 풀**에서 사용자를 이동할 풀을 선택합니다.

7.  (선택 사항) 대상 서버나 풀을 사용할 수 없는 경우 **강제 적용** 확인란을 선택합니다.
    

    > [!WARNING]
    > <STRONG>강제 적용</STRONG>을 선택하면 사용자 계정이 이동되지만 연결된 사용자 데이터가 삭제됩니다(예: 사용자가 예약한 회의). 이 확인란을 선택하지 않으면 계정 및 연결된 데이터가 둘 다 이동됩니다.



## 필터를 사용하여 한 풀에서 다른 풀로 사용자를 이동하려면

1.  CsUserAdministrator 역할 또는 CsAdministrator 역할에 할당된 사용자 계정에서 내부 배포된 컴퓨터에 로그온합니다.

2.  브라우저 창을 연 다음 Admin URL을 입력하여 Lync Server 제어판을 엽니다. Lync Server 제어판을 시작하는 데 사용할 수 있는 다양한 방법에 대한 자세한 내용은 [Lync Server 관리 도구 열기](lync-server-2013-open-lync-server-administrative-tools.md)를 참조하세요.

3.  왼쪽 탐색 모음에서 **사용자**를 클릭합니다.

4.  **사용자 검색**에서 **검색**을 클릭하고 **필터 추가**를 클릭합니다.

5.  검색 조건에서 **등록자 풀**, **같음**, **현재 풀 FQDN**을 차례로 선택한 후 **찾기**를 클릭합니다.

6.  **동작** 메뉴에서 **모든 사용자를 풀로 이동**을 클릭합니다.
    

    > [!NOTE]
    > 필터를 기존 사용자 집합에 적용하면 <STRONG>모든 사용자를 풀로 이동</STRONG> 옵션이 사용 가능한 <STRONG><EM>모든</EM></STRONG> 사용자가 아닌 필터링된 사용자 하위 집합의 컨텍스트로 표시됩니다.



7.  **사용자 이동**의 **원본 등록자 풀**에서 이동할 사용자 계정이 있는 풀을 선택합니다.

8.  **대상 등록자 풀**에서 사용자를 이동할 풀을 선택합니다.

9.  (선택 사항) 대상 서버나 풀을 사용할 수 없는 경우 **강제 적용** 확인란을 선택합니다.
    

    > [!WARNING]
    > <STRONG>강제 적용</STRONG>을 선택하면 사용자 계정이 이동되지만 연결된 사용자 데이터가 삭제됩니다(예: 사용자가 예약한 회의 및 대화 상대). 이 확인란을 선택하지 않으면 계정 및 연결된 데이터가 둘 다 이동됩니다.



## Lync 관리 셸을 사용하여 한 풀의 사용자를 다른 풀로 이동하려면

1.  Windows PowerShell 명령 실행 방법(로컬 또는 원격)에 따라 다음과 같이 올바른 Lync Server 2013 관리 역할의 구성원으로 로그온해야 합니다.
    
    1.  로컬 컴퓨터에서 명령을 실행하는 경우(예: 프런트 엔드 서버에 직접 로그온하는 경우): Lync Server 관리 셸이 설치된 컴퓨터에 RTCUniversalServerAdmins 그룹의 구성원으로 로그온하거나 [Lync Server 2013에서 설치 권한 위임](lync-server-2013-delegate-setup-permissions.md)에 설명된 대로 필요한 사용자 권한으로 로그온합니다.
    
    2.  다른 컴퓨터에서 원격으로 명령을 실행하는 경우(예: 자신의 컴퓨터에 로그온하여 Standard Edition 프런트 엔드 서버에서 명령을 원격으로 실행하는 경우): CsUserAdministrator 역할 또는 CsAdministrator 역할에 할당된 사용자 계정에서 내부 배포된 컴퓨터에 로그온합니다.

2.  Lync Server 관리 셸 시작: **시작**, **모든 프로그램**, **Microsoft Lync Server 2013**을 차례로 클릭한 다음 **Lync Server 관리 셸**을 클릭합니다.

3.  단일 사용자를 이동하려면 다음과 같이 Move-CsUser cmdlet을 사용합니다.
    
        Move-CsUser -Identity "Pilar Ackerman" -Target "pool01.contoso.net"
    
    이동할 사용자가 Pilar Ackerman이면 이 사용자가 현재 지정된 홈 풀에서 pool01.contoso.net 풀로 이동됩니다.

4.  많은 수의 사용자를 이동하려면 **Get-CsUser** cmdlet과 함께 필터를 사용하고 결과 사용자 집합을 **Move-CsUser**에 전달합니다.
    
        Get-CsUser -Filter {RegistrarPool -eq "CurrentPoolFqdn"} | Move-CsUser -Target "TargetPoolFQDN"
    
    **Get-CsUser** 및 **Move-CsUser**의 조합 명령의 결과는 다음과 같을 수 있습니다.
    
        Get-CsUser -Filter {RegistrarPool -eq "pool02.contoso.net"} | Move-CsUser -Target "pool01.contoso.net"

## 참고 항목

#### 기타 리소스

[사용자 계정 속성 수정](lync-server-2013-modifying-user-account-properties.md)

