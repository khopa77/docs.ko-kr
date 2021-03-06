---
title: <system.codedom> 요소
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.codedom
- http://schemas.microsoft.com/.NetConfiguration/v2.0#system.codedom
helpviewer_keywords:
- compiler configuration elements, <system.codedom> element
- system.codedom element
- <system.codedom> element
ms.assetid: 672a68f7-e69f-4479-ac30-e980085ec4fe
ms.openlocfilehash: 40a3c84e1deed4d215383670176623a6a79ac41d
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/06/2020
ms.locfileid: "79155390"
---
# <a name="systemcodedom-element"></a>\<system.codedom> 요소
사용 가능한 언어 공급자에 대한 컴파일러 구성 설정을 지정합니다.  
  
[**\<configuration>**](../configuration-element.md)  
&nbsp;&nbsp;**\<system.codedom>**  
  
## <a name="syntax"></a>구문  
  
```xml  
<system.codedom>  
  <compilers> ... </compilers>  
</system.codedom>  
```  
  
## <a name="attributes-and-elements"></a>특성 및 요소  
 다음 섹션에서는 특성, 자식 요소 및 부모 요소에 대해 설명합니다.  
  
### <a name="attributes"></a>특성  
 없음  
  
### <a name="child-elements"></a>자식 요소  
  
|요소|Description|  
|-------------|-----------------|  
|[\<compilers>](compilers-element.md)|컴파일러 구성 요소에 대 한 컨테이너입니다. 0 개 이상의 [\<compiler>](compiler-element.md) 요소를 포함 합니다.|  
  
### <a name="parent-elements"></a>부모 요소  
  
|요소|Description|  
|-------------|-----------------|  
|[\<configuration>](../configuration-element.md)|공용 언어 런타임 및 .NET Framework 애플리케이션에서 사용하는 모든 구성 파일의 루트 요소입니다.|  
  
## <a name="remarks"></a>설명  
  
## <a name="net-framework-version-20"></a>.NET Framework 버전 2.0  
 요소에는 [\<system.codedom>](system-codedom-element.md) 및와 같은 .NET Framework와 함께 설치 되는 기본 공급자 외에도 컴퓨터에 설치 된 언어 공급자에 대 한 컴파일러 구성 설정이 포함 되어 있습니다 <xref:Microsoft.CSharp.CSharpCodeProvider> <xref:Microsoft.VisualBasic.VBCodeProvider> . [\<compilers>](compilers-element.md)요소는 0 개 이상의 요소를 포함 [\<compiler>](compiler-element.md) 합니다. 각 [\<compiler>](compiler-element.md) 요소는 특정 언어 공급자에 대 한 컴파일러 구성 특성을 지정 합니다.  
  
 개발자와 컴파일러 공급 업체는 새 구현에 대 한 구성 설정을 컴퓨터 구성 파일 (machine.config)에 추가할 수 있습니다 <xref:System.CodeDom.Compiler.CodeDomProvider> . 메서드를 사용 <xref:System.CodeDom.Compiler.CodeDomProvider.GetAllCompilerInfo%2A?displayProperty=nameWithType> 하 여 컴퓨터의 컴파일러 구성 설정으로 식별 되는 기본 언어 공급자와 언어 공급자를 프로그래밍 방식으로 열거 합니다.  
  
> [!NOTE]
> .NET Framework 버전 1.0 및 1.1에서는 .NET Framework에서 제공 하는 기본 언어 공급자가 요소에서 식별 됩니다 [\<compilers>](compilers-element.md) . .NET Framework 버전 2.0에서 기본 언어 공급자는 요소에서 식별 되지 [\<compilers>](compilers-element.md) 않지만 메서드를 사용 하 여 열거할 수 있습니다 <xref:System.CodeDom.Compiler.CodeDomProvider.GetAllCompilerInfo%2A> .  
  
## <a name="net-framework-versions-10-and-11"></a>.NET Framework 버전 1.0 및 1.1  
 요소에는 [\<system.codedom>](system-codedom-element.md) 컴퓨터의 언어 공급자에 대 한 컴파일러 구성 설정이 포함 되어 있습니다. [\<compilers>](compilers-element.md)요소는 0 개 이상의 요소를 포함 [\<compiler>](compiler-element.md) 합니다. 각 [\<compiler>](compiler-element.md) 요소는 특정 언어 공급자에 대 한 컴파일러 구성 특성을 지정 합니다.  
  
 .NET Framework는 컴퓨터 구성 파일(Machine.config)의 초기 컴파일러 설정을 정의합니다. 개발자 및 컴파일러 공급업체는 새로운 <xref:System.CodeDom.Compiler.CodeDomProvider> 구현에 대한 구성 설정을 추가할 수 있습니다. <xref:System.CodeDom.Compiler.CodeDomProvider.GetAllCompilerInfo%2A?displayProperty=nameWithType> 메서드를 사용하여 컴퓨터에서 언어 공급자 및 컴파일러 구성 설정을 프로그래밍 방식으로 열거할 수 있습니다.  
  
## <a name="configuration-file"></a>구성 파일  
 이 요소는 컴퓨터 구성 파일 및 응용 프로그램 구성 파일에서 사용할 수 있습니다.  
  
## <a name="example"></a>예제  
 다음 예제에서는 일반적인 컴파일러 구성을 보여 줍니다.  
  
```xml  
<configuration>  
  <system.codedom>  
    <compilers>  
      <!-- zero or more compiler elements -->  
      <compiler
        language="c#;cs;csharp"  
        extension=".cs"  
        type="Microsoft.CSharp.CSharpCodeProvider, System,
          Version=1.0.5000.0, Culture=neutral,
          PublicKeyToken=b77a5c561934e089"  
        compilerOptions=""  
        warningLevel="1" />  
    </compilers>  
  </system.codedom>  
</configuration>  
```  
  
## <a name="see-also"></a>참조

- <xref:System.CodeDom.Compiler.CompilerInfo>
- <xref:System.CodeDom.Compiler.CodeDomProvider>
- [구성 파일 스키마](../index.md)
- [컴파일러 및 언어 공급자 설정 스키마](index.md)
- [\<compiler>요소인](compiler-element.md)
