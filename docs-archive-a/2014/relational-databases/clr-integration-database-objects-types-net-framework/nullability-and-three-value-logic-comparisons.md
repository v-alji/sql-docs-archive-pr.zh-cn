---
title: 为空性和三值逻辑比较 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: clr
ms.topic: reference
helpviewer_keywords:
- precision [CLR integration]
- overflow detections [CLR integration]
- null values [CLR integration]
- three-value logic comparisons [CLR integration]
- data types [CLR integration]
- SqlBoolean data type
ms.assetid: 13da4c7f-1010-4b2d-a63c-c69b6bfd96f1
author: rothja
ms.author: jroth
ms.openlocfilehash: 7b8000c1c28d5a1d3d129b6e8d01c4ab2fbbbc7d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87693974"
---
# <a name="nullability-and-three-value-logic-comparisons"></a><span data-ttu-id="4fd53-102">为 Null 性和三值逻辑比较</span><span class="sxs-lookup"><span data-stu-id="4fd53-102">Nullability and Three-Value Logic Comparisons</span></span>
  <span data-ttu-id="4fd53-103">如果您熟悉 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 数据类型，您会在 [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] 中的 `System.Data.SqlTypes` 命名空间中发现类似语义和精度。</span><span class="sxs-lookup"><span data-stu-id="4fd53-103">If you are familiar with the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] data types, you will find similar semantics and precision in the `System.Data.SqlTypes` namespace in the [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)].</span></span> <span data-ttu-id="4fd53-104">但是，这些数据类型之间存在一些不同之处，本主题介绍了这些不同之处中最重要的内容。</span><span class="sxs-lookup"><span data-stu-id="4fd53-104">There are some differences, however, and this topic covers the most important of these differences.</span></span>  
  
## <a name="null-values"></a><span data-ttu-id="4fd53-105">NULL 值</span><span class="sxs-lookup"><span data-stu-id="4fd53-105">NULL Values</span></span>  
 <span data-ttu-id="4fd53-106">本机公共语言运行时 (CLR) 数据类型和 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 数据类型之间的一个主要不同就是前者不允许 NULL 值，而后者提供了完整 NULL 语义。</span><span class="sxs-lookup"><span data-stu-id="4fd53-106">A primary difference between native common language runtime (CLR) data types and [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] data types is that the former do not allow for NULL values, while the latter provide full NULL semantics.</span></span>  
  
 <span data-ttu-id="4fd53-107">NULL 值对比较会产生影响。</span><span class="sxs-lookup"><span data-stu-id="4fd53-107">Comparisons are affected by NULL values.</span></span> <span data-ttu-id="4fd53-108">当对 x 和 y 两个值进行比较时，如果 x 或 y 其中一个为 NULL，则某些逻辑比较将为 UNKNOWN 值而不是 True 或 False。</span><span class="sxs-lookup"><span data-stu-id="4fd53-108">When comparing two values x and y, if either x or y is NULL, then some logical comparisons evaluate to an UNKNOWN value rather than true or false.</span></span>  
  
## <a name="sqlboolean-data-type"></a><span data-ttu-id="4fd53-109">SqlBoolean 数据类型</span><span class="sxs-lookup"><span data-stu-id="4fd53-109">SqlBoolean Data Type</span></span>  
 <span data-ttu-id="4fd53-110">`System.Data.SqlTypes` 命名空间引入了一个 `SqlBoolean` 类型以表示该三值逻辑。</span><span class="sxs-lookup"><span data-stu-id="4fd53-110">The `System.Data.SqlTypes` namespace introduces a `SqlBoolean` type to represent this 3-value logic.</span></span> <span data-ttu-id="4fd53-111">在任何 `SqlTypes` 之间进行比较将返回一个 `SqlBoolean` 值类型。</span><span class="sxs-lookup"><span data-stu-id="4fd53-111">Comparisons between any `SqlTypes` return a `SqlBoolean` value type.</span></span> <span data-ttu-id="4fd53-112">UNKNOWN 值由 `SqlBoolean` 类型的 Null 值表示。</span><span class="sxs-lookup"><span data-stu-id="4fd53-112">The UNKNOWN value is represented by the null value of the `SqlBoolean` type.</span></span> <span data-ttu-id="4fd53-113">提供了属性 `IsTrue`、`IsFalse` 和 `IsNull` 来检查 `SqlBoolean` 类型的值。</span><span class="sxs-lookup"><span data-stu-id="4fd53-113">The properties `IsTrue`, `IsFalse`, and `IsNull` are provided to check the value of a `SqlBoolean` type.</span></span>  
  
## <a name="operations-functions-and-null-values"></a><span data-ttu-id="4fd53-114">操作、函数和 NULL 值</span><span class="sxs-lookup"><span data-stu-id="4fd53-114">Operations, Functions, and NULL Values</span></span>  
 <span data-ttu-id="4fd53-115">所有算术运算符 (+、-、 \* 、/、% ) 、按位运算符 (~、& 和 |) ，如果的任何操作数或参数为 null，则大多数函数都返回 NULL `SqlTypes` 。</span><span class="sxs-lookup"><span data-stu-id="4fd53-115">All arithmetic operators (+, -, \*, /, %), bitwise operators (~, &, and |), and most functions return NULL if any of the operands or arguments of `SqlTypes` are NULL.</span></span> <span data-ttu-id="4fd53-116">`IsNull` 属性始终返回一个 True 或 False 值。</span><span class="sxs-lookup"><span data-stu-id="4fd53-116">The `IsNull` property always returns a true or false value.</span></span>  
  
## <a name="precision"></a><span data-ttu-id="4fd53-117">精度</span><span class="sxs-lookup"><span data-stu-id="4fd53-117">Precision</span></span>  
 <span data-ttu-id="4fd53-118">[!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] CLR 中的 decimal 数据类型较 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 中的 numeric 和 decimal 数据类型具有不同的最大值。</span><span class="sxs-lookup"><span data-stu-id="4fd53-118">Decimal data types in the [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] CLR have different maximum values than those of the numeric and decimal data types in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="4fd53-119">另外，在 [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] CLR 中，decimal 数据类型假设具有最大精度。</span><span class="sxs-lookup"><span data-stu-id="4fd53-119">In addition, in the [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] CLR decimal data types assume the maximum precision.</span></span> <span data-ttu-id="4fd53-120">但是，在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 的 CLR 中，`SqlDecimal` 提供了与 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 中的 decimal 数据类型相同的最大精度和小数位数以及相同的语义。</span><span class="sxs-lookup"><span data-stu-id="4fd53-120">In the CLR for [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], however, `SqlDecimal` provides the same maximum precision and scale, and the same semantics as the decimal data type in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
## <a name="overflow-detection"></a><span data-ttu-id="4fd53-121">溢出检测</span><span class="sxs-lookup"><span data-stu-id="4fd53-121">Overflow Detection</span></span>  
 <span data-ttu-id="4fd53-122">在 [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] CLR 中，两个很大的数字相加可能不会引发异常。</span><span class="sxs-lookup"><span data-stu-id="4fd53-122">In the [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] CLR, the addition of two very large numbers may not throw an exception.</span></span> <span data-ttu-id="4fd53-123">相反，如果未使用检查运算符，则返回的值可能作为负整数“环绕”。</span><span class="sxs-lookup"><span data-stu-id="4fd53-123">Instead, if no check operator has been used, the returned result may "wrap around" as a negative integer.</span></span> <span data-ttu-id="4fd53-124">在 `System.Data.SqlTypes` 中，所有上溢和下溢错误以及被零除错误均会引发异常。</span><span class="sxs-lookup"><span data-stu-id="4fd53-124">In `System.Data.SqlTypes`, exceptions are thrown for all overflow and underflow errors, and divide-by-zero errors.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4fd53-125">另请参阅</span><span class="sxs-lookup"><span data-stu-id="4fd53-125">See Also</span></span>  
 [<span data-ttu-id="4fd53-126">.NET Framework 中的 SQL Server 数据类型</span><span class="sxs-lookup"><span data-stu-id="4fd53-126">SQL Server Data Types in the .NET Framework</span></span>](sql-server-data-types-in-the-net-framework.md)  
  
  
