---
title: 사용자별 다이얼 플랜 정책 할당
TOCTitle: 사용자별 다이얼 플랜 정책 할당
ms:assetid: 9fea861f-7770-4cae-9b1f-2a960595bfc9
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/JJ688156(v=OCS.15)
ms:contentKeyID: 49885902
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# 사용자별 다이얼 플랜 정책 할당

 

_**마지막으로 수정된 항목:** 2013-02-22_

Enterprise Voice 사용자 또는 전화 접속 회의 사용자에 대한 사용자 계정 구성을 완료하려면 사용자에게 다이얼 플랜이 할당되어 있어야 합니다. 기존 사용자별 다이얼 플랜을 명시적으로 할당하지 않은 경우 사용자 계정에는 전역 다이얼 플랜 또는 사이트 수준 다이얼 플랜 중에서 이미 있는 항목이 자동으로 사용됩니다. Enterprise Voice를 사용하도록 설정된 모든 사용자에 대해 전역 또는 사이트 다이얼 플랜을 사용하려면 이 섹션을 건너뛸 수 있습니다.

## Lync Server 2013 제어판을 사용하여 다이얼 플랜을 할당하려면

1.  CsUserAdministrator 역할 또는 CsAdministrator 역할에 할당된 사용자 계정에서 내부 배포된 컴퓨터에 로그온합니다.

2.  브라우저 창을 연 다음 Admin URL을 입력하여 Lync Server 제어판을 엽니다. Lync Server 제어판을 시작하는 데 사용할 수 있는 다양한 방법에 대한 자세한 내용은 [Lync Server 관리 도구 열기](lync-server-2013-open-lync-server-administrative-tools.md)를 참조하세요.

3.  왼쪽 탐색 모음에서 **사용자**를 클릭합니다.

4.  **사용자 검색** 상자에 사용하도록 설정할 사용자 계정의 표시 이름, 이름, 성, SAM(보안 계정 관리자) 계정 이름, SIP 주소 또는 줄 URI(Uniform Resource Identifier)를 모두 또는 첫부분을 입력하고 **찾기**를 클릭합니다.

5.  테이블에서 다이얼 플랜을 할당할 사용자 계정을 클릭합니다.

6.  **편집** 메뉴에서 **자세한 정보 표시**를 클릭합니다.

7.  **Lync Server 사용자 편집** 페이지의 **전화 통신** 아래에서 **Enterprise Voice**를 클릭합니다.

8.  **다이얼 플랜 정책**을 클릭한 후 원하는 다이얼 플랜을 선택합니다.

9.  **커밋**을 클릭합니다.

다이얼 플랜을 구성하는 방법에 대한 자세한 내용은 [Lync Server 2013에서 다이얼 플랜 구성](lync-server-2013-configuring-dial-plans.md) 항목을 참조하십시오.

## Lync Server 2013 관리 셸을 사용하여 다이얼 플랜을 할당하려면

1.  CsUserAdministrator 역할 또는 CsAdministrator 역할에 할당된 사용자 계정에서 내부 배포된 컴퓨터에 로그온합니다.

2.  Lync Server 관리 셸 시작: **시작**, **모든 프로그램**, **Microsoft Lync Server 2013**을 차례로 클릭한 다음 **Lync Server 관리 셸**을 클릭합니다.

3.  사용자별 다이얼 플랜을 할당하려면 명령 프롬프트에서 다음을 실행합니다.
    
        Grant-CsDialPlan -Identity <UserIdParameter> -PolicyName <String>
    
    예를 들면 다음과 같습니다.
    
        Grant-CsDialPlan -Identity "Bob Kelly" -PolicyName DialPlanJapan
    
    이 예에서는 표시 이름이 김진국인 사용자에게 이름이 **DialPlanJapan**인 다이얼 플랜이 할당되었습니다.

사용자에게 다이얼 플랜 할당 또는 **Grant-CsDialPlan** cmdlet을 실행하는 방법에 대한 자세한 내용은 [Lync Server 관리 셸](lync-server-2013-lync-server-management-shell.md) 설명서를 참조하십시오.

## Windows PowerShell cmdlet을 사용하여 사용자별 다이얼 플랜 할당

Windows PowerShell 및 **Grant-CsdialPlan** cmdlet을 사용하여 사용자별 다이얼 플랜을 할당할 수도 있습니다. 이 cmdlet은 Lync Server 2013 관리 셸 또는 Windows PowerShell의 원격 세션에서 실행할 수 있습니다. 원격 Windows PowerShell을 사용하여 Lync Server에 연결하는 방법에 대한 자세한 내용은 Lync Server Windows PowerShell 블로그 문서인 "빠른 시작: 원격 PowerShell을 사용하여 Microsoft Lync Server 2010 관리"([http://go.microsoft.com/fwlink/p/?linkId=255876](http://go.microsoft.com/fwlink/p/?linkid=255876))를 참조하세요.

## 한 명의 사용자에게 사용자별 다이얼 플랜 할당

  - 다음 명령은 사용자 Ken Myer에게 사용자별 다이얼 플랜 RedmondDialPlan을 할당합니다.
    
        Grant-CsDialPlan -Identity "Ken Myer" -PolicyName "RedmondDialPlan"

## 여러 사용자에게 사용자별 다이얼 플랜 할당

  - 이 명령은 사용자별 다이얼 플랜 RedmondDialPlan을 Redmond 도시에서 작업하는 모든 사용자에게 할당합니다. 이 명령에 사용되는 LdapFilter 매개 변수에 대한 자세한 내용은 [Get-CsUser](get-csuser.md) cmdlet에 대한 설명서를 참조하십시오.
    
        Get-CsUser -LdapFilter "l=Redmond" | Grant-CsDialPlan -PolicyName "RedmondDialPlan"

## 사용자별 다이얼 플랜 할당 해제

  - 다음 명령은 Ken Myer에게 이전에 할당된 사용자별 다이얼 플랜을 할당 해제합니다. 사용자별 다이얼 플랜을 할당 해제한 후에는 Ken Myer가 자동으로 전역 다이얼 플랜, 해당 로컬 사이트 플랜(있는 경우) 또는 해당 등록자 또는 PSTN 게이트웨이에 할당된 서비스 범위 다이얼 플랜을 사용하여 관리됩니다. 사이트 다이얼 플랜이 전역 다이얼 플랜보다 우선합니다.
    
        Grant-CsDialPlan -Identity "Ken Myer" -PolicyName $Null

자세한 내용은 [Grant-CsDialPlan](grant-csdialplan.md) cmdlet에 대한 도움말 항목을 참조하십시오.

## 참고 항목

#### 기타 리소스

[Lync Server 2013에서 다이얼 플랜 구성](lync-server-2013-configuring-dial-plans.md)  
[Lync Server 2013에 사용되는 사용자 계정](lync-server-2013-user-accounts-enabled-for-lync-server.md)

