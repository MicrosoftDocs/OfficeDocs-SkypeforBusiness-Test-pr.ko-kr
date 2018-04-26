---
title: Set-CsQoEConfiguration
TOCTitle: Set-CsQoEConfiguration
ms:assetid: 199f0127-7444-4f88-993a-8e6a33fdcb61
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg398245(v=OCS.15)
ms:contentKeyID: 49302954
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Set-CsQoEConfiguration

 

_**마지막으로 수정된 항목:** 2015-03-09_

QoE(체감 품질) 설정의 기존 컬렉션을 수정합니다. 이 cmdlet은 Lync Server 2010에서 도입되었습니다.

## 구문

    Set-CsQoEConfiguration [-Identity <XdsIdentity>] <COMMON PARAMETERS>

    Set-CsQoEConfiguration [-Instance <PSObject>] <COMMON PARAMETERS>

    COMMON PARAMETERS: [-Confirm [<SwitchParameter>]] [-EnableExternalConsumer <$true | $false>] [-EnablePurging <$true | $false>] [-EnableQoE <$true | $false>] [-ExternalConsumerIssuedCertId <IssuedCertId>] [-ExternalConsumerName <String>] [-ExternalConsumerURL <String>] [-Force <SwitchParameter>] [-KeepQoEDataForDays <UInt32>] [-PurgeHourOfDay <UInt32>] [-WhatIf [<SwitchParameter>]]

## 예제

## 예제 1

예제 1의 명령은 **Set-CsQoEConfiguration** cmdlet을 사용하여 Redmond 사이트(-Identity site:Redmond)의 체감 품질 설정을 수정합니다. 새 설정은 EnableQoE 매개 변수를 False로 설정하여 QoE를 해제합니다.

    Set-CsQoEConfiguration -Identity site:Redmond -EnableQoE $False

## 예제 2

이 명령은 Dublin 사이트에 적용되는 QoE 설정을 수정합니다. 이 예제에서는 KeepQoEDataForDays 매개 변수를 45로 설정하여 QoE 데이터가 45일 후에 데이터베이스에서 삭제되도록 했습니다. 또한 PurgeHourOfDay 매개 변수를 4로 설정하여 45일보다 오래된 데이터를 오전 4시에 삭제하도록 했습니다.

참고: QoE와 CDR(통화 정보 기록)을 사용하도록 설정한 경우 성능을 위해 QoE의 PurgeHourOfDay 설정을 CDR과 다르게 설정하는 것이 좋습니다.

    Set-CsQoEConfiguration -Identity site:Dublin -KeepQoEDataForDays 45 -PurgeHourOfDay 4

## 자세한 정보

QoE 품질 기준은 손실된 네트워크 패킷 수, 백그라운드 노이즈, "지터"(패킷 지연의 차이) 크기 등 조직의 오디오 및 비디오 통화 품질을 추적합니다. 이러한 품질 기준은 통화 정보 기록과 같은 다른 데이터와 별도로 데이터베이스에 저장되므로 다른 데이터 기록에 관계없이 QoE를 설정 및 해제할 수 있습니다. 이 cmdlet을 사용하여 전역 또는 사이트 수준에서 QoE를 구성하는 설정을 수정할 수 있습니다.

QoE는 모니터링 서버 역할의 일부입니다. 따라서 QoE 기록을 적용하거나 QoE 데이터를 수집하려면 먼저 Lync Server 설치에 모니터링 서버를 배포해야 합니다.

이 cmdlet을 실행할 수 있는 사용자: 기본적으로 RTCUniversalServerAdmins 그룹의 구성원은 **Set-CsQoEConfiguration** cmdlet을 로컬로 실행할 수 있습니다. 사용자가 직접 만든 사용자 지정 RBAC(역할 기반 액세스 제어) 역할을 포함하여 이 cmdlet이 할당된 모든 RBAC 역할의 목록을 반환하려면 Windows PowerShell 프롬프트에서 다음 명령을 실행합니다.

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Set-CsQoEConfiguration"}

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
<td><p><em>Confirm</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>명령을 실행하기 전에 확인 메시지를 표시합니다.</p></td>
</tr>
<tr class="even">
<td><p><em>EnableExternalConsumer</em></p></td>
<td><p>선택</p></td>
<td><p>System.Boolean</p></td>
<td><p>외부 소비자가 QoE 보고서를 받을 수 있는지 여부를 지정합니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>EnablePurging</em></p></td>
<td><p>선택</p></td>
<td><p>System.Boolean</p></td>
<td><p>KeepQoEDataForDays 속성에 정의된 기간이 경과한 후 레코드를 제거할지 여부를 지정합니다.</p></td>
</tr>
<tr class="even">
<td><p><em>EnableQoE</em></p></td>
<td><p>선택</p></td>
<td><p>System.Boolean</p></td>
<td><p>QoE 레코드를 수집하고 모니터링 데이터베이스에 저장할지 여부를 지정합니다.</p>
<p>EnableQoE를 True로 설정한 경우에도 모니터링 서버가 배포되고 등록자 풀과 연결되어 있지 않으면 QoE 데이터가 수집되지 않습니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>ExternalConsumerIssuedCertId</em></p></td>
<td><p>선택</p></td>
<td><p>Microsoft.Rtc.Management.WritableConfig.BaseTypes.IssuedCertId</p></td>
<td><p>외부 소비자 웹 서비스에 액세스를 허용하는 인증서의 인증서 ID입니다.</p></td>
</tr>
<tr class="even">
<td><p><em>ExternalConsumerName</em></p></td>
<td><p>선택</p></td>
<td><p>System.String</p></td>
<td><p>QoE 보고서에서 외부 소비자의 알기 쉬운 이름입니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>ExternalConsumerURL</em></p></td>
<td><p>선택</p></td>
<td><p>System.String</p></td>
<td><p>QoE 보고서가 게시되는 외부 소비자의 URL입니다.</p></td>
</tr>
<tr class="even">
<td><p><em>Force</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>변경하기 전에 표시되는 확인 메시지를 표시하지 않습니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>Identity</em></p></td>
<td><p>선택</p></td>
<td><p>Microsoft.Rtc.Management.Xds.XdsIdentity</p></td>
<td><p>수정할 설정의 고유한 식별자입니다. 가능한 값은 global 및 site:&lt;사이트 이름&gt;입니다. 여기서 &lt;사이트 이름&gt;은 변경 내용을 적용할 Lync Server 배포의 사이트 이름입니다.</p></td>
</tr>
<tr class="even">
<td><p><em>Instance</em></p></td>
<td><p>선택</p></td>
<td><p>QoE 설정</p></td>
<td><p>QoE 구성 개체에 대한 개체 참조입니다. 이 개체는 QoESettings 유형이어야 하며 <strong>Get-CsQoEConfiguration</strong> cmdlet을 호출하여 검색할 수 있습니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>KeepQoEDataForDays</em></p></td>
<td><p>선택</p></td>
<td><p>System.UInt32</p></td>
<td><p>QoE 데이터가 데이터베이스에서 삭제되기 전까지 저장되는 일 수입니다. EnablePurging을 False로 설정하면 이 값이 무시됩니다.</p>
<p>1에서 2562 사이의 값이어야 합니다.</p></td>
</tr>
<tr class="even">
<td><p><em>PurgeHourOfDay</em></p></td>
<td><p>선택</p></td>
<td><p>System.UInt32</p></td>
<td><p>KeepQoEDataForDays 속성에 지정된 일 수를 초과한 QoE 레코드가 삭제되는 시간입니다.</p>
<p>하루 중 시간을 나타내는 0부터 23까지의 값이어야 합니다. 예를 들어 0은 자정을 나타내고 13은 오후 1시를 나타냅니다.</p></td>
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

Microsoft.Rtc.Management.WritableConfig.Settings.QoE.QoESettings 개체입니다. QoE 구성 개체의 파이프라인된 입력을 허용합니다.

## 반환 형식

**Set-CsQoEConfiguration** cmdlet은 값이나 개체를 반환하지 않습니다. 대신 이 cmdlet은 Microsoft.Rtc.Management.WritableConfig.Settings.QoE.QoESettings 개체의 인스턴스를 구성합니다.

## 참고 항목

#### 기타 리소스

[New-CsQoEConfiguration](new-csqoeconfiguration.md)  
[Remove-CsQoEConfiguration](remove-csqoeconfiguration.md)  
[Get-CsQoEConfiguration](get-csqoeconfiguration.md)

