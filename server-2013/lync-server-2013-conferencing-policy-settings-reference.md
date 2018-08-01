---
title: Lync Server 2013용 회의 정책 설정 참조
TOCTitle: Lync Server 2013용 회의 정책 설정 참조
ms:assetid: ec8125f7-ef78-4a2b-8db0-4dd3cf5a4065
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg429724(v=OCS.15)
ms:contentKeyID: 49305434
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Lync Server 2013용 회의 정책 설정 참조

 

_**마지막으로 수정된 항목:** 2014-04-22_

이 항목의 표에는 Lync Server 2013 제어판을 사용하여 지정할 수 있는 회의 정책 설정이 모두 나와 있습니다.

## 이끌이 정책 설정

다음 표에는 회의 이끌이에게 적용될 수 있는 모든 회의 정책 설정이 나와 있습니다. 회의 정책 설정의 최신 목록은 [Set-CsClientPolicy](https://docs.microsoft.com/en-us/powershell/module/skype/Set-CsClientPolicy) cmdlet에 대한 도움말 항목을 참고하세요.

### 이끌이 정책 설정

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th>설정</th>
<th>설명</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>최대 모임 크기</p></td>
<td><p>모임에 허용된 최대 참가자 수를 설정합니다.</p></td>
</tr>
<tr class="even">
<td><p>참가자가 익명 사용자를 초대할 수 있도록 허용</p></td>
<td><p>모임 이끌이가 인증되지 않은 사용자를 모임에 초대할 수 있도록 허용합니다.</p></td>
</tr>
<tr class="odd">
<td><p>기록 사용</p></td>
<td><p>발표자나 참가자가 모임을 기록할 수 있도록 허용합니다.</p></td>
</tr>
<tr class="even">
<td><p>페더레이션 참가자 및 익명 참가자가 기록할 수 있도록 허용</p></td>
<td><p>외부 및 인증되지 않은 참가자가 모임을 기록할 수 있도록 허용합니다.</p></td>
</tr>
<tr class="odd">
<td><p>IP 오디오 사용</p></td>
<td><p>모임에서 오디오 사용을 허용합니다.</p></td>
</tr>
<tr class="even">
<td><p>IP 오디오/비디오 사용</p></td>
<td><p>모임에서 오디오 및 비디오 사용을 허용합니다.</p></td>
</tr>
<tr class="odd">
<td><p>PSTN 전화 접속 회의 사용</p></td>
<td><p>PSTN(공중 전화망)을 통해 전화 접속하여 모임에 참가할 수 있도록 허용합니다.</p></td>
</tr>
<tr class="even">
<td><p>익명 참가자가 전화를 걸 수 있도록 허용</p></td>
<td><p>인증되지 않은 참가자가 전화 접속 전화를 사용하여 모임에 참가할 수 있도록 허용합니다. 전화 접속 전화를 사용하면 전화 회의 서버에서 사용자에게 전화를 걸고 사용자는 이 전화에 응답하여 모임에 참가할 수 있습니다.</p></td>
</tr>
<tr class="odd">
<td><p>회의에 허용되는 최대 비디오 해상도</p></td>
<td><p>비디오 회의에 대한 최대 해상도를 설정합니다. 사용할 수 있는 값은 <strong>640*480(VGA)</strong> 및 <strong>352*288(CIF)</strong>입니다.</p></td>
</tr>
<tr class="even">
<td><p>데이터 공동 작업 사용</p></td>
<td><p>데이터 공동 작업 회의나 웹 회의를 사용할 수 있도록 설정합니다.</p></td>
</tr>
<tr class="odd">
<td><p>페더레이션 참가자 및 익명 참가자가 콘텐츠를 다운로드할 수 있도록 허용</p></td>
<td><p>외부 및 인증되지 않은 참가자가 모임 콘텐츠를 다운로드할 수 있도록 허용합니다.</p></td>
</tr>
<tr class="even">
<td><p>참가자가 파일을 전송할 수 있도록 허용</p></td>
<td><p>모임 동안 모임 참가자가 파일을 전송할 수 있도록 허용합니다.</p></td>
</tr>
<tr class="odd">
<td><p>주석 사용</p></td>
<td><p>모임 참가자가 콘텐츠에 주석을 작성할 수 있도록 허용합니다.</p></td>
</tr>
<tr class="even">
<td><p>설문 사용</p></td>
<td><p>모임 참가자가 모임 동안 설문을 실시할 수 있도록 허용합니다.</p></td>
</tr>
<tr class="odd">
<td><p>응용 프로그램 공유 사용</p></td>
<td><p>사용자가 응용 프로그램 공유를 지원하는 모임을 예약할 수 있도록 허용합니다.</p></td>
</tr>
<tr class="even">
<td><p>참가자가 제어할 수 있도록 허용</p></td>
<td><p>참가자가 다른 사용자의 공유 응용 프로그램을 제어할 수 있도록 허용합니다.</p></td>
</tr>
<tr class="odd">
<td><p>페더레이션 참가자 및 익명 참가자가 제어할 수 있도록 허용</p></td>
<td><p>외부 및 익명의 참가자가 다른 사용자의 공유 응용 프로그램을 제어할 수 있도록 허용합니다.</p>


> [!NOTE]
> 이 설정이 True로 설정되고 <STRONG>참가자가 제어할 수 있도록 허용</STRONG>이 False로 설정된 경우 이 설정이 재정의됩니다.


</td>
</tr>
</tbody>
</table>


## 참가자 정책 설정

다음 표에는 회의 참가자에게 적용할 수 있는 모든 회의 정책 설정이 나와 있습니다.

### 참가자 정책 설정

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th>설정</th>
<th>설명</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>응용 프로그램 공유 사용</p></td>
<td><p>사용자가 응용 프로그램 공유를 지원하는 모임을 예약할 수 있도록 허용합니다.</p></td>
</tr>
<tr class="even">
<td><p>응용 프로그램 및 데스크톱 공유 사용</p></td>
<td><p>사용자가 응용 프로그램 공유 및 데스크톱 공유를 지원하는 모임에 참가할 수 있도록 허용합니다. 전화 회의에서 전화 회의의 이끌이에 적용되는 이 설정의 값은 참가하는 모든 익명 끝점에 적용됩니다.</p></td>
</tr>
<tr class="odd">
<td><p>피어 투 피어 파일 전송 사용</p></td>
<td><p>모임 동안 참가자가 피어 투 피어 파일 전송을 수행할 수 있도록 허용합니다. 일부 모임 참가자는 피어 투 피어 파일 전송을 수행할 수 없습니다.</p></td>
</tr>
<tr class="even">
<td><p>피어 투 피어 기록 사용</p></td>
<td><p>참가자가 피어 투 피어 회의 세션을 기록할 수 있도록 허용합니다.</p></td>
</tr>
</tbody>
</table>

