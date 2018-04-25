---
title: Lync Server 2013 회의에 대한 기술 요구 사항
TOCTitle: 회의에 대한 기술 요구 사항
ms:assetid: 3c0d89e1-53e6-46d7-bf8c-491260b292ea
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg425889(v=OCS.15)
ms:contentKeyID: 49303376
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Lync Server 2013의 회의에 대한 기술 요구 사항

 

_**마지막으로 수정된 항목:** 2015-03-09_

Lync Server 2013의 경우 전화 접속 회의, A/V 회의, 메신저 회의 및 웹 회의 기능은 항상 프런트 엔드 서버에서 실행됩니다.

이 섹션에서는 이러한 서버의 하드웨어 및 소프트웨어 요구 사항과 지원되는 배치에 대해 자세히 설명합니다.

전화 접속 회의는 다양한 구성 요소를 포함하는 기능입니다. 이러한 구성 요소 중 일부는 전화 접속 회의와 관련되어 있으며 다른 일부는 Enterprise Voice 구성 요소입니다. 이 섹션에서는 전화 접속 회의와 관련된 구성 요소의 요구 사항에 대해 설명합니다. 중재 서버 및 PSTN(공중 전화망) 게이트웨이 요구 사항에 대한 자세한 내용은 계획 설명서의 [Lync Server 2013의 중재 서버 구성 요소](lync-server-2013-mediation-server-component.md) and [Lync Server 2013의 중재 서버의 구성 요소 및 토폴로지](lync-server-2013-components-and-topologies-for-mediation-server.md)를 참고하세요.

## 하드웨어 요구 사항

웹 회의 및 A/V 회의는 프런트 엔드 서버와 함께 배치되기 때문에 서버 하드웨어 요구 사항은 프런트 엔드 서버와 동일합니다. 하드웨어 요구 사항에 대한 자세한 내용은 지원 가능성 설명서의 [Lync Server 2013의 서버 하드웨어 플랫폼](lync-server-2013-server-hardware-platforms.md)을 참고하세요. 전화 접속 회의에 필요한 다음 구성 요소도 프런트 엔드 서버와 하드웨어 요구 사항이 동일합니다.

  - 응용 프로그램 서비스

  - 회의 길잡이 응용 프로그램

  - 회의 알림 응용 프로그램

프런트 엔드 서버의 하드웨어 요구 사항은 다음 표에 나와 있는 것처럼 Lync Server 2013의 다른 여러 서버 역할과 동일합니다.

## 소프트웨어 요구 사항

웹 회의 및 A/V 회의는 프런트 엔드 서버와 함께 배치되기 때문에 서버 하드웨어 요구 사항은 프런트 엔드 서버와 동일합니다. 하드웨어 요구 사항에 대한 자세한 내용은 지원 가능성 설명서의 [Lync Server 2013의 서버 및 도구 운영 체제 지원](lync-server-2013-server-and-tools-operating-system-support.md)를 참고하세요. 전화 접속 회의에 필요한 다음 구성 요소도 프런트 엔드 서버와 하드웨어 요구 사항이 동일합니다.

웹 회의의 경우 PowerPoint 프레젠테이션을 처리하려면 Lync Server 2013에 Office Web Apps 및 Office Web Apps 서버(이전의 WAC Server)도 필요합니다. 자세한 내용은 [Office Online Server 및 Lync Server 2013과 통합 구성](lync-server-2013-enabling-office-web-apps-server-and-lync-server-2013.md)를 참고하세요.

전화 접속 회의의 경우 응용 프로그램 서비스, 회의 길잡이 응용 프로그램 및 회의 알림 응용 프로그램은 운영 체제 요구 사항이 프런트 엔드 서버와 동일합니다. 소프트웨어 요구 사항에 대한 자세한 내용은 지원 가능성 설명서의 [Lync Server 2013의 서버 및 도구 운영 체제 지원](lync-server-2013-server-and-tools-operating-system-support.md)를 참고하세요.

회의 길잡이 응용 프로그램 및 회의 알림 응용 프로그램을 사용하려면 Windows Media 형식 런타임이 프런트 엔드 서버에 설치되어 있어야 합니다. Windows Media 형식 런타임은 대기 음악, 녹음된 이름 및 음성 안내에 사용되는 WMA(Windows Media 오디오) 파일을 재생하는 데 필요합니다. Windows Server 2012 및 Windows Server 2012 R2를 제외하고 Windows Media 형식 런타임은 설치 프로그램을 실행할 때 Windows Desktop Experience의 일부로 자동으로 설치되지만 컴퓨터를 다시 시작해야 할 수 있습니다. 따라서 설치 프로그램을 실행하기 전에 Windows Media 형식 런타임이 포함된 Windows Desktop Experience의 일부로 설치하는 것이 좋습니다. Windows Server 2012 및 Windows Server 2012 R2에는 Microsoft 미디어 파운데이션이 필요합니다.

## 전화 접속 회의에 대한 포트 요구 사항

다음 표에서는 전화 접속 회의에 사용되는 포트에 대해 설명합니다. 부하 분산 장치를 사용하는 경우 풀에서 실행할 응용 프로그램이 사용하는 포트에 대해 부하 분산 장치가 구성되었는지 확인합니다.

이러한 포트는 **Set-CsApplicationServer** cmdlet을 사용하여 변경할 수 있는 기본 설정입니다. 이 cmdlet에 대한 자세한 내용은 Lync Server 관리 셸 설명서를 참조하십시오.


> [!NOTE]
> 풀에서 동일한 응용 프로그램의 모든 인스턴스는 동일한 SIP 수신 대기 포트를 사용합니다.



### 전화 접속 회의에서 사용되는 포트

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th>포트 번호</th>
<th>설명</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>5072</p></td>
<td><p>SIP 수신 대기 요청을 위해 회의 길잡이 응용 프로그램에서 사용됨</p></td>
</tr>
<tr class="even">
<td><p>5073</p></td>
<td><p>SIP 수신 대기 요청을 위해 회의 알림 응용 프로그램에서 사용됨</p></td>
</tr>
</tbody>
</table>


## 전화 접속 회의에 지원되는 클라이언트

다음 클라이언트를 사용하여 전화 접속 액세스를 지원하는 온-프레미스 회의를 예약할 수 있습니다.

  - Lync 2013용 온라인 모임 추가 기능( Lync 2013 또는 Attendee 설치 시 자동으로 설치됨)

## 전화 접속 회의 설정 페이지 요구 사항

전화 접속 회의 설정 페이지에서는 다음 표에 설명된 운영 체제 및 웹 브라우저 결합이 지원됩니다.


> [!NOTE]
> 32비트 및 64비트 버전의 운영 체제가 지원됩니다.



### 지원되는 운영 체제 및 웹 브라우저

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th>운영 체제</th>
<th>웹 브라우저</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Windows 7</p></td>
<td><p>Internet Explorer 9</p>
<p>Internet Explorer 8</p>
<p>Firefox</p></td>
</tr>
<tr class="even">
<td> </td>
<td> </td>
</tr>
<tr class="odd">
<td> </td>
<td> </td>
</tr>
<tr class="even">
<td><p>Windows Server 2008 R2</p></td>
<td><p>Internet Explorer 9</p>
<p>Internet Explorer 8</p>
<p>Internet Explorer 7</p></td>
</tr>
<tr class="odd">
<td><p>Mac OS</p></td>
<td><p>Firefox</p>
<p>Safari</p></td>
</tr>
</tbody>
</table>


## 전화 접속 회의에 대한 오디오 파일 요구 사항

Lync Server 2013에서는 전화 접속 회의에 대해 음성 안내 및 음악을 사용자 지정할 수 없습니다. 하지만 업무상 기본 오디오 파일을 반드시 변경해야 하는 경우 Microsoft 기술 자료 문서 961177, [Microsoft Office Communications Server 2007 R2의 전화 접속 오디오 회의에 대한 음성 프롬프트 또는 음악 파일을 사용자 지정하는 방법](http://go.microsoft.com/fwlink/p/?linkid=3052%26kbid=961177)을 참고하세요.

또한 [Microsoft Lync Server 회의 길잡이 사용자 지정 음성 프롬프트](http://go.microsoft.com/fwlink/p/?linkid=396880) 관리 유틸리티를 사용할 수도 있습니다. 관리자는 이 유틸리티를 사용하여 전화 발신자가 Lync 모임에 참가할 때 사용되는 기본 음성 프롬프트를 사용자 지정 프롬프트로 대체하여 다른 모임 임장 환경을 제공할 수 있습니다. 사용자 지정 음성 프롬프트는 Lync Server 2010이나 Lync Server 2013의 Enterprise 또는 Standard Edition을 실행하는 서버에 설치할 수 있습니다.

회의 길잡이 응용 프로그램 및 회의 알림 응용 프로그램에는 대기 음악, 기록된 이름 및 오디오 음성 안내 파일에 대한 다음과 같은 요구 사항이 있습니다.

  - WMA(Windows Media 오디오) 파일 형식

  - 16비트 모노

  - 48kbps 2-pass CBR(상수 비트 전송률)

  - \-24DB의 음량 수준

## 전화 접속 회의에 대한 사용자 요구 사항

전화 접속 회의 사용자의 계정에 고유한 전화 번호나 내선 번호가 지정되어야 합니다. 이 요구 사항은 전화 접속 회의를 진행하는 동안 인증을 지원합니다. 엔터프라이즈 사용자(즉 조직 내 Active Directory 도메인 서비스 자격 증명 및 Lync Server 계정을 가지고 있는 사용자)는 본인의 전화 번호(또는 내선 번호) 및 PIN(개인 식별 번호)을 입력하여 인증된 사용자로 회의에 전화 접속하게 됩니다.

