---
title: Lync Server에 사용자 계정 추가 및 사용
TOCTitle: Lync Server에 사용자 계정 추가 및 사용
ms:assetid: 1edd1c1c-307d-450b-abea-33aaf56bdf13
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg520961(v=OCS.15)
ms:contentKeyID: 49303009
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Lync Server에 사용자 계정 추가 및 사용

 

_**마지막으로 수정된 항목:** 2012-11-02_

Active Directory 사용자 및 컴퓨터에서 사용자 계정을 사용하도록 설정한 후에는 Lync Server 제어판을 사용하여 Lync Server에 Active Directory 사용자를 추가함으로써 새 Lync Server 2013 사용자 계정을 만들고 사용하도록 설정할 수 있습니다.

## 새 Lync Server 사용자를 추가하고 사용하도록 설정하려면

1.  CsUserAdministrator 역할 또는 CsAdministrator 역할에 할당된 사용자 계정에서 내부 배포된 컴퓨터에 로그온합니다.

2.  브라우저 창을 연 다음 Admin URL을 입력하여 Lync Server 제어판을 엽니다. Lync Server 제어판을 시작하는 데 사용할 수 있는 다양한 방법에 대한 자세한 내용은 [Lync Server 관리 도구 열기](lync-server-2013-open-lync-server-administrative-tools.md)를 참조하세요.

3.  왼쪽 탐색 모음에서 **사용자**를 클릭합니다.

4.  **사용자 사용**을 클릭합니다.

5.  **새 Lync Server 사용자** 대화 상자에서 **추가**를 클릭합니다.

6.  **사용자 검색** 상자에 원하는 Active Directory 사용자 계정의 이름, 표시 이름, 성, SAM(보안 계정 관리자) 계정 이름, 전자 메일 주소, UPN(사용자 계정 이름) 또는 전화 번호를 모두 또는 일부분 입력하고 **찾기**를 클릭합니다.

7.  표에서 Lync Server에 추가할 계정을 선택하고 **확인**을 클릭합니다.

8.  풀에 사용자를 할당하고, 세부 정보를 추가로 지정하고, 원하는 사용자에게 정책을 할당한 후에 **사용**을 클릭합니다.

## 참고 항목

#### 작업

[사용자 계정에서 Lync Server를 사용하거나 사용하지 않도록 설정](lync-server-2013-disable-or-re-enable-user-account-for-lync-server.md)  
[Lync Server에서 사용자 계정 제거](lync-server-2013-remove-a-user-account-from-lync-server.md)  

#### 기타 리소스

[Lync Server 2013에 사용자 사용 또는 사용 안 함](lync-server-2013-enabling-and-disabling-users-for-lync-server.md)

