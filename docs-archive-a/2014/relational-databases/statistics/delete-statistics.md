---
title: 删除统计信息 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: performance
ms.topic: conceptual
helpviewer_keywords:
- statistics [SQL Server], deleting
- deleting statistics
ms.assetid: eccce0aa-591e-4a1d-bd10-373b022f8749
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 36b74d7e1465c0742cda4fef9f34fb4b3930719c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87590116"
---
# <a name="delete-statistics"></a><span data-ttu-id="c4965-102">删除统计信息</span><span class="sxs-lookup"><span data-stu-id="c4965-102">Delete Statistics</span></span>
  <span data-ttu-id="c4965-103">你可以通过使用 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] ，删除 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 中表和视图中的统计信息，或 [!INCLUDE[tsql](../../includes/tsql-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c4965-103">You can delete (drop) statistics from tables and views in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)]</span></span>  
  
 <span data-ttu-id="c4965-104">**本主题内容**</span><span class="sxs-lookup"><span data-stu-id="c4965-104">**In This Topic**</span></span>  
  
-   <span data-ttu-id="c4965-105">**开始之前：**</span><span class="sxs-lookup"><span data-stu-id="c4965-105">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="c4965-106">限制和局限</span><span class="sxs-lookup"><span data-stu-id="c4965-106">Limitations and Restrictions</span></span>](#Restrictions)  
  
     [<span data-ttu-id="c4965-107">安全性</span><span class="sxs-lookup"><span data-stu-id="c4965-107">Security</span></span>](#Security)  
  
-   <span data-ttu-id="c4965-108">**若要从表或视图中删除统计信息，请使用：**</span><span class="sxs-lookup"><span data-stu-id="c4965-108">**To drop statistics from a table or view, using:**</span></span>  
  
     [<span data-ttu-id="c4965-109">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="c4965-109">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="c4965-110">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="c4965-110">Transact-SQL</span></span>](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="c4965-111">开始之前</span><span class="sxs-lookup"><span data-stu-id="c4965-111">Before You Begin</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="c4965-112">限制和局限</span><span class="sxs-lookup"><span data-stu-id="c4965-112">Limitations and Restrictions</span></span>  
  
-   <span data-ttu-id="c4965-113">删除统计信息时，请谨慎从事。</span><span class="sxs-lookup"><span data-stu-id="c4965-113">Be careful when you drop statistics.</span></span> <span data-ttu-id="c4965-114">这样做可能会影响查询优化器选择的执行计划。</span><span class="sxs-lookup"><span data-stu-id="c4965-114">Doing so may affect the execution plan chosen by the query optimizer.</span></span>  
  
-   <span data-ttu-id="c4965-115">不能使用 DROP STATISTICS 删除有关索引的统计信息。</span><span class="sxs-lookup"><span data-stu-id="c4965-115">Statistics on indexes cannot be dropped by using DROP STATISTICS.</span></span> <span data-ttu-id="c4965-116">统计信息的保留时间与索引存在的时间相同。</span><span class="sxs-lookup"><span data-stu-id="c4965-116">Statistics remain as long as the index exists.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="c4965-117">Security</span><span class="sxs-lookup"><span data-stu-id="c4965-117">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="c4965-118">权限</span><span class="sxs-lookup"><span data-stu-id="c4965-118">Permissions</span></span>  
 <span data-ttu-id="c4965-119">要求对表或视图具有 ALTER 权限。</span><span class="sxs-lookup"><span data-stu-id="c4965-119">Requires ALTER permission on the table or view.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="c4965-120">使用 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="c4965-120">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-drop-statistics-from-a-table-or-view"></a><span data-ttu-id="c4965-121">从表或视图中删除统计信息</span><span class="sxs-lookup"><span data-stu-id="c4965-121">To drop statistics from a table or view</span></span>  
  
1.  <span data-ttu-id="c4965-122">在 **“对象资源管理器”** 中，单击加号以便展开要删除统计信息的数据库。</span><span class="sxs-lookup"><span data-stu-id="c4965-122">In **Object Explorer**, click the plus sign to expand the database in which you want to delete a statistic.</span></span>  
  
2.  <span data-ttu-id="c4965-123">单击加号以便展开 **“表”** 文件夹。</span><span class="sxs-lookup"><span data-stu-id="c4965-123">Click the plus sign to expand the **Tables** folder.</span></span>  
  
3.  <span data-ttu-id="c4965-124">单击加号以便展开要删除统计信息的表。</span><span class="sxs-lookup"><span data-stu-id="c4965-124">Click the plus sign to expand the table in which you want to delete a statistic.</span></span>  
  
4.  <span data-ttu-id="c4965-125">单击加号以便展开 **“统计信息”** 文件夹。</span><span class="sxs-lookup"><span data-stu-id="c4965-125">Click the plus sign to expand the **Statistics** folder.</span></span>  
  
5.  <span data-ttu-id="c4965-126">右键单击要删除的统计信息对象，然后选择“删除”。</span><span class="sxs-lookup"><span data-stu-id="c4965-126">Right-click the statistics object that you want to delete and select **Delete**.</span></span>  
  
6.  <span data-ttu-id="c4965-127">在 **“删除对象”** 对话框中，确保已选择正确的统计信息，然后单击 **“确定”** 。</span><span class="sxs-lookup"><span data-stu-id="c4965-127">In the **Delete Object** dialog box, ensure that the correct statistic has been selected and click **OK**.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="c4965-128">使用 Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="c4965-128">Using Transact-SQL</span></span>  
  
#### <a name="to-drop-statistics-from-a-table-or-view"></a><span data-ttu-id="c4965-129">从表或视图中删除统计信息</span><span class="sxs-lookup"><span data-stu-id="c4965-129">To drop statistics from a table or view</span></span>  
  
1.  <span data-ttu-id="c4965-130">在 **“对象资源管理器”** 中，连接到 [!INCLUDE[ssDE](../../includes/ssde-md.md)]的实例。</span><span class="sxs-lookup"><span data-stu-id="c4965-130">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="c4965-131">在标准菜单栏上，单击 **“新建查询”** 。</span><span class="sxs-lookup"><span data-stu-id="c4965-131">On the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="c4965-132">将以下示例复制并粘贴到查询窗口中，然后单击“执行” 。</span><span class="sxs-lookup"><span data-stu-id="c4965-132">Copy and paste the following example into the query window and click **Execute**.</span></span>  
  
    ```  
    USE AdventureWorks2012;  
    GO  
    -- First, create two statistics named VendorCredit and CustomerTotal  
    -- The first statistic uses a random 50% sample of information provided from the Name and CreditRating columns in the Purchasing.Vendor table.  
    CREATE STATISTICS VendorCredit  
        ON Purchasing.Vendor (Name, CreditRating)  
        WITH SAMPLE 50 PERCENT  
    -- The second statistic uses all of the information from the CustomerID and TotalDue columns in the Sales.SalesOrderHeader table  
    CREATE STATISTICS CustomerTotal  
        ON Sales.SalesOrderHeader (CustomerID, TotalDue)  
        WITH FULLSCAN;  
    GO  
    -- This next statement drops both of the statistics created above. Note that the naming convention is [table_name].[statistics_name].  
    DROP STATISTICS Purchasing.Vendor.VendorCredit, Sales.SalesOrderHeader.CustomerTotal;  
    GO  
    ```  
  
 <span data-ttu-id="c4965-133">有关详细信息，请参阅 [DROP STATISTICS (Transact-SQL)](/sql/t-sql/statements/drop-statistics-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="c4965-133">For more information, see [DROP STATISTICS &#40;Transact-SQL&#41;](/sql/t-sql/statements/drop-statistics-transact-sql).</span></span>  
  
  
