---
title: Standard Edition 서버 복원
TOCTitle: Standard Edition 서버 복원
ms:assetid: d1845663-3138-4fd6-b3e7-337e294d40d8
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Hh202190(v=OCS.15)
ms:contentKeyID: 52056959
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Standard Edition 서버 복원

 

_**마지막으로 수정된 항목:** 2013-02-21_

중앙 관리 저장소를 호스트하지 않는 Standard Edition 서버가 실패하면 이 섹션의 절차를 따릅니다. 중앙 관리 저장소가 실패하면 [중앙 관리 저장소를 호스트하는 서버 복원](lync-server-2013-restoring-the-server-hosting-the-central-management-store.md)을 참조하십시오.


> [!TIP]
> 복원을 시작하기 전에 시스템에 대한 이미지 복사본을 만드는 것이 좋습니다. 복원 중 오류가 발생하면 이 이미지를 롤백 지점으로 사용할 수 있습니다. 운영 체제 및 SQL Server를 설치한 후에 이미지 복사본을 만들고 인증서를 복원하거나 다시 등록할 수도 있습니다.



## Standard Edition Server를 복원하려면

1.  오류가 발생한 컴퓨터와 FQDN(정규화된 도메인 이름)이 동일한 정상 상태의 서버 또는 새 서버에 운영 체제를 설치하고 인증서를 복원하거나 다시 등록합니다.
    

    > [!NOTE]
    > 조직의 서버 배포 절차에 따라 이 단계를 수행합니다.



2.  RTCUniversalServerAdmins 그룹 및 Local Administrators 그룹의 구성원인 사용자 계정을 사용하여 복원 중인 서버에 로그온합니다.

3.  $Backup에서 서버의 파일 저장소 위치에 적합한 파일 저장소를 복사하여 파일 저장소를 복원하고 폴더를 공유합니다.
    

    > [!IMPORTANT]
    > 복원된 파일 저장소의 경로 및 파일 이름은 파일을 사용하는 구성 요소가 액세스할 수 있도록 백업된 파일 저장소와 정확하게 동일해야 합니다.



4.  토폴로지 작성기를 실행합니다.
    
    1.  토폴로지 작성기 시작: **시작**, **모든 프로그램**, **Microsoft Lync Server 2013**을 차례로 클릭한 다음 **Lync Server 토폴로지 작성기**를 클릭합니다.
    
    2.  **기존 배포에서 토폴로지 다운로드**를 클릭한 후 **확인**을 클릭합니다.
    
    3.  토폴로지를 선택한 후 **저장**을 클릭합니다. **예**를 클릭하여 선택을 확인합니다.

5.  Lync Server 설치 폴더 또는 미디어로 이동하여 Lync Server 배포 마법사(\\setup\\amd64\\Setup.exe)를 시작합니다. Lync Server 배포 마법사를 사용하여 다음을 수행합니다.
    
    1.  **1단계: 로컬 구성 저장소 설치**를 실행하여 로컬 구성 파일을 설치합니다.
    
    2.  **2단계: Lync Server 구성 요소 설치 또는 제거**를 실행하여 Lync Server 서버 역할을 설치합니다.
    
    3.  **3단계: 인증서 요청, 설치 또는 지정**을 실행하여 인증서를 지정합니다.
    
    4.  **4단계: 서비스 시작**을 실행하여 서버에서 서비스를 시작합니다.
    
    배포 마법사 실행에 대한 자세한 내용은 복원 중인 서버 역할에 대한 배포 설명서를 참조하십시오.

6.  다음을 수행하여 사용자 데이터를 복원합니다.
    
    1.  ExportedUserData.zip을 $Backup\\에서 로컬 디렉터리로 복사합니다.
    
    2.  사용자 데이터를 복원하기 전에 Lync 서비스를 중지해야 합니다. 이렇게 하려면 다음을 입력합니다.
        
            Stop-CsWindowsService
    
    3.  사용자 데이터를 복원하려면 명령줄에 다음을 입력합니다.
        
            Import-CsUserData -PoolFqdn <Fqdn> -FileName <String>
        
        예:
        
            Import-CsUserData -PoolFqdn "atl0cs-001.litwareinc.com" -FileName "C:\Logs\ExportedUserDatal.zip"
    
    4.  다음을 입력하여 Lync 서비스를 다시 시작합니다.
        
            Start-CsWindowsService

7.  이 Standard Edition 서버에 응답 그룹을 배포한 경우 응답 그룹 구성 데이터를 복원합니다. 자세한 내용은 [응답 그룹 설정 복원](lync-server-2013-restoring-response-group-settings.md)을 참조하십시오.

8.  이 Standard Edition 서버에 영구 채팅을 배포한 경우 영구 채팅 데이터베이스(mgc.mdf)를 복원합니다.
    
    SQL Server 백업을 사용하여 영구 채팅 데이터베이스를 백업한 경우에는 SQL Server 복원 절차를 사용하여 해당 데이터베이스를 복원합니다.
    
    Export-CsPersistentChatData cmdlet을 사용하여 데이터베이스를 백업한 경우에는 Import-CsPersistentChatData를 사용하여 복원합니다.

