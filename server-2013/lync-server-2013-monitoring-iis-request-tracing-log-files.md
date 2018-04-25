---
title: IIS 요청 추적 로그 파일 모니터링
TOCTitle: IIS 요청 추적 로그 파일 모니터링
ms:assetid: b6730e92-6d74-4fa7-a83f-50b7bdadbffa
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Hh690034(v=OCS.15)
ms:contentKeyID: 49304794
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# IIS 요청 추적 로그 파일 모니터링

 

_**마지막으로 수정된 항목:** 2013-02-14_

Lync Server Mobility Service에 대해 IIS(인터넷 정보 서비스) 요청 추적을 사용하도록 설정하면 생성되는 로그 파일이 매일 디스크 공간을 3GB까지 사용할 수 있습니다. IIS 추적 로깅은 기본적으로 사용하도록 설정됩니다. 프런트 엔드 서버를 모니터링하여 디스크 공간 부족 현상이 발생하지 않는지 확인해야 합니다.

IIS에서는 로그 파일이 기본적으로 %SystemDrive%\\inetpub\\logs\\LogFiles에 저장됩니다.

전체 서버에 대해 IIS 요청 추적을 해제하려면 명령줄에서 다음을 입력합니다.

    %SystemDrive%\Windows\System32\inetsrv\appcmd set config /section:httpLogging /dontLog:True

**httpLogging** 명령에 대한 자세한 내용은 [http://go.microsoft.com/fwlink/?linkid=234927\&clcid=0x412](http://go.microsoft.com/fwlink/?linkid=234927%26clcid=0x412)를 참조하십시오.

