---
title: 하이브리드 및 분할 도메인 - 자동 검색
TOCTitle: 하이브리드 및 분할 도메인 - 자동 검색
ms:assetid: c855bcc5-b656-4d2d-92d6-f016f2797d3a
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/JJ945652(v=OCS.15)
ms:contentKeyID: 52056958
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# 하이브리드 및 분할 도메인 - 자동 검색

 

_**마지막으로 수정된 항목:** 2013-02-14_

*분할 도메인* 배포 또는 *하이브리드* 배포라고도 하는 공유 SIP 주소 공간은 사용자가 온-프레미스 배포 및 온라인 환경 전체에 배포되는 구성입니다. 이 경우 적절한 결과는 홈 서버의 위치(온-프레미스 또는 온라인)에 관계없이 사용자가 배포로 로그인하면 홈 서버 위치로 리디렉션되도록 하는 것입니다. 이를 가능하게 하기 위해 Lync Server 2013의 자동 검색 기능을 사용하여 온라인 사용자를 온라인 토폴로지로 리디렉션합니다. 이 작업은 Lync Server 관리 셸, **Get-CsHostingProvider** cmdlet 및 **Set-CsHostingProvider** cmdlet을 사용하여 자동 검색 URL(Uniform Resource Locator)을 구성하는 방법으로 수행할 수 있습니다.

## 분할 도메인 배포의 모바일 기능

수집 및 기록해야 하는 배포된 특성은 다음과 같습니다.

  - Lync Server 관리 셸에서 다음을 입력합니다.
    
        Get-CsHostingProvider

  - 결과에서 **ProxyFQDN** 특성이 포함된 온라인 공급자를 찾습니다. 예를 들면 sipfed.online.lync.com과 같습니다.

  - ProxyFQDN의 값을 기록합니다.

  - 온-프레미스 Lync Server 제어판에서 페더레이션을 사용하도록 설정하여 온라인 공급자와의 페더레이션을 허용합니다.

  - 온라인 공급자에 대한 페더레이션을 사용하도록 설정합니다. 기본적으로 모든 온라인 사용자는 도메인 페더레이션에 대해 사용하도록 설정되며 모든 도메인과 통신할 수 있습니다.

  - 차단 도메인 및 허용 도메인을 정의하려는 경우 명시적으로 허용하거나 차단할 도메인을 결정합니다.

  - 온라인 페더레이션의 경우 방화벽 예외, 인증서 및 DNS 호스트(A 또는 IPv6 사용 시 AAAA) 레코드를 계획해야 합니다. 또한 페더레이션 정책도 구성해야 합니다. 자세한 내용은 [Lync Server 및 Office Communications Server 페더레이션 계획](lync-server-2013-planning-for-lync-server-and-office-communications-server-federation.md)을 참조하십시오.

