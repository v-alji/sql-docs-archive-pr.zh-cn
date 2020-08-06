---
title: MSSQLSERVER_511 | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2016
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 511 (Database Engine error)
ms.assetid: 0c85686a-53c1-4180-ba8c-2000e68a0d63
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 5b69d2c043997e2947563de119bc4ee89fdf4e32
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87688924"
---
# <a name="mssqlserver_511"></a><span data-ttu-id="cea91-102">MSSQLSERVER_511</span><span class="sxs-lookup"><span data-stu-id="cea91-102">MSSQLSERVER_511</span></span>
    
## <a name="details"></a><span data-ttu-id="cea91-103">详细信息</span><span class="sxs-lookup"><span data-stu-id="cea91-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="cea91-104">产品名称</span><span class="sxs-lookup"><span data-stu-id="cea91-104">Product Name</span></span>|<span data-ttu-id="cea91-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="cea91-105">SQL Server</span></span>|  
|<span data-ttu-id="cea91-106">事件 ID</span><span class="sxs-lookup"><span data-stu-id="cea91-106">Event ID</span></span>|<span data-ttu-id="cea91-107">511</span><span class="sxs-lookup"><span data-stu-id="cea91-107">511</span></span>|  
|<span data-ttu-id="cea91-108">事件源</span><span class="sxs-lookup"><span data-stu-id="cea91-108">Event Source</span></span>|<span data-ttu-id="cea91-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="cea91-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="cea91-110">组件</span><span class="sxs-lookup"><span data-stu-id="cea91-110">Component</span></span>|<span data-ttu-id="cea91-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="cea91-111">SQLEngine</span></span>|  
|<span data-ttu-id="cea91-112">符号名称</span><span class="sxs-lookup"><span data-stu-id="cea91-112">Symbolic Name</span></span>|<span data-ttu-id="cea91-113">ROW_TOOBIG</span><span class="sxs-lookup"><span data-stu-id="cea91-113">ROW_TOOBIG</span></span>|  
|<span data-ttu-id="cea91-114">消息正文</span><span class="sxs-lookup"><span data-stu-id="cea91-114">Message Text</span></span>|<span data-ttu-id="cea91-115">不能创建大小为 %d 的行，该大小大于所允许的最大值 %d。</span><span class="sxs-lookup"><span data-stu-id="cea91-115">Cannot create a row of size %d which is greater than the allowable maximum of %d.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="cea91-116">说明</span><span class="sxs-lookup"><span data-stu-id="cea91-116">Explanation</span></span>  
 <span data-ttu-id="cea91-117">尝试的操作已超出行大小的最大值。</span><span class="sxs-lookup"><span data-stu-id="cea91-117">The operation you have tried has exceeded the maximum size of a row.</span></span> <span data-ttu-id="cea91-118">通常，行大小的最大值为 8,060 个字节。</span><span class="sxs-lookup"><span data-stu-id="cea91-118">Usually, the maximum size of a row is 8,060 bytes.</span></span> <span data-ttu-id="cea91-119">某些存储格式包含的开销可减小数据可用的行大小。</span><span class="sxs-lookup"><span data-stu-id="cea91-119">Some storage formats contain overhead that can reduce the row size that is available for data.</span></span> <span data-ttu-id="cea91-120">例如，使用稀疏列时，行大小的最大值为 8,018 个字节。</span><span class="sxs-lookup"><span data-stu-id="cea91-120">For example, when you use sparse columns, the maximum size of a row is 8,018 bytes.</span></span> <span data-ttu-id="cea91-121">某些添加或删除行的操作和某些更改列的数据类型的操作要求在数据页重写此行，然后才能删除原始行。</span><span class="sxs-lookup"><span data-stu-id="cea91-121">Some operations that add or remove rows and some operations that change the data type of a column require the row to be rewritten on the data page, and then the original row is removed.</span></span> <span data-ttu-id="cea91-122">在这些操作中，行大小的有效限制值为最大限制值的一半。</span><span class="sxs-lookup"><span data-stu-id="cea91-122">In these operations, the effective limit to the size of the row is half the maximum limit.</span></span> <span data-ttu-id="cea91-123">这是因为，在短时间内，原始行和已修改的行都必须保留在数据页中。</span><span class="sxs-lookup"><span data-stu-id="cea91-123">This is because the original row and the modified row must both be contained on the data page for a short period.</span></span>  
  
> [!WARNING]  
>  <span data-ttu-id="cea91-124">每个非 null \*\*varchar (max) **或**nvarchar (max) \*\*列需要24个字节的附加固定分配，该分配在排序操作期间针对8060字节行限制进行计数。</span><span class="sxs-lookup"><span data-stu-id="cea91-124">Each non-null  **varchar(max)** or **nvarchar(max)** column requires 24 bytes of additional fixed allocation which counts against the 8,060 byte row limit during a sort operation.</span></span> <span data-ttu-id="cea91-125">这会为非 null \*\*varchar (最大) **或 nvarchar 数创建隐式限制， (可以在表中创建的**最大) \*\*列数。</span><span class="sxs-lookup"><span data-stu-id="cea91-125">This can create an implicit limit to the number of non-null **varchar(max)** or **nvarchar(max)** columns that can be created in a table.</span></span> <span data-ttu-id="cea91-126">在以下情况下不提供特殊错误：创建表格（最大行大小超过允许的最大 8060 字节时出现的一般警告除外）时，或插入数据时。</span><span class="sxs-lookup"><span data-stu-id="cea91-126">No special error is provided when the table is created (beyond the usual warning that the maximum row size exceeds the allowed maximum of 8060 bytes) or at the time of data insertion.</span></span> <span data-ttu-id="cea91-127">这一较大的行大小可能会导致在执行某些正常操作（例如聚集索引键更新或完整列集排序）期间出现错误（例如错误 512），使得用户在执行操作前无法预料到此类错误。</span><span class="sxs-lookup"><span data-stu-id="cea91-127">This large row size can cause errors (such as error 512) during some normal operations, such as a clustered index key update, or sorts of the full column set, which users cannot anticipate until performing an operation.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="cea91-128">用户操作</span><span class="sxs-lookup"><span data-stu-id="cea91-128">User Action</span></span>  
 <span data-ttu-id="cea91-129">如果可能，请减小该行的大小。</span><span class="sxs-lookup"><span data-stu-id="cea91-129">If it is possible, reduce the size of the row.</span></span>  
  
 <span data-ttu-id="cea91-130">如果您认为此问题是由对该行进行就地更新引起，则必须采用多个步骤更改此表。</span><span class="sxs-lookup"><span data-stu-id="cea91-130">If you think the problem is caused by an in-place update of the row, you must change the table in multiple steps.</span></span> <span data-ttu-id="cea91-131">创建一个新表，并将数据传输到此新表中。</span><span class="sxs-lookup"><span data-stu-id="cea91-131">Create a new table, and transfer the data into the new table.</span></span> <span data-ttu-id="cea91-132">然后，或者删除原始表并重命名此新表，或者截断原始表，修改原始表中的行，然后将数据重新移到原始表中。</span><span class="sxs-lookup"><span data-stu-id="cea91-132">Then, either delete the original table and rename the new table, or truncate the original table, modify the rows in the original table, and then move the data back into it.</span></span>  
  
  
