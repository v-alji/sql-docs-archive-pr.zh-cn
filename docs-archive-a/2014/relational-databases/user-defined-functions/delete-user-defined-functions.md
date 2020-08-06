---
title: 删除用户定义函数 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
ms.assetid: db1d668a-23b7-4757-a9c5-1bd848ba7f6d
author: rothja
ms.author: jroth
ms.openlocfilehash: e5f6b2b306c4fe8db08b088d9607cfb19ab0f25e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87590600"
---
# <a name="delete-user-defined-functions"></a><span data-ttu-id="6d0de-102">删除用户定义函数</span><span class="sxs-lookup"><span data-stu-id="6d0de-102">Delete User-defined Functions</span></span>
  <span data-ttu-id="6d0de-103">你可以通过使用 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 删除 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 中的用户定义函数 [!INCLUDE[tsql](../../includes/tsql-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6d0de-103">You can delete (drop) user-defined functions in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)]</span></span>  
  
 <span data-ttu-id="6d0de-104">**本主题内容**</span><span class="sxs-lookup"><span data-stu-id="6d0de-104">**In This Topic**</span></span>  
  
-   <span data-ttu-id="6d0de-105">**开始之前：**</span><span class="sxs-lookup"><span data-stu-id="6d0de-105">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="6d0de-106">限制和局限</span><span class="sxs-lookup"><span data-stu-id="6d0de-106">Limitations and Restrictions</span></span>](#Restrictions)  
  
     [<span data-ttu-id="6d0de-107">安全性</span><span class="sxs-lookup"><span data-stu-id="6d0de-107">Security</span></span>](#Security)  
  
-   <span data-ttu-id="6d0de-108">**若要删除用户定义函数，请使用：**</span><span class="sxs-lookup"><span data-stu-id="6d0de-108">**To delete a user-defined function, using:**</span></span>  
  
     [<span data-ttu-id="6d0de-109">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="6d0de-109">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="6d0de-110">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="6d0de-110">Transact-SQL</span></span>](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="6d0de-111">开始之前</span><span class="sxs-lookup"><span data-stu-id="6d0de-111">Before You Begin</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="6d0de-112">限制和局限</span><span class="sxs-lookup"><span data-stu-id="6d0de-112">Limitations and Restrictions</span></span>  
  
-   <span data-ttu-id="6d0de-113">如果数据库中存在引用此函数的 Transact-SQL 函数或视图并且这些函数或视图通过使用 SCHEMABINDING 创建，或者存在引用该函数的计算列、CHECK 约束或 DEFAULT 约束，则您将无法删除该函数。</span><span class="sxs-lookup"><span data-stu-id="6d0de-113">You will not be able to delete the function if there are Transact-SQL functions or views in the database that reference this function and were created by using SCHEMABINDING, or if there are computed columns, CHECK constraints, or DEFAULT constraints that reference the function.</span></span>  
  
-   <span data-ttu-id="6d0de-114">如果存在引用此函数并且已生成索引的计算列，则您将无法删除该函数。</span><span class="sxs-lookup"><span data-stu-id="6d0de-114">You will not be able to delete the function if there are computed columns that reference this function and have been indexed.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="6d0de-115">Security</span><span class="sxs-lookup"><span data-stu-id="6d0de-115">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="6d0de-116">权限</span><span class="sxs-lookup"><span data-stu-id="6d0de-116">Permissions</span></span>  
 <span data-ttu-id="6d0de-117">需要具有对该函数所属架构的 ALTER 权限，或对该函数的 CONTROL 权限。</span><span class="sxs-lookup"><span data-stu-id="6d0de-117">Requires ALTER permission on the schema to which the function belongs, or CONTROL permission on the function.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="6d0de-118">使用 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="6d0de-118">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-delete-a-user-defined-function"></a><span data-ttu-id="6d0de-119">删除用户定义函数</span><span class="sxs-lookup"><span data-stu-id="6d0de-119">To delete a user-defined function</span></span>  
  
1.  <span data-ttu-id="6d0de-120">单击包含要修改的函数的数据库旁边的加号。</span><span class="sxs-lookup"><span data-stu-id="6d0de-120">Click on the plus sign next to the database that contains the function you wish to modify.</span></span>  
  
2.  <span data-ttu-id="6d0de-121">单击 **“可编程性”** 文件夹旁的加号。</span><span class="sxs-lookup"><span data-stu-id="6d0de-121">Click on the plus sign next to the **Programmability** folder.</span></span>  
  
3.  <span data-ttu-id="6d0de-122">单击包含要修改的函数的文件夹旁边的加号：</span><span class="sxs-lookup"><span data-stu-id="6d0de-122">Click the plus sign next to the folder that contains the function you wish to modify:</span></span>  
  
    -   <span data-ttu-id="6d0de-123">Table-valued Function</span><span class="sxs-lookup"><span data-stu-id="6d0de-123">Table-valued Function</span></span>  
  
    -   <span data-ttu-id="6d0de-124">标量值函数</span><span class="sxs-lookup"><span data-stu-id="6d0de-124">Scalar-valued Function</span></span>  
  
    -   <span data-ttu-id="6d0de-125">Aggregate 函数</span><span class="sxs-lookup"><span data-stu-id="6d0de-125">Aggregate Function</span></span>  
  
4.  <span data-ttu-id="6d0de-126">右键单击要删除的函数，然后选择“删除”  。</span><span class="sxs-lookup"><span data-stu-id="6d0de-126">Right-click the function you want to delete and select **Delete**.</span></span>  
  
5.  <span data-ttu-id="6d0de-127">在 **“删除对象”** 对话框中，单击 **“确定”** 。</span><span class="sxs-lookup"><span data-stu-id="6d0de-127">In the **Delete Object** dialog box, click **OK**.</span></span>  
  
    > [!IMPORTANT]  
    >  <span data-ttu-id="6d0de-128">单击 "**删除对象**" 对话框中的 "**显示依赖关系**"，打开 " _function_name_**依赖**关系" 对话框。</span><span class="sxs-lookup"><span data-stu-id="6d0de-128">Click **Show Dependencies** in the **Delete Object** dialog box to open the _function_name_**Dependencies** dialog box.</span></span> <span data-ttu-id="6d0de-129">这将显示依赖于该函数的所有对象和该函数依赖的所有对象。</span><span class="sxs-lookup"><span data-stu-id="6d0de-129">This will show all of the objects that depend on the function and all of the objects on which the function depends.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="6d0de-130">使用 Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="6d0de-130">Using Transact-SQL</span></span>  
  
#### <a name="to-delete-a-user-defined-function"></a><span data-ttu-id="6d0de-131">删除用户定义函数</span><span class="sxs-lookup"><span data-stu-id="6d0de-131">To delete a user-defined function</span></span>  
  
1.  <span data-ttu-id="6d0de-132">在 **“对象资源管理器”** 中，连接到 [!INCLUDE[ssDE](../../includes/ssde-md.md)]的实例。</span><span class="sxs-lookup"><span data-stu-id="6d0de-132">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="6d0de-133">在标准菜单栏上，单击 **“新建查询”** 。</span><span class="sxs-lookup"><span data-stu-id="6d0de-133">On the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="6d0de-134">将以下示例复制并粘贴到查询窗口中，然后单击“执行”  。</span><span class="sxs-lookup"><span data-stu-id="6d0de-134">Copy and paste the following example into the query window and click **Execute**.</span></span>  
  
    ```  
    -- creates function called "Sales.ufn_SalesByStore"  
    USE AdventureWorks2012;  
    GO  
    CREATE FUNCTION Sales.ufn_SalesByStore (@storeid int)  
    RETURNS TABLE  
    AS  
    RETURN   
    (  
        SELECT P.ProductID, P.Name, SUM(SD.LineTotal) AS 'Total'  
        FROM Production.Product AS P   
        JOIN Sales.SalesOrderDetail AS SD ON SD.ProductID = P.ProductID  
        JOIN Sales.SalesOrderHeader AS SH ON SH.SalesOrderID = SD.SalesOrderID  
        JOIN Sales.Customer AS C ON SH.CustomerID = C.CustomerID  
        WHERE C.StoreID = @storeid  
        GROUP BY P.ProductID, P.Name  
    );  
    GO  
    ```  
  
    ```  
    USE AdventureWorks2012;  
    GO  
    -- determines if function exists in database  
    IF OBJECT_ID (N'Sales.fn_SalesByStore', N'IF') IS NOT NULL  
    -- deletes function  
        DROP FUNCTION Sales.fn_SalesByStore;  
    GO  
    ```  
  
 <span data-ttu-id="6d0de-135">有关详细信息，请参阅 [DROP FUNCTION (Transact-SQL)](/sql/t-sql/statements/drop-function-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="6d0de-135">For more information, see [DROP FUNCTION &#40;Transact-SQL&#41;](/sql/t-sql/statements/drop-function-transact-sql).</span></span>  
  
  
