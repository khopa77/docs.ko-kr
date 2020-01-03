---
ms.openlocfilehash: a56c5fc32b5fd274d5da0d9b295918f5ea3b345e
ms.sourcegitcommit: 2e95559d957a1a942e490c5fd916df04b39d73a9
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/16/2019
ms.locfileid: "72394061"
---
### <a name="signalr-hubconnection-resetsendping-and-resettimeout-methods-removed"></a><span data-ttu-id="4b625-101">SignalR: HubConnection ResetSendPing 및 ResetTimeout 메서드가 제거됨</span><span class="sxs-lookup"><span data-stu-id="4b625-101">SignalR: HubConnection ResetSendPing and ResetTimeout methods removed</span></span>

<span data-ttu-id="4b625-102">`ResetSendPing` 및 `ResetTimeout` 메서드가 SignalR `HubConnection` API에서 제거되었습니다.</span><span class="sxs-lookup"><span data-stu-id="4b625-102">The `ResetSendPing` and `ResetTimeout` methods were removed from the SignalR `HubConnection` API.</span></span> <span data-ttu-id="4b625-103">이러한 메서드는 원래 내부용으로만 사용되었지만 ASP.NET Core 2.2에서 공개되었습니다.</span><span class="sxs-lookup"><span data-stu-id="4b625-103">These methods were originally intended only for internal use but were made public in ASP.NET Core 2.2.</span></span> <span data-ttu-id="4b625-104">이러한 메서드는 ASP.NET Core 3.0 Preview 4 릴리스부터 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="4b625-104">These methods won't be available starting in the ASP.NET Core 3.0 Preview 4 release.</span></span> <span data-ttu-id="4b625-105">자세한 내용은 [aspnet/AspNetCore#8543](https://github.com/aspnet/AspNetCore/issues/8543)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="4b625-105">For discussion, see [aspnet/AspNetCore#8543](https://github.com/aspnet/AspNetCore/issues/8543).</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="4b625-106">도입된 버전</span><span class="sxs-lookup"><span data-stu-id="4b625-106">Version introduced</span></span>

<span data-ttu-id="4b625-107">3.0</span><span class="sxs-lookup"><span data-stu-id="4b625-107">3.0</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="4b625-108">이전 동작</span><span class="sxs-lookup"><span data-stu-id="4b625-108">Old behavior</span></span>

<span data-ttu-id="4b625-109">API를 사용할 수 있었습니다.</span><span class="sxs-lookup"><span data-stu-id="4b625-109">APIs were available.</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="4b625-110">새 동작</span><span class="sxs-lookup"><span data-stu-id="4b625-110">New behavior</span></span>

<span data-ttu-id="4b625-111">API가 제거되었습니다.</span><span class="sxs-lookup"><span data-stu-id="4b625-111">APIs are removed.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="4b625-112">변경 이유</span><span class="sxs-lookup"><span data-stu-id="4b625-112">Reason for change</span></span>

<span data-ttu-id="4b625-113">이러한 메서드는 원래 내부용으로만 사용되었지만 ASP.NET Core 2.2에서 공개되었습니다.</span><span class="sxs-lookup"><span data-stu-id="4b625-113">These methods were originally intended only for internal use but were made public in ASP.NET Core 2.2.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="4b625-114">권장 작업</span><span class="sxs-lookup"><span data-stu-id="4b625-114">Recommended action</span></span>

<span data-ttu-id="4b625-115">이러한 메서드를 사용하지 마세요.</span><span class="sxs-lookup"><span data-stu-id="4b625-115">Don't use these methods.</span></span>

#### <a name="category"></a><span data-ttu-id="4b625-116">범주</span><span class="sxs-lookup"><span data-stu-id="4b625-116">Category</span></span>

<span data-ttu-id="4b625-117">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="4b625-117">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="4b625-118">영향을 받는 API</span><span class="sxs-lookup"><span data-stu-id="4b625-118">Affected APIs</span></span>

- <xref:Microsoft.AspNetCore.SignalR.Client.HubConnection.ResetSendPing?displayProperty=nameWithType>
- <xref:Microsoft.AspNetCore.SignalR.Client.HubConnection.ResetTimeout?displayProperty=nameWithType>

<!--

#### Affected APIs

- `M:Microsoft.AspNetCore.SignalR.Client.HubConnection.ResetSendPing`
- `M:Microsoft.AspNetCore.SignalR.Client.HubConnection.ResetTimeout`

-->