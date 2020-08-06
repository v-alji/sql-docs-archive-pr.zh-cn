---
title: 数据截断 (SSIS) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- truncating data
- data truncation [Integration Services]
- expressions [Integration Services], data truncation
- truncate options [Integration Services]
ms.assetid: 02461e15-49ca-445b-abb3-5c369c283ec2
author: chugugrace
ms.author: chugu
ms.openlocfilehash: e0c4280c9eacd22ebf84bf1570d485de51cab09b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87590927"
---
# <a name="data-truncation-ssis"></a><span data-ttu-id="1ba92-102">数据截断 (SSIS)</span><span class="sxs-lookup"><span data-stu-id="1ba92-102">Data Truncation (SSIS)</span></span>
  <span data-ttu-id="1ba92-103">表达式可能因疏忽而致使数据截断。</span><span class="sxs-lookup"><span data-stu-id="1ba92-103">An expression may inadvertently cause data to be truncated.</span></span> <span data-ttu-id="1ba92-104">在下列情况下会发生截断：</span><span class="sxs-lookup"><span data-stu-id="1ba92-104">Truncation can occur under the following circumstances:</span></span>  
  
-   <span data-ttu-id="1ba92-105">Strings.</span><span class="sxs-lookup"><span data-stu-id="1ba92-105">Strings.</span></span> <span data-ttu-id="1ba92-106">例如，将 DT_WSTR 数据类型的字符串数据转换为相同长度（以字符计）的 DT_STR 数据类型字符串时，如果原始字符串包含有双字节字符将导致数据丢失。</span><span class="sxs-lookup"><span data-stu-id="1ba92-106">For example, translating string data with a DT_WSTR data type to the same length string, measured in characters, with a DT_STR data type causes data loss if the original string contains double-byte characters.</span></span>  
  
-   <span data-ttu-id="1ba92-107">有效数字。</span><span class="sxs-lookup"><span data-stu-id="1ba92-107">Significant digits.</span></span> <span data-ttu-id="1ba92-108">例如，将整数从 DT_I4 数据类型转换为 DT_I2 数据类型，或将无符号整数转换为有符号整数。</span><span class="sxs-lookup"><span data-stu-id="1ba92-108">For example, casting an integer from a DT_I4 data type to a DT_I2 data type or an unsigned integer to a signed integer.</span></span>  
  
-   <span data-ttu-id="1ba92-109">无效数字。</span><span class="sxs-lookup"><span data-stu-id="1ba92-109">Insignificant digits.</span></span> <span data-ttu-id="1ba92-110">例如，将实数从 DT_R8 转换为 DT_R4 或将整数从 DT_I4 数据类型转换为 DT_R4 数据类型。</span><span class="sxs-lookup"><span data-stu-id="1ba92-110">For example, casting a real number from a DT_R8 to a DT_R4 or an integer from a DT_I4 data type to a DT_R4 data type.</span></span>  
  
 <span data-ttu-id="1ba92-111">在分析表达式时，表达式计算器会标识可能导致截断的显式转换并发出警告。</span><span class="sxs-lookup"><span data-stu-id="1ba92-111">The expression evaluator identifies explicit casts that may cause truncation and issues a warning when the expression is parsed.</span></span> <span data-ttu-id="1ba92-112">例如，如果要将 30 个字符的字符串转换为 20 个字符的字符串，则表达式计算器会发出警告。</span><span class="sxs-lookup"><span data-stu-id="1ba92-112">For example, the expression evaluator warns you if a 30-character string is cast into a 20-character string.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="1ba92-113">运行时不检查截断；数据被截断而不发出警告。</span><span class="sxs-lookup"><span data-stu-id="1ba92-113">Truncation is not checked at run time; data is truncated without warning.</span></span> <span data-ttu-id="1ba92-114">但是，大部分数据适配器和转换支持可处理错误行处置的错误输出。</span><span class="sxs-lookup"><span data-stu-id="1ba92-114">However, most data adapters and transformations support error outputs that can handle the disposition of error rows.</span></span> <span data-ttu-id="1ba92-115">有关处理数据截断的详细信息，请参阅[数据中的错误处理](../data-flow/error-handling-in-data.md)。</span><span class="sxs-lookup"><span data-stu-id="1ba92-115">For more information about handling truncation of data, see [Error Handling in Data](../data-flow/error-handling-in-data.md).</span></span>  
  
  
