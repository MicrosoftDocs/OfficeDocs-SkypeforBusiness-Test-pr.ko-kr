---
title: 'Lync Server 2013: 서버에 대한 Kerberos 인증 계정 암호 설정'
TOCTitle: 서버에 대한 Kerberos 인증 계정 암호 설정
ms:assetid: 902d3292-678d-4512-9248-586053cb638b
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg398734(v=OCS.15)
ms:contentKeyID: 49304369
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Lync Server 2013에서 서버에 대한 Kerberos 인증 계정 암호 설정

 

_**마지막으로 수정된 항목:** 2012-01-16_

이 절차를 성공적으로 완료하려면 RTCUniversalServerAdmins 그룹의 구성원인 사용자로 로그온해야 합니다.

프런트 엔드 서버, Standard Edition Server 및 디렉터가 있는 각 사이트의 Kerberos 계정에 대한 암호를 설정해야 합니다. 사이트의 한 서버(예: 한 프런트 엔드 서버)에 대해 **Set-CsKerberosAccountPassword**  Windows PowerShell cmdlet을 실행하여 암호를 설정할 수 있습니다. 각 사이트에 대해 **Set-CsKerberosAccountPassword** cmdlet을 실행해야 합니다. 이 cmdlet은 웹 서비스 서비스에 대해 IIS(인터넷 정보 서비스)를 구성한 다음 Active Directory 도메인 서비스의 컴퓨터 계정에 대한 암호를 설정합니다. cmdlet에 사용되는 매개 변수를 기반으로 한 다른 방법에서는 Kerbero 계정 암호의 소스로 구성된 다른 서버를 사용하면서 한 서버에 대해 IIS를 구성합니다.

**Set-CsKerberosAccountPassword** cmdlet을 사용하여 암호를 설정할 때 Kerberos는 암호를 임의로 생성된 문자열로 설정합니다. 이 cmdlet은 이 계정이 할당된 모든 Lync Server 2013 중앙 사이트에서 모든 IIS 인스턴스에 연결합니다.

## Kerberos 인증 계정에 대한 암호를 설정하려면

1.  Lync Server 관리 셸이 RTCUniversalServerAdmins 그룹의 구성원으로 설치된 도메인 컴퓨터에 로그온합니다.

2.  Lync Server 관리 셸 시작: **시작**, **모든 프로그램**, **Microsoft Lync Server 2013**을 차례로 클릭한 다음 **Lync Server 관리 셸**을 클릭합니다.

3.  명령줄에서 다음의 두 명령을 실행합니다.
    
        Set-CsKerberosAccountPassword -UserAccount "Domain\UserAccount"
    
    예를 들면 다음과 같습니다.
    
        Set-CsKerberosAccountPassword -UserAccount "contoso\KerbAuth"
    

    > [!NOTE]
    > 도메인\사용자 형식을 사용하여 UserAccount 매개 변수를 지정해야 합니다. Kerberos 인증 목적으로 만들어진 컴퓨터 개체를 참조할 때 User@Domain.extension 형식은 지원되지 않습니다.

    

    > [!IMPORTANT]
    > 계정을 추가하거나 제거하는 등 Kerberos 인증을 변경한 후에는 Lync Server 관리 셸 명령 프롬프트에서 <STRONG>Enable-CsTopology</STRONG>를 실행해야 합니다.


