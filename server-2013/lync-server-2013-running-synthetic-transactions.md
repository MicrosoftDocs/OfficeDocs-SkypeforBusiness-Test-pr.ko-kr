---
title: 'Lync Server 2013: Running synthetic transactions'
TOCTitle: Running synthetic transactions
ms:assetid: 2b56c7bd-8956-4fa1-8232-1876b959b258
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Dn720911(v=OCS.15)
ms:contentKeyID: 62240113
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Running synthetic transactions in Lync Server 2013

 

_**마지막으로 수정된 항목:** 2014-08-18_

Synthetic transactions are typically conducted in two ways. You can use the CsHealthMonitoringConfiguration cmdlets to set up test users for each of their Registrar pools. These test users are a pair of users who were preconfigured for use with synthetic transactions. (Typically these are test accounts and not accounts that belong to actual users.) With test users configured for a pool, you can run a synthetic transaction against that pool without having to specify the identities of (and supply the credentials for) the user accounts involved in the test.

Or, you can run a synthetic transaction by using actual user accounts. For example, if two users cannot exchange instant messages, you could run a synthetic transaction using those two user accounts (instead of a pair of test accounts), and then try to diagnose and resolve the issue. If you decide to conduct a synthetic transaction using actual user accounts, you must supply the logon names and passwords for each user.

## 참고 항목

#### 개념

[감시자 노드 테스트 사용자 및 구성 설정 구성](lync-server-2013-configuring-watcher-node-test-users-and-configuration-settings.md)  
[가상 트랜잭션에 대한 특별 설치 지침](lync-server-2013-special-setup-instructions-for-synthetic-transactions.md)

