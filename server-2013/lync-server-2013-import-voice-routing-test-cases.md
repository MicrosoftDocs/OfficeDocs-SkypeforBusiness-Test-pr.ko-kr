---
title: 'Lync Server 2013: 음성 라우팅 테스트 사례 가져오기'
TOCTitle: 음성 라우팅 테스트 사례 가져오기
ms:assetid: 6546e24c-9ad2-428b-92b2-63948ed0f884
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg398460(v=OCS.15)
ms:contentKeyID: 49303858
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Lync Server 2013에서 음성 라우팅 테스트 사례 가져오기

 

_**마지막으로 수정된 항목:** 2013-02-21_

테스트 사례를 사용하면 조직에서 음성 경로를 테스트할 수 있습니다. 다이얼할 번호 및 적용할 다이얼 플랜과 음성 정책 등으로 테스트 사례를 정의하면 Lync Server 2013에서 특정 조건에 따라 제공된 번호가 PSTN 네트워크로 성공적으로 라우팅되는지 확인할 수 있습니다.

Lync Server 제어판을 사용해서 만들 수 있는 테스트 사례는 일반적으로 원래 테스트 사례가 만들어졌고 실행되는 서버에만 저장됩니다. 하지만 이러한 테스트 사례를 XML 파일(.vtest 확장명)로 내보내고 다른 서버에서 가져올 수 있습니다. 이러한 방식을 통해 토폴로지의 여러 지점에 있는 서로 다른 컴퓨터에서 동일한 테스트를 실행할 수 있습니다.

## 음성 라우팅 테스트 사례를 가져오려면

1.  RTCUniversalServerAdmins 그룹의 구성원이나 CsVoiceAdministrator, CsServerAdministrator 또는 CsAdministrator 역할의 구성원으로 컴퓨터에 로그온합니다. 자세한 내용은 [Lync Server 2013에서 설치 권한 위임](lync-server-2013-delegate-setup-permissions.md)을 참조하세요.

2.  브라우저 창을 연 다음 Admin URL을 입력하여 Lync Server 제어판을 엽니다. Lync Server 제어판을 시작하는 데 사용할 수 있는 다양한 방법에 대한 자세한 내용은 [Lync Server 관리 도구 열기](lync-server-2013-open-lync-server-administrative-tools.md)를 참조하세요.

3.  왼쪽 탐색 모음에서 **음성 라우팅** 을 클릭합니다.

4.  **동작** 메뉴에서 **테스트 사례 가져오기** 를 클릭합니다.

5.  가져올 테스트 사례 파일(.vtest)을 찾아 **열기** 를 클릭합니다.

6.  **커밋** , **모두 커밋** 을 차례로 클릭합니다.
    

    > [!NOTE]
    > .vtest 파일을 가져올 때마다 <STRONG>모두 커밋</STRONG> 명령을 실행하여 테스트 사례를 게시해야 합니다. 자세한 내용은 작업 설명서에서 <A href="lync-server-2013-publish-pending-changes-to-the-voice-routing-configuration.md">Lync Server 2013에서 음성 라우팅 구성에 보류 중인 변경 사항 게시</A>를 참조하십시오.



## 참고 항목

#### 작업

[Lync Server 2013에서 음성 라우팅 테스트 사례 내보내기](lync-server-2013-export-voice-routing-test-cases.md)

