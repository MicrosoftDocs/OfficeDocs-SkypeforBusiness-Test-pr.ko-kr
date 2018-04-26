---
title: 2단계 인증 계획
TOCTitle: 2단계 인증 계획
ms:assetid: 16f08710-8961-4659-acbf-ebb95a198fb4
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Dn308562(v=OCS.15)
ms:contentKeyID: 56270218
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# 2단계 인증 계획

 

_**마지막으로 수정된 항목:** 2015-04-06_

다음은 2단계 인증을 지원하도록 Microsoft Lync Server 2013 환경을 구성할 때 배포 고려 사항 목록입니다.

## 클라이언트 지원

Lync Server 2013용 누적 업데이트(2013년 7월)가 적용된 Lync 2013 데스크톱 클라이언트는 현재 2단계 인증을 지원하는 유일한 Lync 클라이언트입니다.

## 토폴로지 요구 사항

고객은 Lync Server 2013용 누적 업데이트(2013년 7월): 에지, 디렉터 및 사용자 풀이 포함된 전용 Lync Server 2013을 사용하여 2단계 인증을 배포하는 것이 좋습니다. Lync 사용자가 사용할 수 있도록 수동 인증을 설정하려면 다른 역할 및 서비스에 대해 다음을 포함하는 기타 인증 방법을 사용하지 않도록 설정해야 합니다.


<table>
<colgroup>
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
</colgroup>
<thead>
<tr class="header">
<th>구성 유형</th>
<th>서비스 종류</th>
<th>서버 역할</th>
<th>해제할 인증 유형</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>웹 서비스</p></td>
<td><p>WebServer</p></td>
<td><p>디렉터</p></td>
<td><p>Kerberos, NTLM, 인증서</p></td>
</tr>
<tr class="even">
<td><p>웹 서비스</p></td>
<td><p>WebServer</p></td>
<td><p>프런트 엔드</p></td>
<td><p>Kerberos, NTLM, 인증서</p></td>
</tr>
<tr class="odd">
<td><p>프록시</p></td>
<td><p>EdgeServer</p></td>
<td><p>에지</p></td>
<td><p>Kerberos 및 NTLM</p></td>
</tr>
<tr class="even">
<td><p>프록시</p></td>
<td><p>등록자</p></td>
<td><p>프런트 엔드</p></td>
<td><p>Kerberos 및 NTLM</p></td>
</tr>
</tbody>
</table>


서비스 수준에서 이 인증 유형을 사용하지 않도록 설정된 경우를 제외하면 배포 시 2단계 인증을 설정하면 Lync 클라이언트의 다른 모든 버전에서 로그인할 수 없습니다.

## Lync 서비스 검색

내부/외부 클라이언트에서 Lync 서비스를 검색하기 위해 사용하는 DNS 레코드는 2단계 인증이 해제된 Lync 서버를 확인하도록 구성해야 합니다. 이 구성을 통해 2단계 인증을 사용할 수 없는 Lync 풀의 사용자는 PIN을 입력하지 않아도 인증할 수 있지만 2단계 인증을 사용할 수 있는 Lync 풀의 사용자는 PIN을 입력해야만 인증할 수 있습니다.

## Exchange 인증

Microsoft Exchange에 대해 2단계 인증을 배포한 고객의 경우 Lync 클라이언트의 특정 기능을 사용하지 못할 수도 있습니다. 현재 Lync 클라이언트는 Exchange 통합에 의존하는 기능에 대해 기본적으로 2단계 인증을 지원하지 않도록 설계되었습니다.

## Lync 대화 상대

통합 연락처 저장소 기능을 활용하도록 구성된 Lync 사용자의 경우 2단계 인증을 사용하여 로그인한 후에는 대화 상대를 더 이상 볼 수 없습니다.

2단계 인증을 설정하기 전에 **Invoke-CsUcsRollback** cmdlet을 사용하여 통합 연락처 저장소에서 기존 사용자 대화 상대를 제거하고 Lync Server 2013에 저장해야 합니다.

## 기술 검색

Lync 환경에서 기술 검색 기능을 구성한 고객의 경우 2단계 인증을 사용하도록 Lync를 구성하면 이 기능이 작동하지 않습니다. Microsoft SharePoint가 현재 2단계 인증을 지원하지 않기 때문에 이는 정상적인 동작입니다.

## Lync 자격 증명

저장된 Lync 자격 증명과 관련하여 2단계 인증을 사용하도록 구성된 사용자에게 영향을 줄 수 있는 여러 가지 배포 고려 사항이 있습니다.

## 저장된 자격 증명 삭제

사용자는 처음으로 2단계 인증을 사용해 서명하기 전에 Lync 클라이언트에서 **내 로그인 정보 삭제** 옵션을 사용하고 %localappdata%\\Microsoft\\Office\\15.0\\Lync에서 SIP 프로필 폴더를 삭제해야 합니다.

## DisableNTCredentials

Kerberos 또는 NTLM 인증 방법을 사용할 경우 사용자의 Windows 자격 증명이 인증에 자동으로 사용됩니다. 인증에 Kerberos 및/또는 NTLM을 사용할 수 있는 일반적인 Lync Server 2013 배포의 경우 사용자는 로그인할 때마다 자격 증명을 입력하지 않아도 됩니다.

사용자에게 PIN을 입력하라는 메시지가 나타나기 전에 자격 증명을 묻는 메시지가 나타나면 의도와 다르게 클라이언트 컴퓨터에서 그룹 정책을 통해 **DisableNTCredentials** 레지스트리 키가 구성될 수 있습니다.

자격 증명을 묻는 추가 메시지가 표시되지 않게 하려면 로컬 워크스테이션에 다음 레지스트리 키를 만들거나 Lync 관리 템플릿을 사용하여 그룹 정책을 사용하는 풀에 대한 모든 사용자에게 적용합니다.

HKEY\_LOCAL\_MACHINE\\Software\\Policies\\Microsoft\\Office\\15.0\\Lync

REG\_DWORD: DisableNTCredentials

값: 0x0

## SavePassword

사용자가 최초로 Lync에 로그인하면 암호를 저장하라는 메시지가 나타납니다. 선택할 경우 이 옵션을 통해 사용자의 클라이언트 인증서를 개인 인증서 저장소에 저장하고 사용자의 Windows 자격 증명을 로컬 컴퓨터의 자격 증명 관리자에 저장할 수 있습니다.

2단계 인증을 지원하도록 Lync를 구성한 경우 **SavePassword** 레지스트리 설정을 사용하지 않도록 설정해야 합니다. 사용자가 암호를 저장하지 못하게 하려면 로컬 워크스테이션에서 다음 레지스트리 키를 변경하거나 Lync 관리 양식을 사용하여 그룹 정책을 사용하는 풀에 대한 모든 사용자에게 적용합니다.

HKEY\_CURRENT\_USER\\Software\\Microsoft\\Office\\15.0\\Lync

REG\_DWORD: SavePassword

값: 0x0

## AD FS 2.0 토큰 재생

AD FS 2.0에서는 토큰 재생 검색이라고 하는 기능을 제공합니다. 이는 동일한 토큰을 사용한 여러 토큰 요청이 검색된 후에 버려지는 기능입니다. 이 기능을 사용하도록 설정하면 WS-Federation 수동 프로필과 SAML WebSSO 프로필에서 동일한 토큰이 한 번만 사용되도록 하여 인증 요청의 무결성을 보호합니다.

이 기능은 키오스크와 같이 보안이 중요하게 여겨지는 경우에 사용하도록 설정해야 합니다. 토큰 재생 검색에 대한 자세한 내용은 [http://go.microsoft.com/fwlink/p/?LinkId=309215](http://go.microsoft.com/fwlink/p/?linkid=309215)에서 'AD FS 2.0의 보안 계획 및 배포를 위한 모범 사례(영어)'를 참고하세요.

## 외부 사용자 액세스

외부 네트워크에서 2단계 인증을 지원하도록 ADFS 프록시 또는 역방향 프록시를 구성하는 방법은 이 항목에서 다루지 않습니다.

