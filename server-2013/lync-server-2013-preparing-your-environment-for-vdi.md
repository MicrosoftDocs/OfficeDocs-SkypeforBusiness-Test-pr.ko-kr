---
title: 'Lync Server 2013: VDI에 대한 환경 준비'
TOCTitle: VDI에 대한 환경 준비
ms:assetid: a3ec2e13-1a73-4b1c-a54a-8db7d4cd50f9
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/JJ205154(v=OCS.15)
ms:contentKeyID: 49304599
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# VDI에 대한 Lync Server 2013 환경 준비

 

_**마지막으로 수정된 항목:** 2013-02-22_

Lync VDI 플러그인을 위한 환경을 준비하려면 다음 단계를 수행해야 합니다.

1.  Lync Server 2013에서 EnableMediaRedirection이 모든 VDI 사용자에 대해 TRUE로 설정되어 있는지 확인합니다. 자세한 내용은 [New-CsClientPolicy](https://docs.microsoft.com/en-us/powershell/module/skype/New-CsClientPolicy) cmdlet 및 [Set-CsClientPolicy](https://docs.microsoft.com/en-us/powershell/module/skype/Set-CsClientPolicy) cmdlet의 도움말 항목을 참고하세요.

2.  데이터 센터 컴퓨터에서 모든 가상 컴퓨터에 Lync 2013 클라이언트를 설치합니다.

3.  로컬 컴퓨터에서 Lync VDI 플러그인을 설치합니다.

