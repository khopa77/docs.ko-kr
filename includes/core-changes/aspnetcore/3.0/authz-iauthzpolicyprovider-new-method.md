---
ms.openlocfilehash: a16d443a37fb0bb5f6bdc4a39e7dcb4f91c54ead
ms.sourcegitcommit: 2e95559d957a1a942e490c5fd916df04b39d73a9
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/16/2019
ms.locfileid: "72394248"
---
### <a name="authorization-iauthorizationpolicyprovider-implementations-require-new-method"></a><span data-ttu-id="cd5ec-101">권한 부여: IAuthorizationPolicyProvider 구현에는 새 메서드가 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="cd5ec-101">Authorization: IAuthorizationPolicyProvider implementations require new method</span></span>

<span data-ttu-id="cd5ec-102">ASP.NET Core 3.0에서는 새 `GetFallbackPolicyAsync` 메서드가 `IAuthorizationPolicyProvider`에 추가되었습니다.</span><span class="sxs-lookup"><span data-stu-id="cd5ec-102">In ASP.NET Core 3.0, a new `GetFallbackPolicyAsync` method was added to `IAuthorizationPolicyProvider`.</span></span> <span data-ttu-id="cd5ec-103">이 대체 정책은 정책이 지정되지 않은 경우 권한 부여 미들웨어에서 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="cd5ec-103">This fallback policy is used by the authorization middleware when no policy is specified.</span></span>

<span data-ttu-id="cd5ec-104">자세한 내용은 [aspnet/AspNetCore#9759](https://github.com/aspnet/AspNetCore/pull/9759)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="cd5ec-104">For more information, see [aspnet/AspNetCore#9759](https://github.com/aspnet/AspNetCore/pull/9759).</span></span> 

#### <a name="version-introduced"></a><span data-ttu-id="cd5ec-105">도입된 버전</span><span class="sxs-lookup"><span data-stu-id="cd5ec-105">Version introduced</span></span>

<span data-ttu-id="cd5ec-106">3.0</span><span class="sxs-lookup"><span data-stu-id="cd5ec-106">3.0</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="cd5ec-107">이전 동작</span><span class="sxs-lookup"><span data-stu-id="cd5ec-107">Old behavior</span></span>

<span data-ttu-id="cd5ec-108">`IAuthorizationPolicyProvider`의 구현에는 `GetFallbackPolicyAsync` 메서드가 필요하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="cd5ec-108">Implementations of `IAuthorizationPolicyProvider` didn't require a `GetFallbackPolicyAsync` method.</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="cd5ec-109">새 동작</span><span class="sxs-lookup"><span data-stu-id="cd5ec-109">New behavior</span></span>

<span data-ttu-id="cd5ec-110">`IAuthorizationPolicyProvider`의 구현에는 `GetFallbackPolicyAsync` 메서드가 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="cd5ec-110">Implementations of `IAuthorizationPolicyProvider` require a `GetFallbackPolicyAsync` method.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="cd5ec-111">변경 이유</span><span class="sxs-lookup"><span data-stu-id="cd5ec-111">Reason for change</span></span>

<span data-ttu-id="cd5ec-112">정책이 지정되지 않은 경우 새 `AuthorizationMiddleware`를 사용할 수 있는 새로운 메서드가 필요했습니다.</span><span class="sxs-lookup"><span data-stu-id="cd5ec-112">A new method was needed for the new `AuthorizationMiddleware` to use when no policy is specified.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="cd5ec-113">권장 작업</span><span class="sxs-lookup"><span data-stu-id="cd5ec-113">Recommended action</span></span>

<span data-ttu-id="cd5ec-114">`IAuthorizationPolicyProvider`의 구현에 `GetFallbackPolicyAsync` 메서드를 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="cd5ec-114">Add the `GetFallbackPolicyAsync` method to your implementations of `IAuthorizationPolicyProvider`.</span></span>

#### <a name="category"></a><span data-ttu-id="cd5ec-115">범주</span><span class="sxs-lookup"><span data-stu-id="cd5ec-115">Category</span></span>

<span data-ttu-id="cd5ec-116">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="cd5ec-116">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="cd5ec-117">영향을 받는 API</span><span class="sxs-lookup"><span data-stu-id="cd5ec-117">Affected APIs</span></span>

<xref:Microsoft.AspNetCore.Authorization.IAuthorizationPolicyProvider?displayProperty=fullName>

<!-- 

#### Affected APIs

`T:Microsoft.AspNetCore.Authorization.IAuthorizationPolicyProvider`

-->