---
title: 중앙화된 로깅 서비스의 로그 캡처 읽기
TOCTitle: 중앙화된 로깅 서비스의 로그 캡처 읽기
ms:assetid: c86ccf61-d86f-4ebd-b8d1-984a1b73005d
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/JJ721879(v=OCS.15)
ms:contentKeyID: 49885980
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# 중앙화된 로깅 서비스의 로그 캡처 읽기

 

_**마지막으로 수정된 항목:** 2013-02-22_

검색을 실행하고 보고된 문제를 추적하는 데 사용할 수 있는 파일이 생성되었다면 중앙 로깅 서비스의 실제 이점을 실감하셨을 것입니다. 파일을 읽을 수 있는 방법은 여러 가지가 있습니다. 출력 파일이 표준 텍스트 형식이면 Notepad.exe 또는 텍스트 파일을 열고 읽을 수 있는 기타 프로그램을 사용할 수 있습니다. 파일이 크거나 좀 더 복잡한 문제가 있으면 중앙 로깅 서비스의 로깅 출력 파일을 읽고 구문 분석하기 위해 고안된 Snooper.exe 같은 도구를 사용할 수 있습니다. Snooper는 Lync Server 2013 Debug Tools에 포함되어 있으며 별도로 다운로드할 수 있습니다. Lync Server 2013 Debugging Tools용으로 만들어진 바로 가기나 메뉴 항목은 없습니다. Lync Server 2013 Debug Tools를 설치한 후 Windows 탐색기, 명령줄 창 또는 Lync Server 관리 셸을 열고 C:\\Program Files\\Microsoft Lync Server 2013\\Debugging Tools 디렉터리(기본 디렉터리임)로 이동합니다. Snooper.exe를 두 번 클릭하거나, 명령줄 또는 Lync Server 관리 셸을 사용하는 경우 Snooper.exe를 입력합니다.


> [!IMPORTANT]
> 이 문서에서는 문제 해결 기술에 대해 자세히 설명하거나 논의하지 않습니다. 문제 해결 및 관련 프로세스는 복잡한 주제입니다. 문제 해결 기초 및 문제 해결 관련 작업에 대한 자세한 내용은 <A class=uri href="http://go.microsoft.com/fwlink/?linkid=211003%26clcid=0x412">http://go.microsoft.com/fwlink/?linkid=211003&amp;clcid=0x412</A>()에서 Microsoft Lync Server 2010 리소스 키트 문서를 참조하십시오. 프로세스와 절차는 계속 Lync Server 2013에 적용됩니다.



Lync Server 2013에는 일부 새로운 기능을 제공하는 업데이트 버전의 Snooper가 도입됩니다. 다음 스크린 샷은 Office Communications Server 2007의 Snooper 버전을 보여줍니다.

![Office Communications 2007 버전의 Snooper.](images/JJ721879.129503a8-8edd-4bb0-a68f-c43f9a548b93(OCS.15).jpg "Office Communications 2007 버전의 Snooper.")

다음 스크린 샷은 Lync Server 2013 Debug Tools에 포함된 새 Snooper 버전을 보여줍니다.

![Lync Server 2013 버전의 Snooper.](images/JJ721879.131495dd-8220-4ae4-af37-0ac5c318fd45(OCS.15).jpg "Lync Server 2013 버전의 Snooper.")

다음 스크린 샷은 자주 사용되는 기능이 포함된 도구 모음을 보여줍니다.

![Snooper 2013 도구 모음.](images/JJ721879.989249c5-a33e-4251-b8b4-411019cc12b2(OCS.15).jpg "Snooper 2013 도구 모음.")

또한 가치를 더 발하는 최신 기능으로는 순서도(또는 흐름) 다이어그램 보기가 있습니다. **Message(메시지)** 탭에서 메시지 흐름을 선택하고 **Call Flow(통화 흐름)** 단추를 클릭합니다. 메시지 간을 이동하면 통화 흐름 다이어그램이 새 데이터로 업데이트됩니다.

![Snooper 2013 통화 흐름 다이어그램.](images/JJ721879.bb8be45d-a842-48fe-86f8-380207d70bab(OCS.15).jpg "Snooper 2013 통화 흐름 다이어그램.")

다이어그램 보기에 마우스 커서를 놓으면 메시지에 대한 정보, 흐름 및 메시지의 구성 내용, 서버 요소 등을 볼 수 있습니다. 통화 흐름 화살표를 클릭하면 메시지 보기의 메시지로 이동합니다.

![통화 흐름 다이어그램 메시지 정보.](images/JJ721879.1147d720-38a9-4bda-8361-78f27ecde3d1(OCS.15).jpg "통화 흐름 다이어그램 메시지 정보.")

## Snooper에서 로그 파일을 열려면

1.  Snooper를 사용하여 로그 파일을 열려면 로그 파일에 대한 읽기 액세스 권한이 있어야 합니다. Snooper를 사용하여 로그 파일에 액세스하려면 CsAdministrator 또는 CsServerAdministrator RBAC(역할 기반 액세스 제어) 보안 그룹의 구성원이거나 이들 두 그룹 중 하나를 포함하는 사용자 지정 RBAC 역할의 구성원이어야 합니다.

2.  LyncDebugTools.msi를 사용하여 Lync Server Debugging Tools를 설치한 후 Windows 탐색기 또는 명령줄을 사용하여 Snooper.exe 위치로 이동합니다. 기본적으로 Debugging Tools는 C:\\Program Files\\Microsoft Lync Server 2013\\Debugging Tools에 위치합니다. Snooper.exe를 두 번 클릭하거나 실행합니다.

3.  Snooper가 열리면 **File(파일)**을 클릭하고 **OpenFile**을 클릭한 다음 **Open(열기)** 대화 상자에서 로그 파일을 찾아 선택한 후 **Open(열기)**을 클릭합니다.

4.  로그 파일의 **Trace(추적)** 메시지가 **Trace(추적)** 탭에 표시됩니다. **Messages(메시지)** 탭을 클릭하여 수집된 추적 메시지 내용을 봅니다.

## 통화 흐름 다이어그램을 표시하려면

1.  Snooper를 사용하여 로그 파일을 열려면 로그 파일에 대한 읽기 액세스 권한이 있어야 합니다. Snooper를 사용하여 로그 파일에 액세스하려면 CsAdministrator 또는 CsServerAdministrator RBAC(역할 기반 액세스 제어) 보안 그룹의 구성원이거나 이들 두 그룹 중 하나를 포함하는 사용자 지정 RBAC 역할의 구성원이어야 합니다.

2.  로그 파일을 열고 **Messages(메시지)** 탭을 클릭한 다음 메시지 보기에서 대화를 선택하거나, **Trace(추적)** 탭에서 추적 구성 요소를 선택합니다.

3.  **Call Flow(통화 흐름)**을 클릭합니다.
    

    > [!NOTE]
    > 통화 흐름의 일부가 아닌 메시지나 추적을 클릭하면 다이어그램이 나타나지 않고 "이 메시지는 통화 흐름에 적용되지 않습니다"와 같은 상태 메시지가 Snooper 아래에 나타납니다. 통화 흐름의 일부인 다른 메시지나 추적을 선택하면 통화 흐름이 나타납니다.



4.  메시지 또는 추적 줄 간을 이동하여 통화 흐름 다이어그램이 새로운 다이어그램을 표시하도록 업데이트 또는 변경되는지 확인합니다.

5.  통화 메시지, 끝점, 기타 구성 요소에 대한 정보를 확인하려면 요소 위에 마우스 커서를 놓습니다.

