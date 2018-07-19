---
title: 사용자에게 보관 정책 적용
TOCTitle: 사용자에게 보관 정책 적용
ms:assetid: 624a7d3e-389d-403a-97e5-f7bb17023ef3
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg521004(v=OCS.15)
ms:contentKeyID: 49303820
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# 사용자에게 보관 정책 적용

 

_**마지막으로 수정된 항목:** 2013-02-23_

Lync Server 2013에 대해 사용자가 설정되었고 Lync Server 2013에 있는 사용자의 보관에 대해 하나 이상의 사용자 정책을 만든 경우, 해당 사용자 또는 사용자 그룹에 적합한 정책을 적용하여 특정 사용자에 대한 보관 지원을 구현할 수 있습니다. 예를 들어 내부 통신의 보관을 지원하기 위한 정책을 만들었으면 이를 하나 이상의 사용자 또는 사용자 그룹에 적용하여 해당 사용자의 Lync Server 2013 통신에 대해 보관 기능을 지원할 수 있습니다.


> [!NOTE]
> 배포에 Microsoft Exchange 통합을 사용하도록 설정할 경우 Exchange 원본 위치 유지 정책은 Exchange 2013에 있고 사서함이 원본 위치 유지로 설정된 사용자에 대해 보관을 설정할지 여부를 제어합니다. 자세한 내용은 배포 설명서에서 <A href="lync-server-2013-setting-up-policies-for-archiving-when-using-exchange-server-integration.md">Exchange Server 통합 사용 시 보관용 정책 설정</A>을 참조하십시오.<BR>보관을 사용하도록 설정하기 전에 보관 구성에서 모든 적합한 옵션을 지정해야 합니다. 자세한 내용은 작업 설명서에서 <A href="lync-server-2013-managing-archiving-configuration-options-for-your-organization-sites-and-pools.md">Lync Server 2013에서 조직, 사이트 및 풀에 대한 보관 구성 옵션 관리</A>를 참조하십시오.



이 항목의 절차를 사용하여 이전에 만든 보관 사용자 정책을 하나 이상의 사용자 계정 또는 사용자 그룹에 적용합니다.

## 사용자 계정에 보관 사용자 정책을 적용하려면

1.  CsArchivingAdministrator 또는 CsAdministrator 역할에 할당된 사용자 계정에서 내부 배포된 컴퓨터에 로그온합니다.

2.  브라우저 창을 연 다음 Admin URL을 입력하여 Lync Server 제어판을 엽니다. Lync Server 제어판을 시작하는 데 사용할 수 있는 다양한 방법에 대한 자세한 내용은 [Lync Server 관리 도구 열기](lync-server-2013-open-lync-server-administrative-tools.md)를 참조하세요.

3.  왼쪽 탐색 모음에서 **사용자**를 클릭하고 구성하려는 사용자 계정을 검색합니다.

4.  검색 결과가 나열된 표에서 사용자 계정을 클릭하고 **편집**을 클릭한 후에 **세부 정보 표시**를 클릭합니다.

5.  **보관 정책** 아래의 **Lync Server 사용자 편집**에서 적용하려는 보관 사용자 정책을 선택합니다.
    

    > [!NOTE]
    > <STRONG>&lt;자동&gt;</STRONG> 설정을 선택하면 기본 서버 설치 설정이 적용됩니다. 이러한 설정은 서버에 의해 자동으로 적용됩니다.



6.  **커밋**을 클릭합니다.

## Lync Server 관리 셸 Cmdlet을 사용하여 사용자별 보관 정책 지정

사용자별 보관 정책은 Lync ServerWindows PowerShell 및 **Grant-CsArchivingPolicy** cmdlet을 사용하여 지정할 수도 있습니다. 이 cmdlet은 Lync Server 2013 관리 셸 또는 Windows PowerShell의 원격 세션에서 실행할 수 있습니다. 원격 Windows PowerShell을 사용하여 Lync Server에 연결하는 방법에 대한 자세한 내용은 Lync Server Windows PowerShell 블로그 문서인 "빠른 시작: 원격 PowerShell을 사용하여 Microsoft Lync Server 2010 관리"([http://go.microsoft.com/fwlink/p/?linkId=255876](http://go.microsoft.com/fwlink/p/?linkid=255876))를 참조하세요.

## 사용자별 보관 정책을 단일 사용자에게 지정

  - 다음 명령은 사용자별 보관 정책 RedmondArchivingPolicy를 Ken Myer라는 사용자에게 지정합니다.
    
        Grant-CsArchivingPolicy -Identity "Ken Myer" -PolicyName "RedmondArchivingPolicy"

## 사용자별 보관 정책을 여러 사용자에게 지정

  - 이 명령은 사용자별 보관 정책 RedmondArchivingPolicy를 계정이 등록자 풀 atl-cs-001.litwareinc.com에 있는 모든 사용자에게 지정합니다. 이 명령에 사용되는 필터 매개 변수에 대한 자세한 내용은 [Get-CsUser](https://docs.microsoft.com/en-us/powershell/module/skype/Get-CsUser) cmdlet 설명서를 참조하십시오.
    
        Get-CsUser -Filter {RegistrarPool -eq "atl-cs-001.litwareinc.com"} | Grant-CsArchivingPolicy -PolicyName "RedmondArchivingPolicy"

## 사용자별 보관 정책 지정 해제

  - 다음 명령은 이전에 Ken Myer에게 지정되었던 사용자별 보관 정책의 지정을 해제합니다. 사용자별 정책을 지정 해제한 후 Ken Myer는 자동으로 글로벌 정책 또는 로컬 사이트 정책(있는 경우)을 사용해서 관리됩니다. 사이트 정책은 글로벌 정책보다 우선 적용됩니다.
    
        Grant-CsArchivingPolicy -Identity "Ken Myer" -PolicyName $Null

자세한 내용은 [Grant-CsArchivingPolicy](https://docs.microsoft.com/en-us/powershell/module/skype/Grant-CsArchivingPolicy) cmdlet 설명서를 참조하십시오.

## 참고 항목

#### 기타 리소스

[Lync Server 2013에서 내부 및 외부 통신의 보관 관리](lync-server-2013-managing-the-archiving-of-internal-and-external-communications.md)  
[사용자별 정책 할당](lync-server-2013-assigning-per-user-policies.md)

