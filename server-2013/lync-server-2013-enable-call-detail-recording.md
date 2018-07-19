---
title: 통화 정보 기록 사용
TOCTitle: 통화 정보 기록 사용
ms:assetid: 3b28e432-596f-45a5-a070-577d6fa748d9
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg520980(v=OCS.15)
ms:contentKeyID: 49303363
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# 통화 정보 기록 사용

 

_**마지막으로 수정된 항목:** 2013-02-23_

CDR(통화 정보 기록)은 인스턴트 메시징, VoIP(Voice over Internet Protocol) 통화, 응용 프로그램 공유, 파일 전송, 모임 등의 피어 투 피어 활동에 대한 사용 및 진단 정보를 기록합니다. 이러한 사용 데이터는 ROI(투자 수익률)를 계산하는 데 사용하고, 진단 데이터는 피어-투-피어 활동 및 모임 관련 문제를 해결하는 데 사용할 수 있습니다.

다음 절차에 따라 조직의 각 사이트 또는 조직 전체에 대해 CDR을 사용하도록 설정합니다.


> [!NOTE]
> CDR을 사용하도록 설정하려면 먼저 모니터링 및 모니터링 데이터베이스를 구성해야 합니다. 자세한 내용은 <A href="lync-server-2013-deploying-monitoring.md">Lync Server 2013의 모니터링 배포</A>를 참조하십시오.



## Lync Server 제어판을 사용하여 CDR을 사용하도록 설정하려면

1.  RTCUniversalServerAdmins 그룹의 구성원인 사용자 계정(또는 이와 동일한 사용자 권한을 가진 사용자 계정)이나 CsServerAdministrator 또는 CsAdministrator 역할이 할당된 사용자 계정에서 Lync Server 2013을 배포한 네트워크에 있는 컴퓨터에 로그온합니다.

2.  브라우저 창을 연 다음 Admin URL을 입력하여 Lync Server 제어판을 엽니다. Lync Server 제어판을 시작하는 데 사용할 수 있는 다양한 방법에 대한 자세한 내용은 [Lync Server 관리 도구 열기](lync-server-2013-open-lync-server-administrative-tools.md)를 참조하세요.

3.  왼쪽 탐색 모음에서 **모니터링 및 보관**을 클릭하고 **통화 정보 기록**을 클릭합니다.

4.  **통화 정보 기록** 페이지의 표에서 적절한 사이트를 클릭하고 **동작**을 클릭한 후에 **CDR 사용**을 클릭합니다.
    

    > [!NOTE]
    > CDR은 기본적으로 사용하도록 설정됩니다.



## Lync Server 관리 셸 cmdlet을 사용하여 CDR을 사용하도록 설정하려면

Windows PowerShell 및 **Set-CsCdrConfiguration** cmdlet을 사용하여 CDR을 사용하도록 설정할 수도 있습니다. 이 cmdlet은 Lync Server 2013 관리 셸 또는 Windows PowerShell의 원격 세션에서 실행할 수 있습니다. 원격 Windows PowerShell을 사용하여 Lync Server에 연결하는 방법에 대한 자세한 내용은 Lync Server Windows PowerShell 블로그 문서인 "빠른 시작: 원격 PowerShell을 사용하여 Microsoft Lync Server 2010 관리"([http://go.microsoft.com/fwlink/p/?linkId=255876](http://go.microsoft.com/fwlink/p/?linkid=255876))를 참조하세요.

## 단일 위치에 대해 CDR을 사용하도록 설정하려면

  - CDR을 사용하도록 설정하려면 EnableCDR 매개 변수를 True($True)로 설정합니다.
    
        Set-CsCdrConfiguration -Identity "site:Redmond" -EnableCDR $True

## 단일 위치에 대해 CDR을 사용하지 않도록 설정하려면

  - CDR을 사용하지 않도록 설정하려면 EnableCDR 매개 변수를 False($False)로 설정합니다. 이렇게 해도 모니터링이 제거되는 것은 아니며, CDR 데이터 수집 및 저장만 일시 중지됩니다.
    
        Set-CsCdrConfiguration -Identity "site:Redmond" -EnableCDR $False

## 단일 명령을 사용하여 여러 위치에서 CDR을 사용하도록 설정하려면

  - 다음 명령은 조직에서 현재 사용 중인 모든 CDR 구성 설정에 대해 CDR을 사용하도록 설정합니다.
    
        Get-CsCdrConfiguration | Set-CsCdrConfiguration "site:Redmond" -EnableCDR $True

자세한 내용은 [Set-CsCdrConfiguration](https://docs.microsoft.com/en-us/powershell/module/skype/Set-CsCdrConfiguration) cmdlet에 대한 도움말 항목을 참조하십시오.

## 참고 항목

#### 기타 리소스

[Lync Server 2013의 모니터링 계획](lync-server-2013-planning-for-monitoring.md)  
[Lync Server 2013의 모니터링 배포](lync-server-2013-deploying-monitoring.md)

