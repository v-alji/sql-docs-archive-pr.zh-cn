---
title: 指定 Oracle 发布服务器的数据类型映射 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- Oracle publishing [SQL Server replication], data type mapping
- data types [SQL Server replication], Oracle publishing
- mapping data types [SQL Server replication]
ms.assetid: f172d631-3b8c-4912-bd0f-568366cd9870
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 26331e3864940b9c7f2a2588e3d3cbfa9944c900
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87691658"
---
# <a name="specify-data-type-mappings-for-an-oracle-publisher"></a><span data-ttu-id="e6025-102">指定 Oracle 发布服务器的数据类型映射</span><span class="sxs-lookup"><span data-stu-id="e6025-102">Specify Data Type Mappings for an Oracle Publisher</span></span>
  <span data-ttu-id="e6025-103">本主题说明如何使用 [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] 或 [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] 在 [!INCLUDE[tsql](../../../includes/tsql-md.md)]中指定 Oracle 发布服务器的数据类型映射。</span><span class="sxs-lookup"><span data-stu-id="e6025-103">This topic describes how to specify data type mappings for an Oracle Publisher in [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../../includes/tsql-md.md)].</span></span> <span data-ttu-id="e6025-104">虽然已经为 Oracle 发布服务器提供了一组默认数据类型映射，但可能仍有必要为给定发布指定不同的映射。</span><span class="sxs-lookup"><span data-stu-id="e6025-104">Although a set of default data type mappings are provided for Oracle Publishers, it might be necessary to specify different mappings for a given publication.</span></span>  
  
 <span data-ttu-id="e6025-105">**本主题内容**</span><span class="sxs-lookup"><span data-stu-id="e6025-105">**In This Topic**</span></span>  
  
-   <span data-ttu-id="e6025-106">**指定 Oracle 发布服务器的数据类型映射，使用：**</span><span class="sxs-lookup"><span data-stu-id="e6025-106">**To specify data type mappings for an Oracle Publisher, using:**</span></span>  
  
     [<span data-ttu-id="e6025-107">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="e6025-107">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="e6025-108">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="e6025-108">Transact-SQL</span></span>](#TsqlProcedure)  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="e6025-109">使用 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="e6025-109">Using SQL Server Management Studio</span></span>  
 <span data-ttu-id="e6025-110">在“项目属性 - \<Article>”对话框的“数据映射”选项卡上指定数据类型映射 。</span><span class="sxs-lookup"><span data-stu-id="e6025-110">Specify data type mappings on the **Data Mapping** tab of the **Article Properties - \<Article>** dialog box.</span></span> <span data-ttu-id="e6025-111">可以从新建发布向导和“发布属性 - \<Publication>”对话框的“项目”页中访问该对话框 。</span><span class="sxs-lookup"><span data-stu-id="e6025-111">This is available from the **Articles** page of the New Publication Wizard and the **Publication Properties - \<Publication>** dialog box.</span></span> <span data-ttu-id="e6025-112">有关使用该向导和访问该对话框的详细信息，请参阅[从 Oracle 数据库创建发布](create-a-publication-from-an-oracle-database.md)以及[查看和修改发布属性](view-and-modify-publication-properties.md)。</span><span class="sxs-lookup"><span data-stu-id="e6025-112">For more information about using the wizard and accessing the dialog box, see [Create a Publication from an Oracle Database](create-a-publication-from-an-oracle-database.md) and [View and Modify Publication Properties](view-and-modify-publication-properties.md).</span></span>  
  
#### <a name="to-specify-a-data-type-mapping"></a><span data-ttu-id="e6025-113">指定数据类型映射</span><span class="sxs-lookup"><span data-stu-id="e6025-113">To specify a data type mapping</span></span>  
  
1.  <span data-ttu-id="e6025-114">在新建发布向导或“发布属性 - \<Publication>”对话框的“项目”页上，选择一个表，然后单击“项目属性”  。</span><span class="sxs-lookup"><span data-stu-id="e6025-114">On the **Articles** page of the New Publication Wizard or the **Publication Properties - \<Publication>** dialog box, select a table, and then click **Article Properties**.</span></span>  
  
2.  <span data-ttu-id="e6025-115">单击 **“设置突出显示的表项目的属性”** 。</span><span class="sxs-lookup"><span data-stu-id="e6025-115">Click **Set Properties of Highlighted Table Article**.</span></span>  
  
3.  <span data-ttu-id="e6025-116">在“项目属性 - \<Article>”对话框的“数据映射”选项卡上，从“订阅服务器数据类型”列中选择映射  ：</span><span class="sxs-lookup"><span data-stu-id="e6025-116">On the **Data Mapping** tab of the **Article Properties - \<Article>** dialog box, select mappings from the **Subscriber Data Type** column:</span></span>  
  
    -   <span data-ttu-id="e6025-117">对于某些数据类型，只能有一种可能的映射，在这种情况下，属性网格中的相应列是只读的。</span><span class="sxs-lookup"><span data-stu-id="e6025-117">For some data types there is only one possible mapping, in which case the column in the property grid is read-only.</span></span>  
  
    -   <span data-ttu-id="e6025-118">对于某些数据类型，有多种可供选择的映射类型。</span><span class="sxs-lookup"><span data-stu-id="e6025-118">For some types, there is more than one type that you can select.</span></span> <span data-ttu-id="e6025-119">除非您的应用程序需要使用其他映射，否则[!INCLUDE[msCoName](../../../includes/msconame-md.md)] 建议使用默认映射。</span><span class="sxs-lookup"><span data-stu-id="e6025-119">[!INCLUDE[msCoName](../../../includes/msconame-md.md)] recommends that you use the default mapping unless your application requires a different mapping.</span></span> <span data-ttu-id="e6025-120">有关详细信息，请参阅 [Data Type Mapping for Oracle Publishers](../non-sql/data-type-mapping-for-oracle-publishers.md)。</span><span class="sxs-lookup"><span data-stu-id="e6025-120">For more information, see [Data Type Mapping for Oracle Publishers](../non-sql/data-type-mapping-for-oracle-publishers.md).</span></span>  
  
4.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="e6025-121">使用 Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="e6025-121">Using Transact-SQL</span></span>  
 <span data-ttu-id="e6025-122">可以使用复制存储过程，以编程方式指定自定义数据类型映射。</span><span class="sxs-lookup"><span data-stu-id="e6025-122">You can specify custom data type mappings programmatically using replication stored procedures.</span></span> <span data-ttu-id="e6025-123">还可以设置在 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 与非数据库管理系统之间的数据类型之间映射 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] (DBMS) 时使用的默认映射。</span><span class="sxs-lookup"><span data-stu-id="e6025-123">You can also set the default mappings that are used when mapping data types between [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] and a non-[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] database management system (DBMS).</span></span> <span data-ttu-id="e6025-124">有关详细信息，请参阅 [Data Type Mapping for Oracle Publishers](../non-sql/data-type-mapping-for-oracle-publishers.md)。</span><span class="sxs-lookup"><span data-stu-id="e6025-124">For more information, see [Data Type Mapping for Oracle Publishers](../non-sql/data-type-mapping-for-oracle-publishers.md).</span></span>  
  
#### <a name="to-define-custom-data-type-mappings-when-creating-an-article-belonging-to-an-oracle-publication"></a><span data-ttu-id="e6025-125">在创建属于 Oracle 发布的项目时定义自定义数据类型映射</span><span class="sxs-lookup"><span data-stu-id="e6025-125">To define custom data type mappings when creating an article belonging to an Oracle publication</span></span>  
  
1.  <span data-ttu-id="e6025-126">如果尚不存在 Oracle 发布，请创建一个。</span><span class="sxs-lookup"><span data-stu-id="e6025-126">If one does not already exist, create an Oracle publication.</span></span>  
  
2.  <span data-ttu-id="e6025-127">在分发服务器上，执行 [sp_addarticle](/sql/relational-databases/system-stored-procedures/sp-addarticle-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="e6025-127">At the Distributor, execute [sp_addarticle](/sql/relational-databases/system-stored-procedures/sp-addarticle-transact-sql).</span></span> <span data-ttu-id="e6025-128">将 \@use_default_datatypes 的值指定为 0。</span><span class="sxs-lookup"><span data-stu-id="e6025-128">Specify a value of **0** for **\@use_default_datatypes**.</span></span> <span data-ttu-id="e6025-129">有关详细信息，请参阅 [定义项目](define-an-article.md)。</span><span class="sxs-lookup"><span data-stu-id="e6025-129">For more information, see [Define an Article](define-an-article.md).</span></span>  
  
3.  <span data-ttu-id="e6025-130">在分发服务器上，执行 [sp_helparticlecolumns](/sql/relational-databases/system-stored-procedures/sp-helparticlecolumns-transact-sql) 以查看已发布项目中某列的现有映射。</span><span class="sxs-lookup"><span data-stu-id="e6025-130">At the Distributor, execute [sp_helparticlecolumns](/sql/relational-databases/system-stored-procedures/sp-helparticlecolumns-transact-sql) to view the existing mapping for a column in a published article.</span></span>  
  
4.  <span data-ttu-id="e6025-131">在分发服务器上，执行 [sp_changearticlecolumndatatype](/sql/relational-databases/system-stored-procedures/sp-changearticlecolumndatatype-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="e6025-131">At the Distributor, execute [sp_changearticlecolumndatatype](/sql/relational-databases/system-stored-procedures/sp-changearticlecolumndatatype-transact-sql).</span></span> <span data-ttu-id="e6025-132">为 \@publisher 指定 Oracle 发布服务器的名称，并指定 \@publication、\@article 和 \@column 以定义已发布的列。</span><span class="sxs-lookup"><span data-stu-id="e6025-132">Specify the name of the Oracle Publisher for **\@publisher**, as well as **\@publication**, **\@article**, and **\@column** to define the published column.</span></span> <span data-ttu-id="e6025-133">为 \@type 指定要映射到的 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 数据类型的名称，并在必要时指定 \@length、\@precision 和 \@scale。</span><span class="sxs-lookup"><span data-stu-id="e6025-133">Specify the name of the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] data type to map to for **\@type**, as well as **\@length**, **\@precision**, and **\@scale**, where applicable.</span></span>  
  
5.  <span data-ttu-id="e6025-134">在分发服务器上，执行 [sp_articleview](/sql/relational-databases/system-stored-procedures/sp-articleview-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="e6025-134">At the Distributor, execute [sp_articleview](/sql/relational-databases/system-stored-procedures/sp-articleview-transact-sql).</span></span> <span data-ttu-id="e6025-135">这将创建用于从 Oracle 发布生成快照的视图。</span><span class="sxs-lookup"><span data-stu-id="e6025-135">This creates the view used to generate the snapshot from the Oracle publication.</span></span>  
  
#### <a name="to-specify-a-mapping-as-the-default-mapping-for-a-data-type"></a><span data-ttu-id="e6025-136">将映射指定为数据类型的默认映射</span><span class="sxs-lookup"><span data-stu-id="e6025-136">To specify a mapping as the default mapping for a data type</span></span>  
  
1.  <span data-ttu-id="e6025-137">（可选）在分发服务器上，对任意一个数据库执行 [sp_getdefaultdatatypemapping](/sql/relational-databases/system-stored-procedures/sp-getdefaultdatatypemapping-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="e6025-137">(Optional) At the Distributor on any database, execute [sp_getdefaultdatatypemapping](/sql/relational-databases/system-stored-procedures/sp-getdefaultdatatypemapping-transact-sql).</span></span> <span data-ttu-id="e6025-138">指定 \@source_dbms、\@source_type、\@destination_dbms、\@destination_version 以及标识源 DBMS 所需的其他任何参数。</span><span class="sxs-lookup"><span data-stu-id="e6025-138">Specify **\@source_dbms**, **\@source_type**, **\@destination_dbms**, **\@destination_version**, and any other parameters needed to identify the source DBMS.</span></span> <span data-ttu-id="e6025-139">将使用输出参数返回有关目标 DBMS 中当前映射的数据类型的信息。</span><span class="sxs-lookup"><span data-stu-id="e6025-139">Information on the currently mapped data type in the destination DBMS is returned using the output parameters.</span></span>  
  
2.  <span data-ttu-id="e6025-140">（可选）在分发服务器上，对任意一个数据库执行 [sp_helpdatatypemap](/sql/relational-databases/system-stored-procedures/sp-helpdatatypemap-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="e6025-140">(Optional) At the Distributor on any database, execute [sp_helpdatatypemap](/sql/relational-databases/system-stored-procedures/sp-helpdatatypemap-transact-sql).</span></span> <span data-ttu-id="e6025-141">指定 \@source_dbms 以及筛选结果集所需的其他任何参数。</span><span class="sxs-lookup"><span data-stu-id="e6025-141">Specify **\@source_dbms** and any other parameters needed to filter the result set.</span></span> <span data-ttu-id="e6025-142">记下结果集中所需映射的 **mapping_id** 的值。</span><span class="sxs-lookup"><span data-stu-id="e6025-142">Note the value of **mapping_id** for the desired mapping in the result set.</span></span>  
  
3.  <span data-ttu-id="e6025-143">在分发服务器上，对任意一个数据库执行 [sp_setdefaultdatatypemapping](/sql/relational-databases/system-stored-procedures/sp-setdefaultdatatypemapping-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="e6025-143">At the Distributor on any database, execute [sp_setdefaultdatatypemapping](/sql/relational-databases/system-stored-procedures/sp-setdefaultdatatypemapping-transact-sql).</span></span>  
  
    -   <span data-ttu-id="e6025-144">如果知道在步骤 2 中获取的 mapping_id 的所需值，请为 \@mapping_id 指定该值。</span><span class="sxs-lookup"><span data-stu-id="e6025-144">If you know the desired value of **mapping_id** obtained in step 2, specify it for **\@mapping_id**.</span></span>  
  
    -   <span data-ttu-id="e6025-145">如果不知道 mapping_id，请指定 \@source_dbms、\@source_type、\@destination_dbms、\@destination_type 参数以及标识现有映射所需的其他任何参数。</span><span class="sxs-lookup"><span data-stu-id="e6025-145">If you do not know the **mapping_id**, specify the parameters **\@source_dbms**, **\@source_type**, **\@destination_dbms**, **\@destination_type**, and any other parameters required to identify an existing mapping.</span></span>  
  
#### <a name="to-find-valid-data-types-for-a-given-oracle-data-type"></a><span data-ttu-id="e6025-146">查找针对给定的 Oracle 数据类型的有效数据类型</span><span class="sxs-lookup"><span data-stu-id="e6025-146">To find valid data types for a given Oracle data type</span></span>  
  
1.  <span data-ttu-id="e6025-147">在分发服务器上，对任何一个数据库执行 [sp_helpdatatypemap](/sql/relational-databases/system-stored-procedures/sp-helpdatatypemap-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="e6025-147">At the Distributor on any database, execute [sp_helpdatatypemap](/sql/relational-databases/system-stored-procedures/sp-helpdatatypemap-transact-sql).</span></span> <span data-ttu-id="e6025-148">将 \@source_dbms 的值指定为 ORACLE ，并指定筛选结果集所需的其他任何参数。</span><span class="sxs-lookup"><span data-stu-id="e6025-148">Specify a value of **ORACLE** for **\@source_dbms** and any other parameters needed to filter the result set.</span></span>  
  
###  <a name="examples-transact-sql"></a><a name="TsqlExample"></a> <span data-ttu-id="e6025-149">示例 (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="e6025-149">Examples (Transact-SQL)</span></span>  
 <span data-ttu-id="e6025-150">此示例将对其类型为 Oracle 数据类型 NUMBER 的列进行更改，以将该列映射到 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 数据类型 `numeric`(38,38) 而非默认数据类型 `float`。</span><span class="sxs-lookup"><span data-stu-id="e6025-150">This example changes a column with an Oracle data type of NUMBER so it is mapped to [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] data type `numeric`(38,38), instead of the default data type `float`.</span></span>  
  
 [!code-sql[HowTo#sp_changecolumndatatype](../../../snippets/tsql/SQL15/replication/howto/tsql/datatypemapping.sql#sp_changecolumndatatype)]  
  
 <span data-ttu-id="e6025-151">此示例查询将返回 Oracle 9 数据类型 `CHAR` 的默认映射及替代映射。</span><span class="sxs-lookup"><span data-stu-id="e6025-151">This example query returns the default and alternative mappings for the Oracle 9 data type `CHAR`.</span></span>  
  
 [!code-sql[HowTo#sp_helpcolumndatatype_char](../../../snippets/tsql/SQL15/replication/howto/tsql/datatypemapping.sql#sp_helpcolumndatatype_char)]  
  
 <span data-ttu-id="e6025-152">此示例查询在未对 Oracle 9 数据类型 `NUMBER` 指定小数位数或精度时，返回该数据类型的默认映射。</span><span class="sxs-lookup"><span data-stu-id="e6025-152">This example query returns the default mappings for the Oracle 9 data type `NUMBER` when it is specified without a scale or precision.</span></span>  
  
 [!code-sql[HowTo#sp_helpcolumndatatype_number](../../../snippets/tsql/SQL15/replication/howto/tsql/datatypemapping.sql#sp_helpcolumndatatype_number)]  
  
## <a name="see-also"></a><span data-ttu-id="e6025-153">另请参阅</span><span class="sxs-lookup"><span data-stu-id="e6025-153">See Also</span></span>  
 <span data-ttu-id="e6025-154">[Data Type Mapping for Oracle Publishers](../non-sql/data-type-mapping-for-oracle-publishers.md) </span><span class="sxs-lookup"><span data-stu-id="e6025-154">[Data Type Mapping for Oracle Publishers](../non-sql/data-type-mapping-for-oracle-publishers.md) </span></span>  
 <span data-ttu-id="e6025-155">[异类数据库复制](../non-sql/heterogeneous-database-replication.md) </span><span class="sxs-lookup"><span data-stu-id="e6025-155">[Heterogeneous Database Replication](../non-sql/heterogeneous-database-replication.md) </span></span>  
 <span data-ttu-id="e6025-156">[Replication System Stored Procedures Concepts](../concepts/replication-system-stored-procedures-concepts.md) </span><span class="sxs-lookup"><span data-stu-id="e6025-156">[Replication System Stored Procedures Concepts](../concepts/replication-system-stored-procedures-concepts.md) </span></span>  
 [<span data-ttu-id="e6025-157">配置 Oracle 发布服务器</span><span class="sxs-lookup"><span data-stu-id="e6025-157">Configure an Oracle Publisher</span></span>](../non-sql/configure-an-oracle-publisher.md)  
  
  
