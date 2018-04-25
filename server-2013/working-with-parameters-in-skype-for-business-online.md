---
title: 매개 변수 사용
TOCTitle: 매개 변수 사용
ms:assetid: 29ebda0f-ae5f-4512-ad59-240c3605b240
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Dn362778(v=OCS.15)
ms:contentKeyID: 56270222
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# 매개 변수 사용

 

_**마지막으로 수정된 항목:** 2015-06-22_

Identity 매개 변수를 사용하는 경우 매개 변수 값 kenmyer@litwareinc.com은 큰따옴표로 묶여 있습니다.

    -Identity "kenmyer@litwareinc.com"

Windows PowerShell을 처음 사용하는 사람이 예외없이 묻는 질문 중 하나는 큰따옴표를 사용해야 할 때와 사용하지 않아야 할 때에 관한 것입니다. 이 질문에 대한 명확한 답은 없지만 몇 가지 일반적인 규칙이 있습니다.

  - 일반적으로 매개 변수 값이 숫자인 경우 큰따옴표는 필요하지 않습니다. 예를 들어 [Get-CsOnlineUser](get-csonlineuser.md) cmdlet에 의해 반환되는 사용자 수를 제한하려면 다음 구문을 사용합니다.
    
        -ResultSize 100
    
    사실 숫자를 큰따옴표로 묶어서는 안 됩니다. 숫자를 큰따옴표로 묶은 경우 Windows PowerShell에서 해당 값을 숫자로 인식하기 어려울 수 있습니다.
    
    마찬가지로 숫자에 쉼표가 포함되지 않도록 합니다. 예를 들어 결과 크기를 10,000으로 설정하려는 경우 다음 구문은 잘못되었습니다.
    
        -ResultSize 10,000
    
    Windows PowerShell에서는 인수 값을 구분하는 방법으로 쉼표를 사용하므로 위 구문을 사용하면 오류가 발생합니다. 이 경우 Windows PowerShell에서는 서로 다른 두 매개 변수 값(10 및 000)을 전달하는 것으로 간주됩니다. 결과 크기를 동시에 10과 0으로 설정할 수 없으므로 오류가 발생합니다. 다음과 같이 쉼표가 없는 구문을 사용하세요.
    
        -ResultSize 10000

  - 매개 변수 값이 날짜인 경우에도 일반적으로 큰따옴표가 필요하지 않습니다.
    
        -StartDate 6/1/2013
    
    하지만 이는 시간이 포함되지 않은 경우에만 적용됩니다. 시간을 포함한 경우 즉, 날짜와 시간 사이에 공백을 삽입한 경우에는 매개 변수 값을 큰따옴표로 묶어야 합니다.
    
        -StartDate "6/1/2013 10:00AM"
    
    위의 명령 형식은 지역 설정으로 영어(미국)를 사용하는 컴퓨터를 기준으로 지정되어 있습니다. 영어(미국)를 사용하지 않는 경우 사용자의 컴퓨터 설정을 기반으로 날짜 및 시간 형식을 지정해야 합니다. Windows PowerShell에서 사용되는 지역 설정을 확인하려면 Windows PowerShell 프롬프트에서 다음 명령을 실행합니다.
    
        Get-Host | Select-Object CurrentUICulture

  - 사람 이름과 같은 문자열 값에는 일반적으로 큰따옴표가 필요하지 않습니다. 하지만 해당 문자열 값에 공백, 쉼표 또는 기타 문장 부호 등의 제한 문자가 포함된 경우는 예외입니다. 예를 들어 다음 구문은 사용자의 ID에 제한 문자가 포함되지 않으므로 제대로 작동합니다.
    
        -Identity "kenmyer@litwareinc.com"
    
    하지만 다음 명령은 ID에 공백이 포함되므로 실패합니다.
    
        -Identity Ken Myer
    
    Windows PowerShell에서는 공백을 사용하여 개별 매개 변수를 구분하므로 위 명령은 실패합니다. 즉, Windows PowerShell에서는 Identity 매개 변수를 Ken으로 인식하고 Myer를 새로운 매개 변수로 인식하므로 다음과 같은 오류 메시지를 반환합니다.
    
        Get-CsOnlineUser : 'Myer' 인수를 허용하는 위치 매개 변수를 찾을 수 없습니다..
    
    공백(또는 쉼표 또는 다른 제한 문자)을 포함하는 매개 변수 값을 사용하려면 해당 값을 큰따옴표로 묶습니다.
    
        -Identity "Ken Myer"
    
    대부분의 경우 Windows PowerShell에서는 큰따옴표 대신 작은따옴표를 사용할 수 있습니다. 예를 들어 다음 Windows PowerShell 구문은 유효합니다.
    
        -Identity 'Ken Myer'
    
    하지만 다음 Windows PowerShell 구문은 유효하지 않습니다.
    
        -Identity "Ken Myer'
    
    이 명령을 실행하려고 하면 Windows PowerShell 콘솔에서 다음과 같이 표시됩니다.
    
    ``` 
    >>
    ```
    
    Windows PowerShell에서 양방향 화살표는 명령을 완료하도록 요청하는 표시이며 큰따옴표로 시작하였으므로 큰따옴표로 마쳐야 합니다. \>\> 프롬프트가 표시되면 Ctrl-C를 눌러 명령을 취소하고 다시 시도하세요.

  - 큰따옴표는 부울(True/False) 값과 함께 사용할 수 없습니다. True/False 값을 지정할 때는 Windows PowerShell 변수 $True 및 $False를 사용해야 합니다. 예를 들면 다음과 같습니다.
    
        -EnterpriseVoiceEnabled $True

매개 변수 값을 허용하지 않는 *스위치 매개 변수*로 알려진 특정 Windows PowerShell 매개 변수도 있습니다.

    -WhatIf

스위치 매개 변수를 사용하는 경우 매개 변수 값이 필요하지 않으며, 실제로 매개 변수 값을 포함하면 오류가 발생합니다. 예를 들어 다음 명령을 실행하려는 경우를 살펴보겠습니다.

    -WhatIf $True

이 명령은 실패하며 다음과 비슷한 오류 메시지가 표시됩니다.

    Set-CsUserAcp : 'True' 인수를 허용하는 위치 매개 변수를 찾을 수 없습니다.

Windows PowerShell을 사용하여 비즈니스용 Skype Online을 관리하려면 사용할 수 있는 cmdlet에 대해 알아야 합니다. 또한 각 cmdlet에 사용할 수 있는 매개 변수 및 각 매개 변수의 *데이터 형식*(즉, 매개 변수가 데이터 값, 문자열 값, 숫자 등을 포함하는지 여부)도 알아야 합니다. 이러한 정보 및 cmdlet 사용 방법에 대한 여러 예제는 비즈니스용 Skype Online cmdlet에 대한 도움말 항목에서 찾을 수 있습니다. 예를 들어 [Set-CsTenantPublicProvider](set-cstenantpublicprovider.md) cmdlet에 사용할 수 있는 매개 변수는 다음과 같습니다.

![특정 PowerShell cmdlet의 매개 변수](images/Dn362778.ead7add1-eec3-4fa4-8bbe-9aa72bb7a1ae(OCS.15).png "특정 PowerShell cmdlet의 매개 변수")

보다시피 매개 변수 표에는 cmdlet에 대한 설명, 매개 변수가 필수인지 선택 사항인지 여부, 각 매개 변수의 데이터 형식이 나타나 있습니다. 표에 나타난 데이터 형식은 .NET Framework에서 사용되는 공식 데이터 형식입니다. 이는 데이터 형식이 단순히 Switch Parameter가 아닌 System.Management.Automation.SwitchParameter로 표시된다는 것을 의미합니다. 다음은 비즈니스용 Skype Online cmdlet에서 가장 일반적으로 사용되는 데이터 형식에 대한 빠른 가이드입니다.


<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th>매개 변수</th>
<th>설명</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Microsoft.Rtc.Management.AD.UserIdParameter</p></td>
<td><p>사용자의 ID를 나타내는 문자열 값입니다. 일반적으로 사용자의 UPN 또는 SIP 주소입니다.</p>
<pre><code>-Identity &quot;kenmyer@litwareinc.com&quot;</code></pre></td>
</tr>
<tr class="even">
<td><p>Microsoft.Rtc.Management.Deploy.Fqdn</p></td>
<td><p>FQDN은 정규화된 도메인 이름입니다. 예를 들면 다음과 같습니다.</p>
<pre><code>-Fqdn &quot;atl-lync-001.litwareinc.com&quot;</code></pre></td>
</tr>
<tr class="odd">
<td><p>System.Boolean</p></td>
<td><p>부울 값은 True/False 값입니다. 부울 값을 지정할 때는 Windows PowerShell 변수 $True 및 $False를 사용해야 합니다.</p>
<pre><code>-Enabled $True -EnterpriseVoiceEnabled $False</code></pre></td>
</tr>
<tr class="even">
<td><p>System.Guid</p></td>
<td><p>GUID는 <em>Globally Unique Identifier</em>의 약어이며 비즈니스용 Skype Online에서 각 비즈니스용 Skype Online 테넌트에 할당된 고유 식별자입니다. 예를 들면 다음과 같습니다.</p>
<pre><code>-Tenant &quot;38aad667-af54-4397-aaa7-e94c79ec2308&quot;</code></pre>
<p>다음 명령을 사용하여 비즈니스용 Skype Online 테넌트에 할당된 GUID를 검색할 수 있습니다.</p>
<pre><code>Get-CsTenant | Select-Object TenantId</code></pre></td>
</tr>
<tr class="odd">
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>스위치 매개 변수는 사용하거나 사용하지 않을 수 있기 때문에 붙여진 이름입니다. 다시 말해서, 해당 매개 변수가 있으면 이를 사용하고, 없으면 사용하지 않습니다. 예를 들어 명령을 실행하기 전 확인할 것을 요구하기 위해 Confirm 매개 변수를 사용하려면, 해당 명령에 Confirm 매개 변수(매개 변수 값은 없음)를 포함합니다. 예를 들면 다음과 같습니다.</p>
<pre><code>Remove-CsUserAcp -Identity &quot;Ken Myer&quot; -Confirm</code></pre>
<p>확인을 요구하지 않으려면 Confirm 매개 변수를 포함하지 않습니다.</p>
<pre><code>Remove-CsUserAcp -Identity &quot;Ken Myer&quot;</code></pre></td>
</tr>
<tr class="even">
<td><p>System.String</p></td>
<td><p>문자열 값은 영숫자 값입니다. 즉, 일반적으로 키보드에서 입력할 수 있는 모든 문자가 포함됩니다. 예를 들면 다음과 같습니다.</p>
<pre><code>-Password &quot;abc123%&amp;*&quot;</code></pre>
<p>문자열 값을 큰따옴표로 묶는 것이 좋습니다. 항상 필요하지는 않지만 문자열 값에 공백 또는 쉼표가 포함되거나 예약된 Windows PowerShell 키워드인 경우에는 큰따옴표가 필요합니다. 키워드는 Windows PowerShell 언어 자체의 일부인 명령 또는 기타 요소입니다. 예를 들어 &quot;If&quot; 및 &quot;End&quot;는 모두 Windows PowerShell 키워드입니다. 자세한 내용은 Windows PowerShell 명령 프롬프트에서 다음 명령을 입력해 보세요.</p>
<p>Get-Help about_Reserved_Words</p></td>
</tr>
</tbody>
</table>


## 참고 항목

#### 개념

[Windows PowerShell 및 Lync Online 소개](an-introduction-to-windows-powershell-and-skype-for-business-online.md)

