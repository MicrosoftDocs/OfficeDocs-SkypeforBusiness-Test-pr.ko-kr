---
title: 'Lync Server 2013: 영구 채팅 서버에 대한 용량 계획'
TOCTitle: 영구 채팅 서버에 대한 용량 계획
ms:assetid: 7a850cd5-c789-4795-a8ff-083be21ae784
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg615006(v=OCS.15)
ms:contentKeyID: 49304127
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Lync Server 2013의 영구 채팅 서버에 대한 용량 계획

 

_**마지막으로 수정된 항목:** 2015-03-09_

영구 채팅 서버는 이후 검색을 위해 보존할 수 있는 다중 사용자 실시간 채팅을 수행할 수 있습니다. 대화 내용이 구성된 경우 사용자의 사서함에 저장되는 그룹 IM(인스턴트 메시징)과 달리 영구 채팅 서버 세션은 열린 상태로 더 오랫동안 지속되며 메시지, 파일, URL 및 기타 진행중인 대화에 포함되는 데이터와 함께 콘텐츠가 서버에 저장됩니다.

용량 계획은 영구 채팅 서버 배포를 준비하는 데 있어 중요한 부분입니다. 이 항목에서는 배포에 가장 적합한 구성을 결정하는 데 사용할 수 있는 지원되는 영구 채팅 서버 토폴로지 및 용량 계획 테이블에 대해 자세히 설명합니다. 또한 최대 사용 시 더 많은 용량이 필요한 영구 채팅 서버 배포를 관리하는 최상의 방법에 대해서도 설명합니다.

영구 채팅 서버를 다운로드하려면 "Microsoft Lync Server 13 영구 채팅 서버"( [http://go.microsoft.com/fwlink/?linkid=209539\&clcid=0x412](http://go.microsoft.com/fwlink/?linkid=209539%26clcid=0x412))를 참조하십시오.

영구 채팅 서버 설치에 대한 자세한 내용은 배포 설명서에서 [Lync Server 2013에서 영구 채팅 서버 설치](lync-server-2013-installing-persistent-chat-server.md) 및 [Lync Server 2013에서 영구 채팅 서버 구성](lync-server-2013-configuring-persistent-chat-server.md)을 참조하십시오.

Lync Server 계획 도구와 같은 지원 도구는 용량 계획을 추가로 지원할 수 있습니다. 계획 도구에 대한 자세한 내용은 계획 설명서에서 [Lync Server 2013에 대한 계획 프로세스 시작](lync-server-2013-beginning-the-planning-process.md)을 참조하십시오.

## 영구 채팅 서버 지원 토폴로지

단일 서버 또는 다중 서버 풀에 단일 풀 또는 다중 풀 토폴로지로 영구 채팅 서버를 배포할 수 있습니다.

이제는 Standard Edition 서버에서 새 Lync Server 2013 배포에 대해 영구 채팅 서버가 지원됩니다. 하지만 성능 및 확장성에 영향을 주며, 이 새 배포에 대해 고가용성 옵션이 제공되지 않기 때문에 개념 증명, 평가 등의 제한된 목적으로만 주로 사용하는 것이 좋습니다.


> [!NOTE]
> 두 기술에 대한 자세한 내용은 이 설명서 집합의 <A href="lync-server-2013-planning-for-persistent-chat-server.md">Lync Server 2013의 영구 채팅 서버 계획</A> 및 배포 설명서의 <A href="lync-server-2013-deploying-persistent-chat-server.md">Lync Server 2013에서 영구 채팅 서버 배포</A>를 참조하십시오.



## 단일 서버 토폴로지

영구 채팅 서버의 최소 구성 및 가장 간단한 배포는 단일 영구 채팅 서버프런트 엔드 서버 토폴로지입니다. 이 배포를 위해서는 영구 채팅 서버(준수가 설정된 경우 선택적으로 준수 서비스 실행)를 실행하는 단일 서버, SQL Server 데이터베이스를 모두 실행하는 서버, 준수 데이터를 저장하기 위한 SQL Server 데이터베이스(준수가 필요한 경우)가 필요합니다.


> [!IMPORTANT]
> 토폴로지 작성기에서 단일 서버 배포로 시작된 영구 채팅 서버 풀에는 서버를 추가할 수 없습니다. 단일 서버를 사용하더라도 나중에 필요에 따라 서버를 추가할 수 있도록 다중 서버 풀 토폴로지를 사용하는 것이 좋습니다.



다음 그림에서는 준수를 지원하는 단일 영구 채팅 서버프런트 엔드 서버에 대한 모든 필수 및 선택적인 구성 요소를 보여줍니다.

**단일 영구 채팅 서버**

![Compliance Service를 사용하는 단일 서버 토폴로지](images/Gg398500.9168fa52-61e0-4d17-a14d-45fd32e81456(OCS.15).jpg "Compliance Service를 사용하는 단일 서버 토폴로지")

## 다중 서버 토폴로지

더 큰 용량 및 안정성을 제공하려면 [Lync Server 2013의 영구 채팅 서버 계획](lync-server-2013-planning-for-persistent-chat-server.md)에 설명된 대로 다중 서버 토폴로지를 배포할 수 있습니다. 다중 서버 토폴로지는 영구 채팅 서버를 실행하는 최대 4개의 활성 컴퓨터를 포함할 수 있습니다. 고가용성 및 재해 복구 구성에서는 최대 8개까지 허용되지만 4개만 활성 상태일 수 있으며 남은 4개는 대기 상태로 유지됩니다. 각 서버는 최대 20,000명까지 동시 사용자를 지원할 수 있으며, 4개의 서버로 영구 채팅 서버 풀에 연결된 사용자를 총 80,000명까지 지원할 수 있습니다. 다중 서버 토폴로지는 여러 서버가 영구 채팅 서버를 호스팅할 수 있고 더 많이 확장될 수 있다는 것을 제외하고는 단일 서버 토폴로지와 동일합니다. 영구 채팅 서버를 실행하는 여러 컴퓨터는 Lync Server 및 준수 서비스와 동일한 Active Directory 도메인 서비스 도메인에 있어야 합니다.

다음 그림에서는 영구 채팅 서버를 실행하는 여러 컴퓨터가 포함된 다중 서버 토폴로지의 모든 구성 요소, 선택적인 준수 서비스 및 별도의 준수 데이터베이스를 보여줍니다.

**다중 영구 채팅 서버**

![다중 서버 토폴로지](images/Gg398500.19aea898-28df-4d9b-903c-f72ef062d919(OCS.15).jpg "다중 서버 토폴로지")

80,000명의 사용자가 동시에 로그인할 수 있고 영구 채팅을 사용할 수 있는 4개 서버 영구 채팅 서버 배포에서는 서버당 20,000명씩 부하가 고르게 분산됩니다. 한 서버를 사용할 수 없게 되면 해당 서버에 연결된 사용자가 영구 채팅 서버에 액세스할 수 없습니다. 연결이 끊긴 사용자는 해당 서버가 복원될 때까지 자동으로 다른 서버로 이전됩니다. 네트워크에서 영구 채팅 트래픽에 따라 이러한 사용자 이전은 몇 분 이상 걸릴 수 있습니다. 이 경우 남은 각 서버는 최대 30,000명까지 호스팅할 수 있기 때문에 성능 문제를 방지하기 위해 사용할 수 없는 서버를 가능한 한 빨리 복원하는 것이 좋습니다. 그렇지 않으면 토폴로지 작성기 또는 Windows PowerShell cmdlet, **set-CsPersistentChatActiveServer**를 사용해서 다른 영구 채팅 서버를 사용하도록 설정할 수 있습니다.

## 영구 채팅 서버 용량 계획

다음 표는 영구 채팅 서버 용량을 계획하는 데 활용할 수 있습니다. 여기에서는 여러 가지 영구 채팅 서버 설정 변경에 따라 용량 기능에 어떤 영향을 주는지 보여줍니다.

## 영구 채팅 서버의 최대 용량 계획

다음 샘플 표를 사용하여 지원할 사용자 수를 결정할 수 있습니다.

### 영구 채팅 서버 풀 최대 용량 샘플

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p>활성 영구 채팅 서비스 인스턴스</p></td>
<td><p><em>4</em></p></td>
</tr>
<tr class="even">
<td><p>영구 채팅 서비스 인스턴스</p></td>
<td><p><em>8 (4 must be inactive; only a maximum of 4 can be active)</em></p></td>
</tr>
<tr class="odd">
<td><p>연결된 활성 사용자</p></td>
<td><p><em>80,000</em></p></td>
</tr>
<tr class="even">
<td><p>총 프로비전된 사용자</p></td>
<td><p>150,000</p></td>
</tr>
<tr class="odd">
<td><p>끝점 수</p></td>
<td><p>120,000</p></td>
</tr>
</tbody>
</table>


위 샘플에서 계획의 목적은 영구 채팅 서버에서 허용되는 최대 사용자 수를 지원하기 위한 것입니다. 4개의 영구 채팅 서비스 서버/인스턴스(고가용성 및 재해 복구를 위해서는 영구 채팅 서버를 실행하는 수동 서버를 4개 이상 지정할 수 있음)와 서버당 20,000명 사용자로 총 80,000명의 활성 사용자를 지원하기 위한 것입니다.

## 영구 채팅방 액세스 관리를 위한 용량 계획

다음 샘플 테이블은 영구 채팅 서버 풀에서 영구 채팅방 액세스를 계획하는 데 도움이 됩니다.

### 대화방 액세스 관리 샘플

<table>
<colgroup>
<col style="width: 20%" />
<col style="width: 20%" />
<col style="width: 20%" />
<col style="width: 20%" />
<col style="width: 20%" />
</colgroup>
<thead>
<tr class="header">
<th></th>
<th>작은 채팅방</th>
<th>중간 채팅방</th>
<th>큰 채팅방</th>
<th>합계</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>채팅방 크기(연결된 사용자 수)</p></td>
<td><p>채팅방당 30명</p></td>
<td><p>채팅방당 150명</p></td>
<td><p>채팅방당 16,000명</p></td>
<td><p></p></td>
</tr>
<tr class="even">
<td><p>대화방 수</p></td>
<td><p>32,000</p></td>
<td><p>1,067</p></td>
<td><p>10</p></td>
<td><p>33,077</p></td>
</tr>
<tr class="odd">
<td><p>강당인 채팅방 비율</p></td>
<td><p>1%</p></td>
<td><p>1%</p></td>
<td><p>50%</p></td>
<td><p></p></td>
</tr>
<tr class="even">
<td><p>공개된 채팅방 비율</p></td>
<td><p>3%</p></td>
<td><p>3%</p></td>
<td><p>50%</p></td>
<td><p></p></td>
</tr>
<tr class="odd">
<td><p>공개방(명시적인 구성원 자격 없음)</p></td>
<td><p>960</p></td>
<td><p>32</p></td>
<td><p>5</p></td>
<td><p>997</p></td>
</tr>
<tr class="even">
<td><p>비공개 채팅방(구성원 자격이 명시된 일반 채팅방)</p></td>
<td><p>31,040</p></td>
<td><p>1.035</p></td>
<td><p>5</p></td>
<td><p>32,080</p></td>
</tr>
<tr class="odd">
<td><p>강당 채팅방(추가 발표자 입장)</p></td>
<td><p>0</p></td>
<td><p>32</p></td>
<td><p>5</p></td>
<td><p></p></td>
</tr>
<tr class="even">
<td><p>직접 구성원 자격으로 관리되는 채팅방</p></td>
<td><p>50%</p></td>
<td><p>10%</p></td>
<td><p>0%</p></td>
<td><p></p></td>
</tr>
<tr class="odd">
<td><p>사용자 그룹에서 관리하는 대화방 수</p></td>
<td><p>50%</p></td>
<td><p>90%</p></td>
<td><p>100%</p></td>
<td><p></p></td>
</tr>
<tr class="even">
<td><p>공개 채팅방을 위한 각 채팅방의 구성원 자격 목록에 포함된 사용자 그룹(명시적으로 지정되지 않음)</p></td>
<td><p>0</p></td>
<td><p>0</p></td>
<td><p>0</p></td>
<td><p></p></td>
</tr>
<tr class="odd">
<td><p>비공개 채팅방을 위한 각 채팅방의 구성원 자격 목록에 포함된 사용자</p></td>
<td><p>30</p></td>
<td><p>150</p></td>
<td><p>16,000</p></td>
<td><p></p></td>
</tr>
<tr class="even">
<td><p>비공개 채팅방을 위한 각 채팅방의 구성원 자격 목록에 포함된 사용자 그룹</p></td>
<td><p>3</p></td>
<td><p>5</p></td>
<td><p>10</p></td>
<td><p></p></td>
</tr>
<tr class="odd">
<td><p>각 채팅방의 관리자 목록에 있는 사용자 및 사용자 그룹(공개 및 비공개 채팅방용)</p></td>
<td><p>6</p></td>
<td><p>6</p></td>
<td><p>6</p></td>
<td><p></p></td>
</tr>
<tr class="even">
<td><p>각 강당 채팅방의 발표자 목록에 있는 사용자 및 사용자 그룹(공개 및 비공개 채팅방용)</p></td>
<td><p>6</p></td>
<td><p>6</p></td>
<td><p>6</p></td>
<td><p></p></td>
</tr>
<tr class="odd">
<td><p>모든 비공개 채팅방의 사용자 기반 구성원 자격 엔터티</p></td>
<td><p>465,600</p></td>
<td><p>15,520</p></td>
<td><p>-</p></td>
<td><p></p></td>
</tr>
<tr class="even">
<td><p>모든 비공개 채팅방의 사용자 그룹 기반 구성원 자격</p></td>
<td><p>46,560</p></td>
<td><p>4656</p></td>
<td><p>50</p></td>
<td><p></p></td>
</tr>
<tr class="odd">
<td><p>모든 강당 채팅방의 사용자 및 사용자 그룹 기반 엔터티</p></td>
<td><p>0</p></td>
<td><p>192</p></td>
<td><p>50</p></td>
<td><p></p></td>
</tr>
<tr class="even">
<td><p>모든 채팅방 관리자 목록의 사용자 및 사용자 그룹 기반 관리자 엔터티</p></td>
<td><p>192,000</p></td>
<td><p>6,400</p></td>
<td><p>60</p></td>
<td><p></p></td>
</tr>
<tr class="odd">
<td><p>대화방당 활성 사용자 수</p></td>
<td><p><em>30</em></p></td>
<td><p><em>150</em></p></td>
<td><p><em>16,000</em></p></td>
<td><p></p></td>
</tr>
<tr class="even">
<td><p>사용자당 대화방 수</p></td>
<td><p><em>12</em></p></td>
<td><p><em>2</em></p></td>
<td><p><em>2</em></p></td>
<td><p><em>16</em></p></td>
</tr>
<tr class="odd">
<td><p>각 대화방의 구성원 목록에 있는 사용자 그룹 수</p></td>
<td><p><em>10</em></p></td>
<td><p><em>10</em></p></td>
<td><p><em>15</em></p></td>
<td><p></p></td>
</tr>
<tr class="even">
<td><p>사용자 그룹에서 관리하는 대화방 수</p></td>
<td><p><em>50%</em></p></td>
<td><p><em>50%</em></p></td>
<td><p><em>50%</em></p></td>
<td><p></p></td>
</tr>
<tr class="odd">
<td><p>모든 대화방의 사용자 그룹 기반 구성원 엔터티 수</p></td>
<td><p>155,200</p></td>
<td><p>5173</p></td>
<td><p>68</p></td>
<td><p></p></td>
</tr>
<tr class="even">
<td><p>모든 대화방의 사용자 기반 구성원 엔터티 수</p></td>
<td><p>465,600</p></td>
<td><p>77,600</p></td>
<td><p>72,000</p></td>
<td><p></p></td>
</tr>
<tr class="odd">
<td><p>각 대화방의 관리자, 발표자 및 범위 목록에 있는 사용자 및 사용자 그룹 수</p></td>
<td><p>6</p></td>
<td><p>6</p></td>
<td><p>6</p></td>
<td><p></p></td>
</tr>
<tr class="even">
<td><p>모든 채팅방의 관리자, 발표자 및 범위 목록의 사용자 및 사용자 그룹</p></td>
<td><p>192,000</p></td>
<td><p>6400</p></td>
<td><p>60</p></td>
<td><p></p></td>
</tr>
<tr class="odd">
<td><p>액세스 제어 항목 수</p></td>
<td><p>704,160</p></td>
<td><p>26,768</p></td>
<td><p>160</p></td>
<td><p>731,088</p></td>
</tr>
<tr class="even">
<td><p>최대 액세스 제어 항목 수</p></td>
<td><p></p></td>
<td><p></p></td>
<td><p></p></td>
<td><p>2,000,000</p></td>
</tr>
</tbody>
</table>


이전 샘플에서 권장 지침에 따라 영구 채팅 서버를 배포하면 준수 기능을 설정한 상태로 4개의 서버 풀에서 최대 80,000명의 활성 사용자를 처리할 수 있습니다.

이 샘플에서는 소규모(지정된 시간의 활성 사용자 수 30명), 중규모(활성 사용자 수 150명) 및 대규모(활성 사용자 수 16,000명)로 분류된 대화방을 보여 줍니다. 특정 크기의 대화방 수는 다음 항목의 합계를 기반으로 계산됩니다.

  - 시스템의 활성 사용자 수

  - 지정된 크기의 대화방에 있는 활성 사용자 수

  - 단일 사용자가 참가하는 지정된 크기의 대화방 수

각 채팅방에 대해 위 용량 계획 표에서는 채팅방에 직접 지정된 항목을 포함하여 채팅방과 연결된 액세스 제어 항목 수를 지정합니다. ACL(액세스 제어 목록)을 사용해서 개별 채팅방에 대한 액세스를 제어할 수 있습니다. 또한 범주 수준에서 액세스를 제어할 수도 있습니다. ACL에서 개별 액세스 제어 목록은 임의의 사용자 그룹(예: 보안 그룹, 메일 그룹 또는 단일 사용자)일 수 있습니다. 채팅방 관리자, 발표자 및 구성원에 대한 액세스 제어 항목을 정의할 수 있습니다.


> [!IMPORTANT]
> 채팅방 관리를 위한 전략을 계획할 때는 허용되는 액세스 제어 항목의 총 개수가 2백만 개라는 사실에 주의해야 합니다. 계산한 액세스 제어 항목이 200만개를 넘을 경우 서버 성능이 크게 저하될 수 있습니다. 이 문제를 방지하기 위해서는 가능한 한 개별 사용자 대신 사용자 그룹을 액세스 제어 항목으로 설정해야 합니다.



## 초대에 의한 대화방 액세스 관리를 위한 용량 계획

영구 채팅 서버가 초대를 보내도록 구성된 경우 다음과 같은 용량 계획 테이블을 사용해서 영구 채팅 데이터베이스에 만들고 저장하는 초대 개수를 이해할 수 있습니다. 범주에서 초대를 관리하는 작업은 Lync Server 제어판에서 **채팅방 범주 설정** 을 사용하거나 Windows PowerShell cmdlet, **set-csPersistentChatCategory**를 사용해서 수행할 수 있습니다. 채팅방(범주에서 허용하는 조건에 따라)에서 초대를 관리하는 작업은 Lync 클라이언트에서 실행된 **방 관리** 페이지를 사용하거나 Windows PowerShell cmdlet, **set-csPersistentChatRoom**을 사용해서 수행할 수 있습니다.

다음 테이블의 샘플 데이터에서는 모든 채팅의 50%에 해당하는 **채팅방 설정** 페이지에서 **초대** 옵션이 **예** 로 설정되었다고 가정합니다.


> [!IMPORTANT]
> 서버에서 생성되는 것으로 계산된 초대 개수 값이 100만 개를 초과할 경우 서버 성능이 크게 저하될 수 있습니다. 이 문제를 방지하려면 초대를 보내도록 구성된 채팅방 개수를 최소화하거나 초대를 보내도록 구성된 채팅방에 참가할 수 있는 사용자 수를 제한합니다.



### 초대에 의한 대화방 액세스 샘플

<table>
<colgroup>
<col style="width: 20%" />
<col style="width: 20%" />
<col style="width: 20%" />
<col style="width: 20%" />
<col style="width: 20%" />
</colgroup>
<thead>
<tr class="header">
<th></th>
<th>작은 채팅방</th>
<th>중간 채팅방</th>
<th>큰 채팅방</th>
<th>합계</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>채팅방에 액세스할 수 있는 사용자</p></td>
<td><p>채팅방당 30명</p></td>
<td><p>채팅방당 150명</p></td>
<td><p>채팅방당 16,000명</p></td>
<td><p></p></td>
</tr>
<tr class="even">
<td><p>초대를 포함하는 방 비율</p></td>
<td><p>50%</p></td>
<td><p>50%</p></td>
<td><p>50%</p></td>
<td><p></p></td>
</tr>
<tr class="odd">
<td><p>초대를 보내도록 구성된 대화방 수</p></td>
<td><p><em>16,000</em></p></td>
<td><p><em>533</em></p></td>
<td><p><em>5</em></p></td>
<td><p></p></td>
</tr>
<tr class="even">
<td><p>대화방에 액세스할 수 있는 사용자 수</p></td>
<td><p><em>60</em></p></td>
<td><p><em>225</em></p></td>
<td><p><em>16,000</em></p></td>
<td><p></p></td>
</tr>
<tr class="odd">
<td><p>영구 채팅 서버에서 생성된 초대 수</p></td>
<td><p>960,000</p></td>
<td><p>120,000</p></td>
<td><p>80,000</p></td>
<td><p>1,160,000</p></td>
</tr>
<tr class="even">
<td><p>허용되는 최대 초대 수</p></td>
<td><p></p></td>
<td><p></p></td>
<td><p></p></td>
<td><p>2,000,000</p></td>
</tr>
<tr class="odd">
<td><p>모델 1 - 방당 하루에 예상되는 메시지 개수로 시작</p></td>
<td><p></p></td>
<td><p></p></td>
<td><p></p></td>
<td><p></p></td>
</tr>
<tr class="even">
<td><p>방당 채팅 비율(1일 기준)</p></td>
<td><p>50</p></td>
<td><p>500</p></td>
<td><p>100</p></td>
<td><p>650</p></td>
</tr>
<tr class="odd">
<td><p>모든 방의 채팅 비율(초당)</p></td>
<td><p>55.56</p></td>
<td><p>18.52</p></td>
<td><p>0.03</p></td>
<td><p>74</p></td>
</tr>
<tr class="even">
<td><p>모델 2 - 사용자당 하루에 게시되는 메시지 개수로 시작</p></td>
<td><p></p></td>
<td><p></p></td>
<td><p></p></td>
<td><p></p></td>
</tr>
<tr class="odd">
<td><p>사용자당 일일 채팅 비율</p></td>
<td><p>15</p></td>
<td><p>5</p></td>
<td><p>0.1</p></td>
<td><p>20</p></td>
</tr>
<tr class="even">
<td><p>방당 채팅 비율(1일 기준)</p></td>
<td><p>38</p></td>
<td><p>375</p></td>
<td><p>800</p></td>
<td><p>1,213</p></td>
</tr>
<tr class="odd">
<td><p>모든 방의 채팅 비율(초당)</p></td>
<td><p>41.67</p></td>
<td><p>13.89</p></td>
<td><p>0.28</p></td>
<td><p>56</p></td>
</tr>
</tbody>
</table>


## 영구 채팅 서버 성능 사용자 모델

다음 표에서는 영구 채팅 서버의 사용자 모델에 대해 설명합니다. 여기에서는 용량 계획 요구 사항에 대한 기준을 제공하고 4개의 서버로 80,000명의 동시 사용자를 지원하는 일반적인 조직을 보여줍니다.

### 영구 채팅 서버 성능 사용자 모델

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p>연결된 활성 사용자 수</p></td>
<td><p>80,000</p></td>
</tr>
<tr class="even">
<td><p>영구 채팅 서버 서비스 인스턴스 수</p></td>
<td><p>4</p></td>
</tr>
<tr class="odd">
<td><p>소규모 대화방의 크기</p></td>
<td><p>사용자 30명</p></td>
</tr>
<tr class="even">
<td><p>중규모 대화방의 크기</p></td>
<td><p>사용자 150명</p></td>
</tr>
<tr class="odd">
<td><p>대규모 대화방의 크기</p></td>
<td><p>사용자 16,000명</p></td>
</tr>
<tr class="even">
<td><p>총 대화방 수</p></td>
<td><p>33,077</p></td>
</tr>
<tr class="odd">
<td><p>소규모 대화방 수</p></td>
<td><p>32,000</p></td>
</tr>
<tr class="even">
<td><p>중규모 대화방 수</p></td>
<td><p>1,067</p></td>
</tr>
<tr class="odd">
<td><p>대규모 대화방 수</p></td>
<td><p>10</p></td>
</tr>
<tr class="even">
<td><p>사용자당 총 대화방 수</p></td>
<td><p>16</p></td>
</tr>
<tr class="odd">
<td><p>사용자당 소규모 대화방 수</p></td>
<td><p>12</p></td>
</tr>
<tr class="even">
<td><p>사용자당 중규모 대화방 수</p></td>
<td><p>2</p></td>
</tr>
<tr class="odd">
<td><p>사용자당 대규모 대화방 수</p></td>
<td><p>2</p></td>
</tr>
<tr class="even">
<td><p>사용자당 참가한 방 개수</p></td>
<td><p>24</p></td>
</tr>
<tr class="odd">
<td><p>최대 참가 비율</p></td>
<td><p>10/초</p></td>
</tr>
<tr class="even">
<td><p>총 채팅 비율</p></td>
<td><p>24/초</p></td>
</tr>
<tr class="odd">
<td><p>소규모 대화방의 채팅 비율</p></td>
<td><p>22.22/초</p></td>
</tr>
<tr class="even">
<td><p>중규모 대화방의 채팅 비율</p></td>
<td><p>1.67/초</p></td>
</tr>
<tr class="odd">
<td><p>대규모 대화방의 채팅 비율</p></td>
<td><p>~0.15/초</p></td>
</tr>
<tr class="even">
<td><p>초대에 대해 구성된 대화방의 비율</p></td>
<td><p>50%</p></td>
</tr>
<tr class="odd">
<td><p>직접 구성원의 비율</p></td>
<td><p>50%</p></td>
</tr>
<tr class="even">
<td><p>그룹 구성원의 비율</p></td>
<td><p>50%</p></td>
</tr>
<tr class="odd">
<td><p>Active Directory 도메인 서비스의 평균 상위 소속 수</p></td>
<td><p>100 - 200</p></td>
</tr>
<tr class="even">
<td><p>사용자당 등록된 대화 상대 수</p></td>
<td><p>80</p></td>
</tr>
<tr class="odd">
<td><p>사용자당 평균 끝점 수</p></td>
<td><p>1.5</p></td>
</tr>
<tr class="even">
<td><p>끝점당 표시 가능한 평균 채팅방 수</p></td>
<td><p>1.5</p></td>
</tr>
<tr class="odd">
<td><p>사용자당 표시 가능한 평균 채팅방 수</p></td>
<td><p>2.25(1개 방의 50% 및 2개 방의 50%), 최대 6개의 공개방, 모니터당 한 개</p></td>
</tr>
<tr class="even">
<td><p>간격당 폴링되는 참가자 수</p></td>
<td><p>표시되는 대화방당 25개</p></td>
</tr>
<tr class="odd">
<td><p>폴링 간격</p></td>
<td><p>5분</p></td>
</tr>
<tr class="even">
<td><p>초당당 폴링되는 참가자 수</p></td>
<td><p>15,000</p></td>
</tr>
<tr class="odd">
<td><p>사용자별 시간당 현재 상태 변경 수</p></td>
<td><p>6</p></td>
</tr>
<tr class="even">
<td><p>초당 현재 상태 변경 수</p></td>
<td><p>133.33</p></td>
</tr>
</tbody>
</table>

