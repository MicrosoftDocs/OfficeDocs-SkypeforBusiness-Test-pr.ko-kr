---
title: 'Lync Server 2013: 네트워크 사이트에 서브넷 연결'
TOCTitle: 네트워크 사이트에 서브넷 연결
ms:assetid: aa69e3ac-542a-4ba1-9582-2e6bee29f633
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg412804(v=OCS.15)
ms:contentKeyID: 49304671
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Lync Server 2013 에서 네트워크 사이트에 서브넷 연결

 

_**마지막으로 수정된 항목:** 2014-10-20_

네트워크의 모든 서브넷은 특정 네트워크 사이트에 연결되어야 합니다. 새 세션이 시작되는 동안 끝점이 있는 네트워크 사이트를 확인하는 데 서브넷 정보가 사용되기 때문입니다. 세션에서 각 당사자의 위치가 알려진 경우 고급 Enterprise Voice 기능은 해당 정보를 적용하여 통화 설정이나 라우팅을 처리하는 방법을 결정할 수 있습니다.


> [!IMPORTANT]
> 배포의 오디오/비디오 에지 서버에 대해 구성된 모든 공용 IP 주소를 네트워크 구성 설정에 추가해야 합니다. 이러한 IP 주소는 마스크가 32인 서브넷으로 추가되며, 연결된 네트워크 사이트는 구성된 해당 네트워크 사이트와 일치해야 합니다. 예를 들어 중앙 사이트 시카고의 A/V 에지 서버에 해당하는 공용 IP 주소는 NetworkSiteID Chicago가 됩니다. 공용 IP 주소에 대한 자세한 내용은 계획 설명서에서 <A href="lync-server-2013-determine-external-a-v-firewall-and-port-requirements.md">Lync Server 2013에 대한 외부 A/V 방화벽 및 포트 요구 사항 확인</A>을 참조하십시오.




> [!NOTE]
> 네트워크에 있지만 서브넷과 연결되지 않은 IP 주소 목록 또는 IP 주소가 포함되어 있지만 네트워크 사이트에 연결되지 않은 서브넷 목록을 지정하는 KHI(Key Health Indicator) 알림이 표시됩니다. 이 알림은 8시간 간격으로 한 번만 발생합니다(해당되는 경우). 관련 알림 정보 및 예는 다음과 같습니다.<BR><STRONG>원본 :</STRONG> CS 대역폭 정책 서비스(핵심)<BR><STRONG>이벤트 번호 :</STRONG> 36034<BR><STRONG>수준 :</STRONG> 2<BR><STRONG>설명 :</STRONG> 다음 IP 주소에 대한 서브넷: &lt;IP 주소 목록&gt;에 대한 서브넷이 구성되지 않았거나 서브넷이 네트워크 사이트에 연결되지 않았습니다.<BR><STRONG>원인 :</STRONG> 해당 IP 주소에 대한 서브넷이 네트워크 구성 설정에서 누락되었거나 서브넷이 네트워크 사이트에 연결되지 않았습니다.<BR><STRONG>해결 방법 :</STRONG> IP 주소 목록에 해당하는 서브넷을 네트워크 구성 설정에 추가하고 모든 서브넷을 네트워크 사이트에 연결합니다.<BR>예를 들어 알림에 표시된 IP 주소 목록이 10.121.248.226 및 10.121.249.20을 나타내는 경우 이러한 IP 주소가 서브넷에 연결되지 않았거나, 이러한 IP 주소가 연결된 서브넷이 네트워크 사이트 속해 있지 않습니다. 10.121.248.0/24 및 10.121.249.0/24가 이러한 주소에 해당하는 서브넷인 경우 다음과 같이 이 문제를 해결할 수 있습니다. 
> <OL>
> <LI>
> <P>IP 주소 10.121.248.226이 10.121.248.0/24 서브넷과 연결되고, IP 주소 10.121.249.20이 10.121.249.0/24 서브넷과 연결되어 있는지 확인합니다.</P>
> <LI>
> <P>10.121.248.0/24 및 10.121.249.0/24 서브넷이 각각 네트워크 사이트와 연결되어 있는지 확인합니다.</P></LI></OL>



네트워크 서브넷을 사용하는 방법에 대한 자세한 내용은 다음 cmdlet에 대한 Lync Server 관리 셸 설명서를 참조하십시오.

  - [New-CsNetworkSubnet](https://docs.microsoft.com/en-us/powershell/module/skype/New-CsNetworkSubnet)

  - [Get-CsNetworkSubnet](get-csnetworksubnet.md)

  - [Set-CsNetworkSubnet](set-csnetworksubnet.md)

  - [Remove-CsNetworkSubnet](remove-csnetworksubnet.md)


> [!TIP]
> 여러 개의 서브넷을 사용하는 경우에는 CSV(쉼표로 구분된 값) 파일을 사용하여 서브넷을 사이트에 연결하는 것이 좋습니다. CSV 파일에는 <STRONG>IPAddress</STRONG>, <STRONG>mask</STRONG>, <STRONG>description</STRONG>, <STRONG>NetworkSiteID</STRONG> 등과 같은 네 개의 열이 있어야 합니다.



## 관리 셸을 사용하여 서브넷을 네트워크 사이트에 연결하려면

1.  Lync Server 관리 셸 시작: **시작**, **모든 프로그램**, **Microsoft Lync Server 2013**을 차례로 클릭한 다음 **Lync Server 관리 셸**을 클릭합니다.

2.  **New-CsNetworkSubnet** cmdlet을 실행하여 서브넷과 네트워크 사이트를 연결합니다.
    
        New-CsNetworkSubnet -SubnetID <String> -MaskBits <Int32> -NetworkSiteID <String>
    
    예를 들면 다음과 같습니다.
    
        New-CsNetworkSubnet -SubnetID 172.11.12.13 - MaskBits 20 -NetworkSiteID Chicago
    
    이 예에서는 서브넷 172.11.12.13과 네트워크 사이트 “Chicago” 간 연결이 만들어졌습니다.

3.  토폴로지의 모든 서브넷에 대해 2단계를 반복합니다.

## CSV 파일을 가져와서 서브넷과 네트워크 사이트를 연결하려면

1.  추가할 모든 서브넷을 포함하는 CSV 파일을 만듭니다. 예를 들어 다음 내용이 포함된 **subnet.csv** 이름의 파일을 만듭니다.
    
    `IPAddress, mask, description, NetworkSiteID`
    
    `172.11.12.0, 24, "NA:Subnet in Portland", Portland`
    
    `172.11.13.0, 24, "NA:Subnet in Reno", Reno`
    
    `172.11.14.0, 25, "EMEA:Subnet in Warsaw", Warsaw`
    
    `172.11.15.0, 31, "EMEA:Subnet in Paris", Paris`

2.  Lync Server 관리 셸 시작: **시작**, **모든 프로그램**, **Microsoft Lync Server 2013**을 차례로 클릭한 다음 **Lync Server 관리 셸**을 클릭합니다.

3.  다음 cmdlet을 실행하여 **subnet.csv**를 가져온 다음 Lync Server 관리 저장소에 파일의 내용을 저장합니다.
    
        import-csv subnet.csv | foreach {New-CsNetworkSubnet $_IPAddress -MaskBits $_.mask -Description $_.description -NetworkSiteID $_.NetworkSiteID}

## Lync Server 제어판을 사용하여 서브넷과 네트워크 사이트를 연결하려면

1.  브라우저 창을 연 다음 Admin URL을 입력하여 Lync Server 제어판을 엽니다. Lync Server 제어판을 시작하는 데 사용할 수 있는 다양한 방법에 대한 자세한 내용은 [Lync Server 관리 도구 열기](lync-server-2013-open-lync-server-administrative-tools.md)를 참조하세요.

2.  왼쪽 탐색 모음에서 **네트워크 구성** 을 클릭합니다.

3.  **서브넷** 탐색 단추를 클릭합니다.

4.  **새로 만들기** 를 클릭합니다.

5.  **새 서브넷** 페이지에서 **서브넷 ID** 를 클릭한 다음 네트워크 사이트와 연결할 서브넷에서 정의한 IP 주소 범위에 첫 번째 주소를 입력합니다.

6.  **마스크** 를 클릭한 다음 서브넷에 적용할 비트 마스크를 입력합니다.

7.  **네트워크 사이트 ID** 를 클릭한 다음 이 서브넷을 추가하고 있는 사이트의 사이트 ID를 선택합니다.
    

    > [!NOTE]
    > 네트워크 사이트를 아직 만들지 않은 경우에는 이 목록이 비어 있게 됩니다. 절차를 보려면 <A href="lync-server-2013-create-or-modify-a-network-site.md">Lync Server 2013에서 네트워크 사이트 만들기 또는 수정</A>을 참조하십시오. <STRONG>Get-CsNetworkSite</STRONG> cmdlet을 실행하여 배포에 사용할 사이트 ID를 검색할 수 있습니다. 자세한 내용은 Lync Server 관리 셸 설명서를 참조하십시오.



8.  경우에 따라 **설명** 을 클릭하고 이 서브넷을 설명하는 추가 정보를 입력합니다.

9.  **커밋** 을 클릭합니다.

다른 서브넷을 네트워크 사이트에 추가하려면 이러한 단계를 반복합니다.

