---
title: 修改用户定义函数 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
ms.assetid: 891c37b3-cb72-411f-9937-ee87e6d95f34
author: rothja
ms.author: jroth
ms.openlocfilehash: 1cf25fef91834e237f5cbaac26350220840830bc
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87590597"
---
# <a name="modify-user-defined-functions"></a><span data-ttu-id="e14c3-102">修改用户定义函数</span><span class="sxs-lookup"><span data-stu-id="e14c3-102">Modify User-defined Functions</span></span>
  <span data-ttu-id="e14c3-103">您可以通过使用 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 或 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 修改 [!INCLUDE[tsql](../../includes/tsql-md.md)]中的用户定义函数。</span><span class="sxs-lookup"><span data-stu-id="e14c3-103">You can modify user-defined functions in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span> <span data-ttu-id="e14c3-104">按如下所述修改用户定义函数将不会更改函数的权限，并且也不会影响任何依赖的函数、存储过程或触发器。</span><span class="sxs-lookup"><span data-stu-id="e14c3-104">Modifying user-defined functions as described below will not change the functions' permissions, nor will it affect any dependent functions, stored procedures, or triggers.</span></span>  
  
 <span data-ttu-id="e14c3-105">**本主题内容**</span><span class="sxs-lookup"><span data-stu-id="e14c3-105">**In This Topic**</span></span>  
  
-   <span data-ttu-id="e14c3-106">**开始之前：**</span><span class="sxs-lookup"><span data-stu-id="e14c3-106">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="e14c3-107">限制和局限</span><span class="sxs-lookup"><span data-stu-id="e14c3-107">Limitations and Restrictions</span></span>](#Restrictions)  
  
     [<span data-ttu-id="e14c3-108">安全性</span><span class="sxs-lookup"><span data-stu-id="e14c3-108">Security</span></span>](#Security)  
  
-   <span data-ttu-id="e14c3-109">**若要修改用户定义函数，请使用：**</span><span class="sxs-lookup"><span data-stu-id="e14c3-109">**To modify a user-defined function, using:**</span></span>  
  
     [<span data-ttu-id="e14c3-110">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="e14c3-110">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="e14c3-111">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="e14c3-111">Transact-SQL</span></span>](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="e14c3-112">开始之前</span><span class="sxs-lookup"><span data-stu-id="e14c3-112">Before You Begin</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="e14c3-113">限制和局限</span><span class="sxs-lookup"><span data-stu-id="e14c3-113">Limitations and Restrictions</span></span>  
 <span data-ttu-id="e14c3-114">ALTER FUNCTION 不能用于执行以下任何操作：</span><span class="sxs-lookup"><span data-stu-id="e14c3-114">ALTER FUNCTION cannot be used to perform any of the following actions:</span></span>  
  
-   <span data-ttu-id="e14c3-115">将标量值函数更改为表值函数，反之亦然。</span><span class="sxs-lookup"><span data-stu-id="e14c3-115">Change a scalar-valued function to a table-valued function, or vice versa.</span></span>  
  
-   <span data-ttu-id="e14c3-116">将内联函数更改为多语句函数，反之亦然。</span><span class="sxs-lookup"><span data-stu-id="e14c3-116">Change an inline function to a multistatement function, or vice versa.</span></span>  
  
-   <span data-ttu-id="e14c3-117">将 Transact-SQL 函数更改为 CLR 函数，反之亦然。</span><span class="sxs-lookup"><span data-stu-id="e14c3-117">Change a Transact-SQL function to a CLR function, or vice-versa.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="e14c3-118">Security</span><span class="sxs-lookup"><span data-stu-id="e14c3-118">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="e14c3-119">权限</span><span class="sxs-lookup"><span data-stu-id="e14c3-119">Permissions</span></span>  
 <span data-ttu-id="e14c3-120">需要对函数或架构具有 ALTER 权限。</span><span class="sxs-lookup"><span data-stu-id="e14c3-120">Requires ALTER permission on the function or on the schema.</span></span> <span data-ttu-id="e14c3-121">如果函数指定用户定义类型，则需要对该类型具有 EXECUTE 权限。</span><span class="sxs-lookup"><span data-stu-id="e14c3-121">If the function specifies a user-defined type, requires EXECUTE permission on the type.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="e14c3-122">使用 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="e14c3-122">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-modify-a-user-defined-function"></a><span data-ttu-id="e14c3-123">修改用户定义函数</span><span class="sxs-lookup"><span data-stu-id="e14c3-123">To modify a user-defined function</span></span>  
  
1.  <span data-ttu-id="e14c3-124">单击包含要修改的函数的数据库旁边的加号。</span><span class="sxs-lookup"><span data-stu-id="e14c3-124">Click on the plus sign next to the database that contains the function you wish to modify.</span></span>  
  
2.  <span data-ttu-id="e14c3-125">单击 **“可编程性”** 文件夹旁的加号。</span><span class="sxs-lookup"><span data-stu-id="e14c3-125">Click on the plus sign next to the **Programmability** folder.</span></span>  
  
3.  <span data-ttu-id="e14c3-126">单击包含要修改的函数的文件夹旁边的加号：</span><span class="sxs-lookup"><span data-stu-id="e14c3-126">Click the plus sign next to the folder that contains the function you wish to modify:</span></span>  
  
    -   <span data-ttu-id="e14c3-127">Table-valued Function</span><span class="sxs-lookup"><span data-stu-id="e14c3-127">Table-valued Function</span></span>  
  
    -   <span data-ttu-id="e14c3-128">标量值函数</span><span class="sxs-lookup"><span data-stu-id="e14c3-128">Scalar-valued Function</span></span>  
  
    -   <span data-ttu-id="e14c3-129">Aggregate 函数</span><span class="sxs-lookup"><span data-stu-id="e14c3-129">Aggregate Function</span></span>  
  
4.  <span data-ttu-id="e14c3-130">右键单击要修改的函数，然后单击“修改”  。</span><span class="sxs-lookup"><span data-stu-id="e14c3-130">Right-click the function you want to modify and select **Modify**.</span></span>  
  
5.  <span data-ttu-id="e14c3-131">在查询窗口中，对 ALTER FUNCTION 语句进行必要的更改。</span><span class="sxs-lookup"><span data-stu-id="e14c3-131">In the Query Window, make the necessary changes to the ALTER FUNCTION statement.</span></span>  
  
6.  <span data-ttu-id="e14c3-132">在“文件”  菜单上，点击“保存”  function_name  。</span><span class="sxs-lookup"><span data-stu-id="e14c3-132">On the **File** menu, click **Save**_function_name_.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="e14c3-133">使用 Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="e14c3-133">Using Transact-SQL</span></span>  
  
#### <a name="to-modify-a-user-defined-function"></a><span data-ttu-id="e14c3-134">修改用户定义函数</span><span class="sxs-lookup"><span data-stu-id="e14c3-134">To modify a user-defined function</span></span>  
  
1.  <span data-ttu-id="e14c3-135">在 **“对象资源管理器”** 中，连接到 [!INCLUDE[ssDE](../../includes/ssde-md.md)]的实例。</span><span class="sxs-lookup"><span data-stu-id="e14c3-135">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="e14c3-136">在标准菜单栏上，单击 **“新建查询”** 。</span><span class="sxs-lookup"><span data-stu-id="e14c3-136">On the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="e14c3-137">将以下示例复制并粘贴到查询窗口中，然后单击“执行”  。</span><span class="sxs-lookup"><span data-stu-id="e14c3-137">Copy and paste the following example into the query window and click **Execute**.</span></span>  
  
    ```  
    -- Scalar-Valued Function  
    USE [AdventureWorks2012]  
    GO  
    ALTER FUNCTION [dbo].[ufnGetAccountingEndDate]()  
    RETURNS [datetime]   
    AS   
    BEGIN  
        RETURN DATEADD(millisecond, -2, CONVERT(datetime, '20040701', 112));  
    END;  
    ```  
  
    ```  
    -- Table-Valued Function   
    USE [AdventureWorks2012]  
    GO  
    ALTER FUNCTION [dbo].[ufnGetContactInformation](@PersonID int)  
    RETURNS @retContactInformation TABLE   
    (  
        -- Columns returned by the function  
        [PersonID] int NOT NULL,   
        [FirstName] [nvarchar](50) NULL,   
        [LastName] [nvarchar](50) NULL,   
        [JobTitle] [nvarchar](50) NULL,  
        [BusinessEntityType] [nvarchar](50) NULL  
    )  
    AS   
    -- Returns the first name, last name, job title and business entity type for the specified contact.  
    -- Since a contact can serve multiple roles, more than one row may be returned.  
    BEGIN  
    IF @PersonID IS NOT NULL   
    BEGIN  
         IF EXISTS(SELECT * FROM [HumanResources].[Employee] e   
         WHERE e.[BusinessEntityID] = @PersonID)   
         INSERT INTO @retContactInformation  
              SELECT @PersonID, p.FirstName, p.LastName, e.[JobTitle], 'Employee'  
              FROM [HumanResources].[Employee] AS e  
              INNER JOIN [Person].[Person] p ON p.[BusinessEntityID] = e.[BusinessEntityID]  
              WHERE e.[BusinessEntityID] = @PersonID;  
  
         IF EXISTS(SELECT * FROM [Purchasing].[Vendor] AS v  
         INNER JOIN [Person].[BusinessEntityContact] bec ON bec.[BusinessEntityID] = v.[BusinessEntityID]  
         WHERE bec.[PersonID] = @PersonID)  
         INSERT INTO @retContactInformation  
              SELECT @PersonID, p.FirstName, p.LastName, ct.[Name], 'Vendor Contact'   
              FROM [Purchasing].[Vendor] AS v  
              INNER JOIN [Person].[BusinessEntityContact] bec ON bec.[BusinessEntityID] = v.[BusinessEntityID]  
              INNER JOIN [Person].ContactType ct ON ct.[ContactTypeID] = bec.[ContactTypeID]  
              INNER JOIN [Person].[Person] p ON p.[BusinessEntityID] = bec.[PersonID]  
              WHERE bec.[PersonID] = @PersonID;  
  
         IF EXISTS(SELECT * FROM [Sales].[Store] AS s  
         INNER JOIN [Person].[BusinessEntityContact] bec ON bec.[BusinessEntityID] = s.[BusinessEntityID]  
         WHERE bec.[PersonID] = @PersonID)  
         INSERT INTO @retContactInformation  
              SELECT @PersonID, p.FirstName, p.LastName, ct.[Name], 'Store Contact'   
              FROM [Sales].[Store] AS s  
              INNER JOIN [Person].[BusinessEntityContact] bec ON bec.[BusinessEntityID] = s.[BusinessEntityID]  
              INNER JOIN [Person].ContactType ct ON ct.[ContactTypeID] = bec.[ContactTypeID]  
              INNER JOIN [Person].[Person] p ON p.[BusinessEntityID] = bec.[PersonID]  
              WHERE bec.[PersonID] = @PersonID;  
  
         IF EXISTS(SELECT * FROM [Person].[Person] AS p  
         INNER JOIN [Sales].[Customer] AS c ON c.[PersonID] = p.[BusinessEntityID]  
         WHERE p.[BusinessEntityID] = @PersonID AND c.[StoreID] IS NULL)   
         INSERT INTO @retContactInformation  
              SELECT @PersonID, p.FirstName, p.LastName, NULL, 'Consumer'   
              FROM [Person].[Person] AS p  
              INNER JOIN [Sales].[Customer] AS c ON c.[PersonID] = p.[BusinessEntityID]  
              WHERE p.[BusinessEntityID] = @PersonID AND c.[StoreID] IS NULL;   
         END  
    RETURN;  
    END;  
    ```  
  
 <span data-ttu-id="e14c3-138">有关详细信息，请参阅[ALTER FUNCTION (Transact-SQL)](/sql/t-sql/statements/alter-function-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="e14c3-138">For more information, see [ALTER FUNCTION &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-function-transact-sql).</span></span>  
  
  
