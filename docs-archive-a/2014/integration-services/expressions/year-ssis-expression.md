---
title: YEAR（SSIS 表达式）| Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- dates [Integration Services], YEAR
- YEAR function
ms.assetid: 9d88dead-ace8-44b9-b8e2-916c1842e155
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 181375d489fbf7abf0718386efacf4167ba555d7
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87589198"
---
# <a name="year-ssis-expression"></a><span data-ttu-id="7b1bf-102">YEAR（SSIS 表达式）</span><span class="sxs-lookup"><span data-stu-id="7b1bf-102">YEAR (SSIS Expression)</span></span>
  <span data-ttu-id="7b1bf-103">返回一个表示日期中的“年份”日期部分的整数。</span><span class="sxs-lookup"><span data-stu-id="7b1bf-103">Returns an integer that represents the year datepart of a date.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7b1bf-104">语法</span><span class="sxs-lookup"><span data-stu-id="7b1bf-104">Syntax</span></span>  
  
```  
  
YEAR(date)  
```  
  
## <a name="arguments"></a><span data-ttu-id="7b1bf-105">参数</span><span class="sxs-lookup"><span data-stu-id="7b1bf-105">Arguments</span></span>  
 <span data-ttu-id="7b1bf-106">*date*</span><span class="sxs-lookup"><span data-stu-id="7b1bf-106">*date*</span></span>  
 <span data-ttu-id="7b1bf-107">是任意日期格式的日期。</span><span class="sxs-lookup"><span data-stu-id="7b1bf-107">Is a date in any date format.</span></span>  
  
## <a name="result-types"></a><span data-ttu-id="7b1bf-108">结果类型</span><span class="sxs-lookup"><span data-stu-id="7b1bf-108">Result Types</span></span>  
 <span data-ttu-id="7b1bf-109">DT_I4</span><span class="sxs-lookup"><span data-stu-id="7b1bf-109">DT_I4</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="7b1bf-110">备注</span><span class="sxs-lookup"><span data-stu-id="7b1bf-110">Remarks</span></span>  
 <span data-ttu-id="7b1bf-111">如果参数为空，则 YEAR 返回的结果为空。</span><span class="sxs-lookup"><span data-stu-id="7b1bf-111">YEAR returns a null result if the argument is null.</span></span>  
  
 <span data-ttu-id="7b1bf-112">日期文字必须显式转换为日期数据类型之一。</span><span class="sxs-lookup"><span data-stu-id="7b1bf-112">A date literal must be explicitly cast to one of the date data types.</span></span> <span data-ttu-id="7b1bf-113">有关详细信息，请参阅 [Integration Services 数据类型](../data-flow/integration-services-data-types.md)。</span><span class="sxs-lookup"><span data-stu-id="7b1bf-113">For more information, see [Integration Services Data Types](../data-flow/integration-services-data-types.md).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="7b1bf-114">在日期文本显式转换为以下日期数据类型之一时，表达式验证失败：DT_DBTIMESTAMPOFFSET 和 DT_DBTIMESTAMP2。</span><span class="sxs-lookup"><span data-stu-id="7b1bf-114">The expression fails to validate when a date literal is explicitly cast to one of these date data types: DT_DBTIMESTAMPOFFSET and DT_DBTIMESTAMP2.</span></span>  
  
 <span data-ttu-id="7b1bf-115">使用 YEAR 函数更为简要，但其等价于使用 DATEPART("Year", date) 函数。</span><span class="sxs-lookup"><span data-stu-id="7b1bf-115">Using the YEAR function is briefer but equivalent to using the DATEPART("Year", date) function.</span></span>  
  
## <a name="expression-examples"></a><span data-ttu-id="7b1bf-116">表达式示例</span><span class="sxs-lookup"><span data-stu-id="7b1bf-116">Expression Examples</span></span>  
 <span data-ttu-id="7b1bf-117">此示例返回日期文字中表示年份的数字。</span><span class="sxs-lookup"><span data-stu-id="7b1bf-117">This example returns the number of the year in a date literal.</span></span> <span data-ttu-id="7b1bf-118">如果日期格式为 mm/dd/yyyy，则此示例返回“2002”。</span><span class="sxs-lookup"><span data-stu-id="7b1bf-118">If the date is in mm/dd/yyyy format, this example returns "2002".</span></span>  
  
```  
YEAR((DT_DBTIMESTAMP)"11/23/2002")  
```  
  
 <span data-ttu-id="7b1bf-119">此示例返回 **ModifiedDate** 列中表示年份的整数。</span><span class="sxs-lookup"><span data-stu-id="7b1bf-119">This example returns the integer that represents the year in the **ModifiedDate** column.</span></span>  
  
```  
YEAR(ModifiedDate)  
```  
  
 <span data-ttu-id="7b1bf-120">此示例返回当前日期中表示年的整数。</span><span class="sxs-lookup"><span data-stu-id="7b1bf-120">This example returns the integer that represents the year of the current date.</span></span>  
  
```  
YEAR(GETDATE())  
```  
  
## <a name="see-also"></a><span data-ttu-id="7b1bf-121">另请参阅</span><span class="sxs-lookup"><span data-stu-id="7b1bf-121">See Also</span></span>  
 <span data-ttu-id="7b1bf-122">[DATEADD（SSIS 表达式）](dateadd-ssis-expression.md) </span><span class="sxs-lookup"><span data-stu-id="7b1bf-122">[DATEADD &#40;SSIS Expression&#41;](dateadd-ssis-expression.md) </span></span>  
 <span data-ttu-id="7b1bf-123">[DATEDIFF（SSIS 表达式）](datediff-ssis-expression.md) </span><span class="sxs-lookup"><span data-stu-id="7b1bf-123">[DATEDIFF &#40;SSIS Expression&#41;](datediff-ssis-expression.md) </span></span>  
 <span data-ttu-id="7b1bf-124">[DATEPART（SSIS 表达式）](datepart-ssis-expression.md) </span><span class="sxs-lookup"><span data-stu-id="7b1bf-124">[DATEPART &#40;SSIS Expression&#41;](datepart-ssis-expression.md) </span></span>  
 <span data-ttu-id="7b1bf-125">[DAY（SSIS 表达式）](day-ssis-expression.md) </span><span class="sxs-lookup"><span data-stu-id="7b1bf-125">[DAY &#40;SSIS Expression&#41;](day-ssis-expression.md) </span></span>  
 <span data-ttu-id="7b1bf-126">[MONTH（SSIS 表达式）](month-ssis-expression.md) </span><span class="sxs-lookup"><span data-stu-id="7b1bf-126">[MONTH &#40;SSIS Expression&#41;](month-ssis-expression.md) </span></span>  
 [<span data-ttu-id="7b1bf-127">函数（SSIS 表达式）</span><span class="sxs-lookup"><span data-stu-id="7b1bf-127">Functions &#40;SSIS Expression&#41;</span></span>](functions-ssis-expression.md)  
  
  
