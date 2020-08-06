---
title: 数据类型（扩展存储过程 API）| Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: stored-procedures
ms.topic: reference
helpviewer_keywords:
- extended stored procedures [SQL Server], data types
- data types [SQL Server], extended stored procedures
ms.assetid: 37fb86b9-8819-4387-bcdc-9616968e15ad
author: rothja
ms.author: jroth
ms.openlocfilehash: aae0c6f2b309d182a93274171d2f8c21344fe3b0
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87576759"
---
# <a name="data-types-extended-stored-procedure-api"></a><span data-ttu-id="12e12-102">数据类型（扩展存储过程 API）</span><span class="sxs-lookup"><span data-stu-id="12e12-102">Data Types (Extended Stored Procedure API)</span></span>
    
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureDontUse](../../includes/ssnotedepfuturedontuse-md.md)]<span data-ttu-id="12e12-103">请改用 CLR 集成。</span><span class="sxs-lookup"><span data-stu-id="12e12-103">Use CLR integration instead.</span></span>  
  
 <span data-ttu-id="12e12-104">若要使用扩展存储过程 API 数据类型，请在程序中包括 Srv.h 头文件。</span><span class="sxs-lookup"><span data-stu-id="12e12-104">To use the Extended Stored Procedure API data types, include the Srv.h header file in your program.</span></span>  
  
|<span data-ttu-id="12e12-105">数据类型</span><span class="sxs-lookup"><span data-stu-id="12e12-105">Data type</span></span>|<span data-ttu-id="12e12-106">SQL Server 数据类型</span><span class="sxs-lookup"><span data-stu-id="12e12-106">SQL Server data type</span></span>|<span data-ttu-id="12e12-107">说明</span><span class="sxs-lookup"><span data-stu-id="12e12-107">Description</span></span>|  
|---------------|--------------------------|-----------------|  
|<span data-ttu-id="12e12-108">SRVBIGBINARY</span><span class="sxs-lookup"><span data-stu-id="12e12-108">SRVBIGBINARY</span></span>|`binary`|<span data-ttu-id="12e12-109">`binary` 数据类型，长度为 0 至 8000 个字节。</span><span class="sxs-lookup"><span data-stu-id="12e12-109">`binary` data type, length 0 to 8000 bytes.</span></span>|  
|<span data-ttu-id="12e12-110">SRVBIGCHAR</span><span class="sxs-lookup"><span data-stu-id="12e12-110">SRVBIGCHAR</span></span>|`char`|<span data-ttu-id="12e12-111">`character` 数据类型，长度为 0 至 8000 个字节。</span><span class="sxs-lookup"><span data-stu-id="12e12-111">`character` data type, length 0 to 8000 bytes.</span></span>|  
|<span data-ttu-id="12e12-112">SRVBIGVARBINARY</span><span class="sxs-lookup"><span data-stu-id="12e12-112">SRVBIGVARBINARY</span></span>|`varbinary`|<span data-ttu-id="12e12-113">长度可变的 `binary` 数据类型，长度为 0 至 8000 个字节。</span><span class="sxs-lookup"><span data-stu-id="12e12-113">Variable-length `binary` data type, length 0 to 8000 bytes.</span></span>|  
|<span data-ttu-id="12e12-114">SRVBIGVARCHAR</span><span class="sxs-lookup"><span data-stu-id="12e12-114">SRVBIGVARCHAR</span></span>|`varchar`|<span data-ttu-id="12e12-115">长度可变的 `character` 数据类型，长度为 0 至 8000 个字节。</span><span class="sxs-lookup"><span data-stu-id="12e12-115">Variable-length `character` data type, length 0 to 8000 bytes.</span></span>|  
|<span data-ttu-id="12e12-116">SRVBINARY</span><span class="sxs-lookup"><span data-stu-id="12e12-116">SRVBINARY</span></span>|`binary`|<span data-ttu-id="12e12-117">`binary`数据类型。</span><span class="sxs-lookup"><span data-stu-id="12e12-117">`binary` data type.</span></span>|  
|<span data-ttu-id="12e12-118">SRVBIT</span><span class="sxs-lookup"><span data-stu-id="12e12-118">SRVBIT</span></span>|`Bit`|<span data-ttu-id="12e12-119">`bit`数据类型。</span><span class="sxs-lookup"><span data-stu-id="12e12-119">`bit` data type.</span></span>|  
|<span data-ttu-id="12e12-120">SRVBITN</span><span class="sxs-lookup"><span data-stu-id="12e12-120">SRVBITN</span></span>|`bit null`|<span data-ttu-id="12e12-121">`bit` 数据类型，允许为 Null 值。</span><span class="sxs-lookup"><span data-stu-id="12e12-121">`bit` data type, null values allowed.</span></span>|  
|<span data-ttu-id="12e12-122">SRVCHAR</span><span class="sxs-lookup"><span data-stu-id="12e12-122">SRVCHAR</span></span>|`char`|<span data-ttu-id="12e12-123">`character`数据类型。</span><span class="sxs-lookup"><span data-stu-id="12e12-123">`character` data type.</span></span>|  
|<span data-ttu-id="12e12-124">SRVDATETIME</span><span class="sxs-lookup"><span data-stu-id="12e12-124">SRVDATETIME</span></span>|`datetime`|<span data-ttu-id="12e12-125">8 个字节的 `datetime` 数据类型。</span><span class="sxs-lookup"><span data-stu-id="12e12-125">8-byte `datetime` data type.</span></span>|  
|<span data-ttu-id="12e12-126">SRVDATETIM4</span><span class="sxs-lookup"><span data-stu-id="12e12-126">SRVDATETIM4</span></span>|`smalldatetime`|<span data-ttu-id="12e12-127">4个字节的 `smalldatetime` 数据类型。</span><span class="sxs-lookup"><span data-stu-id="12e12-127">4-byte `smalldatetime` data type.</span></span>|  
|<span data-ttu-id="12e12-128">SRVDATETIMN</span><span class="sxs-lookup"><span data-stu-id="12e12-128">SRVDATETIMN</span></span>|<span data-ttu-id="12e12-129">**datetime null**</span><span class="sxs-lookup"><span data-stu-id="12e12-129">**datetime null**</span></span>|<span data-ttu-id="12e12-130">`smalldatetime` 或 `datetime` 数据类型，允许为 Null 值。</span><span class="sxs-lookup"><span data-stu-id="12e12-130">`smalldatetime` or `datetime` data type, null values allowed.</span></span>|  
|<span data-ttu-id="12e12-131">SRVDECIMAL</span><span class="sxs-lookup"><span data-stu-id="12e12-131">SRVDECIMAL</span></span>|`decimal`|<span data-ttu-id="12e12-132">`decimal`数据类型。</span><span class="sxs-lookup"><span data-stu-id="12e12-132">`decimal` data type.</span></span>|  
|<span data-ttu-id="12e12-133">SRVDECIMALN</span><span class="sxs-lookup"><span data-stu-id="12e12-133">SRVDECIMALN</span></span>|`decimal null`|<span data-ttu-id="12e12-134">`decimal` 数据类型，允许为 Null 值。</span><span class="sxs-lookup"><span data-stu-id="12e12-134">`decimal` data type, null values allowed.</span></span>|  
|<span data-ttu-id="12e12-135">SRVFLT4</span><span class="sxs-lookup"><span data-stu-id="12e12-135">SRVFLT4</span></span>|`real`|<span data-ttu-id="12e12-136">4个字节的 `real` 数据类型。</span><span class="sxs-lookup"><span data-stu-id="12e12-136">4-byte `real` data type.</span></span>|  
|<span data-ttu-id="12e12-137">SRVFLT8</span><span class="sxs-lookup"><span data-stu-id="12e12-137">SRVFLT8</span></span>|`float`|<span data-ttu-id="12e12-138">8 个字节的 `float` 数据类型。</span><span class="sxs-lookup"><span data-stu-id="12e12-138">8-byte `float` data type.</span></span>|  
|<span data-ttu-id="12e12-139">SRVFLTN</span><span class="sxs-lookup"><span data-stu-id="12e12-139">SRVFLTN</span></span>|<span data-ttu-id="12e12-140">`real` &#124; `float null`</span><span class="sxs-lookup"><span data-stu-id="12e12-140">`real` &#124; `float null`</span></span>|<span data-ttu-id="12e12-141">`real` 或 `float` 数据类型，允许为 Null 值。</span><span class="sxs-lookup"><span data-stu-id="12e12-141">`real` or `float` data type, null values allowed.</span></span>|  
|<span data-ttu-id="12e12-142">SRVIMAGE</span><span class="sxs-lookup"><span data-stu-id="12e12-142">SRVIMAGE</span></span>|`image`|<span data-ttu-id="12e12-143">`image`数据类型。</span><span class="sxs-lookup"><span data-stu-id="12e12-143">`image` data type.</span></span>|  
|<span data-ttu-id="12e12-144">SRVINT1</span><span class="sxs-lookup"><span data-stu-id="12e12-144">SRVINT1</span></span>|`tinyint`|<span data-ttu-id="12e12-145">1个字节的 `tinyint` 数据类型。</span><span class="sxs-lookup"><span data-stu-id="12e12-145">1-byte `tinyint` data type.</span></span>|  
|<span data-ttu-id="12e12-146">SRVINT2</span><span class="sxs-lookup"><span data-stu-id="12e12-146">SRVINT2</span></span>|`smallint`|<span data-ttu-id="12e12-147">两个字节的 `smallint` 数据类型。</span><span class="sxs-lookup"><span data-stu-id="12e12-147">2-byte `smallint` data type.</span></span>|  
|<span data-ttu-id="12e12-148">SRVINT4</span><span class="sxs-lookup"><span data-stu-id="12e12-148">SRVINT4</span></span>|`int`|<span data-ttu-id="12e12-149">4个字节的 `int` 数据类型。</span><span class="sxs-lookup"><span data-stu-id="12e12-149">4-byte `int` data type.</span></span>|  
|<span data-ttu-id="12e12-150">SRVINTN</span><span class="sxs-lookup"><span data-stu-id="12e12-150">SRVINTN</span></span>|<span data-ttu-id="12e12-151">`tinyint` &#124; `smallint` &#124; `int null`</span><span class="sxs-lookup"><span data-stu-id="12e12-151">`tinyint` &#124; `smallint` &#124; `int null`</span></span>|<span data-ttu-id="12e12-152">`tinyint`、`smallint` 或 `int` 数据类型，允许为 Null 值。</span><span class="sxs-lookup"><span data-stu-id="12e12-152">`tinyint`, `smallint`, or `int` data type, null values allowed.</span></span>|  
|<span data-ttu-id="12e12-153">SRVMONEY4</span><span class="sxs-lookup"><span data-stu-id="12e12-153">SRVMONEY4</span></span>|`smallmoney`|<span data-ttu-id="12e12-154">4个字节的 `smallmoney` 数据类型。</span><span class="sxs-lookup"><span data-stu-id="12e12-154">4-byte `smallmoney` data type.</span></span>|  
|<span data-ttu-id="12e12-155">SRVMONEY</span><span class="sxs-lookup"><span data-stu-id="12e12-155">SRVMONEY</span></span>|`money`|<span data-ttu-id="12e12-156">8 个字节的 `money` 数据类型。</span><span class="sxs-lookup"><span data-stu-id="12e12-156">8-byte `money` data type.</span></span>|  
|<span data-ttu-id="12e12-157">SRVMONEYN</span><span class="sxs-lookup"><span data-stu-id="12e12-157">SRVMONEYN</span></span>|<span data-ttu-id="12e12-158">`money` &#124; `smallmoney null`</span><span class="sxs-lookup"><span data-stu-id="12e12-158">`money` &#124; `smallmoney null`</span></span>|<span data-ttu-id="12e12-159">`smallmoney` 或 `money` 数据类型，允许为 Null 值。</span><span class="sxs-lookup"><span data-stu-id="12e12-159">`smallmoney` or `money` data type, null values allowed.</span></span>|  
|<span data-ttu-id="12e12-160">SRVNCHAR</span><span class="sxs-lookup"><span data-stu-id="12e12-160">SRVNCHAR</span></span>|<span data-ttu-id="12e12-161">**nchar**</span><span class="sxs-lookup"><span data-stu-id="12e12-161">**nchar**</span></span>|<span data-ttu-id="12e12-162">Unicode `character` 数据类型。</span><span class="sxs-lookup"><span data-stu-id="12e12-162">Unicode `character` data type.</span></span>|  
|<span data-ttu-id="12e12-163">SRVNTEXT</span><span class="sxs-lookup"><span data-stu-id="12e12-163">SRVNTEXT</span></span>|`ntext`|<span data-ttu-id="12e12-164">Unicode `text` 数据类型。</span><span class="sxs-lookup"><span data-stu-id="12e12-164">Unicode `text` data type.</span></span>|  
|<span data-ttu-id="12e12-165">SRVNUMERIC</span><span class="sxs-lookup"><span data-stu-id="12e12-165">SRVNUMERIC</span></span>|`numeric`|<span data-ttu-id="12e12-166">`numeric`数据类型。</span><span class="sxs-lookup"><span data-stu-id="12e12-166">`numeric` data type.</span></span>|  
|<span data-ttu-id="12e12-167">SRVNUMERICN</span><span class="sxs-lookup"><span data-stu-id="12e12-167">SRVNUMERICN</span></span>|`numeric null`|<span data-ttu-id="12e12-168">`numeric` 数据类型，允许为 Null 值。</span><span class="sxs-lookup"><span data-stu-id="12e12-168">`numeric` data type, null values allowed.</span></span>|  
|<span data-ttu-id="12e12-169">SRVNVARCHAR</span><span class="sxs-lookup"><span data-stu-id="12e12-169">SRVNVARCHAR</span></span>|<span data-ttu-id="12e12-170">**nvarchar**</span><span class="sxs-lookup"><span data-stu-id="12e12-170">**nvarchar**</span></span>|<span data-ttu-id="12e12-171">长度可变的 Unicode `character` 数据类型。</span><span class="sxs-lookup"><span data-stu-id="12e12-171">Unicode variable-length `character` data type.</span></span>|  
|<span data-ttu-id="12e12-172">SRVTEXT</span><span class="sxs-lookup"><span data-stu-id="12e12-172">SRVTEXT</span></span>|`text`|<span data-ttu-id="12e12-173">`text`数据类型。</span><span class="sxs-lookup"><span data-stu-id="12e12-173">`text` data type.</span></span>|  
|<span data-ttu-id="12e12-174">SRVVARBINARY</span><span class="sxs-lookup"><span data-stu-id="12e12-174">SRVVARBINARY</span></span>|`varbinary`|<span data-ttu-id="12e12-175">长度可变的 `binary` 数据类型。</span><span class="sxs-lookup"><span data-stu-id="12e12-175">Variable-length `binary` data type.</span></span>|  
|<span data-ttu-id="12e12-176">SRVVARCHAR</span><span class="sxs-lookup"><span data-stu-id="12e12-176">SRVVARCHAR</span></span>|`varchar`|<span data-ttu-id="12e12-177">长度可变的 `character` 数据类型。</span><span class="sxs-lookup"><span data-stu-id="12e12-177">Variable-length `character` data type.</span></span>|  
  
> [!IMPORTANT]  
>  <span data-ttu-id="12e12-178">应全面检查扩展存储过程的源代码，并在生产服务器中安装编译的 DLL 之前，对这些 DLL 进行测试。</span><span class="sxs-lookup"><span data-stu-id="12e12-178">You should thoroughly review the source code of extended stored procedures, and you should test the compiled DLLs before you install them on a production server.</span></span> <span data-ttu-id="12e12-179">有关安全检查和测试的信息，请访问此 [Microsoft 网站](https://go.microsoft.com/fwlink/?LinkID=54761&amp;clcid=0x409https://msdn.microsoft.com/security/)。</span><span class="sxs-lookup"><span data-stu-id="12e12-179">For information about security review and testing, see this [Microsoft Web site](https://go.microsoft.com/fwlink/?LinkID=54761&amp;clcid=0x409https://msdn.microsoft.com/security/).</span></span>  
  
  
