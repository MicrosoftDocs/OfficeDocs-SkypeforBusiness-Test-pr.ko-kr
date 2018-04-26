---
title: 'Lync Server 2013: 위치 얻기'
TOCTitle: 위치 얻기
ms:assetid: 9bf069aa-d240-4d95-be3a-e795537f8e70
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/JJ205110(v=OCS.15)
ms:contentKeyID: 49304510
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Lync Server 2013에서 위치 얻기

 

_**마지막으로 수정된 항목:** 2012-06-06_

Lync Server 2013 E9-1-1 배포에서 내부적으로 연결된 각 Lync 또는 Lync Phone Edition 클라이언트는 자체 위치를 얻습니다. SIP 등록 후에 클라이언트는 자신에 대해 알게 된 모든 네트워크 연결 정보를 위치 요청에 포함하여, 복제된 SQL Server 데이터베이스를 기반으로 하는 웹 서비스인 위치 정보 서비스에 제공합니다. 각 중앙 사이트 풀에 있는 위치 정보 서비스는 이 네트워크 정보를 사용하여 레코드에서 일치하는 위치를 쿼리합니다. 일치 항목이 있는 경우 위치 정보 서비스가 클라이언트에 위치를 반환합니다. 일치 항목이 없는 경우 사용자에게 수동으로 위치를 입력하라는 메시지가 표시될 수 있습니다(위치 정책 설정에 따라 다름). 위치 데이터는 PIDF-LO(Presence Information Data Format Location Object)라는 IETF(Internet Engineering Task Force) 표준화 XML 형식으로 클라이언트에 다시 전송됩니다.

Lync Server 클라이언트에는 긴급 통화의 일부로 PIDF-LO 데이터가 포함됩니다. E9-1-1 서비스 공급자는 이 데이터를 사용하여 해당 PSAP를 확인하고 올바른 ESQK와 함께 이 PSAP로 통화를 라우팅하며, 이를 통해 PSAP 발송자가 발신자 위치를 얻을 수 있습니다.

다음 다이어그램에서는 Lync Server 클라이언트가 위치를 얻는 방법(타사 클라이언트 MAC 주소 기반으로 위치를 얻는 방법 제외)을 보여 줍니다.

![클라이언트가 위치를 가져오는 방법 다이어그램](images/JJ205110.4438f5fc-f1b2-444b-8565-09035363ed43(OCS.15).jpg "클라이언트가 위치를 가져오는 방법 다이어그램")

클라이언트가 위치를 얻도록 하려면 다음 단계를 수행해야 합니다.

1.  관리자가 네트워크 와이어맵(wiremap)으로 위치 정보 서비스 데이터베이스를 채웁니다. 네트워크 와이어맵은 다양한 유형의 네트워크 주소를 해당 ERL(Emergency Response Location)에 매핑하는 테이블입니다.

2.  SIP 트렁크 E9-1-1 서비스 공급자를 사용하는 경우 관리자는 E9-1-1 서비스 공급자가 유지 관리하는 MSAG(마스터 주소 가이드) 데이터베이스를 기준으로 ERL의 구/군/시 주소 부분이 올바른지 확인합니다. ELIN 게이트웨이를 사용하는 경우 관리자는 PSTN 통신사에서 ELIN을 ALI(Automatic Location Identification) 데이터베이스에 업로드했는지 확인합니다.

3.  등록 시 또는 네트워크 변경 시마다 내부적으로 연결된 클라이언트는 클라이언트에서 검색된 네트워크 주소가 포함된 위치 요청을 위치 정보 서비스에 전송합니다.

4.  위치 정보 서비스는 게시된 레코드에서 위치를 쿼리하고 일치 항목이 발견되면 해당 ERL을 PIDF-LO 형식으로 클라이언트에 반환합니다.

