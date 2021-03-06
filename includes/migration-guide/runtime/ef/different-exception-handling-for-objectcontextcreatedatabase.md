---
ms.openlocfilehash: 687118157020ede200f97a0125c4740a06bf4b5e
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85620306"
---
### <a name="different-exception-handling-for-objectcontextcreatedatabase-and-dbproviderservicescreatedatabase-methods"></a>ObjectContext.CreateDatabase 및 DbProviderServices.CreateDatabase 메서드를 처리하는 다른 예외

#### <a name="details"></a>설명

.NET Framework 4.5부터 데이터베이스 만들기에 실패하면 <code>CreateDatabase</code> 메서드는 빈 데이터베이스를 삭제하려고 합니다. 해당 작업에 성공하면 원래의 <xref:System.Data.SqlClient.SqlException?displayProperty=fullName>이 전파됩니다(항상 .NET Framework 4.0에서 throw된 <xref:System.InvalidOperationException?displayProperty=fullName> 대신).

#### <a name="suggestion"></a>제안 해결 방법

<xref:System.Data.Objects.ObjectContext.CreateDatabase> 또는 <xref:System.Data.Common.DbProviderServices.CreateDatabase(System.Data.Common.DbConnection,System.Nullable{System.Int32},System.Data.Metadata.Edm.StoreItemCollection)>를 실행하는 동안 <xref:System.InvalidOperationException?displayProperty=fullName>을 catch하는 경우, 이제 SQLExceptions도 catch됩니다.

| 이름    | 값       |
|:--------|:------------|
| Scope   |부|
|버전|4.5|
|형식|런타임

#### <a name="affected-apis"></a>영향을 받는 API

-<xref:System.Data.Objects.ObjectContext.CreateDatabase?displayProperty=nameWithType></li><li><xref:System.Data.Common.DbProviderServices.CreateDatabase(System.Data.Common.DbConnection,System.Nullable{System.Int32},System.Data.Metadata.Edm.StoreItemCollection)?displayProperty=nameWithType></li></ul>|
