---
title: 체감 품질 구성 설정 만들기
TOCTitle: 체감 품질 구성 설정 만들기
ms:assetid: 64f05569-07c7-4f76-a96b-ea4125a510d5
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg521006(v=OCS.15)
ms:contentKeyID: 49303849
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# 체감 품질 구성 설정 만들기

 

_**마지막으로 수정된 항목:** 2015-03-09_

QoE(체감 품질) 메트릭은 손실된 네트워크 패킷 수, 백그라운드 노이즈, "지터"(패킷 지연의 차이) 크기 등 조직의 음성 및 화상 통화 품질을 추적합니다. 이러한 품질 기준은 통화 정보 기록과 같은 다른 데이터와 별도로 데이터베이스에 저장되므로 다른 데이터 기록에 관계없이 QoE를 설정 및 해제할 수 있습니다.

Microsoft Lync Server 2013을 설치하면 QoE 구성 설정에 대한 단일 전역 컬렉션이 만들어집니다. 관리자도 사이트 범위에서 사용자 지정 설정을 만들 수 있습니다. 이러한 사이트 범위 설정을 사용할 때마다 전역 설정보다 우선 적용됩니다. 예를 들어 Redmond 사이트에 대해 사이트 범위의 설정을 만들었으면 해당 설정(전역 설정이 아니라)이 Redmond의 QoE를 관리하는 데 사용됩니다.

QoE 구성 설정은 Lync Server 제어판 또는 [New-CsQoEConfiguration](https://docs.microsoft.com/en-us/powershell/module/skype/New-CsQoEConfiguration) cmdlet을 사용하여 만들 수 있습니다. Lync Server 제어판을 사용해서 새 설정을 만들 경우 다음과 같은 옵션을 사용할 수 있습니다.


<table>
<colgroup>
<col style="width: 33%" />
<col style="width: 33%" />
<col style="width: 33%" />
</colgroup>
<thead>
<tr class="header">
<th>UI 설정</th>
<th>PowerShell 매개 변수</th>
<th>설명</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>이름</p></td>
<td><p>Identity</p></td>
<td><p>만들려는 설정에 대한 고유한 식별자입니다. QoE 구성 설정은 사이트 범위에서만 만들 수 있습니다.</p></td>
</tr>
<tr class="even">
<td><p>QoE 데이터에 대한 모니터링 사용</p></td>
<td><p>EnableQoE</p></td>
<td><p>QoE 레코드를 수집하고 모니터링 데이터베이스에 저장할지 여부를 지정합니다.</p></td>
</tr>
<tr class="odd">
<td><p>QoE 데이터에 대한 삭제 사용</p></td>
<td><p>EnablePurging</p></td>
<td><p><strong>QoE 데이터 보관 최대 기간(일 수)</strong> 속성에 정의된 기간이 경과한 후 레코드를 삭제할지 여부를 지정합니다.</p></td>
</tr>
<tr class="even">
<td><p>QoE 데이터 보관 최대 기간(일 수)</p></td>
<td><p>KeepQoEDataForDays</p></td>
<td><p>데이터베이스에서 삭제되기 전에 QoE 데이터를 저장할 기간(일)입니다. 삭제를 사용하지 않도록 설정하면 이 값이 무시됩니다.</p></td>
</tr>
</tbody>
</table>



> [!NOTE]
> New-CsQoEConfiguration cmdlet에는 Lync Server 제어판에서 사용할 수 없는 추가 옵션이 포함됩니다. 자세한 내용은 <A href="https://docs.microsoft.com/en-us/powershell/module/skype/New-CsQoEConfiguration">New-CsQoEConfiguration</A> 도움말 항목을 참조하십시오.



## Lync Server 제어판을 사용하여 QoE 구성 설정을 만들려면

1.  RTCUniversalServerAdmins 그룹의 구성원이나 CsVoiceAdministrator, CsServerAdministrator 또는 CsAdministrator 역할의 구성원으로 컴퓨터에 로그온합니다. 자세한 내용은 [Lync Server 2013에서 설치 권한 위임](lync-server-2013-delegate-setup-permissions.md)을 참조하세요.

2.  브라우저 창을 연 다음 Admin URL을 입력하여 Lync Server 제어판을 엽니다. Lync Server 제어판을 시작하는 데 사용할 수 있는 다양한 방법에 대한 자세한 내용은 [Lync Server 관리 도구 열기](lync-server-2013-open-lync-server-administrative-tools.md)를 참조하세요.

3.  왼쪽 탐색 모음에서 **모니터링 및 보관**을 클릭하고 **체감 품질 데이터**를 클릭합니다.

4.  **체감 품질 데이터** 페이지에서 **새로 만들기**를 클릭합니다.

5.  **사이트 선택**에서 정책을 적용할 사이트를 클릭하고 **확인**을 클릭합니다.

6.  **새 체감 품질 설정**에서 다음을 수행합니다.
    
      - **QoE 데이터 모니터링 사용**을 선택하여 모니터링을 설정합니다.
    
      - **QoE 데이터 삭제 사용**을 선택하여 삭제를 설정합니다.
    
      - **QoE 보관 최대 기간(일 수)**에서 QoE 레코드를 보관할 최대 기간(일 수)을 선택합니다.

7.  **커밋**을 클릭합니다.

## Windows PowerShell cmdlet을 사용하여 QoE 구성 설정을 만들려면

QoE 구성 설정은 Windows PowerShell 및 New-CsQoEConfiguration cmdlet을 사용하여 만들 수 있습니다. 이 cmdlet은 Lync Server 2013 관리 셸 또는 Windows PowerShell의 원격 세션에서 실행할 수 있습니다. 원격 Windows PowerShell을 사용하여 Lync Server에 연결하는 방법에 대한 자세한 내용은 Lync Server Windows PowerShell 블로그 문서인 "빠른 시작: 원격 PowerShell을 사용하여 Microsoft Lync Server 2010 관리"([http://go.microsoft.com/fwlink/p/?linkId=255876](http://go.microsoft.com/fwlink/p/?linkid=255876))를 참조하세요.

## QoE 구성 설정의 새 컬렉션을 만들려면

  - 이 명령은 Redmond 사이트에 적용되는 QoE 구성 설정의 새 컬렉션을 만듭니다.
    
        New-CsQoEConfiguration -Identity "site:Redmond"

## QoE 모니터링이 사용하지 않도록 설정된 QoE 구성 설정의 새 컬렉션을 만들려면

  - 이전 명령에서 매개 변수(필수 Identity 매개 변수 제외)가 지정되지 않았기 때문에 구성 설정의 새 컬렉션에는 모든 속성에 대해 기본값이 사용됩니다. 다른 속성 값을 사용하는 설정을 만들려면 단순히 적합한 매개 변수와 매개 변수 값을 포함합니다. 예를 들어 기본적으로 QoE 기록을 사용하지 않도록 설정하는 QoE(체감 품질) 구성 설정의 컬렉션을 만들려면 다음과 같은 명령을 사용합니다.
    
        New-CsQoEConfiguration -Identity "site:Redmond" -EnableQoE $False

## QoE 구성 설정의 새 컬렉션을 만들 때 여러 속성 값을 지정하려면

  - 여러 매개 변수를 포함하여 여러 속성 값을 지정할 수 있습니다. 예를 들어 다음 명령은 QoE 데이터를 30일 동안 보관하고 오전 3시에 오래된 데이터를 삭제하도록 지정하는 새 설정을 구성합니다.
    
        New-CsQoEConfiguration -Identity "site:Redmond" -KeepQoEDataForDays 30 -PurgeHourOfDay 3

자세한 내용은 [New-CsQoEConfiguration](https://docs.microsoft.com/en-us/powershell/module/skype/New-CsQoEConfiguration) cmdlet의 도움말 항목을 참조하십시오.

