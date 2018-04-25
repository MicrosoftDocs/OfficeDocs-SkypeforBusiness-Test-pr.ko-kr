---
title: 'Lync Server 2013: 음성 경로 구성 파일 가져오기'
TOCTitle: 음성 경로 구성 파일 가져오기
ms:assetid: 4bac05e5-ed8b-4f10-96b0-b8a65ff356ec
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg398301(v=OCS.15)
ms:contentKeyID: 49303557
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Lync Server 2013에서 음성 경로 구성 파일 가져오기

 

_**마지막으로 수정된 항목:** 2012-11-01_

음성 라우팅 구성을 게시하지 않고 저장하려면 다음 단계를 통해 Lync Server 제어판 구성 내보내기 및 가져오기 명령을 사용하여 음성 라우팅 구성에 대한 스냅숏을 저장하고 검색할 수 있습니다. 음성 라우팅 구성 파일(.vcfg)을 가져왔지만 그 사이에 서버에서 음성 라우팅 구성이 변경된 경우 음성 라우팅에 대해 커밋되지 않은 변경 내용이 있다는 내용이 Lync Server 제어판에 있는 **음성 라우팅** 그룹의 페이지에 표시됩니다. 커밋되지 않은 이러한 변경 내용으로 인해 두 구성 간 차이가 발생하며, 이러한 차이를 조정해야 합니다.

그룹 내부의 페이지에서 설정에 대해 커밋되지 않은 변경 내용이 있을 경우 이러한 변경 내용은 내보낸 음성 구성 파일(.vcfg)에 저장됩니다. 따라서 변경 내용을 게시하기 전에 여러 세션 중에 음성 라우팅 구성을 변경할 수 있습니다.

## 음성 라우팅 구성을 가져오려면

1.  RTCUniversalServerAdmins 그룹의 구성원이나 CsVoiceAdministrator, CsServerAdministrator 또는 CsAdministrator 역할의 구성원으로 컴퓨터에 로그온합니다. 자세한 내용은 [Lync Server 2013에서 설치 권한 위임](lync-server-2013-delegate-setup-permissions.md)을 참조하세요.

2.  브라우저 창을 연 다음 Admin URL을 입력하여 Lync Server 제어판을 엽니다. Lync Server 제어판을 시작하는 데 사용할 수 있는 다양한 방법에 대한 자세한 내용은 [Lync Server 관리 도구 열기](lync-server-2013-open-lync-server-administrative-tools.md)를 참조하세요.

3.  왼쪽 탐색 모음에서 **음성 라우팅** 을 클릭합니다.

4.  **동작** 메뉴에서 **구성 가져오기** 를 클릭합니다.

5.  가져올 구성 파일을 찾아 **열기** 를 클릭합니다.

6.  **커밋** , **모두 커밋** 을 차례로 클릭합니다.
    

    > [!NOTE]
    > 음성 구성 파일을 가져올 때마다 <STRONG>모두 커밋</STRONG> 명령을 실행하여 구성 변경 내용을 게시해야 합니다. 자세한 내용은 작업 설명서에서 <A href="lync-server-2013-publish-pending-changes-to-the-voice-routing-configuration.md">Lync Server 2013에서 음성 라우팅 구성에 보류 중인 변경 사항 게시</A>를 참조하십시오.



## 참고 항목

#### 작업

[Lync Server 2013에서 음성 경로 구성 파일 내보내기](lync-server-2013-export-a-voice-route-configuration-file.md)  
[Lync Server 2013에서 음성 라우팅 구성에 보류 중인 변경 사항 게시](lync-server-2013-publish-pending-changes-to-the-voice-routing-configuration.md)

