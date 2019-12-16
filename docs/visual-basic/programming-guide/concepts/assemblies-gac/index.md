---
title: "어셈블리와 전역 어셈블리 캐시(Visual Basic)"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
ms.assetid: fcf78ff1-f1ab-4a5d-b6d8-00d2046b6c80
caps.latest.revision: 3
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: c5a1a3a651fc7d2b42f8ac55ab6f2d832f258bb0
ms.contentlocale: ko-kr
ms.lasthandoff: 07/28/2017

---
# <a name="assemblies-and-the-global-assembly-cache-visual-basic"></a><span data-ttu-id="14643-102">어셈블리와 전역 어셈블리 캐시(Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="14643-102">Assemblies and the Global Assembly Cache (Visual Basic)</span></span>
<span data-ttu-id="14643-103">어셈블리는 .NET 기반 응용 프로그램에 대한 배포, 버전 제어, 재사용, 활성화 범위 및 보안 권한의 기본 단위를 형성합니다.</span><span class="sxs-lookup"><span data-stu-id="14643-103">Assemblies form the fundamental unit of deployment, version control, reuse, activation scoping, and security permissions for a .NET-based application.</span></span> <span data-ttu-id="14643-104">어셈블리는 실행 파일(.exe) 또는 동적 연결 라이브러리(.dll) 파일의 형태를 가지며 .NET Framework의 구성 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="14643-104">Assemblies take the form of an executable (.exe) file or dynamic link library (.dll) file, and are the building blocks of the .NET Framework.</span></span> <span data-ttu-id="14643-105">어셈블리는 형식 구현을 인식하는 데 필요한 정보와 함께 공용 언어 런타임을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="14643-105">They provide the common language runtime with the information it needs to be aware of type implementations.</span></span> <span data-ttu-id="14643-106">어셈블리를 함께 작동하도록 빌드되고 논리적 기능 단위를 형성하는 리소스 및 형식 컬렉션으로 생각할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="14643-106">You can think of an assembly as a collection of types and resources that form a logical unit of functionality and are built to work together.</span></span>  
  
 <span data-ttu-id="14643-107">어셈블리에는 하나 이상의 모듈이 포함될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="14643-107">Assemblies can contain one or more modules.</span></span> <span data-ttu-id="14643-108">예를 들어 여러 개별 개발자가 별도 모듈로 작업하다가 함께 모여 단일 어셈블리를 만드는 방식으로 대규모 프로젝트를 계획할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="14643-108">For example, larger projects may be planned in such a way that several individual developers work on separate modules, all coming together to create a single assembly.</span></span> <span data-ttu-id="14643-109">모듈에 대한 자세한 내용은 [방법: 다중 파일 어셈블리 빌드](https://msdn.microsoft.com/library/226t7yxe)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="14643-109">For more information about modules, see the topic [How to: Build a Multifile Assembly](https://msdn.microsoft.com/library/226t7yxe).</span></span>  
  
 <span data-ttu-id="14643-110">어셈블리에는 다음과 같은 속성이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="14643-110">Assemblies have the following properties:</span></span>  
  
-   <span data-ttu-id="14643-111">어셈블리는 .exe 또는 .dll 파일로 구현됩니다.</span><span class="sxs-lookup"><span data-stu-id="14643-111">Assemblies are implemented as .exe or .dll files.</span></span>  
  
-   <span data-ttu-id="14643-112">어셈블리를 전역 어셈블리 캐시에 저장하면 응용 프로그램 간에 공유할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="14643-112">You can share an assembly between applications by putting it in the global assembly cache.</span></span> <span data-ttu-id="14643-113">어셈블리를 전역 어셈블리 캐시에 넣으려면 강력한 이름이 지정되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="14643-113">Assemblies must be strong-named before they can be included in the global assembly cache.</span></span> <span data-ttu-id="14643-114">자세한 내용은 [강력한 이름의 어셈블리](https://msdn.microsoft.com/library/wd40t7ad)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="14643-114">For more information, see [Strong-Named Assemblies](https://msdn.microsoft.com/library/wd40t7ad).</span></span>  
  
-   <span data-ttu-id="14643-115">어셈블리는 필요한 경우에만 메모리에 로드됩니다.</span><span class="sxs-lookup"><span data-stu-id="14643-115">Assemblies are only loaded into memory if they are required.</span></span> <span data-ttu-id="14643-116">사용되지 않을 때는 로드되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="14643-116">If they are not used, they are not loaded.</span></span> <span data-ttu-id="14643-117">즉, 어셈블리는 대규모 프로젝트에서 리소스를 관리하는 효율적인 방법일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="14643-117">This means that assemblies can be an efficient way to manage resources in larger projects.</span></span>  
  
-   <span data-ttu-id="14643-118">리플렉션을 사용하여 프로그래밍 방식으로 어셈블리에 대한 정보를 얻을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="14643-118">You can programmatically obtain information about an assembly by using reflection.</span></span> <span data-ttu-id="14643-119">자세한 내용은 [리플렉션(Visual Basic)](../../../../visual-basic/programming-guide/concepts/reflection.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="14643-119">For more information, see [Reflection (Visual Basic)](../../../../visual-basic/programming-guide/concepts/reflection.md).</span></span>  
  
-   <span data-ttu-id="14643-120">검사할 어셈블리만 로드하려면 <xref:System.Reflection.Assembly.ReflectionOnlyLoadFrom%2A> 같은 메서드를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="14643-120">If you want to load an assembly only to inspect it, use a method such as <xref:System.Reflection.Assembly.ReflectionOnlyLoadFrom%2A>.</span></span>  
  
## <a name="assembly-manifest"></a><span data-ttu-id="14643-121">어셈블리 매니페스트</span><span class="sxs-lookup"><span data-stu-id="14643-121">Assembly Manifest</span></span>  
 <span data-ttu-id="14643-122">모든 어셈블리 내에는 *어셈블리 매니페스트*가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="14643-122">Within every assembly is an *assembly manifest*.</span></span> <span data-ttu-id="14643-123">목차와 마찬가지로, 어셈블리 매니페스트에는 다음이 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="14643-123">Similar to a table of contents, the assembly manifest contains the following:</span></span>  
  
-   <span data-ttu-id="14643-124">어셈블리의 ID(해당 이름 및 버전).</span><span class="sxs-lookup"><span data-stu-id="14643-124">The assembly's identity (its name and version).</span></span>  
  
-   <span data-ttu-id="14643-125">어셈블리를 구성하는 다른 모든 파일을 설명하는 파일 테이블(예: 사용자의 .exe 또는 .dll 파일이 의존하는 사용자가 만든 다른 모든 어셈블리 또는 비트맵이나 추가 정보 파일)</span><span class="sxs-lookup"><span data-stu-id="14643-125">A file table describing all the other files that make up the assembly, for example, any other assemblies you created that your .exe or .dll file relies on, or even bitmap or Readme files.</span></span>  
  
-   <span data-ttu-id="14643-126">*어셈블리 참조 목록*: 누군가가 만들었을 수 있으며 사용자의 응용 프로그램에 필요한 .dlls 또는 기타 파일을 비롯한 모든 외부 종속성 목록</span><span class="sxs-lookup"><span data-stu-id="14643-126">An *assembly reference list*, which is a list of all external dependencies—.dlls or other files your application needs that may have been created by someone else.</span></span> <span data-ttu-id="14643-127">어셈블리 참조는 global 및 private 개체에 대한 참조를 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="14643-127">Assembly references contain references to both global and private objects.</span></span> <span data-ttu-id="14643-128">global 개체는 System32 디렉터리 등과 같이 다른 응용 프로그램에서 사용할 수 있는 영역인 전역 어셈블리 캐시에 상주합니다.</span><span class="sxs-lookup"><span data-stu-id="14643-128">Global objects reside in the global assembly cache, an area available to other applications, somewhat like the System32 directory.</span></span> <span data-ttu-id="14643-129"><xref:Microsoft.VisualBasic?displayProperty=fullName> 네임스페이스는 전역 어셈블리 캐시의 어셈블리에 대한 예입니다.</span><span class="sxs-lookup"><span data-stu-id="14643-129">The <xref:Microsoft.VisualBasic?displayProperty=fullName> namespace is an example of an assembly in the global assembly cache.</span></span> <span data-ttu-id="14643-130">private 개체는 응용 프로그램이 설치된 디렉터리와 같거나 낮은 수준에 있는 디렉터리에 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="14643-130">Private objects must be in a directory at either the same level as or below the directory in which your application is installed.</span></span>  
  
 <span data-ttu-id="14643-131">어셈블리는 콘텐츠, 버전 관리 및 종속성에 대한 정보를 포함하므로 Visual Basic으로 만드는 응용 프로그램은 제대로 작동하기 위해 Windows 레지스트리 값에 의존하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="14643-131">Because assemblies contain information about content, versioning, and dependencies, the applications you create with Visual Basic do not rely on Windows registry values to function properly.</span></span> <span data-ttu-id="14643-132">어셈블리는 .dll 충돌을 줄이고 더 안정적이고 배포하기 쉬운 응용 프로그램을 구현합니다.</span><span class="sxs-lookup"><span data-stu-id="14643-132">Assemblies reduce .dll conflicts and make your applications more reliable and easier to deploy.</span></span> <span data-ttu-id="14643-133">많은 경우에 해당 파일을 대상 컴퓨터에 복사하는 것만으로 .NET 기반 응용 프로그램을 설치할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="14643-133">In many cases, you can install a .NET-based application simply by copying its files to the target computer.</span></span>  
  
 <span data-ttu-id="14643-134">자세한 내용은 [어셈블리 매니페스트](https://msdn.microsoft.com/library/1w45z383)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="14643-134">For more information see [Assembly Manifest](https://msdn.microsoft.com/library/1w45z383).</span></span>  
  
## <a name="adding-a-reference-to-an-assembly"></a><span data-ttu-id="14643-135">어셈블리에 대한 참조 추가</span><span class="sxs-lookup"><span data-stu-id="14643-135">Adding a Reference to an Assembly</span></span>  
 <span data-ttu-id="14643-136">어셈블리를 사용하려면 해당 참조를 추가해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="14643-136">To use an assembly, you must add a reference to it.</span></span> <span data-ttu-id="14643-137">다음에는 [Imports 문](../../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md)을 사용하여 사용하려는 항목의 네임스페이스를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="14643-137">Next, you use the [Imports statement](../../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md) to choose the namespace of the items you want to use.</span></span> <span data-ttu-id="14643-138">어셈블리를 참조하고 가져오면 해당 코드가 소스 파일에 속해 있는 것처럼 해당 네임스페이스의 액세스 가능한 모든 클래스, 속성, 메서드 및 다른 멤버를 응용 프로그램에서 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="14643-138">Once an assembly is referenced and imported, all the accessible classes, properties, methods, and other members of its namespaces are available to your application as if their code were part of your source file.</span></span>  
  
## <a name="creating-an-assembly"></a><span data-ttu-id="14643-139">어셈블리 만들기</span><span class="sxs-lookup"><span data-stu-id="14643-139">Creating an Assembly</span></span>  
 <span data-ttu-id="14643-140">명령줄 컴파일러를 사용하여 명령줄에서 빌드하는 방식으로 응용 프로그램을 컴파일합니다.</span><span class="sxs-lookup"><span data-stu-id="14643-140">Compile your application by building it from the command line using the command-line compiler.</span></span> <span data-ttu-id="14643-141">명령줄에서 어셈블리를 빌드하는 방법에 대한 자세한 내용은 [명령줄에서 빌드](../../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="14643-141">For details about building assemblies from the command line, see [Building from the Command Line](../../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="14643-142">Visual Studio에서 어셈블리를 빌드하려면 **빌드** 메뉴에서 **빌드**를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="14643-142">To build an assembly in Visual Studio, on the **Build** menu choose **Build**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="14643-143">참고 항목</span><span class="sxs-lookup"><span data-stu-id="14643-143">See Also</span></span>  
 <span data-ttu-id="14643-144">[공용 언어 런타임의 어셈블리](https://msdn.microsoft.com/library/k3677y81) </span><span class="sxs-lookup"><span data-stu-id="14643-144">[Assemblies in the Common Language Runtime](https://msdn.microsoft.com/library/k3677y81) </span></span>  
 <span data-ttu-id="14643-145">[Friend 어셈블리(Visual Basic)](friend-assemblies.md) </span><span class="sxs-lookup"><span data-stu-id="14643-145">[Friend Assemblies (Visual Basic)](friend-assemblies.md) </span></span>  
 <span data-ttu-id="14643-146">[방법: 다른 응용 프로그램과 어셈블리 공유(Visual Basic)](how-to-share-an-assembly-with-other-applications.md) </span><span class="sxs-lookup"><span data-stu-id="14643-146">[How to: Share an Assembly with Other Applications (Visual Basic)](how-to-share-an-assembly-with-other-applications.md) </span></span>  
 <span data-ttu-id="14643-147">[방법: 어셈블리 로드 및 언로드(Visual Basic)](how-to-load-and-unload-assemblies.md) </span><span class="sxs-lookup"><span data-stu-id="14643-147">[How to: Load and Unload Assemblies (Visual Basic)](how-to-load-and-unload-assemblies.md) </span></span>  
 <span data-ttu-id="14643-148">[방법: 파일이 어셈블리인지 확인(Visual Basic)](how-to-determine-if-a-file-is-an-assembly.md) </span><span class="sxs-lookup"><span data-stu-id="14643-148">[How to: Determine If a File Is an Assembly (Visual Basic)](how-to-determine-if-a-file-is-an-assembly.md) </span></span>  
 <span data-ttu-id="14643-149">[방법: 명령줄을 사용하여 어셈블리 만들기 및 사용(Visual Basic)](how-to-create-and-use-assemblies-using-the-command-line.md) </span><span class="sxs-lookup"><span data-stu-id="14643-149">[How to: Create and Use Assemblies Using the Command Line (Visual Basic)](how-to-create-and-use-assemblies-using-the-command-line.md) </span></span>  
 <span data-ttu-id="14643-150">[연습: Visual Studio에서 관리되는 어셈블리의 형식 포함(Visual Basic)](walkthrough-embedding-types-from-managed-assemblies-in-vs.md) </span><span class="sxs-lookup"><span data-stu-id="14643-150">[Walkthrough: Embedding Types from Managed Assemblies in Visual Studio (Visual Basic)](walkthrough-embedding-types-from-managed-assemblies-in-vs.md) </span></span>  
 [<span data-ttu-id="14643-151">연습: Visual Studio에서 Microsoft Office 어셈블리의 형식 정보 포함(Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="14643-151">Walkthrough: Embedding Type Information from Microsoft Office Assemblies in Visual Studio (Visual Basic)</span></span>](walkthrough-embedding-type-information-from-microsoft-office-assemblies-in-vs.md)
