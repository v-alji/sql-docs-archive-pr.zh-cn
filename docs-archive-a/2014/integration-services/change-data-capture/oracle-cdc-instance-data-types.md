---
title: Oracle CDC 实例数据类型 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: eec13d8d-c15a-4542-bfc4-da66b1a6bfe0
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 71d4ce02db89c1bfd11fe9a3a3535fc92fbc49fc
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87683007"
---
# <a name="oracle-cdc-instance-data-types"></a><span data-ttu-id="92b9f-102">Oracle CDC 实例数据类型</span><span class="sxs-lookup"><span data-stu-id="92b9f-102">Oracle CDC Instance Data Types</span></span>
  <span data-ttu-id="92b9f-103">Oracle CDC 实例支持大多数 Oracle 数据类型。</span><span class="sxs-lookup"><span data-stu-id="92b9f-103">The Oracle CDC Instance supports most Oracle data types.</span></span> <span data-ttu-id="92b9f-104">下面的部分介绍支持的数据类型和不支持的数据类型。</span><span class="sxs-lookup"><span data-stu-id="92b9f-104">The following sections describe the supported data types and the non-supported data types.</span></span>  
  
## <a name="supported-data-types"></a><span data-ttu-id="92b9f-105">支持的数据类型</span><span class="sxs-lookup"><span data-stu-id="92b9f-105">Supported Data Types</span></span>  
 <span data-ttu-id="92b9f-106">下表介绍可捕获的 Oracle 数据类型及其与更改表中 SQL Server 数据类型的默认映射。</span><span class="sxs-lookup"><span data-stu-id="92b9f-106">The following table describes the Oracle data types that can be captured and their default mapping to SQL Server data types in the change tables.</span></span> <span data-ttu-id="92b9f-107">在为源 Oracle 表添加捕获实例时，您可以覆盖其中某些映射。</span><span class="sxs-lookup"><span data-stu-id="92b9f-107">When adding a capture instance for a source Oracle table, you can override some of these mappings.</span></span>  
  
|<span data-ttu-id="92b9f-108">Oracle 数据库数据类型</span><span class="sxs-lookup"><span data-stu-id="92b9f-108">Oracle Database Data Type</span></span>|<span data-ttu-id="92b9f-109">SQL Server 数据类型</span><span class="sxs-lookup"><span data-stu-id="92b9f-109">SQL Server Data Type</span></span>|  
|-------------------------------|--------------------------|  
|<span data-ttu-id="92b9f-110">BINARY_FLOAT</span><span class="sxs-lookup"><span data-stu-id="92b9f-110">BINARY_FLOAT</span></span>|<span data-ttu-id="92b9f-111">real</span><span class="sxs-lookup"><span data-stu-id="92b9f-111">REAL</span></span>|  
|<span data-ttu-id="92b9f-112">BINARY_DOUBLE</span><span class="sxs-lookup"><span data-stu-id="92b9f-112">BINARY_DOUBLE</span></span>|<span data-ttu-id="92b9f-113">FLOAT</span><span class="sxs-lookup"><span data-stu-id="92b9f-113">FLOAT</span></span>|  
|<span data-ttu-id="92b9f-114">CHAR</span><span class="sxs-lookup"><span data-stu-id="92b9f-114">CHAR</span></span>|<span data-ttu-id="92b9f-115">NVARCHAR</span><span class="sxs-lookup"><span data-stu-id="92b9f-115">NVARCHAR</span></span>|  
|<span data-ttu-id="92b9f-116">DATE</span><span class="sxs-lookup"><span data-stu-id="92b9f-116">DATE</span></span>|<span data-ttu-id="92b9f-117">DATETIME</span><span class="sxs-lookup"><span data-stu-id="92b9f-117">DATETIME</span></span>|  
|<span data-ttu-id="92b9f-118">FLOAT</span><span class="sxs-lookup"><span data-stu-id="92b9f-118">FLOAT</span></span>|<span data-ttu-id="92b9f-119">FLOAT</span><span class="sxs-lookup"><span data-stu-id="92b9f-119">FLOAT</span></span>|  
|<span data-ttu-id="92b9f-120">INT</span><span class="sxs-lookup"><span data-stu-id="92b9f-120">INT</span></span>|<span data-ttu-id="92b9f-121">NUMERIC (38)</span><span class="sxs-lookup"><span data-stu-id="92b9f-121">NUMERIC (38)</span></span>|  
|<span data-ttu-id="92b9f-122">INTERVAL</span><span class="sxs-lookup"><span data-stu-id="92b9f-122">INTERVAL</span></span>|<span data-ttu-id="92b9f-123">DATETIME</span><span class="sxs-lookup"><span data-stu-id="92b9f-123">DATETIME</span></span>|  
|<span data-ttu-id="92b9f-124">NCHAR</span><span class="sxs-lookup"><span data-stu-id="92b9f-124">NCHAR</span></span>|<span data-ttu-id="92b9f-125">NVARCHAR</span><span class="sxs-lookup"><span data-stu-id="92b9f-125">NVARCHAR</span></span>|  
|<span data-ttu-id="92b9f-126">NUMBER</span><span class="sxs-lookup"><span data-stu-id="92b9f-126">NUMBER</span></span>|<span data-ttu-id="92b9f-127">FLOAT</span><span class="sxs-lookup"><span data-stu-id="92b9f-127">FLOAT</span></span>|  
|<span data-ttu-id="92b9f-128">NAVARCHAR2</span><span class="sxs-lookup"><span data-stu-id="92b9f-128">NAVARCHAR2</span></span>|<span data-ttu-id="92b9f-129">NVARCHAR</span><span class="sxs-lookup"><span data-stu-id="92b9f-129">NVARCHAR</span></span>|  
|<span data-ttu-id="92b9f-130">RAW</span><span class="sxs-lookup"><span data-stu-id="92b9f-130">RAW</span></span>|<span data-ttu-id="92b9f-131">VARBINARY</span><span class="sxs-lookup"><span data-stu-id="92b9f-131">VARBINARY</span></span>|  
|<span data-ttu-id="92b9f-132">real</span><span class="sxs-lookup"><span data-stu-id="92b9f-132">REAL</span></span>|<span data-ttu-id="92b9f-133">FLOAT</span><span class="sxs-lookup"><span data-stu-id="92b9f-133">FLOAT</span></span>|  
|<span data-ttu-id="92b9f-134">TIMESTAMP</span><span class="sxs-lookup"><span data-stu-id="92b9f-134">TIMESTAMP</span></span>|<span data-ttu-id="92b9f-135">DATETIME2</span><span class="sxs-lookup"><span data-stu-id="92b9f-135">DATETIME2</span></span>|  
|<span data-ttu-id="92b9f-136">TIMESTAMP WITH TIME ZONE</span><span class="sxs-lookup"><span data-stu-id="92b9f-136">TIMESTAMP WITH TIME ZONE</span></span>|<span data-ttu-id="92b9f-137">VARCHAR (37)</span><span class="sxs-lookup"><span data-stu-id="92b9f-137">VARCHAR (37)</span></span>|  
|<span data-ttu-id="92b9f-138">TIMESTAMP WITH LOCAL TIME ZONE</span><span class="sxs-lookup"><span data-stu-id="92b9f-138">TIMESTAMP WITH LOCAL TIME ZONE</span></span>|<span data-ttu-id="92b9f-139">VARCHAR (37)</span><span class="sxs-lookup"><span data-stu-id="92b9f-139">VARCHAR (37)</span></span>|  
|<span data-ttu-id="92b9f-140">VARCHAR2</span><span class="sxs-lookup"><span data-stu-id="92b9f-140">VARCHAR2</span></span>|<span data-ttu-id="92b9f-141">VARCHAR</span><span class="sxs-lookup"><span data-stu-id="92b9f-141">VARCHAR</span></span>|  
|<span data-ttu-id="92b9f-142">XMLTYPE</span><span class="sxs-lookup"><span data-stu-id="92b9f-142">XMLTYPE</span></span>|<span data-ttu-id="92b9f-143">NVARCHAR (MAX)</span><span class="sxs-lookup"><span data-stu-id="92b9f-143">NVARCHAR (MAX)</span></span>|  
  
## <a name="non-supported-data-types"></a><span data-ttu-id="92b9f-144">不支持的数据类型</span><span class="sxs-lookup"><span data-stu-id="92b9f-144">Non-Supported Data Types</span></span>  
 <span data-ttu-id="92b9f-145">无法捕获含以下 Oracle 数据类型的列的源 Oracle 表。</span><span class="sxs-lookup"><span data-stu-id="92b9f-145">Source Oracle tables with columns of the following Oracle data types cannot be captured.</span></span> <span data-ttu-id="92b9f-146">具有这些数据类型的捕获列将显示为 Null；但是，其值中的更改将在捕获表的更改掩码中指示。</span><span class="sxs-lookup"><span data-stu-id="92b9f-146">Captured columns with these data types will show as null; however, a change in their value is indicated in the change mask of the captured tables.</span></span>  
  
-   <span data-ttu-id="92b9f-147">LONG</span><span class="sxs-lookup"><span data-stu-id="92b9f-147">LONG</span></span>  
  
-   <span data-ttu-id="92b9f-148">XMLTYPE</span><span class="sxs-lookup"><span data-stu-id="92b9f-148">XMLTYPE</span></span>  
  
-   <span data-ttu-id="92b9f-149">BLOB</span><span class="sxs-lookup"><span data-stu-id="92b9f-149">BLOB</span></span>  
  
-   <span data-ttu-id="92b9f-150">CLOB</span><span class="sxs-lookup"><span data-stu-id="92b9f-150">CLOB</span></span>  
  
 <span data-ttu-id="92b9f-151">无法捕获含以下 Oracle 数据类型的列的源 Oracle 表。</span><span class="sxs-lookup"><span data-stu-id="92b9f-151">Source Oracle tables with columns of the following Oracle data types cannot be captured.</span></span>  
  
-   <span data-ttu-id="92b9f-152">BFILE</span><span class="sxs-lookup"><span data-stu-id="92b9f-152">BFILE</span></span>  
  
-   <span data-ttu-id="92b9f-153">ROWID</span><span class="sxs-lookup"><span data-stu-id="92b9f-153">ROWID</span></span>  
  
-   <span data-ttu-id="92b9f-154">REF</span><span class="sxs-lookup"><span data-stu-id="92b9f-154">REF</span></span>  
  
-   <span data-ttu-id="92b9f-155">UROWID</span><span class="sxs-lookup"><span data-stu-id="92b9f-155">UROWID</span></span>  
  
-   <span data-ttu-id="92b9f-156">嵌套表</span><span class="sxs-lookup"><span data-stu-id="92b9f-156">Nested Table</span></span>  
  
 <span data-ttu-id="92b9f-157">如果在表中存在以下数据类型，则它们将阻止 LogMinder 获取任何表列的任何数据：</span><span class="sxs-lookup"><span data-stu-id="92b9f-157">If the following data types are present in a table they will prevent the LogMinder from getting any data for any column of the table:</span></span>  
  
-   <span data-ttu-id="92b9f-158">用户定义数据类型</span><span class="sxs-lookup"><span data-stu-id="92b9f-158">User-defined data types</span></span>  
  
-   <span data-ttu-id="92b9f-159">VARRAY</span><span class="sxs-lookup"><span data-stu-id="92b9f-159">VARRAY</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="92b9f-160">另请参阅</span><span class="sxs-lookup"><span data-stu-id="92b9f-160">See Also</span></span>  
 <span data-ttu-id="92b9f-161">[Change Data Capture Designer for Oracle by Attunity](change-data-capture-designer-for-oracle-by-attunity.md) </span><span class="sxs-lookup"><span data-stu-id="92b9f-161">[Change Data Capture Designer for Oracle by Attunity](change-data-capture-designer-for-oracle-by-attunity.md) </span></span>  
 [<span data-ttu-id="92b9f-162">Oracle CDC 实例</span><span class="sxs-lookup"><span data-stu-id="92b9f-162">The Oracle CDC Instance</span></span>](the-oracle-cdc-instance.md)  
  
  
