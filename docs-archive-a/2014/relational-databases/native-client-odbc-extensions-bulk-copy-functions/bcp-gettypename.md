---
title: bcp_gettypename |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
api_name:
- bcp_gettypename
api_location:
- sqlncli11.dll
topic_type:
- apiref
helpviewer_keywords:
- bcp_gettypename function
ms.assetid: 65f036d1-f60e-4b8a-97b3-76fccf0dfed4
author: rothja
ms.author: jroth
ms.openlocfilehash: b2d92498b9d863fa2cb700ec4d88868c0984c4d4
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87580253"
---
# <a name="bcp_gettypename"></a><span data-ttu-id="2fe7e-102">bcp_gettypename</span><span class="sxs-lookup"><span data-stu-id="2fe7e-102">bcp_gettypename</span></span>
  <span data-ttu-id="2fe7e-103">返回指定 BCP 类型标记的 SQL 类型名称。</span><span class="sxs-lookup"><span data-stu-id="2fe7e-103">Returns the SQL type name for a specified BCP type token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2fe7e-104">语法</span><span class="sxs-lookup"><span data-stu-id="2fe7e-104">Syntax</span></span>  
  
```  
  
RETCODE bcp_gettypename (  
INT   
token  
,  
DBBOOL   
fIsMaxType  
);  
  
```  
  
## <a name="arguments"></a><span data-ttu-id="2fe7e-105">参数</span><span class="sxs-lookup"><span data-stu-id="2fe7e-105">Arguments</span></span>  
 <span data-ttu-id="2fe7e-106">*token*</span><span class="sxs-lookup"><span data-stu-id="2fe7e-106">*token*</span></span>  
 <span data-ttu-id="2fe7e-107">指示 BCP 类型标记的值。</span><span class="sxs-lookup"><span data-stu-id="2fe7e-107">A value indicating a BCP type token.</span></span>  
  
 <span data-ttu-id="2fe7e-108">*定义域*</span><span class="sxs-lookup"><span data-stu-id="2fe7e-108">*field*</span></span>  
 <span data-ttu-id="2fe7e-109">指示请求的标记是否为 max 类型。</span><span class="sxs-lookup"><span data-stu-id="2fe7e-109">Indicates if token requested is a max type.</span></span>  
  
## <a name="returns"></a><span data-ttu-id="2fe7e-110">返回</span><span class="sxs-lookup"><span data-stu-id="2fe7e-110">Returns</span></span>  
 <span data-ttu-id="2fe7e-111">一个字符串，其中包含与 BCP 类型对应的 SQL 类型名称。</span><span class="sxs-lookup"><span data-stu-id="2fe7e-111">A string containing the SQL type name corresponding to the BCP type.</span></span> <span data-ttu-id="2fe7e-112">如果指定了无效的 BCP 类型，则返回空字符串。</span><span class="sxs-lookup"><span data-stu-id="2fe7e-112">If an invalid BCP type is specified, an empty string is returned..</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="2fe7e-113">备注</span><span class="sxs-lookup"><span data-stu-id="2fe7e-113">Remarks</span></span>  
 <span data-ttu-id="2fe7e-114">BCP 类型标记在 sqlncli.h 头文件和 sqlncli11.lib 库中定义。</span><span class="sxs-lookup"><span data-stu-id="2fe7e-114">The BCP type tokens are defined in the sqlncli.h header file and the sqlncli11.lib library.</span></span>  
  
 <span data-ttu-id="2fe7e-115">下表指定了可能的 BCP 类型、这些类型是否是 max 类型以及预期的输出。</span><span class="sxs-lookup"><span data-stu-id="2fe7e-115">The table below specifies the possible BCP types, whether or not they are max types, and the expected output.</span></span>  
  
|<span data-ttu-id="2fe7e-116">BCP 类型名称</span><span class="sxs-lookup"><span data-stu-id="2fe7e-116">BCP type name</span></span>|<span data-ttu-id="2fe7e-117">MaxType</span><span class="sxs-lookup"><span data-stu-id="2fe7e-117">MaxType</span></span>|<span data-ttu-id="2fe7e-118">Output</span><span class="sxs-lookup"><span data-stu-id="2fe7e-118">Output</span></span>|  
|-------------------|-------------|------------|  
|`SQLDECIMAL`|<span data-ttu-id="2fe7e-119">任一个</span><span class="sxs-lookup"><span data-stu-id="2fe7e-119">Either</span></span>|<span data-ttu-id="2fe7e-120">**decimal**</span><span class="sxs-lookup"><span data-stu-id="2fe7e-120">**decimal**</span></span>|  
|`SQLNUMERIC`|<span data-ttu-id="2fe7e-121">任一个</span><span class="sxs-lookup"><span data-stu-id="2fe7e-121">Either</span></span>|<span data-ttu-id="2fe7e-122">**numeric**</span><span class="sxs-lookup"><span data-stu-id="2fe7e-122">**numeric**</span></span>|  
|`SQLINT1`|<span data-ttu-id="2fe7e-123">任一个</span><span class="sxs-lookup"><span data-stu-id="2fe7e-123">Either</span></span>|<span data-ttu-id="2fe7e-124">**tinyint**</span><span class="sxs-lookup"><span data-stu-id="2fe7e-124">**tinyint**</span></span>|  
|`SQLINT2`|<span data-ttu-id="2fe7e-125">任一个</span><span class="sxs-lookup"><span data-stu-id="2fe7e-125">Either</span></span>|<span data-ttu-id="2fe7e-126">**smallint**</span><span class="sxs-lookup"><span data-stu-id="2fe7e-126">**smallint**</span></span>|  
|`SQLINT4`|<span data-ttu-id="2fe7e-127">任一个</span><span class="sxs-lookup"><span data-stu-id="2fe7e-127">Either</span></span>|<span data-ttu-id="2fe7e-128">**int**</span><span class="sxs-lookup"><span data-stu-id="2fe7e-128">**int**</span></span>|  
|`SQLMONEY`|<span data-ttu-id="2fe7e-129">任一个</span><span class="sxs-lookup"><span data-stu-id="2fe7e-129">Either</span></span>|<span data-ttu-id="2fe7e-130">**money**</span><span class="sxs-lookup"><span data-stu-id="2fe7e-130">**money**</span></span>|  
|`SQLFLT8`|<span data-ttu-id="2fe7e-131">任一个</span><span class="sxs-lookup"><span data-stu-id="2fe7e-131">Either</span></span>|<span data-ttu-id="2fe7e-132">**float**</span><span class="sxs-lookup"><span data-stu-id="2fe7e-132">**float**</span></span>|  
|`SQLDATETIME`|<span data-ttu-id="2fe7e-133">任一个</span><span class="sxs-lookup"><span data-stu-id="2fe7e-133">Either</span></span>|<span data-ttu-id="2fe7e-134">**datetime**</span><span class="sxs-lookup"><span data-stu-id="2fe7e-134">**datetime**</span></span>|  
|`SQLBITN`|<span data-ttu-id="2fe7e-135">任一个</span><span class="sxs-lookup"><span data-stu-id="2fe7e-135">Either</span></span>|<span data-ttu-id="2fe7e-136">**bit-null**</span><span class="sxs-lookup"><span data-stu-id="2fe7e-136">**bit-null**</span></span>|  
|`SQLBIT`|<span data-ttu-id="2fe7e-137">任一个</span><span class="sxs-lookup"><span data-stu-id="2fe7e-137">Either</span></span>|<span data-ttu-id="2fe7e-138">**bit**</span><span class="sxs-lookup"><span data-stu-id="2fe7e-138">**bit**</span></span>|  
|`SQLBIGCHAR`|<span data-ttu-id="2fe7e-139">否</span><span class="sxs-lookup"><span data-stu-id="2fe7e-139">No</span></span>|<span data-ttu-id="2fe7e-140">**char**</span><span class="sxs-lookup"><span data-stu-id="2fe7e-140">**char**</span></span>|  
|`SQLCHARACTER`|<span data-ttu-id="2fe7e-141">否</span><span class="sxs-lookup"><span data-stu-id="2fe7e-141">No</span></span>|<span data-ttu-id="2fe7e-142">**char**</span><span class="sxs-lookup"><span data-stu-id="2fe7e-142">**char**</span></span>|  
|`SQLBIGVARCHAR`|<span data-ttu-id="2fe7e-143">否</span><span class="sxs-lookup"><span data-stu-id="2fe7e-143">No</span></span>|<span data-ttu-id="2fe7e-144">**varchar**</span><span class="sxs-lookup"><span data-stu-id="2fe7e-144">**varchar**</span></span>|  
|`SQLVARCHAR`|<span data-ttu-id="2fe7e-145">否</span><span class="sxs-lookup"><span data-stu-id="2fe7e-145">No</span></span>|<span data-ttu-id="2fe7e-146">**varchar**</span><span class="sxs-lookup"><span data-stu-id="2fe7e-146">**varchar**</span></span>|  
|`SQLTEXT`|<span data-ttu-id="2fe7e-147">任一个</span><span class="sxs-lookup"><span data-stu-id="2fe7e-147">Either</span></span>|<span data-ttu-id="2fe7e-148">**text**</span><span class="sxs-lookup"><span data-stu-id="2fe7e-148">**text**</span></span>|  
|`SQLBIGBINARY`|<span data-ttu-id="2fe7e-149">否</span><span class="sxs-lookup"><span data-stu-id="2fe7e-149">No</span></span>|<span data-ttu-id="2fe7e-150">**binary**</span><span class="sxs-lookup"><span data-stu-id="2fe7e-150">**binary**</span></span>|  
|`SQLBINARY`|<span data-ttu-id="2fe7e-151">否</span><span class="sxs-lookup"><span data-stu-id="2fe7e-151">No</span></span>|<span data-ttu-id="2fe7e-152">**二进制**</span><span class="sxs-lookup"><span data-stu-id="2fe7e-152">**Binary**</span></span>|  
|`SQLBIGVARBINARY`|<span data-ttu-id="2fe7e-153">否</span><span class="sxs-lookup"><span data-stu-id="2fe7e-153">No</span></span>|<span data-ttu-id="2fe7e-154">**Varbinary**</span><span class="sxs-lookup"><span data-stu-id="2fe7e-154">**Varbinary**</span></span>|  
|`SQLVARBINARY`|<span data-ttu-id="2fe7e-155">否</span><span class="sxs-lookup"><span data-stu-id="2fe7e-155">No</span></span>|<span data-ttu-id="2fe7e-156">**Varbinary**</span><span class="sxs-lookup"><span data-stu-id="2fe7e-156">**Varbinary**</span></span>|  
|`SQLIMAGE`|<span data-ttu-id="2fe7e-157">任一个</span><span class="sxs-lookup"><span data-stu-id="2fe7e-157">Either</span></span>|<span data-ttu-id="2fe7e-158">**Image**</span><span class="sxs-lookup"><span data-stu-id="2fe7e-158">**Image**</span></span>|  
|`SQLINTN`|<span data-ttu-id="2fe7e-159">任一个</span><span class="sxs-lookup"><span data-stu-id="2fe7e-159">Either</span></span>|<span data-ttu-id="2fe7e-160">**int-null**</span><span class="sxs-lookup"><span data-stu-id="2fe7e-160">**int-null**</span></span>|  
|`SQLDATETIMN`|<span data-ttu-id="2fe7e-161">任一个</span><span class="sxs-lookup"><span data-stu-id="2fe7e-161">Either</span></span>|<span data-ttu-id="2fe7e-162">**datetime-null**</span><span class="sxs-lookup"><span data-stu-id="2fe7e-162">**datetime-null**</span></span>|  
|`SQLMONEYN`|<span data-ttu-id="2fe7e-163">任一个</span><span class="sxs-lookup"><span data-stu-id="2fe7e-163">Either</span></span>|<span data-ttu-id="2fe7e-164">**money-null**</span><span class="sxs-lookup"><span data-stu-id="2fe7e-164">**money-null**</span></span>|  
|`SQLFLTN`|<span data-ttu-id="2fe7e-165">任一个</span><span class="sxs-lookup"><span data-stu-id="2fe7e-165">Either</span></span>|<span data-ttu-id="2fe7e-166">**float-null**</span><span class="sxs-lookup"><span data-stu-id="2fe7e-166">**float-null**</span></span>|  
|`SQLAOPSUM`|<span data-ttu-id="2fe7e-167">任一个</span><span class="sxs-lookup"><span data-stu-id="2fe7e-167">Either</span></span>|<span data-ttu-id="2fe7e-168">**长度**</span><span class="sxs-lookup"><span data-stu-id="2fe7e-168">**Sum**</span></span>|  
|`SQLAOPAVG`|<span data-ttu-id="2fe7e-169">任一个</span><span class="sxs-lookup"><span data-stu-id="2fe7e-169">Either</span></span>|<span data-ttu-id="2fe7e-170">**Avg**</span><span class="sxs-lookup"><span data-stu-id="2fe7e-170">**Avg**</span></span>|  
|`SQLAOPCNT`|<span data-ttu-id="2fe7e-171">任一个</span><span class="sxs-lookup"><span data-stu-id="2fe7e-171">Either</span></span>|<span data-ttu-id="2fe7e-172">**Count**</span><span class="sxs-lookup"><span data-stu-id="2fe7e-172">**Count**</span></span>|  
|`SQLAOPMIN`|<span data-ttu-id="2fe7e-173">任一个</span><span class="sxs-lookup"><span data-stu-id="2fe7e-173">Either</span></span>|<span data-ttu-id="2fe7e-174">**最小值**</span><span class="sxs-lookup"><span data-stu-id="2fe7e-174">**Min**</span></span>|  
|`SQLAOPMAX`|<span data-ttu-id="2fe7e-175">任一个</span><span class="sxs-lookup"><span data-stu-id="2fe7e-175">Either</span></span>|<span data-ttu-id="2fe7e-176">**最大值**</span><span class="sxs-lookup"><span data-stu-id="2fe7e-176">**Max**</span></span>|  
|`SQLDATETIM4`|<span data-ttu-id="2fe7e-177">任一个</span><span class="sxs-lookup"><span data-stu-id="2fe7e-177">Either</span></span>|<span data-ttu-id="2fe7e-178">**smalldatetime**</span><span class="sxs-lookup"><span data-stu-id="2fe7e-178">**smalldatetime**</span></span>|  
|`SQLMONEY4`|<span data-ttu-id="2fe7e-179">任一个</span><span class="sxs-lookup"><span data-stu-id="2fe7e-179">Either</span></span>|<span data-ttu-id="2fe7e-180">**Smallmoney**</span><span class="sxs-lookup"><span data-stu-id="2fe7e-180">**Smallmoney**</span></span>|  
|`SQLFLT4`|<span data-ttu-id="2fe7e-181">任一个</span><span class="sxs-lookup"><span data-stu-id="2fe7e-181">Either</span></span>|<span data-ttu-id="2fe7e-182">**实际上**</span><span class="sxs-lookup"><span data-stu-id="2fe7e-182">**Real**</span></span>|  
|`SQLUNIQUEID`|<span data-ttu-id="2fe7e-183">任一个</span><span class="sxs-lookup"><span data-stu-id="2fe7e-183">Either</span></span>|<span data-ttu-id="2fe7e-184">**uniqueidentifier**</span><span class="sxs-lookup"><span data-stu-id="2fe7e-184">**uniqueidentifier**</span></span>|  
|`SQLNCHAR`|<span data-ttu-id="2fe7e-185">否</span><span class="sxs-lookup"><span data-stu-id="2fe7e-185">No</span></span>|<span data-ttu-id="2fe7e-186">**Nchar**</span><span class="sxs-lookup"><span data-stu-id="2fe7e-186">**Nchar**</span></span>|  
|`SQLNVARCHAR`|<span data-ttu-id="2fe7e-187">否</span><span class="sxs-lookup"><span data-stu-id="2fe7e-187">No</span></span>|<span data-ttu-id="2fe7e-188">**Nvarchar**</span><span class="sxs-lookup"><span data-stu-id="2fe7e-188">**Nvarchar**</span></span>|  
|`SQLNTEXT`|<span data-ttu-id="2fe7e-189">任一个</span><span class="sxs-lookup"><span data-stu-id="2fe7e-189">Either</span></span>|<span data-ttu-id="2fe7e-190">**Ntext**</span><span class="sxs-lookup"><span data-stu-id="2fe7e-190">**Ntext**</span></span>|  
|`SQLVARIANT`|<span data-ttu-id="2fe7e-191">任一个</span><span class="sxs-lookup"><span data-stu-id="2fe7e-191">Either</span></span>|<span data-ttu-id="2fe7e-192">**sql_variant**</span><span class="sxs-lookup"><span data-stu-id="2fe7e-192">**sql_variant**</span></span>|  
|`SQLINT8`|<span data-ttu-id="2fe7e-193">任一个</span><span class="sxs-lookup"><span data-stu-id="2fe7e-193">Either</span></span>|<span data-ttu-id="2fe7e-194">**Bigint**</span><span class="sxs-lookup"><span data-stu-id="2fe7e-194">**Bigint**</span></span>|  
|`SQLCHARACTER`|<span data-ttu-id="2fe7e-195">是</span><span class="sxs-lookup"><span data-stu-id="2fe7e-195">Yes</span></span>|<span data-ttu-id="2fe7e-196">**varchar(max)**</span><span class="sxs-lookup"><span data-stu-id="2fe7e-196">**varchar(max)**</span></span>|  
|`SQLBIGCHAR`|<span data-ttu-id="2fe7e-197">是</span><span class="sxs-lookup"><span data-stu-id="2fe7e-197">Yes</span></span>|<span data-ttu-id="2fe7e-198">**varchar(max)**</span><span class="sxs-lookup"><span data-stu-id="2fe7e-198">**varchar(max)**</span></span>|  
|`SQLBIGVARCHAR`|<span data-ttu-id="2fe7e-199">是</span><span class="sxs-lookup"><span data-stu-id="2fe7e-199">Yes</span></span>|<span data-ttu-id="2fe7e-200">**varchar(max)**</span><span class="sxs-lookup"><span data-stu-id="2fe7e-200">**varchar(max)**</span></span>|  
|`SQLVARCHAR`|<span data-ttu-id="2fe7e-201">是</span><span class="sxs-lookup"><span data-stu-id="2fe7e-201">Yes</span></span>|<span data-ttu-id="2fe7e-202">**varchar(max)**</span><span class="sxs-lookup"><span data-stu-id="2fe7e-202">**varchar(max)**</span></span>|  
|`SQLBINARY`|<span data-ttu-id="2fe7e-203">是</span><span class="sxs-lookup"><span data-stu-id="2fe7e-203">Yes</span></span>|<span data-ttu-id="2fe7e-204">**varbinary(max)**</span><span class="sxs-lookup"><span data-stu-id="2fe7e-204">**varbinary(max)**</span></span>|  
|`SQLBIGBINARY`|<span data-ttu-id="2fe7e-205">是</span><span class="sxs-lookup"><span data-stu-id="2fe7e-205">Yes</span></span>|<span data-ttu-id="2fe7e-206">**varbinary(max)**</span><span class="sxs-lookup"><span data-stu-id="2fe7e-206">**varbinary(max)**</span></span>|  
|`SQLBIGVARBINARY`|<span data-ttu-id="2fe7e-207">是</span><span class="sxs-lookup"><span data-stu-id="2fe7e-207">Yes</span></span>|<span data-ttu-id="2fe7e-208">**varbinary(max)**</span><span class="sxs-lookup"><span data-stu-id="2fe7e-208">**varbinary(max)**</span></span>|  
|`SQLVARBINARY`|<span data-ttu-id="2fe7e-209">是</span><span class="sxs-lookup"><span data-stu-id="2fe7e-209">Yes</span></span>|<span data-ttu-id="2fe7e-210">**varbinary(max)**</span><span class="sxs-lookup"><span data-stu-id="2fe7e-210">**varbinary(max)**</span></span>|  
|`SQLNCHAR`|<span data-ttu-id="2fe7e-211">是</span><span class="sxs-lookup"><span data-stu-id="2fe7e-211">Yes</span></span>|<span data-ttu-id="2fe7e-212">**nvarchar(max)**</span><span class="sxs-lookup"><span data-stu-id="2fe7e-212">**nvarchar(max)**</span></span>|  
|`SQLNVARCHAR`|<span data-ttu-id="2fe7e-213">是</span><span class="sxs-lookup"><span data-stu-id="2fe7e-213">Yes</span></span>|<span data-ttu-id="2fe7e-214">**nvarchar(max)**</span><span class="sxs-lookup"><span data-stu-id="2fe7e-214">**nvarchar(max)**</span></span>|  
|`SQLXML`|<span data-ttu-id="2fe7e-215">是</span><span class="sxs-lookup"><span data-stu-id="2fe7e-215">Yes</span></span>|<span data-ttu-id="2fe7e-216">**Xml**</span><span class="sxs-lookup"><span data-stu-id="2fe7e-216">**Xml**</span></span>|  
|`SQLUDT`|<span data-ttu-id="2fe7e-217">任一个</span><span class="sxs-lookup"><span data-stu-id="2fe7e-217">Either</span></span>|<span data-ttu-id="2fe7e-218">**Udt**</span><span class="sxs-lookup"><span data-stu-id="2fe7e-218">**Udt**</span></span>|  
  
## <a name="bcp_gettypename-support-for-enhanced-date-and-time-features"></a><span data-ttu-id="2fe7e-219">bcp_gettypename 对日期和时间增强功能的支持</span><span class="sxs-lookup"><span data-stu-id="2fe7e-219">bcp_gettypename Support for Enhanced Date and Time Features</span></span>  
 <span data-ttu-id="2fe7e-220">有关日期/时间类型的令牌参数值，请参阅 sqlncli.msi [OLE DB 和 ODBC&#41;的增强日期和时间 &#40;类型的大容量复制更改](../native-client-odbc-date-time/bulk-copy-changes-for-enhanced-date-and-time-types-ole-db-and-odbc.md)中表的 "Type in" 列。</span><span class="sxs-lookup"><span data-stu-id="2fe7e-220">The token parameter values for date/time types are described in the "Type in sqlncli.h" column of the table in [Bulk Copy Changes for Enhanced Date and Time Types &#40;OLE DB and ODBC&#41;](../native-client-odbc-date-time/bulk-copy-changes-for-enhanced-date-and-time-types-ole-db-and-odbc.md).</span></span> <span data-ttu-id="2fe7e-221">返回值位于“文件存储类型”列的对应行中。</span><span class="sxs-lookup"><span data-stu-id="2fe7e-221">The returned value is in the corresponding row of the "File storage type" column.</span></span>  
  
 <span data-ttu-id="2fe7e-222">有关详细信息，请参阅[ODBC&#41;&#40;日期和时间改进](../native-client-odbc-date-time/date-and-time-improvements-odbc.md)。</span><span class="sxs-lookup"><span data-stu-id="2fe7e-222">For more information, see [Date and Time Improvements &#40;ODBC&#41;](../native-client-odbc-date-time/date-and-time-improvements-odbc.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2fe7e-223">另请参阅</span><span class="sxs-lookup"><span data-stu-id="2fe7e-223">See Also</span></span>  
 [<span data-ttu-id="2fe7e-224">大容量复制函数</span><span class="sxs-lookup"><span data-stu-id="2fe7e-224">Bulk Copy Functions</span></span>](sql-server-driver-extensions-bulk-copy-functions.md)  
  
  
