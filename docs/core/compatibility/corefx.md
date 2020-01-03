---
title: 기본 클래스 라이브러리 주요 변경 내용 - .NET Core
description: 기본 클래스 라이브러리인 .NET CoreFx 관련 호환성이 손상되는 변경 목록입니다.
ms.date: 09/20/2019
ms.openlocfilehash: 9462e8f8a54a12c19744f7cce55b2a8998ae9f94
ms.sourcegitcommit: 79a2d6a07ba4ed08979819666a0ee6927bbf1b01
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/28/2019
ms.locfileid: "74568227"
---
# <a name="corefx-breaking-changes"></a><span data-ttu-id="13089-103">CoreFx 관련 호환성이 손상되는 변경</span><span class="sxs-lookup"><span data-stu-id="13089-103">CoreFx breaking changes</span></span>

<span data-ttu-id="13089-104">다음은 .NET Core 버전별 CoreFx 관련 호환성이 손상되는 변경 목록입니다.</span><span class="sxs-lookup"><span data-stu-id="13089-104">The following is a list of CoreFx breaking changes by .NET Core version.</span></span> <span data-ttu-id="13089-105">CoreFx는 .NET Core에서 사용되는 기본 형식과 기타 일반적인 형식을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="13089-105">CoreFx provides the primitives and other general types used by .NET Core.</span></span>

## <a name="net-core-30"></a><span data-ttu-id="13089-106">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="13089-106">.NET Core 3.0</span></span>

[!INCLUDE[APIs that report version now report product and not file version](~/includes/core-changes/corefx/3.0/version-information-changes.md)]

***

[!INCLUDE[Custom EncoderFallbackBuffer instances cannot fall back recursively](~/includes/core-changes/corefx/3.0/custom-encoderfallbackbuffer-cannot-be-recursive.md)]

***

[!INCLUDE[Floating point formatting and parsing behavior changes](~/includes/core-changes/corefx/3.0/floating-point-changes.md)]

***

[!INCLUDE[Floating-point parsing operations no longer fail or throw an OverflowException](~/includes/core-changes/corefx/3.0/floating-point-parsing-does-not-overflow.md)]

***

[!INCLUDE[InvalidAsynchronousStateException moved to another assembly](~/includes/core-changes/corefx/3.0/move-invalidasynchronousstateexception.md)]

***

[!INCLUDE[NET Core 3.0 follows Unicode best practices when replacing ill-formed UTF-8 byte sequences](~/includes/core-changes/corefx/3.0/net-core-3-0-follows-unicode-utf8-best-practices.md)]

***

[!INCLUDE[TypeDescriptionProviderAttribute moved to another assembly](~/includes/core-changes/corefx/3.0/move-typedescriptionproviderattribute.md)]

***

[!INCLUDE[ZipArchiveEntry no longer handles archives with inconsistent entry sizes](~/includes/core-changes/corefx/3.0/ziparchiveentry-and-inconsistent-entry-sizes.md)]

## <a name="net-core-30-preview-9"></a><span data-ttu-id="13089-107">.NET Core 3.0 미리 보기 9</span><span class="sxs-lookup"><span data-stu-id="13089-107">.NET Core 3.0 Preview 9</span></span>

[!INCLUDE[Json serializer exception type changed from JsonException to NotSupportedException](~/includes/core-changes/corefx/3.0/serializer-throws-notsupportedexception.md)]

## <a name="net-core-30-preview-8"></a><span data-ttu-id="13089-108">.NET Core 3.0 미리 보기 8</span><span class="sxs-lookup"><span data-stu-id="13089-108">.NET Core 3.0 Preview 8</span></span>

[!INCLUDE[Change in semantics of (string)null in Utf8JsonWriter](~/includes/core-changes/corefx/3.0/change-in-null-in-utf8jsonwriter.md)]

***

[!INCLUDE[JsonEncodedText.Encode methods have an additional JavaScriptEncoder argument](~/includes/core-changes/corefx/3.0/jsonencodedtext-encode-has-additional-argument.md)]

***

[!INCLUDE[JsonFactoryConverter.CreateConverter signature changed](~/includes/core-changes/corefx/3.0/jsonfactoryconverter-createconverter.md)]

## <a name="net-core-30-preview-7"></a><span data-ttu-id="13089-109">.NET Core 3.0 미리 보기 7</span><span class="sxs-lookup"><span data-stu-id="13089-109">.NET Core 3.0 Preview 7</span></span>

[!INCLUDE[JsonElement API changes](~/includes/core-changes/corefx/3.0/jsonelement-api-changes.md)]