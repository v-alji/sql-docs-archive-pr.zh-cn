---
title: REVERSE（SSIS 表达式）| Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- REVERSE function
- reverse character expressions
ms.assetid: bcebcc55-7247-4896-8f53-4d582d58cfb4
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 2ace136eed0abcb9df7b25d9370c46d7556c1d48
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87689981"
---
# <a name="reverse-ssis-expression"></a><span data-ttu-id="a47fd-102">REVERSE（SSIS 表达式）</span><span class="sxs-lookup"><span data-stu-id="a47fd-102">REVERSE (SSIS Expression)</span></span>
  <span data-ttu-id="a47fd-103">按相反顺序返回字符表达式。</span><span class="sxs-lookup"><span data-stu-id="a47fd-103">Returns a character expression in reverse order.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a47fd-104">语法</span><span class="sxs-lookup"><span data-stu-id="a47fd-104">Syntax</span></span>  
  
```  
  
REVERSE(character_expression)  
```  
  
## <a name="arguments"></a><span data-ttu-id="a47fd-105">参数</span><span class="sxs-lookup"><span data-stu-id="a47fd-105">Arguments</span></span>  
 <span data-ttu-id="a47fd-106">*character_expression*</span><span class="sxs-lookup"><span data-stu-id="a47fd-106">*character_expression*</span></span>  
 <span data-ttu-id="a47fd-107">是要反转的字符表达式。</span><span class="sxs-lookup"><span data-stu-id="a47fd-107">Is a character expression to be reversed.</span></span>  
  
## <a name="result-types"></a><span data-ttu-id="a47fd-108">结果类型</span><span class="sxs-lookup"><span data-stu-id="a47fd-108">Result Types</span></span>  
 <span data-ttu-id="a47fd-109">DT_WSTR</span><span class="sxs-lookup"><span data-stu-id="a47fd-109">DT_WSTR</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a47fd-110">备注</span><span class="sxs-lookup"><span data-stu-id="a47fd-110">Remarks</span></span>  
 <span data-ttu-id="a47fd-111">character_expression 参数必须具有 DT_WSTR 数据类型  。</span><span class="sxs-lookup"><span data-stu-id="a47fd-111">The *character_expression* argument must have the DT_WSTR data type.</span></span>  
  
 <span data-ttu-id="a47fd-112">如果 character_expression 为 Null，则 REVERSE 将返回 Null 结果  。</span><span class="sxs-lookup"><span data-stu-id="a47fd-112">REVERSE returns a null result if *character_expression* is null.</span></span>  
  
## <a name="expression-examples"></a><span data-ttu-id="a47fd-113">表达式示例</span><span class="sxs-lookup"><span data-stu-id="a47fd-113">Expression Examples</span></span>  
 <span data-ttu-id="a47fd-114">此示例使用一个字符串文字。</span><span class="sxs-lookup"><span data-stu-id="a47fd-114">This example uses a string literal.</span></span> <span data-ttu-id="a47fd-115">返回结果为“ekiB niatnuoM”。</span><span class="sxs-lookup"><span data-stu-id="a47fd-115">The return result is "ekiB niatnuoM".</span></span>  
  
```  
REVERSE("Mountain Bike")  
```  
  
 <span data-ttu-id="a47fd-116">此示例使用一个变量。</span><span class="sxs-lookup"><span data-stu-id="a47fd-116">This example uses a variable.</span></span> <span data-ttu-id="a47fd-117">如果 **Name** 包含 Touring Bike，则返回的结果为“ekiB gniruoT”。</span><span class="sxs-lookup"><span data-stu-id="a47fd-117">If **Name** contains Touring Bike, the return result is "ekiB gniruoT".</span></span>  
  
```  
REVERSE(@Name)  
```  
  
## <a name="see-also"></a><span data-ttu-id="a47fd-118">另请参阅</span><span class="sxs-lookup"><span data-stu-id="a47fd-118">See Also</span></span>  
 [<span data-ttu-id="a47fd-119">函数（SSIS 表达式）</span><span class="sxs-lookup"><span data-stu-id="a47fd-119">Functions &#40;SSIS Expression&#41;</span></span>](functions-ssis-expression.md)  
  
  
