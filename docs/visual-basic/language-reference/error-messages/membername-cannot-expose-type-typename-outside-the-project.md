---
title: "'<membername>'은(는) <typename> '<containertype>'을(를) 통해 '<containertypename>' 형식을 프로젝트 외부로 노출할 수 없습니다."
ms.date: 07/20/2015
f1_keywords:
- bc30909
- vbc30909
helpviewer_keywords:
- BC30909
ms.assetid: ffa7395d-e182-4087-8ce8-079810fdae54
ms.openlocfilehash: 729a9f385d94412469d318cb804d216827eeb0fd
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84397287"
---
# <a name="membername-cannot-expose-type-typename-outside-the-project-through-containertype-containertypename"></a>'\<membername>'은(는) \<typename> '\<containertype>'을(를) 통해 '\<containertypename>' 형식을 프로젝트 외부로 노출할 수 없습니다.
변수, 프로시저 매개 변수 또는 함수 반환은 해당 컨테이너 외부에 노출 되지만 컨테이너 외부에 노출 되지 않아야 하는 형식으로 선언 됩니다.  
  
 다음 기본 코드는이 오류를 생성 하는 상황을 보여 줍니다.  
  
```vb  
Private Class privateClass  
End Class  
Public Class mainClass  
    Public exposedVar As New privateClass  
End Class  
```  
  
 ,, 또는로 선언 된 형식은 `Protected` `Friend` `Protected Friend` `Private` 선언 컨텍스트 외부에서 제한 된 액세스를 제공 하기 위한 것입니다. 제한 된 액세스 권한이 있는 변수의 데이터 형식으로 사용 하면 이러한 목적이 줄어듭니다. 위의 기본 코드에서는 이며 `exposedVar` `Public` 에 액세스할 수 없는 `privateClass` 코드에 노출 됩니다.  
  
 **오류 ID:** BC30909  
  
## <a name="to-correct-this-error"></a>이 오류를 해결하려면  
  
- 변수, 프로시저 매개 변수 또는 함수 반환의 액세스 수준을 해당 데이터 형식의 액세스 수준 보다 최소한 제한적으로 변경 합니다.  
  
## <a name="see-also"></a>참고 항목

- [Visual Basic의 액세스 수준](../../programming-guide/language-features/declared-elements/access-levels.md)
