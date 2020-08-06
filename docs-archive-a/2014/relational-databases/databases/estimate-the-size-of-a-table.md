---
title: 估计表的大小 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- pages [SQL Server], space
- space [SQL Server], tables
- row size [SQL Server]
- size [SQL Server], tables
- column size [SQL Server]
- predicting table size [SQL Server]
- table size [SQL Server]
- estimating table size
- clustered indexes, table size
- disk space [SQL Server], tables
- space allocation [SQL Server], table size
- designing databases [SQL Server], estimating size
- reserved free rows per page [SQL Server]
- calculating table size
ms.assetid: 15c17c92-616f-402e-894b-907a296efe5f
author: stevestein
ms.author: sstein
ms.openlocfilehash: 4a16d439d3b2bc59479866b7bb36295ec4fc8950
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87691737"
---
# <a name="estimate-the-size-of-a-table"></a><span data-ttu-id="8bef3-102">估计表的大小</span><span class="sxs-lookup"><span data-stu-id="8bef3-102">Estimate the Size of a Table</span></span>
  <span data-ttu-id="8bef3-103">可以使用下列步骤估计在表中存储数据所需的空间：</span><span class="sxs-lookup"><span data-stu-id="8bef3-103">You can use the following steps to estimate the amount of space required to store data in a table:</span></span>  
  
1.  <span data-ttu-id="8bef3-104">按照 [估计堆的大小](estimate-the-size-of-a-heap.md) 或 [估计聚集索引的大小](estimate-the-size-of-a-clustered-index.md)中的说明来计算堆或聚集索引所需空间。</span><span class="sxs-lookup"><span data-stu-id="8bef3-104">Calculate the space required for the heap or clustered index following the instructions in [Estimate the Size of a Heap](estimate-the-size-of-a-heap.md) or [Estimate the Size of a Clustered Index](estimate-the-size-of-a-clustered-index.md).</span></span>  
  
2.  <span data-ttu-id="8bef3-105">对于每个非聚集索引，按照 [估计非聚集索引的大小](estimate-the-size-of-a-nonclustered-index.md)中的说明来计算其所需空间。</span><span class="sxs-lookup"><span data-stu-id="8bef3-105">For each nonclustered index, calculate the space required for it by following the instructions in [Estimate the Size of a Nonclustered Index](estimate-the-size-of-a-nonclustered-index.md).</span></span>  
  
3.  <span data-ttu-id="8bef3-106">对步骤 1 和步骤 2 中计算的值求和。</span><span class="sxs-lookup"><span data-stu-id="8bef3-106">Add the values calculated in steps 1 and 2.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8bef3-107">另请参阅</span><span class="sxs-lookup"><span data-stu-id="8bef3-107">See Also</span></span>  
 <span data-ttu-id="8bef3-108">[估计数据库的大小](estimate-the-size-of-a-database.md) </span><span class="sxs-lookup"><span data-stu-id="8bef3-108">[Estimate the Size of a Database](estimate-the-size-of-a-database.md) </span></span>  
 <span data-ttu-id="8bef3-109">[估计堆的大小](estimate-the-size-of-a-heap.md) </span><span class="sxs-lookup"><span data-stu-id="8bef3-109">[Estimate the Size of a Heap](estimate-the-size-of-a-heap.md) </span></span>  
 <span data-ttu-id="8bef3-110">[估计聚集索引的大小](estimate-the-size-of-a-clustered-index.md) </span><span class="sxs-lookup"><span data-stu-id="8bef3-110">[Estimate the Size of a Clustered Index](estimate-the-size-of-a-clustered-index.md) </span></span>  
 [<span data-ttu-id="8bef3-111">估计非聚集索引的大小</span><span class="sxs-lookup"><span data-stu-id="8bef3-111">Estimate the Size of a Nonclustered Index</span></span>](estimate-the-size-of-a-nonclustered-index.md)  
  
  
