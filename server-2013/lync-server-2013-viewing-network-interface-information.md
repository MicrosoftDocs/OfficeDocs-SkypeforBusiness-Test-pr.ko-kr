---
title: 네트워크 인터페이스 정보 보기
TOCTitle: 네트워크 인터페이스 정보 보기
ms:assetid: e7dbb1ec-62b3-48be-a419-c493df5740e6
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/JJ721916(v=OCS.15)
ms:contentKeyID: 49886029
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# 네트워크 인터페이스 정보 보기

 

_**마지막으로 수정된 항목:** 2013-02-23_

## Lync Server 관리 셸 Cmdlet을 사용하여 네트워크 인터페이스 정보 보기

Lync Server 관리 셸과 **Get-CsNetworkInterface** cmdlet을 사용하여 네트워크 인터페이스 정보를 볼 수 있습니다. 이 cmdlet을 Windows PowerShell의 원격 세션이나 Lync Server 2013 관리 셸에서 실행할 수 있습니다. 원격 Windows PowerShell을 사용하여 Lync Server에 연결하는 방법에 대한 자세한 내용은 Lync Server Windows PowerShell 블로그 문서인 "빠른 시작: 원격 PowerShell을 사용하여 Microsoft Lync Server 2010 관리"([http://go.microsoft.com/fwlink/p/?linkId=255876](http://go.microsoft.com/fwlink/p/?linkid=255876))를 참조하세요.

## 네트워크 인터페이스 정보를 보려면

  - 네트워크 인터페이스 정보를 보려면 Lync Server 관리 셸에서 다음 명령을 입력하고 Enter 키를 누릅니다.
    
        Get-CsNetworkInterface
    
    이 명령은 각 네트워크 인터페이스에 대해 다음과 같은 정보를 반환합니다.
    
        Identity              : dc.vdomain.com/Primary/1
        ComputerFqdn          : dc.vdomain.com
        IPAddress             : 0.0.0.0
        IPv6Address           :
        Interface             : Primary
        InterfaceNumber       : 1
        ConfiguredFqdn        :
        ConfiguredIPAddress   :
        ConfiguredIPv6Address :

자세한 내용은 [Get-CsNetworkInterface](get-csnetworkinterface.md)를 참조하십시오.

