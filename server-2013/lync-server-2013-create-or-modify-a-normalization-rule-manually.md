---
title: 'Lync Server 2013: 수동으로 정규화 규칙 만들기 또는 수정'
TOCTitle: 수동으로 정규화 규칙 만들기 또는 수정
ms:assetid: fc0335e6-8830-4cfb-8c64-6aeb98c0a992
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg413074(v=OCS.15)
ms:contentKeyID: 49305618
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Lync Server 2013에서 수동으로 정규화 규칙 만들기 또는 수정

 

_**마지막으로 수정된 항목:** 2012-09-22_

정규화 규칙을 수동으로 만들거나 수정하려면 다음 단계를 수행합니다. Lync Server 제어판에서 '정규화 규칙 작성'을 사용하여 정규화 규칙을 만들거나 수정하려면 [Lync Server 2013에서 정규화 규칙 작성을 사용하여 정규화 규칙 만들기 또는 수정](lync-server-2013-create-or-modify-a-normalization-rule-by-using-build-a-normalization-rule.md)을 참조하십시오.

## 정규화 규칙을 수동으로 정의하려면

1.  RTCUniversalServerAdmins 그룹의 구성원이나 CsVoiceAdministrator, CsServerAdministrator 또는 CsAdministrator 역할의 구성원으로 컴퓨터에 로그온합니다. 자세한 내용은 [Lync Server 2013에서 설치 권한 위임](lync-server-2013-delegate-setup-permissions.md)을 참조하세요.

2.  브라우저 창을 연 다음 Admin URL을 입력하여 Lync Server 제어판을 엽니다. Lync Server 제어판을 시작하는 데 사용할 수 있는 다양한 방법에 대한 자세한 내용은 [Lync Server 관리 도구 열기](lync-server-2013-open-lync-server-administrative-tools.md)를 참조하세요.

3.  (선택 사항) [Lync Server 2013에서 다이얼 플랜 만들기](lync-server-2013-create-a-dial-plan.md) 또는 [Lync Server 2013에서 다이얼 플랜 수정](lync-server-2013-modify-a-dial-plan.md)의 단계를 수행합니다.

4.  **새 정규화 규칙** 또는 **정규화 규칙 편집** 의 **이름** 에 정규화 중인 숫자 패턴을 설명하는 이름을 입력합니다(예: 정규화 규칙의 이름을 **5DigitExtension** 으로 지정).

5.  (선택 사항) **설명** 필드에 정규화 규칙에 대한 설명을 입력합니다(예: "Translates 5-digit extensions").

6.  **정규화 규칙 작성** 에서 **편집** 을 클릭합니다.

7.  **정규식 입력** 에 다음을 입력합니다.
    
      - **다음 패턴과 일치시킴** 에서 전화 건 전화 번호와 일치시키는 데 사용할 패턴을 지정합니다.
    
      - **변환 규칙** 에서 변환된 E.164 전화 번호 형식에 대한 패턴을 지정합니다.
    
    예를 들어 **다음 패턴과 일치시킴** 에 **^(\\d{7})$** 을 입력하고 **변환 규칙** 에 **+1425$1** 을 입력한 경우 규칙에서 5550100을 +14255550100으로 정규화합니다.

8.  (선택 사항) 정규화 규칙의 결과가 조직 내부의 전화 번호가 되는 경우 **내부 확장** 을 선택합니다.

9.  (선택 사항) 정규화 규칙을 테스트할 번호를 입력한 다음 **이동** 을 클릭합니다. 테스트 결과가 **테스트할 번호 입력** 아래에 표시됩니다.
    

    > [!NOTE]
    > 아직 테스트를 통과하지 않는 정규화 규칙을 저장한 다음 나중에 다시 구성할 수 있습니다. 자세한 내용은 <A href="lync-server-2013-test-voice-routing.md">Lync Server 2013에서 음성 라우팅 테스트</A>를 참조하십시오.



10. 정규화 규칙을 저장하려면 **확인** 을 클릭합니다.

11. 다이얼 플랜을 저장하려면 **확인** 을 클릭합니다.

12. **다이얼 플랜** 페이지에서 **커밋** 을 클릭한 다음 **모두 커밋** 을 클릭합니다.
    

    > [!NOTE]
    > 정규화 규칙을 만들거나 변경할 때마다 <STRONG>모두 커밋</STRONG> 명령을 실행하여 구성 변경 내용을 게시해야 합니다. 자세한 내용은 작업 설명서에서 <A href="lync-server-2013-publish-pending-changes-to-the-voice-routing-configuration.md">Lync Server 2013에서 음성 라우팅 구성에 보류 중인 변경 사항 게시</A>를 참조하십시오.



## 참고 항목

#### 작업

[Lync Server 2013에서 정규화 규칙 작성을 사용하여 정규화 규칙 만들기 또는 수정](lync-server-2013-create-or-modify-a-normalization-rule-by-using-build-a-normalization-rule.md)  
[Lync Server 2013에서 다이얼 플랜 만들기](lync-server-2013-create-a-dial-plan.md)  
[Lync Server 2013에서 다이얼 플랜 수정](lync-server-2013-modify-a-dial-plan.md)  
[Lync Server 2013에서 음성 라우팅 구성에 보류 중인 변경 사항 게시](lync-server-2013-publish-pending-changes-to-the-voice-routing-configuration.md)  

#### 기타 리소스

[Lync Server 2013에서 음성 라우팅 테스트](lync-server-2013-test-voice-routing.md)

