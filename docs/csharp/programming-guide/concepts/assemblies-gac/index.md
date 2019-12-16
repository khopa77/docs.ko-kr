---
title: "어셈블리 및 전역 어셈블리 캐시(C#)"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
ms.assetid: 149f5ca5-5b34-4746-9542-1ae43b2d0256
caps.latest.revision: 3
author: BillWagner
ms.author: wiwagn
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 2b98bd872bfdcbebb34fff3d878b92f39e27bbe0
ms.contentlocale: ko-kr
ms.lasthandoff: 07/28/2017

---
# <a name="assemblies-and-the-global-assembly-cache-c"></a><span data-ttu-id="b978f-102">어셈블리 및 전역 어셈블리 캐시(C#)</span><span class="sxs-lookup"><span data-stu-id="b978f-102">Assemblies and the Global Assembly Cache (C#)</span></span>
<span data-ttu-id="b978f-103">어셈블리는 .NET 기반 응용 프로그램에 대한 배포, 버전 제어, 재사용, 활성화 범위 및 보안 권한의 기본 단위를 형성합니다.</span><span class="sxs-lookup"><span data-stu-id="b978f-103">Assemblies form the fundamental unit of deployment, version control, reuse, activation scoping, and security permissions for a .NET-based application.</span></span> <span data-ttu-id="b978f-104">어셈블리는 실행 파일(.exe) 또는 동적 연결 라이브러리(.dll) 파일의 형태를 가지며 .NET Framework의 구성 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="b978f-104">Assemblies take the form of an executable (.exe) file or dynamic link library (.dll) file, and are the building blocks of the .NET Framework.</span></span> <span data-ttu-id="b978f-105">어셈블리는 형식 구현을 인식하는 데 필요한 정보와 함께 공용 언어 런타임을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="b978f-105">They provide the common language runtime with the information it needs to be aware of type implementations.</span></span> <span data-ttu-id="b978f-106">어셈블리를 함께 작동하도록 빌드되고 논리적 기능 단위를 형성하는 리소스 및 형식 컬렉션으로 생각할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b978f-106">You can think of an assembly as a collection of types and resources that form a logical unit of functionality and are built to work together.</span></span>  
  
 <span data-ttu-id="b978f-107">어셈블리에는 하나 이상의 모듈이 포함될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b978f-107">Assemblies can contain one or more modules.</span></span> <span data-ttu-id="b978f-108">예를 들어 여러 개별 개발자가 별도 모듈로 작업하다가 함께 모여 단일 어셈블리를 만드는 방식으로 대규모 프로젝트를 계획할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b978f-108">For example, larger projects may be planned in such a way that several individual developers work on separate modules, all coming together to create a single assembly.</span></span> <span data-ttu-id="b978f-109">모듈에 대한 자세한 내용은 [방법: 다중 파일 어셈블리 빌드](https://msdn.microsoft.com/library/226t7yxe)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="b978f-109">For more information about modules, see the topic [How to: Build a Multifile Assembly](https://msdn.microsoft.com/library/226t7yxe).</span></span>  
  
 <span data-ttu-id="b978f-110">어셈블리에는 다음과 같은 속성이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b978f-110">Assemblies have the following properties:</span></span>  
  
-   <span data-ttu-id="b978f-111">어셈블리는 .exe 또는 .dll 파일로 구현됩니다.</span><span class="sxs-lookup"><span data-stu-id="b978f-111">Assemblies are implemented as .exe or .dll files.</span></span>  
  
-   <span data-ttu-id="b978f-112">어셈블리를 전역 어셈블리 캐시에 저장하면 응용 프로그램 간에 공유할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b978f-112">You can share an assembly between applications by putting it in the global assembly cache.</span></span> <span data-ttu-id="b978f-113">어셈블리를 전역 어셈블리 캐시에 넣으려면 강력한 이름이 지정되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="b978f-113">Assemblies must be strong-named before they can be included in the global assembly cache.</span></span> <span data-ttu-id="b978f-114">자세한 내용은 [강력한 이름의 어셈블리](https://msdn.microsoft.com/library/wd40t7ad)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="b978f-114">For more information, see [Strong-Named Assemblies](https://msdn.microsoft.com/library/wd40t7ad).</span></span>  
  
-   <span data-ttu-id="b978f-115">어셈블리는 필요한 경우에만 메모리에 로드됩니다.</span><span class="sxs-lookup"><span data-stu-id="b978f-115">Assemblies are only loaded into memory if they are required.</span></span> <span data-ttu-id="b978f-116">사용되지 않을 때는 로드되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="b978f-116">If they are not used, they are not loaded.</span></span> <span data-ttu-id="b978f-117">즉, 어셈블리는 대규모 프로젝트에서 리소스를 관리하는 효율적인 방법일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b978f-117">This means that assemblies can be an efficient way to manage resources in larger projects.</span></span>  
  
-   <span data-ttu-id="b978f-118">리플렉션을 사용하여 프로그래밍 방식으로 어셈블리에 대한 정보를 얻을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b978f-118">You can programmatically obtain information about an assembly by using reflection.</span></span> <span data-ttu-id="b978f-119">자세한 내용은 [리플렉션(C#)](../../../../csharp/programming-guide/concepts/reflection.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="b978f-119">For more information, see [Reflection (C#)](../../../../csharp/programming-guide/concepts/reflection.md).</span></span>  
  
-   <span data-ttu-id="b978f-120">검사할 어셈블리만 로드하려면 <xref:System.Reflection.Assembly.ReflectionOnlyLoadFrom%2A> 같은 메서드를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="b978f-120">If you want to load an assembly only to inspect it, use a method such as <xref:System.Reflection.Assembly.ReflectionOnlyLoadFrom%2A>.</span></span>  
  
## <a name="assembly-manifest"></a><span data-ttu-id="b978f-121">어셈블리 매니페스트</span><span class="sxs-lookup"><span data-stu-id="b978f-121">Assembly Manifest</span></span>  
 <span data-ttu-id="b978f-122">모든 어셈블리 내에는 *어셈블리 매니페스트*가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b978f-122">Within every assembly is an *assembly manifest*.</span></span> <span data-ttu-id="b978f-123">목차와 마찬가지로, 어셈블리 매니페스트에는 다음이 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="b978f-123">Similar to a table of contents, the assembly manifest contains the following:</span></span>  
  
-   <span data-ttu-id="b978f-124">어셈블리의 ID(해당 이름 및 버전).</span><span class="sxs-lookup"><span data-stu-id="b978f-124">The assembly's identity (its name and version).</span></span>  
  
-   <span data-ttu-id="b978f-125">어셈블리를 구성하는 다른 모든 파일을 설명하는 파일 테이블(예: 사용자의 .exe 또는 .dll 파일이 의존하는 사용자가 만든 다른 모든 어셈블리 또는 비트맵이나 추가 정보 파일)</span><span class="sxs-lookup"><span data-stu-id="b978f-125">A file table describing all the other files that make up the assembly, for example, any other assemblies you created that your .exe or .dll file relies on, or even bitmap or Readme files.</span></span>  
  
-   <span data-ttu-id="b978f-126">*어셈블리 참조 목록*: 누군가가 만들었을 수 있으며 사용자의 응용 프로그램에 필요한 .dlls 또는 기타 파일을 비롯한 모든 외부 종속성 목록</span><span class="sxs-lookup"><span data-stu-id="b978f-126">An *assembly reference list*, which is a list of all external dependencies—.dlls or other files your application needs that may have been created by someone else.</span></span> <span data-ttu-id="b978f-127">어셈블리 참조는 global 및 private 개체에 대한 참조를 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="b978f-127">Assembly references contain references to both global and private objects.</span></span> <span data-ttu-id="b978f-128">global 개체는 다른 응용 프로그램에서 사용할 수 있는 영역인 전역 어셈블리 캐시에 상주합니다.</span><span class="sxs-lookup"><span data-stu-id="b978f-128">Global objects reside in the global assembly cache, an area available to other applications.</span></span> <span data-ttu-id="b978f-129">private 개체는 응용 프로그램이 설치된 디렉터리와 같거나 낮은 수준에 있는 디렉터리에 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="b978f-129">Private objects must be in a directory at either the same level as or below the directory in which your application is installed.</span></span>  
  
 <span data-ttu-id="b978f-130">어셈블리는 콘텐츠, 버전 관리 및 종속성에 대한 정보를 포함하므로 C#으로 만드는 응용 프로그램은 제대로 작동하기 위해 Windows 레지스트리 값에 의존하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="b978f-130">Because assemblies contain information about content, versioning, and dependencies, the applications you create with C# do not rely on Windows registry values to function properly.</span></span> <span data-ttu-id="b978f-131">어셈블리는 .dll 충돌을 줄이고 더 안정적이고 배포하기 쉬운 응용 프로그램을 구현합니다.</span><span class="sxs-lookup"><span data-stu-id="b978f-131">Assemblies reduce .dll conflicts and make your applications more reliable and easier to deploy.</span></span> <span data-ttu-id="b978f-132">많은 경우에 해당 파일을 대상 컴퓨터에 복사하는 것만으로 .NET 기반 응용 프로그램을 설치할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b978f-132">In many cases, you can install a .NET-based application simply by copying its files to the target computer.</span></span>  
  
 <span data-ttu-id="b978f-133">자세한 내용은 [어셈블리 매니페스트](https://msdn.microsoft.com/library/1w45z383)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="b978f-133">For more information see [Assembly Manifest](https://msdn.microsoft.com/library/1w45z383).</span></span>  
  
## <a name="adding-a-reference-to-an-assembly"></a><span data-ttu-id="b978f-134">어셈블리에 대한 참조 추가</span><span class="sxs-lookup"><span data-stu-id="b978f-134">Adding a Reference to an Assembly</span></span>  
 <span data-ttu-id="b978f-135">어셈블리를 사용하려면 해당 참조를 추가해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="b978f-135">To use an assembly, you must add a reference to it.</span></span> <span data-ttu-id="b978f-136">다음에는 [using 지시문](../../../../csharp/language-reference/keywords/using-directive.md)을 사용하여 사용하려는 항목의 네임스페이스를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="b978f-136">Next, you use the [using directive](../../../../csharp/language-reference/keywords/using-directive.md) to choose the namespace of the items you want to use.</span></span> <span data-ttu-id="b978f-137">어셈블리를 참조하고 가져오면 해당 코드가 소스 파일에 속해 있는 것처럼 해당 네임스페이스의 액세스 가능한 모든 클래스, 속성, 메서드 및 다른 멤버를 응용 프로그램에서 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b978f-137">Once an assembly is referenced and imported, all the accessible classes, properties, methods, and other members of its namespaces are available to your application as if their code were part of your source file.</span></span>  
  
 <span data-ttu-id="b978f-138">C#에서는 단일 응용 프로그램에서 동일한 어셈블리의 두 버전을 사용할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b978f-138">In C#, you can also use two versions of the same assembly in a single application.</span></span> <span data-ttu-id="b978f-139">자세한 내용은 [extern alias](../../../../csharp/language-reference/keywords/extern-alias.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="b978f-139">For more information, see [extern alias](../../../../csharp/language-reference/keywords/extern-alias.md).</span></span>  
  
## <a name="creating-an-assembly"></a><span data-ttu-id="b978f-140">어셈블리 만들기</span><span class="sxs-lookup"><span data-stu-id="b978f-140">Creating an Assembly</span></span>  
 <span data-ttu-id="b978f-141">**빌드** 메뉴의 **빌드**를 클릭하거나 명령줄 컴파일러를 사용하여 명령줄에서 빌드하는 방식으로 응용 프로그램을 컴파일합니다.</span><span class="sxs-lookup"><span data-stu-id="b978f-141">Compile your application by clicking **Build** on the **Build** menu or by building it from the command line using the command-line compiler.</span></span> <span data-ttu-id="b978f-142">명령줄에서 어셈블리를 빌드하는 방법에 대한 자세한 내용은 [csc.exe를 사용한 명령줄 빌드](../../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="b978f-142">For details about building assemblies from the command line, see [Command-line Building With csc.exe](../../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="b978f-143">Visual Studio에서 어셈블리를 빌드하려면 **빌드** 메뉴에서 **빌드**를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="b978f-143">To build an assembly in Visual Studio, on the **Build** menu choose **Build**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b978f-144">참고 항목</span><span class="sxs-lookup"><span data-stu-id="b978f-144">See Also</span></span>  
 <span data-ttu-id="b978f-145">[C# 프로그래밍 가이드](../../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="b978f-145">[C# Programming Guide](../../../../csharp/programming-guide/index.md) </span></span>  
 <span data-ttu-id="b978f-146">[공용 언어 런타임의 어셈블리](https://msdn.microsoft.com/library/k3677y81) </span><span class="sxs-lookup"><span data-stu-id="b978f-146">[Assemblies in the Common Language Runtime](https://msdn.microsoft.com/library/k3677y81) </span></span>  
 <span data-ttu-id="b978f-147">[Friend 어셈블리(C#)](friend-assemblies.md) </span><span class="sxs-lookup"><span data-stu-id="b978f-147">[Friend Assemblies (C#)](friend-assemblies.md) </span></span>  
 <span data-ttu-id="b978f-148">[방법: 다른 응용 프로그램과 어셈블리 공유(C#)](how-to-share-an-assembly-with-other-applications.md) </span><span class="sxs-lookup"><span data-stu-id="b978f-148">[How to: Share an Assembly with Other Applications (C#)](how-to-share-an-assembly-with-other-applications.md) </span></span>  
 <span data-ttu-id="b978f-149">[방법: 어셈블리 로드 및 언로드(C#)](how-to-load-and-unload-assemblies.md) </span><span class="sxs-lookup"><span data-stu-id="b978f-149">[How to: Load and Unload Assemblies (C#)](how-to-load-and-unload-assemblies.md) </span></span>  
 <span data-ttu-id="b978f-150">[방법: 파일이 어셈블리인지 확인(C#)](how-to-determine-if-a-file-is-an-assembly.md) </span><span class="sxs-lookup"><span data-stu-id="b978f-150">[How to: Determine If a File Is an Assembly (C#)](how-to-determine-if-a-file-is-an-assembly.md) </span></span>  
 <span data-ttu-id="b978f-151">[방법: 명령줄을 사용하여 어셈블리 만들기 및 사용(C#)](how-to-create-and-use-assemblies-using-the-command-line.md) </span><span class="sxs-lookup"><span data-stu-id="b978f-151">[How to: Create and Use Assemblies Using the Command Line (C#)](how-to-create-and-use-assemblies-using-the-command-line.md) </span></span>  
 <span data-ttu-id="b978f-152">[연습: Visual Studio에서 관리되는 어셈블리의 형식 포함(C#)](walkthrough-embedding-types-from-managed-assemblies-in-visual-studio.md) </span><span class="sxs-lookup"><span data-stu-id="b978f-152">[Walkthrough: Embedding Types from Managed Assemblies in Visual Studio (C#)](walkthrough-embedding-types-from-managed-assemblies-in-visual-studio.md) </span></span>  
 [<span data-ttu-id="b978f-153">연습: Visual Studio에서 Microsoft Office 어셈블리의 형식 정보 포함(C#)</span><span class="sxs-lookup"><span data-stu-id="b978f-153">Walkthrough: Embedding Type Information from Microsoft Office Assemblies in Visual Studio (C#)</span></span>](walkthrough-embedding-type-information-from-microsoft-office-assemblies.md)
