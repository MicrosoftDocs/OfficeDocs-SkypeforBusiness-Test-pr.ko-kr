---
title: Lync Server 2013 인증서 인프라 요구 사항
TOCTitle: 인증서 인프라 요구 사항
ms:assetid: 0051aa23-0bbe-4e72-9f29-e01c6bcc6190
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg398066(v=OCS.15)
ms:contentKeyID: 49302603
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Lync Server 2013에 대한 인증서 인프라 요구 사항

 

_**마지막으로 수정된 항목:** 2013-03-22_

Lync Server 2013에서는 TLS 및 MTLS(Mutual TLS) 연결을 지원하는 데 PKI(공개 키 인프라)가 필요합니다.

Lync Server에서는 인증서가 다음과 같은 용도로 사용됩니다.

  - 클라이언트와 서버 간의 TLS 연결

  - 서버 간의 MTLS 연결

  - 파트너의 자동 DNS 검색을 사용한 페더레이션

  - IM(메신저 대화)에 대한 원격 사용자 액세스

  - A/V(오디오/비디오) 세션, 응용 프로그램 공유 및 웹 회의에 대한 외부 사용자 액세스

  - 웹 서비스 자동 검색을 사용하는 모바일 요청

Lync Server의 경우에는 다음의 일반 요구 사항이 적용됩니다.

  - 모든 서버 인증서는 서버 권한 부여(서버 EKU)를 지원해야 합니다.

  - 모든 서버 인증서에는 CDP(CRL 배포 지점)가 포함되어 있어야 합니다.

  - 모든 인증서는 운영 체제에서 지원하는 서명 알고리즘을 사용하여 서명해야 합니다. Lync Server 2013에서는 SHA-1 및 SHA-2의 다이제스트 크기 모음(224, 256, 384 및 512비트)을 지원하며, 운영 체제 요구 사항을 충족하거나 초과합니다. 운영 체제 지원은 [http://go.microsoft.com/fwlink/?LinkId=287002](http://go.microsoft.com/fwlink/?linkid=287002)를 참고하세요.

  - Lync Server를 실행하는 내부 서버에 대해 자동 등록이 지원됩니다.

  - Lync Server 에지 서버에 대해서는 자동 등록이 지원되지 않습니다.

  - Windows Server 2003 CA로 웹 기반 인증서 요청을 전송할 때는 Windows Server 2003 SP2 또는 Windows XP를 실행하는 컴퓨터에서 요청을 전송해야 합니다.
    
    KB 922706에서는 Windows Server 2003 인증서 서비스 웹 등록에 대해 웹 인증서를 등록할 때 발생하는 문제를 해결하기 위한 지원 정보가 제공되지만, Windows Server 2008, Windows Vista 또는 Windows 7을 사용하여 Windows Server 2003 CA에서 인증서를 요청할 수는 없습니다.

  - 1024, 2048 및 4096의 암호화 키 길이가 지원됩니다. 2048 이상의 키 길이를 사용하는 것이 좋습니다.

  - 기본 다이제스트 또는 해시 서명의 경우 알고리즘은 RSA입니다. ECDH\_P256, ECDH\_P384 및 ECDH\_P521 해시 알고리즘도 지원됩니다.

## 이 단원의 내용

  - [Lync Server 2013의 내부 서버에 대한 인증서 요구 사항](lync-server-2013-certificate-requirements-for-internal-servers.md)

  - [Lync Server 2013의 외부 사용자 액세스에 대한 인증서 요구 사항](lync-server-2013-certificate-requirements-for-external-user-access.md)

  - [Lync Server 2013의 영구 채팅 서버에 대한 인증서 요구 사항](lync-server-2013-certificate-requirements-for-persistent-chat-server.md)

  - [Lync Server 2013의 모바일 기능에 대한 인증서 요구 사항](lync-server-2013-certificate-requirements-for-mobility.md)

