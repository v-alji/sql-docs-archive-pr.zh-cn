---
title: GETUTCDATE（SSIS 表达式）| Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- dates [Integration Services], GETUTCDATE
- current date
- UTC time
- GETUTCDATE function
ms.assetid: 2282339c-c24f-493e-8e66-181ea8af5ad0
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 4f157ab5641e521a42cb3c96c96446b31de5dfa5
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87690000"
---
# <a name="getutcdate-ssis-expression"></a><span data-ttu-id="38bff-102">GETUTCDATE（SSIS 表达式）</span><span class="sxs-lookup"><span data-stu-id="38bff-102">GETUTCDATE (SSIS Expression)</span></span>
  <span data-ttu-id="38bff-103">使用 DT_DBTIMESTAMP 格式返回以 UTC 时间（协调世界时或格林尼治标准时间）表示的系统当前日期。</span><span class="sxs-lookup"><span data-stu-id="38bff-103">Returns the current date of the system in UTC time (Universal Time Coordinate or Greenwich Mean Time) using a DT_DBTIMESTAMP format.</span></span> <span data-ttu-id="38bff-104">GETUTCDATE 函数不带参数。</span><span class="sxs-lookup"><span data-stu-id="38bff-104">The GETUTCDATE function takes no arguments.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="38bff-105">语法</span><span class="sxs-lookup"><span data-stu-id="38bff-105">Syntax</span></span>  
  
```  
  
GETUTCDATE()  
```  
  
## <a name="arguments"></a><span data-ttu-id="38bff-106">参数</span><span class="sxs-lookup"><span data-stu-id="38bff-106">Arguments</span></span>  
 <span data-ttu-id="38bff-107">无</span><span class="sxs-lookup"><span data-stu-id="38bff-107">None</span></span>  
  
## <a name="result-types"></a><span data-ttu-id="38bff-108">结果类型</span><span class="sxs-lookup"><span data-stu-id="38bff-108">Result Types</span></span>  
 <span data-ttu-id="38bff-109">DT_DBTIMESTAMP</span><span class="sxs-lookup"><span data-stu-id="38bff-109">DT_DBTIMESTAMP</span></span>  
  
## <a name="expression-examples"></a><span data-ttu-id="38bff-110">表达式示例</span><span class="sxs-lookup"><span data-stu-id="38bff-110">Expression Examples</span></span>  
 <span data-ttu-id="38bff-111">此示例返回以 UTC 时间表示的当前日期的年份。</span><span class="sxs-lookup"><span data-stu-id="38bff-111">This example returns the year of the current date in UTC time.</span></span>  
  
```  
DATEPART("year",GETUTCDATE())  
```  
  
 <span data-ttu-id="38bff-112">此示例返回 **ModifiedDate** 列中的日期和当前 UTC 日期之间的天数。</span><span class="sxs-lookup"><span data-stu-id="38bff-112">This example returns the number of days between a date in the **ModifiedDate** column and the current UTC date.</span></span>  
  
```  
DATEDIFF("dd",ModifiedDate,GETUTCDATE())  
```  
  
 <span data-ttu-id="38bff-113">此示例将三个月加到当前 UTC 日期。</span><span class="sxs-lookup"><span data-stu-id="38bff-113">This example adds three months to the current UTC date.</span></span>  
  
```  
DATEADD("Month",3,GETUTCDATE())  
```  
  
## <a name="see-also"></a><span data-ttu-id="38bff-114">另请参阅</span><span class="sxs-lookup"><span data-stu-id="38bff-114">See Also</span></span>  
 <span data-ttu-id="38bff-115">[GETDATE（SSIS 表达式）](getdate-ssis-expression.md) </span><span class="sxs-lookup"><span data-stu-id="38bff-115">[GETDATE &#40;SSIS Expression&#41;](getdate-ssis-expression.md) </span></span>  
 [<span data-ttu-id="38bff-116">函数（SSIS 表达式）</span><span class="sxs-lookup"><span data-stu-id="38bff-116">Functions &#40;SSIS Expression&#41;</span></span>](functions-ssis-expression.md)  
  
  
