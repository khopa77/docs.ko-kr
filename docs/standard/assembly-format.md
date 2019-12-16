---
title: ".NET 어셈블리 파일 형식"
description: ".NET 앱 및 라이브러리를 설명하고 포함하는 데 사용되는 .NET 어셈블리 파일 형식에 대해 알아봅니다."
keywords: .NET, .NET Core
author: richlander
ms.author: mairaw
ms.date: 06/20/2016
ms.topic: article
ms.prod: .net
ms.technology: dotnet-standard
ms.devlang: dotnet
ms.assetid: 6520323e-ff28-4c8a-ba80-e64a413199e6
ms.translationtype: HT
ms.sourcegitcommit: 934373d61407c8cc19b7d6424898a582880f9c21
ms.openlocfilehash: 47e895274f6d400639878e0bd5c700e04b554ce5
ms.contentlocale: ko-kr
ms.lasthandoff: 08/21/2017

---

# <a name="net-assembly-file-format"></a><span data-ttu-id="5907f-104">.NET 어셈블리 파일 형식</span><span class="sxs-lookup"><span data-stu-id="5907f-104">.NET Assembly File Format</span></span>

<span data-ttu-id="5907f-105">.NET은 .NET 프로그램을 완벽하게 설명하고 포함하는 데 사용되는 이진 파일 형식(“어셈블리”)을 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="5907f-105">.NET defines a binary file format - "assembly" - that is used to fully-describe and contain .NET programs.</span></span> <span data-ttu-id="5907f-106">어셈블리는 프로그램 자체와 모든 종속 라이브러리에 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="5907f-106">Assemblies are used for the programs themselves as well as any dependent libraries.</span></span> <span data-ttu-id="5907f-107">적절한 .NET 구현 외에 다른 필수 아티팩트 없이 추가 어셈블리 중 하나로 .NET 프로그램을 실행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5907f-107">A .NET program can be executed as one of more assemblies, with no other required artifacts, beyond the appropriate .NET implementation.</span></span> <span data-ttu-id="5907f-108">운영 체제 API를 비롯한 기본 종속성은 별도의 문제이며, .NET 어셈블리 형식으로 설명되는 경우도 있지만(예: WinRT) 이 형식에 포함되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="5907f-108">Native dependencies, including operating system APIs, are a separate concern and are not contained within the .NET assembly format, although are sometimes described with this format (for example, WinRT).</span></span>

> <span data-ttu-id="5907f-109">각 CLI 구성 요소는 해당 구성 요소와 관련된 선언, 구현 및 참조에 대한 메타데이터를 전달합니다.</span><span class="sxs-lookup"><span data-stu-id="5907f-109">Each CLI component carries the metadata for declarations, implementations, and references specific to that component.</span></span> <span data-ttu-id="5907f-110">따라서 구성 요소 관련 메타데이터는 구성 요소별 메타데이터라고 하며 결과 구성 요소는 자기 설명적입니다(ECMA 335 I.9.1, Components and assemblies).</span><span class="sxs-lookup"><span data-stu-id="5907f-110">Therefore, the component-specific metadata is referred to as component metadata, and the resulting component is said to be self-describing – from ECMA 335 I.9.1, Components and assemblies.</span></span>

<span data-ttu-id="5907f-111">형식은 완벽하게 지정되며 ECMA 335로 표준화됩니다.</span><span class="sxs-lookup"><span data-stu-id="5907f-111">The format is fully specified and standardized as ECMA 335.</span></span> <span data-ttu-id="5907f-112">모든 .NET 컴파일러와 런타임에서 이 형식을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="5907f-112">All .NET compilers and runtimes use this format.</span></span> <span data-ttu-id="5907f-113">문서화되고 자주 업데이트되지 않는 이진 형식이 있을 경우 상호 운용성에 특히 도움이 됩니다(요구 사항인 경우도 있음).</span><span class="sxs-lookup"><span data-stu-id="5907f-113">The presence of a documented and infrequently updated binary format has been a major benefit (arguably a requirement) for interoperatibility.</span></span> <span data-ttu-id="5907f-114">형식은 2005(.NET 2.0)에서 대체 방법을 사용하여 제네릭 및 프로세서 아키텍처에 맞게 마지막으로 업데이트되었습니다.</span><span class="sxs-lookup"><span data-stu-id="5907f-114">The format was last updated in a substantive way in 2005 (.NET 2.0) to accommodate generics and processor architecture.</span></span>

<span data-ttu-id="5907f-115">형식은 CPU 및 OS와 관련이 없습니다.</span><span class="sxs-lookup"><span data-stu-id="5907f-115">The format is CPU- and OS-agnostic.</span></span> <span data-ttu-id="5907f-116">많은 칩과 CPU를 대상으로 하는 .NET 구현의 일부로 사용되었습니다.</span><span class="sxs-lookup"><span data-stu-id="5907f-116">It has been used as part of .NET implementations that target many chips and CPUs.</span></span> <span data-ttu-id="5907f-117">형식 자체에 Windows 유산이 있을 경우 모든 운영 체제에서 구현할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5907f-117">While the format itself has Windows heritage, it is implementable on any operating system.</span></span> <span data-ttu-id="5907f-118">논란의 여지는 있지만 OS 상호 운용성에 가장 중요한 선택 사항은 대부분의 값을 little-endian 형식으로 저장하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="5907f-118">It’s arguably most significant choice for OS interoperability is that most values are stored in little-endian format.</span></span> <span data-ttu-id="5907f-119">컴퓨터 포인터 크기(예: 32비트, 64비트)에 대한 특정 선호도는 없습니다.</span><span class="sxs-lookup"><span data-stu-id="5907f-119">It doesn’t have a specific affinity to machine pointer size (for example, 32-bit, 64-bit).</span></span>

<span data-ttu-id="5907f-120">.NET 어셈블리 형식은 지정된 프로그램 또는 라이브러리의 구조에 대해 매우 설명적이기도 합니다.</span><span class="sxs-lookup"><span data-stu-id="5907f-120">The .NET assembly format is also very descriptive about the structure of a given program or library.</span></span> <span data-ttu-id="5907f-121">어셈블리의 내부 구성 요소, 특히 정의된 어셈블리 참조 및 형식과 해당 내부 구조를 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="5907f-121">It describes the internal components of an assembly, specifically: assembly references and types defined and their internal structure.</span></span> <span data-ttu-id="5907f-122">도구 또는 API는 표시하거나 프로그래밍 방식으로 결정을 내리기 위해 이 정보를 읽고 처리할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5907f-122">Tools or APIs can read and process this information for display or to make programmatic decisions.</span></span>

## <a name="format"></a><span data-ttu-id="5907f-123">서식</span><span class="sxs-lookup"><span data-stu-id="5907f-123">Format</span></span>

<span data-ttu-id="5907f-124">.NET 이진 형식은 Windows [PE 파일](http://en.wikipedia.org/wiki/Portable_Executable) 형식을 기반으로 합니다.</span><span class="sxs-lookup"><span data-stu-id="5907f-124">The .NET binary format is based on the Windows [PE file](http://en.wikipedia.org/wiki/Portable_Executable) format.</span></span> <span data-ttu-id="5907f-125">실제로 .NET 클래스 라이브러리는 규칙에 부합되는 Windows PE이며, 처음에는 Windows DLL(동적 연결 라이브러리) 또는 EXE(응용 프로그램 실행 파일)처럼 보입니다.</span><span class="sxs-lookup"><span data-stu-id="5907f-125">In fact, .NET class libraries are conformant Windows PEs, and appear on first glance to be Windows dynamic link libraries (DLLs) or application executables (EXEs).</span></span> <span data-ttu-id="5907f-126">이는 Windows에서 매우 유용한 특성으로, 네이티브 실행 이진 파일로 가장하고 동일한 처리 중 일부(예: OS 로드, PE 도구)를 얻을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5907f-126">This is a very useful characteristic on Windows, where they can masquerade as native executable binaries and get some of the same treatment (for example, OS load, PE tools).</span></span>

![어셈블리 헤더](./media/assembly-format/assembly-headers.png)

<span data-ttu-id="5907f-128">ECMA 335 II.25.1 런타임 파일 형식 구조의 어셈블리 헤더입니다.</span><span class="sxs-lookup"><span data-stu-id="5907f-128">Assembly Headers from ECMA 335 II.25.1, Structure of the runtime file format.</span></span>

## <a name="processing-the-assemblies"></a><span data-ttu-id="5907f-129">어셈블리 처리</span><span class="sxs-lookup"><span data-stu-id="5907f-129">Processing the Assemblies</span></span>

<span data-ttu-id="5907f-130">어셈블리를 처리할 도구 또는 API를 작성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5907f-130">It is possible to write tools or APIs to process assemblies.</span></span> <span data-ttu-id="5907f-131">어셈블리 정보를 사용하면 런타임에 프로그래밍 방식으로 결정을 내리고, 어셈블리를 다시 작성하고, 편집기에서 API IntelliSense를 제공하고, 설명서를 생성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5907f-131">Assembly information enables making programmatic decisions at runtime, re-writing assemblies, providing API IntelliSense in an editor and generating documentation.</span></span> <span data-ttu-id="5907f-132"><xref:System.Reflection?displayProperty=fullName> 및 [Mono.Cecil](http://www.mono-project.com/docs/tools+libraries/libraries/Mono.Cecil/)은 이러한 용도에 자주 사용되는 도구의 좋은 예입니다.</span><span class="sxs-lookup"><span data-stu-id="5907f-132"><xref:System.Reflection?displayProperty=fullName> and [Mono.Cecil](http://www.mono-project.com/docs/tools+libraries/libraries/Mono.Cecil/) are good examples of tools that are frequently used for this purpose.</span></span>
