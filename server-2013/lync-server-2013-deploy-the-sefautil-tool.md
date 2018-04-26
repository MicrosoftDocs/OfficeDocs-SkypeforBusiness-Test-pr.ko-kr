---
title: SEFAUtil 도구 배포
TOCTitle: SEFAUtil 도구 배포
ms:assetid: fb556e50-88dd-4404-a3d5-be36f5ba41e6
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/JJ945659(v=OCS.15)
ms:contentKeyID: 52057004
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# SEFAUtil 도구 배포

 

_**마지막으로 수정된 항목:** 2013-01-30_

그룹 호출 받기를 배포 및 관리하려면 SEFAUtil 리소스 키트 도구를 사용해야 합니다. 이 도구는 Lync Server 2013 리소스 키트 도구의 일부분입니다. SEFAUtil을 설치하려면 토폴로지에 신뢰할 수 있는 응용 프로그램 풀을 포함하고, SEFAUtil을 신뢰할 수 있는 응용 프로그램으로 지정하고 토폴로지를 사용하도록 설정해야 합니다.


> [!IMPORTANT]
> SEFAUtil 도구를 실행하려는 모든 컴퓨터에 Microsoft Unified Communications Managed API(UCMA) 3.0 Core SDK를 설치해야 합니다.



배포의 모든 프런트 엔드 풀에서 SEFAUtil을 실행할 수 있습니다.


> [!NOTE]
> SEFAUtil을 실행하는 방법에 대한 자세한 내용은 TechNet 블로그 문서 "SEFAUtil을 실행하는 방법"(<A class=uri href="http://go.microsoft.com/fwlink/?linkid=278940">http://go.microsoft.com/fwlink/?linkid=278940</A>)을 참조하십시오.



## SEFAUtil을 배포하려면

1.  Lync Server 관리 셸이 설치된 컴퓨터에 RTCUniversalServerAdmins 그룹의 구성원으로 로그온하거나 [Lync Server 2013에서 설치 권한 위임](lync-server-2013-delegate-setup-permissions.md)에 설명된 대로 필요한 사용자 권한으로 로그온합니다.

2.  Lync Server 관리 셸 시작: **시작**, **모든 프로그램**, **Microsoft Lync Server 2013**을 차례로 클릭한 다음 **Lync Server 관리 셸**을 클릭합니다.

3.  SEFAUtil 도구는 신뢰할 수 있는 응용 프로그램 풀의 일부분인 컴퓨터에서만 실행할 수 있습니다. 필요한 경우 SEFAUtil을 실행하려는 프런트 엔드 풀에 대해 신뢰할 수 있는 응용 프로그램 풀을 정의합니다. 명령줄에서 다음을 실행합니다.
    
        New-CsTrustedApplicationPool -id <Pool FQDN> -Registrar <Pool Registrar FQDN> -site Site:<Pool Site>

4.  SEFAUtil 도구를 신뢰할 수 있는 응용 프로그램으로 정의합니다. 명령줄에서 다음을 실행합니다.
    
        New-CsTrustedApplication -ApplicationId sefautil -TrustedApplicationPoolFqdn <Pool FQDN>  -Port 7489
    

    > [!NOTE]
    > 필요한 경우 다른 포트를 사용할 수 있습니다.



5.  변경 내용을 적용하여 토폴로지를 사용하도록 설정합니다. 명령줄에서 다음을 실행합니다.
    
        Enable-CsTopology

6.  3단계에서 만든 신뢰할 수 있는 응용 프로그램 풀에 포함된 프런트 엔드 서버에서 Lync Server 2013 리소스 키트 도구를 설치합니다.

7.  다음과 같이 SEFAUtil 도구가 정상적으로 실행되고 있는지 확인합니다.
    
    1.  관리자 권한으로 Windows 명령 프롬프트에서 도구를 실행하여 배포에 포함된 사용자의 착신 전환 설정을 표시합니다.
        

        > [!NOTE]
        > 이 도구는 \Program Files\Microsoft Lync Server 2013\Reskit에 있습니다.

    
    2.  사용자의 착신 전환 설정을 표시합니다. 명령줄에서 다음을 실행합니다.
        
            SEFAUtil.exe <user SIP address> /server:<Lync Server/Pool FQDN>
        
        사용자의 착신 전환 설정이 표시됩니다.

