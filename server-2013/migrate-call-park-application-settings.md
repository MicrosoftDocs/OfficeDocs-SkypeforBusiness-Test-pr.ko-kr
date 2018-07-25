---
title: 통화 대기 응용 프로그램 설정 마이그레이션
TOCTitle: 통화 대기 응용 프로그램 설정 마이그레이션
ms:assetid: 23b192d2-93ec-42a8-b175-b6ed502a2c35
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/JJ687993(v=OCS.15)
ms:contentKeyID: 49885682
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# 통화 대기 응용 프로그램 설정 마이그레이션

 

_**마지막으로 수정된 항목:** 2012-10-19_

Lync Server 2010에서 Lync Server 2013으로 통화 대기 응용 프로그램을 마이그레이션할 때는 Lync Server 2010에 업로드된 사용자 지정 대기 음악 파일을 사용하여 Lync Server 2013 풀을 프로비저닝하고, 서비스 수준 설정을 복원하고, 모든 통화 대기 파킹된 통화 번호의 대상을 Lync Server 2013 풀로 다시 지정합니다. Lync Server 2010 풀에서 사용자 지정된 대기 음악 파일이 구성된 경우에는 이러한 파일을 새 Lync Server 2013 풀로 복사해야 합니다. 또한 통화 대기 사용자 지정된 대기 음악 파일을 Lync Server 2010에서 다른 대상으로 백업하여 통화 대기용으로 업로드한 모든 사용자 지정된 대기 음악 파일의 별도 백업 복사본을 보관해야 합니다. 통화 대기 응용 프로그램용 사용자 지정된 대기 음악 파일은 풀의 파일 저장소에 저장됩니다. Lync Server 2010 풀 파일 저장소에서 Lync Server 2013 파일 저장소로 오디오 파일을 복사하려면 다음 매개 변수를 포함하여 **Xcopy** 명령을 사용합니다.

```
    Xcopy <Source: Lync Server 2010 Pool CPS File Store Path> <Destination: Lync Server 2013 Pool CPS File Store Path>
```
```
    Example usage:  Xcopy "<Lync Server 2010 File Store Path>\OcsFileStore\coX-ApplicationServer-X\AppServerFiles\CPS\"  "<Lync Server 2013 File Store Path>\OcsFileStore\coX-ApplicationServer-X\AppServerFiles\CPS\" 
```

사용자 지정된 모든 오디오 파일을 Lync Server 2013 파일 저장소로 복사한 후에는 Lync Server 2013 풀의 통화 대기 응용 프로그램 설정을 구성해야 하며, Lync Server 2010 풀에 연결된 통화 대기 파킹된 통화 번호 범위를 Lync Server 2013 풀에 다시 할당해야 합니다.

통화 대기 응용 프로그램 설정에는 선택 시간 제한 임계값, 대기 음악 사용/사용 안 함, 최대 통화 선택 시도 및 시간 제한 요청이 포함됩니다. Lync Server 관리 셸을 사용해 **Set-CsCpsConfiguration** cmdlet을 실행하여 통화 대기 응용 프로그램 설정을 관리해야 합니다. Lync Server 제어판을 사용하여 통화 대기 응용 프로그램 설정을 관리할 수는 없습니다.

**통화 대기 서비스 설정 다시 구성**

1.  Lync Server 2013 프런트 엔드 서버에서 Lync Server 관리 셸을 엽니다.

2.  명령줄에 다음을 입력합니다.
    

    > [!NOTE]  
    > Lync Server 2013 통화 대기 응용 프로그램 설정이 레거시 Lync Server 2010 설정과 동일한 경우에는 이 단계 실행을 건너뛰어도 됩니다. Lync Server 2013 및 Lync Server 2010 환경에서 통화 대기 응용 프로그램 설정이 서로 다른 경우에는 아래 cmdlet을 템플릿으로 사용하여 해당 변경 내용을 업데이트합니다.

    
        Set-CsCpsConfiguration -Identity "<LS2013 Call Park Service ID>" -CallPickupTimeoutThreshold "<LS2010 CPS TimeSpan>" -EnableMusicOnHold "<LS2010 CPS value>" -MaxCallPickupAttempts "<LS2010 CPS pickup attempts>" -OnTimeoutURI "<LS2010 CPS timeout URI>"

Lync Server 2010 풀에서 Lync Server 2013 풀로 모든 통화 대기 파킹된 통화 번호 범위를 다시 할당하려면 Lync Server 제어판 또는 Lync Server 관리 셸을 사용하면 됩니다.

**Lync Server 제어판을 사용하여 모든 통화 대기 파킹된 통화 번호 범위 다시 할당**

1.  Lync Server 제어판을 엽니다.

2.  왼쪽 창에서 **음성 기능**을 선택합니다.

3.  **통화 대기** 탭을 선택합니다.

4.  Lync Server 2010 풀에 할당된 각 통화 대기 파킹된 통화 번호 범위에 대해 **대상 서버 FQDN** 설정을 편집하고 통화 대기 요청을 처리할 Lync Server 2013 풀을 선택합니다.

5.  **커밋**을 선택하여 변경 내용을 저장합니다.

**Lync Server 관리 셸을 사용하여 모든 통화 대기 파킹된 통화 번호 범위 다시 할당**

1.  Lync Server 관리 셸을 엽니다.

2.  명령줄에 다음을 입력합니다.
    
        Get-CsCallParkOrbit
    
    이 cmdlet은 배포의 모든 통화 대기 파킹된 통화 번호 범위를 나열합니다. **CallParkServiceId** 및 **CallParkServerFqdn** 매개 변수가 Lync Server 2010 풀로 설정된 모든 통화 대기 파킹된 통화 번호를 다시 할당해야 합니다.
    
    Lync Server 2010 통화 대기 파킹된 통화 번호 범위를 Lync Server 2013 풀로 다시 할당하려면 명령줄에 다음을 입력합니다.
    
        Set-CsCallParkOrbit -Identity "<Call Park Orbit Identity>" -CallParkService "service:ApplicationServer:<Lync Server 2013 Pool FQDN>"

모든 통화 대기 파킹된 통화 번호 범위를 Lync Server 2013 풀로 다시 할당하고 나면 통화 대기 응용 프로그램 마이그레이션 프로세스가 완료되며 Lync Server 2013 풀에서 이후의 모든 통화 대기 요청을 처리합니다.

