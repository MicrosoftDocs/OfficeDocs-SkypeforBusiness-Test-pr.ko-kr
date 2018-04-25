---
title: Lync Server 2013에서 새 신뢰할 수 있는 응용 프로그램 서버 구성
TOCTitle: Lync Server 2013에서 새 신뢰할 수 있는 응용 프로그램 서버 구성
ms:assetid: a7233db7-fac3-43ff-972e-3bc29a56adb3
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg617964(v=OCS.15)
ms:contentKeyID: 49304633
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Lync Server 2013에서 새 신뢰할 수 있는 응용 프로그램 서버 구성

 

_**마지막으로 수정된 항목:** 2012-11-01_

신뢰할 수 있는 응용 프로그램은 Microsoft Lync Server 2013에서 신뢰하는 Microsoft Unified Communications Managed API(UCMA) 3.0 Core SDK 기반 응용 프로그램입니다. UCMA 응용 프로그램에 대한 자세한 내용은 "Unified Communications Managed API 3.0 Core SDK 설명서"([http://go.microsoft.com/fwlink/?linkid=210320\&clcid=0x412](http://go.microsoft.com/fwlink/?linkid=210320%26clcid=0x412))를 참조하십시오.

Microsoft OWA(Outlook Web Access) 및 Lync Server 2013을 구성하는 방법에 대한 자세한 내용은 Microsoft Exchange Server 2013 설명서에서 "Outlook Web App 및 Lync Server 2010 통합 구성"을 참조하십시오.

서버 역할을 추가하거나 제거할 때 토폴로지를 게시, 사용하도록 설정 또는 사용하지 않도록 설정하려면 RTCUniversalServerAdmins 및 Domain Admins 그룹의 구성원인 사용자로 로그온해야 합니다. 적절한 관리자 권한을 위임하여 서버 역할을 추가할 수도 있습니다. 자세한 내용은 배포 설명서에서 [Lync Server 2013에서 설치 권한 위임](lync-server-2013-delegate-setup-permissions.md)을 참조하십시오. 기타 구성을 변경하려는 경우에는 RTCUniversalServerAdmins 그룹 구성원 자격만 있으면 됩니다.

## 신뢰할 수 있는 응용 프로그램 서버를 구성하려면

1.  토폴로지 작성기가 Domain Admins 그룹 및 RTCUniversalServerAdmins 그룹의 구성원으로 설치되어 있는 컴퓨터에 로그온합니다.

2.  토폴로지 작성기 시작: **시작**, **모든 프로그램**, **Microsoft Lync Server 2013**을 차례로 클릭한 다음 **Lync Server 토폴로지 작성기**를 클릭합니다.

3.  **기존 배포에서 토폴로지 다운로드** 및 **확인**을 차례로 클릭합니다.

4.  **토폴로지를 다른 이름으로 저장** 대화 상자에서 사용할 토폴로지 작성기 파일 및 **저장**을 차례로 클릭합니다.

5.  왼쪽 창에서 **신뢰할 수 있는 응용 프로그램 서버**를 마우스 오른쪽 단추로 클릭한 후 **새 신뢰할 수 있는 응용 프로그램 풀**을 클릭합니다.

6.  신뢰할 수 있는 응용 프로그램 풀에 대한 **풀 FQDN**을 입력하고 단일 서버로 설정할지 다중 서버로 설정할지 여부를 선택한 후 **다음**을 클릭합니다.

7.  **다음 홉 선택** 페이지의 목록에서 Lync Server 2013 프런트 엔드 풀을 선택합니다.

8.  **마침**을 클릭합니다.

9.  최상위 노드인 **Lync Server 2013**을 선택한 후 **동작** 메뉴에서 **게시**를 클릭합니다.
    
    **신뢰할 수 있는 응용 프로그램 풀**이 성공적으로 만들어졌으며 올바른 프런트 엔드 풀에 연결되었습니다.

