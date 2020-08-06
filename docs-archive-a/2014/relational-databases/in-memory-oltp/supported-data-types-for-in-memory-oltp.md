---
title: 支持的数据类型 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: in-memory-oltp
ms.topic: conceptual
ms.assetid: a7380ef0-c9d7-49e4-b6de-fad34752b9f3
author: rothja
ms.author: jroth
ms.openlocfilehash: a7dda500486c39a66f871d5934f957028fc51e9d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87693330"
---
# <a name="supported-data-types"></a><span data-ttu-id="9ab39-102">支持的数据类型</span><span class="sxs-lookup"><span data-stu-id="9ab39-102">Supported Data Types</span></span>
  <span data-ttu-id="9ab39-103">内存优化表和本机编译存储过程中 **支持** 以下数据类型：</span><span class="sxs-lookup"><span data-stu-id="9ab39-103">The following data types are **supported** in memory-optimized tables and natively compiled stored procedures:</span></span>  
  
 <span data-ttu-id="9ab39-104">**数值数据类型**</span><span class="sxs-lookup"><span data-stu-id="9ab39-104">**Numeric Data Types**</span></span>  
  
|<span data-ttu-id="9ab39-105">数据类型</span><span class="sxs-lookup"><span data-stu-id="9ab39-105">Data type</span></span>|<span data-ttu-id="9ab39-106">更多信息</span><span class="sxs-lookup"><span data-stu-id="9ab39-106">For more information</span></span>|  
|---------------|--------------------------|  
|<span data-ttu-id="9ab39-107">int</span><span class="sxs-lookup"><span data-stu-id="9ab39-107">int</span></span>|[<span data-ttu-id="9ab39-108">int、bigint、smallint 和 tinyint (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="9ab39-108">int, bigint, smallint, and tinyint &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/data-types/int-bigint-smallint-and-tinyint-transact-sql)|  
|<span data-ttu-id="9ab39-109">bigint</span><span class="sxs-lookup"><span data-stu-id="9ab39-109">bigint</span></span>|[<span data-ttu-id="9ab39-110">int、bigint、smallint 和 tinyint (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="9ab39-110">int, bigint, smallint, and tinyint &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/data-types/int-bigint-smallint-and-tinyint-transact-sql)|  
|<span data-ttu-id="9ab39-111">smallint</span><span class="sxs-lookup"><span data-stu-id="9ab39-111">smallint</span></span>|[<span data-ttu-id="9ab39-112">int、bigint、smallint 和 tinyint (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="9ab39-112">int, bigint, smallint, and tinyint &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/data-types/int-bigint-smallint-and-tinyint-transact-sql)|  
|<span data-ttu-id="9ab39-113">tinyint</span><span class="sxs-lookup"><span data-stu-id="9ab39-113">tinyint</span></span>|[<span data-ttu-id="9ab39-114">int、bigint、smallint 和 tinyint (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="9ab39-114">int, bigint, smallint, and tinyint &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/data-types/int-bigint-smallint-and-tinyint-transact-sql)|  
|<span data-ttu-id="9ab39-115">Decimal</span><span class="sxs-lookup"><span data-stu-id="9ab39-115">decimal</span></span>|[<span data-ttu-id="9ab39-116">decimal 和 numeric (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="9ab39-116">decimal and numeric &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/data-types/decimal-and-numeric-transact-sql)|  
|<span data-ttu-id="9ab39-117">numeric</span><span class="sxs-lookup"><span data-stu-id="9ab39-117">numeric</span></span>|[<span data-ttu-id="9ab39-118">decimal 和 numeric (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="9ab39-118">decimal and numeric &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/data-types/decimal-and-numeric-transact-sql)|  
|<span data-ttu-id="9ab39-119">FLOAT</span><span class="sxs-lookup"><span data-stu-id="9ab39-119">float</span></span>|[<span data-ttu-id="9ab39-120">float 和 real (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="9ab39-120">float and real &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/data-types/float-and-real-transact-sql)|  
|<span data-ttu-id="9ab39-121">real</span><span class="sxs-lookup"><span data-stu-id="9ab39-121">real</span></span>|[<span data-ttu-id="9ab39-122">float 和 real (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="9ab39-122">float and real &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/data-types/float-and-real-transact-sql)|  
|<span data-ttu-id="9ab39-123">money</span><span class="sxs-lookup"><span data-stu-id="9ab39-123">money</span></span>|[<span data-ttu-id="9ab39-124">money 和 smallmoney (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="9ab39-124">money and smallmoney &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/data-types/money-and-smallmoney-transact-sql)|  
|<span data-ttu-id="9ab39-125">smallmoney</span><span class="sxs-lookup"><span data-stu-id="9ab39-125">smallmoney</span></span>|[<span data-ttu-id="9ab39-126">money 和 smallmoney (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="9ab39-126">money and smallmoney &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/data-types/money-and-smallmoney-transact-sql)|  
  
 <span data-ttu-id="9ab39-127">**字符串数据类型**</span><span class="sxs-lookup"><span data-stu-id="9ab39-127">**String Data Types**</span></span>  
  
|<span data-ttu-id="9ab39-128">数据类型</span><span class="sxs-lookup"><span data-stu-id="9ab39-128">Data type</span></span>|<span data-ttu-id="9ab39-129">更多信息</span><span class="sxs-lookup"><span data-stu-id="9ab39-129">For more information</span></span>|  
|---------------|--------------------------|  
|<span data-ttu-id="9ab39-130">char(n)</span><span class="sxs-lookup"><span data-stu-id="9ab39-130">char(n)</span></span>|[<span data-ttu-id="9ab39-131">char 和 varchar (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="9ab39-131">char and varchar &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/data-types/char-and-varchar-transact-sql)|  
|<span data-ttu-id="9ab39-132">varchar (n) <sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="9ab39-132">varchar(n) <sup>1</sup></span></span>|[<span data-ttu-id="9ab39-133">char 和 varchar (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="9ab39-133">char and varchar &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/data-types/char-and-varchar-transact-sql)|  
|<span data-ttu-id="9ab39-134">nchar(n)</span><span class="sxs-lookup"><span data-stu-id="9ab39-134">nchar(n)</span></span>|[<span data-ttu-id="9ab39-135">nchar 和 nvarchar (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="9ab39-135">nchar and nvarchar &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/data-types/nchar-and-nvarchar-transact-sql)|  
|<span data-ttu-id="9ab39-136">nvarchar (n) <sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="9ab39-136">nvarchar(n) <sup>1</sup></span></span>|[<span data-ttu-id="9ab39-137">nchar 和 nvarchar (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="9ab39-137">nchar and nvarchar &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/data-types/nchar-and-nvarchar-transact-sql)|  
|<span data-ttu-id="9ab39-138">sysname</span><span class="sxs-lookup"><span data-stu-id="9ab39-138">sysname</span></span>|[<span data-ttu-id="9ab39-139">nchar 和 nvarchar (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="9ab39-139">nchar and nvarchar &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/data-types/nchar-and-nvarchar-transact-sql)|  
  
 <span data-ttu-id="9ab39-140"><sup>1</sup>限制为每行总数8060个字节，计算可变长度类型中 (n) 。</span><span class="sxs-lookup"><span data-stu-id="9ab39-140"><sup>1</sup> Limitation is 8060 bytes per row total, counting (n) in variable-length types.</span></span>  
  
 <span data-ttu-id="9ab39-141">有关支持的排序规则的信息，请参阅 [Collations and Code Pages](../../database-engine/collations-and-code-pages.md)。</span><span class="sxs-lookup"><span data-stu-id="9ab39-141">For information about supported collations, see [Collations and Code Pages](../../database-engine/collations-and-code-pages.md).</span></span>  
  
 <span data-ttu-id="9ab39-142">**日期和时间数据类型**</span><span class="sxs-lookup"><span data-stu-id="9ab39-142">**Date and Time Data Types**</span></span>  
  
|<span data-ttu-id="9ab39-143">数据类型</span><span class="sxs-lookup"><span data-stu-id="9ab39-143">Data type</span></span>|<span data-ttu-id="9ab39-144">更多信息</span><span class="sxs-lookup"><span data-stu-id="9ab39-144">For more information</span></span>|  
|---------------|--------------------------|  
|<span data-ttu-id="9ab39-145">date</span><span class="sxs-lookup"><span data-stu-id="9ab39-145">date</span></span>|[<span data-ttu-id="9ab39-146">date (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="9ab39-146">date &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/data-types/date-transact-sql)|  
|<span data-ttu-id="9ab39-147">time</span><span class="sxs-lookup"><span data-stu-id="9ab39-147">time</span></span>|[<span data-ttu-id="9ab39-148">time (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="9ab39-148">time &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/data-types/time-transact-sql)|  
|<span data-ttu-id="9ab39-149">datetime</span><span class="sxs-lookup"><span data-stu-id="9ab39-149">datetime</span></span>|[<span data-ttu-id="9ab39-150">datetime (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="9ab39-150">datetime &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/data-types/datetime-transact-sql)|  
|<span data-ttu-id="9ab39-151">datetime2</span><span class="sxs-lookup"><span data-stu-id="9ab39-151">datetime2</span></span>|[<span data-ttu-id="9ab39-152">datetime2 (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="9ab39-152">datetime2 &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/data-types/datetime2-transact-sql)|  
|<span data-ttu-id="9ab39-153">smalldatetime</span><span class="sxs-lookup"><span data-stu-id="9ab39-153">smalldatetime</span></span>|[<span data-ttu-id="9ab39-154">smalldatetime (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="9ab39-154">smalldatetime &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/data-types/smalldatetime-transact-sql)|  
  
 <span data-ttu-id="9ab39-155">**二进制数据类型**</span><span class="sxs-lookup"><span data-stu-id="9ab39-155">**Binary Data Types**</span></span>  
  
|<span data-ttu-id="9ab39-156">数据类型</span><span class="sxs-lookup"><span data-stu-id="9ab39-156">Data type</span></span>|<span data-ttu-id="9ab39-157">更多信息</span><span class="sxs-lookup"><span data-stu-id="9ab39-157">For more information</span></span>|  
|---------------|--------------------------|  
|<span data-ttu-id="9ab39-158">bit</span><span class="sxs-lookup"><span data-stu-id="9ab39-158">bit</span></span>|[<span data-ttu-id="9ab39-159">bit (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="9ab39-159">bit &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/data-types/bit-transact-sql)|  
|<span data-ttu-id="9ab39-160">binary(n)</span><span class="sxs-lookup"><span data-stu-id="9ab39-160">binary(n)</span></span>|[<span data-ttu-id="9ab39-161">binary 和 varbinary (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="9ab39-161">binary and varbinary &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/data-types/binary-and-varbinary-transact-sql)|  
|<span data-ttu-id="9ab39-162">varbinary (n) <sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="9ab39-162">varbinary(n) <sup>1</sup></span></span>|[<span data-ttu-id="9ab39-163">binary 和 varbinary (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="9ab39-163">binary and varbinary &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/data-types/binary-and-varbinary-transact-sql)|  
  
 <span data-ttu-id="9ab39-164"><sup>1</sup>限制为每行总数8060个字节，计算可变长度类型中 (n) 。</span><span class="sxs-lookup"><span data-stu-id="9ab39-164"><sup>1</sup> Limitation is 8060 bytes per row total, counting (n) in variable-length types.</span></span>  
  
 <span data-ttu-id="9ab39-165">**其他数据类型**</span><span class="sxs-lookup"><span data-stu-id="9ab39-165">**Other data types**</span></span>  
  
|<span data-ttu-id="9ab39-166">数据类型</span><span class="sxs-lookup"><span data-stu-id="9ab39-166">Data type</span></span>|<span data-ttu-id="9ab39-167">更多信息</span><span class="sxs-lookup"><span data-stu-id="9ab39-167">For more information</span></span>|  
|---------------|--------------------------|  
|<span data-ttu-id="9ab39-168">uniqueidentifier</span><span class="sxs-lookup"><span data-stu-id="9ab39-168">uniqueidentifier</span></span>|[<span data-ttu-id="9ab39-169">uniqueidentifier (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="9ab39-169">uniqueidentifier &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/data-types/uniqueidentifier-transact-sql)|  
  
 <span data-ttu-id="9ab39-170">**不支持的数据类型**</span><span class="sxs-lookup"><span data-stu-id="9ab39-170">**Unsupported Data Types**</span></span>  
  
 <span data-ttu-id="9ab39-171">不支持以下数据类型：</span><span class="sxs-lookup"><span data-stu-id="9ab39-171">The following data types are not supported:</span></span>  
  
||||  
|-|-|-|  
|<span data-ttu-id="9ab39-172">DATETIMEOFFSET</span><span class="sxs-lookup"><span data-stu-id="9ab39-172">DATETIMEOFFSET</span></span>|<span data-ttu-id="9ab39-173">GEOGRAPHY</span><span class="sxs-lookup"><span data-stu-id="9ab39-173">GEOGRAPHY</span></span>|<span data-ttu-id="9ab39-174">GEOMETRY</span><span class="sxs-lookup"><span data-stu-id="9ab39-174">GEOMETRY</span></span>|  
|<span data-ttu-id="9ab39-175">HIERARCHYID</span><span class="sxs-lookup"><span data-stu-id="9ab39-175">HIERARCHYID</span></span>|<span data-ttu-id="9ab39-176">大型对象 (LOB)。</span><span class="sxs-lookup"><span data-stu-id="9ab39-176">Large Objects (LOBs).</span></span> <span data-ttu-id="9ab39-177">例如，varchar(max)、nvarchar(max)、varbinary(max)、image、xml、text 和 ntext。</span><span class="sxs-lookup"><span data-stu-id="9ab39-177">For example, varchar(max), nvarchar(max), varbinary(max), image, xml, text, and ntext.</span></span>|<span data-ttu-id="9ab39-178">ROWVERSION</span><span class="sxs-lookup"><span data-stu-id="9ab39-178">ROWVERSION</span></span>|  
|<span data-ttu-id="9ab39-179">sql_variant</span><span class="sxs-lookup"><span data-stu-id="9ab39-179">sql_variant</span></span>|<span data-ttu-id="9ab39-180">CLR 函数</span><span class="sxs-lookup"><span data-stu-id="9ab39-180">CLR functions</span></span>|<span data-ttu-id="9ab39-181">用户定义类型 (UDT)</span><span class="sxs-lookup"><span data-stu-id="9ab39-181">User-defined types (UDTs)</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="9ab39-182">另请参阅</span><span class="sxs-lookup"><span data-stu-id="9ab39-182">See Also</span></span>  
 <span data-ttu-id="9ab39-183">[对内存中 OLTP 的 Transact-SQL 支持](transact-sql-support-for-in-memory-oltp.md) </span><span class="sxs-lookup"><span data-stu-id="9ab39-183">[Transact-SQL Support for In-Memory OLTP](transact-sql-support-for-in-memory-oltp.md) </span></span>  
 <span data-ttu-id="9ab39-184">[在内存优化表中实现 LOB 列](../../database-engine/implementing-lob-columns-in-a-memory-optimized-table.md) </span><span class="sxs-lookup"><span data-stu-id="9ab39-184">[Implementing LOB Columns in a Memory-Optimized Table](../../database-engine/implementing-lob-columns-in-a-memory-optimized-table.md) </span></span>  
 [<span data-ttu-id="9ab39-185">在内存优化的表中实现 SQL_VARIANT</span><span class="sxs-lookup"><span data-stu-id="9ab39-185">Implementing SQL_VARIANT in a Memory-Optimized Table</span></span>](implementing-sql-variant-in-a-memory-optimized-table.md)  
  
  
