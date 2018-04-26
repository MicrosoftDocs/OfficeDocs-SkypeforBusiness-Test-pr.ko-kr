---
title: Config.xml로 설치 작업 수행
TOCTitle: Config.xml로 설치 작업 수행
ms:assetid: 0813184a-ab40-417c-b3a3-c2090766b831
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/JJ204651(v=OCS.15)
ms:contentKeyID: 49302719
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Config.xml로 설치 작업 수행

 

_**마지막으로 수정된 항목:** 2015-03-09_

사용자 지정 설치에는 기본적으로 OCT(Office 사용자 지정 도구)가 사용되기는 하지만, 관리자는 Config.xml 파일을 사용하여 OCT에서 사용할 수 없는 추가 설치 지침을 지정할 수 있습니다. Config.xml 파일을 통해서만 수행할 수 있는 사용자 지정 작업은 다음과 같습니다.

  - 네트워크 설치 지점 경로 지정

  - 설치할 제품 선택

  - 설치 사용자 지정 파일 및 소프트웨어 업데이트의 위치와 로깅 구성

  - 사용자 이름 등의 설치 옵션 지정

  - Office를 설치하지 않고 사용자 컴퓨터에 LIS(로컬 설치 원본) 복사

  - 설치에 언어 추가 또는 설치에서 언어 제거

Config.xml 파일을 사용하여 Lync 2013 자동 설치를 구성하는 것이 좋습니다.

기본적으로 핵심 제품 폴더(예: \\*제품*.WW)에 저장된 Config.xml 파일은 설치 프로그램에 해당 제품을 설치하도록 명령합니다. 예를 들어 다음 폴더의 Config.xml 파일은 Lync 2013을 설치합니다.

  - \\\\server\\share\\Lync15\\Lync.WW \\Config.xml

아래 표에는 Lync 2013 설치에 가장 일반적으로 사용되는 Config.xml 요소가 나와 있습니다.

### Config.xml 요소

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th>요소</th>
<th>설명</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Configuration</p></td>
<td><p>최상위 요소(필수)입니다. Product=Lync 등의 Product 특성을 포함합니다.</p></td>
</tr>
<tr class="even">
<td><p>OptionState</p></td>
<td><p>특정 제품 기능이 설치 중에 처리되는 방법을 지정합니다. Outlook 2010의 설치를 방해하는 공유 구성 요소가 포함된 Business Connectivity Services의 설치를 방지하려면 다음 특성을 사용합니다.</p>
<ul>
<li><p>Id=&quot;LOBiMain&quot;</p></li>
<li><p>State=&quot;Absent&quot;</p></li>
<li><p>Children=&quot;Force&quot;</p></li>
</ul></td>
</tr>
<tr class="odd">
<td><p>Display</p>
<p></p></td>
<td><p>설치 프로그램에서 사용자에게 표시하는 UI의 수준입니다. 일반적인 특성은 다음과 같습니다.</p>
<ul>
<li><p>CompletionNotice=&quot;Yes&quot; | &quot;No&quot;(기본값)</p></li>
<li><p>AcceptEula=&quot;Yes&quot; | &quot;No&quot;(기본값)</p></li>
</ul></td>
</tr>
<tr class="even">
<td><p>Logging</p></td>
<td><p>설치 프로그램이 수행하는 로깅 종류에 대한 옵션입니다. 일반적인 특성은 다음과 같습니다.</p>
<ul>
<li><p>Type =&quot;Off&quot; | &quot;Standard&quot;(기본값) | &quot;Verbose&quot;</p></li>
<li><p>Template=”<em>파일 이름</em>.txt”(로그 파일의 이름)</p></li>
</ul></td>
</tr>
<tr class="odd">
<td><p>Setting</p></td>
<td><p>Windows Installer 속성의 값을 지정합니다. 일반적인 특성은 다음과 같습니다.</p>
<ul>
<li><p>Setting Id=&quot;<em>이름</em>&quot;(Windows Installer 속성의 이름)</p></li>
<li><p>Value=&quot;<em>값</em>&quot;(속성에 할당할 값)</p></li>
</ul></td>
</tr>
<tr class="even">
<td><p>DistributionPoint</p></td>
<td><p>설치를 실행할 네트워크 설치 지점의 정규화된 경로입니다. Location 특성을 포함합니다.</p>
<ul>
<li><p>Location=”<em>경로</em>”</p></li>
</ul></td>
</tr>
</tbody>
</table>


다음 예제에서는 일반적인 Lync 2013의 자동 설치용 Config.xml 파일을 보여 줍니다.

    <Configuration Product="Lync">
      <OptionState Id="LOBiMain" State="Absent" Children="Force" />
      <Display Level="None" CompletionNotice="No" AcceptEula="Yes" />
      <Logging Type="verbose" Path="%temp%" Template="LyncSetupVerbose(*).log" />
      <Setting Id="SETUP_REBOOT" Value="Never" />
      <DistributionPoint Location="\\server\share\Lync15" />
    </Configuration>

Config.xml 파일을 사용하여 Office 설치 및 유지 관리 작업을 수행하는 방법에 대한 자세한 내용은 [http://go.microsoft.com/fwlink/?linkid=267514\&clcid=0x412](http://go.microsoft.com/fwlink/?linkid=267514%26clcid=0x412)에서 확인할 수 있습니다.

## Config.xml 파일을 사용자 지정하려면

1.  메모장과 같은 텍스트 편집기 도구를 사용하여 Config.xml 파일을 엽니다.

2.  변경할 요소가 포함된 줄을 찾습니다.

3.  요소 항목을 사용하려는 자동 옵션으로 수정합니다. 주석 구분 기호 "\<\!--" 및 "--\>"은 제거해야 합니다. 예를 들어 다음과 같은 구문을 사용할 수 있습니다.
    
        < DistributionPoint Location="\\server\share\Lync15" />

4.  Config.xml 파일을 저장합니다.

