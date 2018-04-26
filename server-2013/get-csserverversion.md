---
title: Get-CsServerVersion
TOCTitle: Get-CsServerVersion
ms:assetid: 66af07c0-fdfe-491a-ad48-b8821fb58904
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg398470(v=OCS.15)
ms:contentKeyID: 49303870
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Get-CsServerVersion

 

_**마지막으로 수정된 항목:** 2015-03-09_

Lync Server를 실행하는 컴퓨터에 대한 서버 수신 정보를 반환합니다. 이 cmdlet은 Lync Server 2010에서 도입되었습니다.

## 구문

    Get-CsServerVersion

## 예제

## 예제 1

예제 1에 표시된 명령은 로컬 컴퓨터에 대한 라이선스 정보를 반환합니다. **Get-CsServerVersion** cmdlet은 이 방식으로만 사용할 수 있습니다.

    Get-CsServerVersion

## 자세한 정보

Lync Server는 평가판 버전(일정 기간 후 만료됨)과 정식 버전의 두 가지 버전으로 제공됩니다. 관리자는 **Get-CsServerVersion** cmdlet을 사용하여 컴퓨터에서 실행 중인 Lync Server의 버전을 확인할 수 있습니다. 로컬 컴퓨터에서만 실행되고 추가 매개 변수를 사용하지 않도록 만들어진 **Get-CsServerVersion** cmdlet은 HKEY\_LOCAL\_MACHINE\\SOFTWARE\\Microsoft\\Real-Time Communications\\{A593FD00-64F1-4288-A6F4-E699ED9DCA35}\\Type 레지스트리 키를 읽습니다. 그런 다음 이 레지스트리 값에 따라 소프트웨어 버전 번호 및 Lync Server 라이선스 정보를 다시 보고합니다. 라이선스 정보를 통해 다음 중 하나를 알 수 있습니다.

평가 라이선스 키가 설치되었는지 여부

볼륨 라이선스 키가 설치되었는지 여부

로컬 컴퓨터에 설치된 구성 요소에 라이선스 키가 필요 없는지 여부. 라이선스는 프런트 엔드 서버, 디렉터 또는 에지 서버 역할을 하는 컴퓨터에만 필요합니다.

오류가 발생한 경우 **Get-CsServerVersion** cmdlet은 라이선스 유형 및 버전 정보를 검색할 수 없음을 보고하며 Lync Server 구성 요소를 다시 설치하도록 권장합니다.

Get-CsServerVersion은 기본 버전 번호만 반환합니다. 예를 들어 Get-CsServerVersion은 업데이트를 통해 버전 번호가 5.0.8308.291로 변경된 경우에도 5.0.8308 같은 값을 반환합니다. 구체적인 버전 번호가 필요한 경우에는 Windows 제어판을 사용해야 합니다.

## 매개 변수


<table>
<colgroup>
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
</colgroup>
<thead>
<tr class="header">
<th>매개 변수</th>
<th>필수</th>
<th>유형</th>
<th>설명</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p></p></td>
<td><p></p></td>
<td><p></p></td>
<td><p></p></td>
</tr>
</tbody>
</table>


## 입력 형식

없음. **Get-CsServerVersion** cmdlet은 파이프라인된 입력을 지원하지 않습니다.

## 반환 형식

**Get-CsServerVersion** cmdlet은 문자열 값을 반환합니다.

