---
title: 알림 삭제
TOCTitle: 알림 삭제
ms:assetid: 26ea7149-4470-4c22-9bab-8a4065aca44e
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/JJ687998(v=OCS.15)
ms:contentKeyID: 49885689
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# 알림 삭제

 

_**마지막으로 수정된 항목:** 2012-11-01_

다음 절차에 따라 지정되지 않은 번호에 대한 통화에 사용되는 알림을 삭제합니다.

## 알림을 삭제하려면

1.  Lync Server 관리 셸이 설치된 컴퓨터에 RTCUniversalServerAdmins 그룹의 구성원으로 로그온하거나 [Lync Server 2013에서 설치 권한 위임](lync-server-2013-delegate-setup-permissions.md)에 설명된 대로 필요한 사용자 권한으로 로그온합니다.

2.  Lync Server 관리 셸 시작: **시작**, **모든 프로그램**, **Microsoft Lync Server 2013**을 차례로 클릭한 다음 **Lync Server 관리 셸**을 클릭합니다.

3.  조직의 모든 알림을 나열합니다. 명령줄에서 다음을 실행합니다.
    
        Get-CsAnnouncement

4.  그러면 표시되는 목록에서 삭제할 알림을 찾아 GUID를 복사합니다. 그런 후에 명령줄에서 다음을 실행합니다.
    
        Remove-CsAnnouncement -Identity "<Service:service ID/guid>" 
    
    예를 들면 다음과 같습니다.
    
        Remove-CsAnnouncement -Identity "ApplicationServer:Redmond.contoso.com/1951f734-c80f-4fb2-965d-51807c792b90"
    

    > [!NOTE]
    > 추가 옵션에 대한 자세한 내용은 <A href="https://docs.microsoft.com/en-us/powershell/module/skype/Get-CsAnnouncement">Get-CsAnnouncement</A> 및 <A href="https://docs.microsoft.com/en-us/powershell/module/skype/Remove-CsAnnouncement">Remove-CsAnnouncement</A>를 참조하십시오.



## 참고 항목

#### 작업

[Lync Server 2013에서 알림 만들기](lync-server-2013-create-an-announcement.md)  

#### 기타 리소스

[Remove-CsAnnouncement](https://docs.microsoft.com/en-us/powershell/module/skype/Remove-CsAnnouncement)  
[Get-CsAnnouncement](https://docs.microsoft.com/en-us/powershell/module/skype/Get-CsAnnouncement)

