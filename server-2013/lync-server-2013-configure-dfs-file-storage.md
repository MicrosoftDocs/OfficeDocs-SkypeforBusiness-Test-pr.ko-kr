---
title: 'Lync Server 2013: 파일 저장소 구성'
TOCTitle: 파일 저장소 구성
ms:assetid: a985be20-5a00-4f38-b45b-83dc82de3827
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/JJ205150(v=OCS.15)
ms:contentKeyID: 49304666
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Lync Server 2013의 파일 저장소 구성

 

_**마지막으로 수정된 항목:** 2012-09-13_

Lync Server 2013에서는 DFS(분산 파일 시스템)에서 파일 공유를 사용할 수 있도록 지원합니다. Windows Server 2008의 DFS에 대한 자세한 내용은 Windows Server 2008의 분산 파일 시스템에 대한 단계별 가이드( [http://go.microsoft.com/fwlink/?linkid=202835\&clcid=0x412](http://go.microsoft.com/fwlink/?linkid=202835%26clcid=0x412))를 참조하십시오. DFS를 사용하기 위해 Lync Server 2013에서 요구되는 사항은 다음과 같습니다.

  - 네임스페이스가 도메인 기반이어야 함

  - 모든 네임스페이스 서버가 Windows 2008 이상을 실행해야 함

Lync Server 2013을 설치하려면 관리자에게 공유 폴더에 대한 모든 권한을 부여해야 합니다. 그러면 Lync Server 2013에서 NTFS 파일 사용 권한을 사용하여 해당 폴더를 ACL에 추가합니다. 상속된 DFS 공유 사용 권한은 액세스를 제한하는 데 사용되지 않습니다.

파일 공유 요구 사항에 대한 자세한 내용은 지원 가능성 설명서에서 [Lync Server 2013의 파일 저장소 지원](lync-server-2013-file-storage-support.md)을 참조하십시오.

다음 절차에서는 DFS 설정 가이드에 설명된 대로 DFS 네임스페이스 마법사를 사용하여 공유 폴더 사용 권한을 올바르게 구성하는 방법에 대해 설명합니다.

## 공유 폴더 사용 권한을 구성하려면

1.  **시작** 을 클릭하고 **모든 프로그램** , **관리 도구** 를 차례로 가리킨 다음 **DFS 관리** 를 클릭합니다.

2.  DFS 관리 스냅인의 콘솔 트리에서 해당 네임스페이스 서버(예: filesrv1.contoso.com)를 마우스 오른쪽 단추로 클릭한 다음 **설정 편집** 을 클릭합니다.

3.  **공유 폴더 사용 권한** 을 선택합니다.

4.  **사용자 지정 권한 사용** 을 선택합니다.

5.  관리자 그룹에 대해 **허용** 아래에서 다음을 선택합니다.
    
      - **모든 권한**
    
      - **변경**
    
      - **읽기**

6.  **적용** 을 클릭한 다음 **확인** 을 클릭합니다.

