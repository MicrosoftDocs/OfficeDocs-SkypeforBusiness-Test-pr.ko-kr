---
title: 토폴로지 정보 확인
TOCTitle: 토폴로지 정보 확인
ms:assetid: aa4c424e-f87c-4be6-8df6-a0cd193b11fc
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/JJ205151(v=OCS.15)
ms:contentKeyID: 49304679
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# 토폴로지 정보 확인

 

_**마지막으로 수정된 항목:** 2012-09-26_

병합이 성공적으로 완료되었는지 확인하는 첫 번째 단계는 Office Communications Server 2007 R2과 병합한 Lync Server 2013 토폴로지 정보를 확인하는 것입니다. 토폴로지 작성기에서 **BackCompatSite** 노드는 병합한 각 Office Communications Server 2007 R2 풀 및 서버에 대한 FQDN(정규화된 도메인 이름)을 표시합니다.

## 토폴로지 작성기에서 BackCompatSite를 보려면

1.  Office Communications Server 2007 R2 환경에서 Office Communications Server 2007 R2 관리 도구를 열고 레거시 풀 및 서버의 FQDN을 확인합니다.

2.  Lync Server 2013 환경에서 토폴로지 작성기를 연 후 **BackCompatSite** 노드를 확장합니다.

3.  병합하는 풀 및 서버의 FQDN이 표시되는지 확인합니다.
    

    > [!NOTE]
    > 프런트 엔드 서버 또는 Standard Edition Server에 배치된 서버 역할에 대해서는 <STRONG>BackCompatSite</STRONG> 에 아무 정보도 표시되지 않습니다. Office Communications Server 2007 R2와 Lync Server 2013 사이의 상호 운용성에 필요한 서버 역할만 표시됩니다.



![토폴로지 작성기 BackCompatSite 대화 상자](images/JJ205243.62751c76-f018-4c6d-bb48-c61ef8974d31(OCS.15).jpg "토폴로지 작성기 BackCompatSite 대화 상자")

또한 Lync Server 2013 제어판을 사용하여 병합된 토폴로지를 볼 수도 있습니다. Lync Server 2013 제어판에서는 병합된 토폴로지에 대한 각 서버 FQDN, 풀 FQDN 및 사이트 이름을 볼 수 있습니다. 병합된 서버는 **BackCompatSite** 라는 **사이트** 를 포함합니다.

## Lync Server 2013 제어판에서 병합된 토폴로지를 보려면

1.  Lync Server 2013 제어판을 엽니다.

2.  **토폴로지** 를 클릭합니다.

3.  **상태** 탭의 **사이트** 열에서 **BackCompatSite** 를 찾아서 병합한 서버 및 풀이 표시되는지 확인합니다.

![병합된 토폴로지를 보여 주는 Lync Server 제어판](images/JJ205151.f986ddd4-2040-454d-9389-7f6154b59cc9(OCS.15).jpg "병합된 토폴로지를 보여 주는 Lync Server 제어판")

병합된 풀에 대한 자세한 내용을 보려면 **Get-CsPool** cmdlet을 사용합니다. 토폴로지 작성기 및 Lync Server 2013 제어판에 제공되는 정보 외에도 이 cmdlet은 Lync Server 2013 풀에서 실행되는 서비스를 표시합니다.


> [!NOTE]
> 토폴로지 작성기에서 병합 마법사를 실행한 후 토폴로지를 게시하면 회의 디렉터리가 Lync Server 2013에 병합됩니다. <STRONG>Get-CsConferenceDirectory</STRONG> cmdlet을 실행하여 회의 디렉터리를 확인할 수 있습니다.



## 병합된 풀에서 서비스를 보려면

1.  Lync Server 2013 관리 셸를 엽니다.

2.  명령줄에 다음을 입력합니다.
    
        Get-CsPool [-Identity <FQDN of the pool>]
    
    예를 들면 다음과 같습니다.
    
        Get-CsPool -Identity pool02.contoso.net

## 병합된 회의 디렉터리를 보려면

1.  Lync Server 2013 관리 셸를 엽니다.

2.  명령줄에 다음을 입력합니다.
    
        Get-CsConferenceDirectory

3.  병합하는 풀 또는 서버의 모든 회의 디렉터리가 이제 Lync Server 2013에 있는지 확인합니다.

