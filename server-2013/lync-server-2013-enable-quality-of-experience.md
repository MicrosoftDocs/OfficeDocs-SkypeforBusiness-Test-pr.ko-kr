---
title: QoE(체감 품질) 사용
TOCTitle: QoE(체감 품질) 사용
ms:assetid: c8bb3c67-b324-4d94-8158-00c792c7ac42
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg182583(v=OCS.15)
ms:contentKeyID: 49305006
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# QoE(체감 품질) 사용

 

_**마지막으로 수정된 항목:** 2013-02-23_

QoE(체감 품질)는 통화 및 세션에 포함된 참가자, 장치 이름, 드라이버, IP 주소, 끝점 유형에 대한 정보 및 미디어의 품질을 나타내는 숫자 데이터를 기록합니다. 자세한 내용은 계획 설명서에서 [Lync Server 2013의 모니터링 계획](lync-server-2013-planning-for-monitoring.md)을 참조하십시오.

다음 절차를 사용하여 전체 조직이나 조직의 각 사이트에 대해 QoE를 사용하도록 설정할 수 있습니다.


> [!NOTE]
> QoE를 사용하도록 설정하려면 먼저 모니터링 및 모니터링 백 엔드 데이터베이스를 구성해야 합니다. 자세한 내용은 <A href="lync-server-2013-deploying-monitoring.md">Lync Server 2013의 모니터링 배포</A>를 참조하십시오.



## Lync Server 제어판을 사용하여 QoE를 사용하도록 설정하려면

1.  RTCUniversalServerAdmins 그룹의 구성원인 사용자 계정(또는 이와 동일한 사용자 권한을 가진 사용자 계정)이나 CsServerAdministrator 또는 CsAdministrator 역할이 할당된 사용자 계정에서 Lync Server 2013을 배포한 네트워크에 있는 컴퓨터에 로그온합니다.

2.  브라우저 창을 연 다음 Admin URL을 입력하여 Lync Server 제어판을 엽니다. Lync Server 제어판을 시작하는 데 사용할 수 있는 다양한 방법에 대한 자세한 내용은 [Lync Server 관리 도구 열기](lync-server-2013-open-lync-server-administrative-tools.md)를 참조하세요.

3.  왼쪽 탐색 모음에서 **모니터링 및 보관**을 클릭하고 **체감 품질 데이터**를 클릭합니다.

4.  **체감 품질 데이터** 페이지의 테이블에서 적합한 컬렉션을 클릭하고 **동작**, **QoE 사용**을 차례로 클릭합니다.

## Windows PowerShell cmdlet을 사용하여 QoE를 사용하도록 설정

Windows PowerShell 및 **Set-CsQoEConfiguration** cmdlet을 사용하여 QoE를 사용하도록 설정할 수 있습니다. 이 cmdlet은 Lync Server 2013 관리 셸 또는 원격 세션의 Windows PowerShell에서 실행할 수 있습니다. 원격 Windows PowerShell을 사용하여 Lync Server에 연결하는 방법에 대한 자세한 내용은 Lync Server Windows PowerShell 블로그 문서인 "빠른 시작: 원격 PowerShell을 사용하여 Microsoft Lync Server 2010 관리"([http://go.microsoft.com/fwlink/p/?linkId=255876](http://go.microsoft.com/fwlink/p/?linkid=255876))를 참조하세요.

## 단일 위치에서 QoE를 사용하도록 설정하려면

  - QoE를 사용하도록 설정하려면 EnableQoE 매개 변수를 True($True)로 설정합니다.
    
        Set-CsQoEConfiguration -Identity "site:Redmond" -EnableQoE $True

## 단일 위치에서 QoE를 사용하지 않도록 설정하려면

  - QoE를 사용하지 않도록 설정하려면 EnableQoE 매개 변수를 False($False)로 설정합니다. 이 경우 모니터링이 제거되지는 않습니다. 다만 컬렉션과 QoE 데이터 저장소가 일시 중지됩니다.
    
        Set-CsQoEConfiguration -Identity "site:Redmond" -EnableQoE $False

## 단일 명령을 사용하여 여러 위치에서 QoE를 사용하도록 설정하려면

  - 다음 명령을 사용하면 조직에서 현재 사용 중인 모든 QoE 구성 설정에 대해 QoE를 사용하도록 설정할 수 있습니다.
    
        Get-CsQoEConfiguration | Set-CsQoEConfiguration "site:Redmond" -EnableQoE $True

자세한 내용은 [Set-CsQoEConfiguration](https://docs.microsoft.com/en-us/powershell/module/skype/Set-CsQoEConfiguration)을 참조하십시오.

## 참고 항목

#### 기타 리소스

[Lync Server 2013의 모니터링 계획](lync-server-2013-planning-for-monitoring.md)  
[Lync Server 2013의 모니터링 배포](lync-server-2013-deploying-monitoring.md)

