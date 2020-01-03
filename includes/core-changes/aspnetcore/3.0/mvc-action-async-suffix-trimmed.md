---
ms.openlocfilehash: 503d61cb86c83e2f32ad40c60a127ae255ef71b0
ms.sourcegitcommit: 5a28f8eb071fcc09b045b0c4ae4b96898673192e
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/31/2019
ms.locfileid: "73198508"
---
### <a name="mvc-async-suffix-trimmed-from-controller-action-names"></a><span data-ttu-id="56770-101">MVC: 컨트롤러 작업 이름에서 잘린 비동기 접미사</span><span class="sxs-lookup"><span data-stu-id="56770-101">MVC: Async suffix trimmed from controller action names</span></span>

<span data-ttu-id="56770-102">[aspnet/AspNetCore#4849](https://github.com/aspnet/AspNetCore/issues/4849)를 해결하는 과정의 일부로, ASP.NET Core MVC는 기본적으로 작업 이름에서 `Async` 접미사를 잘라냅니다.</span><span class="sxs-lookup"><span data-stu-id="56770-102">As part of addressing [aspnet/AspNetCore#4849](https://github.com/aspnet/AspNetCore/issues/4849), ASP.NET Core MVC trims the suffix `Async` from action names by default.</span></span> <span data-ttu-id="56770-103">ASP.NET Core 3.0부터 이 변경 내용은 라우팅 및 링크 생성 모두에 영향을 줍니다.</span><span class="sxs-lookup"><span data-stu-id="56770-103">Starting with ASP.NET Core 3.0, this change affects both routing and link generation.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="56770-104">도입된 버전</span><span class="sxs-lookup"><span data-stu-id="56770-104">Version introduced</span></span>

<span data-ttu-id="56770-105">3.0</span><span class="sxs-lookup"><span data-stu-id="56770-105">3.0</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="56770-106">이전 동작</span><span class="sxs-lookup"><span data-stu-id="56770-106">Old behavior</span></span>

<span data-ttu-id="56770-107">다음 ASP.NET Core MVC 컨트롤러를 고려하세요.</span><span class="sxs-lookup"><span data-stu-id="56770-107">Consider the following ASP.NET Core MVC controller:</span></span>

```csharp
public class ProductController : Controller
{
    public async IActionResult ListAsync()
    {
        var model = await DbContext.Products.ToListAsync();
        return View(model);
    }
}
```

<span data-ttu-id="56770-108">작업은 `Product/ListAsync`를 통해 라우팅할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="56770-108">The action is routable via `Product/ListAsync`.</span></span> <span data-ttu-id="56770-109">링크 생성을 위해서는 `Async` 접미사를 지정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="56770-109">Link generation requires specifying the `Async` suffix.</span></span> <span data-ttu-id="56770-110">예:</span><span class="sxs-lookup"><span data-stu-id="56770-110">For example:</span></span>

```cshtml
<a asp-controller="Product" asp-action="ListAsync">List</a>
```

#### <a name="new-behavior"></a><span data-ttu-id="56770-111">새 동작</span><span class="sxs-lookup"><span data-stu-id="56770-111">New behavior</span></span>

<span data-ttu-id="56770-112">ASP.NET Core 3.0에서 작업은 `Product/List`를 통해 라우팅할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="56770-112">In ASP.NET Core 3.0, the action is routable via `Product/List`.</span></span> <span data-ttu-id="56770-113">링크 생성 코드는 `Async` 접미사를 생략해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="56770-113">Link generation code should omit the `Async` suffix.</span></span> <span data-ttu-id="56770-114">예:</span><span class="sxs-lookup"><span data-stu-id="56770-114">For example:</span></span>

```cshtml
<a asp-controller="Product" asp-action="List">List</a>
```

<span data-ttu-id="56770-115">이 변경 내용은 `[ActionName]` 특성을 사용하여 지정된 이름에는 영향을 주지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="56770-115">This change doesn't affect names specified using the `[ActionName]` attribute.</span></span> <span data-ttu-id="56770-116">`Startup.ConfigureServices`에서 `MvcOptions.SuppressAsyncSuffixInActionNames`를 `false`로 설정하여 새 동작을 사용하지 않도록 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="56770-116">The new behavior can be disabled by setting `MvcOptions.SuppressAsyncSuffixInActionNames` to `false` in `Startup.ConfigureServices`:</span></span>

```csharp
services.AddMvc(options =>
{
   options.SuppressAsyncSuffixInActionNames = false;
});
```

#### <a name="reason-for-change"></a><span data-ttu-id="56770-117">변경 이유</span><span class="sxs-lookup"><span data-stu-id="56770-117">Reason for change</span></span>

<span data-ttu-id="56770-118">규칙에 따라 비동기 .NET 메서드는 `Async`로 접미사가 붙습니다.</span><span class="sxs-lookup"><span data-stu-id="56770-118">By convention, asynchronous .NET methods are suffixed with `Async`.</span></span> <span data-ttu-id="56770-119">그러나 메서드가 MVC 작업을 정의할 때 `Async` 접미사를 사용하는 것은 바람직하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="56770-119">However, when a method defines an MVC action, it's undesirable to use the `Async` suffix.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="56770-120">권장 작업</span><span class="sxs-lookup"><span data-stu-id="56770-120">Recommended action</span></span>

<span data-ttu-id="56770-121">앱이 이름의 `Async` 접미사를 유지하는 MVC 작업에 의존하는 경우 다음 완화 방법 중 하나를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="56770-121">If your app depends on MVC actions preserving the name's `Async` suffix, choose one of the following mitigations:</span></span>

- <span data-ttu-id="56770-122">`[ActionName]` 특성을 사용하여 원래 이름을 유지합니다.</span><span class="sxs-lookup"><span data-stu-id="56770-122">Use the `[ActionName]` attribute to preserve the original name.</span></span>
- <span data-ttu-id="56770-123">`Startup.ConfigureServices`에서 `MvcOptions.SuppressAsyncSuffixInActionNames`를 `false`로 설정하여 전체 이름 바꾸기를 사용하지 않도록 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="56770-123">Disable the renaming entirely by setting `MvcOptions.SuppressAsyncSuffixInActionNames` to `false` in `Startup.ConfigureServices`:</span></span>

```csharp
services.AddMvc(options =>
{
   options.SuppressAsyncSuffixInActionNames = false;
});
```

#### <a name="category"></a><span data-ttu-id="56770-124">범주</span><span class="sxs-lookup"><span data-stu-id="56770-124">Category</span></span>

<span data-ttu-id="56770-125">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="56770-125">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="56770-126">영향을 받는 API</span><span class="sxs-lookup"><span data-stu-id="56770-126">Affected APIs</span></span>

<span data-ttu-id="56770-127">없음</span><span class="sxs-lookup"><span data-stu-id="56770-127">None</span></span>

<!-- 

#### Affected APIs

Not detectable via API analysis

-->