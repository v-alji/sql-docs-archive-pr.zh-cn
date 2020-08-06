---
title: 数值数据格式 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- integer data types [Integration Services]
- numeric data formats for fast parse
- locale-sensitive parsing [Integration Services]
- fast parse [Integration Services]
ms.assetid: fa3975ce-9d21-408a-857d-f85e30af27b0
author: chugugrace
ms.author: chugu
ms.openlocfilehash: cc54a331c3762e31ba9d9a431aaca7eda6374d8c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87586790"
---
# <a name="numeric-data-formats"></a><span data-ttu-id="553cd-102">数字数据格式</span><span class="sxs-lookup"><span data-stu-id="553cd-102">Numeric Data Formats</span></span>
  <span data-ttu-id="553cd-103">快速分析提供了一组简单、快捷、不受区域设置影响的数据分析例程。</span><span class="sxs-lookup"><span data-stu-id="553cd-103">Fast parse provides a fast, simple, locale-insensitive set of routines for parsing data.</span></span> <span data-ttu-id="553cd-104">快速分析仅支持有限的一组整数数据类型格式。</span><span class="sxs-lookup"><span data-stu-id="553cd-104">Fast parse supports only a limited set of formats for integer data types.</span></span>  
  
## <a name="integer-data-types"></a><span data-ttu-id="553cd-105">整数数据类型</span><span class="sxs-lookup"><span data-stu-id="553cd-105">Integer Data Types</span></span>  
 <span data-ttu-id="553cd-106">[!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 所提供的整数数据类型有：DT_I1、DT_UI1、DT_I2、DT_UI2、DT_I4、DT_UI4、DT_I8 和 DT_UI8。</span><span class="sxs-lookup"><span data-stu-id="553cd-106">The integer data types that [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] provides are DT_I1, DT_UI1, DT_I2, DT_UI2, DT_I4, DT_UI4, DT_I8, and DT_UI8.</span></span> <span data-ttu-id="553cd-107">有关详细信息，请参阅 [Integration Services 数据类型](data-flow/integration-services-data-types.md)。</span><span class="sxs-lookup"><span data-stu-id="553cd-107">For more information, see [Integration Services Data Types](data-flow/integration-services-data-types.md).</span></span>  
  
 <span data-ttu-id="553cd-108">快速分析支持下列整数数据类型的格式：</span><span class="sxs-lookup"><span data-stu-id="553cd-108">Fast parse supports the following formats for integer data types:</span></span>  
  
-   <span data-ttu-id="553cd-109">零个或多个前导及尾随空格或制表位。</span><span class="sxs-lookup"><span data-stu-id="553cd-109">Zero or more leading and trailing spaces or tab stops.</span></span> <span data-ttu-id="553cd-110">例如，“  123  ”是有效值。</span><span class="sxs-lookup"><span data-stu-id="553cd-110">For example, the value "  123  " is valid.</span></span> <span data-ttu-id="553cd-111">全部是空格的值计算结果为零。</span><span class="sxs-lookup"><span data-stu-id="553cd-111">A value that is all spaces evaluates to zero.</span></span>  
  
-   <span data-ttu-id="553cd-112">前导加号、减号或无加减号。</span><span class="sxs-lookup"><span data-stu-id="553cd-112">A leading plus sign, minus sign, or neither.</span></span> <span data-ttu-id="553cd-113">例如，+123、-123 和 123 都是有效值。</span><span class="sxs-lookup"><span data-stu-id="553cd-113">For example, the values +123, -123, and 123 are valid.</span></span>  
  
-   <span data-ttu-id="553cd-114">一位或多位阿拉伯数字 (0-9)。</span><span class="sxs-lookup"><span data-stu-id="553cd-114">One or more Hindu-Arabic numerals (0-9).</span></span> <span data-ttu-id="553cd-115">例如，345 是有效值。</span><span class="sxs-lookup"><span data-stu-id="553cd-115">For example, the value 345 is valid.</span></span> <span data-ttu-id="553cd-116">不支持其他语言的数字。</span><span class="sxs-lookup"><span data-stu-id="553cd-116">Other language numerals are not supported.</span></span>  
  
 <span data-ttu-id="553cd-117">不支持下列数据格式：</span><span class="sxs-lookup"><span data-stu-id="553cd-117">Non-supported data formats include the following:</span></span>  
  
-   <span data-ttu-id="553cd-118">特殊字符。</span><span class="sxs-lookup"><span data-stu-id="553cd-118">Special characters.</span></span> <span data-ttu-id="553cd-119">例如，不支持货币字符“$”，因而无法分析值“$20”。</span><span class="sxs-lookup"><span data-stu-id="553cd-119">For example, the currency character $ is not supported, and the value $20 cannot be parsed.</span></span>  
  
-   <span data-ttu-id="553cd-120">空白字符，如换行符、回车符和不间断空格符。</span><span class="sxs-lookup"><span data-stu-id="553cd-120">White-space characters such as line feed, carriage returns, and non-breaking spaces.</span></span> <span data-ttu-id="553cd-121">例如，无法分析值“ 123”。</span><span class="sxs-lookup"><span data-stu-id="553cd-121">For example, the value " 123" cannot be parsed.</span></span>  
  
-   <span data-ttu-id="553cd-122">以十六进制形式表示的整数。</span><span class="sxs-lookup"><span data-stu-id="553cd-122">Hexadecimal representations of integers.</span></span> <span data-ttu-id="553cd-123">例如，无法分析值 2EE。</span><span class="sxs-lookup"><span data-stu-id="553cd-123">For example, the value 2EE cannot be parsed.</span></span>  
  
-   <span data-ttu-id="553cd-124">以科学记数法形式表示的整数。</span><span class="sxs-lookup"><span data-stu-id="553cd-124">Scientific notation representation of integers.</span></span> <span data-ttu-id="553cd-125">例如，无法分析值 1E+10。</span><span class="sxs-lookup"><span data-stu-id="553cd-125">For example, the value 1E+10 cannot be parsed.</span></span>  
  
 <span data-ttu-id="553cd-126">下列格式为整数的输出数据格式：</span><span class="sxs-lookup"><span data-stu-id="553cd-126">The following formats are output data formats for integers:</span></span>  
  
-   <span data-ttu-id="553cd-127">负数用减号，正数不用符号。</span><span class="sxs-lookup"><span data-stu-id="553cd-127">A minus sign for negative numbers and nothing for positive ones.</span></span>  
  
-   <span data-ttu-id="553cd-128">没有空白。</span><span class="sxs-lookup"><span data-stu-id="553cd-128">No white spaces.</span></span>  
  
-   <span data-ttu-id="553cd-129">一位或多位阿拉伯数字 (0-9)。</span><span class="sxs-lookup"><span data-stu-id="553cd-129">One or more Hindu-Arabic numerals (0-9).</span></span>  
  
  
