---
title: Lync 연결 분석기 사용
TOCTitle: Lync 연결 분석기 사용
ms:assetid: 954953fb-0c7a-4fd5-8acd-68ecb59b20af
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/JJ907302(v=OCS.15)
ms:contentKeyID: 52056894
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Lync 연결 분석기 사용

 

_**마지막으로 수정된 항목:** 2014-02-11_

Lync 관리자는 Microsoft Lync 연결 분석기를 사용하여 Office 365 또는 온-프레미스 Lync Server 환경의 배포 및 구성이 모바일 장치의 Lync Windows 스토어 앱 및 Lync 앱으로부터의 연결을 지원하기 위한 요구 사항을 충족하는지 여부를 확인할 수 있습니다.

Lync 연결 분석기는 Lync Windows 스토어 앱 및 Lync 모바일 앱에서 사용하는 것과 같은 서비스 및 프로토콜을 사용하여 Lync Server 온-프레미스 또는 비즈니스용 Skype Online으로 연결을 시도합니다. Lync Server 또는 비즈니스용 Skype Online에 연결하는 외부 네트워크 또는 내부 네트워크를 통해 연결 테스트를 수행할 수 있습니다. Lync 연결 분석기는 각 연결 단계에 대한 자세한 정보가 포함된 보고서를 제공하므로 구성 유효성을 확인하고 연결 문제를 해결할 수 있습니다.

Lync 연결 분석기가 테스트하는 Lync Server 구성 요소는 다음과 같습니다.

  - 자동 검색 서비스

  - 인증 브로커(Reach) 서비스

  - Mobility(MCX) Service

  - Mobility(UCWA) service

  - 웹 티켓 서비스

또한 Lync 연결 분석기는 다음과 같은 기타 구성 요소의 구성도 테스트합니다.

  - 자동 검색 URL에 대한 DNS 레코드 게시

  - 인증서

  - 프록시 서버

Lync 연결 분석기는 Microsoft 다운로드 센터(<http://go.microsoft.com/fwlink/?linkid=277056>)에서 다운로드할 수 있습니다.

## 연결을 분석하려면

1.  도구에서 연결을 테스트하는 데 사용할 유효한 Lync 계정(온-프레미스 Lync 계정 또는 Office 365Lync 계정)의 자격 증명을 입력합니다.
    
      - **Lync Account Type(Lync 계정 유형)** 에서 **Office 365** 또는 **On-Premises(온-프레미스)** 를 선택합니다.
    
      - **SIP URI** 에 Lync 연결의 SIP 로그인 주소를 **사용자@도메인.com** 형식으로 입력합니다.
    
      - **Password(암호)** 에 해당 계정과 연결된 암호를 입력합니다.
    
      - 해당하는 경우 **User name (optional)(사용자 이름(옵션))** 에 사용자 이름을 입력합니다. 사용자 이름은 UPN(사용자 계정 이름)이라고도 합니다. 사용자 이름과 SIP URI가 같은 경우 사용자 이름을 입력하지 않아도 됩니다. 두 항목이 다른 경우에는 **사용자@도메인.com** 또는 **도메인\\사용자** 중 적절한 형식으로 사용자 이름을 입력합니다.
    
      - 내부 네트워크에 연결된 컴퓨터에서 Lync 연결 분석기를 실행하는 경우 **Network access(네트워크 액세스)** 에서 **From inside my organization(조직 내부)** 를 선택합니다. 그렇지 않으면 **External (Internet)(외부(인터넷))** 을 선택합니다. Lync 연결 분석기는 항상 내부 테스트와 외부 테스트를 모두 수행하지만 컴퓨터의 위치가 네트워크 내부인지 외부인지를 지정하면 특정 오류 발생 가능 여부를 해석할 수 있습니다.
    
      - **Client(클라이언트)** 에서 연결 테스트를 수행할 대상을 **Lync Windows Store app(Lync Windows 스토어 앱)** 또는 **Lync mobile apps(Lync 모바일 앱)** 중에서 선택합니다.
    
      - **Server discovery(서버 검색)** 에서 수행할 테스트의 유형을 선택합니다.
        
          - Lync 서버를 자동으로 검색하려면 **Automatic(자동)** 을 선택합니다.
        
          - 자동 검색 테스트를 건너뛰거나 연결하려는 서버의 이름을 알고 있으면 **Manual using address:(수동 주소 사용:)** 를 선택하고 Lync 서버의 FQDN(정규화된 도메인 이름)을 **lync.company.com** 과 같이 지정합니다.

2.  (선택 사항) 지정된 경로에서 로그 파일을 만들려면 **Log File(로그 파일)** 에서 확인란을 선택합니다. 로깅을 사용하도록 설정된 경우 **Clear(지우기)** 를 클릭하여 로그 파일을 지우고 **Open(열기)** 을 클릭하여 로그 파일을 열어 표시한 다음 **Email(전자 메일)** 을 클릭하여 전자 메일 메시지를 열어 지원 팀에 결과를 보냅니다. 지정된 경로에서 로그 파일을 수동으로 첨부해야 합니다.

3.  **Start(시작)** 를 클릭합니다.

다음 그림에는 Lync 연결 분석기의 예제 결과가 나와 있습니다.

**Lync 연결 분석기**

![Lync 연결 분석기 스크린샷](images/JJ907302.a7cc0abe-fac2-4691-a7d8-9ffef59cdee5(OCS.15).png "Lync 연결 분석기 스크린샷")

## Lync 연결 분석기에서 테스트하는 구성 요소

Lync 연결 분석기는 Lync Windows 스토어 앱 및 Lync 모바일 앱에서 사용하는 것과 같은 단계를 사용하여 Lync 서버 검색 및 연결 설정을 시도합니다. 또한 이 섹션에서 설명하는 대로 테스트를 수행합니다.

**Automatic discovery(자동 검색)** 를 선택하면 Lync 연결 분석기는 다음을 수행합니다.

  - 자동 검색 URL에 대해 DNS(도메인 이름 서비스)를 쿼리합니다.

  - 보안 내부 채널을 사용하여 검색을 시도합니다. 예를 들어 **HTTPS://lyncdiscoverinternal.company.com/** 과 같은 채널을 사용합니다.

  - 비보안 내부 채널을 사용하여 검색을 시도합니다. 예를 들어 **HTTP://lyncdiscoverinternal.company.com/** 과 같은 채널을 사용합니다.

  - 보안 외부 채널을 사용하여 검색을 시도합니다. 예를 들어 **HTTPS://lyncdiscover.company.com/** 과 같은 채널을 사용합니다.

  - 비보안 외부 채널을 사용하여 검색을 시도합니다. 예를 들어 **HTTP://lyncdiscover.company.com/** 과 같은 채널을 사용합니다.

**Use the following server discovery address(다음 서버 검색 주소 사용)**를 선택하면 Lync 연결 분석기는 다음을 수행합니다.

  - DNS에 서버의 FQDN을 쿼리합니다.

  - 보안 채널을 사용하여 검색을 시도합니다. 예를 들어 **HTTPS://serverFQDN/** 과 같은 채널을 사용합니다.

  - 비보안 채널을 사용하여 검색을 시도합니다. 예를 들어 **HTTP://serverFQDN/** 과 같은 채널을 사용합니다.

**Test the requirements for(요구 사항 테스트)** 에서 **Lync Windows Store app(Lync Windows 스토어 앱)** 을 선택하면 Lync 연결 분석기는 다음을 수행합니다.

  - 웹 티켓 서비스를 사용할 수 있는지 확인하고 Lync 계정 자격 증명의 인증을 테스트합니다.

  - 인증 브로커(Reach) 서비스를 사용할 수 있는지 확인합니다.

**Client** 에서 **Lync Mobile 2010 App** 이 선택된 경우 Lync 연결 분석기가 다음을 수행합니다.

  - 웹 티켓 서비스를 사용할 수 있는지 확인하고 Lync 계정 자격 증명의 인증을 테스트합니다.

  - Mobility(MCX) Service를 사용할 수 있는지 확인합니다.

**Client** 에서 **Lync Mobile 2013 App** 이 선택된 경우 Lync 연결 분석기가 다음을 수행합니다.

  - 웹 티켓 서비스를 사용할 수 있는지 확인하고 Lync 계정 자격 증명의 인증을 테스트합니다.

  - Mobility(UCWA) Service를 사용할 수 있는지 확인합니다.

Lync 연결 분석기는 이러한 테스트를 수행하는 중에 테스트를 실행하는 컴퓨터, 프록시 서버, 하드웨어 부하 분산 장치 및 Lync Server에 설치된 인증서의 유효성을 검사합니다.

## 기타 리소스

Microsoft에서 제공하는 또 다른 웹 기반 연결 테스트 도구인 Microsoft 원격 연결 분석기를 <https://testconnectivity.microsoft.com/>에서 다운로드할 수 있습니다. Lync 연결 분석기와 원격 연결 분석기의 차이는 다음과 같습니다.

  - 원격 연결 분석기는 Microsoft Lync뿐 아니라 Microsoft Exchange 및 Outlook에 대한 연결도 테스트할 수 있습니다.

  - 원격 연결 분석기는 SIP 로그인을 완료하는 반면 Lync 연결 분석기는 로그인은 하지 않고 계정 자격 증명의 유효성만 검사합니다.

  - 원격 연결 분석기는 공용 웹 서버에서 실행되므로 조직 네트워크 외부로부터의 연결만 테스트합니다.

  - 원격 연결 분석기는 인증 브로커(Reach) 서비스, Mobility(MCX) Service 및 웹 티켓 서비스의 사용 가능 여부를 테스트하지 않습니다.

  - Lync 연결 분석기는 자동 검색 서비스를 테스트합니다.

  - 원격 연결 분석기는 모든 Lync Server 버전에 연결할 수 있지만 Lync 연결 분석기는 최소한 Lync Server 2010용 누적 업데이트(2012년 2월)가 적용된 Lync Server 2010 또는 최신 Lync Server 버전에만 정상적으로 연결할 수 있습니다.

다음 문서에서는 Lync Windows 스토어 앱 및 Lync 모바일 클라이언트를 지원하도록 Lync Server를 배포 및 구성하는 절차와 요구 사항에 대해 설명합니다.

  - [Lync Server 2013에서 클라이언트 및 장치 배포](lync-server-2013-deploying-clients-and-devices.md)

  - [Lync Server 2013의 모바일 기능 계획](lync-server-2013-planning-for-mobility.md)

  - [Lync Server 2013에서 모바일 기능 배포](lync-server-2013-deploying-mobility.md)

