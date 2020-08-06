---
title: 传输 SQL Server 对象任务编辑器 (对象 "页) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.transfersqlserverobjects.objects.f1
helpviewer_keywords:
- Transfer SQL Server Objects Task Editor
ms.assetid: 8cc09118-70ac-4013-8308-d87f8411ca0c
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 7038939b02d17b2449a374be51f7f9fa42eae7d8
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87690712"
---
# <a name="transfer-sql-server-objects-task-editor-objects-page"></a><span data-ttu-id="bd8c6-102">传输 SQL Server 对象任务编辑器（“对象”页）</span><span class="sxs-lookup"><span data-stu-id="bd8c6-102">Transfer SQL Server Objects Task Editor (Objects Page)</span></span>
  <span data-ttu-id="bd8c6-103">可以使用 **“传输 SQL Server 对象任务编辑器”** 对话框的 **“对象”** 页，指定用于将一个或多个 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 对象从一个 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 实例复制到另一个实例的属性。</span><span class="sxs-lookup"><span data-stu-id="bd8c6-103">Use the **Objects** page of the **Transfer SQL Server Objects Task Editor** dialog box to specify properties for copying one or more [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] objects from one instance of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] to another.</span></span> <span data-ttu-id="bd8c6-104">可复制的 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 对象的几个示例包括表、视图、存储过程和用户定义函数。</span><span class="sxs-lookup"><span data-stu-id="bd8c6-104">Tables, views, stored procedures, and user-defined functions are a few examples of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] objects that you can copy.</span></span> <span data-ttu-id="bd8c6-105">有关此任务的详细信息，请参阅 [Transfer SQL Server Objects Task](control-flow/transfer-sql-server-objects-task.md)。</span><span class="sxs-lookup"><span data-stu-id="bd8c6-105">For more information about this task, see [Transfer SQL Server Objects Task](control-flow/transfer-sql-server-objects-task.md).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="bd8c6-106">创建传输 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 对象任务的用户必须具有对源服务器对象的足够权限以选择对象进行复制，还必须具有访问这些对象将传输到的目标服务器数据库的权限。</span><span class="sxs-lookup"><span data-stu-id="bd8c6-106">The user who creates the Transfer [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Objects task must have sufficient permissions on the source server objects to select them for copying, and permission to access the destination server database where the objects will be transferred.</span></span>  
  
## <a name="static-options"></a><span data-ttu-id="bd8c6-107">静态选项</span><span class="sxs-lookup"><span data-stu-id="bd8c6-107">Static Options</span></span>  
 <span data-ttu-id="bd8c6-108">**SourceConnection**</span><span class="sxs-lookup"><span data-stu-id="bd8c6-108">**SourceConnection**</span></span>  
 <span data-ttu-id="bd8c6-109">从列表中选择一个 SMO 连接管理器，或单击 \<New connection...> 创建与源服务器的新连接。</span><span class="sxs-lookup"><span data-stu-id="bd8c6-109">Select a SMO connection manager in the list, or click **\<New connection...>** to create a new connection to the source server.</span></span>  
  
 <span data-ttu-id="bd8c6-110">**SourceDatabase**</span><span class="sxs-lookup"><span data-stu-id="bd8c6-110">**SourceDatabase**</span></span>  
 <span data-ttu-id="bd8c6-111">选择要从源服务器上的哪个数据库复制对象。</span><span class="sxs-lookup"><span data-stu-id="bd8c6-111">Select a database on the source server from which objects will be copied.</span></span>  
  
 <span data-ttu-id="bd8c6-112">**DestinationConnection**</span><span class="sxs-lookup"><span data-stu-id="bd8c6-112">**DestinationConnection**</span></span>  
 <span data-ttu-id="bd8c6-113">从列表中选择一个 SMO 连接管理器，或单击 \<New connection...> 创建与目标服务器的新连接。</span><span class="sxs-lookup"><span data-stu-id="bd8c6-113">Select a SMO connection manager in the list, or click **\<New connection...>** to create a new connection to the destination server.</span></span>  
  
 <span data-ttu-id="bd8c6-114">**DestinationDatabase**</span><span class="sxs-lookup"><span data-stu-id="bd8c6-114">**DestinationDatabase**</span></span>  
 <span data-ttu-id="bd8c6-115">选择对象要复制到目标服务器上的哪个数据库。</span><span class="sxs-lookup"><span data-stu-id="bd8c6-115">Select a database on the destination server to which objects will be copied.</span></span>  
  
 <span data-ttu-id="bd8c6-116">**DropObjectsFirst**</span><span class="sxs-lookup"><span data-stu-id="bd8c6-116">**DropObjectsFirst**</span></span>  
 <span data-ttu-id="bd8c6-117">选择复制前是否先在目标服务器上删除所选对象。</span><span class="sxs-lookup"><span data-stu-id="bd8c6-117">Select whether the selected objects will be dropped first on the destination server before copying.</span></span>  
  
 <span data-ttu-id="bd8c6-118">**IncludeExtendedProperties**</span><span class="sxs-lookup"><span data-stu-id="bd8c6-118">**IncludeExtendedProperties**</span></span>  
 <span data-ttu-id="bd8c6-119">选择将对象从源服务器复制到目标服务器时是否包含扩展属性。</span><span class="sxs-lookup"><span data-stu-id="bd8c6-119">Select whether extended properties will be included when objects are copied from the source to the destination server.</span></span>  
  
 <span data-ttu-id="bd8c6-120">**CopyData**</span><span class="sxs-lookup"><span data-stu-id="bd8c6-120">**CopyData**</span></span>  
 <span data-ttu-id="bd8c6-121">选择将对象从源服务器复制到目标服务器时是否包含数据。</span><span class="sxs-lookup"><span data-stu-id="bd8c6-121">Select whether data will be included when objects are copied from the source to the destination server.</span></span>  
  
 <span data-ttu-id="bd8c6-122">**ExistingData**</span><span class="sxs-lookup"><span data-stu-id="bd8c6-122">**ExistingData**</span></span>  
 <span data-ttu-id="bd8c6-123">指定将数据复制到目标服务器的方式。</span><span class="sxs-lookup"><span data-stu-id="bd8c6-123">Specify how data will be copied to the destination server.</span></span> <span data-ttu-id="bd8c6-124">此属性具有下表所列的选项：</span><span class="sxs-lookup"><span data-stu-id="bd8c6-124">This property has the options listed in the following table:</span></span>  
  
|<span data-ttu-id="bd8c6-125">值</span><span class="sxs-lookup"><span data-stu-id="bd8c6-125">Value</span></span>|<span data-ttu-id="bd8c6-126">说明</span><span class="sxs-lookup"><span data-stu-id="bd8c6-126">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="bd8c6-127">**替换**</span><span class="sxs-lookup"><span data-stu-id="bd8c6-127">**Replace**</span></span>|<span data-ttu-id="bd8c6-128">将覆盖目标服务器上的数据。</span><span class="sxs-lookup"><span data-stu-id="bd8c6-128">Data on the destination server will be overwritten.</span></span>|  
|<span data-ttu-id="bd8c6-129">**Append**</span><span class="sxs-lookup"><span data-stu-id="bd8c6-129">**Append**</span></span>|<span data-ttu-id="bd8c6-130">从源服务器复制的数据将追加到目标服务器上的现有数据中。</span><span class="sxs-lookup"><span data-stu-id="bd8c6-130">Data copied from the source server will be appended to existing data on the destination server.</span></span>|  
  
> [!NOTE]  
>  <span data-ttu-id="bd8c6-131">只有在 **CopyData** 设置为 **True** 时， **ExistingData**选项才可用。</span><span class="sxs-lookup"><span data-stu-id="bd8c6-131">The **ExistingData** option is only available when **CopyData** is set to **True**.</span></span>  
  
 <span data-ttu-id="bd8c6-132">**CopySchema**</span><span class="sxs-lookup"><span data-stu-id="bd8c6-132">**CopySchema**</span></span>  
 <span data-ttu-id="bd8c6-133">选择在传输 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 对象任务过程中是否复制架构。</span><span class="sxs-lookup"><span data-stu-id="bd8c6-133">Select whether the schema is copied during the Transfer [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Objects task.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="bd8c6-134">**CopySchema** 仅适用于 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="bd8c6-134">**CopySchema** is only available for [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].</span></span>  
  
 <span data-ttu-id="bd8c6-135">**UseCollation**</span><span class="sxs-lookup"><span data-stu-id="bd8c6-135">**UseCollation**</span></span>  
 <span data-ttu-id="bd8c6-136">选择对象的传输是否应包含源服务器上指定的排序规则。</span><span class="sxs-lookup"><span data-stu-id="bd8c6-136">Select whether the transfer of objects should include the collation specified on the source server.</span></span>  
  
 <span data-ttu-id="bd8c6-137">**IncludeDependentObjects**</span><span class="sxs-lookup"><span data-stu-id="bd8c6-137">**IncludeDependentObjects**</span></span>  
 <span data-ttu-id="bd8c6-138">选择复制所选对象时是否级联以包含依赖于所选复制对象的其他对象。</span><span class="sxs-lookup"><span data-stu-id="bd8c6-138">Select whether copying the selected objects will cascade to include other objects that depend on the objects selected for copying.</span></span>  
  
 <span data-ttu-id="bd8c6-139">**CopyAllObjects**</span><span class="sxs-lookup"><span data-stu-id="bd8c6-139">**CopyAllObjects**</span></span>  
 <span data-ttu-id="bd8c6-140">选择该任务是复制指定源数据库中的所有对象还是仅复制所选对象。</span><span class="sxs-lookup"><span data-stu-id="bd8c6-140">Select whether the task will copy all objects in the specified source database or only selected objects.</span></span>  <span data-ttu-id="bd8c6-141">如果此选项设置为 False，您就可以选择要传输的对象，并且在 **CopyAllObjects**部分中将显示动态选项。</span><span class="sxs-lookup"><span data-stu-id="bd8c6-141">Setting this option to False gives you the option to select the objects to transfer, and displays the dynamic options in the section, **CopyAllObjects**.</span></span>  
  
 <span data-ttu-id="bd8c6-142">**ObjectsToCopy**</span><span class="sxs-lookup"><span data-stu-id="bd8c6-142">**ObjectsToCopy**</span></span>  
 <span data-ttu-id="bd8c6-143">展开 **ObjectsToCopy** 以指定应从源数据库复制到目标数据库的对象。</span><span class="sxs-lookup"><span data-stu-id="bd8c6-143">Expand **ObjectsToCopy** to specify which objects should be copied from the source database to the destination database.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="bd8c6-144">**CopyAllObjects** 设置为 **False** 时， **ObjectsToCopy**选项才可用。</span><span class="sxs-lookup"><span data-stu-id="bd8c6-144">**ObjectsToCopy** is only available when **CopyAllObjects** is set to **False**.</span></span>  
  
 <span data-ttu-id="bd8c6-145">只有 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]支持用于复制以下类型的对象的选项：</span><span class="sxs-lookup"><span data-stu-id="bd8c6-145">The options to copy the following types of objects are supported only on [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]:</span></span>  
  
 <span data-ttu-id="bd8c6-146">程序集</span><span class="sxs-lookup"><span data-stu-id="bd8c6-146">Assemblies</span></span>  
  
 <span data-ttu-id="bd8c6-147">分区函数</span><span class="sxs-lookup"><span data-stu-id="bd8c6-147">Partition functions</span></span>  
  
 <span data-ttu-id="bd8c6-148">分区方案</span><span class="sxs-lookup"><span data-stu-id="bd8c6-148">Partition schemes</span></span>  
  
 <span data-ttu-id="bd8c6-149">架构</span><span class="sxs-lookup"><span data-stu-id="bd8c6-149">Schemas</span></span>  
  
 <span data-ttu-id="bd8c6-150">用户定义聚合</span><span class="sxs-lookup"><span data-stu-id="bd8c6-150">User-defined aggregates</span></span>  
  
 <span data-ttu-id="bd8c6-151">用户定义类型</span><span class="sxs-lookup"><span data-stu-id="bd8c6-151">User-defined types</span></span>  
  
 <span data-ttu-id="bd8c6-152">XML 架构集合</span><span class="sxs-lookup"><span data-stu-id="bd8c6-152">XML schema collections</span></span>  
  
 <span data-ttu-id="bd8c6-153">**CopyDatabaseUsers**</span><span class="sxs-lookup"><span data-stu-id="bd8c6-153">**CopyDatabaseUsers**</span></span>  
 <span data-ttu-id="bd8c6-154">指定传输中是否应包含数据库用户。</span><span class="sxs-lookup"><span data-stu-id="bd8c6-154">Specify whether database users should be included in the transfer.</span></span>  
  
 <span data-ttu-id="bd8c6-155">**CopyDatabaseRoles**</span><span class="sxs-lookup"><span data-stu-id="bd8c6-155">**CopyDatabaseRoles**</span></span>  
 <span data-ttu-id="bd8c6-156">指定传输中是否应包含数据库角色。</span><span class="sxs-lookup"><span data-stu-id="bd8c6-156">Specify whether database roles should be included in the transfer.</span></span>  
  
 <span data-ttu-id="bd8c6-157">**CopySqlServerLogins**</span><span class="sxs-lookup"><span data-stu-id="bd8c6-157">**CopySqlServerLogins**</span></span>  
 <span data-ttu-id="bd8c6-158">指定传输中是否应包含 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 登录名。</span><span class="sxs-lookup"><span data-stu-id="bd8c6-158">Specify whether [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] logins should be included in the transfer.</span></span>  
  
 <span data-ttu-id="bd8c6-159">**CopyObjectLevelPermissions**</span><span class="sxs-lookup"><span data-stu-id="bd8c6-159">**CopyObjectLevelPermissions**</span></span>  
 <span data-ttu-id="bd8c6-160">指定传输中是否应包含对象级权限。</span><span class="sxs-lookup"><span data-stu-id="bd8c6-160">Specify whether object-level permissions should be included in the transfer.</span></span>  
  
 <span data-ttu-id="bd8c6-161">**CopyIndexes**</span><span class="sxs-lookup"><span data-stu-id="bd8c6-161">**CopyIndexes**</span></span>  
 <span data-ttu-id="bd8c6-162">指定传输中是否应包含索引。</span><span class="sxs-lookup"><span data-stu-id="bd8c6-162">Specify whether indexes should be included in the transfer.</span></span>  
  
 <span data-ttu-id="bd8c6-163">**CopyTriggers**</span><span class="sxs-lookup"><span data-stu-id="bd8c6-163">**CopyTriggers**</span></span>  
 <span data-ttu-id="bd8c6-164">指定传输中是否应包含触发器。</span><span class="sxs-lookup"><span data-stu-id="bd8c6-164">Specify whether triggers should be included in the transfer.</span></span>  
  
 <span data-ttu-id="bd8c6-165">**CopyFullTextIndexes**</span><span class="sxs-lookup"><span data-stu-id="bd8c6-165">**CopyFullTextIndexes**</span></span>  
 <span data-ttu-id="bd8c6-166">指定传输中是否应包含全文索引。</span><span class="sxs-lookup"><span data-stu-id="bd8c6-166">Specify whether full-text indexes should be included in the transfer.</span></span>  
  
 <span data-ttu-id="bd8c6-167">**CopyPrimaryKeys**</span><span class="sxs-lookup"><span data-stu-id="bd8c6-167">**CopyPrimaryKeys**</span></span>  
 <span data-ttu-id="bd8c6-168">指定传输中是否应包含主键。</span><span class="sxs-lookup"><span data-stu-id="bd8c6-168">Specify whether primary keys should be included in the transfer.</span></span>  
  
 <span data-ttu-id="bd8c6-169">**CopyForeignKeys**</span><span class="sxs-lookup"><span data-stu-id="bd8c6-169">**CopyForeignKeys**</span></span>  
 <span data-ttu-id="bd8c6-170">指定传输中是否应包含外键。</span><span class="sxs-lookup"><span data-stu-id="bd8c6-170">Specify whether foreign keys should be included in the transfer.</span></span>  
  
 <span data-ttu-id="bd8c6-171">**GenerateScriptsInUnicode**</span><span class="sxs-lookup"><span data-stu-id="bd8c6-171">**GenerateScriptsInUnicode**</span></span>  
 <span data-ttu-id="bd8c6-172">指定生成的传输脚本是否为 Unicode 格式。</span><span class="sxs-lookup"><span data-stu-id="bd8c6-172">Specify whether the generated transfer scripts are in Unicode format.</span></span>  
  
## <a name="dynamic-options"></a><span data-ttu-id="bd8c6-173">动态选项</span><span class="sxs-lookup"><span data-stu-id="bd8c6-173">Dynamic Options</span></span>  
  
### <a name="copyallobjects--false"></a><span data-ttu-id="bd8c6-174">CopyAllObjects = False</span><span class="sxs-lookup"><span data-stu-id="bd8c6-174">CopyAllObjects = False</span></span>  
 <span data-ttu-id="bd8c6-175">**CopyAllTables**</span><span class="sxs-lookup"><span data-stu-id="bd8c6-175">**CopyAllTables**</span></span>  
 <span data-ttu-id="bd8c6-176">选择该任务是复制指定源数据库中的所有表还是仅复制所选表。</span><span class="sxs-lookup"><span data-stu-id="bd8c6-176">Select whether the task will copy all tables in the specified source database or only the selected tables.</span></span>  
  
 <span data-ttu-id="bd8c6-177">**TablesList**</span><span class="sxs-lookup"><span data-stu-id="bd8c6-177">**TablesList**</span></span>  
 <span data-ttu-id="bd8c6-178">单击此项将打开“选择表”  对话框。</span><span class="sxs-lookup"><span data-stu-id="bd8c6-178">Click to open the **Select Tables** dialog box.</span></span>  
  
 <span data-ttu-id="bd8c6-179">**CopyAllViews**</span><span class="sxs-lookup"><span data-stu-id="bd8c6-179">**CopyAllViews**</span></span>  
 <span data-ttu-id="bd8c6-180">选择该任务是复制指定源数据库中的所有视图还是仅复制所选视图。</span><span class="sxs-lookup"><span data-stu-id="bd8c6-180">Select whether the task will copy all views in the specified source database or only the selected views.</span></span>  
  
 <span data-ttu-id="bd8c6-181">**ViewsList**</span><span class="sxs-lookup"><span data-stu-id="bd8c6-181">**ViewsList**</span></span>  
 <span data-ttu-id="bd8c6-182">单击此项将打开“选择视图”  对话框。</span><span class="sxs-lookup"><span data-stu-id="bd8c6-182">Click to open the **Select Views** dialog box.</span></span>  
  
 <span data-ttu-id="bd8c6-183">**CopyAllStoredProcedures**</span><span class="sxs-lookup"><span data-stu-id="bd8c6-183">**CopyAllStoredProcedures**</span></span>  
 <span data-ttu-id="bd8c6-184">选择该任务是复制指定源数据库中的所有用户定义存储过程还是仅复制所选过程。</span><span class="sxs-lookup"><span data-stu-id="bd8c6-184">Select whether the task will copy all user-defined stored procedures in the specified source database or only the selected procedures.</span></span>  
  
 <span data-ttu-id="bd8c6-185">**StoredProceduresList**</span><span class="sxs-lookup"><span data-stu-id="bd8c6-185">**StoredProceduresList**</span></span>  
 <span data-ttu-id="bd8c6-186">单击此项将打开“选择存储过程”  对话框。</span><span class="sxs-lookup"><span data-stu-id="bd8c6-186">Click to open the **Select Stored Procedures** dialog box.</span></span>  
  
 <span data-ttu-id="bd8c6-187">**CopyAllUserDefinedFunctions**</span><span class="sxs-lookup"><span data-stu-id="bd8c6-187">**CopyAllUserDefinedFunctions**</span></span>  
 <span data-ttu-id="bd8c6-188">选择该任务是复制指定源数据库中的所有用户定义函数还是仅复制所选用户定义函数。</span><span class="sxs-lookup"><span data-stu-id="bd8c6-188">Select whether the task will copy all user-defined functions in the specified source database or only the selected UDFs.</span></span>  
  
 <span data-ttu-id="bd8c6-189">**UserDefinedFunctionsList**</span><span class="sxs-lookup"><span data-stu-id="bd8c6-189">**UserDefinedFunctionsList**</span></span>  
 <span data-ttu-id="bd8c6-190">单击此项将打开“选择用户定义函数”对话框。</span><span class="sxs-lookup"><span data-stu-id="bd8c6-190">Click to open the **Select User Defined Functions** dialog box.</span></span>  
  
 <span data-ttu-id="bd8c6-191">**CopyAllDefaults**</span><span class="sxs-lookup"><span data-stu-id="bd8c6-191">**CopyAllDefaults**</span></span>  
 <span data-ttu-id="bd8c6-192">选择该任务是复制指定源数据库中的所有默认值还是仅复制所选默认值。</span><span class="sxs-lookup"><span data-stu-id="bd8c6-192">Select whether the task will copy all defaults in the specified source database or only the selected defaults.</span></span>  
  
 <span data-ttu-id="bd8c6-193">**DefaultsList**</span><span class="sxs-lookup"><span data-stu-id="bd8c6-193">**DefaultsList**</span></span>  
 <span data-ttu-id="bd8c6-194">单击此项将打开“选择默认值”对话框。</span><span class="sxs-lookup"><span data-stu-id="bd8c6-194">Click to open the **Select Defaults** dialog box.</span></span>  
  
 <span data-ttu-id="bd8c6-195">**CopyAllUserDefinedDataTypes**</span><span class="sxs-lookup"><span data-stu-id="bd8c6-195">**CopyAllUserDefinedDataTypes**</span></span>  
 <span data-ttu-id="bd8c6-196">选择该任务是复制指定源数据库中的所有用户定义数据类型还是仅复制所选用户定义数据类型。</span><span class="sxs-lookup"><span data-stu-id="bd8c6-196">Select whether the task will copy all user-defined data types in the specified source database or only the selected user-defined data types.</span></span>  
  
 <span data-ttu-id="bd8c6-197">**UserDefinedDataTypesList**</span><span class="sxs-lookup"><span data-stu-id="bd8c6-197">**UserDefinedDataTypesList**</span></span>  
 <span data-ttu-id="bd8c6-198">单击此项将打开“选择用户定义数据类型”对话框。</span><span class="sxs-lookup"><span data-stu-id="bd8c6-198">Click to open the **Select User-Defined Data Types** dialog box.</span></span>  
  
 <span data-ttu-id="bd8c6-199">**CopyAllPartitionFunctions**</span><span class="sxs-lookup"><span data-stu-id="bd8c6-199">**CopyAllPartitionFunctions**</span></span>  
 <span data-ttu-id="bd8c6-200">选择该任务是复制指定源数据库中的所有用户定义分区函数还是仅复制所选分区函数。</span><span class="sxs-lookup"><span data-stu-id="bd8c6-200">Select whether the task will copy all user-defined partition functions in the specified source database or only the selected partition functions.</span></span> <span data-ttu-id="bd8c6-201">仅在 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]中支持。</span><span class="sxs-lookup"><span data-stu-id="bd8c6-201">Supported only on [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].</span></span>  
  
 <span data-ttu-id="bd8c6-202">**PartitionFunctionsList**</span><span class="sxs-lookup"><span data-stu-id="bd8c6-202">**PartitionFunctionsList**</span></span>  
 <span data-ttu-id="bd8c6-203">单击此项将打开“选择分区函数”对话框。</span><span class="sxs-lookup"><span data-stu-id="bd8c6-203">Click to open the **Select Partition Functions** dialog box.</span></span>  
  
 <span data-ttu-id="bd8c6-204">**CopyAllPartitionSchemes**</span><span class="sxs-lookup"><span data-stu-id="bd8c6-204">**CopyAllPartitionSchemes**</span></span>  
 <span data-ttu-id="bd8c6-205">选择该任务是复制指定源数据库中的所有分区方案还是仅复制所选分区方案。</span><span class="sxs-lookup"><span data-stu-id="bd8c6-205">Select whether the task will copy all partition schemes in the specified source database or only the selected partition schemes.</span></span> <span data-ttu-id="bd8c6-206">仅在 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]中支持。</span><span class="sxs-lookup"><span data-stu-id="bd8c6-206">Supported only on [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].</span></span>  
  
 <span data-ttu-id="bd8c6-207">**PartitionSchemesList**</span><span class="sxs-lookup"><span data-stu-id="bd8c6-207">**PartitionSchemesList**</span></span>  
 <span data-ttu-id="bd8c6-208">单击此项将打开“选择分区方案”对话框。</span><span class="sxs-lookup"><span data-stu-id="bd8c6-208">Click to open the **Select Partition Schemes** dialog box.</span></span>  
  
 <span data-ttu-id="bd8c6-209">**CopyAllSchemas**</span><span class="sxs-lookup"><span data-stu-id="bd8c6-209">**CopyAllSchemas**</span></span>  
 <span data-ttu-id="bd8c6-210">选择该任务是复制指定源数据库中的所有架构还是仅复制所选架构。</span><span class="sxs-lookup"><span data-stu-id="bd8c6-210">Select whether the task will copy all schemas in the specified source database or only the selected schemas.</span></span> <span data-ttu-id="bd8c6-211">仅在 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]中支持。</span><span class="sxs-lookup"><span data-stu-id="bd8c6-211">Supported only on [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].</span></span>  
  
 <span data-ttu-id="bd8c6-212">**SchemasList**</span><span class="sxs-lookup"><span data-stu-id="bd8c6-212">**SchemasList**</span></span>  
 <span data-ttu-id="bd8c6-213">单击此项将打开“选择架构”对话框。</span><span class="sxs-lookup"><span data-stu-id="bd8c6-213">Click to open the **Select Schemas** dialog box.</span></span>  
  
 <span data-ttu-id="bd8c6-214">**CopyAllSqlAssemblies**</span><span class="sxs-lookup"><span data-stu-id="bd8c6-214">**CopyAllSqlAssemblies**</span></span>  
 <span data-ttu-id="bd8c6-215">选择该任务是复制指定源数据库中的所有 SQL 程序集还是仅复制所选 SQL 程序集。</span><span class="sxs-lookup"><span data-stu-id="bd8c6-215">Select whether the task will copy all SQL assemblies in the specified source database or only the selected SQL assemblies.</span></span> <span data-ttu-id="bd8c6-216">仅在 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]中支持。</span><span class="sxs-lookup"><span data-stu-id="bd8c6-216">Supported only on [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].</span></span>  
  
 <span data-ttu-id="bd8c6-217">**SqlAssembliesList**</span><span class="sxs-lookup"><span data-stu-id="bd8c6-217">**SqlAssembliesList**</span></span>  
 <span data-ttu-id="bd8c6-218">单击此项将打开“选择 SQL 程序集”对话框。</span><span class="sxs-lookup"><span data-stu-id="bd8c6-218">Click to open the **Select SQL Assemblies** dialog box.</span></span>  
  
 <span data-ttu-id="bd8c6-219">**CopyAllUserDefinedAggregates**</span><span class="sxs-lookup"><span data-stu-id="bd8c6-219">**CopyAllUserDefinedAggregates**</span></span>  
 <span data-ttu-id="bd8c6-220">选择该任务是复制指定源数据库中的所有用户定义聚合还是仅复制所选用户定义聚合。</span><span class="sxs-lookup"><span data-stu-id="bd8c6-220">Select whether the task will copy all user-defined aggregates in the specified source database or only the selected user-defined aggregates.</span></span> <span data-ttu-id="bd8c6-221">仅在 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]中支持。</span><span class="sxs-lookup"><span data-stu-id="bd8c6-221">Supported only on [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].</span></span>  
  
 <span data-ttu-id="bd8c6-222">**UserDefinedAggregatesList**</span><span class="sxs-lookup"><span data-stu-id="bd8c6-222">**UserDefinedAggregatesList**</span></span>  
 <span data-ttu-id="bd8c6-223">单击此项将打开“选择用户定义聚合”对话框。</span><span class="sxs-lookup"><span data-stu-id="bd8c6-223">Click to open the **Select User-Defined Aggregates** dialog box.</span></span>  
  
 <span data-ttu-id="bd8c6-224">**CopyAllUserDefinedTypes**</span><span class="sxs-lookup"><span data-stu-id="bd8c6-224">**CopyAllUserDefinedTypes**</span></span>  
 <span data-ttu-id="bd8c6-225">选择该任务是复制指定源数据库中的所有用户定义类型还是仅复制所选用户定义类型。</span><span class="sxs-lookup"><span data-stu-id="bd8c6-225">Select whether the task will copy all user-defined types in the specified source database or only the selected UDTs.</span></span> <span data-ttu-id="bd8c6-226">仅在 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]中支持。</span><span class="sxs-lookup"><span data-stu-id="bd8c6-226">Supported only on [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].</span></span>  
  
 <span data-ttu-id="bd8c6-227">**UserDefinedTypes**</span><span class="sxs-lookup"><span data-stu-id="bd8c6-227">**UserDefinedTypes**</span></span>  
 <span data-ttu-id="bd8c6-228">单击此项将打开“选择用户定义类型”对话框。</span><span class="sxs-lookup"><span data-stu-id="bd8c6-228">Click to open the **Select User-Defined Types** dialog box.</span></span>  
  
 <span data-ttu-id="bd8c6-229">**CopyAllXmlSchemaCollections**</span><span class="sxs-lookup"><span data-stu-id="bd8c6-229">**CopyAllXmlSchemaCollections**</span></span>  
 <span data-ttu-id="bd8c6-230">选择该任务是复制指定源数据库中的所有 XML 架构集合还是仅复制所选 XML 架构集合。</span><span class="sxs-lookup"><span data-stu-id="bd8c6-230">Select whether the task will copy all XML Schema collections in the specified source database or only the selected XML schema collections.</span></span> <span data-ttu-id="bd8c6-231">仅在 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]中支持。</span><span class="sxs-lookup"><span data-stu-id="bd8c6-231">Supported only on [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].</span></span>  
  
 <span data-ttu-id="bd8c6-232">**XmlSchemaCollectionsList**</span><span class="sxs-lookup"><span data-stu-id="bd8c6-232">**XmlSchemaCollectionsList**</span></span>  
 <span data-ttu-id="bd8c6-233">单击此项将打开“选择 XML 架构集合”对话框。</span><span class="sxs-lookup"><span data-stu-id="bd8c6-233">Click to open the **Select XML Schema Collections** dialog box.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bd8c6-234">另请参阅</span><span class="sxs-lookup"><span data-stu-id="bd8c6-234">See Also</span></span>  
 <span data-ttu-id="bd8c6-235">[Integration Services 错误和消息引用](../../2014/integration-services/integration-services-error-and-message-reference.md) </span><span class="sxs-lookup"><span data-stu-id="bd8c6-235">[Integration Services Error and Message Reference](../../2014/integration-services/integration-services-error-and-message-reference.md) </span></span>  
 <span data-ttu-id="bd8c6-236">[Integration Services 任务](control-flow/integration-services-tasks.md) </span><span class="sxs-lookup"><span data-stu-id="bd8c6-236">[Integration Services Tasks](control-flow/integration-services-tasks.md) </span></span>  
 <span data-ttu-id="bd8c6-237">[传输 SQL Server 对象任务编辑器（“常规”页）](general-page-of-integration-services-designers-options.md) </span><span class="sxs-lookup"><span data-stu-id="bd8c6-237">[Transfer SQL Server Objects Task Editor &#40;General Page&#41;](general-page-of-integration-services-designers-options.md) </span></span>  
 <span data-ttu-id="bd8c6-238">[“表达式”页](expressions/expressions-page.md) </span><span class="sxs-lookup"><span data-stu-id="bd8c6-238">[Expressions Page](expressions/expressions-page.md) </span></span>  
 <span data-ttu-id="bd8c6-239">[用于批量导入或导出的数据格式 (SQL Server)](../relational-databases/import-export/data-formats-for-bulk-import-or-bulk-export-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="bd8c6-239">[Data Formats for Bulk Import or Bulk Export &#40;SQL Server&#41;](../relational-databases/import-export/data-formats-for-bulk-import-or-bulk-export-sql-server.md) </span></span>  
 [<span data-ttu-id="bd8c6-240">安装 SQL Server 的安全注意事项</span><span class="sxs-lookup"><span data-stu-id="bd8c6-240">Security Considerations for a SQL Server Installation</span></span>](../../2014/sql-server/install/security-considerations-for-a-sql-server-installation.md)  
  
  
