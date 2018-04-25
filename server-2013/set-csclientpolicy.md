---
title: Set-CsClientPolicy
TOCTitle: Set-CsClientPolicy
ms:assetid: 4b7eac0c-50e9-443a-b474-5c4e0c286028
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg398300(v=OCS.15)
ms:contentKeyID: 49303556
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Set-CsClientPolicy

 

_**마지막으로 수정된 항목:** 2015-05-01_

기존 클라이언트 정책의 속성 값을 수정합니다. 특히 클라이언트 정책은 사용자가 사용할 수 있는 Lync Server 기능을 결정하는 데 도움이 됩니다. 예를 들어 일부 사용자에게는 파일 전송 권한을 부여하고 다른 사용자에 대해서는 이 권한을 거부할 수 있습니다. 이 cmdlet은 Lync Server 2010에서 도입되었습니다.

## 구문

    Set-CsClientPolicy [-Identity <XdsIdentity>] <COMMON PARAMETERS>

    Set-CsClientPolicy [-Instance <PSObject>] <COMMON PARAMETERS>

    COMMON PARAMETERS: [-AddressBookAvailability <WebSearchAndFileDownload | WebSearchOnly | FileDownloadOnly>] [-AttendantSafeTransfer <$true | $false>] [-AutoDiscoveryRetryInterval <TimeSpan>] [-BlockConversationFromFederatedContacts <$true | $false>] [-CalendarStatePublicationInterval <UInt32>] [-ConferenceIMIdleTimeout <TimeSpan>] [-Confirm [<SwitchParameter>]] [-CustomizedHelpUrl <String>] [-CustomLinkInErrorMessages <String>] [-CustomStateUrl <String>] [-Description <String>] [-DGRefreshInterval <TimeSpan>] [-DisableCalendarPresence <$true | $false>] [-DisableContactCardOrganizationTab <$true | $false>] [-DisableEmailComparisonCheck <$true | $false>] [-DisableEmoticons <$true | $false>] [-DisableFederatedPromptDisplayName <$true | $false>] [-DisableFeedsTab <$true | $false>] [-DisableFreeBusyInfo <$true | $false>] [-DisableHandsetOnLockedMachine <$true | $false>] [-DisableHtmlIm <$true | $false>] [-DisableInkIM <$true | $false>] [-DisableMeetingSubjectAndLocation <$true | $false>] [-DisableOneNote12Integration <$true | $false>] [-DisableOnlineContextualSearch <$true | $false>] [-DisablePhonePresence <$true | $false>] [-DisablePICPromptDisplayName <$true | $false>] [-DisablePoorDeviceWarnings <$true | $false>] [-DisablePoorNetworkWarnings <$true | $false>] [-DisablePresenceNote <$true | $false>] [-DisableRTFIM <$true | $false>] [-DisableSavingIM <$true | $false>] [-DisplayPhoto <NoPhoto | PhotosFromADOnly | AllPhotos>] [-EnableAppearOffline <$true | $false>] [-EnableCallLogAutoArchiving <$true | $false>] [-EnableClientMusicOnHold <$true | $false>] [-EnableConversationWindowTabs <$true | $false>] [-EnableEnterpriseCustomizedHelp <$true | $false>] [-EnableEventLogging <$true | $false>] [-EnableExchangeContactSync <$true | $false>] [-EnableExchangeDelegateSync <$true | $false>] [-EnableFullScreenVideo <$true | $false>] [-EnableHighPerformanceConferencingAppSharing <$true | $false>] [-EnableHighPerformanceP2PAppSharing <$true | $false>] [-EnableHotdesking <$true | $false>] [-EnableIMAutoArchiving <$true | $false>] [-EnableMediaRedirection <$true | $false>] [-EnableNotificationForNewSubscribers <$true | $false>] [-EnableSQMData <$true | $false>] [-EnableTracing <$true | $false>] [-EnableUnencryptedFileTransfer <$true | $false>] [-EnableURL <$true | $false>] [-EnableVOIPCallDefault <$true | $false>] [-ExcludedContactFolders <String>] [-Force <SwitchParameter>] [-HelpEnvironment <String>] [-HotdeskingTimeout <TimeSpan>] [-IMWarning <String>] [-MAPIPollInterval <TimeSpan>] [-MaximumDGsAllowedInContactList <UInt32>] [-MaximumNumberOfContacts <UInt16>] [-MaxPhotoSizeKB <UInt32>] [-MusicOnHoldAudioFile <String>] [-P2PAppSharingEncryption <Supported | Enforced | NotSupported>] [-PlayAbbreviatedDialTone <$true | $false>] [-PolicyEntry <PSListModifier>] [-SearchPrefixFlags <UInt16>] [-ShowManagePrivacyRelationships <$true | $false>] [-ShowRecentContacts <$true | $false>] [-ShowSharepointPhotoEditLink <$true | $false>] [-SPSearchCenterExternalURL <String>] [-SPSearchCenterInternalURL <String>] [-SPSearchExternalURL <String>] [-SPSearchInternalURL <String>] [-TabURL <String>] [-TracingLevel <Off | Light | Full>] [-WebServicePollInterval <TimeSpan>] [-WhatIf [<SwitchParameter>]]

## 예제

## 예제 1

예제 1에 표시된 명령은 클라이언트 정책 RedmondClientPolicy를 수정합니다. 이 예제에서는 WebServicePollInterval 속성을 15분(00시간: 15분: 00초)으로 설정합니다.

    Set-CsClientPolicy -Identity RedmondClientPolicy -WebServicePollInterval "00:15:00"

## 예제 2

예제 2에서는 클라이언트 정책 RedmondClientPolicy의 세 가지 속성 값이 수정됩니다. DisableEmoticons, DisableHtmlIm 및 DisableRTFIm 속성이 모두 True로 설정됩니다.

    Set-CsClientPolicy -Identity RedmondClientPolicy -DisableEmoticons $True -DisableHtmlIm $True -DisableRTFIm $True

## 예제 3

예제 3에서도 DisableEmoticons, DisableHtmlIm 및 DisableRTFIm 속성을 수정합니다. 그러나 이 예제에서는 사이트 범위에서 구성된 모든 클라이언트 정책이 수정됩니다. 이 작업을 수행하기 위해 먼저 **Get-CsClientPolicy** cmdlet 및 Filter 속성을 사용하여 ID가 "site:" 문자로 시작하는 모든 클라이언트 정책을 반환합니다. 이러한 정책은 사이트 범위에서 구성된 정책입니다. 필터링된 컬렉션은 컬렉션의 각 정책을 가져와 DisableEmoticons, DisableHtmlIm 및 DisableRTFIm 값을 수정하는 **Set-CsClientPolicy** cmdlet에 파이프됩니다.

    Get-CsClientPolicy -Filter "*site:*" | Set-CsClientPolicy -DisableEmoticons $True -DisableHtmlIm $True -DisableRTFIm $True

## 예제 4

예제 4에서는 10KB보다 큰 사진을 허용하는 모든 클라이언트 정책이 수정됩니다. 수정된 후 이러한 정책의 최대 사진 크기는 10KB입니다. 이 작업을 수행하기 위해 먼저 매개 변수 없이 **Get-CsClientPolicy** cmdlet을 호출하여 조직에서 사용하도록 구성된 모든 클라이언트 정책 컬렉션을 반환합니다. 이 컬렉션은 MaxPhotoSizeKb 속성이 10KB보다 큰(-gt) 정책만 선택하는 **Where-Object** cmdlet에 파이프됩니다. 그런 다음 필터링된 컬렉션은 컬렉션에 있는 각 정책의 MaxPhotoSize 속성 값을 10KB로 설정하는 **Set-CsClientPolicy** cmdlet에 파이프됩니다.

    Get-CsClientPolicy | Where-Object {$_.MaxPhotoSizeKb -gt 10} | Set-CsClientPolicy -MaxPhotoSizeKb 10

## 자세한 정보

Lync Server에서는 이전 버전의 제품에서 사용된 그룹 정책 설정 대신 클라이언트 정책을 사용합니다. Microsoft Office Communicator 2007 및 Microsoft Office Communicator 2007 R2에서는 Communicator 및 기타 클라이언트로 사용자가 수행할 수 있는 작업을 결정할 때 그룹 정책을 사용했습니다. 예를 들어 사용자가 메신저 대화 세션의 대화 내용을 저장할 수 있는지 여부, Microsoft Outlook의 정보를 상태 정보로 통합할지 여부, 사용자가 메신저 대화에 이모티콘이나 서식 있는 텍스트를 포함할 수 있는지 여부 등을 결정하는 그룹 정책 설정이 있었습니다.

그룹 정책은 유용하지만 Lync Server에 적용할 때 몇 가지 기술적인 제한이 있습니다. 우선, 그룹 정책은 도메인별 또는 OU(조직 구성 단위)별로 적용하도록 설계되었기 때문에 보다 선별적인 사용자 그룹(예: 특정 부서에서 근무하는 모든 사용자나 특정 직책의 모든 사용자)에 적용하기 어렵습니다. 또한 그룹 정책은 도메인에 로그온하거나 컴퓨터를 사용하여 로그온한 사용자에게만 적용됩니다. 인터넷을 통해 Lync Server에 액세스하거나 휴대폰을 사용하여 시스템에 액세스한 사용자에게는 적용되지 않습니다. 따라서 로그온하는 데 사용한 장치 및 로그온한 위치에 따라 동일한 사용자에게 다른 환경이 제공될 수 있습니다.

이러한 비일관성을 해결하기 위해 Lync Server에서는 그룹 정책 대신 클라이언트 정책을 사용합니다. 클라이언트 정책은 로그온한 위치 및 로그온하는 데 사용한 장치 유형에 관계없이 사용자가 시스템에 액세스할 때마다 적용됩니다. 또한 다른 Lync Server 정책과 마찬가지로 클라이언트 정책을 언제든지 선택한 사용자 그룹으로 지정할 수 있을 뿐만 아니라 단일 사용자에게 할당되는 사용자 지정 정책을 만들 수도 있습니다.

클라이언트 정책은 전역, 사이트 및 사용자별 범위에서 구성할 수 있습니다. **Set-CsClientPolicy** cmdlet을 사용하면 조직에서 사용하도록 구성된 클라이언트 정책의 전부 또는 일부를 수정할 수 있습니다.

클라이언트 정책은 대부분의 정책 설정이 기본값으로 지정되지 않은 다른 여러 정책과 다르다는 점에 유의하세요.

이 cmdlet을 실행할 수 있는 사용자: 기본적으로 RTCUniversalServerAdmins 그룹의 구성원은 **Set-CsClientPolicy** cmdlet을 로컬로 실행할 수 있습니다. 사용자가 직접 만든 사용자 지정 RBAC(역할 기반 액세스 제어) 역할을 포함하여 이 cmdlet이 할당된 모든 RBAC 역할의 목록을 반환하려면 Windows PowerShell 프롬프트에서 다음 명령을 실행합니다.

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Set-CsClientPolicy"}

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
<td><p><em>AddressBookAvailability</em></p></td>
<td><p>선택</p></td>
<td><p>Microsoft.Rtc.Management.WritableConfig.Policy.Client.AddressBookAvailability</p></td>
<td><p>사용자가 주소록 서버의 정보에 액세스하도록 허용된 방법( 주소록 웹 쿼리 서비스 사용 및/또는 로컬 컴퓨터에 주소록 복사본 다운로드)을 나타냅니다. AddressBookAvailability는 다음 값 중 하나로 설정되어야 합니다.</p>
<p>WebSearchAndFileDownload</p>
<p>WebSearchOnly</p>
<p>FileDownloadOnly</p></td>
</tr>
<tr class="even">
<td><p><em>AttendantSafeTransfer</em></p></td>
<td><p>선택</p></td>
<td><p>System.Boolean</p></td>
<td><p>True로 설정하면 Lync 전화 교환이 &quot;안전한 전송&quot; 모드로 작동하므로 원하는 수신자에게 도달하지 못한 전송 통화가 &quot;전송 실패&quot; 알림과 함께 수신 영역에 다시 표시됩니다. False로 설정하면 원하는 수신자에 도달하지 못한 전송 통화가 수신 영역에 다시 표시되지 않습니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>AutoDiscoveryRetryInterval</em></p></td>
<td><p>선택</p></td>
<td><p>System.TimeSpan</p></td>
<td><p>연결 시도에 실패한 후 Lync Server 연결을 다시 시도하기 전에 Lync에서 대기하는 시간을 지정합니다. AutoDiscoveryRetryInterval은 1초에서 60분(1시간)(포함) 사이의 값으로 설정할 수 있습니다.</p>
<p>AutoDiscoveryRetryInterval을 지정할 때는 시:분:초 형식을 사용해야 합니다. 예를 들어 간격을 25분으로 설정하려면 다음 구문을 사용합니다.</p>
<p>- AutoDiscoveryRetryInterval 00:25:00</p>
<p>이 설정은 Office Communications Server 2007 R2 그룹 정책 설정 &quot;자동 검색을 다시 시도할 시간 간격&quot;에 해당합니다.</p></td>
</tr>
<tr class="even">
<td><p><em>BlockConversationFromFederatedContacts</em></p></td>
<td><p>선택</p></td>
<td><p>System.Boolean</p></td>
<td><p>True로 설정하면 조직 외부의 대화 상대가 이 정책이 적용되는 사용자와 메신저 대화를 시작할 수 없습니다. 그러나 내부 사용자가 시작한 대화에 외부 사용자가 참여할 수는 있습니다. False로 설정하면 외부 대화 상대가 조직의 사용자에게 원치 않는 메신저 대화를 보내도록 허용됩니다.</p>
<p>이 설정은 Office Communications Server 2007 R2 그룹 정책 설정 &quot;페더레이션 대화 상대의 대화 차단&quot;에 해당합니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>CalendarStatePublicationInterval</em></p></td>
<td><p>선택</p></td>
<td><p>System.UInt32</p></td>
<td><p>Lync가 Microsoft Outlook에서 일정 정보를 검색하여 이 데이터를 현재 상태 정보에 추가하기 전에 대기하는 시간(초)을 지정합니다.</p>
<p>예를 들어 CalendarStatePublicationInterval을 10분(600초)으로 설정하려면 다음 구문을 사용합니다.</p>
<p>- CalendarStatePublicationInterval 600</p>
<p>이 설정은 Office Communications Server 2007 R2 그룹 정책 설정 &quot;현재 상태에 일정 데이터를 게시할 시간 간격&quot;에 해당합니다.</p></td>
</tr>
<tr class="even">
<td><p><em>ConferenceIMIdleTimeout</em></p></td>
<td><p>선택</p></td>
<td><p>System.TimeSpan</p></td>
<td><p>사용자가 메신저 대화를 보내거나 받지 않고 메신저 대화 세션에 남아 있을 수 있는 시간(분)을 나타냅니다.</p>
<p>ConferenceIMIdleTimeout은 1시간 이하여야 하며 시:분:초 형식을 사용하여 지정해야 합니다. 예를 들어 다음 구문은 시간 제한 값을 45분으로 설정합니다.</p>
<p>-ConferenceIMIdleTimeout 00:45:00</p></td>
</tr>
<tr class="odd">
<td><p><em>Confirm</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>명령을 실행하기 전에 확인 메시지를 표시합니다.</p></td>
</tr>
<tr class="even">
<td><p><em>CustomizedHelpUrl</em></p></td>
<td><p>선택</p></td>
<td><p>System.String</p></td>
<td><p>조직에서 설정한 사용자 지정 Lync 도움말의 URL입니다. 사용자가 Lync에서 도움말 메뉴를 클릭할 때마다 기본 제품 도움말 대신 이 도움말이 표시됩니다. 이 매개 변수는 Lync Server 2013에서는 더 이상 사용되지 않습니다.</p>
<p>EnableEnterpriseCustomizedHelp를 True로 설정하지 않은 경우에도 사용자 지정 도움말을 사용할 수 없습니다.</p>
<p>이 설정은 Office Communications Server 2007 R2 그룹 정책 설정 &quot;도움말 메뉴&quot;에 해당합니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>CustomLinkInErrorMessages</em></p></td>
<td><p>선택</p></td>
<td><p>System.String</p></td>
<td><p>Lync에 표시되는 오류 메시지에 추가할 수 있는 웹 사이트의 URL입니다. URL을 지정하면 Lync에서 발생하는 오류 메시지의 맨 아래에 해당 URL이 표시됩니다. 사용자가 이 링크를 클릭하면 추가 정보, 문제 해결 팁 등이 포함된 사용자 지정 웹 사이트로 이동합니다.</p></td>
</tr>
<tr class="even">
<td><p><em>CustomStateUrl</em></p></td>
<td><p>선택</p></td>
<td><p>System.String</p></td>
<td><p>Lync에 사용자 지정 현재 상태를 추가하는 데 사용되는 XML 파일의 위치를 지정합니다. Lync는 대화 가능, 다른 용무 중, 방해 금지 등의 기본 제공 상태 외에 최대 4개의 사용자 지정 현재 상태를 허용합니다. XML 파일의 위치는 HTTPS 프로토콜을 사용하여 지정해야 합니다.</p>
<p>이 설정은 Office Communications Server 2007 R2 그룹 정책 설정 &quot;사용자 지정 현재 상태 URL&quot;에 해당합니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>Description</em></p></td>
<td><p>선택</p></td>
<td><p>System.String</p></td>
<td><p>관리자가 정책에 대한 추가 정보를 제공할 수 있습니다. 예를 들어 Description은 정책을 할당해야 하는 대상 사용자를 나타낼 수도 있습니다.</p></td>
</tr>
<tr class="even">
<td><p><em>DGRefreshInterval</em></p></td>
<td><p>선택</p></td>
<td><p>System.TimeSpan</p></td>
<td><p>Lync가 대화 상대 목록에서 &quot;확장된&quot; 메일 그룹의 구성원 목록을 자동으로 새로 고치기 전에 대기하는 시간을 나타냅니다. 메일 그룹을 확장하면 해당 그룹의 모든 구성원이 표시됩니다. DGRefreshInterval은 30초에서 28,800초(8시간)(포함) 사이의 정수 값으로 설정할 수 있습니다. 기본값은 28,800초입니다.</p>
<p>이 설정은 Office Communications Server 2007 R2 그룹 정책 설정 &quot;각 메일 그룹의 구성원 자격을 새로 고칠 시간 간격&quot;에 해당합니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>DisableCalendarPresence</em></p></td>
<td><p>선택</p></td>
<td><p>System.Boolean</p></td>
<td><p>True로 설정하면 Microsoft Outlook에서 가져온 연락처 데이터가 현재 상태 정보에 포함되지 않습니다. False로 설정하면 일정 데이터가 현재 상태 정보에 포함됩니다. 예를 들어 약속 있음/없음 정보가 대화 상대 카드에 보고되고, 마찬가지로 Outlook에서 사용자가 모임에 참가 중임을 표시할 때마다 사용자의 상태가 다른 용무 중으로 자동으로 설정됩니다.</p>
<p>이 설정은 Office Communications Server 2007 R2 그룹 정책 설정 &quot;일정 현재 상태 사용 안 함&quot;에 해당합니다.</p></td>
</tr>
<tr class="even">
<td><p><em>DisableContactCardOrganizationTab</em></p></td>
<td><p>선택</p></td>
<td><p>System.Boolean</p></td>
<td><p>True로 설정하면 대화 상대 카드 조직 탭이 Lync 사용자 인터페이스에 표시되지 않습니다. False로 설정하면 Lync에서 대화 상대 카드 조직 탭을 사용할 수 있습니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>DisableEmailComparisonCheck</em></p></td>
<td><p>선택</p></td>
<td><p>System.Boolean</p></td>
<td><p>True로 설정하면 Lync에서 현재 실행 중인 Microsoft Outlook 인스턴스가 Lync를 실행하는 같은 사용자에게 속해 있는지 확인하지 않습니다. 예를 들어 Outlook과 Lync가 둘 다 Ken Myer 사용자 계정으로 실행되고 있는지 확인하지 않습니다. 대신, 두 응용 프로그램이 동일한 계정으로 실행 중인 것으로 간주하여 Outlook의 연락처 및 일정 데이터를 Lync에 포함합니다.</p>
<p>False로 설정하면 Lync에서 SMTP 주소를 사용하여 Outlook과 Lync가 동일한 계정으로 실행되고 있는지 확인합니다. SMTP 주소가 일치하지 않으면 Outlook의 연락처 및 일정 데이터가 Lync에 통합되지 않습니다.</p>
<p></p></td>
</tr>
<tr class="even">
<td><p><em>DisableEmoticons</em></p></td>
<td><p>선택</p></td>
<td><p>System.Boolean</p></td>
<td><p>True로 설정하면 사용자가 메신저 대화를 통해 이모티콘을 보내거나 받을 수 없습니다. 대신, 이러한 이모티콘에 해당하는 텍스트가 표시됩니다. 예를 들어 &quot;스마일 기호&quot; 그림 대신 이 그림에 해당하는 다음 텍스트가 표시됩니다.</p>
<p>: )</p>
<p>False로 설정하면 사용자가 메신저 대화에 이모티콘을 포함하거나, 받은 메신저 대화에 있는 이모티콘을 볼 수 있습니다.</p>
<p>이 설정은 Office Communications Server 2007 R2 그룹 정책 설정 &quot;대화창에 이모티콘 사용 안 함&quot;에 해당합니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>DisableFederatedPromptDisplayName</em></p></td>
<td><p>선택</p></td>
<td><p>System.Boolean</p></td>
<td><p>True로 설정하면 페더레이션 사용자의 대화 상대 목록에 추가될 때 생성되는 알림 대화 상자에 페더레이션 사용자의 SIP 주소(예: sip:kenmyer@fabrikam.com)가 사용됩니다. False로 설정하면 알림 대화 상자에 페더레이션 사용자의 표시 이름(예: Ken Myer)이 사용됩니다.</p>
<p>이 설정은 Office Communications Server 2007 R2 그룹 정책 설정 &quot;알림 대화 상자에 PIC 대화 상대가 아닌 페더레이션 대화 상대의 대화명 표시 안 함&quot;에 해당합니다.</p></td>
</tr>
<tr class="even">
<td><p><em>DisableFeedsTab</em></p></td>
<td><p>선택</p></td>
<td><p>System.Boolean</p></td>
<td><p>True로 설정하면 작업 피드 탭이 Lync에 표시되지 않습니다. False로 설정하면 Lync 내에서 피드 탭을 사용할 수 있습니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>DisableFreeBusyInfo</em></p></td>
<td><p>선택</p></td>
<td><p>System.Boolean</p></td>
<td><p>True로 설정하면 Microsoft Outlook에서 검색된 약속 있음/없음 정보가 대화 상대 카드에 표시되지 않습니다. False로 설정하면 약속 있음/없음 정보가 대화 상대 카드에 표시됩니다. 예를 들어 대화 상대 카드에 다음과 유사한 메모가 포함될 수 있습니다.</p>
<p>일정: 오후 2:00까지 약속 없음</p>
<p>이 설정은 Office Communications Server 2007 R2 그룹 정책 설정 &quot;약속 있음/없음 정보 게시 안 함&quot;에 해당합니다.</p></td>
</tr>
<tr class="even">
<td><p><em>DisableHandsetOnLockedMachine</em></p></td>
<td><p>선택</p></td>
<td><p>System.Boolean</p></td>
<td><p>True로 설정하면 Polycom 송수화기가 연결된 컴퓨터가 잠긴 경우 사용자가 해당 송수화기를 사용할 수 없게 됩니다. 송수화기를 사용하려면 먼저 컴퓨터 잠금을 해제해야 합니다.</p>
<p>False로 설정하면 송수화기가 연결된 컴퓨터가 잠긴 경우에도 사용자가 해당 송수화기를 사용할 수 있습니다.</p>
<p>이 설정은 Office Communications Server 2007 R2 그룹 정책 설정 &quot;잠긴 컴퓨터에 송수화기 사용 구성&quot;에 해당합니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>DisableHtmlIm</em></p></td>
<td><p>선택</p></td>
<td><p>System.Boolean</p></td>
<td><p>True로 설정하면 웹 페이지에서 복사한 HTML 텍스트를 메신저 대화에 붙여 넣을 때 HTML 텍스트가 일반 텍스트로 변환됩니다. False로 설정하면 메신저 대화에 붙여 넣을 때 글꼴 크기 및 색, 드롭다운 목록 및 단추 등의 HTML 서식이 유지됩니다.</p>
<p>False로 설정한 경우에도 스크립트 및 기타 악의적으로 사용될 수 있는 항목(예: 소리를 재생하는 태그)은 메신저 대화에 복사되지 않습니다. 단추 및 기타 컨트롤을 복사하여 메시지에 붙여 넣을 수 있지만 이러한 컨트롤에 연결된 스크립트는 자동으로 제거됩니다.</p>
<p>이 설정은 Office Communications Server 2007 R2 그룹 정책 설정 &quot;메신저 대화에 HTML 텍스트 사용 안 함&quot;에 해당합니다.</p></td>
</tr>
<tr class="even">
<td><p><em>DisableInkIM</em></p></td>
<td><p>선택</p></td>
<td><p>System.Boolean</p></td>
<td><p>True로 설정하면 사용자가 Tablet PC 링크가 포함된 메신저 대화를 받을 수 없습니다. 잉크는 손으로 쓴 메모를 문서에 삽입할 수 있는 기술입니다. False로 설정하면 사용자가 Tablet PC 링크가 포함된 메시지를 받을 수 있습니다.</p>
<p>이 설정은 Office Communications Server 2007 R2 그룹 정책 설정 &quot;메신저 대화에 잉크 사용 금지&quot;에 해당합니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>DisableMeetingSubjectAndLocation</em></p></td>
<td><p>선택</p></td>
<td><p>System.Boolean</p></td>
<td><p>False로 설정하면 대화 상대 카드에서 약속 있음/없음 정보를 볼 때 모임 제목, 모임 위치 등 모임에 대한 자세한 정보가 도구 설명으로 표시됩니다. True로 설정하면 자세한 정보가 표시되지 않습니다. 모임 관련 정보가 완전히 표시되지 않도록 하려면 DisableCalendarPresence도 True로 설정해야 합니다.</p>
<p>이 설정은 Communications Server 2007 R2 그룹 정책 설정 &quot;모임 제목 및 위치 정보 게시 안 함&quot;에 해당합니다.</p></td>
</tr>
<tr class="even">
<td><p><em>DisableOneNote12Integration</em></p></td>
<td><p>선택</p></td>
<td><p>System.Boolean</p></td>
<td><p>True로 설정하면 Lync 내에서 Microsoft OneNote를 시작하는 기능 및 메신저 대화 세션과 OneNote 노트를 자동으로 연결하는 기능을 사용할 수 없습니다. False로 설정하면 Lync에서 OneNote를 사용하여 메모 작성 옵션이 활성화됩니다. 또한 Microsoft Outlook의 대화 내용에서 메신저 대화 내용을 찾은 경우 대화 메모 편집 단추를 클릭하여 해당 대화에 연결된 OneNote 노트를 검색할 수 있습니다.</p>
<p>이 설정은 Office Communications Server 2007 R2 그룹 정책 설정 &quot;OneNote 12 통합 사용 안 함&quot;에 해당합니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>DisableOnlineContextualSearch</em></p></td>
<td><p>선택</p></td>
<td><p>System.Boolean</p></td>
<td><p>True로 설정하면 대화 상대 목록에서 사용자를 마우스 오른쪽 단추로 클릭할 때 표시되는 이전 대화 찾기 메뉴 옵션이 비활성화됩니다. 이 옵션을 사용하면 Microsoft Outlook 대화 내용 폴더에서 해당 사용자와 관련된 이전 메신저 대화 세션을 검색할 수 있습니다. False로 설정하면 대화 상대 목록에서 사용자를 마우스 오른쪽 단추로 클릭할 때 이전 대화 찾기 옵션을 사용할 수 있습니다.</p>
<p>이 설정은 Microsoft Outlook을 캐시 모드에서 실행 중이지 않은 사용자에게만 적용됩니다. 이러한 사용자의 검색은 Exchange 서버에서 실행되어야 하는데 관리자는 이러한 검색으로 인해 네트워크 트래픽이 발생하는 것을 원하지 않을 수 있기 때문입니다. 캐시 모드에서 Outlook을 실행하는 경우에는 로컬에 캐시된 사용자의 받은 편지함 복사본에서 검색이 실행됩니다. 캐시된 검색은 이 설정의 영향을 받지 않습니다.</p>
<p>이 설정은 Office Communications Server 2007 R2 그룹 정책 설정 &quot;온라인 문맥 검색 사용 안 함&quot;에 해당합니다.</p></td>
</tr>
<tr class="even">
<td><p><em>DisablePhonePresence</em></p></td>
<td><p>선택</p></td>
<td><p>System.Boolean</p></td>
<td><p>True로 설정하면 Lync에서 현재 상태를 확인할 때 전화 통화를 고려하지 않습니다. False로 설정하면 상태를 확인할 때 전화 통화가 고려됩니다. 예를 들어 전화를 사용할 때마다 상태가 자동으로 다른 용무 중으로 설정됩니다.</p>
<p>이 설정은 Office Communications Server 2007 R2 그룹 정책 설정 &quot;통화 현재 상태 사용 안 함&quot;에 해당합니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>DisablePICPromptDisplayName</em></p></td>
<td><p>선택</p></td>
<td><p>System.Boolean</p></td>
<td><p>True로 설정하면 사용자가 MSN과 같은 공용 메시지 서비스 계정을 가진 사용자의 대화 상대 목록에 추가될 때 생성되는 알림 대화 상자에 해당 사용자의 SIP 주소(예: sip:kenmyer@litwareinc.com)가 표시됩니다. False로 설정하면 알림 대화 상자에 해당 사용자의 표시 이름(예: Ken Myer)이 사용됩니다.</p>
<p>이 설정은 Communications Server 2007 R2 그룹 정책 설정 &quot;알림 대화 상자에 PIC 대화 상대의 대화명 표시 안 함&quot;에 해당합니다.</p></td>
</tr>
<tr class="even">
<td><p><em>DisablePoorDeviceWarnings</em></p></td>
<td><p>선택</p></td>
<td><p>System.Boolean</p></td>
<td><p>True로 설정하면 오디오 또는 비디오 장치가 제대로 작동하지 않을 때 Lync에서 시작 시, 조정 마법사, 대화 창 등에서 경고를 실행하지 않습니다. False로 설정하면 이러한 경고가 실행됩니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>DisablePoorNetworkWarnings</em></p></td>
<td><p>선택</p></td>
<td><p>System.Boolean</p></td>
<td><p>True로 설정하면 네트워크 품질 저하에 대한 Lync가 표시되지 않습니다.</p></td>
</tr>
<tr class="even">
<td><p><em>DisablePresenceNote</em></p></td>
<td><p>선택</p></td>
<td><p>System.Boolean</p></td>
<td><p>True로 설정하면 Microsoft Outlook에서 구성한 부재 중 메시지가 현재 상태 정보의 일부로 표시되지 않습니다. False로 설정하면 다른 사용자가 자신의 대화 상대 목록에서 사용자 이름을 마우스로 가리킬 때마다 부재 중 메시지가 표시됩니다.</p>
<p>이 설정은 Office Communications Server 2007 R2 그룹 정책 설정 &quot;현재 상태 알림 사용 안 함&quot;에 해당합니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>DisableRTFIM</em></p></td>
<td><p>선택</p></td>
<td><p>System.Boolean</p></td>
<td><p>이 설정과 DisableHtmlIm 설정을 모두 True로 설정하면 서식 있는 텍스트(예: 다양한 글꼴, 글꼴 크기 및 글꼴 색)가 메신저 대화에 사용되지 않습니다. 주고받는 모든 메시지가 일반 텍스트 형식으로 변환됩니다. False로 설정하면 메신저 대화에 서식 있는 텍스트를 사용할 수 있습니다.</p>
<p>이 설정은 Office Communications Server 2007 R2 그룹 정책 설정 &quot;메신저 대화에 서식 있는 텍스트 사용 안 함&quot;에 해당합니다.</p></td>
</tr>
<tr class="even">
<td><p><em>DisableSavingIM</em></p></td>
<td><p>선택</p></td>
<td><p>System.Boolean</p></td>
<td><p>True로 설정하면 메신저 대화 세션을 저장하는 옵션이 Lync 대화 창의 메뉴 표시줄에서 제거됩니다. False로 설정하면 대화 창에서 이러한 옵션을 사용할 수 있습니다.</p>
<p>이 값을 True로 설정하면 사용자가 메신저 대화 내용을 쉽게 저장할 수 있는 메뉴 옵션이 제거됩니다. 그러나 사용자는 메시지 내용의 모든 텍스트를 클립보드로 복사하여 다른 응용 프로그램에 붙여 넣는 방식으로 내용을 저장할 수는 있습니다.</p>
<p>이 설정은 Office Communications Server 2007 R2 그룹 정책 설정 &quot;사용자가 메신저 대화를 저장하지 못하게 함&quot;에 해당합니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>DisplayPhoto</em></p></td>
<td><p>선택</p></td>
<td><p>Microsoft.Rtc.Management.WritableConfig.Policy.Client.DisplayPhoto</p></td>
<td><p>사용자 및 대화 상대의 사진을 Lync에 표시할지 여부를 결정합니다. 유효한 설정은 다음과 같습니다.</p>
<p>NoPhoto - 사진이 Lync에 표시되지 않습니다.</p>
<p>PhotosFromADOnly - Active Directory 도메인 서비스에 게시된 사진만 표시할 수 있습니다.</p>
<p>AllPhotos - Active Directory 사진 또는 사용자 지정 사진을 표시할 수 있습니다.</p>
<p>기본값은 AllPhotos입니다.</p></td>
</tr>
<tr class="even">
<td><p><em>EnableAppearOffline</em></p></td>
<td><p>선택</p></td>
<td><p>System.Boolean</p></td>
<td><p>True로 설정하면 Lync에서 추가 현재 상태(오프라인으로 표시)를 사용할 수 있습니다. 이 상태는 사용자가 오프라인 상태인 것처럼 표시하지만 실제로는 온라인 상태이므로 전화 통화를 받고 메신저 대화에 응답하는 등의 작업을 수행할 수 있습니다. False로 설정하면 Lync에서 오프라인으로 표시 현재 상태를 사용할 수 없습니다.</p>
<p>이 설정은 Office Communications Server 2007 R2 그룹 정책 설정 &quot;[오프라인으로 표시] 상태 사용&quot;에 해당합니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>EnableCallLogAutoArchiving</em></p></td>
<td><p>선택</p></td>
<td><p>System.Boolean</p></td>
<td><p>True로 설정하면 수신 및 발신 전화 통화에 대한 정보가 자동으로 Microsoft Outlook의 대화 내용 폴더에 저장됩니다. 실제 통화 자체는 기록되지 않습니다. 기록되는 내용은 통화에 참가한 사람, 통화 길이, 수신 또는 발신 통화인지 여부 등의 정보입니다. False로 설정하면 이 정보가 Outlook에 저장되지 않습니다.</p>
<p>이 설정은 Office Communications Server 2007 R2 그룹 정책 설정 &quot;Outlook 사서함에 통화 기록 자동 보관 사용/사용 안 함&quot;에 해당합니다.</p></td>
</tr>
<tr class="even">
<td><p><em>EnableClientMusicOnHold</em></p></td>
<td><p>선택</p></td>
<td><p>System.Boolean</p></td>
<td><p>True로 설정하면 발신자가 대기 상태에 있을 때마다 음악이 재생됩니다. False로 설정하면 발신자가 대기 상태에 있을 때마다 음악이 재생되지 않습니다. 기본값은 False입니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>EnableConversationWindowTabs</em></p></td>
<td><p>선택</p></td>
<td><p>System.Boolean</p></td>
<td><p>True로 설정하면 메신저 대화 세션과 관련된 보충 정보가 새 브라우저 창에 표시됩니다. 이 유형의 정보는 Microsoft Unified Communications Managed API(UCMA)를 사용하는 사용자 지정 응용 프로그램에만 사용할 수 있습니다. 예를 들어 고객 서비스 또는 지원 센터 담당자가 다른 사람과 대화하는 동안 관련 정보에 자동으로 액세스할 수 있습니다.</p>
<p>False로 설정하면 보충 정보가 새 브라우저 창에 표시되지 않습니다. 사용자가 메신저 대화 세션에 참가할 수는 있지만 세션과 함께 제공되는 추가 정보에 액세스할 수는 없습니다.</p>
<p>이 설정은 Office Communications Server 2007 R2 그룹 정책 설정 &quot;대화 창 탭 사용&quot;에 해당합니다. 이 매개 변수는 Lync Server 2013에서는 더 이상 사용되지 않습니다.</p></td>
</tr>
<tr class="even">
<td><p><em>EnableEnterpriseCustomizedHelp</em></p></td>
<td><p>선택</p></td>
<td><p>System.Boolean</p></td>
<td><p>True로 설정하면 Lync에서 도움말 메뉴를 클릭하는 사용자에게 조직에서 설정된 사용자 지정 도움말이 제공됩니다. False로 설정하면 도움말 메뉴를 클릭하는 사용자에게 기본 Lync 제품 도움말이 제공됩니다.</p>
<p>사용자 지정 도움말을 사용하려면 사용자 지정 도움말 웹 사이트의 URL도 지정해야 합니다. 이 작업은 CustomizedHelpUrl 매개 변수를 사용하여 수행합니다. 이 매개 변수를 지정하지 않거나 URL이 유효하지 않으면 사용자가 모임을 예약하거나 모임에 참가하려고 할 때 오류가 발생할 수 있습니다.</p>
<p>이 매개 변수는 Lync Server 2013에서는 더 이상 사용되지 않습니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>EnableEventLogging</em></p></td>
<td><p>선택</p></td>
<td><p>System.Boolean</p></td>
<td><p>True로 설정하면 Lync에 대한 자세한 정보가 응용 프로그램 이벤트 로그에 기록됩니다. False로 설정하면 Lync Server에 연결 실패 등의 중요한 이벤트만 이벤트 로그에 기록됩니다.</p>
<p>이 설정은 Office Communications Server 2007 R2 그룹 정책 설정 &quot; Communicator 2007에서 이벤트 로깅 기능 설정&quot;에 해당합니다.</p></td>
</tr>
<tr class="even">
<td><p><em>EnableExchangeContactSync</em></p></td>
<td><p>선택</p></td>
<td><p>System.Boolean</p></td>
<td><p>True(기본값)로 설정하면 Lync가 Microsoft Outlook에서 사용자의 Lync 대화 상대 목록에 있는 각 사용자에 해당하는 개인 연락처를 만듭니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>EnableExchangeDelegateSync</em></p></td>
<td><p>선택</p></td>
<td><p>System.Boolean</p></td>
<td><p>True로 설정하면 Microsoft Exchange에 구성된 사용자에게 모임을 예약할 수 있는 권한이 위임됩니다.</p></td>
</tr>
<tr class="even">
<td><p><em>EnableFullScreenVideo</em></p></td>
<td><p>선택</p></td>
<td><p>System.Boolean</p></td>
<td><p>True로 설정하면 이 매개 변수는 1) Lync 통화에 대해 올바른 가로 세로 비율을 사용하여 화상을 전체 화면으로 표시하고, 2) Lync 통화에 대해 화상 미리 보기를 비활성화합니다. False로 설정하면 Lync에서 화상을 전체 화면으로 표시할 수 없지만 화상 미리 보기는 사용할 수 있습니다.</p>
<p>이 설정은 Office Communications Server 2007 R2 그룹 정책 설정 &quot;모든 OC 화상 통화에 대해 전체 화면 화상을 사용하고 화상 미리 보기는 사용하지 않음&quot;에 해당합니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>EnableHighPerformanceConferencingAppSharing</em></p></td>
<td><p>선택</p></td>
<td><p>System.Boolean</p></td>
<td><p>True로 설정하면 화면 새로 고침 빈도가 높은 응용 프로그램(예: CAD/CAM 응용 프로그램)의 성능이 향상될 수 있습니다. 하지만 이를 통해 성능이 향상되면 다른 응용 프로그램에서 사용 가능한 시스템 리소스 및 네트워크 대역폭이 줄어듭니다.</p></td>
</tr>
<tr class="even">
<td><p><em>EnableHighPerformanceP2PAppSharing</em></p></td>
<td><p>선택</p></td>
<td><p>System.Boolean</p></td>
<td><p>True로 설정하면 피어 투 피어 응용 프로그램 공유 세션이 초당 2.5 프레임의 최대 프레임 속도를 초과할 수 있습니다. 기본값은 False입니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>EnableHotdesking</em></p></td>
<td><p>선택</p></td>
<td><p>System.Boolean</p></td>
<td><p>True로 설정하면 사용자가 Lync Phone Edition 계정을 사용하여 공유 작업 영역에서 Lync Server를 실행하는 전화에 로그온할 수 있습니다. 특히 사용자가 자신의 대화 상대에게 액세스할 수 있게 됩니다. False로 설정하면 사용자가 자신의 자격 증명을 사용하여 공유 작업 영역의 전화에 로그온할 수 없습니다.</p>
<p>이 설정은 사용자 계정이 아니라 공통 영역(공유 작업 영역) 계정에만 적용됩니다. True로 설정하고 공유 작업 영역의 전화에 대한 공통 영역 계정에 적용하면 사용자가 자신의 자격 증명을 사용하여 해당 전화에 로그온할 수 있습니다. False로 설정하면 해당 전화에 아무도 로그온할 수 없게 됩니다.</p>
<p></p></td>
</tr>
<tr class="even">
<td><p><em>EnableIMAutoArchiving</em></p></td>
<td><p>선택</p></td>
<td><p>System.Boolean</p></td>
<td><p>True로 설정하면 사용자가 참가하는 모든 메신저 대화 세션 내용이 Microsoft Outlook의 대화 내용 폴더에 저장됩니다. False로 설정하면 이러한 내용이 자동으로 저장되지 않습니다. 그러나 사용자가 메신저 대화 내용을 수동으로 저장할 수 있습니다.</p>
<p>이 설정은 Office Communications Server 2007 R2 그룹 정책 설정 &quot;Outlook 사서함에 메신저 대화 자동 보관 사용/사용 안 함&quot;에 해당합니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>EnableMediaRedirection</em></p></td>
<td><p>선택</p></td>
<td><p>System.Boolean</p></td>
<td><p>True($True)로 설정하면 오디오 및 비디오 스트림을 다른 네트워크 트래픽에서 분리할 수 있습니다. 이렇게 하면 클라이언트 장치에서 오디오 및 비디오를 로컬에서 인코딩/디코딩할 수 있습니다. 미디어 리디렉션을 사용하면 장치 원격 제어나 코덱 압축 등의 다른 기술에 비해 대개 대역폭 사용량은 낮아지고 서버 확장성은 향상되며 사용자 환경이 보다 최적화됩니다.</p></td>
</tr>
<tr class="even">
<td><p><em>EnableNotificationForNewSubscribers</em></p></td>
<td><p>선택</p></td>
<td><p>System.Boolean</p></td>
<td><p>True로 설정하면 다른 사용자가 연락처 목록에 자신을 추가할 때마다 알림을 받게 됩니다. 또한 알림 대화 상자에서는 해당 사용자를 연락처 목록에 추가하거나 현재 상태 정보를 볼 수 없도록 차단하는 옵션을 제공합니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>EnableSQMData</em></p></td>
<td><p>선택</p></td>
<td><p>System.Boolean</p></td>
<td><p>참고: 이 설정은 Lync Server 2013에서 더 이상 사용되지 않습니다.</p>
<p>CEIP(사용자 환경 개선 프로그램)는 Microsoft가 Lync의 실제 사용 데이터를 수집하는 것을 지원하기 위해 만들어졌습니다. 사용자가 CEIP에 등록하면 Lync를 실행할 때마다 사용자가 수행한 작업 및 해당 작업을 수행한 빈도에 대한 정보가 Microsoft에 다시 전송되어 데이터베이스에 저장되며 사용 추세를 파악할 수 있도록 분석됩니다.</p>
<p>EnableSQMData를 True로 설정하더라도 사용자가 사용자 환경 개선 프로그램에 자동으로 등록되는 것은 아닙니다. 대신 Lync에서 프로그램에 참가할 수 있는 옵션을 제공합니다.</p>
<p>False로 설정하면 사용자가 사용자 환경 개선 프로그램에 등록되지 않습니다. 또한 Lync에서 프로그램에 참가할 수 있는 옵션을 제공하지 않습니다. 사용자가 CEIP 프로그램에 참가하려면 EnableSQMData를 True로 설정하고 이후에 사용자가 수동으로 프로그램에 옵트인(opt in)해야 합니다.</p>
<p>개인 식별 정보는 CEIP에 전송되지 않습니다. CEIP는 사용자가 메신저 대화를 보내는 사람 및 사용자에게 메신저 대화를 보내는 사람을 추적하지 않습니다. 이 프로그램은 Lync를 사용하여 파일을 전송하는 빈도, 대화 상대 목록에 있는 평균 대화 상대 수 등의 정보를 추적합니다.</p>
<p>이 설정은 Office Communications Server 2007 R2 그룹 정책 설정 &quot;Instrumentation 지정&quot;에 해당합니다.</p></td>
</tr>
<tr class="even">
<td><p><em>EnableTracing</em></p></td>
<td><p>선택</p></td>
<td><p>System.Boolean</p></td>
<td><p>True로 설정하면 Lync에서 소프트웨어 추적을 사용할 수 있고, False로 설정하면 소프트웨어 추적을 사용할 수 없습니다. 소프트웨어 추적은 API 통화 추적을 비롯하여 프로그램이 수행하는 모든 작업에 대한 자세한 기록을 유지합니다. 이러한 추적은 대체로 개발자와 응용 프로그램 지원 담당자에게 유용합니다.</p>
<p>이 설정은 Office Communications Server 2007 R2 그룹 정책 설정 &quot; Communicator 2007에서 추적 기능 설정&quot;에 해당합니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>EnableUnencryptedFileTransfer</em></p></td>
<td><p>선택</p></td>
<td><p>System.Boolean</p></td>
<td><p>True로 설정하면 사용자가 암호화된 파일 전송을 지원하지 않는 메신저 소프트웨어를 가진 외부 사용자와 파일을 교환할 수 있습니다. False로 설정하면 사용자가 암호화된 파일 전송을 지원하는 소프트웨어를 가진 외부 사용자하고만 파일을 교환할 수 있습니다.</p>
<p>이 설정은 Office Communications Server 2007 R2 그룹 정책 설정 &quot;암호화되지 않은 파일 전송 허용&quot;에 해당합니다.</p></td>
</tr>
<tr class="even">
<td><p><em>EnableURL</em></p></td>
<td><p>선택</p></td>
<td><p>System.Boolean</p></td>
<td><p>True로 설정하면 메신저 대화에 포함된 하이퍼링크가 &quot;클릭 가능&quot;하게 됩니다. 즉, 사용자가 이 링크를 클릭하면 웹 브라우저에서 지정한 위치가 열립니다. False로 설정하면 메신저 대화에서 하이퍼링크가 일반 텍스트로 표시됩니다. 해당 위치로 이동하려면 사용자가 링크 텍스트를 복사하여 웹 브라우저에 붙여 넣어야 합니다.</p>
<p>이 설정은 Office Communications Server 2007 R2 그룹 정책 설정 &quot;메신저 대화에 하이퍼링크 허용&quot;에 해당합니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>EnableVOIPCallDefault</em></p></td>
<td><p>선택</p></td>
<td><p>System.Boolean</p></td>
<td><p>True로 설정하면 사용자가 통화하려면 클릭 기능을 사용할 때마다 Lync 통화가 연결됩니다.</p>
<p>이 정책 설정은 클릭하여 전화 걸기 기능의 초기 상태에만 영향을 줍니다. 사용자가 클릭하여 전화 걸기 설정의 값을 수정하면 사용자가 선택한 값이 이 정책 설정을 대신합니다. 사용자가 클릭하여 전화 걸기 설정을 수정한 다음 해당 설정은 사용 상태로 유지되며 EnableVOIPCallDefault 정책의 영향을 받지 않습니다.</p></td>
</tr>
<tr class="even">
<td><p><em>ExcludedContactFolders</em></p></td>
<td><p>선택</p></td>
<td><p>System.String</p></td>
<td><p>Lync가 새 대화 상대를 검색할 때마다 검색할 수 없는 Microsoft Outlook 연락처 폴더(있는 경우)를 나타냅니다. 폴더 이름을 세미콜론으로 구분하여 여러 개의 폴더를 지정할 수 있습니다(예: -ExcludedContactFolders &quot;SenderPhotoContacts;OtherContacts&quot;).</p></td>
</tr>
<tr class="odd">
<td><p><em>Force</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>명령을 실행할 때 발생할 수 있는 심각하지 않은 오류 메시지를 표시하지 않습니다.</p></td>
</tr>
<tr class="even">
<td><p><em>HelpEnvironment</em></p></td>
<td><p>선택</p></td>
<td><p>System.String</p></td>
<td><p>&quot;Office 365&quot;로 설정하면 기본적으로 표시되는 온-프레미스 도움말이 아닌 Lync Server 2013용 Office 365 클라이언트 도움말 설명서가 사용자에게 표시됩니다. HelpEnvironment는 &quot;Office 365&quot; 또는 null 값($Null)으로 설정할 수 있습니다. 기본값인 null 값으로 설정하는 경우에는 온-프레미스 도움말이 사용자에게 표시됩니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>HotdeskingTimeout</em></p></td>
<td><p>선택</p></td>
<td><p>System.TimeSpan</p></td>
<td><p>&quot;hot-desk&quot; 전화에 로그온한 사용자의 시간 제한 간격입니다. hot-desk 전화는 공유 작업 영역에 있고 사용자가 Lync Server 계정을 사용하여 로그온할 수 있는 Lync Phone Edition을 실행하는 전화입니다. hot-desk 시간 제한은 사용자가 hot-desk 전화에서 자동으로 로그오프되기 전에 경과할 수 있는 시간(분)을 지정합니다. hot-desk 시간 제한을 지정할 때는 시:분:초 형식을 사용해야 합니다. 예를 들어 다음 구문은 hot-desk 시간 제한 값을 45분으로 설정합니다.</p>
<p>-HotdeskingTimeout 00:45:00</p>
<p>이 정책 설정은 사용자에게 적용되는 것이 아니라 공통 영역 전화에만 적용됩니다. 기본값은 5분(00:05:00)이고 최소값은 30초(00:00:30)입니다.</p></td>
</tr>
<tr class="even">
<td><p><em>Identity</em></p></td>
<td><p>선택</p></td>
<td><p>Microsoft.Rtc.Management.Xds.XdsIdentity</p></td>
<td><p>새 정책에 할당된 고유 식별자입니다. 전역 정책을 참조하려면 -Identity global 구문을 사용합니다. 사이트 정책을 참조하려면 &quot;site:&quot; 접두사와 사이트 이름을 ID로 사용합니다(예: -Identity site:Redmond). 사용자별 정책을 참조하려면 -Identity SalesClientPolicy와 유사한 구문을 사용합니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>IMWarning</em></p></td>
<td><p>선택</p></td>
<td><p>System.String</p></td>
<td><p>이 매개 변수를 구성하면 사용자가 메신저 대화 세션에 참가할 때마다 지정한 메시지가 대화 창에 표시됩니다. 예를 들어 IMWarning을 &quot;All information is the property of Litwareinc&quot;로 설정하면 사용자가 메신저 대화 세션에 참가할 때마다 해당 메시지가 대화 창에 표시됩니다.</p>
<p>경고 메시지는 256자로 제한되며 일반 텍스트만 포함할 수 있습니다. 임의 서식(굵게 또는 기울임꼴)은 사용할 수 없으며 텍스트 내에 클릭 가능한 URL을 포함할 수 없습니다.</p>
<p>이 매개 변수를 null 값($Null)으로 설정하면 대화 창에 메시지가 표시되지 않습니다.</p>
<p>이 설정은 Office Communications Server 2007 R2 그룹 정책 설정 &quot;경고문&quot;에 해당합니다.</p></td>
</tr>
<tr class="even">
<td><p><em>Instance</em></p></td>
<td><p>선택</p></td>
<td><p>ClientPolicy</p></td>
<td><p>개별 매개 변수 값을 설정하는 대신 cmdlet에 개체에 대한 참조를 전달할 수 있습니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>MAPIPollInterval</em></p></td>
<td><p>선택</p></td>
<td><p>System.TimeSpan</p></td>
<td><p>중요: 이 매개 변수는 Lync Server 2013에서는 더 이상 사용되지 않습니다.</p>
<p>Microsoft Exchange Server 2003 사용자의 경우 MAPIPollInterval은 Lync가 Exchange 공용 폴더에서 일정 데이터를 검색하는 빈도를 지정합니다. MAPIPollInterval은 1초에서 1시간(포함) 사이의 모든 값으로 설정할 수 있습니다. MAPI 폴링 간격을 구성하려면 시:분:초 형식을 사용합니다. 예를 들어 다음 명령은 MAPI 폴링 간격을 45분으로 설정합니다.</p>
<p>-MapiPollInterval 00:45:00</p>
<p>이 설정은 전자 메일 계정이 Microsoft Exchange Server 2010 또는 Microsoft Exchange Server 2007인 사용자에게는 적용되지 않습니다. 이러한 사용자에 대한 일정 검색은 WebServicePollInterval을 사용하여 관리합니다.</p>
<p>이 설정은 Office Communications Server 2007 R2 그룹 정책 설정 &quot;MAPI 공급자로부터 일정 데이터를 로드할 시간 간격&quot;에 해당합니다.</p></td>
</tr>
<tr class="even">
<td><p><em>MaximumDGsAllowedInContactList</em></p></td>
<td><p>선택</p></td>
<td><p>System.UInt32</p></td>
<td><p>사용자가 대화 상대로 구성할 수 있는 최대 메일 그룹 수를 나타냅니다. MaximumDGsAllowedInContactList는 0에서 64(포함) 사이의 정수 값으로 설정할 수 있습니다. 기본값은 10입니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>MaximumNumberOfContacts</em></p></td>
<td><p>선택</p></td>
<td><p>System.UInt16</p></td>
<td><p>사용자가 보유할 수 있는 최대 대화 상대 수를 나타냅니다. 최대 대화 상대 수는 0에서 1000(포함) 사이의 정수 값으로 설정할 수 있습니다. 0으로 설정하면 사용자가 대화 상대를 보유할 수 없습니다.</p>
<p>이 설정은 Office Communications Server 2007 R2 그룹 정책 설정 &quot;최대 허용 대화 상대 수&quot;에 해당합니다.</p></td>
</tr>
<tr class="even">
<td><p><em>MaxPhotoSizeKB</em></p></td>
<td><p>선택</p></td>
<td><p>System.UInt32</p></td>
<td><p>Lync에 표시되는 사진의 최대 크기(킬로바이트)를 나타냅니다.</p>
<p>기본값은 30KB입니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>MusicOnHoldAudioFile</em></p></td>
<td><p>선택</p></td>
<td><p>System.String</p></td>
<td><p>발신자가 대기 상태에 있을 때 재생할 오디오 파일의 경로입니다. 이 속성의 값을 구성하면 대기 음악이 사용되며 사용자가 이 기능을 비활성화할 수 없습니다. 이 속성의 값을 구성하지 않으면 EnableClientMusicOnHold가 True로 설정된 경우 사용자가 고유한 대기 음악 파일을 지정할 수 있습니다.</p></td>
</tr>
<tr class="even">
<td><p><em>P2PAppSharingEncryption</em></p></td>
<td><p>선택</p></td>
<td><p>Microsoft.Rtc.Management.WritableConfig.Policy.Client.P2PAppSharingEncryption</p></td>
<td><p>피어 간 대화 중에 교환되는 데스크톱 및 응용 프로그램 공유 데이터를 암호화할지 여부를 나타냅니다. 허용되는 값은 다음과 같습니다.</p>
<p>Supported. 가능한 경우 데스크톱 및 응용 프로그램 공유 데이터가 암호화됩니다.</p>
<p>Enforced. 데스크톱 및 응용 프로그램 공유 데이터를 암호화해야 합니다. 데이터를 암호화할 수 없는 경우 데스크톱 및 응용 프로그램 공유가 대화에 사용되지 않습니다.</p>
<p>NotSupported. 데스크톱 및 응용 프로그램 공유 데이터가 암호화되지 않습니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>PlayAbbreviatedDialTone</em></p></td>
<td><p>선택</p></td>
<td><p>System.Boolean</p></td>
<td><p>True로 설정하면 Lync 호환 송수화기를 들 때마다 3초 동안 발신음이 재생됩니다. Lync 호환 송수화기는 표준 전화처럼 보이지만 컴퓨터의 USB 포트에 연결되고 &quot;일반&quot; 전화 통화가 아니라 Lync 통화를 수행하는 데 사용됩니다. False로 설정하면 Lync 호환 송수화기를 들 때마다 30초 동안 발신음이 재생됩니다.</p>
<p>이 설정은 Office Communications Server 2007 R2 그룹 정책 설정 &quot;단축된 발신음 재생&quot;에 해당합니다.</p></td>
</tr>
<tr class="even">
<td><p><em>PolicyEntry</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.PSListModifier</p></td>
<td><p>기본 매개 변수로 처리되지 않는 설정을 추가할 수 있습니다. 예를 들어 Microsoft Lync Server 2010 시험판 버전을 테스트할 때는 Microsoft Lync 2010에 사용자 의견 보내기 옵션을 추가할 수 있었습니다. 이 작업은 다음과 같은 코드를 사용하여 수행되었습니다.</p>
<p>$x = New-CsClientPolicyEntry -Name &quot;OnlineFeedbackURL&quot; -Value &quot;http://www.litwareinc.com/feedback&quot;Set-CsClientPolicy -Identity global -PolicyEntry @{Add=$x}</p>
<p>자세한 내용 및 예제는 <a href="new-csclientpolicyentry.md">New-CsClientPolicyEntry</a> cmdlet 도움말 항목을 참고하세요.</p></td>
</tr>
<tr class="odd">
<td><p><em>SearchPrefixFlags</em></p></td>
<td><p>선택</p></td>
<td><p>System.UInt16</p></td>
<td><p>사용자가 새 대화 상대를 검색할 때마다 사용해야 하는 주소록 특성을 나타냅니다. 검색 접두사 플래그는 유사 이진 숫자(예: 11101111)로 생성되며, 여기서 1은 특성을 검색해야 함을 나타내고 0은 특성을 검색하지 않아야 함을 나타냅니다. 이진 값의 특성은 오른쪽에서 왼쪽으로 다음과 같습니다.</p>
<p>기본 전자 메일 주소</p>
<p>전자 메일 별칭</p>
<p>모든 전자 메일 주소</p>
<p>회사</p>
<p>표시 이름</p>
<p>이름</p>
<p>성</p>
<p>이진 값 1110111은 특성 4: 회사를 제외한 모든 특성이 검색되어야 함을 나타냅니다. 표시 이름, 이름 및 성만 검색하려면 다음 값을 생성합니다.</p>
<p>1110000</p>
<p>이진 값이 생성된 후 10진수 값으로 변환한 다음 SearchPrefixFlags에 할당해야 합니다. 이진 숫자를 10진수로 변환하려면 다음과 같은 Windows PowerShell 명령을 사용합니다.</p>
<p>[Convert]::ToInt32(&quot;1110111&quot;, 2)</p></td>
</tr>
<tr class="even">
<td><p><em>ShowManagePrivacyRelationships</em></p></td>
<td><p>선택</p></td>
<td><p>System.Boolean</p></td>
<td><p>True로 설정하면 Lync 대화 상대 목록 창에 관계 옵션이 표시됩니다. False로 설정하면 관계 옵션이 숨겨집니다.</p>
<p>이 설정은 Lync 2010에만 적용됩니다. Lync 2013은 ShowManagePrivacyRelationships가 True로 설정된 경우에도 이러한 관계를 표시하지 않습니다.</p>
<p>기본값은 False입니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>ShowRecentContacts</em></p></td>
<td><p>선택</p></td>
<td><p>System.Boolean</p></td>
<td><p>이 매개 변수는 클라이언트에 영향을 주지 않습니다.</p>
<p></p></td>
</tr>
<tr class="even">
<td><p><em>ShowSharepointPhotoEditLink</em></p></td>
<td><p>선택</p></td>
<td><p>System.Boolean</p></td>
<td><p>True로 설정하면 Lync에서 사용자가 SharePoint 내 사이트에 저장된 개인 사진을 편집할 수 있는 링크를 포함합니다. 기본값은 False이며, Lync에서 SharePoint 내 사이트에 대한 링크를 포함하지 않습니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>SPSearchCenterExternalURL</em></p></td>
<td><p>선택</p></td>
<td><p>System.String</p></td>
<td><p>키워드 검색(전문 검색이라고도 함)에 사용되는 SharePoint 사이트의 외부 URL입니다. 이 URL은 Lync에 표시되는 키워드 검색 결과의 맨 아래에 나타납니다. 사용자가 이 URL을 클릭하면 웹 브라우저에서 SharePoint 사이트가 열리며, 사용자는 여기서 SharePoint의 검색 기능을 사용하여 검색할 수 있습니다. SharePoint는 Lync보다 많은 검색 옵션을 제공합니다.</p>
<p>SPSearchCenterExternalURL은 외부 사용자, 즉 조직의 방화벽 외부에서 로그온하는 사용자를 위한 URL을 나타냅니다. SPSearchCenterInternalURL 매개 변수는 방화벽 내부에서 로그온하는 사용자에 사용됩니다.</p></td>
</tr>
<tr class="even">
<td><p><em>SPSearchCenterInternalURL</em></p></td>
<td><p>선택</p></td>
<td><p>System.String</p></td>
<td><p>키워드 검색(전문 검색이라고도 함)에 사용되는 SharePoint 사이트의 내부 URL입니다. 이 URL은 Lync에 표시되는 키워드 검색 결과의 맨 아래에 나타납니다. 사용자가 이 URL을 클릭하면 웹 브라우저에서 SharePoint 사이트가 열리며, 사용자는 여기서 SharePoint의 검색 기능을 사용하여 검색할 수 있습니다. SharePoint는 Lync보다 많은 검색 옵션을 제공합니다.</p>
<p>SPSearchCenterInternalURL은 내부 사용자, 즉 조직의 방화벽 내부에서 로그온하는 사용자를 위한 URL을 나타냅니다. SPSearchCenterExternalURL 매개 변수는 방화벽 외부에서 로그온하는 사용자에 사용됩니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>SPSearchExternalURL</em></p></td>
<td><p>선택</p></td>
<td><p>System.String</p></td>
<td><p>키워드 검색(전문 검색이라고도 함)에 사용되는 SharePoint 사이트의 외부 URL입니다. Lync는 외부 사용자(즉, 조직의 방화벽 외부에서 시스템에 액세스한 사용자)가 키워드 검색을 수행할 때마다 이 URL에 있는 SharePoint 사이트를 사용합니다.</p></td>
</tr>
<tr class="even">
<td><p><em>SPSearchInternalURL</em></p></td>
<td><p>선택</p></td>
<td><p>System.String</p></td>
<td><p>키워드 검색(전문 검색이라고도 함)에 사용되는 SharePoint 사이트의 내부 URL입니다. Lync는 내부 사용자(즉, 조직의 방화벽 내부에서 로그온한 사용자)가 키워드 검색을 수행할 때마다 이 URL에 있는 SharePoint 사이트를 사용합니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>TabURL</em></p></td>
<td><p>선택</p></td>
<td><p>System.String</p></td>
<td><p>Lync 대화 상대 목록 창의 맨 아래에 있는 사용자 지정 탭을 만드는 데 사용되는 XML 파일의 위치를 지정합니다. 사용자 지정 탭을 통해 Lync 내에서 웹 페이지(예: 지원 센터 웹 페이지)에 액세스할 수 있습니다. 이 매개 변수는 Lync Server 2013에서는 더 이상 사용되지 않습니다.</p>
<p>이 설정은 Office Communications Server 2007 R2 그룹 정책 설정 &quot;탭 URL&quot;에 해당합니다.</p></td>
</tr>
<tr class="even">
<td><p><em>TracingLevel</em></p></td>
<td><p>선택</p></td>
<td><p>Microsoft.Rtc.Management.WritableConfig.Policy.Client.TracingLevel</p></td>
<td><p>관리자가 Lync 2013에서 이벤트 추적 및 로깅을 관리할 수 있도록 합니다. 사용 가능한 값은 다음과 같습니다.</p>
<p>* Off - 추적을 사용할 수 없으며 사용자가 이 설정을 변경할 수 없습니다.</p>
<p>* Light - 최소한의 추적을 수행하며 사용자가 이 설정을 변경할 수 없습니다.</p>
<p>* Full - 상세한 추적이 수행되며 사용자가 이 설정을 변경할 수 없습니다.</p>
<p>기본적으로 TracingLevel은 Light로 설정됩니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>WebServicePollInterval</em></p></td>
<td><p>선택</p></td>
<td><p>System.TimeSpan</p></td>
<td><p>Microsoft Exchange Server 2007 이상 버전의 제품 사용자의 경우 WebServicePollInterval은 Lync가 Microsoft Exchange Server 웹 서비스에서 일정 데이터를 검색하는 빈도를 지정합니다. WebServicePollInterval은 1초에서 1시간(포함) 사이의 모든 값으로 설정할 수 있습니다. 웹 서비스 폴링 간격을 구성하려면 시:분:초 형식을 사용합니다. 예를 들어 다음 명령은 웹 서비스 폴링 간격을 45분으로 설정합니다.</p>
<p>-WebServicePollInterval 00:45:00</p>
<p>이 설정은 전자 메일 계정이 Exchange 2003인 사용자에게는 적용되지 않습니다. 이러한 사용자에 대한 일정 검색은 MAPIPollInterval을 사용하여 관리합니다.</p>
<p>이 설정은 Communications Server 2007 R2 그룹 정책 설정 &quot;웹 서비스 공급자로부터 일정 데이터를 로드할 시간 간격&quot;에 해당합니다.</p></td>
</tr>
<tr class="even">
<td><p><em>WhatIf</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>명령을 실제로 실행하지 않고도 명령이 실행될 경우 발생할 수 있는 현상을 설명합니다.</p></td>
</tr>
</tbody>
</table>


## 입력 형식

Microsoft.Rtc.Management.WritableConfig.Policy.Client.ClientPolicy 개체입니다. **Set-CsClientPolicy** cmdlet은 클라이언트 정책 개체의 파이프라인된 인스턴스를 허용합니다.

## 반환 형식

**Set-CsClientPolicy** cmdlet은 값이나 개체를 반환하지 않습니다. 대신 이 cmdlet은 Microsoft.Rtc.Management.WritableConfig.Policy.Client.ClientPolicy 개체의 인스턴스를 구성합니다.

## 참고 항목

#### 기타 리소스

[Get-CsClientPolicy](get-csclientpolicy.md)  
[Grant-CsClientPolicy](grant-csclientpolicy.md)  
[New-CsClientPolicy](new-csclientpolicy.md)  
[Remove-CsClientPolicy](remove-csclientpolicy.md)

