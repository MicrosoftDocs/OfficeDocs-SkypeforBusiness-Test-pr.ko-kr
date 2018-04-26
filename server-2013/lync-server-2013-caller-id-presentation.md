---
title: 'Lync Server 2013: 발신자 번호 표시'
TOCTitle: 발신자 번호 표시
ms:assetid: 6a643961-a0a1-41d1-96ba-6c428a89d82e
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/JJ204980(v=OCS.15)
ms:contentKeyID: 49303924
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Lync Server 2013의 발신자 번호 표시

 

_**마지막으로 수정된 항목:** 2013-02-22_

Lync Server 2010을 사용하여 전화받은 대상(즉, 수신 전화 번호)은 E.164 형식에서 *트렁크 피어* (즉, 관련 게이트웨이, PBX(Private Branch Exchange) 또는 SIP 트렁크)에서 필요한 지역 전화 번호 형식으로 변환될 수 있습니다. 그러려면 트렁크 피어로 라우팅되기 전에 요청 URI를 변환하는 변환 규칙을 하나 이상 정의해야 합니다.

Lync Server 2013에는 발신자의 전화 번호(즉, 발신자가 호출할 때 사용하는 전화 번호)를 E.164 형식에서 트렁크 피어에 필요한 로컬 전화 번호 형식으로 변환할 수 있는 옵션도 제공됩니다. 예를 들어 전화 번호 문자열 시작 부분에서 +44를 제거하고 이를 0144로 바꾸는 변환 규칙을 작성할 수 있습니다.

**Lync Server 제어판을 사용하여 발신자 번호를 구성하려면**

1.  RTCUniversalServerAdmins 그룹의 구성원이나 CsVoiceAdministrator, CsServerAdministrator 또는 CsAdministrator 역할의 구성원으로 컴퓨터에 로그온합니다. 자세한 내용은 [Lync Server 2013에서 설치 권한 위임](lync-server-2013-delegate-setup-permissions.md)을 참조하세요.

2.  브라우저 창을 연 다음 Admin URL을 입력하여 Lync Server 제어판을 엽니다. Lync Server 제어판을 시작하는 데 사용할 수 있는 다양한 방법에 대한 자세한 내용은 [Lync Server 관리 도구 열기](lync-server-2013-open-lync-server-administrative-tools.md)를 참조하세요.

3.  왼쪽 탐색 모음에서 **음성 라우팅** 을 클릭한 다음 **트렁크 구성** 을 클릭합니다.

4.  **트렁크 구성** 페이지에서 기존 트렁크(예: **전역** 트렁크)를 두 번 클릭하여 **트렁크 구성 편집** 대화 상자를 표시합니다.

5.  발신자 번호 표시를 구성하려면
    
      - Enterprise Voice 배포에서 사용 가능한 모든 변환 규칙 목록에서 하나 이상의 규칙을 선택하려면 **선택** 을 클릭합니다. **발신 번호 변환 규칙** 에서 트렁크와 연결할 규칙을 클릭한 후 **확인** 을 클릭합니다.
    
      - 새 변환 규칙을 정의하고 트렁크와 연결하려면 **새로 만들기** 를 클릭합니다. 새 규칙을 정의하는 방법에 대한 자세한 내용은 배포 설명서에서 [Lync Server 2013에서 변환 규칙 정의](lync-server-2013-defining-translation-rules.md)를 참조하십시오.
    
      - 트렁크와 이미 연결된 변환 규칙을 편집하려면 규칙 이름을 클릭한 다음 **자세한 정보 표시** 를 클릭합니다. 자세한 내용은 배포 설명서에서 [Lync Server 2013에서 변환 규칙 정의](lync-server-2013-defining-translation-rules.md)를 참조하십시오.
    
      - 기존 변환 규칙을 복사하여 새 규칙을 정의하는 시작점으로 사용하려면 규칙 이름을 클릭하고 **복사** 를 클릭한 다음 **붙여넣기** 를 클릭합니다. 자세한 내용은 [Lync Server 2013에서 변환 규칙 정의](lync-server-2013-defining-translation-rules.md)를 참조하십시오.
    
      - 트렁크에서 변환 규칙을 제거하려면 규칙 이름을 강조 표시하고 **제거** 를 클릭합니다.
    

    > [!WARNING]
    > 연결된 트렁크 피어에서 변환 규칙을 구성한 경우에는 변환 규칙을 트렁크와 연결하지 마십시오. 두 규칙이 충돌할 수 있습니다.


