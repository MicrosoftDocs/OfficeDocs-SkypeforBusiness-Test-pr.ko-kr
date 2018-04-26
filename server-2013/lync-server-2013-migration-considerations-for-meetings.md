---
title: 모임 마이그레이션 고려 사항
TOCTitle: 모임 마이그레이션 고려 사항
ms:assetid: a9807d58-99a3-4cff-b4c6-74950d106a2b
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg412800(v=OCS.15)
ms:contentKeyID: 61093018
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# 모임 마이그레이션 고려 사항

 

_**마지막으로 수정된 항목:** 2014-02-10_

이 섹션에서는 다음 항목에 대해 설명합니다.

  - Microsoft Lync Server 2013의 모임 변경 사항

  - 회의 요구에 따른 사용자 마이그레이션

  - 기존 모임 및 모임 콘텐츠 마이그레이션

  - Lync Server 2010 마이그레이션 중 사용자 환경

  - Office Communications Server 2007 R2 마이그레이션 중 사용자 환경

  - 이전 서버 버전의 모임에 대한 Microsoft Lync 2013 호환성

## Lync Server 2013의 모임 변경 사항

**Lync Server 2013 기능.**   Lync Server 2013에서는 사용자의 계정이 Lync Server 2013으로 이동되고 사용자가 Lync 2013 클라이언트에 로그인한 후 사용 가능한 새로운 회의 기능이 제공됩니다. 새로운 기능은 [Lync Server 2013의 새로운 회의 기능](lync-server-2013-new-conferencing-features.md) 및 [Lync Server 2013의 새로운 클라이언트 기능](lync-server-2013-what-s-new-for-clients.md)에 설명되어 있습니다.

**모임 URL.**   Lync Server 2010에서와 마찬가지로, Lync Server 2013에서 새로 예약된 모든 모임에는 https:// URL 접두사가 지정되고 기존 모임은 사용자의 계정과 함께 마이그레이션됩니다. 하지만 Lync Server 2013에서는 Office Communications Server 2007 R2 회의 통화(conf:// URL 접두사) 또는 웹 회의(meet:// URL 접두사)가 지원되지 않습니다. 자세한 내용은 이 항목 뒷부분의 "Office Communications Server 2007 R2에서 모임 마이그레이션"을 참고하세요.

**클라이언트 지원.**   Lync Server 2010과 달리, Lync Server 2013에서는 회의에 대해 Office Communicator 클라이언트가 지원되지 않습니다. 다음 클라이언트를 사용해서는 Lync 2013용 온라인 모임 추가 기능을 통해 예약된 모임에 참가할 수 없습니다.

  - Office Communicator 2007 R2

  - Microsoft Office Communications Server 2007 R2 Attendant

  - Office Communicator 2007

  - Office Live Meeting 2007

마이그레이션 중 Office Communicator 2007 R2 사용자는 해당 클라이언트가 업그레이드될 때까지는 Lync Server 2013 모임에 참가하려면 Lync Web App 2013을 사용해야 합니다. Office Communicator 2007 R2 사용자의 경우 해당 기존 클라이언트를 계속 사용하여 Lync Server 2013의 현재 상태 및 메신저 기능을 이용할 수 있지만 회의 기능은 지원되지 않습니다.


## 회의 요구에 따른 사용자 마이그레이션

**자주 사용되는 모임 이끌이.**   자주 사용되는 모임 이끌이가 [Lync Server 2013의 새로운 회의 기능](lync-server-2013-new-conferencing-features.md) 및 [Lync Server 2013의 새로운 클라이언트 기능](lync-server-2013-what-s-new-for-clients.md)에 설명된 새로운 Lync Server 2013 및 Lync 2013 기능을 활용할 수 있도록 프로세스 초기에 해당 모임 이끌이를 마이그레이션할 수 있습니다.

**Live Meeting 사용자.**   Office Communications Server 2007 R2에서 마이그레이션하는데 Live Meeting 관련 웹 회의 기능(특히 대규모 모임 및 대화방 즉시 시작 지원)이 필요한 사용자가 있는 경우 다음 옵션을 사용할 수 있습니다.

  - 조직에서 사용 가능한 경우 이끌이가 Live Meeting 서비스를 사용하도록 합니다.

  - 서버 기반 Live Meeting 웹 회의를 예약할 수 있도록 이전 버전의 Office Communications Server에 있는 이끌이를 그대로 둡니다.

## 기존 모임 및 모임 콘텐츠 마이그레이션

## Lync Server 2010에서 모임 마이그레이션

Lync Server 2010에서 Lync Server 2013으로 사용자를 이동하는 경우 다음 정보가 사용자의 계정과 함께 이동합니다.

  - 사용자가 이미 예약한 모임. 회의 디렉터리 및 회의 데이터가 포함됩니다.

  - 사용자의 PIN(개인 ID 번호).   사용자의 현재 PIN은 만료되거나 사용자가 새 PIN을 요청할 때까지 계속 작동합니다.

하지만 다음과 같은 사용자 계정 정보는 새 서버로 이동하지 않습니다.

  - 모임 콘텐츠(예: PowerPoint 프레젠테이션, 화이트보드 콘텐츠, 설문 데이터

모임에서 공유한 콘텐츠를 이동하려면 Move-CsUser cmdlet의 MoveMeetingContent 매개 변수를 사용합니다. 이 cmdlet을 사용하는 방법에 대한 자세한 내용은 Lync Server 2013 cmdlet 설명서의 [Move-CsUser](move-csuser.md)를 참고하세요.

## Office Communications Server 2007 R2에서 모임 마이그레이션

Office Communications Server 2007 R2 모임은 회의 통화(conf:// URL 접두사) 또는 웹 회의(meet:// URL 접두사)입니다. Lync Server 2013에서는 이러한 기존 conf:// 및 meet:// 회의가 지원되지 않으며, 이러한 회의는 사용자 계정과 함께 마이그레이션되지 않습니다. 마이그레이션한 후에는 사용자가 예약한 모든 온라인 모임에 대한 링크를 업데이트하도록 안내해야 합니다. 예약된 모임 초대를 열어서 Lync 2013 클라이언트를 설치하여 모임 URL을 업데이트하고 참가자에게 초대를 다시 보낸 후에 이를 수행할 수 있습니다.

## Lync Server 2010 마이그레이션 중 사용자 환경

이 섹션에서는 Lync 2010에서 마이그레이션하는 경우 사용자의 회의 환경에 대해 요약하여 설명합니다. Lync Server 2013 클라이언트를 함께 사용하고 이전 클라이언트 및 서버 버전과 상호 작용하는 방법에 대한 자세한 내용은 [Lync 2013 에서 클라이언트 상호 운용성](lync-server-2013-client-interoperability-in-lync-2013.md)을 참고하세요.

## Lync 2013 클라이언트를 사용하여 Lync Server 2010 모임 참가

Lync Server 2010에서 마이그레이션하는 동안 일정 기간 동안 사용자가 Lync 2013 클라이언트를 사용하여 Lync Server 2010 모임에 참가할 수도 있습니다. 이러한 사용자는 Lync 2013 클라이언트 기능에 액세스할 수 있지만 다음과 같은 예외가 적용됩니다.

  - 모임 창에서 사람 아이콘을 가리켜 액세스할 수 있는 **참가자** 관리 옵션에서는 **모임 메신저 없음** 옵션이 작동하지 않습니다.

  - 비디오 회의에서는 갤러리 보기가 작동하지 않습니다. 사용자에게는 모든 발표자 대신 활성 발표자만 표시됩니다. **레이아웃 선택** 옵션 목록에서는 **갤러리 보기**를 사용할 수 없습니다.

  - 비디오 회의에서는 참가자 목록이 기본적으로 표시됩니다.

  - 참가자 목록에서 사용자를 마우스 오른쪽 단추로 클릭하면 **비디오 스포트라이트 잠금** 및 **갤러리에 고정** 참가자 관리 옵션을 사용할 수 없습니다.

## Office Communications Server 2007 R2 마이그레이션 중 사용자 환경

이 섹션에서는 Office Communications Server 2007 R2에서 마이그레이션하는 경우 Lync 2013을 설치하기 전후의 사용자 회의 환경에 대해 요약하여 설명합니다. Lync Server 2013 클라이언트를 함께 사용하고 이전 클라이언트 및 서버 버전과 상호 작용하는 방법에 대한 자세한 내용은 [Lync 2013 에서 클라이언트 상호 운용성](lync-server-2013-client-interoperability-in-lync-2013.md)을 참고하세요.

## 사용자 계정이 마이그레이션된 후, Lync 2013을 설치하기 전

사용자가 Lync Server 2013 서버로 마이그레이션된 후 새 클라이언트가 설치되기 전에는 Office Communicator 2007 R2 사용자가 해당 기존 클라이언트를 계속 사용하여 Lync Server 2013의 현재 상태 및 메신저 기능을 이용할 수 있지만 회의 기능은 지원되지 않습니다.

## 사용자 계정이 마이그레이션되고 Lync 2013을 설치한 후

마이그레이션된 사용자가 Lync 2013을 설치하면 Lync 2013용 온라인 모임 추가 기능도 설치됩니다. 이 경우 다음과 같은 효과가 있습니다.

  - 이후에 예약된 모든 모임에는 기존 meet:// Live Meeting 주소 대신 https:// 주소를 사용하는 새 모임 형식이 사용됩니다.

  - Lync 2013의 IT 관리 배포에서 관리자는 Live Meeting 서버 및 서비스 기반 모임을 예약하는 데 사용되는 Microsoft Office Outlook용 회의 추가 기능을 제거할 수 있습니다. 하지만 Live Meeting 서비스 모임을 계속 예약해야 하는 사용자가 있을 수 있습니다. 이 경우 두 추가 기능의 동시 사용을 허용할 수 있습니다.

## 이전 클라이언트를 사용하는 페더레이션된 조직과의 모임

Microsoft Office Communicator 2007을 사용하는 페더레이션 조직의 사용자는 Lync Server 2013 모임이 이끌이에 의해 잠겨 있는 경우 해당 모임에 참가할 수 없습니다. 페더레이션 참가자가 새 https:// 모임 URL을 사용하여 모임에 참가하는 경우 Lync Web App을 사용할 수 있도록 이러한 모임을 Lync Server 2013에서 다시 예약해야 합니다.

