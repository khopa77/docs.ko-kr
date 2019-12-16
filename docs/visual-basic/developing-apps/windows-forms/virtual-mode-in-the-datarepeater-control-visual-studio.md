---
title: "DataRepeater 컨트롤 (Visual Studio)에서 가상 모드 | Microsoft 문서"
ms.date: 2015-07-20
ms.prod: .net
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
dev_langs:
- VB
helpviewer_keywords:
- virtual data binding
- DataRepeater
- DataRepeater, virtual mode
ms.assetid: 5fb805dc-2d8b-4139-b1e3-86e4c2667221
caps.latest.revision: 13
author: dotnet-bot
ms.author: dotnetcontent
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
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: acd9321772fb75c84abc8f6c67ee8c13bd035add
ms.contentlocale: ko-kr
ms.lasthandoff: 04/12/2017

---
# <a name="virtual-mode-in-the-datarepeater-control-visual-studio"></a><span data-ttu-id="18559-102">DataRepeater 컨트롤의 가상 모드(Visual Studio)</span><span class="sxs-lookup"><span data-stu-id="18559-102">Virtual Mode in the DataRepeater Control (Visual Studio)</span></span>
<span data-ttu-id="18559-103">많은 양의 테이블 형식 데이터를 표시 하려는 경우는 <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>컨트롤을 설정 하 여 성능을 향상 시킬 수 있습니다는 <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.VirtualMode%2A>속성을 `True` 명시적으로 해당 데이터 원본 컨트롤의 상호 작용을 관리 합니다.</xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.VirtualMode%2A> </xref:Microsoft.VisualBasic.PowerPacks.DataRepeater></span><span class="sxs-lookup"><span data-stu-id="18559-103">When you want to display large quantities of tabular data in a <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> control, you can improve performance by setting the <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.VirtualMode%2A> property to `True` and explicitly managing the control's interaction with its data source.</span></span> <span data-ttu-id="18559-104"><xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>컨트롤은 런타임에 필요에 따라 데이터를 표시 하 고 데이터 소스와 상호 작용을 처리할 수 있는 몇 가지 이벤트를 제공 합니다.</xref:Microsoft.VisualBasic.PowerPacks.DataRepeater></span><span class="sxs-lookup"><span data-stu-id="18559-104">The <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> control provides several events that you can handle to interact with your data source and display the data as needed at run time.</span></span>  
  
## <a name="how-virtual-mode-works"></a><span data-ttu-id="18559-105">가상 모드 작동 방식</span><span class="sxs-lookup"><span data-stu-id="18559-105">How Virtual Mode Works</span></span>  
 <span data-ttu-id="18559-106">에 대 한 가장 일반적인 시나리오는 <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>컨트롤의 자식 컨트롤을 바인딩하는 <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemTemplate%2A>에 대 한 데이터 디자인 타임에 원본 및 허용는 <xref:System.Windows.Forms.BindingSource>앞뒤로 필요에 따라 데이터를 전달 합니다.</xref:System.Windows.Forms.BindingSource> </xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemTemplate%2A> </xref:Microsoft.VisualBasic.PowerPacks.DataRepeater></span><span class="sxs-lookup"><span data-stu-id="18559-106">The most common scenario for the <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> control is to bind the child controls of the <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemTemplate%2A> to a data source at design time and allow the <xref:System.Windows.Forms.BindingSource> to pass data back and forth as needed.</span></span> <span data-ttu-id="18559-107">가상 모드를 사용 하는 경우 컨트롤은 데이터 원본에 바인딩되지 않은 이며 데이터 전달 됩니다 앞뒤로 기본 데이터 원본에 런타임 시.</span><span class="sxs-lookup"><span data-stu-id="18559-107">When you use virtual mode, the controls are not bound to a data source, and data is passed back and forth to the underlying data source at run time.</span></span>  
  
 <span data-ttu-id="18559-108">때는 <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.VirtualMode%2A>속성이 `True`, 컨트롤을 추가 하 여 사용자 인터페이스를 만드는 **도구 상자** 바인딩된 컨트롤을 추가 하는 대신는 **데이터 원본** 창.</xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.VirtualMode%2A></span><span class="sxs-lookup"><span data-stu-id="18559-108">When the <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.VirtualMode%2A> property is set to `True`, you create the user interface by adding controls from the **Toolbox** instead of adding bound controls from the **Data Sources** window.</span></span>  
  
 <span data-ttu-id="18559-109">컨트롤 단위로 별로 이벤트는 발생 하 고 데이터의 표시를 처리 하는 코드를 추가 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="18559-109">Events are raised on a control-by-control basis, and you must add code to handle the display of data.</span></span> <span data-ttu-id="18559-110">새 <xref:Microsoft.VisualBasic.PowerPacks.DataRepeaterItem>스크롤될는 <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemValueNeeded>이벤트는 각 컨트롤에 대해 한 번씩 발생 하 고 각 컨트롤에 대 한 값을 제공 해야는 <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemValueNeeded>이벤트 처리기입니다.</xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemValueNeeded> </xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemValueNeeded> </xref:Microsoft.VisualBasic.PowerPacks.DataRepeaterItem></span><span class="sxs-lookup"><span data-stu-id="18559-110">When a new <xref:Microsoft.VisualBasic.PowerPacks.DataRepeaterItem> is scrolled into view, the <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemValueNeeded> event is raised one time for each control and you must supply the values for each control in the <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemValueNeeded> event handler.</span></span>  
  
 <span data-ttu-id="18559-111">데이터 컨트롤 중 하나에 사용자가 변경 되는 <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemValuePushed>이벤트가 발생 하 고 데이터의 유효성을 검사 하 고 데이터 원본에 저장 해야 합니다.</xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemValuePushed></span><span class="sxs-lookup"><span data-stu-id="18559-111">If data in one of the controls is changed by the user, the <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemValuePushed> event is raised and you must validate the data and save it to your data source.</span></span>  
  
 <span data-ttu-id="18559-112">사용자가 새 항목을 추가할 경우는 <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.NewItemNeeded>이벤트가 발생 합니다.</xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.NewItemNeeded></span><span class="sxs-lookup"><span data-stu-id="18559-112">If the user adds a new item, the <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.NewItemNeeded> event is raised.</span></span> <span data-ttu-id="18559-113">이 이벤트 처리기를 사용 하 여 데이터 원본에 새 레코드를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="18559-113">Use this event's handler to create a new record in your data source.</span></span> <span data-ttu-id="18559-114">의도 하지 않은 변경 내용을 방지 하려면 모니터링 해야는 <xref:System.Windows.Forms.Control.KeyDown>각 컨트롤 및 호출에 대 한 이벤트 <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.CancelEdit%2A>사용자가 ESC 키를 누르면.</xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.CancelEdit%2A> </xref:System.Windows.Forms.Control.KeyDown></span><span class="sxs-lookup"><span data-stu-id="18559-114">To prevent unintended changes, you must also monitor the <xref:System.Windows.Forms.Control.KeyDown> event for each control and call <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.CancelEdit%2A> if the user presses the ESC key.</span></span>  
  
 <span data-ttu-id="18559-115">데이터 소스가 변경 하는 경우 새로 고칠 수 있습니다는 <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>호출 하 여 컨트롤의 <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.BeginResetItemTemplate%2A>및 <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.EndResetItemTemplate%2A>메서드.</xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.EndResetItemTemplate%2A> </xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.BeginResetItemTemplate%2A> </xref:Microsoft.VisualBasic.PowerPacks.DataRepeater></span><span class="sxs-lookup"><span data-stu-id="18559-115">If your data source changes, you can refresh the <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> control by calling the <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.BeginResetItemTemplate%2A> and <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.EndResetItemTemplate%2A> methods.</span></span> <span data-ttu-id="18559-116">순서에서 두 메서드를 호출 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="18559-116">Both methods must be called in order.</span></span>  
  
 <span data-ttu-id="18559-117">에 대 한 이벤트 처리기를 구현 해야 하는 마지막으로 <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemsRemoved>항목이 삭제 될 때 및 필요에 따라 발생 하는 이벤트는 <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.UserDeletingItems>및 <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.UserDeletedItems>DELETE 키를 눌러 항목을 삭제 하는 사용자 때마다 발생 하는 이벤트입니다.</xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.UserDeletedItems> </xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.UserDeletingItems> </xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemsRemoved></span><span class="sxs-lookup"><span data-stu-id="18559-117">Finally, you must implement event handlers for the <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemsRemoved> event, which occurs when an item is deleted, and optionally for the <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.UserDeletingItems> and <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.UserDeletedItems> events, which occur whenever a user deletes an item by pressing the DELETE key.</span></span>  
  
## <a name="implementing-virtual-mode"></a><span data-ttu-id="18559-118">가상 모드 구현</span><span class="sxs-lookup"><span data-stu-id="18559-118">Implementing Virtual Mode</span></span>  
 <span data-ttu-id="18559-119">다음은 가상 모드를 구현 하는 데 필요한 단계입니다.</span><span class="sxs-lookup"><span data-stu-id="18559-119">Following are the steps that are required to implement virtual mode.</span></span>  
  
#### <a name="to-implement-virtual-mode"></a><span data-ttu-id="18559-120">가상 모드 구현 하려면</span><span class="sxs-lookup"><span data-stu-id="18559-120">To implement virtual mode</span></span>  
  
1.  <span data-ttu-id="18559-121">끌기는 <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>에서 제어는 **Visual Basic PowerPacks** 탭에 **도구 상자** 폼 이나 컨테이너 컨트롤로.</xref:Microsoft.VisualBasic.PowerPacks.DataRepeater></span><span class="sxs-lookup"><span data-stu-id="18559-121">Drag a <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> control from the **Visual Basic PowerPacks** tab in the **Toolbox** to a form or container control.</span></span> <span data-ttu-id="18559-122">설정의 <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.VirtualMode%2A>속성을 `True`.</xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.VirtualMode%2A></span><span class="sxs-lookup"><span data-stu-id="18559-122">Set the <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.VirtualMode%2A> property to `True`.</span></span>  
  
2.  <span data-ttu-id="18559-123">컨트롤을 끌어는 **도구 상자** 의 항목 템플릿 영역 (위쪽 영역)으로 <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>제어 합니다.</xref:Microsoft.VisualBasic.PowerPacks.DataRepeater></span><span class="sxs-lookup"><span data-stu-id="18559-123">Drag controls from the **Toolbox** onto the item template region (the upper region) of the <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> control.</span></span> <span data-ttu-id="18559-124">각 필드는 표시 하려는 데이터 원본에 대 한 제어를 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="18559-124">You will need one control for each field in your data source that you want to display.</span></span>  
  
3.  <span data-ttu-id="18559-125">구현에 대 한 처리기는 <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemValueNeeded>각 컨트롤에 대 한 값을 제공 하는 이벤트입니다.</xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemValueNeeded></span><span class="sxs-lookup"><span data-stu-id="18559-125">Implement a handler for the <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemValueNeeded> event to provide values for each control.</span></span> <span data-ttu-id="18559-126">이 이벤트는 새 <xref:Microsoft.VisualBasic.PowerPacks.DataRepeaterItem>스크롤될.</xref:Microsoft.VisualBasic.PowerPacks.DataRepeaterItem></span><span class="sxs-lookup"><span data-stu-id="18559-126">This event is raised when a new <xref:Microsoft.VisualBasic.PowerPacks.DataRepeaterItem> is scrolled into view.</span></span> <span data-ttu-id="18559-127">코드는 다음 예와 같이, 라는 데이터 원본에 `Employees`합니다.</span><span class="sxs-lookup"><span data-stu-id="18559-127">The code will resemble the following example, which is for a data source named `Employees`.</span></span>  
  
     <span data-ttu-id="18559-128">[!code-vb[#1 VbPowerPacksDataRepeaterVirtualMode](../../../visual-basic/developing-apps/windows-forms/codesnippet/VisualBasic/virtual-mode-in-the-datarepeater-control-visual-studio_1.vb) ] 
     [!code-cs [VbPowerPacksDataRepeaterVirtualMode&#1;](../../../visual-basic/developing-apps/windows-forms/codesnippet/CSharp/virtual-mode-in-the-datarepeater-control-visual-studio_1.cs)]</span><span class="sxs-lookup"><span data-stu-id="18559-128">[!code-vb[VbPowerPacksDataRepeaterVirtualMode#1](../../../visual-basic/developing-apps/windows-forms/codesnippet/VisualBasic/virtual-mode-in-the-datarepeater-control-visual-studio_1.vb)]
 [!code-cs[VbPowerPacksDataRepeaterVirtualMode#1](../../../visual-basic/developing-apps/windows-forms/codesnippet/CSharp/virtual-mode-in-the-datarepeater-control-visual-studio_1.cs)]</span></span>  
  
4.  <span data-ttu-id="18559-129">구현에 대 한 처리기는 <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemValuePushed>이벤트 데이터를 저장 합니다.</xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemValuePushed></span><span class="sxs-lookup"><span data-stu-id="18559-129">Implement a handler for the <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemValuePushed> event to store the data.</span></span> <span data-ttu-id="18559-130">이 이벤트는 사용자 <xref:Microsoft.VisualBasic.PowerPacks.DataRepeaterItem>.</xref:Microsoft.VisualBasic.PowerPacks.DataRepeaterItem> 의 자식 컨트롤에 변경 내용이 커밋될 때</span><span class="sxs-lookup"><span data-stu-id="18559-130">This event is raised when the user commits changes to a child control of the <xref:Microsoft.VisualBasic.PowerPacks.DataRepeaterItem>.</span></span> <span data-ttu-id="18559-131">코드는 다음 예와 같이, 라는 데이터 원본에 `Employees`합니다.</span><span class="sxs-lookup"><span data-stu-id="18559-131">The code will resemble the following example, which is for a data source named `Employees`.</span></span>  
  
     <span data-ttu-id="18559-132">[!code-vb[#2 VbPowerPacksDataRepeaterVirtualMode](../../../visual-basic/developing-apps/windows-forms/codesnippet/VisualBasic/virtual-mode-in-the-datarepeater-control-visual-studio_2.vb) ] 
     [!code-cs [VbPowerPacksDataRepeaterVirtualMode&#2;](../../../visual-basic/developing-apps/windows-forms/codesnippet/CSharp/virtual-mode-in-the-datarepeater-control-visual-studio_2.cs)]</span><span class="sxs-lookup"><span data-stu-id="18559-132">[!code-vb[VbPowerPacksDataRepeaterVirtualMode#2](../../../visual-basic/developing-apps/windows-forms/codesnippet/VisualBasic/virtual-mode-in-the-datarepeater-control-visual-studio_2.vb)]
 [!code-cs[VbPowerPacksDataRepeaterVirtualMode#2](../../../visual-basic/developing-apps/windows-forms/codesnippet/CSharp/virtual-mode-in-the-datarepeater-control-visual-studio_2.cs)]</span></span>  
  
5.  <span data-ttu-id="18559-133">각 자식 컨트롤에 대 한 처리기를 구현 <xref:System.Windows.Forms.Control.KeyDown>이벤트 및 모니터 ESC 키.</xref:System.Windows.Forms.Control.KeyDown></span><span class="sxs-lookup"><span data-stu-id="18559-133">Implement a handler for each child control's <xref:System.Windows.Forms.Control.KeyDown> event and monitor the ESC key.</span></span> <span data-ttu-id="18559-134">호출 된 <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.CancelEdit%2A>방지 하기 위해 메서드는 <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemValuePushed>이벤트가 발생 하지.</xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemValuePushed> </xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.CancelEdit%2A></span><span class="sxs-lookup"><span data-stu-id="18559-134">Call the <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.CancelEdit%2A> method to prevent the <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemValuePushed> event from being raised.</span></span> <span data-ttu-id="18559-135">코드에는 다음 예와 비슷하게 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="18559-135">The code will resemble the following example.</span></span>  
  
     <span data-ttu-id="18559-136">[!code-vb[#3 VbPowerPacksDataRepeaterVirtualMode](../../../visual-basic/developing-apps/windows-forms/codesnippet/VisualBasic/virtual-mode-in-the-datarepeater-control-visual-studio_3.vb) ] 
     [!code-cs [VbPowerPacksDataRepeaterVirtualMode&#3;](../../../visual-basic/developing-apps/windows-forms/codesnippet/CSharp/virtual-mode-in-the-datarepeater-control-visual-studio_3.cs)]</span><span class="sxs-lookup"><span data-stu-id="18559-136">[!code-vb[VbPowerPacksDataRepeaterVirtualMode#3](../../../visual-basic/developing-apps/windows-forms/codesnippet/VisualBasic/virtual-mode-in-the-datarepeater-control-visual-studio_3.vb)]
 [!code-cs[VbPowerPacksDataRepeaterVirtualMode#3](../../../visual-basic/developing-apps/windows-forms/codesnippet/CSharp/virtual-mode-in-the-datarepeater-control-visual-studio_3.cs)]</span></span>  
  
6.  <span data-ttu-id="18559-137">구현에 대 한 처리기는 <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.NewItemNeeded>이벤트.</xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.NewItemNeeded></span><span class="sxs-lookup"><span data-stu-id="18559-137">Implement a handler for the <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.NewItemNeeded> event.</span></span> <span data-ttu-id="18559-138">이 이벤트는 사용자에 새 항목을 추가 하는 경우는 <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>제어 합니다.</xref:Microsoft.VisualBasic.PowerPacks.DataRepeater></span><span class="sxs-lookup"><span data-stu-id="18559-138">This event is raised when the user adds a new item to the <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> control.</span></span> <span data-ttu-id="18559-139">코드는 다음 예와 같이, 라는 데이터 원본에 `Employees`합니다.</span><span class="sxs-lookup"><span data-stu-id="18559-139">The code will resemble the following example, which is for a data source named `Employees`.</span></span>  
  
     <span data-ttu-id="18559-140">[!code-vb[#4 VbPowerPacksDataRepeaterVirtualMode](../../../visual-basic/developing-apps/windows-forms/codesnippet/VisualBasic/virtual-mode-in-the-datarepeater-control-visual-studio_4.vb) ] 
     [!code-cs [VbPowerPacksDataRepeaterVirtualMode&#4;](../../../visual-basic/developing-apps/windows-forms/codesnippet/CSharp/virtual-mode-in-the-datarepeater-control-visual-studio_4.cs)]</span><span class="sxs-lookup"><span data-stu-id="18559-140">[!code-vb[VbPowerPacksDataRepeaterVirtualMode#4](../../../visual-basic/developing-apps/windows-forms/codesnippet/VisualBasic/virtual-mode-in-the-datarepeater-control-visual-studio_4.vb)]
 [!code-cs[VbPowerPacksDataRepeaterVirtualMode#4](../../../visual-basic/developing-apps/windows-forms/codesnippet/CSharp/virtual-mode-in-the-datarepeater-control-visual-studio_4.cs)]</span></span>  
  
7.  <span data-ttu-id="18559-141">구현에 대 한 처리기는 <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemsRemoved>이벤트.</xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemsRemoved></span><span class="sxs-lookup"><span data-stu-id="18559-141">Implement a handler for the <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemsRemoved> event.</span></span> <span data-ttu-id="18559-142">이 이벤트는 사용자는 기존 항목을 삭제 하는 경우에 발생 합니다.</span><span class="sxs-lookup"><span data-stu-id="18559-142">This event occurs when a user deletes an existing item.</span></span> <span data-ttu-id="18559-143">코드는 다음 예와 같이, 라는 데이터 원본에 `Employees`합니다.</span><span class="sxs-lookup"><span data-stu-id="18559-143">The code will resemble the following example, which is for a data source named `Employees`.</span></span>  
  
     <span data-ttu-id="18559-144">[!code-vb[#5 VbPowerPacksDataRepeaterVirtualMode](../../../visual-basic/developing-apps/windows-forms/codesnippet/VisualBasic/virtual-mode-in-the-datarepeater-control-visual-studio_5.vb) ] 
     [!code-cs [VbPowerPacksDataRepeaterVirtualMode&#5;](../../../visual-basic/developing-apps/windows-forms/codesnippet/CSharp/virtual-mode-in-the-datarepeater-control-visual-studio_5.cs)]</span><span class="sxs-lookup"><span data-stu-id="18559-144">[!code-vb[VbPowerPacksDataRepeaterVirtualMode#5](../../../visual-basic/developing-apps/windows-forms/codesnippet/VisualBasic/virtual-mode-in-the-datarepeater-control-visual-studio_5.vb)]
 [!code-cs[VbPowerPacksDataRepeaterVirtualMode#5](../../../visual-basic/developing-apps/windows-forms/codesnippet/CSharp/virtual-mode-in-the-datarepeater-control-visual-studio_5.cs)]</span></span>  
  
8.  <span data-ttu-id="18559-145">제어 수준 유효성 검사에 대 한 처리기를 구현할 필요에 따라는 <xref:System.Windows.Forms.Control.Validating>자식 컨트롤의 이벤트.</xref:System.Windows.Forms.Control.Validating></span><span class="sxs-lookup"><span data-stu-id="18559-145">For control-level validation, optionally implement handlers for the <xref:System.Windows.Forms.Control.Validating> events of the child controls.</span></span> <span data-ttu-id="18559-146">코드에는 다음 예와 비슷하게 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="18559-146">The code will resemble the following example.</span></span>  
  
     <span data-ttu-id="18559-147">[!code-vb[#6 VbPowerPacksDataRepeaterVirtualMode](../../../visual-basic/developing-apps/windows-forms/codesnippet/VisualBasic/virtual-mode-in-the-datarepeater-control-visual-studio_6.vb) ] 
     [!code-cs [VbPowerPacksDataRepeaterVirtualMode&#6;](../../../visual-basic/developing-apps/windows-forms/codesnippet/CSharp/virtual-mode-in-the-datarepeater-control-visual-studio_6.cs)]</span><span class="sxs-lookup"><span data-stu-id="18559-147">[!code-vb[VbPowerPacksDataRepeaterVirtualMode#6](../../../visual-basic/developing-apps/windows-forms/codesnippet/VisualBasic/virtual-mode-in-the-datarepeater-control-visual-studio_6.vb)]
 [!code-cs[VbPowerPacksDataRepeaterVirtualMode#6](../../../visual-basic/developing-apps/windows-forms/codesnippet/CSharp/virtual-mode-in-the-datarepeater-control-visual-studio_6.cs)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="18559-148">참고 항목</span><span class="sxs-lookup"><span data-stu-id="18559-148">See Also</span></span>  
 <span data-ttu-id="18559-149"><xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemValuePushed></xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemValuePushed></span><span class="sxs-lookup"><span data-stu-id="18559-149"><xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemValuePushed></span></span>   
 <span data-ttu-id="18559-150"><xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.NewItemNeeded></xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.NewItemNeeded></span><span class="sxs-lookup"><span data-stu-id="18559-150"><xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.NewItemNeeded></span></span>   
 <span data-ttu-id="18559-151"><xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemValueNeeded></xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemValueNeeded></span><span class="sxs-lookup"><span data-stu-id="18559-151"><xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemValueNeeded></span></span>   
<span data-ttu-id="18559-152"> [DataRepeater 컨트롤 소개](../../../visual-basic/developing-apps/windows-forms/introduction-to-the-datarepeater-control-visual-studio.md)</span><span class="sxs-lookup"><span data-stu-id="18559-152"> [Introduction to the DataRepeater Control](../../../visual-basic/developing-apps/windows-forms/introduction-to-the-datarepeater-control-visual-studio.md)</span></span>