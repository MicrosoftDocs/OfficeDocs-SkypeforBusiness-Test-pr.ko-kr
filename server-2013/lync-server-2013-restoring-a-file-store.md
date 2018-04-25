---
title: 파일 저장소 복원
TOCTitle: 파일 저장소 복원
ms:assetid: 89916fc6-31d3-4c7f-9eaf-c02584761ef4
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Hh202180(v=OCS.15)
ms:contentKeyID: 52056887
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# 파일 저장소 복원

 

_**마지막으로 수정된 항목:** 2013-02-18_

Standard Edition의 파일 저장소는 일반적으로 Standard Edition 서버에 있습니다. Enterprise Edition의 파일 저장소는 일반적으로 파일 서버 또는 클러스터에 있습니다. 다음 절차에서는 파일 저장소를 복원하는 방법에 대해 설명합니다.

## 파일 저장소를 복원하려면

1.  파일 저장소가 실패하면 $Backup\\에서 파일 서버 또는 Standard Edition 서버의 파일 저장소 위치에 적합한 파일 저장소를 복사한 후 폴더를 공유합니다.
    

    > [!IMPORTANT]
    > 복원된 파일 저장소의 경로 및 파일 이름은 파일을 사용하는 구성 요소가 액세스할 수 있도록 백업된 파일 저장소와 정확하게 동일해야 합니다.



2.  필요에 따라 파일 저장소에 대한 ACL(액세스 제어 목록)을 설정합니다. 명령줄에 다음을 입력합니다.
    
        Enable-CsTopology
    

    > [!NOTE]
    > 복원 프로세스 중에 토폴로지 작성기를 실행하지 않은 경우 이 단계만 수행하면 됩니다.


