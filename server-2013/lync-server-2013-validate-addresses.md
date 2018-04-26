---
title: 주소 유효성 검사
TOCTitle: 주소 유효성 검사
ms:assetid: aae557c9-e6f5-4d23-8af1-1d4cd7968c54
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg412808(v=OCS.15)
ms:contentKeyID: 49304685
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# 주소 유효성 검사

 

_**마지막으로 수정된 항목:** 2012-09-17_

위치 데이터베이스를 게시하려면 SIP 트렁크 또는 PSTN(공중 전화망) E9-1-1 서비스 공급자에서 유지 관리된 MSAG(Master Street Address Guide)를 대상으로 새 위치를 확인해야 합니다.

SIP 트렁크 E9-1-1 서비스 공급자에 대한 자세한 내용은 [Lync Server 2013에 대한 E9-1-1 서비스 공급자 선택](lync-server-2013-choosing-an-e9-1-1-service-provider.md)을 참조하십시오.

주소를 확인하는 방법에 대한 자세한 내용은 다음 cmdlet에 대한 Lync Server 관리 셸 설명서를 참조하십시오.

  - **Get-CsLisServiceProvider**

  - **Set-CsLisServiceProvider**

  - **Remove-CsLisServiceProvider**

  - **Get-CsLisCivicAddress**

  - **Test-CsLisCivicAddress**

## 위치 데이터베이스에 있는 주소를 확인하려면

1.  Lync Server 관리 셸 시작: **시작**, **모든 프로그램**, **Microsoft Lync Server 2013**을 차례로 클릭한 다음 **Lync Server 관리 셸**을 클릭합니다.

2.  다음 cmdlet을 실행하여 응급 서비스 공급자 연결을 구성합니다.
    
        $pwd = Read-Host -AsSecureString <password>
        Set-CsLisServiceProvider -ServiceProviderName Provider1 -ValidationServiceUrl <URL provided by provider> -CertFileName <location of certificate provided by provider> -Password $pwd

3.  다음 cmdlet을 실행하여 위치 데이터베이스의 주소를 확인합니다.
    
        Get-CsLisCivicAddress | Test-CsLisCivicAddress -UpdateValidationStatus
    
    **Test-CsLisCivicAddress** cmdlet을 사용하여 개별 주소를 확인할 수도 있습니다.

