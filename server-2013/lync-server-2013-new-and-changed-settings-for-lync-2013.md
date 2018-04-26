---
title: Lync 2013의 새로운 기능과 변경된 기능
TOCTitle: Lync 2013의 새로운 기능과 변경된 기능
ms:assetid: bb13789c-7eda-461c-a387-02ea8ca4dabe
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/JJ205204(v=OCS.15)
ms:contentKeyID: 49304857
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Lync 2013의 새로운 기능과 변경된 기능

 

_**마지막으로 수정된 항목:** 2015-03-09_

이 항목에서는 클라이언트 관리와 직접적으로 관련된, Lync Server 관리 셸 cmdlet에 대한 변경 내용을 설명합니다. Lync Server 2013에는 여러 가지 새로운 매개 변수가 도입된 한편, 다른 수단을 통해 구성할 수 있는 기능에 대한 매개 변수가 제거되었습니다.

## 새로운 클라이언트 관리 매개 변수


<table>
<colgroup>
<col style="width: 33%" />
<col style="width: 33%" />
<col style="width: 33%" />
</colgroup>
<thead>
<tr class="header">
<th>새로운 매개 변수</th>
<th>Lync Server 관리 셸 Cmdlet</th>
<th>설명</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>TracingLevel</p></td>
<td><p>CsClientPolicy</p></td>
<td><p>True로 설정하면 Lync 2010에서 소프트웨어 추적을 사용할 수 있고, False로 설정하면 소프트웨어 추적을 사용할 수 없습니다. 소프트웨어 추적은 API 통화 추적을 비롯하여 프로그램이 수행하는 모든 작업에 대한 자세한 기록을 유지합니다. 이러한 추적은 대체로 개발자와 응용 프로그램 지원 담당자에게 유용합니다. 이 설정은 Communications Server 2007 R2 그룹 정책 설정 &quot;Communicator에서 추적 기능 설정&quot;에 해당합니다. 설정 값은 다음과 같습니다.</p>
<ul>
<li><p>Off = 추적을 사용할 수 없고 사용자가 이 설정을 변경할 수 없습니다.</p></li>
<li><p>Light = 최소한의 추적이 수행되고 사용자가 이 설정을 변경할 수 없습니다.</p></li>
<li><p>On = 자세한 추적이 수행되고 사용자가 이 설정을 변경할 수 없습니다.</p></li>
</ul>
<p>기본적으로 TracingLevel은 null 값으로 설정됩니다. 즉, 최소한의 추적이 수행되지만 사용자가 이 최소한의 추적을 사용하거나 사용하지 않도록 설정할 수 없습니다.</p></td>
</tr>
<tr class="even">
<td><p>EnableMediaRedirection</p></td>
<td><p>CsClientPolicy</p></td>
<td><p>True($True)로 설정하면 오디오 및 비디오 스트림을 다른 네트워크 트래픽과 분리할 수 있습니다. 따라서 클라이언트 장치에서 로컬로 오디오 및 비디오의 인코딩과 디코딩을 수행할 수 있습니다. 일반적으로 미디어 리디렉션은 장치 원격 사용 또는 코덱 압축과 같은 유사한 방법에 비해 대역폭 사용 감소, 서버 확장성 향상, 사용자 환경 최적화 측면에서 더욱 효과적입니다.</p></td>
</tr>
<tr class="odd">
<td><p>AllowLargeMeetings</p></td>
<td><p>CsConferencing</p></td>
<td><p>True로 설정하면 모든 Lync 모임이 &quot;대규모 모임&quot;으로 간주됩니다. 대규모 모임에서는 참가자에게 전송되는 알림 수와 기본적으로 전송되는 모임 명단 크기에 제한이 적용됩니다.</p></td>
</tr>
<tr class="even">
<td><p>DisablePowerPointAnnotations</p></td>
<td><p>CsConferencing</p></td>
<td><p>True($True)로 설정하면 사용자가 전화 회의에 사용되는 PowerPoint 슬라이드에 주석을 추가할 수 없습니다. 그러나 AllowAnnotations 속성의 값에 따라 사용자가 다른 화이트보드 기능에 여전히 액세스할 수 있습니다. 기본값은 False입니다. 즉, PowerPoint 주석을 사용할 수 있습니다.</p></td>
</tr>
<tr class="odd">
<td><p>AllowSharedNotes</p></td>
<td><p>CsConferencing</p></td>
<td><p>True(기본값)로 설정하면 전화 회의에 연결된 열려 있는 모든 OneNote 전자 필기장이 전화 회의 참가자 및 전화 회의 중 공유되는 콘텐츠 정보와 같은 정보를 포함하여 자동으로 업데이트됩니다.</p></td>
</tr>
<tr class="even">
<td><p>EnableInviteCustomization</p></td>
<td><p>CsMeetingConfiguration</p></td>
<td><p>다른 새 CsMeetingConfiguration 매개 변수와 함께 Lync 2013용 온라인 모임 추가 기능에서 생성되는 모임 초대를 사용자 지정하는 데 사용됩니다.</p></td>
</tr>
<tr class="odd">
<td><p>LogoURL</p></td>
<td><p>CsMeetingConfiguration</p></td>
<td><p>Lync 2013용 온라인 모임 추가 기능에서 생성되는 모든 모임에 조직의 로고를 추가합니다. GIF 또는 JPG 이미지의 URL을 지정하면 됩니다.</p></td>
</tr>
<tr class="even">
<td><p>HelpURL</p></td>
<td><p>CsMeetingConfiguration</p></td>
<td><p>Lync 2013용 온라인 모임 추가 기능에서 생성되는 모든 초대에 조직의 도움말 또는 지원 URL을 추가합니다.</p></td>
</tr>
<tr class="odd">
<td><p>LegalURL</p></td>
<td><p>CsMeetingConfiguration</p></td>
<td><p>Lync 2013용 온라인 모임 추가 기능에서 생성되는 모든 초대에 법적 고지 사항 텍스트를 추가합니다. 텍스트 위치의 URL을 지정하면 됩니다.</p></td>
</tr>
<tr class="even">
<td><p>CustomFooterText</p></td>
<td><p>CsMeetingConfiguration</p></td>
<td><p>Lync 2013용 온라인 모임 추가 기능에서 생성되는 모든 초대에 사용자 지정 바닥글을 추가합니다. 사용자 지정 바닥글 텍스트 위치의 URL을 지정하면 됩니다.</p></td>
</tr>
<tr class="odd">
<td><p>IsPublicDisclosureAllowed</p></td>
<td><p>CsWebServiceConfiguration</p></td>
<td><p>새로운 2013 버전의 Lync Web App을 사용하도록 설정합니다. 새로운 버전의 Lync Web App은 기본적으로 사용하지 않도록 설정되어 있으며 관리자가 사용하도록 설정해야 합니다.</p></td>
</tr>
</tbody>
</table>


## 더 이상 사용되지 않는 클라이언트 관리 매개 변수


<table>
<colgroup>
<col style="width: 33%" />
<col style="width: 33%" />
<col style="width: 33%" />
</colgroup>
<thead>
<tr class="header">
<th>매개 변수</th>
<th>Lync Server 관리 셸 cmdlet</th>
<th>설명</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>EnableSQMData</p></td>
<td><p>CsClientPolicy</p></td>
<td><p>Set-CSClientPolicy cmdlet의 EnableSQMData 매개 변수는 Lync Server 2013에서 제거되었습니다. 대신 SQM(Software Quality Management) 데이터에 대한 공유 그룹 정책 설정을 사용하여 Lync 클라이언트 일반 옵션 페이지에 있는 사용자 환경 개선 옵션의 사용자 인터페이스를 확인할 수 있습니다.</p>
<p>HKEY_CURRENT_USER\Software\Policies\Microsoft\Office\Common\QMEnable</p>
<p>값은 다음과 같습니다.</p>
<p>1 = 확인란을 선택하고 표시합니다(사용자가 확인란을 선택 취소할 수 있음)</p>
<p>0 = 확인란을 선택 취소하고 비활성화합니다(사용자가 이를 무시할 수 없음)</p>
<p>Null = 값이 Office 설치 프로그램에서 결정되며 사용자가 원할 경우 선택할 수 있도록 확인란이 표시됩니다.</p></td>
</tr>
<tr class="even">
<td><p>AllowExchangeContactStore</p></td>
<td><p>CsClientPolicy</p></td>
<td><p>이 매개 변수는 제거되었습니다. 대신 Lync Server 2013을 배포하고 토폴로지를 게시할 때 기본적으로 모든 사용자가 통합 연락처 저장소를 사용할 수 있도록 설정됩니다. 이를 통해 Exchange에 유지되는 사용자의 모든 대화 상대를 Lync, Outlook 및 Outlook Web Access에서 사용할 수 있습니다. Set-CsUserServicesPolicy cmdlet을 통해 통합 연락처 저장소를 사용할 수 있는 사용자를 사용자 지정할 수 있습니다. 전역적으로, 사이트별로, 테넌트별로 또는 개인 및 개인 그룹별로 사용자가 통합 연락처 저장소를 사용할 수 있도록 설정할 수 있습니다. 자세한 내용은 <a href="lync-server-2013-enable-users-for-unified-contact-store.md">Lync Server 2013에서 통합 연락처 저장소에 사용자 사용</a>을 참조하십시오.</p></td>
</tr>
<tr class="odd">
<td><p>MAPIPollInterval</p></td>
<td><p>CsClientPolicy</p></td>
<td><p>이 매개 변수는 Lync 2013에서 사용되지 않습니다. 이전 릴리즈에서 이 매개 변수는 클라이언트가 Exchange 공용 폴더에서 MAPI 데이터를 검색한 빈도를 지정했습니다.</p></td>
</tr>
</tbody>
</table>

