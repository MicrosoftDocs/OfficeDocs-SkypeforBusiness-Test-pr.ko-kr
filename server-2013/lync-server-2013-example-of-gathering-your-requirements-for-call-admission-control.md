---
title: 'Lync Server 2013: 통화 허용 제어 서비스에 대한 요구 사항 수집의 예'
TOCTitle: '예: 통화 허용 제어 서비스에 대한 조직의 요구 사항 수집'
ms:assetid: 3363ac53-b7c4-4a59-aea1-b2f3ee016ae1
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg425827(v=OCS.15)
ms:contentKeyID: 49303250
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# 예: Lync Server 2013에서 통화 허용 제어 서비스에 대한 요구 사항 수집

 

_**마지막으로 수정된 항목:** 2015-03-09_

이 예에서는 CAC(통화 허용 제어)를 계획하고 구현하는 방법을 보여 줍니다. 이 과정은 크게 다음 작업으로 구성됩니다.

1.  모든 네트워크 허브 및 백본( *네트워크 지역* 이라고 함) 확인

2.  각 네트워크 지역에 대한 CAC를 관리할 Lync Server 중앙 사이트 확인

3.  각 네트워크 지역에 연결된 *네트워크 사이트* 확인 및 정의

4.  WAN 연결에 대한 대역폭이 제한된 각 네트워크 사이트에 대해 WAN 연결의 대역폭 용량 및 네트워크 관리자가 Lync Server 미디어 트래픽에 대해 설정한 대역폭 제한(해당되는 경우) 설명. WAN 연결에 대한 대역폭 제한이 없는 사이트는 포함하지 않아도 됩니다.

5.  네트워크의 각 서브넷을 네트워크 사이트와 연결

6.  네트워크 지역 간의 링크 매핑. 각 링크에 대해 해당 대역폭 용량 및 네트워크 관리자가 Lync Server 미디어 트래픽에 대해 설정한 제한을 설명합니다.

7.  모든 네트워크 지역 쌍 간의 경로 정의

## 필요한 정보 수집

통화 허용 제어를 준비하려면 다음 단계에 설명된 정보를 수집합니다.

1.  네트워크 지역을 확인합니다. 네트워크 지역은 네트워크 백본 또는 네트워크 허브를 나타냅니다.
    
    네트워크 백본 또는 네트워크 허브는 네트워크의 여러 부분을 상호 연결하는 컴퓨터 네트워크 인프라의 일부로서, 서로 다른 LAN 또는 서브넷 간의 정보 교환 경로를 제공합니다. 백본은 소규모 위치에서 지리적으로 넓은 지역에 이르기까지 다양한 네트워크를 함께 묶을 수 있습니다. 따라서 백본의 용량은 일반적으로 백본에 연결된 네트워크의 용량보다 큽니다.
    
    여기에 설명된 토폴로지에는 북미, EMEA, APAC, 이렇게 세 개의 네트워크 지역이 있습니다. 네트워크 지역은 네트워크 사이트 모음을 포함합니다. 네트워크 관리자와 함께 회사의 네트워크 지역을 정의하십시오.

2.  각 네트워크 지역의 연결된 중앙 사이트를 확인합니다. 중앙 사이트는 네트워크 지역의 WAN 연결을 통과하는 모든 미디어 트래픽에 대한 CAC를 관리하도록 배포된 Lync Server이며, 하나 이상의 프런트 엔드 서버를 포함합니다.
    
    **세 개의 네트워크 지역으로 분할된 엔터프라이즈 네트워크의 예**
    
    ![네트워크 지역이 3개인 네트워크 토폴로지 예제](images/Gg425827.08937347-250f-488f-ba5f-c256e6afcd8b(OCS.15).jpg "네트워크 지역이 3개인 네트워크 토폴로지 예제")  
    

    > [!NOTE]
    > MPLS(Multiprotocol Label Switching) 네트워크는 각 지리적 위치에 해당하는 네트워크 사이트가 있는 네트워크 지역으로 표시됩니다. 자세한 내용은 계획 설명서에서 " <A href="lync-server-2013-call-admission-control-on-an-mpls-network.md">Lync Server 2013의 MPLS 네트워크에 대한 통화 허용 제어 서비스</A>" 항목을 참조하십시오.

    
    위의 네트워크 토폴로지 예는 각각 CAC를 관리하는 Lync Server 중앙 사이트가 있는 세 개의 네트워크 지역으로 구성되어 있습니다. 네트워크 지역에 적합한 중앙 사이트는 지리적 근접성에 따라 선택됩니다. 미디어 트래픽은 네트워크 지역 내에서 부하가 가장 크기 때문에 지리적 근접성에 따라 소유권을 할당하면 네트워크 지역이 자동으로 포함되고 다른 중앙 사이트를 사용할 수 없는 경우에도 네트워크 지역이 계속 작동합니다.
    
    이 예에서 시카고라는 Lync Server 배포는 북미 지역의 중앙 사이트입니다.
    
    북미의 모든 Lync 사용자는 시카고 배포의 서버에 속합니다. 다음 표에서는 세 개의 네트워크 지역에 대한 중앙 사이트를 보여 줍니다.
    
    ### 네트워크 지역 및 관련 중앙 사이트
    
    <table>
    <colgroup>
    <col style="width: 50%" />
    <col style="width: 50%" />
    </colgroup>
    <thead>
    <tr class="header">
    <th>네트워크 지역</th>
    <th>중앙 사이트</th>
    </tr>
    </thead>
    <tbody>
    <tr class="odd">
    <td><p>북미</p></td>
    <td><p>시카고</p></td>
    </tr>
    <tr class="even">
    <td><p>EMEA</p></td>
    <td><p>런던</p></td>
    </tr>
    <tr class="odd">
    <td><p>APAC</p></td>
    <td><p>베이징</p></td>
    </tr>
    </tbody>
    </table>
    

    > [!NOTE]
    > Lync Server 토폴로지에 따라 같은 중앙 사이트가 여러 네트워크 지역에 할당될 수 있습니다.



3.  각 네트워크 지역에 대해 WAN 연결에 대역폭 제한이 없는 모든 네트워크 사이트(사무실 또는 위치)를 확인합니다. 이러한 사이트는 대역폭 제한이 없으므로 CAC 대역폭 정책을 적용할 필요가 없습니다.
    
    아래 표의 예에서는 WAN 링크에 대한 대역폭 제한이 없는 세 개의 네트워크 사이트(뉴욕, 시카고 및 디트로이트)를 보여 줍니다.
    
    ### WAN 대역폭 제한이 없는 네트워크 사이트
    
    <table>
    <colgroup>
    <col style="width: 50%" />
    <col style="width: 50%" />
    </colgroup>
    <thead>
    <tr class="header">
    <th>네트워크 사이트</th>
    <th>네트워크 지역</th>
    </tr>
    </thead>
    <tbody>
    <tr class="odd">
    <td><p>뉴욕</p></td>
    <td><p>북미</p></td>
    </tr>
    <tr class="even">
    <td><p>시카고</p></td>
    <td><p>북미</p></td>
    </tr>
    <tr class="odd">
    <td><p>디트로이트</p></td>
    <td><p>북미</p></td>
    </tr>
    </tbody>
    </table>


4.  각 네트워크 지역에 대해 대역폭이 제한된 WAN 링크를 통해 네트워크 지역에 연결되는 모든 네트워크 사이트를 확인합니다.
    
    오디오 및 비디오 품질을 보장하기 위해 대역폭이 제한된 이러한 네트워크 사이트에서는 WAN을 모니터링하고 네트워크 지역에서 들어오고 나가는 미디어(음성 또는 비디오) 트래픽 흐름을 제한하는 CAC 대역폭 정책을 적용하는 것이 좋습니다.
    
    아래 표의 예에서는 WAN 대역폭이 제한된 세 개의 네트워크 사이트(포틀랜드, 리노 및 앨버커키)를 보여 줍니다.
    
    ### WAN 대역폭이 제한된 네트워크 사이트
    
    <table>
    <colgroup>
    <col style="width: 50%" />
    <col style="width: 50%" />
    </colgroup>
    <thead>
    <tr class="header">
    <th>네트워크 사이트</th>
    <th>네트워크 지역</th>
    </tr>
    </thead>
    <tbody>
    <tr class="odd">
    <td><p>앨버커키</p></td>
    <td><p>북미</p></td>
    </tr>
    <tr class="even">
    <td><p>리노</p></td>
    <td><p>북미</p></td>
    </tr>
    <tr class="odd">
    <td><p>포틀랜드</p></td>
    <td><p>북미</p></td>
    </tr>
    </tbody>
    </table>
    
    **대역폭 제한이 없는 세 개의 네트워크 사이트(시카고, 뉴욕 및 디트로이트)와 WAN 대역폭이 제한된 세 개의 네트워크 사이트(포틀랜드, 리노 및 앨버커키)가 포함된 북미 CAC 네트워크 지역**
    
    ![WAN 대역폭이 제한된 예제 네트워크 사이트](images/Gg425827.d9d1f231-db4d-4dd7-8fbc-eb0b6d1e705d(OCS.15).jpg "WAN 대역폭이 제한된 예제 네트워크 사이트")  

5.  대역폭이 제한된 각 WAN 링크에 대해 다음 사항을 확인합니다.
    
      - 모든 동시 오디오 세션에 대해 설정할 전체 대역폭 제한. 새 오디오 세션으로 인해 이러한 제한을 초과하는 경우에는 Lync Server에서 세션 시작을 허용하지 않습니다.
    
      - 각각의 개별 오디오 세션에 대해 설정할 대역폭 제한. 기본 CAC 대역폭 제한은 175kbps이지만 관리자가 수정할 수 있습니다.
    
      - 모든 동시 비디오 세션에 대해 설정할 전체 대역폭 제한. 새 비디오 세션으로 인해 이러한 제한을 초과하는 경우에는 Lync Server에서 세션 시작을 허용하지 않습니다.
    
      - 각각의 개별 비디오 세션에 대해 설정할 대역폭 제한. 기본 CAC 대역폭 제한은 700kbps이지만 관리자가 수정할 수 있습니다.
    
    ### WAN 대역폭 제한 정보가 있는 네트워크 사이트(대역폭 단위: kbps)
    
    <table style="width:100%;">
    <colgroup>
    <col style="width: 14%" />
    <col style="width: 14%" />
    <col style="width: 14%" />
    <col style="width: 14%" />
    <col style="width: 14%" />
    <col style="width: 14%" />
    <col style="width: 14%" />
    </colgroup>
    <thead>
    <tr class="header">
    <th>네트워크 사이트</th>
    <th>네트워크 지역</th>
    <th>대역폭 제한</th>
    <th>오디오 제한</th>
    <th>오디오 세션 제한</th>
    <th>비디오 제한</th>
    <th>비디오 세션 제한</th>
    </tr>
    </thead>
    <tbody>
    <tr class="odd">
    <td><p>앨버커키</p></td>
    <td><p>북미</p></td>
    <td><p>5,000</p></td>
    <td><p>2,000</p></td>
    <td><p>175</p></td>
    <td><p>1,400</p></td>
    <td><p>700</p></td>
    </tr>
    <tr class="even">
    <td><p>리노</p></td>
    <td><p>북미</p></td>
    <td><p>10,000</p></td>
    <td><p>4,000</p></td>
    <td><p>175</p></td>
    <td><p>2,800</p></td>
    <td><p>700</p></td>
    </tr>
    <tr class="odd">
    <td><p>포틀랜드</p></td>
    <td><p>북미</p></td>
    <td><p>5,000</p></td>
    <td><p>4,000</p></td>
    <td><p>175</p></td>
    <td><p>2,800</p></td>
    <td><p>700</p></td>
    </tr>
    <tr class="even">
    <td><p>뉴욕</p></td>
    <td><p>북미</p></td>
    <td><p>(제한 없음)</p></td>
    <td><p>(제한 없음)</p></td>
    <td><p>(제한 없음)</p></td>
    <td><p>(제한 없음)</p></td>
    <td><p>(제한 없음)</p></td>
    </tr>
    <tr class="odd">
    <td><p>시카고</p></td>
    <td><p>북미</p></td>
    <td><p>(제한 없음)</p></td>
    <td><p>(제한 없음)</p></td>
    <td><p>(제한 없음)</p></td>
    <td><p>(제한 없음)</p></td>
    <td><p>(제한 없음)</p></td>
    </tr>
    <tr class="even">
    <td><p>디트로이트</p></td>
    <td><p>북미</p></td>
    <td><p>(제한 없음)</p></td>
    <td><p>(제한 없음)</p></td>
    <td><p>(제한 없음)</p></td>
    <td><p>(제한 없음)</p></td>
    <td><p>(제한 없음)</p></td>
    </tr>
    </tbody>
    </table>


6.  네트워크의 모든 서브넷에 대해 연결된 네트워크 사이트를 지정합니다.
    

    > [!IMPORTANT]
    > 네트워크의 모든 서브넷은 네트워크 사이트와 연결되어야 하며, 네트워크 사이트에 대한 대역폭 제한이 없는 경우에도 마찬가지입니다. 이는 통화 허용 제어에서 서브넷 정보를 사용하여 끝점이 있는 네트워크 사이트를 확인하기 때문입니다. 세션에 참가한 두 대상의 위치가 확인되면 통화 허용 제어에서 통화를 연결하기에 충분한 대역폭이 있는지 확인할 수 있습니다. 대역폭 제한이 없는 링크를 통해 세션이 설정된 경우 알림이 생성됩니다.<BR>오디오/비디오 에지 서버를 배포하는 경우 각 에지 서버의 공용 IP 주소를 해당 에지 서버가 배포된 네트워크 사이트와 연결해야 합니다. A/V 에지 서버의 각 공용 IP 주소는 서브넷 마스크가 32인 서브넷으로 네트워크 구성 설정에 추가해야 합니다. 예를 들어 시카고에 A/V 에지 서버를 배포하는 경우 이러한 서버의 각 외부 IP 주소에 대해 서브넷 마스크가 32인 서브넷을 만들고 시카고 네트워크 사이트를 해당 서브넷과 연결합니다. 공용 IP 주소에 대한 자세한 내용은 계획 설명서에서 <A href="lync-server-2013-determine-external-a-v-firewall-and-port-requirements.md">Lync Server 2013에 대한 외부 A/V 방화벽 및 포트 요구 사항 확인</A>을 참조하십시오.

    

    > [!NOTE]
    > 네트워크에 있지만 서브넷과 연결되지 않은 IP 주소 목록 또는 IP 주소가 포함되어 있지만 네트워크 사이트에 연결되지 않은 서브넷 목록을 지정하는 KHI(Key Health Indicator) 알림이 표시됩니다. 이 알림은 8시간 간격으로 한 번만 발생합니다(해당되는 경우). 관련 알림 정보 및 예는 다음과 같습니다.<BR><STRONG>원본 :</STRONG> CS 대역폭 정책 서비스(핵심)<BR><STRONG>이벤트 번호 :</STRONG> 36034<BR><STRONG>수준 :</STRONG> 2<BR><STRONG>설명 :</STRONG> 다음 IP 주소에 대한 서브넷: &lt;IP 주소 목록&gt;에 대한 서브넷이 구성되지 않았거나 서브넷이 네트워크 사이트에 연결되지 않았습니다.<BR><STRONG>원인 :</STRONG> 해당 IP 주소에 대한 서브넷이 네트워크 구성 설정에서 누락되었거나 서브넷이 네트워크 사이트에 연결되지 않았습니다.<BR><STRONG>해결 방법 :</STRONG> 위의 IP 주소 목록에 해당하는 서브넷을 네트워크 구성 설정에 추가하고 모든 서브넷을 네트워크 사이트에 연결하십시오.<BR>예를 들어 알림에 표시된 IP 주소 목록이 10.121.248.226 및 10.121.249.20을 나타내는 경우 이러한 IP 주소가 서브넷에 연결되지 않았거나, 이러한 IP 주소가 연결된 서브넷이 네트워크 사이트 속해 있지 않습니다. 10.121.248.0/24 및 10.121.249.0/24가 이러한 주소에 해당하는 서브넷인 경우 다음과 같이 이 문제를 해결할 수 있습니다. 
    > <OL>
    > <LI>
    > <P>IP 주소 10.121.248.226이 10.121.248.0/24 서브넷과 연결되고, IP 주소 10.121.249.20이 10.121.249.0/24 서브넷과 연결되어 있는지 확인합니다.</P>
    > <LI>
    > <P>10.121.248.0/24 및 10.121.249.0/24 서브넷이 각각 네트워크 사이트와 연결되어 있는지 확인합니다.</P></LI></OL>

    
    ### 네트워크 사이트 및 연결된 서브넷(대역폭 단위: kbps)
    
    <table>
    <colgroup>
    <col style="width: 12%" />
    <col style="width: 12%" />
    <col style="width: 12%" />
    <col style="width: 12%" />
    <col style="width: 12%" />
    <col style="width: 12%" />
    <col style="width: 12%" />
    <col style="width: 12%" />
    </colgroup>
    <thead>
    <tr class="header">
    <th>네트워크 사이트</th>
    <th>네트워크 지역</th>
    <th>대역폭 제한</th>
    <th>오디오 제한</th>
    <th>오디오 세션 제한</th>
    <th>비디오 제한</th>
    <th>비디오 세션 제한</th>
    <th>서브넷</th>
    </tr>
    </thead>
    <tbody>
    <tr class="odd">
    <td><p>앨버커키</p></td>
    <td><p>북미</p></td>
    <td><p>5,000</p></td>
    <td><p>2,000</p></td>
    <td><p>175</p></td>
    <td><p>1,400</p></td>
    <td><p>700</p></td>
    <td><p>172.29.79.0/23, 157.57.215.0/25, 172.29.90.0/23, 172.29.80.0/24</p></td>
    </tr>
    <tr class="even">
    <td><p>리노</p></td>
    <td><p>북미</p></td>
    <td><p>10,000</p></td>
    <td><p>4,000</p></td>
    <td><p>175</p></td>
    <td><p>2,800</p></td>
    <td><p>700</p></td>
    <td><p>157.57.210.0/23, 172.28.151.128/25</p></td>
    </tr>
    <tr class="odd">
    <td><p>포틀랜드</p></td>
    <td><p>북미</p></td>
    <td><p>5,000</p></td>
    <td><p>4,000</p></td>
    <td><p>175</p></td>
    <td><p>2,800</p></td>
    <td><p>700</p></td>
    <td><p>172.29.77.0/24 10.71.108.0/24, 157.57.208.0/23</p></td>
    </tr>
    <tr class="even">
    <td><p>뉴욕</p></td>
    <td><p>북미</p></td>
    <td><p>(제한 없음)</p></td>
    <td><p>(제한 없음)</p></td>
    <td><p>(제한 없음)</p></td>
    <td><p>(제한 없음)</p></td>
    <td><p>(제한 없음)</p></td>
    <td><p>172.29.80.0/23, 157.57.216.0/25, 172.29.91.0/23, 172.29.81.0/24</p></td>
    </tr>
    <tr class="odd">
    <td><p>시카고</p></td>
    <td><p>북미</p></td>
    <td><p>(제한 없음)</p></td>
    <td><p>(제한 없음)</p></td>
    <td><p>(제한 없음)</p></td>
    <td><p>(제한 없음)</p></td>
    <td><p>(제한 없음)</p></td>
    <td><p>157.57.211.0/23, 172.28.152.128/25</p></td>
    </tr>
    <tr class="even">
    <td><p>디트로이트</p></td>
    <td><p>북미</p></td>
    <td><p>(제한 없음)</p></td>
    <td><p>(제한 없음)</p></td>
    <td><p>(제한 없음)</p></td>
    <td><p>(제한 없음)</p></td>
    <td><p>(제한 없음)</p></td>
    <td><p>172.29.78.0/24 10.71.109.0/24, 157.57.209.0/23</p></td>
    </tr>
    </tbody>
    </table>


7.  Lync Server 통화 허용 제어에서는 네트워크 지역 간의 연결을 *지역 링크* 라고 합니다. 각 지역 링크에 대해 네트워크 사이트와 마찬가지로 다음 사항을 확인합니다.
    
      - 모든 동시 오디오 세션에 대해 설정할 전체 대역폭 제한. 새 오디오 세션으로 인해 이러한 제한을 초과하는 경우에는 Lync Server에서 세션 시작을 허용하지 않습니다.
    
      - 각각의 개별 오디오 세션에 대해 설정할 대역폭 제한. 기본 CAC 대역폭 제한은 175kbps이지만 관리자가 수정할 수 있습니다.
    
      - 모든 동시 비디오 세션에 대해 설정할 전체 대역폭 제한. 새 비디오 세션으로 인해 이러한 제한을 초과하는 경우에는 Lync Server에서 세션 시작을 허용하지 않습니다.
    
      - 각각의 개별 비디오 세션에 대해 설정할 대역폭 제한. 기본 CAC 대역폭 제한은 700kbps이지만 관리자가 수정할 수 있습니다.
    
    **연관된 대역폭 제한이 있는 네트워크 지역 링크**
    
    ![3개 지역 간의 제한 예제](images/Gg425827.25259afa-ee7c-4d26-bc41-92ba9cb56dec(OCS.15).jpg "3개 지역 간의 제한 예제")  
    
    ### 지역 링크 대역폭 정보(대역폭 단위: kbps)
    
    <table>
    <colgroup>
    <col style="width: 12%" />
    <col style="width: 12%" />
    <col style="width: 12%" />
    <col style="width: 12%" />
    <col style="width: 12%" />
    <col style="width: 12%" />
    <col style="width: 12%" />
    <col style="width: 12%" />
    </colgroup>
    <thead>
    <tr class="header">
    <th>지역 링크 이름</th>
    <th>첫 번째 지역</th>
    <th>두 번째 지역</th>
    <th>대역폭 제한</th>
    <th>오디오 제한</th>
    <th>오디오 세션 제한</th>
    <th>비디오 제한</th>
    <th>비디오 세션 제한</th>
    </tr>
    </thead>
    <tbody>
    <tr class="odd">
    <td><p>NA-EMEA-LINK</p></td>
    <td><p>북미</p></td>
    <td><p>EMEA</p></td>
    <td><p>50,000</p></td>
    <td><p>20,000</p></td>
    <td><p>175</p></td>
    <td><p>14,000</p></td>
    <td><p>700</p></td>
    </tr>
    <tr class="even">
    <td><p>EMEA-APAC-LINK</p></td>
    <td><p>EMEA</p></td>
    <td><p>APAC</p></td>
    <td><p>25,000</p></td>
    <td><p>10,000</p></td>
    <td><p>175</p></td>
    <td><p>7,000</p></td>
    <td><p>700</p></td>
    </tr>
    </tbody>
    </table>


8.  모든 네트워크 지역 쌍 간의 경로 정의
    

    > [!NOTE]
    > 북미 지역과 APAC 지역 간의 경로에는 두 지역을 직접 연결하는 지역 링크가 없으므로 두 개의 링크가 필요합니다.

    
    ### 지역 경로
    
    <table>
    <colgroup>
    <col style="width: 25%" />
    <col style="width: 25%" />
    <col style="width: 25%" />
    <col style="width: 25%" />
    </colgroup>
    <thead>
    <tr class="header">
    <th>지역 경로 이름</th>
    <th>첫 번째 지역</th>
    <th>두 번째 지역</th>
    <th>지역 링크</th>
    </tr>
    </thead>
    <tbody>
    <tr class="odd">
    <td><p>NA-EMEA-ROUTE</p></td>
    <td><p>북미</p></td>
    <td><p>EMEA</p></td>
    <td><p>NA-EMEA-LINK</p></td>
    </tr>
    <tr class="even">
    <td><p>EMEA-APAC-ROUTE</p></td>
    <td><p>EMEA</p></td>
    <td><p>APAC</p></td>
    <td><p>EMEA-APAC-LINK</p></td>
    </tr>
    <tr class="odd">
    <td><p>NA-APAC-ROUTE</p></td>
    <td><p>북미</p></td>
    <td><p>APAC</p></td>
    <td><p>NA-EMEA-LINK, EMEA-APAC-LINK</p></td>
    </tr>
    </tbody>
    </table>


9.  단일 링크( *사이트 간* 링크라고 함)로 직접 연결되는 모든 네트워크 사이트 쌍에 대해 다음 사항을 확인합니다.
    
      - 모든 동시 오디오 세션에 대해 설정할 전체 대역폭 제한. 새 오디오 세션으로 인해 이러한 제한을 초과하는 경우에는 Lync Server에서 세션 시작을 허용하지 않습니다.
    
      - 각각의 개별 오디오 세션에 대해 설정할 대역폭 제한. 기본 CAC 대역폭 제한은 175kbps이지만 관리자가 수정할 수 있습니다.
    
      - 모든 동시 비디오 세션에 대해 설정할 전체 대역폭 제한. 새 비디오 세션으로 인해 이러한 제한을 초과하는 경우에는 Lync Server에서 세션 시작을 허용하지 않습니다.
    
      - 각각의 개별 비디오 세션에 대해 설정할 대역폭 제한. 기본 CAC 대역폭 제한은 700kbps이지만 관리자가 수정할 수 있습니다.
    
    **북미 CAC 네트워크 지역의 리노와 앨버커키 간의 사이트 간 링크에 대한 대역폭 용량 및 대역폭 제한**
    
    ![WAN 대역폭이 제한된 네트워크 사이트 예제](images/Gg425827.063e5e1d-b6c8-4e8c-98db-c227c78f671d(OCS.15).jpg "WAN 대역폭이 제한된 네트워크 사이트 예제")  
    
    ### 두 네트워크 사이트 간의 사이트 간 링크에 대한 대역폭 정보(대역폭 단위: kbps)
    
    <table>
    <colgroup>
    <col style="width: 12%" />
    <col style="width: 12%" />
    <col style="width: 12%" />
    <col style="width: 12%" />
    <col style="width: 12%" />
    <col style="width: 12%" />
    <col style="width: 12%" />
    <col style="width: 12%" />
    </colgroup>
    <thead>
    <tr class="header">
    <th>사이트 간 링크 이름</th>
    <th>첫 번째 사이트</th>
    <th>두 번째 사이트</th>
    <th>대역폭 제한</th>
    <th>오디오 제한</th>
    <th>오디오 세션 제한</th>
    <th>비디오 제한</th>
    <th>비디오 세션 제한</th>
    </tr>
    </thead>
    <tbody>
    <tr class="odd">
    <td><p>Reno-Albu-Intersite-Link</p></td>
    <td><p>리노</p></td>
    <td><p>앨버커키</p></td>
    <td><p>20,000</p></td>
    <td><p>12,000</p></td>
    <td><p>175</p></td>
    <td><p>5,000</p></td>
    <td><p>700</p></td>
    </tr>
    </tbody>
    </table>


## 다음 단계

필요한 정보를 수집한 후에는 Lync Server 관리 셸 또는 Lync Server 제어판을 사용하여 CAC 배포를 수행할 수 있습니다.


> [!NOTE]
> Lync Server 제어판을 사용하여 대부분의 네트워크 구성 작업을 수행할 수 있지만 서브넷 및 사이트 간 링크를 만들려면 Lync Server 관리 셸을 사용해야 합니다. 자세한 내용은 <STRONG>New-CsNetworkSubnet</STRONG> cmdlet 및 <STRONG>New-CsNetworkIntersitePolicy</STRONG> cmdlet에 대한 Lync Server 관리 셸 설명서를 참조하십시오.


