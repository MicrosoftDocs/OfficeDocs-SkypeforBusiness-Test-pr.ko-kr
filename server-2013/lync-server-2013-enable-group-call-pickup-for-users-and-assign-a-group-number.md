---
title: 사용자에 대해 그룹 호출 받기를 사용하도록 설정하고 그룹 번호 할당
TOCTitle: 사용자에 대해 그룹 호출 받기를 사용하도록 설정하고 그룹 번호 할당
ms:assetid: c33bb6c2-d43b-4fb6-a0fa-6d82a7b09abe
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/JJ945650(v=OCS.15)
ms:contentKeyID: 52056954
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# 사용자에 대해 그룹 호출 받기를 사용하도록 설정하고 그룹 번호 할당

 

_**마지막으로 수정된 항목:** 2013-01-30_

호출 받기 그룹 번호를 통화 대기 번호 테이블에 추가한 후에는 사용자에게 해당 그룹 번호를 할당하고 사용자가 그룹 호출 받기를 사용하도록 설정합니다. 보조 확장 기능 활성화(SEFAUtil) 리소스 키트 도구를 사용하여 그룹 번호를 할당하고 그룹 호출 받기를 사용하도록 설정합니다.


> [!NOTE]
> 하이브리드 배포에서는 온라인상의 사용자에게 그룹 호출 받기 그룹을 할당하지 마십시오. 온라인상의 사용자는 그룹 호출 받기에 참가할 수 없습니다. 즉, 온라인 사용자의 전화를 다른 사람이 받을 수도 없고 온라인 사용자가 다른 사람에게 걸려온 전화를 받을 수도 없습니다.



## 사용자에 대해 그룹 번호를 할당하고 그룹 호출 받기를 사용하도록 설정하려면

1.  SEFAUtil 도구를 설치한 컴퓨터에 관리자 권한으로 로그온합니다.

2.  명령줄에서 다음을 실행합니다.
    
        SEFAUtil.exe sip:<sip address of user> /server:<pool FQDN> /enablegrouppickup:<group number>
    
    예를 들어 사용자에게 그룹 번호 199를 할당하려면 다음을 실행합니다.
    
        SEFAUtil.exe katarina@contoso.com /server:pool01.contoso.com /enablegrouppickup:199 

## 참고 항목

#### 작업

[사용자에 대해 그룹 호출 받기를 사용하지 않도록 설정](lync-server-2013-disable-group-call-pickup-for-users.md)

