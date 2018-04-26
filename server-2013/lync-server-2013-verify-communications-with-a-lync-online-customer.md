---
title: Lync Online 고객과의 통신 확인
TOCTitle: Lync Online 고객과의 통신 확인
ms:assetid: c8287b15-e1bb-4b26-8354-0ec90b2fcfe7
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Hh202189(v=OCS.15)
ms:contentKeyID: 49305005
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Lync Online 고객과의 통신 확인

 

_**마지막으로 수정된 항목:** 2012-10-08_

조직 내 Lync 사용자가 Microsoft Lync Online 2010 고객의 사용자와 통신할 수 있도록 하려면 다음 단계가 완료되어야 합니다.

  - 모든 필수 구성 요소가 충족되었습니다. 여기에는 내부 및 에지 서버 배포, 조직의 페더레이션 지원 설정 및 사용자 계정 설정이 포함됩니다. 자세한 내용은 [Lync Online 고객과의 페더레이션을 위한 필수 구성 요소](lync-server-2013-prerequisites-for-federating-with-a-lync-online-customer.md)를 참조하십시오.

  - 내부 배포에서 도메인 액세스 지원을 구성했습니다. 여기에는 호스트 공급자 항목을 작성하고 Lync Online 고객의 도메인으로부터 액세스를 허용하도록 배포를 구성하는 작업이 포함됩니다. 자세한 내용은 [Lync Online 도메인에 대한 페더레이션 지원 구성](lync-server-2013-configure-federation-support-for-a-lync-online-domain.md)을 참조하십시오.

  - 페더레이션을 지원하도록 사용자 계정을 구성했습니다. 자세한 내용은 [Lync Online 고객과의 페더레이션을 위한 사용자 액세스 구성](lync-server-2013-configure-user-access-for-federation-with-a-lync-online-customer.md)을 참조하십시오.

이러한 모든 단계를 완료하고 Lync Online 2010 고객의 관리자가 조직 내 페더레이션 지원을 위해 온라인 서비스 구성을 모두 마친 후에는 조직 내 내부 사용자와 Lync Online 고객의 사용자 간의 통신을 테스트하여 통신이 되는지 확인합니다. 통신이 성공적이지 않으면 에지 서버에서 로깅 도구를 사용하여 로그 및 추적 파일을 캡처하여 문제를 해결합니다. 로깅 도구 사용에 대한 자세한 내용은 작업 설명서에서 [Lync Server 관리 도구 열기](lync-server-2013-open-lync-server-administrative-tools.md)를 참조하십시오. 로깅 도구에 대한 자세한 내용은 TechNet 라이브러리의 Lync Server 2010 로깅 도구 설명서 [http://go.microsoft.com/fwlink/?linkid=199265\&clcid=0x412](http://go.microsoft.com/fwlink/?linkid=199265%26clcid=0x412)()를 참조하십시오.

