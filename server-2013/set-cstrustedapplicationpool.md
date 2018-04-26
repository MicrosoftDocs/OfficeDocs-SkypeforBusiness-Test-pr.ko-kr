---
title: Set-CsTrustedApplicationPool
TOCTitle: Set-CsTrustedApplicationPool
ms:assetid: 0f42d12b-d09a-41fd-892f-2b7515a35344
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg398187(v=OCS.15)
ms:contentKeyID: 49302824
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Set-CsTrustedApplicationPool

 

_**마지막으로 수정된 항목:** 2015-03-09_

신뢰할 수 있는 응용 프로그램을 호스트하는 컴퓨터가 포함된 풀을 수정합니다. 이 cmdlet은 Lync Server 2010에서 도입되었습니다.

## 구문

    Set-CsTrustedApplicationPool [-Identity <XdsGlobalRelativeIdentity>] [-AppSharingPortCount <UInt16>] [-AppSharingPortStart <UInt16>] [-AudioPortCount <UInt16>] [-AudioPortStart <UInt16>] [-Confirm [<SwitchParameter>]] [-Force <SwitchParameter>] [-OutboundOnly <$true | $false>] [-Registrar <String>] [-RequiresReplication <$true | $false>] [-ThrottleAsServer <$true | $false>] [-TreatAsAuthenticated <$true | $false>] [-VideoPortCount <UInt16>] [-VideoPortStart <UInt16>] [-WhatIf [<SwitchParameter>]]

## 예제

## 예제 1

이 예제에서는 FQDN이 TrustPool.litwareinc.com인 풀을 수정합니다. Identity 매개 변수를 사용하여 수정할 풀의 FQDN을 지정합니다. 또한 OutboundOnly 매개 변수에 대해 값 True($True)를 지정하여 풀의 OutboundOnly 속성을 수정합니다. 기본값은 False입니다.

    Set-CsTrustedApplicationPool -Identity TrustPool.litwareinc.com -OutboundOnly $True

## 자세한 정보

Lync Server 배포 내에서 신뢰할 수 있는 응용 프로그램을 실행하는 컴퓨터는 신뢰할 수 있는 응용 프로그램 전용으로 사용되는 별도의 풀에 추가하는 것이 좋습니다. 그러나 다용도로 사용되는 기존 풀에 신뢰할 수 있는 응용 프로그램 컴퓨터를 추가할 수도 있습니다. **Set-CsTrustedApplicationPool** cmdlet은 기존의 트러스트된 응용 프로그램 풀에 대한 설정을 수정합니다. 풀과 연결된 컴퓨터는 이 cmdlet을 사용하여 수정할 수 없으며, 이 작업을 수행하려면 CsTrustedApplicationComputer cmdlet을 사용해야 합니다.

이 cmdlet을 실행할 수 있는 사용자: 기본적으로 RTCUniversalServerAdmins 그룹의 구성원은 **Set-CsTrustedApplicationPool** cmdlet을 로컬로 실행할 수 있습니다. 사용자가 직접 만든 사용자 지정 RBAC(역할 기반 액세스 제어) 역할을 포함하여 이 cmdlet이 할당된 모든 RBAC 역할의 목록을 반환하려면 Windows PowerShell 프롬프트에서 다음 명령을 실행합니다.

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Set-CsTrustedApplicationPool"}

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
<td><p><em>AppSharingPortCount</em></p></td>
<td><p>선택</p></td>
<td><p>System.UInt16</p></td>
<td><p>응용 프로그램 공유 연결의 포트 범위에서 사용할 수 있는 포트의 개수입니다.</p></td>
</tr>
<tr class="even">
<td><p><em>AppSharingPortStart</em></p></td>
<td><p>선택</p></td>
<td><p>System.UInt16</p></td>
<td><p>응용 프로그램 공유 연결에 사용할 수 있는 포트 범위에서 첫 번째 포트의 번호입니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>AudioPortCount</em></p></td>
<td><p>선택</p></td>
<td><p>System.UInt16</p></td>
<td><p>오디오 연결의 포트 범위에서 사용할 수 있는 포트의 개수입니다.</p></td>
</tr>
<tr class="even">
<td><p><em>AudioPortStart</em></p></td>
<td><p>선택</p></td>
<td><p>System.UInt16</p></td>
<td><p>오디오 연결에 사용할 수 있는 포트 범위에서 첫 번째 포트의 번호입니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>Confirm</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>명령을 실행하기 전에 확인 메시지를 표시합니다.</p></td>
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
<td><p>Microsoft.Rtc.Management.Xds.XdsGlobalRelativeIdentity</p></td>
<td><p>설정을 수정하려는 풀의 FQDN(정규화된 도메인 이름) 또는 서비스 ID입니다.</p></td>
</tr>
<tr class="even">
<td><p><em>OutboundOnly</em></p></td>
<td><p>선택</p></td>
<td><p>System.Boolean</p></td>
<td><p>신뢰할 수 있는 응용 프로그램이 풀의 서버에 대해 연결을 시작할 수 있는지 지정합니다. 모든 연결을 응용 프로그램이 아닌 서버에서 시작하려면 이 값을 True로 설정합니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>Registrar</em></p></td>
<td><p>선택</p></td>
<td><p>System.String</p></td>
<td><p>풀 등록자 서비스의 서비스 ID 또는 FQDN입니다. 등록자를 변경하면 응용 프로그램과 연결된 모든 연락처가 분리됩니다. 이러한 연락처는 <strong>Move-CsApplicationEndpoint</strong> cmdlet을 호출하여 이동해야 합니다.</p></td>
</tr>
<tr class="even">
<td><p><em>RequiresReplication</em></p></td>
<td><p>선택</p></td>
<td><p>System.Boolean</p></td>
<td><p>이 풀에 복제가 필요한지 여부를 지정합니다. 복제가 필요하지 않은 경우 이 값을 False로 설정합니다. 일반적으로 Microsoft Outlook Web Access 및 수동으로 프로비전되는 응용 프로그램의 경우 이 매개 변수를 False로 설정합니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>ThrottleAsServer</em></p></td>
<td><p>선택</p></td>
<td><p>System.Boolean</p></td>
<td><p>풀의 서버와 신뢰할 수 있는 응용 프로그램 간의 연결을 클라이언트로 제한하려면 이 매개 변수를 false로 설정합니다. 이렇게 하면 연결을 서버로 제한하는 기본값 True보다 연결에 더 많은 제한이 적용됩니다. 연결을 제한하면 동시에 발생할 수 있는 트랜잭션 수에 대해 제한이 적용됩니다.</p></td>
</tr>
<tr class="even">
<td><p><em>TreatAsAuthenticated</em></p></td>
<td><p>선택</p></td>
<td><p>System.Boolean</p></td>
<td><p>풀의 서버에 연결하는 신뢰할 수 있는 응용 프로그램에 인증을 요구할지 여부를 지정합니다. 신뢰할 수 있는 응용 프로그램에 인증을 요구하려면 이 매개 변수를 False로 설정합니다. 기본값 True는 신뢰할 수 있는 응용 프로그램이 이미 인증되었다는 가정하에 연결을 허용합니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>VideoPortCount</em></p></td>
<td><p>선택</p></td>
<td><p>System.UInt16</p></td>
<td><p>비디오 연결의 포트 범위에서 사용할 수 있는 포트의 개수입니다.</p></td>
</tr>
<tr class="even">
<td><p><em>VideoPortStart</em></p></td>
<td><p>선택</p></td>
<td><p>System.UInt16</p></td>
<td><p>비디오 연결에 사용할 수 있는 포트 범위에서 첫 번째 포트의 번호입니다.</p></td>
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

Microsoft.Rtc.Management.Xds.DisplayExternalServer 개체입니다. 신뢰할 수 있는 응용 프로그램 풀 개체의 파이프라인된 입력을 허용합니다.

## 반환 형식

이 cmdlet은 값을 반환하지 않습니다. Microsoft.Rtc.Management.Xds.DisplayExternalServer 유형의 개체를 수정합니다.

## 참고 항목

#### 기타 리소스

[New-CsTrustedApplicationPool](new-cstrustedapplicationpool.md)  
[Remove-CsTrustedApplicationPool](remove-cstrustedapplicationpool.md)  
[Get-CsTrustedApplicationPool](get-cstrustedapplicationpool.md)  
[New-CsTrustedApplicationComputer](new-cstrustedapplicationcomputer.md)

