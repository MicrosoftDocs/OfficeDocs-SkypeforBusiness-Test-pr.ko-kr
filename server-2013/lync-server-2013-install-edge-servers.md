---
title: 'Lync Server 2013: 에지 서버 설치'
TOCTitle: 에지 서버 설치
ms:assetid: 1655ab69-3899-4ee4-a1cc-8243bc1bfa0f
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg398230(v=OCS.15)
ms:contentKeyID: 49302915
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Lync Server 2013의 에지 서버 설치

 

_**마지막으로 수정된 항목:** 2012-09-08_

Lync Server 배포 마법사를 사용하여 에지 서버에 Lync Server 2013을 설치합니다. 각 에지 서버에서 배포 마법사를 실행하면 에지 서버를 설정하는 데 필요한 대부분의 작업을 완료할 수 있습니다. Lync Server 2013을 에지 서버에 배포하려면 토폴로지 작성기를 실행하여 에지 서버 토폴로지를 정의 및 게시하고, 에지 서버에서 사용할 수 있는 미디어로 이 서버 토폴로지를 내보낸 상태여야 합니다. 자세한 내용은 [Lync Server 2013의 외부 사용자 액세스에 대한 시나리오](lync-server-2013-scenarios-for-external-user-access.md) 및 [Lync Server 2013 토폴로지 내보내기 및 에지 설치용 외부 미디어에 토폴로지 복사](lync-server-2013-export-your-topology-and-copy-it-to-external-media-for-edge-installation.md)를 참조하십시오.

배포 마법사를 사용하여 각 에지 서버를 설치하고, 필요한 인증서를 설치 및 할당하고, 필요한 서비스를 시작한 후에는 [Lync Server 2013에서 외부 사용자 액세스에 대한 지원 구성](lync-server-2013-configuring-support-for-external-user-access.md)의 정보를 사용하여 설치를 완료하고 [Lync Server 2013에서 에지 배포 확인](lync-server-2013-verifying-your-edge-deployment.md)에서 외부 사용자 액세스 및 정보를 사용하도록 설정 및 구성하여 서버 및 클라이언트 연결을 비롯한 설치의 유효성을 검사할 수 있습니다.

## 에지 서버를 설치하려면

1.  로컬 Administrators 그룹의 구성원 또는 그에 해당하는 사용자 권한이 있는 계정으로 에지 서버를 설치할 컴퓨터에 로그온합니다.

2.  토폴로지 작성기를 사용하여 만든 다음 외부 미디어로 내보내고 복사한 토폴로지 구성 파일을 에지 서버에서 사용할 수 있는지 확인합니다(예: 토폴로지 구성 파일을 복사한 USB 드라이브에 액세스하거나, 파일을 복사한 네트워크 공유에 대한 액세스 확인).

3.  배포 마법사를 시작합니다.
    

    > [!NOTE]
    > Microsoft Visual C++ 재배포 가능 파일을 설치해야 한다는 메시지가 표시되면 <STRONG>예</STRONG> 를 클릭합니다. 다음 대화 상자에서 기본 <STRONG>설치 위치</STRONG> 를 그대로 적용하거나 <STRONG>찾아보기</STRONG> 를 클릭하여 다른 위치를 선택한 후에 <STRONG>설치</STRONG> 를 클릭합니다. 그 다음 대화 상자에서 <STRONG>동의함</STRONG> 확인란을 선택하고 <STRONG>확인</STRONG> 을 클릭합니다.



4.  배포 마법사에서 **Lync Server 시스템 설치 또는 업데이트** 를 클릭합니다.

5.  마법사에서 배포 상태를 확인하고 나면 **1단계. 로컬 구성 저장소 설치** 에서 **실행** 을 클릭하고 다음을 수행합니다.
    
      - **중앙 관리 저장소의 로컬 복제본 구성** 대화 상자에서 **파일에서 가져오기(에지 서버에 권장)** 을 클릭하고 내보낸 토폴로지 파일이 있는 위치로 이동한 다음 .zip 파일을 선택하고 **열기** , **다음** 을 차례로 클릭합니다.
    
      - 배포 마법사가 구성 파일에서 구성 정보를 읽고 XML 구성 파일을 로컬 컴퓨터에 씁니다.
    
      - **명령 실행** 프로세스가 완료되면 **마침** 을 클릭합니다.

6.  배포 마법사에서 **2단계: Lync Server 구성 요소 설치 또는 제거** 를 클릭하여 로컬 컴퓨터에 저장한 XML 구성 파일에 지정된 Lync Server 2013 에지 구성 요소를 설치합니다.

7.  설치를 완료한 후 [Lync Server 2013의 에지 인증서 설정](lync-server-2013-set-up-edge-certificates.md)의 정보를 사용하여 서비스를 시작하기 전에 필요한 인증서를 설치 및 할당합니다.

