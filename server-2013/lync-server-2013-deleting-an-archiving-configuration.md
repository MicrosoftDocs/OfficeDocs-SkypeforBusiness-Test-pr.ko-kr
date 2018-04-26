---
title: 보관 구성 삭제
TOCTitle: 보관 구성 삭제
ms:assetid: a8744d39-5cf2-474c-9a99-a0f3a37f846f
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/JJ205167(v=OCS.15)
ms:contentKeyID: 49304651
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# 보관 구성 삭제

 

_**마지막으로 수정된 항목:** 2013-02-23_

사이트 구성 또는 풀 구성은 삭제할 수 있습니다. 전역 정책은 제거할 수 없습니다. 전역 구성을 삭제하는 경우 자동으로 구성이 기본값으로 다시 설정됩니다. 지정할 수 있는 옵션과 보관 구성의 계층 구조를 비롯하여 보관 구성이 구현되는 방식에 대한 자세한 내용은 계획 설명서, 배포 설명서 또는 작업 설명서에서 [Lync Server 2013의 보관 작동 방식](lync-server-2013-how-archiving-works.md)을 참조하십시오.

## 보관을 위해 사이트 또는 풀 구성을 삭제하려면

1.  CsArchivingAdministrator 또는 CsAdministrator 역할에 할당된 사용자 계정에서 내부 배포된 컴퓨터에 로그온합니다.

2.  브라우저 창을 연 다음 Admin URL을 입력하여 Lync Server 제어판을 엽니다. Lync Server 제어판을 시작하는 데 사용할 수 있는 다양한 방법에 대한 자세한 내용은 [Lync Server 관리 도구 열기](lync-server-2013-open-lync-server-administrative-tools.md)를 참조하세요.

3.  왼쪽 탐색 모음에서 **모니터링 및 보관**을 클릭하고 **보관 구성**을 클릭합니다.

4.  보관 구성 목록에서 삭제할 사이트 또는 풀 구성을 클릭하고 **편집**을 클릭한 다음 **삭제**를 클릭합니다.

5.  **커밋**을 클릭합니다.

## Lync Server 관리 셸 cmdlet을 사용하여 보관 구성 설정 제거

Windows PowerShell 및 Remove-CsArchivingConfiguration cmdlet을 사용하여 보관 구성 설정을 삭제할 수도 있습니다. 이 cmdlet은 Lync Server 2013 관리 셸 또는 Windows PowerShell의 원격 세션에서 실행할 수 있습니다.

## 보관 구성 설정의 지정된 컬렉션 제거

  - 다음 명령은 Redmond 사이트에 적용된 보관 구성 설정을 제거합니다.
    
        Remove-CsArchivingConfiguration -Identity "site:Redmond"

## 사이트 범위에 적용된 모든 보관 구성 설정 제거

  - 다음 명령은 서비스 범위에 적용된 모든 보관 구성 설정을 제거합니다.
    
        Get-CsArchivingConfiguration -Filter "site:*" | Remove-CsArchivingConfiguration

## 지정된 속성 값을 기반으로 보관 구성 설정 제거

  - 다음 명령은 Exchange 보관을 사용할 수 없도록 설정된 모든 보관 구성 설정을 제거합니다.
    
        Get-CsArchivingConfiguration | Where-Object {$_.EnableExchangeArchiving -eq $False} | Remove-CsArchivingConfiguration

자세한 내용은 [Remove-CsArchivingConfiguration](remove-csarchivingconfiguration.md) cmdlet에 대한 도움말 항목을 참조하십시오.

## 참고 항목

#### 개념

[Lync Server 2013의 보관 작동 방식](lync-server-2013-how-archiving-works.md)  

#### 기타 리소스

[Lync Server 2013에서 내부 및 외부 통신의 보관 관리](lync-server-2013-managing-the-archiving-of-internal-and-external-communications.md)

