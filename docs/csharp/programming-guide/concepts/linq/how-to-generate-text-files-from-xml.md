---
title: XML에서 텍스트 파일을 생성하는 방법(C#)
ms.date: 07/20/2015
ms.assetid: 9ad283f7-7cac-42ff-bf32-92aa866e6883
ms.openlocfilehash: 9ca76cf955e07bdcc8e095b30f6fadc74edba739
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75345926"
---
# <a name="how-to-generate-text-files-from-xml-c"></a>XML에서 텍스트 파일을 생성하는 방법(C#)
이 예제에서는 XML 파일에서 CSV(쉼표로 구분된 값) 파일을 생성하는 방법을 보여 줍니다.  
  
## <a name="example"></a>예제  
 이 예제의 C# 버전에서는 메서드 구문과 `Aggregate` 연산자를 사용하여 단일 식으로 XML 문서에서 CSV 파일을 생성합니다. 자세한 내용은 [LINQ의 쿼리 구문 및 메서드 구문](./query-syntax-and-method-syntax-in-linq.md)을 참조하세요.  
  
 이 예제에서는 XML 문서 [샘플 XML 파일: 고객 및 주문(LINQ to XML)](./sample-xml-file-customers-and-orders-linq-to-xml-2.md)을 사용합니다.  
  
```csharp  
XElement custOrd = XElement.Load("CustomersOrders.xml");  
string csv =  
    (from el in custOrd.Element("Customers").Elements("Customer")  
    select  
        String.Format("{0},{1},{2},{3},{4},{5},{6},{7},{8},{9}{10}",  
            (string)el.Attribute("CustomerID"),  
            (string)el.Element("CompanyName"),  
            (string)el.Element("ContactName"),  
            (string)el.Element("ContactTitle"),  
            (string)el.Element("Phone"),  
            (string)el.Element("FullAddress").Element("Address"),  
            (string)el.Element("FullAddress").Element("City"),  
            (string)el.Element("FullAddress").Element("Region"),  
            (string)el.Element("FullAddress").Element("PostalCode"),  
            (string)el.Element("FullAddress").Element("Country"),  
            Environment.NewLine  
        )  
    )  
    .Aggregate(  
        new StringBuilder(),  
        (sb, s) => sb.Append(s),  
        sb => sb.ToString()  
    );  
Console.WriteLine(csv);  
```  
  
 이 코드의 결과는 다음과 같습니다.  
  
```output  
GREAL,Great Lakes Food Market,Howard Snyder,Marketing Manager,(503) 555-7555,2732 Baker Blvd.,Eugene,OR,97403,USA  
HUNGC,Hungry Coyote Import Store,Yoshi Latimer,Sales Representative,(503) 555-6874,City Center Plaza 516 Main St.,Elgin,OR,97827,USA  
LAZYK,Lazy K Kountry Store,John Steel,Marketing Manager,(509) 555-7969,12 Orchestra Terrace,Walla Walla,WA,99362,USA  
LETSS,Let's Stop N Shop,Jaime Yorres,Owner,(415) 555-5938,87 Polk St. Suite 5,San Francisco,CA,94117,USA  
```  
  
## <a name="see-also"></a>참고 항목

- [프로젝션 및 변환(LINQ to XML)(C#)](how-to-work-with-dictionaries-using-linq-to-xml.md)
