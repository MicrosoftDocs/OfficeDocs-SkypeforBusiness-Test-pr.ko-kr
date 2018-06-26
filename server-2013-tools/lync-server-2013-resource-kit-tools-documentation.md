---
title: Lync Server 2013 리소스 키트 도구 설명서
TOCTitle: Lync Server 2013 리소스 키트 도구 설명서
ms:assetid: b1c341f1-86fa-479d-ba4d-28df5a4c1622
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/JJ945604(v=OCS.15)
ms:contentKeyID: 52057023
ms.date: 01/08/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Lync Server 2013 리소스 키트 도구 설명서

 

_**마지막으로 수정된 항목:** 2014-01-09_

이 항목에서는 Lync Server 2013 리소스 키트에 포함된 도구(각 도구의 용도 및 도구 사용 예제 포함)에 대해 설명합니다. Lync Server 2013, 리소스 키트 도구를 사용하면 Lync Server 2013을 배포하고 관리하는 IT 관리자가 일상적인 작업을 더욱 쉽게 수행할 수 있습니다. 예를 들어 **Web Conf Data** 도구를 사용하면 온라인 모임 도중 사용자가 업로드한 데이터를 쉽게 제어할 수 있습니다. **SEFAUtil** 도구를 사용하면 사용자를 위한 착신 전환 및 응답 대리인을 설정할 수 있습니다. IT 관리자가 Lync Server 2013을 더욱 효과적으로 관리하려면 이러한 도구를 사용하는 것이 좋습니다.

## 리소스 키트 도구 설치

Lync Server 2013, 리소스 키트 도구를 설치하려면 **OCSReskit.msi**를 다운로드합니다. 리소스 키트 도구 설치 관리자는 다운로드 센터([http://go.microsoft.com/fwlink/p/?LinkID=330429](http://go.microsoft.com/fwlink/p/?linkid=330429))에서 다운로드할 수 있습니다.

**OCSResKit.msi**를 실행하여 간단하게 설치할 수 있습니다. **%Program Files%\\Microsoft Lync Server 2013\\ResKit** 경로에 모든 도구가 설치됩니다. 자체 포함 실행 파일인 도구는 이 폴더 안에 있으며, 파일을 포함하는 도구는 고유의 하위 폴더 안에 있습니다.

## 지원 환경

성능을 최적화하려면 Lync Server 2013, 리소스 키트 도구를 Lync Server 2013에 요구되는 것과 동일한 환경 및 사양에서 설치합니다.

## 리소스 키트 도구 개요

다음 목록에서는 Lync Server 2013 리소스 키트에 제공되는 도구에 대해 설명합니다. 각 도구의 요구 사항과 예제 사용을 비롯한 설명은 다음 섹션에서 다룹니다.

  - ABSConfig

  - Bandwidth Policy Service Monitor

  - Bandwidth Utilization Analyzer

  - Call Parkometer

  - CleanupStorageServiceData

  - DBAnalyze

  - ImportStorageServiceData

  - LCSSync

  - LookupUserConsole

  - MsTurnPing

  - Network Configuration Viewer

  - Response Group Agent Live

  - SEFAUtil

  - SYSPrep.ps1

  - Unassigned Number Announcements Migration

  - Web Conf Data

## ABSConfig

ABSConfig는 관리자가 Lync Server 2013에서 주소록 서비스 구성을 사용자 지정할 수 있는 관리 도구입니다. 또한 이 도구를 사용하여 Lync Server 2013 관리자가 기본 주소록 서비스 설정을 복원할 수 있습니다.

## 설명

ABSConfig는 그래픽 사용자 인터페이스 응용 프로그램으로, 관리자는 이 도구를 사용하여 주소록 서비스와 관련된 Active Directory 도메인 서비스 특성을 구성할 수 있습니다.

이 도구의 기본 시나리오는 다음과 같습니다.

  - 관리자가 Active Directory 도메인 서비스 특성을 Lync Server 2013 특성에 매핑할 수 있습니다.

  - 관리자가 주소록 서비스 파일에 Active Directory 도메인 서비스 특성을 포함하거나 제외하도록 지정할 수 있습니다.

  - 관리자가 기본 주소록 서비스 설정을 복원할 수 있습니다.

absConfig.exe 파일을 사용하여 ABSConfig를 시작합니다. 도구에서 **Configure Attributes(특성 구성)** 탭이 열립니다. 이 테이블에는 Active Directory 도메인 서비스 특성을 Lync Server 2013의 특성 필드에 매핑하고 특정한 특성 필터에 따라 주소록 서비스 파일에 포함하거나 제외할 사용자를 지정할 수 있는 옵션이 있습니다. 관리자는 **기본값 복원(Restore Defaults)** 옵션을 사용하여 주소록 서비스 설정을 기본값으로 복원할 수 있습니다.

## Lync Server 2010에서 변경된 내용

Lync Server 2013 ABS 구성 도구에서 특성에 대한 "사용" 확인란 선택을 취소하여 해당 특성(행)을 제거할 수 있습니다. 이는 Lync Server 2010에서 행을 삭제하는 것과 같은 효과를 가집니다.


> [!NOTE]
> 사용 확인란은 맨 오른쪽 열에 있으므로 해당 열을 보기 위해 오른쪽으로 스크롤해야 할 수도 있습니다.



## 출력

ABSConfig는 데이터베이스에 주소록 서비스 구성을 저장합니다.
```C++
    Path: %ProgramFiles%\Microsoft Lync Server 2013\Reskit
```
## 용도

ABSConfig를 사용하면 Lync Server 2013 주소록 서비스를 간편하고 쉽게 사용자 지정할 수 있습니다.

## 요구 사항

## 컴퓨터

ABSConfig는 Lync Server 2013이 설치되어 있는, 도메인에 가입된 컴퓨터에서만 실행할 수 있습니다. Lync Server 2013 Enterprise Edition의 경우 이 도구는 설치 도중 주소록 서비스를 설정한 모든 프런트 엔드 서버에서 실행할 수 있습니다.

## 네트워크

컴퓨터에서 프런트 엔드 풀과 백 엔드 데이터베이스에 연결할 수 있어야 합니다.

## 소프트웨어

ABSConfig를 실행하기 전에 다음 소프트웨어 구성 요소를 설치해야 합니다.

  - Microsoft Lync Server 2013

## 사용자

Lync Server 2013 배포를 업데이트하는 데 필요한 권한이 있는 관리자여야 합니다.

## 예제

명령 프롬프트에 **ABSConfig.exe**를 입력하여 ABSConfig를 시작합니다. 아래 그림은 ABSConfig 사용자 인터페이스입니다.

![ABSConfig.exe 도구.](images/JJ945604.6fb63a70-7b63-4b8b-b7d1-82fe9aa2028f(OCS.15).jpg "ABSConfig.exe 도구.")

## 요약

관리자는 ABSConfig 도구를 사용하여 Lync Server 2013 주소록 서비스를 간편하고 쉽게 사용자 지정할 수 있습니다.

## Bandwidth Policy Service Monitor

Bandwidth Policy Service Monitor 도구는 관리자에게 다음 목록을 볼 수 있는 권한을 부여합니다.

1.  토폴로지에서 구성된 모든 Lync Server 2013 대역폭 정책 서비스(인증 및 핵심)

2.  각 서비스에서 다른 대역폭 정책 서비스로의 연결 및 에지 서버로의 연결

3.  네트워크 구성 문서에 구성된 모든 링크 및 각 대역폭 정책 서비스에서 보고된 실시간 대역폭 사용량

## 설명

Bandwidth Policy Service Monitor 도구는 GUI 기반 응용 프로그램으로 구현됩니다.관리자는 PDPMonUI.exe를 실행하여 도구를 시작합니다.

도구를 시작하면 토폴로지의 대역폭 정책 서비스 목록이 검색됩니다. 초기 업데이트가 완료되면 서비스 목록이 각 서비스가 포함된 클러스터로 그룹화되어 왼쪽 창에 표시됩니다.

관리자가 특정 대역폭 정책 서비스를 선택하면 오른쪽 창에 해당 특정 서비스에 대한 정보가 표시됩니다. 해당 창에는 정보를 표시하는 두 개의 기본 탭이 있습니다.

## Machine Info(컴퓨터 정보) 탭

**Machine Info(컴퓨터 정보)** 탭에는 선택한 대역폭 정책 서비스 세부 정보와 선택한 대역폭 정책 서비스에서 다른 서비스에 대해 만든 모든 연결 목록 및 상태가 표시됩니다.

## Topology Info(토폴로지 정보) 탭

**Topology Info(토폴로지 정보)** 탭에는 네트워크 구성 설정에서 구성된 모든 링크 목록이 표시됩니다. 각 링크에 대한 오디오 및 비디오 대역폭 용량이 표시되고, 최근에 사용한 대역폭이 Kbps 및 용량의 백분율로 표시됩니다. 사용량이 용량에 근접한 링크를 강조하기 위해 색 구분이 사용되므로 관리자가 이러한 링크를 빠르게 구분할 수 있습니다.


> [!NOTE]
> Bandwidth Policy Service Monitor 도구를 구성된 대역폭 정책 서비스에 연결할 때 오류가 발생하면 <STRONG>Machine Info(컴퓨터 정보)</STRONG> 및 <STRONG>Topology Info(토폴로지 정보)</STRONG> 탭에 정보가 표시되지 않습니다. 그러나 도구가 초기에 서비스에 연결되었다가 이후에 연결이 끊어진 경우에는 관리자에게 이전 정보가 표시될 수 있습니다. 각 탭에 있는 <STRONG>Last Updated(마지막으로 업데이트한 날짜)</STRONG> 타임스탬프를 통해 관리자는 특정 대역폭 정책 서비스의 데이터가 마지막으로 업데이트된 날짜를 볼 수 있습니다.



## 출력

명령줄 출력은 없으며, 프로그램 출력은 기본 그래픽 사용자 인터페이스(GUI) 안에 포함됩니다.

## 용도

Bandwidth Policy Service Monitor 도구의 용도는 관리자에게 토폴로지에 정의된 각 대역폭 정책 서비스 상태를 표시하는 것입니다. 또한 관리자는 네트워크 구성 문서에 정의된 모든 링크의 실시간 대역폭 사용량을 볼 수 있습니다.

## 요구 사항

Bandwidth Policy Service Monitor 도구는 Lync Server 토폴로지에 포함된 컴퓨터에서 실행됩니다.

## 요약

Bandwidth Policy Service Monitor 도구는 관리자가 토폴로지의 대역폭 정책 서비스 상태를 검사할 수 있는 중요한 리소스이며, 무엇보다 네트워크 구성 설정에 정의된 링크의 실시간 대역폭 사용량을 확인할 수 있습니다.

## Bandwidth Utilization Analyzer

Bandwidth Utilization Analyzer는 엔터프라이즈 네트워크의 WAN 링크를 통해 UC 끝점에서 이루어진 대역폭 소비의 다양한 관점에 대한 보고서를 만드는 도구입니다. 이러한 보고서는 현재 대역폭 소비 패턴을 이해하고 대역폭 용량 계획을 돕는 데 사용할 수 있습니다.

## 설명

Bandwidth Utilization Analyzer는 GUI 기반 응용 프로그램으로 구현됩니다. 이 도구에서는 특별히 네트워크를 통한 오디오 사용량에 대한 보고서를 생성하여 용량 계획에 도움을 주며, 다양한 링크에 할당된 대역폭 용량에 대해 반복 작업을 수행합니다.

## 출력

Bandwidth Utilization Analyzer는 시스템에 구성된 모든 WAN 링크의 오디오 대역폭 용량 및 사용량을 그래픽 그림으로 제공합니다.

## 용도

모든 음성 및 비디오 배포에 있어서 엔터프라이즈 네트워크를 통한 미디어 트래픽의 대역폭 사용량 추세를 모니터링하고 이해하는 것은 중요하며, 관리자는 Bandwidth Utilization Analyzer 도구를 사용하여 이를 수행할 수 있습니다. 이 도구는 다음을 지원합니다.

  - 네트워크를 통한 오디오 사용량에 대한 특정 보고서 생성

  - 더욱 효과적인 용량 계획 및 다양한 링크에 할당된 대역폭 용량에 대한 반복 작업 지원

Bandwidth Utilization Analyzer는 다음에 대한 대역폭 용량 및 사용량 보고서의 그래픽 그림을 생성합니다.

  - 엔터프라이즈 네트워크의 모든 WAN 링크

  - 선택한 WAN 링크로 필터링됨

  - 링크 용량을 초과한 WAN 링크로 필터링됨

  - 프로비전된 대역폭 활용도가 낮은 WAN 링크로 필터링됨

  - 임계값에 도달한 WAN 링크(대역폭 사용량이 WAN 링크의 대역폭 용량의 90%를 초과한 경우)로 필터링됨

  - WAN 링크 유형(네트워크 사이트 링크, 영역간 링크, 사이트 내 링크)으로 필터링됨

  - 네트워크 지역으로 필터링됨

## 응용 프로그램

Bandwidth Utilization Analyzer에는 다음 두 개의 응용 프로그램(도구)이 포함되어 있습니다.

  - **WanLinkLogCollector.exe**   사용자는 이 도구를 사용하여 필수 정보를 입력할 수 있습니다.

  - **BandwidthUtilizationAnalyzer.xlsm **  Microsoft Excel 스프레드시트 소프트웨어 보고서가 WanLinkLogCollector.exe에서 자동으로 실행됩니다. 사용자는 이 응용 프로그램을 사용하여 보고서에 필터를 적용할 수 있으며, 해당 내용은 이 문서 뒷부분에서 설명합니다.

## Bandwidth Utilization Analyzer 사용 단계

Bandwidth Utilization Analyzer는 다음 두 단계로 사용할 수 있습니다.

  - WanLinkLogCollector.exe를 사용하여 로그 수집

  - BandwidthUtilizationAnalyzer.xlsm을 사용하여 보고서 사용자 지정


> [!IMPORTANT]
> BandwidthUtilizationAnalyzer.xlsm은 최종 사용자가 수동으로 실행하지 않는 것이 좋습니다.



## Bandwidth Utilization Analyzer 시작

명령 프롬프트에서 또는 Windows 탐색기를 사용하여 WanLinkLogCollector.exe를 시작합니다.

**WanLinkLogCollector.exe 사용**

다음 세 단계로 WanLinkLogCollector.exe를 사용합니다.

1.  **시간 표시 막대 로깅**   보고서 생성에 필요한 시간 표시 막대를 제공합니다.

2.  **파일 디렉터리 지정**   파일 위치 정보를 제공합니다.

3.  **로그 수집 및 보고서 뷰어 시작 **  명령을 실행하여 보고서를 생성합니다.

## 1단계 - 시간 표시 막대 로깅

도구 사용자는 시간 표시 막대를 로깅하여 아래 그림과 같이 다음 항목을 지정할 수 있습니다.

1.  **시작 날짜** 보고서를 생성할 시간 표시 막대의 시작 날짜입니다(예: 2010년 8월 1일).

2.  **종료 날짜** 보고서를 생성할 시간 표시 막대의 종료 날짜입니다(예: 2010년 9월 30일).
    
    ![Bandwidth Utilization Analyzer의 시작 및 종료 날짜](images/JJ945604.2c597cfc-3372-4d41-816b-26202f607ad8(OCS.15).jpg "Bandwidth Utilization Analyzer의 시작 및 종료 날짜")  

## 2단계 - 파일 디렉터리 지정

다음과 같이 사용자가 파일 디렉터리를 지정할 수 있습니다.

  - **서버 로그 파일 위치** 대역폭 정책 서버 로그를 저장할 폴더 위치입니다. 일반적으로 \<fileserver\>\\\<FE 선택\>\\AppServerFiles\\PDP입니다.

  - **임시 파일 저장 위치 ** 보고서가 생성되는 동안 중간 파일을 저장할 임시 파일 위치입니다.

![Bandwidth Utilization Analyzer의 파일 디렉터리](images/JJ945604.d66daeac-1669-45e3-932d-3f6782840c2a(OCS.15).jpg "Bandwidth Utilization Analyzer의 파일 디렉터리")


> [!NOTE]
> 도구 사용자에게 서버 로그와 임시 파일 저장 폴더에 대한 충분한 파일 액세스 권한이 제공되었는지 확인합니다.



## 3단계 - 로그 수집 및 보고서 뷰어 시작

로그를 수집하고 보고서 뷰어를 시작하려면 아래와 같이 **Execute(실행)**를 클릭합니다. 이 단계에서는 필수 데이터를 수집합니다.

![Bandwidth Utilization Analyzer의 데이터 수집](images/JJ945604.0019cb2c-7c01-4dc9-ac90-ac47c47d1bfd(OCS.15).jpg "Bandwidth Utilization Analyzer의 데이터 수집")

입력 유효성 검사에 성공하면 아래와 같은 메시지가 표시됩니다.

![Bandwidth Utilization Analyzer에 수집된 알림 로그](images/JJ945604.eda91da8-3285-4eab-8ccb-c6d89c8cc221(OCS.15).jpg "Bandwidth Utilization Analyzer에 수집된 알림 로그")

**OK(확인)**를 클릭하면 BandwidthUtilizationAnalyzer.xlsm이 자동으로 시작됩니다. 메시지 상자의 지침을 따릅니다. 자세한 내용은 다음 섹션의 **BandwidthUtilizationAnalyzer.xlsm 사용**을 참고하세요.


**BandwidthUtilizationAnalyzer.xlsm 사용**

1.  BandwidthUtilizationAnalyzer.xlsm이 자동으로 시작되면 아래와 같이 **Refresh(새로 고침)**를 클릭합니다.
    
    ![BandwidthUtilizationAnalyzer.xlsm](images/JJ945604.c4e675b9-1671-400e-a712-6db82d731b39(OCS.15).jpg "BandwidthUtilizationAnalyzer.xlsm")

2.  파일 폴더가 열리면 아래와 같이 메시지 상자의 지정된 위치에서 consolidated.csv를 선택합니다. 해당 위치는 **C:\\Temp**입니다.
    
    ![BandwidthUtilizationAnalyzer의 폴더 열기.](images/JJ945604.601cc572-cee9-45fb-9ed1-c4b96a2fa21e(OCS.15).jpg "BandwidthUtilizationAnalyzer의 폴더 열기.")

3.  **Import(가져오기)**를 클릭합니다.

4.  그래픽 그림은 자동으로 생성되며, 백그라운드 작업 포인터가 사라지면 사용할 수 있습니다.
    
    ![보고서 보기의 필터 적용.](images/JJ945604.1416468e-e3ab-478e-b569-e42ba9c27a17(OCS.15).jpg "보고서 보기의 필터 적용.")

## 보고서 보기에 필터 적용

아래와 같이 보고서 보기에 적용할 수 있는 필터를 다음에서 설명합니다.

![보고서 보기의 필터 적용.](images/JJ945604.1416468e-e3ab-478e-b569-e42ba9c27a17(OCS.15).jpg "보고서 보기의 필터 적용.")

1.  **Name(이름)** WAN 링크를 기준으로 필터링합니다(필터는 그래프 오른쪽에 있음). 접두사는 다음 링크 유형을 나타냅니다. 파란색 세로 상자를 참고하세요.
    
      - **S Site(S 사이트)** 네트워크 사이트에서 네트워크 지역으로의 WAN 링크
    
      - **IS Inter-Site(IS 사이트 간)** 두 네트워크 사이트 사이의 WAN 링크
    
      - **R Inter-Region(R 영역 간)** 두 네트워크 지역 사이의 WAN 링크

2.  **Exceeded limit(제한 초과)** 대역폭 사용량이 대역폭 용량을 초과하는 WAN 링크를 기준으로 필터링합니다.

3.  **Critical levels(위험 수준)** 대역폭 사용량이 대역폭 용량의 90%에 도달했거나 초과한 WAN 링크를 기준으로 필터링합니다.

4.  **Under-utilized(낮은 활용도)** 대역폭 사용량이 대역폭 용량의 25% 미만인 WAN 링크를 기준으로 필터링합니다.

5.  **Link type(링크 유형)** 다음 WAN 링크 유형을 기준으로 필터링합니다.
    
      - **Network site(네트워크 사이트)** 유형
    
      - **Inter-site(사이트 간)** 유형
    
      - **Inter-Region link(영역 간 링크)** 유형

6.  **Region(영역)** 네트워크 지역을 기준으로 필터링합니다.

다음 그림은 앞에서 설명한 필터를 보여 줍니다.

**Name(이름)**을 기준으로 필터링. 그래프에 표시할 링크 목록을 선택합니다.

![BandwidthUtilizationAnalyzer의 이름을 기준으로 필터링.](images/JJ945604.002b7c8e-f0da-48ce-9e1a-5c34d2cab063(OCS.15).jpg "BandwidthUtilizationAnalyzer의 이름을 기준으로 필터링.")

**Exceeded limit(제한 초과)**를 기준으로 필터링. **True**를 선택하여 필터를 적용합니다.

![Exceeded Limit(제한 초과)를 기준으로 필터링.](images/JJ945604.5946c95e-76ce-46ca-8f3e-a79be1e5c527(OCS.15).jpg "Exceeded Limit(제한 초과)를 기준으로 필터링.")

**Critical levels(위험 수준)**를 기준으로 필터링. **True**를 선택하여 필터를 적용합니다.

![Critical Levels(위험 수준)를 기준으로 필터링.](images/JJ945604.60771a52-d8ba-4cb9-a02d-d6c888cb5505(OCS.15).jpg "Critical Levels(위험 수준)를 기준으로 필터링.")

**Under-utilized(낮은 활용도)**를 기준으로 필터링. **True**를 선택하여 필터를 적용합니다.

![Under Utilized(낮은 활용도)를 기준으로 필터링.](images/JJ945604.95a2bf01-5aba-4927-af47-1ad3c459d791(OCS.15).jpg "Under Utilized(낮은 활용도)를 기준으로 필터링.")

**Link type(링크 유형)**를 기준으로 필터링. 표시할 유형을 선택합니다.

![Link Type(링크 유형)을 기준으로 필터링.](images/JJ945604.08757949-06bd-4cf3-809f-d81fd23a6639(OCS.15).jpg "Link Type(링크 유형)을 기준으로 필터링.")

**Region(영역)**별 필터. 해당 영역의 링크를 표시할 영역 목록을 선택합니다.

![Region(영역)을 기준으로 필터링.](images/JJ945604.5de4cec4-6c09-48bb-98c7-b56f7bdb3d5a(OCS.15).jpg "Region(영역)을 기준으로 필터링.")

## 요구 사항

  - NET Framework 3.5

  - Microsoft Excel 2010 또는 Excel 2007

## 요약

Bandwidth Utilization Analyzer는 네트워크를 통한 UC 트래픽의 오디오 대역폭 사용량을 표시하는 데 사용됩니다. 이 도구는 네트워크 상의 비디오 대역폭 사용량을 보고하는 데도 사용됩니다.

## Call Parkometer

Call Parkometer는 통화 대기 번호 데이터베이스에 쉽게 액세스할 수 있도록 하는 명령줄 응용 프로그램입니다.

## 설명

Call Parkometer는 현재 대기된 통화를 추적하는 도구입니다. 또한 이 도구는 파킹된 통화 번호 및 CPS(통화 대기 서버) 사용에 대한 통계를 수집합니다. 이 명령줄 도구는 로컬 또는 원격으로 연결된 컴퓨터의 CPS 파킹된 통화 번호 SQL Server 데이터베이스에 대한 읽기 및 쓰기 권한을 제공합니다.

모든 옵션은 함께 사용할 수 없습니다. 명령줄 구문은 다음과 같습니다.

  - **–o** 매개 변수 - 이 풀에 대해 구성된 모든 파킹된 통화 번호 범위를 표시합니다.

  - **–n** 매개 변수 - 이 풀에서 현재 사용된 모든 파킹된 통화 번호를 표시합니다. 표시되는 정보는 다음과 같습니다.
    
      - 대기자 및 대기 요청자의 SIP URI(Uniform Resource Identifier)
    
      - 통화가 대기된 CPS의 호스트 이름
    
      - 통화가 대기된 시점의 타임스탬프

  - **–f** 매개 변수 - 풀에서 현재 사용 가능한 파킹된 통화 번호 수를 표시합니다.

  - **–r \<n\>** 매개 변수 - 마지막으로 대기된 \<n\>개의 통화를 표시합니다. 표시되는 정보는 다음과 같습니다.
    
      - 대기자 SIP URI
    
      - 대기 요청자 SIP URI
    
      - 통화가 대기된 CPS의 호스트 이름
    
      - 통화가 회수되거나 끊어진 시점의 타임스탬프

  - **-t\<n\>** 매개 변수 - 할당된 파킹된 통화 번호의 무작위성을 표시하기 위해 데이터베이스에서 파킹된 통화 번호 예약을 테스트합니다.

## 출력

명령 프롬프트에 지정된 입력 매개 변수에 따라 Call Parkometer에서 다음 출력을 표시합니다.

  - 이 풀에 대해 구성된 모든 파킹된 통화 번호 범위

  - 현재 대기된 통화

  - 사용 가능한 파킹된 통화 번호 수

  - 최근에 대기된 통화

  - 파킹된 통화 번호 값의 균일성 및 무작위성을 테스트하기 위해 예약된 파킹된 통화 번호

## 용도

CPS 도구의 용도는 CPS 데이터베이스에 대한 명령줄 액세스 권한을 제공하는 것입니다. 관리자는 CPS 사용 현황을 보고 풀에 할당된 파킹된 통화 번호 수를 확인할 수 있습니다.

## 요구 사항

이 도구가 CPS를 실행하는 컴퓨터와 동일한 컴퓨터에서 실행되는 경우에는 요구 사항이 없습니다. 원격 컴퓨터에서 이 도구가 실행되는 경우에는 Lync Server 2013에서 사용하는 SQL Server 데이터베이스가 원격 액세스를 허용하도록 구성되어야 합니다. Call Parkometer는 풀의 SQL Server에 연결하기 위해 SQL Server 데이터베이스 연결 문자열을 사용하여 구성해야 합니다. 이 SQL Server 데이터베이스 연결 문자열은 구성 파일인 **parkometer.exe.config**에서 정의됩니다. 이 파일은 parkometer.exe가 위치한 디렉터리와 동일한 디렉터리에 위치해야 합니다. 다음 XML 파일은 parkometer.exe.config의 예입니다. 구성해야 하는 매개 변수는 사용자 이름(예: mydomain\\Administrator), 암호(예: mypassword), 호스트 이름(예: myserver)입니다.
```XML
    <?xml version="1.0" encoding="utf-8" ?>
    <configuration>
      <appSettings>
       <add key="SQL" value="server=myserver\RTC;
    database=cpsdyn;
    User Id=mydomain\Administrator;
    Password=mypassword.;
    Integrated Security=false;"/>
      </appSettings>
    </configuration>
```
## 예제

배포된 파킹된 통화 번호 범위: –o 매개 변수는 아래와 같이 이 풀에 대해 구성된 모든 파킹된 통화 번호 범위를 표시합니다.

![Call Parkometer의 통화 번호 범위.](images/JJ945604.9ede64cb-29d9-4782-a34b-b76c42fbdcad(OCS.15).jpg "Call Parkometer의 통화 번호 범위.")

현재 대기된 통화: –n 매개 변수는 아래와 같이 이 풀에서 현재 사용된 모든 파킹된 통화 번호를 표시합니다.

![Call Parkometer의 현재 대기 중인 통화.](images/JJ945604.07a7eec4-7999-4c92-93f0-95525b244b4c(OCS.15).jpg "Call Parkometer의 현재 대기 중인 통화.")

사용 가능한 파킹된 통화 번호 수: –f 매개 변수는 아래와 같이 현재 사용 가능한 파킹된 통화 번호 수를 표시합니다.

![Call Parkometer의 사용 가능한 통화 번호.](images/JJ945604.ecc1d621-0ca0-4ecf-a579-08b41c6f08ed(OCS.15).jpg "Call Parkometer의 사용 가능한 통화 번호.")

최근에 대기된 통화: –r \<n\> 매개 변수는 아래와 같이 마지막으로 대기된 \<n\>개의 통화를 표시합니다.

![Call Parkometer의 최근 대기 통화.](images/JJ945604.1c5eb27d-faa1-491b-b4aa-b484255c3353(OCS.15).jpg "Call Parkometer의 최근 대기 통화.")

파킹된 통화 번호 예약 테스트: –t \<n\> 매개 변수는 아래와 같이 데이터베이스에서 파킹된 통화 번호 예약을 테스트합니다.

![Call Parkometer의 테스트 통화 번호 예약.](images/JJ945604.84c9b69e-7af0-4224-8711-a43a28f08691(OCS.15).jpg "Call Parkometer의 테스트 통화 번호 예약.")

## 요약

Call Parkometer는 통화 대기 서버에 대한 자세한 정보를 제공하는 명령줄 도구입니다.

## CleanupStorageServiceData

CleanupStorageServiceData 리소스 키트 도구를 사용하면 LYSS(Lync Server 저장소 서비스)에서 사용하는 데이터베이스에서 분리된 데이터를 삭제할 수 있습니다. 저장소 서비스의 한 가지 기능은 Lync Server와 다양한 백 엔드 데이터 저장소 끝점(예: SQL Server 및 Exchange) 간의 통신을 버퍼링하는 것입니다.

## 설명

LYSS는 고가용성 지원을 위해 풀에 있는 여러 프런트 엔드 서버의 데이터 복사본을 임시로 허용 및 저장하고, 해당 데이터가 최종 장기 저장 위치로 배달되면 제거합니다. 일반적인 작업 도중 서버가 충돌하거나 처리 문제가 발생하면 일부 데이터가 제대로 정리되지 않는 특수한 발생할 수 있습니다. 이러한 데이터가 해를 입히지는 않지만 제한된 처리 리소스를 소모합니다. 대부분의 일반적인 필수 데이터 유지 관리는 자동으로 이루어지지만, 자동 제거가 가능하지 않은 경우에는 이 도구를 사용하여 그러한 분리된 데이터를 안전하게 식별 및 제거할 수 있습니다. 관리자에게 풀의 로컬 LYSS 데이터베이스에서 불필요한 데이터를 제거하도록 요청하는 상태 모니터링 SCOM(System Center Operations Manager) 알림이 표시되는 경우 이 도구의 사용법이 표시됩니다. 알림이 트리거된 프런트 엔드의 이벤트 로그에 해당 이벤트가 있습니다. 이벤트 세부 정보에는 프런트 엔드에 포함된 분리된 데이터량에 대한 정보가 포함되며 해당 데이터가 미리 지정된 특정 임계값을 초과하는 경우에 표시됩니다.

## 요구 사항

Lync Server 2013, 리소스 키트 도구를 설치합니다. 이 도구는 Lync Server 및 Lync Server 2013 관리 셸이 설치되어 있는 도메인에 가입된 컴퓨터에서 실행되며, 관리 셸에서 cmdlet을 사용하여 풀의 모든 프런트 엔드 서버를 식별합니다. 두 번째로, 이 도구는 **RtcLocal** 데이터베이스가 설치된 풀의 컴퓨터에서 실행해야 합니다. CleanupStorageServiceData 도구는 이 데이터베이스를 사용하여 Lync Server 라우팅 서비스와 통신하는 데 필요한 연결 세부 정보에 액세스할 수 있습니다. 마지막으로, 도구를 호출할 계정 또는 자격 증명에 출력 로그를 기록하려는 파일 공유에 대한 읽기/쓰기 권한이 있어야 합니다. 또한 이 도구를 사용하려면 풀이 안정된 상태에 있어야 합니다. 즉 기본적으로 모든 프런트 엔드 서버가 사용할 수 있는 상태여야 하고, SQL Server LYNCLOCAL 인스턴스 및 LYSS 데이터베이스에 연결할 수 있어야 하며, 각 라우팅 그룹에 기본 프런트 엔드 서버 1개와 보조 프런트 엔드 서버 2개의 전체 집합이 있어야 합니다.

## 예제

C:\\Program Files\\Microsoft Lync Server 2013\\ResKit\\StorageService\> ImportStorageServiceData.exe
```C++
    Description:
    This tool will remove orphaned data from the Storage Service database
    for a pool. You are required to run this tool on a machine inside the
    pool which has the Lync Server Management Shell installed and has RtcLocal database installed.
    Usage: Default behavior is to clean up orphaned data from the all the 
           Storage Service databases in the current pool.
    Additional Options:
    -Verbose    : Turn verbose output on.
    -LogPath    : The UNC path to which to write the log.
    ------------------------------------------------------------------------------
    Please wait while we initialize...
    Found 4 front end servers
    Replica Instances for LYSS Service
    Address: server2.vdomain.com - Primaries: 7 Secondaries: 14
    Address: server.vdomain.com - Primaries: 7 Secondaries: 14
    Address: server1.vdomain.com - Primaries: 7 Secondaries: 14
    Address: server3.vdomain.com - Primaries: 7 Secondaries: 14
    Primary Total Count = 28, Secondary Total Count = 56
    Finding and removing orphaned data for 28 routing groups
    Removing 1 stale groups from FE server.vdomain.com
    No stale routing groups detected on FE server2.vdomain.com
    No stale routing groups detected on FE server1.vdomain.com
    No stale routing groups detected on FE server3.vdomain.com
    Searching for stale queue items
    Removed 20 stale queue items for routing group 17D5435AE40259F7BBDF1866776386E4
    No stale queue items found for routing group 1975349662315F90B119DACB4F2AE3AD
    No stale queue items found for routing group 1A23E3D58BDB5A458A0B73F34AB7ACBE
    No stale queue items found for routing group 1AC91E3A1029535A80123121989CEADC
    No stale queue items found for routing group 3313935458E35B9B9759E08A15D251E6
    No stale queue items found for routing group 39BB0035B06B5427873FC6099720462A
    No stale queue items found for routing group 40721948E7B55CE893A53E911F76D185
    No stale queue items found for routing group 4501E04EAE4856059346949FF817C220
    No stale queue items found for routing group 4D833C98801F546F8E45E417EE028E2E
    No stale queue items found for routing group 5AD77443AD955A22A876749BE66D5317
    No stale queue items found for routing group 69844A271E6C5633A1F2B46A42287DD6
    No stale queue items found for routing group 69DA3BE407A95C7284EB4B1337718C93
    No stale queue items found for routing group 8437358AB34A5CC8967D5EF39494AB8D
    No stale queue items found for routing group 8ED455B1789655359816E1C5BF4C430F
    No stale queue items found for routing group 904F6C9B8AC951AE8B3C86684D3832E4
    No stale queue items found for routing group 90AAB3AE9A1950E0ADE7809A27021D63
    No stale queue items found for routing group 944F5724C65C5F93900DC1C8C898B102
    No stale queue items found for routing group 9E8A2630250C51769E39F63F0FB552BA
    No stale queue items found for routing group A11E27AE439A582288D4657EDA86B565
    No stale queue items found for routing group A9B10C76E764556FAEA3E47301EDF518
    No stale queue items found for routing group AEA2699E74ED59848ACEA7896699430D
    No stale queue items found for routing group B269961603E75065AFDA4F4F006DA5E4
    No stale queue items found for routing group BB873D9A3DA959DAB2FD743E5AA619F7
    No stale queue items found for routing group BCC6A48FBA2454B79B9EDB276657A404
    No stale queue items found for routing group C8EF4805722B5F6C876EBC0440B420FD
    No stale queue items found for routing group CA38EBDAC4845489ACE208C2240E4056
    No stale queue items found for routing group F5921887DB025C5F908CE42DB7F1AEE8
    No stale queue items found for routing group F9E606A825395422B3BF7A01ECBB7B1F
    Writing log: M:\Dev\Server\ResKit\StorageService\CleanupStorageServiceData.Log_20121009_151040
    Tool has finished execution.  Errors encountered: 0
    C:\Program Files\Microsoft Lync Server 2013\ResKit\StorageService>
```
## DBAnalyze

## 설명

DBAnalyze는 관리자가 Lync Server 2013 데이터베이스에 대한 분석 보고서를 수집할 수 있도록 돕는 명령줄 도구입니다. DBAnalyze에는 다음과 같은 모드(진단, 사용자 데이터, 전화 회의, MCU, 디스크 조각화)가 있습니다.

  - **진단 모드**   테이블(레코드 수, 조각화, 데이터 크기, 인덱스 크기), 데이터 및 로그 파일 크기, 마지막으로 백업한 시간, Microsoft Office Communications Server를 실행 중인 서버의 대화 상대 분포, 사용 권한의 평균 수, 대화 상대, 컨테이너, 구독, 게시, 사용자당 끝점, 잘못 이동된 사용자, 라우팅되지 않는 사용자, 사용자별로 주최한 전화 회의의 평균 수, 예약된 전화 회의, 활성 전화 회의, 데이터베이스 버전에 대한 정보를 포함하는 보고서를 생성합니다.
    

    > [!NOTE]
    > 진단 모드로 실행하면 서버 성능에 영향을 줄 수 있습니다.



  - **사용자 데이터 모드**  특정 사용자 또는 해당 사용자가 자신의 대화 상대 및 사용 권한 목록에 있는 사용자의 대화 상대, 컨테이너, 구독, 게시, 사용 권한, 대화 상대 그룹 데이터를 보고합니다. 또한 이 모드에서는 사용자가 주최하거나 초대된 전화 회의에 대한 요약 데이터를 보고합니다.

  - **전화 회의 모드**   전화 회의가 예약된 모든 시간 세부 정보, 초대 대상자 목록, 전화 회의에 허용된 미디어 유형 목록, 활성 MCU(Multipoint Control Unit), 활성 참가자 목록, 각 참가자의 신호 상태를 비롯한 특정 전화 회의에 대한 자세한 데이터를 보고합니다.

  - **모임 ID 디코딩**   **/pstnid** 스위치로 지정되었지만 자세한 정보를 위해 백 엔드에 연결되지 않은 PSTN(공중 전화망) 모임 ID를 디코딩합니다.

  - **전화 회의 확인**   **/pstnid** 스위치로 지정된 PSTN 모임 ID를 디코딩하고 해당 ID가 나타내는 전화 회의에 대한 정보를 표시합니다.

  - **MCU 모드**  풀의 각 MCU에 대한 ID, 미디어 유형, URL, 하트비트 상태, 전화 회의 부하, 참가자 부하를 보고합니다.

  - **디스크 조각화 모드**  모든 디스크의 조각화 상태를 표시합니다.

이 도구는 다양한 문제를 진단하거나 관리자의 용량 계획을 돕는 데 사용됩니다. 예를 들어 서버 A에 있는 대부분의 사용자가 자신의 대화 상대로 서버 B에 있는 사용자를 선택하는 경우, 관리자는 서버 간 트래픽을 줄이기 위해 서버 A의 사용자를 서버 B로 이동할 수 있습니다.

## 출력

이 도구는 Lync Server 2013 데이터베이스에 대해 미리 정의된 보고서를 출력합니다. **경로:** %ProgramFiles%\\Microsoft Lync Server 2013\\Reskit

## 용도

Dbanalyze.exe를 설치하려면 로컬 폴더로 복사한 다음 도구를 실행합니다. 도구를 사용하려면 명령줄에서 다음 명령을 실행합니다. `dbanalyze.exe [/v] [/report:value] [/sqlserver:value] [/user:user@domain.com] [/conf:value][/pstnid:Value] [/maxcontacts:value]` 아래에 명령줄 옵션에 대한 설명이 나와 있습니다.

![Dbanalyze.exe의 명령줄 옵션.](images/JJ945604.22bf3432-af6d-495b-8f48-d94c5d259523(OCS.15).jpg "Dbanalyze.exe의 명령줄 옵션.")

## 요구 사항

**컴퓨터** DBAnalyze는 Lync Server 2013이 설치된 도메인에 가입된 컴퓨터에서만 실행됩니다.

**네트워크** 컴퓨터를 백 엔드 데이터베이스에 연결할 수 있어야 합니다.

**소프트웨어** DBAnalyze를 실행하기 전에 Lync Server 2013 소프트웨어 구성 요소가 설치되어 있어야 합니다.

**사용자** 아래 표에는 Lync Server 2013 데이터베이스에 액세스하는 데 필요한 권한을 가진 관리자가 표시되어 있습니다.

![Dbanalyze.exe의 사용 권한 테이블.](images/JJ945604.b8931e9e-834e-4dec-8a84-2fc47d1613e9(OCS.15).jpg "Dbanalyze.exe의 사용 권한 테이블.")


> [!NOTE]
> <STRONG>/report:disk</STRONG> 모드에는 로컬 관리자 계정이 필요합니다.



## 예제

다음은 유효한 Dbanalyze.exe 명령의 예입니다.
```C++
    dbanalyze.exe /report:diag
    dbanalyze.exe /report:user /user:usera@domainb.com
    dbanalyze.exe /report:conf /user:bob@example.com /conf:1W9J71SKSX2X
    dbanalyze.exe /report:resolve /pstnid:12345
    dbanalyze.exe /report:mcus
    dbanalyze.exe /report:disk
```
## 요약

DBAnalyzer를 사용하면 관리자가 Lync Server 2013 데이터베이스를 빠르고 쉽게 분석할 수 있습니다.

## ImportStorageServiceData

ImportStorageServiceData 리소스 키트 도구를 사용하면 LYSS(Lync 저장소 서비스)에서 저장소 서비스로 플러시된 큐 및 끝점 데이터를 다시 가져올 수 있습니다.

## 설명

큐 항목 상태 또는 데이터베이스 크기에 따라 저장소 서비스에서 데이터가 자동으로(정기적으로) 플러시되었을 수 있습니다. 이는 풀 장애 조치(failover) cmdlet 또는 StorageServiceFullFlush cmdlet(풀 장애 조치 cmdlet이 호출)을 수동으로 호출했기 때문일 수 있습니다. 프런트 엔드의 LYSS(Lync 저장소 서비스) 데이터베이스 크기가 일반적인 수준 이상인 경우에는 데이터를 다시 가져올 수 없어야 합니다. 데이터를 다시 가져오는 경우 이렇게 더 많은 데이터를 다시 내보내야 할 수 있기 때문입니다. 또한 오류를 발생시켜 저장소 서비스 큐가 늘어나게 한 원인이 되는 모든 문제(예: Exchange 끝점 오류, 네트워크 문제 또는 기타 문제)를 먼저 해결해야 합니다.

**시나리오 1:** 풀 장애 조치(failover) 도중 각 프런트 엔드의 저장소 서비스에서 파일이 플러시될 수 있습니다. 장애 조치(failover)가 완료된 후 도구를 실행하여 데이터를 다시 가져와야 합니다.

**시나리오 2:** 데이터가 매일 또는 저장소 서비스 데이터베이스가 특정 크기 임계값(예: 전체 60%, 80%, 90%)을 초과하는 경우에 자동으로 플러시됩니다. 관리자는 이렇게 자동으로 플러시된 데이터를 정기적으로 다시 가져와야 합니다. 이와 같은 상황에서 모니터링 SCOM 팩이 배포되지 않은 경우, 저장소 서비스에서 플러시된 데이터와 관련된 Lync Server 저장소 서비스의 이벤트가 있습니다. 이벤트 ID 32075(전체 플러시 작업 시작), 32076(전체 플러시 완료), 32082(유지 관리 수준 플러시 시작), 32083(유지 관리 수준 플러시 완료), 32089(데이터베이스 가득 참으로 인한 플러시 발생). 이러한 이벤트 ID는 RTM 릴리스에 해당합니다. 관리자에게 이러한 이벤트가 표시되면 플러시된 파일이 있는 것입니다. 이 도구를 사용하여 정기적으로(예: 일주일에 한 번) 이러한 데이터를 다시 가져와야 합니다.

온라인 서비스 릴리스의 경우 Lync Server에 대한 상태 모니터링 SCOM 팩이 배포되면 관리자가 플러시된 데이터를 저장소 서비스로 다시 가져오도록 요청하는 새 알림이 표시될 수 있습니다. 알림이 트리거된 프런트 엔드 서버의 이벤트 로그에 해당 이벤트가 있습니다. 이벤트는 플러시된 데이터가 있는 상위 경로에 대한 설명을 제공합니다. 알림 조건은 특정 상위 경로에 최소 Y일이 지난 X개 이상의 파일이 있는 경우이며 X와 Y는 저장소 서비스에 설정되어 있지만 APPCONFIG 파일을 변경하여 재정의할 수 있습니다. 아래에는 상태 알림을 트리거할 수 있고 상위 경로가 다른 두 가지 이벤트의 예가 나와 있습니다. 하나는 웹 서비스 파일 공유에 있고 다른 하나는 각 프런트 엔드의 로컬 응용 프로그램 데이터 디렉터리(예: c:\\ProgramData\\Microsoft\\Lync Server\\StorageService)에 있습니다. 그런 다음 관리자가 이 리소스 키트 도구를 실행합니다.

이 도구는 데이터가 도구를 실행하는 프런트 엔드에 속하지 않은 경우, 도구를 실행 중인 프런트 엔드와 다른 프런트 엔드의 CPU 및 IO 부하를 늘립니다. 피크 시간을 피하는 등 프런트 엔드의 CPU 및 IO 부하가 심하지 않은 시간에 이 도구를 실행하는 것이 좋습니다. 두 번째로, 이 도구는 한 데이터 파일을 가져오는 데 2-3분이 걸릴 수 있습니다. 도구 실행 시간을 예측할 때 이 점에 유의합니다. 도구에서 생성한 자세한 정보 로그 파일은 파일 저장소에 기본적으로 표시됩니다. 로그 파일은 수십 MB 이상일 수 있으므로 보고된 오류가 없으면 삭제합니다.

![샘플 저장소 서버 이벤트 로그 이벤트.](images/JJ945604.3a903ef7-ea8a-4606-8229-a3e32f13af3a(OCS.15).jpg "샘플 저장소 서버 이벤트 로그 이벤트.")

## 요구 사항

Lync Server 2013, 리소스 키트 도구를 설치합니다. 이 도구는 Lync Server 및 Lync Server 관리 셸이 설치된 도메인에 가입된 컴퓨터에서 실행되며, 관리 셸에서 cmdlet을 사용하여 풀의 모든 프런트 엔드 서버를 식별합니다. 두 번째로, 이 도구는 **RtcLocal** 데이터베이스가 설치된 컴퓨터의 풀에서 실행해야 합니다. 도구는 이 데이터베이스를 사용하여 풀의 WEBSERVICE 파일 공유 위치를 검색합니다. 또한 도구를 사용하기 전에 각 프런트 엔드 서버는 도구를 실행한 컴퓨터와 각 프런트 엔드 서버에서 **Enable-PSRemoting**을 사용하여 Windows PowerShell 원격을 사용하도록 설정해야 합니다. 그렇지 않으면 이 도구의 원격 Windows PowerShell 명령이 실패합니다. 완료된 후에는 Windows PowerShell 원격이 풀의 모든 프런트 엔드 서버에서 해제될 수 있습니다. 마지막으로, 도구를 호출할 계정 또는 자격 증명에 도구를 실행 중인 풀의 웹 서비스 파일 공유에 대한 읽기/쓰기 권한이 있어야 합니다. 그렇지 않으면 도구가 IP 사용 권한 오류로 실패하게 됩니다.


> [!NOTE]
> Windows Server 2012에서는 기본적으로 Windows PowerShell원격을 사용하도록 설정되어 있지만 Windows Server 2008 운영 체제에서는 그렇지 않습니다.



## 예제
```C++
    >  C:\StorageService>ImportStorageServiceData.exe
    Description:
    This tool will re-import Storage Service (LYSS) flushed queue data back in.  For a pool: you are required to run this tool on a machine inside the pool which has the Lync Server Management Shell installed.  Additionally, all front end machines need to have Windows Powershell Remoting enabled before executing this tool by executing Enable-PSRemoting.  Also, please ensure that all Storage Service instance DB Size are at the 'Normal' level (verify this by viewing Eventlog events). Otherwise re-importing may cause data to be flushed out again if any Storage Service instance DB size level goes above 'Normal'.
    Usage: Default behavior is to Import data from web service file share as well as any files on all Front End machines in pool.
    Additional Options:
    -Verbose                    : Turn verbose output on.
    
    -StorageServiceHostName     : Host Name of Storage Service WCF endpoint.  ( Default=localhost netnamedpipe binding. )
                                        
    -FileSharePath              : Import only all data from just under the UNC path specified.
    
    ActivityID: cc3b62ff-bb66-4e61-a6e2-96cb3626315c. <-- Use this to correlate with StorageService trace logs if troubleshooting.
    Type Server name (TCP binding) or press <enter> for localhost (NamePipe binding):
    Using NetNamedPipeBinding...
    OnTopologyChanged Event received
    Web Service File Share: \\dc.vdomain.com\OcsFileStore\co1-WebServices-1\StorageService
    
    Front Ends:
    server.vdomain.com
    server2.vdomain.com
    server1.vdomain.com
    server3.vdomain.com
    Looking under directory: \\dc.vdomain.com\OcsFileStore\co1-WebServices-1\StorageService for exported data.
    # Files found: 8
    Starting Import for file:\\dc.vdomain.com\OcsFileStore\co1-WebServices-1\StorageService\DataExport\2
    0120910\SERVER.vdomain.com\944f5724c65c5f93900dc1c8c898b102__0.xml
    Items deserialized: 20
    
    All items in file were enqueued successfully, will try to delete file: \\dc.vdomain.com\OcsFileStore\co1-WebServices-1\StorageService\DataExport\20120910\SERVER.vdomain.com\944f5724c65c5f93900dc1c8c898b102__0.xml
    
    All items in file failed to enqueue so file will not be deleted.  File path: \\dc.vdomain.com\OcsFileStore\co1-WebServices-1\StorageService\DataExport\20120910\SERVER.vdomain.com\944f5724c65c5f93900dc1c8c898b102__0.xml
    
    Summary for file \\dc.vdomain.com\OcsFileStore\co1-WebServices-1\StorageService\DataExport\20120910\SERVER.vdomain.com\944f5724c65c5f93900dc1c8c898b102__0.xml: succeeded: 20, failed: 0
    
    Starting Import for file:\\dc.vdomain.com\OcsFileStore\co1-WebServices-1\StorageService\DataExport\20120910\SERVER1.vdomain.com\17d5435ae40259f7bbdf1866776386e4__0.xml
    Items deserialized: 20
    
    [cc3b62ff-bb66-4e61-a6e2-96cb3626315c] Send EnqueueMessages to redirected, targetServer=server1.vdomain.com, queueItems=20
    
    All items in file were enqueued successfully, will try to delete file: \\dc.vdomain.com\OcsFileStore\co1-WebServices-1\StorageService\DataExport\20120910\SERVER1.vdomain.com\17d5435ae40259f7bbdf1866776386e4__0.xml
    
    All items in file failed to enqueue so file will not be deleted.  File path: \\dc.vdomain.com\OcsFileStore\co1-WebServices-1\StorageService\DataExport\20120910\SERVER1.vdomain.com\17d5435ae40259f7bbdf1866776386e4__0.xml
    
    Summary for file \\dc.vdomain.com\OcsFileStore\co1-WebServices-1\StorageService\DataExport\20120910\
    SERVER1.vdomain.com\17d5435ae40259f7bbdf1866776386e4__0.xml: succeeded: 20, failed: 0
    
    Starting Import for file:\\dc.vdomain.com\OcsFileStore\co1-WebServices-1\StorageService\DataExport\20120910\SERVER1.vdomain.com\904f6c9b8ac951ae8b3c86684d3832e4__0.xml
    
    Items deserialized: 20
    [cc3b62ff-bb66-4e61-a6e2-96cb3626315c] Send EnqueueMessages to redirected, targetServer=server1.vdomain.com, queueItems=20
    
    All items in file were enqueued successfully, will try to delete file: \\dc.vdomain.com\OcsFileStore
    \co1-WebServices-1\StorageService\DataExport\20120910\SERVER1.vdomain.com\904f6c9b8ac951ae8b3c86684d
    3832e4__0.xml
    
    All items in file failed to enqueue so file will not be deleted.  File path: \\dc.vdomain.com\OcsFil
    eStore\co1-WebServices-1\StorageService\DataExport\20120910\SERVER1.vdomain.com\904f6c9b8ac951ae8b3c
    86684d3832e4__0.xml
    
    
    Summary for file \\dc.vdomain.com\OcsFileStore\co1-WebServices-1\StorageService\DataExport\20120910\
    SERVER1.vdomain.com\904f6c9b8ac951ae8b3c86684d3832e4__0.xml: succeeded: 20, failed: 0
    
    Starting Import for file:\\dc.vdomain.com\OcsFileStore\co1-WebServices-1\StorageService\DataExport\2
    0120910\SERVER2.vdomain.com\69844a271e6c5633a1f2b46a42287dd6__0.xml
    
    Items deserialized: 20
    
    [cc3b62ff-bb66-4e61-a6e2-96cb3626315c] Send EnqueueMessages to redirected, targetServer=server2.vdom
    ain.com, queueItems=20
    
    All items in file were enqueued successfully, will try to delete file: \\dc.vdomain.com\OcsFileStore
    \co1-WebServices-1\StorageService\DataExport\20120910\SERVER2.vdomain.com\69844a271e6c5633a1f2b46a42
    287dd6__0.xml
    
    All items in file failed to enqueue so file will not be deleted.  File path: \\dc.vdomain.com\OcsFil
    eStore\co1-WebServices-1\StorageService\DataExport\20120910\SERVER2.vdomain.com\69844a271e6c5633a1f2
    b46a42287dd6__0.xml
    
    Summary for file \\dc.vdomain.com\OcsFileStore\co1-WebServices-1\StorageService\DataExport\20120910\
    SERVER2.vdomain.com\69844a271e6c5633a1f2b46a42287dd6__0.xml: succeeded: 20, failed: 0
    
    Starting Import for file:\\dc.vdomain.com\OcsFileStore\co1-WebServices-1\StorageService\DataExport\2
    0120910\SERVER3.vdomain.com\3313935458e35b9b9759e08a15d251e6__0.xml
    
    Items deserialized: 20
    
    [cc3b62ff-bb66-4e61-a6e2-96cb3626315c] Send EnqueueMessages to redirected, targetServer=server3.vdom
    ain.com, queueItems=1
    
    All items in file were enqueued successfully, will try to delete file: \\dc.vdomain.com\OcsFileStore
    \co1-WebServices-1\StorageService\DataExport\20120910\SERVER3.vdomain.com\3313935458e35b9b9759e08a15
    d251e6__0.xml
    
    All items in file failed to enqueue so file will not be deleted.  File path: \\dc.vdomain.com\OcsFil
    eStore\co1-WebServices-1\StorageService\DataExport\20120910\SERVER3.vdomain.com\3313935458e35b9b9759
    e08a15d251e6__0.xml
    
    Summary for file \\dc.vdomain.com\OcsFileStore\co1-WebServices-1\StorageService\DataExport\20120910\
    SERVER3.vdomain.com\3313935458e35b9b9759e08a15d251e6__0.xml: succeeded: 20, failed: 0
    
    Starting Import for file:\\dc.vdomain.com\OcsFileStore\co1-WebServices-1\StorageService\DataExport\2
    0120910\SERVER3.vdomain.com\4501e04eae4856059346949ff817c220__0.xml
    Items deserialized: 20
    [cc3b62ff-bb66-4e61-a6e2-96cb3626315c] Send EnqueueMessages to redirected, targetServer=server3.vdom
    ain.com, queueItems=1
    All items in file were enqueued successfully, will try to delete file: \\dc.vdomain.com\OcsFileStore
    \co1-WebServices-1\StorageService\DataExport\20120910\SERVER3.vdomain.com\4501e04eae4856059346949ff8
    17c220__0.xml
    All items in file failed to enqueue so file will not be deleted.  File path: \\dc.vdomain.com\OcsFil
    eStore\co1-WebServices-1\StorageService\DataExport\20120910\SERVER3.vdomain.com\4501e04eae4856059346
    949ff817c220__0.xml
    
    Summary for file \\dc.vdomain.com\OcsFileStore\co1-WebServices-1\StorageService\DataExport\20120910\
    SERVER3.vdomain.com\4501e04eae4856059346949ff817c220__0.xml: succeeded: 20, failed: 0
    Starting Import for file:\\dc.vdomain.com\OcsFileStore\co1-WebServices-1\StorageService\DataExport\2
    0120910\SERVER3.vdomain.com\5ad77443ad955a22a876749be66d5317__0.xml
    
    Items deserialized: 20
    [cc3b62ff-bb66-4e61-a6e2-96cb3626315c] Send EnqueueMessages to redirected, targetServer=server3.vdom
    ain.com, queueItems=20
    All items in file were enqueued successfully, will try to delete file: \\dc.vdomain.com\OcsFileStore
    \co1-WebServices-1\StorageService\DataExport\20120910\SERVER3.vdomain.com\5ad77443ad955a22a876749be6
    6d5317__0.xml
    All items in file failed to enqueue so file will not be deleted.  File path: \\dc.vdomain.com\OcsFil
    eStore\co1-WebServices-1\StorageService\DataExport\20120910\SERVER3.vdomain.com\5ad77443ad955a22a876
    749be66d5317__0.xml
    Summary for file \\dc.vdomain.com\OcsFileStore\co1-WebServices-1\StorageService\DataExport\20120910\
    SERVER3.vdomain.com\5ad77443ad955a22a876749be66d5317__0.xml: succeeded: 20, failed: 0
    Starting Import for file:\\dc.vdomain.com\OcsFileStore\co1-WebServices-1\StorageService\DataExport\2
    0120910\SERVER3.vdomain.com\a11e27ae439a582288d4657eda86b565__0.xml
    Items deserialized: 20
    [cc3b62ff-bb66-4e61-a6e2-96cb3626315c] Send EnqueueMessages to redirected, targetServer=server3.vdom
    ain.com, queueItems=20
    All items in file were enqueued successfully, will try to delete file: \\dc.vdomain.com\OcsFileStore
    \co1-WebServices-1\StorageService\DataExport\20120910\SERVER3.vdomain.com\a11e27ae439a582288d4657eda
    86b565__0.xml
    All items in file failed to enqueue so file will not be deleted.  File path: \\dc.vdomain.com\OcsFil
    eStore\co1-WebServices-1\StorageService\DataExport\20120910\SERVER3.vdomain.com\a11e27ae439a582288d4
    657eda86b565__0.xml
    Summary for file \\dc.vdomain.com\OcsFileStore\co1-WebServices-1\StorageService\DataExport\20120910\
    SERVER3.vdomain.com\a11e27ae439a582288d4657eda86b565__0.xml: succeeded: 20, failed: 0
    All files have been imported into Storage Service for path: \\dc.vdomain.com\OcsFileStore\co1-WebSer
    vices-1\StorageService
    Importing files for: server.vdomain.com
    No files founds.
    Importing files for: server2.vdomain.com
    No files founds.
    Importing files for: server1.vdomain.com
    No files founds.
    Importing files for: server3.vdomain.com
    No files founds.
    Writing log: \\dc.vdomain.com\OcsFileStore\co1-WebServices-1\StorageService\ImportStorageServiceData
    Log20120910_1609SS
    Tool has finished execution.
    >  C:\StorageService>
```
## LCSSync

LCSSync 도구를 사용하여 다중 포리스트 환경에서 Lync Server 2013 통신 소프트웨어를 배포할 수 있습니다. 이 도구는 다른 사용자 포리스트의 사용자 및 그룹을 Active Directory 도메인 서비스 대화 상대 개체로 Lync Server 2013이 설치된 중앙 포리스트와 동기화하는 데 사용됩니다.

## 설명

LCSSync는 동기화된 중앙 포리스트의 Active Directory 도메인 서비스 대화 상대 개체를 사용하여 사용자가 Lync Server를 사용할 수 있도록 설정합니다. Single Sign-On을 제공하려면 기본 사용자 계정이 Lync Server 2013에 대한 중앙 포리스트의 Active Directory 도메인 서비스 대화 상대 개체에 매핑되어야 합니다. 이 도구를 사용하면 이러한 매핑을 수행할 수 있습니다. 이 도구는 Microsoft Identity Integration Server에서 관리 에이전트를 만들 수 있는 서식 파일을 제공합니다.

## 요약

LCSSync 도구를 사용하여 다중 포리스트 환경에서 Lync Server를 배포할 수 있습니다.

## LookupUserConsole

LookupUserConsole 도구는 특정 사용자에 대한 내부 Lync Server 라우팅 정보를 표시합니다. 이러한 정보는 Microsoft 지원 담당자가 배포 및 라우팅 문제를 진단하는 데 유용합니다.

## 설명

LookupUserConsole.exe를 실행하면 SIP 주소를 허용하는 명령 프롬프트가 열리고 이와 관련된 내부 Lync Server 라우팅 정보를 표시합니다. LookupUserConsole 도구를 종료하려면 **exit**를 입력합니다.

## 요구 사항

Lync Server 2013, 리소스 키트 도구를 설치합니다. 이 도구는 Lync Server가 설치된 도메인에 가입된 컴퓨터에서 실행됩니다.

## 예제

C:\\Program Files\\Microsoft Lync Server 2013\\ResKit\>LookupUserConsole.exe
```C++
    > sip:john.doe@vdomain.com
    
      Execution time (ms):                            171.094
      Exeuction result:                               Success
      SIP URI:                                        sip:john.doe@vdomain.com
      User info:
        SID:                                          S-1-5-21-2831376166-29632525...    Display name:                                     John Doe
        Grouping ID:                                  00000000-0000-0000-0000-...
        Line URI:                                     <null>
        Policy assignment:                            TenantId={00000000--0000-000....
        SIP enabled:                                  True
        UC enabled:                                   False
        Tenant ID:                                    00000000-0000-0000-0000-...  Cluster info:
        Active cluster:                               pool0.vdomain.com
        Backup registrar cluster:                     <null>
        Deployment location:                          <null>
        Home Front-End FQDN:                          SERVER.vdomain.com
        Primary Registrar cluster:                    pool0.vdomain.com
        Remote Director external SIP FQDN:            <null>
        Remote Director internal SIP FQDN:            <null>
        Remote Director Web FQDN:                     <null>
        Routing group ID:                             4501e04e-ae48-5605-9346...
        Service tag ID:                               1266953005
        User Front-End resolved:                      True
        User in local forest:                         True
        User in remote forest:                        False
        User in split domain:                         False
        User-Services cluster:                        pool0.vdomain.com
    
    > sip:nouser@vdomain.com
    
      Execution time (ms):                            948.7574
      Exeuction result:                               UserDoesNotExist
    
    > exit
```
## MsTurnPing

MSTurnPing 도구를 사용하면 Microsoft Lync Server 2013 통신 소프트웨어의 관리자가 토폴로지에서 오디오/비디오 에지 및 오디오/비디오 인증 서비스를 실행하는 서버와 대역폭 정책 서비스를 실행하는 서버의 상태를 확인할 수 있습니다.

## 설명

MSTurnPing 도구를 사용하면 Lync Server 2013 통신 소프트웨어의 관리자가 토폴로지에서 오디오/비디오 에지 및 오디오/비디오 인증 서비스를 실행하는 서버와 대역폭 정책 서비스를 실행하는 서버의 상태를 확인할 수 있습니다.

관리자는 이 도구를 사용하여 다음 테스트를 수행할 수 있습니다.

1.  A/V 에지 서버 테스트: 다음을 통해 토폴로지의 모든 A/V 에지 서버에 대한 테스트를 수행합니다.
    
      - Lync Server 오디오/비디오 인증 서비스가 시작되고 적절한 자격 증명을 발급할 수 있는지 확인합니다.
    
      - Lync Server 오디오/비디오 에지 서비스가 시작되고 리소스를 외부 에지에 성공적으로 할당할 수 있는지 확인합니다.

2.  대역폭 정책 서비스 테스트: 다음을 통해 토폴로지에서 대역폭 정책 서비스를 실행하는 모든 서버에 대한 테스트를 수행합니다.
    
      - Lync Server 대역폭 정책 서비스(인증)가 시작되고 적절한 자격 증명을 발급할 수 있는지 확인합니다.
    
      - Lync Server 대역폭 정책 서비스(핵심)가 시작되고 대역폭 검사를 성공적으로 수행할 수 있는지 확인합니다.

이 도구는 토폴로지에 속해 있으며 로컬 저장소가 설치된 컴퓨터에서 실행해야 합니다.

## 출력

이 도구는 각 작업의 결과를 출력합니다.

  - **AudioVideoEdgeServer** 테스트를 수행한 경우에는 다음을 출력합니다.
    
      - 토폴로지의 Lync Server 오디오/비디오 인증 서비스를 제공하는 컴퓨터의 테스트 결과
    
      - 토폴로지의 Lync Server 오디오/비디오 에지 서비스를 제공하는 컴퓨터의 테스트 결과

  - **BandwidthPolicyServer** 테스트를 수행한 경우에는 다음을 출력합니다.
    
      - 토폴로지의 Lync Server 대역폭 정책 서비스(인증)를 제공하는 컴퓨터의 테스트 결과
    
      - 토폴로지의 Lync Server 대역폭 정책 서비스(핵심)를 제공하는 컴퓨터의 테스트 결과

## 요구 사항

  - 이 도구는 토폴로지에 있으며 로컬 저장소를 보유한 컴퓨터에서 실행해야 합니다.

  - 로컬 저장소 액세스 권한이 있는 관리자가 이 도구를 실행해야 합니다.

## 예제

다음은 도구 입력의 예입니다.
```C++
    MsTurnPing -ServerRole AudioVideoEdgeServer
    
    MsTurnPing -ServerRole BandwidthPolicyServer
```
## 요약

이 도구는 오디오/비디오 및 대역폭 정책 서비스 실행 서버의 상태를 확인하려는 Lync Server 2013 관리자에게 중요한 리소스입니다.

## Network Configuration Viewer

Network Configuration Viewer는 Microsoft Lync Server 2013 통신 소프트웨어 관리자가 지정된 대역폭 용량에 따라 음성 또는 비디오 통화 같은 실시간 통신 세션을 허용하도록 프로비전된 엔터프라이즈의 CAC(통화 허용 제어) 네트워크 토폴로지를 보는 데 사용됩니다. Lync Server 2013 관리자는 Lync Server 2013과 함께 설치된 대역폭 정책 서비스에 의해 적용되는 CAC 정책을 정의합니다.

## 설명

관리자는 Network Configuration Viewer(NetworkConfigurationViewer.exe)를 사용하여 다음 작업을 수행할 수 있습니다.

  - Lync Server 2013 배포에서 그래픽 형식으로 CAC 네트워크 토폴로지 로드 및 보기

  - 대역폭 정책 서버 로그 파일에서 그래픽 형식으로 CAC 네트워크 토폴로지 로드 및 보기

  - XML 형식으로 디스크에 CAC 네트워크 토폴로지 저장 및 보관

  - JPG 또는 BMP 형식으로 CAC 네트워크 토폴로지 다이어그램 저장 및 보관

  - CAC 네트워크 토폴로지 구성 데이터 보기

  - 트리 보기 스타일로 CAC 네트워크 토폴로지 보기

  - CAC 네트워크 토폴로지 링크(예:사이트와 영역 간, 영역과 영역 간, 사이트와 사이트 간 링크)에 대한 사용자 지정 연결선 정의

  - CAC 네트워크 토폴로지 사이트 정보, 영역 정보, 프로비전된 대역폭 정책 및 네트워크 링크 보기

## 용도

그래픽 인터페이스에서 엔터프라이즈 CAC 네트워크 토폴로지 링크를 봅니다.

## 예제

**Lync Server 2013 배포에서 그래픽 형식으로 CAC 네트워크 토폴로지 로드 및 보기:** Lync Server 2013 관리자는 아래 그림과 같이 **Download Network Configuration(네트워크 구성 다운로드)** 옵션을 사용하여 모든 Lync Server 2013 컴퓨터의 CAC 네트워크 토폴로지 구성을 로드하고 볼 수 있습니다. 도구가 Lync 구성 저장소에 연결할 수 없는 컴퓨터에 배포된 경우에는 이러한 구성을 다운로드하거나 보지 못합니다.

![네트워크 구성 다운로드.](images/JJ945604.8d126d3f-2545-4f13-a244-974f09614982(OCS.15).jpg "네트워크 구성 다운로드.")

**대역폭 정책 서버 로그 파일에서 그래픽 형식으로 CAC 네트워크 토폴로지 로드 및 보기:**Lync Server 2013 대역폭 정책 서버에서 로깅 메커니즘의 일부로 Lync Server 2013 파일 공유 위치에 CAC 네트워크 토폴로지를 저장합니다. Lync Server 관리자는 아래에 표시된 것처럼 **Open Network Configuration(네트워크 구성 열기)** 옵션을 사용하여 그래픽 형식으로 이러한 파일을 볼 수 있습니다.

![대역폭 정책 서버 로그 파일 열기.](images/JJ945604.3e503e92-aacb-4921-a8d2-23f860fe2df6(OCS.15).jpg "대역폭 정책 서버 로그 파일 열기.")

XML 형식으로 디스크에 CAC 네트워크 토폴로지 저장 및 보관: Lync Server 2013 관리자는 아래와 같이 **Save a copy of Network Configuration(네트워크 구성 복사본 저장)** 옵션을 사용하여 CAC 네트워크 토폴로지 구성 파일을 XML 형식으로 저장할 수 있습니다. 저장된 구성 파일은 오프라인 상태에서 그래픽 보기 용도로 사용할 수 있습니다.

![네트워크 구성을 XML 파일로 저장.](images/JJ945604.6eeef3b0-78b5-4ee6-8d94-1a4ddf3d8676(OCS.15).jpg "네트워크 구성을 XML 파일로 저장.")

JPG 또는 BMP 형식으로 CAC 네트워크 토폴로지 다이어그램 저장 및 보관: Lync Server 2013 관리자는 아래와 같이 **Save Network Configuration diagram as picture(네트워크 구성 다이어그램을 그림으로 저장)** 옵션을 사용하여 CAC 네트워크 토폴로지 구성을 그래픽 형식(JPG 및 BMP 파일 형식)으로 저장할 수 있습니다.

![네트워크 구성을 그림으로 저장.](images/JJ945604.145a6fb9-58b1-46b1-bbd5-a661ceba07b4(OCS.15).jpg "네트워크 구성을 그림으로 저장.")

**CAC 네트워크 토폴로지 구성 데이터 보기:**Lync Server 2013 관리자는 아래와 같이 View Network Configuration data(네트워크 구성 데이터 보기) 옵션을 사용하여 네트워크 지역, 네트워크 사이트, 대역폭 프로필, 사이트 서브넷 IP 주소와 같은 관련 네트워크 구성 데이터를 텍스트 형식으로 볼 수 있습니다.

![네트워크 구성 데이터 보기.](images/JJ945604.b72a4c21-a042-4d91-bf96-fcb396af0679(OCS.15).jpg "네트워크 구성 데이터 보기.")

**트리 보기 스타일로 CAC 네트워크 토폴로지 보기:**Lync Server 2013 관리자는 아래와 같이 도구 창의 왼쪽에 있는 제어판을 사용하여 그래픽 트리 보기 스타일로 관련 네트워크 구성 데이터를 볼 수 있습니다.

![네트워크 구성 데이터를 트리 뷰로 보기.](images/JJ945604.4d924ac9-fd96-430f-b211-ee35b7ef9a23(OCS.15).jpg "네트워크 구성 데이터를 트리 뷰로 보기.")

**CAC 네트워크 토폴로지 링크(예:사이트와 영역 간, 영역과 영역 간, 사이트와 사이트 간 링크)에 대한 사용자 지정 연결선 정의:**Lync Server 2013 관리자는 아래와 같이 Settings(설정) 옵션을 사용하여 CAC 네트워크 구성 WAN 링크에 대한 사용자 지정 그래픽 연결선을 정의할 수 있습니다. 이는 네트워크 구성에 프로비전된 다양한 유형의 네트워크 링크를 식별하는 데 도움이 됩니다.

![CAC 네트워크 토폴로지에 대한 사용자 지정 커넥터 정의](images/JJ945604.b20bea67-c8e1-453e-b1dd-e2aa17b62566(OCS.15).jpg "CAC 네트워크 토폴로지에 대한 사용자 지정 커넥터 정의")

**CAC 네트워크 토폴로지 사이트 정보, 영역 정보, 프로비전된 대역폭 정책 보기:**Lync Server 2013 관리자는 아래에 표시된 옵션을 사용하여 관련 CAC 네트워크 지역 정보, 사이트 정보, CAC 대역폭 프로비저닝 정보를 볼 수 있습니다(예: 네트워크 지역 또는 네트워크 사이트 개체에서 **Info(정보)** 클릭).

![네트워크의 사용자 지정 커넥터 정의.](images/JJ945604.26262c75-4342-41c3-bc98-1793aa6a7713(OCS.15).jpg "네트워크의 사용자 지정 커넥터 정의.")

## 요약

이 도구는 배포에서 CAC 네트워크 토폴로지를 그래픽 형식으로 보려는 Lync Server 2013 관리자에게 중요한 리소스입니다.

## Response Group Agent Live

응답 그룹 응용 프로그램은 에이전트가 기본 제공 웹 서비스를 사용하여 유용한 실시간 정보에 액세스할 수 있는 권한을 제공합니다. 안타깝게도 응용 프로그램을 사용하지 않고는 이러한 데이터에 대한 그래픽 보기를 사용할 수 없습니다. Response Group Agent Live 리소스 키트 도구는 다른 에이전트의 상태와 같은 향상된 실시간 Microsoft Lync 2013 통신 소프트웨어 정보와 함께 이러한 정보를 그래픽으로 볼 수 있는 간단한 방법을 제공하여 이 문제를 해결합니다.

## 설명

Response Group Agent Live는 응답 그룹 에이전트에게 로그인 및 로그아웃 기능과 일부 실시간 정보를 제공하는 Windows 응용 프로그램입니다. 즉, 에이전트 그룹 페이지(Lync 2013에서 액세스 가능)의 향상된 버전입니다.

## 용도

응답 그룹 응용 프로그램은 수신 전화를 큐에 대기시킨 다음 에이전트 그룹으로 라우팅합니다. 서비스할 통화에 대해 충분한 정보를 바탕으로 올바른 결정을 하려면 에이전트가 사용 가능한 다른 에이전트, 각 큐에 대기 중인 전화 수 등 에이전트 그룹에 대한 실시간 정보에 액세스할 수 있어야 합니다. 초기에는 응답 그룹 서비스를 통해서만 액세스할 수 있었던 이러한 정보를 Response Group Agent Live를 통해 직관적인 방법으로 사용할 수 있게 되었습니다.

## 기능

Response Group Agent Live 도구는 응답 그룹 서비스 및 Microsoft Lync 2013 SDK에서 기본 제공됩니다. 이 도구는 응답 그룹 에이전트에게 응답 그룹 서비스에서 사용 가능한 정보와 기능(그룹 멤버십, 다른 에이전트의 상태, 대기 중인 전화 등)을 제공합니다.

아래 그림은 Response Group Agent Live의 기본 인터페이스를 보여 줍니다.

![Response Group Agent Live 도구.](images/JJ945604.63cb0374-a6ef-4a59-b60e-bec86a880d09(OCS.15).jpg "Response Group Agent Live 도구.")

에이전트는 Response Group Agent Live에서 다음 세 가지 기본 기능을 사용할 수 있습니다.

  - **로그인/로그아웃:** Lync 2013에서 액세스할 수 있는 에이전트 그룹 페이지와 대조적으로 Response Group Agent Live에서는 에이전트가 모든 에이전트 그룹에 한 번에 로그인하거나 로그아웃할 수 있습니다. 이 응용프로그램은 에이전트가 로그인 또는 로그아웃할 수 있는 세 가지 빠른 방법을 제공합니다.
    
      - 응용 프로그램 내에서 로그인/로그아웃(녹색/빨강) 단추를 클릭합니다.
    
      - 시스템 트레이 아이콘을 마우스 오른쪽 단추로 클릭하고 로그인 또는 로그아웃을 선택합니다.
    
      - 구성 가능한 키보드 바로 가기 키를 사용합니다.

  - **그룹 멤버십:** 에이전트 그룹이 선택되면 Response Group Agent Live의 오른쪽 창에 해당 그룹의 에이전트 목록이 표시됩니다. Lync 2013이 이 응용 프로그램과 동일한 컴퓨터에서 실행되고 있으면 현재 상태 정보 및 대화 상대 카드가 Response Group Agent Live에 표시됩니다. 에이전트는 여기서 직접 다른 에이전트에게 메신저 대화를 보내거나 전화를 걸 수 있습니다.

  - **실시간 통계:** Response Group Agent Live는 모든 에이전트 그룹에 대한 실시간 통계를 제공합니다. 업데이트 주기는 1분입니다. 응답 그룹이 전화를 받으면 해당 그룹 이름 옆에 현재 대기 중인 전화 수와 함께 시각적 표시기가 추가됩니다. 그룹 위에 표시기를 놓으면 최장 대기 시간이 표시됩니다.

## 요구 사항

Response Group Agent Live를 사용하려면 .NET Framework 4.0이 있어야 합니다. 또한 현재 상태와 대화 상대 카드 기능을 활용하려면 로컬에 Lync 2013이 설치되어 있고 실행되어야 합니다.

## 구성

Response Group Agent Live는 응용 프로그램의 옵션 대화 상자를 사용하여 개인의 상황에 맞게 사용자 지정할 수 있습니다. 또한 관리자가 RGAgentLive.exe.config file의 defaultHostAddress 속성을 직접 편집하여 기본 호스트 주소를 정의할 수 있습니다.

아래 그림에서는 에이전트가 호스트 주소와 바로 가기 키를 구성하는 데 사용할 수 있는 옵션 대화 상자를 보여 줍니다. 이 대화 상자는 기본 인터페이스의 맨 오른쪽에 있는 옵션 단추를 클릭하여 액세스할 수 있습니다.

![Response Group Agent Live 옵션 대화 상자.](images/JJ945604.3cc15e29-8699-45ab-90c3-e1565fa6ebf6(OCS.15).jpg "Response Group Agent Live 옵션 대화 상자.")

Response Group Agent Live 구성에서 다음 세 가지 설정을 사용자 지정할 수 있습니다.

  - 호스트 주소: 일반적으로 에이전트의 홈 풀에 속하는 웹 풀 FQDN입니다. 정확한 응답 그룹 서비스 주소는 이 정보의 배경에서 가져옵니다(호스트 뒤에 올바른 경로 추가).

  - 바로 가기 키: 정확한 로그인/로그아웃 바로 가기 키를 사용자 지정할 수 있습니다. 한 가지 제한 사항은 두 개의 바로 가기 키 모두 다른 키와 함께 “Windows 로고” 키를 포함해야 합니다.

  - Windows에서 시작: 이 응용 프로그램은 Windows를 시작할 때 자동으로 시작하도록 구성할 수 있습니다.

## 예제

아래 그림은 오른쪽 창의 대화 상대를 마우스 오른쪽 단추로 클릭하여 다른 에이전트에게 전화를 걸거나 메신저 대화를 보내는 방법을 보여 줍니다.

![전화 걸기 또는 메신저 대화 보내기.](images/JJ945604.009cebe0-5a93-4745-89c3-8a16c7c13009(OCS.15).jpg "전화 걸기 또는 메신저 대화 보내기.")

아래 그림은 Response Group Agent Live에서 모든 수신 전화 중 현재 큐에 대기 중인 전화 수와 최장 대기 시간을 표시하는 방식을 보여 줍니다.

![대기열 정보 보기.](images/JJ945604.131d7f79-b7ed-41f5-a9da-ffc556e31037(OCS.15).jpg "대기열 정보 보기.")

## 요약

빠른 로그인 및 로그아웃, 그룹 멤버십, 기본 실시간 통계는 응용 프로그램 외부의 응답 그룹 서비스에서만 사용할 수 있는 응답 그룹 에이전트의 흥미로운 기능입니다. Response Group Agent Live 리소스 키트 도구를 사용하면 Lync 관리자는 더욱 빠르게 그래픽으로 작업을 수행할 수 있는 Windows 응용 프로그램을 에이전트에게 제공할 수 있습니다.

## SEFAUtil

SEFAUtil(보조 확장 기능 활성화)은 Microsoft Lync Server 2013 통신 소프트웨어 관리자와 지원 센터 에이전트가 Lync Server 2013 사용자를 대신하여 대리인 신호 울림, 착신 전환, 동시 연결, 팀 통화 설정, 그룹 호출 받기를 구성할 수 있도록 하는 명령줄 도구입니다. 관리자는 이 도구를 사용하여 특정 사용자에게 게시된 통화 라우팅 설정을 쿼리할 수 있습니다. 관리자는 SEFAUtil 도구를 사용하여 사용자 대신 착신 전환 또는 동시 연결을 사용/해제/수정할 수 있습니다. 관리자는 대상을 지정하거나(SIP URI 형태) 사용자가 이미 게시한 대상을 사용할 수 있습니다. 또한 관리자는 이 도구를 사용하여 사용자 대신 대리인 또는 팀 통화 그룹 구성원을 추가하거나 제거할 수 있습니다. 이 도구는 Microsoft Unified Communications Managed API(UCMA) 3.0에서 기본 제공되며 관리자가 SEFAUtil에 대한 중앙 관리 저장소에 신뢰할 수 있는 응용 프로그램을 만들어야 합니다.

Lync Server 2013 관리자와 지원 센터 에이전트는 SEFAUtil(보조 확장 기능 활성화)을 사용하여 Lync Server 2013 사용자 대신 대리인 신호 울림, 착신 전환, 동시 연결, 팀 통화 설정, 그룹 호출 받기를 구성할 수 있습니다. 관리자는 또한 이 도구를 사용하여 특정 사용자에게 게시된 통화 라우팅 설정을 쿼리할 수 있습니다.

## 설명

SEFAUtil의 현재 버전은 명령줄 도구이며 그래픽 사용자 인터페이스는 지원되지 않습니다. 이 도구는 Microsoft Unified Communications Managed API(UCMA) 3.0을 기반으로 합니다. 관리자와 지원 센터 에이전트는 이 도구를 사용하여 다음을 수행할 수 있습니다.

  - 사용자에 대한 모든 통화 라우팅 설정 보기(착신 전환, 대리인 신호 울림, 동시 연결, 팀 통화, 그룹 호출 받기 포함)

  - 착신 전환 설정 사용/해제/수정(대상 및 응답 없음 타이머 포함)

  - 즉시 착신 전환 구성 사용/해제/수정

  - 대리인 설정 사용/해제/수정

  - 팀 통화 그룹 설정 설정/해제/수정
    

    > [!NOTE]
    > Lync Server 2013 SEFAUtil 도구의 새로운 기능



  - 동시 연결 설정 사용/해제/수정(대상 포함)
    

    > [!NOTE]
    > Lync Server 2013 SEFAUtil 도구의 새로운 기능



  - 그룹 호출 받기 설정 사용/해제/수정
    

    > [!WARNING]
    > Lync Server 2013 SEFAUtil 도구의 새로운 기능



다음은 이 도구의 제한 사항입니다.

  - Lync Server 풀에 있는 사용자만 지원

  - 여러 사용자에 대한 통화 라우팅 설정 일괄 편집 미지원

## 출력

이 도구의 현재 버전은 명령 프롬프트 창에서만 출력을 제공합니다. 자세한 내용은 이 문서 뒷부분에 나오는 예제 섹션을 참고하세요.

## 용도

다음은 이 도구가 사용될 수 있는 몇 가지 주요 시나리오입니다.

  - 영일은 임원이며 Lync Server 전화 통신으로 이동했습니다. 그에게는 기존 PBX 시스템에 대한 대리인이 있습니다. Lync로의 이동에 따라 관리자는 영일의 라우팅이 기존 대리인 구성을 반영하도록 구성할 수 있습니다.

  - 선희는 여행 도중 고객 중 한 명으로부터 중요한 전화를 받아야 한다는 사실이 생각났습니다. 그러나 선희가 머무는 호텔에서는 컴퓨터에 액세스할 수가 없습니다. 그녀는 지원 센터에 전화를 걸어 회사 번호로 걸려 온 모든 전화를 자신의 휴대폰 번호로 착신 전환해줄 것을 요청합니다. 이 경우 지원 센터 직원이 선희를 대신하여 구성을 수행할 수 있습니다.

  - 진국이 회사에 있을 때 회사 번호로 걸려 오는 전화는 휴대폰 음성 메일로 전환되는 반면 다른 모든 위치에서는 정상적으로 작동됩니다. 지원 센터 기술자는 진국의 라우팅 구성을 볼 수 있으며, 휴대폰으로 동시 연결이 구성된 것을 발견합니다. 기술자는 진국에게 회사에서 휴대폰으로 응답한 통화 범위를 물은 후, 네트워크 연결 상태가 나쁜 경우 동시 연결 규칙 때문에 전화가 휴대폰 음성 메일로 전환된다는 것을 확인할 수 있습니다.

  - 석규는 한미의 신입 직원으로 Microsoft Lync가 설정되어 모든 팀 구성원이 팀 통화를 하도록 구성된 새로운 팀에 들어가게 되었습니다. 관리자는 석규의 팀 통화 그룹 설정이 새로운 모든 팀 구성원을 포함하도록 설정하고, 팀의 각 구성원에 대해서도 석규를 팀 통화 그룹 구성원으로 추가할 수 있습니다.

  - 한미의 인사 관리부의 고객 서비스 방침은 첫 번째 전화부터 전화를 건 사람에게 개인 서비스를 제공하는 것입니다. 이 부서의 모든 직원의 자리가 서로 아주 가까운 것을 고려하면 팀 통화로 모든 전화가 동시에 울리는 것은 팀에 큰 방해가 될 것입니다. 팀 구성원을 방해하지 않고 최상의 서비스를 제공하기 위해 Lync 관리자는 그룹 호출 받기 기능을 활용합니다. 관리자는 모든 부서 직원을 호출 받기 그룹에 추가하고 해당 부서에 호출 받기 그룹 번호를 알려줍니다. 영희가 부재 중인 경우 태준이 그녀의 자리에서 전화가 울리는 것을 듣고 자신의 자리에서 받을 수 있습니다.

## 요구 사항

SEFAUtil 도구는 신뢰할 수 있는 응용 프로그램 풀에 속한 컴퓨터에서만 실행할 수 있습니다. UCMA 3.0이 해당 컴퓨터에 설치되어 있어야 합니다. 이 도구를 실행하려면 SEFAUtil 응용 프로그램 ID를 사용하여 해당 풀에서 새로운 신뢰할 수 있는 응용 프로그램을 만들어야 합니다.

**SEFAUtil 도구에 대한 새로운 신뢰할 수 있는 응용 프로그램 만들기**

1.  SEFAUTil 도구는 신뢰할 수 있는 응용 프로그램 풀에 속한 컴퓨터에서만 실행할 수 있습니다. 필요한 경우, Lync Server 관리 셸을 통해 다음 cmdlet을 사용하여 풀을 새로운 신뢰할 수 있는 응용 프로그램 풀로 추가할 수 있습니다.
    ```C++
        New-CsTrustedApplicationPool -id <Pool FQDN> -Registrar <Pool Registrar FQDN> -site Site:<Pool Site>
    ```

    > [!NOTE]
    > SEFAUtil 도구를 실행하는 데 사용할 모든 컴퓨터에 UCMA 3.0이 설치되어 있어야 합니다.



2.  신뢰할 수 있는 응용 프로그램이 SEFAUtil 도구에 대한 토폴로지에 정의되어야 합니다. SEFAUtil을 새로운 신뢰할 수 있는 응용 프로그램으로 정의하려면 Lync Server 관리 셸을 사용하여 다음 cmdlet을 실행합니다.
    ```C++
        New-CsTrustedApplication -ApplicationId sefautil -TrustedApplicationPoolFqdn <Pool FQDN>  -Port 7489
    ```

    > [!NOTE]
    > 필요한 경우 다른 포트를 사용할 수 있습니다.



3.  토폴로지 변경 내용을 사용하도록 설정해야 합니다. 토폴로지 변경 내용은 Lync Server 관리 셸을 통해 다음 cmdlet을 실행하여 사용하도록 설정할 수 있습니다.
    ```C++
        Enable-CsToplogy
    ```
4.  필요한 경우, SEFAUtil 도구를 실행하는 데 사용할 서버에 Lync Server 2013 리소스 키트 도구를 설치합니다(해당 서버는 신뢰할 수 있는 응용 프로그램 풀에 속해 있어야 함).

5.  SEFAUtil이 정상적으로 실행되고 있는지 확인합니다. 이렇게 하려면 관리자 권한으로 Windows 명령 프롬프트에서 도구를 실행하여 배포에서 사용자의 착신 전환 설정을 표시합니다. 기본적으로 도구는 “…\\Program Files\\Microsoft Lync Server 2013\\Reskit”에 있습니다. 사용자의 착신 전환 설정을 표시하려면 다음 명령을 사용합니다.
    ```C++
        SEFAUtil.exe <user SIP address> /server:<Lync Server/Pool FQDN>
    ```
    사용자의 착신 전환 설정이 표시되어야 합니다.

## 그룹 호출 받기

그룹 호출 받기의 기능을 모두 사용하려면 Lync Server에서 추가 구성이 필요합니다. 사용자에게 받기 그룹을 지정하기 전에 그룹 호출 받기 제품 설명서에서 이 기능의 계획 및 배포 단계를 참고하세요.

## 예제

## 현재 통화 처리 설정 표시

다음 명령은 사용자에 대한 통화 처리를 표시합니다. `SEFAUtil.exe /server:lyncserver.contoso.com katarina@contoso.com`


> [!NOTE]
> 이 예제에서는 <STRONG>/server</STRONG> 스위치를 사용하여 연결할 Lync Server를 지정합니다.



**출력**
```C++
    User Aor: sip:katarina@contoso.com
    Display Name: Katarina Larsson
    UM Enabled: True
    Simulring enabled: False
    User Ring time: 00:00:20
    Call Forward No Answer to: voicemail
```
## 착신 전환/응답 없음 대상 설정

이 예제에서는 착신 전환/응답 없음 대상과 연결 지연을 설정합니다. 여기에서는 /server 스위치가 제공되지 않습니다. SEFAUtil에서 Lync Server를 자동 검색합니다.
```C++
    SEFAUtil.exe /server:lyncserver.contoso.com sip:katarina@contoso.com /enablefwdnoanswer /callanswerwaittime:30 /setfwddestination:+1425555 0126@contoso.com;user=phone
```
**출력**
```C++
    User Aor: sip:katarina@contoso.com
    Display Name: Katarina Larsson
    UM Enabled: True
    Simulring enabled: False
    User Ring time: 00:00:30
    Call Forward No Answer to: sip:+14255550126@contoso.com;user=phone
```
## 즉시 착신 전환 사용

이 예제에서는 다른 사용자에게 즉시 착신 전환되도록 설정합니다.
```C++
    SEFAUtil.exe sip:katarina@contoso.com /enablefwdimmediate /setfwddestination:anders@contoso.com
```
**출력**
```C++
    User Aor: sip:katarina@contoso.com
    Display Name: Katarina Larsson
    UM Enabled: True
    Simulring enabled: False
    Forward immediate to: sip:anders@contoso.com
```
## 즉시 착신 전환 해제

이 예제에서는 즉시 착신 전환을 해제합니다.
```C++
    SEFAUtil.exe /server:lyncserver.contoso.com katarina@contoso.com  /disablefwdimmediate
```
**출력**
```C++
    User Aor: sip:katarina@contoso.com
    Display Name: Katarina Larsson
    UM Enabled: True
    Simulring enabled: False
    User Ring time: 00:00:30
    Call Forward No Answer to: voicemail
```
## 사용자를 대리인으로 추가 및 대리인의 동시 연결 설정

이 예제에서는 사용자를 대리인으로 추가하고 대리인의 동시 연결을 설정합니다.
```C++
    SEFAUtil.exe /server:lyncserver.contoso.com sip:katarina@contoso.com /adddelegate:joe@contoso.com /simulringdelegates
```
**출력**
```C++
    User Aor: sip:katarina@contoso.com
    Display Name: Katarina Larsson
    UM Enabled: True
    Simultaneously Ringing Delegates: sip:joe@contoso.com
```
## 대리인의 동시 연결 규칙 변경

이 예제에서는 지연된 신호 울림 규칙에 대한 이전 예제에서 설정한 동시 연결 규칙을 변경합니다.
```C++
    SEFAUtil.exe /server:lyncserver.contoso.com sip:katarina@contoso.com /delayringdelegates:10
```
**출력**
```C++
    User Aor: sip:katarina@contoso.com
    Display Name: Katarina Larsson
    UM Enabled: True
    Simulring enabled: False
    Delay Ringing Delegates (delay:10 seconds): sip:joe@contoso.com
```
## 대리인 제거

이 예제에서는 대리인을 제거합니다.


> [!NOTE]
> 마지막 대리인이 제거되면 대리인 신호 울림은 자동으로 해제됩니다.


```C++
    SEFAUtil.exe /server:lyncserver.contoso.com sip:katarina@contoso.com /removedelegate:joe@contoso.com
```
**출력**
```C++
    User Aor: sip:katarina@contoso.com
    Display Name: Katarina Larsson
    UM Enabled: True
    Simulring enabled: False
    User Ring time: 00:00:30
    Call Forward No Answer to: voicemail
```
## 대리인 추가 및 대리인에 대한 착신 전환 규칙 설정

이 예제에서는 대리인을 추가하고 대리인에 대한 착신 전환 규칙을 설정합니다.
```C++
    SEFAUtil.exe /server:lyncserver.contoso.com sip:katarina@contoso.com /adddelegate:anders@contoso.com /fwdtodelegates
```
**출력**
```C++
    User Aor: sip:katarina@contoso.com
    Display Name: Katarina Larsson
    UM Enabled: True
    Forwarding calls to Delegates: sip:anders@contoso.com
```
## 동시 연결 사용 및 대상 번호 설정

이 예제에서는 동시 연결을 사용하도록 설정하고 동시 연결 대상 번호를 설정합니다.
```C++
    SEFAUtil.exe /server:lyncserver.contoso.com sip:katarina@contoso.com /setsimulringdestination:+14255550126 /enablesimulring
```

> [!NOTE]
> 이미 동시 연결을 사용하도록 설정된 사용자의 동시 연결 대상 번호를 변경하려면 /enablesimulring 스위치를 사용하여 명령을 유지합니다. 그렇지 않으면 대상 번호가 변경되지 않습니다.



**출력**
```C++
    User Aor: sip:katarina@contoso.com
    Display Name: Katarina Larsson
    UM Enabled: True
    Simulring enabled: True
    Simul_Ringing to: sip:+14255550126@contoso.com;user=phone
```
## 동시 연결 해제

이 예제에서는 동시 연결을 해제합니다.
```C++
    SEFAUtil.exe /server:lyncserver.contoso.com sip:katarina@contoso.com /disablesimulring
```
**출력**
```C++
    User Aor: sip:katarina@contoso.com
    Display Name: Katarina Larsson
    UM Enabled: True
    Simulring enabled: False
    User Ring time: 00:00:30
    Call Forward No Answer to: voicemail
```
## 팀 통화에 팀 구성원 추가 및 팀 통화 구성원 그룹에 동시 연결 설정

이 예제에서는 사용자의 팀 통화 그룹에 팀 구성원을 추가하고 팀 통화 그룹에 동시 연결을 사용하도록 설정합니다.
```C++
    SEFAUtil.exe /server:lyncserver.contoso.com sip:katarina@contoso.com /addteammember:anders@contoso.com /simulringteam
```

> [!NOTE]
> 사용자의 팀 통화 그룹에 구성원을 추가하면 팀 통화 그룹에 동시 연결되는 사용자의 동시 연결 설정이 자동으로 전환됩니다.



**출력**
```C++
    User Aor: sip:katarina@contoso.com
    Display Name: Katarina Larsson
    UM Enabled: True
    Team ringing enabled. Team: sip:anders@contoso.com
```
## 팀 통화 그룹에서 구성원 제거

이 예제에서는 사용자의 팀 통화 그룹에서 팀 구성원을 제거합니다.
```C++
    SEFAUtil.exe /server:lyncserver.contoso.com sip:katarina@contoso.com /removeteammember:anders@contoso.com
```

> [!NOTE]
> 제거된 구성원이 팀 통화 그룹의 유일한 구성원이었다면 팀 통화 그룹에 대한 동시 연결이 자동으로 해제됩니다.



**출력**
```C++
    User Aor: sip:katarina@contoso.com
    Display Name: Katarina Larsson
    UM Enabled: True
    User Ring time: 00:00:30
    Call Forward No Answer to: voicemail
```
## 팀 통화 그룹에 연결 지연 설정

이 예제에서는 팀 통화 그룹에 대한 연결 지연 설정을 변경합니다.
```C++  
    SEFAUtil.exe /server:lyncserver.contoso.com sip:katarina@contoso.com /delayringteam:5
```
**출력**
```C++
    User Aor: sip:katarina@contoso.com
    Display Name: Katarina Larsson
    UM Enabled: True
    Delay Ringing Team (delay:5 seconds). Team: sip:anders@contoso.com
```
## 팀 통화 사용

이 예제에서는 지정된 사용자가 팀 통화를 사용하도록 설정합니다.
```C++
    SEFAUtil.exe /server:lyncserver.contoso.com sip:katarina@contoso.com /simulringteam
```

> [!NOTE]
> 사용자의 팀 통화 그룹에 구성원이 없는 경우 팀 통화를 사용하도록 설정할 수 없습니다.



**출력**

## 팀 통화 해제

이 예제에서는 지정된 사용자의 팀 통화를 해제합니다.
```C++
    SEFAUtil.exe /server:lyncserver.contoso.com sip:katarina@contoso.com /disableteamcall
```
**출력**
```C++
    User Aor: sip:katarina@contoso.com
    Display Name: Katarina Larsson
    UM Enabled: True
    User Ring time: 00:00:30
    Call Forward No Answer to: voicemail
```
## 그룹 호출 받기 사용 및 사용자에게 받기 그룹 할당

이 예제에서는 사용자에게 받기 그룹을 할당하고 그룹 호출 받기를 사용하도록 설정합니다.
```C++
    SEFAUtil.exe /server:lyncserver.contoso.com sip:katarina@contoso.com /enablegrouppickup:199
```
**출력**

    User Aor: sip:katarina@contoso.com
    Display Name: Katarina Larsson
    UM Enabled: True
    Group Pickup Orbit: sip:199;phone-context=user-default@ contoso.com;user=phone

## 그룹 호출 받기 해제

이 예제에서는 지정된 사용자의 그룹 호출 받기를 해제합니다.
```C++
    SEFAUtil.exe /server:lyncserver.contoso.com sip:katarina@contoso.com /disablegrouppickup
```

> [!NOTE]
> 사용자에 대해 그룹 호출 받기를 해제하면 해당 사용자에게 할당된 그룹 번호가 보존되지 않습니다. 나중에 해당 사용자에 대해 그룹 호출 받기를 다시 설정하려면 /enablegrouppickup 스위치를 사용하여 그룹 번호를 다시 할당해야 합니다.


```C++
    User Aor: sip:katarina@contoso.com
    Display Name: Katarina Larsson
    UM Enabled: True
```
## SYSPrep.ps1

## 설명

SYSPrep.ps1은 사용자의 Windows Server 2008 운영 체제 컴퓨터에 다음 Lync Server 2013 필수 구성 요소를 설치하는 Windows PowerShell 스크립트입니다.

  - Microsoft .Net Framework 4.5

  - Microsoft SQL Server Express

  - Windows Powershell 버전 3.0

  - Microsoft Visual C++ 2010 재배포 가능

  - Internet Information Server Updates

  - Windows Identity Foundation

  - Lync Server 2013 핵심 파일

스크립트 이름이 Microsoft Windows 운영 체제에 대한 시스템 준비 도구의 이름과 비슷하더라도 실제는 다릅니다. 이 스크립트는 Lync Server 2013에 대한 필수 구성 요소만 설치합니다. 필수 구성 요소가 설치되면 Windows SYSPrep 도구를 사용하여 서버 이미지를 만들 수 있습니다.

## 요구 사항

SYSPrep.ps1 스크립트를 실행하기 전에 Windows Server 2008 운영 체제 컴퓨터의 로컬 폴더(예: **D:\\Setup**)로 필수 구성 요소 파일을 복사해야 합니다. 이 폴더에는 Lync Server 2013 파일(특히 **Setup.exe.**)의 복사본이 포함되어야 합니다. 필수 구성 요소 파일은 다음 위치에서 다운로드할 수 있습니다.


<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th>필수 구성 요소</th>
<th>위치</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Microsoft .Net Framework 4.5</p></td>
<td><p>http://go.microsoft.com/?linkid=9816306</p></td>
</tr>
<tr class="even">
<td><p>Microsoft SQL Server Express 2008 R2</p></td>
<td><p>http://www.microsoft.com/ko-kr/download/details.aspx?id=23650</p></td>
</tr>
<tr class="odd">
<td><p>Windows Powershell 버전 3.0</p></td>
<td><p>http://www.microsoft.com/en-us/download/details.aspx?id=34595</p></td>
</tr>
<tr class="even">
<td><p>Microsoft Visual C++ 2010 재배포 가능</p></td>
<td><p>http://www.microsoft.com/ko-kr/download/details.aspx?id=5555</p></td>
</tr>
<tr class="odd">
<td><p>Internet Information Server Updates</p></td>
<td><p>http://www.microsoft.com/ko-kr/download/details.aspx?id=34869</p></td>
</tr>
<tr class="even">
<td><p>Windows Identity Foundation</p></td>
<td><p>http://www.microsoft.com/ko-kr/download/details.aspx?id=17331</p></td>
</tr>
<tr class="odd">
<td><p>Lync Server 2013 Setup.exe</p></td>
<td><p>Lync Server 2013 미디어에서 복사</p></td>
</tr>
</tbody>
</table>


## 매개 변수

**–SetupFolder** 매개 변수는 필수 구성 요소 파일의 디렉터리 위치를 인수로 가져옵니다.

## 예제

SYSPrep.ps1 스크립트를 실행하여 Lync Server 2013 필수 구성 요소를 설치하려면 관리자 권한 명령 프롬프트에서 다음 명령을 실행합니다.
```C++
    ./SysPrep.PS1 -SetupFolder D:\Setup
```
## Unassigned Number Announcements Migration

Lync 관리자는 Unassigned Number Announcements Migration 도구를 사용하여 알림 응용 프로그램에서 서비스를 받고 있는 지정되지 않은 번호 구성을 원본 Lync Server 또는 풀에서 대상 Lync Server 또는 풀로 이동할 수 있습니다.

## 설명

Unassigned Number Announcements Migration 도구는 원본 Lync Server 또는 풀의 알림 응용 프로그램에서 서비스를 받고 있는 지정되지 않은 번호 구성을 대상 Lync Server 또는 풀로 이동하는 Windows PowerShell 스크립트입니다.

Unassigned Number Announcements Migration 스크립트를 실행하면 다음 작업이 수행됩니다.

1.  원본 서버 또는 풀에서 호스트된 알림 응용 프로그램의 지정되지 않은 번호 알림에 사용되는 모든 오디오 파일을 대상 서버 또는 풀의 파일 저장소로 이동합니다.
    

    > [!NOTE]
    > 오디오 파일이 대상 풀로 복사되면 원본 풀에서 제거됩니다.



2.  원본 서버 또는 풀에서 호스트된 알림 응용 프로그램에 대해 구성된 모든 지정되지 않은 번호 알림을 대상 서버 또는 풀로 이동합니다.

3.  원본 서버 또는 풀에서 호스트된 알림 응용 프로그램에서 서비스를 받고 있는 모든 지정되지 않은 번호 범위를 대상 서버 또는 풀로 다시 지정합니다.

스크립트가 성공적으로 실행되면, 원본 서버 또는 풀에서 호스트된 알림 응용 프로그램에서 서비스를 받고 있는 모든 지정되지 않은 번호 범위가 동일한 구성으로 대상 서버 또는 풀에서 서비스를 받게 됩니다.

## 출력

Lync 관리 셸 창의 **Move-CsAnnouncementConfiguration** 스크립트는 실행된 위치에서 마이그레이션 작업이 성공 또는 실패했는지 여부를 나타냅니다.

오류로 인해 작업 실행이 중단된 경우, 성공적으로 대상으로 이동된 지정되지 않은 번호 범위는 대상에 운영상의 형태로 남아 있고, 마이그레이션할 나머지 지정되지 않은 번호 범위는 원본에 운영상의 형태로 남게 됩니다. 나머지 구성을 완전히 마이그레이션하려면 문제 해결 후 스크립트를 다시 실행합니다.

## 용도

Unassigned Number Announcements Migration 스크립트는 다음 세 가지 시나리오에서 사용할 수 있습니다.

  - **구성 설정을 Lync Server의 새 버전으로 마이그레이션:** 한미는 Lync Server 2013으로 마이그레이션하는 중이며, 마이그레이션 절차의 일부로 Lync Server 관리자가 Lync Server 2010 배포의 알림 응용 프로그램에서 서비스를 받고 있는 지정되지 않은 번호 구성을 새 Lync Server 2013 배포로 이동하려고 합니다. Lync Server 관리자가 구성 설정을 이동하기 위해 Unassigned Number Announcements Migration 도구를 사용합니다.

  - **Lync Server 2013에서 Lync Server 2010으로 배포 롤백:** 예기치 않은 요인 때문에 한미는 새 Lync Server 2013 배포에 대한 마이그레이션을 롤백해야 합니다. Lync Server 관리자가 서비스 중단을 최소화하기 위해 Unassigned Number Announcements Migration 도구를 사용하여 Lync Server 2013 배포에서 Lync Server 2010 배포로 구성을 롤백합니다.

  - **Lync 배포 간 데이터 이동:** 한미는 한 풀의 모든 서버를 새로운 서버로 바꾸는 중입니다. 한미의 전략은 새 Lync Server 2013 풀을 배포하고, 이전 풀에서 새 풀로 모든 데이터를 이동한 다음, 이전 풀을 더 이상 사용하지 않는 것입니다. 새 풀이 배포되고 나면 Unassigned Number Announcements Migration 도구를 사용하여 이전 풀에서 새 풀로 구성을 이동할 수 있습니다.

## 요구 사항

다음은 도구를 성공적으로 실행하는 데 필요한 기본 요구 사항입니다.

1.  스크립트는 Lync Server 2013 관리 셸이 설치된 컴퓨터에서 실행되어야 합니다.

2.  알림 응용 프로그램이 원본 및 대상 Lync Server 또는 풀에 성공적으로 배포되어야 합니다.

## Move-CsAnnouncementConfiguration 스크립트

Move-CsAnnouncementConfiguration 스크립트에는 아래 표의 설명에 나오는 두 매개 변수가 필요합니다.

![Move-CsAnnouncementConfiguration 매개 변수.](images/JJ945604.7ab66ad3-d0db-4d77-8b93-ebccf0cb0663(OCS.15).jpg "Move-CsAnnouncementConfiguration 매개 변수.")

## 예제

## Lync Server 2010 풀에서 Lync Server 2013 풀로 지정되지 않은 번호 알림 구성 이동

이 예제에서는 원본 풀(Lync Server 2010)에서 대상 풀(Lync Server 2013)로 지정되지 않은 번호 알림을 이동합니다.
```C++
    Move-CsAnnouncementConfiguration.ps1 -Source LS2010Pool.contoso.com -Destination LS2013Pool.contoso.com
```
## Lync Server 2013 풀에서 Lync Server 2010 풀로 지정되지 않은 번호 알림 구성 이동

이 예제에서는 원본 풀(Lync Server 2013)에서 대상 풀(Lync Server 2010)로 지정되지 않은 번호 알림을 이동합니다.
```C++
    Move-CsAnnouncementConfiguration.ps1 -Source LS2013Pool.contoso.com -Destination LS2010Pool.contoso.com
```
## Web Conf Data

Lync Server 2013 통신 소프트웨어의 관리자는 Web Conf Data 도구를 사용하여 이끌이의 웹 회의와 관련된 데이터를 효율적으로 제어할 수 있습니다. 시나리오에는 타임스탬프 조건에 따라 특정 사용자의 모임 데이터를 삭제하는 기능이 포함됩니다.

## 설명

관리자는 이 도구를 사용하여 다음 작업을 수행할 수 있습니다.

1.  단일 사용자와 관련된 모든 웹 회의 데이터를 찾습니다.

2.  단일 사용자와 관련된 모든 웹 회의 데이터를 삭제합니다.

3.  단일 사용자와 관련되고 특정 날짜보다 오래된 모든 웹 회의 데이터를 삭제합니다.

4.  사용자가 한 풀에서 다른 풀로 이동한 경우 해당 단일 사용자와 관련된 모든 웹 회의 데이터를 이동합니다.


> [!NOTE]
> Lync Server 2010용 리소스 키트 도구에서는 사용자가 한 풀에서 다른 풀로 이동한 경우 해당 단일 사용자와 관련된 모든 웹 회의 데이터 이동이 지원되었습니다. 이 도구에서는 <STRONG>MoveConferenceData</STRONG> 매개 변수로 인해 해당 기능은 더 이상 사용되지 않습니다. 이 매개 변수에 대한 자세한 내용은 <A href="https://technet.microsoft.com/ko-kr/library/gg398528(v=ocs.15)">Move-CsUser</A> cmdlet을 참고하세요.



이 도구는 비활성 모임의 모임 데이터만 삭제합니다. 활성 모임(진행 중인 모임)은 삭제되지 않습니다.

이 도구는 대상 사용자와 동일한 풀에 있는 컴퓨터에서 실행되어야 합니다. 이 도구를 사용하여 모임 콘텐츠 데이터를 관리하는 사용자는 동일한 사용자 풀에 있어야 합니다.

## 출력

이 도구는 다음 각 작업의 결과를 출력합니다.

  - 쿼리를 수행하면 해당 사용자가 이끌이로 있는 모든 비활성 모임 데이터 폴더의 목록이 출력됩니다.

  - 삭제를 수행하면 데이터가 삭제되는 모든 모임 데이터 폴더의 목록이 출력됩니다.

## 요구 사항

현재 이끌이가 있는 풀과 동일한 풀에서 도구를 실행해야 합니다.

콘텐츠 파일 저장소에 액세스할 수 있는 관리자 권한을 사용하여 도구를 실행해야 합니다.

## 예제

다음 표에서는 매개 변수에 대해 설명하며, 일부 매개 변수는 예제에서 사용됩니다.

![Web Conf Data Tool 매개 변수.](images/JJ945604.a733c1c6-5dfc-4874-a74f-bfdee81c1401(OCS.15).jpg "Web Conf Data Tool 매개 변수.")
```C++
    WebConfDataTool.exe /User:user0@contoso.com /Action:query ""/ExpirationDate:08/09/2010 12:00:00""
```
위의 예제에서는 쿼리 명령이 작동하는 방식을 보여 줍니다. 이 명령은 이 도구의 영향을 받는 모든 모임 콘텐츠 폴더 목록을 출력합니다.
```C++
    WebConfDataTool.exe /User:user0@contoso.com /Action:delete
```
위의 예제는 삭제 명령을 보여 줍니다. 삭제 명령을 사용하면 이 사용자의 모든 비활성 모임 폴더가 제거됩니다.

## 요약

이 도구는 모임 데이터를 보다 정교하게 제어하려는 관리자에게 중요한 리소스입니다.

