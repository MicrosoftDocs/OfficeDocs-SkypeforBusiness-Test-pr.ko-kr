---
title: 보관 정책을 만들어 특정 사이트 및 사용자에 대해 내부 또는 외부 통신의 보관 사용 또는 사용 안 함
TOCTitle: 보관 정책을 만들어 특정 사이트 및 사용자에 대해 내부 또는 외부 통신의 보관 사용 또는 사용 안 함
ms:assetid: 5864793a-ba72-470c-bb5b-9fb41e968896
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg398385(v=OCS.15)
ms:contentKeyID: 49303700
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# 보관 정책을 만들어 특정 사이트 및 사용자에 대해 내부 또는 외부 통신의 보관 사용 또는 사용 안 함

 

_**마지막으로 수정된 항목:** 2013-02-23_

Lync Server 2013에서는 정책을 사용하여 Lync Server 2013에 있는 사용자의 내부 통신 및 외부 통신에 대한 보관을 사용 및 사용하지 않도록 설정합니다. 여기에는 다음과 같은 보관 정책이 포함됩니다.

  - Lync Server 2013을 배포할 때 기본적으로 만들어지는 글로벌 정책

  - 특정 사이트 또는 사용자에 대한 보관 구현 방법을 지정하기 위해 만들고 사용할 수 있는 선택적인 사이트 수준 및 사용자 수준의 정책

처음에 보관을 배포할 때 보관 정책을 설정하지만 배포 후 정책을 변경, 추가 및 삭제할 수 있습니다. Lync Server 2013 제어판에서는 **보관 및 모니터링** 그룹의 **보관 정책** 페이지를 사용하여 전역 수준, 사이트 수준 및 사용자 수준에서 정책을 관리할 수 있습니다. Lync Server 저장소를 Exchange 2013 저장소와 통합하면 Exchange 사용자 정책이 Lync Server 2013 보관 정책보다 우선 적용됩니다.

정책 계층을 포함하여 정책 구현 방법에 대한 자세한 내용은 계획 설명서, 배포 설명서 또는 작업 설명서에서 [Lync Server 2013의 보관 작동 방식](lync-server-2013-how-archiving-works.md)을 참조하십시오.


> [!NOTE]
> 보관 구현을 제어하려면 보관 구성에서 IM 또는 회의 내용을 보관할지 여부, 중요 모드 사용, 삭제 옵션 등과 같은 옵션을 지정해야 합니다. 기본적으로 전역 보관 구성이나 사이트 또는 풀 보관 구성에서는 어떤 옵션도 사용하도록 설정되어 있지 않습니다. 보관 정책에서 내부 또는 외부 통신에 대한 보관을 사용하도록 설정하려면 먼저 보관 구성에서 모든 적합한 옵션을 지정해야 합니다. 자세한 내용은 작업 설명서에서 <A href="lync-server-2013-managing-archiving-configuration-options-for-your-organization-sites-and-pools.md">Lync Server 2013에서 조직, 사이트 및 풀에 대한 보관 구성 옵션 관리</A>를 참조하십시오.<BR>배포에서 Microsoft Exchange 통합을 사용하도록 설정할 경우 Exchange 정책은 Exchange 2013에 있고 해당 사서함이 원본 위치 유지로 설정된 사용자에 대해 보관을 설정할지 여부를 제어합니다. 자세한 내용은 배포 설명서에서 <A href="lync-server-2013-setting-up-policies-for-archiving-when-using-exchange-server-integration.md">Exchange Server 통합 사용 시 보관용 정책 설정</A>을 참조하십시오.



## 사이트 또는 사용자에 대한 보관 정책을 만들려면

1.  CsArchivingAdministrator 또는 CsAdministrator 역할에 할당된 사용자 계정에서 내부 배포된 컴퓨터에 로그온합니다.

2.  브라우저 창을 연 다음 Admin URL을 입력하여 Lync Server 제어판을 엽니다. Lync Server 제어판을 시작하는 데 사용할 수 있는 다양한 방법에 대한 자세한 내용은 [Lync Server 관리 도구 열기](lync-server-2013-open-lync-server-administrative-tools.md)를 참조하세요.

3.  왼쪽 탐색 모음에서 **모니터링 및 보관**을 클릭하고 **보관 정책**을 클릭합니다.

4.  **새로 만들기**를 클릭하고 다음 중 하나를 수행합니다.
    
      - 사이트 수준의 보관 정책을 만들려면 **사이트 정책**을 클릭한 후 **사이트 선택**에서 정책을 적용할 사이트를 클릭합니다.
    
      - 사용자 수준의 보관 정책을 만들려면 **사용자 정책**을 클릭합니다.

5.  **새 보관 정책**에서 다음을 수행합니다.
    
      - **이름**에 새 정책의 이름을 지정합니다(예: externalContoso).
    
      - **설명**에 정책에 대한 자세한 설명을 입력합니다(예: Contoso용 외부 사용자 보관 정책).
    
      - 내부 사용자와의 통신 내용의 보관을 제어하려면 **내부 통신 보관** 확인란을 선택하거나 선택을 취소합니다.
    
      - 외부 사용자와의 통신 내용의 보관을 제어하려면 **외부 통신 보관** 확인란을 선택하거나 선택을 취소합니다.

6.  **커밋**을 클릭합니다.
    

    > [!IMPORTANT]
    > 사용자 정책의 설정은 해당 정책을 적용하는 특정 사용자 및 사용자 그룹에만 적용됩니다. 자세한 내용은 <A href="lync-server-2013-applying-an-archiving-policy-to-users.md">사용자에게 보관 정책 적용</A>을 참조하십시오.



## Lync Server 관리 셸 Cmdlet을 사용하여 보관 정책 만들기

보관 정책은 Windows PowerShell 및 **Remove-CsArchivingPolicy** cmdlet을 사용하여 만들 수도 있습니다. 이 cmdlet은 Lync Server 2013 관리 셸 또는 Windows PowerShell의 원격 세션에서 실행할 수 있습니다. 원격 Windows PowerShell을 사용하여 Lync Server에 연결하는 방법에 대한 자세한 내용은 Lync Server Windows PowerShell 블로그 문서인 "빠른 시작: 원격 PowerShell을 사용하여 Microsoft Lync Server 2010 관리"([http://go.microsoft.com/fwlink/p/?linkId=255876](http://go.microsoft.com/fwlink/p/?linkid=255876))를 참조하세요.

## 사이트 범위에서 새 보관 정책 만들기

  - 이 명령은 Redmond 사이트에 대한 새로운 보관 정책을 만듭니다.
    
        New-CsArchivingPolicy -Identity "site:Redmond"

## 사용자별 범위에서 새 보관 정책 만들기

  - 사용자별 범위에서 새 보관 정책을 만들려면 단순히 정책을 만들 때 고유 ID만 지정하면 됩니다.
    
        New-CsArchivingPolicy -Identity "RedmondArchivingPolicy"

## 내부 통신 세션의 보관을 사용하도록 설정하는 새 보관 정책 만들기

  - 이전 명령에서는 필수 Identity 매개 변수를 제외하고 어떤 매개 변수도 지정되지 않았기 때문에 새로운 정책이 모든 속성에 대해 기본값을 사용합니다. 다른 속성 값을 사용하는 정책을 만들려면 적합한 매개 변수 및 매개 변수 값을 포함하기만 하면 됩니다. 예를 들어 내부 인스턴트 메시징 세션의 보관을 허용하는 보관 정책을 만들려면 다음과 같은 명령을 사용합니다.
    
        New-CsArchivingPolicy -Identity "site:Redmond" -ArchiveInternal $True

## 내부 및 외부 통신 세션의 보관을 모두 사용하도록 설정하는 새 보관 정책 만들기

  - 여러 매개 변수를 포함하여 여러 속성 값을 수정할 수 있습니다. 예를 들어 이 명령은 내부 및 외부 인스턴트 메시징 세션을 모두 보관하는 새 정책을 구성합니다.
    
        New-CsArchivingPolicy -Identity "site:Redmond" -ArchiveInternal $True -ArchiveExternal $True

자세한 내용은 [New-CsArchivingPolicy](https://docs.microsoft.com/en-us/powershell/module/skype/New-CsArchivingPolicy) cmdlet의 도움말 항목을 참조하십시오.

## 참고 항목

#### 기타 리소스

[Lync Server 2013에서 내부 및 외부 통신의 보관 관리](lync-server-2013-managing-the-archiving-of-internal-and-external-communications.md)

