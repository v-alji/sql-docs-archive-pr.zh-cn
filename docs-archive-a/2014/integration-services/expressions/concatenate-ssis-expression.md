---
title: + （连接）（SSIS 表达式）| Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- concatenation [Integration Services]
- + (concatenate operator)
- concatenate operator (+)
ms.assetid: 0fed6334-7a4f-42dc-a611-191fcaa0e443
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 1c01f82a50962f42862db836171b0ad683c97453
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87690006"
---
# <a name="-concatenate-ssis-expression"></a><span data-ttu-id="091b6-102">+（连接）（SSIS 表达式）</span><span class="sxs-lookup"><span data-stu-id="091b6-102">+ (Concatenate) (SSIS Expression)</span></span>
  <span data-ttu-id="091b6-103">将两个表达式连接为一个表达式。</span><span class="sxs-lookup"><span data-stu-id="091b6-103">Concatenates two expressions into one expression.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="091b6-104">语法</span><span class="sxs-lookup"><span data-stu-id="091b6-104">Syntax</span></span>  
  
```  
  
character_expression1 + character_expression2  
  
```  
  
## <a name="arguments"></a><span data-ttu-id="091b6-105">参数</span><span class="sxs-lookup"><span data-stu-id="091b6-105">Arguments</span></span>  
 <span data-ttu-id="091b6-106">*expression1、expression2*</span><span class="sxs-lookup"><span data-stu-id="091b6-106">*expression1, expression2*</span></span>  
 <span data-ttu-id="091b6-107">是任何有效的 DT_STR、DT_WSTR、DT_TEXT、DT_NTEXT 或 DT_IMAGE 数据类型表达式。</span><span class="sxs-lookup"><span data-stu-id="091b6-107">Is any valid DT_STR, DT_WSTR, DT_TEXT, DT_NTEXT, or DT_IMAGE data type expression.</span></span>  
  
## <a name="result-types"></a><span data-ttu-id="091b6-108">结果类型</span><span class="sxs-lookup"><span data-stu-id="091b6-108">Result Types</span></span>  
 <span data-ttu-id="091b6-109">DT_WSTR</span><span class="sxs-lookup"><span data-stu-id="091b6-109">DT_WSTR</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="091b6-110">备注</span><span class="sxs-lookup"><span data-stu-id="091b6-110">Remarks</span></span>  
 <span data-ttu-id="091b6-111">表达式可以使用 DT_STR 和 DT_WSTR 数据类型中的任一种或两者都使用。</span><span class="sxs-lookup"><span data-stu-id="091b6-111">The expression can use either or both of the DT_STR and DT_WSTR data types.</span></span>  
  
 <span data-ttu-id="091b6-112">DT_STR 和 DT_WSTR 数据类型的连接将返回 DT_WSTR 类型的结果。</span><span class="sxs-lookup"><span data-stu-id="091b6-112">The concatenation of the DT_STR and DT_WSTR data types returns a result of the DT_WSTR type.</span></span> <span data-ttu-id="091b6-113">字符串的长度是两个原始字符串长度的和（以字符计）。</span><span class="sxs-lookup"><span data-stu-id="091b6-113">The length of the string is the sum of the lengths of the original strings expressed in characters.</span></span>  
  
 <span data-ttu-id="091b6-114">只有字符串数据类型 DT_STR 和 DT_WSTR 的数据或二进制大型对象块 (BLOB) 数据类型 DT_TEXT、DT_NTEXT 和 DT_IMAGE 类型的数据可以连接。</span><span class="sxs-lookup"><span data-stu-id="091b6-114">Only data with the string data types DT_STR and DT_WSTR or the Binary Large Object Block (BLOB) data types DT_TEXT, DT_NTEXT, and DT_IMAGE can be concatenated.</span></span> <span data-ttu-id="091b6-115">其他数据类型必须显式转换为这些数据类型之一，然后才能进行连接。</span><span class="sxs-lookup"><span data-stu-id="091b6-115">Other data types must be explicitly converted to one of these data types before concatenation occurs.</span></span> <span data-ttu-id="091b6-116">有关数据类型之间的合法转换的详细信息，请参阅[转换（SSIS 表达式）](cast-ssis-expression.md)。</span><span class="sxs-lookup"><span data-stu-id="091b6-116">For more information about legal casts between data types, see [Cast &#40;SSIS Expression&#41;](cast-ssis-expression.md).</span></span>  
  
 <span data-ttu-id="091b6-117">两个表达式必须具有相同的数据类型，或者其中一个表达式必须能够隐式转换为另一表达式的数据类型。</span><span class="sxs-lookup"><span data-stu-id="091b6-117">Both expressions must be of the same data type, or one expression must be implicitly convertible to the data type of the other expression.</span></span> <span data-ttu-id="091b6-118">例如，如果字符串“Order date is”和 **OrderDate** 列进行连接， **OrderDate** 中的值将隐式转换为字符串数据类型。</span><span class="sxs-lookup"><span data-stu-id="091b6-118">For example, if the string "Order date is " and the column **OrderDate** are concatenated, the values in **OrderDate** are implicitly converted to a string data type.</span></span> <span data-ttu-id="091b6-119">若要连接两个数值，这两个数值都必须显式转换为某种字符串数据类型。</span><span class="sxs-lookup"><span data-stu-id="091b6-119">To concatenate two numeric values, both numeric values must be explicitly cast to a string data type.</span></span>  
  
 <span data-ttu-id="091b6-120">连接只能使用一种 BLOB 数据类型：DT_TEXT、DT_NTEXT 或 DT_IMAGE。</span><span class="sxs-lookup"><span data-stu-id="091b6-120">A concatenation can use only one BLOB data type: DT_TEXT, DT_NTEXT, or DT_IMAGE.</span></span>  
  
 <span data-ttu-id="091b6-121">如果任一元素为空，则结果为空。</span><span class="sxs-lookup"><span data-stu-id="091b6-121">If either element is null, the result is null.</span></span>  
  
 <span data-ttu-id="091b6-122">字符串文字必须用引号引起来。</span><span class="sxs-lookup"><span data-stu-id="091b6-122">String literals must be enclosed in quotation marks.</span></span>  
  
## <a name="expression-examples"></a><span data-ttu-id="091b6-123">表达式示例</span><span class="sxs-lookup"><span data-stu-id="091b6-123">Expression Examples</span></span>  
 <span data-ttu-id="091b6-124">此示例连接了 **FirstName** 和 **LastName** 列中的值，并在两个值之间插入一个空格。</span><span class="sxs-lookup"><span data-stu-id="091b6-124">This example concatenates the values in the **FirstName** and **LastName** columns and inserts a space between them.</span></span>  
  
```  
FirstName + ' ' + LastName  
```  
  
 <span data-ttu-id="091b6-125">此示例连接了变量 **ZIPCode** 和 **ZIPCode+4**。</span><span class="sxs-lookup"><span data-stu-id="091b6-125">This example concatenates the variables **ZIPCode** and **ZIPCode+4**.</span></span> <span data-ttu-id="091b6-126">两个变量都具有字符串数据类型。</span><span class="sxs-lookup"><span data-stu-id="091b6-126">Both variables have a string data type.</span></span> <span data-ttu-id="091b6-127">**ZIPCode+4** 必须用方括号括起来，因为该变量名包含 + 字符。</span><span class="sxs-lookup"><span data-stu-id="091b6-127">**ZIPCode+4** must be enclosed in brackets because the variable name includes the + character.</span></span>  
  
```  
@ZIPCcode + "-" + @[ZipCode+4]  
```  
  
## <a name="see-also"></a><span data-ttu-id="091b6-128">另请参阅</span><span class="sxs-lookup"><span data-stu-id="091b6-128">See Also</span></span>  
 <span data-ttu-id="091b6-129">[运算符优先级和结合性](operator-precedence-and-associativity.md) </span><span class="sxs-lookup"><span data-stu-id="091b6-129">[Operator Precedence and Associativity](operator-precedence-and-associativity.md) </span></span>  
 [<span data-ttu-id="091b6-130">运算符（SSIS 表达式）</span><span class="sxs-lookup"><span data-stu-id="091b6-130">Operators &#40;SSIS Expression&#41;</span></span>](operators-ssis-expression.md)  
  
  
