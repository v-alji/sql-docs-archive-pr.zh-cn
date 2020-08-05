---
title: MONTH（SSIS 表达式）| Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- dates [Integration Services], MONTH
- MONTH function
ms.assetid: b5a47a11-c2ef-49bd-bd70-235632ff7bf6
author: chugugrace
ms.author: chugu
ms.openlocfilehash: d1f56906b4d25f2ba01f54fbdbc404d2c9ae4704
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87581391"
---
# <a name="month-ssis-expression"></a><span data-ttu-id="d71e7-102">MONTH（SSIS 表达式）</span><span class="sxs-lookup"><span data-stu-id="d71e7-102">MONTH (SSIS Expression)</span></span>
  <span data-ttu-id="d71e7-103">返回一个表示日期中的“月份”日期部分的整数。</span><span class="sxs-lookup"><span data-stu-id="d71e7-103">Returns an integer that represents the month datepart of a date.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d71e7-104">语法</span><span class="sxs-lookup"><span data-stu-id="d71e7-104">Syntax</span></span>  
  
```  
  
MONTH(date)  
```  
  
## <a name="arguments"></a><span data-ttu-id="d71e7-105">参数</span><span class="sxs-lookup"><span data-stu-id="d71e7-105">Arguments</span></span>  
 <span data-ttu-id="d71e7-106">*date*</span><span class="sxs-lookup"><span data-stu-id="d71e7-106">*date*</span></span>  
 <span data-ttu-id="d71e7-107">是任意日期格式的日期。</span><span class="sxs-lookup"><span data-stu-id="d71e7-107">Is a date in any date format.</span></span>  
  
## <a name="result-types"></a><span data-ttu-id="d71e7-108">结果类型</span><span class="sxs-lookup"><span data-stu-id="d71e7-108">Result Types</span></span>  
 <span data-ttu-id="d71e7-109">DT_I4</span><span class="sxs-lookup"><span data-stu-id="d71e7-109">DT_I4</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d71e7-110">备注</span><span class="sxs-lookup"><span data-stu-id="d71e7-110">Remarks</span></span>  
 <span data-ttu-id="d71e7-111">如果参数为空，则 MONTH 返回的结果为空。</span><span class="sxs-lookup"><span data-stu-id="d71e7-111">MONTH returns a null result if the argument is null.</span></span>  
  
 <span data-ttu-id="d71e7-112">日期文字必须显式转换为日期数据类型之一。</span><span class="sxs-lookup"><span data-stu-id="d71e7-112">A date literal must be explicitly cast to one of the date data types.</span></span> <span data-ttu-id="d71e7-113">有关详细信息，请参阅 [Integration Services 数据类型](../data-flow/integration-services-data-types.md)。</span><span class="sxs-lookup"><span data-stu-id="d71e7-113">For more information, see [Integration Services Data Types](../data-flow/integration-services-data-types.md).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="d71e7-114">在日期文本显式转换为以下日期数据类型之一时，表达式验证失败：DT_DBTIMESTAMPOFFSET 和 DT_DBTIMESTAMP2。</span><span class="sxs-lookup"><span data-stu-id="d71e7-114">The expression fails to validate when a date literal is explicitly cast to one of these date data types: DT_DBTIMESTAMPOFFSET and DT_DBTIMESTAMP2.</span></span>  
  
 <span data-ttu-id="d71e7-115">使用 MONTH 函数更为简要，但等价于使用 DATEPART("Month", date)。</span><span class="sxs-lookup"><span data-stu-id="d71e7-115">Using the MONTH function is briefer but equivalent to using DATEPART("Month", date).</span></span>  
  
## <a name="expression-examples"></a><span data-ttu-id="d71e7-116">表达式示例</span><span class="sxs-lookup"><span data-stu-id="d71e7-116">Expression Examples</span></span>  
 <span data-ttu-id="d71e7-117">此示例返回日期文字中表示月份的数字。</span><span class="sxs-lookup"><span data-stu-id="d71e7-117">This example returns the number of the month in a date literal.</span></span> <span data-ttu-id="d71e7-118">如果日期是“mm/dd/yyyy”格式，则此示例返回 11。</span><span class="sxs-lookup"><span data-stu-id="d71e7-118">If the date is in "mm/dd/yyyy" format, this example returns 11.</span></span>  
  
```  
MONTH((DT_DBTIMESTAMP)"11/23/2002")  
```  
  
 <span data-ttu-id="d71e7-119">此示例返回 **ModifiedDate** 列中表示月份的整数。</span><span class="sxs-lookup"><span data-stu-id="d71e7-119">This example returns the integer that represents the month in the **ModifiedDate** column.</span></span>  
  
```  
MONTH(ModifiedDate)  
```  
  
 <span data-ttu-id="d71e7-120">此示例返回表示当前日期中的月份的整数。</span><span class="sxs-lookup"><span data-stu-id="d71e7-120">This example returns the integer that represents the month of the current date.</span></span>  
  
```  
MONTH(GETDATE())  
```  
  
## <a name="see-also"></a><span data-ttu-id="d71e7-121">另请参阅</span><span class="sxs-lookup"><span data-stu-id="d71e7-121">See Also</span></span>  
 <span data-ttu-id="d71e7-122">[DATEADD（SSIS 表达式）](dateadd-ssis-expression.md) </span><span class="sxs-lookup"><span data-stu-id="d71e7-122">[DATEADD &#40;SSIS Expression&#41;](dateadd-ssis-expression.md) </span></span>  
 <span data-ttu-id="d71e7-123">[DATEDIFF（SSIS 表达式）](datediff-ssis-expression.md) </span><span class="sxs-lookup"><span data-stu-id="d71e7-123">[DATEDIFF &#40;SSIS Expression&#41;](datediff-ssis-expression.md) </span></span>  
 <span data-ttu-id="d71e7-124">[DATEPART（SSIS 表达式）](datepart-ssis-expression.md) </span><span class="sxs-lookup"><span data-stu-id="d71e7-124">[DATEPART &#40;SSIS Expression&#41;](datepart-ssis-expression.md) </span></span>  
 <span data-ttu-id="d71e7-125">[DAY（SSIS 表达式）](day-ssis-expression.md) </span><span class="sxs-lookup"><span data-stu-id="d71e7-125">[DAY &#40;SSIS Expression&#41;](day-ssis-expression.md) </span></span>  
 <span data-ttu-id="d71e7-126">[YEAR（SSIS 表达式）](year-ssis-expression.md) </span><span class="sxs-lookup"><span data-stu-id="d71e7-126">[YEAR &#40;SSIS Expression&#41;](year-ssis-expression.md) </span></span>  
 [<span data-ttu-id="d71e7-127">函数（SSIS 表达式）</span><span class="sxs-lookup"><span data-stu-id="d71e7-127">Functions &#40;SSIS Expression&#41;</span></span>](functions-ssis-expression.md)  
  
  
