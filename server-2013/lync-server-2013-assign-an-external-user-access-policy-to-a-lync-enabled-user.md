---
title: 'Lync Server 2013: Lync 사용이 가능한 사용자에게 외부 사용자 액세스 정책 할당'
TOCTitle: Lync 사용이 가능한 사용자에게 외부 사용자 액세스 정책 할당
ms:assetid: 736fcaad-9f95-4896-b767-e199d86a00a4
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg398551(v=OCS.15)
ms:contentKeyID: 49304029
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Lync Server 2013에서 Lync 사용이 가능한 사용자에게 외부 사용자 액세스 정책 할당

 

_**마지막으로 수정된 항목:** 2013-02-22_

사용자가 Lync Server에 대해 설정된 경우 Lync Server 제어판에서 특정 사용자에게 적합한 정책을 적용하여 SIP 페더레이션, XMPP 페더레이션, 원격 사용자 액세스 및 공용 IM(인스턴트 메시징) 연결을 구성할 수 있습니다. 예를 들어 원격 사용자 액세스를 지원하도록 정책을 만들었으면 이를 사용자에게 적용해야 사용자가 원격 위치에서 Lync Server에 연결하고 원격 위치로부터 내부 사용자와 공동 작업을 수행할 수 있습니다.


> [!NOTE]
> 외부 사용자 액세스에 대해 지원하려면 지원할 각 외부 사용자 액세스 유형에 대한 지원을 사용하도록 설정하고 사용을 제어할 적절한 정책 및 기타 옵션을 구성해야 합니다. 자세한 내용은 배포 설명서의 <A href="lync-server-2013-configuring-support-for-external-user-access.md">Lync Server 2013에서 외부 사용자 액세스에 대한 지원 구성</A> 또는 작업 설명서의 <A href="lync-server-2013-managing-federation-and-external-access-to-lync-server-2013.md">Lync Server 2013에 대한 외부 액세스 및 페더레이션 관리</A>를 참조하십시오.



이 항목의 절차를 사용하여 하나 이상의 사용자 계정에 이전에 만든 외부 사용자 액세스 정책을 적용합니다.

## 사용자 계정에 외부 사용자 정책을 적용하려면

1.  CsUserAdministrator 역할 또는 CsAdministrator 역할에 할당된 사용자 계정에서 내부 배포된 컴퓨터에 로그온합니다.

2.  브라우저 창을 연 다음 Admin URL을 입력하여 Lync Server 제어판을 엽니다. Lync Server 제어판을 시작하는 데 사용할 수 있는 다양한 방법에 대한 자세한 내용은 [Lync Server 관리 도구 열기](lync-server-2013-open-lync-server-administrative-tools.md)를 참조하세요.

3.  왼쪽 탐색 모음에서 **사용자** 를 클릭하고 구성할 사용자 계정을 검색합니다.

4.  검색 결과가 나열된 표에서 사용자 계정을 클릭하고 **편집** 을 클릭한 후에 **자세한 정보 표시** 를 클릭합니다.

5.  **외부 액세스 정책** 아래의 **Lync Server 사용자 편집** 에서 적용할 사용자 정책을 선택합니다.
    

    > [!NOTE]
    > <STRONG>&lt;자동&gt;</STRONG> 설정은 기본 서버 또는 글로벌 정책 설정에 적용됩니다.



## Windows PowerShell cmdlet을 사용하여 사용자별 외부 액세스 정책 지정

사용자별 외부 액세스 정책은 Windows PowerShell 및 Grant-CsExternalAccessPolicy cmdlet을 사용하여 지정할 수 있습니다. 이 cmdlet은 Lync Server 2013 관리 셸 또는 Windows PowerShell의 원격 세션에서 실행할 수 있습니다. 원격 Windows PowerShell을 사용하여 Lync Server에 연결하는 방법에 대한 자세한 내용은 Lync Server Windows PowerShell 블로그 문서인 "빠른 시작: 원격 PowerShell을 사용하여 Microsoft Lync Server 2010 관리"([http://go.microsoft.com/fwlink/p/?linkId=255876](http://go.microsoft.com/fwlink/p/?linkid=255876))를 참조하세요.

## 사용자별 외부 액세스 정책을 단일 사용자에게 지정하려면

  - 이 명령은 사용자별 외부 액세스 정책 RedmondExternalAccessPolicy를 Ken Myer라는 사용자에게 지정합니다.
    
        Grant-CsExternalAccessPolicy -Identity "Ken Myer" -PolicyName "RedmondExternalAccessPolicy"

## 사용자별 외부 액세스 정책을 여러 사용자에게 지정하려면

  - 이 명령은 사용자별 외부 액세스 정책 USAExternalAccessPolicy를 Active Directory의 UnitedStates OU에 계정이 있는 모든 사용자에게 지정합니다. 이 명령에 사용된 OU 매개 변수에 대한 자세한 내용은 [Get-CsUser](https://docs.microsoft.com/en-us/powershell/module/skype/Get-CsUser) cmdlet의 설명서를 참조하십시오.
    
        Get-CsUser -OU "ou=UnitedStates,dc=litwareinc,dc=com" | Grant-CsExternalAccessPolicy -PolicyName "USAExternalAccessPolicy"

## 사용자별 외부 액세스 정책 지정을 취소하려면

  - 이 명령은 이전에 Ken Myer에게 지정되었던 사용자별 외부 액세스 정책의 지정을 해제합니다. 사용자별 정책을 지정 해제한 후 Ken Myer는 자동으로 글로벌 정책 또는 로컬 사이트 정책(있는 경우)을 사용해서 관리됩니다. 사이트 정책은 글로벌 정책보다 우선 적용됩니다.
    
        Grant-CsExternalAccessPolicy -Identity "Ken Myer" -PolicyName $Null

자세한 내용은 [Grant-CsExternalAccessPolicy](grant-csexternalaccesspolicy.md) cmdlet 관련 도움말 항목을 참고하세요.

