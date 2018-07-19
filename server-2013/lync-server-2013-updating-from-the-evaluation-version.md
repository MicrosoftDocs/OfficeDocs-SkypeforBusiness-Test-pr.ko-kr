---
title: Microsoft Lync Server 2013 평가 버전에서 업데이트
TOCTitle: Microsoft Lync Server 2013 평가 버전에서 업데이트
ms:assetid: 62a88180-4289-4a2a-9cb9-1b9899344a63
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg521005(v=OCS.15)
ms:contentKeyID: 49303824
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Microsoft Lync Server 2013 평가 버전에서 업데이트

 

_**마지막으로 수정된 항목:** 2012-06-20_

Microsoft Lync Server 2013의 평가판 버전을 설치한 경우에는 해당 설치를 정식 버전 소프트웨어로 업데이트해야 합니다. 평가판 버전은 설치 180일 후에 만료되기 때문입니다. 그러나 평가판 버전을 완전히 제거하고 정식 버전을 설치할 필요는 없습니다. 대신, 유효한 라이선스 키를 얻은 후에 Lync Server프런트 엔드 서버, 디렉터 또는 에지 서버로 사용되는 각 컴퓨터에서 다음 절차를 수행하여 Lync Server 2013의 평가판 버전을 업데이트할 수 있습니다. 모니터링 서버, 보관 서버 등 기타 서버 역할을 수행하는 컴퓨터는 업데이트하지 않아도 됩니다.

## Microsoft Lync Server 2013 평가판 버전에서 업데이트

컴퓨터에 설치된 Lync Server 2013을 평가판 버전에서 정식 버전 소프트웨어로 업데이트하려면

**Microsoft Lync Server 2013 평가판 버전에서 업데이트**

1.  로컬 관리자로 컴퓨터에 로그온합니다.

2.  **시작**, **모든 프로그램**, **Microsoft Lync Server 2013**, **Lync Server 관리 셸**을 차례로 클릭합니다.

3.  Lync Server 관리 셸에 다음 명령을 입력하고 Enter 키를 누릅니다.
    
        msiexec.exe /fvomus server.msi EVALTOFULL=1 /qb
    
    server.msi 파일의 전체 경로를 지정해야 할 수 있습니다. 이 파일은 Lync Server 볼륨 미디어 설치 파일의 Setup 폴더에 있습니다.

4.  설치 실행이 완료되면 명령 프롬프트에 다음을 입력하고 Enter 키를 누릅니다.
    
        Enable-CsComputer

5.  Lync Server의 평가판 버전을 실행하는 기타 프런트 엔드 서버, 디렉터 또는 에지 서버에서 이 절차를 반복합니다. 또한 Lync Server 미디어 설치 파일을 사용하여 배포된 지점 서버에서도 이 절차를 수행해야 합니다.

특정 컴퓨터에서 Lync Server의 평가판 버전을 실행하고 있는지 확실치 않으면 Lync Server 관리 셸 내에서 다음 명령을 실행하여 확인할 수 있습니다.

    Get-CsServerVersion

[Get-CsServerVersion](https://docs.microsoft.com/en-us/powershell/module/skype/Get-CsServerVersion) cmdlet은 로컬 컴퓨터를 분석하여 다음 중 하나를 보고합니다.

  - Lync Server 볼륨 라이선스 키가 컴퓨터에 설치되어 있음(업데이트가 필요하지 않음)

  - Lync Server 평가판 라이선스 키가 설치되어 있음(컴퓨터를 업데이트해야 함)

  - 해당 볼륨 라이센스 키는 컴퓨터에 필요하지 않습니다. 프런트 엔드 서버, 디렉터 및 에지 서버만 평가판 버전에서 정식 버전으로 업데이트하면 됩니다.

