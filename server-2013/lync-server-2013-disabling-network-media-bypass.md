---
title: 네트워크 미디어 바이패스 사용 안 함
TOCTitle: 네트워크 미디어 바이패스 사용 안 함
ms:assetid: 936d2678-d712-4589-b172-b5793013652f
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/JJ688141(v=OCS.15)
ms:contentKeyID: 49885876
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# 네트워크 미디어 바이패스 사용 안 함

 

_**마지막으로 수정된 항목:** 2012-10-15_

미디어 바이패스 설정은 Microsoft Lync Server 2013 배포에 전역으로 적용됩니다. 미디어 바이패스는 통화가 중재 서버를 바이패스하도록 허용합니다. 미디어 바이패스를 사용하는 경우에 대한 자세한 내용은 계획 섹션의 [Lync Server 2013의 미디어 바이패스 계획](lync-server-2013-planning-for-media-bypass.md)를 참조하십시오. Lync Server 제어판에서 미디어 바이패스를 사용하지 않도록 설정할 수 있습니다. 미디어 바이패스를 사용하도록 설정하고 구성하는 방법에 대한 자세한 내용은 [네트워크 미디어 바이패스 사용](lync-server-2013-enabling-network-media-bypass.md)을 참조하십시오.

## 미디어 바이패스를 사용하지 않도록 설정하려면

1.  RTCUniversalServerAdmins 그룹의 구성원(또는 이와 동일한 사용자 권한을 가진 사용자 계정) 또는 CsAdministrator 역할이 할당된 사용자 계정에서 내부 배포된 컴퓨터에 로그온합니다.

2.  브라우저 창을 연 다음 Admin URL을 입력하여 Lync Server 제어판을 엽니다. Lync Server 제어판을 시작하는 데 사용할 수 있는 다양한 방법에 대한 자세한 내용은 [Lync Server 관리 도구 열기](lync-server-2013-open-lync-server-administrative-tools.md)를 참조하세요.

3.  왼쪽 탐색 모음에서 **네트워크 구성**을 클릭하고 **전역**을 클릭합니다.

4.  **전역** 페이지에서 **전역** 구성을 클릭합니다. 구성은 항상 하나뿐이며 이름은 항상 전역입니다.

5.  **편집** 메뉴에서 **자세히 보기**를 클릭합니다.

6.  **전역 설정 편집** 페이지에서 **미디어 바이패스 사용** 확인란의 선택을 취소합니다.

7.  **커밋**을 클릭하여 변경 내용을 저장합니다.

## 참고 항목

#### 작업

[네트워크 미디어 바이패스 사용](lync-server-2013-enabling-network-media-bypass.md)

