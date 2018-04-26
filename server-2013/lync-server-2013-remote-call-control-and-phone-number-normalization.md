---
title: 'Lync Server 2013: 원격 통화 제어 및 전화 번호 정규화'
TOCTitle: 원격 통화 제어 및 전화 번호 정규화
ms:assetid: 291d9e87-4c65-4ea2-888f-517741391de5
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg558630(v=OCS.15)
ms:contentKeyID: 49303128
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Lync Server 2013의 원격 통화 제어 및 전화 번호 정규화

 

_**마지막으로 수정된 항목:** 2012-09-22_

Lync 클라이언트는 ABS(주소록 서비스) 파일 다운로드의 일부분으로 전화 번호 정규화 규칙을 다운로드합니다. 원격 통화 제어 시나리오에서 주소록 서비스 전화 번호 정규화 규칙은 수신 및 발신 원격 통화 제어 통화에 모두 적용됩니다. 원격 통화 제어를 사용하도록 설정한 사용자에 대한 수신 전화의 경우에는 먼저 발신자의 전화 번호가 SIP/CSTA 게이트웨이 또는 PBX(Private Branch Exchange)를 통해 E.164 형식으로 정규화됩니다. Lync Server 2013은 게이트웨이에서 전화를 받으면 발신자 전화 번호에 대해 주소록 서비스에 저장된 GAL(전체 주소 목록) 또는 수신자의 Microsoft Office Outlook 연락처 목록에 있는 정규화된 번호에 대한 RNL(역방향 번호 조회)을 수행합니다. 역방향 번호 조회에서 일치하는 항목이 검색되면 발신자가 수신 전화 알림에 이름으로 표시됩니다.

발신 원격 통화 제어 통화의 경우에는 Lync에서 전화를 건 번호에 대해 주소록 서비스 전화 번호 정규화 규칙을 적용한 후에 SIP/CSTA 게이트웨이로 통화를 라우팅합니다.

원격 통화 제어용 전화 번호 정규화 규칙을 만드는 방법에 대한 자세한 내용은 계획 설명서에서 [Lync Server 2013의 다이얼 플랜 및 정규화 규칙](lync-server-2013-dial-plans-and-normalization-rules.md)을 참조하십시오.

## 전화 번호 정규화 규칙 마이그레이션

이전에 원격 통화 제어를 사용하도록 설정한 사용자를 마이그레이션하는 경우 마이그레이션 설명서에서 다음 항목을 참조하십시오.

  - Lync Server 2010의 경우 마이그레이션 설명서에서 [주소록 마이그레이션](migrate-address-book.md)을 참조하십시오.

  - Communications Server 2007 R2의 경우 마이그레이션 설명서에서 [주소록 마이그레이션](migrate-address-book_1.md)을 참조하십시오.

