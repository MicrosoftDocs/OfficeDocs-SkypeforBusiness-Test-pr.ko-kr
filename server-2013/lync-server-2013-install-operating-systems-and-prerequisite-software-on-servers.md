---
title: 'Lync Server 2013: 서버에 운영 체제 및 필수 구성 요소 소프트웨어 설치'
TOCTitle: 서버에 운영 체제 및 필수 구성 요소 소프트웨어 설치
ms:assetid: 055991e0-5aeb-43fc-a7ba-d4b02316d73b
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg398103(v=OCS.15)
ms:contentKeyID: 49302671
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Lync Server 2013의 서버에 운영 체제 및 필수 구성 요소 소프트웨어 설치

 

_**마지막으로 수정된 항목:** 2014-07-24_

하드웨어 및 소프트웨어 인프라를 설치한 후에는 배포하려는 각 서버의 다른 모든 소프트웨어 필수 구성 요소와 함께 적절한 Windows 운영 체제 및 업데이트를 설치해야 합니다. 여기에는 배포에 필요한 각 Lync Server 2013 서버 역할 및 SQL Server를 실행하는 추가 인프라 서버가 포함됩니다.


> [!NOTE]
> 이 섹션에서는 내부 서버용 운영 체제 및 소프트웨어 필수 구성 요소 설치에 대해 설명합니다. 외부 사용자 액세스를 지원하기 위해 에지 서버를 배포하려는 경우 에지 서버 및 역방향 프록시 서버를 포함하여 이러한 서버용 운영 체제 및 소프트웨어 필수 구성 요소도 설치해야 합니다. 외부 사용자 액세스를 지원하도록 서버를 준비하는 방법에 대한 자세한 내용은 배포 설명서에서 <A href="lync-server-2013-preparing-for-installation-of-servers-in-the-perimeter-network.md">Lync Server 2013의 경계 네트워크에 서버 설치 준비</A>를 참조하십시오.



## 서버에 Windows 운영 체제 설치

배포하려는 각 서버에 적절한 Windows 운영 체제를 다음과 같이 설치합니다.

  - **Lync Server 2013을 실행하는 서버**   Lync Server 2013을 실행하는 서버의 운영 체제 요구 사항에 대한 자세한 내용은 지원 가능성 설명서에서 [Lync Server 2013의 서버 및 도구 운영 체제 지원](lync-server-2013-server-and-tools-operating-system-support.md)을 참고하세요.

  - **데이터베이스 서버**   백 엔드 데이터베이스, 보관 데이터베이스 및 모니터링 데이터베이스를 포함하여 데이터베이스 서버의 운영 체제 요구 사항에 대한 자세한 내용은 SQL Server 설명서를 참조하십시오. SQL Server 2012의 경우 [http://go.microsoft.com/fwlink/?linkid=218015\&clcid=0x412](http://go.microsoft.com/fwlink/?linkid=218015%26clcid=0x412)의 SQL Server 2012 온라인 설명서를 참조하십시오.


> [!NOTE]
> Windows Server&nbsp;2008&nbsp;R2 SP1에 Lync Server 2013을 설치하는 경우에는 먼저 Microsoft 기술 자료 문서 2646886, "FIX: IIS 7.5에서 모듈이 InsertEntityBody 메서드를 호출할 때 힙 손상이 발생함"( <A class=uri href="http://go.microsoft.com/fwlink/?linkid=3052%26clcid=0x412">http://go.microsoft.com/fwlink/?linkid=3052&amp;clcid=0x412</A>)에 설명되어 있는 업데이트를 설치해야 합니다.<BR>기술 자료 문서 <A href="http://go.microsoft.com/fwlink/p/?linkid=506893">이벤트 ID 32402, 61045가 Windows Server 2012 R2에 설치된 Lync Server 2013 프런트 엔드 서버에 기록됨</A>에 설명된 대로 레지스트리도 수정해야 합니다.



## 서버에 Windows 업데이트 설치

각 서버에 Windows 업데이트의 다음 업데이트를 설치합니다.

  - **Lync Server 2013을 실행하는 서버용 Windows Update**    Lync Server 2013을 실행하는 서버에 필요한 Windows 업데이트의 업데이트에 대한 자세한 내용은 계획 설명서에서 [Lync Server 2013에 대한 추가 소프트웨어 요구 사항](lync-server-2013-additional-software-requirements.md)을 참고하세요.

  - **데이터베이스 서버**   백 엔드 데이터베이스, 보관 데이터베이스 및 모니터링 데이터베이스를 포함하여 데이터베이스 서버에 필요한 Windows 업데이트의 업데이트에 대한 자세한 내용은 SQL Server 2012 설명서를 참조하십시오. SQL Server 2012의 경우 [http://go.microsoft.com/fwlink/?linkid=218015\&clcid=0x412](http://go.microsoft.com/fwlink/?linkid=218015%26clcid=0x412)의 SQL Server 2012 온라인 설명서를 참조하십시오.

## 서버에 다른 소프트웨어 필수 구성 요소 설치

Lync Server 2013을 사용하려면 서버에 다음과 같은 추가 소프트웨어를 설치해야 합니다.

  - **Lync Server 2013을 실행하는 서버용 소프트웨어 필수 구성 요소**    Lync Server 2013을 실행하는 서버용 추가 소프트웨어 필수 구성 요소는 배포하려는 서버 역할에 따라 다릅니다. 각 서버의 특정 소프트웨어 요구 사항에 대한 자세한 내용은 계획 설명서에서 [Lync Server 2013에 대한 추가 소프트웨어 요구 사항](lync-server-2013-additional-software-requirements.md)을 참고하세요.

  - **Windows Identity Foundation**    Lync Server 2013에서 서버 간 인증 시나리오를 지원하려면 Windows Identity Foundation을 설치해야 합니다. 컴퓨터에 Windows Identity Foundation이 이미 설치되었는지 확인하려면 제어판으로 이동하여 **프로그램 및 기능** , **설치된 업데이트 보기** 를 차례로 클릭한 다음 **Microsoft Windows** 아래를 확인합니다. Windows Identity Foundation을 설치하는 방법에 대한 자세한 내용은 [http://go.microsoft.com/fwlink/?linkid=204657\&clcid=0x412](http://go.microsoft.com/fwlink/?linkid=204657%26clcid=0x412)를 참조하십시오.

  - **Microsoft .NET Framework 4.5**    Lync Server 2013을 사용하려면 Microsoft .NET Framework 4.5의 64비트 버전이 필요합니다.

  - **데이터베이스 서버의 소프트웨어 필수 구성 요소**   백 엔드 데이터베이스, 보관 데이터베이스 및 모니터링 데이터베이스를 포함하여 데이터베이스 서버에 필요한 Windows Update에 대한 자세한 내용은 [http://go.microsoft.com/fwlink/?linkid=218015\&clcid=0x412](http://go.microsoft.com/fwlink/?linkid=218015%26clcid=0x412)의 SQL Server 2012 설명서를 참조하십시오.
    

    > [!NOTE]
    > Lync Server 2013은 로컬 구성 저장소가 있는 각 Standard Edition 서버 및 각 Lync Server 2013 실행 서버에 Microsoft SQL Server 2012 Express를 자동으로 설치합니다.



  - **Windows Media 형식 런타임**   회의를 배포할 모든 프런트 엔드 서버 및 Standard Edition 서버에는 Windows Media 형식 런타임이 설치되어 있어야 합니다. Windows Media 형식 런타임은 통화 대기, 알림 및 응답 그룹 응용 프로그램에서 알림 및 음악에 대해 재생하는 Windows Media 오디오(.wma) 파일을 실행하는 데 필요합니다.
    

    > [!NOTE]
    > Windows Server 2012 및 Windows Server 2012 R2의 경우 Windows Media 형식 런타임은 Microsoft 미디어 파운데이션과 함께 설치됩니다.

    

    > [!NOTE]
    > Windows Server&nbsp;2008 및 Windows Server&nbsp;2008&nbsp;R2의 경우 Windows Media 형식 런타임은 Windows Desktop Experience의 일부로 설치됩니다. Lync Server 2013을 설치하기 전에 Windows Desktop Experience를 설치하는 것이 좋습니다. Lync Server 2013이 서버에서 이 소프트웨어를 찾지 못하는 경우 이 소프트웨어를 설치하라는 메시지가 표시되며 소프트웨어를 설치한 후에는 서버를 다시 시작해야 설치가 완료됩니다.


