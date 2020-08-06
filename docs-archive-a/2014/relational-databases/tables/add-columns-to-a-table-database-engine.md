---
title: 向表中添加列（数据库引擎）| Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: table-view-index
ms.topic: conceptual
helpviewer_keywords:
- inserting columns
- columns [SQL Server], adding
- adding columns
ms.assetid: abeb8d52-d562-4e29-9e1e-2923ae874859
author: stevestein
ms.author: sstein
ms.openlocfilehash: f7e9294de10be0df9ef470c75d0934e9f8787b55
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87586579"
---
# <a name="add-columns-to-a-table-database-engine"></a><span data-ttu-id="6c4ac-102">向表中添加列（数据库引擎）</span><span class="sxs-lookup"><span data-stu-id="6c4ac-102">Add Columns to a Table (Database Engine)</span></span>
  <span data-ttu-id="6c4ac-103">本主题说明如何使用 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 或 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 在 [!INCLUDE[tsql](../../includes/tsql-md.md)]中向表添加新列。</span><span class="sxs-lookup"><span data-stu-id="6c4ac-103">This topic describes how to add new columns to a table in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span>  
  
 <span data-ttu-id="6c4ac-104">**本主题内容**</span><span class="sxs-lookup"><span data-stu-id="6c4ac-104">**In This Topic**</span></span>  
  
-   <span data-ttu-id="6c4ac-105">**开始之前：**</span><span class="sxs-lookup"><span data-stu-id="6c4ac-105">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="6c4ac-106">限制和局限</span><span class="sxs-lookup"><span data-stu-id="6c4ac-106">Limitations and Restrictions</span></span>](#Restrictions)  
  
     [<span data-ttu-id="6c4ac-107">安全性</span><span class="sxs-lookup"><span data-stu-id="6c4ac-107">Security</span></span>](#Security)  
  
-   <span data-ttu-id="6c4ac-108">**若要插入列，请使用：**</span><span class="sxs-lookup"><span data-stu-id="6c4ac-108">**To insert columns, using:**</span></span>  
  
     [<span data-ttu-id="6c4ac-109">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="6c4ac-109">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="6c4ac-110">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="6c4ac-110">Transact-SQL</span></span>](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="6c4ac-111">开始之前</span><span class="sxs-lookup"><span data-stu-id="6c4ac-111">Before You Begin</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="6c4ac-112">限制和局限</span><span class="sxs-lookup"><span data-stu-id="6c4ac-112">Limitations and Restrictions</span></span>  
 <span data-ttu-id="6c4ac-113">使用 ALTER TABLE 语句向表添加列会自动将这些列添加到该表的末尾。</span><span class="sxs-lookup"><span data-stu-id="6c4ac-113">Using the ALTER TABLE statement to add columns to a table automatically adds those columns to the end of the table.</span></span> <span data-ttu-id="6c4ac-114">如果您希望该表中的列采用特定顺序，请使用 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="6c4ac-114">If you want the columns in a specific order in the table, use [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].</span></span> <span data-ttu-id="6c4ac-115">但请注意，这并非数据库设计的最佳做法。</span><span class="sxs-lookup"><span data-stu-id="6c4ac-115">However, note that this is not a database design best practice.</span></span> <span data-ttu-id="6c4ac-116">最佳做法是指定在应用程序级别和查询级别返回列的顺序。</span><span class="sxs-lookup"><span data-stu-id="6c4ac-116">Best practice is to specify the order in which the columns are returned at the application and query level.</span></span> <span data-ttu-id="6c4ac-117">您不应依赖于使用 SELECT \* 基于在表中定义列的顺序以预期顺序返回所有列。</span><span class="sxs-lookup"><span data-stu-id="6c4ac-117">You should not rely on the use of SELECT \* to return all columns in an expected order based on the order in which they are defined in the table.</span></span> <span data-ttu-id="6c4ac-118">请始终按照您希望它们出现的顺序在您的查询和应用程序中按名称指定列。</span><span class="sxs-lookup"><span data-stu-id="6c4ac-118">Always specify the columns by name in your queries and applications in the order in which you would like them to appear.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="6c4ac-119">Security</span><span class="sxs-lookup"><span data-stu-id="6c4ac-119">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="6c4ac-120">权限</span><span class="sxs-lookup"><span data-stu-id="6c4ac-120">Permissions</span></span>  
 <span data-ttu-id="6c4ac-121">需要对表的 ALTER 权限。</span><span class="sxs-lookup"><span data-stu-id="6c4ac-121">Requires ALTER permission on the table.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="6c4ac-122">使用 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="6c4ac-122">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-insert-columns-into-a-table-with-table-designer"></a><span data-ttu-id="6c4ac-123">用表设计器向表中插入列</span><span class="sxs-lookup"><span data-stu-id="6c4ac-123">To insert columns into a table with Table Designer</span></span>  
  
1.  <span data-ttu-id="6c4ac-124">在“对象资源管理器”\*\*\*\* 中，右键单击要为其添加列的表，再选择“设计”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="6c4ac-124">In **Object Explorer**, right-click the table to which you want to add columns and choose **Design**.</span></span>  
  
2.  <span data-ttu-id="6c4ac-125">单击 **“列名”** 列中的第一个空单元。</span><span class="sxs-lookup"><span data-stu-id="6c4ac-125">Click in the first blank cell in the **Column Name** column.</span></span>  
  
3.  <span data-ttu-id="6c4ac-126">在该单元中键入列名。</span><span class="sxs-lookup"><span data-stu-id="6c4ac-126">Type the column name in the cell.</span></span> <span data-ttu-id="6c4ac-127">列名是必需设置的值。</span><span class="sxs-lookup"><span data-stu-id="6c4ac-127">The column name is a required value.</span></span>  
  
4.  <span data-ttu-id="6c4ac-128">按 Tab 键转到 **“数据类型”** 单元格，再从下拉列表中选择数据类型。</span><span class="sxs-lookup"><span data-stu-id="6c4ac-128">Press the TAB key to go to the **Data Type** cell and select a data type from the dropdown.</span></span> <span data-ttu-id="6c4ac-129">它也是必需设置的值，如果您没有作出选择，它将被赋以默认值。</span><span class="sxs-lookup"><span data-stu-id="6c4ac-129">This too is a required value, and will be assigned the default value if you don't choose one.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="6c4ac-130"> 可以在 **“选项”** 对话框中的 **“数据库工具”** 之下更改默认值。</span><span class="sxs-lookup"><span data-stu-id="6c4ac-130">You can change the default value in the **Options** dialog box under **Database Tools**.</span></span>  
  
5.  <span data-ttu-id="6c4ac-131">在 **“列属性”** 选项卡上继续定义任何其他列属性。</span><span class="sxs-lookup"><span data-stu-id="6c4ac-131">Continue to define any other column properties in the **Column Properties** tab.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="6c4ac-132"> 列属性的默认值在您创建新列时添加，但您可以在 **“列属性”** 选项卡中更改这些值。</span><span class="sxs-lookup"><span data-stu-id="6c4ac-132">The default values for your column properties are added when you create a new column, but you can change them in the **Column Properties** tab.</span></span>  
  
6.  <span data-ttu-id="6c4ac-133">添加完列后，从“文件”菜单中，选择“保存”_表名称_\*\*\*\*\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="6c4ac-133">When you are finished adding columns, from the **File** menu, choose **Save**_table name_.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="6c4ac-134">使用 Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="6c4ac-134">Using Transact-SQL</span></span>  
  
#### <a name="to-insert-columns-into-a-table"></a><span data-ttu-id="6c4ac-135">向表中插入列</span><span class="sxs-lookup"><span data-stu-id="6c4ac-135">To insert columns into a table</span></span>  
  
1.  <span data-ttu-id="6c4ac-136">连接到 [!INCLUDE[ssDE](../../includes/ssde-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="6c4ac-136">Connect to the [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="6c4ac-137">在标准菜单栏上，单击 **“新建查询”** 。</span><span class="sxs-lookup"><span data-stu-id="6c4ac-137">From the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="6c4ac-138">下面的示例将两列添加到表 `dbo.doc_exa`中。</span><span class="sxs-lookup"><span data-stu-id="6c4ac-138">The following example adds two columns to the table `dbo.doc_exa`.</span></span> <span data-ttu-id="6c4ac-139">将以下示例复制并粘贴到查询窗口中，然后单击 **“执行”** 。</span><span class="sxs-lookup"><span data-stu-id="6c4ac-139">Copy and paste the following example into the query window and click **Execute**</span></span>  
  
```  
ALTER TABLE dbo.doc_exa ADD column_b VARCHAR(20) NULL, column_c INT NULL ;  
```  
  
##  <a name="for-more-information-see-alter-table-40transact-sql41"></a><a name="FollowUp"></a><span data-ttu-id="6c4ac-140">有关详细信息，请参阅[ALTER TABLE &#40;transact-sql&#41;](/sql/t-sql/statements/alter-table-transact-sql)</span><span class="sxs-lookup"><span data-stu-id="6c4ac-140">For more information, see [ALTER TABLE &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-table-transact-sql)</span></span>  
  
  
