---
title: 조직, 사이트 또는 사용자에 대한 내부 또는 외부 통신의 보관을 사용하거나 사용하지 않도록 보관 정책 변경
TOCTitle: 조직, 사이트 또는 사용자에 대한 내부 또는 외부 통신의 보관을 사용하거나 사용하지 않도록 보관 정책 변경
ms:assetid: b85dc3fb-8ebd-4e3c-ac90-fc79270ac867
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg182576(v=OCS.15)
ms:contentKeyID: 49304823
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# 조직, 사이트 또는 사용자에 대한 내부 또는 외부 통신의 보관을 사용하거나 사용하지 않도록 보관 정책 변경

 

_**마지막으로 수정된 항목:** 2013-02-23_

Lync Server 2013에서는 정책을 사용하여 Lync Server 2013에 속한 사용자의 내부 및 외부 통신에 보관을 사용하거나 사용하지 않도록 설정합니다. 여기에는 다음과 같은 보관 정책이 포함됩니다.

  - Lync Server 2013을 배포할 때 기본적으로 만들어지는 전역 정책

  - 특정 사이트 또는 사용자에 대해 보관이 구현되는 방식을 지정하도록 만들어서 사용하는 선택적인 사이트 수준 및 사용자 수준 정책

보관을 배포할 때 처음으로 보관 정책을 설정하게 되며, 배포 후에 정책을 변경, 추가 및 삭제할 수 있습니다. Lync Server 2013 제어판에서는 **보관 및 모니터링** 그룹의 **보관 정책** 페이지를 사용하여 전역 수준, 사이트 수준 및 사용자 수준으로 정책을 관리할 수 있습니다. Lync Server 저장소를 Exchange 2013 저장소와 통합하는 경우 Exchange 사용자 정책이 Lync Server 2013 보관 정책보다 우선합니다.

정책 계층 구조를 포함하여 정책이 구현되는 방식에 대한 자세한 내용은 계획 설명서, 배포 설명서 또는 작업 설명서에서 [Lync Server 2013의 보관 작동 방식](lync-server-2013-how-archiving-works.md)을 참조하십시오.


> [!NOTE]
> 배포에 Microsoft Exchange 통합을 사용하도록 설정한 경우 Exchange 정책이 Exchange 2013에 속해 있고 사서함을 원본 위치 유지로 설정한 사용자에 대해 보관을 사용할지 여부를 제어합니다. 자세한 내용은 배포 설명서에서 <A href="lync-server-2013-setting-up-policies-for-archiving-when-using-exchange-server-integration.md">Exchange Server 통합 사용 시 보관용 정책 설정</A>을 참조하십시오.<BR>보관을 사용하도록 설정하기 전에 보관 구성에서 모든 해당 옵션을 지정해야 합니다. 자세한 내용은 작업 설명서에서 <A href="lync-server-2013-managing-archiving-configuration-options-for-your-organization-sites-and-pools.md">Lync Server 2013에서 조직, 사이트 및 풀에 대한 보관 구성 옵션 관리</A>를 참조하십시오.



## 보관 정책을 변경하려면

1.  CsArchivingAdministrator 또는 CsAdministrator 역할에 할당된 사용자 계정에서 내부 배포된 컴퓨터에 로그온합니다.

2.  브라우저 창을 연 다음 Admin URL을 입력하여 Lync Server 제어판을 엽니다. Lync Server 제어판을 시작하는 데 사용할 수 있는 다양한 방법에 대한 자세한 내용은 [Lync Server 관리 도구 열기](lync-server-2013-open-lync-server-administrative-tools.md)를 참조하세요.

3.  왼쪽 탐색 모음에서 **모니터링 및 보관**을 클릭하고 **보관 정책**을 클릭합니다.

4.  정책 목록에서 다음 중 하나를 수행합니다.
    
      - 전체 배포에 대한 정책을 변경하려면 정책 목록에서 **전역**을 클릭하고 **편집**을 클릭한 후에 **자세한 정보 표시**를 클릭합니다.
    
      - 단일 사이트에 대한 정책을 변경하려면 정책 목록에서 사이트 이름을 클릭하고 **편집**을 클릭한 후에 **자세한 정보 표시**를 클릭합니다.
    
      - 단일 사용자 또는 사용자 그룹에 대한 정책을 변경하려면 정책 목록에서 사용자 또는 사용자 그룹 이름을 클릭하고 **편집**을 클릭한 후에 **자세한 정보 표시**를 클릭합니다.

5.  **보관 정책 편집** 페이지에서 다음을 수행합니다.
    
      - 정책에 내부 보관을 사용하거나 사용하지 않도록 설정하려면 **내부 통신 보관** 확인란을 선택하거나 선택 취소합니다.
    
      - 정책에 외부 보관을 사용하거나 사용하지 않도록 설정하려면 **외부 통신 보관** 확인란을 선택하거나 선택 취소합니다.

6.  **커밋**을 클릭합니다.
    

    > [!IMPORTANT]
    > 사용자 정책 설정은 관리자가 정책을 적용한 특정 사용자 및 사용자 그룹에만 적용됩니다. 자세한 내용은 <A href="lync-server-2013-applying-an-archiving-policy-to-users.md">사용자에게 보관 정책 적용</A>을 참조하십시오.



## Lync Server PowerShell cmdlet을 사용하여 보관을 사용하거나 사용하지 않도록 설정

또한 **Set-CsArchivingPolicy** cmdlet을 사용하여 내부 및 외부 통신 세션 모두에 대해 보관을 사용하거나 사용하지 않도록 설정할 수 있습니다. 이 cmdlet은 Lync Server 2013 관리 셸 또는 Windows PowerShell의 원격 세션에서 실행할 수 있습니다. 원격 Windows PowerShell을 사용하여 Lync Server에 연결하는 방법에 대한 자세한 내용은 Lync Server Windows PowerShell 블로그 문서인 "빠른 시작: 원격 PowerShell을 사용하여 Microsoft Lync Server 2010 관리"([http://go.microsoft.com/fwlink/p/?linkId=255876](http://go.microsoft.com/fwlink/p/?linkid=255876))를 참조하세요.

## 내부 통신 세션의 보관을 사용하도록 설정

  - 내부 통신 세션의 보관을 사용하도록 설정하려면 **ArchiveInternal** 속성의 값을 True($True)로 설정합니다. 예를 들면 다음과 같습니다.
    
        Set-CsArchivingPolicy -Identity "global" -ArchiveInternal $True

## 외부 통신 세션의 보관을 사용하도록 설정

  - 외부 통신 세션의 보관을 사용하도록 설정하려면 **Archiveexternal** 속성의 값을 True($True)로 설정합니다. 예를 들면 다음과 같습니다.
    
        Set-CsArchivingPolicy -Identity "global" -ArchiveExternal $True

## 내부 및 외부 통신 세션의 보관을 사용하도록 설정

  - 내부 및 외부 통신 세션 모두의 보관을 사용하도록 설정하려면 다음과 같이 **ArchiveInternal** 및 **ArchiveExternal** 속성을 모두 True로 설정합니다.
    
        Set-CsArchivingPolicy -Identity "global" -ArchiveInternal $True -ArchiveExternal $True

## 보관을 사용하지 않도록 설정

  - 보관을 모두 사용하지 않도록 설정하려면 **ArchiveInternal** 및 **ArchiveExternal** 속성을 모두 False($False)로 설정합니다. 예를 들면 다음과 같습니다.
    
        Set-CsArchivingPolicy -Identity "global" -ArchiveInternal $False -ArchiveExternal $False

자세한 내용은 [Set-CsArchivingPolicy](https://docs.microsoft.com/en-us/powershell/module/skype/Set-CsArchivingPolicy) cmdlet에 대한 도움말 항목을 참조하십시오.

## 참고 항목

#### 기타 리소스

[Lync Server 2013에서 내부 및 외부 통신의 보관 관리](lync-server-2013-managing-the-archiving-of-internal-and-external-communications.md)

