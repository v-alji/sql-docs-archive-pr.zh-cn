---
title: REPLACENULL（SSIS 表达式）| Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: 70db7832-b5a0-4db5-a8ad-42ad8630d8e8
author: chugugrace
ms.author: chugu
ms.openlocfilehash: f10bb6ef6102076fe7b1cc236461e2358ad96372
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87689984"
---
# <a name="replacenull-ssis-expression"></a><span data-ttu-id="9b57c-102">REPLACENULL（SSIS 表达式）</span><span class="sxs-lookup"><span data-stu-id="9b57c-102">REPLACENULL (SSIS Expression)</span></span>
  <span data-ttu-id="9b57c-103">如果第一个表达式参数的值为 NULL，则返回第二个表达式参数的值；否则，返回第一个表达式的值。</span><span class="sxs-lookup"><span data-stu-id="9b57c-103">Returns the value of second expression parameter if the value of first expression parameter is NULL; otherwise, returns the value of first expression.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9b57c-104">语法</span><span class="sxs-lookup"><span data-stu-id="9b57c-104">Syntax</span></span>  
  
```vb  
REPLACENULL(expression 1,expression 2)  
```  
  
## <a name="arguments"></a><span data-ttu-id="9b57c-105">参数</span><span class="sxs-lookup"><span data-stu-id="9b57c-105">Arguments</span></span>  
 <span data-ttu-id="9b57c-106">*表达式 1*</span><span class="sxs-lookup"><span data-stu-id="9b57c-106">*expression 1*</span></span>  
 <span data-ttu-id="9b57c-107">检查此表达式的结果是否为 NULL。</span><span class="sxs-lookup"><span data-stu-id="9b57c-107">The result of this expression is checked against NULL.</span></span>  
  
 <span data-ttu-id="9b57c-108">*表达式 2*</span><span class="sxs-lookup"><span data-stu-id="9b57c-108">*expression 2*</span></span>  
 <span data-ttu-id="9b57c-109">如果第一个表达式的计算结果为 NULL，则返回此表达式的结果。</span><span class="sxs-lookup"><span data-stu-id="9b57c-109">The result of this expression is returned if the first expression evaluates to NULL.</span></span>  
  
## <a name="result-types"></a><span data-ttu-id="9b57c-110">结果类型</span><span class="sxs-lookup"><span data-stu-id="9b57c-110">Result Types</span></span>  
 <span data-ttu-id="9b57c-111">DT_WSTR</span><span class="sxs-lookup"><span data-stu-id="9b57c-111">DT_WSTR</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="9b57c-112">备注</span><span class="sxs-lookup"><span data-stu-id="9b57c-112">Remarks</span></span>  
  
-   <span data-ttu-id="9b57c-113">*expression 2* 的长度可以为零。</span><span class="sxs-lookup"><span data-stu-id="9b57c-113">The length of *expression 2* may be zero.</span></span>  
  
-   <span data-ttu-id="9b57c-114">如果任何参数为 Null，则 REPLACENULL 的返回结果为 Null。</span><span class="sxs-lookup"><span data-stu-id="9b57c-114">REPLACENULL returns a null result if any argument is null.</span></span>  
  
-   <span data-ttu-id="9b57c-115">任一参数都不支持 BLOB 列（DT_TEXT、DT_NTEXT、DT_IMAGE）。</span><span class="sxs-lookup"><span data-stu-id="9b57c-115">BLOB columns (DT_TEXT, DT_NTEXT, DT_IMAGE) are not supported for either parameter.</span></span>  
  
-   <span data-ttu-id="9b57c-116">两个表达式的返回类型应相同。</span><span class="sxs-lookup"><span data-stu-id="9b57c-116">The two expressions are expected to have the same return type.</span></span> <span data-ttu-id="9b57c-117">如果不相同，则函数尝试将第二个表达式的返回类型转换为第一个表达式的返回类型，如果数据类型不兼容，这可能会导致出现错误。</span><span class="sxs-lookup"><span data-stu-id="9b57c-117">If they do not, the function attempts to cast the 2nd expression to the return type of the 1st expression, which may result in an error if the data types are incompatible.</span></span>  
  
## <a name="expression-examples"></a><span data-ttu-id="9b57c-118">表达式示例</span><span class="sxs-lookup"><span data-stu-id="9b57c-118">Expression Examples</span></span>  
 <span data-ttu-id="9b57c-119">下面的示例将数据库列中的任何 NULL 值替换为字符串 (1900-01-01)。</span><span class="sxs-lookup"><span data-stu-id="9b57c-119">The following example replaces any NULL value in a database column with a string (1900-01-01).</span></span> <span data-ttu-id="9b57c-120">此函数专用在常见的“派生列”模式中，在该模式中，您可以将 NULL 值替换为其他值。</span><span class="sxs-lookup"><span data-stu-id="9b57c-120">This function is especially used in common Derived Column patterns where you want to replace NULL values with something else.</span></span>  
  
```  
REPLACENULL(MyColumn, "1900-01-01")  
```  
  
> [!NOTE]  
>  <span data-ttu-id="9b57c-121">下面的示例演示此函数在 [!INCLUDE[ssISversion2005](../../includes/ssisversion2005-md.md)]/[!INCLUDE[ssISversion10](../../includes/ssisversion10-md.md)]中的实现方式。</span><span class="sxs-lookup"><span data-stu-id="9b57c-121">The following example shows how it was done in [!INCLUDE[ssISversion2005](../../includes/ssisversion2005-md.md)]/[!INCLUDE[ssISversion10](../../includes/ssisversion10-md.md)].</span></span>  
  
```  
(DT_DBTIMESTAMP) (ISNULL(MyColumn) ? "1900-01-01" : MyColumn)   
```  
  
  
