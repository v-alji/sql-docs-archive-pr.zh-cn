---
title: 创建表（数据库引擎）| Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: table-view-index
ms.topic: conceptual
helpviewer_keywords:
- table creation [SQL Server], Visual Database Tools
ms.assetid: 6f7c6ac5-e6d3-4dca-831e-b28442ba535b
author: stevestein
ms.author: sstein
ms.openlocfilehash: a8d84a4da6a10fbcbae311fe1bf738c03b85a4c6
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87591829"
---
# <a name="create-tables-database-engine"></a><span data-ttu-id="b6529-102">创建表（数据库引擎）</span><span class="sxs-lookup"><span data-stu-id="b6529-102">Create Tables (Database Engine)</span></span>
  <span data-ttu-id="b6529-103">您可以通过使用 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 或 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 在 [!INCLUDE[tsql](../../includes/tsql-md.md)]中创建新表，对该表进行命名，然后将其添加到现有数据库中。</span><span class="sxs-lookup"><span data-stu-id="b6529-103">You can create a new table, name it, and add it to an existing database in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span>

> [!NOTE]
>  <span data-ttu-id="b6529-104">如果已连接到 SQL Azure 数据库，则新的表选项将启动一个创建表模板脚本。</span><span class="sxs-lookup"><span data-stu-id="b6529-104">If you are connected to a SQL Azure database, the new table option launches a create table template script.</span></span> <span data-ttu-id="b6529-105">编辑相关参数，然后运行此脚本以创建一个新表。</span><span class="sxs-lookup"><span data-stu-id="b6529-105">Edit the parameters, then run the script to create a new table.</span></span> <span data-ttu-id="b6529-106">有关详细信息，请参阅 [SQL Azure 概述](https://microsoft.sharepoint.com/sites/infopedia_g01/pages/cards/azure-sql-database.aspx)。</span><span class="sxs-lookup"><span data-stu-id="b6529-106">For more information, see [SQL Azure Overview](https://microsoft.sharepoint.com/sites/infopedia_g01/pages/cards/azure-sql-database.aspx).</span></span>

 <span data-ttu-id="b6529-107">**本主题内容**</span><span class="sxs-lookup"><span data-stu-id="b6529-107">**In This Topic**</span></span>

-   <span data-ttu-id="b6529-108">**开始之前：**</span><span class="sxs-lookup"><span data-stu-id="b6529-108">**Before you begin:**</span></span>

     [<span data-ttu-id="b6529-109">安全性</span><span class="sxs-lookup"><span data-stu-id="b6529-109">Security</span></span>](#Security)

-   <span data-ttu-id="b6529-110">**若要创建表，请使用：**</span><span class="sxs-lookup"><span data-stu-id="b6529-110">**To create a table, using:**</span></span>

     [<span data-ttu-id="b6529-111">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="b6529-111">SQL Server Management Studio</span></span>](#SSMSProcedure)

     [<span data-ttu-id="b6529-112">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="b6529-112">Transact-SQL</span></span>](#TsqlProcedure)

##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="b6529-113">开始之前</span><span class="sxs-lookup"><span data-stu-id="b6529-113">Before You Begin</span></span>

###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="b6529-114">Security</span><span class="sxs-lookup"><span data-stu-id="b6529-114">Security</span></span>

####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="b6529-115">权限</span><span class="sxs-lookup"><span data-stu-id="b6529-115">Permissions</span></span>
 <span data-ttu-id="b6529-116">需要在数据库中具有 CREATE TABLE 权限，对在其中创建表的架构具有 ALTER 权限。</span><span class="sxs-lookup"><span data-stu-id="b6529-116">Requires CREATE TABLE permission in the database and ALTER permission on the schema in which the table is being created.</span></span>

 <span data-ttu-id="b6529-117">如果 CREATE TABLE 语句中的任何列被定义为 CLR 用户定义类型，则需要具有对此类型的所有权或 REFERENCES 权限。</span><span class="sxs-lookup"><span data-stu-id="b6529-117">If any columns in the CREATE TABLE statement are defined as a CLR user-defined type, either ownership of the type or REFERENCES permission on it is required.</span></span>

 <span data-ttu-id="b6529-118">如果 CREATE TABLE 语句中的任何列具有与其关联的 XML 架构集合，则需要具有对 XML 架构集合的所有权或 REFERENCES 权限。</span><span class="sxs-lookup"><span data-stu-id="b6529-118">If any columns in the CREATE TABLE statement have an XML schema collection associated with them, either ownership of the XML schema collection or REFERENCES permission on it is required.</span></span>

##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="b6529-119">使用 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="b6529-119">Using SQL Server Management Studio</span></span>

#### <a name="to-create-a-table-with-table-designer"></a><span data-ttu-id="b6529-120">使用表设计器创建表</span><span class="sxs-lookup"><span data-stu-id="b6529-120">To create a table with Table Designer</span></span>

1.  <span data-ttu-id="b6529-121">在 **“对象资源管理器”** 中，连接到包含要修改的数据库的 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 实例。</span><span class="sxs-lookup"><span data-stu-id="b6529-121">In **Object Explorer**, connect to the instance of [!INCLUDE[ssDE](../../includes/ssde-md.md)] that contains the database to be modified.</span></span>

2.  <span data-ttu-id="b6529-122">在 **“对象资源管理器”** 中，展开 **“数据库”** 节点，然后展开将包含新表的数据库。</span><span class="sxs-lookup"><span data-stu-id="b6529-122">In **Object Explorer**, expand the **Databases** node and then expand the database that will contain the new table.</span></span>

3.  <span data-ttu-id="b6529-123">在对象资源管理器中，右键单击数据库的“表”节点，然后单击“新建表”\*\*\*\*\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="b6529-123">In Object Explorer, right-click the **Tables** node of your database and then click **New Table**.</span></span>

4.  <span data-ttu-id="b6529-124">键入列名，选择数据类型，并选择各个列是否允许空值，如下图所示。</span><span class="sxs-lookup"><span data-stu-id="b6529-124">Type column names, choose data types, and choose whether to allow nulls for each column as shown in the following illustration.</span></span>

     <span data-ttu-id="b6529-125">![AddColumnsinTableDesigner](../../database-engine/media/addcolumnsintabledesigner.gif "AddColumnsinTableDesigner")</span><span class="sxs-lookup"><span data-stu-id="b6529-125">![AddColumnsinTableDesigner](../../database-engine/media/addcolumnsintabledesigner.gif "AddColumnsinTableDesigner")</span></span>

5.  <span data-ttu-id="b6529-126">若要为某个列指定更多属性，例如标识或计算列值，请单击该列，然后在列属性选项卡中，选择适当的属性。</span><span class="sxs-lookup"><span data-stu-id="b6529-126">To specify more properties for a column, such as identity or computed column values, click the column and in the column properties tab, choose the appropriate properties.</span></span> <span data-ttu-id="b6529-127">有关列属性的详细信息，请参阅[表列属性 (SQL Server Management Studio)](table-column-properties-sql-server-management-studio.md)。</span><span class="sxs-lookup"><span data-stu-id="b6529-127">For more information about column properties, see [Table Column Properties &#40;SQL Server Management Studio&#41;](table-column-properties-sql-server-management-studio.md).</span></span>

6.  <span data-ttu-id="b6529-128">若要将某个列指定为主键，请右键单击该列，然后选择“设置主键”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="b6529-128">To specify a column as a primary key, right-click the column and select **Set Primary Key**.</span></span> <span data-ttu-id="b6529-129">有关详细信息，请参阅 [Create Primary Keys](../tables/create-primary-keys.md)。</span><span class="sxs-lookup"><span data-stu-id="b6529-129">For more information, see [Create Primary Keys](../tables/create-primary-keys.md).</span></span>

7.  <span data-ttu-id="b6529-130">若要创建外键关系、CHECK 约束或索引，请在“表设计器”窗格中右键单击，然后从列表中选择一个对象，如下图中所示。</span><span class="sxs-lookup"><span data-stu-id="b6529-130">To create foreign key relationships, check constraints, or indexes, right-click in the Table Designer pane and select an object from the list as shown in the following illustration.</span></span>

     <span data-ttu-id="b6529-131">![AddTableObjects](../../database-engine/media/addtableobjects.gif "AddTableObjects")</span><span class="sxs-lookup"><span data-stu-id="b6529-131">![AddTableObjects](../../database-engine/media/addtableobjects.gif "AddTableObjects")</span></span>

     <span data-ttu-id="b6529-132">有关这些对象的详细信息，请参阅 [Create Foreign Key Relationships](../tables/create-foreign-key-relationships.md)、 [Create Check Constraints](../tables/create-check-constraints.md) 和 [Indexes](../indexes/indexes.md)。</span><span class="sxs-lookup"><span data-stu-id="b6529-132">For more information about these objects, see [Create Foreign Key Relationships](../tables/create-foreign-key-relationships.md), [Create Check Constraints](../tables/create-check-constraints.md) and [Indexes](../indexes/indexes.md).</span></span>

8.  <span data-ttu-id="b6529-133">默认情况下，该表包含在 **dbo** 架构中。</span><span class="sxs-lookup"><span data-stu-id="b6529-133">By default, the table is contained in the **dbo** schema.</span></span> <span data-ttu-id="b6529-134">若要为该表指定不同架构，请在“表设计器”窗格中右键单击，然后选择“属性”\*\*\*\*，如下图中所示。</span><span class="sxs-lookup"><span data-stu-id="b6529-134">To specify a different schema for the table, right-click in the Table Designer pane and select **Properties** as shown in the following illustration.</span></span> <span data-ttu-id="b6529-135">从“架构”\*\*\*\* 下拉列表中选择适当的架构。</span><span class="sxs-lookup"><span data-stu-id="b6529-135">From the **Schema** drop-down list, select the appropriate schema.</span></span>

     <span data-ttu-id="b6529-136">![Specifyatableschema](../../database-engine/media/specifyatableschema.gif "Specifyatableschema")</span><span class="sxs-lookup"><span data-stu-id="b6529-136">![Specifyatableschema](../../database-engine/media/specifyatableschema.gif "Specifyatableschema")</span></span>

     <span data-ttu-id="b6529-137">有关架构的详细信息，请参阅 [Create a Database Schema](../security/authentication-access/create-a-database-schema.md)。</span><span class="sxs-lookup"><span data-stu-id="b6529-137">For more information about schemas, see [Create a Database Schema](../security/authentication-access/create-a-database-schema.md).</span></span>

9. <span data-ttu-id="b6529-138">从“文件”菜单中，选择“保存”表名称\*\*\*\*\*\*\*\* \*\*。</span><span class="sxs-lookup"><span data-stu-id="b6529-138">From the **File** menu, choose **Save** *table name*.</span></span>

10. <span data-ttu-id="b6529-139">在 **“选择名称”** 对话框中，为该表键入一个名称，再单击 **“确定”**。</span><span class="sxs-lookup"><span data-stu-id="b6529-139">In the **Choose Name** dialog box, type a name for the table and click **OK**.</span></span>

11. <span data-ttu-id="b6529-140">若要查看这个新表，请在 **“对象资源管理器”** 中展开 **“表”** 节点，然后按 **F5** 刷新对象列表。</span><span class="sxs-lookup"><span data-stu-id="b6529-140">To view the new table, in **Object Explorer**, expand the **Tables** node and press **F5** to refresh the list of objects.</span></span> <span data-ttu-id="b6529-141">该新表将显示在表列表中。</span><span class="sxs-lookup"><span data-stu-id="b6529-141">The new table is displayed in the list of tables.</span></span>

##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="b6529-142">使用 Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="b6529-142">Using Transact-SQL</span></span>

#### <a name="to-create-a-table-in-the-query-editor"></a><span data-ttu-id="b6529-143">在查询编辑器中创建表</span><span class="sxs-lookup"><span data-stu-id="b6529-143">To create a table in the Query Editor</span></span>

1.  <span data-ttu-id="b6529-144">在 **“对象资源管理器”** 中，连接到 [!INCLUDE[ssDE](../../includes/ssde-md.md)]的实例。</span><span class="sxs-lookup"><span data-stu-id="b6529-144">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>

2.  <span data-ttu-id="b6529-145">在标准菜单栏上，单击 **“新建查询”** 。</span><span class="sxs-lookup"><span data-stu-id="b6529-145">On the Standard bar, click **New Query**.</span></span>

3.  <span data-ttu-id="b6529-146">将以下示例复制并粘贴到查询窗口中，然后单击“执行” 。</span><span class="sxs-lookup"><span data-stu-id="b6529-146">Copy and paste the following example into the query window and click **Execute**.</span></span>

    ```
    CREATE TABLE dbo.PurchaseOrderDetail
    (
        PurchaseOrderID int NOT NULL
        ,LineNumber smallint NOT NULL
        ,ProductID int NULL
        ,UnitPrice money NULL
        ,OrderQty smallint NULL
        ,ReceivedQty float NULL
        ,RejectedQty float NULL
        ,DueDate datetime NULL
    );
    ```

 <span data-ttu-id="b6529-147">有关详细信息，请参阅 [CREATE TABLE (Transact-SQL)](/sql/t-sql/statements/create-table-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="b6529-147">For more examples, see [CREATE TABLE &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-table-transact-sql).</span></span>


