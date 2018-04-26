---
title: 사용자별 음성 정책 할당
TOCTitle: 사용자별 음성 정책 할당
ms:assetid: 9ee47ee7-1030-43b8-a4dc-bf685ea24659
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/JJ688155(v=OCS.15)
ms:contentKeyID: 49885898
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# 사용자별 음성 정책 할당

 

_**마지막으로 수정된 항목:** 2013-02-22_

전역 및 사이트 수준의 음성 정책은 Enterprise Voice에 대해 설정된 모든 Lync Server 2013 사용자 계정에 자동으로 할당됩니다. 또한 Lync Server 2013 제어판 또는 Lync Server 2013 관리 셸을 사용하여 특정 사용자에게 음성 정책을 할당할 수도 있습니다. Lync Server 사용자에게 사용자별 정책을 명시적으로 할당하려면 이 항목에 있는 절차를 따르십시오.

## Lync Server 제어판을 사용하여 사용자별 음성 정책을 할당하려면

1.  CsUserAdministrator 역할 또는 CsAdministrator 역할에 할당된 사용자 계정에서 내부 배포된 컴퓨터에 로그온합니다.

2.  브라우저 창을 연 다음 Admin URL을 입력하여 Lync Server 제어판을 엽니다. Lync Server 제어판을 시작하는 데 사용할 수 있는 다양한 방법에 대한 자세한 내용은 [Lync Server 관리 도구 열기](lync-server-2013-open-lync-server-administrative-tools.md)를 참조하세요.

3.  왼쪽 탐색 모음에서 **사용자**를 클릭하고 구성할 사용자 계정을 검색합니다.

4.  검색 결과가 나열된 표에서 사용자 계정을 클릭하고 **편집**을 클릭한 후에 **자세한 정보 표시**를 클릭합니다.

5.  **음성 정책** 아래의 **Lync Server 사용자 편집**에서 적용할 사용자 정책을 선택합니다.
    

    > [!NOTE]
    > <STRONG>&lt;자동&gt;</STRONG> 설정을 선택하면 기본 서버 또는 전역 정책 설정이 적용됩니다.



## Lync Server 관리 셸을 사용하여 사용자별 음성 정책을 할당하려면

1.  CsUserAdministrator 역할 또는 CsAdministrator 역할에 할당된 사용자 계정에서 내부 배포된 컴퓨터에 로그온합니다.

2.  Lync Server 관리 셸 시작: **시작**, **모든 프로그램**, **Microsoft Lync Server 2013**을 차례로 클릭한 다음 **Lync Server 관리 셸**을 클릭합니다.

3.  기존 사용자 음성 정책을 사용자에게 할당하려면 명령 프롬프트에서 다음을 실행합니다.
    
        Grant-CsVoicePolicy -Identity <UserIdParameter> -PolicyName <String>
    
    예를 들면 다음과 같습니다.
    
        Grant-CsVoicePolicy -Identity "Bob Kelly" -PolicyName VoicePolicyJapan
    
    이 예에서는 표시 이름이 김진국인 사용자에게 이름이 **VoicePolicyJapan**인 음성 정책이 할당되었습니다.

사용자별 음성 정책 할당 및 **Grant-CsVoicePolicy** cmdlet을 실행하는 방법에 대한 자세한 내용은 [Lync Server 관리 셸](lync-server-2013-lync-server-management-shell.md) 설명서를 참조하십시오.

## Windows PowerShell cmdlet을 사용하여 사용자별 음성 정책 할당

Windows PowerShell 및 **Grant-CsVoicePolicy** cmdlet을 사용하여 사용자별 음성 정책을 할당할 수도 있습니다. 이 cmdlet은 Lync Server 2013 관리 셸 또는 Windows PowerShell의 원격 세션에서 실행할 수 있습니다. 원격 Windows PowerShell을 사용하여 Lync Server에 연결하는 방법에 대한 자세한 내용은 Lync Server Windows PowerShell 블로그 문서인 "빠른 시작: 원격 PowerShell을 사용하여 Microsoft Lync Server 2010 관리"([http://go.microsoft.com/fwlink/p/?linkId=255876](http://go.microsoft.com/fwlink/p/?linkid=255876))를 참조하세요.

## 한 명의 사용자에게 사용자별 음성 정책 할당

  - 다음 명령은 사용자 Ken Myer에게 사용자별 음성 정책 RedmondVoicePolicy를 할당합니다.
    
        Grant-CsVoicePolicy -Identity "Ken Myer" -PolicyName "RedmondVoicePolicy"

## 여러 사용자에게 사용자별 음성 정책 할당

  - 이 명령은 사용자별 음성 정책 FinanceVoicePolicy를 Active Directory의 Finance OU에 계정이 있는 모든 사용자에게 할당합니다. 이 명령에 사용되는 OU 매개 변수에 대한 자세한 내용은 [Get-CsUser](get-csuser.md) cmdlet에 대한 설명서를 참조하십시오.
    
        Get-CsUser -OU "ou=Finance,ou=North America,dc=litwareinc,dc=com" | Grant-CsVoicePolicy -PolicyName "FinanceVoicePolicy"

## 사용자별 음성 정책 할당 해제

  - 다음 명령은 Ken Myer에게 이전에 할당된 사용자별 음성 정책을 할당 해제합니다. 사용자별 정책을 할당 해제한 후에는 Ken Myer가 자동으로 전역 정책 또는 해당 로컬 사이트 정책(있는 경우)을 사용하여 관리됩니다. 사이트 정책이 전역 정책보다 우선합니다.
    
        Grant-CsVoicePolicy -Identity "Ken Myer" -PolicyName $Null

자세한 내용은 [Grant-CsVoicePolicy](grant-csvoicepolicy.md) cmdlet에 대한 도움말 항목을 참조하십시오.

## 참고 항목

#### 작업

[Lync Server 2013에서 Enterprise Voice에 사용자 사용 안 함](lync-server-2013-disable-a-user-for-enterprise-voice.md)  

#### 기타 리소스

[Lync Server 관리 셸](lync-server-2013-lync-server-management-shell.md)

