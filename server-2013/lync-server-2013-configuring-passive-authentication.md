---
title: Lync Server 수동 인증 구성
TOCTitle: Lync Server 수동 인증 구성
ms:assetid: 9a904b8d-9fce-4abf-be73-5c8e48cfb53a
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Dn308569(v=OCS.15)
ms:contentKeyID: 56270282
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Lync Server 수동 인증 구성

 

_**마지막으로 수정된 항목:** 2013-07-11_

다음 섹션에서는 수동 인증을 지원하는 누적 업데이트(2013년 7월)가 적용된 Lync Server 2013을 구성하는 방법을 설명합니다. 설정된 경우, 2단계 인증을 사용할 수 있는 Lync 사용자는 누적 업데이트( 2013년 7월) 클라이언트가 적용된 Lync 2013을 사용할 때 실제 또는 가상 스마트 카드와 유효한 PIN을 사용하여 로그인해야 합니다.


> [!NOTE]
> 고객은 서비스 수준에서 등록자 및 웹 서비스에 대해 수동 인증을 사용하도록 설정하는 것이 좋습니다. 전역 수준에서 등록자 및 웹 서비스에 대해 수동 인증을 사용하도록 설정하면 누적 업데이트(2013년 7월)가 적용된 데스크톱 클라이언트로 로그인하지 않는 사용자의 경우 조직 전체에서 인증 오류가 발생할 수 있습니다.



## 웹 서비스 구성

다음 단계에서는 수동 인증에 사용할 수 있도록 설정된 디렉터, 엔터프라이즈 풀 및 Standard Edition 서버에 대해 사용자 지정 웹 서비스 구성을 만드는 방법을 설명합니다.

**사용자 지정 웹 서비스 구성을 만들려면**

1.  Lync 관리자 계정을 사용하여 누적 업데이트(2013년 7월)가 적용된 Lync Server 2013 프런트 엔드 서버에 로그인합니다.

2.  Lync Server 2013 관리 셸을 시작합니다.

3.  Lync Server 관리 셸 명령줄에서 다음 명령을 실행하여 수동 인증에 사용하도록 설정된 각 디렉터, 엔터프라이즈 풀 및 Standard Edition 서버에 대해 새 웹 서비스 구성을 만듭니다.
    
        New-CsWebServiceConfiguration -Identity "Service:WebServer:LyncPool01.contoso.com" -UseWsFedPassiveAuth $true -WsFedPassiveMetadataUri https://dc.contoso.com/federationmetadata/2007-06/federationmetadata.xml
    

    > [!WARNING]
    > WsFedPassiveMetadataUri FQDN의 값은 AD FS 2.0 서버의 페더레이션 서비스 이름입니다. 페더레이션 서비스 이름 값은 AD FS 2.0 관리 콘솔의 탐색 창에서 <STRONG>서비스</STRONG>를 마우스 오른쪽 단추로 클릭한 후 <STRONG>페더레이션 서비스 속성 편집</STRONG>을 선택하여 찾을 수 있습니다.



4.  다음 명령을 실행하여 UseWsFedPassiveAuth 및 WsFedPassiveMetadataUri 값이 올바로 설정되었는지 확인합니다.
    
        Get-CsWebServiceConfiguration -identity "Service:WebServer:LyncPool01.contoso.com" | format-list UseWsFedPassiveAuth, WsFedPassiveMetadataUri

5.  클라이언트의 경우 수동 인증은 웹 티켓 인증에 가장 선호되지 않는 인증 방법입니다. 수동 인증을 사용하도록 설정된 모든 디렉터, 엔터프라이즈 풀 및 Standard Edition 서버의 경우 다음 명령을 사용하여 Lync 웹 서비스에서 다른 모든 인증 유형을 사용하지 않도록 설정해야 합니다.
    
        Set-CsWebServiceConfiguration -Identity "Service:WebServer:LyncPool01.contoso.com" -UseCertificateAuth $false -UsePinAuth $false -UseWindowsAuth NONE

6.  다음 명령을 실행하여 다른 모든 인증 유형을 사용하지 않도록 설정했는지 확인합니다.
    
        Get-CsWebServiceConfiguration -Identity "Service:WebServer:LyncPool01.contoso.com" | format-list UseCertificateAuth, UsePinAuth, UseWindowsAuth

## 프록시 구성

Lync 웹 서비스에 대해 인증서 인증을 사용하지 않도록 설정한 경우 Lync 클라이언트가 Kerberos 또는 NTLM처럼 선호도가 낮은 인증 유형을 사용하여 등록자 서비스로 인증합니다. Lync 클라이언트가 웹 티켓을 검색할 수 있도록 허용하려면 여전히 인증서 인증이 필요하지만, 등록자 서비스에 대해 Kerberos 및 NTLM을 사용하지 않도록 설정해야 합니다.

다음 단계에서는 수동 인증을 사용하도록 설정된 에지 풀, 엔터프라이즈 풀 및 Standard Edition 서버에 대해 사용자 지정 프록시 구성을 만드는 방법에 대해 설명합니다.

**사용자 지정 프록시 구성을 만들려면**

1.  Lync Server 관리 셸 명령줄에서 다음 명령을 사용하여 수동 인증을 사용할 수 있는 누적 업데이트(2013년 7월)가 적용된 각 Lync Server 2013 에지 풀, 엔터프라이즈 풀 및 Standard Edition 서버에 대해 새 프록시 구성을 만듭니다.
    
```
        New-CsProxyConfiguration -Identity "Service:EdgeServer:EdgePool01.contoso.com" 
        -UseKerberosForClientToProxyAuth $False -UseNtlmForClientToProxyAuth $False
```
```    
        New-CsProxyConfiguration -Identity "Service:Registrar:LyncPool01.contoso.com" 
        -UseKerberosForClientToProxyAuth $False -UseNtlmForClientToProxyAuth $False
```

2.  다음 명령을 실행하여 기타 모든 프록시 인증 유형을 사용하지 않도록 설정했는지 확인합니다.
    
        Get-CsProxyConfiguration -Identity "Service:Registrar:LyncPool01.contoso.com"
         | format-list UseKerberosForClientToProxyAuth, UseNtlmForClientToProxyAuth, UseCertifcateForClientToProxyAuth

