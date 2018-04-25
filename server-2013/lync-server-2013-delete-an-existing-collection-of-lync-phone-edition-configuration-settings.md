---
title: Lync Phone Edition 구성 설정의 기존 컬렉션 삭제
TOCTitle: Lync Phone Edition 구성 설정의 기존 컬렉션 삭제
ms:assetid: 1bfc427d-4dcd-4199-b25f-8d5cfec2164f
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/JJ687984(v=OCS.15)
ms:contentKeyID: 49885669
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Lync Phone Edition 구성 설정의 기존 컬렉션 삭제

 

_**마지막으로 수정된 항목:** 2013-02-23_

Lync Phone Edition을 실행하는 장치의 설정 컬렉션을 더 이상 사용하지 않으려는 경우 삭제합니다. 사이트의 컬렉션을 삭제하면 전역 설정이 해당 사이트의 전화에 적용됩니다. 전역 컬렉션은 삭제할 수 없습니다.


> [!NOTE]
> 컬렉션을 삭제하는 대신 일부 설정을 변경만 할 수 있습니다. 이 작업을 수행하는 방법에 대한 자세한 내용은 <A href="lync-server-2013-create-or-modify-a-collection-of-lync-phone-edition-configuration-settings.md">Lync Phone Edition 구성 설정 모음 만들기 및 수정</A>을 참조하십시오.



## Lync Phone Edition 구성 설정 컬렉션을 삭제하려면

1.  CsUserAdministrator 역할 또는 CsAdministrator 역할에 할당된 사용자 계정에서 내부 배포된 컴퓨터에 로그온합니다.

2.  브라우저 창을 연 다음 Admin URL을 입력하여 Lync Server 제어판을 엽니다. Lync Server 제어판을 시작하는 데 사용할 수 있는 다양한 방법에 대한 자세한 내용은 [Lync Server 관리 도구 열기](lync-server-2013-open-lync-server-administrative-tools.md)를 참조하세요.

3.  왼쪽 탐색 모음에서 **클라이언트**를 클릭하고 **장치 구성** 탐색 단추를 클릭합니다.

4.  **장치 구성** 페이지에서 삭제할 컬렉션을 클릭하고 **편집** 메뉴를 클릭한 후에 **삭제**를 클릭합니다.
    

    > [!NOTE]
    > 전역 컬렉션을 삭제해도 단순히 설정이 기본 설정으로 돌아가며 컬렉션이 제거되는 것은 아닙니다.



5.  확인 상자에서 **확인**을 클릭합니다.

## Lync Server 관리 셸 cmdlet을 사용하여 Lync Phone Edition 구성 설정을 제거하려면

Windows PowerShell 및 **Remove-CsUCConfiguration** cmdlet을 사용하여 Lync Phone Edition 구성 정보를 삭제할 수도 있습니다. 이 cmdlet은 Lync Server 2013 관리 셸 또는 Windows PowerShell의 원격 세션에서 실행할 수 있습니다. 원격 Windows PowerShell을 사용하여 Lync Server에 연결하는 방법에 대한 자세한 내용은 Lync Server Windows PowerShell 블로그 문서인 "빠른 시작: 원격 PowerShell을 사용하여 Microsoft Lync Server 2010 관리"([http://go.microsoft.com/fwlink/p/?linkId=255876](http://go.microsoft.com/fwlink/p/?linkid=255876))를 참조하세요.

## Lync Phone Edition 구성 설정의 지정된 컬렉션을 제거하려면

  - 다음 명령은 Redmond 사이트에 적용된 UC 전화 구성 설정을 삭제합니다.
    
        Remove-CsUCPhoneConfiguration -Identity "site:Redmond"

## 사이트 범위에 적용된 모든 Lync Phone Edition 구성 설정을 제거하려면

  - 다음 명령은 서비스 범위에 적용된 모든 UC 전화 구성 설정을 제거합니다.
    
        Get-CsUCPhoneConfiguration -Filter "site:*" | Remove-CsUCPhoneConfiguration

## 전화 잠금이 사용하지 않도록 설정된 모든 Lync Phone Edition 구성 설정을 제거하려면

  - 다음 명령은 전화 잠금이 사용하지 않도록 설정된 UC 전화 구성 설정 컬렉션을 삭제합니다.
    
        Get-CsUCPhoneConfiguration | Where-Object {$_.EnforcePhoneLock -eq $False} | Remove-CsUCPhoneConfiguration

자세한 내용은 [Remove-CsUCPhoneConfiguration](remove-csucphoneconfiguration.md)을 참조하십시오.

