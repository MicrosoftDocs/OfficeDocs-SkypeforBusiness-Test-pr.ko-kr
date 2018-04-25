---
title: 'Lync Server 2013: 역방향 프록시를 통해 액세스 확인'
TOCTitle: 역방향 프록시를 통해 액세스 확인
ms:assetid: 3076a786-e022-4d41-91ec-1bf252b2a468
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg429697(v=OCS.15)
ms:contentKeyID: 49303209
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Lync Server 2013에서 역방향 프록시를 통해 액세스 확인

 

_**마지막으로 수정된 항목:** 2013-03-29_

다음 절차를 수행하여 사용자가 역방향 프록시에 대한 정보에 액세스할 수 있는지 확인합니다. 액세스가 제대로 작동하려면 먼저 방화벽 구성과 DNS(Domain Name System) 구성을 완료해야 할 수도 있습니다.

## 인터넷을 통해 웹 사이트에 액세스할 수 있는지 확인하려면

  - 웹 브라우저를 열고 **주소** 표시줄에 클라이언트에서 웹 회의용 주소록 파일과 웹 사이트에 액세스하는 데 사용하는 URL을 다음과 같이 입력합니다.
    
      - 주소록 서버의 경우 **https:// *외부 웹 팜 FQDN* /abs**와 같은 URL을 입력하며, 여기서 *외부 웹 팜 FQDN* 은 주소록 서비스를 호스팅하는 외부 웹 서비스의 외부 FQDN입니다. 기본적으로 주소록 서버 폴더의 디렉터리 보안은 Windows 인증으로 구성되므로 사용자는 HTTP 챌린지를 받아야 합니다.
    
      - 회의의 경우 **https:// *외부 웹 팜 FQDN* /meet**와 같은 URL을 입력하며, 여기서 *외부 웹 팜 FQDN* 은 모임 콘텐츠를 호스팅하는 웹 팜의 외부 FQDN입니다. 이 URL은 회의에 대한 문제 해결 페이지를 표시해야 합니다. 또는 회의용 단순 URL이 올바르게 작동하는지 확인하세요. 전화 회의 참가를 위한 단순 URL의 예는 https://meet.contoso.com과 같습니다.
    
      - 메일 그룹 확장의 경우 **https:// *외부 웹 팜 FQDN* /GroupExpansion/service.svc**와 유사한 URL을 입력합니다. 기본적으로 메일 그룹 확장 서비스의 디렉터리 보안은 Windows 인증으로 구성되므로 사용자는 HTTP 챌린지를 받아야 합니다.
    
      - 전화 접속의 경우 **https:// *외부 웹 팜 FQDN* /dialin**과 같은 단순 URL을 입력하며, 여기서 *외부 웹 팜 FQDN* 은 전화 접속 회의용 전화 접속 페이지를 호스팅하는 웹 팜의 외부 FQDN입니다. 사용자는 전화 접속 페이지로 이동되어야 합니다. 또는 단순 URL 전화 접속 기능이 올바르게 작동하는지 확인하세요. 전화 접속용 단순 URL의 예는 https://dialin.contoso.com과 같습니다.
    
      - 자동 검색 URL이 작동하는지 확인하려면 https://lyncdiscover를 입력합니다. *externaldomainFQDN* . 그러면 브라우저에 파일을 열라는 메시지가 표시됩니다. 메모장을 선택해 파일을 엽니다. 일반적인 응답은 다음과 비슷합니다.
        
            {"AccessLocation":"External","Root":{"Links":[{"href":"https:\/\/extweb.contoso.com\/Autodiscover\/AutodiscoverService.svc\/root\/domain","token":"Domain"},
            {"href":"https:\/\/extweb.contoso.com\/Autodiscover\/AutodiscoverService.svc\/root\/user","token":"User"},
            {"href":"https:\/\/lyncweb.contoso.com\/Autodiscover\/AutodiscoverService.svc\/root\/oauth\/user","token":"OAuth"}]}}

