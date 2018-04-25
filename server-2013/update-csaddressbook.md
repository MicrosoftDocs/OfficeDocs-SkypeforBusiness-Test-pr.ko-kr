---
title: Update-CsAddressBook
TOCTitle: Update-CsAddressBook
ms:assetid: 109c5fe7-0154-4161-b19f-01bab024bb3d
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg398194(v=OCS.15)
ms:contentKeyID: 49302836
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Update-CsAddressBook

 

_**마지막으로 수정된 항목:** 2015-03-09_

지정된 주소록 서버의 콘텐츠를 사용자 데이터베이스와 강제로 동기화합니다. 이 cmdlet은 Lync Server 2010에서 도입되었습니다.

## 구문

    Update-CsAddressBook [-Force <SwitchParameter>] [-Fqdn <Fqdn>]

## 예제

## 예제 1

예제 1에서는 **Update-CsAddressBook** cmdlet을 매개 변수 없이 호출합니다. 이에 따라 조직의 모든 주소록 서버가 동기화됩니다.

    Update-CsAddressBook

## 예제 2

예제 2에서는 FQDN이 atl-abs-001.litwareinc.com인 하나의 주소록 서버만 동기화합니다.

    Update-CsAddressBook -Fqdn atl-abs-001.litwareinc.com

## 자세한 정보

주소록 서버는 Active Directory와 Lync Server 간의 중계자입니다. 주소록 서버를 사용하면 Lync Server에 저장된 사용자 정보와 Active Directory에 저장된 사용자 정보가 동기화됩니다. 이 작업은 주소록 파일을 사용자 데이터베이스에 저장된 정보와 주기적으로 동기화하는 방식으로 수행됩니다. 기본적으로 이 동기화는 5분마다 수행됩니다. 그러나 시간 간격은 **Set-CsAddressBookConfiguration** cmdlet을 사용하여 수정할 수 있습니다.

동기화가 수행되는 것을 기다릴 수 없거나 어떤 이유에서 동기화가 수행되지 않는 것으로 보이는 경우 **Update-CsAddressBook** cmdlet을 사용하여 주소록 서버를 즉시 사용자 데이터베이스에 저장된 사용자 정보와 강제로 동기화할 수 있습니다.

이 cmdlet을 실행할 수 있는 사용자: 기본적으로 RTCUniversalUserAdmins 및 RTCUniversalServerAdmins 그룹의 구성원은 **Update-CsAddressBook** cmdlet을 로컬로 실행할 수 있습니다. 사용자가 직접 만든 사용자 지정 RBAC(역할 기반 액세스 제어) 역할을 포함하여 이 cmdlet이 할당된 모든 RBAC 역할의 목록을 반환하려면 Windows PowerShell 프롬프트에서 다음 명령을 실행합니다.

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Update-CsAddressBook"}

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
<td><p><em>Force</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>cmdlet을 실행할 때 나타날 수 있는 확인 프롬프트 또는 심각하지 않은 오류 메시지를 표시하지 않습니다.</p></td>
</tr>
<tr class="even">
<td><p><em>Fqdn</em></p></td>
<td><p>선택</p></td>
<td><p>Microsoft.Rtc.Management.Deploy.Fqdn</p></td>
<td><p>업데이트할 개별 주소록을 지정하는 데 사용됩니다. 이 매개 변수를 포함하지 않으면 모든 주소록 서버가 사용자 데이터베이스와 동기화됩니다. 개별 주소록 서버는 FQDN(정규화된 도메인 이름)(예: atl-abs-001.litwareinc.com)으로 참조해야 합니다.</p></td>
</tr>
</tbody>
</table>


## 입력 형식

없음. **Update-CsAddressBook** cmdlet은 파이프라인된 입력을 허용하지 않습니다.

## 반환 형식

없음. 대신 **Update-CsAddressBook** cmdlet은 Microsoft.Rtc.Management.WriteableConfig.Settings.AddressBook.AddressBookSettings 개체의 기존 인스턴스를 업데이트합니다.

## 참고 항목

#### 기타 리소스

[Get-CsAddressBookConfiguration](get-csaddressbookconfiguration.md)  
[Test-CsAddressBookService](test-csaddressbookservice.md)  
[Test-CsAddressBookWebQuery](test-csaddressbookwebquery.md)

