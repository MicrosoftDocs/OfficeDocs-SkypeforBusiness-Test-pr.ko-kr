---
title: Lync Server 2013 제어판 문제 해결
TOCTitle: Lync Server 2013 제어판 문제 해결
ms:assetid: 54e7ab57-34ce-4a07-bcc9-643379eb4eb7
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg195689(v=OCS.15)
ms:contentKeyID: 49303662
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Lync Server 2013 제어판 문제 해결

 

_**마지막으로 수정된 항목:** 2013-02-21_

이 항목에서는 Lync Server 2013 제어판 액세스 문제 해결을 도울 수 있는 정보 및 절차를 제공합니다.

## 인터넷 브라우저 요구 사항

Lync Server 제어판을 사용하려면 Microsoft Silverlight 브라우저 플러그 인 버전 4.0.50524.0 또는 최신 버전이 설치되어 있어야 합니다. Silverlight가 설치되지 않았거나 이전 버전이 설치된 경우 메시지의 지침에 따라 필요한 버전을 설치하십시오.


> [!NOTE]
> Lync Server 제어판에 대한 다른 소프트웨어 요구 사항은 Lync Server 제어판 및 다른 모든 Lync Server 2013 관리 도구를 설치할 수 있는 운영 체제와 관련이 있습니다. 자세한 내용은 지원 가능성 <A href="lync-server-2013-server-and-tools-operating-system-support.md">Lync Server 2013의 서버 및 도구 운영 체제 지원</A>을 참조하십시오.



인터넷 브라우저에서 보안 고려 사항으로 인해 Silverlight 설치가 차단될 경우 Lync Server 제어판을 여는 URL(Uniform Resource Locator)을 신뢰할 수 있는 사이트 목록에 추가합니다. Internet Explorer 보안 설정에서 **ActiveX 컨트롤 및 플러그인 실행**이 **사용**으로 설정되었는지 확인합니다. 자세한 내용은 [http://go.microsoft.com/fwlink/?linkid=214060\&clcid=0x412](http://go.microsoft.com/fwlink/?linkid=214060%26clcid=0x412)를 참조하십시오. 또한 브라우저가 SSL 3.0을 사용하도록 구성되었는지 확인합니다.

인터넷 브라우저가 프록시 서버를 사용하도록 구성된 경우 자동으로 내부 사이트로 검색된 사이트에 대해 프록시 서버를 바이패스하도록 브라우저가 구성되었는지 확인합니다. 또는 프록시 서버 구성 설정에서 해당 주소를 브라우저의 예외 목록에 추가합니다.

## 관리 액세스 URL에 대한 DNS 레코드 및 인증서 요구 사항

Lync Server 제어판에 액세스하기 위해 단순 URL을 구성한 경우 해당 관리 액세스 URL을 사용하는 데 필요한 정적 DNS(Domain Name System) 호스트 (A) 리소스 레코드와 인증서도 구성되었는지 확인합니다. 언제라도 기본 URL을 변경할 경우에는 변경 내용이 적절한 DNS 레코드 및 인증서에 반영되어 있고 변경 내용을 등록하기 위해 각 디렉터 및 프런트 엔드 서버에서 *Enable-CsComputer*를 실행했는지 확인합니다. 자세한 내용은 계획 설명서에서 다음 항목들을 참조하십시오.

  - [Lync Server 2013의 단순 URL 계획](lync-server-2013-planning-for-simple-urls.md)

  - [Lync Server 2013의 단순 URL에 대한 DNS 요구 사항](lync-server-2013-dns-requirements-for-simple-urls.md)

  - [Lync Server 2013의 내부 서버에 대한 인증서 요구 사항](lync-server-2013-certificate-requirements-for-internal-servers.md)

관리 액세스 URL을 구성하기 위한 단계별 절차를 보려면 배포 설명서에서 [Lync Server 2013에서 단순 URL 편집 또는 구성](lync-server-2013-edit-or-configure-simple-urls.md)을 참조하십시오.


> [!NOTE]
> 웹 서버에 네트워크 어댑터가 두 개 이상 있는 경우 DNS 확인이 올바르게 작동할 수 있으려면 각 추가 네트워크 어댑터에 대해 DNS를 수동으로 구성해야 합니다.



## IIS(인터넷 정보 서비스) 요구 사항

Lync Server 제어판은 IIS(인터넷 정보 서비스)가 필요한 Lync Server 2013의 구성 요소 중 하나입니다. 특히 HTTP 리디렉션 및 Windows 인증 기능이 사용하도록 설정되었고 W3SVC(World Wide Web Publishing Service)가 실행 중인지 확인합니다.

## World Wide Publishing Service(Windows Service) 종속성

World Wide Web Publishing Service가 중지된 경우 Lync Server 제어판에 액세스할 수 없습니다. Windows Services MMC(Microsoft Management Console)를 사용하여 서비스를 다시 시작할 수 있습니다.

**World Wide Web Publishing Service를 시작하려면**

1.  World Wide Web Publishing Service가 IIS(인터넷 정보 서비스)의 일부로 설치된 컴퓨터에 로그온합니다.

2.  **시작**, **관리 도구**, **서비스**를 클릭합니다.

3.  **World Wide Web Publishing Service**를 마우스 오른쪽 단추로 클릭한 후 **시작**을 클릭합니다.

## 응용 프로그램 풀 모드

CsManagementAppPool 응용 프로그램 풀에서 네트워크 서비스 계정을 프로세스 모델 ID로 사용하도록 IIS를 구성합니다.

## 사용자 권한 및 사용 권한

CsAdministrator 그룹의 구성원인 도메인 계정을 사용하거나 사용자 권한 및 사용 권한을 위임한 계정을 사용하여 Lync Server 제어판에 로그인해야 합니다. 로컬 컴퓨터 계정을 사용해서는 Lync Server 제어판에 로그인할 수 없습니다. RBAC(역할 기반 액세스 제어)를 통한 관리 작업 위임에 대한 자세한 내용은 계획 설명서에서 [Lync Server 2013의 역할 기반 액세스 제어 계획](lync-server-2013-planning-for-role-based-access-control.md)를 참조하십시오.

단순 URL을 사용하여 Lync Server 제어판에 액세스하는 경우 웹 서버가 RTCUniversalServerAdmins 및 RTCUniversalUserAdmins 그룹에 추가되었는지 확인합니다.

## 참고 항목

#### 개념

[Lync Server 2013 관리 도구](lync-server-2013-lync-server-administrative-tools.md)

