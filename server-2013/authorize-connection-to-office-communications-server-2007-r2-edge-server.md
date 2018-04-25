---
title: Office Communications Server 2007 R2 에지 서버에 대한 연결 권한 부여
TOCTitle: Office Communications Server 2007 R2 에지 서버에 대한 연결 권한 부여
ms:assetid: 14f6798a-28d6-4b3d-8734-942192e1bbf5
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/JJ204702(v=OCS.15)
ms:contentKeyID: 49302905
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Office Communications Server 2007 R2 에지 서버에 대한 연결 권한 부여

 

_**마지막으로 수정된 항목:** 2012-09-28_

파일럿 풀에 있는 각 Lync Server 2013 프런트 엔드 서버 또는 Standard Edition 서버에 대해 Office Communications Server 2007 R2 에지 서버 연결 권한이 부여된 내부 서버 목록을 업데이트해야 합니다. 이와 같이 업데이트하지 않으면 레거시 에지 서버를 사용하여 참가하는 사용자에 대해 외부 A/V(오디오/비디오) 회의가 작동하지 않습니다.

## Office Communications Server 2007 R2 에지 서버 연결 권한을 부여하려면

1.  Office Communications Server 2007 R2 에지 서버의 **관리 도구** 그룹에서 **컴퓨터 관리** 스냅인을 엽니다.

2.  콘솔 트리에서 **서비스 및 응용 프로그램** 을 확장합니다.

3.  **Office Communications Server 2007 R2**를 마우스 오른쪽 단추로 클릭하고 **속성** 을 클릭합니다.

4.  **내부** 탭을 클릭합니다.

5.  **서버 추가** 에서 **추가** 를 클릭합니다.

6.  **Office Communications Server 추가** 대화 상자에서 적절한 정보를 입력합니다.
    
      - 각 Lync Server 2013 프런트 엔드 서버 또는 Standard Edition 서버와 Lync Server 2013 풀의 FQDN(정규화된 도메인 이름)을 지정합니다.
    
      - 다음 홉 컴퓨터를 해당 FQDN으로 지정하는 고정 경로를 풀에 구성한 경우 Lync Server 2013 디렉터의 FQDN을 지정합니다.

7.  각 Lync Server 2013, 프런트 엔드 서버, Standard Edition 서버, 풀 및 디렉터에 대한 항목을 추가한 후 **적용**을 클릭하고 **확인** 을 클릭하여 속성 페이지를 닫습니다.

