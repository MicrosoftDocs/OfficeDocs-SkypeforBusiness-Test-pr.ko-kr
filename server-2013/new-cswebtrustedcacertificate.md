---
title: New-CsWebTrustedCACertificate
TOCTitle: New-CsWebTrustedCACertificate
ms:assetid: a0a94971-372a-401a-8ae0-9ff649a9c301
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg412746(v=OCS.15)
ms:contentKeyID: 49304560
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# New-CsWebTrustedCACertificate

 

_**마지막으로 수정된 항목:** 2015-03-09_

기존 CA(인증 기관) 인증서를 기반으로 새 인증서 ID 개체를 만듭니다. 이 cmdlet은 Lync Server 2010에서 도입되었습니다.

## 구문

    New-CsWebTrustedCACertificate -CAStore <TrustedRootCA | IntermediateCA | ThirdPartyRootCA> -Thumbprint <String>

## 예제

## 예제 1

예제 1에 표시된 명령은 신뢰할 수 있는 새 CA 인증서를 만든 다음 Redmond 사이트에 대한 웹 서비스 구성 설정의 TrustedCACerts 속성에 해당 인증서를 추가합니다. 이 작업을 수행하기 위해 이 예제의 첫 번째 명령은 **New-CsWebTrustedCACertificate** cmdlet을 사용하여 신뢰할 수 있는 새 CA 인증서를 만듭니다. 이 인증서는 신뢰할 수 있는 루트 인증서 저장소에 있으며 지문은 D543DFF74FEEA425162FD25F342786F1AB453BB3입니다. 결과 인증서 개체는 $x라는 변수에 저장됩니다.

인증서 개체를 만든 후 이 예제의 두 번째 명령은 해당 인증서를 TrustedCACerts 속성에 추가합니다. 이 작업을 수행하기 위해 이 명령은 **Set-CsWebServiceConfiguration** cmdlet과 TrustedCACerts 매개 변수를 사용합니다. 매개 변수 값 ${Add=$x}는 변수 $x에 저장된 인증서를 신뢰할 수 있는 CA 인증서 컬렉션에 추가하도록 cmdlet에 지시합니다.

    $x = New-CsWebTrustedCACertificate -Thumbprint "D543DFF74FEEA425162FD25F342786F1AB453BB3" -CAStore TrustedRootCA
    
    Set-CsWebServiceConfiguration -Identity site:Redmond -TrustedCACerts @{Add=$x}

## 자세한 정보

웹 서비스 구성 설정은 Lync Server 웹 서버 및 웹 서비스 관리를 지원하는 데 사용됩니다. 이러한 설정을 사용하여 관리할 수 있는 속성 값 중에 TrustedCACerts 속성이 있습니다. 이 속성은 Lync Phone Edition에서 신뢰하는 인증 기관의 컬렉션을 나타냅니다. 신뢰할 수 있는 CA에서 가져온 인증서를 통해 이러한 클라이언트에서 Lync Server를 실행하는 서버에 대한 연결의 보안을 향상시킬 수 있습니다. 신뢰할 수 있는 인증 기관의 컬렉션에 새 CA를 추가하려면 로컬 컴퓨터의 인증서 저장소에 해당 CA에 대한 인증서 체인을 추가해야 합니다. 인증서 체인이 추가되었는지 확인한 후에는 **New-CsWebTrustedCACertificate** cmdlet을 사용하여 웹 서비스 구성 설정에 추가할 수 있는 인증서 ID 개체를 만들 수 있습니다.

Lync Server를 설치할 때 사용된 기본 서버 인증서를 서명한 인증 기관은 신뢰할 수 있는 CA에 자동으로 포함되므로 웹 서비스 구성 설정 컬렉션의 TrustedCACerts 속성에 추가할 필요가 없습니다. TrustedCACerts는 기본 인증서를 발급한 CA 외에 신뢰할 필요가 있는 CA의 ID만 포함해야 합니다. 대부분의 경우 기본 인증서를 발급한 CA만 신뢰할 필요가 있는 인증 기관입니다.

이 cmdlet을 실행할 수 있는 사용자: 기본적으로 RTCUniversalServerAdmins 그룹의 구성원은 **New-CsWebTrustedCACertificate** cmdlet을 로컬로 실행할 수 있습니다. 사용자가 직접 만든 사용자 지정 RBAC(역할 기반 액세스 제어) 역할을 포함하여 이 cmdlet이 할당된 모든 RBAC 역할의 목록을 반환하려면 Windows PowerShell 프롬프트에서 다음 명령을 실행합니다.

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "New-CsWebTrustedCACertificate"}

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
<td><p><em>CAStore</em></p></td>
<td><p>필수</p></td>
<td><p>Microsoft.Rtc.Management.WritableConfig.Settings.Web.CAStore</p></td>
<td><p>인증서가 저장된 로컬 컴퓨터의 인증서 저장소 이름을 나타냅니다. 사용할 수 있는 값은 다음과 같습니다.</p>
<p>TrustedRootCA</p>
<p>IntermediateCA</p>
<p>ThirdPartyRootCA</p></td>
</tr>
<tr class="even">
<td><p><em>Thumbprint</em></p></td>
<td><p>필수</p></td>
<td><p>System.String</p></td>
<td><p>Lync Phone Edition에서 신뢰할 수 있어야 하는 인증서 지문입니다. 다음 명령을 실행하여 인증서 발급자 및 지문 값을 검색할 수 있습니다.</p>
<p>Get-CsCertificate | Select-Object Issuer, Thumbprint</p></td>
</tr>
</tbody>
</table>


## 입력 형식

없음. **New-CsWebTrustedCACertificate** cmdlet은 파이프라인된 입력을 허용하지 않습니다.

## 반환 형식

**New-CsWebTrustedCACertificate** cmdlet은 Microsoft.Rtc.Management.WritableConfig.Settings.Web.CACertID 개체의 새 인스턴스를 만듭니다.

## 참고 항목

#### 기타 리소스

[New-CsWebServiceConfiguration](new-cswebserviceconfiguration.md)  
[Set-CsWebServiceConfiguration](set-cswebserviceconfiguration.md)

