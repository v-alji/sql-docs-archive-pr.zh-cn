---
title: NULL（SSIS 表达式）| Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- NULL function
- null values [Integration Services]
ms.assetid: df144237-3fbb-41ac-8624-efd92b6522b9
author: chugugrace
ms.author: chugu
ms.openlocfilehash: e14cd51b4e245ca6984a4c62eae2b9d5536ab1f4
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87577752"
---
# <a name="null-ssis-expression"></a><span data-ttu-id="2f6a9-102">NULL（SSIS 表达式）</span><span class="sxs-lookup"><span data-stu-id="2f6a9-102">NULL (SSIS Expression)</span></span>
  <span data-ttu-id="2f6a9-103">返回请求的数据类型的 Null 值。</span><span class="sxs-lookup"><span data-stu-id="2f6a9-103">Returns a null value of a requested data type.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2f6a9-104">语法</span><span class="sxs-lookup"><span data-stu-id="2f6a9-104">Syntax</span></span>  
  
```  
  
NULL(typespec)  
```  
  
## <a name="arguments"></a><span data-ttu-id="2f6a9-105">参数</span><span class="sxs-lookup"><span data-stu-id="2f6a9-105">Arguments</span></span>  
 <span data-ttu-id="2f6a9-106">*typespec*</span><span class="sxs-lookup"><span data-stu-id="2f6a9-106">*typespec*</span></span>  
 <span data-ttu-id="2f6a9-107">有效的数据类型。</span><span class="sxs-lookup"><span data-stu-id="2f6a9-107">Is a valid data type.</span></span> <span data-ttu-id="2f6a9-108">有关详细信息，请参阅 [Integration Services 数据类型](../data-flow/integration-services-data-types.md)。</span><span class="sxs-lookup"><span data-stu-id="2f6a9-108">For more information, see [Integration Services Data Types](../data-flow/integration-services-data-types.md).</span></span>  
  
## <a name="result-types"></a><span data-ttu-id="2f6a9-109">结果类型</span><span class="sxs-lookup"><span data-stu-id="2f6a9-109">Result Types</span></span>  
 <span data-ttu-id="2f6a9-110">任何包含 Null 值的有效数据类型。</span><span class="sxs-lookup"><span data-stu-id="2f6a9-110">Any valid data type with a null value.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="2f6a9-111">备注</span><span class="sxs-lookup"><span data-stu-id="2f6a9-111">Remarks</span></span>  
 <span data-ttu-id="2f6a9-112">如果参数为 Null，则 NULL 返回的结果为 Null。</span><span class="sxs-lookup"><span data-stu-id="2f6a9-112">NULL returns a null result if the argument is null.</span></span>  
  
 <span data-ttu-id="2f6a9-113">请求某些数据类型的 Null 值时需要提供参数。</span><span class="sxs-lookup"><span data-stu-id="2f6a9-113">Parameters are required to request a null value for some data types.</span></span> <span data-ttu-id="2f6a9-114">下表列出了这些数据类型及其参数。</span><span class="sxs-lookup"><span data-stu-id="2f6a9-114">The following table lists these data types and their parameters.</span></span>  
  
|<span data-ttu-id="2f6a9-115">数据类型</span><span class="sxs-lookup"><span data-stu-id="2f6a9-115">Data type</span></span>|<span data-ttu-id="2f6a9-116">参数</span><span class="sxs-lookup"><span data-stu-id="2f6a9-116">Parameter</span></span>|<span data-ttu-id="2f6a9-117">示例</span><span class="sxs-lookup"><span data-stu-id="2f6a9-117">Example</span></span>|  
|---------------|---------------|-------------|  
|<span data-ttu-id="2f6a9-118">DT_STR</span><span class="sxs-lookup"><span data-stu-id="2f6a9-118">DT_STR</span></span>|<span data-ttu-id="2f6a9-119">*charcount*</span><span class="sxs-lookup"><span data-stu-id="2f6a9-119">*charcount*</span></span><br /><br /> <span data-ttu-id="2f6a9-120">*codepage*</span><span class="sxs-lookup"><span data-stu-id="2f6a9-120">*codepage*</span></span>|<span data-ttu-id="2f6a9-121">(DT_STR,30,1252) 将 30 个字符转换为使用 1252 代码页的 DT_STR 数据类型。</span><span class="sxs-lookup"><span data-stu-id="2f6a9-121">(DT_STR,30,1252) casts 30 characters to the DT_STR data type using the 1252 code page.</span></span>|  
|<span data-ttu-id="2f6a9-122">DT_WSTR</span><span class="sxs-lookup"><span data-stu-id="2f6a9-122">DT_WSTR</span></span>|<span data-ttu-id="2f6a9-123">*charcount*</span><span class="sxs-lookup"><span data-stu-id="2f6a9-123">*charcount*</span></span>|<span data-ttu-id="2f6a9-124">(DT_WSTR,20) 将 20 个字符转换为 DT_WSTR 数据类型。</span><span class="sxs-lookup"><span data-stu-id="2f6a9-124">(DT_WSTR,20) casts 20 characters to the DT_WSTR data type.</span></span>|  
|<span data-ttu-id="2f6a9-125">DT_BYTES</span><span class="sxs-lookup"><span data-stu-id="2f6a9-125">DT_BYTES</span></span>|<span data-ttu-id="2f6a9-126">*bytecount*</span><span class="sxs-lookup"><span data-stu-id="2f6a9-126">*bytecount*</span></span>|<span data-ttu-id="2f6a9-127">(DT_BYTES,50) 将 50 个字节的数据转换为 DT_BYTES 数据类型。</span><span class="sxs-lookup"><span data-stu-id="2f6a9-127">(DT_BYTES,50) casts 50 bytes to the DT_BYTES data type.</span></span>|  
|<span data-ttu-id="2f6a9-128">DT_DECIMAL</span><span class="sxs-lookup"><span data-stu-id="2f6a9-128">DT_DECIMAL</span></span>|<span data-ttu-id="2f6a9-129">*scale*</span><span class="sxs-lookup"><span data-stu-id="2f6a9-129">*scale*</span></span>|<span data-ttu-id="2f6a9-130">(DT_DECIMAL,2) 将数值转换为带 2 位小数的 DT_DECIMAL 数据类型。</span><span class="sxs-lookup"><span data-stu-id="2f6a9-130">(DT_DECIMAL,2) casts a numeric value to the DT_DECIMAL data type using a scale of 2.</span></span>|  
|<span data-ttu-id="2f6a9-131">DT_NUMERIC</span><span class="sxs-lookup"><span data-stu-id="2f6a9-131">DT_NUMERIC</span></span>|<span data-ttu-id="2f6a9-132">*精度*</span><span class="sxs-lookup"><span data-stu-id="2f6a9-132">*precision*</span></span><br /><br /> <span data-ttu-id="2f6a9-133">*scale*</span><span class="sxs-lookup"><span data-stu-id="2f6a9-133">*scale*</span></span>|<span data-ttu-id="2f6a9-134">(DT_NUMERIC,10,3) 将数值转换为带 3 位小数且精度为 10 的 DT_NUMERIC 数据类型。</span><span class="sxs-lookup"><span data-stu-id="2f6a9-134">(DT_NUMERIC,10,3) casts a numeric value to the DT_NUMERIC data type using a precision of 10 and a scale of 3.</span></span>|  
|<span data-ttu-id="2f6a9-135">DT_TEXT</span><span class="sxs-lookup"><span data-stu-id="2f6a9-135">DT_TEXT</span></span>|<span data-ttu-id="2f6a9-136">*codepage*</span><span class="sxs-lookup"><span data-stu-id="2f6a9-136">*codepage*</span></span>|<span data-ttu-id="2f6a9-137">(DT_TEXT,1252) 将值转换为使用 1252 代码页的 DT_TEXT 数据类型。</span><span class="sxs-lookup"><span data-stu-id="2f6a9-137">(DT_TEXT,1252) casts a value to the DT_TEXT data type using the 1252 code page.</span></span>|  
  
## <a name="expression-examples"></a><span data-ttu-id="2f6a9-138">表达式示例</span><span class="sxs-lookup"><span data-stu-id="2f6a9-138">Expression Examples</span></span>  
 <span data-ttu-id="2f6a9-139">以下示例将返回下列数据类型的 Null 值：DT_STR、DT_DATE 和 DT_BOOL。</span><span class="sxs-lookup"><span data-stu-id="2f6a9-139">These examples return the null value of the data types: DT_STR, DT_DATE, and DT_BOOL.</span></span>  
  
```  
NULL(DT_STR,10,1252)  
NULL(DT_DATE)  
NULL(DT_BOOL)  
```  
  
## <a name="see-also"></a><span data-ttu-id="2f6a9-140">另请参阅</span><span class="sxs-lookup"><span data-stu-id="2f6a9-140">See Also</span></span>  
 <span data-ttu-id="2f6a9-141">[ISNULL（SSIS 表达式）](null-ssis-expression.md) </span><span class="sxs-lookup"><span data-stu-id="2f6a9-141">[ISNULL &#40;SSIS Expression&#41;](null-ssis-expression.md) </span></span>  
 [<span data-ttu-id="2f6a9-142">函数（SSIS 表达式）</span><span class="sxs-lookup"><span data-stu-id="2f6a9-142">Functions &#40;SSIS Expression&#41;</span></span>](functions-ssis-expression.md)  
  
  
