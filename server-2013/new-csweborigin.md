---
title: New-CsWebOrigin
TOCTitle: New-CsWebOrigin
ms:assetid: 16053a99-b5ff-45e1-be95-b04e3f2fe528
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/JJ950236(v=OCS.15)
ms:contentKeyID: 52056789
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# New-CsWebOrigin

 

_**마지막으로 수정된 항목:** 2015-03-09_

Lync Server 2013 배포로 도메인 간 스크립팅 요청을 보내도록 허용되는 도메인 모음에 추가할 수 있는 새 도메인 개체를 만듭니다.

이 cmdlet은 Lync Server 2013용 누적 업데이트(2013년 2월)에 도입되었습니다.

## 구문

    New-CsWebOrigin -Url <String>

## 예제

## 예제 1

예제 1에 나와 있는 명령은 Redmond 사이트에 대해 만드는 새로운 웹 서비스 구성 설정 모음에 http://fabrikam.com 도메인을 추가합니다. 이 작업을 수행하기 위해 예제의 첫 번째 명령은 **New-CsWebOrigin** cmdlet을 사용하여 fabrikam.com에 대한 도메인 개체를 만듭니다. 그러면 생성되는 도메인 개체는 $x라는 변수에 저장됩니다.

예제의 두 번째 명령은 **New-CsWebServiceConfiguration** cmdlet을 사용하여 Redmond 사이트에 대해 웹 서비스 구성 설정을 만듭니다. "-CrossDomainAuthorizationList $x" 구문은 도메인 간 스크립팅 권한이 부여된 도메인 모음에 http://fabrikam.com을 추가합니다.

    $x = New-CsWebOrigin -Url "http://fabrikam.com"
    New-CsWebServiceConfiguration -Identity "site:Redmond" - CrossDomainAuthorizationList $x

## 예제 2

예제 2에 나와 있는 명령은 기존 웹 서비스 구성 설정 모음에 http://fabrikam.com 도메인을 추가합니다. 이 작업을 수행하기 위해 예제의 첫 번째 명령은 **New-CsWebOrigin** cmdlet을 사용하여 fabrikam.com에 대한 도메인 개체를 만듭니다. 그러면 생성되는 도메인 개체는 $x라는 변수에 저장됩니다.

예제의 두 번째 명령은 **Set-CsWebServiceConfiguration** cmdlet을 사용하여 Redmond 사이트에 적용된 웹 서비스 구성 설정에 http://fabrikam.com을 추가합니다. @{Add=$x} 구문은 도메인 간 스크립팅 권한이 부여된 도메인 모음에 이미 포함되어 있는 도메인에 해당 도메인을 추가합니다. http://fabrikam.com만 포함하도록 기존 도메인을 바꾸려면 @{Replace=$x} 구문을 사용합니다.

    $x = New-CsWebOrigin -Url "http://fabrikam.com"
    Set-CsWebServiceConfiguration -Identity "site:Redmond" - CrossDomainAuthorizationList @{Add=$x}

## 자세한 정보

New-CsWebOrigin cmdlet은 웹 응용 프로그램(Lync Server 2013 배포로 도메인 간 스크립팅 요청을 보내도록 허용됨)을 호스트할 권한이 있는 도메인을 지정하는 데 사용됩니다. 이 cmdlet은 주로 UCWA API(Unified Communications Web API) 외에 생성된 응용 프로그램에 사용됩니다.

웹 서비스 구성 설정 모음에 도메인을 추가하려면 먼저 New-CsWebOrigin cmdlet을 사용하여 도메인 개체를 만들어야 합니다. 메모리에만 있는 이 도메인 개체는 변수에 저장해야 합니다. 개체를 만든 후에는 New-CsWebServiceConfiguration cmdlet 또는 Set-CsWebServiceConfiguration cmdlet을 사용하여 웹 서비스 구성 설정 모음에 해당 개체를 추가할 수 있습니다.

직접 만든 사용자 지정 RBAC(역할 기반 액세스 제어) 역할을 포함하여 이 cmdlet이 할당된 모든 RBAC 역할의 목록을 반환하려면 Windows PowerShell 프롬프트에서 다음 명령을 실행합니다.

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "New-CsWebOrigin"}

**Lync Server 제어판:** **New-CsWebOrigin** cmdlet에 의해 수행되는 기능은 Lync Server 제어판에서는 사용할 수 없습니다.

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
<th>형식</th>
<th>설명</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><em>Url</em></p></td>
<td><p>필수</p></td>
<td><p>System.String</p></td>
<td><p>도메인 간 스크립팅 요청을 보낼 권한이 있는 도메인의 URL입니다. URL 앞에는 http: 또는 https: 접두사를 붙여야 합니다. 예를 들면 다음과 같습니다.</p>
<p>-Url &quot;http://contoso.com&quot;</p></td>
</tr>
</tbody>
</table>


## 입력 형식

없음. **New-CsWebOrigin** cmdlet은 파이프라인된 입력을 허용하지 않습니다.

## 반환 형식

**New-CsWebOrigin** cmdlet은 Microsoft.Rtc.Management.WritableConfig.Settings.Web.Origin 개체의 새 인스턴스를 만듭니다.

## 참고 항목

#### 기타 리소스

[New-CsWebServiceConfiguration](new-cswebserviceconfiguration.md)  
[Set-CsWebServiceConfiguration](set-cswebserviceconfiguration.md)

