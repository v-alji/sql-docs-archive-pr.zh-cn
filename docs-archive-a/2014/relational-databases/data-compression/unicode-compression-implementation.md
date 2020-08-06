---
title: Unicode 压缩的实现 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: performance
ms.topic: conceptual
helpviewer_keywords:
- Unicode data compression
- compression [SQL Server], Unicode data
ms.assetid: 44e69e60-9b35-43fe-b9c7-8cf34eaea62a
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 4c928062169ed7feb03f1031362530474109976a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87589690"
---
# <a name="unicode-compression-implementation"></a><span data-ttu-id="58d4c-102">Unicode 压缩的实现</span><span class="sxs-lookup"><span data-stu-id="58d4c-102">Unicode Compression Implementation</span></span>
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="58d4c-103">使用 Unicode 标准压缩方案 (SCSU) 算法实现来压缩在行或页压缩对象中存储的 Unicode 值。</span><span class="sxs-lookup"><span data-stu-id="58d4c-103">uses an implementation of the Standard Compression Scheme for Unicode (SCSU) algorithm to compress Unicode values that are stored in row or page compressed objects.</span></span> <span data-ttu-id="58d4c-104">对于这些压缩对象，Unicode 压缩对于 `nchar(n)` 和 `nvarchar(n)` 列而言是自动的。</span><span class="sxs-lookup"><span data-stu-id="58d4c-104">For these compressed objects, Unicode compression is automatic for `nchar(n)` and `nvarchar(n)` columns.</span></span> <span data-ttu-id="58d4c-105">[!INCLUDE[ssDE](../../includes/ssde-md.md)] 将 Unicode 数据存储为 2 个字节，无论区域设置如何。</span><span class="sxs-lookup"><span data-stu-id="58d4c-105">The [!INCLUDE[ssDE](../../includes/ssde-md.md)] stores Unicode data as 2 bytes, regardless of locale.</span></span> <span data-ttu-id="58d4c-106">这称为 UCS-2 编码。</span><span class="sxs-lookup"><span data-stu-id="58d4c-106">This is known as UCS-2 encoding.</span></span> <span data-ttu-id="58d4c-107">对于某些区域设置而言，在 SQL Server 中实现 SCSU 压缩可节省高达 50% 的存储空间。</span><span class="sxs-lookup"><span data-stu-id="58d4c-107">For some locales, the implementation of SCSU compression in SQL Server can save up to 50 percent in storage space.</span></span>  
  
## <a name="supported-data-types"></a><span data-ttu-id="58d4c-108">支持的数据类型</span><span class="sxs-lookup"><span data-stu-id="58d4c-108">Supported Data Types</span></span>  
 <span data-ttu-id="58d4c-109">Unicode 压缩支持固定长度 `nchar(n)` 和 `nvarchar(n)` 数据类型。</span><span class="sxs-lookup"><span data-stu-id="58d4c-109">Unicode compression supports the fixed-length `nchar(n)` and `nvarchar(n)` data types.</span></span> <span data-ttu-id="58d4c-110">存储于行外或 `nvarchar(max)` 列中的数据值不压缩。</span><span class="sxs-lookup"><span data-stu-id="58d4c-110">Data values that are stored off row or in `nvarchar(max)` columns are not compressed.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="58d4c-111">`nvarchar(max)` 不支持 Unicode 压缩，即使数据存储于行内。</span><span class="sxs-lookup"><span data-stu-id="58d4c-111">Unicode compression is not supported for `nvarchar(max)` data even if it is stored in row.</span></span> <span data-ttu-id="58d4c-112">但是，此数据类型仍可以从页压缩中受益。</span><span class="sxs-lookup"><span data-stu-id="58d4c-112">However, this data type can still benefit from page compression.</span></span>  
  
## <a name="upgrading-from-earlier-versions-of-sql-server"></a><span data-ttu-id="58d4c-113">从 SQL Server 的早期版本升级</span><span class="sxs-lookup"><span data-stu-id="58d4c-113">Upgrading from Earlier Versions of SQL Server</span></span>  
 <span data-ttu-id="58d4c-114">在某一 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 数据库升级到 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 时，将不会对任何数据库对象（无论是压缩的还是未压缩的）进行与 Unicode 压缩相关的更改。</span><span class="sxs-lookup"><span data-stu-id="58d4c-114">When a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] database is upgraded to [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)], Unicode compression-related changes are not made to any database object, compressed or uncompressed.</span></span> <span data-ttu-id="58d4c-115">在数据库升级后，对象会受到影响，如下所示：</span><span class="sxs-lookup"><span data-stu-id="58d4c-115">After the database is upgraded, objects are affected as follows:</span></span>  
  
-   <span data-ttu-id="58d4c-116">如果该对象未压缩，则不会进行更改，并且对象继续像以前一样工作。</span><span class="sxs-lookup"><span data-stu-id="58d4c-116">If the object is not compressed, no changes are made and the object continues to function as it did previously.</span></span>  
  
-   <span data-ttu-id="58d4c-117">行或页压缩的对象继续像以前那样工作。</span><span class="sxs-lookup"><span data-stu-id="58d4c-117">Row- or page-compressed objects continue to function as they did previously.</span></span> <span data-ttu-id="58d4c-118">未压缩的数据将一直保持未压缩的形式，直到其值被更新。</span><span class="sxs-lookup"><span data-stu-id="58d4c-118">Uncompressed data remains in uncompressed form until its value is updated.</span></span>  
  
-   <span data-ttu-id="58d4c-119">插入行或页压缩表的新行使用 Unicode 压缩进行压缩。</span><span class="sxs-lookup"><span data-stu-id="58d4c-119">New rows that are inserted into a row- or page-compressed table are compressed using Unicode compression.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="58d4c-120">为了充分利用 Unicode 压缩的好处，必须使用页或行压缩重新生成对象。</span><span class="sxs-lookup"><span data-stu-id="58d4c-120">To take full advantage of the benefits of Unicode compression, the object must be rebuilt with page or row compression.</span></span>  
  
## <a name="how-unicode-compression-affects-data-storage"></a><span data-ttu-id="58d4c-121">Unicode 压缩影响数据存储的方式</span><span class="sxs-lookup"><span data-stu-id="58d4c-121">How Unicode Compression Affects Data Storage</span></span>  
 <span data-ttu-id="58d4c-122">在创建或重新生成某一索引时，或者在使用行或页压缩进行压缩的表中更改某一值时，只有在其压缩大小小于其当前大小时，受影响的索引或值才以压缩的形式存储。</span><span class="sxs-lookup"><span data-stu-id="58d4c-122">When an index is created or rebuilt or when a value is changed in a table that was compressed with row or page compression, the affected index or value is stored compressed only if its compressed size is less than its current size.</span></span> <span data-ttu-id="58d4c-123">这样可避免表或索引中的行由于 Unicode 压缩而增大。</span><span class="sxs-lookup"><span data-stu-id="58d4c-123">This prevents rows in a table or index from increasing in size because of Unicode compression.</span></span>  
  
 <span data-ttu-id="58d4c-124">压缩节省的存储空间取决于所压缩数据的特性和数据的区域设置。</span><span class="sxs-lookup"><span data-stu-id="58d4c-124">The storage space that compression saves depends on the characteristics of the data that is being compressed and the locale of the data.</span></span> <span data-ttu-id="58d4c-125">下表列出了可以为若干区域设置节省的空间。</span><span class="sxs-lookup"><span data-stu-id="58d4c-125">The following table lists the space savings that can be achieved for several locales.</span></span>  
  
|<span data-ttu-id="58d4c-126">Locale</span><span class="sxs-lookup"><span data-stu-id="58d4c-126">Locale</span></span>|<span data-ttu-id="58d4c-127">压缩百分比</span><span class="sxs-lookup"><span data-stu-id="58d4c-127">Compression percent</span></span>|  
|------------|-------------------------|  
|<span data-ttu-id="58d4c-128">英语</span><span class="sxs-lookup"><span data-stu-id="58d4c-128">English</span></span>|<span data-ttu-id="58d4c-129">50%</span><span class="sxs-lookup"><span data-stu-id="58d4c-129">50%</span></span>|  
|<span data-ttu-id="58d4c-130">德语</span><span class="sxs-lookup"><span data-stu-id="58d4c-130">German</span></span>|<span data-ttu-id="58d4c-131">50%</span><span class="sxs-lookup"><span data-stu-id="58d4c-131">50%</span></span>|  
|<span data-ttu-id="58d4c-132">Hindi</span><span class="sxs-lookup"><span data-stu-id="58d4c-132">Hindi</span></span>|<span data-ttu-id="58d4c-133">50%</span><span class="sxs-lookup"><span data-stu-id="58d4c-133">50%</span></span>|  
|<span data-ttu-id="58d4c-134">土耳其语</span><span class="sxs-lookup"><span data-stu-id="58d4c-134">Turkish</span></span>|<span data-ttu-id="58d4c-135">48%</span><span class="sxs-lookup"><span data-stu-id="58d4c-135">48%</span></span>|  
|<span data-ttu-id="58d4c-136">越南语</span><span class="sxs-lookup"><span data-stu-id="58d4c-136">Vietnamese</span></span>|<span data-ttu-id="58d4c-137">39%</span><span class="sxs-lookup"><span data-stu-id="58d4c-137">39%</span></span>|  
|<span data-ttu-id="58d4c-138">日语</span><span class="sxs-lookup"><span data-stu-id="58d4c-138">Japanese</span></span>|<span data-ttu-id="58d4c-139">15%</span><span class="sxs-lookup"><span data-stu-id="58d4c-139">15%</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="58d4c-140">另请参阅</span><span class="sxs-lookup"><span data-stu-id="58d4c-140">See Also</span></span>  
 <span data-ttu-id="58d4c-141">[数据压缩](data-compression.md) </span><span class="sxs-lookup"><span data-stu-id="58d4c-141">[Data Compression](data-compression.md) </span></span>  
 <span data-ttu-id="58d4c-142">[sp_estimate_data_compression_savings (Transact-SQL)](/sql/relational-databases/system-stored-procedures/sp-estimate-data-compression-savings-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="58d4c-142">[sp_estimate_data_compression_savings &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-estimate-data-compression-savings-transact-sql) </span></span>  
 <span data-ttu-id="58d4c-143">[页压缩的实现](page-compression-implementation.md) </span><span class="sxs-lookup"><span data-stu-id="58d4c-143">[Page Compression Implementation](page-compression-implementation.md) </span></span>  
 [<span data-ttu-id="58d4c-144">sys.dm_db_persisted_sku_features (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="58d4c-144">sys.dm_db_persisted_sku_features &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-dynamic-management-views/sys-dm-db-persisted-sku-features-transact-sql)  
  
  
