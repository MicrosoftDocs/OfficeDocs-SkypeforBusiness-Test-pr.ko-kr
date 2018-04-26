---
title: 사용자에 대해 그룹 호출 받기를 사용하도록 설정
TOCTitle: 사용자에 대해 그룹 호출 받기를 사용하도록 설정
ms:assetid: 20ec5f41-6ba2-4156-82ed-b91d05b62a6d
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/JJ945620(v=OCS.15)
ms:contentKeyID: 52056802
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# 사용자에 대해 그룹 호출 받기를 사용하도록 설정

 

_**마지막으로 수정된 항목:** 2013-01-30_

SEFAUtil 리소스 키트 도구를 통해 사용자에 대한 그룹 호출 받기를 사용하도록 설정합니다. 그룹 호출 받기를 사용하도록 설정하려면 통화 대기 번호 테이블에서 유형이 GroupPickup인 그룹 번호를 사용자에게 지정해야 합니다. SEFAUtil.exe를 실행할 때 /enablegrouppickup 매개 변수를 사용하여 호출 받기 그룹 번호를 지정하는 동시에 그룹 호출 받기를 사용하도록 설정합니다.

## 사용자에 대해 그룹 호출 받기를 사용하도록 설정하려면

1.  SEFAUtil 도구를 설치한 컴퓨터에 관리자 권한으로 로그온합니다.

2.  명령줄에서 다음을 실행합니다.
    
        SEFAUtil.exe sip:<sip address of user> /server:<pool FQDN> /enablegrouppickup:<group number>
    
    예를 들면 다음과 같습니다.
    
        SEFAUtil.exe katarina@contoso.com /server:pool01.contoso.com /enablegrouppickup:199

## 참고 항목

#### 작업

[사용자에게 그룹 호출 받기 번호 할당](lync-server-2013-assign-group-call-pickup-numbers-to-users.md)  
[사용자에 대해 그룹 호출 받기를 사용하지 않도록 설정](lync-server-2013-disable-group-call-pickup-for-users.md)

