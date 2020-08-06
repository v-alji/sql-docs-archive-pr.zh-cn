---
title: ISNULL（SSIS 表达式）| Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- null values [Integration Services]
- ISNULL function
ms.assetid: 88dbf49e-1307-4dda-b9db-ff1632053550
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 51eda21b5c9b85c5f9cfd613d0d92df9729fe620
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87689988"
---
# <a name="isnull-ssis-expression"></a><span data-ttu-id="35908-102">ISNULL（SSIS 表达式）</span><span class="sxs-lookup"><span data-stu-id="35908-102">ISNULL (SSIS Expression)</span></span>
  <span data-ttu-id="35908-103">根据表达式是否为空，返回一个布尔值结果。</span><span class="sxs-lookup"><span data-stu-id="35908-103">Returns a Boolean result based on whether an expression is null.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="35908-104">语法</span><span class="sxs-lookup"><span data-stu-id="35908-104">Syntax</span></span>  
  
```  
  
ISNULL(expression)  
```  
  
## <a name="arguments"></a><span data-ttu-id="35908-105">参数</span><span class="sxs-lookup"><span data-stu-id="35908-105">Arguments</span></span>  
 <span data-ttu-id="35908-106">*expression*</span><span class="sxs-lookup"><span data-stu-id="35908-106">*expression*</span></span>  
 <span data-ttu-id="35908-107">是任何数据类型的有效表达式。</span><span class="sxs-lookup"><span data-stu-id="35908-107">Is a valid expression of any data type.</span></span>  
  
## <a name="result-types"></a><span data-ttu-id="35908-108">结果类型</span><span class="sxs-lookup"><span data-stu-id="35908-108">Result Types</span></span>  
 <span data-ttu-id="35908-109">DT_BOOL</span><span class="sxs-lookup"><span data-stu-id="35908-109">DT_BOOL</span></span>  
  
## <a name="expression-examples"></a><span data-ttu-id="35908-110">表达式示例</span><span class="sxs-lookup"><span data-stu-id="35908-110">Expression Examples</span></span>  
 <span data-ttu-id="35908-111">如果 **DiscontinuedDate** 列包含 Null 值，此示例将返回 TRUE。</span><span class="sxs-lookup"><span data-stu-id="35908-111">This example returns TRUE if the **DiscontinuedDate** column contains a null value.</span></span>  
  
```  
ISNULL(DiscontinuedDate)  
```  
  
 <span data-ttu-id="35908-112">如果 **LastName** 列中的值为空，则此示例返回“Unknown last name”，否则返回 **LastName**中的值。</span><span class="sxs-lookup"><span data-stu-id="35908-112">This example returns "Unknown last name" if the value in the **LastName** column is null, otherwise it returns the value in **LastName**.</span></span>  
  
```  
ISNULL(LastName)? "Unknown last name":LastName  
```  
  
 <span data-ttu-id="35908-113">如果 **DaysToManufacture** 列为空，则不管变量 **AddDays**的值如何，此示例都始终返回 TRUE。</span><span class="sxs-lookup"><span data-stu-id="35908-113">This example always returns TRUE if the **DaysToManufacture** column is null, regardless of the value of the variable **AddDays**.</span></span>  
  
```  
ISNULL(DaysToManufacture + @AddDays)  
```  
  
## <a name="see-also"></a><span data-ttu-id="35908-114">另请参阅</span><span class="sxs-lookup"><span data-stu-id="35908-114">See Also</span></span>  
 <span data-ttu-id="35908-115">[函数（SSIS 表达式）](functions-ssis-expression.md) </span><span class="sxs-lookup"><span data-stu-id="35908-115">[Functions &#40;SSIS Expression&#41;](functions-ssis-expression.md) </span></span>  
 [<span data-ttu-id="35908-116">COALESCE (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="35908-116">COALESCE &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/language-elements/coalesce-transact-sql)  
  
  
