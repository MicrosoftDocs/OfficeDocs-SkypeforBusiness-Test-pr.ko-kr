---
title: 'Lync Server 2013: 보안 구성 마법사가 IIS에서 포트를 닫은 후 서버 다시 활성화'
TOCTitle: 보안 구성 마법사가 IIS에서 포트를 닫은 후 서버 다시 활성화
ms:assetid: cb8e17cf-f8c1-4099-b63b-c242d656c26a
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg398851(v=OCS.15)
ms:contentKeyID: 49305049
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# 보안 구성 마법사가 IIS에서 포트를 닫은 후 서버 다시 활성화

 

_**마지막으로 수정된 항목:** 2012-10-01_

일부 Lync Server 2013 역할은 IIS(인터넷 정보 서비스) 포트 4443에서 웹 서비스를 실행합니다. Lync Server 배포 마법사인 Bootstrapper.exe를 실행하거나 **Enable-CsComputer** cmdlet을 사용하면 방화벽에 예외가 만들어지고 포트가 열립니다. Windows Server 2008 R2 보안 구성 마법사(또는 기타 강화 스크립트)를 실행하면 포트 4443이 차단되고 외부 클라이언트에서 웹 서비스에 연결할 수 없습니다. 포트를 다시 열려면 방화벽 예외를 직접 수정하거나 서버를 다시 활성화하면 됩니다.

## 배포 마법사를 사용하여 서버를 다시 활성화하려면

1.  Lync Server 배포 마법사 페이지에서 **실행** 을 클릭합니다( **2단계: Lync Server 구성 요소 설치 또는 제거** 를 사용합니다.

2.  **Lync Server 구성 요소 설치** 페이지에서 **다음** 을 클릭합니다.

3.  **명령 실행** 페이지에서 작업 상태가 완료됨으로 표시되면 **마침** 을 클릭합니다.
    

    > [!NOTE]
    > bootstrapper.exe 또는 <STRONG>Enable-CsComputer</STRONG>를 사용하여 서버를 다시 활성화할 수도 있습니다.


