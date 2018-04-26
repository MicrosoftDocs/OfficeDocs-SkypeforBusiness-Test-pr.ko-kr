---
title: 'Lync Server 2013: Standard Edition 서버 테스트'
TOCTitle: Standard Edition 서버 테스트
ms:assetid: b6ef67bb-9665-43e4-b8b3-eac8898eebf6
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg412890(v=OCS.15)
ms:contentKeyID: 49304804
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Lync Server 2013에서 Standard Edition 서버 테스트

 

_**마지막으로 수정된 항목:** 2012-10-01_

다음 절차에서는 Standard Edition 서버의 배포를 테스트하는 방법에 대해 설명합니다.

## Standard Edition Server 배포를 테스트하려면

1.  Active Directory 컴퓨터 및 사용자를 사용하여 Lync Server 2013이 설치된 Lync Server 제어판 배포에 대한 관리자 역할의 Active Directory 사용자 개체를 **CSAdministrator** 그룹에 추가합니다.

2.  사용자 개체가 현재 로그온되어 있는 경우 로그오프하고 다시 로그온하여 새 그룹 지정을 등록합니다.
    

    > [!NOTE]
    > Lync Server 2013, Standard Edition을 실행하는 서버의 로컬 관리자는 사용자 계정으로 설정할 수 없습니다. CsAdministors 그룹에 적합한 사용자와 그룹을 추가하지 않으면 Lync Server 2013 제어판을 열 때 권한 없음: RBAC(역할 기반 액세스 제어) 인증이 실패했기 때문에 액세스가 거부되었습니다."와 같은 오류 메시지가 표시됩니다.



3.  관리 계정을 사용하여 Lync Server 제어판이 설치된 컴퓨터에 로그온합니다.

4.  Lync Server 제어판을 시작한 후 자격 증명을 제공하라는 메시지가 나타나면 자격 증명을 제공합니다. Lync Server 2013 제어판에 배포 정보가 표시됩니다.

5.  왼쪽 탐색 표시줄에서 **토폴로지** 를 클릭한 후 서비스 상태에 녹색 화살표가 표시된 컴퓨터가 나타나며, 배포되어 온라인 상태로 설정된 각 Lync Server 서버 역할 옆에 복제 상태를 나타내는 녹색 확인 표시가 있는지 확인합니다.

6.  왼쪽 탐색 표시줄에서 **사용자** 를 클릭하고 두 명의 사용자가 Lync Server 2013을 사용할 수 있도록 설정합니다.

7.  도메인에 가입된 컴퓨터에 사용자로 로그온하고 도메인의 다른 컴퓨터에 다른 사용자로 로그온합니다.

8.  두 개의 클라이언트 컴퓨터 각각에 Lync Server 2013을 설치한 다음 두 사용자가 모두 Lync Server 2013에 로그인하고 서로에게 인스턴트 메시지를 보낼 수 있는지 확인합니다.

## 참고 항목

#### 개념

[Lync Server 2013에서 클라이언트 및 장치 배포](lync-server-2013-deploying-clients-and-devices.md)

