---
title: "Nullable 형식 boxing(C# 프로그래밍 가이드)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
helpviewer_keywords:
- boxing [C#], nullable types
- unboxing [C#], nullable types
- nullable types [C#], boxing and unboxing
ms.assetid: bdb5b626-abc0-405d-8f64-0f0a0bf883a4
caps.latest.revision: 12
author: BillWagner
ms.author: wiwagn
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 5ce063a70ced98fd8b99b4b46d704e08ddc96e10
ms.contentlocale: ko-kr
ms.lasthandoff: 07/28/2017

---
# <a name="boxing-nullable-types-c-programming-guide"></a><span data-ttu-id="56a03-102">Nullable 형식 boxing(C# 프로그래밍 가이드)</span><span class="sxs-lookup"><span data-stu-id="56a03-102">Boxing Nullable Types (C# Programming Guide)</span></span>
<span data-ttu-id="56a03-103">Nullable 형식을 기반으로 하는 개체는 개체가 null이 아닌 경우에만 boxing됩니다.</span><span class="sxs-lookup"><span data-stu-id="56a03-103">Objects based on nullable types are only boxed if the object is non-null.</span></span> <span data-ttu-id="56a03-104"><xref:System.Nullable%601.HasValue%2A>가 `false`이면 boxing 대신 개체 참조가 `null`에 할당됩니다.</span><span class="sxs-lookup"><span data-stu-id="56a03-104">If <xref:System.Nullable%601.HasValue%2A> is `false`, the object reference is assigned to `null` instead of boxing.</span></span> <span data-ttu-id="56a03-105">예:</span><span class="sxs-lookup"><span data-stu-id="56a03-105">For example:</span></span>  
  
```csharp  
bool? b = null;  
object o = b;  
// Now o is null.  
```  
  
 <span data-ttu-id="56a03-106">개체가 null이 아닌 경우(<xref:System.Nullable%601.HasValue%2A>가 `true`인 경우) boxing이 발생하지만 nullable 개체의 기반이 되는 기본 형식만 boxing됩니다.</span><span class="sxs-lookup"><span data-stu-id="56a03-106">If the object is non-null -- if <xref:System.Nullable%601.HasValue%2A> is `true` -- then boxing occurs, but only the underlying type that the nullable object is based on is boxed.</span></span> <span data-ttu-id="56a03-107">null이 아닌 nullable 값 형식을 boxing하면 값 형식을 래핑하는 <xref:System.Nullable%601?displayProperty=fullName>이 아니라 값 형식 자체가 boxing됩니다.</span><span class="sxs-lookup"><span data-stu-id="56a03-107">Boxing a non-null nullable value type boxes the value type itself, not the <xref:System.Nullable%601?displayProperty=fullName> that wraps the value type.</span></span> <span data-ttu-id="56a03-108">예:</span><span class="sxs-lookup"><span data-stu-id="56a03-108">For example:</span></span>  
  
```csharp  
bool? b = false;  
int? i = 44;  
object bBoxed = b; // bBoxed contains a boxed bool.  
object iBoxed = i; // iBoxed contains a boxed int.  
```  
  
 <span data-ttu-id="56a03-109">두 boxed 개체는 nullable이 아닌 형식을 boxing하여 만들어진 개체와 동일합니다.</span><span class="sxs-lookup"><span data-stu-id="56a03-109">The two boxed objects are identical to those created by boxing non-nullable types.</span></span> <span data-ttu-id="56a03-110">또한 nullable이 아닌 boxed 형식과 마찬가지로, 다음 예제와 같이 nullable 형식으로 unboxed할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="56a03-110">And, just like non-nullable boxed types, they can be unboxed into nullable types, as in the following example:</span></span>  
  
```csharp  
bool? b2 = (bool?)bBoxed;  
int? i2 = (int?)iBoxed;  
```  
  
## <a name="remarks"></a><span data-ttu-id="56a03-111">설명</span><span class="sxs-lookup"><span data-stu-id="56a03-111">Remarks</span></span>  
 <span data-ttu-id="56a03-112">boxed 시 nullable 형식의 동작은 다음 두 가지 이점을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="56a03-112">The behavior of nullable types when boxed provides two advantages:</span></span>  
  
1.  <span data-ttu-id="56a03-113">nullable 개체 및 boxed 상대 항목이 null인지 테스트할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="56a03-113">Nullable objects and their boxed counterpart can be tested for null:</span></span>  
  
    ```csharp  
    bool? b = null;  
    object boxedB = b;  
    if (b == null)  
    {  
      // True.  
    }  
    if (boxedB == null)  
    {  
      // Also true.  
    }  
    ```  
  
2.  <span data-ttu-id="56a03-114">boxed nullable 형식은 기본 형식의 기능을 완벽하게 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="56a03-114">Boxed nullable types fully support the functionality of the underlying type:</span></span>  
  
    ```csharp  
    double? d = 44.4;  
    object iBoxed = d;  
    // Access IConvertible interface implemented by double.  
    IConvertible ic = (IConvertible)iBoxed;  
    int i = ic.ToInt32(null);  
    string str = ic.ToString();  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="56a03-115">참고 항목</span><span class="sxs-lookup"><span data-stu-id="56a03-115">See Also</span></span>  
 <span data-ttu-id="56a03-116">[C# 프로그래밍 가이드](../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="56a03-116">[C# Programming Guide](../../../csharp/programming-guide/index.md) </span></span>  
 <span data-ttu-id="56a03-117">[Nullable 형식](../../../csharp/programming-guide/nullable-types/index.md) </span><span class="sxs-lookup"><span data-stu-id="56a03-117">[Nullable Types](../../../csharp/programming-guide/nullable-types/index.md) </span></span>  
 [<span data-ttu-id="56a03-118">방법: Nullable 형식 식별</span><span class="sxs-lookup"><span data-stu-id="56a03-118">How to: Identify a Nullable Type</span></span>](../../../csharp/programming-guide/nullable-types/how-to-identify-a-nullable-type.md)
