---
title: 复制表 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: table-view-index
ms.topic: conceptual
helpviewer_keywords:
- copying tables
- tables [SQL Server], duplicating
- duplicating tables
- table copying [SQL Server]
ms.assetid: c6b07423-d1e5-4e5e-8681-5088921f5df3
author: stevestein
ms.author: sstein
ms.openlocfilehash: 793a38416f86a5b43a3e3bb2420127d7acf2af1f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87580110"
---
# <a name="duplicate-tables"></a><span data-ttu-id="61b88-102">复制表</span><span class="sxs-lookup"><span data-stu-id="61b88-102">Duplicate Tables</span></span>
  <span data-ttu-id="61b88-103">您可以使用 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 或 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] ，通过创建新表后从现有表复制列信息，在 [!INCLUDE[tsql](../../includes/tsql-md.md)] 中复制现有表。</span><span class="sxs-lookup"><span data-stu-id="61b88-103">You can duplicate an existing table in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)] by creating a new table and then copying column information from an existing table.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="61b88-104">此操作仅复制表的结构，不复制任何表行。</span><span class="sxs-lookup"><span data-stu-id="61b88-104">This operation duplicates only the structure of a table; it does not duplicate any table rows.</span></span>  
  
 <span data-ttu-id="61b88-105">**本主题内容**</span><span class="sxs-lookup"><span data-stu-id="61b88-105">**In This Topic**</span></span>  
  
-   <span data-ttu-id="61b88-106">**开始之前：**</span><span class="sxs-lookup"><span data-stu-id="61b88-106">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="61b88-107">安全性</span><span class="sxs-lookup"><span data-stu-id="61b88-107">Security</span></span>](#Security)  
  
-   <span data-ttu-id="61b88-108">**使用以下工具复制表：**</span><span class="sxs-lookup"><span data-stu-id="61b88-108">**To duplicate a table, using:**</span></span>  
  
     [<span data-ttu-id="61b88-109">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="61b88-109">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="61b88-110">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="61b88-110">Transact-SQL</span></span>](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="61b88-111">开始之前</span><span class="sxs-lookup"><span data-stu-id="61b88-111">Before You Begin</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="61b88-112">Security</span><span class="sxs-lookup"><span data-stu-id="61b88-112">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="61b88-113">权限</span><span class="sxs-lookup"><span data-stu-id="61b88-113">Permissions</span></span>  
 <span data-ttu-id="61b88-114">在目标数据库中要求 CREATE TABLE 权限。</span><span class="sxs-lookup"><span data-stu-id="61b88-114">Requires CREATE TABLE permission in the destination database.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="61b88-115">使用 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="61b88-115">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-duplicate-a-table"></a><span data-ttu-id="61b88-116">复制表</span><span class="sxs-lookup"><span data-stu-id="61b88-116">To duplicate a table</span></span>  
  
1.  <span data-ttu-id="61b88-117">请确保您已经连接到要在其中创建表的数据库并在对象资源管理器中选中该数据库。</span><span class="sxs-lookup"><span data-stu-id="61b88-117">Make sure you are connected to the database in which you want to create the table and that the database is selected in Object Explorer.</span></span>  
  
2.  <span data-ttu-id="61b88-118">在对象资源管理器中，右键单击  “表”，再单击  “新建表”。</span><span class="sxs-lookup"><span data-stu-id="61b88-118">In Object Explorer, right-click **Tables** and click **New Table**.</span></span>  
  
3.  <span data-ttu-id="61b88-119">在对象资源管理器中，右键单击要复制的表，再单击  “设计”。</span><span class="sxs-lookup"><span data-stu-id="61b88-119">In Object Explorer right-click the table you want to copy and click **Design**.</span></span>  
  
4.  <span data-ttu-id="61b88-120">在现有表中选择列，在 **“编辑”** 菜单上单击 **“复制”** 。</span><span class="sxs-lookup"><span data-stu-id="61b88-120">Select the columns in the existing table and, from the **Edit** menu, click **Copy**.</span></span>  
  
5.  <span data-ttu-id="61b88-121">切换回新表并选择第一行。</span><span class="sxs-lookup"><span data-stu-id="61b88-121">Switch back to the new table and select the first row.</span></span>  
  
6.  <span data-ttu-id="61b88-122">在 **“编辑”** 菜单上，单击 **“粘贴”** 。</span><span class="sxs-lookup"><span data-stu-id="61b88-122">From the **Edit** menu, click **Paste**.</span></span>  
  
7.  <span data-ttu-id="61b88-123">从“文件”  菜单上，单击“保存”  表格名称  。</span><span class="sxs-lookup"><span data-stu-id="61b88-123">From the **File** menu, click **Save**_table name_.</span></span>  
  
8.  <span data-ttu-id="61b88-124">在 **“选择名称”** 对话框中，键入新表的名称，然后单击 **“确定”** 。</span><span class="sxs-lookup"><span data-stu-id="61b88-124">In the **Choose Name** dialog box, type a name for the new table and click **OK**.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="61b88-125">使用 Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="61b88-125">Using Transact-SQL</span></span>  
  
#### <a name="to-duplicate-a-table-in-query-editor"></a><span data-ttu-id="61b88-126">在查询编辑器中复制表</span><span class="sxs-lookup"><span data-stu-id="61b88-126">To duplicate a table in Query Editor</span></span>  
  
1.  <span data-ttu-id="61b88-127">请确保您已经连接到要在其中创建表的数据库并在对象资源管理器中选中该数据库。</span><span class="sxs-lookup"><span data-stu-id="61b88-127">Make sure you are connected to the database in which you want to create the table and that the database is selected in Object Explorer.</span></span>  
  
2.  <span data-ttu-id="61b88-128">右键单击要复制的表，指向  “编写表脚本为”，然后指向  “CREATE 到”，再选择  “新查询编辑器窗口”。</span><span class="sxs-lookup"><span data-stu-id="61b88-128">Right-click the table you wish to duplicate, point to **Script Table as**, then point to **CREATE to**, and then select **New Query Editor Window**.</span></span>  
  
3.  <span data-ttu-id="61b88-129">更改表的名称。</span><span class="sxs-lookup"><span data-stu-id="61b88-129">Change the name of the table.</span></span>  
  
4.  <span data-ttu-id="61b88-130">删除新表中不需要的列。</span><span class="sxs-lookup"><span data-stu-id="61b88-130">Remove any columns that are not needed in the new table.</span></span>  
  
5.  <span data-ttu-id="61b88-131">单击“执行”  。</span><span class="sxs-lookup"><span data-stu-id="61b88-131">Click **Execute**.</span></span>  
  
  
