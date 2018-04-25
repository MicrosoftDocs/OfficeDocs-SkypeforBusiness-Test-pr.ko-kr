---
title: Lync Server 2013에서 서비스에 대한 세션 금지
TOCTitle: Lync Server 2013에서 서비스에 대한 세션 금지
ms:assetid: 977dcc5c-2aac-48ef-86a1-a8d47b4d9e74
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg182553(v=OCS.15)
ms:contentKeyID: 49304461
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Lync Server 2013에서 서비스에 대한 세션 금지

 

_**마지막으로 수정된 항목:** 2012-11-01_

Lync Server 제어판을 사용하여 특정 컴퓨터에서 모든 Lync Server 2013 서비스의 새 세션이 실행되지 않도록 하거나 특정 Lync Server 2013 서비스의 새 세션을 금지할 수 있습니다.

## 컴퓨터의 모든 Lync Server 서비스에 대한 새 세션을 금지하려면

1.  RTCUniversalServerAdmins 그룹의 구성원인 사용자 계정(또는 이와 동일한 사용자 권한을 가진 사용자 계정)이나 CsServerAdministrator 또는 CsAdministrator 역할이 할당된 사용자 계정에서 Lync Server 2013을 배포한 네트워크에 있는 컴퓨터에 로그온합니다.

2.  브라우저 창을 연 다음 Admin URL을 입력하여 Lync Server 제어판을 엽니다. Lync Server 제어판을 시작하는 데 사용할 수 있는 다양한 방법에 대한 자세한 내용은 [Lync Server 관리 도구 열기](lync-server-2013-open-lync-server-administrative-tools.md)를 참조하세요.

3.  왼쪽 탐색 모음에서 **토폴로지**를 클릭하고 **상태**를 클릭합니다.

4.  **상태** 페이지에서 새 세션을 금지할 서비스를 실행 중인 컴퓨터를 찾기 위해 필요한 경우 목록을 정렬하거나 검색한 다음 해당 컴퓨터를 클릭합니다.

5.  **동작**을 클릭합니다.

6.  **모든 서비스에 대한 새 세션 금지**를 클릭합니다.

## 특정 서비스에 대한 새 세션을 금지하려면

1.  RTCUniversalServerAdmins 그룹의 구성원인 사용자 계정(또는 이와 동일한 사용자 권한을 가진 사용자 계정)이나 CsServerAdministrator 또는 CsAdministrator 역할이 할당된 사용자 계정에서 Lync Server 2013을 배포한 네트워크에 있는 컴퓨터에 로그온합니다.

2.  브라우저 창을 연 다음 Admin URL을 입력하여 Lync Server 제어판을 엽니다. Lync Server 제어판을 시작하는 데 사용할 수 있는 다양한 방법에 대한 자세한 내용은 [Lync Server 관리 도구 열기](lync-server-2013-open-lync-server-administrative-tools.md)를 참조하세요.

3.  왼쪽 탐색 모음에서 **토폴로지**를 클릭하고 **상태**를 클릭합니다.

4.  **상태** 페이지에서 시작하거나 중지할 서비스를 실행 중인 컴퓨터를 찾기 위해 필요한 경우 목록을 정렬하거나 검색한 다음 해당 서비스를 클릭합니다.

5.  **속성**을 클릭합니다.

6.  필요한 경우 서비스 목록을 정렬하고 새 세션을 금지할 서비스를 클릭합니다.

7.  **동작**을 클릭합니다.

8.  **서비스에 대한 새 세션 금지**를 클릭합니다.

9.  **닫기**를 클릭합니다.

## 참고 항목

#### 기타 리소스

[Lync Server 2013 토폴로지 관리](lync-server-2013-managing-the-lync-server-topology.md)

