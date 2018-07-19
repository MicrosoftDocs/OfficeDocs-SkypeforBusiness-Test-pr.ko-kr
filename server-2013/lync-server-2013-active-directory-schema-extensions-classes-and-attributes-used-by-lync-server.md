---
title: 'Lync Server 2013: Lync Server에서 사용하는 Active Directory 스키마 확장, 클래스 및 속성'
TOCTitle: Lync Server 2013에서 사용하는 Active Directory 스키마 확장, 클래스 및 속성
ms:assetid: 579bfa5a-9443-46dd-9a8e-07d00ba2824d
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg398379(v=OCS.15)
ms:contentKeyID: 49303694
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Lync Server 2013에서 사용하는 Active Directory 스키마 확장, 클래스 및 속성

 

_**마지막으로 수정된 항목:** 2012-06-19_

이 참조 섹션에서 다루는 내용은 다음과 같습니다.

  - Lync Server 2013에서 새롭게 제공되거나 변경된 Active Directory 스키마 확장
    
    Active Directory 스키마에는 Active Directory 포리스트에서 만들어질 수 있는 모든 개체 클래스에 대한 형식 정의가 들어 있습니다. 또한 Active Directory 개체에서 가능한 모든 특성에 대한 형식 정의도 포함되어 있습니다. Active Directory 전역 카탈로그에는 포리스트의 모든 개체에 대한 복제본이 각 개체의 일부 특성과 함께 들어 있습니다. 이 섹션에서는 Lync Server 2013에서 새롭게 제공되거나 변경된 클래스 및 특성에 대해 설명합니다.

  - Lync Server에서 사용하는 모든 클래스 및 각 클래스에 대한 설명

  - Lync Server에서 사용하는 모든 특성 및 각 특성에 대한 설명

  - Lync Server에서 사용하는 클래스 목록 및 각 클래스가 포함할 수 있는 특성

  - 포리스트 준비 도중 생성되는 유니버설 서비스 및 관리 그룹과 전역 설정 및 개체

  - 도메인 준비 도중 도메인 루트 및 기본 제공 컨테이너에 대해 생성되는 ACE(액세스 제어 항목)

  - Active Directory OU(조직 구성 단위)에서 Grant\_CsSetupPermission cmdlet으로 수행한 변경 내용

  - Active Directory OU에서 Grant\_CsOUPermission cmdlet으로 수행한 변경 내용

## 이 섹션의 내용

  - [Lync Server 2013의 스키마 변경 사항](lync-server-2013-schema-changes-in-lync-server-2013.md)

  - [Lync Server 2013의 스키마 클래스 및 설명](lync-server-2013-schema-classes-and-descriptions.md)

  - [Lync Server 2013의 스키마 특성 및 설명](lync-server-2013-schema-attributes-and-descriptions.md)

  - [Lync Server 2013의 클래스별 스키마 특성](lync-server-2013-schema-attributes-by-class.md)

  - [Lync Server 2013에서 포리스트 준비로 인한 변경](lync-server-2013-changes-made-by-forest-preparation.md)

  - [Lync Server 2013에서 도메인 준비로 인한 변경](lync-server-2013-changes-made-by-domain-preparation.md)

  - [Lync Server 2013에서 Grant-CsSetupPermission으로 인한 변경](lync-server-2013-changes-made-by-https://docs.microsoft.com/en-us/powershell/module/skype/Grant-CsSetupPermission)

  - [Lync Server 2013에서 Grant-CsOUPermission으로 인한 변경](lync-server-2013-changes-made-by-https://docs.microsoft.com/en-us/powershell/module/skype/Grant-CsOUPermission)

