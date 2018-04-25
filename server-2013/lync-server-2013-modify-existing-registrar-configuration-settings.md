---
title: 기존 고급 등록자 구성 설정 수정
TOCTitle: 기존 고급 등록자 구성 설정 수정
ms:assetid: a8931511-3e66-49ed-a3ec-03bcd61ce1f0
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg182566(v=OCS.15)
ms:contentKeyID: 49304654
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# 기존 고급 등록자 구성 설정 수정

 

_**마지막으로 수정된 항목:** 2012-11-01_

등록자를 사용하여 프록시 서버 인증 프토토콜을 구성할 수 있습니다. 사용 가능한 프로토콜에 대한 자세한 내용은 [고급 등록자 구성 설정 만들기](lync-server-2013-create-registrar-configuration-settings.md)를 참조하십시오.


> [!NOTE]
> 서버에서 원격 클라이언트 및 엔터프라이즈 클라이언트 둘 다에 대한 인증을 지원할 경우 Kerberos 및 NTLM을 모두 사용하도록 설정하는 것이 좋습니다. 이렇게 하면 원격 클라이언트에는 NTLM 인증만 제공되도록 에지 서버와 내부 서버가 통신합니다. 이 서버에서 Kerberos만 사용하도록 설정한 경우에는 원격 사용자를 인증할 수 없습니다. 서버에 대해 엔터프라이즈 사용자를 인증할 경우에도 Kerberos가 사용됩니다.



다음 단계에 따라 기존의 등록자를 수정할 수 있습니다.

## 기존의 등록자를 수정하려면

1.  RTCUniversalServerAdmins 그룹의 구성원인 사용자 계정(또는 이와 동일한 사용자 권한을 가진 사용자 계정)이나 CsServerAdministrator 또는 CsAdministrator 역할이 할당된 사용자 계정에서 Lync Server 2013을 배포한 네트워크에 있는 컴퓨터에 로그온합니다.

2.  브라우저 창을 연 다음 Admin URL을 입력하여 Lync Server 제어판을 엽니다. Lync Server 제어판을 시작하는 데 사용할 수 있는 다양한 방법에 대한 자세한 내용은 [Lync Server 관리 도구 열기](lync-server-2013-open-lync-server-administrative-tools.md)를 참조하세요.

3.  왼쪽 탐색 표시줄에서 **보안**, **등록자**를 차례로 클릭합니다.

4.  **등록자** 페이지에서 서비스를 클릭하고 **편집**, **자세한 정보 표시**를 차례로 클릭합니다.

5.  환경의 지원 및 클라이언트 기능에 따라 **등록자 설정 편집**에서 다음 중 하나 이상을 선택합니다.
    
      - **Kerberos 인증 사용** - 이 풀의 서버가 Kerberos 인증을 사용하여 시도합니다.
    
      - **NTLM 인증 사용** - 이 풀의 서버가 NTLM을 사용하여 시도합니다.
    
      - **인증서 인증 사용** - 이 풀의 서버가 클라이언트에 대한 인증서를 발급합니다.

6.  **커밋**을 클릭합니다.

