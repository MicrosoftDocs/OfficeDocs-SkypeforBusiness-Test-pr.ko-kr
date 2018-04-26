---
title: Lync Server 2013에서 조직, 사이트 및 풀에 대한 보관 구성 옵션 관리
TOCTitle: Lync Server 2013에서 조직, 사이트 및 풀에 대한 보관 구성 옵션 관리
ms:assetid: 377a6f80-5f2b-4bc1-b507-e930a461fb1d
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/JJ204802(v=OCS.15)
ms:contentKeyID: 49303309
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Lync Server 2013에서 조직, 사이트 및 풀에 대한 보관 구성 옵션 관리

 

_**마지막으로 수정된 항목:** 2012-11-01_

Lync Server 2013 제어판에서는 보관 구성을 사용하여 보관 구현 방법을 지정합니다. 여기에는 다음과 같은 보관 구성이 포함됩니다.

  - Lync Server 2013 배포 시 기본적으로 만들어지는 전역 구성

  - 직접 만들어 특정 사이트 또는 풀에 대한 보관 구현 방법을 지정하는 데 사용할 수 있는 선택적 사이트 수준 및 풀 수준 구성

보관을 배포할 때 보관 구성을 처음 설정하지만 배포 후에 구성을 변경, 추가 및 삭제할 수 있습니다. Lync Server 2013 제어판에서는 **보관 및 모니터링** 그룹의 **보관 구성** 페이지를 사용하여 전역/사이트/풀 수준에서 구성을 관리할 수 있습니다. 지정 가능한 옵션 및 보관 구성의 계층 구조를 비롯하여 보관 구성을 구현하는 방법에 대한 자세한 내용은 계획 설명서, 배포 설명서 또는 작업 설명서에서 [Lync Server 2013의 보관 작동 방식](lync-server-2013-how-archiving-works.md)을 참조하십시오.


> [!NOTE]
> 보관을 사용하려면 Lync Server 2013에 있는 모든 사용자에 대해 내부 통신이나 외부 통신 중 하나 또는 둘 다에 대해 보관을 사용하도록 설정할지 여부를 지정하는 보관 정책을 구성해야 합니다. 기본적으로는 내부 또는 외부 통신에 대해 보관이 사용하도록 설정되지 않습니다. Microsoft Exchange 통합을 사용하는 경우에는 Exchange 2013에 있으며 해당 사서함이 원본 위치 유지 상태인 모든 사용자에 대해 보관을 지원하도록 Exchange 2013을 설정 및 구성해야 합니다.<BR>정책에서 보관을 사용하도록 설정하기 전에 이 섹션에서 설명하는 대로 배포에 대해 적절한 보관 구성을 지정해야 하며 원하는 경우 특정 사이트와 풀에 대해서도 구성을 지정해야 합니다. 보관을 사용하도록 설정하는 방법에 대한 자세한 내용은 배포 설명서에서 <A href="lync-server-2013-configuring-and-assigning-archiving-policies.md">보관 정책 구성 및 할당</A>을 참조하십시오.



**Lync Server 관리 셸 cmdlet을 사용하여 보관 구성 정보를 보려면**

  - Lync ServerWindows PowerShell 및 **Get-CsArchivingConfiguration** cmdlet을 사용하여 보관 구성 정보를 확인할 수도 있습니다. 이 cmdlet은 Lync Server 2013 관리 셸 또는 Windows PowerShell의 원격 세션에서 실행할 수 있습니다. 원격 Windows PowerShell을 사용하여 Lync Server에 연결하는 방법에 대한 자세한 내용은 Lync Server Windows PowerShell 블로그 문서인 "빠른 시작: 원격 PowerShell을 사용하여 Microsoft Lync Server 2010 관리"([http://go.microsoft.com/fwlink/p/?linkId=255876](http://go.microsoft.com/fwlink/p/?linkid=255876))를 참조하세요.
    
    Lync Server 관리 셸에서 다음 명령을 사용하여 모든 보관 구성 설정에 대한 정보를 확인합니다.
    
        Get-CsArchivingConfiguration

## 이 단원의 내용

  - [보관 구성을 만들어서 특정 사이트나 풀에 대한 보관 관리](lync-server-2013-creating-an-archiving-configuration-to-manage-archiving-for-specific-sites-or-pools.md)

  - [IM 또는 회의 세션 보관 사용 또는 사용 안 함](lync-server-2013-enabling-or-disabling-archiving-of-im-or-conferencing-sessions.md)

  - [보관 데이터 제거 사용 또는 사용 안 함](lync-server-2013-enabling-or-disabling-the-purging-of-archived-data.md)

  - [보관하지 못할 경우 IM 및 웹 회의 세션을 차단 또는 허용하도록 중요 모드 사용 또는 사용 안 함](lync-server-2013-enabling-or-disabling-critical-mode-to-block-or-allow-im-and-web-conferencing-sessions-if-archiving-fails.md)

  - [Lync Server 2013에서 페더레이션 파트너에게 보관 고지 사항 보내기를 사용하거나 사용하지 않도록 설정](lync-server-2013-enable-or-disable-sending-an-archiving-disclaimer-to-federated-partners.md)

  - [Exchange Storage와 통합 사용 또는 사용 안 함](lync-server-2013-enabling-or-disabling-integration-with-exchange-storage.md)

  - [보관 구성 삭제](lync-server-2013-deleting-an-archiving-configuration.md)

## 참고 항목

#### 기타 리소스

[Lync Server 2013 보관 관리](lync-server-2013-managing-archiving.md)

