---
title: 'Lync Server 2013: 호스팅된 음성 메일 정책'
TOCTitle: 호스팅된 음성 메일 정책
ms:assetid: d62a35ed-cbe2-4f06-86b4-e192c18435c1
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg398932(v=OCS.15)
ms:contentKeyID: 49305166
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Lync Server 2013의 호스팅된 음성 메일 정책

 

_**마지막으로 수정된 항목:** 2012-10-01_

*호스팅된 음성 메일 정책* 은 해당 사서함이 호스팅된 Exchange 서비스에 있는 사용자에 대한 호출을 라우팅할 위치에 대한 정보를 Lync Server 2013 ExUM 라우팅 응용 프로그램에 제공합니다.


> [!NOTE]
> 호스팅된 음성 메일 정책은 호스팅된 Exchange UM과 Lync Server 2013을 통합할 경우에만 필요합니다. 온-프레미스 Exchange UM과 통합할 경우에는 필요하지 않습니다.



## 호스팅된 음성 메일 정책 범위

호스팅된 음성 메일 정책 범위는 정책이 적용되는 계층 수준을 결정합니다. 다음과 같은 범위 수준으로 호스팅된 음성 메일 정책을 구성할 수 있습니다.

  - *전역* 정책은 잠재적으로 Lync Server 2013 배포의 모든 사용자에게 영향을 미칠 수 있습니다. 사용자가 호스팅된 Exchange UM 액세스를 사용할 수 있도록 설정되어 있고 사용자별 정책이 사용자에게 할당되지 않은 경우, 사이트 정책이 사용자 사이트에 할당되지 않은 경우 전역 정책이 적용됩니다. 전역 정책은 Lync Server 2013과 함께 설치되며 요구 사항을 충족하도록 정책을 수정할 수 있지만 정책의 이름을 변경하거나 정책을 삭제할 수는 없습니다.

  - *사이트* 정책은 정책이 정의된 사이트에 속한 모든 사용자에게 영향을 미칠 수 있습니다. 사용자가 호스팅된 Exchange UM에 액세스할 수 있도록 구성되어 있는데 사용자별 정책이 할당되지 않은 경우에는 사이트 정책이 적용됩니다.

  - *사용자별* 정책은 개별 사용자나 그룹에만 영향을 미칠 수 있습니다. 사용자별 정책을 적용하려면 개별 사용자, 그룹 및 대화 상대 개체에 정책을 명시적으로 할당해야 합니다.


> [!NOTE]
> 대부분의 경우 호스팅된 음성 메일 정책은 하나만 필요합니다. 요구 사항을 모두 충족하기 위해 전역 정책을 수정해야 하는 경우도 있습니다. 호스팅된 음성 메일 정책을 여러 개 배포할 경우 이러한 모든 정책에는 사용자별 범위가 지정됩니다.



## 호스팅된 음성 메일 정책 특성

음성 메일 정책은 Lync Server 2013 ExUM 라우팅 응용 프로그램이 호스팅된 UM 구현에서 보낸 INVITE 메시지의 요청 URI에 삽입하는 다음과 같은 두 개의 특성을 정의합니다.

  - **Destination :** 호스팅된 Exchange UM 서비스의 FQDN(정규화된 도메인 이름). 이 값은 라우팅을 위해 온-프레미스 Lync Server 에지 서버에서 사용됩니다.
    

    > [!NOTE]
    > Exchange Online의 FQDN은 exap.um.outlook.com입니다.



  - **Organization :** Lync Server 2013 사용자의 사서함이 속한 호스팅된 Exchange UM 서비스의 테넌트에 대한 FQDN. 음성 메일 정책에는 여러 개의 조직이 포함될 수 있습니다. 정책에 둘 이상의 조직이 포함된 경우 이 특성은 Lync Server 2013 사용자 사서함이 속한 Exchange Server 테넌트에 대해 쉼표로 구분된 목록이어야 합니다.


> [!NOTE]
> 호스팅된 Exchange UM 서비스의 테넌트 관리자는 Destination 및 Organization 특성 설정에 필요한 값을 제공합니다. 정책을 구성하려면 New-CsHostedVoicemailPolicy cmdlet를 실행하거나 Set-CsHostedVoicemailPolicy cmdlet를 사용하여 기존의 정책(예: 전역 정책)을 수정해야 합니다.



호스팅된 음성 메일 정책을 관리하는 방법에 대한 자세한 내용은 다음 cmdlet에 대한 Lync Server 관리 셸 설명서를 참조하십시오.

  - New-CsHostedVoicemailPolicy

  - Set-CsHostedVoicemailPolicy

  - Get-CsHostedVoicemailPolicy

## 사용자별 음성 메일 정책 할당

호스팅된 음성 메일 정책이 사용자별 범위에서 정의된 경우 정책을 명시적으로 할당해야 합니다. Grant-CsHostedVoicemailPolicy cmdlet를 실행하여 정책을 개별 사용자나 그룹에 할당할 수 있습니다.

사용자별 호스팅된 음성 메일 정책을 할당하거나 제거하는 방법에 대한 자세한 내용은 다음 cmdlet에 대한 Lync Server 관리 셸 설명서를 참조하십시오.

  - Grant-CsHostedVoicemailPolicy

  - Remove-CsHostedVoicemailPolicy

