---
title: 删除计划指南 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: performance
ms.topic: conceptual
helpviewer_keywords:
- plan guides [SQL Server], deleting
ms.assetid: aa4d3188-6927-43de-a3e3-90fc16eeaca7
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 303ad6f59cbe24265aec66f3cb780a5b4ad4f157
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87688845"
---
# <a name="delete-a-plan-guide"></a><span data-ttu-id="c55ac-102">删除计划指南</span><span class="sxs-lookup"><span data-stu-id="c55ac-102">Delete a Plan Guide</span></span>
  <span data-ttu-id="c55ac-103">您可以通过使用 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 或 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 在 [!INCLUDE[tsql](../../includes/tsql-md.md)]中删除计划指南。</span><span class="sxs-lookup"><span data-stu-id="c55ac-103">You can delete (drop) a plan guide in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span> <span data-ttu-id="c55ac-104">使用 [!INCLUDE[tsql](../../includes/tsql-md.md)]，您还可以删除数据库中的所有计划指南。</span><span class="sxs-lookup"><span data-stu-id="c55ac-104">Using [!INCLUDE[tsql](../../includes/tsql-md.md)], you can also delete all of the plan guides in a database.</span></span>  
  
 <span data-ttu-id="c55ac-105">**本主题内容**</span><span class="sxs-lookup"><span data-stu-id="c55ac-105">**In This Topic**</span></span>  
  
-   <span data-ttu-id="c55ac-106">**开始之前：**</span><span class="sxs-lookup"><span data-stu-id="c55ac-106">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="c55ac-107">安全性</span><span class="sxs-lookup"><span data-stu-id="c55ac-107">Security</span></span>](#Security)  
  
-   <span data-ttu-id="c55ac-108">**若要删除计划指南，请使用：**</span><span class="sxs-lookup"><span data-stu-id="c55ac-108">**To delete a plan guide, using:**</span></span>  
  
     [<span data-ttu-id="c55ac-109">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="c55ac-109">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="c55ac-110">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="c55ac-110">Transact-SQL</span></span>](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="c55ac-111">开始之前</span><span class="sxs-lookup"><span data-stu-id="c55ac-111">Before You Begin</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="c55ac-112">Security</span><span class="sxs-lookup"><span data-stu-id="c55ac-112">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="c55ac-113">权限</span><span class="sxs-lookup"><span data-stu-id="c55ac-113">Permissions</span></span>  
 <span data-ttu-id="c55ac-114">删除 OBJECT 计划指南要求对计划指南引用的对象（例如：函数、存储过程）具有 ALTER 权限。</span><span class="sxs-lookup"><span data-stu-id="c55ac-114">Deleting an OBJECT plan guide requires ALTER permission on the object (for example: function, stored procedure) that is referenced by the plan guide.</span></span> <span data-ttu-id="c55ac-115">其他所有计划指南都需要 ALTER DATABASE 权限。</span><span class="sxs-lookup"><span data-stu-id="c55ac-115">All other plan guides require ALTER DATABASE permission.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="c55ac-116">使用 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="c55ac-116">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-delete-a-plan-guide"></a><span data-ttu-id="c55ac-117">删除计划指南</span><span class="sxs-lookup"><span data-stu-id="c55ac-117">To delete a plan guide</span></span>  
  
1.  <span data-ttu-id="c55ac-118">单击加号以展开要从中删除计划指南的数据库，然后单击加号以展开 **“可编程性”** 文件夹。</span><span class="sxs-lookup"><span data-stu-id="c55ac-118">Click the plus sign to expand the database in which you want to delete a plan guide, and then click the plus sign to expand the **Programmability** folder.</span></span>  
  
2.  <span data-ttu-id="c55ac-119">单击加号以便展开 **“计划指南”** 文件夹。</span><span class="sxs-lookup"><span data-stu-id="c55ac-119">Click the plus sign to expand the **Plan Guides** folder.</span></span>  
  
3.  <span data-ttu-id="c55ac-120">右键单击要删除的计划指南，然后选择“删除”。</span><span class="sxs-lookup"><span data-stu-id="c55ac-120">Right-click the plan guide you want to delete and select **Delete**.</span></span>  
  
4.  <span data-ttu-id="c55ac-121">在 **“删除对象”** 对话框中，确保已选择正确的计划指南，然后单击 **“确定”** 。</span><span class="sxs-lookup"><span data-stu-id="c55ac-121">In the **Delete Object** dialog box, ensure that the correct plan guide is selected and then click **OK**.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="c55ac-122">使用 Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="c55ac-122">Using Transact-SQL</span></span>  
  
#### <a name="to-delete-a-single-plan-guide"></a><span data-ttu-id="c55ac-123">删除单个计划指南</span><span class="sxs-lookup"><span data-stu-id="c55ac-123">To delete a single plan guide</span></span>  
  
1.  <span data-ttu-id="c55ac-124">在 **“对象资源管理器”** 中，连接到 [!INCLUDE[ssDE](../../includes/ssde-md.md)]的实例。</span><span class="sxs-lookup"><span data-stu-id="c55ac-124">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="c55ac-125">在标准菜单栏上，单击 **“新建查询”** 。</span><span class="sxs-lookup"><span data-stu-id="c55ac-125">On the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="c55ac-126">将以下示例复制并粘贴到查询窗口中，然后单击“执行” 。</span><span class="sxs-lookup"><span data-stu-id="c55ac-126">Copy and paste the following example into the query window and click **Execute**.</span></span>  
  
    ```  
    --Create a procedure on which to define the plan guide.  
    IF OBJECT_ID(N'Sales.GetSalesOrderByCountry', N'P') IS NOT NULL  
        DROP PROCEDURE Sales.GetSalesOrderByCountry;  
    GO  
    CREATE PROCEDURE Sales.GetSalesOrderByCountry   
        (@Country nvarchar(60))  
    AS  
    BEGIN  
        SELECT *  
        FROM Sales.SalesOrderHeader AS h   
        INNER JOIN Sales.Customer AS c ON h.CustomerID = c.CustomerID  
        INNER JOIN Sales.SalesTerritory AS t ON c.TerritoryID = t.TerritoryID  
        WHERE t.CountryRegionCode = @Country;  
    END  
    GO  
    --Create the plan guide.  
    EXEC sp_create_plan_guide N'Guide3',  
        N'SELECT *  
        FROM Sales.SalesOrderHeader AS h   
        INNER JOIN Sales.Customer AS c ON h.CustomerID = c.CustomerID  
        INNER JOIN Sales.SalesTerritory AS t ON c.TerritoryID = t.TerritoryID  
        WHERE t.CountryRegionCode = @Country',  
        N'OBJECT',  
        N'Sales.GetSalesOrderByCountry',  
        NULL,  
        N'OPTION (OPTIMIZE FOR (@Country = N''US''))';  
    GO  
    --Drop the plan guide.  
    EXEC sp_control_plan_guide N'DROP', N'Guide3';  
    GO  
    ```  
  
#### <a name="to-delete-all-plan-guides-in-a-database"></a><span data-ttu-id="c55ac-127">删除数据库中的所有计划指南</span><span class="sxs-lookup"><span data-stu-id="c55ac-127">To delete all plan guides in a database</span></span>  
  
1.  <span data-ttu-id="c55ac-128">在 **“对象资源管理器”** 中，连接到 [!INCLUDE[ssDE](../../includes/ssde-md.md)]的实例。</span><span class="sxs-lookup"><span data-stu-id="c55ac-128">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="c55ac-129">在标准菜单栏上，单击 **“新建查询”** 。</span><span class="sxs-lookup"><span data-stu-id="c55ac-129">On the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="c55ac-130">将以下示例复制并粘贴到查询窗口中，然后单击“执行” 。</span><span class="sxs-lookup"><span data-stu-id="c55ac-130">Copy and paste the following example into the query window and click **Execute**.</span></span>  
  
    ```  
    USE AdventureWorks2012;  
    GO  
    EXEC sp_control_plan_guide N'DROP ALL';  
    GO  
    ```  
  
 <span data-ttu-id="c55ac-131">有关详细信息，请参阅 [sp_control_plan_guide (Transact SQL)](/sql/relational-databases/system-stored-procedures/sp-control-plan-guide-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="c55ac-131">For more information, see [sp_control_plan_guide &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-control-plan-guide-transact-sql).</span></span>  
  
  
