---
title: Lync Server 2013에서 음성 경로 만들기
TOCTitle: Lync Server 2013에서 음성 경로 만들기
ms:assetid: d189057d-cc9d-4622-9d10-f5385d703faf
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg398898(v=OCS.15)
ms:contentKeyID: 49305115
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Lync Server 2013에서 음성 경로 만들기

 

_**마지막으로 수정된 항목:** 2012-11-01_

다음 절차에서는 Lync Server 2013 제어판을 사용하여 새 음성 경로를 만드는 방법에 대해 설명합니다. 기존의 경로를 편집하려면 [Lync Server 2013에서 음성 경로 수정](lync-server-2013-modify-a-voice-route.md)의 절차를 참조하십시오.

## Lync Server 제어판을 사용하여 음성 경로를 만들려면

1.  RTCUniversalServerAdmins 그룹의 구성원이나 **CsVoiceAdministrator**, **CsServerAdministrator** 또는 **CsAdministrator** 관리 역할의 구성원으로 컴퓨터에 로그온합니다.

2.  브라우저 창을 연 다음 Admin URL을 입력하여 Lync Server 제어판을 엽니다. Lync Server 제어판을 시작하는 데 사용할 수 있는 다양한 방법에 대한 자세한 내용은 [Lync Server 관리 도구 열기](lync-server-2013-open-lync-server-administrative-tools.md)를 참조하세요.

3.  왼쪽 탐색 모음에서 **음성 라우팅**을 클릭합니다.

4.  **경로**를 클릭합니다.

5.  **새로 만들기**를 클릭하여 **새 음성 경로** 대화 상자를 표시합니다.

6.  **이름**에 음성 경로에 대한 설명적 이름을 입력합니다.

7.  (선택 사항) **설명**에 음성 경로에 대한 추가 설명 정보를 입력합니다.

8.  이 경로에 사용할 패턴을 지정하려면 **일치시킬 패턴 작성** 도구를 사용하여 정규식을 생성하거나 정규식을 수동으로 작성합니다.
    
      - **일치시킬 패턴 작성** 도구를 사용하여 정규식을 생성하려면 다음과 같이 값을 입력합니다. 두 가지 유형의 패턴 일치를 지정할 수 있습니다.
        
          - **허용할 번호의 시작 숫자:** 이 경로에 사용할 접두사 값을 입력합니다(필요한 경우 앞에 + 포함). 예를 들어 **+425**를 입력한 다음 **추가**를 클릭합니다. 경로에 포함할 각 접두사 값에 대해 이 단계를 반복합니다.
        
          - **예외:** 접두사 값에 대해 하나 이상의 예외를 지정하려면 접두사를 강조 표시하고 **예외**를 클릭합니다. 이 경로에 포함하지 *않을* 일치 패턴에 대해 하나 이상의 값을 입력합니다. 예를 들어 +425237로 시작하는 숫자를 경로에서 제외하려면 **예외** 필드에 값 **+425237**을 입력한 다음 **확인**을 클릭합니다.
    
      - 일치하는 패턴을 수동으로 정의하려면 **일치시킬 패턴 작성** 도구에서 **편집**을 클릭한 다음 .NET Framework 정규식을 입력하여 경로를 적용할 대상 전화 번호의 일치하는 패턴을 지정합니다. 정규식을 작성하는 방법에 대한 자세한 내용은 [http://go.microsoft.com/fwlink/?linkid=140927\&clcid=0x412](http://go.microsoft.com/fwlink/?linkid=140927%26clcid=0x412)에서 ".NET Framework 정규식"을 참조하십시오.

9.  아웃바운드 전화를 거는 전화의 번호를 통화 수신자에게 표시하지 않으려면 **발신자 번호 표시 안 함**을 선택합니다. 이 옵션을 선택하는 경우 수신자의 발신자 번호 화면에 표시할 **대체 발신자 번호**를 지정해야 합니다.

10. 하나 이상의 트렁크를 음성 경로와 연결하려면 **추가**를 클릭한 다음 목록에서 트렁크를 선택합니다.
    

    > [!NOTE]
    > 배포에 Microsoft Office Communications Server 2007 R2 중재 서버가 포함된 경우 이러한 서버도 목록에 표시됩니다.



11. 하나 이상의 PSTN 사용 레코드를 음성 경로와 연결하려면 **선택**을 클릭하고 Enterprise Voice 배포에 대해 정의된 PSTN(공중 전화망) 사용 레코드 목록에서 레코드를 선택합니다.
    

    > [!NOTE]
    > 사용 가능한 각 PSTN 사용 레코드의 속성을 보려면 <A href="lync-server-2013-view-pstn-usage-records.md">Lync Server 2013에서 PSTN 사용 레코드 보기</A>를 참조하십시오.<BR>PSTN 사용 레코드를 만들거나 편집하려면 <A href="lync-server-2013-create-a-voice-policy-and-configure-pstn-usage-records.md">Lync Server 2013에서 음성 정책 수정 및 PSTN 사용 레코드 만들기</A> 또는 <A href="lync-server-2013-modify-a-voice-policy-and-configure-pstn-usage-records.md">Lync Server 2013에서 음성 정책 수정 및 PSTN 사용 레코드 구성</A>을 참조하십시오.



12. 최적의 성능을 유지하도록 PSTN 사용 레코드를 정렬합니다. 목록에서 레코드의 위치를 변경하려면 레코드 이름을 강조 표시하고 위쪽 또는 아래쪽 화살표를 클릭합니다.
    

    > [!NOTE]
    > PSTN 사용 레코드가 나열되는 순서가 중요한 음성 정책과 달리, 음성 경로에서는 PSTN 사용 레코드가 나열되는 순서가 중요하지 않습니다. 그러나 사용 빈도별로 목록을 구성하는 것이 좋습니다(예: RedmondLocal, RedmondLongDist, RedmondInternational, RedmondBackup). 참고로, Lync Server는 목록을 위에서 아래로 통과합니다.



13. (선택 사항) **테스트할 변환된 번호 입력** 필드에 값을 입력하고 **이동**을 클릭합니다. 테스트 결과가 필드 아래에 표시됩니다.
    

    > [!NOTE]
    > 아직 테스트를 통과하지 않은 음성 경로를 저장한 다음 나중에 다시 구성할 수 있습니다. 자세한 내용은 <A href="lync-server-2013-test-voice-routing.md">Lync Server 2013에서 음성 라우팅 테스트</A>를 참조하십시오.



14. **확인**을 클릭하여 음성 경로를 저장합니다.


> [!IMPORTANT]
> 음성 경로를 만들 때마다 <STRONG>모두 커밋</STRONG> 명령을 실행하여 구성 변경을 게시해야 합니다. 자세한 내용은 <A href="lync-server-2013-publish-pending-changes-to-the-voice-routing-configuration.md">Lync Server 2013에서 음성 라우팅 구성에 보류 중인 변경 사항 게시</A>를 참조하십시오.



## 참고 항목

#### 작업

[Lync Server 2013에서 음성 경로 수정](lync-server-2013-modify-a-voice-route.md)  
[Lync Server 2013에서 PSTN 사용 레코드 보기](lync-server-2013-view-pstn-usage-records.md)  
[Lync Server 2013에서 음성 정책 수정 및 PSTN 사용 레코드 만들기](lync-server-2013-create-a-voice-policy-and-configure-pstn-usage-records.md)  
[Lync Server 2013에서 음성 정책 수정 및 PSTN 사용 레코드 구성](lync-server-2013-modify-a-voice-policy-and-configure-pstn-usage-records.md)  
[Lync Server 2013에서 음성 라우팅 구성에 보류 중인 변경 사항 게시](lync-server-2013-publish-pending-changes-to-the-voice-routing-configuration.md)  

#### 기타 리소스

[Lync Server 2013에서 음성 라우팅 테스트](lync-server-2013-test-voice-routing.md)

