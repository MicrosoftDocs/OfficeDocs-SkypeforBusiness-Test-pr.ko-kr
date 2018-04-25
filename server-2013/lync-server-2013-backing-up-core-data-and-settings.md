---
title: 핵심 데이터 및 설정 백업
TOCTitle: 핵심 데이터 및 설정 백업
ms:assetid: 278bc95a-7b8d-4e01-a872-a844830459de
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Hh202170(v=OCS.15)
ms:contentKeyID: 52056815
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# 핵심 데이터 및 설정 백업

 

_**마지막으로 수정된 항목:** 2014-04-23_

다음 절차에서는 Lync Server 관리 셸 cmdlet을 사용하여 설정에 대한 백업 파일 및 핵심 서비스에 대한 데이터를 만듭니다. 이 섹션에 사용된 도구 및 도구가 배치된 위치에 대한 자세한 내용은 [백업 및 복원 요구 사항: 도구 및 사용 권한](lync-server-2013-backup-and-restoration-requirements-tools-and-permissions.md)을 참조하십시오. 보관 및 모니터링 데이터 백업에 대한 자세한 내용은 [보관 및 모니터링 데이터베이스 백업](lync-server-2013-backing-up-archiving-and-monitoring-databases.md)을 참조하십시오.


> [!NOTE]
> 중앙 관리 저장소 백업을 위한 이 섹션의 단계에는 보관 및 모니터링을 위한 설정 및 구성이 포함됩니다.



이 섹션에 설명된 cmdlet은 로컬 또는 원격으로 실행할 수 있습니다.

## 핵심 데이터 및 설정을 백업하려면

1.  RTCUniversalServerAdmins 그룹의 구성원인 사용자 계정을 사용하여 내부 배포에 포함된 컴퓨터에 로그온합니다.

2.  다음 단계에서 만드는 백업을 저장하려면 새 공유 폴더를 만들고 **$Backup**에서 참조되는 경로를 새 공유 폴더로 업데이트합니다.

3.  Lync Server 관리 셸 시작: **시작**, **모든 프로그램**, **Microsoft Lync Server 2013**을 차례로 클릭한 다음 **Lync Server 관리 셸**을 클릭합니다.

4.  중앙 관리 저장소 구성 파일을 백업합니다. 명령줄에 다음을 입력합니다.
    
        Export-CsConfiguration -FileName <path and file name for backup>
    
    예:
    
        Export-CsConfiguration -FileName "C:\Config.zip"
    

    > [!NOTE]
    > 이 단계에서는 Lync Server 토폴로지, 정책 및 구성 설정을 파일로 내보냅니다. 토폴로지 데이터를 백업하는 데 다른 단계는 필요하지 않습니다.



5.  백업된 중앙 관리 저장소 구성 파일을 $Backup\\에 복사합니다.

6.  위치 정보 서비스 데이터를 백업합니다. 명령줄에 다음을 입력합니다.
    
        Export-CsLisConfiguration -FileName <path and file name for backup>
    
    예:
    
        Export-CsLisConfiguration -FileName "C:\E911Config.zip"

7.  백업된 위치 정보 서비스 구성 파일을 $Backup\\에 복사합니다.

8.  프런트 엔드 풀의 모든 백 엔드 데이터베이스 및 모든 Standard Edition 서버에서 사용자 데이터를 백업합니다. 명령줄에 다음을 입력합니다.
    
        Export-CsUserData -PoolFQDN <Fqdn> -FileName <String>
    
    예:
    
        Export-CsUserData -PoolFQDN "atl-cs-001.litwareinc.com" -FileName "C:\Logs\ExportedUserData.zip"

9.  백업된 사용자 파일을 $Backup\\에 복사합니다.

10. 응답 그룹 응용 프로그램을 실행하는 모든 풀에서 응답 그룹 구성을 백업합니다. 다음을 수행합니다.
    
    1.  명령줄에 다음을 입력합니다.
        
            Export-CsRgsConfiguration -Source "service:ApplicationServer:<pool FQDN>" -FileName <path and file name for backup>
        
        예:
        
            Export-CsRgsConfiguration -Source ApplicationServer:pool01.contoso.com -FileName C:\RgsConfiguration.zip

11. 백업된 응답 그룹 구성 파일을 $Backup\\에 복사합니다.

