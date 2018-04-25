---
title: 서비스에 대한 세션 방지
TOCTitle: 서비스에 대한 세션 방지
ms:assetid: 4b541c72-cdc1-4f86-a5a8-c43c24f41d8b
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/JJ688049(v=OCS.15)
ms:contentKeyID: 49885756
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# 서비스에 대한 세션 방지

 

_**마지막으로 수정된 항목:** 2012-10-04_

Microsoft Lync Server 2010 제어판을 사용하여 특정 컴퓨터에서 모든 Lync Server 2010 서비스의 새 세션이 실행되지 않도록 하거나 특정 Lync Server 2010 서비스의 새 세션을 금지할 수 있습니다.

## 컴퓨터의 모든 Lync Server 서비스에 대한 새 세션을 금지하려면

1.  RTCUniversalServerAdmins 그룹의 구성원인 사용자 계정(또는 이와 동일한 사용자 권한을 가진 사용자 계정)이나 CsServerAdministrator 또는 CsAdministrator 역할이 할당된 사용자 계정에서 Lync Server 2013을 배포한 네트워크에 있는 컴퓨터에 로그온합니다.

2.  Lync Server 제어판을 엽니다.

3.  왼쪽 탐색 모음에서 **토폴로지** 를 클릭하고 **상태** 를 클릭합니다.

4.  **상태** 페이지에서 새 세션을 금지할 서비스를 실행 중인 컴퓨터를 찾기 위해 필요한 경우 목록을 정렬하거나 검색한 다음 해당 컴퓨터를 클릭합니다.

5.  **동작** 을 클릭합니다.

6.  **모든 서비스에 대한 새 세션 금지** 를 클릭합니다.

## 특정 서비스에 대한 새 세션을 금지하려면

1.  RTCUniversalServerAdmins 그룹의 구성원인 사용자 계정(또는 이와 동일한 사용자 권한을 가진 사용자 계정)이나 CsServerAdministrator 또는 CsAdministrator 역할이 할당된 사용자 계정에서 Lync Server 2013을 배포한 네트워크에 있는 컴퓨터에 로그온합니다.

2.  Lync Server 제어판을 엽니다.

3.  왼쪽 탐색 모음에서 **토폴로지** 를 클릭하고 **상태** 를 클릭합니다.

4.  **상태** 페이지에서 시작하거나 중지할 서비스를 실행 중인 컴퓨터를 찾기 위해 필요한 경우 목록을 정렬하거나 검색한 다음 해당 서비스를 클릭합니다.

5.  **속성** 을 클릭합니다.

6.  필요한 경우 서비스 목록을 정렬하고 새 세션을 금지할 서비스를 클릭합니다.

7.  **동작** 을 클릭합니다.

8.  **서비스에 대한 새 세션 금지** 를 클릭합니다.

9.  **닫기** 를 클릭합니다.

