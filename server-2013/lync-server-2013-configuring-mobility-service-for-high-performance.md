---
title: 높은 성능을 위해 Mobility Service 구성
TOCTitle: 높은 성능을 위해 Mobility Service 구성
ms:assetid: c2b8aadb-cffb-49f0-ba7a-e8541a1ff475
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Hh690042(v=OCS.15)
ms:contentKeyID: 49304940
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# 높은 성능을 위해 Mobility Service 구성

 

_**마지막으로 수정된 항목:** 2013-02-17_

IIS(인터넷 정보 서비스) 7.5에 Lync Server 2013 Mobility Service를 설치하면 Mobility Service 설치 관리자가 프런트 엔드 서버에서 일부 성능 설정을 구성합니다. 모바일 기능에는 IIS 7.5를 사용하는 것이 좋습니다. Windows Server 2008에서 IIS 7.0을 사용하는 경우에는 이러한 설정을 수동으로 구성해야 합니다. 이러한 설정은 최대 동시 사용자 요청 수 및 Mobility Service에 대해 허용되는 최대 스레드 수에 영향을 줍니다.

성능 설정은 다음과 같습니다.

  - **maxConcurrentThreadsPerCPU**는 영(0)으로 설정됩니다.

  - **maxConcurrentRequestsPerCPU**는 영(0)으로 설정됩니다.

  - ASP.NET 프로세스 모델은 AutoConfig로 설정됩니다(IIS 7.5에만 해당).

  - HTTP.sys 큐 제한은 기본적으로 1,000으로 설정됩니다.

IIS 7.0을 사용할 경우 Microsoft 기술 자료 문서 2290617, "수정: IIS 7.0에서 각 응용 프로그램 풀에 대한 일부 ASP.NET 속성의 구성을 사용하도록 설정할 수 있는 핫픽스가 제공됩니다."([http://go.microsoft.com/fwlink/?linkid=3052\&clcid=0x412](http://go.microsoft.com/fwlink/?linkid=3052%26clcid=0x412))에서 제공되는 업데이트를 설치하여 Mobility Service에 대해서만 변경 내용을 적용하고 다른 웹 서비스에는 영향을 주지 않도록 하는 것이 좋습니다.

아래 절차에서는 기술 자료 문서 2290617에서 소개하는 업데이트를 설치하지 않는 경우 IIS 7.0에서 ASP.NET 동시 요청 및 스레드 최대값을 변경하는 방법에 대해 설명합니다. 그러나 기술 자료 문서 2290617의 업데이트를 설치하더라도 해당 문서에서 제공하는 설명서를 참조하여 IIS 응용 프로그램 풀 내부 및 외부의 모바일 기능에만 동일한 변경 내용을 적용해야 합니다. 이 경우 ASP.NET 설정에 대해 별도의 구성 파일을 사용합니다.


> [!IMPORTANT]
> 아래 절차를 통해 최대값을 변경하는 경우 해당 변경 내용은 모든 IIS 응용 프로그램 풀에 적용됩니다.



이러한 설정을 구성하는 방법에 대한 자세한 내용은 [http://go.microsoft.com/fwlink/?linkid=234537\&clcid=0x412](http://go.microsoft.com/fwlink/?linkid=234537%26clcid=0x412)를 참조하십시오.

## 동시 요청 및 스레드 최대값을 변경하려면

1.  **시작**을 클릭한 다음 **실행**을 클릭합니다.

2.  **실행** 상자에 다음을 입력합니다.
    
        notepad %SystemRoot%\Microsoft.NET\Framework64\v2.0.50727\Aspnet.config

3.  **확인**을 클릭합니다.

4.  다음의 \<system.web\> 요소를 Aspnet.config 파일에 있는 \<configuration\> 요소의 하위 요소로 추가하거나, 해당 요소가 이미 있는 경우 아래 요소로 바꿉니다.
    
        <system.web>
        <applicationPool maxConcurrentRequestsPerCPU="<#>" maxConcurrentThreadsPerCPU="0" requestQueueLimit="5000"/>
        </system.web>
    
    여기서 \#는 제한을 제거하려는 경우 0이고, 그렇지 않으면 이 섹션 앞부분에서 설명한 새로운 숫자입니다.

5.  Aspnet.config 파일을 저장하고 메모장을 닫습니다.

