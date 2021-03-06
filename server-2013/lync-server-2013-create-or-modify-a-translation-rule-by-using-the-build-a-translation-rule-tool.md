﻿---
title: 변환 규칙 작성 도구를 사용하여 변환 규칙 만들기 또는 수정
TOCTitle: 변환 규칙 작성 도구를 사용하여 변환 규칙 만들기 또는 수정
ms:assetid: ba112df8-3bb4-48e4-a353-4bf9110ccd71
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg412909(v=OCS.15)
ms:contentKeyID: 49304844
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# 변환 규칙 작성 도구를 사용하여 변환 규칙 만들기 또는 수정

 

_**마지막으로 수정된 항목:** 2012-10-05_

**변환 규칙 작성** 도구로 값 집합을 입력하고 Lync Server 제어판에서 해당 일치 패턴 및 변환 규칙을 생성할 수 있도록 설정하여 변환 규칙을 정의하려면 다음 단계를 따릅니다. 또는 정규 표현식을 수동으로 작성하여 일치 패턴과 변환 규칙을 정의할 수 있습니다. 자세한 내용은 [수동으로 변환 규칙 만들기 또는 수정](lync-server-2013-create-or-modify-a-translation-rule-manually.md)을 참조하십시오.

## 변환 규칙 작성 도구를 사용하여 규칙을 정의하려면

1.  RTCUniversalServerAdmins 그룹의 구성원이나 CsVoiceAdministrator, CsServerAdministrator 또는 CsAdministrator 역할의 구성원으로 컴퓨터에 로그온합니다. 자세한 내용은 [Lync Server 2013에서 설치 권한 위임](lync-server-2013-delegate-setup-permissions.md)을 참조하세요.

2.  브라우저 창을 연 다음 Admin URL을 입력하여 Lync Server 제어판을 엽니다. Lync Server 제어판을 시작하는 데 사용할 수 있는 다양한 방법에 대한 자세한 내용은 [Lync Server 관리 도구 열기](lync-server-2013-open-lync-server-administrative-tools.md)를 참조하세요.

3.  변환 규칙 정의를 시작하려면 [Lync Server 2013에서 미디어 바이패스로 트렁크 구성](lync-server-2013-configure-a-trunk-with-media-bypass.md)의 10단계까지 또는 [Lync Server 2013에서 미디어 바이패스 없이 트렁크 구성](lync-server-2013-configure-a-trunk-without-media-bypass.md)의 9단계까지를 수행하십시오.

4.  **새 변환 규칙** 또는 **변환 규칙 편집** 페이지의 **이름** 아래에서 변환 대상 숫자 패턴을 설명하는 이름을 입력합니다.

5.  (선택 사항) **설명** 아래에서 변환 규칙에 대한 설명을 **미국 국제 시외 전화**와 같이 입력합니다.

6.  대화 상자의 **변환 규칙 작성** 섹션에 있는 다음 필드에 값을 입력합니다.
    
      - **시작 숫자**: (선택 사항) 패턴을 일치시킬 선행 자릿수를 지정합니다. 예를 들어 이 필드에 **+**를 입력하면 +로 시작하는 E.164 형식의 번호가 일치됩니다.
    
      - **길이**: 일치하는 패턴의 자릿수를 지정하고 패턴을 이 길이와 정확히 일치하는 번호와 일치시킬지 또는 이 길이 이상인 번호와 일치시킬지 또는 길이에 상관없이 일치시킬지 여부를 선택합니다 예를 들어 **11**을 입력하고 드롭다운 목록에서 **최소**를 선택하면 길이가 11자리 이상인 번호와 일치하게 됩니다.
    
      - **제거할 숫자**: (선택 사항) 제거할 시작 자릿수를 지정합니다. 예를 들어 **1**을 입력하면 번호 앞부분에서 **+**가 제거됩니다.
    
      - **추가할 숫자**: (선택 사항) 변환된 번호의 앞에 추가할 자릿수를 지정합니다. 예를 들어 **011**을 입력하면 규칙이 적용될 때 변환된 번호 앞에 011이 추가됩니다.
    
    이 필드에 입력한 값은 **일치시킬 패턴** 및 **변환 규칙** 필드에 적용됩니다. 예를 들어 위의 예 값을 지정한 경우 **일치시킬 패턴** 필드의 정규식 결과는 다음과 같습니다.
    
    **^\\+(\\d{9}\\d+)$**
    
    **변환 규칙** 필드에서는 변환된 번호 형식에 대한 패턴이 지정됩니다. 이 패턴은 두 부분으로 되어 있습니다.
    
      - 일치하는 패턴의 자릿수를 나타내는 값(예: **$1**)
    
      - (선택 사항) **추가할 숫자** 필드에 입력하여 번호 앞에 추가할 수 있는 값
    
    위의 예 값을 사용하면 **변환 규칙** 필드에 **011$1**이 나타납니다.
    
    이 변환 규칙이 적용되면 +441235551010이 011441235551010이 됩니다.

7.  **확인**을 클릭하여 변환 규칙을 저장합니다.

8.  **확인**을 클릭하여 트렁크 구성을 저장합니다.

9.  **트렁크 구성** 페이지에서 **커밋**을 클릭하고 **모두 커밋**을 클릭합니다.
    

    > [!NOTE]
    > 변환 규칙을 만들거나 수정할 때마다 <STRONG>모두 커밋</STRONG> 명령을 실행하여 구성 변경 내용을 게시해야 합니다. 자세한 내용은 작동 설명서에서 <A href="lync-server-2013-publish-pending-changes-to-the-voice-routing-configuration.md">Lync Server 2013에서 음성 라우팅 구성에 보류 중인 변경 사항 게시</A>를 참조하십시오.



## 참고 항목

#### 작업

[수동으로 변환 규칙 만들기 또는 수정](lync-server-2013-create-or-modify-a-translation-rule-manually.md)  
[Lync Server 2013에서 미디어 바이패스로 트렁크 구성](lync-server-2013-configure-a-trunk-with-media-bypass.md)  
[Lync Server 2013에서 미디어 바이패스 없이 트렁크 구성](lync-server-2013-configure-a-trunk-without-media-bypass.md)  
[Lync Server 2013에서 음성 라우팅 구성에 보류 중인 변경 사항 게시](lync-server-2013-publish-pending-changes-to-the-voice-routing-configuration.md)  

#### 개념

[Lync Server 2013의 전역 미디어 바이패스 옵션](lync-server-2013-global-media-bypass-options.md)

