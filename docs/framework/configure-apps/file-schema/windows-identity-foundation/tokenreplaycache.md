---
title: <tokenReplayCache>
ms.date: 03/30/2017
ms.assetid: 1572ab23-6933-41b5-bfb4-0c4548145500
author: BrucePerlerMS
ms.openlocfilehash: 9f3a95fd0a39f199eaf13c7509aff22caa0e3b66
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/06/2020
ms.locfileid: "70251780"
---
# \<tokenReplayCache>
서비스 또는 보안 토큰 처리기 컬렉션을 사용 하 여 토큰 재생 캐시를 등록 합니다.  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.identityModel>**](system-identitymodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<identityConfiguration>**](identityconfiguration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<caches>**](caches.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<tokenReplayCache>**  
  
## <a name="syntax"></a>구문  
  
```xml  
<system.identityModel>  
  <identityConfiguration>  
    <caches>  
      <tokenReplayCache type=xs:string>  
      </tokenReplayCache>  
    </caches>  
  </identityConfiguration>  
</system.identityModel>  
```  
  
## <a name="attributes-and-elements"></a>특성 및 요소  
 다음 섹션에서는 특성, 자식 요소 및 부모 요소에 대해 설명합니다.  
  
### <a name="attributes"></a>특성  
  
|attribute|Description|  
|---------------|-----------------|  
|type|클래스에서 파생 되는 형식 <xref:System.IdentityModel.Tokens.TokenReplayCache> 입니다. 사용자 지정을 지정 하는 방법에 대 한 자세한 내용은 `type` [사용자 지정 형식 참조]를 참조 하세요.
  
### <a name="child-elements"></a>자식 요소  
 None  
  
### <a name="parent-elements"></a>부모 요소  
  
|요소|Description|  
|-------------|-----------------|  
|[\<caches>](caches.md)|서비스 또는 보안 토큰 처리기 컬렉션에서 사용 하는 캐시를 등록 합니다.|  
  
## <a name="remarks"></a>설명  
 토큰 재생 캐시는 재생 된 토큰을 검색 하는 데 사용 됩니다. 토큰 재생 검색은 토큰 [\<tokenReplayDetection>](tokenreplaydetection.md) 의 최대 만료 시간을 지정 하는 요소에 의해 사용 하도록 설정 됩니다.  
  
## <a name="example"></a>예제  
 다음 XML에서는 재생 된 토큰을 검색 하기 위한 사용자 지정 캐시의 구성을 보여 줍니다.  
  
```xml  
<caches>  
  <tokenReplayCache type="MyCacheLibrary.MyTokenReplayCache, MyCacheLibrary">  
  </tokenReplayCache>  
</caches>  
```  
  
## <a name="see-also"></a>참고 항목

- <xref:System.IdentityModel.Tokens.TokenReplayCache>
- [\<tokenReplayDetection>](tokenreplaydetection.md)
