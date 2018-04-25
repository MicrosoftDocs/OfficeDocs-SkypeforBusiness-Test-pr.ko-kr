---
title: 자동 검색용 DNS 구성
TOCTitle: 자동 검색용 DNS 구성
ms:assetid: f07a634c-3cf3-4958-8556-84596319ef54
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/JJ945656(v=OCS.15)
ms:contentKeyID: 52056985
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# 자동 검색용 DNS 구성

 

_**마지막으로 수정된 항목:** 2012-12-12_

Lync 클라이언트에 대해 자동 검색을 지원하려면 다음 DNS(Domain Name System) 레코드를 만들어야 합니다.

  - 조직 네트워크 내에서 연결하는 Lync 클라이언트를 지원하기 위한 내부 DNS 레코드

  - 인터넷에서 연결하는 Lync 클라이언트를 지원하기 위한 외부(공용) DNS 레코드

각 SIP 도메인에 대해 내부 DNS 레코드 및 외부 DNS 레코드를 만들어야 합니다.

DNS 레코드는 추가 SAN(주체 대체 이름)을 사용하여 새 인증서를 만드는 기능에 따라 A(호스트) 레코드 또는 CNAME 레코드일 수 있습니다. lyncdiscover.\<도메인 이름\> SAN을 사용하여 새 외부(공용) 인증서를 요청 및 배포할 수 없는 경우 HTTP/TCP 포트 80을 사용하는 절차를 따르십시오. 다음 절차에서는 내부 및 외부 DNS 레코드를 만드는 방법을 설명합니다.

## DNS CNAME 레코드를 만들려면

1.  다음과 같이 DNS 서버에 로그온합니다.
    
      - 내부 DNS 레코드를 만들려면 Domain Admins 그룹 또는 DnsAdmins 그룹의 구성원으로 네트워크의 DNS 서버에 로그온합니다.
    
      - 외부 DNS 레코드를 만들려면 공용 DNS 공급자에 연결합니다.

2.  **시작**, **관리 도구**를 차례로 클릭한 다음 **DNS**를 클릭하여 DNS 관리 스냅인을 엽니다.

3.  다음 중 하나를 수행합니다.
    
      - 내부 DNS 레코드의 경우 DNS 서버의 콘솔 트리에서 Active Directory 도메인(예: contoso.local)의 **정방향 조회 영역**을 확장합니다.
        

        > [!NOTE]
        > 이 도메인은 Lync Server 2013디렉터 풀 및 프런트 엔드 풀이 설치되는 Active Directory 도메인입니다.

    
      - 외부 DNS 레코드의 경우 DNS 서버의 콘솔 트리에서 SIP 도메인(예: contoso.com)의 **정방향 조회 영역**을 확장합니다.

4.  다음과 같이 디렉터 풀의 호스트 A 레코드가 있는지 확인합니다.
    
      - 내부 DNS 레코드의 경우에는 디렉터 풀의 내부 웹 서비스 FQDN(정규화된 도메인 이름)(예: lyncwebdir01.contoso.local)에 대해 호스트 A 레코드가 있어야 합니다.
    
      - 외부 DNS 레코드의 경우에는 디렉터 풀의 외부 웹 서비스 FQDN(예: lyncwebextdir.contoso.com)에 대해 호스트 A 레코드가 있어야 합니다.

5.  다음과 같이 프런트 엔드 풀의 호스트 A 레코드가 있는지 확인합니다.
    
      - 내부 DNS 레코드의 경우에는 프런트 엔드 풀의 내부 웹 서비스 FQDN(예: lyncwebpool01.contoso.local)에 대해 호스트 A 레코드가 있어야 합니다.
    
      - 외부 DNS 레코드의 경우에는 프런트 엔드 풀의 외부 웹 서비스 FQDN(예: lyncwebextpool01.contoso.com)에 대해 호스트 A 레코드가 있어야 합니다.

6.  내부 DNS 레코드의 경우 DNS 서버의 콘솔 트리에서 SIP 도메인(예: contoso.com)의 **정방향 조회 영역**을 확장합니다.
    

    > [!NOTE]
    > 외부 DNS 레코드를 만드는 경우에는 3단계에서 SIP 도메인에 대해 <STRONG>정방향 조회 영역</STRONG>이 이미 확장된 상태입니다.



7.  SIP 도메인 이름을 마우스 오른쪽 단추로 클릭한 다음 **새 별칭(CNAME)**을 클릭합니다.

8.  **별칭 이름**에 다음 중 하나를 입력합니다.
    
      - 내부 DNS 레코드의 경우 내부 자동 검색 서비스 URL의 호스트 이름으로 lyncdiscoverinternal을 입력합니다.
    
      - 외부 DNS 레코드의 경우 외부 자동 검색 서비스 URL의 호스트 이름으로 lyncdiscover를 입력합니다.

9.  **대상 호스트의 FQDN(정규화된 도메인 이름)**에서 다음 중 하나를 수행합니다.
    
      - 내부 DNS 레코드의 경우 디렉터 풀의 내부 웹 서비스 FQDN(예: lyncwebdir01.contoso.local)을 입력하거나 찾은 다음 **확인**을 클릭합니다.
    
      - 외부 DNS 레코드의 경우 디렉터 풀의 외부 웹 서비스 FQDN(예: lyncwebextdir.contoso.com)을 입력하거나 찾은 다음 **확인**을 클릭합니다.
    

    > [!NOTE]
    > 디렉터를 사용하지 않는 경우 프런트 엔드 풀의 내부 및 외부 웹 서비스 FQDN을 사용하거나, 단일 서버의 경우 프런트 엔드 서버 또는 Standard Edition 서버의 FQDN을 사용합니다.

    

    > [!IMPORTANT]
    > Lync Server 2013 환경에서 지원하는 각 SIP 도메인의 정방향 조회 영역에서 새 자동 검색 CNAME 레코드를 만들어야 합니다.



## DNS A 레코드를 만들려면

1.  다음과 같이 DNS 서버에 로그온합니다.
    
      - 내부 DNS 레코드를 만들려면 Domain Admins 그룹 또는 DnsAdmins 그룹의 구성원으로 네트워크의 DNS 서버에 로그온합니다.
    
      - 외부 DNS레코드를 만들려면 공용 DNS 공급자 또는 외부 DNS 서버에 연결합니다.

2.  **시작**, **관리 도구**를 차례로 클릭한 다음 **DNS**를 클릭하여 DNS 관리 스냅인을 엽니다.

3.  다음 중 하나를 수행합니다.
    
      - 내부 DNS 레코드의 경우 DNS 서버의 콘솔 트리에서 Active Directory 도메인(예: contoso.local)의 **정방향 조회 영역**을 확장합니다.
        

        > [!NOTE]
        > 이 도메인은 Lync Server 2013디렉터 풀 및 프런트 엔드 풀이 설치되는 Active Directory 도메인입니다.

    
      - 외부 DNS 레코드의 경우 DNS 서버의 콘솔 트리에서 SIP 도메인(예: contoso.com)의 **정방향 조회 영역**을 확장합니다.

4.  다음과 같이 디렉터 풀의 호스트 A(IPv6의 경우 AAAA) 레코드가 있는지 확인합니다.
    
      - 내부 DNS 레코드의 경우에는 디렉터 풀의 내부 웹 서비스 FQDN(예: lyncwebdir01.contoso.local)에 대해 호스트 A(IPv6의 경우 AAAA) 레코드가 있어야 합니다.
    
      - 외부 DNS 레코드의 경우에는 디렉터 풀의 외부 웹 서비스 FQDN(예: lyncwebextdir.contoso.com)에 대해 호스트 A(IPv6의 경우 AAAA) 레코드가 있어야 합니다.

5.  다음과 같이 프런트 엔드 풀의 호스트 A(IPv6의 경우 AAAA) 레코드가 있는지 확인합니다.
    
      - 내부 DNS 레코드의 경우에는 프런트 엔드 풀의 내부 웹 서비스 FQDN(예: lyncwebpool01.contoso.local)에 대해 호스트 A(IPv6의 경우 AAAA) 레코드가 있어야 합니다.
    
      - 외부 DNS 레코드의 경우에는 프런트 엔드 풀의 외부 웹 서비스 FQDN(예: lyncwebextpool01.contoso.com)에 대해 호스트 A(IPv6의 경우 AAAA) 레코드가 있어야 합니다.

6.  내부 DNS 레코드의 경우 DNS 서버의 콘솔 트리에서 SIP 도메인(예: contoso.com)의 **정방향 조회 영역**을 확장합니다.
    

    > [!NOTE]
    > 외부 DNS 레코드를 만드는 경우에는 3단계에서 SIP 도메인에 대해 <STRONG>정방향 조회 영역</STRONG>이 이미 확장된 상태입니다.



7.  SIP 도메인 이름을 마우스 오른쪽 단추로 클릭한 다음 **새 호스트(A 또는 AAAA)**를 클릭합니다.

8.  **이름**에 호스트 이름을 다음과 같이 입력합니다.
    
      - 내부 DNS 레코드의 경우 내부 자동 검색 서비스 URL의 호스트 이름으로 lyncdiscoverinternal을 입력합니다.
    
      - 외부 DNS 레코드의 경우 외부 자동 검색 서비스 URL의 호스트 이름으로 lyncdiscover를 입력합니다.
    

    > [!NOTE]
    > 도메인 이름은 레코드가 정의된 영역에서 가져온 것으로 가정되므로 A 레코드의 일부로 입력할 필요는 없습니다.



9.  **IP 주소**에 IP 주소를 다음과 같이 입력합니다.
    
      - 내부 DNS 레코드의 경우 디렉터의 내부 웹 서비스 IP 주소를 입력하거나, 부하 분산 장치를 사용하는 경우 디렉터 부하 분산 장치의 VIP(가상 IP)를 입력합니다.
        

        > [!NOTE]
        > 디렉터를 사용하지 않는 경우 프런트 엔드 서버 또는 Standard Edition 서버의 IP 주소를 입력하거나, 부하 분산 장치를 사용하는 경우 프런트 엔드 풀 부하 분산 장치의 VIP를 입력합니다.

    
      - 외부 DNS 레코드의 경우 역방향 프록시의 외부(공용) IP 주소를 입력합니다.

10. **호스트 추가**를 클릭한 다음 **확인**을 클릭합니다.

11. A 레코드를 추가로 만들려면 8-10단계를 반복합니다.
    

    > [!IMPORTANT]
    > Lync Server 2013 환경에서 지원하는 각 SIP 도메인의 정방향 조회 영역에서 새 lyncdiscover 및 lyncdiscoverinternal A 레코드를 만들어야 합니다.



12. A(IPv6의 경우 AAAA) 레코드를 모두 만든 후에 **완료**를 클릭합니다.

