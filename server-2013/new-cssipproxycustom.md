---
title: New-CsSipProxyCustom
TOCTitle: New-CsSipProxyCustom
ms:assetid: 3dc75cb0-c3d2-48bd-af32-2b2034b655dd
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg425904(v=OCS.15)
ms:contentKeyID: 49303401
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# New-CsSipProxyCustom

 

_**마지막으로 수정된 항목:** 2015-03-09_

프록시 구성 설정 컬렉션에 사용자 지정 영역(SIP 통신 서비스)을 할당하는 데 사용됩니다. 영역(보호 도메인이라고도 함)은 로그온 중에 사용자 자격 증명을 인증하는 데 사용됩니다. 이 cmdlet은 Lync Server 2010에서 도입되었습니다.

## 구문

    New-CsSipProxyCustom -CustomValue <String>

## 예제

## 예제 1

예제 1에 표시된 명령은 사용자 지정 영역(Litwareinc Communications Service)을 $x라는 변수에 할당합니다.

    $x = New-CsSipProxyCustom -CustomValue "Litwareinc Communications Service"

## 자세한 정보

각 프록시 서버에 영역이 연결되어야 합니다. 영역(보호 도메인이라고도 함)은 사용자의 로그온 자격 증명을 처리할 위치를 나타냅니다. 기본적으로 Lync Server에서는 SIP 통신 서비스를 기본 영역으로 사용하지만 프록시 서버에 사용되는 영역을 변경할 수 있습니다. 이 작업을 수행하려면 SipProxy.Custom 개체를 만들어 해당 프록시 서버의 Realm 속성에 할당합니다. **New-CsSipProxyCustom** cmdlet을 사용하여 사용자 지정 영역을 만들 수 있습니다.

이 cmdlet을 실행할 수 있는 사용자: 기본적으로 RTCUniversalServerAdmins 그룹의 구성원은 **New-CsSipProxyCustom** cmdlet을 로컬로 실행할 수 있습니다. 사용자가 직접 만든 사용자 지정 RBAC(역할 기반 액세스 제어) 역할을 포함하여 이 cmdlet이 할당된 모든 RBAC 역할의 목록을 반환하려면 Windows PowerShell 프롬프트에서 다음 명령을 실행합니다.

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "New-CsSipProxyCustom"}

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
<td><p><em>CustomValue</em></p></td>
<td><p>필수</p></td>
<td><p>System.String</p></td>
<td><p>인증 용도로 사용할 영역의 이름입니다.</p></td>
</tr>
</tbody>
</table>


## 입력 형식

없음. **New-CsSipProxyCustom** cmdlet은 파이프라인된 입력을 허용하지 않습니다.

## 반환 형식

**New-CsSipProxyCustom** cmdlet은 Microsoft.Rtc.Management.WritableConfig.Settings.SipProxy.Custom 개체의 새 인스턴스를 만듭니다.

## 참고 항목

#### 기타 리소스

[New-CsSipProxyRealm](new-cssipproxyrealm.md)  
[New-CsSipProxyUseDefault](new-cssipproxyusedefault.md)

