---
title: 기본 사진 옵션 구성
TOCTitle: 기본 사진 옵션 구성
ms:assetid: b1c986f0-6400-447a-9e36-78c1c3a4f793
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Dn205074(v=OCS.15)
ms:contentKeyID: 53901598
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# 기본 사진 옵션 구성

 

_**마지막으로 수정된 항목:** 2013-03-22_

기본적으로 사용자의 사진은 자동으로 표시됩니다. 사용자가 사진을 숨기기 원하는 경우 Lync 클라이언트에서 **내 사진 숨기기** 옵션을 선택할 수 있습니다. 그러나 일부 다른 Office 응용 프로그램에서 이 설정은 무시됩니다.

사용자가 사진을 해제한 경우에도 사진이 표시될 수 있는 가능성이 걱정되는 경우, 사용자의 사진이 기본적으로 표시되지 않도록 Lync 사진 표시 설정을 전체적으로 변경하거나, 사이트 또는 서비스별로 변경할 수 있습니다. 다음 Lync Server 관리 셸 cmdlet을 사용하면 사용자가 클라이언트에서 명시적으로 **내 사진 표시** 옵션을 선택할 때까지 사용자의 사진이 표시되지 않습니다.

    Set-CsPrivacyConfiguration -DisplayPublishedPhotoDefault $False

이 cmdlet에 대한 자세한 내용은 Lync Server 관리 셸 설명서에서 [Set-CsPrivacyConfiguration](set-csprivacyconfiguration.md)을 참고하세요.

