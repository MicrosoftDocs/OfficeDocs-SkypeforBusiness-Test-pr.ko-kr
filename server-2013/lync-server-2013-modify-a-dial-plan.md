---
title: 'Lync Server 2013: 다이얼 플랜 수정'
TOCTitle: 다이얼 플랜 수정
ms:assetid: a91f02df-cf60-40cf-82fe-e0342c118b91
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg412797(v=OCS.15)
ms:contentKeyID: 49304662
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Lync Server 2013에서 다이얼 플랜 수정

 

_**마지막으로 수정된 항목:** 2012-11-01_

기존의 다이얼 플랜을 수정하려면 다음 절차의 단계를 수행하십시오. 새 다이얼 플랜을 만들려는 경우 [Lync Server 2013에서 다이얼 플랜 만들기](lync-server-2013-create-a-dial-plan.md)를 참조하십시오.

## 다이얼 플랜을 수정하려면

1.  RTCUniversalServerAdmins 그룹의 구성원이나 CsVoiceAdministrator, CsServerAdministrator 또는 CsAdministrator 역할의 구성원으로 컴퓨터에 로그온합니다. 자세한 내용은 [Lync Server 2013에서 설치 권한 위임](lync-server-2013-delegate-setup-permissions.md)을 참조하세요.

2.  브라우저 창을 연 다음 Admin URL을 입력하여 Lync Server 제어판을 엽니다. Lync Server 제어판을 시작하는 데 사용할 수 있는 다양한 방법에 대한 자세한 내용은 [Lync Server 관리 도구 열기](lync-server-2013-open-lync-server-administrative-tools.md)를 참조하세요.

3.  왼쪽 탐색 모음에서 **음성 라우팅** 을 클릭한 다음 **다이얼 플랜** 을 클릭합니다.

4.  **다이얼 플랜** 페이지에서 다이얼 플랜 이름을 두 번 클릭합니다.
    

    > [!NOTE]
    > 다이얼 플랜 범위 및 이름은 다이얼 플랜이 만들어질 때 설정되었습니다. 이러한 설정은 변경할 수 없습니다.



5.  (선택 사항) **다이얼 플랜 편집** 에서 **이름** 필드에 나타나는 것과 동일한 이름으로 미리 채워진 **단순한 이름** 필드를 편집하여 다이얼 플랜을 적용할 사이트, 서비스 또는 사용자를 나타내는 자세한 이름을 지정합니다.
    

    > [!IMPORTANT]
    > <STRONG>단순한 이름</STRONG>은 Lync Server 2013 배포 내 모든 다이얼 플랜 간에 고유해야 합니다. 256 유니코드 문자를 초과할 수 없으며, 각각의 문자는 알파벳 문자 또는 숫자, 하이픈(-), 마침표(.), 더하기 기호(+) 또는 밑줄(_)이 될 수 있습니다.<BR><STRONG>단순한 이름</STRONG> 필드에는 공백이 허용되지 않습니다.



6.  (선택 사항) **설명** 필드에 다이얼 플랜에 대한 자세한 정보를 입력합니다.

7.  (선택 사항) 이 다이얼 플랜을 전화 접속 액세스 번호의 지역으로 사용하려면 **전화 접속 회의 지역** 을 지정합니다. 전화 접속 액세스 번호에 이 다이얼 플랜을 사용하지 않으려면 이 필드를 비워 둡니다.
    

    > [!NOTE]
    > 전화 접속 회의 액세스 번호를 하나 이상의 다이얼 플랜과 연결하려면 전화 접속 회의 지역이 필요합니다.



8.  (선택 사항) 사용자가 외부 회선에 연결하기 위해 하나 이상의 추가 선행 번호(예: 9)를 눌러야 하는 경우에만 **외부 액세스 접두사** 필드에 값을 지정합니다. 최대 4자의 접두사 값을 입력할 수 있습니다(즉, \#, \*, 0-9).
    

    > [!NOTE]
    > 외부 액세스 접두사를 지정하면 접두사를 수용하기 위해 새 정규화 규칙을 만들 필요가 없습니다.



9.  다이얼 플랜의 정규화 규칙을 연결하고 구성합니다.
    
      - Enterprise Voice 배포에서 사용할 수 있는 모든 정규화 규칙 목록에서 하나 이상의 규칙을 선택하려면 **선택** 을 클릭합니다. **정규화 규칙 선택** 대화 상자에서 다이얼 플랜과 연결할 규칙을 강조한 다음 **확인** 을 클릭합니다.
    
      - 새 정규화 규칙을 정의하고 다이얼 플랜과 연결하려면 **새로 만들기** 를 클릭합니다. 새 규칙 정의에 대한 자세한 내용은 [Lync Server 2013에서 정규화 규칙 정의](lync-server-2013-defining-normalization-rules.md)를 참고하세요.
    
      - 다이얼 플랜과 이미 연결된 정규화 규칙을 편집하려면 규칙 이름을 강조하고 **자세한 정보 표시** 를 클릭합니다. 규칙 편집에 대한 자세한 내용은 [Lync Server 2013에서 정규화 규칙 정의](lync-server-2013-defining-normalization-rules.md)를 참고하세요.
    
      - 기존의 정규화 규칙을 복사한 후 이를 기반으로 새 규칙을 정의하려면 규칙 이름을 강조하고 **복사** 를 클릭한 다음 **붙여넣기** 를 클릭합니다. 복사본 편집에 대한 자세한 내용은 [Lync Server 2013에서 정규화 규칙 정의](lync-server-2013-defining-normalization-rules.md)를 참고하세요.
    
      - 정규화 규칙을 다이얼 플랜에서 제거하려면 규칙 이름을 강조하고 **제거** 를 클릭합니다.
    

    > [!NOTE]
    > 각각의 다이얼 플랜마다 적어도 하나의 정규화 규칙이 연결되어 있어야 합니다. 다이얼 플랜에 필요한 모든 정규화 규칙을 확인하는 방법에 대한 자세한 내용은 계획 설명서에서 <A href="lync-server-2013-dial-plans-and-normalization-rules.md">Lync Server 2013의 다이얼 플랜 및 정규화 규칙</A>을 참조하십시오.



10. 다이얼 플랜의 정규화 규칙이 올바른 순서로 정렬되어 있는지 확인합니다. 목록에서 규칙의 위치를 변경하려면 규칙 이름을 강조 표시하고 위쪽 또는 아래쪽 화살표를 클릭합니다.
    

    > [!IMPORTANT]
    > Lync Server는 정규화 규칙 목록을 위에서 아래로 통과하고 전화를 건 번호와 일치하는 첫 번째 규칙을 사용합니다. 전화를 건 번호가 둘 이상의 정규화 규칙과 일치하도록 다이얼 플랜을 구성하는 경우 더 제한적인 규칙을 덜 제한적인 규칙보다 위에 정렬되게 하세요.<BR>기본값 <STRONG>Keep All</STRONG> 정규화 규칙 <STRONG>^(\d{11})$</STRONG> 는 모든 11자리 번호와 일치합니다. 예를 들어 1425로 시작하는 11자리 번호와 일치하는 정규화 규칙을 추가하는 경우 <STRONG>Keep All</STRONG> 이 덜 제한적인 <STRONG>^(1425\d{7})$</STRONG> 규칙 아래에 정렬되게 하십시오.



11. (선택 사항) 다이얼 플랜을 테스트할 번호를 입력한 다음 **이동** 을 클릭합니다. 테스트 결과가 **테스트할 번호 입력** 아래에 표시됩니다.
    

    > [!NOTE]
    > 아직 테스트를 통과하지 않은 다이얼 플랜을 저장한 다음 나중에 다시 구성할 수 있습니다. 자세한 내용은 <A href="lync-server-2013-test-voice-routing.md">Lync Server 2013에서 음성 라우팅 테스트</A>를 참고하세요.



12. **확인** 을 클릭합니다.

13. **다이얼 플랜** 페이지에서 **커밋** 을 클릭한 다음 **모두 커밋** 을 클릭합니다.
    

    > [!NOTE]
    > 다이얼 플랜을 만들거나 수정할 때마다 <STRONG>모두 커밋</STRONG> 명령을 실행하며 구성 변경을 게시해야 합니다. 자세한 내용은 작업 설명서에서 <A href="lync-server-2013-publish-pending-changes-to-the-voice-routing-configuration.md">Lync Server 2013에서 음성 라우팅 구성에 보류 중인 변경 사항 게시</A>를 참조하십시오.



## 참고 항목

#### 작업

[Lync Server 2013에서 다이얼 플랜 만들기](lync-server-2013-create-a-dial-plan.md)  
[Lync Server 2013에서 음성 라우팅 구성에 보류 중인 변경 사항 게시](lync-server-2013-publish-pending-changes-to-the-voice-routing-configuration.md)  

#### 기타 리소스

[Lync Server 2013에서 정규화 규칙 정의](lync-server-2013-defining-normalization-rules.md)

