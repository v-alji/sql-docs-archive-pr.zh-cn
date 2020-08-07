---
title: 教程：所有权链和上下文切换 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- context switching [SQL Server], tutorials
- ownership chains [SQL Server]
ms.assetid: db5d4cc3-5fc5-4cf5-afc1-8d4edc1d512b
author: rothja
ms.author: jroth
ms.openlocfilehash: 1e9072a68dd3179e5900fda06d4fea58b484a37e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87580102"
---
# <a name="tutorial-ownership-chains-and-context-switching"></a><span data-ttu-id="a93d3-102">Tutorial: Ownership Chains and Context Switching</span><span class="sxs-lookup"><span data-stu-id="a93d3-102">Tutorial: Ownership Chains and Context Switching</span></span>
  <span data-ttu-id="a93d3-103">本教程使用一个应用场景说明 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 安全性概念，其中包括所有权链和用户上下文切换。</span><span class="sxs-lookup"><span data-stu-id="a93d3-103">This tutorial uses a scenario to illustrate [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] security concepts involving ownership chains and user context switching.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="a93d3-104">若要运行本教程中的代码，您必须已配置混合模式安全性并且已安装 [!INCLUDE[ssSampleDBobject](../includes/sssampledbobject-md.md)] 数据库。</span><span class="sxs-lookup"><span data-stu-id="a93d3-104">To run the code in this tutorial you must have both Mixed Mode security configured and the [!INCLUDE[ssSampleDBobject](../includes/sssampledbobject-md.md)] database installed.</span></span> <span data-ttu-id="a93d3-105">有关混合模式安全性的详细信息，请参阅 [选择身份验证模式](security/choose-an-authentication-mode.md)。</span><span class="sxs-lookup"><span data-stu-id="a93d3-105">For more information about Mixed Mode security, see [Choose an Authentication Mode](security/choose-an-authentication-mode.md).</span></span>  
  
## <a name="scenario"></a><span data-ttu-id="a93d3-106">场景</span><span class="sxs-lookup"><span data-stu-id="a93d3-106">Scenario</span></span>  
 <span data-ttu-id="a93d3-107">在此应用场景中，两个用户需要帐户访问存储在 [!INCLUDE[ssSampleDBobject](../includes/sssampledbobject-md.md)] 数据库中的采购订单数据。</span><span class="sxs-lookup"><span data-stu-id="a93d3-107">In this scenario, two users need accounts to access purchase order data stored in the [!INCLUDE[ssSampleDBobject](../includes/sssampledbobject-md.md)] database.</span></span> <span data-ttu-id="a93d3-108">要求如下：</span><span class="sxs-lookup"><span data-stu-id="a93d3-108">The requirements are as follows:</span></span>  
  
-   <span data-ttu-id="a93d3-109">第一个帐户 (TestManagerUser) 必须能够查看每个采购订单中的所有详细信息。</span><span class="sxs-lookup"><span data-stu-id="a93d3-109">The first account (TestManagerUser) must be able to see all details in every purchase order.</span></span>  
  
-   <span data-ttu-id="a93d3-110">第二个帐户 (TestEmployeeUser) 必须能够根据采购订单号，查看已收到部分货物的项的采购订单号、订单日期、发货日期、产品 ID 号以及每个采购订单中已定购和已收到的项。</span><span class="sxs-lookup"><span data-stu-id="a93d3-110">The second account (TestEmployeeUser) must be able to see the purchase order number, order date, shipping date, product ID numbers, and the ordered and received items per purchase order, by purchase order number, for items where partial shipments have been received.</span></span>  
  
-   <span data-ttu-id="a93d3-111">所有其他帐户必须保留当前的权限。</span><span class="sxs-lookup"><span data-stu-id="a93d3-111">All other accounts must retain their current permissions.</span></span>  
  
 <span data-ttu-id="a93d3-112">若要满足本应用场景的要求，此示例分为四个部分来说明所有权链和上下文切换的概念：</span><span class="sxs-lookup"><span data-stu-id="a93d3-112">To fulfill the requirements of this scenario, the example is broken into four parts that demonstrate the concepts of ownership chains and context switching:</span></span>  
  
1.  <span data-ttu-id="a93d3-113">配置环境。</span><span class="sxs-lookup"><span data-stu-id="a93d3-113">Configuring the environment.</span></span>  
  
2.  <span data-ttu-id="a93d3-114">创建存储过程以按采购订单访问数据。</span><span class="sxs-lookup"><span data-stu-id="a93d3-114">Creating a stored procedure to access data by purchase order.</span></span>  
  
3.  <span data-ttu-id="a93d3-115">通过存储过程访问数据。</span><span class="sxs-lookup"><span data-stu-id="a93d3-115">Accessing the data through the stored procedure.</span></span>  
  
4.  <span data-ttu-id="a93d3-116">重置环境。</span><span class="sxs-lookup"><span data-stu-id="a93d3-116">Resetting the environment.</span></span>  
  
 <span data-ttu-id="a93d3-117">本示例中的每个代码块都将逐一加以说明。</span><span class="sxs-lookup"><span data-stu-id="a93d3-117">Each code block in this example is explained in line.</span></span> <span data-ttu-id="a93d3-118">若要复制完整的示例，请参阅本教程结尾部分的 [完整示例](#CompleteExample) 。</span><span class="sxs-lookup"><span data-stu-id="a93d3-118">To copy the complete example, see [Complete Example](#CompleteExample) at the end of this tutorial.</span></span>  
  
## <a name="1-configure-the-environment"></a><span data-ttu-id="a93d3-119">1.配置环境</span><span class="sxs-lookup"><span data-stu-id="a93d3-119">1. Configure the Environment</span></span>  
 <span data-ttu-id="a93d3-120">使用 [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] 和以下代码打开 `AdventureWorks2012` 数据库，然后使用 `CURRENT_USER` [!INCLUDE[tsql](../includes/tsql-md.md)] 语句检查 dbo 用户是否显示为上下文。</span><span class="sxs-lookup"><span data-stu-id="a93d3-120">Use [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] and the following code to open the `AdventureWorks2012` database, and use the `CURRENT_USER` [!INCLUDE[tsql](../includes/tsql-md.md)] statement to check that the dbo user is displayed as the context.</span></span>  
  
```  
USE AdventureWorks2012;  
GO  
SELECT CURRENT_USER AS 'Current User Name';  
GO  
```  
  
 <span data-ttu-id="a93d3-121">有关 CURRENT_USER 语句的详细信息，请参阅 [CURRENT_USER (Transact-SQL)](/sql/t-sql/functions/current-user-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="a93d3-121">For more information about the CURRENT_USER statement, see [CURRENT_USER &#40;Transact-SQL&#41;](/sql/t-sql/functions/current-user-transact-sql).</span></span>  
  
 <span data-ttu-id="a93d3-122">使用此代码以使 dbo 用户在服务器及 [!INCLUDE[ssSampleDBobject](../includes/sssampledbobject-md.md)] 数据库中创建两个用户。</span><span class="sxs-lookup"><span data-stu-id="a93d3-122">Use this code as the dbo user to create two users on the server and in the [!INCLUDE[ssSampleDBobject](../includes/sssampledbobject-md.md)] database.</span></span>  
  
```  
CREATE LOGIN TestManagerUser   
    WITH PASSWORD = '340$Uuxwp7Mcxo7Khx';  
GO  
CREATE USER TestManagerUser   
   FOR LOGIN TestManagerUser  
   WITH DEFAULT_SCHEMA = Purchasing;  
GO   
  
CREATE LOGIN TestEmployeeUser  
    WITH PASSWORD = '340$Uuxwp7Mcxo7Khy';  
GO  
CREATE USER TestEmployeeUser   
   FOR LOGIN TestEmployeeUser;  
GO   
```  
  
 <span data-ttu-id="a93d3-123">有关 CREATE USER 语句的详细信息，请参阅 [CREATE USER (Transact-SQL)](/sql/t-sql/statements/create-user-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="a93d3-123">For more information about the CREATE USER statement, see [CREATE USER &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-user-transact-sql).</span></span> <span data-ttu-id="a93d3-124">有关 CREATE LOGIN 语句的详细信息，请参阅 [CREATE LOGIN (Transact-SQL)](/sql/t-sql/statements/create-login-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="a93d3-124">For more information about the CREATE LOGIN statement, see [CREATE LOGIN &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-login-transact-sql).</span></span>  
  
 <span data-ttu-id="a93d3-125">使用以下代码将 `Purchasing` 架构的所有权更改为 `TestManagerUser` 帐户。</span><span class="sxs-lookup"><span data-stu-id="a93d3-125">Use the following code to change the ownership of the `Purchasing` schema to the `TestManagerUser` account.</span></span> <span data-ttu-id="a93d3-126">这样将允许该帐户对其包含的对象使用所有数据操作语言 (DML) 语句访问权限（如 `SELECT` 和 `INSERT` 权限）。</span><span class="sxs-lookup"><span data-stu-id="a93d3-126">This allows that account to use all Data Manipulation Language (DML) statement access (such as `SELECT` and `INSERT` permissions) on the objects it contains.</span></span> <span data-ttu-id="a93d3-127">`TestManagerUser` 授予创建存储过程的能力。</span><span class="sxs-lookup"><span data-stu-id="a93d3-127">`TestManagerUser` is also granted the ability to create stored procedures.</span></span>  
  
```  
/* Change owner of the Purchasing Schema to TestManagerUser */  
ALTER AUTHORIZATION   
   ON SCHEMA::Purchasing   
   TO TestManagerUser;  
GO  
  
GRANT CREATE PROCEDURE   
   TO TestManagerUser   
   WITH GRANT OPTION;  
GO  
```  
  
 <span data-ttu-id="a93d3-128">有关 GRANT 语句的详细信息，请参阅 [GRANT (Transact-SQL)](/sql/t-sql/statements/grant-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="a93d3-128">For more information about the GRANT statement, see [GRANT &#40;Transact-SQL&#41;](/sql/t-sql/statements/grant-transact-sql).</span></span> <span data-ttu-id="a93d3-129">有关存储过程的详细信息，请参阅[存储过程（数据库引擎）](stored-procedures/stored-procedures-database-engine.md)。</span><span class="sxs-lookup"><span data-stu-id="a93d3-129">For more information about stored procedures, see [Stored Procedures &#40;Database Engine&#41;](stored-procedures/stored-procedures-database-engine.md).</span></span> <span data-ttu-id="a93d3-130">有关所有权限的海报 [!INCLUDE[ssDE](../includes/ssde-md.md)] ，请参阅 [https://github.com/microsoft/sql-server-samples/blob/master/samples/features/security/permissions-posters/Microsoft_SQL_Server_2017_and_Azure_SQL_Database_permissions_infographic.pdf](https://github.com/microsoft/sql-server-samples/blob/master/samples/features/security/permissions-posters/Microsoft_SQL_Server_2017_and_Azure_SQL_Database_permissions_infographic.pdf) 。</span><span class="sxs-lookup"><span data-stu-id="a93d3-130">For a poster of all [!INCLUDE[ssDE](../includes/ssde-md.md)] permissions, see [https://github.com/microsoft/sql-server-samples/blob/master/samples/features/security/permissions-posters/Microsoft_SQL_Server_2017_and_Azure_SQL_Database_permissions_infographic.pdf](https://github.com/microsoft/sql-server-samples/blob/master/samples/features/security/permissions-posters/Microsoft_SQL_Server_2017_and_Azure_SQL_Database_permissions_infographic.pdf).</span></span>  
  
## <a name="2-create-a-stored-procedure-to-access-data"></a><span data-ttu-id="a93d3-131">2.创建存储过程以访问数据</span><span class="sxs-lookup"><span data-stu-id="a93d3-131">2. Create a Stored Procedure to Access Data</span></span>  
 <span data-ttu-id="a93d3-132">若要切换数据库内的上下文，请使用 EXECUTE AS 语句。</span><span class="sxs-lookup"><span data-stu-id="a93d3-132">To switch context within a database, use the EXECUTE AS statement.</span></span> <span data-ttu-id="a93d3-133">EXECUTE AS 需要 IMPERSONATE 权限。</span><span class="sxs-lookup"><span data-stu-id="a93d3-133">EXECUTE AS requires IMPERSONATE permissions.</span></span>  
  
 <span data-ttu-id="a93d3-134">使用以下代码中的 `EXECUTE AS` 语句将上下文更改为 `TestManagerUser` ，并创建一个仅显示 `TestEmployeeUser`需要的数据的存储过程。</span><span class="sxs-lookup"><span data-stu-id="a93d3-134">Use the `EXECUTE AS` statement in the following code to change the context to `TestManagerUser` and create a stored procedure showing only the data required by `TestEmployeeUser`.</span></span> <span data-ttu-id="a93d3-135">为了满足这些要求，存储过程接受一个代表采购订单号的变量并且不显示财务信息，WHERE 子句则将结果限制为部分货物。</span><span class="sxs-lookup"><span data-stu-id="a93d3-135">To satisfy the requirements, the stored procedure accepts one variable for the purchase order number and does not display financial information, and the WHERE clause limits the results to partial shipments.</span></span>  
  
```  
EXECUTE AS LOGIN = 'TestManagerUser'  
GO  
SELECT CURRENT_USER AS 'Current User Name';  
GO  
  
/* Note: The user that calls the EXECUTE AS statement must have IMPERSONATE permissions on the target principal */  
CREATE PROCEDURE usp_ShowWaitingItems @ProductID int  
AS  
BEGIN   
   SELECT a.PurchaseOrderID, a.OrderDate, a.ShipDate  
      , b.ProductID, b.OrderQty, b.ReceivedQty  
   FROM Purchasing.PurchaseOrderHeader a  
      INNER JOIN Purchasing.PurchaseOrderDetail b  
         ON a.PurchaseOrderID = b.PurchaseOrderID  
   WHERE b.OrderQty > b.ReceivedQty  
      AND @ProductID = b.ProductID  
   ORDER BY b.ProductID ASC  
END  
GO  
```  
  
 <span data-ttu-id="a93d3-136">当前 `TestEmployeeUser` 对任何数据库对象都没有访问权限。</span><span class="sxs-lookup"><span data-stu-id="a93d3-136">Currently `TestEmployeeUser` does not have access to any database objects.</span></span> <span data-ttu-id="a93d3-137">以下代码（仍位于 `TestManagerUser` 上下文中）授予用户帐户通过存储过程查询基表信息的能力。</span><span class="sxs-lookup"><span data-stu-id="a93d3-137">The following code (still in the `TestManagerUser` context) grants the user account the ability to query base-table information through the stored procedure.</span></span>  
  
```  
GRANT EXECUTE  
   ON OBJECT::Purchasing.usp_ShowWaitingItems  
   TO TestEmployeeUser;  
GO  
```  
  
 <span data-ttu-id="a93d3-138">即使没有显式指定架构，存储过程也是 `Purchasing` 架构的一部分，因为默认情况下系统将把 `TestManagerUser` 分配给 `Purchasing` 架构。</span><span class="sxs-lookup"><span data-stu-id="a93d3-138">The stored procedure is part of the `Purchasing` schema, even though no schema was explicitly specified, because `TestManagerUser` is assigned by default to the `Purchasing` schema.</span></span> <span data-ttu-id="a93d3-139">您可以使用系统目录信息查找对象，如以下代码所示。</span><span class="sxs-lookup"><span data-stu-id="a93d3-139">You can use system catalog information to locate objects, as shown in the following code.</span></span>  
  
```  
SELECT a.name AS 'Schema'  
   , b.name AS 'Object Name'  
   , b.type AS 'Object Type'  
FROM sys.schemas a  
   INNER JOIN sys.objects b  
      ON a.schema_id = b.schema_id   
WHERE b.name = 'usp_ShowWaitingItems';  
GO  
```  
  
 <span data-ttu-id="a93d3-140">完成本部分示例之后，代码使用 `REVERT` 语句将上下文切换回 dbo。</span><span class="sxs-lookup"><span data-stu-id="a93d3-140">With this section of the example completed, the code switches context back to dbo using the `REVERT` statement.</span></span>  
  
```  
REVERT;  
GO  
```  
  
 <span data-ttu-id="a93d3-141">有关 REVERT 语句的详细信息，请参阅 [REVERT (Transact-SQL)](/sql/t-sql/statements/revert-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="a93d3-141">For more information about the REVERT statement, see [REVERT &#40;Transact-SQL&#41;](/sql/t-sql/statements/revert-transact-sql).</span></span>  
  
## <a name="3-access-data-through-the-stored-procedure"></a><span data-ttu-id="a93d3-142">3.通过存储过程访问数据</span><span class="sxs-lookup"><span data-stu-id="a93d3-142">3. Access Data Through the Stored Procedure</span></span>  
 <span data-ttu-id="a93d3-143">`TestEmployeeUser` 除了拥有一个登录名以及分配给公共数据库角色的权限之外，对 [!INCLUDE[ssSampleDBobject](../includes/sssampledbobject-md.md)] 数据库对象没有其他权限。</span><span class="sxs-lookup"><span data-stu-id="a93d3-143">`TestEmployeeUser` has no permissions on the [!INCLUDE[ssSampleDBobject](../includes/sssampledbobject-md.md)] database objects other than a login and the rights assigned to the public database role.</span></span> <span data-ttu-id="a93d3-144">如果 `TestEmployeeUser` 试图访问基表，以下代码在将返回一个错误。</span><span class="sxs-lookup"><span data-stu-id="a93d3-144">The following code returns an error when `TestEmployeeUser` attempts to access base tables.</span></span>  
  
```  
EXECUTE AS LOGIN = 'TestEmployeeUser'  
GO  
SELECT CURRENT_USER AS 'Current User Name';  
GO  
/* This won't work */  
SELECT *  
FROM Purchasing.PurchaseOrderHeader;  
GO  
SELECT *  
FROM Purchasing.PurchaseOrderDetail;  
GO  
```  
  
 <span data-ttu-id="a93d3-145">因为在最后一部分中创建的存储过程引用的对象由 `TestManagerUser` 凭借 `Purchasing` 架构所有权而拥有，因此 `TestEmployeeUser` 可以通过此存储过程访问基表。</span><span class="sxs-lookup"><span data-stu-id="a93d3-145">Because the objects referenced by the stored procedure created in the last section are owned by `TestManagerUser` by virtue of the `Purchasing` schema ownership, `TestEmployeeUser` can access the base tables through the stored procedure.</span></span> <span data-ttu-id="a93d3-146">以下代码仍使用 `TestEmployeeUser` 上下文将采购订单 952 作为参数传递。</span><span class="sxs-lookup"><span data-stu-id="a93d3-146">The following code, still using the `TestEmployeeUser` context, passes purchase order 952 as a parameter.</span></span>  
  
```  
EXEC Purchasing.usp_ShowWaitingItems 952  
GO  
```  
  
## <a name="4-reset-the-environment"></a><span data-ttu-id="a93d3-147">4.重置环境</span><span class="sxs-lookup"><span data-stu-id="a93d3-147">4. Reset the Environment</span></span>  
 <span data-ttu-id="a93d3-148">以下代码使用 `REVERT` 命令将当前帐户的上下文返回至 `dbo`，然后重置环境。</span><span class="sxs-lookup"><span data-stu-id="a93d3-148">The following code uses the `REVERT` command to return the context of the current account to `dbo`, and then resets the environment.</span></span>  
  
```  
REVERT;  
GO  
ALTER AUTHORIZATION   
ON SCHEMA::Purchasing TO dbo;  
GO  
DROP PROCEDURE Purchasing.usp_ShowWaitingItems;  
GO  
DROP USER TestEmployeeUser;  
GO  
DROP USER TestManagerUser;  
GO  
DROP LOGIN TestEmployeeUser;  
GO  
DROP LOGIN TestManagerUser;  
GO  
```  
  
##  <a name="complete-example"></a><a name="CompleteExample"></a><span data-ttu-id="a93d3-149">完整示例</span><span class="sxs-lookup"><span data-stu-id="a93d3-149">Complete Example</span></span>  
 <span data-ttu-id="a93d3-150">本部分显示完整的示例代码。</span><span class="sxs-lookup"><span data-stu-id="a93d3-150">This section displays the complete example code.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="a93d3-151">此代码不包括两个说明 `TestEmployeeUser` 无法从基表中进行选择的预期错误。</span><span class="sxs-lookup"><span data-stu-id="a93d3-151">This code does not include the two expected errors that demonstrate the inability of `TestEmployeeUser` to select from base tables.</span></span>  
  
```  
/*   
Script:       UserContextTutorial.sql  
Author:       Microsoft  
Last Updated: Books Online  
Conditions:   Execute as DBO or sysadmin in the AdventureWorks database  
Section 1:    Configure the Environment   
*/  
USE AdventureWorks2012;  
GO  
SELECT CURRENT_USER AS 'Current User Name';  
GO  
/* Create server and database users */  
CREATE LOGIN TestManagerUser   
    WITH PASSWORD = '340$Uuxwp7Mcxo7Khx';  
  
GO  
  
CREATE USER TestManagerUser   
   FOR LOGIN TestManagerUser  
   WITH DEFAULT_SCHEMA = Purchasing;  
GO   
  
CREATE LOGIN TestEmployeeUser  
    WITH PASSWORD = '340$Uuxwp7Mcxo7Khy';  
GO  
CREATE USER TestEmployeeUser   
   FOR LOGIN TestEmployeeUser;  
GO   
  
/* Change owner of the Purchasing Schema to TestManagerUser */  
ALTER AUTHORIZATION   
   ON SCHEMA::Purchasing   
   TO TestManagerUser;  
GO  
  
GRANT CREATE PROCEDURE   
   TO TestManagerUser   
   WITH GRANT OPTION;  
GO  
  
/*   
Section 2: Switch Context and Create Objects  
*/  
EXECUTE AS LOGIN = 'TestManagerUser';  
GO  
SELECT CURRENT_USER AS 'Current User Name';  
GO  
  
/* Note: The user that calls the EXECUTE AS statement must have IMPERSONATE permissions on the target principal */  
CREATE PROCEDURE usp_ShowWaitingItems @ProductID int  
AS  
BEGIN   
   SELECT a.PurchaseOrderID, a.OrderDate, a.ShipDate  
      , b.ProductID, b.OrderQty, b.ReceivedQty  
   FROM Purchasing.PurchaseOrderHeader AS a  
      INNER JOIN Purchasing.PurchaseOrderDetail AS b  
         ON a.PurchaseOrderID = b.PurchaseOrderID  
   WHERE b.OrderQty > b.ReceivedQty  
      AND @ProductID = b.ProductID  
   ORDER BY b.ProductID ASC  
END;  
GO  
  
/* Give the employee the ability to run the procedure */  
GRANT EXECUTE   
   ON OBJECT::Purchasing.usp_ShowWaitingItems  
   TO TestEmployeeUser;  
GO   
  
/* Notice that the stored procedure is located in the Purchasing   
schema. This also demonstrates system catalogs */  
SELECT a.name AS 'Schema'  
   , b.name AS 'Object Name'  
   , b.type AS 'Object Type'  
FROM sys.schemas AS a  
   INNER JOIN sys.objects AS b  
      ON a.schema_id = b.schema_id   
WHERE b.name = 'usp_ShowWaitingItems';  
GO  
  
/* Go back to being the dbo user */  
REVERT;  
GO  
  
/*  
Section 3: Switch Context and Observe Security   
*/  
EXECUTE AS LOGIN = 'TestEmployeeUser';  
GO  
SELECT CURRENT_USER AS 'Current User Name';  
GO  
EXEC Purchasing.usp_ShowWaitingItems 952;  
GO  
  
/*   
Section 4: Clean Up Example  
*/  
REVERT;  
GO  
ALTER AUTHORIZATION   
ON SCHEMA::Purchasing TO dbo;  
GO  
DROP PROCEDURE Purchasing.usp_ShowWaitingItems;  
GO  
DROP USER TestEmployeeUser;  
GO  
DROP USER TestManagerUser;  
GO  
DROP LOGIN TestEmployeeUser;  
GO  
DROP LOGIN TestManagerUser;  
GO  
```  
  
## <a name="see-also"></a><span data-ttu-id="a93d3-152">另请参阅</span><span class="sxs-lookup"><span data-stu-id="a93d3-152">See Also</span></span>  
 [<span data-ttu-id="a93d3-153">SQL Server 数据库引擎和 Azure SQL Database 的安全中心</span><span class="sxs-lookup"><span data-stu-id="a93d3-153">Security Center for SQL Server Database Engine and Azure SQL Database</span></span>](security/security-center-for-sql-server-database-engine-and-azure-sql-database.md)  
  
  
