---
title: '방법: 서명된 friend 어셈블리 만들기'
ms.date: 08/19/2019
ms.assetid: bab62063-61e6-453f-905f-77673df9534e
dev_langs:
- csharp
- vb
ms.openlocfilehash: 19c301c6b96e1070447401af9105fba2e0f0837f
ms.sourcegitcommit: 7b1ce327e8c84f115f007be4728d29a89efe11ef
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/13/2019
ms.locfileid: "70972812"
---
# <a name="how-to-create-signed-friend-assemblies"></a><span data-ttu-id="192d7-102">방법: 서명된 friend 어셈블리 만들기</span><span class="sxs-lookup"><span data-stu-id="192d7-102">How to: Create signed friend assemblies</span></span>
<span data-ttu-id="192d7-103">이 예제에서는 강력한 이름을 가진 어셈블리와 함께 friend 어셈블리를 사용하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="192d7-103">This example shows how to use friend assemblies with assemblies that have strong names.</span></span> <span data-ttu-id="192d7-104">두 어셈블리에 모두 강력한 이름을 지정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="192d7-104">Both assemblies must be strong named.</span></span> <span data-ttu-id="192d7-105">이 예제의 두 어셈블리는 모두 동일한 키를 사용하지만 두 어셈블리에 서로 다른 키를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="192d7-105">Although both assemblies in this example use the same keys, you could use different keys for two assemblies.</span></span>  
  
## <a name="create-a-signed-assembly-and-a-friend-assembly"></a><span data-ttu-id="192d7-106">서명된 어셈블리 및 friend 어셈블리 만들기</span><span class="sxs-lookup"><span data-stu-id="192d7-106">Create a signed assembly and a friend assembly</span></span>  
  
1. <span data-ttu-id="192d7-107">명령 프롬프트를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="192d7-107">Open a command prompt.</span></span>  
  
2. <span data-ttu-id="192d7-108">강력한 이름 도구와 함께 다음 명령 시퀀스를 사용하여 키 파일을 생성하고 해당 공개 키를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="192d7-108">Use the following sequence of commands with the Strong Name tool to generate a keyfile and to display its public key.</span></span> <span data-ttu-id="192d7-109">자세한 내용은 [Sn.exe(강력한 이름 도구)](../../framework/tools/sn-exe-strong-name-tool.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="192d7-109">For more information, see [Sn.exe (Strong Name tool)](../../framework/tools/sn-exe-strong-name-tool.md).</span></span>  
  
    1. <span data-ttu-id="192d7-110">이 예제를 위한 강력한 이름 키를 생성하고 *FriendAssemblies.snk* 파일에 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="192d7-110">Generate a strong-name key for this example and store it in the file *FriendAssemblies.snk*:</span></span>  
  
         `sn -k FriendAssemblies.snk`  
  
    2. <span data-ttu-id="192d7-111">*FriendAssemblies.snk*에서 공개 키를 추출하고 *FriendAssemblies.publickey*에 넣습니다.</span><span class="sxs-lookup"><span data-stu-id="192d7-111">Extract the public key from *FriendAssemblies.snk* and put it into *FriendAssemblies.publickey*:</span></span>  
  
         `sn -p FriendAssemblies.snk FriendAssemblies.publickey`  
  
    3. <span data-ttu-id="192d7-112">*FriendAssemblies.publickey* 파일에 저장된 공개 키를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="192d7-112">Display the public key stored in the file *FriendAssemblies.publickey*:</span></span>  
  
         `sn -tp FriendAssemblies.publickey`  
  
3. <span data-ttu-id="192d7-113">다음 코드를 포함하는 *friend_signed_A*라는 C# 또는 Visual Basic 파일을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="192d7-113">Create a C# or Visual Basic file named *friend_signed_A* that contains the following code.</span></span> <span data-ttu-id="192d7-114">이 코드는 <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> 특성을 사용하여 *friend_signed_B*를 friend 어셈블리로 선언합니다.</span><span class="sxs-lookup"><span data-stu-id="192d7-114">The code uses the <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> attribute to declare *friend_signed_B* as a friend assembly.</span></span>  
   
   <span data-ttu-id="192d7-115">강력한 이름 도구는 실행할 때마다 새 공개 키를 생성합니다.</span><span class="sxs-lookup"><span data-stu-id="192d7-115">The Strong Name tool generates a new public key every time it runs.</span></span> <span data-ttu-id="192d7-116">따라서 다음 예제와 같이 다음 코드의 공개 키를 방금 생성한 공개 키로 대체해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="192d7-116">Therefore, you must replace the public key in the following code with the public key you just generated, as shown in the following example.</span></span>  
   
   ```csharp  
   // friend_signed_A.cs  
   // Compile with:   
   // csc /target:library /keyfile:FriendAssemblies.snk friend_signed_A.cs  
   using System.Runtime.CompilerServices;  
   
   [assembly: InternalsVisibleTo("friend_signed_B, PublicKey=0024000004800000940000000602000000240000525341310004000001000100e3aedce99b7e10823920206f8e46cd5558b4ec7345bd1a5b201ffe71660625dcb8f9a08687d881c8f65a0dcf042f81475d2e88f3e3e273c8311ee40f952db306c02fbfc5d8bc6ee1e924e6ec8fe8c01932e0648a0d3e5695134af3bb7fab370d3012d083fa6b83179dd3d031053f72fc1f7da8459140b0af5afc4d2804deccb6")]  
   class Class1  
   {  
       public void Test()  
       {  
           System.Console.WriteLine("Class1.Test");  
           System.Console.ReadLine();  
       }  
   }  
   ```  
   
   ```vb  
   ' friend_signed_A.vb  
   ' Compile with:   
   ' Vbc -target:library -keyfile:FriendAssemblies.snk friend_signed_A.vb  
   Imports System.Runtime.CompilerServices  
   
   <Assembly: InternalsVisibleTo("friend_signed_B, PublicKey=0024000004800000940000000602000000240000525341310004000001000100e3aedce99b7e10823920206f8e46cd5558b4ec7345bd1a5b201ffe71660625dcb8f9a08687d881c8f65a0dcf042f81475d2e88f3e3e273c8311ee40f952db306c02fbfc5d8bc6ee1e924e6ec8fe8c01932e0648a0d3e5695134af3bb7fab370d3012d083fa6b83179dd3d031053f72fc1f7da8459140b0af5afc4d2804deccb6")>   
   Public Class Class1  
       Public Sub Test()  
           System.Console.WriteLine("Class1.Test")  
           System.Console.ReadLine()  
       End Sub  
   End Class  
   ```  
   
4. <span data-ttu-id="192d7-117">다음 명령을 사용하여 *friend_signed_A*를 컴파일하고 서명합니다.</span><span class="sxs-lookup"><span data-stu-id="192d7-117">Compile and sign *friend_signed_A* by using the following command.</span></span>  
   
   ```csharp
   csc /target:library /keyfile:FriendAssemblies.snk friend_signed_A.cs  
   ```  
   
   ```vb
   Vbc -target:library -keyfile:FriendAssemblies.snk friend_signed_A.vb  
   ```  
   
5. <span data-ttu-id="192d7-118">다음 코드를 포함하는 *friend_signed_B*라는 C# 또는 Visual Basic 파일을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="192d7-118">Create a C# or Visual Basic file named *friend_signed_B* that contains the following code.</span></span> <span data-ttu-id="192d7-119">*friend_signed_A*는 *friend_signed_B*를 friend 어셈블리로 지정하기 때문에 *friend_signed_B*의 코드는 *friend_signed_A*의 `internal`(C#) 또는 `Friend`(Visual Basic) 형식과 멤버에 액세스할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="192d7-119">Because *friend_signed_A* specifies *friend_signed_B* as a friend assembly, the code in *friend_signed_B* can access `internal` (C#) or `Friend` (Visual Basic) types and members from *friend_signed_A*.</span></span> <span data-ttu-id="192d7-120">파일에는 다음 코드가 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="192d7-120">The file contains the following code.</span></span>  
   
   ```csharp  
   // friend_signed_B.cs  
   // Compile with:   
   // csc /keyfile:FriendAssemblies.snk /r:friend_signed_A.dll /out:friend_signed_B.exe friend_signed_B.cs  
   public class Program  
   {  
       static void Main()  
       {  
           Class1 inst = new Class1();  
           inst.Test();  
       }  
   }  
   ```  
   
   ```vb  
   ' friend_signed_B.vb  
   ' Compile with:   
   ' Vbc -keyfile:FriendAssemblies.snk -r:friend_signed_A.dll friend_signed_B.vb  
   Module Sample  
       Public Sub Main()  
           Dim inst As New Class1  
           inst.Test()  
       End Sub  
   End Module  
   ```  
   
6. <span data-ttu-id="192d7-121">다음 명령을 사용하여 *friend_signed_B*를 컴파일하고 서명합니다.</span><span class="sxs-lookup"><span data-stu-id="192d7-121">Compile and sign *friend_signed_B* by using the following command.</span></span>  
   
   ```csharp
   csc /keyfile:FriendAssemblies.snk /r:friend_signed_A.dll /out:friend_signed_B.exe friend_signed_B.cs  
   ```  
   
   ```vb
   vbc -keyfile:FriendAssemblies.snk -r:friend_signed_A.dll friend_signed_B.vb  
   ```  
   
   <span data-ttu-id="192d7-122">컴파일러에서 생성된 어셈블리 이름은 <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> 특성에 전달된 friend 어셈블리 이름과 일치해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="192d7-122">The name of the assembly generated by the compiler must match the friend assembly name passed to the <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> attribute.</span></span> <span data-ttu-id="192d7-123">`/out` 컴파일러 옵션을 사용하여 출력 어셈블리( *.exe* 또는 *.dll*)의 이름을 명시적으로 지정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="192d7-123">You must explicitly specify the name of the output assembly (*.exe* or *.dll*) by using the `/out` compiler option.</span></span> <span data-ttu-id="192d7-124">자세한 내용은 [/out(C# 컴파일러 옵션)](../../csharp/language-reference/compiler-options/out-compiler-option.md) 또는 [-out(Visual Basic)](../../visual-basic/reference/command-line-compiler/out.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="192d7-124">For more information, see [/out (C# compiler options)](../../csharp/language-reference/compiler-options/out-compiler-option.md) or [-out (Visual Basic)](../../visual-basic/reference/command-line-compiler/out.md).</span></span>  
   
7. <span data-ttu-id="192d7-125">*friend_signed_B.exe* 파일을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="192d7-125">Run the *friend_signed_B.exe* file.</span></span>  
   
   <span data-ttu-id="192d7-126">프로그램이 **Class1.Test** 문자열을 출력합니다.</span><span class="sxs-lookup"><span data-stu-id="192d7-126">The program outputs the string **Class1.Test**.</span></span>  
  
## <a name="net-security"></a><span data-ttu-id="192d7-127">.NET 보안</span><span class="sxs-lookup"><span data-stu-id="192d7-127">.NET security</span></span>  
 <span data-ttu-id="192d7-128"><xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> 특성과 <xref:System.Security.Permissions.StrongNameIdentityPermission> 클래스 간에는 유사점이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="192d7-128">There are similarities between the <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> attribute and the <xref:System.Security.Permissions.StrongNameIdentityPermission> class.</span></span> <span data-ttu-id="192d7-129">주요 차이점은 <xref:System.Security.Permissions.StrongNameIdentityPermission>은 코드의 특정 섹션을 실행하는 보안 권한을 요구할 수 있는 반면, <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> 특성은 `internal`(C#) 또는 `Friend`(Visual Basic) 형식 및 멤버의 표시 유형을 제어한다는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="192d7-129">The main difference is that <xref:System.Security.Permissions.StrongNameIdentityPermission> can demand security permissions to run a particular section of code, whereas the <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> attribute controls the visibility of `internal` (C#) or `Friend` (Visual Basic) types and members.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="192d7-130">참고 항목</span><span class="sxs-lookup"><span data-stu-id="192d7-130">See also</span></span>

- <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute>
- [<span data-ttu-id="192d7-131">.NET 어셈블리</span><span class="sxs-lookup"><span data-stu-id="192d7-131">Assemblies in .NET</span></span>](index.md)
- [<span data-ttu-id="192d7-132">Friend 어셈블리</span><span class="sxs-lookup"><span data-stu-id="192d7-132">Friend assemblies</span></span>](friend.md)
- [<span data-ttu-id="192d7-133">방법: 서명되지 않은 friend 어셈블리 만들기</span><span class="sxs-lookup"><span data-stu-id="192d7-133">How to: Create unsigned friend assemblies</span></span>](create-unsigned-friend.md)
- [<span data-ttu-id="192d7-134">/keyfile(C#)</span><span class="sxs-lookup"><span data-stu-id="192d7-134">/keyfile (C#)</span></span>](../../csharp/language-reference/compiler-options/keyfile-compiler-option.md)
- [<span data-ttu-id="192d7-135">-keyfile(Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="192d7-135">-keyfile (Visual Basic)</span></span>](../../visual-basic/reference/command-line-compiler/keyfile.md)
- [<span data-ttu-id="192d7-136">Sn.exe(강력한 이름 도구)</span><span class="sxs-lookup"><span data-stu-id="192d7-136">Sn.exe (Strong Name tool)</span></span>](../../framework/tools/sn-exe-strong-name-tool.md)
- [<span data-ttu-id="192d7-137">강력한 이름의 어셈블리 만들기 및 사용</span><span class="sxs-lookup"><span data-stu-id="192d7-137">Create and use strong-named assemblies</span></span>](create-use-strong-named.md)
- [<span data-ttu-id="192d7-138">C# 프로그래밍 가이드</span><span class="sxs-lookup"><span data-stu-id="192d7-138">C# programming guide</span></span>](../../csharp/programming-guide/index.md)
- [<span data-ttu-id="192d7-139">프로그래밍 개념(Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="192d7-139">Programming concepts (Visual Basic)</span></span>](../../visual-basic/programming-guide/concepts/index.md)