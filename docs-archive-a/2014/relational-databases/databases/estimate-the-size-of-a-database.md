---
title: 估计数据库的大小 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- space allocation [SQL Server], database size
- calculating database size
- increasing database size
- database size [SQL Server], estimating
- predicting database size
- size [SQL Server], databases
- estimating database size
- designing databases [SQL Server], estimating size
ms.assetid: 5b240161-eba4-44b0-946c-61a8fc00fc8c
author: stevestein
ms.author: sstein
ms.openlocfilehash: 6e3a390c4ade2c2dc08f67d2d1461955516e866c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87581292"
---
# <a name="estimate-the-size-of-a-database"></a><span data-ttu-id="d9234-102">估计数据库的大小</span><span class="sxs-lookup"><span data-stu-id="d9234-102">Estimate the Size of a Database</span></span>
  <span data-ttu-id="d9234-103">在设计数据库时，可能需要估计填入数据后数据库的大小。</span><span class="sxs-lookup"><span data-stu-id="d9234-103">When you design a database, you may have to estimate how large the database will be when filled with data.</span></span> <span data-ttu-id="d9234-104">估计数据库的大小可以帮助您确定执行下列操作所需的硬件配置：</span><span class="sxs-lookup"><span data-stu-id="d9234-104">Estimating the size of the database can help you determine the hardware configuration you will require to do the following:</span></span>  
  
-   <span data-ttu-id="d9234-105">获得应用程序所需的性能。</span><span class="sxs-lookup"><span data-stu-id="d9234-105">Achieve the performance required by your applications.</span></span>  
  
-   <span data-ttu-id="d9234-106">保证有足够的物理磁盘空间用于存储数据和索引。</span><span class="sxs-lookup"><span data-stu-id="d9234-106">Guarantee the appropriate physical amount of disk space required to store the data and indexes.</span></span>  
  
 <span data-ttu-id="d9234-107">估计数据库的大小还可以帮助您确定是否需要修改数据库设计。</span><span class="sxs-lookup"><span data-stu-id="d9234-107">Estimating the size of a database can also help you determine whether the database design needs refining.</span></span> <span data-ttu-id="d9234-108">例如，您可能会发现估计的数据库大小太大，无法在您的单位中实现，因此需要进行更多的规范化处理。</span><span class="sxs-lookup"><span data-stu-id="d9234-108">For example, you may determine that the estimated size of the database is too large to implement in your organization and that more normalization is required.</span></span> <span data-ttu-id="d9234-109">相反，也可能估计大小比需要的更小。</span><span class="sxs-lookup"><span data-stu-id="d9234-109">Conversely, the estimated size may be smaller than expected.</span></span> <span data-ttu-id="d9234-110">这就允许您降低数据库的规范化以提高查询性能。</span><span class="sxs-lookup"><span data-stu-id="d9234-110">This would allow you to denormalize the database to improve query performance.</span></span>  
  
 <span data-ttu-id="d9234-111">若要估计数据库的大小，请分别估计每个表的大小，然后将各个值累加起来即可。</span><span class="sxs-lookup"><span data-stu-id="d9234-111">To estimate the size of a database, estimate the size of each table individually and then add the values obtained.</span></span> <span data-ttu-id="d9234-112">表的大小取决于表是否有索引，如果有索引，还取决于索引的类型。</span><span class="sxs-lookup"><span data-stu-id="d9234-112">The size of a table depends on whether the table has indexes and, if they do, what type of indexes.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="d9234-113">本节内容</span><span class="sxs-lookup"><span data-stu-id="d9234-113">In This Section</span></span>  
  
|<span data-ttu-id="d9234-114">主题</span><span class="sxs-lookup"><span data-stu-id="d9234-114">Topic</span></span>|<span data-ttu-id="d9234-115">说明</span><span class="sxs-lookup"><span data-stu-id="d9234-115">Description</span></span>|  
|-----------|-----------------|  
|[<span data-ttu-id="d9234-116">估计表的大小</span><span class="sxs-lookup"><span data-stu-id="d9234-116">Estimate the Size of a Table</span></span>](estimate-the-size-of-a-table.md)|<span data-ttu-id="d9234-117">定义估计用于存储表和相关索引中的数据的空间量所需的步骤和计算。</span><span class="sxs-lookup"><span data-stu-id="d9234-117">Defines the steps and calculations needed to estimate the amount of space required to store the data in a table and associated indexes.</span></span>|  
|[<span data-ttu-id="d9234-118">估计堆的大小</span><span class="sxs-lookup"><span data-stu-id="d9234-118">Estimate the Size of a Heap</span></span>](estimate-the-size-of-a-heap.md)|<span data-ttu-id="d9234-119">定义估计用于存储堆中的数据的空间量所需的步骤和计算。</span><span class="sxs-lookup"><span data-stu-id="d9234-119">Defines the steps and calculations needed to estimate the amount of space required to store the data in a heap.</span></span> <span data-ttu-id="d9234-120">堆是没有聚集索引的表。</span><span class="sxs-lookup"><span data-stu-id="d9234-120">A heap is a table that does not have a clustered index.</span></span>|  
|[<span data-ttu-id="d9234-121">估计聚集索引的大小</span><span class="sxs-lookup"><span data-stu-id="d9234-121">Estimate the Size of a Clustered Index</span></span>](estimate-the-size-of-a-clustered-index.md)|<span data-ttu-id="d9234-122">定义估计用于存储聚集索引中的数据的空间量所需的步骤和计算。</span><span class="sxs-lookup"><span data-stu-id="d9234-122">Defines the steps and calculations needed to estimate the amount of space required to store the data in a clustered index.</span></span>|  
|[<span data-ttu-id="d9234-123">估计非聚集索引的大小</span><span class="sxs-lookup"><span data-stu-id="d9234-123">Estimate the Size of a Nonclustered Index</span></span>](estimate-the-size-of-a-nonclustered-index.md)|<span data-ttu-id="d9234-124">定义估计用于存储非聚集索引中的数据的空间量所需的步骤和计算。</span><span class="sxs-lookup"><span data-stu-id="d9234-124">Defines the steps and calculations needed to estimate the amount of space required to store the data in a nonclustered index.</span></span>|  
  
  
