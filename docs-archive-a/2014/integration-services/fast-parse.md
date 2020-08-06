---
title: 快速分析 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- fast parse [Integration Services]
ms.assetid: 6688707d-3c5b-404e-aa2f-e13092ac8d95
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 343b8b8b74338512dbf29b3d2efd436df1ffa8ae
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87691312"
---
# <a name="fast-parse"></a><span data-ttu-id="bae79-102">Fast Parse</span><span class="sxs-lookup"><span data-stu-id="bae79-102">Fast Parse</span></span>
  <span data-ttu-id="bae79-103">快速分析提供一组快速、简单的数据分析例程。</span><span class="sxs-lookup"><span data-stu-id="bae79-103">Fast parse provides a fast, simple set of routines for parsing data.</span></span> <span data-ttu-id="bae79-104">这些例程是不区分区域设置的，并且它们只支持日期、时间和整数格式的一个子集。</span><span class="sxs-lookup"><span data-stu-id="bae79-104">These routines are not locale-sensitive and they support only a subset of date, time, and integer formats.</span></span>  
  
## <a name="requirements-and-limitations"></a><span data-ttu-id="bae79-105">要求和限制</span><span class="sxs-lookup"><span data-stu-id="bae79-105">Requirements and Limitations</span></span>  
 <span data-ttu-id="bae79-106">通过实现快速分析，包失去了以特定于区域设置的格式和很多常用的 ISO 8601 基本及扩展格式来转换日期、时间和数值数据的能力，但包的性能得到了提高。</span><span class="sxs-lookup"><span data-stu-id="bae79-106">By implementing fast parse, a package forfeits its ability to interpret date, time, and numeric data in locale-specific formats and many frequently used ISO 8601 basic and extended formats, but the package enhances its performance.</span></span> <span data-ttu-id="bae79-107">例如，快速分析仅支持最常用的日期格式表示形式（比如，YYYYMMDD 和 YYYY-MM-DD），不执行区域设置特定的分析，不能识别货币数据中的特殊字符，也不能转换对整数的十六进制或科学表示形式。</span><span class="sxs-lookup"><span data-stu-id="bae79-107">For example, fast parse supports only the most commonly used date format representations such as YYYYMMDD and YYYY-MM-DD, does not perform locale-specific parsing, does not recognize special characters in currency data, and cannot convert hexadecimal or scientific representation of integers.</span></span>  
  
 <span data-ttu-id="bae79-108">快速分析仅在使用平面文件源或数据转换时才可用。</span><span class="sxs-lookup"><span data-stu-id="bae79-108">Fast parse is available only when you use the Flat File source or the Data Conversion transformation.</span></span> <span data-ttu-id="bae79-109">包的性能可能会得到显著提高，您应尽可能考虑在这些数据流组件中使用快速分析。</span><span class="sxs-lookup"><span data-stu-id="bae79-109">The increase in performance can be significant, and you should consider using fast parse in these data flow components if you can.</span></span>  
  
 <span data-ttu-id="bae79-110">如果包中的数据流需要受区域设置影响的分析，则应使用标准分析，而不是快速分析。</span><span class="sxs-lookup"><span data-stu-id="bae79-110">If the data flow in the package requires locale-sensitive parsing, standard parse is recommended instead of fast parse.</span></span> <span data-ttu-id="bae79-111">例如，快速分析不能识别受区域设置影响的数据，包括小数符号（如逗号）、与“年-月-日”格式不同的日期格式以及货币符号。</span><span class="sxs-lookup"><span data-stu-id="bae79-111">For example, fast parse does not recognize locale-sensitive data that includes decimal symbols such as the comma, date formats other than year-month-date formats, and currency symbols.</span></span>  
  
 <span data-ttu-id="bae79-112">快速分析不能识别隐含一个或多个日期部分（如世纪、年、月）的截断的表示形式。</span><span class="sxs-lookup"><span data-stu-id="bae79-112">Truncated representations that imply one or more date parts, such as a century, a year, or a month, are not recognized by fast parse.</span></span> <span data-ttu-id="bae79-113">例如，快速分析既不能识别“**-YYMM**”格式（指定某个隐含世纪中的年和月），也不能识别“**--MM**”格式（指定某个隐含年中的月）。</span><span class="sxs-lookup"><span data-stu-id="bae79-113">For example, fast parse recognizes neither the '**-YYMM**' format, which specifies a year and month in an implied century, nor '**--MM**', which specifies a month in an implied year.</span></span> <span data-ttu-id="bae79-114">但是，某些降低了精度的表示形式可以被识别。</span><span class="sxs-lookup"><span data-stu-id="bae79-114">However, some representations with reduced precision are recognized.</span></span> <span data-ttu-id="bae79-115">例如，快速分析可以识别“hhmm;”格式（仅指示时和分）和“**YYYY**”格式（仅指示年）。</span><span class="sxs-lookup"><span data-stu-id="bae79-115">For example, fast parse recognizes the 'hhmm;' format, which indicates hour and minute only, and '**YYYY**', which indicates year only.</span></span>  
  
 <span data-ttu-id="bae79-116">快速分析在列级指定。</span><span class="sxs-lookup"><span data-stu-id="bae79-116">Fast parse is specified at the column level.</span></span> <span data-ttu-id="bae79-117">在平面文件源和数据转换中，可以指定对输出列进行快速分析。</span><span class="sxs-lookup"><span data-stu-id="bae79-117">In the Flat File source and the Data Conversion transformation, you can specify Fast parse on output columns.</span></span> <span data-ttu-id="bae79-118">输入和输出可以同时包含受区域设置影响的列和不受区域设置影响的列。</span><span class="sxs-lookup"><span data-stu-id="bae79-118">Inputs and outputs can include both locale-sensitive and locale-insensitive columns.</span></span>  
  
 <span data-ttu-id="bae79-119">有关快速分析支持的数据格式的详细信息，请参阅 [Numeric Data Formats](../../2014/integration-services/numeric-data-formats.md) 和 [Date and Time Formats](../../2014/integration-services/date-and-time-formats.md).</span><span class="sxs-lookup"><span data-stu-id="bae79-119">For more information about the data formats that Fast parse supports, see [Numeric Data Formats](../../2014/integration-services/numeric-data-formats.md) and [Date and Time Formats](../../2014/integration-services/date-and-time-formats.md).</span></span>  
  
## <a name="related-tasks"></a><span data-ttu-id="bae79-120">Related Tasks</span><span class="sxs-lookup"><span data-stu-id="bae79-120">Related Tasks</span></span>  
 [<span data-ttu-id="bae79-121">设置快速分析</span><span class="sxs-lookup"><span data-stu-id="bae79-121">Set Fast Parse</span></span>](../../2014/integration-services/set-fast-parse.md)  
  
  
