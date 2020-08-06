---
title: 实现程序集 |Microsoft Docs
ms.custom: ''
ms.date: 03/07/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: clr
ms.topic: reference
helpviewer_keywords:
- assemblies [CLR integration], implementing
ms.assetid: c228d7bf-a906-4f37-a057-5d464d962ff8
author: rothja
ms.author: jroth
ms.openlocfilehash: 3cb3818ed644eede3cf4f2c256a0dcb94ec58c3a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87691249"
---
# <a name="implementing-assemblies"></a><span data-ttu-id="89df8-102">实现程序集</span><span class="sxs-lookup"><span data-stu-id="89df8-102">Implementing Assemblies</span></span>
  <span data-ttu-id="89df8-103">本主题提供有关以下方面的信息以帮助您在数据库中实现和使用程序集：</span><span class="sxs-lookup"><span data-stu-id="89df8-103">This topic provides information about the following areas to help you implement and work with assemblies in the database:</span></span>  
  
-   <span data-ttu-id="89df8-104">创建程序集</span><span class="sxs-lookup"><span data-stu-id="89df8-104">Creating assemblies</span></span>  
  
-   <span data-ttu-id="89df8-105">修改程序集</span><span class="sxs-lookup"><span data-stu-id="89df8-105">Modifying assemblies</span></span>  
  
-   <span data-ttu-id="89df8-106">删除、禁用和启用程序集</span><span class="sxs-lookup"><span data-stu-id="89df8-106">Dropping, disabling, and enabling assemblies</span></span>  
  
-   <span data-ttu-id="89df8-107">管理程序集版本</span><span class="sxs-lookup"><span data-stu-id="89df8-107">Managing assembly versions</span></span>  
  
## <a name="creating-assemblies"></a><span data-ttu-id="89df8-108">创建程序集</span><span class="sxs-lookup"><span data-stu-id="89df8-108">Creating Assemblies</span></span>  
 <span data-ttu-id="89df8-109">使用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] CREATE ASSEMBLY 语句在 [!INCLUDE[tsql](../../includes/tsql-md.md)] 中创建程序集或者使用程序集辅助编辑器在 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 中创建程序集。</span><span class="sxs-lookup"><span data-stu-id="89df8-109">Assemblies are created in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] by using the [!INCLUDE[tsql](../../includes/tsql-md.md)] CREATE ASSEMBLY statement, or in the [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] by using the Assembly Assisted Editor.</span></span> <span data-ttu-id="89df8-110">此外，在中部署 SQL Server 项目将在 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] 为该项目指定的数据库中注册一个程序集。</span><span class="sxs-lookup"><span data-stu-id="89df8-110">Additionally, deploying a SQL Server Project in [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] registers an assembly in the database that was specified for the project.</span></span> <span data-ttu-id="89df8-111">有关详细信息，请参阅 [Deploying CLR Database Objects](deploying-clr-database-objects.md)。</span><span class="sxs-lookup"><span data-stu-id="89df8-111">For more information, see [Deploying CLR Database Objects](deploying-clr-database-objects.md).</span></span>  
  
 <span data-ttu-id="89df8-112">**使用 Transact-SQL 创建程序集**</span><span class="sxs-lookup"><span data-stu-id="89df8-112">**To create an assembly by using Transact-SQL**</span></span>  
  
-   [<span data-ttu-id="89df8-113">CREATE ASSEMBLY (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="89df8-113">CREATE ASSEMBLY &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/create-assembly-transact-sql)  
  
 <span data-ttu-id="89df8-114">**使用 SQL Server Management Studio 创建程序集**</span><span class="sxs-lookup"><span data-stu-id="89df8-114">**To create an assembly by using SQL Server Management Studio**</span></span>  
  
-   [<span data-ttu-id="89df8-115">&#40;常规页的程序集属性&#41;</span><span class="sxs-lookup"><span data-stu-id="89df8-115">Assembly Properties &#40;General Page&#41;</span></span>](assemblies-properties.md)  
  
## <a name="modifying-assemblies"></a><span data-ttu-id="89df8-116">修改程序集</span><span class="sxs-lookup"><span data-stu-id="89df8-116">Modifying Assemblies</span></span>  
 <span data-ttu-id="89df8-117">使用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ALTER ASSEMBLY 语句在 [!INCLUDE[tsql](../../includes/tsql-md.md)] 中修改程序集或者使用程序集辅助编辑器在 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 中修改程序集。</span><span class="sxs-lookup"><span data-stu-id="89df8-117">Assemblies are modified in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] by using the [!INCLUDE[tsql](../../includes/tsql-md.md)] ALTER ASSEMBLY statement or in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] by using the Assembly Assisted Editor.</span></span> <span data-ttu-id="89df8-118">当要执行以下操作时，可以修改程序集：</span><span class="sxs-lookup"><span data-stu-id="89df8-118">You can modify an assembly when you want to do the following:</span></span>  
  
-   <span data-ttu-id="89df8-119">通过上载二进制的程序集的较新版本来更改程序集的实现。</span><span class="sxs-lookup"><span data-stu-id="89df8-119">Change the implementation of the assembly by uploading a newer version of the binaries of the assembly.</span></span> <span data-ttu-id="89df8-120">有关详细信息，请参阅本主题后面的[管理程序集版本](#_managing)。</span><span class="sxs-lookup"><span data-stu-id="89df8-120">For more information, see [Managing Assembly Versions](#_managing) later in this topic.</span></span>  
  
-   <span data-ttu-id="89df8-121">更改程序集的权限集。</span><span class="sxs-lookup"><span data-stu-id="89df8-121">Change the permission set of the assembly.</span></span> <span data-ttu-id="89df8-122">有关详细信息，请参阅[设计程序集](../../relational-databases/clr-integration/assemblies-designing.md)。</span><span class="sxs-lookup"><span data-stu-id="89df8-122">For more information, see [Designing Assemblies](../../relational-databases/clr-integration/assemblies-designing.md).</span></span>  
  
-   <span data-ttu-id="89df8-123">更改程序集的可见性。</span><span class="sxs-lookup"><span data-stu-id="89df8-123">Change the visibility of the assembly.</span></span> <span data-ttu-id="89df8-124">在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 中可引用可见程序集。</span><span class="sxs-lookup"><span data-stu-id="89df8-124">Visible assemblies are available for referencing in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="89df8-125">不可以引用不可见程序集，即使它们已上载在数据库中。</span><span class="sxs-lookup"><span data-stu-id="89df8-125">Nonvisible assemblies are not available, even if they have been uploaded in the database.</span></span> <span data-ttu-id="89df8-126">默认情况下，上载到 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 实例的程序集是可见的。</span><span class="sxs-lookup"><span data-stu-id="89df8-126">By default, assemblies uploaded to an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] are visible.</span></span>  
  
-   <span data-ttu-id="89df8-127">添加或删除与程序集关联的调试文件或源文件。</span><span class="sxs-lookup"><span data-stu-id="89df8-127">Add or drop a debug or source file associated with the assembly.</span></span>  
  
 <span data-ttu-id="89df8-128">**使用 Transact-SQL 修改程序集**</span><span class="sxs-lookup"><span data-stu-id="89df8-128">**To modify an assembly by using Transact-SQL**</span></span>  
  
-   [<span data-ttu-id="89df8-129">ALTER ASSEMBLY (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="89df8-129">ALTER ASSEMBLY &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/alter-assembly-transact-sql)  
  
 <span data-ttu-id="89df8-130">**使用 SQL Server Management Studio 修改程序集**</span><span class="sxs-lookup"><span data-stu-id="89df8-130">**To modify an assembly by using SQL Server Management Studio**</span></span>  
  
-   [<span data-ttu-id="89df8-131">&#40;常规页的程序集属性&#41;</span><span class="sxs-lookup"><span data-stu-id="89df8-131">Assembly Properties &#40;General Page&#41;</span></span>](assemblies-properties.md)  
  
## <a name="dropping-disabling-and-enabling-assemblies"></a><span data-ttu-id="89df8-132">删除、禁用和启用程序集</span><span class="sxs-lookup"><span data-stu-id="89df8-132">Dropping, Disabling, and Enabling Assemblies</span></span>  
 <span data-ttu-id="89df8-133">使用 [!INCLUDE[tsql](../../includes/tsql-md.md)] DROP ASSEMBLY 语句或 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 删除程序集。</span><span class="sxs-lookup"><span data-stu-id="89df8-133">Assemblies are dropped by using the [!INCLUDE[tsql](../../includes/tsql-md.md)] DROP ASSEMBLY statement or [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].</span></span>  
  
 <span data-ttu-id="89df8-134">**使用 Transact-SQL 删除程序集**</span><span class="sxs-lookup"><span data-stu-id="89df8-134">**To drop an assembly by using Transact-SQL**</span></span>  
  
-   [<span data-ttu-id="89df8-135">DROP ASSEMBLY (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="89df8-135">DROP ASSEMBLY &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/drop-assembly-transact-sql)  
  
 <span data-ttu-id="89df8-136">**使用 SQL Server Management Studio 删除程序集**</span><span class="sxs-lookup"><span data-stu-id="89df8-136">**To drop an assembly by using SQL Server Management Studio**</span></span>  
  
-   [<span data-ttu-id="89df8-137">删除对象</span><span class="sxs-lookup"><span data-stu-id="89df8-137">Delete Objects</span></span>](../../ssms/object/delete-objects.md)  
  
 <span data-ttu-id="89df8-138">默认情况下，不执行 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 中创建的所有程序集。</span><span class="sxs-lookup"><span data-stu-id="89df8-138">By default, all assemblies that are created in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] are disabled from executing.</span></span> <span data-ttu-id="89df8-139">您可以使用**sp_configure**系统存储过程的**clr enabled**选项来禁用或启用上传的所有程序集的执行 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="89df8-139">You can use the **clr enabled** option of the **sp_configure** system stored procedure to disable or enable the execution of all assemblies that are uploaded in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="89df8-140">禁用程序集执行防止公共语言运行时 (CLR) 函数、存储过程、触发器、聚合和用户定义类型执行并使当前正在执行的那些停止执行。</span><span class="sxs-lookup"><span data-stu-id="89df8-140">Disabling assembly execution prevents common language runtime (CLR) functions, stored procedures, triggers, aggregates, and user-defined types from executing, and stops those that are currently executing.</span></span> <span data-ttu-id="89df8-141">禁用程序集执行并不禁用创建、更改或删除程序集的功能。</span><span class="sxs-lookup"><span data-stu-id="89df8-141">Disabling assembly execution does not disable the ability to create, alter, or drop assemblies.</span></span> <span data-ttu-id="89df8-142">有关详细信息，请参阅[clr Enabled 服务器配置选项](../../database-engine/configure-windows/clr-enabled-server-configuration-option.md)。</span><span class="sxs-lookup"><span data-stu-id="89df8-142">For more information, see [clr enabled Server Configuration Option](../../database-engine/configure-windows/clr-enabled-server-configuration-option.md).</span></span>  
  
 <span data-ttu-id="89df8-143">**禁用和启用程序集执行**</span><span class="sxs-lookup"><span data-stu-id="89df8-143">**To disable and enable assembly execution**</span></span>  
  
-   [<span data-ttu-id="89df8-144">sp_configure &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="89df8-144">sp_configure &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql)  
  
##  <a name="managing-assembly-versions"></a><a name="_managing"></a><span data-ttu-id="89df8-145">管理程序集版本</span><span class="sxs-lookup"><span data-stu-id="89df8-145">Managing Assembly Versions</span></span>  
 <span data-ttu-id="89df8-146">将程序集上载到 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 实例后，将在数据库系统目录中存储并管理该程序集。</span><span class="sxs-lookup"><span data-stu-id="89df8-146">When an assembly is uploaded to an instance [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], the assembly is stored and managed within the database system catalogs.</span></span> <span data-ttu-id="89df8-147">对中的程序集定义所做的任何更改都 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] 应传播到数据库目录中存储的程序集。</span><span class="sxs-lookup"><span data-stu-id="89df8-147">Any changes made to the definition of the assembly in the [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] should be propagated to the assembly that is stored in the database catalog.</span></span>  
  
 <span data-ttu-id="89df8-148">当必须修改程序集时，您必须发出 ALTER ASSEMBLY 语句以更新数据库中的程序集。</span><span class="sxs-lookup"><span data-stu-id="89df8-148">When you have to modify an assembly, you must issue an ALTER ASSEMBLY statement to update the assembly in the database.</span></span> <span data-ttu-id="89df8-149">这将使该程序集更新为控制其实现的 [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] 模块的最新副本。</span><span class="sxs-lookup"><span data-stu-id="89df8-149">This will update the assembly to the latest copy of [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] modules holding its implementation.</span></span>  
  
 <span data-ttu-id="89df8-150">ALTER ASSEMBLY 语句中的 WITH UNCHECKED DATA 子句指示 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 甚至刷新数据库中的持久化数据依赖的那些程序集。</span><span class="sxs-lookup"><span data-stu-id="89df8-150">The WITH UNCHECKED DATA clause of the ALTER ASSEMBLY statement instructs [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] to refresh even those assemblies upon which persisted data in the database is dependent.</span></span> <span data-ttu-id="89df8-151">特别地，如果存在以下任何内容，您必须指定 WITH UNCHECKED DATA：</span><span class="sxs-lookup"><span data-stu-id="89df8-151">Specifically, you must specify WITH UNCHECKED DATA if any of the following exist:</span></span>  
  
-   <span data-ttu-id="89df8-152">通过 [!INCLUDE[tsql](../../includes/tsql-md.md)] 函数或方法直接或间接引用程序集中的方法的持久化计算列。</span><span class="sxs-lookup"><span data-stu-id="89df8-152">Persisted computed columns that reference methods in the assembly, either directly, or indirectly, through [!INCLUDE[tsql](../../includes/tsql-md.md)] functions or methods.</span></span>  
  
-   <span data-ttu-id="89df8-153">属于 CLR 用户定义类型且依赖于程序集的列，并且该类型实现的是 UserDefined（非 Native）序列化格式 。</span><span class="sxs-lookup"><span data-stu-id="89df8-153">Columns of a CLR user-defined type that depend on the assembly, and the type implements a **UserDefined** (non-**Native**) serialization format.</span></span>  
  
> [!CAUTION]  
>  <span data-ttu-id="89df8-154">未指定 WITH UNCHECKED DATA 时，如果新的程序集版本对表、索引或其他持久性站点中的现有数据造成影响，则 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 将尝试阻止 ALTER ASSEMBLY 执行。</span><span class="sxs-lookup"><span data-stu-id="89df8-154">If WITH UNCHECKED DATA is not specified, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] tries to prevent ALTER ASSEMBLY from executing if the new assembly version affects existing data in tables, indexes, or other persistent sites.</span></span> <span data-ttu-id="89df8-155">但是，当 CLR 程序集更新时，[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 不能保证计算列、索引、索引视图或表达式与基本例程和类型保持一致。</span><span class="sxs-lookup"><span data-stu-id="89df8-155">However, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] does not guarantee that computed columns, indexes, indexed views, or expressions will be consistent with the underlying routines and types when the CLR assembly is updated.</span></span> <span data-ttu-id="89df8-156">执行 ALTER ASSEMBLY 时一定要谨慎，以确保表达式的结果与程序集中存储的基于该表达式的值相互匹配。</span><span class="sxs-lookup"><span data-stu-id="89df8-156">Be careful when you execute ALTER ASSEMBLY to make sure that there is no mismatch between the result of an expression and a value that is based on that expression stored in the assembly.</span></span>  
  
 <span data-ttu-id="89df8-157">只有**db_owner**和**db_ddlowner**固定数据库角色的成员才能通过使用 WITH UNCHECKED DATA 子句来执行运行 ALTER ASSEMBLY。</span><span class="sxs-lookup"><span data-stu-id="89df8-157">Only members of the **db_owner** and **db_ddlowner** fixed database role can execute run ALTER ASSEMBLY by using the WITH UNCHECKED DATA clause.</span></span>  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="89df8-158">将消息（程序集对表中的未检查数据已修改）投递给 Windows 应用程序事件日志。</span><span class="sxs-lookup"><span data-stu-id="89df8-158">posts a message to the Windows application event log that the assembly has been modified with unchecked data in the tables.</span></span> <span data-ttu-id="89df8-159">然后 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 将任何包含依赖于程序集的数据的表标记为带有未检查数据的表。</span><span class="sxs-lookup"><span data-stu-id="89df8-159">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] then marks any tables that contain data dependent on the assembly as having unchecked data.</span></span> <span data-ttu-id="89df8-160">对于包含未检查数据的表， **sys.databases**目录视图的 " **has_unchecked_assembly_data** " 列包含值 1; 对于不包含未检查数据的表，则包含0。</span><span class="sxs-lookup"><span data-stu-id="89df8-160">The **has_unchecked_assembly_data** column of the **sys.tables** catalog view contains the value 1 for tables that contain unchecked data, and 0 for tables without unchecked data.</span></span>  
  
 <span data-ttu-id="89df8-161">若要解析未检查数据的完整性，请对带有未检查数据的每个表运行 DBCC CHECKTABLE。</span><span class="sxs-lookup"><span data-stu-id="89df8-161">To resolve the integrity of unchecked data, run DBCC CHECKTABLE against each table that has unchecked data.</span></span> <span data-ttu-id="89df8-162">如果 DBCC CHECKTABLE 失败，则您必须删除无效的表行或修改程序集代码以处理问题，然后发出其他 ALTER ASSEMBLY 语句。</span><span class="sxs-lookup"><span data-stu-id="89df8-162">If DBCC CHECKTABLE fails, you must either delete the table rows that are not valid or modify the assembly code to address problems, and then issue additional ALTER ASSEMBLY statements.</span></span>  
  
 <span data-ttu-id="89df8-163">ALTER ASSEMBLY 可更改程序集版本。</span><span class="sxs-lookup"><span data-stu-id="89df8-163">ALTER ASSEMBLY changes the assembly version.</span></span> <span data-ttu-id="89df8-164">程序集的区域性和公钥标记保持不变。SQL Server 不允许使用相同的名称、区域性和公钥注册不同版本的程序集。</span><span class="sxs-lookup"><span data-stu-id="89df8-164">The culture and public key token of the assembly remain the same.SQL Server does not allow registering different versions of an assembly with the same name, culture and public key.</span></span>  
  
### <a name="interactions-with-computer-wide-policy-for-version-binding"></a><span data-ttu-id="89df8-165">与版本绑定的计算机范围的策略交互</span><span class="sxs-lookup"><span data-stu-id="89df8-165">Interactions with Computer-wide Policy for Version Binding</span></span>  
 <span data-ttu-id="89df8-166">如果通过使用发行者策略或计算机范围的管理员策略将存储在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 中的程序集的引用重定向到了特定版本，则必须执行以下两个操作之一：</span><span class="sxs-lookup"><span data-stu-id="89df8-166">If references to assemblies stored in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] are redirected to specific versions by using publisher policy or computer-wide administrator policy, you must do either of the following:</span></span>  
  
-   <span data-ttu-id="89df8-167">请确保此重定向到的新版本在数据库中。</span><span class="sxs-lookup"><span data-stu-id="89df8-167">Make sure the new version to which this redirection is made is in the database.</span></span>  
  
-   <span data-ttu-id="89df8-168">对计算机策略或发行者策略的外部策略文件的任何语句进行修改以确保它们引用数据库中的特定版本。</span><span class="sxs-lookup"><span data-stu-id="89df8-168">Modify any statements to the external policy files of the computer or publisher policy to make sure that they reference the specific version that is in the database.</span></span>  
  
 <span data-ttu-id="89df8-169">否则，将新程序集版本加载到 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 实例的尝试将失败。</span><span class="sxs-lookup"><span data-stu-id="89df8-169">Otherwise, an attempt to load a new assembly version to the instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] will fail.</span></span>  
  
 <span data-ttu-id="89df8-170">**更新程序集的版本**</span><span class="sxs-lookup"><span data-stu-id="89df8-170">**To update the version of an assembly**</span></span>  
  
-   [<span data-ttu-id="89df8-171">ALTER ASSEMBLY (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="89df8-171">ALTER ASSEMBLY &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/alter-assembly-transact-sql)  
  
## <a name="see-also"></a><span data-ttu-id="89df8-172">另请参阅</span><span class="sxs-lookup"><span data-stu-id="89df8-172">See Also</span></span>  
 <span data-ttu-id="89df8-173">[程序集 &#40;数据库引擎&#41;](../../relational-databases/clr-integration/assemblies-database-engine.md) </span><span class="sxs-lookup"><span data-stu-id="89df8-173">[Assemblies &#40;Database Engine&#41;](../../relational-databases/clr-integration/assemblies-database-engine.md) </span></span>  
 [<span data-ttu-id="89df8-174">获取有关程序集的信息</span><span class="sxs-lookup"><span data-stu-id="89df8-174">Getting Information About Assemblies</span></span>](../../relational-databases/clr-integration/assemblies-getting-information.md)  
  
  
