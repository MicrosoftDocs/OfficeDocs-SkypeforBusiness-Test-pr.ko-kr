---
title: Lync Server 2013에서 중재 서버를 항상 바이패스하도록 미디어 바이패스 구성
TOCTitle: Lync Server 2013에서 중재 서버를 항상 바이패스하도록 미디어 바이패스 구성
ms:assetid: 370c4f54-e520-4d77-96a3-84c5e84a9996
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg425846(v=OCS.15)
ms:contentKeyID: 49303295
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Lync Server 2013에서 중재 서버를 항상 바이패스하도록 미디어 바이패스 구성

 

_**마지막으로 수정된 항목:** 2013-02-25_


> [!NOTE]
> 이 항목에서는 미디어가 중재 서버를 바이패스하도록 할 특정 사이트 또는 서비스에 대해 모든 트렁크 연결에 대한 미디어 바이패스를 피어(ITSP(인터넷 전화 통신 서비스 공급자)의 SBC(Session Border Controller), IP-PBX 또는 공중 전화망(PSTN) 게이트웨이)로 이미 구성했다고 가정합니다.<BR>통화 허용 제어를 사용하도록 설정하는 동시에 중재 서버를 항상 바이패스하도록 미디어를 구성할 수는 없습니다. 이 두 설정은 호환되지 않으므로 Lync Server 제어판 사용자 인터페이스에서 함께 사용할 수 없는 설정입니다.



피어와 연결된 개별 트렁크 연결에 대해 미디어가 중재 서버를 바이패스하도록 설정하는 것 외에, 미디어 바이패스를 위한 전역 설정도 구성해야 합니다. 이 항목의 단계를 사용하여 미디어 바이패스를 위한 전역 설정을 구성하는 경우, 트렁크 연결에 대해 미디어 바이패스를 구성한 피어 및 Lync 끝점에 정상적으로 연결할 수 있다고 가정합니다.

개별 트렁크 연결이 미디어 바이패스를 사용하도록 설정된 중재 서버로의 모든 피어와 Lync Server 끝점이 정상적으로 연결되지 않는 경우에는 미디어 바이패스를 적용할 때 사이트 및 지역 정보를 사용하도록 전역 미디어 바이패스 설정을 구성해야 합니다. 이렇게 하면 미디어가 중재 서버를 바이패스하는 경우를 보다 정밀하게 제어할 수 있습니다. 이렇게 하려면[사이트 및 지역 정보를 사용하도록 Lync Server 2013에서 미디어 바이패스 전역 설정 구성](lync-server-2013-configure-media-bypass-global-settings-to-use-site-and-region-information.md) 및 [Lync Server 2013 에서 네트워크 사이트에 서브넷 연결](lync-server-2013-associate-a-subnet-with-a-network-site.md)의 단계를 대신 사용합니다.

## 항상 중재 서버를 바이패스하도록 전역적으로 미디어 바이패스를 설정하려면

1.  브라우저 창을 연 다음 Admin URL을 입력하여 Lync Server 제어판을 엽니다. Lync Server 제어판을 시작하는 데 사용할 수 있는 다양한 방법에 대한 자세한 내용은 [Lync Server 관리 도구 열기](lync-server-2013-open-lync-server-administrative-tools.md)를 참조하세요.

2.  왼쪽 탐색 모음에서 **네트워크 구성**을 클릭합니다.

3.  목록에서 **전역** 구성을 두 번 클릭합니다.

4.  **전역 설정 편집** 페이지에서 **미디어 바이패스 사용** 확인란을 선택합니다.

5.  **항상 바이패스**를 클릭합니다.

6.  **커밋**을 클릭합니다.

## 참고 항목

#### 개념

[Lync Server 2013에서 미디어 바이패스 구성](lync-server-2013-configure-media-bypass.md)  
[Lync Server 2013의 전역 미디어 바이패스 옵션](lync-server-2013-global-media-bypass-options.md)  
[Lync Server 2013의 미디어 바이패스 및 중재 서버](lync-server-2013-media-bypass-and-mediation-server.md)  

#### 기타 리소스

[Lync Server 2013의 미디어 바이패스 계획](lync-server-2013-planning-for-media-bypass.md)

