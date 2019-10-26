---
ms.openlocfilehash: da1ec7908b3082fc61313cb805773aa600bc1b5d
ms.sourcegitcommit: 2e95559d957a1a942e490c5fd916df04b39d73a9
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/16/2019
ms.locfileid: "72394421"
---
### <a name="localization-resourcemanagerwithculturestringlocalizer-and-withculture-marked-obsolete"></a><span data-ttu-id="093c7-101">지역화: 사용되지 않는 것으로 표시된 ResourceManagerWithCultureStringLocalizer 및 WithCulture</span><span class="sxs-lookup"><span data-stu-id="093c7-101">Localization: ResourceManagerWithCultureStringLocalizer and WithCulture marked obsolete</span></span>

<span data-ttu-id="093c7-102">[ResourceManagerWithCultureStringLocalizer](https://github.com/aspnet/Localization/blob/43b974482c7b703c92085c6f68b3b23d8fe32720/src/Microsoft.Extensions.Localization/ResourceManagerWithCultureStringLocalizer.cs#L18) 클래스 및 [WithCulture](https://github.com/aspnet/Localization/blob/master/src/Microsoft.Extensions.Localization/ResourceManagerStringLocalizer.cs#L154-L170) 인터페이스 멤버는 특히 고유한 `IStringLocalizer` 구현을 만들 때 지역화 사용자에게 혼동의 원인이 됩니다.</span><span class="sxs-lookup"><span data-stu-id="093c7-102">The [ResourceManagerWithCultureStringLocalizer](https://github.com/aspnet/Localization/blob/43b974482c7b703c92085c6f68b3b23d8fe32720/src/Microsoft.Extensions.Localization/ResourceManagerWithCultureStringLocalizer.cs#L18) class and [WithCulture](https://github.com/aspnet/Localization/blob/master/src/Microsoft.Extensions.Localization/ResourceManagerStringLocalizer.cs#L154-L170) interface member are often sources of confusion for users of localization, especially when creating their own `IStringLocalizer` implementation.</span></span> <span data-ttu-id="093c7-103">이러한 항목은 사용자에게 `IStringLocalizer` 인스턴스가 "언어별, 리소스별"이라는 인상을 줍니다.</span><span class="sxs-lookup"><span data-stu-id="093c7-103">These items give the user the impression that an `IStringLocalizer` instance is "per-language, per-resource".</span></span> <span data-ttu-id="093c7-104">실제로 인스턴스는 "리소스별"이어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="093c7-104">In reality, the instances should only be "per-resource".</span></span> <span data-ttu-id="093c7-105">검색된 언어는 실행 시 `CultureInfo.CurrentUICulture`에 의해 결정됩니다.</span><span class="sxs-lookup"><span data-stu-id="093c7-105">The language searched for is determined by the `CultureInfo.CurrentUICulture` at execution time.</span></span> <span data-ttu-id="093c7-106">혼동의 원인을 제거하기 위해 API는 ASP.NET Core 3.0 Preview 3에서 사용되지 않는 것으로 표시되었습니다.</span><span class="sxs-lookup"><span data-stu-id="093c7-106">To eliminate the source of confusion, the APIs were marked as obsolete in ASP.NET Core 3.0 Preview 3.</span></span> <span data-ttu-id="093c7-107">API는 이후 릴리스에서 제거됩니다.</span><span class="sxs-lookup"><span data-stu-id="093c7-107">The APIs will be removed in a future release.</span></span>

<span data-ttu-id="093c7-108">컨텍스트는 [aspnet/AspNetCore#3324](https://github.com/aspnet/AspNetCore/issues/3324)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="093c7-108">For context, see [aspnet/AspNetCore#3324](https://github.com/aspnet/AspNetCore/issues/3324).</span></span> <span data-ttu-id="093c7-109">자세한 내용은 [aspnet/AspNetCore#7756](https://github.com/aspnet/AspNetCore/issues/7756)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="093c7-109">For discussion, see [aspnet/AspNetCore#7756](https://github.com/aspnet/AspNetCore/issues/7756).</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="093c7-110">도입된 버전</span><span class="sxs-lookup"><span data-stu-id="093c7-110">Version introduced</span></span>

<span data-ttu-id="093c7-111">3.0</span><span class="sxs-lookup"><span data-stu-id="093c7-111">3.0</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="093c7-112">이전 동작</span><span class="sxs-lookup"><span data-stu-id="093c7-112">Old behavior</span></span>

<span data-ttu-id="093c7-113">메서드가 `Obsolete`로 표시되지 않았습니다.</span><span class="sxs-lookup"><span data-stu-id="093c7-113">Methods weren't marked as `Obsolete`.</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="093c7-114">새 동작</span><span class="sxs-lookup"><span data-stu-id="093c7-114">New behavior</span></span>

<span data-ttu-id="093c7-115">메서드는 `Obsolete`로 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="093c7-115">Methods are marked `Obsolete`.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="093c7-116">변경 이유</span><span class="sxs-lookup"><span data-stu-id="093c7-116">Reason for change</span></span>

<span data-ttu-id="093c7-117">API는 권장되지 않는 사용 사례를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="093c7-117">The APIs represented a use case that isn't recommended.</span></span> <span data-ttu-id="093c7-118">지역화 디자인에 대한 혼동이 있었습니다.</span><span class="sxs-lookup"><span data-stu-id="093c7-118">There was confusion about the design of localization.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="093c7-119">권장 작업</span><span class="sxs-lookup"><span data-stu-id="093c7-119">Recommended action</span></span>

<span data-ttu-id="093c7-120">대신 `ResourceManagerStringLocalizer`를 사용하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="093c7-120">The recommendation is to use `ResourceManagerStringLocalizer` instead.</span></span> <span data-ttu-id="093c7-121">`CurrentCulture`에서 문화권을 설정하도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="093c7-121">Let the culture be set by the `CurrentCulture`.</span></span> <span data-ttu-id="093c7-122">옵션이 아닌 경우 [ResourceManagerWithCultureStringLocalizer](https://github.com/aspnet/Localization/blob/43b974482c7b703c92085c6f68b3b23d8fe32720/src/Microsoft.Extensions.Localization/ResourceManagerWithCultureStringLocalizer.cs#L18) 복사본을 만들고 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="093c7-122">If that isn't an option, create and use a copy of [ResourceManagerWithCultureStringLocalizer](https://github.com/aspnet/Localization/blob/43b974482c7b703c92085c6f68b3b23d8fe32720/src/Microsoft.Extensions.Localization/ResourceManagerWithCultureStringLocalizer.cs#L18).</span></span>

#### <a name="category"></a><span data-ttu-id="093c7-123">범주</span><span class="sxs-lookup"><span data-stu-id="093c7-123">Category</span></span>

<span data-ttu-id="093c7-124">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="093c7-124">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="093c7-125">영향을 받는 API</span><span class="sxs-lookup"><span data-stu-id="093c7-125">Affected APIs</span></span>

- <xref:Microsoft.Extensions.Localization.ResourceManagerWithCultureStringLocalizer>
- <xref:Microsoft.Extensions.Localization.ResourceManagerStringLocalizer.WithCulture%2A?displayProperty=nameWithType>

<!--

#### Affected APIs

- `T:Microsoft.Extensions.Localization.ResourceManagerWithCultureStringLocalizer`
- `Overload:Microsoft.Extensions.Localization.ResourceManagerStringLocalizer.WithCulture`

-->