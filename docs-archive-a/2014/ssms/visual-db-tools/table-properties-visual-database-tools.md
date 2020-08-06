---
title: 表属性 (Visual Database Tools) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
f1_keywords:
- vdt.tabledesigner
- vdt.designers.properties.Table
ms.assetid: cc392987-1aab-45f5-b5af-a26be53409bf
author: stevestein
ms.author: sstein
ms.openlocfilehash: df4a0332ebc622b069c468e51c461b7cba20aa36
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87691462"
---
# <a name="table-properties-visual-database-tools"></a><span data-ttu-id="33a63-102">表属性 (Visual Database Tools)</span><span class="sxs-lookup"><span data-stu-id="33a63-102">Table Properties (Visual Database Tools)</span></span>
  <span data-ttu-id="33a63-103">如果您在表设计器中右键单击，再选择“属性”，则会在“属性”窗口中显示这些属性。</span><span class="sxs-lookup"><span data-stu-id="33a63-103">These properties appear in the Properties window when you right click in Table Designer and select Properties.</span></span> <span data-ttu-id="33a63-104">除非另行说明，否则在选定表后可以在“属性”窗口中编辑这些属性。</span><span class="sxs-lookup"><span data-stu-id="33a63-104">Unless otherwise noted, you can edit these properties in the Properties window when the table is selected.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="33a63-105">如果表是为复制发布的，则必须使用 Transact-SQL 语句 [ALTER TABLE](/sql/t-sql/statements/alter-table-transact-sql) 或 SQL Server 管理对象 (SMO) 对架构进行更改。</span><span class="sxs-lookup"><span data-stu-id="33a63-105">If the table is published for replication, you must make schema changes using the Transact-SQL statement [ALTER TABLE](/sql/t-sql/statements/alter-table-transact-sql) or SQL Server Management Objects (SMO).</span></span> <span data-ttu-id="33a63-106">使用表设计器或数据库关系图设计器更改架构后，会尝试删除并重新创建表。</span><span class="sxs-lookup"><span data-stu-id="33a63-106">When schema changes are made using the Table Designer or the Database Diagram Designer, it attempts to drop and recreate the table.</span></span> <span data-ttu-id="33a63-107">由于您不能删除已发布的对象，因此架构更改将失败。</span><span class="sxs-lookup"><span data-stu-id="33a63-107">You cannot drop published objects, therefore the schema change will fail.</span></span>  
  
## <a name="show-table-properties-in-table-designer"></a><span data-ttu-id="33a63-108">在表设计器中显示表属性</span><span class="sxs-lookup"><span data-stu-id="33a63-108">Show Table Properties in Table Designer</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="33a63-109">本主题中的属性按类别排序，而不是按字母顺序排序。</span><span class="sxs-lookup"><span data-stu-id="33a63-109">The properties in this topic are ordered by category rather than alphabet.</span></span>  
  
 <span data-ttu-id="33a63-110">**标识类别**</span><span class="sxs-lookup"><span data-stu-id="33a63-110">**Identity Category**</span></span>  
 <span data-ttu-id="33a63-111">展开此项可显示“名称”  、“说明”  和“架构”  的属性。</span><span class="sxs-lookup"><span data-stu-id="33a63-111">Expands to show properties for **Name**, **Description**, and **Schema**.</span></span>  
  
 <span data-ttu-id="33a63-112">**名称**</span><span class="sxs-lookup"><span data-stu-id="33a63-112">**Name**</span></span>  
 <span data-ttu-id="33a63-113">显示表的名称。</span><span class="sxs-lookup"><span data-stu-id="33a63-113">Displays the name of the table.</span></span> <span data-ttu-id="33a63-114">若要编辑名称，请在文本框中键入相应的内容。</span><span class="sxs-lookup"><span data-stu-id="33a63-114">To edit the name, type in the text box.</span></span>  
  
> [!CAUTION]  
>  <span data-ttu-id="33a63-115">如果现有查询、视图、用户定义函数、存储过程或程序引用该表，则对名称的修改将使这些对象无效。</span><span class="sxs-lookup"><span data-stu-id="33a63-115">If existing queries, views, user-defined functions, stored procedures, or programs refer to the table, the name modification will make these objects invalid.</span></span>  
  
 <span data-ttu-id="33a63-116">**Database Name**</span><span class="sxs-lookup"><span data-stu-id="33a63-116">**Database Name**</span></span>  
 <span data-ttu-id="33a63-117">显示所选表的数据源的名称。</span><span class="sxs-lookup"><span data-stu-id="33a63-117">Shows the name of the data source of the selected table.</span></span>  
  
 <span data-ttu-id="33a63-118">**说明**</span><span class="sxs-lookup"><span data-stu-id="33a63-118">**Description**</span></span>  
 <span data-ttu-id="33a63-119">显示所选表的说明。</span><span class="sxs-lookup"><span data-stu-id="33a63-119">Shows a description of the selected table.</span></span> <span data-ttu-id="33a63-120">若要查看或编辑完整的说明，请单击相应的说明，再单击属性右侧的省略号 (…)  。</span><span class="sxs-lookup"><span data-stu-id="33a63-120">To see the entire description, or to edit it, click the description and then click the ellipses **(...)** to the right of the property.</span></span>  
  
 <span data-ttu-id="33a63-121">**架构**</span><span class="sxs-lookup"><span data-stu-id="33a63-121">**Schema**</span></span>  
 <span data-ttu-id="33a63-122">显示此表所属的架构的名称。</span><span class="sxs-lookup"><span data-stu-id="33a63-122">Shows the name of the schema to which this table belongs.</span></span> <span data-ttu-id="33a63-123">（仅适用于 Microsoft SQL Server。）</span><span class="sxs-lookup"><span data-stu-id="33a63-123">(Applies only to Microsoft SQL Server.)</span></span>  
  
 <span data-ttu-id="33a63-124">**服务器名称**</span><span class="sxs-lookup"><span data-stu-id="33a63-124">**Server Name**</span></span>  
 <span data-ttu-id="33a63-125">显示用于数据源的服务器的名称。</span><span class="sxs-lookup"><span data-stu-id="33a63-125">Shows the name of the server for the data source.</span></span>  
  
 <span data-ttu-id="33a63-126">**表设计器类别**</span><span class="sxs-lookup"><span data-stu-id="33a63-126">**Table Designer Category**</span></span>  
 <span data-ttu-id="33a63-127">展开此项可显示“标识列”  、“可编制索引”  和“是复制的”  的属性。</span><span class="sxs-lookup"><span data-stu-id="33a63-127">Expands to show properties for **Identity Column**, **Is Indexable**, and **Is Replicated**.</span></span>  
  
 <span data-ttu-id="33a63-128">**标识列**</span><span class="sxs-lookup"><span data-stu-id="33a63-128">**Identity Column**</span></span>  
 <span data-ttu-id="33a63-129">显示用作表的标识列的列。</span><span class="sxs-lookup"><span data-stu-id="33a63-129">Shows the column used as the table's identity column.</span></span> <span data-ttu-id="33a63-130">若要更改标识列，请从下拉列表中进行选择。</span><span class="sxs-lookup"><span data-stu-id="33a63-130">To change the identity column, choose from the drop-down list.</span></span> <span data-ttu-id="33a63-131">该列表中只显示数值数据类型的列。</span><span class="sxs-lookup"><span data-stu-id="33a63-131">Only columns of a numeric data type will show in the list.</span></span>  
  
 <span data-ttu-id="33a63-132">**可编制索引**</span><span class="sxs-lookup"><span data-stu-id="33a63-132">**Is Indexable**</span></span>  
 <span data-ttu-id="33a63-133">显示该表是否可以索引。</span><span class="sxs-lookup"><span data-stu-id="33a63-133">Shows whether the table can be indexed.</span></span> <span data-ttu-id="33a63-134">如果表不可索引，则可能是因为您不是该表的所有者或因为该表包含具有 text、ntext 或 image 数据类型的列。</span><span class="sxs-lookup"><span data-stu-id="33a63-134">If the table is not indexable it may be because you are not the table owner or because the table contains columns with data types of text, ntext, or image.</span></span>  
  
 <span data-ttu-id="33a63-135">**是复制的**</span><span class="sxs-lookup"><span data-stu-id="33a63-135">**Is Replicated**</span></span>  
 <span data-ttu-id="33a63-136">显示是否在另一个位置复制了该表。</span><span class="sxs-lookup"><span data-stu-id="33a63-136">Shows whether the table is replicated in another location.</span></span>  
  
 <span data-ttu-id="33a63-137">**常规数据空间规范类别**</span><span class="sxs-lookup"><span data-stu-id="33a63-137">**Regular Data Space Specification Category**</span></span>  
 <span data-ttu-id="33a63-138">展开此项可显示“（数据空间类型）”  、“文件组或分区方案名称”  和“分区列列表”  的属性。</span><span class="sxs-lookup"><span data-stu-id="33a63-138">Expands to show properties for **(Data Space Type)**, **Filegroup or Partition Scheme Name**, and **Partition Column List**.</span></span>  
  
 <span data-ttu-id="33a63-139">**(数据空间类型)**</span><span class="sxs-lookup"><span data-stu-id="33a63-139">**(Data Space Type)**</span></span>  
 <span data-ttu-id="33a63-140">显示是使用文件组还是使用分区方案存储此表。</span><span class="sxs-lookup"><span data-stu-id="33a63-140">Shows whether this table is stored using a filegroup or partition scheme.</span></span>  
  
 <span data-ttu-id="33a63-141">**文件组或分区方案名称**</span><span class="sxs-lookup"><span data-stu-id="33a63-141">**Filegroup or Partition Scheme Name**</span></span>  
 <span data-ttu-id="33a63-142">显示文件组或分区方案的名称。</span><span class="sxs-lookup"><span data-stu-id="33a63-142">Shows the name of the filegroup or partition scheme.</span></span>  
  
 <span data-ttu-id="33a63-143">**分区列列表**</span><span class="sxs-lookup"><span data-stu-id="33a63-143">**Partition Column List**</span></span>  
 <span data-ttu-id="33a63-144">通过此项可访问“分区列列表”  对话框。</span><span class="sxs-lookup"><span data-stu-id="33a63-144">Provides access to the **Partition Column List** dialog box.</span></span>  
  
 <span data-ttu-id="33a63-145">**行 GUID 列**</span><span class="sxs-lookup"><span data-stu-id="33a63-145">**Row GUID Column**</span></span>  
 <span data-ttu-id="33a63-146">显示由 Microsoft SQL Server 用作表的 ROWGUID 列的列。</span><span class="sxs-lookup"><span data-stu-id="33a63-146">Shows the column used by Microsoft SQL Server as the table's ROWGUID column.</span></span> <span data-ttu-id="33a63-147">若要更改 ROWGUID 列，请从下拉列表中进行选择。</span><span class="sxs-lookup"><span data-stu-id="33a63-147">To change the ROWGUID column, choose from the drop-down list.</span></span> <span data-ttu-id="33a63-148">（仅适用于 SQL Server 7.0 或更高版本。）</span><span class="sxs-lookup"><span data-stu-id="33a63-148">(Applies only to SQL Server 7.0 or higher.)</span></span>  
  
 <span data-ttu-id="33a63-149">**Text/Image 文件组**</span><span class="sxs-lookup"><span data-stu-id="33a63-149">**Text/Image Filegroup**</span></span>  
 <span data-ttu-id="33a63-150">提供一个下拉列表，您可以从中为具有 text 或 image 数据类型的列选择文件组。</span><span class="sxs-lookup"><span data-stu-id="33a63-150">Provides a drop-down list from which you can choose the filegroup for columns that have text or image data types.</span></span> <span data-ttu-id="33a63-151">如果该表是使用分区方案存储的，则将此字段保留为空。</span><span class="sxs-lookup"><span data-stu-id="33a63-151">If the table is stored using a partition scheme, leave this field blank.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="33a63-152">另请参阅</span><span class="sxs-lookup"><span data-stu-id="33a63-152">See Also</span></span>  
 [<span data-ttu-id="33a63-153">设计表 (Visual Database Tools)</span><span class="sxs-lookup"><span data-stu-id="33a63-153">Design Tables &#40;Visual Database Tools&#41;</span></span>](visual-database-tools.md)  
  
  
