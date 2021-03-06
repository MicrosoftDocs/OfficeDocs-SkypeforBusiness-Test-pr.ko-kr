﻿---
title: 'Lync Server 2013: Lync 채팅방 시스템 관리 웹 포털 사용'
TOCTitle: Lync 채팅방 시스템 관리 웹 포털 사용
ms:assetid: c387b2a3-3e42-4642-af72-88126ed2820f
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Dn743660(v=OCS.15)
ms:contentKeyID: 62269006
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Lync Server 2013에서 Lync 채팅방 시스템 관리 웹 포털 사용

 

_**마지막으로 수정된 항목:** 2014-11-10_

LRS를 서버에 배포한 후 브라우저에서 LRS 관리 웹 포털에 로그인하여 모든 LRS 채팅방의 상태를 확인할 수 있습니다.

## 로그인

1.  다음 URL로 이동합니다.
    
    https://\<fe-server\>/lrs

2.  LRSSupport 계정 또는 LRSSupportAdminGroup 보안 그룹에 추가된 계정의 자격 증명을 입력합니다.

![Lync Room System 관리 포털 로그인 화면](images/Dn436326.050bcf70-2f3b-46b2-9b96-ebd12679b713(OCS.15).png "Lync Room System 관리 포털 로그인 화면")

## LRS 관리 웹 포털 요약 페이지

요약 페이지에서는 서버에 배포된 모든 LRS 채팅방에 대한 다음 정보를 제공합니다.

  - **태그**   관리자가 채팅방에 부여한 사용자 지정 이름입니다. 채팅방 이름을 클릭하여 포털에서 태그를 설정할 수 있습니다.

  - **상태**   채팅방의 상태 집계 상태에서 가져온 채팅방 상태이며, 채팅방 설정 페이지의 상태 섹션에 표시됩니다.

  - **다음 모임**   다음 모임이 예정된 날짜와 시간입니다.

  - **LRS 버전, 제조업체, 모델**   이 값은 LRS에 미리 설정되어 있습니다. 제조업체에 따라 이 필드가 공백으로 남겨질 수 있습니다.

  - **마지막 새로 고침**   웹 페이지를 마지막으로 새로 고친 시간입니다.

![Lync Room System 관리 포털 요약 보기](images/Dn743660.f829ce90-dd95-4725-bd94-6870c5dcf046(OCS.15).png "Lync Room System 관리 포털 요약 보기")

## LRS 채팅방 정보

포털의 채팅방 정보 섹션을 통해 각 LRS 채팅방을 보고 구성할 수 있습니다. 여기에는 설정, 세부 정보, 로깅, 상태의 4가지 섹션이 있습니다.

## 설정

설정 섹션에서는 암호, 채팅방 태그, 채팅방의 기본 볼륨 수준을 설정할 수 있습니다. 이러한 설정을 구성하는 경우 LRS 콘솔을 다시 시작해야만 변경 내용이 적용됩니다.

![Lync Room System 관리 포털 채팅방 설정](images/Dn743660.ab162e19-41ac-4991-9b2a-92575aa53eda(OCS.15).png "Lync Room System 관리 포털 채팅방 설정")

## 세부 정보

세부 정보 섹션에서는 마지막으로 새로 고친 시간, 다음 모임, 마지막 업데이트, 유지 관리 및 보정, 기본 스피커, 마이크 및 신호음 설정, 버전, SIP URI, 화면 수 및 각 화면에 대한 세부 정보, 상태 및 작업 등 LRS 대화방 설정의 읽기 전용 요약을 제공합니다.

![Lync Room System 관리 포털 세부 정보 보기](images/Dn743660.2958bbba-db74-4670-a920-87fdfb2fc22d(OCS.15).png "Lync Room System 관리 포털 세부 정보 보기")

## 로깅

로깅 섹션을 사용하여 로그를 원격으로 수집하고 지정된 위치에 저장할 수 있습니다. LRS 콘솔(LRS 사용자 인터페이스)을 다시 시작하거나 전체 시스템을 다시 시작할 수도 있습니다.

![Lync Room System 관리 포털 채팅방 로깅](images/Dn743660.749aee71-deaa-4ace-a146-fe2b349f0f42(OCS.15).png "Lync Room System 관리 포털 채팅방 로깅")

## 상태

상태 섹션에서는 Lync Server 연결, 오디오 장치, 비디오 장치, 복원 상태, 화면 장치의 상태를 시각적으로 확인할 수 있습니다.

![Lync Room System 관리 포털 채팅방 상태](images/Dn743660.8cc644f8-8e3e-42d5-9079-045d8fe9daa7(OCS.15).png "Lync Room System 관리 포털 채팅방 상태")

## 관리 웹 포털에 대한 추가 설명


> [!NOTE]
> <UL>
> <LI>
> <P>보안상의 이유로 관리 웹 포털은 15분마다 자동으로 로그아웃됩니다.</P>
> <LI>
> <P>설정 변경 내용은 LRS 시스템을 다시 시작한 후에만 적용됩니다.</P>
> <LI>
> <P>LRS 관리 웹 포털의 알림은 고정되어 있으며 사라지지 않습니다.</P>
> <LI>
> <P>알림은 페이지를 새로 고친 후에만 나타납니다.</P>
> <LI>
> <P>LRS 채팅방 상태는 페이지를 새로 고친 후에 나타납니다.</P>
> <LI>
> <P>LRSApp 계정 암호가 만료되면 채팅방 상태를 볼 수 없게 됩니다. LRSAppuser 계정 암호가 만료되지 않도록 구성하고 만료 기간이 가까워지면 암호를 업데이트해야 합니다.</P>
> <LI>
> <P>LRS 관리 웹 포털은 온-프레미스 배포에 대해서만 지원됩니다.</P></LI></UL>



## 문제 해결

## 관리 웹 포털에 로그인할 수 없는 이유는 무엇인가요?

  - https://localhost/lrs를 열면 로그인 페이지가 표시되지만 자격 증명을 입력해도 로그인할 수 없습니다. 이 경우 https://FQDNofFEserver/lrs를 열어 관리 웹 포털에 로그인해야 합니다.

  - 작업 그룹에 관리 웹 포털에 액세스 중인 컴퓨터가 있는 경우 "http://"가 작동하지 않습니다. 대신 "https"를 사용하세요.

## 관리 웹 포털에 LRS가 표시되지 않는 이유는 무엇인가요?

  - 배포에 LRS 계정이 있으며 LRS 관리 웹 포털 배포 권장 사항에 따라 계정을 만들었는지 확인하세요. LRS 계정은 Lync 서버에서 Enable-CsUser가 아닌 Enable-CsMeetingRoom을 사용하여 생성해야 합니다.

  - LRS 계정을 만들었지만 해당 계정을 관리 웹 포털에서 볼 수 없는 경우, 선택한 **MeetingPortal** 구성 요소와 함께 Lync Server 로깅 도구를 사용하여 서버 로그를 수집한 다음 LRS 지원 담당 부서로 보내세요.

## 관리 웹 포털에서 LRS 상태가 표시되지 않는 이유는 무엇인가요?

  - LRSApp 사용자 계정이 SIP을 사용하도록 설정되어 있는지 확인하세요.

  - 여전히 문제가 발생하면 D:\\Tracing\\LRSAdminLogs\\에서 LRS 시스템의 **Trace.log** 파일을 수집한 다음 LRS 지원 담당 부서로 보내세요.

