---
title: ICorDebugManagedCallback3 인터페이스
ms.date: 03/30/2017
api_name:
- ICorDebugManagedCallback3
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugManagedCallback3
helpviewer_keywords:
- ICorDebugManagedCallback3 interface [.NET Framework debugging]
ms.assetid: a95389d3-cf2e-47a4-9805-61426acc6b65
topic_type:
- apiref
ms.openlocfilehash: 63e3f166c4cbf17f4892dccf770343bfbf6e0284
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/12/2020
ms.locfileid: "83209749"
---
# <a name="icordebugmanagedcallback3-interface"></a>ICorDebugManagedCallback3 인터페이스
활성화된 사용자 지정 디버거 알림이 발생했음을 나타내는 콜백 메서드를 제공합니다.  
  
## <a name="methods"></a>메서드  
  
|메서드|설명|  
|------------|-----------------|  
|[CustomNotification 메서드](icordebugmanagedcallback3-customnotification-method.md)|사용 하도록 설정 된 사용자 지정 디버거 알림이 발생 했음을 나타냅니다.|  
  
## <a name="remarks"></a>설명  
 이 인터페이스는 [ICorDebugManagedCallback](icordebugmanagedcallback-interface.md) 및 [ICorDebugManagedCallback2](icordebugmanagedcallback2-interface.md) 인터페이스의 논리적 확장입니다.  
  
> [!NOTE]
> 이 인터페이스는 크로스 시스템 또는 크로스 프로세스 원격 호출을 지원하지 않습니다.  
  
## <a name="requirements"></a>요구 사항  
 **플랫폼:**[시스템 요구 사항](../../get-started/system-requirements.md)을 참조하세요.  
  
 **헤더:** CorDebug.idl, CorDebug.h  
  
 **라이브러리:** CorGuids.lib  
  
 **.NET Framework 버전:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>참고 항목

- [ICorDebugManagedCallback 인터페이스](icordebugmanagedcallback-interface.md)
- [ICorDebugManagedCallback2 인터페이스](icordebugmanagedcallback2-interface.md)
- [디버깅 인터페이스](debugging-interfaces.md)
- [디버깅](index.md)
