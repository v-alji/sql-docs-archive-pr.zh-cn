---
title: GETDATE（SSIS 表达式）| Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- current date
- GETDATE function
- dates [Integration Services], GETDATE
ms.assetid: 6d20ec93-3244-4d63-baf6-70eff7bd598c
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 0acb384a8c3c3dfdae55c7172f341f9e32765e44
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87580796"
---
# <a name="getdate-ssis-expression"></a><span data-ttu-id="e62ef-102">GETDATE（SSIS 表达式）</span><span class="sxs-lookup"><span data-stu-id="e62ef-102">GETDATE (SSIS Expression)</span></span>
  <span data-ttu-id="e62ef-103">以 DT_DBTIMESTAMP 格式返回系统的当前日期。</span><span class="sxs-lookup"><span data-stu-id="e62ef-103">Returns the current date of the system in a DT_DBTIMESTAMP format.</span></span> <span data-ttu-id="e62ef-104">GETDATE 函数不使用参数。</span><span class="sxs-lookup"><span data-stu-id="e62ef-104">The GETDATE function takes no arguments.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="e62ef-105">GETDATE 函数的返回结果的长度为 29 个字符。</span><span class="sxs-lookup"><span data-stu-id="e62ef-105">The length of the return result from the GETDATE function is 29 characters.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e62ef-106">语法</span><span class="sxs-lookup"><span data-stu-id="e62ef-106">Syntax</span></span>  
  
```  
  
GETDATE()  
```  
  
## <a name="arguments"></a><span data-ttu-id="e62ef-107">参数</span><span class="sxs-lookup"><span data-stu-id="e62ef-107">Arguments</span></span>  
 <span data-ttu-id="e62ef-108">无</span><span class="sxs-lookup"><span data-stu-id="e62ef-108">None</span></span>  
  
## <a name="result-types"></a><span data-ttu-id="e62ef-109">结果类型</span><span class="sxs-lookup"><span data-stu-id="e62ef-109">Result Types</span></span>  
 <span data-ttu-id="e62ef-110">DT_DBTIMESTAMP</span><span class="sxs-lookup"><span data-stu-id="e62ef-110">DT_DBTIMESTAMP</span></span>  
  
## <a name="expression-examples"></a><span data-ttu-id="e62ef-111">表达式示例</span><span class="sxs-lookup"><span data-stu-id="e62ef-111">Expression Examples</span></span>  
 <span data-ttu-id="e62ef-112">此示例返回当前日期的年份。</span><span class="sxs-lookup"><span data-stu-id="e62ef-112">This example returns the year of the current date.</span></span>  
  
```  
DATEPART("year",GETDATE())  
```  
  
 <span data-ttu-id="e62ef-113">此示例返回 **ModifiedDate** 列中的日期和当前日期之间的天数。</span><span class="sxs-lookup"><span data-stu-id="e62ef-113">This example returns the number of days between a date in the **ModifiedDate** column and the current date.</span></span>  
  
```  
DATEDIFF("dd",ModifiedDate,GETDATE())  
```  
  
 <span data-ttu-id="e62ef-114">此示例将三个月加到当前日期。</span><span class="sxs-lookup"><span data-stu-id="e62ef-114">This example adds three months to the current date.</span></span>  
  
```  
DATEADD("Month",3,GETDATE())  
```  
  
## <a name="see-also"></a><span data-ttu-id="e62ef-115">另请参阅</span><span class="sxs-lookup"><span data-stu-id="e62ef-115">See Also</span></span>  
 <span data-ttu-id="e62ef-116">[GETUTCDATE（SSIS 表达式）](getutcdate-ssis-expression.md) </span><span class="sxs-lookup"><span data-stu-id="e62ef-116">[GETUTCDATE &#40;SSIS Expression&#41;](getutcdate-ssis-expression.md) </span></span>  
 [<span data-ttu-id="e62ef-117">函数（SSIS 表达式）</span><span class="sxs-lookup"><span data-stu-id="e62ef-117">Functions &#40;SSIS Expression&#41;</span></span>](functions-ssis-expression.md)  
  
  
