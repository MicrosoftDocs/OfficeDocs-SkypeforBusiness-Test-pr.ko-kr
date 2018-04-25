---
title: 모범 사례 분석기에 대한 그룹 구성원 자격 및 사용자 권한 요구 사항
TOCTitle: 모범 사례 분석기에 대한 그룹 구성원 자격 및 사용자 권한 요구 사항
ms:assetid: f812e343-8f75-454e-b7a8-1b404e32071a
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg591354(v=OCS.15)
ms:contentKeyID: 49305575
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# 모범 사례 분석기에 대한 그룹 구성원 자격 및 사용자 권한 요구 사항

 

_**마지막으로 수정된 항목:** 2012-10-21_

모범 사례 분석기를 실행하려면 로그온할 때 사용하는 사용자 계정이 로컬 컴퓨터에서 관리자 그룹의 구성원이어야 합니다. 또한 환경을 검사하려면 사용자 계정이 다음 그룹의 구성원이어야 합니다.

  - **Domain Admins**   Active Directory 도메인 서비스 정보를 열거하고 도메인 컨트롤러와 글로벌 카탈로그 서버에서 WMI(Windows Management Instrumentation) 공급자를 호출하려는 경우

  - **Administrators**   각 Lync Server 2013 내부 컴퓨터와 각 에지 서버에서 WMI(Windows Management Instrumentation) 공급자를 호출하고 레지스트리에 액세스하는 데 필요합니다.

  - **RTCUniversalReadOnlyAdmins**   전체 또는 위임된 읽기 전용 Lync Server 2013 관리 권한입니다.

  - **Exchange View Only Administrator**   Microsoft Exchange 조직에서 전체 또는 위임된 Exchange 보기 전용 관리자입니다.

사용자 계정에 사용자 권한이 충분하지 않은 경우 다음과 같은 두 가지 옵션이 있습니다.

  - 명령 프롬프트에서 **runas** 명령을 사용하여 충분한 사용자 권한이 있는 계정에서 도구를 실행합니다. 구문은 다음과 같습니다.
    
        runas /netonly /user:<domain>\<userName> rtcbpa.exe

  - **Active Directory에 연결** 페이지에서 모범 사례 분석기를 실행하는 데 사용하려는 계정에대한 자격 증명을 설정합니다. **고급 로그인 옵션 표시**를 클릭합니다. 세 가지 계정(Active Directory 도메인 서비스용 계정, Lync Server 2013에지 서버 연결용 계정 및 Exchange Server 연결용 계정)을 입력할 수 있습니다. 이러한 계정을 하나도 지정하지 않으면 모범 사례 분석기에 로그온 및 실행하는 데 사용된 사용자 계정이 사용됩니다.

