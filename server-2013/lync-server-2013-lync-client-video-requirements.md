---
title: 'Lync Server 2013: Lync 클라이언트 비디오 요구 사항'
TOCTitle: Lync 클라이언트 비디오 요구 사항
ms:assetid: 8f68f4c2-3194-487c-bd2f-fbe71ba8ad70
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/JJ688132(v=OCS.15)
ms:contentKeyID: 49885870
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Lync Server 2013에 대한 Lync 클라이언트 비디오 요구 사항

 

_**마지막으로 수정된 항목:** 2015-03-09_

이 섹션에서는 Lync 2013 비디오 통화에 대한 비디오 하드웨어 지원에 대해 설명하고 다양한 컴퓨터, 태블릿, 모바일 장치 구성에 대한 예상 비디오 품질을 확인하는 방법에 대해 설명합니다.

## Windows 데스크톱/태블릿 비디오 요구 사항 및 기능

Lync 2013에는 H.264/MPEG-4 Part 10 고급 비디오 코딩 표준을 기반으로 비디오 인코딩 및 디코딩을 위한 하드웨어 가속 기능이 도입되었습니다. 이 기능은 CPU 클럭 속도가 낮은 컴퓨터가 고해상도 비디오를 인코딩 및 디코딩할 수 있게 해줍니다. 비디오 하드웨어 요구 사항은 컴퓨터 구성 및 원하는 비디오 해상도에 따라 다릅니다.

## 비디오 하드웨어 요구 사항


<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th>기능</th>
<th>요구 사항</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>DXVA(DirectX 비디오 가속 설정)를 사용한 하드웨어 가속 H.264 디코딩</p></td>
<td><ul>
<li><p>그래픽 카드가 DirectX 9.0을 지원해야 하며 DXVA2_ModeH264_VLD_NoFGT 디코딩 모드를 제공해야 합니다.</p></li>
<li><p>최신 그래픽 카드 드라이버를 설치해야 합니다.</p></li>
</ul>


> [!NOTE]
> 디코딩 모드에 대한 자세한 내용은 <A class=uri href="http://go.microsoft.com/fwlink/?linkid=268530%26clcid=0x412">http://go.microsoft.com/fwlink/?linkid=268530&amp;clcid=0x412</A>를 참조하세요.


</td>
</tr>
<tr class="even">
<td><p>하드웨어 가속 H.264 인코딩: 칩셋 요구 사항</p></td>
<td><p>다음 Intel 하드웨어 가속 비디오 인코딩 솔루션이 지원됩니다.</p>
<ul>
<li><p>2세대 및 3세대 Intel HD Graphics 2000, 2500, 3000 및 4000 칩셋(또는 최신 버전)과 통합 하드웨어 비디오 인코더. Intel HD Graphics 드라이버 15.28.9.2884 또는 다음을 포함하는 최신 드라이버를 설치해야 합니다.</p>
<ul>
<li><p>디스플레이 드라이버 9.17.10.2828 또는 최신 드라이버</p></li>
<li><p>HMFT(Hardware Media Foundation Transform) 버전 3.12.10.31 또는 최신 HMFT</p></li>
</ul></li>
</ul>
<p>다음과 같은 AMD 하드웨어 가속 인코딩 솔루션이 지원됩니다(Lync Server 2013에 대한 CU1 업데이트 필요).</p>
<ul>
<li><p>여러 개별 그래픽 카드와 AMD A-Series Accelerated Processors의 통합 가속 처리 장치에서 사용할 수 있는 AMD Video Codec Engine. AMD Video Codec Engine 드라이버 9.12.0.0 이상을 설치해야 합니다.</p></li>
</ul></td>
</tr>
<tr class="odd">
<td><p>하드웨어 가속 H.264 인코딩: 카메라 요구 사항</p></td>
<td><p>UVC(USB Video Class) 사양 버전 1.5를 준수하는 통합 H.264 하드웨어 인코더가 포함된 USB 비디오 카메라</p>


> [!NOTE]
> Lync 2013은 Windows 8 또는 Windows 8.1에서 UVC 1.5에 대한 지원을 포함하는 UVC 1.5 카메라를 지원합니다. Windows 7에는 UVC 1.5에 대한 지원이 포함되지 않기 때문에 Lync 2013은 UVC 1.5 카메라를 일반 카메라로 취급하고 하드웨어 인코딩을 지원하지 않습니다.


</td>
</tr>
<tr class="even">
<td><p>DXVA(DirectX 비디오 가속 설정)를 사용한 하드웨어 가속 H.264 디코딩</p></td>
<td><ul>
<li><p>그래픽 카드가 DirectX 9.0을 지원해야 하며 DXVA2_ModeH264_VLD_NoFGT 디코딩 모드를 제공해야 합니다.</p></li>
<li><p>최신 그래픽 카드 드라이버를 설치해야 합니다.</p></li>
</ul>


> [!NOTE]
> 디코딩 모드에 대한 자세한 내용은 <A class=uri href="http://go.microsoft.com/fwlink/?linkid=268530%26clcid=0x412">http://go.microsoft.com/fwlink/?linkid=268530&amp;clcid=0x412</A>를 참조하세요.


</td>
</tr>
<tr class="odd">
<td><p>하드웨어 가속 H.264 인코딩: 칩셋 요구 사항</p></td>
<td><p>다음 Intel 하드웨어 가속 비디오 인코딩 솔루션이 지원됩니다.</p>
<ul>
<li><p>2세대 및 3세대 Intel HD Graphics 2000, 2500, 3000 및 4000 칩셋(또는 최신 버전)과 통합 하드웨어 비디오 인코더. Intel HD Graphics 드라이버 15.28.9.2884 또는 다음을 포함하는 최신 드라이버를 설치해야 합니다.</p>
<ul>
<li><p>디스플레이 드라이버 9.17.10.2828 또는 최신 드라이버</p></li>
<li><p>HMFT(Hardware Media Foundation Transform) 버전 3.12.10.31 또는 최신 HMFT</p></li>
</ul></li>
</ul>
<p>다음과 같은 AMD 하드웨어 가속 인코딩 솔루션이 지원됩니다(Lync Server 2013에 대한 CU1 업데이트 필요).</p>
<ul>
<li><p>여러 개별 그래픽 카드와 AMD A-Series Accelerated Processors의 통합 가속 처리 장치에서 사용할 수 있는 AMD Video Codec Engine. AMD Video Codec Engine 드라이버 9.12.0.0 이상을 설치해야 합니다.</p></li>
</ul></td>
</tr>
<tr class="even">
<td><p>하드웨어 가속 H.264 인코딩: 카메라 요구 사항</p></td>
<td><p>UVC(USB Video Class) 사양 버전 1.5를 준수하는 통합 H.264 하드웨어 인코더가 포함된 USB 비디오 카메라</p>


> [!NOTE]
> Lync 2013은 Windows 8 또는 Windows 8.1에서 UVC 1.5에 대한 지원을 포함하는 UVC 1.5 카메라를 지원합니다. Windows 7에는 UVC 1.5에 대한 지원이 포함되지 않기 때문에 Lync 2013은 UVC 1.5 카메라를 일반 카메라로 취급하고 하드웨어 인코딩을 지원하지 않습니다.


</td>
</tr>
</tbody>
</table>


## H.264 비디오 인코딩 및 디코딩 기능 확인

일반적으로 특정 컴퓨터 구성에 대한 최대 인코딩 및 디코딩 기능을 확인하는 데에는 4가지 기본 요소가 있습니다.

  - DXVA를 사용하는 하드웨어 가속 디코딩에 대한 지원

  - 하드웨어 가속 인코딩 지원

  - 물리적 코어 수

  - WEI(Windows 체험 지수)

WinSAT(Windows 시스템 평가 도구)는 WEI를 확인합니다. WinSAT 도구를 실행하면 컴퓨터의 %windir%\\Performance\\WinSAT\\DataStore 디렉터리에 Formal.Assessment XML 문서가 생성됩니다. 이 XML 파일에는 인코딩 및 디코딩 기능을 확인하는 데 특히 중요한 다음 두 가지 점수가 포함됩니다.

  - VideoEncodeScore는 컴퓨터의 소프트웨어 기반 비디오 인코딩 기능을 나타냅니다.

  - GraphicsScore 값은 컴퓨터의 하드웨어 가속 인코딩 기능을 나타냅니다.

다음 3개의 테이블에서는 지원하는 하드웨어 가속에 따라 서로 다른 PC 유형에 대한 최대 인코딩 및 디코딩 기능을 설명합니다. 640x360 이상 해상도의 경우 지원되는 최대 프레임 속도는 30fps(초당 프레임 수)입니다. 640x360 미만 해상도의 경우 지원되는 최대 프레임 속도는 15fps입니다.

### DXVA 및 하드웨어 가속 인코더가 없는 컴퓨터

<table>
<colgroup>
<col style="width: 33%" />
<col style="width: 33%" />
<col style="width: 33%" />
</colgroup>
<thead>
<tr class="header">
<th>지원 가능한 인코더 해상도</th>
<th>지원 가능한 디코더 해상도</th>
<th>요구 사항</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>424x240</p></td>
<td><p>424x240(수신 전용 시나리오의 경우 15fps에서 640x360)</p></td>
<td><p>1개 코어 및 VideoEncodeScore ≥ 4.0</p></td>
</tr>
<tr class="even">
<td><p>640x360</p></td>
<td><p>640x360</p></td>
<td><p>2개 코어 및 VideoEncodeScore ≥ 4.5</p></td>
</tr>
<tr class="odd">
<td><p>640x360</p></td>
<td><p>1280x720</p></td>
<td><p>2개 코어 및 VideoEncodeScore ≥ 4.5</p></td>
</tr>
<tr class="even">
<td><p>640x360</p></td>
<td><p>1920x1080</p></td>
<td><p>4개 코어 및 VideoEncodeScore ≥ 4.5</p></td>
</tr>
<tr class="odd">
<td><p>1280x720</p></td>
<td><p>1280x720</p></td>
<td><p>4개 코어 및 VideoEncodeScore ≥ 7.3</p></td>
</tr>
<tr class="even">
<td><p>1280x720</p></td>
<td><p>1920x1080</p></td>
<td><p>4개 코어 및 VideoEncodeScore ≥ 7.3</p></td>
</tr>
<tr class="odd">
<td><p>1920x1080</p></td>
<td><p>1920x1080</p></td>
<td><p>해당 없음</p></td>
</tr>
<tr class="even">
<td><p>424x240</p></td>
<td><p>424x240(수신 전용 시나리오의 경우 15fps에서 640x360)</p></td>
<td><p>1개 코어 및 VideoEncodeScore ≥ 4.0</p></td>
</tr>
<tr class="odd">
<td><p>640x360</p></td>
<td><p>640x360</p></td>
<td><p>2개 코어 및 VideoEncodeScore ≥ 4.5</p></td>
</tr>
<tr class="even">
<td><p>640x360</p></td>
<td><p>1280x720</p></td>
<td><p>2개 코어 및 VideoEncodeScore ≥ 4.5</p></td>
</tr>
<tr class="odd">
<td><p>640x360</p></td>
<td><p>1920x1080</p></td>
<td><p>4개 코어 및 VideoEncodeScore ≥ 4.5</p></td>
</tr>
<tr class="even">
<td><p>1280x720</p></td>
<td><p>1280x720</p></td>
<td><p>4개 코어 및 VideoEncodeScore ≥ 7.3</p></td>
</tr>
<tr class="odd">
<td><p>1280x720</p></td>
<td><p>1920x1080</p></td>
<td><p>4개 코어 및 VideoEncodeScore ≥ 7.3</p></td>
</tr>
<tr class="even">
<td><p>1920x1080</p></td>
<td><p>1920x1080</p></td>
<td><p>해당 없음</p></td>
</tr>
</tbody>
</table>


### DXVA가 있지만 하드웨어 가속 인코더가 없는 컴퓨터

<table>
<colgroup>
<col style="width: 33%" />
<col style="width: 33%" />
<col style="width: 33%" />
</colgroup>
<thead>
<tr class="header">
<th>지원 가능한 인코더 해상도</th>
<th>지원 가능한 디코더 해상도</th>
<th>요구 사항</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>424x240</p></td>
<td><p>1920x1080</p></td>
<td><p>1개 코어 및 VideoEncodeScore ≥ 3.0</p></td>
</tr>
<tr class="even">
<td><p>640x360</p></td>
<td><p>1920x1080</p></td>
<td><p>2개 코어 및 VideoEncodeScore ≥ 4.5</p></td>
</tr>
<tr class="odd">
<td><p>960x540</p></td>
<td><p>1920x1080</p></td>
<td><p>2개 코어 및 VideoEncodeScore ≥ 6.0</p></td>
</tr>
<tr class="even">
<td><p>1280x720</p></td>
<td><p>1920x1080</p></td>
<td><p>4개 코어 및 VideoEncodeScore ≥ 6.7</p></td>
</tr>
<tr class="odd">
<td><p>1920x1080</p></td>
<td><p>1920x1080</p></td>
<td><p>4개 코어 및 VideoEncodeScore ≥ 8.2</p></td>
</tr>
<tr class="even">
<td><p>424x240</p></td>
<td><p>1920x1080</p></td>
<td><p>1개 코어 및 VideoEncodeScore ≥ 3.0</p></td>
</tr>
<tr class="odd">
<td><p>640x360</p></td>
<td><p>1920x1080</p></td>
<td><p>2개 코어 및 VideoEncodeScore ≥ 4.5</p></td>
</tr>
<tr class="even">
<td><p>960x540</p></td>
<td><p>1920x1080</p></td>
<td><p>2개 코어 및 VideoEncodeScore ≥ 6.0</p></td>
</tr>
<tr class="odd">
<td><p>1280x720</p></td>
<td><p>1920x1080</p></td>
<td><p>4개 코어 및 VideoEncodeScore ≥ 6.7</p></td>
</tr>
<tr class="even">
<td><p>1920x1080</p></td>
<td><p>1920x1080</p></td>
<td><p>4개 코어 및 VideoEncodeScore ≥ 8.2</p></td>
</tr>
</tbody>
</table>



> [!NOTE]
> Windows 7에서 WinSAT 점수는 최대 7.9로 제한됩니다. 따라서 하드웨어 가속 인코더가 없는 컴퓨터의 인코딩 성능은 최대 WinSAT 점수가 9.9인 Windows 8 또는 Windows 8.1에서만 얻을 수 있습니다.



### DXVA 및 Intel HD Graphics 하드웨어 가속 인코더가 있는 컴퓨터

<table>
<colgroup>
<col style="width: 33%" />
<col style="width: 33%" />
<col style="width: 33%" />
</colgroup>
<thead>
<tr class="header">
<th>지원 가능한 인코더 해상도</th>
<th>지원 가능한 디코더 해상도</th>
<th>요구 사항</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>1280x720</p></td>
<td><p>1920x1080</p></td>
<td><p>모든 2세대 및 3세대 Intel HD Graphics</p></td>
</tr>
<tr class="even">
<td><p>1920x1080</p></td>
<td><p>1920x1080</p></td>
<td><p>2세대 및 3세대 Intel HD Graphics 및 GraphicsScore ≥ 5.0</p></td>
</tr>
<tr class="odd">
<td><p>1280x720</p></td>
<td><p>1920x1080</p></td>
<td><p>모든 2세대 및 3세대 Intel HD Graphics</p></td>
</tr>
<tr class="even">
<td><p>1920x1080</p></td>
<td><p>1920x1080</p></td>
<td><p>2세대 및 3세대 Intel HD Graphics 및 GraphicsScore ≥ 5.0</p></td>
</tr>
</tbody>
</table>


## 모바일 장치 비디오 기능

다음 표에서는 지원되는 모바일 장치의 최대 비디오 기능에 대해 설명합니다. 모바일 장치 지원에 대한 자세한 내용은 [Lync Server 2013의 모바일 클라이언트 계획](lync-server-2013-planning-for-mobile-clients.md)을 참조하세요.


<table>
<colgroup>
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
</colgroup>
<thead>
<tr class="header">
<th>기능</th>
<th>Windows Phone</th>
<th>iPhone 및 iPad</th>
<th>Android</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>H.264 인코딩 최대 해상도</p></td>
<td><p>640x480</p></td>
<td><p>iPhone 4: 192x144</p>
<p>iPad 및 기타 지원되는 모든 iPhone 모델: 352x288</p></td>
<td><p>320x2401</p></td>
</tr>
<tr class="even">
<td><p>H.264 디코딩 최대 해상도</p></td>
<td><p>640x480</p></td>
<td><p>iPhone 및 iPad: 352x288</p></td>
<td><p>320x2401</p></td>
</tr>
<tr class="odd">
<td><p>H.264 인코딩 최대 해상도</p></td>
<td><p>640x480</p></td>
<td><p>iPhone 4: 192x144</p>
<p>iPad 및 기타 지원되는 모든 iPhone 모델: 352x288</p></td>
<td><p>320x2401</p></td>
</tr>
<tr class="even">
<td><p>H.264 디코딩 최대 해상도</p></td>
<td><p>640x480</p></td>
<td><p>iPhone 및 iPad: 352x288</p></td>
<td><p>320x2401</p></td>
</tr>
</tbody>
</table>


18x60 칩셋을 사용하는 Qualcomm Snapdragon S3 또는 S4 프로세서가 포함된 Android 장치의 경우 640x480 해상도로 보내고 받을 수 있습니다.

