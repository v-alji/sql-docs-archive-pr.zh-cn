---
title: 修改唯一约束 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: table-view-index
ms.topic: conceptual
helpviewer_keywords:
- modifying constraints
- UNIQUE constraints [SQL Server], modifying
- constraints [SQL Server], modifying
- constraints [SQL Server], unique
ms.assetid: fddbdc9e-958b-4614-8e88-6ca205d64a4e
author: stevestein
ms.author: sstein
ms.openlocfilehash: 74b044202f7e8e9bc762f025833cf2d0ff84c4c8
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87591827"
---
# <a name="modify-unique-constraints"></a><span data-ttu-id="34d43-102">修改唯一约束</span><span class="sxs-lookup"><span data-stu-id="34d43-102">Modify Unique Constraints</span></span>
  <span data-ttu-id="34d43-103">您可以使用 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 或 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 在 [!INCLUDE[tsql](../../includes/tsql-md.md)]中修改唯一约束。</span><span class="sxs-lookup"><span data-stu-id="34d43-103">You can modify a unique constraint in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span>  
  
 <span data-ttu-id="34d43-104">**本主题内容**</span><span class="sxs-lookup"><span data-stu-id="34d43-104">**In This Topic**</span></span>  
  
-   <span data-ttu-id="34d43-105">**开始之前：**</span><span class="sxs-lookup"><span data-stu-id="34d43-105">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="34d43-106">安全性</span><span class="sxs-lookup"><span data-stu-id="34d43-106">Security</span></span>](#Security)  
  
-   <span data-ttu-id="34d43-107">**使用以下工具修改唯一约束：**</span><span class="sxs-lookup"><span data-stu-id="34d43-107">**To modify a unique constraint using:**</span></span>  
  
     [<span data-ttu-id="34d43-108">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="34d43-108">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="34d43-109">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="34d43-109">Transact-SQL</span></span>](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="34d43-110">开始之前</span><span class="sxs-lookup"><span data-stu-id="34d43-110">Before You Begin</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="34d43-111">Security</span><span class="sxs-lookup"><span data-stu-id="34d43-111">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="34d43-112">权限</span><span class="sxs-lookup"><span data-stu-id="34d43-112">Permissions</span></span>  
 <span data-ttu-id="34d43-113">需要对表的 ALTER 权限。</span><span class="sxs-lookup"><span data-stu-id="34d43-113">Requires ALTER permission on the table.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="34d43-114">使用 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="34d43-114">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-modify-a-unique-constraint"></a><span data-ttu-id="34d43-115">修改唯一约束</span><span class="sxs-lookup"><span data-stu-id="34d43-115">To modify a unique constraint</span></span>  
  
1.  <span data-ttu-id="34d43-116">在“对象资源管理器”  中，右键单击包含唯一约束的表，然后选择“设计”  。</span><span class="sxs-lookup"><span data-stu-id="34d43-116">In the **Object Explorer**, right-click the table containing the unique constraint and select **Design**.</span></span>  
  
2.  <span data-ttu-id="34d43-117">在“表设计器”菜单上，单击“索引/键...”   。</span><span class="sxs-lookup"><span data-stu-id="34d43-117">On the **Table Designer** menu, click **Indexes/Keys...**.</span></span>  
  
3.  <span data-ttu-id="34d43-118">在“索引/键”  对话框中的“选定的主/唯一键或索引”  下，选择要编辑的约束。</span><span class="sxs-lookup"><span data-stu-id="34d43-118">In the **Indexes/Keys** dialog box, under **Selected Primary/Unique Key or Index**, select the constraint you wish to edit.</span></span>  
  
4.  <span data-ttu-id="34d43-119">完成下表中的相应操作：</span><span class="sxs-lookup"><span data-stu-id="34d43-119">Complete an action from the following table:</span></span>  
  
    |<span data-ttu-id="34d43-120">目标</span><span class="sxs-lookup"><span data-stu-id="34d43-120">To</span></span>|<span data-ttu-id="34d43-121">需要遵循的步骤</span><span class="sxs-lookup"><span data-stu-id="34d43-121">Follow these steps</span></span>|  
    |--------|------------------------|  
    |<span data-ttu-id="34d43-122">更改与约束关联的列</span><span class="sxs-lookup"><span data-stu-id="34d43-122">Change the columns that the constraint is associated with</span></span>|<span data-ttu-id="34d43-123">1) 在“(常规)”下的网格中，单击“列”，再单击属性右侧的省略号 (…)    。</span><span class="sxs-lookup"><span data-stu-id="34d43-123">1) In the grid under **(General)**, click **Columns** and then click the ellipses **(...)** to the right of the property.</span></span><br /><br /> <span data-ttu-id="34d43-124">2) 在“索引列”  对话框中，为索引指定新列和/或排序顺序。</span><span class="sxs-lookup"><span data-stu-id="34d43-124">2) In the **Index Columns** dialog box, specify the new column or sort order or both for the index.</span></span>|  
    |<span data-ttu-id="34d43-125">重命名约束</span><span class="sxs-lookup"><span data-stu-id="34d43-125">Rename the constraint</span></span>|<span data-ttu-id="34d43-126">在 **“标识”** 下的网格中，在 **“名称”** 框中键入新名称。</span><span class="sxs-lookup"><span data-stu-id="34d43-126">In the grid under **Identity**, type a new name in the **Name** box.</span></span> <span data-ttu-id="34d43-127">确保新名称不与“选定的主/唯一键或索引”  列表中的名称重复。</span><span class="sxs-lookup"><span data-stu-id="34d43-127">Make sure that your new name does not duplicate a name in the **Selected Primary/Unique Key or Index** list.</span></span>|  
    |<span data-ttu-id="34d43-128">设置聚集选项</span><span class="sxs-lookup"><span data-stu-id="34d43-128">Set the clustered option</span></span>|<span data-ttu-id="34d43-129">在“表设计器”  下的网格中，选择“创建为群集索引”  ，并从下拉列表中选择“是”创建群集索引，或选择“否”创建非聚集索引。</span><span class="sxs-lookup"><span data-stu-id="34d43-129">In the grid under **Table Designer**, select **Create As Clustered** and from the dropdown choose Yes to create a clustered index and No to create a nonclustered one.</span></span> <span data-ttu-id="34d43-130">对于每个表，只允许存在一个聚集索引。</span><span class="sxs-lookup"><span data-stu-id="34d43-130">Only one clustered index can exist per table.</span></span> <span data-ttu-id="34d43-131">如果此表中已经存在聚集索引，则您必须首先对原始索引清除此设置。</span><span class="sxs-lookup"><span data-stu-id="34d43-131">If a clustered index already exists in this table, you must clear this setting on the original index.</span></span>|  
    |<span data-ttu-id="34d43-132">定义填充因子</span><span class="sxs-lookup"><span data-stu-id="34d43-132">Define a fill factor</span></span>|<span data-ttu-id="34d43-133">在 **“表设计器”** 下的网格中，展开 **“填充规范”** 类别，然后在 **“填充因子”** 框中键入一个 0 到 100 之间的整数。</span><span class="sxs-lookup"><span data-stu-id="34d43-133">In the grid under **Table Designer**, expand the **Fill Specification** category and type an integer from 0 to 100 in the **Fill Factor** box.</span></span>|  
  
5.  <span data-ttu-id="34d43-134">在“文件”  菜单上，单击“保存”  以保存表名  。</span><span class="sxs-lookup"><span data-stu-id="34d43-134">On the **File** menu, click **Save**_table name_.</span></span>  
  
##  <a name="to-modify-a-unique-constraint"></a><a name="TsqlProcedure"></a> <span data-ttu-id="34d43-135">**修改唯一约束**</span><span class="sxs-lookup"><span data-stu-id="34d43-135">**To modify a unique constraint**</span></span>  
  
 <span data-ttu-id="34d43-136">若要使用 Transact-SQL 修改 UNIQUE 约束，必须首先删除现有的 UNIQUE 约束，然后用新定义重新创建。</span><span class="sxs-lookup"><span data-stu-id="34d43-136">To modify a UNIQUE constraint using Transact-SQL, you must first delete the existing UNIQUE constraint and then re-create it with the new definition.</span></span> <span data-ttu-id="34d43-137">有关详细信息，请参阅 [Delete Unique Constraints](delete-unique-constraints.md) 和 [Create Unique Constraints](create-unique-constraints.md)。</span><span class="sxs-lookup"><span data-stu-id="34d43-137">For more information, see [Delete Unique Constraints](delete-unique-constraints.md) and [Create Unique Constraints](create-unique-constraints.md).</span></span>  
  
###  <a name="TsqlExample"></a>  
