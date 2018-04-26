---
title: 'Lync Server 2013: 사용자가 Enterprise Voice를 사용할 수 있도록 설정'
TOCTitle: 사용자가 Enterprise Voice를 사용할 수 있도록 설정
ms:assetid: f252b23b-9641-4160-aa81-bf06dc2eced3
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg413011(v=OCS.15)
ms:contentKeyID: 49305494
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Lync Server 2013에서 사용자가 Enterprise Voice를 사용할 수 있도록 설정

 

_**마지막으로 수정된 항목:** 2012-11-01_

하나 이상의 중재 서버에 대한 파일을 설치하고, 아웃바운드 통화 라우팅을 구성한 다음, 선택적으로 하나 이상의 고급 Enterprise Voice 기능을 배포한 후 다음 절차를 사용하여 사용자가 Enterprise Voice를 통해 전화를 걸 수 있도록 설정할 수 있습니다.


> [!NOTE]
> 다음 절차 중 첫 번째 단계만 Lync Server 제어판을 사용하여 수행할 수 있습니다. 나머지 절차는 Lync Server 관리 셸만 사용할 수 있습니다.



  - Enterprise Voice를 사용하도록 사용자 계정을 설정합니다.

  - (선택 사항) 사용자 계정에 사용자별 음성 정책을 할당합니다.

  - (선택 사항) 사용자 계정에 사용자별 다이얼 플랜을 할당합니다.

## Enterprise Voice를 사용하도록 사용자 계정을 설정하려면

1.  CsUserAdministrator 역할 또는 CsAdministrator 역할에 할당된 사용자 계정에서 내부 배포된 컴퓨터에 로그온합니다.

2.  브라우저 창을 연 다음 Admin URL을 입력하여 Lync Server 제어판을 엽니다. Lync Server 제어판을 시작하는 데 사용할 수 있는 다양한 방법에 대한 자세한 내용은 [Lync Server 관리 도구 열기](lync-server-2013-open-lync-server-administrative-tools.md)를 참조하세요.

3.  왼쪽 탐색 모음에서 **사용자** 를 클릭합니다.

4.  **사용자 검색** 상자에 사용하도록 설정할 사용자 계정의 표시 이름, 이름, 성, SAM(보안 계정 관리자) 계정 이름, SIP 주소 또는 줄 URI(Uniform Resource Identifier)를 모두 또는 첫부분을 입력하고 **찾기** 를 클릭합니다.

5.  테이블에서 Enterprise Voice를 사용하도록 설정할 사용자 계정을 클릭합니다.

6.  **편집** 메뉴에서 **자세한 정보 표시** 를 클릭합니다.

7.  **Lync Server 사용자 편집** 페이지의 **전화 통신** 아래에서 **Enterprise Voice** 를 클릭합니다.

8.  **줄 URI** 를 클릭하고 정규화된 고유 전화 번호(예: tel:+14255550200)를 입력합니다.

9.  **커밋** 을 클릭합니다.

Enterprise Voice를 사용하도록 사용자를 설정하는 단계를 마치려면 사용자에게 전역(기본적으로 할당됨) 수준에서든 사용자 수준에서든 음성 정책 및 다이얼 플랜이 할당되었는지 확인합니다.

기본적으로 모든 사용자에게는 전역 음성 정책 및 다이얼 플랜이 할당됩니다. 음성 정책 또는 다이얼 플랜이 사용자 계정이 홈으로 지정된 사이트의 사이트 수준에 존재하는 경우 해당 사이트 정책이 사용자에게 자동으로 적용됩니다. 사용자별 음성 정책 및 다이얼 플랜을 사용자에게 적용하려면 **Grant-CsVoicePolicy** 및 **Grant-CsDialPlan** cmdlet을 실행해야 합니다. 자세한 내용은 [Lync Server 관리 셸](lync-server-2013-lync-server-management-shell.md) 설명서를 참조하십시오.

## 음성 정책 할당

전역 및 사이트 수준의 음성 정책은 Enterprise Voice에 대해 설정된 모든 사용자 계정에 자동으로 할당됩니다. 또한 특정 사용자 또는 그룹에 적용되는 음성 정책을 만들 수도 있습니다. 이러한 사용자별 정책은 사용자 또는 그룹에 명시적으로 할당되어야 합니다. Enterprise Voice를 사용하도록 설정된 모든 사용자에 대해 전역 또는 사이트 음성 정책을 사용하려면 이 섹션을 건너뛰고 이 항목의 뒷부분에 나오는 다이얼 계획 할당 섹션을 계속 진행하면 됩니다.

## 사용자별 음성 정책을 할당하려면

1.  CsUserAdministrator 역할 또는 CsAdministrator 역할에 할당된 사용자 계정에서 내부 배포된 컴퓨터에 로그온합니다.

2.  Lync Server 관리 셸 시작: **시작**, **모든 프로그램**, **Microsoft Lync Server 2013**을 차례로 클릭한 다음 **Lync Server 관리 셸**을 클릭합니다.

3.  기존 사용자 음성 정책을 사용자에게 할당하려면 명령 프롬프트에서 다음을 실행합니다.
    
        Grant-CsVoicePolicy -Identity <UserIdParameter> -PolicyName <String>
    
    예를 들면 다음과 같습니다.
    
        Grant-CsVoicePolicy -Identity "Bob Kelly" -PolicyName VoicePolicyJapan
    
    이 예에서는 표시 이름이 김진국인 사용자에게 이름이 **VoicePolicyJapan**인 음성 정책이 할당되었습니다.

사용자별 음성 정책 할당 및 **Grant-CsVoicePolicy** cmdlet을 실행하는 방법에 대한 자세한 내용은 [Lync Server 관리 셸](lync-server-2013-lync-server-management-shell.md) 설명서를 참조하십시오.

## 다이얼 플랜 할당

Enterprise Voice 사용자 또는 전화 접속 회의 사용자에 대한 사용자 계정 구성을 완료하려면 사용자에게 다이얼 플랜이 할당되어 있어야 합니다. 기존 사용자별 다이얼 플랜을 명시적으로 할당하지 않은 경우 사용자 계정에는 전역 다이얼 플랜 또는 사이트 수준 다이얼 플랜(이미 있는 경우)이 자동으로 사용됩니다. Enterprise Voice를 사용하도록 설정된 모든 사용자에 대해 전역 또는 사이트 다이얼 플랜을 사용하려면 이 섹션을 건너뛸 수 있습니다.

## 다이얼 플랜을 할당하려면

1.  CsUserAdministrator 역할 또는 CsAdministrator 역할에 할당된 사용자 계정에서 내부 배포된 컴퓨터에 로그온합니다.

2.  Lync Server 관리 셸 시작: **시작**, **모든 프로그램**, **Microsoft Lync Server 2013**을 차례로 클릭한 다음 **Lync Server 관리 셸**을 클릭합니다.

3.  사용자별 다이얼 플랜을 할당하려면 명령 프롬프트에서 다음을 실행합니다.
    
        Grant-CsDialPlan -Identity <UserIdParameter> -PolicyName <String>
    
    예를 들면 다음과 같습니다.
    
        Grant-CsDialPlan -Identity "Bob Kelly" -PolicyName DialPlanJapan
    
    이 예에서는 표시 이름이 김진국인 사용자에게 이름이 **DialPlanJapan**인 다이얼 플랜이 할당되었습니다.

사용자에게 다이얼 플랜 할당 또는 **Grant-CsDialPlan** cmdlet을 실행하는 방법에 대한 자세한 내용은 [Lync Server 관리 셸](lync-server-2013-lync-server-management-shell.md) 설명서를 참조하십시오.

## 참고 항목

#### 작업

[Lync Server 2013에서 Enterprise Voice에 사용자 사용 안 함](lync-server-2013-disable-a-user-for-enterprise-voice.md)

