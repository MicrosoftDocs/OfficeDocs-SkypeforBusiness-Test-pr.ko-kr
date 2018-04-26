---
title: Lync Server 2013에서 조직의 장치에 대한 소프트웨어 업데이트 보기
TOCTitle: Lync Server 2013에서 조직의 장치에 대한 소프트웨어 업데이트 보기
ms:assetid: d2cca12b-ed43-4e1f-90ab-d14bca8b482c
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg182592(v=OCS.15)
ms:contentKeyID: 49305117
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Lync Server 2013에서 조직의 장치에 대한 소프트웨어 업데이트 보기

 

_**마지막으로 수정된 항목:** 2012-11-01_

Lync Server 2013에서는 장치 업데이트 웹 서비스를 사용하여 조직의 장치에 대한 소프트웨어 업데이트를 보고 관리할 수 있습니다. 이 업데이트는 Microsoft 고객지원 웹 사이트([http://go.microsoft.com/fwlink/?linkid=204091\&clcid=0x412](http://go.microsoft.com/fwlink/?linkid=204091%26clcid=0x412))의 .cab(캐비넷) 파일에 있습니다. .cab 파일을 다운로드했으면 **Import-CSdeviceUpdate** cmdlet을 사용하여 .cab 파일에서 장치 업데이트 규칙을 가져옵니다. **Import-CSdeviceUpdate** cmdlet에 대한 자세한 내용은 Lync Server 관리 셸 설명서에서 [Import-CsDeviceUpdate](import-csdeviceupdate.md)를 참조하십시오.


> [!TIP]
> 조직에 새 업데이트를 배포하기 전에 테스트 장치에서 이 업데이트가 제대로 작동하는지 확인합니다.



## UC 장치에 대한 소프트웨어 업데이트를 보려면

1.  CsUserAdministrator 역할 또는 CsAdministrator 역할에 할당된 사용자 계정에서 내부 배포된 컴퓨터에 로그온합니다.

2.  Microsoft 고객 지원 웹 사이트([http://go.microsoft.com/fwlink/?linkid=204091\&clcid=0x412](http://go.microsoft.com/fwlink/?linkid=204091%26clcid=0x412))에서 Lync Server 2013 컴퓨터의 해당 위치에 .cab 파일을 다운로드합니다(예: C:\\Updates\\UCUpdates.cab).

3.  다음 cmdlet 중 하나를 실행하여 C:\\Updates\\UCUpdates.cab 파일에서 장치 업데이트 규칙을 가져옵니다.
    
      - .cab 파일이 업데이트할 서비스(service:Redmond-websvc-2)가 실행되는 컴퓨터와 동일한 컴퓨터에 있는 경우 다음 cmdlet를 실행합니다.
        
            Import-CsDeviceUpdate -Identity service:Redmond-websvc-2 -FileName C:\Updates\UCUpdates.cab
    
      - .cab 파일이 업데이트할 서비스(service:Redmond-websvc-3)가 실행되는 컴퓨터가 아닌 다른 컴퓨터에 있는 경우에는 다음 cmdlet를 실행합니다.
        
            Import-CsDeviceUpdate -Identity service:Redmond-websvc-3 -ByteInput C:\Updates\UCUpdates.cab

4.  브라우저 창을 연 다음 Admin URL을 입력하여 Lync Server 제어판을 엽니다. Lync Server 제어판을 시작하는 데 사용할 수 있는 다양한 방법에 대한 자세한 내용은 [Lync Server 관리 도구 열기](lync-server-2013-open-lync-server-administrative-tools.md)를 참조하세요.

5.  왼쪽 탐색 표시줄에서 **클라이언트**, **장치 업데이트**를 차례로 클릭합니다.

6.  **장치 업데이트** 페이지의 목록에서 업데이트를 클릭하고 다음 중 하나를 수행합니다.
    
      - **대기 중인 업데이트 취소.** 선택한 업데이트가 조직의 장치에 배포되지 않도록 제한하려면 **동작** 메뉴에서 **대기 중인 업데이트 취소**를 클릭합니다.
    
      - **업데이트 승인.** 선택한 업데이트가 조직의 장치에 배포되도록 허용하려면 **동작** 메뉴에서 **승인**을 클릭합니다.
    
      - **업데이트 복원.** 이전에 승인된 업데이트를 조직의 장치에 배포하도록 허용하려면 **동작** 메뉴에서 **복원**을 클릭합니다.

## 참고 항목

#### 기타 리소스

[Lync Server 2013에서 장치, 전화 및 클라이언트 응용 프로그램 관리](lync-server-2013-managing-devices-phones-and-client-applications.md)

