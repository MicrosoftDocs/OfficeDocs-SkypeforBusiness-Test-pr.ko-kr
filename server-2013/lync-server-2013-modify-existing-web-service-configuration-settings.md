---
title: 기존 웹 서비스 구성 설정 수정
TOCTitle: 기존 웹 서비스 구성 설정 수정
ms:assetid: bd9c7aa5-d31c-4fab-b31d-8baae26b1296
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg182580(v=OCS.15)
ms:contentKeyID: 49304881
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# 기존 웹 서비스 구성 설정 수정

 

_**마지막으로 수정된 항목:** 2012-11-01_

**웹 서비스** 페이지에서 Lync Server 2013 관련 웹 서버 및 웹 서비스에 액세스하는 데 필요한 인증 방법을 구성할 수 있습니다.

다음 단계에 따라 기존의 웹 서비스 정책을 수정할 수 있습니다.

## 기존의 웹 서비스를 수정하려면

1.  RTCUniversalServerAdmins 그룹의 구성원인 사용자 계정(또는 이와 동일한 사용자 권한을 가진 사용자 계정)이나 CsServerAdministrator 또는 CsAdministrator 역할이 할당된 사용자 계정에서 Lync Server 2013을 배포한 네트워크에 있는 컴퓨터에 로그온합니다.

2.  브라우저 창을 연 다음 Admin URL을 입력하여 Lync Server 제어판을 엽니다. Lync Server 제어판을 시작하는 데 사용할 수 있는 다양한 방법에 대한 자세한 내용은 [Lync Server 관리 도구 열기](lync-server-2013-open-lync-server-administrative-tools.md)를 참조하세요.

3.  왼쪽 탐색 표시줄에서 **보안**, **웹 서비스**를 차례로 클릭합니다.

4.  **웹 서비스** 페이지에서 구성을 클릭하고 **편집**, **자세한 정보 표시**를 차례로 클릭합니다.

5.  **웹 서비스 설정 편집**의 **Windows 통합 인증**에서 **협상**, **NTLM**, **Windows 통합 인증** 또는 **없음**을 선택합니다.

6.  환경의 지원 및 클라이언트 기능에 따라 다음 중 하나 이상을 선택합니다.
    
      - **PIN 인증 사용** - PIN 번호를 사용하여 클라이언트를 인증합니다.
    
      - **인증서 인증 사용** - 이 풀의 서버가 클라이언트에 대한 인증서를 발급합니다.
    
      - **인증서 체인 다운로드 사용** - 인증 인증서가 있는 서버에서 해당 인증서에 대해 인증서 체인을 다운로드하도록 합니다

7.  **커밋**을 클릭합니다.

## 참고 항목

#### 기타 리소스

[Lync Server 2013 제어판에서 보안 구성](lync-server-2013-configuring-authentication-in-the-lync-server-control-panel.md)

