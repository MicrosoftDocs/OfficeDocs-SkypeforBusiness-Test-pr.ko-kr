---
title: 할당되지 않은 번호 범위 삭제
TOCTitle: 할당되지 않은 번호 범위 삭제
ms:assetid: a8141bfb-b94d-4d0f-a7a9-2e60d10b103a
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg182565(v=OCS.15)
ms:contentKeyID: 49304645
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# 할당되지 않은 번호 범위 삭제

 

_**마지막으로 수정된 항목:** 2012-11-01_

알림에 대해 할당되지 않은 번호 범위를 삭제하려면 다음 절차를 따르십시오.

## Lync Server 제어판을 사용하여 할당되지 않은 번호 범위를 삭제하려면

1.  RTCUniversalServerAdmins 그룹의 구성원이나 CsVoiceAdministrator, CsServerAdministrator 또는 CsAdministrator 역할의 구성원으로 컴퓨터에 로그온합니다. 자세한 내용은 [Lync Server 2013에서 설치 권한 위임](lync-server-2013-delegate-setup-permissions.md)을 참조하세요.

2.  브라우저 창을 연 다음 Admin URL을 입력하여 Lync Server 제어판을 엽니다. Lync Server 제어판을 시작하는 데 사용할 수 있는 다양한 방법에 대한 자세한 내용은 [Lync Server 관리 도구 열기](lync-server-2013-open-lync-server-administrative-tools.md)를 참조하세요.

3.  왼쪽 탐색 모음에서 **음성 기능**을 클릭하고 **지정되지 않은 번호**를 클릭합니다.

4.  **지정되지 않은 번호** 페이지의 검색 필드에 삭제할 할당되지 않은 번호 범위의 이름 일부나 전체를 입력합니다.

5.  결과 번호 범위 목록에서 이름을 클릭하고 **편집**을 클릭한 다음 **자세한 정보 표시**를 클릭합니다.

6.  **모두 커밋**을 클릭합니다.

## cmdlet을 사용하여 할당되지 않은 번호 범위를 삭제하려면

1.  Lync Server 관리 셸이 설치된 컴퓨터에 RTCUniversalServerAdmins 그룹의 구성원으로 로그온하거나 [Lync Server 2013에서 설치 권한 위임](lync-server-2013-delegate-setup-permissions.md)에 설명된 대로 필요한 사용자 권한으로 로그온합니다.

2.  Lync Server 관리 셸 시작: **시작**, **모든 프로그램**, **Microsoft Lync Server 2013**을 차례로 클릭한 다음 **Lync Server 관리 셸**을 클릭합니다.

3.  명령줄에 다음을 입력합니다.
    
        Remove-CsUnassignedNumber -Identity "<name of unassigned number range>" 
    
    예를 들면 다음과 같습니다.
    
        Remove-CsUnassignedNumber -Identity "Unassigned range 1"
    

    > [!NOTE]
    > 추가 옵션에 대한 자세한 내용은 <A href="remove-cscallparkorbit.md">Remove-CsCallParkOrbit</A>를 참조하십시오.



## 참고 항목

#### 작업

[Lync Server 2013에서 할당되지 않은 번호 범위 만들기 또는 수정](lync-server-2013-create-or-modify-an-unassigned-number-range.md)  

#### 기타 리소스

[Remove-CsUnassignedNumber](remove-csunassignednumber.md)  
[Get-CsUnassignedNumber](get-csunassignednumber.md)

