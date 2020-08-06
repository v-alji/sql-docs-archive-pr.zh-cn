---
title: 修改存储过程 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.technology: stored-procedures
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- modifying stored procedures
- editing stored procedures
- stored procedures [SQL Server], modifying
ms.assetid: 13396239-6100-48ce-aa34-461358d99c92
author: stevestein
ms.author: sstein
ms.openlocfilehash: 906f0e06650da505094d18774ce86dab53d53f38
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87682773"
---
# <a name="modify-a-stored-procedure"></a><span data-ttu-id="77094-102">修改存储过程</span><span class="sxs-lookup"><span data-stu-id="77094-102">Modify a Stored Procedure</span></span>
    
##  <a name="this-topic-describes-how-to-modify-a-stored-procedure-in-sscurrent-by-using-ssmanstudiofull-or-tsql"></a><a name="Top"></a> <span data-ttu-id="77094-103">本主题介绍了如何使用 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 或 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 在 [!INCLUDE[tsql](../../includes/tsql-md.md)]中修改存储过程。</span><span class="sxs-lookup"><span data-stu-id="77094-103">This topic describes how to modify a stored procedure in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span>  
  
-   <span data-ttu-id="77094-104">**开始之前：** [限制和局限](#Restrictions)、[安全性](#Security)</span><span class="sxs-lookup"><span data-stu-id="77094-104">**Before you begin:**  [Limitations and Restrictions](#Restrictions), [Security](#Security)</span></span>  
  
-   <span data-ttu-id="77094-105">要更改该过程，请使用：[SQL Server Management Studio](#SSMSProcedure)、[Transact-SQL](#TsqlProcedure)</span><span class="sxs-lookup"><span data-stu-id="77094-105">**To alter a procedure, using:**  [SQL Server Management Studio](#SSMSProcedure), [Transact-SQL](#TsqlProcedure)</span></span>  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="77094-106">开始之前</span><span class="sxs-lookup"><span data-stu-id="77094-106">Before You Begin</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="77094-107">限制和局限</span><span class="sxs-lookup"><span data-stu-id="77094-107">Limitations and Restrictions</span></span>  
 [!INCLUDE[tsql](../../includes/tsql-md.md)] <span data-ttu-id="77094-108">存储过程修改为 CLR 存储过程，反之亦然。</span><span class="sxs-lookup"><span data-stu-id="77094-108">stored procedures cannot be modified to be CLR stored procedures and vice versa.</span></span>  
  
 <span data-ttu-id="77094-109">如果原来的过程定义是使用 WITH ENCRYPTION 或 WITH RECOMPILE 创建的，那么只有在 ALTER PROCEDURE 语句中也包含这些选项时，这些选项才有效。</span><span class="sxs-lookup"><span data-stu-id="77094-109">If the previous procedure definition was created using WITH ENCRYPTION or WITH RECOMPILE, these options are enabled only if they are included in the ALTER PROCEDURE statement.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="77094-110">Security</span><span class="sxs-lookup"><span data-stu-id="77094-110">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="77094-111">权限</span><span class="sxs-lookup"><span data-stu-id="77094-111">Permissions</span></span>  
 <span data-ttu-id="77094-112">要求对过程具有 ALTER PROCEDURE 权限。</span><span class="sxs-lookup"><span data-stu-id="77094-112">Requires ALTER PROCEDURE permission on the procedure.</span></span>  
  
##  <a name="how-to-modify-a-stored-procedure"></a><a name="Procedures"></a> <span data-ttu-id="77094-113">修改存储过程</span><span class="sxs-lookup"><span data-stu-id="77094-113">How to Modify a Stored Procedure</span></span>  
 <span data-ttu-id="77094-114">您可以使用以下项之一：</span><span class="sxs-lookup"><span data-stu-id="77094-114">You can use one of the following:</span></span>  
  
-   [<span data-ttu-id="77094-115">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="77094-115">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
-   [<span data-ttu-id="77094-116">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="77094-116">Transact-SQL</span></span>](#TsqlProcedure)  
  
###  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="77094-117">使用 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="77094-117">Using SQL Server Management Studio</span></span>  
 <span data-ttu-id="77094-118">**在 Management Studio 中修改过程**</span><span class="sxs-lookup"><span data-stu-id="77094-118">**To modify a procedure in Management Studio**</span></span>  
  
1.  <span data-ttu-id="77094-119">在对象资源管理器中，连接到 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 的实例，然后展开该实例。</span><span class="sxs-lookup"><span data-stu-id="77094-119">In Object Explorer, connect to an instance of [!INCLUDE[ssDE](../../includes/ssde-md.md)] and then expand that instance.</span></span>  
  
2.  <span data-ttu-id="77094-120">展开 **“数据库”** 、过程所属的数据库以及 **“可编程性”** 。</span><span class="sxs-lookup"><span data-stu-id="77094-120">Expand **Databases**, expand the database in which the procedure belongs, and then expand **Programmability**.</span></span>  
  
3.  <span data-ttu-id="77094-121">展开“存储过程”，右键单击要修改的过程，再单击“修改”。</span><span class="sxs-lookup"><span data-stu-id="77094-121">Expand **Stored Procedures**, right-click the procedure to modify, and then click **Modify**.</span></span>  
  
4.  <span data-ttu-id="77094-122">修改存储过程的文本。</span><span class="sxs-lookup"><span data-stu-id="77094-122">Modify the text of the stored procedure.</span></span>  
  
5.  <span data-ttu-id="77094-123">若要测试语法，请在 **“查询”** 菜单上，单击 **“分析”** 。</span><span class="sxs-lookup"><span data-stu-id="77094-123">To test the syntax, on the **Query** menu, click **Parse**.</span></span>  
  
6.  <span data-ttu-id="77094-124">若要将修改信息保存到过程定义中，请在 **“查询”** 菜单上单击 **“执行”** 。</span><span class="sxs-lookup"><span data-stu-id="77094-124">To save the modifications to the procedure definition, on the **Query** menu, click **Execute**.</span></span>  
  
7.  <span data-ttu-id="77094-125">若要将更新的过程定义另存为 [!INCLUDE[tsql](../../includes/tsql-md.md)] 脚本，请在 **“文件”** 菜单上单击 **“另存为”** 。</span><span class="sxs-lookup"><span data-stu-id="77094-125">To save the updated procedure definition as a [!INCLUDE[tsql](../../includes/tsql-md.md)] script, on the **File** menu, click **Save As**.</span></span> <span data-ttu-id="77094-126">接受该文件名或将其替换为新的名称，再单击 **“保存”** 。</span><span class="sxs-lookup"><span data-stu-id="77094-126">Accept the file name or replace it with a new name, and then click **Save**.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="77094-127">验证所有用户的输入。</span><span class="sxs-lookup"><span data-stu-id="77094-127">Validate all user input.</span></span> <span data-ttu-id="77094-128">验证前请勿连接用户输入。</span><span class="sxs-lookup"><span data-stu-id="77094-128">Do not concatenate user input before you validate it.</span></span> <span data-ttu-id="77094-129">绝对不要执行根据尚未验证的用户输入构造的命令。</span><span class="sxs-lookup"><span data-stu-id="77094-129">Never execute a command constructed from unvalidated user input.</span></span>  
  
###  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="77094-130">使用 Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="77094-130">Using Transact-SQL</span></span>  
 <span data-ttu-id="77094-131">**在查询编辑器中修改过程**</span><span class="sxs-lookup"><span data-stu-id="77094-131">**To modify a procedure in Query Editor**</span></span>  
  
1.  <span data-ttu-id="77094-132">在 **“对象资源管理器”** 中，连接到 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 的实例，然后展开该实例。</span><span class="sxs-lookup"><span data-stu-id="77094-132">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../includes/ssde-md.md)] and then expand that instance.</span></span>  
  
2.  <span data-ttu-id="77094-133">展开 **“数据库”** ，然后展开过程所属的数据库。</span><span class="sxs-lookup"><span data-stu-id="77094-133">Expand **Databases**, expand the database in which the procedure belongs.</span></span> <span data-ttu-id="77094-134">或者，在工具栏上，从可用数据库列表中选择该数据库。</span><span class="sxs-lookup"><span data-stu-id="77094-134">Or, from the tool bar, select the database from the list of available databases.</span></span> <span data-ttu-id="77094-135">对于此示例，选择 [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] 数据库。</span><span class="sxs-lookup"><span data-stu-id="77094-135">For this example, select the [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] database.</span></span>  
  
3.  <span data-ttu-id="77094-136">在 **“文件”** 菜单上，单击 **“新建查询”** 。</span><span class="sxs-lookup"><span data-stu-id="77094-136">On the **File** menu, click **New Query**.</span></span>  
  
4.  <span data-ttu-id="77094-137">复制以下示例并将其粘贴到查询编辑器中。</span><span class="sxs-lookup"><span data-stu-id="77094-137">Copy and paste the following example into the query editor.</span></span> <span data-ttu-id="77094-138">此示例创建 `uspVendorAllInfo` 过程，该过程返回 [!INCLUDE[ssSampleDBCoFull](../../includes/sssampledbcofull-md.md)] 数据库中所有供应商的名称、所提供的产品、信用等级以及可用性。</span><span class="sxs-lookup"><span data-stu-id="77094-138">The example creates the `uspVendorAllInfo` procedure, which returns the names of all the vendors in the [!INCLUDE[ssSampleDBCoFull](../../includes/sssampledbcofull-md.md)] database, the products they supply, their credit ratings, and their availability.</span></span>  
  
    ```  
  
    IF OBJECT_ID ( 'Purchasing.uspVendorAllInfo', 'P' ) IS NOT NULL   
        DROP PROCEDURE Purchasing.uspVendorAllInfo;  
    GO  
    CREATE PROCEDURE Purchasing.uspVendorAllInfo  
    WITH EXECUTE AS CALLER  
    AS  
        SET NOCOUNT ON;  
        SELECT v.Name AS Vendor, p.Name AS 'Product name',   
          v.CreditRating AS 'Rating',   
          v.ActiveFlag AS Availability  
        FROM Purchasing.Vendor v   
        INNER JOIN Purchasing.ProductVendor pv  
          ON v.BusinessEntityID = pv.BusinessEntityID   
        INNER JOIN Production.Product p  
          ON pv.ProductID = p.ProductID   
        ORDER BY v.Name ASC;  
    GO  
  
    ```  
  
5.  <span data-ttu-id="77094-139">在 **“文件”** 菜单上，单击 **“新建查询”** 。</span><span class="sxs-lookup"><span data-stu-id="77094-139">On the **File** menu, click **New Query**.</span></span>  
  
6.  <span data-ttu-id="77094-140">复制以下示例并将其粘贴到查询编辑器中。</span><span class="sxs-lookup"><span data-stu-id="77094-140">Copy and paste the following example into the query editor.</span></span> <span data-ttu-id="77094-141">该示例修改 `uspVendorAllInfo` 过程。</span><span class="sxs-lookup"><span data-stu-id="77094-141">The example modifies the `uspVendorAllInfo` procedure.</span></span> <span data-ttu-id="77094-142">将删除 EXECUTE AS CALLER 子句并且将过程的主体修改为只返回那些提供指定产品的供应商。</span><span class="sxs-lookup"><span data-stu-id="77094-142">The EXECUTE AS CALLER clause is removed and the body of the procedure is modified to return only those vendors that supply the specified product.</span></span> <span data-ttu-id="77094-143">`LEFT` 和 `CASE` 函数自定义结果集的外观。</span><span class="sxs-lookup"><span data-stu-id="77094-143">The `LEFT` and `CASE` functions customize the appearance of the result set.</span></span>  
  
    ```  
    ALTER PROCEDURE Purchasing.uspVendorAllInfo  
        @Product varchar(25)   
    AS  
        SET NOCOUNT ON;  
        SELECT LEFT(v.Name, 25) AS Vendor, LEFT(p.Name, 25) AS 'Product name',   
        'Rating' = CASE v.CreditRating   
            WHEN 1 THEN 'Superior'  
            WHEN 2 THEN 'Excellent'  
            WHEN 3 THEN 'Above average'  
            WHEN 4 THEN 'Average'  
            WHEN 5 THEN 'Below average'  
            ELSE 'No rating'  
            END  
        , Availability = CASE v.ActiveFlag  
            WHEN 1 THEN 'Yes'  
            ELSE 'No'  
            END  
        FROM Purchasing.Vendor AS v   
        INNER JOIN Purchasing.ProductVendor AS pv  
          ON v.BusinessEntityID = pv.BusinessEntityID   
        INNER JOIN Production.Product AS p   
          ON pv.ProductID = p.ProductID   
        WHERE p.Name LIKE @Product  
        ORDER BY v.Name ASC;  
    GO  
  
    ```  
  
7.  <span data-ttu-id="77094-144">若要将修改信息保存到过程定义中，请在 **“查询”** 菜单上单击 **“执行”** 。</span><span class="sxs-lookup"><span data-stu-id="77094-144">To save the modifications to the procedure definition, on the **Query** menu, click **Execute**.</span></span>  
  
8.  <span data-ttu-id="77094-145">若要将更新的过程定义另存为 [!INCLUDE[tsql](../../includes/tsql-md.md)] 脚本，请在 **“文件”** 菜单上单击 **“另存为”** 。</span><span class="sxs-lookup"><span data-stu-id="77094-145">To save the updated procedure definition as a [!INCLUDE[tsql](../../includes/tsql-md.md)] script, on the **File** menu, click **Save As**.</span></span> <span data-ttu-id="77094-146">接受该文件名或将其替换为新的名称，再单击 **“保存”** 。</span><span class="sxs-lookup"><span data-stu-id="77094-146">Accept the file name or replace it with a new name, and then click **Save**.</span></span>  
  
9. <span data-ttu-id="77094-147">若要运行修改的存储过程，请执行以下示例。</span><span class="sxs-lookup"><span data-stu-id="77094-147">To run the modified stored procedure, execute the following example.</span></span>  
  
    ```  
    EXEC Purchasing.uspVendorAllInfo N'LL Crankarm';  
    GO  
  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="77094-148">另请参阅</span><span class="sxs-lookup"><span data-stu-id="77094-148">See Also</span></span>  
 [<span data-ttu-id="77094-149">ALTER PROCEDURE (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="77094-149">ALTER PROCEDURE &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/alter-procedure-transact-sql)  
  
  
