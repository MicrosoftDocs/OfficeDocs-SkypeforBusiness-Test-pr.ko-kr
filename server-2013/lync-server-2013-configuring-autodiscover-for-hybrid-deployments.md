---
title: 하이브리드 배포용 자동 검색 구성
TOCTitle: 하이브리드 배포용 자동 검색 구성
ms:assetid: ca605e62-181c-42ca-80a1-e37e610f8277
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/JJ945653(v=OCS.15)
ms:contentKeyID: 52056941
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# 하이브리드 배포용 자동 검색 구성

 

_**마지막으로 수정된 항목:** 2012-12-12_

하이브리드 배포는 Microsoft Lync Online 클라우드 서비스와 온 프레미스 배포를 둘 다 사용하는 구성입니다. 이러한 유형의 구성에서 자동 검색 서비스는 사용자의 실제 위치를 찾을 수 있어야 합니다. 자동 검색은 온 프레미스 배포에 있는지 비즈니스용 Skype Online 배포에 있는지에 관계없이 사용자 계정과 사용자 계정을 호스트하는 서버의 위치를 찾는 데 도움이 됩니다.

예를 들어 사용자 계정이 비즈니스용 Skype Online의 서버에서 호스트되는 경우 *검색 성능*이라는 프로세스에서 다음과 같이 사용자 위치를 찾으려고 합니다.

  - 사용자가 **contoso.com**이라는 온 프레미스 배포와의 연결 시도를 시작합니다.

  - 시도가 자동 검색 서비스와 연결된 DNS 이름인 lyncdiscover.contoso.com으로 전송됩니다.

  - 자동 검색은 contoso.com 온 프레미스 배포에서 가정된 고급 등록자 풀을 참조하며 비즈니스용 Skype Online에서 호스트된 사용자의 실제 홈 서버의 정보가 자동 검색에 제공됩니다. 그러면 자동 검색에서 사용자에게 **lync.com** 온라인 자동 검색 서비스 조회를 전송합니다.

  - 사용자가 lync.com 온라인 자동 검색 서비스와의 연결 시도를 시작하고 사용자의 계정과 사용자의 홈 서버를 찾을 수 있습니다.

클라이언트에서 사용자 홈 서버가 있는 배포를 찾을 수 있도록 하려면 새로운 URL(Uniform Resource Locator)로 자동 검색 서비스를 구성해야 합니다. 다음을 수행하여 자동 검색 서비스를 구성합니다.

## 하이브리드 배포용 자동 검색 구성

1.  [Lync Server 2013에 대한 자동 검색 서비스 요구 사항](lync-server-2013-autodiscover-service-requirements.md) 항목에서 Get-CsHostingProvider를 사용하여 ProxyFQDN 특성의 값을 검색할 수 있습니다.

2.  Lync Server 관리 셸에서 다음을 입력합니다.
    
        Set-CsHostingProvider -Identity [identity] -AutodiscoverUrl https://webdir.online.lync.com/autodiscover/autodisccoverservice.svc/root
    
    여기서 \[identity\]는 공유 SIP 주소 공간의 도메인 이름으로 대체됩니다.

## 참고 항목

#### 기타 리소스

[Get-CsHostingProvider](https://docs.microsoft.com/en-us/powershell/module/skype/Get-CsHostingProvider)  
[Set-CsHostingProvider](https://docs.microsoft.com/en-us/powershell/module/skype/Set-CsHostingProvider)

