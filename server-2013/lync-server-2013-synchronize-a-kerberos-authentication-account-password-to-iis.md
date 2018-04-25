---
title: 'Lync Server 2013: IIS에 Kerberos 인증 계정 암호 동기화'
TOCTitle: IIS에 Kerberos 인증 계정 암호 동기화
ms:assetid: 05925a66-2684-4c1b-adfa-69bd0da1bf38
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg398107(v=OCS.15)
ms:contentKeyID: 49302682
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Lync Server 2013에서 IIS에 Kerberos 인증 계정 암호 동기화

 

_**마지막으로 수정된 항목:** 2010-11-08_

이 절차를 성공적으로 완료하려면 RTCUniversalServerAdmins 그룹의 구성원인 사용자로 로그온해야 합니다.

사이트에서 프런트 엔드 서버, Standard Edition 서버 및 디렉터는 웹 서비스 서비스에 대한 요청을 인증하기 위한 용도로 Kerberos 인증 계정을 사용할 수 있습니다. 이 절차에서는 Kerberos 계정이 할당된 사이트에서 웹 서비스를 실행하는 각 서버를 찾고, Kerberos 계정을 사용하도록 IIS(인터넷 정보 서비스) 구성 설정을 업데이트합니다. 자세한 내용은 [Lync Server 2013에서 서버에 대한 Kerberos 인증 계정 암호 설정](lync-server-2013-set-a-kerberos-authentication-account-password-on-a-server.md)을 참조하십시오.

## Kerberos 인증 계정 암호를 설정 및 구성하려면

1.  fe01.contoso.com 등의 원본 컴퓨터에 RTCUniversalServerAdmins 그룹의 구성원으로 로그온합니다.

2.  Lync Server 관리 셸 시작: **시작**, **모든 프로그램**, **Microsoft Lync Server 2013**을 차례로 클릭한 다음 **Lync Server 관리 셸**을 클릭합니다.

3.  Lync Server 관리 셸 명령줄에서 다음의 두 명령을 실행합니다.
    
        Set-CsKerberosAccountPassword -FromComputer SourceComputer -ToComputer DestinationComputer
    
    예를 들면 다음과 같습니다.
    
        Set-CsKerberosAccountPassword -FromComputer fe01.contoso.com -ToComputer dir01.contoso.com
    

    > [!IMPORTANT]
    > 원본 컴퓨터 및 대상 컴퓨터의 이름은 서버의 FQDN(정규화된 도메인 이름)이어야 합니다. 풀 이름이 원본 컴퓨터 또는 대상 컴퓨터로 사용하는 컴퓨터의 이름과 같지 않으면 풀 FQDN은 사용할 수 없습니다.

    

    > [!IMPORTANT]
    > 계정을 추가하거나 제거하는 등 Kerberos 인증을 변경한 후에는 Lync Server 관리 셸 명령 프롬프트에서 <STRONG>Enable-CsTopology</STRONG>를 실행해야 합니다.


