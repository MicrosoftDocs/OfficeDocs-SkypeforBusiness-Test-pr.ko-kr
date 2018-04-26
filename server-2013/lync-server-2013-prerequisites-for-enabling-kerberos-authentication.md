---
title: 'Lync Server 2013: Kerberos 인증을 사용하기 위한 필수 구성 요소'
TOCTitle: Kerberos 인증을 사용하기 위한 필수 구성 요소
ms:assetid: 3f276a21-7476-4bc0-9fd1-59e844d2e9c1
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg425909(v=OCS.15)
ms:contentKeyID: 49303413
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Lync Server 2013의 Kerberos 인증을 사용하기 위한 필수 구성 요소

 

_**마지막으로 수정된 항목:** 2013-02-21_

Kerberos 인증을 사용하도록 설정하기 전에 모든 필수 구성 및 인프라 준비가 완료되었는지 확인하세요.

  - Active Directory 스키마가 Lync Server 2013용으로 확장되어 있습니다.

  - Lync Server 2013에 대한 Active Directory 포리스트 준비가 완료되었습니다.

  - Lync Server 2013에 대한 Active Directory 도메인 준비가 완료되었습니다.

  - 중앙 관리 저장소가 설치되었으며 사용할 수 있습니다.

  - 토폴로지 작성기를 사용하여 토폴로지를 만들고 게시했습니다.

  - 프런트 엔드 서버, Standard Edition 서버 및 디렉터를 비롯하여 웹 서비스를 필요로 하는 서버와 역할이 정의되고 배포되었습니다.

  - IIS(인터넷 정보 서비스)가 Lync Server 2013에서 웹 서비스를 지원하기 위한 권장 역할 서비스를 사용하여 구성되고 배포되었습니다.

필수 구성 요소가 충족되면 배포에 대해 Kerberos 인증에 사용할 웹 서비스용 계정을 하나 이상 만들 수 있도록 준비해야 합니다. 최소한 각 배포에 대해 Kerberos 인증 계정 하나를 만들어야 합니다. 그러나 각 사이트에 대해 계정을 만들어 사이트에서 로컬 Kerberos 인증을 제공할 수 있습니다. Kerberos 인증 계정은 사이트당 하나만 지정할 수 있습니다.

