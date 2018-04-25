---
title: 'Lync Server 2013: Kerberos 계정 할당 보고'
TOCTitle: Kerberos 계정 할당 보고
ms:assetid: 523231f6-81b3-454b-996d-663d9bd5cf83
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg398343(v=OCS.15)
ms:contentKeyID: 49303636
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Lync Server 2013에서 Kerberos 계정 할당 보고

 

_**마지막으로 수정된 항목:** 2012-01-16_

이 절차를 성공적으로 완료하려면 RTCUniversalServerAdmins 그룹의 구성원인 사용자로 로그온해야 합니다.

**Get-CsKerberosAccountAssignment** cmdlet을 사용하여 Kerberos 인증 계정 지정에 대한 정보를 쿼리하고 배포의 현재 지정에 대한 정보를 보고할 수 있습니다.

## 사이트에 대한 Kerberos 인증 계정 지정을 쿼리하려면

1.  RTCUniversalServerAdmins 그룹의 구성원으로 Lync Server 2013을 실행하는 도메인의 컴퓨터 또는 관리 도구가 설치된 컴퓨터에 로그온합니다.

2.  Lync Server 관리 셸 시작: **시작**, **모든 프로그램**, **Microsoft Lync Server 2013**을 차례로 클릭한 다음 **Lync Server 관리 셸**을 클릭합니다.

3.  명령줄에서 다음 명령 중 하나를 실행합니다.
    
      - 조직의 모든 Kerberos 인증 계정 지정을 쿼리하고 각 계정에 대한 지정 정보를 반환하려면 매개 변수 없이 cmdlet을 실행합니다.
        
            Get-CsKerberosAccountAssignment
    
      - 배포의 모든 Kerberos 인증 계정 지정을 쿼리하고 각 계정에 대한 사이트 지정 정보를 반환하려면 ID 매개 변수를 사용하여 cmdlet을 실행합니다.
        
            Get-CsKerberosAccountAssignment -Identity "site:SiteName"
        
        예를 들면 다음과 같습니다.
        
            Get-CsKerberosAccountAssignment -Identity "site:Redmond"
    
      - 단일 사이트의 모든 Kerberos 인증 계정 지정을 쿼리하고 각 계정에 대한 지정 정보를 반환하려면 필터 매개 변수를 사용하여 cmdlet을 실행합니다.
        
            Get-CsKerberosAccountAssignment -Filter "SiteName"
        
        예를 들면 다음과 같습니다.
        
            Get-CsKerberosAccountAssignment -Filter "*Redmond"
        

        > [!NOTE]
        > 필터 매개 변수에 대해 *SiteName을 지정하면 사이트 식별자에서 임의의 위치에 지정한 사이트 이름이 포함된 모든 사이트(예: 사이트 식별자에 Redmond 문자열이 포함된 모든 사이트)에 대한 정보가 반환됩니다.


