---
title: 查看用户定义函数 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
f1_keywords:
- sql12.swb.udfproperties.general.f1
- sql12.swb.functionproperties.general.f1
helpviewer_keywords:
- displaying user-defined functions
- viewing user-defined functions
- user-defined functions [SQL Server], viewing
- status information [SQL Server], user-defined functions
ms.assetid: a45dfab5-6384-4311-b935-2e23a70c5c10
author: rothja
ms.author: jroth
ms.openlocfilehash: 5248f75540b72b489a7605b2cca34144dfcfedbf
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87576583"
---
# <a name="view-user-defined-functions"></a><span data-ttu-id="95788-102">查看用户定义函数</span><span class="sxs-lookup"><span data-stu-id="95788-102">View User-defined Functions</span></span>
  <span data-ttu-id="95788-103">在 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 中，通过使用 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 或 [!INCLUDE[tsql](../../includes/tsql-md.md)]可以获取有关用户定义函数的定义或属性的信息。</span><span class="sxs-lookup"><span data-stu-id="95788-103">You can gain information about the definition or properties of a user-defined function in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span> <span data-ttu-id="95788-104">您可能需要查看函数的定义，以理解其数据从源表中派生的方式或查看函数所定义的数据。</span><span class="sxs-lookup"><span data-stu-id="95788-104">You may need to see the definition of the function to understand how its data is derived from the source tables or to see the data defined by the function.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="95788-105">如果您更改函数所引用的对象的名称，则必须修改函数，使其文本反映新名称。</span><span class="sxs-lookup"><span data-stu-id="95788-105">If you change the name of an object referenced by a function, you must modify that function so that its text reflects the new name.</span></span> <span data-ttu-id="95788-106">因此，在重命名对象前，首先显示该对象的依赖关系，以确定所建议的更改是否影响任何函数。</span><span class="sxs-lookup"><span data-stu-id="95788-106">Therefore, before renaming an object, display the dependencies of the object first to determine if any functions are affected by the proposed change.</span></span>  
  
 <span data-ttu-id="95788-107">**本主题内容**</span><span class="sxs-lookup"><span data-stu-id="95788-107">**In This Topic**</span></span>  
  
-   <span data-ttu-id="95788-108">**开始之前：**</span><span class="sxs-lookup"><span data-stu-id="95788-108">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="95788-109">安全性</span><span class="sxs-lookup"><span data-stu-id="95788-109">Security</span></span>](#Security)  
  
-   <span data-ttu-id="95788-110">**若要获取有关函数的信息，请使用：**</span><span class="sxs-lookup"><span data-stu-id="95788-110">**To get information about a function, using:**</span></span>  
  
     [<span data-ttu-id="95788-111">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="95788-111">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="95788-112">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="95788-112">Transact-SQL</span></span>](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="95788-113">开始之前</span><span class="sxs-lookup"><span data-stu-id="95788-113">Before You Begin</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="95788-114">Security</span><span class="sxs-lookup"><span data-stu-id="95788-114">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="95788-115">权限</span><span class="sxs-lookup"><span data-stu-id="95788-115">Permissions</span></span>  
 <span data-ttu-id="95788-116">使用 **sys.sql_expression_dependencies** 查找函数的依赖关系要求对该数据库具有 VIEW DEFINITION 权限，以及对数据库具有 **sys.sql_expression_dependencies** 的 SELECT 权限。</span><span class="sxs-lookup"><span data-stu-id="95788-116">Using **sys.sql_expression_dependencies** to find all the dependencies on a function requires VIEW DEFINITION permission on the database and SELECT permission on **sys.sql_expression_dependencies** for the database.</span></span> <span data-ttu-id="95788-117">系统对象定义（如 OBJECT_DEFINITION 中返回的对象定义）是公开可见的。</span><span class="sxs-lookup"><span data-stu-id="95788-117">System object definitions, like the ones returned in OBJECT_DEFINITION, are publicly visible.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="95788-118">使用 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="95788-118">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-show-a-user-defined-functions-properties"></a><span data-ttu-id="95788-119">显示用户定义函数的属性</span><span class="sxs-lookup"><span data-stu-id="95788-119">To show a user-defined function's properties</span></span>  
  
1.  <span data-ttu-id="95788-120">在 **“对象资源管理器”** 中，单击包含要查看属性的函数的数据库旁边的加号，然后单击加号以展开 **“可编程性”** 文件夹。</span><span class="sxs-lookup"><span data-stu-id="95788-120">In **Object Explorer**, click the plus sign next to the database that contains the function to which you want to view the properties, and then click the plus sign to expand the **Programmability** folder.</span></span>  
  
2.  <span data-ttu-id="95788-121">单击加号以便展开 **“函数”** 文件夹。</span><span class="sxs-lookup"><span data-stu-id="95788-121">Click the plus sign to expand the **Functions** folder.</span></span>  
  
3.  <span data-ttu-id="95788-122">单击加号以展开包含您要查看属性的函数的文件夹：</span><span class="sxs-lookup"><span data-stu-id="95788-122">Click the plus sign to expand the folder that contains the function to which you want to view the properties:</span></span>  
  
    -   <span data-ttu-id="95788-123">Table-valued Function</span><span class="sxs-lookup"><span data-stu-id="95788-123">Table-valued Function</span></span>  
  
    -   <span data-ttu-id="95788-124">标量值函数</span><span class="sxs-lookup"><span data-stu-id="95788-124">Scalar-valued Function</span></span>  
  
    -   <span data-ttu-id="95788-125">Aggregate 函数</span><span class="sxs-lookup"><span data-stu-id="95788-125">Aggregate Function</span></span>  
  
4.  <span data-ttu-id="95788-126">右键单击要查看其属性的函数，然后选择“属性”  。</span><span class="sxs-lookup"><span data-stu-id="95788-126">Right-click the function of which you want to view the properties and select **Properties**.</span></span>  
  
     <span data-ttu-id="95788-127">“函数属性 - function_name”对话框中将显示以下属性   。</span><span class="sxs-lookup"><span data-stu-id="95788-127">The following properties appear in the **Function Properties -** _function_name_ dialog box.</span></span>  
  
     <span data-ttu-id="95788-128">**Database**</span><span class="sxs-lookup"><span data-stu-id="95788-128">**Database**</span></span>  
     <span data-ttu-id="95788-129">包含此函数的数据库的名称。</span><span class="sxs-lookup"><span data-stu-id="95788-129">The name of the database containing this function.</span></span>  
  
     <span data-ttu-id="95788-130">**Server**</span><span class="sxs-lookup"><span data-stu-id="95788-130">**Server**</span></span>  
     <span data-ttu-id="95788-131">当前服务器实例的名称。</span><span class="sxs-lookup"><span data-stu-id="95788-131">The name of the current server instance.</span></span>  
  
     <span data-ttu-id="95788-132">**用户**</span><span class="sxs-lookup"><span data-stu-id="95788-132">**User**</span></span>  
     <span data-ttu-id="95788-133">此连接的用户名。</span><span class="sxs-lookup"><span data-stu-id="95788-133">The name of the user of this connection.</span></span>  
  
     <span data-ttu-id="95788-134">**创建日期**</span><span class="sxs-lookup"><span data-stu-id="95788-134">**Created date**</span></span>  
     <span data-ttu-id="95788-135">显示函数的创建日期。</span><span class="sxs-lookup"><span data-stu-id="95788-135">Displays the date the function was created.</span></span>  
  
     <span data-ttu-id="95788-136">**执行身份**</span><span class="sxs-lookup"><span data-stu-id="95788-136">**Execute As**</span></span>  
     <span data-ttu-id="95788-137">执行该函数的上下文。</span><span class="sxs-lookup"><span data-stu-id="95788-137">Execution context for the function.</span></span>  
  
     <span data-ttu-id="95788-138">**名称**</span><span class="sxs-lookup"><span data-stu-id="95788-138">**Name**</span></span>  
     <span data-ttu-id="95788-139">当前函数的名称。</span><span class="sxs-lookup"><span data-stu-id="95788-139">The name of the current function.</span></span>  
  
     <span data-ttu-id="95788-140">**架构**</span><span class="sxs-lookup"><span data-stu-id="95788-140">**Schema**</span></span>  
     <span data-ttu-id="95788-141">显示函数所属的架构。</span><span class="sxs-lookup"><span data-stu-id="95788-141">Displays the schema that owns the function.</span></span>  
  
     <span data-ttu-id="95788-142">**系统对象**</span><span class="sxs-lookup"><span data-stu-id="95788-142">**System object**</span></span>  
     <span data-ttu-id="95788-143">指示该函数是否为系统对象。</span><span class="sxs-lookup"><span data-stu-id="95788-143">Indicates whether the function is a system object.</span></span> <span data-ttu-id="95788-144">值为 True 和 False。</span><span class="sxs-lookup"><span data-stu-id="95788-144">Values are True and False.</span></span>  
  
     <span data-ttu-id="95788-145">**ANSI NULLs**</span><span class="sxs-lookup"><span data-stu-id="95788-145">**ANSI NULLs**</span></span>  
     <span data-ttu-id="95788-146">指示创建对象时是否选择了 ANSI NULLs 选项。</span><span class="sxs-lookup"><span data-stu-id="95788-146">Indicates if the object was created with the ANSI NULLs option.</span></span>  
  
     <span data-ttu-id="95788-147">**已加密**</span><span class="sxs-lookup"><span data-stu-id="95788-147">**Encrypted**</span></span>  
     <span data-ttu-id="95788-148">指示该函数是否已加密。</span><span class="sxs-lookup"><span data-stu-id="95788-148">Indicates whether the function is encrypted.</span></span> <span data-ttu-id="95788-149">值为 True 和 False。</span><span class="sxs-lookup"><span data-stu-id="95788-149">Values are True and False.</span></span>  
  
     <span data-ttu-id="95788-150">**函数类型**</span><span class="sxs-lookup"><span data-stu-id="95788-150">**Function Type**</span></span>  
     <span data-ttu-id="95788-151">用户定义函数的类型。</span><span class="sxs-lookup"><span data-stu-id="95788-151">The type of user defined function.</span></span>  
  
     <span data-ttu-id="95788-152">**带引号的标识符**</span><span class="sxs-lookup"><span data-stu-id="95788-152">**Quoted identifier**</span></span>  
     <span data-ttu-id="95788-153">指示创建对象时是否选择了“带引号的标识符”选项。</span><span class="sxs-lookup"><span data-stu-id="95788-153">Indicates if the object was created with the quoted identifier option.</span></span>  
  
     <span data-ttu-id="95788-154">**架构已绑定**</span><span class="sxs-lookup"><span data-stu-id="95788-154">**Schema bound**</span></span>  
     <span data-ttu-id="95788-155">指示该函数是否已绑定到架构。</span><span class="sxs-lookup"><span data-stu-id="95788-155">Indicates whether the function is schema-bound.</span></span> <span data-ttu-id="95788-156">值为 True 和 False。</span><span class="sxs-lookup"><span data-stu-id="95788-156">Values are True and False.</span></span> <span data-ttu-id="95788-157">有关绑定到架构的函数的信息，请参阅 [CREATE FUNCTION (Transact-SQL)](/sql/t-sql/statements/create-function-transact-sql) 的 SCHEMABINDING 部分。</span><span class="sxs-lookup"><span data-stu-id="95788-157">For information about schema-bound functions, see the SCHEMABINDING section of [CREATE FUNCTION &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-function-transact-sql).</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="95788-158">使用 Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="95788-158">Using Transact-SQL</span></span>  
  
#### <a name="to-get-the-definition-and-properties-of-a-function"></a><span data-ttu-id="95788-159">获取函数的定义和属性</span><span class="sxs-lookup"><span data-stu-id="95788-159">To get the definition and properties of a function</span></span>  
  
1.  <span data-ttu-id="95788-160">在 **“对象资源管理器”** 中，连接到 [!INCLUDE[ssDE](../../../includes/ssde-md.md)]的实例。</span><span class="sxs-lookup"><span data-stu-id="95788-160">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="95788-161">在标准菜单栏上，单击 **“新建查询”** 。</span><span class="sxs-lookup"><span data-stu-id="95788-161">On the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="95788-162">将以下示例之一复制并粘贴到查询窗口中，然后单击 **“执行”** 。</span><span class="sxs-lookup"><span data-stu-id="95788-162">Copy and paste one of the following examples into the query window and click **Execute**.</span></span>  
  
    ```  
    USE AdventureWorks2012;  
    GO  
    -- Get the function name, definition, and relevant properties  
    SELECT sm.object_id,   
       OBJECT_NAME(sm.object_id) AS object_name,   
       o.type,   
       o.type_desc,   
       sm.definition,  
       sm.uses_ansi_nulls,  
       sm.uses_quoted_identifier,  
       sm.is_schema_bound,  
       sm.execute_as_principal_id  
    -- using the two system tables sys.sql_modules and sys.objects  
    FROM sys.sql_modules AS sm  
    JOIN sys.objects AS o ON sm.object_id = o.object_id  
    -- from the function 'dbo.ufnGetProductDealerPrice'  
    WHERE sm.object_id = OBJECT_ID('dbo.ufnGetProductDealerPrice')  
    ORDER BY o.type;  
    GO  
  
    ```  
  
    ```  
    USE AdventureWorks2012;  
    GO  
    -- Get the definition of the function dbo.ufnGetProductDealerPrice  
    SELECT OBJECT_DEFINITION (OBJECT_ID('dbo.ufnGetProductDealerPrice')) AS ObjectDefinition;  
    GO  
    ```  
  
 <span data-ttu-id="95788-163">有关详细信息，请参阅 [sys.sql_modules (Transact-SQL)](/sql/relational-databases/system-catalog-views/sys-sql-modules-transact-sql) 和 [OBJECT_DEFINITION (Transact-SQL)](/sql/t-sql/functions/object-definition-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="95788-163">For more information, see [sys.sql_modules &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-sql-modules-transact-sql) and [OBJECT_DEFINITION &#40;Transact-SQL&#41;](/sql/t-sql/functions/object-definition-transact-sql).</span></span>  
  
#### <a name="to-get-the-dependencies-of-a-function"></a><span data-ttu-id="95788-164">获取函数的依赖关系</span><span class="sxs-lookup"><span data-stu-id="95788-164">To get the dependencies of a function</span></span>  
  
1.  <span data-ttu-id="95788-165">在 **“对象资源管理器”** 中，连接到 [!INCLUDE[ssDE](../../../includes/ssde-md.md)]的实例。</span><span class="sxs-lookup"><span data-stu-id="95788-165">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="95788-166">在标准菜单栏上，单击 **“新建查询”** 。</span><span class="sxs-lookup"><span data-stu-id="95788-166">On the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="95788-167">将以下示例复制并粘贴到查询窗口中，然后单击“执行”  。</span><span class="sxs-lookup"><span data-stu-id="95788-167">Copy and paste the following example into the query window and click **Execute**.</span></span>  
  
    ```  
    USE AdventureWorks2012;  
    GO  
    -- Get all of the dependency information  
    SELECT OBJECT_NAME(sed.referencing_id) AS referencing_entity_name,   
        o.type_desc AS referencing_desciption,   
        COALESCE(COL_NAME(sed.referencing_id, sed.referencing_minor_id), '(n/a)') AS referencing_minor_id,   
        sed.referencing_class_desc, sed.referenced_class_desc,  
        sed.referenced_server_name, sed.referenced_database_name, sed.referenced_schema_name,  
        sed.referenced_entity_name,   
        COALESCE(COL_NAME(sed.referenced_id, sed.referenced_minor_id), '(n/a)') AS referenced_column_name,  
        sed.is_caller_dependent, sed.is_ambiguous  
    -- from the two system tables sys.sql_expression_dependencies and sys.object  
    FROM sys.sql_expression_dependencies AS sed  
    INNER JOIN sys.objects AS o ON sed.referencing_id = o.object_id  
    -- on the function dbo.ufnGetProductDealerPrice  
    WHERE sed.referencing_id = OBJECT_ID('dbo.ufnGetProductDealerPrice');  
    GO  
    ```  
  
 <span data-ttu-id="95788-168">有关详细信息，请参阅 [sys.sql_expression_dependencies (Transact-SQL)](/sql/relational-databases/system-catalog-views/sys-sql-expression-dependencies-transact-sql) 和 [sys.objects (Transact-SQL)](/sql/relational-databases/system-catalog-views/sys-objects-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="95788-168">For more information, see [sys.sql_expression_dependencies &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-sql-expression-dependencies-transact-sql) and [sys.objects &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-objects-transact-sql).</span></span>  
  
  
