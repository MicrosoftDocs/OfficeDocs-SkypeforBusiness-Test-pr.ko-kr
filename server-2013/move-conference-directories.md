---
title: 회의 디렉터리 이동
TOCTitle: 회의 디렉터리 이동
ms:assetid: 71a28308-1f3b-4717-b535-2f4bfe3499a1
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/JJ204994(v=OCS.15)
ms:contentKeyID: 49304013
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# 회의 디렉터리 이동

 

_**마지막으로 수정된 항목:** 2012-10-04_

풀을 해제하기 전에 Office Communications Server 2007 R2 풀에서 각 회의 디렉터리에 대한 다음 절차를 수행해야 합니다.

## 회의 디렉터리를 Lync Server 2013으로 이동하려면

1.  Lync Server 관리 셸를 엽니다.

2.  조직에서 회의 디렉터리의 ID를 가져오려면 다음 명령을 실행합니다.
    
        Get-CsConferenceDirectory
    
    이 cmdlet은 조직에 있는 모든 회의 디렉터리를 반환하므로 해제하려는 풀로만 결과를 제한해야 할 수 있습니다. 예를 들어 FQDN(정규화된 도메인 이름)이 pool01.contoso.net인 풀을 해제하려는 경우 다음을 수행합니다.
    
        Get-CsConferenceDirectory | Where-Object {$_.ServiceID -match "pool01.contoso.net"}
    
    이 cmdlet은 서비스 ID에 FQDN pool01.contoso.net이 포함된 모든 회의 디렉터리를 반환합니다.

3.  회의 디렉터리를 이동하려면 풀의 각 회의 디렉터리에 대해 다음을 실행합니다.
    
        Move-CsConferenceDirectory -Identity <Numeric identity of conference directory> -TargetPool <FQDN of pool where ownership is to be transitioned>
    
    예를 들면 다음과 같습니다.
    
        Move-CsConferenceDirectory -Identity 3 -TargetPool pool02.contoso.net


> [!NOTE]
> 아래 표시된 것처럼 Active Directory에서 업데이트된 권한 집합을 요구하는 Lync Server 관리 셸로 인해 오류가 발생할 수 있습니다. 오류를 해결하려면 현재 창을 닫고 새 Lync Server 관리 셸을 열고 명령을 다시 실행합니다.



![Move-CsConferenceDirectory 오류 출력](images/JJ204994.4748b9e8-9651-4527-afe1-cbdc6d5ce4a8(OCS.15).jpg "Move-CsConferenceDirectory 오류 출력")

