---
title: Lync Server 2013 파일럿 풀 배포
TOCTitle: Lync Server 2013 파일럿 풀 배포
ms:assetid: 19c27053-8b21-401f-ad91-75c2dd355e91
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/JJ204718(v=OCS.15)
ms:contentKeyID: 49302959
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Lync Server 2013 파일럿 풀 배포

 

_**마지막으로 수정된 항목:** 2013-11-22_

Lync Server 2013으로 마이그레이션하는 데 필요한 첫 번째 단계 중 하나는 파일럿 풀을 배포하는 것입니다. 파일럿 풀에서는 Lync Server 2013과 Office Communications Server 2007 R2 배포의 동시 사용을 테스트합니다. 동시 사용은 모든 사용자 및 풀을 Lync Server 2013으로 이동할 때까지 지속되는 임시 상태입니다.

파일럿 풀을 배포할 때는 새 프런트 엔드 풀 정의 마법사를 사용합니다. Office Communications Server 2007 R2 풀에 설정된 것과 동일한 기능 및 작업을 Lync Server 2013 파일럿 풀에 배포해야 합니다. Office Communications Server 2007 R2 환경을 보관 및 모니터링하기 위해 보관 서버, 모니터링 서버 또는 System Center Operations Manager를 배포했으며 마이그레이션 중에도 보관 또는 모니터링을 계속하려는 경우 파일럿 환경에도 이러한 기능을 배포해야 합니다. Office Communications Server 2007 R2 환경을 보관 또는 모니터링하기 위해 배포한 버전은 Lync Server 2013 환경에서 데이터를 캡처하지 않습니다.


> [!NOTE]
> 다음 절차에서는 전체 파일럿 풀 배포 프로세스에서 고려해야 하는 기능 및 설정에 대해 설명합니다. 이 섹션에서는 파일럿 풀 배포 중에 고려해야 하는 핵심 사항들에 대해서만 설명합니다. 자세한 단계는 <A href="lync-server-2013-deploying-lync-server.md">Lync Server 2013 배포</A> 배포 가이드를 참조하십시오.



**Lync Server 2013 파일럿 풀을 배포하려면**

1.  토폴로지 작성기가 Domain Admins 그룹 및 RTCUniversalServerAdmins 그룹의 구성원으로 설치되어 있는 컴퓨터에 로그온합니다.

2.  토폴로지 작성기를 열고 새 토폴로지 만들기를 선택합니다.

3.  기본 SIP 도메인을 입력합니다.
    
    ![새 토폴로지 만들기, 주 도메인 정의 페이지](images/JJ204718.68775d87-f32c-494a-8386-6d4c81e81284(OCS.15).jpg "새 토폴로지 만들기, 주 도메인 정의 페이지")

4.  **새 프런트 엔드 풀 정의**가 표시될 때까지 마법사의 단계를 계속해서 완료합니다. 이 단계가 표시되면 다음을 클릭합니다.

5.  풀의 FQDN을 입력합니다. 파일럿 풀을 정의할 때는 Enterprise Edition 프런트 엔드 풀과 Standard Edition 서버 중 어느 것을 배포할지를 선택할 수 있습니다. Lync Server 2013에서는 파일럿 풀 기능이 레거시 풀에 배포된 기능과 일치할 필요가 없습니다.
    

    > [!WARNING]
    > 파일럿 풀에 대해 정의하는 풀 또는 서버의 FQDN(정규화된 도메인 이름)은 고유해야 합니다. 이 FQDN은 현재 배포된 Office Communications Server 2007 R2 풀 또는 현재 배포된 다른 서버의 이름과 일치할 수 없습니다.

    
    ![프런트 엔드 풀 FQDN 정의 페이지](images/JJ204718.5ff4336c-13fa-47cc-899b-066f267eb3f0(OCS.15).jpg "프런트 엔드 풀 FQDN 정의 페이지")

6.  풀에 추가할 컴퓨터를 정의합니다.
    
    ![새 프런트 엔드 풀 정의 대화 상자](images/JJ204718.374f0ed4-988b-465f-9861-8d1db401e76f(OCS.15).jpg "새 프런트 엔드 풀 정의 대화 상자")

7.  **기능 선택** 페이지에서 이 프런트 엔드 풀에 필요한 기능의 확인란을 선택합니다. 예를 들어 IM(인스턴트 메시징) 및 현재 상태 기능만 배포하려면 회의 확인란을 선택하여 단체 IM을 허용하고 음성, 화상 및 공동 작업 회의 기능을 나타내는 전화 접속(PSTN) 회의, Enterprise Voice 또는 통화 허용 제어는 선택하지 않습니다. 기능 선택에 대한 자세한 내용은 배포 설명서에서 [Lync Server 2013에서 프런트 엔드 풀 또는 Standard Edition 서버 정의 및 구성](lync-server-2013-define-and-configure-a-front-end-pool-or-standard-edition-server.md)을 참조하십시오.
    
    ![프런트 엔드 풀 기능 선택 페이지](images/JJ205144.5c3f3ff9-6e17-4d66-9b13-3bd55b38246b(OCS.15).jpg "프런트 엔드 풀 기능 선택 페이지")

8.  **배치된 서버 역할 선택** 페이지에서는 중재 서버를 Lync Server 2013에 배치할 것을 권장합니다. 레거시 토폴로지를 Lync Server 2013과 병합할 때는 먼저 Office Communications Server 2007 R2중재 서버를 배치해야 합니다. 토폴로지를 병합하고 Lync Server 2013 중재 서버를 구성한 후에는 배치된 중재 서버를 유지할지, 이후 배포 프로세스에서 중재 서버 역할을 Lync Server 2013으로 이동할 때 독립 실행형 서버로 변경할지 선택할 수 있습니다.
    
    ![프런트 엔드 풀 배치된 서버 역할 선택 페이지](images/JJ205144.e00b7eba-010b-44ed-b0a6-6ab3e534fb8c(OCS.15).jpg "프런트 엔드 풀 배치된 서버 역할 선택 페이지")

9.  파일럿 풀 배포 중에는 **이 프런트 엔드 풀과 서버 역할 연결** 에서 **에지 풀을 이 프런트 엔드 풀의 미디어 구성 요소에서 사용하도록 설정** 옵션을 선택하지 마십시오. 이 기능은 나중에 마이그레이션 중에 사용하고 온라인으로 설정합니다. 현재는 이 설정을 해제한 상태로 둡니다.
    
    ![프런트 엔드 풀과 서버 역할 연결 페이지](images/JJ205144.2d95a798-ad76-4dad-9392-ce41f4d938d1(OCS.15).jpg "프런트 엔드 풀과 서버 역할 연결 페이지")

10. **Office Web Apps 서버 선택** 페이지에서 **새로 만들기** 를 클릭한 다음 응용 프로그램 서버의 FQDN을 지정합니다.
    
    ![새 Office Online 서버 FQDN 속성 정의](images/JJ205144.25c6b455-f1b8-4326-a569-6e338153d398(OCS.15).jpg "새 Office Online 서버 FQDN 속성 정의")

11. **보관 SQL Server 저장소 정의** 페이지에서 이전에 Lync Server 2013용으로 만든 SQL Server 인스턴스를 선택합니다.
    
    ![보관 SQL Server 저장소 정의 페이지](images/JJ205144.0f76f1dc-d0d7-42a0-aea3-400b8e1f35cd(OCS.15).jpg "보관 SQL Server 저장소 정의 페이지")

12. **모니터링 SQL Server 저장소 정의** 페이지에서 이전에 Lync Server 2013용으로 만든 SQL Server 인스턴스를 선택합니다. **마침**을 클릭합니다.

13. 토폴로지 작성기의 최상위 노드에서 **Lync Server**를 마우스 오른쪽 단추로 클릭하고 **속성 편집**을 클릭합니다. 그런 다음 **단순 URL**을 클릭합니다.

14. **관리 액세스 URL**을 업데이트합니다.
    
    ![속성 편집, 단순 URL 페이지](images/JJ204718.ef596dd2-1983-47e0-b342-4fc7a0e36380(OCS.15).jpg "속성 편집, 단순 URL 페이지")
    
    단순 URL에 대한 자세한 내용은 배포 설명서에서 [Lync Server 2013에서 단순 URL 편집 또는 구성](lync-server-2013-edit-or-configure-simple-urls.md) 항목을 참조하십시오.

15. **속성 편집**에서 **중앙 관리 서버**를 클릭합니다.

16. 드롭다운 목록에서 Lync Server 2013 풀을 선택합니다.
    
    ![속성 편집, 중앙 관리 서버 페이지](images/JJ204718.211955fc-85f2-462d-8709-e6ea67092e89(OCS.15).jpg "속성 편집, 중앙 관리 서버 페이지")

17. 확인을 클릭하여 **the 속성 편집** 페이지를 닫습니다.

18. **동작** 메뉴에서 **토폴로지 게시**를 선택합니다.

19. 게시 프로세스를 완료했으면 **마침** 을 클릭합니다.

20. Lync Server 2013 배포 마법사로 돌아와서 **Lync Server 시스템 설치 또는 업데이트**를 클릭합니다.
    
    ![Lync Server 2013 배포 마법사](images/JJ204718.fb05adef-ad29-4905-9090-d409261b0e48(OCS.15).jpg "Lync Server 2013 배포 마법사")

구성 저장소의 로컬 복사본을 설치하고 필요한 서비스를 시작하려면 배포 설명서에서 [Lync Server 2013에 대한 프런트 엔드 서버 및 프런트 엔드 풀 설정](lync-server-2013-setting-up-front-end-servers-and-front-end-pools.md)을 참조하십시오.


