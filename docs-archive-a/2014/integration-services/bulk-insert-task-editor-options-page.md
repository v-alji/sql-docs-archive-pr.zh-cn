---
title: 大容量插入任务编辑器 (选项 "页面) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.bulkinserttask.options.f1
helpviewer_keywords:
- Bulk Insert Task Editor
ms.assetid: b3702811-3eb8-4b28-9190-5ae7a1a7bb6f
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 1751d1e0ac01d5459a8c76e6a48626c2ad6deafd
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87692493"
---
# <a name="bulk-insert-task-editor-options-page"></a><span data-ttu-id="bfdd4-102">大容量插入任务编辑器（“选项”页）</span><span class="sxs-lookup"><span data-stu-id="bfdd4-102">Bulk Insert Task Editor (Options Page)</span></span>
  <span data-ttu-id="bfdd4-103">使用 **“大容量插入任务编辑器”** 对话框的 **“选项”** 页，可以设置大容量插入操作的属性。</span><span class="sxs-lookup"><span data-stu-id="bfdd4-103">Use the **Options** page of the **Bulk Insert Task Editor** dialog box to set properties for the bulk insert operation.</span></span> <span data-ttu-id="bfdd4-104">大容量插入任务可以将大量的数据复制到 [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 表或视图中。</span><span class="sxs-lookup"><span data-stu-id="bfdd4-104">The Bulk Insert task copies large amounts of data into a [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] table or view.</span></span>  
  
 <span data-ttu-id="bfdd4-105">若要了解如何使用大容量插入，请参阅[大容量插入任务](control-flow/bulk-insert-task.md)和 [BULK INSERT (Transact-SQL)](/sql/t-sql/statements/bulk-insert-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="bfdd4-105">To learn about working with bulk inserts, see [Bulk Insert Task](control-flow/bulk-insert-task.md) and [BULK INSERT &#40;Transact-SQL&#41;](/sql/t-sql/statements/bulk-insert-transact-sql).</span></span>  
  
## <a name="options"></a><span data-ttu-id="bfdd4-106">选项</span><span class="sxs-lookup"><span data-stu-id="bfdd4-106">Options</span></span>  
 <span data-ttu-id="bfdd4-107">**CodePage**</span><span class="sxs-lookup"><span data-stu-id="bfdd4-107">**CodePage**</span></span>  
 <span data-ttu-id="bfdd4-108">指定数据文件中数据的代码页。</span><span class="sxs-lookup"><span data-stu-id="bfdd4-108">Specify the code page of the data in the data file.</span></span>  
  
 <span data-ttu-id="bfdd4-109">**DataFileType**</span><span class="sxs-lookup"><span data-stu-id="bfdd4-109">**DataFileType**</span></span>  
 <span data-ttu-id="bfdd4-110">指定在加载操作中要使用的数据类型值。</span><span class="sxs-lookup"><span data-stu-id="bfdd4-110">Specify the data-type value to use in the load operation.</span></span>  
  
 <span data-ttu-id="bfdd4-111">**BatchSize**</span><span class="sxs-lookup"><span data-stu-id="bfdd4-111">**BatchSize**</span></span>  
 <span data-ttu-id="bfdd4-112">指定每批中的行数。</span><span class="sxs-lookup"><span data-stu-id="bfdd4-112">Specify the number of rows in a batch.</span></span> <span data-ttu-id="bfdd4-113">默认设置为整个数据文件。</span><span class="sxs-lookup"><span data-stu-id="bfdd4-113">The default is the entire data file.</span></span> <span data-ttu-id="bfdd4-114">如果将 **BatchSize** 设置为零，则数据是在一批中加载的。</span><span class="sxs-lookup"><span data-stu-id="bfdd4-114">If you set **BatchSize** to zero, the data is loaded in a single batch.</span></span>  
  
 <span data-ttu-id="bfdd4-115">**LastRow**</span><span class="sxs-lookup"><span data-stu-id="bfdd4-115">**LastRow**</span></span>  
 <span data-ttu-id="bfdd4-116">指定要复制的最后一行。</span><span class="sxs-lookup"><span data-stu-id="bfdd4-116">Specify the last row to copy.</span></span>  
  
 <span data-ttu-id="bfdd4-117">**FirstRow**</span><span class="sxs-lookup"><span data-stu-id="bfdd4-117">**FirstRow**</span></span>  
 <span data-ttu-id="bfdd4-118">指定要开始复制的第一行。</span><span class="sxs-lookup"><span data-stu-id="bfdd4-118">Specify the first row from which to start copying.</span></span>  
  
 <span data-ttu-id="bfdd4-119">**选项**</span><span class="sxs-lookup"><span data-stu-id="bfdd4-119">**Options**</span></span>  
 |<span data-ttu-id="bfdd4-120">术语</span><span class="sxs-lookup"><span data-stu-id="bfdd4-120">Term</span></span>|<span data-ttu-id="bfdd4-121">定义</span><span class="sxs-lookup"><span data-stu-id="bfdd4-121">Definition</span></span>|  
|----------|----------------|  
|<span data-ttu-id="bfdd4-122">**检查约束**</span><span class="sxs-lookup"><span data-stu-id="bfdd4-122">**Check constraints**</span></span>|<span data-ttu-id="bfdd4-123">选择此项将检查表约束和列约束。</span><span class="sxs-lookup"><span data-stu-id="bfdd4-123">Select to check the table and column constraints.</span></span>|  
|<span data-ttu-id="bfdd4-124">**保留 Null**</span><span class="sxs-lookup"><span data-stu-id="bfdd4-124">**Keep nulls**</span></span>|<span data-ttu-id="bfdd4-125">选择此项将在大容量插入操作期间保留 Null 值，而不是为空列插入任意默认值。</span><span class="sxs-lookup"><span data-stu-id="bfdd4-125">Select to retain null values during the bulk insert operation, instead of inserting any default values for empty columns.</span></span>|  
|<span data-ttu-id="bfdd4-126">**启用标识插入**</span><span class="sxs-lookup"><span data-stu-id="bfdd4-126">**Enable identity insert**</span></span>|<span data-ttu-id="bfdd4-127">选择此项可将现有值插入到标识列中。</span><span class="sxs-lookup"><span data-stu-id="bfdd4-127">Select to insert existing values into an identity column.</span></span>|  
|<span data-ttu-id="bfdd4-128">**表锁**</span><span class="sxs-lookup"><span data-stu-id="bfdd4-128">**Table lock**</span></span>|<span data-ttu-id="bfdd4-129">选择此项将在大容量插入期间锁定表。</span><span class="sxs-lookup"><span data-stu-id="bfdd4-129">Select to lock the table during the bulk insert.</span></span>|  
|<span data-ttu-id="bfdd4-130">**激发触发器**</span><span class="sxs-lookup"><span data-stu-id="bfdd4-130">**Fire triggers**</span></span>|<span data-ttu-id="bfdd4-131">选择此项将激发对表上的触发器的任意插入、更新或删除操作。</span><span class="sxs-lookup"><span data-stu-id="bfdd4-131">Select to fire any insert, update, or delete triggers on the table.</span></span>|  
  
 <span data-ttu-id="bfdd4-132">**SortedData**</span><span class="sxs-lookup"><span data-stu-id="bfdd4-132">**SortedData**</span></span>  
 <span data-ttu-id="bfdd4-133">指定大容量插入语句中的 ORDER BY 子句。</span><span class="sxs-lookup"><span data-stu-id="bfdd4-133">Specify the ORDER BY clause in the bulk insert statement.</span></span> <span data-ttu-id="bfdd4-134">所提供的列名必须是目标表中的有效列。</span><span class="sxs-lookup"><span data-stu-id="bfdd4-134">The column name that you supply must be a valid column in the destination table.</span></span> <span data-ttu-id="bfdd4-135">默认值为 `false`。</span><span class="sxs-lookup"><span data-stu-id="bfdd4-135">The default is `false`.</span></span> <span data-ttu-id="bfdd4-136">这意味着 ORDER BY 子句将不对数据进行排序。</span><span class="sxs-lookup"><span data-stu-id="bfdd4-136">This means that the data is not sorted by an ORDER BY clause.</span></span>  
  
 <span data-ttu-id="bfdd4-137">**MaxErrors**</span><span class="sxs-lookup"><span data-stu-id="bfdd4-137">**MaxErrors**</span></span>  
 <span data-ttu-id="bfdd4-138">指定在取消大容量插入操作之前可以发生的最大错误数量。</span><span class="sxs-lookup"><span data-stu-id="bfdd4-138">Specify the maximum number of errors that can occur before the bulk insert operation is canceled.</span></span> <span data-ttu-id="bfdd4-139">如果值为 0，则指示对错误的数量没有限制。</span><span class="sxs-lookup"><span data-stu-id="bfdd4-139">A value of 0 indicates that an infinite number of errors are allowed.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="bfdd4-140">大容量加载操作不能导入的每一行都被计为一个错误。</span><span class="sxs-lookup"><span data-stu-id="bfdd4-140">Each row that cannot be imported by the bulk load operation is counted as one error.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bfdd4-141">另请参阅</span><span class="sxs-lookup"><span data-stu-id="bfdd4-141">See Also</span></span>  
 <span data-ttu-id="bfdd4-142">[Integration Services 错误和消息引用](../../2014/integration-services/integration-services-error-and-message-reference.md) </span><span class="sxs-lookup"><span data-stu-id="bfdd4-142">[Integration Services Error and Message Reference](../../2014/integration-services/integration-services-error-and-message-reference.md) </span></span>  
 <span data-ttu-id="bfdd4-143">[大容量插入任务编辑器 &#40;常规页&#41;](general-page-of-integration-services-designers-options.md) </span><span class="sxs-lookup"><span data-stu-id="bfdd4-143">[Bulk Insert Task Editor &#40;General Page&#41;](general-page-of-integration-services-designers-options.md) </span></span>  
 <span data-ttu-id="bfdd4-144">[大容量插入任务编辑器 &#40;连接页&#41;](../../2014/integration-services/bulk-insert-task-editor-connection-page.md) </span><span class="sxs-lookup"><span data-stu-id="bfdd4-144">[Bulk Insert Task Editor &#40;Connection Page&#41;](../../2014/integration-services/bulk-insert-task-editor-connection-page.md) </span></span>  
 <span data-ttu-id="bfdd4-145">[“表达式”页](expressions/expressions-page.md) </span><span class="sxs-lookup"><span data-stu-id="bfdd4-145">[Expressions Page](expressions/expressions-page.md) </span></span>  
 [<span data-ttu-id="bfdd4-146">控制流</span><span class="sxs-lookup"><span data-stu-id="bfdd4-146">Control Flow</span></span>](control-flow/control-flow.md)  
  
  
