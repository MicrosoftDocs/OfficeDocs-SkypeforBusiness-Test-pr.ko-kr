---
title: Lync Server 2010 회의 디렉터리를 Lync Server 2013으로 이동
TOCTitle: 회의 디렉터리 이동
ms:assetid: 659867e0-ce91-4a95-9787-b1c1566460a8
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Dn727126(v=OCS.15)
ms:contentKeyID: 62388727
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# 회의 디렉터리 이동

 

_**마지막으로 수정된 항목:** 2014-05-28_

풀을 해제하기 전에 Lync Server 2010 풀에서 각 전화 회의 디렉터리에 대한 다음 절차를 수행해야 합니다.

## 전화 회의 디렉터리에서 Lync Server 2013으로 이동하려면

1.  Lync Server 관리 셸를 엽니다.

2.  조직에서 전화 회의 디렉터리의 ID를 가져오려면 다음 명령을 실행합니다.
    
        Get-CsConferenceDirectory
    
    위 명령은 조직의 모든 전화 회의 디렉터리를 반환합니다. 때로는 서비스 해제된 풀로 결과를 제한하고 싶을 수 있습니다. 예를 들어, FQDN(정규화된 도메인 이름)이 pool01.contoso.net인 풀을 서비스 해제하는 경우, 이 명령을 사용하여 반환된 데이터를 해당 풀의 전화 회의 디렉터리로 제한합니다.
    
        Get-CsConferenceDirectory | Where-Object {$_.ServiceID -match "pool01.contoso.net"}
    
    이 명령은 ServiceID 속성에 FQDN pool01.contoso.net이 포함된 전화 회의 디렉터리만 반환합니다.

3.  전화 회의 디렉터리를 이동하려면 풀에 있는 각 전화 회의 디렉터리에 대해 다음 명령을 실행합니다.
    
        Move-CsConferenceDirectory -Identity <Numeric identity of conference directory> -TargetPool <FQDN of pool where ownership is to be transitioned>
    
    예를 들어 전화 회의 디렉터리 3을 이동하려면 다음 명령을 사용하여 Lync Server 2013 풀을 TargetPool로 지정합니다.
    
        Move-CsConferenceDirectory -Identity 3 -TargetPool "pool02.contoso.net"
    
    풀의 모든 전화 회의 디렉터리를 이동하려면 다음과 비슷한 명령을 사용합니다.
    
        Get-CsConferenceDirectory | Where-Object {$_.ServiceID -match "pool01.contoso.net"} | Move-CsConferenceDirectory -TargetPool "pool02.contoso.net"

Lync 2010 풀 서비스 해제에 대한 포괄적인 단계별 지침은 "Microsoft Lync Server 2010 제거 및 서버 역할 제거" 문서([http://go.microsoft.com/fwlink/p/?linkId=246227](http://go.microsoft.com/fwlink/p/?linkid=246227)에서 다운로드)를 참고하세요.

전화 회의 디렉터리를 이동할 때 다음과 같은 오류가 발생할 수 있습니다.

    WARNING: Move operation failed for conference directory with ID "5". Cannot perform a rollback because data migration might have already started. Retry the operation.
    WARNING: Before using the -Force parameter, ensure that you have exported the conference directory data using DBImpExp.exe and imported the data on the target pool. Refer to the DBImpExp-Readme.htm file for more information.
    Move-CsConferenceDirectory : Unable to cast COM object of type 'System._ComObject' to interface type 'Microsoft.Rtc.Interop.User.IRtcConfDirManagement'. 
    This operation failed because the QueryInterface call on the COM component for the interface with SID '{4262B886-503F-4BEA-868C-04E8DF562CEB}' failed due to the following error: The specified module could not be found.

이 오류는 일반적으로 Lync Server 관리 셸에서 작업을 완료하기 위해 업데이트된 Active Directory 사용 권한 집합을 요구할 때 발생합니다. 이 문제를 해결하려면 관리 셸의 현재 인스턴스를 닫은 다음 셸의 새 인스턴스를 열고 전화 회의 디렉터리를 이동하기 위한 명령을 다시 실행합니다.

