---
title: Microsoft Exchange Server 2013 보관을 사용하도록 Lync Server 2013 구성
TOCTitle: Exchange Server 2013 보관을 사용하도록 Lync Server 2013 구성
ms:assetid: 260346d1-edc8-4a0c-8ad2-6c2401c3c377
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/JJ679896(v=OCS.15)
ms:contentKeyID: 49885686
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Microsoft Exchange Server 2013 보관을 사용하도록 Microsoft Lync Server 2013 구성

 

_**마지막으로 수정된 항목:** 2014-06-24_

관리자는 Microsoft Lync Server 2013을 사용하여 인스턴트 메시징 및 웹 회의 대화 내용을 SQL Server 데이터베이스가 아닌 사용자의 Microsoft Exchange Server 2013 사서함에 보관할 수 있습니다. 이 옵션을 사용하도록 설정하는 경우 대화 내용이 사용자 사서함의 Purges 폴더에 기록됩니다. Purges 폴더는 복구 가능한 항목 폴더에 있는 숨김 폴더입니다. 이 폴더는 최종 사용자에게는 표시되지 않지만 Exchange 검색 엔진에 의해 인덱싱되며 Exchange 사서함 검색 및/또는 Microsoft SharePoint Server 2013을 통해 검색할 수 있습니다. 정보는 Exchange 원본 위치 유지 기능(전자 메일 및 기타 Exchange 통신 내용 보관을 담당함)에서 사용하는 것과 같은 폴더에 저장되므로 관리자는 하나의 도구로 사용자에 대해 보관되는 모든 전자 통신 내용을 검색할 수 있습니다.


> [!IMPORTANT]
> Lync 대화 보관을 완전히 사용하지 않도록 설정하려면 Lync 대화 내용도 사용하지 않도록 설정해야 합니다. 자세한 내용은 <A href="lync-server-2013-managing-the-archiving-of-internal-and-external-communications.md">Lync Server 2013에서 내부 및 외부 통신의 보관 관리</A>, <A href="https://docs.microsoft.com/en-us/powershell/module/skype/New-CsClientPolicy">New-CsClientPolicy</A>, <A href="https://docs.microsoft.com/en-us/powershell/module/skype/Set-CsClientPolicy">Set-CsClientPolicy</A> 항목을 참고하세요.



대화 내용을 Exchange 2013에 보관하려면 먼저 두 서버 간의 서버 간 인증을 구성해야 합니다. 서버 간 인증을 구성한 후에는 Microsoft Lync Server 2013에서 다음 작업을 수행할 수 있습니다(설정 및 구성에 따라서는 이러한 작업 중 일부만 완료하면 됨).

1.  Lync Server 보관 구성 설정을 수정하여 Exchange 보관을 사용하도록 설정합니다. 모든 배포에서 이 단계를 수행해야 합니다.

2.  사용자에 대한 내부 및/또는 외부 통신 내용 보관을 사용하도록 설정합니다. 모든 배포에서 이 단계를 수행해야 합니다.

3.  각 사용자에 대해 ExchangeArchivingPolicy 속성을 구성합니다. 이 단계는 서로 다른 포리스트에 있는 Lync Server와 Exchange에 대해서만 수행하면 됩니다.

## 1단계: Exchange 보관을 사용하도록 설정

Lync Server의 보관 기능은 기본적으로 보관 구성 설정을 사용하여 관리됩니다. Lync Server 2013을 설치하면 이러한 설정의 단일 전역 컬렉션이 자동으로 제공됩니다. 관리자는 원하는 경우 사이트 범위에서 보관 설정의 새 컬렉션을 만들 수 있습니다. 기본적으로 보관은 전역 설정에서 사용하도록 설정되지 않으며 이러한 설정에서 Exchange 보관이 사용하도록 설정되지도 않습니다. Exchange 보관을 사용하려면 관리자는 이러한 구성 설정에서 EnableArchiving 및 EnableExchangeArchiving 속성을 둘 다 구성해야 합니다. EnableArchiving 속성은 다음의 세 가지 값 중 하나로 설정할 수 있습니다.

  - **None** . 보관이 사용하지 않도록 설정됩니다. 이 값이 기본값입니다. EnableArchiving을 None으로 설정하면 Lync Server 보관 데이터베이스나 Exchange 2013에 아무런 항목도 보관되지 않습니다.

  - **ImOnly** . 인스턴트 메시지 대화 내용만 보관됩니다. Exchange 보관이 사용하도록 설정된 경우 이러한 대화 내용은 Exchange 2013에 보관됩니다. Exchange 보관이 사용하지 않도록 설정된 경우에는 이러한 대화 내용이 Lync Server에 보관됩니다.

  - **ImAndWebConf** . 인스턴트 메시지 대화 내용과 웹 회의 대화 내용이 모두 보관됩니다. Exchange 보관이 사용하도록 설정된 경우 이러한 대화 내용은 Exchange 2013에 보관됩니다. Exchange 보관이 사용하지 않도록 설정된 경우에는 이러한 대화 내용이 Lync Server에 보관됩니다.

EnableExchangeArchiving 속성은 부울 값입니다. Exchange 보관을 사용하도록 설정하려면 EnableExchangeArchiving을 True($True)로 설정하고, Exchange 보관을 사용하지 않도록 설정하려면 EnableExchangeArchiving을 False($False)로 설정합니다. 예를 들어 다음 명령은 인스턴트 메시징 대화 내용 보관과 Exchange 보관을 모두 사용하도록 설정합니다.

    Set-CsArchivingConfiguration -Identity "global" -EnableArchiving ImOnly -EnableExchangeArchiving $True

Exchange 보관을 사용하지 않도록 설정하려면 인스턴트 메시징 보관은 사용하도록 설정하되 Exchange로의 보관은 사용하지 않도록 설정하는(대화 내용이 Lync Server에 보관됨) 다음과 같은 명령을 사용합니다.

    Set-CsArchivingConfiguration -Identity "global" -EnableArchiving ImOnly -EnableExchangeArchiving $False


> [!NOTE]
> EnableArchiving 속성을 None으로 설정하면 Lync Server에서는 인스턴트 메시징 및 웹 회의 대화 내용을 보관하지 않습니다. 이 경우 서버는 EnableExchangeArchiving에 대해 구성된 값을 무시합니다.



Lync Server 제어판을 통해 Exchange 보관을 사용하거나 사용하지 않도록 설정할 수도 있습니다. 이렇게 하려면 다음 절차를 완료합니다.

1.  제어판에서 **모니터링 및 보관** 을 클릭하고 **보관 구성** 을 클릭합니다.

2.  **보관 구성** 탭에서 수정할 보관 설정 컬렉션(예: **Global** 컬렉션)을 두 번 클릭합니다.

3.  **보관 설정 편집** 창에서 **보관 설정** 드롭다운 목록을 클릭하고 **메신저 대화 세션 보관** (인스턴트 메시징 세션만 보관) 또는 **메신저 대화 및 웹 회의 세션 보관** (인스턴트 메시징 및 웹 회의 세션을 모두 보관)을 선택합니다.

4.  보관할 항목을 선택한 후 **Exchange Server 통합** 확인란을 선택하여 Exchange 보관을 사용하도록 설정합니다. Exchange 보관을 사용하지 않도록 설정하려면 이 확인란의 선택을 취소합니다.


> [!NOTE]
> <STRONG>Exchange Server 통합</STRONG> 확인란은 <STRONG>보관 설정</STRONG> 이 <STRONG>보관 사용 안 함</STRONG> 으로 설정되어 있으면 사용할 수 없습니다. 먼저 보관을 사용하도록 설정한 후에 Exchange 보관을 사용하도록 설정해야 합니다.



Lync Server 2013과 Exchange 2013이 같은 포리스트에 있으면 개별 사용자(또는 최소한 Exchange 2013에 전자 메일 계정이 있는 사용자)에 대한 보관은 Exchange 원본 위치 유지 정책을 사용하여 관리됩니다. 이전 버전 Exchange에 사용자가 있는 경우 해당 사용자에 대한 보관은 Lync Server 보관 정책을 사용하여 관리됩니다. Exchange 2013에 계정이 있는 사용자만 Lync 대화 내용을 Exchange에 보관할 수 있습니다.

Lync Server 2013과 Exchange 2013이 서로 다른 포리스트에 있으면 개별 사용자 계정에 대해 ExchangeArchivingPolicy 속성을 구성하여 개별 사용자에 대한 보관을 관리합니다. 자세한 내용은 3단계를 참조하십시오.

## 2단계: 내부 및/또는 외부 통신 보관을 사용하도록 설정

보관 및 Exchange 보관을 사용하도록 설정한 후에는 적절한 보관 정책을 수정하여 사용자 세션이 실제로 보관되는지 확인해야 합니다. 1단계를 수행하여 보관을 사용하도록 설정한다고 해서 Lync Server가 인스턴트 메시징 및 웹 회의 대화 내용 보관을 시작하는 것은 아닙니다. 대신 보관 정책을 사용하여 내부 및/또는 외부 보관을 사용하도록 설정해야 합니다. Lync Server 2013을 설치하면 다음의 두 속성을 포함하는 단일 전역 보관 정책도 설치됩니다.

  - **ArchiveInternal** . True($True)로 설정하면 조직에 Active Directive 계정이 있는 사용자만 참가하는 내부 통신 세션이 보관됩니다.

  - **ArchiveExternal** . True($True)로 설정하면 조직에 Active Directive 계정이 없는 사용자가 한 명 이상 참가하는 내부 통신 세션이 보관됩니다.

기본적으로 이 두 속성 값은 모두 False로 설정되므로 내부 및 외부 통신 세션이 모두 보관되지 않습니다. 글로벌 정책을 수정하려면 Lync Server 관리 셸 및 Set-CsArchivingPolicy cmdlet을 사용하면 됩니다. 다음 명령을 실행하면 내부 및 외부 통신 세션 보관이 모두 사용하도록 설정됩니다.

    Set-CsArchivingPolicy -Identity "global" -ArchiveInternal $True -ArchiveExternal $True

New-CsArchivingPolicy를 사용하여 사이트 범위 또는 사용자별 범위에서 새 정책을 만들 수도 있습니다. 예를 들어 다음 명령은 RedmondArchivingPolicy라는 새 사용자별 보관 정책을 만듭니다.

    New-CsArchivingPolicy -Identity "RedmondArchivingPolicy" -ArchiveInternal $True -ArchiveExternal $True

사용자별 정책을 만드는 경우에는 해당 정책을 적절한 사용자에게 할당해야 합니다. 예를 들면 다음과 같습니다.

    Grant-CsArchivingPolicy -Identity "Ken Myer" -PolicyName  "RedmondArchivingPolicy"

Lync Server 제어판을 사용하여 보관 정책을 관리할 수도 있습니다. 제어판 내에서 **모니터링 및 보관** 을 클릭하고 **보관 구성** 을 클릭합니다. 기존 정책을 수정하려면 정책(예: Global)을 두 번 클릭하고 **보관 정책 편집** 창에서 **내부 통신 보관** 및 **외부 통신 보관** 확인란을 필요한 대로 선택하거나 선택을 취소합니다. 새 보관 정책을 만들려면 **새로 만들기** 를 클릭하고 **사이트 정책** 또는 **사용자 정책** 을 선택합니다. 새 사용자 정책을 만들려면 **사용자** 탭에서 적절한 사용자 계정에 액세스하여 새 정책을 해당 사용자에게 할당해야 합니다.

## 3단계: ExchangeArchivingPolicy 정책 구성

Lync Server 2013과 Exchange 2013이 서로 다른 포리스트에 있는 경우에는 단순히 보관 구성 설정에서 Exchange 보관을 사용하도록 설정하는 것은 충분하지 않습니다. 이렇게 해도 Lync Server에 인스턴트 메시징 및 웹 회의 대화 내용이 보관되지 않습니다. 대신 각 관련 Exchange 사용자 계정에 대해 ExchangeArchivingPolicy 속성도 구성해야 합니다. 이 속성은 다음의 네 가지 값 중 하나로 설정할 수 있습니다.

1.  Uninitialized. 보관이 사용자 Exchange 사서함에 대해 구성된 원본 위치 유지 설정을 기반으로 함을 나타냅니다. 사용자 사서함에 대해 원본 위치 유지가 사용하도록 설정되지 않은 경우에는 사용자의 메시징 및 웹 회의 대화 내용이 Lync Server에 보관됩니다.

2.  **UseLyncArchivingPolicy** . 사용자의 인스턴트 메시징 및 웹 회의 대화 내용을 Exchange가 아닌 Lync Server에 보관해야 함을 나타냅니다.

3.  **NoArchiving** . 사용자의 인스턴트 메시징 및 웹 회의 대화 내용을 보관하지 않음을 나타냅니다. 이 설정은 사용자에게 할당된 모든 Lync Server 보관 정책을 다시 설정합니다.

4.  **ArchivingToExchange** . 사용자 사서함에 할당된 원본 위치 유지 설정(설정이 할당되지 않은 경우에도 마찬가지)에 관계없이 사용자의 인스턴트 메시징 및 웹 회의 대화 내용을 Exchange에 보관해야 함을 나타냅니다.

예를 들어 인스턴트 메시징 및 웹 회의 대화 내용이 항상 Exchange에 보관되도록 사용자 계정을 구성하려면 Lync Server 관리 셸에서 다음과 같은 명령을 사용하면 됩니다.

    Set-CsUser -Identity "Ken Myer" -ExchangeArchivingPolicy ArchivingToExchange

사용자 그룹(예: 지정된 등록자 풀에 있는 모든 사용자)에 대해 같은 보관 정책을 설정하려면 다음과 같은 명령을 사용하면 됩니다.

    Get-CsUser -Filter {RegistrarPool -eq "atl-cs-001.litwareinc.com"} | Set-CsUser -ExchangeArchivingPolicy ArchivingToExchange

ExchangeArchivingPolicy 속성 값을 구성하려면 Lync Server 관리 셸 및 Windows PowerShell을 사용해야 합니다. 이 속성은 Lync Server 제어판 관리자에게 표시되지 않습니다.

특정 보관 정책이 할당된 모든 사용자의 목록을 확인하려면 다음과 같은 명령을 사용하면 됩니다(ExchangeArchivingPolicy 속성이 Uninitialized로 설정된 모든 사용자의 Active Directory 표시 이름이 반환됨).

    Get-CsUser | Where-Object {$_.ExchangeArchivingPolicy -eq "Uninitialized"} | Select-Object DisplayName

마찬가지로 다음 명령은 ExchangeArchivingPolicy 속성이 UseLyncArchivingPolicy로 설정되지 않은 사용자의 표시 이름을 반환합니다.

    Get-CsUser | Where-Object {$_.ExchangeArchivingPolicy -ne "UseLyncArchivingPolicy"} | Select-Object DisplayName

