---
title: 수동으로 변환 규칙 만들기 또는 수정
TOCTitle: 수동으로 변환 규칙 만들기 또는 수정
ms:assetid: 049d1db3-af58-48c5-be89-52e1d068a4bd
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg398099(v=OCS.15)
ms:contentKeyID: 49302661
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# 수동으로 변환 규칙 만들기 또는 수정

 

_**마지막으로 수정된 항목:** 2012-08-06_

일치하는 패턴 및 변환 규칙에 대한 정규식을 작성하여 변환 규칙을 정의하려면 다음 단계를 따르십시오. 또는 **변환 규칙 작성** 도구에서 값 집합을 입력하고 Lync Server 제어판에서 일치하는 해당 패턴과 변환 규칙을 자동으로 생성하도록 허용할 수 있습니다. 자세한 내용은 [변환 규칙 작성 도구를 사용하여 변환 규칙 만들기 또는 수정](lync-server-2013-create-or-modify-a-translation-rule-by-using-the-build-a-translation-rule-tool.md)을 참조하십시오.

## 변환 규칙을 수동으로 정의하려면

1.  RTCUniversalServerAdmins 그룹의 구성원이나 CsVoiceAdministrator, CsServerAdministrator 또는 CsAdministrator 역할의 구성원으로 컴퓨터에 로그온합니다. 자세한 내용은 [Lync Server 2013에서 설치 권한 위임](lync-server-2013-delegate-setup-permissions.md)을 참조하세요.

2.  브라우저 창을 연 다음 Admin URL을 입력하여 Lync Server 제어판을 엽니다. Lync Server 제어판을 시작하는 데 사용할 수 있는 다양한 방법에 대한 자세한 내용은 [Lync Server 관리 도구 열기](lync-server-2013-open-lync-server-administrative-tools.md)를 참조하세요.

3.  변환 규칙 정의를 시작하려면 [Lync Server 2013에서 미디어 바이패스로 트렁크 구성](lync-server-2013-configure-a-trunk-with-media-bypass.md)의 10단계까지 또는 [Lync Server 2013에서 미디어 바이패스 없이 트렁크 구성](lync-server-2013-configure-a-trunk-without-media-bypass.md)의 9단계까지를 수행하십시오.

4.  **새 변환 규칙** 또는 **변환 규칙 편집** 페이지의 **이름** 필드에 변환 대상 숫자 패턴을 설명하는 이름을 입력합니다.

5.  (선택 사항) **설명**에 변환 규칙에 대한 설명을 **미국 국제 시외 전화**와 같이 입력합니다.

6.  **변환 규칙 작성** 섹션 아래쪽의 **편집**을 클릭합니다.

7.  **정규식 입력**에 다음을 입력합니다.
    
      - **다음 패턴과 일치시킴**에 변환할 숫자와 일치시키는 데 사용할 패턴을 지정합니다.
    
      - **변환 규칙**에 변환된 숫자 형식의 패턴을 지정합니다.
    
    예를 들어 **다음 패턴과 일치시킴**에 **^\\+(\\d{9}\\d+)$** 를 입력하고 **변환 규칙**에 **011$1**을 입력하면 규칙이 +441235551010을 011441235551010으로 변환합니다.

8.  **확인**을 클릭하여 변환 규칙을 저장합니다.

9.  **확인**을 클릭하여 트렁크 구성을 저장합니다.

10. **트렁크 구성** 페이지에서 **커밋**을 클릭하고 **모두 커밋**을 클릭합니다.
    

    > [!NOTE]
    > 변환 규칙을 만들거나 수정할 때는 항상 <STRONG>모두 커밋</STRONG> 명령을 실행하여 구성 변경 내용을 게시해야 합니다. 자세한 내용은 작업 설명서에서 <A href="lync-server-2013-publish-pending-changes-to-the-voice-routing-configuration.md">Lync Server 2013에서 음성 라우팅 구성에 보류 중인 변경 사항 게시</A>를 참조하십시오.



## 참고 항목

#### 작업

[변환 규칙 작성 도구를 사용하여 변환 규칙 만들기 또는 수정](lync-server-2013-create-or-modify-a-translation-rule-by-using-the-build-a-translation-rule-tool.md)  
[Lync Server 2013에서 미디어 바이패스로 트렁크 구성](lync-server-2013-configure-a-trunk-with-media-bypass.md)  
[Lync Server 2013에서 미디어 바이패스 없이 트렁크 구성](lync-server-2013-configure-a-trunk-without-media-bypass.md)  
[Lync Server 2013에서 음성 라우팅 구성에 보류 중인 변경 사항 게시](lync-server-2013-publish-pending-changes-to-the-voice-routing-configuration.md)  

#### 개념

[Lync Server 2013의 전역 미디어 바이패스 옵션](lync-server-2013-global-media-bypass-options.md)

