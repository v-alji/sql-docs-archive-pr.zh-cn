---
title: “XML 索引”对话框 (Visual Database Tools) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
f1_keywords:
- vdt.dlgbox.xmlindexes
ms.assetid: eef38310-4498-4ccc-bb77-5bbd1c7cc477
author: stevestein
ms.author: sstein
ms.openlocfilehash: f1fb23a801a9129611c032fa1d659caf624088aa
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87588186"
---
# <a name="xml-indexes-dialog-box-visual-database-tools"></a><span data-ttu-id="dd9fb-102">“XML 索引”对话框 (Visual Database Tools)</span><span class="sxs-lookup"><span data-stu-id="dd9fb-102">XML Indexes Dialog Box (Visual Database Tools)</span></span>
  <span data-ttu-id="dd9fb-103">使用“XML 索引”  对话框可为 XML 数据类型的列创建索引，这些列不能使用“索引/键”  对话框创建索引。</span><span class="sxs-lookup"><span data-stu-id="dd9fb-103">Use the **XML Indexes** dialog box to create indexes for columns of the data type XML, which cannot be indexed using the **Index/Keys** dialog box.</span></span> <span data-ttu-id="dd9fb-104">每个 XML 列都可以有多个 XML 索引，但最先创建的索引（主索引）将成为其他索引（二级索引）的基础。</span><span class="sxs-lookup"><span data-stu-id="dd9fb-104">Each XML column can have more than one XML Index, but the first one created (primary) will be the basis of the others (secondary).</span></span> <span data-ttu-id="dd9fb-105">删除主 XML 索引后，二级索引也会随之删除。</span><span class="sxs-lookup"><span data-stu-id="dd9fb-105">If you delete the primary XML index, the secondary indexes will also be deleted.</span></span>  
  
## <a name="options"></a><span data-ttu-id="dd9fb-106">选项</span><span class="sxs-lookup"><span data-stu-id="dd9fb-106">Options</span></span>  
 <span data-ttu-id="dd9fb-107">**选定的 XML 索引**</span><span class="sxs-lookup"><span data-stu-id="dd9fb-107">**Selected XML Index**</span></span>  
 <span data-ttu-id="dd9fb-108">列出现有的 XML 索引。</span><span class="sxs-lookup"><span data-stu-id="dd9fb-108">Lists existing XML indexes.</span></span> <span data-ttu-id="dd9fb-109">选择一个索引即可在右侧网格中显示其属性。</span><span class="sxs-lookup"><span data-stu-id="dd9fb-109">Select to show its properties in the grid to the right.</span></span> <span data-ttu-id="dd9fb-110">如果该列表为空，则表示尚未为该表定义任何 XML 索引。</span><span class="sxs-lookup"><span data-stu-id="dd9fb-110">If the list is empty, none have been defined for the table.</span></span>  
  
 <span data-ttu-id="dd9fb-111">**添加**</span><span class="sxs-lookup"><span data-stu-id="dd9fb-111">**Add**</span></span>  
 <span data-ttu-id="dd9fb-112">创建新的 XML 索引。</span><span class="sxs-lookup"><span data-stu-id="dd9fb-112">Create a new XML index.</span></span>  
  
 <span data-ttu-id="dd9fb-113">**删除**</span><span class="sxs-lookup"><span data-stu-id="dd9fb-113">**Delete**</span></span>  
 <span data-ttu-id="dd9fb-114">删除在“选定的 XML 索引”  列表中选定的 XML 索引。</span><span class="sxs-lookup"><span data-stu-id="dd9fb-114">Delete XML index selected in the **Selected XML Index** list.</span></span> <span data-ttu-id="dd9fb-115">如果删除主 XML 索引，系统将通知您这会同时删除所有二级索引，此时您可以继续操作或取消操作。</span><span class="sxs-lookup"><span data-stu-id="dd9fb-115">If you delete the primary XML index, you will be notified that this will delete all secondary ones as well, and you can either continue or cancel the action.</span></span>  
  
 <span data-ttu-id="dd9fb-116">**常规类别**</span><span class="sxs-lookup"><span data-stu-id="dd9fb-116">**General Category**</span></span>  
 <span data-ttu-id="dd9fb-117">展开此项可显示“列”  、“是主要的”  和“类型”  的属性字段。</span><span class="sxs-lookup"><span data-stu-id="dd9fb-117">When expanded, shows the property fields for **Columns**, **Is Primary**, and **Type**.</span></span>  
  
 <span data-ttu-id="dd9fb-118">**“列”**</span><span class="sxs-lookup"><span data-stu-id="dd9fb-118">**Columns**</span></span>  
 <span data-ttu-id="dd9fb-119">显示此索引按升序排序。</span><span class="sxs-lookup"><span data-stu-id="dd9fb-119">Shows that this index is sorted in ascending order.</span></span>  
  
 <span data-ttu-id="dd9fb-120">**是主要的**</span><span class="sxs-lookup"><span data-stu-id="dd9fb-120">**Is Primary**</span></span>  
 <span data-ttu-id="dd9fb-121">指示此索引是否为主索引。</span><span class="sxs-lookup"><span data-stu-id="dd9fb-121">Indicates whether this is the primary index.</span></span> <span data-ttu-id="dd9fb-122">基于该列创建的第一个 XML 索引将成为其他索引的基础。</span><span class="sxs-lookup"><span data-stu-id="dd9fb-122">The first XML index created on the column will be the basis of the others.</span></span>  
  
 <span data-ttu-id="dd9fb-123">**主引用名**</span><span class="sxs-lookup"><span data-stu-id="dd9fb-123">**Primary reference name**</span></span>  
 <span data-ttu-id="dd9fb-124">在此索引为二级索引时显示主索引的名称。</span><span class="sxs-lookup"><span data-stu-id="dd9fb-124">Shows the name of the primary index if this is a secondary index.</span></span> <span data-ttu-id="dd9fb-125">只有在此索引为二级索引时才可用。</span><span class="sxs-lookup"><span data-stu-id="dd9fb-125">Only available if this is a secondary index.</span></span>  
  
 <span data-ttu-id="dd9fb-126">**次要类型**</span><span class="sxs-lookup"><span data-stu-id="dd9fb-126">**Secondary type**</span></span>  
 <span data-ttu-id="dd9fb-127">显示二级索引的类型。</span><span class="sxs-lookup"><span data-stu-id="dd9fb-127">Shows the type of secondary index.</span></span> <span data-ttu-id="dd9fb-128">只有在此索引为二级索引时才可用。</span><span class="sxs-lookup"><span data-stu-id="dd9fb-128">Only available if this is a secondary index.</span></span>  
  
 <span data-ttu-id="dd9fb-129">类型 </span><span class="sxs-lookup"><span data-stu-id="dd9fb-129">**Type**</span></span>  
 <span data-ttu-id="dd9fb-130">显示此索引为 XML 索引。</span><span class="sxs-lookup"><span data-stu-id="dd9fb-130">Shows that this is an XML index.</span></span>  
  
 <span data-ttu-id="dd9fb-131">**标识类别**</span><span class="sxs-lookup"><span data-stu-id="dd9fb-131">**Identity Category**</span></span>  
 <span data-ttu-id="dd9fb-132">展开此项可显示“名称”  和“说明”  属性字段。</span><span class="sxs-lookup"><span data-stu-id="dd9fb-132">When expanded, shows the **Name** and **Description** property fields.</span></span>  
  
 <span data-ttu-id="dd9fb-133">**名称**</span><span class="sxs-lookup"><span data-stu-id="dd9fb-133">**Name**</span></span>  
 <span data-ttu-id="dd9fb-134">显示 XML 索引的名称。</span><span class="sxs-lookup"><span data-stu-id="dd9fb-134">Shows the name of the XML index.</span></span> <span data-ttu-id="dd9fb-135">在创建一个新索引时，将基于表设计器的活动窗口中的表为其指定默认名称。</span><span class="sxs-lookup"><span data-stu-id="dd9fb-135">When a new one is created, it is given a default name based on the table in the active window in Table Designer.</span></span> <span data-ttu-id="dd9fb-136">可随时更改名称。</span><span class="sxs-lookup"><span data-stu-id="dd9fb-136">You can change the name at any time.</span></span>  
  
 <span data-ttu-id="dd9fb-137">**说明**</span><span class="sxs-lookup"><span data-stu-id="dd9fb-137">**Description**</span></span>  
 <span data-ttu-id="dd9fb-138">描述该索引。</span><span class="sxs-lookup"><span data-stu-id="dd9fb-138">Describe the index.</span></span> <span data-ttu-id="dd9fb-139">若要编写更详细的说明，请单击“说明”，再单击属性字段右侧显示的省略号按钮 (…)   。</span><span class="sxs-lookup"><span data-stu-id="dd9fb-139">To write a more detailed description, click **Description** and then click the ellipsis button (**...**) that appears to the right of the property field.</span></span> <span data-ttu-id="dd9fb-140">这可以提供一个更大的文本编写区域。</span><span class="sxs-lookup"><span data-stu-id="dd9fb-140">This provides a larger area in which to write text.</span></span>  
  
 <span data-ttu-id="dd9fb-141">**表设计器类别**</span><span class="sxs-lookup"><span data-stu-id="dd9fb-141">**Table Designer Category**</span></span>  
 <span data-ttu-id="dd9fb-142">展开此项可显示有关此 XML 索引的属性的信息。</span><span class="sxs-lookup"><span data-stu-id="dd9fb-142">When expanded, shows information about the properties of this XML index.</span></span>  
  
 <span data-ttu-id="dd9fb-143">**填充规范**</span><span class="sxs-lookup"><span data-stu-id="dd9fb-143">**Fill Specification**</span></span>  
 <span data-ttu-id="dd9fb-144">展开此项可显示有关“填充因子”  和“填充索引”  的信息。</span><span class="sxs-lookup"><span data-stu-id="dd9fb-144">When expanded, shows information for **Fill Factor** and **Pad Index**.</span></span>  
  
 <span data-ttu-id="dd9fb-145">**填充因子**</span><span class="sxs-lookup"><span data-stu-id="dd9fb-145">**Fill Factor**</span></span>  
 <span data-ttu-id="dd9fb-146">指定系统在索引页中能够填充的空间百分比。</span><span class="sxs-lookup"><span data-stu-id="dd9fb-146">Specify what percentage of the index page the system can fill.</span></span> <span data-ttu-id="dd9fb-147">页面已满后，系统必须拆分页面才能添加新数据，从而影响性能。</span><span class="sxs-lookup"><span data-stu-id="dd9fb-147">Once a page is full, the system must split the page if new data is added, which impairs performance.</span></span>  
  
-   <span data-ttu-id="dd9fb-148">值为 100 表示将填满页面，这时需要的存储空间量最小但效率最低。</span><span class="sxs-lookup"><span data-stu-id="dd9fb-148">A value of 100 means the pages will be full; this requires the least amount of storage space but is the least efficient.</span></span> <span data-ttu-id="dd9fb-149">只有在不会对数据进行更改时（例如，对于只读表），才可以使用此设置。</span><span class="sxs-lookup"><span data-stu-id="dd9fb-149">This setting should be used only when there will be no changes to the data, for example, on a read-only table.</span></span>  
  
-   <span data-ttu-id="dd9fb-150">值越小，数据页上留出的可用空间就越大，这会减少随索引的增长而拆分数据页的需求。</span><span class="sxs-lookup"><span data-stu-id="dd9fb-150">A lower value leaves more empty space on the data pages, which reduces the need to split data pages as indexes grow.</span></span> <span data-ttu-id="dd9fb-151">但是，这需要更大的存储空间。</span><span class="sxs-lookup"><span data-stu-id="dd9fb-151">However, it requires more storage space.</span></span> <span data-ttu-id="dd9fb-152">在需要对表中的数据进行更改的情况下，此设置更为适用。</span><span class="sxs-lookup"><span data-stu-id="dd9fb-152">This setting is more appropriate when there will be changes to the data in the table.</span></span>  
  
 <span data-ttu-id="dd9fb-153">**填充索引**</span><span class="sxs-lookup"><span data-stu-id="dd9fb-153">**Pad Index**</span></span>  
 <span data-ttu-id="dd9fb-154">为此索引中的页提供与“填充因子”  中所指定百分比相同的可用空间（填充）百分比。</span><span class="sxs-lookup"><span data-stu-id="dd9fb-154">Provide pages in this index the same percentage of empty space (padding) that is specified in **Fill Factor**.</span></span>  
  
 <span data-ttu-id="dd9fb-155">**已禁用**</span><span class="sxs-lookup"><span data-stu-id="dd9fb-155">**Is Disabled**</span></span>  
 <span data-ttu-id="dd9fb-156">指定是否禁用此索引。</span><span class="sxs-lookup"><span data-stu-id="dd9fb-156">Specify whether this index is disabled.</span></span> <span data-ttu-id="dd9fb-157">禁用的索引不支持搜索，也不会在表中添加新项时随之更新。</span><span class="sxs-lookup"><span data-stu-id="dd9fb-157">Disabled indexes do not support searches, nor do they get updated when new items are added to the table.</span></span> <span data-ttu-id="dd9fb-158">您可以通过禁用索引来提高大容量插入和更新操作的性能。</span><span class="sxs-lookup"><span data-stu-id="dd9fb-158">You can improve performance for bulk inserts and updates by disabling an index.</span></span>  
  
 <span data-ttu-id="dd9fb-159">**允许页锁定**</span><span class="sxs-lookup"><span data-stu-id="dd9fb-159">**Page Locks Allowed**</span></span>  
 <span data-ttu-id="dd9fb-160">指定对此索引是否允许页级锁定。</span><span class="sxs-lookup"><span data-stu-id="dd9fb-160">Specify whether page-level locking is allowed on this index.</span></span> <span data-ttu-id="dd9fb-161">允许或禁用页级锁定会影响数据库性能。</span><span class="sxs-lookup"><span data-stu-id="dd9fb-161">Allowing or disallowing page-level locking affects database performance.</span></span>  
  
 <span data-ttu-id="dd9fb-162">**重新计算统计数据**</span><span class="sxs-lookup"><span data-stu-id="dd9fb-162">**Re-compute Statistics**</span></span>  
 <span data-ttu-id="dd9fb-163">在创建索引时计算新的统计数据。</span><span class="sxs-lookup"><span data-stu-id="dd9fb-163">Compute new statistics when the index is created.</span></span> <span data-ttu-id="dd9fb-164">重新计算统计数据会降低索引的生成速度，但通常会提高查询性能。</span><span class="sxs-lookup"><span data-stu-id="dd9fb-164">Re-computing statistics slows the building of indexes but usually improves query performance.</span></span>  
  
 <span data-ttu-id="dd9fb-165">**允许行锁定**</span><span class="sxs-lookup"><span data-stu-id="dd9fb-165">**Row Locks Allowed**</span></span>  
 <span data-ttu-id="dd9fb-166">指定对此索引是否允许行级锁定。</span><span class="sxs-lookup"><span data-stu-id="dd9fb-166">Specify whether row-level locking is allowed on this index.</span></span> <span data-ttu-id="dd9fb-167">允许或禁用行级锁定会影响数据库性能。</span><span class="sxs-lookup"><span data-stu-id="dd9fb-167">Allowing or disallowing row-level locking affects database performance.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dd9fb-168">另请参阅</span><span class="sxs-lookup"><span data-stu-id="dd9fb-168">See Also</span></span>  
 [<span data-ttu-id="dd9fb-169">创建 XML 索引</span><span class="sxs-lookup"><span data-stu-id="dd9fb-169">Create XML Indexes</span></span>](../../relational-databases/xml/create-xml-indexes.md)  
  
  
