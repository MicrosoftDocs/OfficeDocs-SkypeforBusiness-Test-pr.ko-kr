---
title: 보관 데이터 제거 사용 또는 사용 안 함
TOCTitle: 보관 데이터 제거 사용 또는 사용 안 함
ms:assetid: 28cef09f-0970-4fc3-8315-f26689e3e187
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg520968(v=OCS.15)
ms:contentKeyID: 49303124
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# 보관 데이터 제거 사용 또는 사용 안 함

 

_**마지막으로 수정된 항목:** 2013-02-23_

Lync Server 2013 제어판 에서는 보관 구성을 사용하여 삭제를 사용 및 사용하지 않도록 설정하고 삭제 구현 방법을 구성합니다. 여기에는 다음과 같은 보관 구성이 포함됩니다.

  - Lync Server 2013 배포 시 기본적으로 만들어지는 전역 구성

  - 직접 만들어 특정 사이트 또는 풀에 대한 보관 구현 방법을 지정하는 데 사용할 수 있는 선택적 사이트 수준 및 풀 수준 구성

보관을 배포할 때 보관 구성을 처음 설정하지만 배포 후에 구성을 변경, 추가 및 삭제할 수 있습니다. 지정 가능한 옵션 및 보관 구성의 계층 구조를 비롯하여 보관 구성을 구현하는 방법에 대한 자세한 내용은 계획 설명서, 배포 설명서 또는 작업 설명서에서 [Lync Server 2013의 보관 작동 방식](lync-server-2013-how-archiving-works.md)을 참조하십시오.


> [!NOTE]
> Lync Server 2013에 있는 사용자에 대해 보관을 사용하려면 내부 통신이나 외부 통신 중 하나 또는 둘 다에 대해 보관을 사용하도록 설정할지 여부를 지정하는 보관 정책을 구성해야 합니다. 기본적으로는 내부 또는 외부 통신에 대해 보관이 사용하도록 설정되지 않습니다. 정책에서 보관을 사용하도록 설정하기 전에 이 섹션에서 설명하는 대로 배포에 대해 적절한 보관 구성을 지정해야 하며 원하는 경우 특정 사이트와 풀에 대해서도 구성을 지정해야 합니다. 보관을 사용하도록 설정하는 방법에 대한 자세한 내용은 배포 설명서에서 <A href="lync-server-2013-configuring-and-assigning-archiving-policies.md">보관 정책 구성 및 할당</A>을 참조하십시오.<BR>보관을 배포한 후 Microsoft Exchange 통합을 사용하여 보관 데이터 및 파일을 Exchange 2013 서버에 저장하려는 경우, 모든 사용자가 Exchange 2013 서버에 있으면 토폴로지에서 SQL Server 데이터베이스 구성을 제거해야 합니다. 이 작업은 토폴로지 작성기를 사용하여 수행해야 합니다. 자세한 내용은 작업 설명서에서 <A href="lync-server-2013-changing-archiving-database-options.md">Lync Server 2013에서 데이터베이스 보관 옵션 변경</A>을 참조하십시오.



## 보관 삭제를 사용하거나 사용하지 않도록 설정하려면

1.  CsArchivingAdministrator 또는 CsAdministrator 역할에 할당된 사용자 계정에서 내부 배포된 컴퓨터에 로그온합니다.

2.  브라우저 창을 연 다음 Admin URL을 입력하여 Lync Server 제어판을 엽니다. Lync Server 제어판을 시작하는 데 사용할 수 있는 다양한 방법에 대한 자세한 내용은 [Lync Server 관리 도구 열기](lync-server-2013-open-lync-server-administrative-tools.md)를 참조하세요.

3.  왼쪽 탐색 모음에서 **모니터링 및 보관**을 클릭하고 **보관 구성**을 클릭합니다.

4.  보관 구성 목록에서 적절한 전역, 사이트 또는 풀 구성의 이름을 클릭하고 **편집**을 클릭한 후에 **자세한 정보 표시**를 클릭하고 다음을 수행합니다.
    
      - 삭제를 사용하도록 설정하려면 **보관 데이터 삭제 사용** 확인란을 선택하고 다음 중 하나를 수행합니다.
        
          - 모든 레코드를 삭제하려면 **내보낸 보관 데이터 및 최대 기간(일)이 지난 저장된 보관 데이터 삭제**를 클릭하고 기간(일)을 지정합니다.
        
          - 내보낸 데이터만 삭제하려면 **내보낸 보관 데이터만 삭제**를 클릭합니다.
    
      - 삭제를 사용하지 않도록 설정하려면 **보관 데이터 삭제 사용** 확인란 선택을 취소합니다.

5.  **커밋**을 클릭합니다.

## Lync Server 관리 셸 cmdlet을 사용하여 보관 삭제를 사용 및 사용하지 않도록 설정

Windows PowerShell 및 **Set-CsArchivingConfiguration** cmdlet을 사용하여 보관 데이터의 자동 삭제 사용/사용 안 함을 관리할 수도 있습니다. 이 cmdlet은 Lync Server 2013 관리 셸 또는 Windows PowerShell의 원격 세션에서 실행할 수 있습니다. 원격 Windows PowerShell을 사용하여 Lync Server에 연결하는 방법에 대한 자세한 내용은 Lync Server Windows PowerShell 블로그 문서인 "빠른 시작: 원격 PowerShell을 사용하여 Microsoft Lync Server 2010 관리"([http://go.microsoft.com/fwlink/p/?linkId=255876](http://go.microsoft.com/fwlink/p/?linkid=255876))를 참조하세요.

## 모든 보관 데이터 삭제 사용

  - 모든 보관 데이터의 삭제를 사용하도록 설정하려면 **EnablePurging** 속성을 true($True)로 설정합니다. 예를 들면 다음과 같습니다.
    
        Set-CsArchivingConfiguration -Identity "site:Redmond" -EnablePurging $True
    
    이 명령을 실행하고 나면 Lync Server에서는 **KeepArchivingDataForDays** 속성에 대해 지정된 값보다 오래된 모든 보관 레코드를 매일 삭제합니다.

## 내보낸 보관 데이터 삭제만 사용

  - [Export-CsArchivingData](https://docs.microsoft.com/en-us/powershell/module/skype/Export-CsArchivingData) cmdlet을 사용하여 데이터 파일로 내보낸 보관 레코드만 삭제하려면 PurgeExportedArchivedOnly 속성도 True($True)로 설정해야 합니다. 예를 들면 다음과 같습니다.
    
        Set-CsArchivingConfiguration -Identity "site:Redmond" -EnablePurging $True -PurgeExportedArchivesOnly $True
    
    이 명령을 실행하고 나면 Lync Server에서는 두 가지 기준을 충족하는 보관 레코드, 즉 1) **KeepArchivingDataForDays** 속성에 대해 지정된 값보다 오래되었으며 2) **Export-CsArchivingData** cmdlet을 사용하여 내보낸 보관 레코드만 삭제합니다.

## 모든 보관 데이터 삭제 사용 안 함

  - 보관 레코드의 자동 삭제를 사용하지 않도록 설정하려면 **EnablePurging** 속성을 False($False)로 설정합니다. 예를 들면 다음과 같습니다.
    
        Set-CsArchivingConfiguration -Identity "site:Redmond" -EnablePurging $False

보관 데이터 삭제용 추가 옵션을 비롯한 자세한 내용은 [Set-CsArchivingConfiguration](https://docs.microsoft.com/en-us/powershell/module/skype/Set-CsArchivingConfiguration) cmdlet에 대한 도움말 항목을 참조하십시오.

## 참고 항목

#### 개념

[Lync Server 2013의 보관 작동 방식](lync-server-2013-how-archiving-works.md)  

#### 기타 리소스

[보관 정책 구성 및 할당](lync-server-2013-configuring-and-assigning-archiving-policies.md)  
[Lync Server 2013에서 조직, 사이트 및 풀에 대한 보관 구성 옵션 관리](lync-server-2013-managing-archiving-configuration-options-for-your-organization-sites-and-pools.md)

