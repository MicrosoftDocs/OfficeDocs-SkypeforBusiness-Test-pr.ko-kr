---
title: 'Lync Server 2013: 사이트에서 Kerberos 인증 제거'
TOCTitle: 사이트에서 Kerberos 인증 제거
ms:assetid: 93171b02-bb36-42dc-943d-86d9dde45b59
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg398749(v=OCS.15)
ms:contentKeyID: 49304406
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Lync Server 2013의 사이트에서 Kerberos 인증 제거

 

_**마지막으로 수정된 항목:** 2012-01-16_

이 절차를 성공적으로 완료하려면 RTCUniversalServerAdmins 그룹의 구성원인 사용자로 로그온해야 합니다.

사이트에서 Kerberos 인증을 제거하거나 사이트를 폐기해야 하는 경우 **Remove-CsKerberosAccountAssignment** cmdlet을 사용하여 사이트에서 Kerberos 인증 계정 할당을 제거해야 합니다. 다음 절차를 사용하여 Kerberos 인증 계정 할당을 제거하면 사이트의 모든 컴퓨터에서 할당이 제거됩니다.


> [!WARNING]  
> Kerberos 사용 계정을 영구적으로 폐기하려는 경우 할당을 제거한 후 Active Directory 사용자 및 컴퓨터를 사용하여 Active Directory 도메인 서비스에서 해당 계정을 삭제해야 합니다. 나중에 개체를 사용하려는 경우 Active Directory 개체를 유지하고자 할 수 있습니다.



## 사이트에서 Kerberos 인증을 제거하려면

1.  RTCUniversalServerAdmins 그룹의 구성원으로 Lync Server 2013을 실행하는 도메인의 컴퓨터 또는 관리 도구가 설치된 컴퓨터에 로그온합니다.

2.  Lync Server 관리 셸 시작: **시작**, **모든 프로그램**, **Microsoft Lync Server 2013**을 차례로 클릭한 다음 **Lync Server 관리 셸**을 클릭합니다.

3.  명령줄에서 다음의 두 명령을 실행합니다.
    
```
        Remove-CsKerberosAccountAssignment -Identity "site:SiteName"
```
```    
        Enable-CsTopology
```    
예를 들면 다음과 같습니다.
    
```
        Remove-CsKerberosAccountAssignment -Identity "site:Redmond"
```
```    
        Enable-CsTopology
```    

 > [!IMPORTANT]  
> 계정을 추가하거나 제거하는 등 Kerberos 인증을 변경한 후에는 Lync Server 관리 셸 명령 프롬프트에서 <STRONG>Enable-CsTopology</STRONG>를 실행해야 합니다.


