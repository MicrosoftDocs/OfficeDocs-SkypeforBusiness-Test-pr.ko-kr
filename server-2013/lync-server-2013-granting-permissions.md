---
title: 'Lync Server 2013: 사용 권한 부여'
TOCTitle: 사용 권한 부여
ms:assetid: d1c9ea66-bd07-480e-99a0-011108f97e42
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg398901(v=OCS.15)
ms:contentKeyID: 49305109
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Lync Server 2013에서 사용 권한 부여

 

_**마지막으로 수정된 항목:** 2012-10-15_

설치의 경우 특정 Active Directory OU(조직 구성 단위)에 대한 RTCUniversalServerAdmins 유니버설 그룹에 사용 권한을 부여하여 해당 OU의 RTCUniversalServerAdmins 그룹의 구성원이 지정된 도메인에서 Lync Server 2013을 설치할 수 있습니다. OU에 대한 사용 권한을 부여하는 경우 다음 사용 권한이 부여됩니다.

  - 읽기

  - 쓰기

  - ReadSPN

  - WriteSPN

관리의 경우 지정된 OU에 사용 권한을 추가하여 포리스트 준비에서 만들어진 RTC 유니버설 그룹의 구성원이 Domain Admins 그룹의 구성원 자격 없이 OU에 액세스할 수 있습니다. 지정된 OU에 추가된 사용 권한은 **Enable-CsAdDomain** cmdlet가 컴퓨터 및 사용자 OU 컨테이너에 추가하는 사용 권한과 동일합니다.

## 이 섹션의 내용

  - [Lync Server 2013에서 설치 권한 부여](lync-server-2013-granting-setup-permissions.md)

  - [Lync Server 2013에서 조직 구성 단위 권한 부여](lync-server-2013-granting-organizational-unit-permissions.md)

