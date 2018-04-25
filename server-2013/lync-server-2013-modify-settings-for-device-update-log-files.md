---
title: 장치 업데이트 로그 파일의 설정 수정
TOCTitle: 장치 업데이트 로그 파일의 설정 수정
ms:assetid: 9b57f126-1853-43b3-bbd4-06401e6498bd
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg182554(v=OCS.15)
ms:contentKeyID: 49304505
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# 장치 업데이트 로그 파일의 설정 수정

 

_**마지막으로 수정된 항목:** 2015-03-09_

Lync Server 제어판 또는 Lync Server 관리 셸을 사용하여 조직에서 장치 업데이트 정보가 기록되는 방법에 대한 설정을 변경할 수 있습니다. 아래 표에는 수정 가능한 설정과 해당 설정을 수정하는 데 사용하는 도구가 나와 있습니다.

로그 설정은 전역적으로 또는 사이트별로 적용 및 변경할 수 있습니다.


<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th>변경할 설정</th>
<th>사용할 도구</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>로그 파일의 최대 크기(바이트)</p></td>
<td><p>Lync Server 제어판</p>
<p>-또는-</p>
<p>Lync Server 관리 셸</p></td>
</tr>
<tr class="even">
<td><p>캐시에 포함할 수 있는 정보의 최대 양(바이트)</p></td>
<td><p>Lync Server 제어판</p>
<p>-또는-</p>
<p>Lync Server 관리 셸</p></td>
</tr>
<tr class="odd">
<td><p>로그 파일에 캐시된 정보를 쓰는 빈도(분)</p></td>
<td><p>Lync Server 제어판</p>
<p>-또는-</p>
<p>Lync Server 관리 셸</p></td>
</tr>
<tr class="even">
<td><p>로그 파일을 보관할 기간(일)</p></td>
<td><p>Lync Server 제어판</p>
<p>-또는-</p>
<p>Lync Server 관리 셸</p></td>
</tr>
<tr class="odd">
<td><p>삭제해야 하는 만료된 파일을 확인할 시간</p></td>
<td><p>Lync Server 관리 셸</p></td>
</tr>
<tr class="even">
<td><p>허용할 로그 파일 확장명</p></td>
<td><p>Lync Server 관리 셸</p></td>
</tr>
<tr class="odd">
<td><p>보관할 로그 파일 형식</p></td>
<td><p>Lync Server 관리 셸</p></td>
</tr>
</tbody>
</table>


## Lync Server 제어판을 사용하여 로깅 설정을 변경하려면

1.  브라우저 창을 연 다음 Admin URL을 입력하여 Lync Server 제어판을 엽니다. Lync Server 제어판을 시작하는 데 사용할 수 있는 다양한 방법에 대한 자세한 내용은 [Lync Server 관리 도구 열기](lync-server-2013-open-lync-server-administrative-tools.md)를 참조하세요.

2.  왼쪽 탐색 표시줄에서 **클라이언트**, **장치 로그 구성**을 차례로 클릭합니다.

3.  **장치 로그 구성** 페이지에서 변경할 구성을 두 번 클릭합니다.

4.  **로그 설정 편집** 대화 상자에서 다음 설정 중 원하는 설정을 변경합니다.
    
      - **최대 파일 크기(바이트)**   로그 파일 삭제 전 로그 파일의 최대 크기를 지정합니다. 기본 크기는 1,024,000바이트(1MB)입니다.
    
      - **최대 캐시 크기(바이트)**   캐시를 지우고 데이터를 로그 파일에 작성하기 전 로그 파일 캐시에 보관할 수 있는 최대 정보 양(바이트)을 지정합니다. 기본 크기는 512,000바이트(0.5MB)입니다.
    
      - **캐시를 플러시할 기간(분)(1-60)**   로그 파일 캐시에 저장된 정보가 실제 로그 파일에 작성되는 간격을 나타냅니다. 데이터가 로그에 기록되면 캐시가 지워집니다. 기본 간격은 5분입니다.
    
      - **로그 파일을 유지할 기간(일)(1-365)**   로그 파일 삭제 전 로그 파일이 유지되는 일수를 지정합니다. 기본 일수는 10일입니다.

5.  **커밋**을 클릭합니다.

## Windows PowerShell cmdlet을 사용하여 로깅 설정 변경

Windows PowerShell 및 **Set-CsDeviceUpdateConfiguration** cmdlet 사용하여 장치 업데이트 로그 파일 설정을 수정할 수 있습니다. 이 cmdlet은 Lync Server 2013 관리 셸 또는 Windows PowerShell의 원격 세션에서 실행할 수 있습니다.


> [!NOTE]
> 원격 Windows PowerShell을 사용하여 Lync Server에 연결하는 방법에 대한 자세한 내용은 Lync Server Windows PowerShell 블로그 문서인 "빠른 시작: 원격 PowerShell을 사용하여 Microsoft Lync Server 2010 관리"(<A href="http://go.microsoft.com/fwlink/p/?linkid=255876">http://go.microsoft.com/fwlink/p/?linkId=255876</A>)를 참조하세요.



다음 예제에서는 **Set-CsDeviceUpdateConfiguration**을 사용하여 설정을 수정할 수 있는 두 가지 방법을 보여 줍니다.

## 최대 로그 파일 크기 및 로그 정리 간격을 수정하려면

  - 다음 명령은 Redmond 사이트에 적용되는 장치 업데이트 로그 설정을 수정합니다. 이 예제에서 최대 로그 파일 크기는 204800바이트로, 로그 정리 간격은 14일로 설정됩니다.
    
        Set-CsDeviceUpdateConfiguration -Identity "site:Redmond" -MaxLogFileSize 204800 -LogCleanUpInterval 14.00:00:00

## 로그 정리 시간을 수정하려면

  - 이 명령은 Redmond 사이트의 로그 정리 시간을 오전 3시로 설정합니다.
    
        Set-CsDeviceUpdateConfiguration -Identity "site:Redmond" -LogCleanupTimeOfDay 03:00

자세한 내용은 [Set-CsDeviceUpdateConfiguration](set-csdeviceupdateconfiguration.md) cmdlet의 도움말 항목을 참조하십시오.

