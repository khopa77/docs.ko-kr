---
title: Windows Presentation Foundation의 개념
description: 이 문서에서는 .NET Core와 관련해서 WPF(Windows Presentation Foundation)의 개념 및 제공되는 기능을 간단히 살펴봅니다.
ms.date: 07/18/2019
ms.topic: overview
ms.openlocfilehash: 63b2e431b5ab5fd3875887b8b574a77aa12018a6
ms.sourcegitcommit: 961ec21c22d2f1d55c9cc8a7edf2ade1d1fd92e3
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/02/2020
ms.locfileid: "85840294"
---
# <a name="what-is-windows-presentation-foundation"></a>Windows Presentation Foundation의 개념

Windows용 데스크톱 클라이언트 애플리케이션을 만드는 UI 프레임워크인 WPF(Windows Presentation Foundation)에 관한 데스크톱 가이드를 시작합니다. WPF 개발 플랫폼은 애플리케이션 모델, 컨트롤, 그래픽 및 데이터 바인딩을 포함하여 다양한 애플리케이션 개발 기능 세트를 지원합니다. WPF는 XAML(Extensible Application Markup Language)을 사용하여 애플리케이션 프로그래밍을 위한 선언적 모델을 제공합니다.

[!INCLUDE [desktop guide under construction](../../../includes/desktop-guide-preview-note.md)]

WPF에는 다음과 같은 두 가지 구현이 있습니다.

01. [GitHub](https://github.com/dotnet/wpf)에서 호스트되는 오픈 소스 구현. 이 버전은 .NET Core 3.0에서 실행됩니다. XAML용 WPF 비주얼 디자이너에는 최소한 [Visual Studio 2019 버전 16.3](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019+desktopguide)이 필요합니다.

01. Visual Studio 2019 및 Visual Studio 2017에서 지원되는 .NET Framework 구현.

이 데스크톱 가이드는 .NET Core 3.0 및 WPF용으로 작성되었습니다. .NET Framework와 함께 WPF의 기존 설명서에 관한 자세한 내용은 [프레임워크 Windows Presentation Foundation](../../framework/wpf/index.md)을 참조하세요.

## <a name="xaml"></a>XAML

XAML은 WPF에서 리소스 또는 UI 요소 정의와 같은 작업에 사용하는 선언적 XML 기반 언어입니다. XAML로 정의된 요소는 어셈블리에서 개체의 인스턴스화를 나타냅니다. XAML은 지원 형식 시스템에 직접 연결하지 않고 런타임에 해석되는 대부분의 다른 태그 언어와 다릅니다.

다음 예제에서는 UI의 일부로 단추를 만드는 방법을 보여 줍니다. 이 예제는 XAML이 개체를 나타내는 방법을 설명하기 위한 것입니다. 여기서 `Button`은 형식이고 `Content`는 속성입니다.

```xaml
<StackPanel>
    <Button Content="Click Me!" />
</StackPanel>
```

<!--For more information, see [XAML overview (WPF)](../../../framework/wpf/advanced/xaml-overview-wpf.md).-->

### <a name="xaml-extensions"></a>XAML 확장

XAML은 태그 확장 구문을 제공합니다. 태그 확장은 특성 양식, 속성 요소 양식 또는 둘 다에서 속성 값을 제공하는 데 사용할 수 있습니다.

예를 들어 이전 XAML 코드는 표시된 콘텐츠가 리터럴 문자열 `"Click Me!"`로 설정된 단추를 정의했지만, 콘텐츠는 지원되는 태그 확장을 통해 설정될 수 있습니다. 태그 확장은 여는 중괄호와 닫는 중괄호 `{ }`를 사용하여 정의됩니다. 태그 확장 형식은 여는 중괄호 바로 다음에 오는 문자열 토큰으로 식별됩니다.

```xaml
<StackPanel>
    <Button Content="{MarkupType}" />
</StackPanel>
```

WPF는 데이터 바인딩의 `{Binding}`과 같이 XAML에 대해 다른 태그 확장을 제공합니다.

자세한 내용은 [태그 확장 및 WPF XAML](../../framework/wpf/advanced/markup-extensions-and-wpf-xaml.md)을 참조하세요.

## <a name="property-system"></a>속성 시스템

WPF는 형식 [속성](../../standard/base-types/common-type-system.md#properties)의 기능을 확장하는 데 사용할 수 있는 서비스 세트를 제공합니다. 해당 서비스를 ‘WPF 속성 시스템’이라고 통칭합니다. WPF 속성 시스템에서 지원하는 속성을 종속성 속성이라고 합니다.

종속성 속성은 속성을 백업하는 <xref:System.Windows.DependencyProperty> 형식을 제공하여 속성 기능을 확장합니다. 종속성 속성 형식은 프라이빗 필드를 사용하여 속성을 지원하는 표준 패턴의 대체 구현입니다.

### <a name="dependency-property"></a>종속성 속성

WPF에서 종속성 속성은 일반적으로 표준 .NET [속성](../../standard/base-types/common-type-system.md#properties)으로 공개됩니다. 기본 수준에서는 이 속성을 직접 조작할 수 있으며 종속성 속성으로 구현되는지를 알 수 없습니다.

종속성 속성의 용도는 다른 입력 값을 기반으로 속성의 값을 계산하는 방법을 제공하는 것입니다. 이와 같은 다른 입력에는 테마 및 사용자 기본 설정과 같은 시스템 속성이나 데이터 바인딩 및 애니메이션의 Just-In-Time 속성이 포함될 수 있습니다.

유효성 검사, 기본값 및 다른 속성의 변경 내용을 모니터링하는 콜백을 제공하기 위해 종속성 속성을 구현할 수 있습니다. 파생 클래스는 새 속성을 만들거나 기존 속성의 실제 구현을 재정의하는 대신 종속성 속성 메타데이터를 재정의하여 기존 속성의 일부 특정 특성을 변경할 수도 있습니다.

### <a name="dependency-object"></a>종속성 개체

WPF 속성 시스템에 대한 키인 또 다른 형식은 <xref:System.Windows.DependencyObject>입니다. 이 형식은 종속성 속성을 등록하고 소유할 수 있는 기본 클래스를 정의합니다. <xref:System.Windows.DependencyObject.GetValue%2A> 및 <xref:System.Windows.DependencyObject.SetValue%2A> 메서드는 종속성 개체 인스턴스를 위한 종속성 속성의 지원 구현을 제공합니다.

다음 예제에서는 `ValueProperty`라는 단일 종속성 속성 식별자를 정의하는 종속성 개체를 보여 줍니다. 종속성 속성은 `Value` .NET 속성을 사용하여 만듭니다.

```csharp
public class TextField: DependencyObject
{
    public static readonly DependencyProperty ValueProperty =
        DependencyProperty.Register("Value", typeof(string), typeof(TextField), new PropertyMetadata(""));

    public string Value
    {
        get { return (string)GetValue(ValueProperty); }
        set { SetValue(ValueProperty, value); }
    }
}
```

종속성 속성은 위 예제의 `TextField`와 같은 종속성 개체 형식의 정적 멤버로 정의됩니다. 종속성 속성은 종속성 개체에 등록해야 합니다.

위 예제의 `Value` 속성은 종속성 속성을 래핑하여 사용될 수 있는 표준 .NET 속성 패턴을 제공합니다.

<!--For more information, see [Dependency properties overview](../../../framework/wpf/advanced/dependency-properties-overview.md).-->

## <a name="events"></a>이벤트

WPF는 친숙한 .NET CLR(공용 언어 런타임) 이벤트 위에 계층화된 이벤트 시스템을 제공합니다. 이 WPF 이벤트를 라우트된 이벤트라고 합니다.

라우트된 이벤트는 `RoutedEvent` 클래스의 인스턴스에서 지원되고 WPF 이벤트 시스템에 등록된 CLR 이벤트입니다. 일반적으로 이벤트 등록에서 얻은 `RoutedEvent` 인스턴스는 라우트된 이벤트를 등록하고 이에 따라 ‘소유’하는 클래스의 `public static readonly` 필드 멤버로 유지됩니다. 동일하게 명명된 CLR 이벤트(경우에 따라 ‘래퍼’ 이벤트라고 함)에 연결하려면 CLR 이벤트에 대한 `add` 및 `remove` 구현을 재정의합니다. 라우트된 이벤트 지원 및 연결 메커니즘은 [종속성 속성](#dependency-property)이 `DependencyProperty` 클래스에서 지원되고 WPF 속성 시스템에 등록된 CLR 속성이 되는 방식과 개념적으로 비슷합니다.

라우트된 이벤트 시스템의 주요 장점은 이벤트가 처리기를 검색하는 컨트롤 요소 트리를 ‘버블링’된다는 것입니다. 예를 들어 WPF에는 풍부한 콘텐츠 모델이 있으므로 이미지 컨트롤을 단추 컨트롤의 콘텐츠로 설정합니다. 이미지 컨트롤에서 마우스를 클릭하면 마우스 이벤트를 사용하므로 단추가 `Click` 이벤트를 호출하도록 하는 적중 테스트를 중단할 것으로 예상됩니다. 기존 CLR 이벤트 모델에서는 동일한 처리기를 이미지와 단추에 둘 다 연결하여 이 제한을 해결합니다. 그러나 라우트된 이벤트 시스템을 사용하면 이미지 컨트롤에서 호출된 마우스 이벤트(예: 이미지 컨트롤 선택)가 부모 단추 컨트롤에 버블링됩니다.

<!--For more information, including other types of event models, see [Events overview](../../../framework/wpf/advanced/routed-events-overview.md).-->

## <a name="data-binding"></a>데이터 바인딩

WPF 데이터 바인딩을 통해 애플리케이션은 단순하고 일관되게 데이터를 제공하고 데이터와 상호 작용할 수 있습니다. 요소는 CLR(공용 언어 런타임) 개체 및 XML 형식으로 다양한 형식의 데이터 소스에서 데이터에 바인딩할 수 있습니다. 또한 WPF는 끌어서 놓기 작업을 통해 데이터 전송을 위한 메커니즘을 제공합니다.

데이터 바인딩은 애플리케이션 UI와 비즈니스 논리 간에 연결을 설정하는 프로세스입니다. 바인딩 설정이 올바르고 데이터가 적절한 알림을 제공하는 경우에는 데이터의 값이 변경될 때 데이터에 바인딩된 요소에 변경 내용이 자동으로 반영됩니다. 또한 데이터 바인딩에서는 요소에서 데이터의 외부 표현이 변경되면 내부 데이터가 자동으로 업데이트되어 변경 내용을 반영합니다. 예를 들어 사용자가 TextBox 요소의 값을 편집하면 내부 데이터 값이 자동으로 업데이트되어 해당 변경 내용이 반영됩니다.

`{Binding}` 태그 확장을 통해 XAML에서 데이터 바인딩을 구성할 수 있습니다. 다음 예제에서는 데이터 개체의 `ButtonText` 속성에 바인딩하는 작업을 보여 줍니다. 바인딩에 실패하면 `Click Me!` 값이 사용됩니다.

```xaml
<StackPanel>
    <Button Content="{Binding ButtonText, FallbackValue='Click Me!'}" />
</StackPanel>
```

자세한 내용은 [데이터 바인딩 개요](../data/data-binding-overview.md)를 참조하세요.

## <a name="ui-components"></a>UI 구성 요소

WPF는 `Button`, `Label`, `TextBox`, `Menu` 및 `ListBox`와 같이 거의 모든 Windows 애플리케이션에서 사용되는 많은 공통적인 UI 구성 요소를 제공합니다. 지금까지 이러한 개체는 컨트롤이라고 불렀습니다. WPF SDK에서는 계속해서 컨트롤이라는 용어를 사용하여 애플리케이션에 표시되는 개체를 나타내는 모든 클래스를 대략적으로 지칭합니다. 그러나 클래스는 반드시 `Control` 클래스에서 상속되어야 그 존재가 표시되는 것은 아닙니다. `Control` 클래스에서 상속된 클래스에는 `ControlTemplate`이 포함되어 있습니다. 따라서 컨트롤 소비자는 새 서브클래스를 만들지 않아도 컨트롤의 모양을 대폭 변경할 수 있습니다.

## <a name="styles-and-templates"></a>스타일 및 템플릿

WPF 스타일 지정 및 템플릿은 애플리케이션, 문서 또는 UI 디자이너가 시각적으로 눈에 띄는 애플리케이션을 만들고 제품의 특정 모양을 표준화할 수 있는 기능 모음(스타일, 템플릿, 트리거 및 스토리보드)을 나타냅니다.

WPF 스타일 지정 모델의 또 다른 기능은 프레젠테이션과 논리를 분리하는 것입니다. 즉, 개발자가 다른 곳에서 프로그래밍 논리 작업을 하는 동안 디자이너는 XAML을 사용하여 애플리케이션의 모양 작업을 할 수 있습니다.

또한 스타일 및 템플릿을 다시 사용하도록 지원하는 리소스를 이해해야 합니다.

자세한 내용은 [스타일 및 템플릿](../fundamentals/styles-templates-overview.md)을 참조하세요.

## <a name="resources"></a>리소스

WPF 리소스는 애플리케이션의 여러 위치에서 다시 사용할 수 있는 개체입니다. 리소스의 예로는 스타일, 템플릿 및 색 브러시가 있습니다. 리소스는 코드 및 XAML 형식으로 정의되고 참조될 수 있습니다.

모든 프레임워크 수준 요소(<xref:System.Windows.FrameworkElement> 또는 <xref:System.Windows.FrameworkContentElement>)에는 정의된 리소스를 포함하는 <xref:System.Windows.ResourceDictionary> 형식의 `Resources` 속성이 있습니다. 모든 요소는 프레임워크 수준 요소에서 상속되므로 모든 요소가 리소스를 정의할 수 있습니다. 그러나 XAML 문서의 루트 요소에서 리소스를 정의하는 것이 가장 일반적입니다.

<!--For more information, see [XAML Resources](../../../framework/wpf/advanced/xaml-resources.md).-->

## <a name="next-steps"></a>다음 단계

- [WPF 애플리케이션 만들기](https://docs.microsoft.com/visualstudio/get-started/csharp/tutorial-wpf?toc=/dotnet/desktop-wpf/toc.json&bc=/dotnet/breadcrumb/toc.json)
- [.NET Framework의 차이점 살펴보기](../migration/differences-from-net-framework.md)
- [XAML에 관한 자세한 정보](../fundamentals/xaml.md)
