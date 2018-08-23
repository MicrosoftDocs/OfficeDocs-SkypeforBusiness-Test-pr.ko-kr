---
title: Lync Server 2013의 Lync PreCall 진단 도구
TOCTitle: Lync Server 2013의 Lync PreCall 진단 도구
ms:assetid: 0ff291ec-cfb4-43eb-b5d6-a7a325681e3f
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Dn451255(v=OCS.15)
ms:contentKeyID: 59602766
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Lync Server 2013의 Lync PreCall 진단 도구

 

_**마지막으로 수정된 항목:** 2014-01-14_

Lync PCD(PreCall Diagnostics) 도구는 네트워크의 현재 상태가 예정된 엔터프라이즈 음성 통화의 오디오 품질에 미치는 영향을 확인하는 데 사용되는 클라이언트 기반 응용 프로그램입니다.

PCD는 네트워크의 마지막 홉이 가장 취약할 수 있는 상황(랩톱으로 공용 Wi-Fi 네트워크를 사용하거나 가정용 사용자인 경우 등)에서 가장 유용합니다. PCD는 이러한 네트워크의 최종 레그를 트래버스하는 작은 패킷 스트림을 만듭니다. 그런 다음 해당 패킷 스트림을 분석하여 이러한 레그에서 지터 및 손실이 통화 품질에 미칠 수 있는 영향을 측정한 후 보고서를 제공합니다. 클라이언트에서 지속적으로 PCD를 실행할 수 있으며 통화가 배치되는 중에도 PCD를 실행할 수 있습니다. 패킷 스트림은 대역폭에 중대한 영향을 미치지는 않습니다.

**최신 PCD 릴리스인 버전 1.1에는 다음과 같은 향상 기능이 추가됩니다.**

  - 최대 127자의 긴 암호 지원

  - 인증 로그인 문제에 대한 추가 진단

  - Lync 하이브리드 배포에 대한 향상된 지원

  - 자격 증명 선택 업데이트

  - 안정성 향상

Microsoft는 사용자의 의견을 환영합니다. 모든 지원 관련 질문 및 문제는 [PCD Feedback](mailto:pcdfb@microsoft.com)(전자 메일 주소: <pcdfb@microsoft.com>)으로 보내주세요.

이 섹션에는 다음 항목이 포함되어 있습니다.

  - Lync PCD 버전

  - Lync PCD 시스템 요구 사항

  - Lync PCD 기능

  - Lync PCD 실행

  - Lync PCD 제거

## Lync PCD 버전

이 항목에서는 다음과 같이 무료로 다운로드할 수 있는 도구 버전에 대해 설명합니다.

  - Windows 데스크톱 앱([http://go.microsoft.com/fwlink/?LinkId=327914](http://go.microsoft.com/fwlink/p/?linkid=327914))

  - Windows 8 Modern App([http://go.microsoft.com/fwlink/?LinkId=322110](http://go.microsoft.com/fwlink/p/?linkid=322110))


> [!NOTE]
> Office 365 Lync 사용자는 PCD의 두 가지 버전을 모두 사용할 수 있습니다.



이전 버전의 PCD를 사용하려면 다음을 참고하세요.

  - Microsoft 다운로드 센터([Office Communications Server 2007 R2, PreCallDiagnostic Resource Kit Tool (32 Bit)](http://go.microsoft.com/fwlink/p/?linkid=164769))에서 32비트 버전의 PCD를 무료로 다운로드하여 사용할 수 있습니다.

  - 64비트 버전의 PCD에는 Office Communications Server 2007 R2 리소스 키트 도구가 포함되어 있으며 Microsoft 다운로드 센터([Office Communications Server 2007 R2 Resource Kit Tools](http://go.microsoft.com/fwlink/p/?linkid=145159))에서 무료로 다운로드하여 사용할 수 있습니다.

## Lync PCD 시스템 요구 사항


> [!NOTE]
> PCD를 사용하려면 Lync Server 배포에서 모바일 클라이언트를 지원할 수 있도록 UCWA(Unified Communications Web API)가 설치 및 구성되어 있어야 합니다.UCWA는 Lync Server와 함께 설치됩니다.



## Windows 데스크톱 앱 요구 사항

  - Windows 7 또는 Windows 8 운영 체제의 모든 버전

  - Microsoft .NET Framework 4.5([http://go.microsoft.com/fwlink/?LinkId=327790](http://go.microsoft.com/fwlink/p/?linkid=327790)에서 제공)

## Windows 8 Modern App 요구 사항

  - Windows 8 운영 체제의 모든 버전

  - Microsoft .NET Framework 4.5([http://go.microsoft.com/fwlink/?LinkId=327790](http://go.microsoft.com/fwlink/p/?linkid=327790)에서 제공)

## Lync PCD 기능

Lync PCD에는 다음 기능이 포함되어 있습니다.

  - 기본 On Demand(2분 버스트)로 실행

  - Always On(맞춤 보기로 최대 24시간) 모드에서 실행

  - 이전 테스트 실행 보기

  - 로그인 실패 진단(Windows 8용 Lync PCD에서만 사용 가능)

![Lync PCD 기능 로그인 프로세스 스크린샷](images/Dn451255.7e0eb891-1481-47ae-8d63-164468f69c96(OCS.15).png "Lync PCD 기능 로그인 프로세스 스크린샷")

  - 네트워크 메트릭의 그래픽 보기 – 전체 화면 및 맞춤 보기에서 네트워크 MOS, 패킷 손실, Interarrival 지터

**전체 화면 보기**

![PreCall Diagnostic 도구 테스트 결과 그래프](images/Dn451255.5d01fd94-9e59-4823-96c7-7a1c83dd7d31(OCS.15).png "PreCall Diagnostic 도구 테스트 결과 그래프")

**맞춤 보기**

![PreCall Diagnostic 도구 사용률 테스트 결과](images/Dn451255.30501ba7-22d1-4db1-9297-56cf7dc6721c(OCS.15).png "PreCall Diagnostic 도구 사용률 테스트 결과")

## Lync PCD 실행

## Windows 데스크톱 앱 실행

1.  Windows 7 시스템에서 PCD를 시작하려면 **시작** 메뉴에서 **PreCall Diagnostics**를 선택합니다.
    
    Windows 8 시스템에서 PCD를 시작하려면 시작 화면에서 해당 아이콘을 선택하거나 "PreCall Diagnostics"를 검색합니다.
    
    ![PreCall Diagnostic 도구 아이콘](images/Dn451255.c9800fde-54f6-4efe-bb35-1a38064ec380(OCS.15).png "PreCall Diagnostic 도구 아이콘")

2.  도구가 시작되면 자격 제공을 증명할 기본 방법을 선택하고 **PreCall Diagnostics Tool Options(PreCall Diagnostics 도구 옵션)** 대화 상자에서 네트워크 운영 모드를 선택한 다음 **OK(확인)** 를 선택합니다.

3.  **Start Test(테스트 시작)** 단추를 선택하여 진단 실행을 시작합니다.
    
    **Use network credentials(네트워크 자격 증명 사용)** 옵션을 선택한 경우 테스트가 즉시 시작됩니다.
    
    **Let me enter my credentials(자격 증명 직접 입력)** 옵션을 선택한 경우 **Windows Security(Windows 보안)** 대화 상자가 열립니다. 자격 증명을 입력하면 테스트가 시작됩니다.

## Windows 8 Modern App 실행


1.  PCD를 시작하려면 시작 화면에서 해당 아이콘을 선택하거나 "PreCall Diagnostics"를 검색합니다.
    
    ![PreCall Diagnostic 도구 아이콘](images/Dn451255.c9800fde-54f6-4efe-bb35-1a38064ec380(OCS.15).png "PreCall Diagnostic 도구 아이콘")

2.  도구가 시작되면 Lync 자격 증명을 제공한 다음 **OK(확인)** 를 선택합니다.
    
    ![Lync PreCall Diagnostics 도구 로그인](images/Dn451255.88039914-4c68-48f6-a9fa-58cb4e3f3488(OCS.15).jpg "Lync PreCall Diagnostics 도구 로그인")

3.  **Start test(테스트 시작)** 단추를 선택하여 진단 실행을 시작합니다.

## Lync PCD 제거

Lync PCD를 제거하려면 운영 체제에 따라 다음 절차를 수행합니다.

  - Windows 7 시스템에서는 **제어판**을 열고 **프로그램 및 기능**을 선택한 다음 **Lync 2013 PreCall Diagnostics**를 두 번 클릭합니다.

  - Windows 8 시스템에서는 PCD 타일을 마우스 오른쪽 단추로 클릭하고 시작 화면 아래쪽에 있는 앱 표시줄에서 **제거**를 클릭합니다.

