---
title: 字符串填充 (SSIS) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- padding strings [Integration Services]
- expressions [Integration Services], string padding
- string padding
ms.assetid: d3fed73d-e0d4-4c67-9355-fb7083a72dd6
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 3985fd1b2f29260e2313a761797d2528f5d0e328
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87689966"
---
# <a name="string-padding-ssis"></a><span data-ttu-id="db1ec-102">字符串填充 (SSIS)</span><span class="sxs-lookup"><span data-stu-id="db1ec-102">String Padding (SSIS)</span></span>
  <span data-ttu-id="db1ec-103">表达式计算器不检查字符串是否包含前导空格和尾随空格，并且比较前不填充字符串来使其具有相同长度。</span><span class="sxs-lookup"><span data-stu-id="db1ec-103">The expression evaluator does not check if a string contains leading and trailing spaces, and it does not pad strings to make them the same length before it compares them.</span></span> <span data-ttu-id="db1ec-104">如果表达式需要字符串填充，可使用 + 运算符连接列值和空字符串。</span><span class="sxs-lookup"><span data-stu-id="db1ec-104">If expressions requires string padding, you can use the + operator to concatenate column values and blank strings.</span></span> <span data-ttu-id="db1ec-105">有关详细信息，请参阅 [+（连接）（SSIS 表达式）](concatenate-ssis-expression.md)。</span><span class="sxs-lookup"><span data-stu-id="db1ec-105">For more information, see [+ &#40;Concatenate&#41; &#40;SSIS Expression&#41;](concatenate-ssis-expression.md).</span></span>  
  
 <span data-ttu-id="db1ec-106">另一方面，如果要删除空格，表达式计算器提供了 LTRIM、RTRIM 和 TRIM 函数，用于删除前导空格和/或尾随空格。</span><span class="sxs-lookup"><span data-stu-id="db1ec-106">On the other hand, if you want to remove spaces, the expression evaluator provides the LTRIM, RTRIM, and TRIM functions, which remove leading or trailing spaces, or both.</span></span> <span data-ttu-id="db1ec-107">有关详细信息，请参阅 [LTRIM（SSIS 表达式）](trim-ssis-expression.md)、[RTRIM（SSIS 表达式）](rtrim-ssis-expression.md)和 [TRIM（SSIS 表达式）](trim-ssis-expression.md)。</span><span class="sxs-lookup"><span data-stu-id="db1ec-107">For more information, see [LTRIM &#40;SSIS Expression&#41;](trim-ssis-expression.md), [RTRIM &#40;SSIS Expression&#41;](rtrim-ssis-expression.md), and [TRIM &#40;SSIS Expression&#41;](trim-ssis-expression.md).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="db1ec-108">LEN 函数将前导空格和尾随空格包含在其计数中。</span><span class="sxs-lookup"><span data-stu-id="db1ec-108">The LEN function includes leading and trailing blanks in its count.</span></span>  
  
## <a name="related-content"></a><span data-ttu-id="db1ec-109">相关内容</span><span class="sxs-lookup"><span data-stu-id="db1ec-109">Related Content</span></span>  
 <span data-ttu-id="db1ec-110">pragmaticworks.com 上的技术文章 [SSIS 表达式小抄表](https://pragmaticworks.com/Resources/Cheat-Sheets/SSIS-Expression-Cheat-Sheet
)。</span><span class="sxs-lookup"><span data-stu-id="db1ec-110">Technical article, [SSIS Expression Cheat Sheet](https://pragmaticworks.com/Resources/Cheat-Sheets/SSIS-Expression-Cheat-Sheet
), on pragmaticworks.com</span></span>  
  
  
