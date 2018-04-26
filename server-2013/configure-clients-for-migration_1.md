---
title: 마이그레이션을 위한 클라이언트 구성
TOCTitle: 마이그레이션을 위한 클라이언트 구성
ms:assetid: 8f17862b-d9d1-47f6-b248-51f4710f5030
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/JJ688130(v=OCS.15)
ms:contentKeyID: 49885866
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# 마이그레이션을 위한 클라이언트 구성

 

_**마지막으로 수정된 항목:** 2015-03-09_

이 항목에는 Lync Server 2013으로 마이그레이션하기 전에 수행해야 하는 권장되는 클라이언트 배포 단계가 포함됩니다. 이러한 구성 변경은 Office Communications Server 2007 R2에서 수행해야 합니다. 이러한 단계는 마이그레이션 전에 수행해야 합니다. 자세한 내용은 [Lync Server 2013에서 클라이언트 및 장치 계획](lync-server-2013-planning-for-clients-and-devices.md)을 참조하십시오.

## 마이그레이션 전에 클라이언트를 구성하려면

1.  Office Communications Server 2007 R2에 대한 최신 서버, 클라이언트, 장치 업데이트(핫픽스)를 배포합니다.
    
      - [Office Communications Server 2007 R2 업데이트 적용](apply-office-communications-server-2007-r2-updates.md)
    
      - [Communicator 2007 R2용 누적 업데이트 패키지에 대한 설명](http://go.microsoft.com/fwlink/p/?linkid=335808)
    
      - [장치에 대한 소프트웨어 업데이트 가져오기](http://go.microsoft.com/fwlink/?linkid=335809)

2.  Office Communications Server 2007 R2에서는 클라이언트 버전 필터링을 사용하여 최신 업데이트가 포함된 Office Communications Server 2007 R2 클라이언트만 로그인하도록 허용할 수 있습니다.

3.  Office Communications Server 2007 R2에서는 클라이언트 버전 필터링을 사용하여 Lync Server 2013 클라이언트가 로그인할 수 없도록 차단합니다. **클라이언트 버전 필터링 구성** ( [http://go.microsoft.com/fwlink/?linkid=202488\&clcid=0x412](http://go.microsoft.com/fwlink/?linkid=202488%26clcid=0x412))에 설명된 단계에 따라 다음 표에 나열된 버전 필터를 추가합니다. 각 버전 필터에 대해 **차단** 동작을 지정합니다.
    
    
    <table>
    <colgroup>
    <col style="width: 33%" />
    <col style="width: 33%" />
    <col style="width: 33%" />
    </colgroup>
    <thead>
    <tr class="header">
    <th>클라이언트</th>
    <th>사용자 에이전트 헤더</th>
    <th>버전</th>
    </tr>
    </thead>
    <tbody>
    <tr class="odd">
    <td><p>Lync 2013</p></td>
    <td><p>OC</p></td>
    <td><p>15.*.*.*</p></td>
    </tr>
    <tr class="even">
    <td><p>Lync Web App</p></td>
    <td><p>CWA</p></td>
    <td><p>5.*.*.*</p></td>
    </tr>
    <tr class="odd">
    <td><p>Lync Phone Edition</p></td>
    <td><p>OCPhone</p></td>
    <td><p>4.*.*.*</p></td>
    </tr>
    </tbody>
    </table>

