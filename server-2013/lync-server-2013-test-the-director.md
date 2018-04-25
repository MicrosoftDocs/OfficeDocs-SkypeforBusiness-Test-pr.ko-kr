---
title: 'Lync Server 2013: 디렉터 테스트'
TOCTitle: 디렉터 테스트
ms:assetid: 9627a7e2-28cc-429c-b79b-7c7a27573bb7
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg398767(v=OCS.15)
ms:contentKeyID: 49304447
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Lync Server 2013에서 디렉터 테스트

 

_**마지막으로 수정된 항목:** 2012-09-08_

이 단계에서는 디렉터나 디렉터 풀이 구성되어 있지만 DNS(Domain Name System) SRV 항목에서 여전히 클라이언트에게 풀이나 Standard Edition Server를 사용하여 로그온하라고 지시합니다. Lync 2013 클라이언트가 디렉터를 사용하여 자동으로 로그온하도록 DNS 레코드를 변경하기 전에 수동으로 클라이언트가 디렉터를 가리키도록 하여 클라이언트를 테스트합니다.

## 배포를 테스트하려면

1.  **CSAdministrator** 그룹에 속하는 도메인 계정으로 Lync Server 제어판을 설치한 컴퓨터에 로그온합니다.

2.  브라우저 창을 연 다음 Admin URL을 입력하여 Lync Server 제어판을 엽니다. Lync Server 제어판을 시작하는 데 사용할 수 있는 다양한 방법에 대한 자세한 내용은 [Lync Server 관리 도구 열기](lync-server-2013-open-lync-server-administrative-tools.md)를 참조하세요.

3.  탐색 창에서 **토폴로지** 를 클릭하고 **상태** 열에서 디렉터나 디렉터 풀에 대한 화살표(즉, ![녹색 화살표가 있는 서버 아이콘](images/Gg398767.2263cdb7-7e60-457a-a528-a3a082bd051b(OCS.15).jpg "녹색 화살표가 있는 서버 아이콘"))가 있는 녹색 서버가 있는지 확인합니다.

4.  Lync Server 2013 클라이언트가 설치되어 있는 두 클라이언트 컴퓨터를 연결하고 Lync Server 2013에 대해 사용하도록 설정된 서로 다른 사용자 계정으로 각 컴퓨터에 로그온합니다.

5.  클라이언트 컴퓨터 중 한 대에서 **옵션** 메뉴를 클릭하고 **개인** 설정 그룹을 선택한 다음 **고급** , **수동 구성** 을 차례로 클릭하고 **내부 서버 이름 또는 IP 주소** 를 새 디렉터나 디렉터 풀의 FQDN(정규화된 도메인 이름)으로 설정합니다.

6.  두 클라이언트에 모두 로그온하고 디렉터를 사용한 클라이언트 로그온이 제대로 로그온되는지를 확인하고 다른 사용자의 현재 상태를 확인한 다음 두 사용자가 인스턴트 메시지를 교환할 수 있는지 확인합니다.

