---
title: 'Lync Server 2013: DNS SRV 레코드 만들기 및 확인'
TOCTitle: DNS SRV 레코드 만들기 및 확인
ms:assetid: 86888c7e-1401-458f-9a7b-08ac726deeec
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg398680(v=OCS.15)
ms:contentKeyID: 49304274
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Lync Server 2013에서 DNS SRV 레코드 만들기 및 확인

 

_**마지막으로 수정된 항목:** 2013-02-21_

이 절차를 성공적으로 완료하려면 서버 또는 도메인에 최소한 Domain Admins 그룹의 구성원 또는 DnsAdmins 그룹의 구성원으로 로그온해야 합니다.

이 항목에서는 Lync Server 2013 배포에서 만드는 데 필요한 DNS(Domain Name System) 레코드 및 자동 클라이언트 로그인에 필요한 DNS(Domain Name System) 레코드를 구성하는 방법에 대해 설명합니다. 프런트 엔드 풀을 만들 때 설치 프로그램에서는 Active Directory 개체 및 풀 FQDN(정규화된 도메인 이름)을 비롯한 풀에 대한 설정을 만듭니다. 유사한 개체 및 설정이 Standard Edition 서버에 대해서도 만들어집니다. 클라이언트가 풀 또는 Standard Edition 서버에 연결하기 위해서는 풀 또는 Standard Edition 서버의 FQDN이 DNS에 등록되어 있어야 합니다. 모든 SIP 도메인에 대해 내부 DNS에 DNS SRV 레코드를 만들어야 합니다. 이 절차에서는 내부 DNS에 SIP 사용자 도메인의 영역이 있다고 가정합니다.

## DNS SRV 레코드를 구성하려면

1.  DNS 서버에서 **시작** , **관리 도구** 를 차례로 클릭한 다음 **DNS** 를 클릭합니다.

2.  SIP 도메인의 콘솔 트리에서 **정방향 조회 영역** 을 확장하고 Lync Server 2013을 설치할 SIP 도메인을 선택합니다.

3.  **다른 새 레코드** 를 클릭합니다.

4.  **리소스 레코드 종류 선택** 에서 **서비스 위치(SRV)** 를 클릭한 다음 **레코드 만들기** 를 클릭합니다.

5.  **서비스** 를 클릭한 다음 **\_sipinternaltls** 를 입력합니다.

6.  **프로토콜** 을 클릭한 다음 **\_tcp** 를 입력합니다.

7.  **포트 번호** 를 클릭한 다음 **5061** 을 입력합니다.

8.  **이 서비스를 제공하는 호스트** 를 클릭한 다음 풀 또는 Standard Edition 서버의 FQDN을 입력합니다.

9.  **확인** 을 클릭한 다음 **완료** 를 클릭합니다.

## DNS SRV 레코드의 생성을 확인하려면

1.  Authenticated Users 그룹의 구성원이거나 이와 동일한 권한을 가진 계정을 사용하여 도메인의 클라이언트 컴퓨터에 로그온합니다.

2.  **시작** 을 클릭한 다음 **실행** 을 클릭합니다.

3.  **열기** 상자에 **cmd** 를 입력한 다음 **확인** 을 클릭합니다.

4.  명령 프롬프트에서 **nslookup** 을 입력한 다음 Enter 키를 누릅니다.

5.  **set type=srv** 를 입력한 다음 Enter 키를 누릅니다.

6.  **\_sipinternaltls.\_tcp.contoso.com** 을 입력한 다음 Enter 키를 누릅니다. TLS(전송 계층 보안) 레코드에 대해 표시되는 결과는 다음과 같습니다.
    
    Server: *\<DNS 서버\>* .contoso.com
    
    Address: *\<DNS 서버의 IP 주소\>*
    
    Non-authoritative answer:
    
    \_sipinternaltls.\_tcp.contoso.com SRV service location:
    
    priority = 0
    
    weight = 0
    
    port = 5061
    
    svr hostname = poolname.contoso.com(또는 Standard Edition 서버 A 레코드)
    
    poolname.contoso.com internet address = *\<부하 분산 장치의 가상 IP 주소\>* 또는 *\<Enterprise Edition 서버가 하나만 있는 풀에 대한 단일 Enterprise Edition 서버의 IP 주소\>* 또는 *\<Standard Edition 서버의 IP 주소\>*

7.  작업이 끝나면 명령 프롬프트에서 **exit** 를 입력한 다음 Enter 키를 누릅니다.

## 프런트 엔드 풀 또는 Standard Edition Server의 FQDN을 확인할 수 있는지 확인하려면

1.  도메인의 클라이언트 컴퓨터에 로그온합니다.

2.  **시작** 을 클릭한 다음 **실행** 을 클릭합니다.

3.  **열기** 상자에 **cmd** 를 입력한 다음 **확인** 을 클릭합니다.

4.  명령 프롬프트에서 **nslookup** *\<프런트 엔드 풀의 FQDN\>* 또는 *\<Standard Edition Server의 FQDN\>* 을 입력한 다음 Enter 키를 누릅니다.

5.  FQDN에 대해 적절한 IP 주소로 확인되는 응답이 수신되는지 점검합니다.

