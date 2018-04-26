---
title: Lync Server 2013에서 통화 대기 음악 사용자 지정
TOCTitle: Lync Server 2013에서 통화 대기 음악 사용자 지정
ms:assetid: 3d78e6f9-a4ae-49f4-a89f-4515acb49dac
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/JJ688031(v=OCS.15)
ms:contentKeyID: 49885733
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Lync Server 2013에서 통화 대기 음악 사용자 지정

 

_**마지막으로 수정된 항목:** 2012-09-10_

Lync Server 2013에 제공되는 기본 음악 파일 대신 대기 음악에 사용할 고유한 음악 파일을 지정할 수 있습니다. 대기 음악을 사용자 지정하려면 **Set-CsCallParkServiceMusicOnHoldFile** cmdlet을 사용합니다.


> [!NOTE]
> 통화 대기 음악을 사용자 지정하고 여러 사이트에 대해 같은 음악을 사용하려는 경우에는 통화 대기 응용 프로그램을 실행하는 각 사이트에 대해 음악 파일을 구성해야 합니다.



## 음악 파일을 사용자 지정하려면

1.  Lync Server 관리 셸이 설치된 컴퓨터에 RTCUniversalServerAdmins 그룹의 구성원으로 로그온하거나 [Lync Server 2013에서 설치 권한 위임](lync-server-2013-delegate-setup-permissions.md)에 설명된 대로 필요한 사용자 권한으로 로그온합니다.

2.  Lync Server 관리 셸 시작: **시작**, **모든 프로그램**, **Microsoft Lync Server 2013**을 차례로 클릭한 다음 **Lync Server 관리 셸**을 클릭합니다.

3.  다음을 실행합니다.
    
        Set-CsCallParkServiceMusicOnHoldFile -Service <ServiceID where the Call Park application resides> -Content <Byte[]>
    

    > [!TIP]
    > <STRONG>Get-CsService</STRONG> cmdlet을 사용하여 서비스를 식별합니다. 자세한 내용은 <A href="get-csservice.md">Get-CsService</A>를 참조하십시오.

    
    다음 예에서는 soothingmusic.wma 파일의 내용을 바이트 배열로 가져와서 변수에 지정하는 방법을 보여 줍니다. 그런 후에 오디오 파일은 통화 대기용 대기 음악 파일로 지정됩니다. 자세한 내용은 [Set-CsCallParkServiceMusicOnHoldFile](set-cscallparkservicemusiconholdfile.md)을 참조하십시오.
    
        $a = Get-Content -ReadCount 0 -Encoding byte "C:\MoHFiles\soothingmusic.wma"
        Set-CsCallParkServiceMusicOnHoldFile -Service Redmond1-applicationserver-1 -Content $a

## 참고 항목

#### 기타 리소스

[Set-CsCallParkServiceMusicOnHoldFile](set-cscallparkservicemusiconholdfile.md)  
[Get-CsService](get-csservice.md)

