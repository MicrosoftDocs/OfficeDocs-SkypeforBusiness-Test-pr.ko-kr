---
title: 사용자별 회의 정책 할당
TOCTitle: 사용자별 회의 정책 할당
ms:assetid: 72f12c72-65f7-44fe-ab81-0f57cb2f87d1
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg521015(v=OCS.15)
ms:contentKeyID: 49304020
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# 사용자별 회의 정책 할당

 

_**마지막으로 수정된 항목:** 2013-02-22_

회의 정책은 Lync Server 제어판에서 구성할 수 있는 개별 사용자 계정 설정 중 하나입니다.

하나 이상의 사용자별 회의 정책을 배포하는 것은 선택 사항입니다. 또한 전역 수준 회의 정책이나 사이트 수준 회의 정책만 배포할 수 있습니다. 사용자별 정책을 배포하는 경우에는 해당 정책을 사용자, 그룹 또는 연락처 개체에 명시적으로 지정해야 합니다. 특정 사이트 수준 또는 사용자별 정책이 지정되지 않은 경우 회의 사용자 권한 및 권한은 전역 수준 회의 정책에 정의된 해당 권한으로 자동으로 기본적으로 설정됩니다.

하나 이상의 사용자별 회의 정책을 만든 후 이 항목의 절차를 사용하여 서버에서 특정 사용자가 이끄는 모임에 부여하도록 할 사용자 권한 및 권한을 지정하는 정책을 지정합니다.

사용 가능한 모든 회의 정책 설정 목록은 [Lync Server 2013용 회의 정책 설정 참조](lync-server-2013-conferencing-policy-settings-reference.md)을 참조하십시오.

회의 정책 만들기에 대한 자세한 내용은 [회의 정책 만들기 또는 수정](lync-server-2013-create-or-modify-a-conferencing-policy.md)을 참조하십시오.

## 사용자별 회의 정책을 지정하려면

1.  CsUserAdministrator 역할 또는 CsAdministrator 역할에 할당된 사용자 계정에서 내부 배포된 컴퓨터에 로그온합니다.

2.  브라우저 창을 연 다음 Admin URL을 입력하여 Lync Server 제어판을 엽니다. Lync Server 제어판을 시작하는 데 사용할 수 있는 다양한 방법에 대한 자세한 내용은 [Lync Server 관리 도구 열기](lync-server-2013-open-lync-server-administrative-tools.md)를 참조하세요.

3.  왼쪽 탐색 모음에서 **사용자**를 클릭합니다.

4.  다음 방법 중 하나를 통해 사용자를 찾습니다.
    
      - **사용자 검색** 상자에 사용자 계정의 표시 이름, 이름, 성, SAM(보안 계정 관리자) 계정 이름, SIP 주소 또는 줄 URI(Uniform Resource Identifier)를 모두 또는 처음 부분을 입력하고 **찾기**를 클릭합니다.
    
      - 저장된 쿼리가 있는 경우 **쿼리 열기** 아이콘을 클릭하고 **열기** 대화 상자를 통해 쿼리(예: .usf 파일)를 검색한 후에 **찾기**를 클릭합니다.

5.  (선택 사항) 추가 검색 조건을 지정하여 결과 범위를 좁힙니다.
    
    1.  **필터 추가**를 클릭합니다.
    
    2.  사용자 속성을 입력하거나 드롭다운 목록의 화살표를 클릭하여 사용자 속성을 선택합니다.
    
    3.  **같음** 드롭다운 목록에서 연산자(예: **같음** 또는 **같지 않음**)를 클릭합니다.
    
    4.  선택한 사용자 속성에 따라 검색 결과를 필터링하는 데 사용할 조건을 직접 입력하거나 드롭다운 목록에서 화살표를 클릭하여 입력합니다.
        

        > [!TIP]
        > 쿼리에 검색 절을 더 추가하려면 <STRONG>필터 추가</STRONG>를 클릭합니다.

    
    5.  **찾기**를 클릭합니다.

6.  검색 결과에서 사용자를 클릭하고 **동작**을 클릭한 후에 **정책 할당**을 클릭합니다.
    

    > [!TIP]
    > 동일한 사용자별 회의 정책을 여러 사용자에게 적용하려면 검색 결과에서 여러 사용자를 선택하고 <STRONG>동작</STRONG>을 클릭한 다음 <STRONG>정책 할당</STRONG>을 클릭합니다.



7.  **정책 할당**의 **회의 정책** 아래에서 다음 중 하나를 수행합니다.
    

    > [!NOTE]
    > <STRONG>정책 할당</STRONG>에서 구성할 수 있는 정책이 여러 개이므로 대화 상자에 있는 모든 정책에 대해 <STRONG>&lt;있는 그대로 유지&gt;</STRONG>가 기본적으로 선택되어 있습니다. 이 설정을 변경하지 않으면 이전에 사용자에게 지정된 정책이 계속 사용됩니다.

    
      - Lync Server 2013에서 자동으로 전역 수준 정책이나 사이트 수준 정책(정의된 경우)을 선택할 수 있도록 하려면 **\<자동\>**을 선택합니다.
    
      - **회의 정책** 페이지에서 이전에 정의한 사용자별 회의 정책의 이름을 클릭합니다.
        

        > [!TIP]
        > 지정할 정책을 쉽게 결정하려면 정책 이름을 클릭한 후 <STRONG>보기</STRONG>를 클릭하여 정책에 정의된 사용자 권한 및 권한을 확인합니다.



8.  작업을 마쳤으면 **확인**을 클릭합니다.

## Lync 서버 PowerShell Cmdlet을 사용하여 사용자별 회의 정책 지정

사용자별 회의 정책은 Lync Server PowerShell 및 Grant-CsConferencingPolicy cmdlet을 사용해서 지정할 수도 있습니다. 이 cmdlet은 Lync Server 2013 관리 셸 또는 Windows PowerShell. 원격 Windows PowerShell을 사용하여 Lync Server에 연결하는 방법에 대한 자세한 내용은 Lync Server Windows PowerShell 블로그 문서인 "빠른 시작: 원격 PowerShell을 사용하여 Microsoft Lync Server 2010 관리"([http://go.microsoft.com/fwlink/p/?linkId=255876](http://go.microsoft.com/fwlink/p/?linkid=255876))를 참조하세요.의 원격 세션에서 실행할 수 있습니다.

## 사용자별 회의 정책을 단일 사용자에게 지정

  - 다음 명령은 사용자별 회의 정책 RedmondConferencingPolicy를 Ken Myer라는 사용자에게 지정합니다.
    
        Grant-CsConferencingPolicy -Identity "Ken Myer" -PolicyName "RedmondConferencingPolicy"

## 사용자별 회의 정책을 여러 사용자에게 지정

  - 이 명령은 사용자별 회의 정책 HRConferencingPolicy를 인사 부서에서 근무하는 모든 사용자에게 지정합니다. 이 명령에 사용된 LdapFilter 매개 변수에 대한 자세한 내용은 [Get-CsUser](get-csuser.md) cmdlet의 설명서를 참조하십시오.
    
        Get-CsUser -LdapFilter "Department=Human Resources" | Grant-CsConferencingPolicy -PolicyName "HRConferencingPolicy"

## 사용자별 회의 정책 지정 해제

  - 다음 명령은 이전에 Ken Myer에게 지정되었던 사용자별 회의 정책의 지정을 해제합니다. 사용자별 정책을 지정 해제한 후 Ken Myer는 자동으로 글로벌 정책 또는 로컬 사이트 정책(있는 경우)을 사용해서 관리됩니다. 사이트 정책은 글로벌 정책보다 우선 적용됩니다.
    
        Grant-CsConferencingPolicy -Identity "Ken Myer" -PolicyName $Null

자세한 내용은 [Grant-CsConferencingPolicy](grant-csconferencingpolicy.md) cmdlet의 도움말 항목을 참조하십시오.

## 참고 항목

#### 작업

[회의 정책 만들기 또는 수정](lync-server-2013-create-or-modify-a-conferencing-policy.md)  

#### 기타 리소스

[사용자별 정책 할당](lync-server-2013-assigning-per-user-policies.md)

