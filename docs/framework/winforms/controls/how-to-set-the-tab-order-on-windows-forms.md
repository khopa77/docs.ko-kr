---
title: 컨트롤의 탭 순서 설정
description: Windows Forms 컨트롤의 탭 순서를 설정 하는 방법에 대해 알아봅니다. Visual Studio를 사용 하 여 탭 순서를 설정 하거나 속성 창의 TabIndex 속성을 사용 합니다.
ms.date: 03/30/2017
f1_keywords:
- TabStop
- TabIndex
helpviewer_keywords:
- tab order [Windows Forms], controls on Windows forms
- Windows Forms controls, setting tab order
- controls [Windows Forms], setting tab order
- Windows Forms, setting tab order
ms.assetid: 71fa8e76-0472-414b-ad3c-0f90166e0ad7
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 3d16da1ac73cc030b92bb36c4bfa3a79985339bf
ms.sourcegitcommit: 3824ff187947572b274b9715b60c11269335c181
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/17/2020
ms.locfileid: "84903364"
---
# <a name="how-to-set-the-tab-order-on-windows-forms"></a>방법: Windows Forms에서 탭 순서 설정

탭 순서는 Tab 키를 눌러 사용자가 한 컨트롤에서 다른 컨트롤로 포커스를 이동 하는 순서입니다. 각 양식에는 자체 탭 순서가 있습니다. 기본적으로 탭 순서는 컨트롤을 만든 순서와 동일 합니다. 탭 순서 번호는 0부터 시작 합니다.

## <a name="to-set-the-tab-order-of-a-control"></a>컨트롤의 탭 순서를 설정 하려면

1. Visual Studio의 **보기** 메뉴에서 **탭 순서**를 선택 합니다.

   이렇게 하면 폼에서 탭 순서 선택 모드가 활성화 됩니다. 속성을 나타내는 숫자가 <xref:System.Windows.Forms.Control.TabIndex%2A> 각 컨트롤의 왼쪽 위 모퉁이에 나타납니다.

2. 원하는 탭 순서를 설정 하려면 컨트롤을 순서 대로 클릭 합니다.

   > [!NOTE]
   > 탭 순서에서 컨트롤의 자리를 0 보다 크거나 같은 값으로 설정할 수 있습니다. 중복이 발생 하면 두 컨트롤의 z 순서가 평가 되 고 맨 위에 있는 컨트롤이 먼저 탭으로 이동 합니다. Z 축은 폼의 z 축 [depth]를 따라 폼에 있는 컨트롤의 시각적 계층화입니다. Z 순서에 따라 다른 컨트롤 앞에 있는 컨트롤이 결정 됩니다. Z 순서에 대 한 자세한 내용은 [Windows Forms에서 개체 계층화](how-to-layer-objects-on-windows-forms.md)를 참조 하세요.

3. 완료 되 면 **보기** 메뉴에서 **탭 순서** 를 다시 선택 하 여 탭 순서 모드를 유지 합니다.

   > [!NOTE]
   > 포커스를 가져올 수 없는 컨트롤 및 비활성화 된 컨트롤과 보이지 않는 컨트롤에는 <xref:System.Windows.Forms.Control.TabIndex%2A> 속성이 없으며 탭 순서에 포함 되지 않습니다. 사용자가 Tab 키를 누를 때 이러한 컨트롤을 건너뜁니다.

또는 속성을 사용 하 여 속성 창에서 탭 순서를 설정할 수 있습니다 <xref:System.Windows.Forms.Control.TabIndex%2A> . <xref:System.Windows.Forms.Control.TabIndex%2A>컨트롤의 속성은 탭 순서에서 위치가 지정 되는 위치를 결정 합니다. 기본적으로 그려진 첫 번째 컨트롤의 값은 <xref:System.Windows.Forms.Control.TabIndex%2A> 0이 고, 두 번째 컨트롤의 값은 <xref:System.Windows.Forms.Control.TabIndex%2A> 1입니다.

또한 기본적으로 컨트롤에는 <xref:System.Windows.Forms.GroupBox> 정수 값이 있습니다 <xref:System.Windows.Forms.Control.TabIndex%2A> . <xref:System.Windows.Forms.GroupBox>컨트롤 자체는 런타임에 포커스를 가질 수 없습니다. 따라서 내의 각 컨트롤에는 <xref:System.Windows.Forms.GroupBox> 0부터 시작 하는 10 진수 값이 있습니다 <xref:System.Windows.Forms.Control.TabIndex%2A> . 물론, 컨트롤의가 증가 하면 그에 <xref:System.Windows.Forms.Control.TabIndex%2A> <xref:System.Windows.Forms.GroupBox> 따라 컨트롤이 증가 합니다. <xref:System.Windows.Forms.Control.TabIndex%2A>5에서 6 사이의 값을 변경한 경우 <xref:System.Windows.Forms.Control.TabIndex%2A> 해당 그룹의 첫 번째 컨트롤 값이 자동으로 6.0로 변경 됩니다.

마지막으로, 폼의 많은 컨트롤은 탭 순서에서 건너뛸 수 있습니다. 일반적으로 런타임에 Tab 키를 누르면 탭 순서의 각 컨트롤이 선택 됩니다. 속성을 끄면 <xref:System.Windows.Forms.Control.TabStop%2A> 폼의 탭 순서에서 컨트롤이 전달 되도록 할 수 있습니다.

## <a name="to-remove-a-control-from-the-tab-order"></a>탭 순서에서 컨트롤을 제거 하려면

<xref:System.Windows.Forms.Control.TabStop%2A> **속성** 창에서 컨트롤의 속성을 **false** 로 설정 합니다.

Tab 키를 사용 하 여 컨트롤을 <xref:System.Windows.Forms.Control.TabStop%2A> 순환할 때 컨트롤이 생략 되더라도 속성이로 설정 된 컨트롤은 `false` 탭 순서에서 해당 위치를 계속 유지 합니다.

> [!NOTE]
> 라디오 단추 그룹은 런타임에 단일 탭 정지를 가집니다. 선택 된 단추 (즉, <xref:System.Windows.Forms.RadioButton.Checked%2A> 속성이로 설정 된 단추 `true` )의 속성은 자동으로로 설정 되 고 <xref:System.Windows.Forms.Control.TabStop%2A> `true` 다른 단추의 <xref:System.Windows.Forms.Control.TabStop%2A> 속성은로 설정 `false` 됩니다. 컨트롤을 그룹화 하는 방법에 대 한 자세한 내용은 <xref:System.Windows.Forms.RadioButton> [그룹화 Windows Forms RadioButton 컨트롤이 집합으로 작동 하도록 설정](how-to-group-windows-forms-radiobutton-controls-to-function-as-a-set.md)을 참조 하세요.

## <a name="see-also"></a>참고 항목

- [Windows Forms 컨트롤](index.md)
- [Windows Forms에 사용할 수 있는 컨트롤](controls-to-use-on-windows-forms.md)
- [기능별 Windows Forms 컨트롤](windows-forms-controls-by-function.md)
