---
title: '방법: 어셈블리의 정규화된 이름 찾기'
ms.date: 08/20/2019
helpviewer_keywords:
- names [.NET Framework], fully qualified type names
- names [.NET Framework], assemblies
- assemblies [.NET Framework], names
ms.assetid: 009dae23-e1f6-4a64-9a9a-32e4c34802b0
author: rpetrusha
ms.author: ronpet
dev_langs:
- csharp
- vb
- cpp
ms.openlocfilehash: 4fc670adc80a6f4ce7b36074185dcd3bb85fbc67
ms.sourcegitcommit: 005980b14629dfc193ff6cdc040800bc75e0a5a5
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/14/2019
ms.locfileid: "70991304"
---
# <a name="how-to-find-an-assemblys-fully-qualified-name"></a><span data-ttu-id="b1c68-102">방법: 어셈블리의 정규화된 이름 찾기</span><span class="sxs-lookup"><span data-stu-id="b1c68-102">How to: Find an assembly's fully qualified name</span></span>

<span data-ttu-id="b1c68-103">전역 어셈블리 캐시에서 .NET Framework 어셈블리의 정규화된 이름을 찾으려면 전역 어셈블리 캐시 도구([Gacutil.exe](../../framework/tools/gacutil-exe-gac-tool.md))를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="b1c68-103">To discover the fully qualified name of a .NET Framework assembly in the global assembly cache, use the Global Assembly Cache tool ([Gacutil.exe](../../framework/tools/gacutil-exe-gac-tool.md)).</span></span> <span data-ttu-id="b1c68-104">[방법: 전역 어셈블리 캐시의 내용 보기](../../framework/app-domains/how-to-view-the-contents-of-the-gac.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="b1c68-104">See [How to: View the contents of the global assembly cache](../../framework/app-domains/how-to-view-the-contents-of-the-gac.md).</span></span>

<span data-ttu-id="b1c68-105">.NET Core 어셈블리와 전역 어셈블리 캐시에 없는 .NET Framework 어셈블리의 경우, 여러 방법으로 정규화된 어셈블리 이름을 가져올 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b1c68-105">For .NET Core assemblies, and for .NET Framework assemblies that aren't in the global assembly cache, you can get the fully qualified assembly name in a number of ways:</span></span>

- <span data-ttu-id="b1c68-106">코드를 사용하여 콘솔이나 변수로 정보를 출력하거나 [Ildasm.exe(IL 디스어셈블러)](../../framework/tools/ildasm-exe-il-disassembler.md)를 사용하여 정규화된 이름이 포함된 어셈블리의 메타데이터를 검사할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b1c68-106">You can use code to output the information to the console or to a variable, or you can use the [Ildasm.exe (IL Disassembler)](../../framework/tools/ildasm-exe-il-disassembler.md) to examine the assembly's metadata, which contains the fully qualified name.</span></span>

- <span data-ttu-id="b1c68-107">애플리케이션에서 어셈블리를 이미 로드한 경우 <xref:System.Reflection.Assembly.FullName%2A?displayProperty=nameWithType> 속성의 값을 검색하여 정규화된 이름을 가져올 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b1c68-107">If the assembly is already loaded by the application, you can retrieve the value of the <xref:System.Reflection.Assembly.FullName%2A?displayProperty=nameWithType> property to get the fully qualified name.</span></span> <span data-ttu-id="b1c68-108">해당 어셈블리에 정의된 <xref:System.Type>의 <xref:System.Type.Assembly> 속성을 사용하여 <xref:System.Reflection.Assembly> 개체에 대한 참조를 검색할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b1c68-108">You can use the <xref:System.Type.Assembly> property of a <xref:System.Type> defined in that assembly to retrieve a reference to the <xref:System.Reflection.Assembly> object.</span></span> <span data-ttu-id="b1c68-109">예제에서는 그림을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="b1c68-109">The example provides an illustration.</span></span>

- <span data-ttu-id="b1c68-110">어셈블리의 파일 시스템 경로를 알고 있는 경우`static`(C#) 또는 `Shared`(Visual Basic) <xref:System.Reflection.AssemblyName.GetAssemblyName%2A?displayProperty=nameWithType> 메서드를 호출하여 정규화된 어셈블리 이름을 가져올 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b1c68-110">If you know the assembly's file system path, you can call the `static` (C#) or `Shared` (Visual Basic) <xref:System.Reflection.AssemblyName.GetAssemblyName%2A?displayProperty=nameWithType> method to get the fully qualified assembly name.</span></span> <span data-ttu-id="b1c68-111">다음은 간단한 예제입니다.</span><span class="sxs-lookup"><span data-stu-id="b1c68-111">The following is a simple example.</span></span>

  ```csharp
  using System;
  using System.Reflection;

  public class Example
  {
     public static void Main()
     {
        Console.WriteLine(AssemblyName.GetAssemblyName(@".\UtilityLibrary.dll"));
     }
  }
  // The example displays output like the following:
  //   UtilityLibrary, Version=1.1.0.0, Culture=neutral, PublicKeyToken=null
  ```

  ```vb
  Imports System.Reflection

  Public Module Example
     Public Sub Main
        Console.WriteLine(AssemblyName.GetAssemblyName(".\UtilityLibrary.dll"))
     End Sub
  End Module
  ' The example displays output like the following:
  '   UtilityLibrary, Version=1.1.0.0, Culture=neutral, PublicKeyToken=null
  ```

- <span data-ttu-id="b1c68-112">[Ildasm.exe(IL 디스어셈블러)](../../framework/tools/ildasm-exe-il-disassembler.md)를 사용하여 정규화된 이름이 포함된 어셈블리의 메타데이터를 검사할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b1c68-112">You can use the [Ildasm.exe (IL Disassembler)](../../framework/tools/ildasm-exe-il-disassembler.md) to examine the assembly's metadata, which contains the fully qualified name.</span></span>

<span data-ttu-id="b1c68-113">버전, 문화권 및 어셈블리 이름과 같은 어셈블리 특성 설정에 대한 자세한 내용은 [어셈블리 특성 설정](set-attributes.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="b1c68-113">For more information about setting assembly attributes such as version, culture, and assembly name, see [Set assembly attributes](set-attributes.md).</span></span> <span data-ttu-id="b1c68-114">어셈블리에 강력한 이름을 지정하는 방법에 대한 자세한 내용은 [강력한 이름의 어셈블리 만들기 및 사용](create-use-strong-named.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="b1c68-114">For more information about giving an assembly a strong name, see [Create and use strong-named assemblies](create-use-strong-named.md).</span></span>

## <a name="example"></a><span data-ttu-id="b1c68-115">예</span><span class="sxs-lookup"><span data-stu-id="b1c68-115">Example</span></span>

<span data-ttu-id="b1c68-116">다음 예제는 지정된 클래스를 포함하는 어셈블리의 정규화된 이름을 콘솔에 표시하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="b1c68-116">The following example shows how to display the fully qualified name of an assembly containing a specified class to the console.</span></span> <span data-ttu-id="b1c68-117">이 예제는 <xref:System.Type.Assembly?displayProperty=nameWithType> 속성을 사용하여 해당 어셈블리에 정의된 형식에서 어셈블리에 대한 참조를 검색합니다.</span><span class="sxs-lookup"><span data-stu-id="b1c68-117">It uses the <xref:System.Type.Assembly?displayProperty=nameWithType> property to retrieve a reference to an assembly from a type that's defined in that assembly.</span></span>

```cpp
#using <System.dll>
#using <System.Data.dll>

using namespace System;
using namespace System::Reflection;

ref class asmname
{
public:
    static void Main()
    {
        Type^ t = System::Data::DataSet::typeid;
        String^ s = t->Assembly->FullName->ToString();
        Console::WriteLine("The fully qualified assembly name " +
            "containing the specified class is {0}.", s);
    }
};

int main()
{
    asmname::Main();
}
```

```csharp
using System;
using System.Reflection;

class asmname
{
    public static void Main()
    {
        Type t = typeof(System.Data.DataSet);
        string s = t.Assembly.FullName.ToString();
        Console.WriteLine("The fully qualified assembly name " +
            "containing the specified class is {0}.", s);
    }
}
```

```vb
Imports System
Imports System.Reflection

Class asmname
    Public Shared Sub Main()
        Dim t As Type = GetType(System.Data.DataSet)
        Dim s As String = t.Assembly.FullName.ToString()
        Console.WriteLine("The fully qualified assembly name " +
            "containing the specified class is {0}.", s)
    End Sub
End Class
```

## <a name="see-also"></a><span data-ttu-id="b1c68-118">참고 항목</span><span class="sxs-lookup"><span data-stu-id="b1c68-118">See also</span></span>

- [<span data-ttu-id="b1c68-119">어셈블리 이름</span><span class="sxs-lookup"><span data-stu-id="b1c68-119">Assembly names</span></span>](names.md)
- [<span data-ttu-id="b1c68-120">어셈블리 만들기</span><span class="sxs-lookup"><span data-stu-id="b1c68-120">Create assemblies</span></span>](create.md)
- [<span data-ttu-id="b1c68-121">강력한 이름의 어셈블리 만들기 및 사용</span><span class="sxs-lookup"><span data-stu-id="b1c68-121">Create and use strong-named assemblies</span></span>](create-use-strong-named.md)
- [<span data-ttu-id="b1c68-122">전역 어셈블리 캐시</span><span class="sxs-lookup"><span data-stu-id="b1c68-122">Global assembly cache</span></span>](../../framework/app-domains/gac.md)
- [<span data-ttu-id="b1c68-123">런타임에서 어셈블리를 찾는 방법</span><span class="sxs-lookup"><span data-stu-id="b1c68-123">How the runtime locates assemblies</span></span>](../../framework/deployment/how-the-runtime-locates-assemblies.md)
- [<span data-ttu-id="b1c68-124">어셈블리를 사용한 프로그램</span><span class="sxs-lookup"><span data-stu-id="b1c68-124">Program with assemblies</span></span>](program.md)