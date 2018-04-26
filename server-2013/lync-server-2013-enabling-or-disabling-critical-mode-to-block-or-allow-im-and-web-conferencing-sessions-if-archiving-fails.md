---
title: 보관하지 못할 경우 IM 및 웹 회의 세션을 차단 또는 허용하도록 중요 모드 사용 또는 사용 안 함
TOCTitle: 보관하지 못할 경우 IM 및 웹 회의 세션을 차단 또는 허용하도록 중요 모드 사용 또는 사용 안 함
ms:assetid: fafdcd2e-b778-4ed5-a25f-09208aa3b699
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg182609(v=OCS.15)
ms:contentKeyID: 49305599
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# 보관하지 못할 경우 IM 및 웹 회의 세션을 차단 또는 허용하도록 중요 모드 사용 또는 사용 안 함

 

_**마지막으로 수정된 항목:** 2013-02-23_

Lync Server 2013 제어판에서는 보관 구성을 사용하여 중요 모드를 사용하거나 사용하지 않도록 설정할 수 있습니다. 여기에는 다음 보관 구성이 포함됩니다.

  - Lync Server 2013을 배포할 때 기본적으로 만들어지는 전역 구성

  - 특정 사이트나 풀에 대해 보관이 어떻게 구현되는지를 지정하기 위해 만들고 사용할 수 있는 사이트 수준 및 풀 수준의 구성(선택 사항)

처음에 보관을 배포할 때 보관 구성을 설정하지만, 배포 후에 구성을 변경, 추가 및 삭제할 수 있습니다. 지정할 수 있는 옵션과 보관 구성 계층 구조를 비롯하여 보관 구성 구현 방식에 대한 자세한 내용은 계획 설명서, 배포 설명서 또는 작업 설명서에서 [Lync Server 2013의 보관 작동 방식](lync-server-2013-how-archiving-works.md)을 참조하십시오.


> [!NOTE]
> 보관을 사용하려면 내부 통신용, 외부 통신용 아니면 Lync Server 2013에 있는 사용자용으로 보관을 사용할지 여부를 지정할 보관 정책을 구성해야 합니다. 기본적으로는 내부 또는 외부 통신에는 보관을 사용할 수 없습니다. 정책에서 보관을 사용하도록 설정하기 전에 이 섹션에 설명된 대로 배포와 특정 사이트 및 풀(선택 사항)에 적합한 보관 구성을 지정해야 합니다. 보관 사용에 대한 자세한 내용은 배포 설명서에서 <A href="lync-server-2013-configuring-and-assigning-archiving-policies.md">보관 정책 구성 및 할당</A>을 참조하십시오.<BR>보관을 배포한 후에 Exchange Server 통합을 사용하여 Exchange 2013 서버에 있는 보관 데이터 및 파일과 Exchange 2013 서버에 있는 모든 사용자를 저장하기로 결정한 경우 토폴로지에서 SQL Server 데이터베이스 구성을 제거해야 합니다. 이 작업을 위해서는 토폴로지 작성기를 사용해야 합니다. 자세한 내용은 작업 설명서에서 <A href="lync-server-2013-changing-archiving-database-options.md">Lync Server 2013에서 데이터베이스 보관 옵션 변경</A>을 참조하십시오.



## 보관이 실패할 경우 IM 및 웹 회의 세션 차단을 사용하거나 사용하지 않으려면

1.  CsArchivingAdministrator 또는 CsAdministrator 역할에 할당된 사용자 계정에서 내부 배포된 컴퓨터에 로그온합니다.

2.  브라우저 창을 연 다음 Admin URL을 입력하여 Lync Server 제어판을 엽니다. Lync Server 제어판을 시작하는 데 사용할 수 있는 다양한 방법에 대한 자세한 내용은 [Lync Server 관리 도구 열기](lync-server-2013-open-lync-server-administrative-tools.md)를 참조하세요.

3.  왼쪽 탐색 모음에서 **모니터링 및 보관**을 클릭하고 **보관 구성**을 클릭합니다.

4.  보관 구성 목록에서 적당한 전역, 사이트 또는 풀 구성을 클릭하고, **편집**, **자세한 정보 표시**를 차례로 클릭한 후 다음을 수행합니다.

5.  보관이 실패할 경우 보관이 작동되는 방식을 설정하려면 **보관이 실패할 경우 IM(인스턴트 메시징) 또는 웹 회의 세션 차단** 확인란을 선택하거나 선택 취소합니다.

6.  **커밋**을 클릭합니다.

## Lync ServerWindows PowerShell Cmdlet을 사용하여 중요 모드 사용/사용 안 함

**Set-CsArchivingConfiguration** cmdlet을 사용하여 중요 모드를 사용하거나 사용하지 않도록 설정할 수 있습니다. Lync Server 2013 관리 셸 또는 Windows PowerShell의 원격 세션에서 이 cmdlet을 실행할 수 있습니다. 원격 Windows PowerShell을 사용하여 Lync Server에 연결하는 방법에 대한 자세한 내용은 Lync Server Windows PowerShell 블로그 문서인 "빠른 시작: 원격 PowerShell을 사용하여 Microsoft Lync Server 2010 관리"([http://go.microsoft.com/fwlink/p/?linkId=255876](http://go.microsoft.com/fwlink/p/?linkid=255876))를 참조하세요.

## 중요 모드 사용

  - 중요 모드를 사용하려면 BlockOnArchiveFailure 속성의 값을 True($True)로 설정합니다. 예를 들면 다음과 같습니다.
    
        Set-CsArchivingConfiguration -Identity "site:Redmond" -BlockOnArchiveFailure $True

## 중요 모드 사용 안 함

  - 중요 모드를 사용하지 않으려면 BlockOnArchiveFailure 속성의 값을 False($False)로 설정합니다. 예를 들면 다음과 같습니다.
    
        Set-CsArchivingConfiguration -Identity "site:Redmond" -BlockOnArchiveFailure $False

자세한 내용은 [Set-CsArchivingConfiguration](set-csarchivingconfiguration.md) cmdlet 관련된 도움말 항목을 참조하십시오.

## 참고 항목

#### 작업

[Lync Server 2013에서 데이터베이스 보관 옵션 변경](lync-server-2013-changing-archiving-database-options.md)  

#### 개념

[Lync Server 2013의 보관 작동 방식](lync-server-2013-how-archiving-works.md)  

#### 기타 리소스

[Lync Server 2013에서 조직, 사이트 및 풀에 대한 보관 구성 옵션 관리](lync-server-2013-managing-archiving-configuration-options-for-your-organization-sites-and-pools.md)

