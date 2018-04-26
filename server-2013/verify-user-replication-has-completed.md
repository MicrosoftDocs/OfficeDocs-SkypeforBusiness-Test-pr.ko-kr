---
title: 사용자 복제가 완료되었는지 확인
TOCTitle: 사용자 복제가 완료되었는지 확인
ms:assetid: 119e9896-45e5-4f8b-af43-7b09360ada0b
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/JJ204680(v=OCS.15)
ms:contentKeyID: 49302848
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# 사용자 복제가 완료되었는지 확인

 

_**마지막으로 수정된 항목:** 2012-09-17_

**Move-CsUser** cmdlet을 실행할 때 초기 복제가 완료되지 않아서 AD DS(Active Directory 도메인 서비스) 및 Lync Server 2013 데이터베이스 간에 사용자 정보가 동기화되지 않아 오류가 발생할 수 있습니다. Lync Server 2013 User Replicator 서비스의 초기 동기화를 성공적으로 완료하기 위해 걸리는 시간은 Lync Server 2013 풀을 호스트하는 Active Directory 포리스트에서 호스트되는 도메인 컨트롤러 수에 따라 달라집니다. Lync Server 2013 User Replicator 서비스의 초기 동기화 프로세스는 Lync Server 2013 프런트 엔드 서버를 처음 시작할 때 수행됩니다. 그 후에는 동기화가 User Replicator 간격을 기준으로 수행됩니다. 다음 단계를 완료하여 **Move-CsUser** cmdlet을 실행하기 전에 사용자 복제가 완료되었는지 확인합니다.

## 사용자 복제가 완료되었는지 확인하려면

1.  토폴로지 작성기가 Domain Admins 그룹 및 RTCUniversalServerAdmins 그룹의 구성원으로 설치되어 있는 컴퓨터에 로그온합니다.

2.  **시작** 메뉴를 클릭한 후 **실행** 을 클릭합니다.

3.  **eventvwr.exe** 를 입력한 후 **확인** 을 클릭합니다.

4.  이벤트 뷰어에서 **응용 프로그램 및 서비스 로그** 를 클릭해서 확장한 후 Lync Server를 선택합니다.

5.  **동작** 창에서 **현재 로그 필터링** 을 클릭합니다.

6.  **이벤트 원본** 목록에서 **LS User Replicator** 를 클릭합니다.

7.  **\<모든 이벤트 ID\>** 에 **30024** 를 입력한 후 **확인** 을 클릭합니다.

8.  필터링된 이벤트 목록의 **일반** 탭에서 사용자 복제가 성공적으로 완료되었음을 나타내는 항목을 찾습니다.

