---
title: 修改 CHECK 约束 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: table-view-index
ms.topic: conceptual
helpviewer_keywords:
- CHECK constraints, modifying
- modifying constraints
- constraints [SQL Server], check
- constraints [SQL Server], modifying
ms.assetid: f22daef8-e350-40ef-8ff0-b5f87d1d9e56
author: stevestein
ms.author: sstein
ms.openlocfilehash: 8377c80590612c8b68c315f7c37823eb8f5c5093
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87587730"
---
# <a name="modify-check-constraints"></a><span data-ttu-id="1f815-102">修改 CHECK 约束</span><span class="sxs-lookup"><span data-stu-id="1f815-102">Modify Check Constraints</span></span>
  <span data-ttu-id="1f815-103">当您希望更改约束表达式或更改对特定条件启用或禁用约束的选项时，可通过使用 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 或 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] ，在 [!INCLUDE[tsql](../../includes/tsql-md.md)] 中修改 CHECK 约束。</span><span class="sxs-lookup"><span data-stu-id="1f815-103">You can modify a check constraint in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)] when you want to change the constraint expression or the options that enable or disable the constraint for specific conditions.</span></span>  
  
 <span data-ttu-id="1f815-104">**本主题内容**</span><span class="sxs-lookup"><span data-stu-id="1f815-104">**In This Topic**</span></span>  
  
-   <span data-ttu-id="1f815-105">**开始之前：**</span><span class="sxs-lookup"><span data-stu-id="1f815-105">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="1f815-106">安全性</span><span class="sxs-lookup"><span data-stu-id="1f815-106">Security</span></span>](#Security)  
  
-   <span data-ttu-id="1f815-107">**使用以下工具修改 CHECK 约束：**</span><span class="sxs-lookup"><span data-stu-id="1f815-107">**To modify a check constraint using:**</span></span>  
  
     [<span data-ttu-id="1f815-108">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="1f815-108">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="1f815-109">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="1f815-109">Transact-SQL</span></span>](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="1f815-110">开始之前</span><span class="sxs-lookup"><span data-stu-id="1f815-110">Before You Begin</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="1f815-111">Security</span><span class="sxs-lookup"><span data-stu-id="1f815-111">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="1f815-112">权限</span><span class="sxs-lookup"><span data-stu-id="1f815-112">Permissions</span></span>  
 <span data-ttu-id="1f815-113">需要对表的 ALTER 权限。</span><span class="sxs-lookup"><span data-stu-id="1f815-113">Requires ALTER permission on the table.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="1f815-114">使用 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="1f815-114">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-modify-a-check-constraint"></a><span data-ttu-id="1f815-115">修改 CHECK 约束</span><span class="sxs-lookup"><span data-stu-id="1f815-115">To modify a check constraint</span></span>  
  
1.  <span data-ttu-id="1f815-116">在“对象资源管理器”  中，右键单击包含 CHECK 约束的表，然后选择“设计”  。</span><span class="sxs-lookup"><span data-stu-id="1f815-116">In the **Object Explorer**, right-click the table containing the check constraint and select **Design**.</span></span>  
  
2.  <span data-ttu-id="1f815-117">在“表设计器”菜单上，单击“CHECK 约束…”   。</span><span class="sxs-lookup"><span data-stu-id="1f815-117">On the **Table Designer** menu, click **Check Constraints...**.</span></span>  
  
3.  <span data-ttu-id="1f815-118">在 **“CHECK 约束”** 对话框中，在 **“选定的 CHECK 约束”** 下选择要编辑的约束。</span><span class="sxs-lookup"><span data-stu-id="1f815-118">In the **Check Constraints** dialog box, under **Selected Check Constraint**, select the constraint you wish to edit.</span></span>  
  
4.  <span data-ttu-id="1f815-119">完成下表中的相应操作：</span><span class="sxs-lookup"><span data-stu-id="1f815-119">Complete an action from the following table:</span></span>  
  
    |<span data-ttu-id="1f815-120">目标</span><span class="sxs-lookup"><span data-stu-id="1f815-120">To</span></span>|<span data-ttu-id="1f815-121">需要遵循的步骤</span><span class="sxs-lookup"><span data-stu-id="1f815-121">Follow these steps</span></span>|  
    |--------|------------------------|  
    |<span data-ttu-id="1f815-122">编辑约束表达式</span><span class="sxs-lookup"><span data-stu-id="1f815-122">Edit the constraint expression</span></span>|<span data-ttu-id="1f815-123">在 **“表达式”** 字段中键入新的表达式。</span><span class="sxs-lookup"><span data-stu-id="1f815-123">Type the new expression in the **Expression** field.</span></span>|  
    |<span data-ttu-id="1f815-124">重命名约束</span><span class="sxs-lookup"><span data-stu-id="1f815-124">Rename the constraint</span></span>|<span data-ttu-id="1f815-125">在 **“名称”** 字段中键入新的名称。</span><span class="sxs-lookup"><span data-stu-id="1f815-125">Type a new name in the **Name** field.</span></span>|  
    |<span data-ttu-id="1f815-126">将该约束应用于现有数据</span><span class="sxs-lookup"><span data-stu-id="1f815-126">Apply the constraint to existing data</span></span>|<span data-ttu-id="1f815-127">选择 **“在创建或启用时检查现有数据”** 选项。</span><span class="sxs-lookup"><span data-stu-id="1f815-127">Select the **Check Existing Data on Creation or Enabling** option.</span></span>|  
    |<span data-ttu-id="1f815-128">向表中添加新数据或更新表中现有数据时禁用该约束。</span><span class="sxs-lookup"><span data-stu-id="1f815-128">Disable the constraint when new data is added to the table or when existing data is updated in the table.</span></span>|<span data-ttu-id="1f815-129">清除 **“对 INSERT 和 UPDATE 强制约束”** 选项。</span><span class="sxs-lookup"><span data-stu-id="1f815-129">Clear the **Enforce Constraint for INSERTs and UPDATEs** option.</span></span>|  
    |<span data-ttu-id="1f815-130">当复制代理在表中插入或更新数据时，禁用该约束。</span><span class="sxs-lookup"><span data-stu-id="1f815-130">Disable the constraint when a replication agent inserts or updates data in your table.</span></span>|<span data-ttu-id="1f815-131">清除 **“强制用于复制”** 选项。</span><span class="sxs-lookup"><span data-stu-id="1f815-131">Clear the **Enforce For Replication** option.</span></span>|  
  
    > [!NOTE]  
    >  <span data-ttu-id="1f815-132">对于 CHECK 约束，有些数据库具有不同的功能。</span><span class="sxs-lookup"><span data-stu-id="1f815-132">Some databases have different functionality for check constraints.</span></span>  
  
5.  <span data-ttu-id="1f815-133">单击“关闭”  。</span><span class="sxs-lookup"><span data-stu-id="1f815-133">Click **Close**.</span></span>  
  
6.  <span data-ttu-id="1f815-134">在“文件”  菜单上，单击“保存”  以保存表名  。</span><span class="sxs-lookup"><span data-stu-id="1f815-134">On the **File** menu, click **Save**_table name_.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="1f815-135">使用 Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="1f815-135">Using Transact-SQL</span></span>  
 <span data-ttu-id="1f815-136">**修改 CHECK 约束**</span><span class="sxs-lookup"><span data-stu-id="1f815-136">**To modify a check constraint**</span></span>  
  
 <span data-ttu-id="1f815-137">必须首先删除现有的 `CHECK` 约束，然后使用新定义重新创建，才能使用 [!INCLUDE[tsql](../../includes/tsql-md.md)]修改 `CHECK` 约束。</span><span class="sxs-lookup"><span data-stu-id="1f815-137">To modify a `CHECK` constraint using [!INCLUDE[tsql](../../includes/tsql-md.md)], you must first delete the existing `CHECK` constraint and then re-create it with the new definition.</span></span> <span data-ttu-id="1f815-138">有关详细信息，请参阅 [删除 CHECK 约束](delete-check-constraints.md) 和 [创建 CHECK 约束](create-check-constraints.md)。</span><span class="sxs-lookup"><span data-stu-id="1f815-138">For more information, see [Delete Check Constraints](delete-check-constraints.md) and [Create Check Constraints](create-check-constraints.md).</span></span>  
  
###  <a name="TsqlExample"></a>  
