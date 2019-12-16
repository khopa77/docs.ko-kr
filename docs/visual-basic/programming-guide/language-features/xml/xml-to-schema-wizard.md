---
title: "XML to Schema 마법사 (Visual Basic) | Microsoft 문서"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vb.XmlToSchemaWizard
dev_langs:
- VB
helpviewer_keywords:
- XML IntelliSense [Visual Basic]
- XML [Visual Basic], IntelliSense
- IntelliSense [Visual Basic], XML
- XML schemas, creating
ms.assetid: 98c495ba-8f37-4517-a0db-aa738611ab76
caps.latest.revision: 16
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: 4b31c0c6671aa48e050468f05457b43bcceffaed
ms.contentlocale: ko-kr
ms.lasthandoff: 04/12/2017

---
# <a name="xml-to-schema-wizard-visual-basic"></a><span data-ttu-id="684a4-102">XML to Schema 마법사(Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="684a4-102">XML to Schema Wizard (Visual Basic)</span></span>
<span data-ttu-id="684a4-103">XML to Schema 마법사를 사용 하 여 하나 이상의 XML 문서에서 유추 하는 XML 스키마 집합을 만들고 프로젝트를 포함 합니다.</span><span class="sxs-lookup"><span data-stu-id="684a4-103">Use the XML to Schema Wizard to create an XML schema set that is inferred from one or more XML documents and include it your project.</span></span> <span data-ttu-id="684a4-104">HTTP 인터넷 주소에서 XML 또는 형식화 하거나 XML to Schema 마법사에 붙여 넣은 XML 텍스트 파일의 형태로 XML 문서의 모든 조합을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="684a4-104">You can use any combination of XML documents in the form of text files, XML from HTTP Internet addresses, or XML that is typed or pasted into the XML to Schema Wizard.</span></span>  
  
 <span data-ttu-id="684a4-105">XML 스키마는 Visual Basic의 XML 속성에 대 한 IntelliSense를 제공 하는 데 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="684a4-105">XML schemas are used to provide IntelliSense for XML properties in Visual Basic.</span></span> <span data-ttu-id="684a4-106">자세한 내용은 참조 [XML](../../../../visual-basic/programming-guide/language-features/xml/index.md) 및 [Visual Basic의 XML IntelliSense](../../../../visual-basic/programming-guide/language-features/xml/xml-intellisense.md)합니다.</span><span class="sxs-lookup"><span data-stu-id="684a4-106">For more information, see [XML](../../../../visual-basic/programming-guide/language-features/xml/index.md) and [XML IntelliSense in Visual Basic](../../../../visual-basic/programming-guide/language-features/xml/xml-intellisense.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="684a4-107">XML to Schema 마법사를 실행 하기 전에 마법사에서 이전에 생성 된 프로젝트에서 기존 XSD 파일을 제거 하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="684a4-107">Before you run the XML to Schema Wizard, it is recommended that you remove any existing XSD files from the project that were previously generated by the wizard.</span></span> <span data-ttu-id="684a4-108">기존 스키마 집합에 일치 하는 XML 스키마 집합을 유추 하려고 하면 충돌이 발생 하 고 [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] XML 속성에 대 한 IntelliSense를 제공할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="684a4-108">If you infer an XML schema set that matches an existing schema set, a conflict can occur and [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] will not be able to provide IntelliSense for XML properties.</span></span>  
  
 <span data-ttu-id="684a4-109">XML to Schema 마법사를 사용 하 여는 <xref:System.Xml.Schema.XmlSchemaInference>클래스를 지정 된 XML에 대 한 스키마를 만듭니다.</xref:System.Xml.Schema.XmlSchemaInference></span><span class="sxs-lookup"><span data-stu-id="684a4-109">The XML to Schema Wizard uses the <xref:System.Xml.Schema.XmlSchemaInference> class to create the schema for the supplied XML.</span></span> <span data-ttu-id="684a4-110">결과적으로, 스키마 집합에 대 한 여러 스키마 파일을 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="684a4-110">As a result, multiple schema files may be created for the schema set.</span></span> <span data-ttu-id="684a4-111">지정 된 XML의 각 XML 네임 스페이스에 대 한 확장 가능한 스키마 정의 (XSD) 파일 생성 됩니다.</span><span class="sxs-lookup"><span data-stu-id="684a4-111">For each XML namespace in the supplied XML, an Extensible Schema Definition (XSD) file is created.</span></span> <span data-ttu-id="684a4-112">자세한 내용은 참조는 <xref:System.Xml.Schema.XmlSchemaInference.InferSchema%2A>메서드.</xref:System.Xml.Schema.XmlSchemaInference.InferSchema%2A></span><span class="sxs-lookup"><span data-stu-id="684a4-112">For more information, see the <xref:System.Xml.Schema.XmlSchemaInference.InferSchema%2A> method.</span></span>  
  
 <span data-ttu-id="684a4-113">XML to Schema 마법사에 액세스 하려면 **새 항목 추가** 에 **프로젝트** 메뉴 추가 **XML 스키마를** 템플릿 중 하나에서 **데이터** 또는 **공통 항목** 템플릿 그룹입니다.</span><span class="sxs-lookup"><span data-stu-id="684a4-113">To access the XML to Schema Wizard, click **Add New Item** on the **Project** menu and add an **XML to Schema** template from either the **Data** or **Common Items** template group.</span></span> <span data-ttu-id="684a4-114">모든 XML 문서 소스에서 XML 스키마 집합을 유추를 포함 한 후 클릭 **확인** 유추 된 스키마를 만들려면 다음을 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="684a4-114">After you have included all the XML document sources to infer the XML schema set from, click **OK** to create the inferred schema set.</span></span>  
  
 <span data-ttu-id="684a4-115">**원본 유형**</span><span class="sxs-lookup"><span data-stu-id="684a4-115">**Source Type**</span></span>  
 <span data-ttu-id="684a4-116">이 열에 XML 문서 소스의 유형을 표시: **파일**, **URL**, 또는 **XML**합니다.</span><span class="sxs-lookup"><span data-stu-id="684a4-116">This column displays the type of the XML document source: **File**, **URL**, or **XML**.</span></span>  
  
 <span data-ttu-id="684a4-117">**XML 문서 위치**</span><span class="sxs-lookup"><span data-stu-id="684a4-117">**XML Document Location**</span></span>  
 <span data-ttu-id="684a4-118">이 열은 XML 문서 경로 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="684a4-118">This column displays the path of the XML document.</span></span> <span data-ttu-id="684a4-119">입력 하거나 붙여넣은 XML 문서에 대 한 XML 문서의 내용을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="684a4-119">For typed or pasted XML documents, displays the contents of the XML document.</span></span>  
  
 <span data-ttu-id="684a4-120">**파일에서 추가**</span><span class="sxs-lookup"><span data-stu-id="684a4-120">**Add from File**</span></span>  
 <span data-ttu-id="684a4-121">파일 탐색기를 사용 하 여 XML 문서 파일을 추가 하려면이 단추를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="684a4-121">Click this button to add XML document files by using File Explorer.</span></span>  
  
 <span data-ttu-id="684a4-122">**웹에서 추가**</span><span class="sxs-lookup"><span data-stu-id="684a4-122">**Add from Web**</span></span>  
 <span data-ttu-id="684a4-123">XML 문서의 HTTP 주소를 제공 하려면이 단추를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="684a4-123">Click this button to supply the HTTP address of an XML document.</span></span>  
  
 <span data-ttu-id="684a4-124">**입력 하거나 XML을 붙여 넣습니다**</span><span class="sxs-lookup"><span data-stu-id="684a4-124">**Type or paste XML**</span></span>  
 <span data-ttu-id="684a4-125">입력 하거나 대화 상자에는 XML 문서를 붙여 넣습니다.이 단추를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="684a4-125">Click this button to type or paste an XML document into the dialog box.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="684a4-126">참고 항목</span><span class="sxs-lookup"><span data-stu-id="684a4-126">See Also</span></span>  
 <span data-ttu-id="684a4-127"><xref:System.Xml.Schema.XmlSchemaInference></xref:System.Xml.Schema.XmlSchemaInference></span><span class="sxs-lookup"><span data-stu-id="684a4-127"><xref:System.Xml.Schema.XmlSchemaInference></span></span>   
<span data-ttu-id="684a4-128"> [Visual Basic의 XML IntelliSense](../../../../visual-basic/programming-guide/language-features/xml/xml-intellisense.md)</span><span class="sxs-lookup"><span data-stu-id="684a4-128"> [XML IntelliSense in Visual Basic](../../../../visual-basic/programming-guide/language-features/xml/xml-intellisense.md)</span></span>