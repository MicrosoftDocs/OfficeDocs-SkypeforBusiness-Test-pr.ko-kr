---
title: Lync Server 2013에서 통화 대기 파킹된 통화 번호 범위 삭제
TOCTitle: Lync Server 2013에서 통화 대기 파킹된 통화 번호 범위 삭제
ms:assetid: 85e9f916-062d-450d-ac0a-aeaefc0f7cdc
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg182546(v=OCS.15)
ms:contentKeyID: 49304264
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Lync Server 2013에서 통화 대기 파킹된 통화 번호 범위 삭제

 

_**마지막으로 수정된 항목:** 2013-02-20_

다음 절차 중 하나를 사용해서 통화 대기 번호 범위를 삭제합니다.

## Lync Server 제어판을 사용해서 통화 대기 번호 범위를 삭제하려면

1.  RTCUniversalServerAdmins 그룹의 구성원이나 CsVoiceAdministrator, CsServerAdministrator 또는 CsAdministrator 역할의 구성원으로 컴퓨터에 로그온합니다. 자세한 내용은 [Lync Server 2013에서 설치 권한 위임](lync-server-2013-delegate-setup-permissions.md)을 참조하세요.

2.  브라우저 창을 연 다음 Admin URL을 입력하여 Lync Server 제어판을 엽니다. Lync Server 제어판을 시작하는 데 사용할 수 있는 다양한 방법에 대한 자세한 내용은 [Lync Server 관리 도구 열기](lync-server-2013-open-lync-server-administrative-tools.md)를 참조하세요.

3.  왼쪽 탐색 모음에서 **음성 기능**을 클릭하고 **통화 대기**를 클릭합니다.

4.  **통화 대기** 페이지의 검색 필드에 삭제할 번호 범위의 이름 전부 또는 일부를 입력합니다.

5.  결과로 표시된 번호 목록에서 번호를 클릭하고 **편집**을 클릭한 후 **삭제**를 클릭합니다.

6.  **확인**을 클릭합니다.

## Cmdlet을 사용해서 통화 대기 번호 범위를 삭제하려면

1.  Lync Server 관리 셸이 설치된 컴퓨터에 RTCUniversalServerAdmins 그룹의 구성원으로 로그온하거나 [Lync Server 2013에서 설치 권한 위임](lync-server-2013-delegate-setup-permissions.md)에 설명된 대로 필요한 사용자 권한으로 로그온합니다.

2.  Lync Server 관리 셸 시작: **시작**, **모든 프로그램**, **Microsoft Lync Server 2013**을 차례로 클릭한 다음 **Lync Server 관리 셸**을 클릭합니다.

3.  명령줄에 다음을 입력합니다.
    
        Remove-CsCallParkOrbit -Identity "<orbit range name>" 
    
    예:
    
        Remove-CsCallParkOrbit -Identity "Redmond orbit 1"
    

    > [!NOTE]
    > 추가 옵션에 대한 자세한 내용은 <A href="remove-cscallparkorbit.md">Remove-CsCallParkOrbit</A>를 참조하십시오.



## 참고 항목

#### 작업

[Lync Server 2013에서 통화 대기 번호 범위 만들기 또는 수정](lync-server-2013-create-or-modify-a-call-park-orbit-range.md)  

#### 기타 리소스

[Remove-CsCallParkOrbit](remove-cscallparkorbit.md)  
[Get-CsCallParkOrbit](get-cscallparkorbit.md)

