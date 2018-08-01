---
title: 'Lync Server 2013: Lync 클라이언트 소프트웨어 지원'
TOCTitle: Lync 클라이언트 소프트웨어 지원
ms:assetid: a6851e38-ba9a-4f19-9aa7-d8accf4d62b3
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg412781(v=OCS.15)
ms:contentKeyID: 49304637
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Lync Server 2013의 Lync 클라이언트 소프트웨어 지원

 

_**마지막으로 수정된 항목:** 2015-07-06_

이 섹션에서는 Lync 2013과 Lync 2013용 온라인 모임 추가 기능를 위한 소프트웨어 지원에 대해 간략하게 설명합니다.


> [!NOTE]
> Outlook 메시징 및 공동 작업 클라이언트 내에서 모임 관리를 지원하는 Lync 2013용 온라인 모임 추가 기능은 Lync 2013과 함께 자동으로 설치됩니다.



### Lync 2013 및 Lync 2013용 온라인 모임 추가 기능의 소프트웨어 요구 사항

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th>시스템 구성 요소</th>
<th>최소 요구 사항</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Windows 운영 체제</p></td>
<td><p>Windows 8.1</p>
<p>Windows 8</p>
<p>Windows 7 운영 체제</p>
<p>Windows Server 2008 R2(최신 서비스 팩 설치)</p>


> [!NOTE]
> Lync 2013 및 Lync 2013용 온라인 모임 추가 기능은 Windows Vista 또는 Windows XP(모든 버전)에서 지원되지 않습니다.


</td>
</tr>
<tr class="even">
<td><p>설치 및 업데이트</p></td>
<td><p>관리자 권한 및 사용 권한</p></td>
</tr>
<tr class="odd">
<td><p>브라우저</p></td>
<td><p>Windows Internet Explorer 10 인터넷 브라우저</p>
<p>Internet Explorer 9 인터넷 브라우저</p>
<p>Internet Explorer 8 인터넷 브라우저</p>
<p>Internet Explorer 7 인터넷 브라우저</p>
<p>Mozilla Firefox 웹 브라우저</p>


> [!NOTE]
> Microsoft Exchange Online에서 Lync를 사용 중이고 조직에서 인증 HTTP 프록시를 배포한 경우 Internet Explorer 9 또는 Internet Explorer 8이 필요합니다.


</td>
</tr>
<tr class="even">
<td><p>Microsoft Office 통합</p></td>
<td><p>완전한 통합 기능을 위해서는 다음이 필요합니다.</p>
<ul>
<li><p>Outlook 2013 메시징 및 공동 작업 클라이언트</p></li>
<li><p>Outlook 2010 메시징 및 공동 작업 클라이언트</p></li>
</ul></td>
</tr>
<tr class="odd">
<td><p>Microsoft Exchange 통합</p></td>
<td><p>완전한 통합 기능을 위해서는 다음이 필요합니다.</p>
<ul>
<li><p>Microsoft Exchange Server 2013</p></li>
<li><p>Microsoft Exchange Server 2010</p></li>
</ul></td>
</tr>
</tbody>
</table>


## Macintosh 운영 체제

Lync 2013은 Windows에서만 사용할 수 있습니다. 그러나 Lync Server 2013은 Mac OS 10.5.8 또는 최신 서비스 팩 또는 릴리스(Intel 기반) 운영 체제를 실행하는 컴퓨터에서 다음과 같은 클라이언트를 지원합니다(Mac OS 10.9 운영 체제는 현재 지원되지 않습니다). 지원되는 기능에 대한 자세한 내용은 [Lync Server 2013 의 클라이언트 비교 표](lync-server-2013-desktop-client-comparison-tables.md)를 참고하세요.

  - Mac 2011용 Microsoft Lync( [http://go.microsoft.com/fwlink/?linkid=268786\&clcid=0x412](http://go.microsoft.com/fwlink/?linkid=268786%26clcid=0x412)에서 "Lync for Mac 2011 배포 가이드"를 참고하세요.)

  - Microsoft Communicator for Mac 2011( [http://go.microsoft.com/fwlink/?linkid=268787\&clcid=0x412](http://go.microsoft.com/fwlink/?linkid=268787%26clcid=0x412)에서 "Communicator for Mac 2011 배포 가이드"를 참고하세요.)

## Lync Web App 브라우저

Lync Web App에서는 특정 운영 체제 및 브라우저 조합을 지원합니다. 자세한 내용은 계획 설명서에서 [Lync Server 2013의 Lync Web App 지원 플랫폼](lync-server-2013-lync-web-app-supported-platforms.md)을 참고하세요.

## Microsoft Office 지원 가능성

Lync Server 2013 클라이언트를 다양한 버전의 Microsoft Office와 통합할 수 있습니다. 요약하면 다음과 같습니다.

  - Outlook 2013 및 Microsoft Outlook 2010에서 Lync 2013 통합 기능이 지원됩니다.

  - Microsoft Exchange Server 2013 및 Microsoft Exchange Server 2010에서 Lync 2013 통합 기능이 지원됩니다.

  - Office 2013 및 Microsoft Office 2010에서 Lync 2013용 온라인 모임 추가 기능이 지원됩니다.

## 필수 프로필 사용

Lync 2013 회의 기능을 사용하려는 사용자는 Active Directory 도메인 서비스 필수 프로필을 사용하여 Lync 2013 클라이언트에 로그인해서는 안 됩니다. 필수 프로필은 읽기 전용 사용자 프로필이므로 Lync 2013 회의에 필요한 PKI(공개 키 인프라) 키를 프로필에 저장할 수 없습니다. 자세한 내용은 Microsoft 기술 자료 문서 2552221, “사용자가 필수 사용자 프로필을 사용하여 로그인하면 Lync 2010 회의 기능에 오류가 발생함”([http://go.microsoft.com/fwlink/?linkid=3052\&clcid=0x412](http://go.microsoft.com/fwlink/?linkid=3052%26clcid=0x412))을 참고하세요.

## 참고 항목

#### 개념

[Lync Server 2013의 Lync 클라이언트 하드웨어 지원](lync-server-2013-lync-client-hardware-support.md)  
[Lync Server 2013에 대한 Lync 클라이언트 비디오 요구 사항](lync-server-2013-lync-client-video-requirements.md)  
[Lync Server 2013의 이전 배포에서 지원되는 클라이언트](lync-server-2013-supported-clients-from-previous-deployments.md)

