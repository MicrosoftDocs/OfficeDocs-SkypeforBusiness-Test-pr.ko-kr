---
title: 전화 접속 회의 PIN(개인 식별 번호) 규칙 구성
TOCTitle: 전화 접속 회의 PIN(개인 식별 번호) 규칙 구성
ms:assetid: 27b79fb1-e2dc-4f71-bc82-b6eb61be2b16
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg520967(v=OCS.15)
ms:contentKeyID: 49303111
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# 전화 접속 회의 PIN(개인 식별 번호) 규칙 구성

 

_**마지막으로 수정된 항목:** 2012-06-19_

조직에서 AD DS(Active Directory 도메인 서비스) 자격 증명이 있는 Lync Server 2013 사용자는 개인 ID 번호(PIN)를 사용하여 인증된 사용자로 전화 접속 회의에 참가할 수 있습니다. PIN 정책은 전화 접속 회의 PIN의 작동 방식에 대한 규칙을 정의합니다.

사이트나 특정 사용자 그룹에 특정 정책을 적용하려면 새 PIN 정책을 만들면 됩니다. 전체 조직에 대해 동일한 PIN 정책을 사용하려면 전역 PIN 정책을 사용하고 필요에 따라 수정하면 됩니다. PIN 정책은 가장 좁은 범위에서 가장 넓은 범위순으로 사용자에게 적용됩니다. 사용자에게 사용자 수준 PIN 정책을 할당하는 경우에는 해당 설정이 우선적으로 적용됩니다. 사용자 정책을 할당하지 않으면 사이트 수준 PIN 정책(있는 경우)이 적용됩니다. 사용자 정책이나 사이트 정책을 적용하지 않는 경우에는 전역 PIN 정책에서 기본 설정을 제공합니다.

## 이 단원의 내용

  - [Lync Server 2013에서 기본 전화 접속 회의 PIN 설정 수정](lync-server-2013-modify-the-default-dial-in-conferencing-pin-settings.md)

  - [Lync Server 2013에서 사이트 또는 사용자 그룹에 대한 전화 접속 회의 PIN 설정 만들기 또는 수정](lync-server-2013-create-or-modify-dial-in-conferencing-pin-settings-for-a-site-or-group-of-users.md)

  - [사이트 또는 사용자 그룹에 대한 전화 접속 회의 PIN 설정 삭제](lync-server-2013-delete-dial-in-conferencing-pin-settings-for-a-site-or-group-of-users.md)

