---
title: New-CsQoEConfiguration
TOCTitle: New-CsQoEConfiguration
ms:assetid: 4fc607d5-1a85-4de5-9d18-39d0425c82dc
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg398325(v=OCS.15)
ms:contentKeyID: 49303610
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# New-CsQoEConfiguration

 

_**마지막으로 수정된 항목:** 2015-03-09_

새 QoE(체감 품질) 설정 컬렉션을 만듭니다. 이 cmdlet은 Lync Server 2010에서 도입되었습니다.

## 구문

    New-CsQoEConfiguration -Identity <XdsIdentity> [-Confirm [<SwitchParameter>]] [-EnableExternalConsumer <$true | $false>] [-EnablePurging <$true | $false>] [-EnableQoE <$true | $false>] [-ExternalConsumerIssuedCertId <IssuedCertId>] [-ExternalConsumerName <String>] [-ExternalConsumerURL <String>] [-Force <SwitchParameter>] [-InMemory <SwitchParameter>] [-KeepQoEDataForDays <UInt32>] [-PurgeHourOfDay <UInt32>] [-WhatIf [<SwitchParameter>]]

## 예제

## 예제 1

예제 1의 명령은 **New-CsQoEConfiguration** cmdlet을 사용하여 Identity가 site:Redmond인 새 QoE(체감 품질) 설정 집합을 만듭니다. 새 설정은 Identity가 site:Redmond일 뿐 아니라 EnableQoE 속성이 False로 설정됩니다. 사이트 설정이 전역 설정보다 우선하기 때문에 이 경우 전역 범위에서 QoE가 활성화되었는지 여부에 관계없이 Redmond 사이트에 대해 QoE가 비활성화됩니다.

    New-CsQoEConfiguration -Identity site:Redmond -EnableQoE $False

## 예제 2

이 명령은 Dublin 사이트에 적용되는 새 QoE 설정을 만듭니다. 이 예제에서는 KeepQoEDataForDays 매개 변수를 30으로 설정했으므로 기본값인 60일 대신 30일 후에 QoE 데이터가 데이터베이스에서 제거됩니다. 또한 PurgeHourOfDay 매개 변수를 4로 설정했으므로 방금 지정한 30일보다 오래된 모든 데이터가 오후 4시에 제거됩니다.

참고: QoE와 CDR(통화 정보 기록)을 사용하도록 설정한 경우 성능을 위해 QoE의 PurgeHourOfDay 설정을 CDR과 다르게 설정하는 것이 좋습니다.

    New-CsQoEConfiguration -Identity site:Dublin -KeepQoEDataForDays 30 -PurgeHourOfDay 4

## 자세한 정보

QoE 품질 기준은 손실된 네트워크 패킷 수, 백그라운드 노이즈, "지터"(패킷 지연의 차이) 크기 등 조직의 오디오 및 비디오 통화 품질을 추적합니다. 이러한 품질 기준은 통화 정보 기록과 같은 다른 데이터와 별도로 데이터베이스에 저장되므로 다른 데이터 기록에 관계없이 QoE를 설정 및 해제할 수 있습니다. 이 cmdlet을 사용하여 사이트 수준에서 QoE를 구성하는 설정을 만들 수 있습니다. 전역 수준의 설정은 기본적으로 존재하며 제거할 수 없습니다.

QoE는 모니터링 서버 역할의 일부입니다. 따라서 QoE 기록을 적용하거나 QoE 데이터를 수집하려면 먼저 Lync Server 설치에 모니터링 서버를 배포해야 합니다.

이 cmdlet을 실행할 수 있는 사용자: 기본적으로 RTCUniversalServerAdmins 그룹의 구성원은 **New-CsQoEConfiguration** cmdlet을 로컬로 실행할 수 있습니다. 사용자가 직접 만든 사용자 지정 RBAC(역할 기반 액세스 제어) 역할을 포함하여 이 cmdlet이 할당된 모든 RBAC 역할의 목록을 반환하려면 Windows PowerShell 프롬프트에서 다음 명령을 실행합니다.

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "New-CsQoEConfiguration"}

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
<td><p><em>Identity</em></p></td>
<td><p>필수</p></td>
<td><p>Microsoft.Rtc.Management.Xds.XdsIdentity</p></td>
<td><p>새 설정이 적용되는 사이트입니다. 이 값은 site:&lt;사이트 이름&gt; 형식으로 입력해야 하며, 여기서 &lt;사이트 이름&gt;은 Lync Server 배포의 사이트 이름입니다.</p></td>
</tr>
<tr class="even">
<td><p><em>Confirm</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>명령을 실행하기 전에 확인 메시지를 표시합니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>EnableExternalConsumer</em></p></td>
<td><p>선택</p></td>
<td><p>System.Boolean</p></td>
<td><p>외부 소비자가 QoE 보고서를 받을 수 있는지 여부를 지정합니다.</p>
<p>기본값: False</p></td>
</tr>
<tr class="even">
<td><p><em>EnablePurging</em></p></td>
<td><p>선택</p></td>
<td><p>System.Boolean</p></td>
<td><p>KeepQoEDataForDays 속성에 정의된 기간이 경과한 후 레코드를 제거할지 여부를 지정합니다.</p>
<p>기본값: True</p></td>
</tr>
<tr class="odd">
<td><p><em>EnableQoE</em></p></td>
<td><p>선택</p></td>
<td><p>System.Boolean</p></td>
<td><p>QoE 레코드를 수집하고 모니터링 데이터베이스에 저장할지 여부를 지정합니다.</p>
<p>EnableQoE를 True로 설정한 경우에도 모니터링 서버가 배포되고 등록자 풀과 연결되어 있지 않으면 QoE 데이터가 수집되지 않습니다.</p>
<p>기본값: True</p></td>
</tr>
<tr class="even">
<td><p><em>ExternalConsumerIssuedCertId</em></p></td>
<td><p>선택</p></td>
<td><p>Microsoft.Rtc.Management.WritableConfig.BaseTypes.IssuedCertId</p></td>
<td><p>외부 소비자 웹 서비스에 액세스할 수 있도록 하는 인증서의 인증서 ID입니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>ExternalConsumerName</em></p></td>
<td><p>선택</p></td>
<td><p>System.String</p></td>
<td><p>QoE 보고서의 외부 소비자 대화명입니다.</p></td>
</tr>
<tr class="even">
<td><p><em>ExternalConsumerURL</em></p></td>
<td><p>선택</p></td>
<td><p>System.String</p></td>
<td><p>QoE 보고서를 게시할 외부 소비자의 URL입니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>Force</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>변경하기 전에 표시되는 확인 메시지를 표시하지 않습니다.</p></td>
</tr>
<tr class="even">
<td><p><em>InMemory</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>개체를 실제로 영구 변경 사항으로 커밋하지 않고 개체 참조를 만듭니다. 이 매개 변수와 함께 호출된 이 cmdlet의 결과를 변수로 할당하면 개체 참조의 속성을 변경한 후 이 cmdlet과 일치하는 Set- cmdlet을 호출하여 해당 변경 사항을 커밋할 수 있습니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>KeepQoEDataForDays</em></p></td>
<td><p>선택</p></td>
<td><p>System.UInt32</p></td>
<td><p>데이터베이스에서 제거되기 전에 QoE 데이터를 저장할 기간(일)입니다. EnablePurging을 False로 설정하면 이 값은 무시됩니다.</p>
<p>1에서 2562 사이의 값이어야 합니다.</p>
<p>기본값: 60</p></td>
</tr>
<tr class="even">
<td><p><em>PurgeHourOfDay</em></p></td>
<td><p>선택</p></td>
<td><p>System.UInt32</p></td>
<td><p>KeepQoEDataForDays 속성에 지정된 기간(일)을 초과한 QoE 레코드를 제거할 시간입니다.</p>
<p>시간을 나타내는 0에서 23 사이의 값이어야 합니다. 예를 들어 0은 자정, 13은 오후 1:00입니다. 기본값: 1</p></td>
</tr>
<tr class="odd">
<td><p><em>WhatIf</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>명령을 실제로 실행하지 않고도 명령이 실행될 경우 발생할 수 있는 현상을 설명합니다.</p></td>
</tr>
</tbody>
</table>


## 입력 형식

없음.

## 반환 형식

Microsoft.Rtc.Management.WritableConfig.Settings.QoE.QoESettings 유형의 개체를 만듭니다.

## 참고 항목

#### 기타 리소스

[Remove-CsQoEConfiguration](remove-csqoeconfiguration.md)  
[Set-CsQoEConfiguration](set-csqoeconfiguration.md)  
[Get-CsQoEConfiguration](get-csqoeconfiguration.md)

