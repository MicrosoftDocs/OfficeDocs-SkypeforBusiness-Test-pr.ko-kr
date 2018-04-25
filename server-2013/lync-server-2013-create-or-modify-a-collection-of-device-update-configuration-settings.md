---
title: 장치 업데이트 구성 설정 모음 만들기 또는 수정
TOCTitle: 장치 업데이트 구성 설정 모음 만들기 또는 수정
ms:assetid: 3e8ce95f-a8c8-417c-b1f7-0f759a567aff
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/JJ994029(v=OCS.15)
ms:contentKeyID: 52056825
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# 장치 업데이트 구성 설정 모음 만들기 또는 수정

 

_**마지막으로 수정된 항목:** 2013-02-23_

장치 업데이트 구성 설정은 Windows PowerShell 및 **New-CsDeviceUpdateConfiguration** cmdlet을 사용하여 만들 수 있으며(사이트 범위에서만) **Set-CsDeviceUpdateConfiguration** cmdlet을 사용하여 수정할 수 있습니다. 이러한 cmdlet은 Lync Server 2013 관리 셸 또는 Windows PowerShell의 원격 세션에서 실행할 수 있습니다.


> [!NOTE]
> 원격 Windows PowerShell을 사용하여 Lync Server에 연결하는 방법에 대한 자세한 내용은 Lync Server Windows PowerShell 블로그 문서인 "빠른 시작: 원격 PowerShell을 사용하여 Microsoft Lync Server 2010 관리"(<A href="http://go.microsoft.com/fwlink/p/?linkid=255876">http://go.microsoft.com/fwlink/p/?linkId=255876</A>)를 참조하세요.




## 기본값을 사용하는 장치 업데이트 구성 설정을 만들려면

  - 다음 명령은 Redmond 사이트에 대해 장치 업데이트 구성 설정 집합을 새로 만듭니다.
    
        New-CsDeviceUpdateConfiguration -Identity "site:Redmond"
    
    앞의 명령에서는 필수 Identity 매개 변수 외에 다른 매개 변수는 지정되지 않았으므로 새 구성 설정 컬렉션은 모든 속성에 대해 기본값을 사용합니다.

## 장치 업데이트 구성 설정을 만들 때 단일 속성 값을 변경하려면

  - 다른 속성 값을 사용하는 설정을 만들려면 해당하는 매개 변수와 매개 변수 값만 포함하면 됩니다. 예를 들어 기본적으로 21일마다 오래된 로그 파일을 삭제하는 장치 업데이트 구성 설정 컬렉션을 만들려면 다음과 같은 명령을 사용합니다.
    
        New-CsDeviceUpdateConfiguration -Identity "site:Redmond" -LogCleanupInterval "21.00:00:00"

## 장치 업데이트 구성 설정을 만들 때 여러 속성 값을 변경하려면

  - 여러 매개 변수를 포함하면 여러 속성 값을 수정할 수 있습니다. 예를 들어 다음 명령은 로그 정리 간격을 21일로, 로그 플러시 간격을 30분으로 설정합니다.
    
        New-CsDeviceUpdateConfiguration -Identity "site:Redmond" -LogCleanupInterval "21.00:00:00" -LogFlushInterval "00:30:00"

기존 장치 구성 설정을 수정하는 방법에 대한 자세한 내용은 [Set-CsDeviceUpdateConfiguration](set-csdeviceupdateconfiguration.md) cmdlet의 도움말 항목을 참조하십시오. 구성 설정 컬렉션을 만드는 방법에 대한 자세한 내용은 [New-CsDeviceUpdateConfiguration](new-csdeviceupdateconfiguration.md)cmdlet의 도움말 항목을 참조하십시오.

