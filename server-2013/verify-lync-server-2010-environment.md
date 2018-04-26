---
title: Lync Server 2010 환경 확인
TOCTitle: Lync Server 2010 환경 확인
ms:assetid: bfc7c620-556a-43cd-b1ed-2c268ec2b5cc
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/JJ205231(v=OCS.15)
ms:contentKeyID: 49304909
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Lync Server 2010 환경 확인

 

_**마지막으로 수정된 항목:** 2012-10-19_

Lync Server 2010과 동시 사용 상태로 Lync Server 2013을 배포하는 경우 먼저 Lync Server 2010 서비스가 구성되고 시작되었는지 확인해야 합니다. Lync Server 2013 파일럿 풀을 배포하기 전에 레거시 환경에 있는 주요 서비스와 기능을 파악하는 것이 중요합니다. 레거시 XMPP 배포와 동시 사용 상태로 Microsoft Lync Server 2013 XMPP를 배포하는 경우 먼저 레거시 XMPP 서비스가 구성 및 시작되었는지 확인하고 레거시 XMPP 구성이 지원하는 페더레이션 파트너를 파악해야 합니다. 레거시 Lync Server 2010 배포를 확인하려면 다음 작업을 수행해야 합니다.

  - Lync Server 2010 서비스가 시작되었는지 확인

  - Lync Server 2010의 토폴로지 및 사용자 검토

  - 페더레이션 및 에지 서버 설정 확인

  - XMPP 서비스 및 페더레이션 파트너 확인

**Lync Server 2010 서비스가 시작되었는지 확인**

1.  Lync Server 2010 프런트 엔드 서버에서 관리 도구\\서비스 애플릿으로 이동합니다.

2.  다음 서비스가 프런트 엔드 서버에서 실행 중인지 확인합니다.
    
    ![프런트 엔드 서버에서 실행 중인 서비스 목록](images/JJ205231.639f2729-b759-4d8e-b4ad-59d7f68adcd2(OCS.15).jpg "프런트 엔드 서버에서 실행 중인 서비스 목록")

**Lync Server 제어판에서 Lync Server 2010 토폴로지 검토**

1.  RTCUniversalServerAdmins 그룹의 구성원이거나 CsAdministrator 또는 CsUserAdministrator 관리 역할의 구성원인 계정으로 프런트 엔드 서버에 로그온합니다.

2.  Lync Server 제어판을 엽니다.

3.  **토폴로지** 를 선택합니다. Lync Server 2010 배포의 여러 서버가 나열되는지 확인합니다.
    
    ![Lync Server 2010 제어판 토폴로지 페이지](images/JJ205231.338ce4fb-2162-4176-a249-ec4ae021fa6a(OCS.15).jpg "Lync Server 2010 제어판 토폴로지 페이지")

**Lync Server 제어판에서 Lync Server 2010 사용자를 검토하려면**

1.  Lync Server 제어판을 엽니다.

2.  **사용자** 를 선택한 후 **찾기** 를 클릭합니다.

3.  **등록자 풀** 열이 나열된 각 사용자의 Lync Server 2010 풀을 가리키는지 확인합니다.
    
    ![Lync Server 2010 제어판에 나열된 사용자](images/JJ205231.a9378c40-7a52-4c78-ad83-1463847c9edb(OCS.15).jpg "Lync Server 2010 제어판에 나열된 사용자")

**Lync Server 2010 에지 및 페더레이션 설정을 확인하려면**

1.  토폴로지 작성기를 시작합니다.

2.  **기존 배포에서 토폴로지 다운로드**를 선택합니다.

3.  파일 이름을 선택하고 토폴로지를 기본 .tbxml 파일 형식으로 저장합니다.

4.  Lync Server 2010 노드를 확장하여 배포의 여러 서버 역할을 표시합니다.

5.  사이트 노드를 선택하고 **사이트 페더레이션 경로 지정** 값이 설정되어 있는지 확인합니다.
    
    ![토폴로지 작성기, 사이트 페더레이션 경로](images/JJ205231.87de3735-af7e-4280-8d72-c42cb0ea1c05(OCS.15).jpg "토폴로지 작성기, 사이트 페더레이션 경로")

6.  그런 다음 Standard Edition Server 또는 Enterprise Edition 프런트 엔드 풀을 선택합니다. **연결** 아래에서 미디어에 대한 에지 풀이 구성되었는지 확인합니다.
    
    ![서버 및 풀을 보여 주는 토폴로지 작성기](images/JJ205231.5ad5ea3b-b122-44dd-8968-f1147d6d45f1(OCS.15).jpg "서버 및 풀을 보여 주는 토폴로지 작성기")

7.  마지막으로 에지 풀을 선택하고 **다음 홉 선택** 아래에서 다음 홉 풀이 구성되어 있는지 확인합니다.
    
    ![토폴로지 작성기, 다음 홉 선택](images/JJ205231.3121e723-fba7-498e-a786-bde7be1a55e2(OCS.15).jpg "토폴로지 작성기, 다음 홉 선택")

**레거시 XMPP 페더레이션 파트너 구성 확인**

1.  레거시 XMPP 서버에서 관리 도구\\서비스 애플릿을 이동합니다.

2.  Office Communications Server XMPP 게이트웨이 서비스가 시작되었는지 확인합니다.
    
    ![Office Communications Server XMPP 게이트웨이 서비스](images/JJ205231.23223724-3c4b-4cb9-ace2-1cab2c3c91c3(OCS.15).jpg "Office Communications Server XMPP 게이트웨이 서비스")

