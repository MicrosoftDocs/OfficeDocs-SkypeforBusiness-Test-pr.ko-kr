---
title: Lync Server 2013에서 SQL Server 비표준 포트 및 별칭 배포
TOCTitle: Lync Server 2013에서 SQL Server 비표준 포트 및 별칭 배포
ms:assetid: 2da92c1f-250e-407a-8651-fb2aec76aeb0
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Dn776290(v=OCS.15)
ms:contentKeyID: 62634501
ms.date: 09/16/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Lync Server 2013에서 SQL Server 비표준 포트 및 별칭 배포

 

_**마지막으로 수정된 항목:** 2015-09-16_

Microsoft Lync Server 2013은 SQL Server에서 비표준 포트 및 별칭 사용을 지원합니다. SQL Server 비표준 포트 및 별칭을 사용하면 보안이 향상되고 보다 유연한 Lync 배포 환경이 만들어집니다. 다음 단계는 Lync Server 2013 환경을 적절히 보호하는 단계 중 하나에 불과합니다. Lync Server 2013의 공격 영역을 줄이려면 추가 단계를 수행해야 합니다.

이 문서에서는 Lync Server 2013에서 SQL Server 비표준 포트 및 별칭을 설정하는 데 필요한 단계를 설명합니다.

## Lync Server 2013에서 SQL Server 비표준 포트 및 별칭 배포

Lync Server 2013토폴로지 작성기에서는 Lync Server 2013을 구성할 때 실제 SQL Server FQDN을 사용하는 대신 SQL Server 별칭을 FQDN(정규화된 도메인 이름)으로 사용할 수 있습니다. 이렇게 하면 악의적인 공격자로부터 실제 SQL Server FQDN을 숨길 수 있습니다. 또한, 다음 그림과 같이 비표준 포트를 사용하면 표준 포트 1433에서 데이터베이스 공격을 시도하는 공격자가 실제 포트를 알 수 없게 됩니다.

![해커가 공격할 포트 번호를 알지 못합니다.](images/Dn776290.2f3923e0-2bdc-416b-a66b-bf56599eb14e(OCS.15).jpg "해커가 공격할 포트 번호를 알지 못합니다.")

Lync Server 2013이 SQL Server와 통신하는 데 사용하는 포트를 알아내기 위해 공격자는 모든 포트를 검색하여 포트 정보를 얻어야 합니다. 공격자가 포트를 검색하는 동안 이러한 명령을 감지하고 중지시킬 수 있는 보안 기회가 많아집니다. 비표준 포트를 사용한 보안 향상 외에도 SQL Server 별칭을 사용하여 배포에 유연성을 가져올 수도 있습니다. 이 기능은 SQL Server 이름을 변경해야 하는 상황에서 구성 변경을 줄이는 데에도 유용합니다.


> [!NOTE]
> SQL Server는 두 가지 내결함성 메서드(장애 조치(failover) 클러스터링 및 미러링)를 제공합니다. Lync Server 2013에서 SQL Server 비표준 포트 및 별칭을 사용하는 데 모든 SQL Server 내결함성 메서드가 지원됩니다.



토폴로지 작성기 내에서 SQL Server 데이터베이스 연결을 구성하거나 Install-CsDatabase cmdlet을 사용할 때 SQL Server 비표준 포트 번호를 명시적으로 정의하고 이를 SQL 인스턴스와 연결할 수 없습니다. 비표준 포트를 설정하려면 SQL Server 및 Windows Server 유틸리티를 사용해야 합니다.

Lync Server 2013에서 SQL Server 비표준 포트 및 별칭을 사용하도록 설정하려면 다음과 같은 세 가지의 기본 단계를 완료해야 합니다.

  - Lync Server 2013에 최신 업데이트가 적용되었는지 확인합니다.

  - SQL Server 비표준 포트 및 별칭을 설정합니다.

  - 토폴로지 작성기를 사용하여 SQL Server 별칭으로 Lync Server 2013을 구성합니다.

  - 토폴로지를 게시하고 데이터베이스를 확인합니다.

## Lync Server 2013에 최신 업데이트가 적용되었는지 확인

Lync Server 2013을 최신 상태로 유지하는 것이 중요합니다. 최신 업데이트 및 업데이트 적용 방법에 대한 정보를 확인하려면 [Lync Server 2013에 대한 업데이트](http://support.microsoft.com/kb/2809243)를 참조하세요.

## SQL Server 비표준 포트 및 별칭 설정

SQL Server 비표준 포트 및 별칭은 데이터베이스 인스턴스에 설정되어야 Lync Server 2013토폴로지 작성기에서 참조할 수 있습니다. SQL Server 비표준 포트 및 별칭을 설정하려면 다음과 같은 세 가지의 기본 단계를 완료해야 합니다.

  - 기본 TCP/IP 프로토콜 값을 변경합니다.

  - SQL Server 별칭을 만들고 구성합니다.

  - DNS(Domain Name System) CNAME(정식 이름) 리소스 레코드를 만듭니다.

**기본 TCP/IP 프로토콜 값 수정**

1.  다음 그림과 같이 **시작**을 선택하고 **SQL Server 구성 관리자**를 선택합니다.
    
    ![SQL Server Management Studio 아이콘](images/Dn776290.6e811f27-cea9-4437-b44c-55bff013150f(OCS.15).png "SQL Server Management Studio 아이콘")

2.  다음 그림과 같이 탐색 창에서 **SQL Server 인스턴스**를 선택하여 확장하고 **SQL Server 네트워크 구성**을 선택하여 확장한 다음 **\<인스턴스 이름\>에 대한 프로토콜**을 선택합니다.
    
    ![TCP/IP 속성으로 이동](images/Dn776290.3d7a964c-f17e-47fd-8f0c-535453da7fad(OCS.15).jpg "TCP/IP 속성으로 이동")

3.  오른쪽 창에서 **TCP/IP**를 마우스 오른쪽 단추로 클릭하고 **속성**을 선택합니다. TCP/IP 속성 대화 상자가 표시됩니다.

4.  **IP 주소** 탭을 선택합니다. IP 주소 탭에는 서버의 모든 활성 IP 주소가 표시됩니다. IP 주소는 다음 그림과 같이 IP1, IP2, ...IPAll 등의 형식으로 되어 있습니다.
    
    ![TCP/IP 속성을 엽니다.](images/Dn776290.ed2fd70d-1836-4ebf-80fe-09191d96585e(OCS.15).jpg "TCP/IP 속성을 엽니다.")

5.  모든 IP 주소에 대해 **TCP 동적 포트** 필드를 제거합니다. 필드에 0 문자가 포함되어 있으면 SQL Server가 동적 포트를 수신한다는 의미입니다. 이러한 필드를 제거하고 0이 포함되지 않았는지 확인합니다.

6.  Lync Server가 데이터베이스에 연결하기 위해 사용하게 될 IP 주소의 경우 다음 그림에서처럼 **사용**이 **예**로 설정되었는지 확인합니다.
    
    ![올바른 IP에 대해 사용을 예로 설정합니다.](images/Dn776290.7f818b91-0793-4594-8932-90447270fad9(OCS.15).jpg "올바른 IP에 대해 사용을 예로 설정합니다.")

7.  다음 그림과 같이 대화 상자 아래쪽에 있는 **IPAll** 섹션의 **TCP 포트** 필드에 원하는 포트를 입력합니다, 이 예제에서는 포트 50062를 사용하지만 49152와 65535 사이의 아무 포트나 사용할 수 있습니다. 이러한 포트는 동적 및 비공개 사용을 위해 할당되며 Lync Server 2013 배포에 사용되는 다른 포트와 충돌하지 않습니다.
    
    ![IPAll 섹션에서 포트를 설정합니다.](images/Dn776290.b5af53e2-7961-4664-b586-3ca8f3a17f06(OCS.15).jpg "IPAll 섹션에서 포트를 설정합니다.")

8.  **확인**을 선택하여 TCP/IP 속성 대화 상자를 종료합니다.

9.  SQL Server 구성 관리자의 왼쪽 창에서 **SQL Server 서비스**를 선택하여 SQL Server 인스턴스를 다시 시작합니다. 그런 다음 아래 그림과 같이 오른쪽 창에서 **SQL Server \<인스턴스 이름\>**을 마우스 오른쪽 단추로 클릭하고 **다시 시작**을 선택합니다.
    
    ![인스턴스에 대한 SQL Server 서비스를 다시 설정합니다.](images/Dn776290.a965c8cf-f769-4b52-bb38-c48a438cf491(OCS.15).jpg "인스턴스에 대한 SQL Server 서비스를 다시 설정합니다.")


> [!IMPORTANT]
> 새 SQL Server 포트가 포함되도록 방화벽 설정을 업데이트해야 합니다.



**SQL Server 별칭 만들기 및 구성**

1.  다음 그림과 같이 **시작**을 선택하고 **SQL Server 구성 관리자**를 선택합니다.
    
    ![SQL Server Management Studio 아이콘](images/Dn776290.6e811f27-cea9-4437-b44c-55bff013150f(OCS.15).png "SQL Server Management Studio 아이콘")

2.  다음 그림과 같이 왼쪽 창에서 **SQL Server 인스턴스**를 선택하여 확장하고 **SQL Native Client \<버전\> 구성**을 선택하여 확장한 다음 **별칭**을 선택합니다.
    
    ![SQL Server 구성 관리자의 별칭](images/Dn776290.95341826-55d7-425f-ae19-d47d6668c5d8(OCS.15).jpg "SQL Server 구성 관리자의 별칭")

3.  **별칭**을 마우스 오른쪽 단추로 클릭하고 **새 별칭…**을 선택합니다.

4.  다음 그림과 같이 **별칭 이름**, **포트 번호**, **프로토콜**, **서버**를 입력합니다.
    
    ![새 별칭 만들기](images/Dn776290.03653588-aecf-4fdd-b58a-95f5b372d478(OCS.15).jpg "새 별칭 만들기")
    

    > [!WARNING]
    > 이 포트는 SQL Server가 수신하게 될 포트이기 때문에 이전 단계에 사용했던 것과 동일한 비표준 포트를 입력해야 합니다. 구성된 별칭이 잘못된 SQL Server FQDN 또는 인스턴스와 연결되는 경우에는 연결된 네트워크 프로토콜을 비활성화한 다음 다시 활성화해야 합니다. 이렇게 하면 캐시된 연결 정보가 모두 삭제되고 클라이언트가 올바르게 연결될 수 있습니다.



**DNS CNAME 리소스 레코드 만들기**

1.  DNS를 관리하는 컴퓨터에 로그인합니다.

2.  다음 그림과 같이 **시작**을 선택하고 **서버 관리자**를 선택합니다.
    
    ![서버 관리자 열기](images/Dn776290.3e4bd8ad-2a65-4a05-af40-c8dd3583bc8f(OCS.15).jpg "서버 관리자 열기")

3.  다음 그림과 같이 **도구** 드롭다운을 선택하고 **DNS**를 선택합니다.
    
    ![서버 관리자에서 DNS 열기](images/Dn776290.415e1da1-7c9a-4a4e-a896-ca34a76aaeff(OCS.15).jpg "서버 관리자에서 DNS 열기")

4.  왼쪽 창에서 서버 이름 노드를 확장하고 정방향 조회 영역 노드를 확장한 다음 관련 도메인을 선택합니다.

5.  다음 그림과 같이 도메인을 마우스 오른쪽 단추로 클릭하고 **새 별칭(CNAME)...**을 선택합니다.
    
    ![옵션을 선택하여 새 별칭 CNAME 만들기](images/Dn776290.abe66cca-b53c-427a-9094-1a59dc6840ca(OCS.15).jpg "옵션을 선택하여 새 별칭 CNAME 만들기")

6.  다음 그림과 같이 **별칭 이름** 및 **SQL Server의 FQDN**을 입력합니다.
    
    ![새 별칭 CNAME 대화 상자 채우기](images/Dn776290.dd0ebd2d-3407-4459-8bd9-2b389a7bc440(OCS.15).jpg "새 별칭 CNAME 대화 상자 채우기")

7.  **확인**을 선택하여 CNAME을 저장하고 DNS 관리자에서 이를 확인합니다.

## 데이터베이스 연결 확인

데이터베이스 연결이 이루어졌는지 확인하는 방법에는 여러 가지가 있습니다. SQL Server 데이터베이스가 별칭을 사용하여 지정된 포트를 수신하는지 확인해야 합니다. **netstat** 및 **telnet** 명령을 사용하여 빠르게 확인할 수 있습니다.


> [!NOTE]
> 텔넷 클라이언트는 Windows Server에 포함된 기능이지만 설치해야 합니다. Windows Server 기능은 서버 관리자를 열고 [관리] 메뉴에서 [역할 및 기능 추가]를 선택하여 설치할 수 있습니다.



**netstat 및 telnet을 사용하여 데이터베이스 연결 확인**

1.  **시작**을 선택하고 **cmd**를 입력하여 명령 프롬프트를 엽니다.

2.  다음 그림과 같이 **netstat -a -f**를 입력하고 SQL Server가 정확한 포트에서 실행되는지 확인합니다.
    
    ![netstat을 사용하여 포트 확인](images/Dn776290.4ff3a1b2-c5eb-4496-8be7-374c351fa027(OCS.15).jpg "netstat을 사용하여 포트 확인")

3.  **telnet \<별칭 이름\> \<포트 번호\>**를 입력하여 SQL Server 인스턴스로의 연결을 확인합니다. 연결에 성공하면 텔넷이 연결되고 오류가 표시되지 않습니다. 이는 SQL Server 인스턴스가 정확한 별칭을 사용하는 정확한 포트를 수신하고 있음을 나타냅니다. SQL Server 데이터베이스에 연결하는 데 문제가 생기면 텔넷에서는 연결되지 않았다는 오류가 표시됩니다. 데이터베이스 서버에서 데이터베이스 연결을 확인한 후에는 Lync Server에서 네트워크를 통해 동일한 작업을 수행할 할 수 있습니다. 이 과정에서 액세스를 차단하는 방화벽이 있는지 확인합니다.

## 결론

SQL Server 별칭이 구성되면 이를 사용하여 토폴로지 작성기 도구에서 Lync Server 2013 토폴로지를 만들 수 있습니다. 토폴로지에 대한 자세한 내용은 [Lync Server 2013에서 토폴로지 정의 및 구성](lync-server-2013-defining-and-configuring-the-topology.md)을 참조하세요.

## 참고 항목

#### 개념

[Microsoft Lync Server 2013](microsoft-lync-server-2013.md)  

#### 기타 리소스

[Lync Server 2013의 보안 계획](lync-server-2013-planning-for-security.md)  
[Lync Server 2013에서 토폴로지 정의 및 구성](lync-server-2013-defining-and-configuring-the-topology.md)  
[Lync Server 2013 배포](lync-server-2013-deploying-lync-server.md)

