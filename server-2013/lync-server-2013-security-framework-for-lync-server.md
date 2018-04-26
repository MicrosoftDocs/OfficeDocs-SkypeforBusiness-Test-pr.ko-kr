---
title: Lync Server 2013용 보안 프레임워크
TOCTitle: Lync Server 2013용 보안 프레임워크
ms:assetid: 01131e28-b38e-40d9-8524-06725b9c6608
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Dn481316(v=OCS.15)
ms:contentKeyID: 59682886
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Lync Server 2013용 보안 프레임워크

 

_**마지막으로 수정된 항목:** 2013-11-08_

이 섹션에서는 Microsoft Lync Server 2013의 보안 프레임워크를 형성하는 기본 요소에 대한 개요를 제공합니다. 특정 Lync Server 2013 배포의 보안과 관련하여 올바른 결정을 내리려면 이러한 요소가 함께 작용하는 방식을 이해하는 것이 필수적입니다.

해당 요소는 다음과 같습니다.

  - AD DS(Active Directory 도메인 서비스)에서는 사용자 계정 및 네트워크 리소스에 대해 신뢰할 수 있는 단일 백 엔드 저장소를 제공합니다.

  - RBAC(역할 기반 액세스 제어)를 사용하면 높은 보안 표준을 유지하면서 관리 작업을 위임할 수 있습니다.

  - PKI(공개 키 인프라)는 CA(인증 기관)에서 발급한 인증서를 사용하여 서버를 인증하고 데이터 무결성을 보장합니다.

  - TLS(전송 계층 보안), HTTPS(SSL을 통한 HTTPS), MTLS(상호 TLS)를 사용하여 끝점 인증 및 메신저 대화 암호화를 수행할 수 있습니다. SRTP(Secure Real-Time Transport Protocol)를 통해 지점 간 오디오, 비디오, 응용 프로그램 공유 스트림이 암호화됩니다.

  - 가능한 경우 사용자 인증에 산업 표준 프로토콜을 사용할 수 있습니다.

  - Windows PowerShell에서는 보안 기능이 기본적으로 설정되어 있기 때문에 사용자가 모르는 상태에서 부주의하게 스크립트를 실행할 수 없습니다.

이러한 기본 보안 요소가 함께 작용하여 트러스트된 사용자, 서버, 연결, 작업이 정의되기 때문에 Lync Server 2013의 보안 토대가 확립됩니다.

## 이 단원의 내용

이 섹션의 항목에서는 이러한 각각의 기본 요소가 작용하여 Lync Server 인프라의 보안을 향상시키는 방식에 대해 설명합니다.

  - [Lync Server 2013용 Active Directory 도메인 서비스](lync-server-2013-active-directory-domain-services-for-lync-server.md)

  - [Lync Server 2013용 RBAC(역할 기반 액세스 제어)](lync-server-2013-role-based-access-control-rbac.md)

  - [Lync Server 2013용 공개 키 인프라](lync-server-2013-public-key-infrastructure.md)

  - [Lync Server 2013용 TLS 및 MTLS](lync-server-2013-tls-and-mtls.md)

  - [Lync Server 2013의 암호화](lync-server-2013-encryption.md)

  - [Lync Server 2013의 사용자 및 클라이언트 인증](lync-server-2013-user-and-client-authentication.md)

  - [Windows PowerShell 및 Lync Server 2013 관리 도구](lync-server-2013-windows-powershell-and-lync-server-management-tools.md)

