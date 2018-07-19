---
title: 그룹 호출 받기 번호 범위 삭제
TOCTitle: 그룹 호출 받기 번호 범위 삭제
ms:assetid: 521891f3-7a5d-45de-92dc-d57025453159
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/JJ945629(v=OCS.15)
ms:contentKeyID: 52056858
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# 그룹 호출 받기 번호 범위 삭제

 

_**마지막으로 수정된 항목:** 2013-01-30_

다음 절차에 따라 그룹 호출 받기 번호 범위를 삭제합니다.

## 호출 받기 그룹 번호 범위를 삭제하려면

1.  Lync Server 관리 셸이 설치된 컴퓨터에 RTCUniversalServerAdmins 그룹의 구성원으로 로그온하거나 [Lync Server 2013에서 설치 권한 위임](lync-server-2013-delegate-setup-permissions.md)에 설명된 대로 필요한 사용자 권한으로 로그온합니다.

2.  Lync Server 관리 셸 시작: **시작**, **모든 프로그램**, **Microsoft Lync Server 2013**을 차례로 클릭한 다음 **Lync Server 관리 셸**을 클릭합니다.

3.  명령줄에 다음을 입력합니다.
    
        Remove-CsCallParkOrbit -Identity "<group number range name>" 
    
    예를 들면 다음과 같습니다.
    
        Remove-CsCallParkOrbit -Identity "Redmond call pickup"
    

    > [!NOTE]
    > 추가 옵션에 대한 자세한 내용은 <A href="https://docs.microsoft.com/en-us/powershell/module/skype/Remove-CsCallParkOrbit">Remove-CsCallParkOrbit</A>을 참조하십시오.



## 참고 항목

#### 작업

[Lync Server 2013에서 통화 대기 번호 범위 만들기 또는 수정](lync-server-2013-create-or-modify-a-call-park-orbit-range.md)  

#### 기타 리소스

[Remove-CsCallParkOrbit](https://docs.microsoft.com/en-us/powershell/module/skype/Remove-CsCallParkOrbit)  
[Get-CsCallParkOrbit](https://docs.microsoft.com/en-us/powershell/module/skype/Get-CsCallParkOrbit)

