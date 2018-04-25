---
title: 'Lync Server 2013: 응답 그룹에 대한 기술 요구 사항'
TOCTitle: 응답 그룹에 대한 기술 요구 사항
ms:assetid: 477488bd-124f-437b-9327-732a0d7271ca
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/JJ204863(v=OCS.15)
ms:contentKeyID: 49303516
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Lync Server 2013의 응답 그룹에 대한 기술 요구 사항

 

_**마지막으로 수정된 항목:** 2015-03-09_

이 섹션에서는 다음과 같은 응답 그룹 응용 프로그램에 대한 기술적 요구 사항에 대해 설명합니다.

  - 하드웨어 요구 사항

  - 소프트웨어 요구 사항

  - 포트 요구 사항

  - 오디오 파일 요구 사항

  - 응답 그룹 구성 도구 요구 사항

## 하드웨어 요구 사항

응답 그룹 응용 프로그램의 하드웨어 요구 사항은 프런트 엔드 서버와 동일합니다. 하드웨어 요구 사항에 대한 자세한 내용은 지원 가능성 설명서에서 [Lync Server 2013의 서버 하드웨어 플랫폼](lync-server-2013-server-hardware-platforms.md)을 참조하십시오.

## 소프트웨어 요구 사항

응답 그룹 응용 프로그램의 운영 체제 요구 사항 및 소프트웨어 필수 구성 요소는 프런트 엔드 서버와 동일합니다. 소프트웨어 요구 사항에 대한 자세한 내용은 지원 가능성 설명서에서 [Lync Server 2013의 서버 및 도구 운영 체제 지원](lync-server-2013-server-and-tools-operating-system-support.md)을 참조하십시오.

응답 그룹 음악 및 알림에 대해 Windows Media 오디오(.wma) 파일을 사용할 경우 모든 프런트 엔드 서버 또는 응답 그룹 응용 프로그램 실행 Standard Edition 서버에 Windows Server 2008 R2 실행 서버의 경우 Windows Media 형식 런타임 또는 Windows Server 2012 또는 Windows Server 2012 R2 실행 서버의 경우 Microsoft 미디어 파운데이션이 설치되어 있어야 합니다. Windows Server 2008 R2의 경우 Windows Media 형식 런타임은 Windows Desktop Experience의 일부로 설치됩니다.

오디오 요구 사항에 대한 자세한 내용은 이 섹션의 뒷 부분에 나오는 "오디오 파일 요구 사항"을 참조하십시오.

## 포트 요구 사항

응답 그룹 응용 프로그램에는 다음과 같은 포트가 사용됩니다.

  - **포트 5071**   SIP 수신 대기 요청에 사용됩니다.

  - **포트 8404**   서버 간 통신에 사용됩니다.
    

    > [!NOTE]
    > 이 포트는 매치 메이킹 서비스에 사용되며 두 개 이상의 프런트 엔드 서버가 포함된 풀에 응답 그룹 응용 프로그램이 배포되었을 때 필요합니다.




> [!NOTE]
> 이러한 포트는 <STRONG>Set-CsApplicationServer</STRONG> cmdlet을 사용하여 변경할 수 있는 기본 설정입니다. 이 cmdlet에 대한 자세한 내용은 Lync Server 관리 셸 설명서를 참조하십시오.



## 오디오 파일 요구 사항

응답 그룹 응용 프로그램에는 응답 그룹 메시지, 대기 음악 또는 IVR(대화형 음성 응답) 질문에 대해 웨이브(.wav) 파일 형식 및 Windows Media 오디오(.wma) 파일 형식이 지원됩니다.

Windows Media 오디오 파일 형식을 사용하려면 Windows Server 2008 R2 및 Windows Server 2008을 실행하는 프런트 엔드 서버에 Windows Media 형식 런타임이 설치되어 있어야 합니다. 자세한 내용은 이 섹션의 앞 부분에 있는 "소프트웨어 요구 사항"을 참조하십시오.

## 지원되는 웨이브 파일 형식

모든 웨이브 파일은 다음 요구 사항을 충족해야 합니다.

  - 8비트 또는 16비트 파일

  - LPCM(선형 펄스 부호 변조), A-Law 또는 mu-Law 형식

  - 모노 또는 스테레오

  - 4MB 이하

최상의 웨이브 파일 성능을 위해서는 16kHz/모노/16비트의 웨이브 파일을 사용하는 것이 좋습니다.

## 지원되는 Windows Media 오디오 파일 형식

Windows Media 오디오 파일을 사용할 경우 낮은 비트 전송률을 사용하고 시스템 성능이 정상인지 확인합니다.

Microsoft Expression Encoder 4를 사용하여 파일을 Windows Media 오디오 형식으로 변환할 수 있습니다. Expression Encoder 4를 다운로드하려면 [http://go.microsoft.com/fwlink/?linkid=202843\&clcid=0x412](http://go.microsoft.com/fwlink/?linkid=202843%26clcid=0x412)를 참조하십시오.

## 응답 그룹 구성 도구 요구 사항

응답 그룹 구성 도구에서는 다음 표에 설명된 운영 체제 및 웹 브라우저 결합이 지원됩니다.


> [!NOTE]
> 32비트 또는 64비트 버전의 운영 체제가 지원됩니다. 32비트 버전의 Internet Explorer만 지원됩니다.



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
<td><p>Windows Vista SP(서비스 팩) 2</p></td>
<td><p>Internet Explorer 7</p>
<p>Internet Explorer 8(기본 모드)</p>
<p>Internet Explorer 9(기본 모드)</p></td>
</tr>
<tr class="even">
<td><p>Windows 7</p>
<p>Windows 7 서비스 팩 1</p></td>
<td><p>Internet Explorer 8(기본 모드)</p>
<p>Internet Explorer 9(기본 모드)</p></td>
</tr>
<tr class="odd">
<td><p>Windows Server 2008 서비스 팩 2</p></td>
<td><p>Internet Explorer 7</p>
<p>Internet Explorer 8(기본 모드)</p>
<p>Internet Explorer 9(기본 모드)</p></td>
</tr>
<tr class="even">
<td><p></p>
<p></p>
<p></p>
<p>Windows Server 2008 R2</p>
<p>Windows Server 2008 R2 서비스 팩 1</p></td>
<td><p>Internet Explorer 8(기본 모드)</p>
<p>Internet Explorer 9(기본 모드)</p></td>
</tr>
</tbody>
</table>


## 응답 그룹 에이전트 콘솔

에이전트 콘솔은 다음 표에 설명된 운영 체제 및 웹 브라우저의 조합을 지원합니다.


> [!NOTE]
> 32비트 또는 64비트 버전의 운영 체제가 지원됩니다. 32비트 버전의 Internet Explorer만 지원됩니다.



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
<td><p>Windows Vista SP(서비스 팩) 2</p></td>
<td><p>Internet Explorer 7</p>
<p>Internet Explorer 8(기본 모드)</p>
<p>Internet Explorer 9(기본 모드)</p></td>
</tr>
<tr class="even">
<td><p>Windows 7</p>
<p>Windows 7 서비스 팩 1</p></td>
<td><p>Internet Explorer 8(기본 모드)</p>
<p>Internet Explorer 9(기본 모드)</p>
<p>Firefox 10.0</p>
<p>Chrome 18.0</p></td>
</tr>
<tr class="odd">
<td><p>Windows Server 2008 서비스 팩 2</p></td>
<td><p>Internet Explorer 7</p>
<p>Internet Explorer 8(기본 모드)</p>
<p>Internet Explorer 9(기본 모드)</p></td>
</tr>
<tr class="even">
<td><p>Windows Server 2008 R2</p>
<p>Windows Server 2008 R2 서비스 팩 1</p></td>
<td><p>Internet Explorer 8(기본 모드)</p>
<p>Internet Explorer 9(기본 모드)</p>
<p>Firefox 10.0</p>
<p>Chrome 18.0</p></td>
</tr>
<tr class="odd">
<td><p></p></td>
<td></td>
</tr>
</tbody>
</table>

