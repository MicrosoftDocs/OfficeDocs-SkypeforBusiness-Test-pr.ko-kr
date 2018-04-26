---
title: Lync 2013용 그룹 정책 설정
TOCTitle: Lync 2013용 그룹 정책 설정
ms:assetid: 5917a52b-dae0-4ec0-8548-a68dc20ab71c
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/JJ204924(v=OCS.15)
ms:contentKeyID: 49303719
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Lync 2013용 그룹 정책 설정

 

_**마지막으로 수정된 항목:** 2012-10-03_

이전 버전의 Lync 및 Office Communicator에서는 독립 실행형 Communicator.adm 관리 템플릿을 사용하여 클라이언트 그룹 정책 설정을 구성할 수 있었습니다. Lync 2013에서는 Office 그룹 정책 관리 템플릿과 함께 새로운 관리 템플릿(.admx 및 .adml 파일)이 포함됩니다. Lync 2013 .admx 및 .adml 파일을 사용해서 모든 Office 프로그램 및 언어 팩에 대한 템플릿을 다운로드하고 그룹 정책 설정을 중앙에서 관리할 수 있습니다. 자세한 내용은 [http://go.microsoft.com/fwlink/?linkid=267516\&clcid=0x412](http://go.microsoft.com/fwlink/?linkid=267516%26clcid=0x412)에서 Office 2013 설명서의 "Office 2013 관리 템플릿 파일(ADMX, ADML)"을 참조하십시오.

## 클라이언트 부트스트래핑 정책

사용자가 처음으로 서버에 로그인하기 전에 구성해야 하는 여러 가지 클라이언트 부트스트랩 정책이 있습니다. 이러한 정책은 클라이언트가 로그인하여 서버로부터 인밴드 프로비전 설정을 받기 전에 적용되므로, 그룹 정책을 사용하여 구성할 수 있습니다. 자세한 내용은 배포 설명서에서 [Lync Server 2013에서 클라이언트 부트스트랩 정책 구성](lync-server-2013-configuring-client-bootstrapping-policies.md)을 참조하십시오.

