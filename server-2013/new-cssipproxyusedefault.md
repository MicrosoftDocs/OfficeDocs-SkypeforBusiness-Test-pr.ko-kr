---
title: New-CsSipProxyUseDefault
TOCTitle: New-CsSipProxyUseDefault
ms:assetid: 1e8bedca-8bd5-4559-b530-0f18ae23d6d3
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg398274(v=OCS.15)
ms:contentKeyID: 49303013
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# New-CsSipProxyUseDefault

 

_**마지막으로 수정된 항목:** 2015-03-09_

프록시 구성 설정 컬렉션에 기본 영역(SIP Communications Service)을 할당하는 데 사용됩니다. 영역(보호 도메인이라고도 함)은 로그온 중에 사용자 자격 증명을 인증하는 데 사용됩니다. 이 cmdlet은 Lync Server 2010에서 도입되었습니다.

## 구문

    New-CsSipProxyUseDefault

## 예제

## 예제 1

예제 1에 표시된 명령은 기본 영역(SIP Communications Service)을 $x라는 변수에 할당합니다.

    $x = New-CsSipProxyUseDefault

## 자세한 정보

프록시 서버를 사용하면 내부 네트워크의 외부 사용자가 내부 네트워크의 리소스에 액세스할 수 있습니다. 각 프록시 서버에 영역이 연결되어야 합니다. 영역(보호 도메인이라고도 함)은 사용자의 로그온 자격 증명을 처리할 위치를 나타냅니다. 기본적으로 Lync Server에서는 SIP 통신 서비스를 기본 영역으로 사용하지만 프록시 서버에 사용되는 영역을 변경할 수 있습니다. 영역을 변경한 다음 기본 영역을 사용하도록 되돌리려면 SipProxy.UseDefault 개체를 만들어 해당 프록시 서버의 Realm 속성에 할당합니다.

이 cmdlet을 실행할 수 있는 사용자: 기본적으로 RTCUniversalServerAdmins 그룹의 구성원은 **New-CsSipProxyUseDefault** cmdlet을 로컬로 실행할 수 있습니다. 사용자가 직접 만든 사용자 지정 RBAC(역할 기반 액세스 제어) 역할을 포함하여 이 cmdlet이 할당된 모든 RBAC 역할의 목록을 반환하려면 Windows PowerShell 프롬프트에서 다음 명령을 실행합니다.

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "New-CsSipProxyUseDefault"}

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
<tr class="even">
<td><p>이 cmdlet은 일반 Windows PowerShell 매개 변수만 제공합니다.</p>
<p></p></td>
<td><p></p></td>
<td><p></p></td>
<td><p></p></td>
</tr>
</tbody>
</table>


## 입력 형식

없음. **New-CsSipProxyUseDefault** cmdlet은 파이프라인된 입력을 허용하지 않습니다.

## 반환 형식

**New-CsSipProxyUseDefault** cmdlet은 Microsoft.Rtc.Management.WritableConfig.Settings.SipProxy.UseDefault 개체의 새 인스턴스를 만듭니다.

## 참고 항목

#### 기타 리소스

[New-CsSipProxyCustom](new-cssipproxycustom.md)  
[New-CsSipProxyRealm](new-cssipproxyrealm.md)

