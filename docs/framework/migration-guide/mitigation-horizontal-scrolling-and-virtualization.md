---
title: "완화: 가로 스크롤 및 가상화"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-bcl
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d5bafd9b-a3b3-4f92-8241-2aad254fb1a9
caps.latest.revision: 6
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 40eaf185e9c0c60493e9a2e5428c58b7463789fe
ms.contentlocale: ko-kr
ms.lasthandoff: 07/28/2017

---
# <a name="mitigation-horizontal-scrolling-and-virtualization"></a><span data-ttu-id="c1d9c-102">완화: 가로 스크롤 및 가상화</span><span class="sxs-lookup"><span data-stu-id="c1d9c-102">Mitigation: Horizontal Scrolling and Virtualization</span></span>
<span data-ttu-id="c1d9c-103">이 변경 내용은 주 스크롤 방향의 직각 방향으로 자체 가상화를 수행하는 <xref:System.Windows.Controls.ItemsControl>에 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="c1d9c-103">This change applies to an <xref:System.Windows.Controls.ItemsControl> that does its own virtualization in the direction orthogonal to the main scrolling direction.</span></span> <span data-ttu-id="c1d9c-104">이러한 가상화의 주요 예제는 <xref:System.Windows.Controls.DataGrid.EnableColumnVirtualization%2A>이 `true`로 설정된 <xref:System.Windows.Controls.DataGrid> 컨트롤에서 확인할 수 있습니다.  특정 가로 스크롤 작업의 결과는 보다 직관적이고 비교 가능한 세로 작업의 결과와 좀 더 유사한 결과를 생성하도록 변경되었습니다.</span><span class="sxs-lookup"><span data-stu-id="c1d9c-104">(The chief  example is a <xref:System.Windows.Controls.DataGrid> control with <xref:System.Windows.Controls.DataGrid.EnableColumnVirtualization%2A> set to `true`.)  The outcome of certain  horizontal scrolling operations has been changed to produce results that are more intuitive and more analogous to the results of comparable vertical operations.</span></span>  <span data-ttu-id="c1d9c-105">구체적인 작업으로는 가로 스크롤 막대를 마우스 오른쪽 단추로 클릭할 때 표시되는 메뉴의 이름을 사용하기 위한 **여기로 스크롤** 및 **오른쪽 가장자리**가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c1d9c-105">The specific operations include **Scroll Here** and **Right Edge**, to use the names from the menu obtained by right-clicking a horizontal scrollbar.</span></span>  <span data-ttu-id="c1d9c-106">이 두 작업에서는 모두 후보 오프셋을 계산하고 <xref:System.Windows.Controls.Primitives.IScrollInfo.SetHorizontalOffset%2A?displayProperty=fullName>을 호출합니다.</span><span class="sxs-lookup"><span data-stu-id="c1d9c-106">Both of these compute a  candidate offset and call <xref:System.Windows.Controls.Primitives.IScrollInfo.SetHorizontalOffset%2A?displayProperty=fullName>.</span></span>  <span data-ttu-id="c1d9c-107">새롭게 가상화가 취소된 콘텐츠에서는 <xref:System.Windows.Controls.Primitives.IScrollInfo.ExtentWidth%2A?displayProperty=fullName>의 값이 변경되었으므로 새 오프셋으로 스크롤한 후에 "여기" 또는 "오른쪽 가장자리"의 정의가 변경되었을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c1d9c-107">After scrolling to the new offset, the definition of "here" or "right edge" may have changed because newly de-virtualized content has changed the value of <xref:System.Windows.Controls.Primitives.IScrollInfo.ExtentWidth%2A?displayProperty=fullName>.</span></span>  
  
## <a name="description-of-the-change"></a><span data-ttu-id="c1d9c-108">변경에 대한 설명</span><span class="sxs-lookup"><span data-stu-id="c1d9c-108">Description of the change</span></span>  
 <span data-ttu-id="c1d9c-109">[!INCLUDE[net_v462](../../../includes/net-v462-md.md)] 이전에는 “여기" 또는 “오른쪽 가장자리"는 더 이상 아닐 수 있지만 스크롤 작업을 수행하면 후보 오프셋이 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="c1d9c-109">Prior to the [!INCLUDE[net_v462](../../../includes/net-v462-md.md)], the scroll operation simply uses the candidate offset, even though it may not be "here" or at the "right edge" any more.</span></span>  <span data-ttu-id="c1d9c-110">결과적으로 그림과 같은 스크롤 상자 "바운스"와 같은 결과가 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="c1d9c-110">This results in effects like "bouncing" the scroll thumb, best illustrated by example.</span></span>  <span data-ttu-id="c1d9c-111"><xref:System.Windows.Controls.DataGrid> 컨트롤의 <xref:System.Windows.Controls.Primitives.IScrollInfo.ExtentWidth%2A>는 1000으로, <xref:System.Windows.FrameworkElement.Width%2A>는 200으로 설정되어 있다고 가정해 보겠습니다.</span><span class="sxs-lookup"><span data-stu-id="c1d9c-111">Suppose a <xref:System.Windows.Controls.DataGrid> control has <xref:System.Windows.Controls.Primitives.IScrollInfo.ExtentWidth%2A> set to 1000 and <xref:System.Windows.FrameworkElement.Width%2A> set to 200.</span></span>  <span data-ttu-id="c1d9c-112">"오른쪽 가장자리"로 스크롤하면 후보 오프셋 1000 - 200 = 800이 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="c1d9c-112">A scroll to "Right Edge" uses candidate offset  1000 - 200 = 800.</span></span>  <span data-ttu-id="c1d9c-113">해당 오프셋으로 스크롤하는 동안 새 열의 가상화가 취소됩니다. 열이 매우 넓어서 <xref:System.Windows.Controls.Primitives.IScrollInfo.ExtentWidth%2A>가 2000으로 변경된다고 가정하겠습니다.</span><span class="sxs-lookup"><span data-stu-id="c1d9c-113">While scrolling to that offset, new columns are de-virtualized; let's suppose they are very wide, so that the <xref:System.Windows.Controls.Primitives.IScrollInfo.ExtentWidth%2A> changes to 2000.</span></span>  <span data-ttu-id="c1d9c-114">스크롤은 <xref:System.Windows.Controls.Primitives.IScrollInfo.HorizontalOffset%2A>=800에서 종료되며 엄지는 스크롤 막대 가운데 근처로 다시 "바운스"됩니다. 이 위치에 해당하는 값은 800/2000=40%입니다.</span><span class="sxs-lookup"><span data-stu-id="c1d9c-114">The scroll ends with <xref:System.Windows.Controls.Primitives.IScrollInfo.HorizontalOffset%2A>=800, and the thumb "bounces" back to near the middle of the scrollbar -- precisely at 800/2000 = 40%.</span></span>  
  
 <span data-ttu-id="c1d9c-115">[!INCLUDE[net_v462](../../../includes/net-v462-md.md)]부터 이러한 상황이 발생하는 경우 새 후보 오프셋이 다시계산 됩니다.</span><span class="sxs-lookup"><span data-stu-id="c1d9c-115">Starting with the [!INCLUDE[net_v462](../../../includes/net-v462-md.md)], a new candidate offset is recomputed when this situation occurs.</span></span> <span data-ttu-id="c1d9c-116">(세로 스크롤도 이미 이와 같이 작동합니다.)</span><span class="sxs-lookup"><span data-stu-id="c1d9c-116">(This is how vertical scrolling works already.)</span></span>  
  
## <a name="impact"></a><span data-ttu-id="c1d9c-117">영향</span><span class="sxs-lookup"><span data-stu-id="c1d9c-117">Impact</span></span>  
 <span data-ttu-id="c1d9c-118">이 변경으로 인해 최종 사용자가 오프셋을 더욱 쉽게 예측할 수 있는 직관적인 환경이 생성됩니다. 하지만 가로 스크롤 이후 <xref:System.Windows.Controls.Primitives.IScrollInfo.HorizontalOffset%2A?displayProperty=fullName>(최종 사용자가 호출하거나 명시적 <xref:System.Windows.Controls.Primitives.IScrollInfo.SetHorizontalOffset%2A?displayProperty=fullName> 호출을 통해 호출됨)의 정확한 값에 따라 동작이 달라지는 앱에도 영향을 줄 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c1d9c-118">The change produces a more predictable and intuitive experience for the end user, but it could also affect any app that depends on the exact value of <xref:System.Windows.Controls.Primitives.IScrollInfo.HorizontalOffset%2A?displayProperty=fullName> after a horizontal scroll, whether invoked by the end user or by an explicit call to <xref:System.Windows.Controls.Primitives.IScrollInfo.SetHorizontalOffset%2A?displayProperty=fullName>.</span></span>  
  
## <a name="mitigation"></a><span data-ttu-id="c1d9c-119">완화</span><span class="sxs-lookup"><span data-stu-id="c1d9c-119">Mitigation</span></span>  
 <span data-ttu-id="c1d9c-120"><xref:System.Windows.Controls.Primitives.IScrollInfo.HorizontalOffset%2A?displayProperty=fullName>의 예측 값을 사용하는 앱의 경우 가상화 취소로 인해 <xref:System.Windows.Controls.Primitives.IScrollInfo.ExtentWidth%2A>가 변경될 수 있는 가로 스크롤 이후 실제 값과 <xref:System.Windows.Controls.Primitives.IScrollInfo.ExtentWidth%2A>의 값을 검색하도록 변경해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="c1d9c-120">An app that uses a predicted value for <xref:System.Windows.Controls.Primitives.IScrollInfo.HorizontalOffset%2A?displayProperty=fullName> should be changed to retrieve the actual value (and the value of <xref:System.Windows.Controls.Primitives.IScrollInfo.ExtentWidth%2A>) after any horizontal scroll that could change <xref:System.Windows.Controls.Primitives.IScrollInfo.ExtentWidth%2A> due to de-virtualization.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c1d9c-121">참고 항목</span><span class="sxs-lookup"><span data-stu-id="c1d9c-121">See Also</span></span>  
 [<span data-ttu-id="c1d9c-122">런타임 변경 내용</span><span class="sxs-lookup"><span data-stu-id="c1d9c-122">Runtime Changes</span></span>](../../../docs/framework/migration-guide/runtime-changes-in-the-net-framework-4-6-2.md)
