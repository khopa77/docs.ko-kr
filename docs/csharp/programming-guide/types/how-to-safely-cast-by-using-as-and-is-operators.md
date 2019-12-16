---
title: "방법: AS 및 IS 연산자를 사용한 안전한 캐스팅(C# 프로그래밍 가이드)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
helpviewer_keywords:
- cast operators [C#], as and is operators
- as operator [C#]
- is operator [C#]
ms.assetid: c1176cea-1426-4a44-8570-3eadafa58863
caps.latest.revision: 10
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
ms.openlocfilehash: c5daa8525f45c123dabb0f59dfd29385b9e50354
ms.contentlocale: ko-kr
ms.lasthandoff: 07/28/2017

---
# <a name="how-to-safely-cast-by-using-as-and-is-operators-c-programming-guide"></a><span data-ttu-id="25879-102">방법: AS 및 IS 연산자를 사용한 안전한 캐스팅(C# 프로그래밍 가이드)</span><span class="sxs-lookup"><span data-stu-id="25879-102">How to: Safely Cast by Using as and is Operators (C# Programming Guide)</span></span>
<span data-ttu-id="25879-103">개체는 다형성이기 때문에 기본 클래스 형식의 변수에 파생 형식이 포함될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="25879-103">Because objects are polymorphic, it is possible for a variable of a base class type to hold a derived type.</span></span> <span data-ttu-id="25879-104">파생 형식의 메서드에 액세스하려면 값을 파생 형식으로 다시 캐스팅해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="25879-104">To access the derived type's method, it is necessary to cast the value back to the derived type.</span></span> <span data-ttu-id="25879-105">그러나 이러한 경우에 단순 캐스트를 시도하면 <xref:System.InvalidCastException>이 throw될 위험이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="25879-105">However, to attempt a simple cast in these cases creates the risk of throwing an <xref:System.InvalidCastException>.</span></span> <span data-ttu-id="25879-106">C#에서 [is](../../../csharp/language-reference/keywords/is.md) 및 [as](../../../csharp/language-reference/keywords/as.md) 연산자를 제공하는 것은 이런 이유 때문입니다.</span><span class="sxs-lookup"><span data-stu-id="25879-106">That is why C# provides the [is](../../../csharp/language-reference/keywords/is.md) and [as](../../../csharp/language-reference/keywords/as.md) operators.</span></span> <span data-ttu-id="25879-107">이러한 연산자를 사용하여 예외가 throw되지 않고 캐스트에 성공할지 여부를 테스트할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="25879-107">You can use these operators to test whether a cast will succeed without causing an exception to be thrown.</span></span> <span data-ttu-id="25879-108">일반적으로 `as` 연산자는 성공적으로 캐스팅할 수 있는 경우 실제로 캐스트 값을 반환하기 때문에 더 효율적입니다.</span><span class="sxs-lookup"><span data-stu-id="25879-108">In general, the `as` operator is more efficient because it actually returns the cast value if the cast can be made successfully.</span></span> <span data-ttu-id="25879-109">`is` 연산자는 부울 값만 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="25879-109">The `is` operator returns only a Boolean value.</span></span> <span data-ttu-id="25879-110">따라서 개체의 형식을 확인하려고 하지만 실제로 캐스팅할 필요는 없는 경우에 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="25879-110">It can therefore be used when you just want to determine an object's type but do not have to actually cast it.</span></span>  
  
## <a name="example"></a><span data-ttu-id="25879-111">예제</span><span class="sxs-lookup"><span data-stu-id="25879-111">Example</span></span>  
 <span data-ttu-id="25879-112">다음 예제에서는 `is` 및 `as` 연산자를 사용하여 예외가 throw될 위험 없이 한 참조 형식에서 다른 참조 형식으로 캐스팅하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="25879-112">The following examples show how to use the `is` and `as` operators to cast from one reference type to another without the risk of throwing an exception.</span></span> <span data-ttu-id="25879-113">또한 예제에서는 `as` 연산자를 nullable 값 형식과 함께 사용하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="25879-113">The example also shows how to use the `as` operator with nullable value types.</span></span>  
  
 <span data-ttu-id="25879-114">[!code-cs[csProgGuideTypes#40](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/how-to-safely-cast-by-using-as-and-is-operators_1.cs)]</span><span class="sxs-lookup"><span data-stu-id="25879-114">[!code-cs[csProgGuideTypes#40](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/how-to-safely-cast-by-using-as-and-is-operators_1.cs)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="25879-115">참고 항목</span><span class="sxs-lookup"><span data-stu-id="25879-115">See Also</span></span>  
 <span data-ttu-id="25879-116">[형식](../../../csharp/programming-guide/types/index.md) </span><span class="sxs-lookup"><span data-stu-id="25879-116">[Types](../../../csharp/programming-guide/types/index.md) </span></span>  
 <span data-ttu-id="25879-117">[캐스팅 및 형식 변환](../../../csharp/programming-guide/types/casting-and-type-conversions.md) </span><span class="sxs-lookup"><span data-stu-id="25879-117">[Casting and Type Conversions](../../../csharp/programming-guide/types/casting-and-type-conversions.md) </span></span>  
 [<span data-ttu-id="25879-118">Nullable 형식</span><span class="sxs-lookup"><span data-stu-id="25879-118">Nullable Types</span></span>](../../../csharp/programming-guide/nullable-types/index.md)
