---
title: ICLRRuntimeInfo::BindAsLegacyV2Runtime 메서드
ms.date: 03/30/2017
api_name:
- ICLRRuntimeInfo.BindAsLegacyV2Runtime
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRRuntimeInfo::BindAsLegacyV2Runtime
helpviewer_keywords:
- ICLRRuntimeInfo::BindAsLegacyV2Runtime method [.NET Framework hosting]
- BindAsLegacyV2Runtime method [.NET Framework hosting]
ms.assetid: 65fd55ac-4a24-4479-9384-a2e8013bfb2b
topic_type:
- apiref
ms.openlocfilehash: 4390f379e5092cc59d123631f5e6d8da82e2bd7f
ms.sourcegitcommit: 0926684d8d34f4c6b5acce58d2193db093cb9cf2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/20/2020
ms.locfileid: "83703900"
---
# <a name="iclrruntimeinfobindaslegacyv2runtime-method"></a>ICLRRuntimeInfo::BindAsLegacyV2Runtime 메서드
모든 레거시 CLR (공용 언어 런타임) 버전 2 활성화 정책 결정에 대 한 현재 런타임을 바인딩합니다.  
  
## <a name="syntax"></a>구문  
  
```cpp  
HRESULT BindAsLegacyV2Runtime ();  
```  
  
## <a name="return-value"></a>Return Value  
 이 메서드는 다음과 같은 특정 Hresult를 반환 합니다.  
  
|HRESULT|설명|  
|-------------|-----------------|  
|S_OK|바인딩이 성공 했거나이 런타임이 이미 레거시 CLR 버전 2 활성화 정책 런타임으로 바인딩되어 있습니다.|  
|CLR_E_SHIM_LEGACYRUNTIMEALREADYBOUND|다른 런타임이 이미 레거시 CLR 버전 2 활성화 정책에 바인딩되어 있습니다.|  
  
## <a name="remarks"></a>설명  
 현재 런타임이 모든 레거시 CLR 버전 2 활성화 정책 결정에 이미 바인딩되어 있는 경우 (예를 들어 `useLegacyV2RuntimeActivationPolicy` 구성 파일에서 [ \< startup> 요소](../../configure-apps/file-schema/startup/startup-element.md) 에 특성을 사용 하 여)이 메서드는 오류 결과를 반환 하지 않습니다. 대신 메서드가 레거시 활성화 정책을 성공적으로 바인딩한 경우와 마찬가지로 결과가 S_OK 됩니다.  
  
## <a name="requirements"></a>요구 사항  
 **플랫폼:**[시스템 요구 사항](../../get-started/system-requirements.md)을 참조하세요.  
  
 **헤더:** MetaHost  
  
 **라이브러리:** Mscoree.dll에 리소스로 포함 됩니다.  
  
 **.NET Framework 버전:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>참고 항목

- [ICLRRuntimeInfo 인터페이스](iclrruntimeinfo-interface.md)
- [호스팅 인터페이스](hosting-interfaces.md)
- [호스팅](index.md)
- [\<startup> 요소](../../configure-apps/file-schema/startup/startup-element.md)
