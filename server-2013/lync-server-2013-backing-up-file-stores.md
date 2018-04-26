---
title: 파일 저장소 백업
TOCTitle: 파일 저장소 백업
ms:assetid: 1a7f4e93-aa3d-461e-878e-2c572baa1293
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Hh202167(v=OCS.15)
ms:contentKeyID: 52056797
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# 파일 저장소 백업

 

_**마지막으로 수정된 항목:** 2013-02-17_

Lync Server 파일 저장소를 백업하면 Lync Server 구성 요소에서 사용되는 모든 파일 및 폴더가 포함됩니다.

## 파일 저장소를 백업하려면

1.  Lync Server 파일 저장소의 특정 위치를 찾으려면 토폴로지 작성기를 열고 **파일 저장소** 노드를 확인합니다.

2.  Robocopy 또는 다른 파일 시스템 관리 도구를 사용하여 각 파일 저장소를 $Backup\\filestore에 복사합니다.

