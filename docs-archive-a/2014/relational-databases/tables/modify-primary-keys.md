---
title: 修改主键 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: table-view-index
ms.topic: conceptual
helpviewer_keywords:
- modifying primary keys
- primary keys [SQL Server], modifying
ms.assetid: 8e2a15ba-1cd1-4408-b860-16c3ee37d635
author: stevestein
ms.author: sstein
ms.openlocfilehash: f24deeac45491f9097d90ee0407464f928a0713b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87576587"
---
# <a name="modify-primary-keys"></a><span data-ttu-id="8650e-102">修改主键</span><span class="sxs-lookup"><span data-stu-id="8650e-102">Modify Primary Keys</span></span>
  <span data-ttu-id="8650e-103">您可以通过使用 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 或 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 修改 [!INCLUDE[tsql](../../includes/tsql-md.md)]中的主键。</span><span class="sxs-lookup"><span data-stu-id="8650e-103">You can modify a primary key in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span> <span data-ttu-id="8650e-104">您可以通过更改列顺序、索引名称、聚集选项或填充因子，修改表的主键。</span><span class="sxs-lookup"><span data-stu-id="8650e-104">You can modify the primary key of a table by changing the column order, index name, clustered option, or fill factor.</span></span>  
  
 <span data-ttu-id="8650e-105">**本主题内容**</span><span class="sxs-lookup"><span data-stu-id="8650e-105">**In This Topic**</span></span>  
  
-   <span data-ttu-id="8650e-106">**开始之前：**</span><span class="sxs-lookup"><span data-stu-id="8650e-106">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="8650e-107">安全性</span><span class="sxs-lookup"><span data-stu-id="8650e-107">Security</span></span>](#Security)  
  
-   <span data-ttu-id="8650e-108">**使用以下工具修改主键：**</span><span class="sxs-lookup"><span data-stu-id="8650e-108">**To modify a primary key, using:**</span></span>  
  
     [<span data-ttu-id="8650e-109">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="8650e-109">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="8650e-110">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="8650e-110">Transact-SQL</span></span>](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="8650e-111">开始之前</span><span class="sxs-lookup"><span data-stu-id="8650e-111">Before You Begin</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="8650e-112">Security</span><span class="sxs-lookup"><span data-stu-id="8650e-112">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="8650e-113">权限</span><span class="sxs-lookup"><span data-stu-id="8650e-113">Permissions</span></span>  
 <span data-ttu-id="8650e-114">需要对表的 ALTER 权限。</span><span class="sxs-lookup"><span data-stu-id="8650e-114">Requires ALTER permission on the table.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="8650e-115">使用 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="8650e-115">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-modify-a-primary-key"></a><span data-ttu-id="8650e-116">修改主键</span><span class="sxs-lookup"><span data-stu-id="8650e-116">To modify a primary key</span></span>  
  
1.  <span data-ttu-id="8650e-117">打开要修改其主键的表的表设计器，在此表设计器中单击右键，然后从快捷菜单中选择“索引/键”  。</span><span class="sxs-lookup"><span data-stu-id="8650e-117">Open the Table Designer for the table whose primary key you want to modify, right-click in the Table Designer, and choose **Indexes/Keys** from the shortcut menu.</span></span>  
  
2.  <span data-ttu-id="8650e-118">在“索引/键”  对话框中，从“选定的主/唯一键或索引”  列表中选择主键索引。</span><span class="sxs-lookup"><span data-stu-id="8650e-118">In the **Indexes/Keys** dialog box, select the primary key index from the **Selected Primary/Unique Key or Index** list.</span></span>  
  
3.  <span data-ttu-id="8650e-119">完成下表中的相应操作：</span><span class="sxs-lookup"><span data-stu-id="8650e-119">Complete an action from the following table:</span></span>  
  
    |<span data-ttu-id="8650e-120">目标</span><span class="sxs-lookup"><span data-stu-id="8650e-120">To</span></span>|<span data-ttu-id="8650e-121">需要遵循的步骤</span><span class="sxs-lookup"><span data-stu-id="8650e-121">Follow these steps</span></span>|  
    |--------|------------------------|  
    |<span data-ttu-id="8650e-122">重命名主键</span><span class="sxs-lookup"><span data-stu-id="8650e-122">Rename the primary key</span></span>|<span data-ttu-id="8650e-123">在 **“名称”** 框中键入新名称。</span><span class="sxs-lookup"><span data-stu-id="8650e-123">Type a new name in the **Name** box.</span></span> <span data-ttu-id="8650e-124">确保新名称不与“选定的主/唯一键或索引”  列表中的名称重复。</span><span class="sxs-lookup"><span data-stu-id="8650e-124">Make sure that your new name does not duplicate a name in the **Selected Primary/Unique Key or Index** list.</span></span>|  
    |<span data-ttu-id="8650e-125">设置聚集选项</span><span class="sxs-lookup"><span data-stu-id="8650e-125">Set the clustered option</span></span>|<span data-ttu-id="8650e-126">若要为主键创建聚集索引，请选择“创建为聚集的”  ，再从下拉列表框中选择相应的选项。</span><span class="sxs-lookup"><span data-stu-id="8650e-126">To create a clustered index for the primary key, select **Create as CLUSTERED**, and select the option from the drop-down list box.</span></span> <span data-ttu-id="8650e-127">对于每个表，只允许存在一个聚集索引。</span><span class="sxs-lookup"><span data-stu-id="8650e-127">Only one clustered index can exist per table.</span></span> <span data-ttu-id="8650e-128">如果此选项对您的索引不可用，则您必须首先对现有的聚集索引清除此设置。</span><span class="sxs-lookup"><span data-stu-id="8650e-128">If this option is not available for your index, you must first clear this setting on the existing clustered index.</span></span><br /><br /> <span data-ttu-id="8650e-129">如果未选择此选项，则创建唯一的非聚集索引。</span><span class="sxs-lookup"><span data-stu-id="8650e-129">If this option is not selected, a unique nonclustered index is created.</span></span>|  
    |<span data-ttu-id="8650e-130">定义填充因子</span><span class="sxs-lookup"><span data-stu-id="8650e-130">Define a fill factor</span></span>|<span data-ttu-id="8650e-131">展开 **“填充规范”** 类别，然后在 **“填充因子”** 框中键入一个 0 到 100 之间的整数。</span><span class="sxs-lookup"><span data-stu-id="8650e-131">Expand the **Fill Specification** category and type an integer from 0 to 100 in the **Fill factor** box.</span></span> <span data-ttu-id="8650e-132">有关填充因子及其用途的详细信息，请参阅 [为索引指定填充因子](../indexes/specify-fill-factor-for-an-index.md)。</span><span class="sxs-lookup"><span data-stu-id="8650e-132">For more information about fill factors and their uses, see [Specify Fill Factor for an Index](../indexes/specify-fill-factor-for-an-index.md).</span></span>|  
    |<span data-ttu-id="8650e-133">更改列顺序</span><span class="sxs-lookup"><span data-stu-id="8650e-133">Change the column order</span></span>|<span data-ttu-id="8650e-134">选择“列”，再单击属性右侧的省略号 (…)   。</span><span class="sxs-lookup"><span data-stu-id="8650e-134">Select **Columns**, and then click the ellipses **(...)** to the right of the property.</span></span> <span data-ttu-id="8650e-135">在  **“索引列”** 对话框中，将这些列从主键中删除。</span><span class="sxs-lookup"><span data-stu-id="8650e-135">In the  **Index Columns** dialog box, remove the columns from the primary key.</span></span> <span data-ttu-id="8650e-136">然后，按所需顺序重新添加这些列。</span><span class="sxs-lookup"><span data-stu-id="8650e-136">Then add the columns back in the order you want.</span></span> <span data-ttu-id="8650e-137">若要将某列从键中移除，只需将其列名从 **“列”** 名称列表名称中移除即可。</span><span class="sxs-lookup"><span data-stu-id="8650e-137">To remove a column from the key, simply remove the column name from the **Column** name list.</span></span>|  
  
4.  <span data-ttu-id="8650e-138">在“文件”  菜单上，单击“保存”  以保存表名  。</span><span class="sxs-lookup"><span data-stu-id="8650e-138">On the **File** menu, click **Save**_table name_.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="8650e-139">使用 Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="8650e-139">Using Transact-SQL</span></span>  
 <span data-ttu-id="8650e-140">**修改主键**</span><span class="sxs-lookup"><span data-stu-id="8650e-140">**To modify a primary key**</span></span>  
  
 <span data-ttu-id="8650e-141">若要使用 Transact-SQL 修改 PRIMARY KEY 约束，必须先删除现有的 PRIMARY KEY 约束，然后再用新定义重新创建该约束。</span><span class="sxs-lookup"><span data-stu-id="8650e-141">To modify a PRIMARY KEY constraint using Transact-SQL, you must first delete the existing PRIMARY KEY constraint and then re-create it with the new definition.</span></span> <span data-ttu-id="8650e-142">有关详细信息，请参阅 [Delete Primary Keys](delete-primary-keys.md) 和 [Create Primary Keys](create-primary-keys.md)。</span><span class="sxs-lookup"><span data-stu-id="8650e-142">For more information, see [Delete Primary Keys](delete-primary-keys.md) and [Create Primary Keys](create-primary-keys.md).</span></span>  
  
###  <a name="TsqlExample"></a>  
