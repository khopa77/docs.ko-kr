---
title: Azure Monitor
description: Azure Monitor를 사용 하 여 시스템에 대 한 가시성을 확보 합니다.
ms.date: 09/23/2019
ms.openlocfilehash: 27503627217c71e4090674945830f6332b202a5b
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/21/2019
ms.locfileid: "74281644"
---
# <a name="azure-monitor"></a><span data-ttu-id="fc376-103">Azure Monitor</span><span class="sxs-lookup"><span data-stu-id="fc376-103">Azure Monitor</span></span>

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

<span data-ttu-id="fc376-104">다른 클라우드 공급자는 Azure에 있는 것과 같은 클라우드 응용 프로그램 모니터링 솔루션을 포함 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="fc376-104">No other cloud provider has as mature of a cloud application monitoring solution as that found in Azure.</span></span> <span data-ttu-id="fc376-105">Azure Monitor는 시스템 상태에 대 한 가시성을 제공 하 고 응용 프로그램의 문제 및 최적화에 대 한 통찰력을 제공 하도록 설계 된 도구 컬렉션의 포괄적인 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="fc376-105">Azure Monitor is an umbrella name for a collection of tools designed to provide visibility into the state of your system, insights into any problems and optimization of your application.</span></span>

<span data-ttu-id="fc376-106">클라우드 네이티브 응용 프로그램이 작동 하는 방식에 대 한 통찰력을 제공 하는 도구에 대 한 컬렉션인 Azure Monitor를 ![합니다. **그림 7-9**을](./media/azure-monitor.png)
합니다.</span><span class="sxs-lookup"><span data-stu-id="fc376-106">![Azure Monitor, a collection to tools to provide insight into how a cloud-native application is functioning.](./media/azure-monitor.png)
**Figure 7-9**.</span></span> <span data-ttu-id="fc376-107">클라우드 네이티브 응용 프로그램이 작동 하는 방식에 대 한 정보를 제공 하는 도구에 대 한 컬렉션을 Azure Monitor 합니다.</span><span class="sxs-lookup"><span data-stu-id="fc376-107">Azure Monitor, a collection to tools to provide insight into how a cloud-native application is functioning.</span></span>

## <a name="gathering-logs-and-metrics"></a><span data-ttu-id="fc376-108">로그 및 메트릭 수집</span><span class="sxs-lookup"><span data-stu-id="fc376-108">Gathering logs and metrics</span></span>

<span data-ttu-id="fc376-109">모니터링 솔루션의 첫 번째 단계는 최대한 많은 데이터를 수집 하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="fc376-109">The first step in any monitoring solution is to gather as much data as possible.</span></span> <span data-ttu-id="fc376-110">수집할 수 있는 데이터가 많을 수록 얻을 수 있는 정보를 심층적으로 파악할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fc376-110">The more data that can be gathered, the deeper the insights that can be obtained.</span></span> <span data-ttu-id="fc376-111">시스템을 계측 하는 것은 일반적으로 어렵습니다.</span><span class="sxs-lookup"><span data-stu-id="fc376-111">Instrumenting systems has traditionally been difficult.</span></span> <span data-ttu-id="fc376-112">SNMP (Simple Network Management Protocol)는 컴퓨터 수준 정보를 수집 하기 위한 골드 표준 프로토콜 이지만 많은 지식과 구성이 필요 합니다.</span><span class="sxs-lookup"><span data-stu-id="fc376-112">Simple Network Management Protocol (SNMP) was the gold standard protocol for collecting machine level information but it required a great deal of knowledge and configuring.</span></span> <span data-ttu-id="fc376-113">다행히 가장 일반적인 메트릭이 Azure Monitor에 의해 자동으로 수집 되기 때문에 대부분의이 하드 작업은 제거 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="fc376-113">Fortunately, much of this hard work has been eliminated as the most common metrics are gathered automatically by Azure Monitor.</span></span>

<span data-ttu-id="fc376-114">응용 프로그램 수준 메트릭과 이벤트는 배포 중인 응용 프로그램에 로컬 이므로 자동으로 계측할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="fc376-114">Application level metrics and events aren't possible to instrument automatically because they're local to the application being deployed.</span></span> <span data-ttu-id="fc376-115">이러한 메트릭을 수집 하기 위해 고객이 등록 하거나 주문을 완료 하는 경우와 같이 이러한 정보를 직접 보고 하는 데 [사용할 수 있는 sdk 및 api](https://docs.microsoft.com/azure/azure-monitor/app/api-custom-events-metrics) 가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fc376-115">In order to gather these metrics, there are [SDKs and APIs available](https://docs.microsoft.com/azure/azure-monitor/app/api-custom-events-metrics) to directly report such information, such as when a customer signs up or completes an order.</span></span> <span data-ttu-id="fc376-116">예외는 Application Insights를 통해 캡처 및 Azure Monitor 다시 보고 될 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fc376-116">Exceptions can also be captured and reported back into Azure Monitor via Application Insights.</span></span> <span data-ttu-id="fc376-117">Sdk는 Go, Python, JavaScript 및 .NET 언어를 포함 하 여 클라우드 네이티브 응용 프로그램에서 발견 된 대부분의 언어를 지원 합니다.</span><span class="sxs-lookup"><span data-stu-id="fc376-117">The SDKs support most every language found in Cloud Native Applications including Go, Python, JavaScript, and the .NET languages.</span></span>

<span data-ttu-id="fc376-118">응용 프로그램의 상태에 대 한 정보를 수집 하는 궁극적인 목표는 최종 사용자에 게 훌륭한 환경이 있는지 확인 하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="fc376-118">The ultimate goal of gathering information about the state of your application is to ensure that your end users have a good experience.</span></span> <span data-ttu-id="fc376-119">사용자에 게 [외부 웹 테스트를](https://docs.microsoft.com/azure/azure-monitor/app/monitor-web-app-availability)수행 하는 것 보다 문제가 발생 하는지 어떻게 알 수 있나요?</span><span class="sxs-lookup"><span data-stu-id="fc376-119">What better way to tell if users are experiencing issues than doing [outside-in web tests](https://docs.microsoft.com/azure/azure-monitor/app/monitor-web-app-availability)?</span></span> <span data-ttu-id="fc376-120">이러한 테스트는 전 세계의 위치에서 웹 사이트를 ping 하거나 에이전트가 사이트에 로그인 하 고 작업을 수행 하는 것과 관련 된 것 처럼 간단할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fc376-120">These tests can be as simple as pinging your website from locations around the world or as involved as having agents log into the site and do actions.</span></span>

## <a name="reporting-data"></a><span data-ttu-id="fc376-121">보고 데이터</span><span class="sxs-lookup"><span data-stu-id="fc376-121">Reporting data</span></span>

<span data-ttu-id="fc376-122">데이터를 수집한 후에는 데이터를 조작 하 고 요약 하 여 차트에 표시할 수 있습니다 .이를 통해 사용자는 문제가 발생 한 시기를 즉시 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fc376-122">Once the data is gathered, it can be manipulated, summarized, and plotted into charts, which allow users to instantly see when there are problems.</span></span> <span data-ttu-id="fc376-123">이러한 차트를 대시보드 또는 통합 문서에 수집할 수 있습니다 .이 보고서는 시스템의 일부 측면에 대해 이야기를 제공 하도록 설계 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="fc376-123">These charts can be gathered into dashboards or into Workbooks, a multi-page report designed to tell a story about some aspect of the system.</span></span>

<span data-ttu-id="fc376-124">일부 인공 지능 또는 기계 학습 없이 최신 응용 프로그램을 완료할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="fc376-124">No modern application would be complete without some artificial intelligence or machine learning.</span></span> <span data-ttu-id="fc376-125">이를 위해 데이터를 Azure의 다양 한 기계 학습 도구에 전달 하 여 다른 방법으로는 숨기는 추세와 정보를 추출할 수 [있습니다](https://www.youtube.com/watch?v=Cuza-I1g9tw) .</span><span class="sxs-lookup"><span data-stu-id="fc376-125">To this end, data [can be passed](https://www.youtube.com/watch?v=Cuza-I1g9tw) to the various machine learning tools in Azure to allow you to extract trends and information that would otherwise be hidden.</span></span>

<span data-ttu-id="fc376-126">Application Insights는 레코드를 찾고 요약 하 고 차트를 그리는 데 사용할 수 있는 Kusto 라는 강력한 쿼리 언어를 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="fc376-126">Application Insights provides a powerful query language called Kusto that can be used to find records, summarize them, and even plot charts.</span></span> <span data-ttu-id="fc376-127">예를 들어이 쿼리는 11 월 2007 월의 모든 레코드를 찾고, 상태별로 그룹화 하 고, 상위 10 개를 원형 차트로 플롯 합니다.</span><span class="sxs-lookup"><span data-stu-id="fc376-127">For instance, this query will locate all the records for the month of November 2007, group them by state, and plot the top 10 as a pie chart.</span></span>

```kusto
StormEvents
| where StartTime >= datetime(2007-11-01) and StartTime < datetime(2007-12-01)
| summarize count() by State
| top 10 by count_
| render piechart
```

<span data-ttu-id="fc376-128">**그림 7-10**](./media/azure-monitor.png)
Application Insights 쿼리의 결과를 ![합니다.</span><span class="sxs-lookup"><span data-stu-id="fc376-128">![The result of the Application Insights Query](./media/azure-monitor.png)
**Figure 7-10**.</span></span> <span data-ttu-id="fc376-129">Application Insights 쿼리의 결과입니다.</span><span class="sxs-lookup"><span data-stu-id="fc376-129">The result of the Application Insights Query.</span></span>

<span data-ttu-id="fc376-130">[Kusto](https://dataexplorer.azure.com/clusters/help/databases/Samples) 쿼리를 시험해 볼 수 있습니다 .이는 한 시간 또는 두 번만 소요 될 수 있는 훌륭한 장소입니다.</span><span class="sxs-lookup"><span data-stu-id="fc376-130">There is a [playground for experimenting with Kusto](https://dataexplorer.azure.com/clusters/help/databases/Samples) queries, which is a fantastic place to spend an hour or two.</span></span> <span data-ttu-id="fc376-131">[예제 쿼리](https://docs.microsoft.com/azure/kusto/query/samples) 읽기가 유용할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fc376-131">Reading [sample queries](https://docs.microsoft.com/azure/kusto/query/samples) can also be instructive.</span></span>

## <a name="dashboards"></a><span data-ttu-id="fc376-132">대시보드</span><span class="sxs-lookup"><span data-stu-id="fc376-132">Dashboards</span></span>

<span data-ttu-id="fc376-133">Azure Monitor에서 정보를 노출 하는 데 사용할 수 있는 여러 가지 대시보드 기술이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fc376-133">There are several different dashboard technologies that may be used to surface the information from Azure Monitor.</span></span> <span data-ttu-id="fc376-134">아마도 Application Insights에서 쿼리를 실행 하 고 [데이터를 차트에 그리는](https://docs.microsoft.com/azure/azure-monitor/learn/tutorial-app-dashboards)것이 가장 간단 합니다.</span><span class="sxs-lookup"><span data-stu-id="fc376-134">Perhaps the simplest is to just run queries in Application Insights and [plot the data into a chart](https://docs.microsoft.com/azure/azure-monitor/learn/tutorial-app-dashboards).</span></span>

<span data-ttu-id="fc376-135">**그림 7-11**](./media/azure-monitor.png)
주 Azure 대시보드에 포함 된 Application Insights 차트의 예를 ![합니다.</span><span class="sxs-lookup"><span data-stu-id="fc376-135">![An example of Application Insights charts embedded in the main Azure Dashboard](./media/azure-monitor.png)
**Figure 7-11**.</span></span> <span data-ttu-id="fc376-136">기본 Azure 대시보드에 포함 된 Application Insights 차트의 예입니다.</span><span class="sxs-lookup"><span data-stu-id="fc376-136">An example of Application Insights charts embedded in the main Azure Dashboard.</span></span>

<span data-ttu-id="fc376-137">그런 다음 이러한 차트를 대시보드 기능을 사용 하 여 적절 하 게 Azure Portal에 포함할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fc376-137">These charts can then be embedded in the Azure portal proper through use of the dashboard feature.</span></span> <span data-ttu-id="fc376-138">여러 가지 데이터 계층으로 드릴 다운할 수 있는 것과 같이 이루기 요구 사항이 더 많은 사용자에 게는 데이터를 [Power BI](https://powerbi.microsoft.com/)수 Azure Monitor.</span><span class="sxs-lookup"><span data-stu-id="fc376-138">For users with more exacting requirements such as being able to drill down into several tiers of data Azure Monitor data is available to [Power BI](https://powerbi.microsoft.com/).</span></span> <span data-ttu-id="fc376-139">Power BI은 다양 한 데이터 원본의 데이터를 집계할 수 있는 업계 최고의 엔터프라이즈 클래스, 비즈니스 인텔리전스 도구입니다.</span><span class="sxs-lookup"><span data-stu-id="fc376-139">Power BI is an industry-leading, enterprise class, business intelligence tool that can aggregate data from many different data sources.</span></span>

<span data-ttu-id="fc376-140">**그림 7-12**](./media/azure-monitor.png)
예제 Power BI 대시보드를 ![합니다.</span><span class="sxs-lookup"><span data-stu-id="fc376-140">![An example Power BI dashboard](./media/azure-monitor.png)
**Figure 7-12**.</span></span> <span data-ttu-id="fc376-141">Power BI 대시보드의 예입니다.</span><span class="sxs-lookup"><span data-stu-id="fc376-141">An example Power BI dashboard.</span></span>

## <a name="alerts"></a><span data-ttu-id="fc376-142">,</span><span class="sxs-lookup"><span data-stu-id="fc376-142">Alerts</span></span>

<span data-ttu-id="fc376-143">경우에 따라 데이터 대시보드가 충분 하지 않을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fc376-143">Sometimes, having data dashboards is insufficient.</span></span> <span data-ttu-id="fc376-144">대시보드를 시청 하기 위해 아무도 해제 되지 않은 경우 문제가 해결 될 때까지 몇 시간이 걸릴 수 있습니다. 또는 검색 하기도 합니다.</span><span class="sxs-lookup"><span data-stu-id="fc376-144">If nobody is awake to watch the dashboards, then it can still be many hours before a problem is addressed, or even detected.</span></span> <span data-ttu-id="fc376-145">이를 위해 Azure Monitor에는 상위 [경고 솔루션](https://docs.microsoft.com/azure/azure-monitor/platform/alerts-overview)도 제공 됩니다.</span><span class="sxs-lookup"><span data-stu-id="fc376-145">To this end, Azure Monitor also provides a top notch [alerting solution](https://docs.microsoft.com/azure/azure-monitor/platform/alerts-overview).</span></span> <span data-ttu-id="fc376-146">경고는 다음과 같은 다양 한 조건에 의해 트리거될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fc376-146">Alerts can be triggered by a wide range of conditions including:</span></span>

- <span data-ttu-id="fc376-147">메트릭 값</span><span class="sxs-lookup"><span data-stu-id="fc376-147">Metric values</span></span>
- <span data-ttu-id="fc376-148">로그 검색 쿼리</span><span class="sxs-lookup"><span data-stu-id="fc376-148">Log search queries</span></span>
- <span data-ttu-id="fc376-149">활동 로그 이벤트</span><span class="sxs-lookup"><span data-stu-id="fc376-149">Activity Log events</span></span>
- <span data-ttu-id="fc376-150">기본 Azure 플랫폼의 상태</span><span class="sxs-lookup"><span data-stu-id="fc376-150">Health of the underlying Azure platform</span></span>
- <span data-ttu-id="fc376-151">웹 사이트 가용성 테스트</span><span class="sxs-lookup"><span data-stu-id="fc376-151">Tests for web site availability</span></span>

<span data-ttu-id="fc376-152">트리거될 때 경고는 다양 한 작업을 수행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fc376-152">When triggered, the alerts can perform a wide variety of tasks.</span></span> <span data-ttu-id="fc376-153">간단한 쪽에서 경고는 메일 그룹에 전자 메일 알림을 보내거나 개인에 게 문자 메시지를 보낼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fc376-153">On the simple side, the alerts may just send an e-mail notification to a mailing list or a text message to an individual.</span></span> <span data-ttu-id="fc376-154">추가 관련 경고는 특정 응용 프로그램에 대 한 호출에 대 한 사용자를 인식 하는 PagerDuty와 같은 도구에서 워크플로를 트리거할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fc376-154">More involved alerts might trigger a workflow in a tool such as PagerDuty, which is aware of who is on call for a particular application.</span></span> <span data-ttu-id="fc376-155">경고는 워크플로에 대 한 무제한 가능성의 잠금 해제 [Microsoft Flow](https://flow.microsoft.com/) 작업을 트리거할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fc376-155">Alerts can trigger actions in [Microsoft Flow](https://flow.microsoft.com/) unlocking near limitless possibilities for workflows.</span></span>

<span data-ttu-id="fc376-156">경고가 일반적인 원인으로 식별 되므로 경고를 해결 하기 위해 수행 해야 하는 단계의 일반적인 원인에 대 한 세부 정보를 사용 하 여 경고를 향상 시킬 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fc376-156">As common causes of alerts are identified, the alerts can be enhanced with details about the common causes of the alerts and the steps to take to resolve them.</span></span> <span data-ttu-id="fc376-157">고성능 클라우드 네이티브 응용 프로그램 배포는 크기 집합에서 실패 한 노드 제거 또는 자동 크기 조정 작업 트리거 등의 작업을 수행 하는 자동 복구 작업을 시작 하도록 선택할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fc376-157">Highly mature Cloud Native Application deployments may opt to kick off self-healing tasks, which perform actions such as removing failing nodes from a scale set or triggering an autoscaling activity.</span></span> <span data-ttu-id="fc376-158">결국 오전 2 시에 호출 직원의 절전 모드를 해제 하 여 라이브 사이트 문제를 해결 하는 데 더 이상 필요 하지 않을 수 있습니다. 시스템은 다음 날에 도착할 때까지 보완 하거나 최소 limp 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fc376-158">Eventually it may no longer be necessary to wake up on-call personnel at 2AM to resolve a live-site issue as the system will be able to adjust itself to compensate or at least limp along until somebody arrives at work the next morning.</span></span>

<span data-ttu-id="fc376-159">Azure Monitor는 자동으로 기계 학습을 활용 하 여 배포 된 응용 프로그램의 일반 운영 매개 변수를 이해 합니다.</span><span class="sxs-lookup"><span data-stu-id="fc376-159">Azure Monitor automatically leverages machine learning to understand the normal operating parameters of deployed applications.</span></span> <span data-ttu-id="fc376-160">이렇게 하면 일반적인 매개 변수 외부에서 작동 하는 서비스를 검색할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fc376-160">This enables it to detect services that are operating outside of their normal parameters.</span></span> <span data-ttu-id="fc376-161">예를 들어 사이트의 일반적인 평일 트래픽은 분당 1만 요청 일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fc376-161">For instance, the typical weekday traffic on the site might be 10,000 requests per minute.</span></span> <span data-ttu-id="fc376-162">그런 다음 지정 된 주에 갑자기 요청 수가 분당 매우 이례적인 2만 요청에 도달 합니다.</span><span class="sxs-lookup"><span data-stu-id="fc376-162">And then, on a given week, suddenly the number of requests hits a highly unusual 20,000 requests per minute.</span></span> <span data-ttu-id="fc376-163">[스마트 감지](https://docs.microsoft.com/azure/azure-monitor/app/proactive-diagnostics) 는 일반에서이 편차를 확인 하 고 경고를 트리거합니다.</span><span class="sxs-lookup"><span data-stu-id="fc376-163">[Smart Detection](https://docs.microsoft.com/azure/azure-monitor/app/proactive-diagnostics) will notice this deviation from the norm and trigger an alert.</span></span> <span data-ttu-id="fc376-164">동시에 추세 분석은 트래픽 부하가 예상 될 때 가양성 발생을 방지할 수 있을 만큼 지능적입니다.</span><span class="sxs-lookup"><span data-stu-id="fc376-164">At the same time, the trend analysis is smart enough to avoid firing false positives when the traffic load is expected.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="fc376-165">[이전](monitoring-azure-kubernetes.md)
>[다음](identity.md)</span><span class="sxs-lookup"><span data-stu-id="fc376-165">[Previous](monitoring-azure-kubernetes.md)
[Next](identity.md)</span></span>