---
title: 修改列（数据库引擎）| Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: table-view-index
ms.topic: conceptual
helpviewer_keywords:
- modifying data types
- column data types [SQL Server]
- data types [SQL Server], columns
ms.assetid: b67b95c5-61ef-4bd8-9a3e-1640eb7583ac
author: stevestein
ms.author: sstein
ms.openlocfilehash: a73c25d91b742f1cc1f7edcc8a95cdf226b2683c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87587729"
---
# <a name="modify-columns-database-engine"></a><span data-ttu-id="6daee-102">修改列（数据库引擎）</span><span class="sxs-lookup"><span data-stu-id="6daee-102">Modify Columns (Database Engine)</span></span>
  <span data-ttu-id="6daee-103">您可以通过使用 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 或 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 在 [!INCLUDE[tsql](../../includes/tsql-md.md)]中修改列的数据类型。</span><span class="sxs-lookup"><span data-stu-id="6daee-103">You can modify the data type of a column in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span>  
  
> [!WARNING]  
>  <span data-ttu-id="6daee-104">如果修改已包含数据的列的数据类型，则在将现有数据转换为新类型时可能会导致永久丢失数据。</span><span class="sxs-lookup"><span data-stu-id="6daee-104">Modifying the data type of a column that already contains data can result in the permanent loss of data when the existing data is converted to the new type.</span></span> <span data-ttu-id="6daee-105">此外，依赖于所修改列的代码和应用程序可能会失败。</span><span class="sxs-lookup"><span data-stu-id="6daee-105">In addition, code and applications that depend on the modified column may fail.</span></span> <span data-ttu-id="6daee-106">这些代码和应用程序包括查询、视图、存储过程、用户定义函数和客户端应用程序等。</span><span class="sxs-lookup"><span data-stu-id="6daee-106">These include queries, views, stored procedures, user-defined functions, and client applications.</span></span> <span data-ttu-id="6daee-107">注意，这些错误会级联发生。</span><span class="sxs-lookup"><span data-stu-id="6daee-107">Note that these failures will cascade.</span></span> <span data-ttu-id="6daee-108">例如，如果一个存储过程调用一个依赖于所修改列的用户定义函数，则该存储过程可能会失败。</span><span class="sxs-lookup"><span data-stu-id="6daee-108">For example, a stored procedure that calls a user-defined function that depends on the modified column may fail.</span></span> <span data-ttu-id="6daee-109">请在需要对列进行任何更改之前慎重考虑。</span><span class="sxs-lookup"><span data-stu-id="6daee-109">Carefully consider any changes you want to make to a column before making it.</span></span>  
  
 <span data-ttu-id="6daee-110">**本主题内容**</span><span class="sxs-lookup"><span data-stu-id="6daee-110">**In This Topic**</span></span>  
  
-   <span data-ttu-id="6daee-111">**开始之前：**</span><span class="sxs-lookup"><span data-stu-id="6daee-111">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="6daee-112">安全性</span><span class="sxs-lookup"><span data-stu-id="6daee-112">Security</span></span>](#Security)  
  
-   <span data-ttu-id="6daee-113">**若要修改列的数据类型，请使用：**</span><span class="sxs-lookup"><span data-stu-id="6daee-113">**To modify the data type of a column, using:**</span></span>  
  
     [<span data-ttu-id="6daee-114">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="6daee-114">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="6daee-115">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="6daee-115">Transact-SQL</span></span>](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="6daee-116">开始之前</span><span class="sxs-lookup"><span data-stu-id="6daee-116">Before You Begin</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="6daee-117">Security</span><span class="sxs-lookup"><span data-stu-id="6daee-117">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="6daee-118">权限</span><span class="sxs-lookup"><span data-stu-id="6daee-118">Permissions</span></span>  
 <span data-ttu-id="6daee-119">需要对表的 ALTER 权限。</span><span class="sxs-lookup"><span data-stu-id="6daee-119">Requires ALTER permission on the table.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="6daee-120">使用 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="6daee-120">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-modify-the-data-type-of-a-column"></a><span data-ttu-id="6daee-121">修改列的数据类型</span><span class="sxs-lookup"><span data-stu-id="6daee-121">To modify the data type of a column</span></span>  
  
1.  <span data-ttu-id="6daee-122">在“对象资源管理器”  中，右键单击要更改其小数位数的列所在的表，再单击“设计”  。</span><span class="sxs-lookup"><span data-stu-id="6daee-122">In **Object Explorer**, right-click the table with columns for which you want to change the scale and click **Design**.</span></span>  
  
2.  <span data-ttu-id="6daee-123">选择要修改其数据类型的列。</span><span class="sxs-lookup"><span data-stu-id="6daee-123">Select the column for which you want to modify the data type.</span></span>  
  
3.  <span data-ttu-id="6daee-124">在“列属性”  选项卡中，单击“数据类型”  属性的网格单元格，再从下拉列表中选择新的数据类型。</span><span class="sxs-lookup"><span data-stu-id="6daee-124">In the **Column Properties** tab, click the grid cell for the **Data Type** property and choose a new data type from the drop-down list.</span></span>  
  
4.  <span data-ttu-id="6daee-125">在“文件”  菜单上，单击“保存”  以保存表名  。</span><span class="sxs-lookup"><span data-stu-id="6daee-125">On the **File** menu, click **Save**_table name_.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="6daee-126">当您修改列的数据类型时，即使已为所选数据类型指定其他长度，表设计器也会使用该数据类型的默认长度。</span><span class="sxs-lookup"><span data-stu-id="6daee-126">When you modify the data type of a column, Table Designer applies the default length of the data type you selected, even if you have already specified another.</span></span> <span data-ttu-id="6daee-127">在指定数据类型之后，始终需要将数据类型长度设置为所需的值。</span><span class="sxs-lookup"><span data-stu-id="6daee-127">Always set the data type length for to the desired value after specifying the data type.</span></span>  
  
> [!WARNING]  
>  <span data-ttu-id="6daee-128">如果您尝试修改与其他表相关的列的数据类型，表设计器会要求您确认也应该对其他表中的列进行更改。</span><span class="sxs-lookup"><span data-stu-id="6daee-128">If you attempt to modify the data type of a column that relates to other tables, Table Designer asks you to confirm that the change should be made to the columns in the other tables as well.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="6daee-129">使用 Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="6daee-129">Using Transact-SQL</span></span>  
  
#### <a name="to-modify-the-data-type-of-a-column"></a><span data-ttu-id="6daee-130">修改列的数据类型</span><span class="sxs-lookup"><span data-stu-id="6daee-130">To modify the data type of a column</span></span>  
  
1.  <span data-ttu-id="6daee-131">在 **“对象资源管理器”** 中，连接到 [!INCLUDE[ssDE](../../includes/ssde-md.md)]的实例。</span><span class="sxs-lookup"><span data-stu-id="6daee-131">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="6daee-132">在标准菜单栏上，单击 **“新建查询”** 。</span><span class="sxs-lookup"><span data-stu-id="6daee-132">On the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="6daee-133">将以下示例复制并粘贴到查询窗口中，然后单击“执行”  。</span><span class="sxs-lookup"><span data-stu-id="6daee-133">Copy and paste the following example into the query window and click **Execute**.</span></span>  
  
    ```  
    CREATE TABLE dbo.doc_exy (column_a INT ) ;  
    GO  
    INSERT INTO dbo.doc_exy (column_a) VALUES (10) ;  
    GO  
    ALTER TABLE dbo.doc_exy ALTER COLUMN column_a DECIMAL (5, 2) ;  
    GO  
  
    ```  
  
 <span data-ttu-id="6daee-134">有关详细信息，请参阅 [ALTER TABLE (Transact-SQL)](/sql/t-sql/statements/alter-table-transact-sql)</span><span class="sxs-lookup"><span data-stu-id="6daee-134">For more information, see [ALTER TABLE &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-table-transact-sql)</span></span>  
  
  
