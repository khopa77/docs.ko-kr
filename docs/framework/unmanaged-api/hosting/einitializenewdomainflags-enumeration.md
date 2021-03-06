---
title: EInitializeNewDomainFlags 열거형
ms.date: 03/30/2017
api_name:
- EInitializeNewDomainFlags
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- EInitializeNewDomainFlags
helpviewer_keywords:
- EInitializeNewDomainFlags enumeration [.NET Framework hosting]
ms.assetid: 3a120ab2-f5ef-4c9b-8595-d3ed7247c342
ms.openlocfilehash: 7ff10f84d8d270d31c5d560fb3c9bd3c81cf3e24
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/19/2020
ms.locfileid: "83616231"
---
# <a name="einitializenewdomainflags-enumeration"></a>EInitializeNewDomainFlags 열거형
호스트에서 응용 프로그램 도메인 초기화에 대 한 정보를 런타임에 제공할 수 있도록 합니다.  
  
## <a name="syntax"></a>구문  
  
```cpp  
typedef enum {  
    eInitializeNewDomainFlags_None              = 0x0000,  
    eInitializeNewDomainFlags_NoSecurityChanges = 0x0002  
} EInitializeNewDomainFlags;  
```  
  
## <a name="members"></a>멤버  
  
|멤버|설명|  
|------------|-----------------|  
|`eInitializeNewDomainFlags_None`|플래그가 없습니다.|  
|`eInitializeNewDomainFlags_NoSecurityChanges`|호스트가 메서드에서 응용 프로그램 도메인의 보안 상태를 변경 하지 않는다는 것을 CLR (공용 언어 런타임)에 알립니다 <xref:System.AppDomainManager.InitializeNewDomain%2A> .|  
  
## <a name="remarks"></a>설명  
 [ICLRDomainManager:: SetAppDomainManagerType](iclrdomainmanager-setappdomainmanagertype-method.md) 메서드는 형식의 매개 변수를 사용 합니다 `EInitializeNewDomainFlags` .  
  
## <a name="requirements"></a>요구 사항  
 **플랫폼:**[시스템 요구 사항](../../get-started/system-requirements.md)을 참조하세요.  
  
 **헤더:** Mscoree.dll  
  
 **라이브러리:** Mscoree.dll  
  
 **.NET Framework 버전:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>참고 항목

- [호스팅 열거형](hosting-enumerations.md)
- [SetAppDomainManagerType 메서드](iclrdomainmanager-setappdomainmanagertype-method.md)
