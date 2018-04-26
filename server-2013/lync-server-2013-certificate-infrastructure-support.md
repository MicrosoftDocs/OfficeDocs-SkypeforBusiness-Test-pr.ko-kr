---
title: Lync Server 2013 인증서 인프라 지원
TOCTitle: 인증서 인프라 지원
ms:assetid: 47aa5c95-eb60-4d4b-81d5-7fdaef1a1145
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg425950(v=OCS.15)
ms:contentKeyID: 49303506
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Lync Server 2013의 인증서 인프라 지원

 

_**마지막으로 수정된 항목:** 2013-11-07_

Lync Server 2013에는 TLS(전송 계층 보안) 및 MTLS(상호 TLS)를 지원하기 위해 PKI(공개 키 인프라)가 필요합니다. 기본적으로 Lync Server 2013은 클라이언트-서버 연결에 대해 TLS를 사용하도록 구성됩니다. 서버 간 연결에는 MTLS가 사용됩니다.

Lync Server 2013에 대해 신뢰할 수 있는 CA(인증 기관)에서 MTLS 인증서를 발급해야 합니다. Lync Server에서는 다음과 같은 CA에서 발급한 인증서를 지원합니다.

  - 내부 CA에서 발급한 인증서:
    
      - Windows Server 2003 운영 체제 CA
    
      - Windows Server 2008 운영 체제 CA
    
      - Windows Server 2008 R2 운영 체제 CA
    
      - Windows Server 2012 운영 체제 CA
    
      - Windows Server 2012 R2 운영 체제 CA

  - 공용 CA에서 발급한 인증서

Exchange 2013 등의 다른 응용 프로그램 및 서버와 통신하려면 다른 응용 프로그램 및 제품에 의해 지원되는 인증서가 필요합니다. 2013 릴리스의 경우 Lync Server 2013 및 기타 Microsoft 서버 제품( Exchange 2013 및 SharePoint Server 포함)은 서버 간 인증 및 권한 부여에 대해 OAuth(Open Authorization) 프로토콜을 지원합니다. 자세한 내용은 배포 설명서 또는 작업 설명서의 [Lync Server 2013에서 서버 간 인증(Oauth) 및 파트너 응용 프로그램 관리](lync-server-2013-managing-server-to-server-authentication-oauth-and-partner-applications.md)를 참고하세요.

Windows 7 운영 체제, Windows Server 2008 R2 운영 체제, Microsoft Office Communicator 2007 Phone Edition 실행 클라이언트에서 연결할 수 있도록 Lync Server 2013에는 SHA-256 암호화 해시 기능을 사용하여 서명된 인증서에 대한 지원(하지만 요구하지는 않음)이 포함됩니다. SHA-256을 사용한 외부 액세스를 지원하기 위해 외부 인증서는 SHA-256을 사용하는 공용 CA에서 발급됩니다.

인증서 요구 사항에 대한 자세한 내용은 계획 설명서에서 [Lync Server 2013에 대한 인증서 인프라 요구 사항](lync-server-2013-certificate-infrastructure-requirements.md)을 참조하십시오. 인증서에서 와일드카드 사용에 대한 자세한 내용은 지원 가능성 설명서에서 [Lync Server 2013의 와일드카드 인증서 지원](lync-server-2013-wildcard-certificate-support.md)을 참조하십시오.

