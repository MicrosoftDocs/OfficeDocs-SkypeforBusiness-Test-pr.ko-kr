---
title: 사용자에 대해 그룹 호출 받기를 사용하지 않도록 설정
TOCTitle: 사용자에 대해 그룹 호출 받기를 사용하지 않도록 설정
ms:assetid: 91b06f9e-2840-45a2-bbb3-6a29179b9a9f
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/JJ945638(v=OCS.15)
ms:contentKeyID: 52056893
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# 사용자에 대해 그룹 호출 받기를 사용하지 않도록 설정

 

_**마지막으로 수정된 항목:** 2013-01-30_

다음 절차에 따라 사용자에 대해 그룹 호출 받기를 사용하지 않도록 설정합니다.


> [!NOTE]
> 사용자에 대해 그룹 호출 받기를 사용하지 않도록 설정하면 해당 사용자에게 할당된 호출 받기 그룹 번호가 보존되지 않습니다. 나중에 해당 사용자에 대해 그룹 호출 받기를 다시 사용하도록 설정하려면 /enablegrouppickup 매개 변수를 사용하여 호출 받기 그룹 번호를 다시 할당해야 합니다.



## 사용자에 대해 그룹 호출 받기를 사용하지 않도록 설정하려면

1.  SEFAUtil 도구를 설치한 컴퓨터에 관리자 권한으로 로그온합니다.

2.  명령줄에서 다음을 실행합니다.
    
        SEFAUtil.exe sip:<sip address of user> /server:<pool FQDN> /disablegrouppickup
    
    예를 들면 다음과 같습니다.
    
        SEFAUtil.exe katarina@contoso.com /server:pool01.contoso.com /disablegrouppickup

## 참고 항목

#### 작업

[사용자에게 그룹 호출 받기 번호 할당](lync-server-2013-assign-group-call-pickup-numbers-to-users.md)  
[사용자에 대해 그룹 호출 받기를 사용하도록 설정](lync-server-2013-enable-group-call-pickup-for-users.md)

