---
title: MSSQLSERVER_4104 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 4104 (Database Engine error)
ms.assetid: 52dc32d8-97ad-4ef0-834d-2e68f215d007
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: cbbc28a3e15af6fdc8fd44633ccbdfc46e49149d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87589130"
---
# <a name="mssqlserver_4104"></a><span data-ttu-id="8061a-102">MSSQLSERVER_4104</span><span class="sxs-lookup"><span data-stu-id="8061a-102">MSSQLSERVER_4104</span></span>
    
## <a name="details"></a><span data-ttu-id="8061a-103">详细信息</span><span class="sxs-lookup"><span data-stu-id="8061a-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="8061a-104">产品名称</span><span class="sxs-lookup"><span data-stu-id="8061a-104">Product Name</span></span>|<span data-ttu-id="8061a-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="8061a-105">SQL Server</span></span>|  
|<span data-ttu-id="8061a-106">事件 ID</span><span class="sxs-lookup"><span data-stu-id="8061a-106">Event ID</span></span>|<span data-ttu-id="8061a-107">4104</span><span class="sxs-lookup"><span data-stu-id="8061a-107">4104</span></span>|  
|<span data-ttu-id="8061a-108">事件源</span><span class="sxs-lookup"><span data-stu-id="8061a-108">Event Source</span></span>|<span data-ttu-id="8061a-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="8061a-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="8061a-110">组件</span><span class="sxs-lookup"><span data-stu-id="8061a-110">Component</span></span>|<span data-ttu-id="8061a-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="8061a-111">SQLEngine</span></span>|  
|<span data-ttu-id="8061a-112">符号名称</span><span class="sxs-lookup"><span data-stu-id="8061a-112">Symbolic Name</span></span>|<span data-ttu-id="8061a-113">ALG_MULTI_ID_BAD</span><span class="sxs-lookup"><span data-stu-id="8061a-113">ALG_MULTI_ID_BAD</span></span>|  
|<span data-ttu-id="8061a-114">消息正文</span><span class="sxs-lookup"><span data-stu-id="8061a-114">Message Text</span></span>|<span data-ttu-id="8061a-115">无法绑定由多个部分组成的标识符 "%.\*ls"。</span><span class="sxs-lookup"><span data-stu-id="8061a-115">The multi-part identifier "%.\*ls" could not be bound.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="8061a-116">说明</span><span class="sxs-lookup"><span data-stu-id="8061a-116">Explanation</span></span>  
 <span data-ttu-id="8061a-117">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 中实体的名称称为其“标识符”。</span><span class="sxs-lookup"><span data-stu-id="8061a-117">The name of an entity in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] is referred to as its *identifier*.</span></span> <span data-ttu-id="8061a-118">在引用实体（例如在查询中指定列名和表名）时可以使用标识符。</span><span class="sxs-lookup"><span data-stu-id="8061a-118">You use identifiers whenever you reference entities, for example, by specifying column and table names in a query.</span></span> <span data-ttu-id="8061a-119">由多个部分组成的标识符包含一个或多个作为标识符前缀的限定符。</span><span class="sxs-lookup"><span data-stu-id="8061a-119">A multi-part identifier contains one or more qualifiers as a prefix for the identifier.</span></span> <span data-ttu-id="8061a-120">例如，表标识符可能以诸如包含表的数据库和架构的名称之类的限定符作为前缀，而列标识符可能以诸如表名称或表别名之类的限定符作为前缀。</span><span class="sxs-lookup"><span data-stu-id="8061a-120">For example, a table identifier may be prefixed with qualifiers such as the database name and schema name in which the table is contained, or a column identifier may be prefixed with qualifiers such as a table name or table alias.</span></span>  
  
 <span data-ttu-id="8061a-121">错误 4104 表示无法将指定的由多个部分组成的标识符映射到现有实体。</span><span class="sxs-lookup"><span data-stu-id="8061a-121">Error 4104 indicates that the specified multi-part identifier could not be mapped to an existing entity.</span></span> <span data-ttu-id="8061a-122">在以下情况下可能会返回此错误：</span><span class="sxs-lookup"><span data-stu-id="8061a-122">This error can be returned under the following conditions:</span></span>  
  
-   <span data-ttu-id="8061a-123">作为列名称前缀提供的限定符与查询中使用的任何表名或别名均不对应。</span><span class="sxs-lookup"><span data-stu-id="8061a-123">The qualifier supplied as a prefix for a column name does not correspond to any table or alias name used in the query.</span></span>  
  
     <span data-ttu-id="8061a-124">例如，下面的语句使用表别名 (`Dept`) 作为列前缀，但是此表别名未在 FROM 子句中引用。</span><span class="sxs-lookup"><span data-stu-id="8061a-124">For example, the following statement uses a table alias (`Dept`) as a column prefix, but the table alias is not referenced in the FROM clause.</span></span>  
  
    ```  
    SELECT Dept.Name FROM HumanResources.Department;  
    ```  
  
     <span data-ttu-id="8061a-125">在下面的语句中，在属于两个表之间的 JOIN 条件的 WHERE 子句中指定了由多个部分组成的列标识符 `TableB.KeyCol`，但是 `TableB` 未在查询中显式引用。</span><span class="sxs-lookup"><span data-stu-id="8061a-125">In the following statements, a multi-part column identifier `TableB.KeyCol` is specified in the WHERE clause as part of a JOIN condition between two tables, however, `TableB` is not explicitly referenced in the query.</span></span>  
  
    ```  
    DELETE FROM TableA WHERE TableA.KeyCol = TableB.KeyCol;  
    ```  
  
    ```  
    SELECT 'X' FROM TableA WHERE TableB.KeyCol = TableA.KeyCol;  
    ```  
  
-   <span data-ttu-id="8061a-126">在 FROM 子句中提供了表的别名，但为列提供的相应限定符却是表名称。</span><span class="sxs-lookup"><span data-stu-id="8061a-126">An alias name for the table is supplied in the FROM clause, but the qualifier supplied for a column is the table name.</span></span> <span data-ttu-id="8061a-127">例如，下面的语句使用表名称 `Department` 作为列前缀，但是，在 FROM 子句中引用的是表别名 (`Dept`)。</span><span class="sxs-lookup"><span data-stu-id="8061a-127">For example, the following statement uses the table name `Department` as the column prefix; however, the table has an alias (`Dept`) referenced in the FROM clause.</span></span>  
  
    ```  
    SELECT Department.Name FROM HumanResources.Department AS Dept;  
    ```  
  
     <span data-ttu-id="8061a-128">使用别名时，不能在语句中的其他地方使用表名称。</span><span class="sxs-lookup"><span data-stu-id="8061a-128">When an alias is used, the table name cannot be used elsewhere in the statement.</span></span>  
  
-   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="8061a-129">无法确定由多个部分组成的标识符是指由表作为前缀的列，还是指由列作为前缀的 CLR 用户定义数据类型 (UDT) 的属性。</span><span class="sxs-lookup"><span data-stu-id="8061a-129">is unable to determine if the multi-part identifier refers to a column prefixed by a table or to a property of a CLR user-defined data type (UDT) prefixed by a column.</span></span> <span data-ttu-id="8061a-130">出现这种情况的原因是：UDT 列的属性是通过在列名称和属性名称之间使用句号分隔符 (.) 引用的，而这与用表名称作为列名称前缀的方式相同。</span><span class="sxs-lookup"><span data-stu-id="8061a-130">This happens because properties of UDT columns are referenced by using the period separator (.) between the column name and the property name in the same way that a column name is prefixed with a table name.</span></span> <span data-ttu-id="8061a-131">以下示例创建两个表：`a` 和 `b`。</span><span class="sxs-lookup"><span data-stu-id="8061a-131">The following example creates two tables, `a` and `b`.</span></span> <span data-ttu-id="8061a-132">表 `b` 包含列 `a`，此列使用 CLR UDT `dbo.myudt2` 作为其数据类型。</span><span class="sxs-lookup"><span data-stu-id="8061a-132">Table `b` contains column `a`, which uses a CLR UDT `dbo.myudt2` as its data type.</span></span> <span data-ttu-id="8061a-133">SELECT 语句包含由多个部分组成的标识符 `a.c2`。</span><span class="sxs-lookup"><span data-stu-id="8061a-133">The SELECT statement contains a multi-part identifier `a.c2`.</span></span>  
  
    ```  
    CREATE TABLE a (c2 int);   
    GO  
    ```  
  
    ```  
    CREATE TABLE b (a dbo.myudt2);   
    GO  
    ```  
  
    ```  
    SELECT a.c2 FROM a, b;   
    ```  
  
     <span data-ttu-id="8061a-134">假定 UDT `myudt2` 不具有名为 `c2` 的属性，则 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 将无法确定标识符 `a.c2` 是指表 `a` 中的列 `c2`，还是指表 `b` 中的列 `a`、属性 `c2`。</span><span class="sxs-lookup"><span data-stu-id="8061a-134">Assuming that the UDT `myudt2` does not have a property named `c2`, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] cannot determine whether identifier `a.c2`refers to column `c2` in table `a` or to the column `a`, property `c2` in table `b`.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="8061a-135">用户操作</span><span class="sxs-lookup"><span data-stu-id="8061a-135">User Action</span></span>  
  
-   <span data-ttu-id="8061a-136">使列前缀与在查询的 FROM 子句中指定的表名或别名相匹配。</span><span class="sxs-lookup"><span data-stu-id="8061a-136">Match the column prefixes against the table names or alias names specified in the FROM clause of the query.</span></span> <span data-ttu-id="8061a-137">如果在 FROM 子句中为表名称定义了别名，则只能将此别名用作与该表关联的列的限定符。</span><span class="sxs-lookup"><span data-stu-id="8061a-137">If an alias is defined for a table name in the FROM clause, you can only use the alias as a qualifier for columns associated with that table.</span></span>  
  
     <span data-ttu-id="8061a-138">上面引用 `HumanResources.Department` 表的语句可以进行如下更正：</span><span class="sxs-lookup"><span data-stu-id="8061a-138">The statements above that reference the `HumanResources.Department` table can be corrected as follows:</span></span>  
  
    ```  
    SELECT Dept.Name FROM HumanResources.Department AS Dept;  
    GO  
    ```  
  
    ```  
    SELECT Department.Name FROM HumanResources.Department;  
    GO  
    ```  
  
-   <span data-ttu-id="8061a-139">确保在查询中指定所有表，并确保正确地指定表之间的 JOIN 条件。</span><span class="sxs-lookup"><span data-stu-id="8061a-139">Ensure that all tables are specified in the query and that the JOIN conditions between tables are specified correctly.</span></span> <span data-ttu-id="8061a-140">上面的 DELETE 语句可以进行如下更正：</span><span class="sxs-lookup"><span data-stu-id="8061a-140">The DELETE statement above can be corrected as follows:</span></span>  
  
    ```  
    DELETE FROM dbo.TableA  
    WHERE TableA.KeyCol = (SELECT TableB.KeyCol   
                            FROM TableB   
                            WHERE TableA.KeyCol = TableB.KeyCol);  
    GO  
    ```  
  
     <span data-ttu-id="8061a-141">上面 `TableA` 的 SELECT 语句可以进行如下更正：</span><span class="sxs-lookup"><span data-stu-id="8061a-141">The SELECT statement above for `TableA` can be corrected as follows:</span></span>  
  
    ```  
    SELECT 'X' FROM TableA, TableB WHERE TableB.KeyCol = TableA.KeyCol;  
    ```  
  
     <span data-ttu-id="8061a-142">或</span><span class="sxs-lookup"><span data-stu-id="8061a-142">or</span></span>  
  
    ```  
    SELECT 'X' FROM TableA INNER JOIN TableB ON TableB.KeyCol = TableA.KeyCol;  
    ```  
  
-   <span data-ttu-id="8061a-143">为标识符使用明确定义的唯一名称。</span><span class="sxs-lookup"><span data-stu-id="8061a-143">Use unique, clearly defined names for identifiers.</span></span> <span data-ttu-id="8061a-144">这样做可以使您的代码更易于理解和维护，并可以将不明确引用多个实体的风险降至最低。</span><span class="sxs-lookup"><span data-stu-id="8061a-144">Doing so makes your code easier to read and maintain, and it also minimizes the risk of ambiguous references to multiple entities.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8061a-145">另请参阅</span><span class="sxs-lookup"><span data-stu-id="8061a-145">See Also</span></span>  
 <span data-ttu-id="8061a-146">[MSSQLSERVER_107](mssqlserver-107-database-engine-error.md) </span><span class="sxs-lookup"><span data-stu-id="8061a-146">[MSSQLSERVER_107](mssqlserver-107-database-engine-error.md) </span></span>  
 [<span data-ttu-id="8061a-147">数据库标识符</span><span class="sxs-lookup"><span data-stu-id="8061a-147">Database Identifiers</span></span>](../databases/database-identifiers.md)  
  
  
