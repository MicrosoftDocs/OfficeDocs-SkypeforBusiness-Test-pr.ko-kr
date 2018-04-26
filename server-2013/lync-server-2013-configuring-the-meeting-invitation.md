---
title: Lync Server 2013에서 모임 초대 구성
TOCTitle: Lync Server 2013에서 모임 초대 구성
ms:assetid: 7faa4797-0344-418b-9fa3-59dfb9c2baf7
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg398638(v=OCS.15)
ms:contentKeyID: 49304180
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Lync Server 2013에서 모임 초대 구성

 

_**마지막으로 수정된 항목:** 2013-07-16_

모임 초대 본문에 다음과 같은 선택적인 항목을 포함하여 Lync 2013용 온라인 모임 추가 기능에서 보내는 모임 초대를 사용자 지정할 수 있습니다.

  - **조직의 로고** 로고 URL 옵션을 사용해서 모임 초대에 조직의 로고를 추가합니다. 모임 초대를 조직 외부의 사용자에게 전송할 경우, 공개적으로 사용 가능한 URL에 이미지를 배치해야 합니다. 지원되는 이미지 형식은 GIF 및 JPG입니다. Lync Server 2013은 이미지에 대한 크기 제한 없이 URL을 저장하지만 최적의 결과를 위해서는 이미지의 최대 크기를 30 x 188 픽셀로 제한해야 합니다.

  - **사용자 지정 도움말 또는 지원 링크** 조직의 도움말 또는 지원 팀 웹 사이트에 대한 URL을 추가합니다. 모임 초대를 조직 외부의 사용자에게 전송할 경우 URL은 공개적으로 사용할 수 있는 URL이어야 합니다. 최대 URL 길이는 1KB입니다.

  - **법적 고지 사항 텍스트** 모든 모임 초대에 표시할 법률 텍스트 또는 고지 사항에 대한 URL을 추가합니다. 모임 초대를 조직 외부의 사용자에게 전송할 경우 URL은 공개적으로 사용할 수 있는 URL이어야 합니다. 최대 URL 길이는 1KB입니다.

  - **사용자 지정 바닥글 텍스트** 초대에서 사용자 지정 바닥글로 렌더링할 텍스트를 추가합니다. 추가할 수 있는 최대 텍스트 길이는 2KB입니다.

이러한 옵션은 Lync Server 제어판 또는 Lync Server 관리 셸을 사용하여 구성할 수 있습니다.


**Lync Server 제어판을 사용하여 모임 초대를 사용자 지정하려면**

1.  RTCUniversalServerAdmins 그룹의 구성원인 사용자 계정(또는 이와 동일한 사용자 권한을 가진 사용자 계정)이나 CsServerAdministrator 또는 CsAdministrator 역할이 할당된 사용자 계정에서 Lync Server 2013을 배포한 네트워크에 있는 컴퓨터에 로그온합니다.

2.  브라우저 창을 연 다음 Admin URL을 입력하여 Lync Server 제어판을 엽니다. Lync Server 제어판을 시작하는 데 사용할 수 있는 다양한 방법에 대한 자세한 내용은 [Lync Server 관리 도구 열기](lync-server-2013-open-lync-server-administrative-tools.md)를 참조하세요.

3.  왼쪽 탐색 표시줄에서 **회의**, **모임 구성**을 차례로 클릭합니다.

4.  **모임 구성** 페이지에서 **새로 만들기**를 클릭하고 다음 중 하나를 수행합니다.
    
      - 사이트 수준 정책을 만들려면 **사이트 구성**을 클릭합니다. **사이트 선택** 검색 필드에 모임 참가 설정을 정의할 사이트의 이름 일부나 전체를 입력합니다. 사이트 결과 목록에서 원하는 사이트를 클릭한 다음 **확인**을 클릭합니다.
    
      - 풀 수준 정책을 만들려면 **풀 구성**을 클릭합니다. **서비스 선택** 검색 필드에 모임 참가 설정을 정의할 풀 서비스의 이름 일부나 전체를 입력합니다. 서비스 결과 목록에서 원하는 풀을 클릭하고 **확인**을 클릭합니다.

5.  다음을 수행합니다.
    
      - **로고 URL** 필드에 조직의 로고 이미지에 대한 URL을 입력합니다.
    
      - **도움말 URL** 필드에 조직의 도움말 또는 지원 사이트에 대한 URL을 입력합니다.
    
      - **법적 고지 사항** 필드에 모임 초대에 포함하려는 법적 고지 사항에 대한 URL을 입력합니다.
    
      - **사용자 지정 바닥글 텍스트** 필드에 최대 2KB의 바닥글 텍스트를 입력합니다.

**Lync Server 관리 셸을 사용하여 모임 초대를 사용자 지정하려면**

1.  Lync Server 관리 셸 시작: **시작**, **모든 프로그램**, **Microsoft Lync Server 2013**을 차례로 클릭한 다음 **Lync Server 관리 셸**을 클릭합니다.

2.  **New-CsMeetingConfiguration** 또는 **Set-CsMeetingConfiguration** cmdlet을 실행하여 모임 초대 옵션을 만들거나 구성합니다. 예를 들어 다음을 실행합니다.
    
        New-CsMeetingConfiguration -Identity site:Redmond -EnableInviteCustomization $True -LogoURL "http://www.contoso.com/logo/contosobanner.gif" -HelpURL "http://www.contoso.com/support" -LegalURL "http://www.contoso.com/disclaimer" -CustomFooterText "Communications may be monitored or recorded."

