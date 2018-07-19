---
title: PowerShell로 중앙화된 로깅 서비스 구성 설정 관리
TOCTitle: PowerShell로 중앙화된 로깅 서비스 구성 설정 관리
ms:assetid: f455c3aa-0061-413d-bdfb-a3e78f82723d
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/JJ721938(v=OCS.15)
ms:contentKeyID: 49886059
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# PowerShell로 중앙화된 로깅 서비스 구성 설정 관리

 

_**마지막으로 수정된 항목:** 2012-11-01_

중앙 로깅 서비스는 중앙 로깅 서비스 컨트롤러(CLSController)에서 개별 컴퓨터의 에이전트(CLSAgent)로 명령을 전송할 목적으로 만들고 사용하는 설정 및 매개 변수를 통해 제어되고 구성됩니다. 이 에이전트는 전송되는 명령을 처리하고 (시작 명령의 경우) 시나리오의 구성, 로그 크기, 추적 기간 및 플래그를 사용하여 제공된 구성 정보에 따라 추적 로그를 수집하기 시작합니다.


> [!IMPORTANT]
> 중앙 로깅 서비스용으로 나열된 일부 Windows PowerShell cmdlet은 Lync Server 2013 온-프레미스 배포용이 아닙니다. 다음 cmdlet은 작동하는 것처럼 보일 수 있지만 Lync Server 2013 온-프레미스 배포에서 작동하도록 디자인되지 않았습니다. 
> <UL>
> <LI>
> <P><STRONG>CsClsRegion cmdlet:</STRONG> <A href="https://docs.microsoft.com/en-us/powershell/module/skype/Get-CsClsRegion">Get-CsClsRegion</A>, <A href="https://docs.microsoft.com/en-us/powershell/module/skype/Set-CsClsRegion">Set-CsClsRegion</A>, <A href="https://docs.microsoft.com/en-us/powershell/module/skype/New-CsClsRegion">New-CsClsRegion</A> 및 <A href="https://docs.microsoft.com/en-us/powershell/module/skype/Remove-CsClsRegion">Remove-CsClsRegion</A>.</P>
> <LI>
> <P><STRONG>CsClsSearchTerm cmdlet:</STRONG> <A href="https://docs.microsoft.com/en-us/powershell/module/skype/Get-CsClsSearchTerm">Get-CsClsSearchTerm</A> 및 <A href="https://docs.microsoft.com/en-us/powershell/module/skype/Set-CsClsSearchTerm">Set-CsClsSearchTerm</A>.</P>
> <LI>
> <P><STRONG>CsClsSecurityGroup cmdlet:</STRONG> <A href="https://docs.microsoft.com/en-us/powershell/module/skype/Get-CsClsSecurityGroup">Get-CsClsSecurityGroup</A>, <A href="https://docs.microsoft.com/en-us/powershell/module/skype/Set-CsClsSecurityGroup">Set-CsClsSecurityGroup</A>, <A href="https://docs.microsoft.com/en-us/powershell/module/skype/New-CsClsSecurityGroup">New-CsClsSecurityGroup</A> 및 <A href="https://docs.microsoft.com/en-us/powershell/module/skype/Remove-CsClsSecurityGroup">Remove-CsClsSecurityGroup</A>.</P></LI></UL>이러한 cmdlet에 정의된 설정은 작업을 방해하거나 부적절한 동작을 유발하지 않지만 Microsoft Office 365용이 아니며 온-프레미스 배포에서 예상한 대로 작동하지 않습니다. 이 말이 온-프레미스 배포에서 이러한 cmdlet을 사용할 수 없음을 의미하는 것은 아니지만 이 설명서에서는 이러한 cmdlet의 용도에 대해 설명하지 않겠습니다.



## 이 단원의 내용

이 섹션의 항목은 중앙 로깅 서비스에 대한 구성 옵션, 매개 변수 및 설정을 정의합니다. 중앙 로깅 서비스를 구성하는 방법, 시나리오 생성, 중앙 로깅 서비스에 대한 보안 그룹 관리, 검색 등은 다음 항목에서 설명합니다.

  - [컴퓨터, 사이트, 전역 중앙 로깅 서비스 구성 관리](lync-server-2013-managing-computer-site-and-global-centralized-logging-service-configuration.md)

  - [중앙 로깅 서비스에 대한 공급자 구성](lync-server-2013-configuring-providers-for-centralized-logging-service.md)

  - [중앙 로깅 서비스에 대한 시나리오 구성](lync-server-2013-configuring-scenarios-for-the-centralized-logging-service.md)

## 참고 항목

#### 개념

[중앙화된 로깅 서비스 개요](lync-server-2013-overview-of-the-centralized-logging-service.md)  
[중앙화된 로깅 Cmdlet](lync-server-2013-centralized-logging-cmdlets.md)

