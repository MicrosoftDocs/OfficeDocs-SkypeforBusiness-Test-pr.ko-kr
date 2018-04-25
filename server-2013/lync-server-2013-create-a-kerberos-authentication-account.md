---
title: 'Lync Server 2013: Kerberos 인증 계정 만들기'
TOCTitle: Kerberos 인증 계정 만들기
ms:assetid: 63f0cef6-562a-4209-ae25-71f8dc7c7295
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg398449(v=OCS.15)
ms:contentKeyID: 49303843
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Lync Server 2013에서 Kerberos 인증 계정 만들기

 

_**마지막으로 수정된 항목:** 2012-01-02_

이 절차를 성공적으로 완료하려면 최소한 Domain Admins 그룹 구성원으로 서버나 도메인에 로그온해야 합니다.

각 사이트에 대해 Kerberos 인증 계정을 만들 수도 있고, 단일 Kerberos 인증 계정을 만들어 모든 사이트에 사용할 수도 있습니다. Windows PowerShell cmdlet을 사용하여 계정을 만들고 관리합니다(각 사이트에 지정되는 계정 식별 작업 포함). 토폴로지 작성기 및 Lync Server 2013 제어판에는 Kerberos 인증 계정이 표시되지 않습니다. 다음 절차에 따라 Kerberos 인증에 사용할 하나 이상의 사용자 계정을 만듭니다.

## Kerberos 계정을 만들려면

1.  Domain Admins 그룹 구성원으로 관리 도구가 설치된 컴퓨터 또는 Lync Server 2013을 실행하는 도메인의 컴퓨터에 로그온합니다.

2.  Lync Server 관리 셸 시작: **시작**, **모든 프로그램**, **Microsoft Lync Server 2013**을 차례로 클릭한 다음 **Lync Server 관리 셸**을 클릭합니다.

3.  명령줄에서 다음 명령을 실행합니다.
    
        New-CsKerberosAccount -UserAccount "Domain\UserAccount" -ContainerDN "CN=Users,DC=DomainName,DC=DomainExtension"
    
    예를 들면 다음과 같습니다.
    
        New-CsKerberosAccount -UserAccount "Contoso\KerbAuth" -ContainerDN "CN=Users,DC=contoso,DC=com"

4.  컴퓨터 개체가 만들어졌는지 확인합니다. 이렇게 하려면 Active Directory 사용자 및 컴퓨터를 열고 **사용자** 컨테이너를 확장한 다음 사용자 계정의 컴퓨터 개체가 컨테이너에 있는지 확인합니다.

