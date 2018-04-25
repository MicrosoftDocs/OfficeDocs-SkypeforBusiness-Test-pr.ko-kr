---
title: New-CsSipProxyRealm
TOCTitle: New-CsSipProxyRealm
ms:assetid: fedf9c71-5a23-4818-9f98-db5008a2ba74
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg413084(v=OCS.15)
ms:contentKeyID: 49305638
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# New-CsSipProxyRealm

 

_**마지막으로 수정된 항목:** 2015-03-09_

프록시 구성 설정 컬렉션에 기본 영역(SIP Communications Service)을 할당하는 데 사용됩니다. 영역(보호 도메인이라고도 함)은 로그온 중에 사용자 자격 증명을 인증하는 데 사용됩니다. 이 cmdlet은 Lync Server 2010에서 도입되었습니다.

## 구문

    New-CsSipProxyRealm -RealmChoice <IRealmChoice>

## 예제

## 예제 1

예제 1에 표시된 명령은 $y 변수에 기본 영역(SIP Communications Service)을 할당합니다. 이 작업을 수행하기 위해 첫 번째 명령은 **New-CsSipProxyUseDefault** cmdlet을 호출하여 SipProxy.UseDefault 개체를 만듭니다. 이 개체는 $x 변수에 저장됩니다.

두 번째 명령에서는 $x를 **New-CsSipProxyRealm** cmdlet 및 RealmChoice 매개 변수의 값으로 사용합니다. 그러면 $y 변수에 저장되는 새 프록시 영역 개체가 만들어집니다.

    $x = New-CsSipProxyUseDefault
    $y = New-CsSipProxyRealm -RealmChoice $x

## 예제 2

예제 2에 표시된 명령은 $y 변수에 사용자 지정 영역(Litwareinc Communications Service)을 할당합니다. 이 작업을 수행하기 위해 첫 번째 명령은 **New-CsSipProxyCustom** cmdlet을 호출하여 SipProxy.Custom 개체를 만듭니다. CustomValue Litwareinc Communications Service를 사용하는 이 개체는 $x 변수에 저장됩니다.

두 번째 명령에서는 **New-CsSipProxyRealm** 및 –RealmChoice 매개 변수와 함께 $x를 사용하여 새 사용자 지정 영역 개체를 만듭니다.

    $x = New-CsSipProxyCustom -CustomValue "Litwareinc Communications Service"
    $y = New-CsSipProxyRealm -RealmChoice $x

## 자세한 정보

프록시 서버를 사용하면 내부 네트워크 외부의 사용자가 내부 네트워크의 리소스에 액세스할 수 있습니다. 각 프록시 서버는 영역과 연결되어야 합니다. 영역(보호 도메인이라고도 함)은 사용자의 로그온 자격 증명을 처리해야 하는 위치를 나타냅니다. 기본적으로 Lync Server에서는 SIP 통신 서비스를 기본 영역으로 사용하지만 프록시 서버에서 사용되는 영역을 변경할 수 있습니다. **New-CsSipProxyUseDefault** cmdlet 및 **New-CsSipProxyCustom** cmdlet을 사용하여 프록시 서버에서 사용되는 영역을 변경할 수 있습니다. **New-CsSipProxyRealm** cmdlet을 사용하여 영역을 변경할 수도 있습니다. 하지만 이 cmdlet에는 추가 단계가 필요하므로 프록시 서버에서 사용되는 영역을 변경해야 할 때마다 다른 두 cmdlet을 사용하고자 할 수도 있습니다.

이 cmdlet을 실행할 수 있는 사용자: 기본적으로 RTCUniversalServerAdmins 그룹의 구성원은 **New-CsSipProxyRealm** cmdlet을 로컬로 실행할 수 있습니다. 사용자가 직접 만든 사용자 지정 RBAC(역할 기반 액세스 제어) 역할을 포함하여 이 cmdlet이 할당된 모든 RBAC 역할의 목록을 반환하려면 Windows PowerShell 프롬프트에서 다음 명령을 실행합니다.

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "New-CsSipProxyRealm"}

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
<td><p><em>RealmChoice</em></p></td>
<td><p>필수</p></td>
<td><p>Microsoft.Rtc.Management.WritableConfig.Settings.SipProxy.IRealmChoice</p></td>
<td><p>프록시 서버에서 사용할 영역을 나타내는 개체입니다. RealmChoice는 <strong>New-CsSipProxyUseDefault</strong> 또는 <strong>New-CsSipProxyCustom</strong> cmdlet을 사용하여 만들어야 합니다.</p></td>
</tr>
</tbody>
</table>


## 입력 형식

없음. **New-CsSipProxyRealm** cmdlet은 파이프라인된 입력을 허용하지 않습니다.

## 반환 형식

**New-CsSipProxyRealm** cmdlet은 Microsoft.Rtc.Management.WritableConfig.Settings.SipProxy.Realm 개체의 새 인스턴스를 만듭니다.

## 참고 항목

#### 기타 리소스

[New-CsSipProxyCustom](new-cssipproxycustom.md)  
[New-CsSipProxyUseDefault](new-cssipproxyusedefault.md)

