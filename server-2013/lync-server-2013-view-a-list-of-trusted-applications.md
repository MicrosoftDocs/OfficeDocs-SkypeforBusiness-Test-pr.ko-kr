---
title: 신뢰할 수 있는 응용 프로그램 목록 보기
TOCTitle: 신뢰할 수 있는 응용 프로그램 목록 보기
ms:assetid: f09300b3-67cf-4e70-a51a-23d62479b913
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg182604(v=OCS.15)
ms:contentKeyID: 49305479
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# 신뢰할 수 있는 응용 프로그램 목록 보기

 

_**마지막으로 수정된 항목:** 2012-09-21_

Lync Server 2013 제어판을 사용하여 Lync Server 2013 환경에 배포된 신뢰할 수 있는 응용 프로그램 목록을 볼 수 있습니다. 신뢰할 수 있는 응용 프로그램은 Lync Server 2013에서 신뢰하는 Microsoft UCMA(Unified Communications Managed API) 3.0 Core SDK에 기준한 응용 프로그램이며, 아래 목록에 이 트러스트 관계가 요약되어 있습니다.

  - 신뢰할 수 있는 응용 프로그램은 Lync Server에서 인증을 시도하지 않습니다.

  - 신뢰할 수 있는 응용 프로그램은 SIP 트랜잭션, 연결 또는 발신 VoIP(Voice over Internet Protocol) 통화에 대해 Lync Server에서 제한하지 않습니다.

  - 신뢰할 수 있는 응용 프로그램은 사용자를 가장할 수 있으며 명단에 표시되지 않아도 회의에 참가할 수 있습니다.

  - 신뢰할 수 있는 응용 프로그램은 가용성 및 복구 가능성이 높습니다.

Lync Server 제어판에서 응용 프로그램 이름, 응용 프로그램이 실행되는 풀 및 응용 프로그램에서 사용하는 포트 등을 확인할 수 있습니다.

## 신뢰할 수 있는 응용 프로그램 목록을 보려면

1.  CsServerAdministrator, CsAdministrator, CsHelpDesk 또는 CsViewOnlyAdministrator 역할이 할당된 사용자 계정에서 내부 배포된 컴퓨터에 로그온합니다. Lync Server 2013에서 사용 가능한 미리 정의된 관리 역할에 대한 자세한 내용은 [Lync Server 2013의 역할 기반 액세스 제어 계획](lync-server-2013-planning-for-role-based-access-control.md)을 참조하세요.

2.  브라우저 창을 연 다음 Admin URL을 입력하여 Lync Server 제어판을 엽니다. Lync Server 제어판을 시작하는 데 사용할 수 있는 다양한 방법에 대한 자세한 내용은 [Lync Server 관리 도구 열기](lync-server-2013-open-lync-server-administrative-tools.md)를 참조하세요.

3.  왼쪽 탐색 표시줄에서 **토폴로지**를 클릭한 다음 **신뢰할 수 있는 응용 프로그램**을 클릭합니다.

4.  필요한 경우 **신뢰할 수 있는 응용 프로그램** 페이지에서 열 머리글을 클릭하여 응용 프로그램을 정렬할 수 있습니다.

## 참고 항목

#### 기타 리소스

[Lync Server 2013 토폴로지 관리](lync-server-2013-managing-the-lync-server-topology.md)

