---
title: 'Lync Server 2013: Lync Server 하이브리드 환경을 준비 및 배포하기 위한 단계'
TOCTitle: Lync Server 2013 하이브리드 환경을 준비 및 배포하기 위한 단계
ms:assetid: a50d4f7b-63f4-4663-af63-56ca87e4e3e7
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/JJ205157(v=OCS.15)
ms:contentKeyID: 49304610
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Lync Server 2013 하이브리드 환경을 준비 및 배포하기 위한 단계

 

_**마지막으로 수정된 항목:** 2015-03-09_

다음 표에는 Microsoft Lync Online 및 Microsoft Office 365의 하이브리드 배포용으로 환경을 준비하기 위해 실행해야 하는 단계가 나와 있습니다.


<table>
<colgroup>
<col style="width: 33%" />
<col style="width: 33%" />
<col style="width: 33%" />
</colgroup>
<thead>
<tr class="header">
<th>완료</th>
<th>단계</th>
<th>설명</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p></p></td>
<td><p>Office 365용 테넌트 계정 만들기 및 Lync Online을 사용하도록 설정</p></td>
<td><p><a href="http://go.microsoft.com/fwlink/?linkid=254980%26clcid=0x412">Office 365</a>에서 Office 365 및 Lync Online에 대한 내용을 확인할 수 있습니다.</p>
<p>환경이 Office 365를 사용할 수 있는 상태인지 확인하려면 <a href="http://go.microsoft.com/fwlink/p/?linkid=401408">시스템 요구 사항</a>을 참고하세요.</p>
<p>Office 365를 설정하는 방법에 대한 자세한 내용은 <a href="http://go.microsoft.com/fwlink/?linkid=254982%26clcid=0x412">Office 365 시작</a> 및 <a href="http://go.microsoft.com/fwlink/?linkid=254979%26clcid=0x412">Office 365 설정</a>을 참고하세요.</p></td>
</tr>
<tr class="even">
<td><p></p></td>
<td><p>도메인 추가 및 소유권 확인</p></td>
<td><p>도메인은 <em>베니티 도메인</em> 이라고도 합니다. 도메인을 Office 365 테넌트에 추가한 다음 해당하는 단계에 따라 Office 365에 대한 도메인의 유효성을 검사해야 합니다. 이 과정을 통해 자신이 도메인의 소유자임을 확인합니다.</p>
<p>Office 365 테넌트에 도메인을 추가하려면 <a href="http://go.microsoft.com/fwlink/?linkid=254983%26clcid=0x412">Office 365에 도메인 추가</a>에서 설명하는 단계를 따르세요.</p>
<p>&quot;Office 365 서비스에 대한 DNS 레코드 편집&quot;을 비롯하여 해당 항목의 각 섹션에 나와 있는 모든 단계를 완료합니다.</p></td>
</tr>
<tr class="odd">
<td><p></p></td>
<td><p>환경 준비 상태 확인</p></td>
<td><p>Office 365 설치 도우미를 사용하면 Office 365를 배포하는 데 도움을 얻을 수 있습니다. 자세한 내용은 <a href="http://go.microsoft.com/fwlink/p/?linkid=254985">설치 도우미를 사용하여 Office 365 준비 상태 확인</a>을 참고하세요.</p>
<p>도구를 사용하는 방법과 Office 365를 배포하는 방법에 대한 자세한 내용은 <a href="http://go.microsoft.com/fwlink/p/?linkid=257337">Office 365 배포 가이드</a>를 참고하세요.</p></td>
</tr>
<tr class="even">
<td><p></p></td>
<td><p>Active Directory 동기화 준비</p></td>
<td><p>Active Directory 동기화에서는 온-프레미스 Active Directory를 Office 365와 동기화된 상태로 유지합니다. 따라서 각 사용자 계정과 그룹의 동기화된 버전을 만들 수 있으며 로컬 Microsoft Exchange Server 환경에서 Microsoft Exchange Online으로의 GAL(전체 주소 목록) 동기화를 수행할 수 있습니다.</p>


> [!IMPORTANT]
> 사용자를 Lync Online으로 이동하지 않았더라도 조직의 모든 Lync 사용자에 대해 온-프레미스와 온라인 Lync 배포 간에 AD 계정을 동기화해야 합니다. 모든 사용자를 동기화하지 않으면 온-프레미스와 조직의 온라인 사용자 간에 통신이 예상대로 이루어지지 않을 수 있습니다.



<p>Active Directory 동기화를 위해 환경을 준비하려면 Single Sign-On 설정을 비롯하여 <a href="http://go.microsoft.com/fwlink/p/?linkid=254988">디렉터리 동기화: 로드맵</a>에 설명되어 있는 단계를 따르세요.</p></td>
</tr>
<tr class="odd">
<td><p></p></td>
<td><p>AD FS(Active Directory Federation Services)용 인증서 만들기</p></td>
<td><p>Office 365와의 ID 페더레이션에 사용되는 인증서를 만들어야 합니다. 자세한 내용은 Single Sign-On에 사용할 AD FS 계획 및 배포 항목( <a href="http://go.microsoft.com/fwlink/p/?linkid=285376">검사 목록: AD FS를 사용하여 Single Sign-On 구현 및 관리</a>)의 &quot;페더레이션 서버 인증서&quot; 섹션을 참고하세요.</p></td>
</tr>
<tr class="even">
<td><p></p></td>
<td><p>AD FS에 대해 인증서 할당</p></td>
<td><p>Office 365와의 ID 페더레이션에 사용되는 인증서를 만든 후에는 인증서를 설치 및 할당해야 합니다.</p></td>
</tr>
<tr class="odd">
<td><p></p></td>
<td><p>파일럿 사용자를 비즈니스용 Skype Online으로 이동</p></td>
<td><p>비즈니스용 Skype Online용으로 환경을 준비 및 구성하는 단계를 완료한 후에 파일럿 사용자를 Lync Online으로 이동할 수 있습니다.</p>
<p><a href="lync-server-2013-move-users-to-lync-online.md">Lync Server 2013에서 Lync Online으로 사용자 이동</a>을 참고하세요.</p></td>
</tr>
<tr class="even">
<td><p></p></td>
<td><p>하이브리드 배포에서 사용자 관리</p></td>
<td><p>하이브리드 배포에서 사용자를 관리하는 방법에 대한 자세한 내용은 <a href="lync-server-2013-administering-users-in-a-hybrid-deployment.md">하이브리드 Lync Server 2013 배포에서 사용자 관리</a>를 참고하세요.</p></td>
</tr>
</tbody>
</table>

