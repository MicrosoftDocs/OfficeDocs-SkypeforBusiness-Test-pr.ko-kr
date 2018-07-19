---
title: (선택 사항) Lync Server 2013에서 응답 그룹 휴일 집합 정의
TOCTitle: (선택 사항) Lync Server 2013에서 응답 그룹 휴일 집합 정의
ms:assetid: 56c37b3b-6517-49b9-86b7-ae48cc349119
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/JJ688063(v=OCS.15)
ms:contentKeyID: 49885773
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# (선택 사항) Lync Server 2013에서 응답 그룹 휴일 집합 정의

 

_**마지막으로 수정된 항목:** 2014-02-07_

휴일 설정에서는 응답 그룹이 근무하지 않는 요일을 정의하고 해당 요일에 수행할 작업을 지정합니다. 휴일 집합은 응답 그룹에 적용되는 휴일의 컬렉션입니다.


> [!NOTE]
> 워크플로가 관리 워크플로로 정의되었고 모든 사용자가 여기에 지정된 경우, CsResponseGroupManager 역할이 자신이 관리하는 워크플로에 대한 휴일을 설정하고 수정할 수 있습니다.



## 휴일 집합을 만들려면

1.  RTCUniversalServerAdmins 그룹의 구성원이나 응답 그룹을 지원하는 미리 정의된 관리 역할 중 하나의 구성원으로 로그온합니다.

2.  Lync Server 관리 셸 시작: **시작**, **모든 프로그램**, **Microsoft Lync Server 2013**을 차례로 클릭한 다음 **Lync Server 관리 셸**을 클릭합니다.

3.  정의할 각 휴일에 대해 다음을 실행합니다.
    
        $x = New-CsRgsHoliday [-Name <holiday name>] -StartDate <starting date of holiday> -EndDate <ending date of holiday>
    
    정의한 휴일이 포함된 휴일 집합을 만들려면 다음을 실행합니다.
    
        New-CsRgsHolidaySet -Parent <service where the workflow is hosted> -Name <unique name for holiday set> -HolidayList <one or more holidays to be included in the holiday set>
    
    다음 예에서는 두 개의 휴일이 포함된 휴일 집합을 보여 줍니다.
    
        $a = New-CsRgsHoliday -Name "New Year's Day" -StartDate "1/1/2013 12:00 AM" -EndDate "1/1/2013 12:00 AM" 
        $b = New-CsRgsHoliday -Name "Independence Day" -StartDate "7/4/2013 12:00 AM" -EndDate "7/5/2013 12:00 AM" 
        New-CsRgsHolidaySet -Parent "ApplicationServer:Redmond.contoso.com -Name "2013 Holidays" -HolidayList ($a, $b)

## 참고 항목

#### 개념

[Lync Server 2013에서 헌트 그룹 워크플로 만들기 또는 수정](lync-server-2013-create-or-modify-a-hunt-group-workflow.md)  
[Lync Server 2013에서 대화형 워크플로 만들기 또는 수정](lync-server-2013-create-or-modify-an-interactive-workflow.md)  

#### 기타 리소스

[New-CsRgsHoliday](https://docs.microsoft.com/en-us/powershell/module/skype/New-CsRgsHoliday)  
[New-CsRgsHolidaySet](https://docs.microsoft.com/en-us/powershell/module/skype/New-CsRgsHolidaySet)

