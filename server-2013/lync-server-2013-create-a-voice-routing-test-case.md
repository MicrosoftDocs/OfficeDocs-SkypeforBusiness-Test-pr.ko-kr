---
title: 'Lync Server 2013: 음성 라우팅 테스트 사례 만들기'
TOCTitle: 음성 라우팅 테스트 사례 만들기
ms:assetid: 43a07a5b-2f20-462a-81e5-d628c18391e0
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg425935(v=OCS.15)
ms:contentKeyID: 49303468
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Lync Server 2013에서 음성 라우팅 테스트 사례 만들기

 

_**마지막으로 수정된 항목:** 2014-02-07_

## 테스트 사례를 만들려면

1.  RTCUniversalServerAdmins 그룹의 구성원이나 CsVoiceAdministrator, CsServerAdministrator 또는 CsAdministrator 역할의 구성원으로 컴퓨터에 로그온합니다. 자세한 내용은 [Lync Server 2013에서 설치 권한 위임](lync-server-2013-delegate-setup-permissions.md)을 참조하세요.

2.  브라우저 창을 연 다음 Admin URL을 입력하여 Lync Server 제어판을 엽니다. Lync Server 제어판을 시작하는 데 사용할 수 있는 다양한 방법에 대한 자세한 내용은 [Lync Server 관리 도구 열기](lync-server-2013-open-lync-server-administrative-tools.md)를 참조하세요.

3.  왼쪽 탐색 모음에서 **음성 라우팅** 을 클릭하고 **음성 라우팅 테스트** 를 클릭합니다.

4.  **음성 라우팅 테스트** 페이지에서 **새로 만들기** 를 클릭하여 새 테스트 사례를 만듭니다.

5.  **이름** 에 테스트 사례의 고유한 이름을 입력합니다.
    
    이름은 Enterprise Voice 배포의 모든 음성 라우팅 테스트 사례에서 고유해야 합니다. 이름은 길이가 최대 32자이고 영숫자 문자와 백슬래시(\\), 마침표(.) 또는 밑줄(\_)을 포함할 수 있습니다.

6.  **테스트를 위해 전화를 건 번호** 에 이 테스트 사례에 대해 지정하는 라우팅 구성을 테스트하기 위해 사용하려는 전화를 건 번호를 입력합니다. 다이얼 플랜 및 음성 정책에 따라 이 번호는 정규화되어 출력으로 표시됩니다.

7.  **다이얼 플랜** 목록에서 테스트를 실행할 때 사용할 다이얼 플랜을 선택합니다. 기본값은 전역 다이얼 플랜입니다.

8.  **음성 정책** 목록에서 테스트를 실행할 때 사용할 음성 정책을 선택합니다. 기본값은 전역 음성 정책입니다.

9.  **예상 변환** 에 변환 후 표시하려는 형식으로 전화 번호를 입력합니다. 이 값은 선택한 다이얼 플랜에서 일치하는 첫 번째 정규화 규칙으로 현재 테스트 중인 전화 번호가 변환된 이후의 값입니다. 테스트 사례를 실행할 때 테스트 중인 번호가 **예상 변환** 의 값으로 표시되지 않으면 테스트가 실패합니다.

10. (선택 사항) **예상 PSTN 사용** 목록에서 지정된 다이얼 플랜 및 음성 정책을 기반으로 테스트 사례를 실행할 때 사용할 PSTN(공중 전화망) 사용 레코드를 선택할 수 있습니다. 다른 PSTN 사용 레코드가 사용된 경우 테스트가 실패합니다.

11. (선택 사항) **예상 경로** 목록에서는 지정된 다이얼 플랜 및 음성 정책을 기반으로 테스트 사례를 실행할 때 사용될 것으로 예상되는 음성 라우팅을 선택할 수 있습니다. 다른 음성 라우팅이 사용되는 경우에는 테스트가 실패합니다.

12. (선택 사항) **실행** 을 클릭하여 테스트 사례를 실행합니다. 결과는 페이지의 아래쪽 패널에 표시됩니다.

13. **확인** 을 클릭합니다.

14. **커밋** , **모두 커밋** 을 차례로 클릭합니다.
    

    > [!NOTE]
    > 음성 라우팅 테스트 사례를 만들 때마다 <STRONG>모두 커밋</STRONG> 명령을 실행하여 구성 변경을 게시해야 합니다. 자세한 내용은 운영 설명서에서 <A href="lync-server-2013-publish-pending-changes-to-the-voice-routing-configuration.md">Lync Server 2013에서 음성 라우팅 구성에 보류 중인 변경 사항 게시</A>를 참조하십시오.

    
    더하기 기호로 시작하는 테스트 표준화 전화 번호(예: +12065551219)에서 다이얼 플랜이 사용되고 있다면 해당 플랜으로 인해 음성 라우팅 테스트가 실패할 수 있습니다. 다이얼 플랜과 음성 라우팅이 작동하겠지만 실제로는 Test-CsDialPlan이 성공하는 것입니다. 그러나 음성 라우팅 테스트는 실패할 수 있습니다. 음성 라우팅을 테스트하는 경우 바로 이 점에 유의해야 합니다.

## 참고 항목

#### 작업

[Lync Server 2013에서 음성 라우팅 테스트 사례 내보내기](lync-server-2013-export-voice-routing-test-cases.md)  
[Lync Server 2013에서 음성 라우팅 테스트 사례 가져오기](lync-server-2013-import-voice-routing-test-cases.md)  

#### 기타 리소스

[Lync Server 2013에서 다이얼 플랜 구성](lync-server-2013-configuring-dial-plans.md)  
[Lync Server 2013에서 음성 정책, PSTN 사용 레코드 및 음성 경로 구성](lync-server-2013-configuring-voice-policies-pstn-usage-records-and-voice-routes.md)

