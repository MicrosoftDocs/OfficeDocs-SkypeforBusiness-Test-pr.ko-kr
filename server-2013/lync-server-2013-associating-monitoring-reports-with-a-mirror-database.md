---
title: 모니터링 보고서와 미러 데이터베이스 연결
TOCTitle: 모니터링 보고서와 미러 데이터베이스 연결
ms:assetid: 42b797c6-8db8-4ad7-886e-8ddf8deb06f9
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/JJ945624(v=OCS.15)
ms:contentKeyID: 52056842
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# 모니터링 보고서와 미러 데이터베이스 연결

 

_**마지막으로 수정된 항목:** 2014-02-07_

모니터링 데이터베이스용 미러를 구성한 경우, 장애 조치(failover) 발생 시 해당 미러 데이터베이스가 기본 데이터베이스 역할을 맡습니다. 그러나 Lync Server 모니터링 보고서를 사용하는 경우 장애 조치(failover)가 발생하면 사용자의 모니터링 보고서가 미러 데이터베이스에 연결되지 않을 수 있습니다. 이는 모니터링 보고서를 설치할 때 기본 데이터베이스 위치만 지정하고 미러 데이터베이스 위치를 지정하지 않았기 때문입니다.

모니터링 보고서가 미러 데이터베이스에 대해 자동으로 장애 조치(failover)를 수행하도록 하려면 미러 데이터베이스를 모니터링 보고서가 사용하는 두 개의 데이터베이스(통화 정보 기록 데이터용 데이터베이스와 QoE(체감 품질) 데이터용 데이터베이스)에 "장애 조치(failover) 파트너"로 추가해야 합니다. 단, 이 단계는 모니터링 보고서를 설치한 후에 수행해야 합니다. 이 두 개의 데이터베이스에서 사용한 연결 문자열 값을 수동으로 편집하여 장애 조치(failover) 파트너 정보를 추가할 수 있습니다. 이렇게 하려면 다음 절차를 완료하세요.

1.  Internet Explorer를 사용하여 **SQL Server Reporting Services** 홈 페이지를 엽니다. Reporting Services 홈 페이지 URL에는 다음이 포함됩니다.
    
      - **http:** 접두사
    
      - Reporting Services가 설치되어 있는 컴퓨터의 FQDN(정규화된 도메인 이름)(예: **atl-sql-001.litwareinc.com**)
    
      - **/Reports\_** 문자열
    
      - 모니터링 보고서가 설치되어 있는 데이터베이스 인스턴스 이름(예: **archinst**)
    
    예를 들어 SQL Server Reporting Services가 atl-sql-001.litwareinc.com 컴퓨터에 설치되어 있고 모니터링 보고서가 데이터베이스 인스턴스 archinst를 사용하는 경우 홈 페이지 URL은 다음과 같이 표시됩니다.
    
    **http://atl-sql-001.litwareinc.com/Reports\_archinst**

2.  Reporting Services 홈 페이지에 액세스한 후에는 **LyncServerReports**를 클릭한 다음 **Reports\_Content**를 클릭합니다. 그러면 Lync Server 모니터링 보고서의 **Reports\_Content** 페이지로 이동합니다.

3.  **Reports\_Content** 페이지에서 **CDRDB** 데이터 원본을 클릭합니다.

4.  **CDRDB** 페이지의 **속성** 탭에서 **연결 문자열**이라는 이름의 텍스트 상자를 찾습니다. 현재 연결 문자열은 다음과 같이 표시됩니다.
    
    **Data source=(local)\\archinst;initial catalog=LcsCDR**

5.  미러 데이터베이스용 서버 이름 및 데이터베이스 인스턴스를 포함하도록 연결 문자열을 편집합니다. 예를 들어 서버 이름이 atl-mirror-001이고 미러 데이터베이스가 archinst 인스턴스에 있다면 다음 구문을 사용하여 미러 데이터베이스를 추가하여 지정합니다.
    
    **Failover Partner=atl-mirror-001\\archinst**
    
    편집한 연결 문자열은 다음과 같이 표시됩니다.
    
    **Data source=(local)\\archinst;Failover Partner=atl-mirror-001\\archinst;initial catalog=LcsCDR**

6.  연결 문자열을 업데이트한 후에는 **적용**을 클릭합니다.

7.  **CDRDB** 페이지에서 **Reports\_Content** 링크를 클릭합니다. **QMSDB** 데이터 원본을 클릭한 다음 QoE 데이터베이스에 대한 연결 문자열을 편집합니다. 편집한 문자열은 다음과 같습니다.
    
    **Data source=(local)\\archinst;Failover Partner=atl-mirror-001\\archinst;initial catalog=QoEMetrics**

8.  **적용**을 클릭합니다.

## 참고 항목

#### 개념

[Lync Server 2013 모니터링 보고서 설치](lync-server-2013-installing-lync-server-2013-monitoring-reports.md)  
[Lync Server 2013에서 모니터링 보고서 사용](lync-server-2013-using-monitoring-reports.md)

