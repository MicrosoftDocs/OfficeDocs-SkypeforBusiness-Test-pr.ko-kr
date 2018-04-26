---
title: 'Lync Server 2013: 포리스트 준비'
TOCTitle: 포리스트 준비
ms:assetid: 3d188fcb-c64e-46cf-a3a7-9e3ebefed7fd
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg425898(v=OCS.15)
ms:contentKeyID: 49303390
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Lync Server 2013에 대한 포리스트 준비

 

_**마지막으로 수정된 항목:** 2013-02-21_

포리스트 준비는 Lync Server 2013에서 사용할 Active Directory 전역 설정과 개체 및 Active Directory 유니버설 그룹을 만들고, Active Directory 개체에 대한 적합한 액세스 권한을 부여합니다. 포리스트 준비를 통해 만들어지는 유니버설 그룹과 전역 설정 및 개체에 대한 설명은 [Lync Server 2013에서 포리스트 준비로 인한 변경](lync-server-2013-changes-made-by-forest-preparation.md)을 참조하십시오.

포리스트 준비에서는 또한 속성 집합을 포함하고 Lync Server 2013에서 사용되는 지정자를 표시하는 개체를 만들고 이를 구성 컨테이너에 저장합니다.


> [!IMPORTANT]
> 포리스트 준비 절차를 수행하기 전에 스키마 준비 변경 내용이 모든 도메인 컨트롤러로 복제되었는지 확인합니다. 복제가 완료되지 않은 경우 오류가 발생합니다.



새로운 Lync Server 배포를 수행하는 경우 구성 컨테이너에 전역 설정을 저장해야 합니다. 이전 버전에서 업그레이드 중이고 전역 설정을 시스템 컨테이너에 저장할 경우에는 시스템 컨테이너를 계속 사용할 수 있습니다.

이 절차를 수행하려면 포리스트 루트 도메인의 Enterprise Admins 또는 Domain Admins 그룹 구성원이어야 합니다.

## 이 단원의 내용

  - [Lync Server 2013에 대한 포리스트 준비 실행](lync-server-2013-running-forest-preparation.md)

  - [Lync Server 2013에 대해 Cmdlet을 사용하여 포리스트 준비 되돌리기](lync-server-2013-using-cmdlets-to-reverse-forest-preparation.md)

