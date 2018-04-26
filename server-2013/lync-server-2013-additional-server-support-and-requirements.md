---
title: 'Lync Server 2013: 추가 서버 지원 및 요구 사항'
TOCTitle: 추가 서버 지원 및 요구 사항
ms:assetid: 7622986b-abd6-4f45-8b5b-d5e2368521e8
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg398577(v=OCS.15)
ms:contentKeyID: 49304071
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Lync Server 2013의 추가 서버 지원 및 요구 사항

 

_**마지막으로 수정된 항목:** 2013-12-09_

이 지원 가능성 설명서의 다른 섹션에 설명된 소프트웨어 지원 외에 Lync Server 2013에는 다음과 같은 지원 제한 사항이 있습니다.

  - Lync Server 2013에서는 특정 서버 역할에 대해 DNS(Domain Name System) 및 하드웨어 부하 분산을 지원합니다. 또한 중재 서버에 대해 응용 프로그램 부하 분산을 지원합니다(해당되는 경우). 각 부하 분산을 사용하는 경우에 대한 자세한 내용은 계획 설명서를 참고하세요.

  - Lync Server 2013에서는 DLX(Distribution List Expansion Protocol)를 사용하여 메일 그룹을 확장합니다. 이 프로토콜은 메일 그룹의 구성원 자격을 가져오는 데 사용되는 웹 서비스 메서드를 지정합니다. Microsoft Exchange Server에서는 정적으로 지정된 구성원이 없는 동적 그룹을 지원합니다. 대신, 그룹이 확장될 때 평가된 쿼리를 저장합니다. DLX는 동적 메일 그룹을 지원하지 않습니다.

  - 사용자 사용 마법사는 영어가 아닌 문자의 SIP 호환 URI로의 자동 변환을 지원하지 않으므로 SIP 주소를 수동으로 수정해야 합니다.

  - 바이러스 방지 소프트웨어를 실행하는 서버의 경우, [Lync Server 2013을 위한 바이러스 백신 검사 제외](lync-server-2013-antivirus-scanning-exclusions.md)에서 권장하는 바이러스 제외 및 기타 보안 관련 권장 사항을 참고하세요.

  - IPsec를 사용하는 경우 오디오 및 비디오 트래픽에 사용되는 포트 범위에서 IPSec를 사용하지 않는 것이 좋습니다. 자세한 내용은 계획 설명서에서 [Lync Server 2013의 IPsec 예외](lync-server-2013-ipsec-exceptions.md)를 참고하세요.

  - 조직에서 QoS(서비스 품질) 인프라를 사용하는 경우 미디어 하위 시스템은 이러한 기존 인프라 내에서 작동하도록 설계됩니다. QoS 구현에 대한 자세한 내용은 작업 설명서에서 [Lync Server 2013에서 QoS(서비스 품질) 관리](lync-server-2013-managing-quality-of-service-qos.md)을 참고하세요.

  - 운영 체제 방화벽 사용이 지원됩니다. Lync Server 2013에서는 Microsoft SQL Server 데이터베이스 소프트웨어를 제외하고 운영 체제 방화벽에 대한 방화벽 예외를 관리합니다. SQL Server 방화벽 요구 사항에 대한 자세한 내용은 SQL Server 설명서를 참고하세요.

  - 외부 사용자 액세스에 대한 지원을 구현하는 데 사용되는 외부 인터페이스는 내부 인터페이스와 같은 네트워크가 *아니라* 별도의 서브넷에 있어야 합니다.

  - Lync Server 2013의 XMPP 기능은 Microsoft에서 Google Talk와의 메신저 페더레이션에 대해 지원 및 테스트합니다. 다른 모든 XMPP 시스템의 경우 타사 공급업체에 문의하여 Lync Server 2013과의 페더레이션 지원 여부, 배포 또는 문제 해결 권장 사항에 대해 알아보십시오.

  - Lync Server 2013 누적 업데이트: 2013년 7월이 출시되면서 Lync Server 2013는 이제 2단계 인증을 지원합니다. 자세한 내용은 [Lync Server 2013의 2단계 인증](lync-server-2013-planning-for-and-deploying-two-factor-authentication.md)을 참고하세요.

  - 대부분의 내부 서버에는 **OAuth(Open Authentication)**로 정의된 인증서 유형이 필요합니다. Lync Server 배포 마법사의 **인증서 요청, 설치 및 지정** 단계 중에 OAuth 인증서를 요청하고 지정해야 합니다. OAuth 인증서 키의 최소 크기는 1024비트입니다. 키 길이가 2048비트보다 작은 인증서를 요청할 경우 경고가 표시될 수 있습니다. 2048 키 길이를 적용할 때 경고가 표시되지 않고 잠재적인 문제가 발생하지 않도록 방지하려면 OAuth 인증서에 대해 항상 키 길이를 2048로 사용하는 것이 좋습니다.

  - Lync Server 2013 및 Microsoft Exchange Server 2010 SP1(서비스 팩 1)은 Windows Server 2008 R2 운영 체제가 시스템 암호화에 FIPS(Federal Information Processing Standard) 140-2 알고리즘을 사용하도록 구성된 경우 FIPS 140-2 알고리즘을 지원하도록 작동합니다. FIPS 지원을 구현하려면 이를 지원하도록 Lync Server 2013을 실행하는 각 서버를 구성해야 합니다. FIPS 호환 알고리즘 및 FIPS 지원 구현 방법에 대한 자세한 내용은 Microsoft 기술 자료 문서 811833, "Windows XP 이상 버전에서 "시스템 암호화: 암호화, 해시, 서명에 FIPS 호환 알고리즘 사용" 보안 설정을 사용할 수 있도록 설정할 때의 영향"( <http://support.microsoft.com/kb/811833>)을 참고하세요. Exchange 2010의 FIPS 140-2 지원 및 제한에 대한 자세한 내용은 "Exchange 2010 SP1 및 FIPS 호환 알고리즘 지원" <http://go.microsoft.com/fwlink/?linkid=205335>)을 참고하세요.

Lync Server 2013을 사용하려면 배포하기 전 또는 배포하는 중에 특정 구성 요소에 다른 소프트웨어를 설치해야 합니다. 여기에는 운영 체제에서 사용되는 소프트웨어, 다운로드 가능 소프트웨어 및 Lync Server 2013 설치 중에 자동으로 설치되는 소프트웨어가 포함됩니다. 필요할 수 있는 추가 소프트웨어 목록은 다음과 같습니다.

  - Windows 업데이트

  - Windows Identity Foundation

  - Microsoft .NET 4.5 Framework

  - Microsoft Visual C++ 2012 재배포 가능 패키지
    

    > [!NOTE]
    > Microsoft Visual C++ 2012 재배포 가능 패키지는 Lync Server 2013을 설치할 때 자동으로 설치됩니다. 다른 버전은 설치 및 사용하지 않아야 합니다.



  - URL 재작성 모듈 버전 2.0 재배포 가능 패키지

  - Windows Media 형식 런타임

  - Windows PowerShell 버전 3.0

  - Microsoft Silverlight 4 브라우저 플러그 인(Lync Server 제어판의 경우 Silverlight 4.0.50524.0 또는 최신 버전)

  - Active Directory 도메인 서비스 도구

이러한 소프트웨어 요구 사항 중 일부는 특정 서버 역할 또는 구성 요소에만 적용됩니다. 이러한 소프트웨어 요구 사항에 대한 자세한 내용은 계획 설명서에서 [Lync Server 2013에 대한 추가 소프트웨어 요구 사항](lync-server-2013-additional-software-requirements.md)을 참고하세요.

