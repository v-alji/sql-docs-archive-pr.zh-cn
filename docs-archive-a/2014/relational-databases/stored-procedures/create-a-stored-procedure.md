---
title: 创建存储过程 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.technology: stored-procedures
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- new stored procedures
- stored procedures [SQL Server], creating
- creating stored procedures
ms.assetid: 76e8a6ba-1381-4620-b356-4311e1331ca7
author: stevestein
ms.author: sstein
ms.openlocfilehash: f6781840e6a6c84773f40a6cd0557ccb79b676eb
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87590098"
---
# <a name="create-a-stored-procedure"></a><span data-ttu-id="ba94e-102">创建存储过程</span><span class="sxs-lookup"><span data-stu-id="ba94e-102">Create a Stored Procedure</span></span>
  <span data-ttu-id="ba94e-103">本主题介绍了如何通过使用 [!INCLUDE[tsql](../../includes/tsql-md.md)] 和 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] CREATE PROCEDURE 语句来创建 [!INCLUDE[tsql](../../includes/tsql-md.md)] 存储过程。</span><span class="sxs-lookup"><span data-stu-id="ba94e-103">This topic describes how to create a [!INCLUDE[tsql](../../includes/tsql-md.md)] stored procedure by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] and by using the [!INCLUDE[tsql](../../includes/tsql-md.md)] CREATE PROCEDURE statement.</span></span>  
  
##  <a name="Top"></a>   
-   <span data-ttu-id="ba94e-104">**开始之前：** [权限](#Permissions)</span><span class="sxs-lookup"><span data-stu-id="ba94e-104">**Before you begin:**  [Permissions](#Permissions)</span></span>  
  
-   <span data-ttu-id="ba94e-105">**要创建该过程，请使用：** [SQL Server Management Studio](#SSMSProcedure)、[Transact-SQL](#TsqlProcedure)</span><span class="sxs-lookup"><span data-stu-id="ba94e-105">**To create a procedure, using:**  [SQL Server Management Studio](#SSMSProcedure), [Transact-SQL](#TsqlProcedure)</span></span>  
  
##  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="ba94e-106">权限</span><span class="sxs-lookup"><span data-stu-id="ba94e-106">Permissions</span></span>  
 <span data-ttu-id="ba94e-107">需要在数据库中有 CREATE PROCEDURE 权限，对在其中创建过程的架构有 ALTER 权限。</span><span class="sxs-lookup"><span data-stu-id="ba94e-107">Requires CREATE PROCEDURE permission in the database and ALTER permission on the schema in which the procedure is being created.</span></span>  
  
##  <a name="how-to-create-a-stored-procedure"></a><a name="Procedures"></a> <span data-ttu-id="ba94e-108">如何创建存储过程</span><span class="sxs-lookup"><span data-stu-id="ba94e-108">How to Create a Stored Procedure</span></span>  
 <span data-ttu-id="ba94e-109">您可以使用以下项之一：</span><span class="sxs-lookup"><span data-stu-id="ba94e-109">You can use one of the following:</span></span>  
  
-   [<span data-ttu-id="ba94e-110">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="ba94e-110">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
-   [<span data-ttu-id="ba94e-111">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="ba94e-111">Transact-SQL</span></span>](#TsqlProcedure)  
  
###  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="ba94e-112">使用 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="ba94e-112">Using SQL Server Management Studio</span></span>  
 <span data-ttu-id="ba94e-113">**在对象资源管理器中创建过程**</span><span class="sxs-lookup"><span data-stu-id="ba94e-113">**To create a procedure in Object Explorer**</span></span>  
  
1.  <span data-ttu-id="ba94e-114">在 **“对象资源管理器”** 中，连接到 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 的实例，然后展开该实例。</span><span class="sxs-lookup"><span data-stu-id="ba94e-114">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../includes/ssde-md.md)] and then expand that instance.</span></span>  
  
2.  <span data-ttu-id="ba94e-115">依次展开 **“数据库”** 、 [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] 数据库和 **“可编程性”** 。</span><span class="sxs-lookup"><span data-stu-id="ba94e-115">Expand **Databases**, expand the [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] database, and then expand **Programmability**.</span></span>  
  
3.  <span data-ttu-id="ba94e-116">右键单击“存储过程”，再单击“新建存储过程”。</span><span class="sxs-lookup"><span data-stu-id="ba94e-116">Right-click **Stored Procedures**, and then click **New Stored Procedure**.</span></span>  
  
4.  <span data-ttu-id="ba94e-117">在 **“查询”** 菜单上，单击 **“指定模板参数的值”** 。</span><span class="sxs-lookup"><span data-stu-id="ba94e-117">On the **Query** menu, click **Specify Values for Template Parameters**.</span></span>  
  
5.  <span data-ttu-id="ba94e-118">在 **“指定模板参数的值”** 对话框中，输入下列所示的参数值。</span><span class="sxs-lookup"><span data-stu-id="ba94e-118">In the **Specify Values for Template Parameters** dialog box, enter the following values for the parameters shown.</span></span>  
  
    |<span data-ttu-id="ba94e-119">参数</span><span class="sxs-lookup"><span data-stu-id="ba94e-119">Parameter</span></span>|<span data-ttu-id="ba94e-120">值</span><span class="sxs-lookup"><span data-stu-id="ba94e-120">Value</span></span>|  
    |---------------|-----------|  
    |<span data-ttu-id="ba94e-121">作者</span><span class="sxs-lookup"><span data-stu-id="ba94e-121">Author</span></span>|<span data-ttu-id="ba94e-122">*您的姓名*</span><span class="sxs-lookup"><span data-stu-id="ba94e-122">*Your name*</span></span>|  
    |<span data-ttu-id="ba94e-123">创建日期</span><span class="sxs-lookup"><span data-stu-id="ba94e-123">Create Date</span></span>|<span data-ttu-id="ba94e-124">*今天的日期*</span><span class="sxs-lookup"><span data-stu-id="ba94e-124">*Today's date*</span></span>|  
    |<span data-ttu-id="ba94e-125">说明</span><span class="sxs-lookup"><span data-stu-id="ba94e-125">Description</span></span>|<span data-ttu-id="ba94e-126">返回雇员数据。</span><span class="sxs-lookup"><span data-stu-id="ba94e-126">Returns employee data.</span></span>|  
    |<span data-ttu-id="ba94e-127">Procedure_name</span><span class="sxs-lookup"><span data-stu-id="ba94e-127">Procedure_name</span></span>|<span data-ttu-id="ba94e-128">HumanResources.uspGetEmployeesTest</span><span class="sxs-lookup"><span data-stu-id="ba94e-128">HumanResources.uspGetEmployeesTest</span></span>|  
    |@Param1|@LastName|  
    |@Datatype_For_Param1|<span data-ttu-id="ba94e-129">`nvarchar`(50)</span><span class="sxs-lookup"><span data-stu-id="ba94e-129">`nvarchar`(50)</span></span>|  
    |<span data-ttu-id="ba94e-130">Default_Value_For_Param1</span><span class="sxs-lookup"><span data-stu-id="ba94e-130">Default_Value_For_Param1</span></span>|<span data-ttu-id="ba94e-131">Null</span><span class="sxs-lookup"><span data-stu-id="ba94e-131">NULL</span></span>|  
    |@Param2|@FirstName|  
    |@Datatype_For_Param2|<span data-ttu-id="ba94e-132">`nvarchar`(50)</span><span class="sxs-lookup"><span data-stu-id="ba94e-132">`nvarchar`(50)</span></span>|  
    |<span data-ttu-id="ba94e-133">Default_Value_For_Param2</span><span class="sxs-lookup"><span data-stu-id="ba94e-133">Default_Value_For_Param2</span></span>|<span data-ttu-id="ba94e-134">Null</span><span class="sxs-lookup"><span data-stu-id="ba94e-134">NULL</span></span>|  
  
6.  <span data-ttu-id="ba94e-135">单击“确定”。</span><span class="sxs-lookup"><span data-stu-id="ba94e-135">Click **OK**.</span></span>  
  
7.  <span data-ttu-id="ba94e-136">在 **“查询编辑器”** 中，使用以下语句替换 SELECT 语句：</span><span class="sxs-lookup"><span data-stu-id="ba94e-136">In the **Query Editor**, replace the SELECT statement with the following statement:</span></span>  
  
    ```sql  
    SELECT FirstName, LastName, Department  
    FROM HumanResources.vEmployeeDepartmentHistory  
    WHERE FirstName = @FirstName AND LastName = @LastName  
        AND EndDate IS NULL;  
    ```  
  
8.  <span data-ttu-id="ba94e-137">若要测试语法，请在 **“查询”** 菜单上，单击 **“分析”** 。</span><span class="sxs-lookup"><span data-stu-id="ba94e-137">To test the syntax, on the **Query** menu, click **Parse**.</span></span> <span data-ttu-id="ba94e-138">如果返回错误消息，则请将这些语句与上述信息进行比较，并视需要进行更正。</span><span class="sxs-lookup"><span data-stu-id="ba94e-138">If an error message is returned, compare the statements with the information above and correct as needed.</span></span>  
  
9. <span data-ttu-id="ba94e-139">若要创建该过程，请在 **“查询”** 菜单上单击 **“执行”** 。</span><span class="sxs-lookup"><span data-stu-id="ba94e-139">To create the procedure, from  the **Query** menu, click **Execute**.</span></span> <span data-ttu-id="ba94e-140">该过程作为数据库中的对象创建。</span><span class="sxs-lookup"><span data-stu-id="ba94e-140">The procedure is created as an object in the database.</span></span>  
  
10. <span data-ttu-id="ba94e-141">若要查看在对象资源管理器中列出的过程，请右键单击“存储过程”，然后选择“刷新”。</span><span class="sxs-lookup"><span data-stu-id="ba94e-141">To see the procedure listed in Object Explorer, right-click **Stored Procedures** and select **Refresh**.</span></span>  
  
11. <span data-ttu-id="ba94e-142">若要运行该过程，请在对象资源管理器中右键单击存储过程名称 **HumanResources.uspGetEmployeesTest**，然后选择“执行存储过程”。</span><span class="sxs-lookup"><span data-stu-id="ba94e-142">To run the procedure, in Object Explorer, right-click the stored procedure name **HumanResources.uspGetEmployeesTest** and select **Execute Stored Procedure**.</span></span>  
  
12. <span data-ttu-id="ba94e-143">在“执行过程”窗口中，输入 Margheim 作为参数 @LastName 的值，并输入值 Diane 作为参数 @FirstName 的值。</span><span class="sxs-lookup"><span data-stu-id="ba94e-143">In the **Execute Procedure** window, enter Margheim as the value for the parameter @LastName and enter the value Diane as the value for the parameter @FirstName.</span></span>  
  
> [!WARNING]  
>  <span data-ttu-id="ba94e-144">验证所有用户的输入。</span><span class="sxs-lookup"><span data-stu-id="ba94e-144">Validate all user input.</span></span> <span data-ttu-id="ba94e-145">验证前请勿连接用户输入。</span><span class="sxs-lookup"><span data-stu-id="ba94e-145">Do not concatenate user input before you validate it.</span></span> <span data-ttu-id="ba94e-146">绝对不要执行根据尚未验证的用户输入构造的命令。</span><span class="sxs-lookup"><span data-stu-id="ba94e-146">Never execute a command constructed from unvalidated user input.</span></span>  
  
###  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="ba94e-147">使用 Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="ba94e-147">Using Transact-SQL</span></span>  
 <span data-ttu-id="ba94e-148">**在查询编辑器中创建过程**</span><span class="sxs-lookup"><span data-stu-id="ba94e-148">**To create a procedure in Query Editor**</span></span>  
  
1.  <span data-ttu-id="ba94e-149">在 **“对象资源管理器”** 中，连接到 [!INCLUDE[ssDE](../../includes/ssde-md.md)]的实例。</span><span class="sxs-lookup"><span data-stu-id="ba94e-149">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="ba94e-150">从 **“文件”** 菜单中，单击 **“新建查询”** 。</span><span class="sxs-lookup"><span data-stu-id="ba94e-150">From the **File** menu, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="ba94e-151">将以下示例复制并粘贴到查询窗口中，然后单击“执行” 。</span><span class="sxs-lookup"><span data-stu-id="ba94e-151">Copy and paste the following example into the query window and click **Execute**.</span></span> <span data-ttu-id="ba94e-152">该示例将使用其他过程名称创建与上述相同的存储过程。</span><span class="sxs-lookup"><span data-stu-id="ba94e-152">This example creates the same stored procedure as above using a different procedure name.</span></span>  
  
    ```sql
    USE AdventureWorks2012;  
    GO  
    CREATE PROCEDURE HumanResources.uspGetEmployeesTest2   
        @LastName nvarchar(50),   
        @FirstName nvarchar(50)   
    AS
  
        SET NOCOUNT ON;  
        SELECT FirstName, LastName, Department  
        FROM HumanResources.vEmployeeDepartmentHistory  
        WHERE FirstName = @FirstName AND LastName = @LastName  
        AND EndDate IS NULL;  
    GO
    ```  
  
4.  <span data-ttu-id="ba94e-153">若要运行该过程，请将以下示例复制并粘贴到一个新的查询窗口中，然后单击 **“执行”** 。</span><span class="sxs-lookup"><span data-stu-id="ba94e-153">To run the procedure, copy and paste the following example into a new query window and click **Execute**.</span></span> <span data-ttu-id="ba94e-154">请注意，将显示指定参数值的不同方法。</span><span class="sxs-lookup"><span data-stu-id="ba94e-154">Notice that different methods of specifying the parameter values are shown.</span></span>  
  
    ```sql
    EXECUTE HumanResources.uspGetEmployeesTest2 N'Ackerman', N'Pilar';  
    -- Or  
    EXEC HumanResources.uspGetEmployeesTest2 @LastName = N'Ackerman', @FirstName = N'Pilar';  
    GO  
    -- Or  
    EXECUTE HumanResources.uspGetEmployeesTest2 @FirstName = N'Pilar', @LastName = N'Ackerman';  
    GO
    ```  
  
## <a name="see-also"></a><span data-ttu-id="ba94e-155">另请参阅</span><span class="sxs-lookup"><span data-stu-id="ba94e-155">See Also</span></span>  
 [<span data-ttu-id="ba94e-156">CREATE PROCEDURE (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="ba94e-156">CREATE PROCEDURE &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/create-procedure-transact-sql)  
  