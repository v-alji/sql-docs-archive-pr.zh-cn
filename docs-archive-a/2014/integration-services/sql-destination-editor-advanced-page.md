---
title: SQL 目标编辑器 (高级页面) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.sqlserverdestadapter.advanced.f1
helpviewer_keywords:
- SQL Server Destination Editor
ms.assetid: 9b46bcf8-ddaf-4d7d-90a6-80bc19517e9b
author: chugugrace
ms.author: chugu
ms.openlocfilehash: ccf25ad888c93f694678a152417affe5c0e16091
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87578945"
---
# <a name="sql-destination-editor-advanced-page"></a><span data-ttu-id="acfe5-102">SQL 目标编辑器（“高级”页）</span><span class="sxs-lookup"><span data-stu-id="acfe5-102">SQL Destination Editor (Advanced Page)</span></span>
  <span data-ttu-id="acfe5-103">可以使用 **“SQL 目标编辑器”** 对话框的 **“高级”** 页指定大容量插入高级选项。</span><span class="sxs-lookup"><span data-stu-id="acfe5-103">Use the **Advanced** page of the **SQL Destination Editor** dialog box to specify advanced bulk insert options.</span></span>  
  
 <span data-ttu-id="acfe5-104">若要了解有关 SQL Server 目标的详细信息，请参阅 [SQL Server Destination](data-flow/sql-server-destination.md)。</span><span class="sxs-lookup"><span data-stu-id="acfe5-104">To learn more about the SQL Server destination, see [SQL Server Destination](data-flow/sql-server-destination.md).</span></span>  
  
## <a name="options"></a><span data-ttu-id="acfe5-105">选项</span><span class="sxs-lookup"><span data-stu-id="acfe5-105">Options</span></span>  
 <span data-ttu-id="acfe5-106">**保留标识**</span><span class="sxs-lookup"><span data-stu-id="acfe5-106">**Keep identity**</span></span>  
 <span data-ttu-id="acfe5-107">指定任务是否应在标识列中插入值。</span><span class="sxs-lookup"><span data-stu-id="acfe5-107">Specify whether the task should insert values into identity columns.</span></span> <span data-ttu-id="acfe5-108">此属性的默认值为 `False`。</span><span class="sxs-lookup"><span data-stu-id="acfe5-108">The default value of this property is `False`.</span></span>  
  
 <span data-ttu-id="acfe5-109">**保留 Null**</span><span class="sxs-lookup"><span data-stu-id="acfe5-109">**Keep nulls**</span></span>  
 <span data-ttu-id="acfe5-110">指定任务是否应保留空值。</span><span class="sxs-lookup"><span data-stu-id="acfe5-110">Specify whether the task should keep null values.</span></span> <span data-ttu-id="acfe5-111">此属性的默认值为 `False`。</span><span class="sxs-lookup"><span data-stu-id="acfe5-111">The default value of this property is `False`.</span></span>  
  
 <span data-ttu-id="acfe5-112">**表锁**</span><span class="sxs-lookup"><span data-stu-id="acfe5-112">**Table lock**</span></span>  
 <span data-ttu-id="acfe5-113">指定在加载数据时是否锁定表。</span><span class="sxs-lookup"><span data-stu-id="acfe5-113">Specify whether the table is locked when the data is loaded.</span></span> <span data-ttu-id="acfe5-114">此属性的默认值为 `True`。</span><span class="sxs-lookup"><span data-stu-id="acfe5-114">The default value of this property is `True`.</span></span>  
  
 <span data-ttu-id="acfe5-115">**检查约束**</span><span class="sxs-lookup"><span data-stu-id="acfe5-115">**Check constraints**</span></span>  
 <span data-ttu-id="acfe5-116">指定任务是否应检查约束。</span><span class="sxs-lookup"><span data-stu-id="acfe5-116">Specify whether the task should check constraints.</span></span> <span data-ttu-id="acfe5-117">此属性的默认值为 `True`。</span><span class="sxs-lookup"><span data-stu-id="acfe5-117">The default value of this property is `True`.</span></span>  
  
 <span data-ttu-id="acfe5-118">**激发触发器**</span><span class="sxs-lookup"><span data-stu-id="acfe5-118">**Fire triggers**</span></span>  
 <span data-ttu-id="acfe5-119">指定大容量插入任务是否应对表激发触发器。</span><span class="sxs-lookup"><span data-stu-id="acfe5-119">Specify whether the bulk insert should fire triggers on tables.</span></span> <span data-ttu-id="acfe5-120">此属性的默认值为 `False`。</span><span class="sxs-lookup"><span data-stu-id="acfe5-120">The default value of this property is `False`.</span></span>  
  
 <span data-ttu-id="acfe5-121">**首行**</span><span class="sxs-lookup"><span data-stu-id="acfe5-121">**First Row**</span></span>  
 <span data-ttu-id="acfe5-122">指定要插入的第一行。</span><span class="sxs-lookup"><span data-stu-id="acfe5-122">Specify the first row to insert.</span></span> <span data-ttu-id="acfe5-123">此属性的默认值为 **-1**，表示尚未分配值。</span><span class="sxs-lookup"><span data-stu-id="acfe5-123">The default value of this property is **-1**, indicating that no value has been assigned.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="acfe5-124">如果在 **“SQL 目标编辑器”** 中清空此文本框，则表示不希望为此属性分配值。</span><span class="sxs-lookup"><span data-stu-id="acfe5-124">Clear the text box in the **SQL Destination Editor** to indicate that you do not want to assign a value for this property.</span></span> <span data-ttu-id="acfe5-125">请在“属性”\*\*\*\* 窗口、“高级编辑器”\*\*\*\* 和对象模型中使用 -1。</span><span class="sxs-lookup"><span data-stu-id="acfe5-125">Use -1 in the **Properties** window, the **Advanced Editor**, and the object model.</span></span>  
  
 <span data-ttu-id="acfe5-126">**末行**</span><span class="sxs-lookup"><span data-stu-id="acfe5-126">**Last Row**</span></span>  
 <span data-ttu-id="acfe5-127">指定要插入的最后一行。</span><span class="sxs-lookup"><span data-stu-id="acfe5-127">Specify the last row to insert.</span></span> <span data-ttu-id="acfe5-128">此属性的默认值为 **-1**，表示尚未分配值。</span><span class="sxs-lookup"><span data-stu-id="acfe5-128">The default value of this property is **-1**, indicating that no value has been assigned.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="acfe5-129">如果在 **“SQL 目标编辑器”** 中清空此文本框，则表示不希望为此属性分配值。</span><span class="sxs-lookup"><span data-stu-id="acfe5-129">Clear the text box in the **SQL Destination Editor** to indicate that you do not want to assign a value for this property.</span></span> <span data-ttu-id="acfe5-130">请在“属性”\*\*\*\* 窗口、“高级编辑器”\*\*\*\* 和对象模型中使用 -1。</span><span class="sxs-lookup"><span data-stu-id="acfe5-130">Use -1 in the **Properties** window, the **Advanced Editor**, and the object model.</span></span>  
  
 <span data-ttu-id="acfe5-131">**最大错误数**</span><span class="sxs-lookup"><span data-stu-id="acfe5-131">**Maximum number of errors**</span></span>  
 <span data-ttu-id="acfe5-132">指定在大容量插入任务停止之前可以发生的错误数量。</span><span class="sxs-lookup"><span data-stu-id="acfe5-132">Specify the number of errors that can occur before the bulk insert stops.</span></span> <span data-ttu-id="acfe5-133">此属性的默认值为 **-1**，表示尚未分配值。</span><span class="sxs-lookup"><span data-stu-id="acfe5-133">The default value of this property is **-1**, indicating that no value has been assigned.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="acfe5-134">如果在 **“SQL 目标编辑器”** 中清空此文本框，则表示不希望为此属性分配值。</span><span class="sxs-lookup"><span data-stu-id="acfe5-134">Clear the text box in the **SQL Destination Editor** to indicate that you do not want to assign a value for this property.</span></span> <span data-ttu-id="acfe5-135">请在“属性”\*\*\*\* 窗口、“高级编辑器”\*\*\*\* 和对象模型中使用 -1。</span><span class="sxs-lookup"><span data-stu-id="acfe5-135">Use -1 in the **Properties** window, the **Advanced Editor**, and the object model.</span></span>  
  
 <span data-ttu-id="acfe5-136">**超时**</span><span class="sxs-lookup"><span data-stu-id="acfe5-136">**Timeout**</span></span>  
 <span data-ttu-id="acfe5-137">指定在大容量插入任务因超时而停止之前等待的秒数。</span><span class="sxs-lookup"><span data-stu-id="acfe5-137">Specify the number of seconds to wait before the bulk insert stops because of a time-out.</span></span>  
  
 <span data-ttu-id="acfe5-138">**设置列顺序**</span><span class="sxs-lookup"><span data-stu-id="acfe5-138">**Order columns**</span></span>  
 <span data-ttu-id="acfe5-139">键入排序列的名称。</span><span class="sxs-lookup"><span data-stu-id="acfe5-139">Type the names of the sort columns.</span></span> <span data-ttu-id="acfe5-140">每一列都可以按升序或降序排序。</span><span class="sxs-lookup"><span data-stu-id="acfe5-140">Each column can be sorted in ascending or descending order.</span></span> <span data-ttu-id="acfe5-141">如果您使用多个排序列，请用逗号分隔列表。</span><span class="sxs-lookup"><span data-stu-id="acfe5-141">If you use multiple sort columns, delimit the list with commas.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="acfe5-142">另请参阅</span><span class="sxs-lookup"><span data-stu-id="acfe5-142">See Also</span></span>  
 <span data-ttu-id="acfe5-143">[Integration Services 错误和消息引用](../../2014/integration-services/integration-services-error-and-message-reference.md) </span><span class="sxs-lookup"><span data-stu-id="acfe5-143">[Integration Services Error and Message Reference](../../2014/integration-services/integration-services-error-and-message-reference.md) </span></span>  
 <span data-ttu-id="acfe5-144">[SQL 目标编辑器 &#40;连接管理器页&#41;](../../2014/integration-services/sql-destination-editor-connection-manager-page.md) </span><span class="sxs-lookup"><span data-stu-id="acfe5-144">[SQL Destination Editor &#40;Connection Manager Page&#41;](../../2014/integration-services/sql-destination-editor-connection-manager-page.md) </span></span>  
 <span data-ttu-id="acfe5-145">[SQL 目标编辑器 &#40;映射 "页面&#41;](../../2014/integration-services/sql-destination-editor-mappings-page.md) </span><span class="sxs-lookup"><span data-stu-id="acfe5-145">[SQL Destination Editor &#40;Mappings Page&#41;](../../2014/integration-services/sql-destination-editor-mappings-page.md) </span></span>  
 [<span data-ttu-id="acfe5-146">使用 SQL Server 目标大容量加载数据</span><span class="sxs-lookup"><span data-stu-id="acfe5-146">Bulk Load Data by Using the SQL Server Destination</span></span>](data-flow/bulk-load-data-by-using-the-sql-server-destination.md)  
  
  
