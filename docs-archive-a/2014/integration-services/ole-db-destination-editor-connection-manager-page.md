---
title: OLE DB 目标编辑器 ("连接管理器" 页) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.oledbdestadapter.connection.f1
helpviewer_keywords:
- OLE DB Destination Editor
ms.assetid: ae2200c6-8ba0-49b7-b01a-53425b84d2ed
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 7217380d664ac5d20cf1ba7b437924ee3460841b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87578953"
---
# <a name="ole-db-destination-editor-connection-manager-page"></a><span data-ttu-id="590e0-102">OLE DB 目标编辑器（“连接管理器”页）</span><span class="sxs-lookup"><span data-stu-id="590e0-102">OLE DB Destination Editor (Connection Manager Page)</span></span>
  <span data-ttu-id="590e0-103">使用 **“OLE DB 目标编辑器”** 对话框的 **“连接管理器”** 页可以为目标选择 OLE DB 连接。</span><span class="sxs-lookup"><span data-stu-id="590e0-103">Use the **Connection Manager** page of the **OLE DB Destination Editor** dialog box to select the OLE DB connection for the destination.</span></span> <span data-ttu-id="590e0-104">使用此页还可以选择数据库中的表或视图。</span><span class="sxs-lookup"><span data-stu-id="590e0-104">This page also lets you select a table or view from the database.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="590e0-105">`CommandTimeout`OLE DB 目标的属性在**OLE DB 目标编辑器**中不可用，但可以使用**高级编辑器**进行设置。</span><span class="sxs-lookup"><span data-stu-id="590e0-105">The `CommandTimeout` property of the OLE DB destination is not available in the **OLE DB Destination Editor**, but can be set by using the **Advanced Editor**.</span></span> <span data-ttu-id="590e0-106">另外，某些快速加载选项仅在 **“高级编辑器”** 中提供。</span><span class="sxs-lookup"><span data-stu-id="590e0-106">In addition, certain fast load options are available only in the **Advanced Editor**.</span></span> <span data-ttu-id="590e0-107">有关这些属性的详细信息，请参阅 [OLE DB Custom Properties](data-flow/ole-db-custom-properties.md)的“OLE DB 目标”部分。</span><span class="sxs-lookup"><span data-stu-id="590e0-107">For more information on these properties, see the OLE DB Destination section of [OLE DB Custom Properties](data-flow/ole-db-custom-properties.md).</span></span>  
  
 <span data-ttu-id="590e0-108">若要了解有关 OLE DB 目标的详细信息，请参阅 [OLE DB Destination](data-flow/ole-db-destination.md)。</span><span class="sxs-lookup"><span data-stu-id="590e0-108">To learn more about the OLE DB destination, see [OLE DB Destination](data-flow/ole-db-destination.md).</span></span>  
  
## <a name="static-options"></a><span data-ttu-id="590e0-109">静态选项</span><span class="sxs-lookup"><span data-stu-id="590e0-109">Static Options</span></span>  
 <span data-ttu-id="590e0-110">**“无缓存”**</span><span class="sxs-lookup"><span data-stu-id="590e0-110">**OLE DB connection manager**</span></span>  
 <span data-ttu-id="590e0-111">从列表中选择一个现有连接管理器，或通过单击“新建”  创建一个新连接。</span><span class="sxs-lookup"><span data-stu-id="590e0-111">Select an existing connection manager from the list, or create a new connection by clicking **New**.</span></span>  
  
 <span data-ttu-id="590e0-112">**新建**</span><span class="sxs-lookup"><span data-stu-id="590e0-112">**New**</span></span>  
 <span data-ttu-id="590e0-113">通过使用“配置 OLE DB 连接管理器”  对话框创建一个新连接管理器。</span><span class="sxs-lookup"><span data-stu-id="590e0-113">Create a new connection manager by using the **Configure OLE DB Connection Manager** dialog box.</span></span>  
  
 <span data-ttu-id="590e0-114">**数据访问模式**</span><span class="sxs-lookup"><span data-stu-id="590e0-114">**Data access mode**</span></span>  
 <span data-ttu-id="590e0-115">指定向目标中加载数据的方法。</span><span class="sxs-lookup"><span data-stu-id="590e0-115">Specify the method for loading data into the destination.</span></span> <span data-ttu-id="590e0-116">加载双字节字符集 (DBCS) 数据需要使用一个快速加载选项。</span><span class="sxs-lookup"><span data-stu-id="590e0-116">Loading double-byte character set (DBCS) data requires use of one of the fast load options.</span></span> <span data-ttu-id="590e0-117">有关针对大容量插入进行了优化的快速加载数据访问模式的详细信息，请参阅 [OLE DB Destination](data-flow/ole-db-destination.md)。</span><span class="sxs-lookup"><span data-stu-id="590e0-117">For more information about the fast load data access modes, which are optimized for bulk inserts, see [OLE DB Destination](data-flow/ole-db-destination.md).</span></span>  
  
|<span data-ttu-id="590e0-118">选项</span><span class="sxs-lookup"><span data-stu-id="590e0-118">Option</span></span>|<span data-ttu-id="590e0-119">说明</span><span class="sxs-lookup"><span data-stu-id="590e0-119">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="590e0-120">表或视图</span><span class="sxs-lookup"><span data-stu-id="590e0-120">Table or view</span></span>|<span data-ttu-id="590e0-121">将数据加载到 OLE DB 目标中的表或视图。</span><span class="sxs-lookup"><span data-stu-id="590e0-121">Load data into a table or view in the OLE DB destination.</span></span>|  
|<span data-ttu-id="590e0-122">表或视图 - 快速加载</span><span class="sxs-lookup"><span data-stu-id="590e0-122">Table or view - fast load</span></span>|<span data-ttu-id="590e0-123">将数据加载到 OLE DB 目标中的表或视图，并使用快速加载选项。</span><span class="sxs-lookup"><span data-stu-id="590e0-123">Load data into a table or view in the OLE DB destination and use the fast load option.</span></span> <span data-ttu-id="590e0-124">有关针对大容量插入进行了优化的快速加载数据访问模式的详细信息，请参阅 [OLE DB Destination](data-flow/ole-db-destination.md)。</span><span class="sxs-lookup"><span data-stu-id="590e0-124">For more information about the fast load data access modes, which are optimized for bulk inserts, see [OLE DB Destination](data-flow/ole-db-destination.md).</span></span>|  
|<span data-ttu-id="590e0-125">表名变量或视图名变量</span><span class="sxs-lookup"><span data-stu-id="590e0-125">Table name or view name variable</span></span>|<span data-ttu-id="590e0-126">在变量中指定表或视图名称。</span><span class="sxs-lookup"><span data-stu-id="590e0-126">Specify the table or view name in a variable.</span></span><br /><br /> <span data-ttu-id="590e0-127">**相关信息**：[在包中使用变量](../../2014/integration-services/use-variables-in-packages.md)</span><span class="sxs-lookup"><span data-stu-id="590e0-127">**Related information**: [Use Variables in Packages](../../2014/integration-services/use-variables-in-packages.md)</span></span>|  
|<span data-ttu-id="590e0-128">表名变量或视图名变量 - 快速加载</span><span class="sxs-lookup"><span data-stu-id="590e0-128">Table name or view name variable - fast load</span></span>|<span data-ttu-id="590e0-129">在变量中指定表或视图名称，并使用快速加载选项加载数据。</span><span class="sxs-lookup"><span data-stu-id="590e0-129">Specify the table or view name in a variable, and use the fast load option to load the data.</span></span> <span data-ttu-id="590e0-130">有关针对大容量插入进行了优化的快速加载数据访问模式的详细信息，请参阅 [OLE DB Destination](data-flow/ole-db-destination.md)。</span><span class="sxs-lookup"><span data-stu-id="590e0-130">For more information about the fast load data access modes, which are optimized for bulk inserts, see [OLE DB Destination](data-flow/ole-db-destination.md).</span></span>|  
|<span data-ttu-id="590e0-131">SQL 命令</span><span class="sxs-lookup"><span data-stu-id="590e0-131">SQL command</span></span>|<span data-ttu-id="590e0-132">使用 SQL 查询将数据加载到 OLE DB 目标中。</span><span class="sxs-lookup"><span data-stu-id="590e0-132">Load data into the OLE DB destination by using a SQL query.</span></span>|  
  
 <span data-ttu-id="590e0-133">**预览**</span><span class="sxs-lookup"><span data-stu-id="590e0-133">**Preview**</span></span>  
 <span data-ttu-id="590e0-134">使用“预览查询结果”  对话框预览结果。</span><span class="sxs-lookup"><span data-stu-id="590e0-134">Preview results by using the **Preview Query Results** dialog box.</span></span> <span data-ttu-id="590e0-135">预览最多可以显示 200 行。</span><span class="sxs-lookup"><span data-stu-id="590e0-135">Preview can display up to 200 rows.</span></span>  
  
## <a name="data-access-mode-dynamic-options"></a><span data-ttu-id="590e0-136">数据访问模式动态选项</span><span class="sxs-lookup"><span data-stu-id="590e0-136">Data Access Mode Dynamic Options</span></span>  
 <span data-ttu-id="590e0-137">每个 **“数据访问模式”** 设置都显示一组特定于该设置的动态选项。</span><span class="sxs-lookup"><span data-stu-id="590e0-137">Each of the settings for **Data access mode** displays a dynamic set of options specific to that setting.</span></span> <span data-ttu-id="590e0-138">下面几节介绍对于每个 **“数据访问模式”** 设置均可用的所有动态选项。</span><span class="sxs-lookup"><span data-stu-id="590e0-138">The following sections describe each of the dynamic options available for each **Data access mode** setting.</span></span>  
  
### <a name="data-access-mode--table-or-view"></a><span data-ttu-id="590e0-139">数据访问模式 = 表或视图</span><span class="sxs-lookup"><span data-stu-id="590e0-139">Data access mode = Table or view</span></span>  
 <span data-ttu-id="590e0-140">**表或视图的名称**</span><span class="sxs-lookup"><span data-stu-id="590e0-140">**Name of the table or the view**</span></span>  
 <span data-ttu-id="590e0-141">从数据源的可用表列表或视图列表中选择表或视图的名称。</span><span class="sxs-lookup"><span data-stu-id="590e0-141">Select the name of the table or view from a list of those available in the data source.</span></span>  
  
 <span data-ttu-id="590e0-142">**新建**</span><span class="sxs-lookup"><span data-stu-id="590e0-142">**New**</span></span>  
 <span data-ttu-id="590e0-143">通过使用“创建表”  对话框创建一个新表。</span><span class="sxs-lookup"><span data-stu-id="590e0-143">Create a new table by using the **Create Table** dialog box.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="590e0-144">单击 **“新建”** 时， [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 将基于所连接的数据源生成一条默认的 CREATE TABLE 语句。</span><span class="sxs-lookup"><span data-stu-id="590e0-144">When you click **New**, [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] generates a default CREATE TABLE statement based on the connected data source.</span></span> <span data-ttu-id="590e0-145">即使源表包含一个已声明了 FILESTREAM 属性的列，此默认 CREATE TABLE 语句也不会包含 FILESTREAM 属性。</span><span class="sxs-lookup"><span data-stu-id="590e0-145">This default CREATE TABLE statement will not include the FILESTREAM attribute even if the source table includes a column with the FILESTREAM attribute declared.</span></span> <span data-ttu-id="590e0-146">若要运行具有 FILESTREAM 属性的 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 组件，首先要在目标数据库上实现 FILESTREAM 存储。</span><span class="sxs-lookup"><span data-stu-id="590e0-146">To run an [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] component with the FILESTREAM attribute, first implement FILESTREAM storage on the destination database.</span></span> <span data-ttu-id="590e0-147">然后在 **“创建表”** 对话框中将 FILESTREAM 属性添加到 CREATE TABLE 语句中。</span><span class="sxs-lookup"><span data-stu-id="590e0-147">Then, add the FILESTREAM attribute to the CREATE TABLE statement in the **Create Table** dialog box.</span></span> <span data-ttu-id="590e0-148">有关详细信息，请参阅[二进制大型对象 (Blob) 数据 (SQL Server)](../relational-databases/blob/binary-large-object-blob-data-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="590e0-148">For more information, see [Binary Large Object &#40;Blob&#41; Data &#40;SQL Server&#41;](../relational-databases/blob/binary-large-object-blob-data-sql-server.md).</span></span>  
  
### <a name="data-access-mode--table-or-view---fast-load"></a><span data-ttu-id="590e0-149">数据访问模式 = 表或视图 – 快速加载</span><span class="sxs-lookup"><span data-stu-id="590e0-149">Data access mode = Table or view - fast load</span></span>  
 <span data-ttu-id="590e0-150">**表或视图的名称**</span><span class="sxs-lookup"><span data-stu-id="590e0-150">**Name of the table or view**</span></span>  
 <span data-ttu-id="590e0-151">使用此列表从数据库中选择表或视图，或单击“新建”  创建新表。</span><span class="sxs-lookup"><span data-stu-id="590e0-151">Select a table or view from the database by using this list, or create a new table by clicking **New**.</span></span>  
  
 <span data-ttu-id="590e0-152">**新建**</span><span class="sxs-lookup"><span data-stu-id="590e0-152">**New**</span></span>  
 <span data-ttu-id="590e0-153">通过使用“创建表”  对话框创建一个新表。</span><span class="sxs-lookup"><span data-stu-id="590e0-153">Create a new table by using the **Create Table** dialog box.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="590e0-154">单击 **“新建”** 时， [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 将基于所连接的数据源生成一条默认的 CREATE TABLE 语句。</span><span class="sxs-lookup"><span data-stu-id="590e0-154">When you click **New**, [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] generates a default CREATE TABLE statement based on the connected data source.</span></span> <span data-ttu-id="590e0-155">即使源表包含一个已声明了 FILESTREAM 属性的列，此默认 CREATE TABLE 语句也不会包含 FILESTREAM 属性。</span><span class="sxs-lookup"><span data-stu-id="590e0-155">This default CREATE TABLE statement will not include the FILESTREAM attribute even if the source table includes a column with the FILESTREAM attribute declared.</span></span> <span data-ttu-id="590e0-156">若要运行具有 FILESTREAM 属性的 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 组件，首先要在目标数据库上实现 FILESTREAM 存储。</span><span class="sxs-lookup"><span data-stu-id="590e0-156">To run an [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] component with the FILESTREAM attribute, first implement FILESTREAM storage on the destination database.</span></span> <span data-ttu-id="590e0-157">然后在 **“创建表”** 对话框中将 FILESTREAM 属性添加到 CREATE TABLE 语句中。</span><span class="sxs-lookup"><span data-stu-id="590e0-157">Then, add the FILESTREAM attribute to the CREATE TABLE statement in the **Create Table** dialog box.</span></span> <span data-ttu-id="590e0-158">有关详细信息，请参阅[二进制大型对象 (Blob) 数据 (SQL Server)](../relational-databases/blob/binary-large-object-blob-data-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="590e0-158">For more information, see [Binary Large Object &#40;Blob&#41; Data &#40;SQL Server&#41;](../relational-databases/blob/binary-large-object-blob-data-sql-server.md).</span></span>  
  
 <span data-ttu-id="590e0-159">**保留标识**</span><span class="sxs-lookup"><span data-stu-id="590e0-159">**Keep identity**</span></span>  
 <span data-ttu-id="590e0-160">指定加载数据时是否复制标识值。</span><span class="sxs-lookup"><span data-stu-id="590e0-160">Specify whether to copy identity values when data is loaded.</span></span> <span data-ttu-id="590e0-161">仅在选择快速加载选项时，此属性才可用。</span><span class="sxs-lookup"><span data-stu-id="590e0-161">This property is available only with the fast load option.</span></span> <span data-ttu-id="590e0-162">此属性的默认值为 `false`。</span><span class="sxs-lookup"><span data-stu-id="590e0-162">The default value of this property is `false`.</span></span>  
  
 <span data-ttu-id="590e0-163">**保留 Null**</span><span class="sxs-lookup"><span data-stu-id="590e0-163">**Keep nulls**</span></span>  
 <span data-ttu-id="590e0-164">指定加载数据时是否复制 Null 值。</span><span class="sxs-lookup"><span data-stu-id="590e0-164">Specify whether to copy null values when data is loaded.</span></span> <span data-ttu-id="590e0-165">仅在选择快速加载选项时，此属性才可用。</span><span class="sxs-lookup"><span data-stu-id="590e0-165">This property is available only with the fast load option.</span></span> <span data-ttu-id="590e0-166">此属性的默认值为 `false`。</span><span class="sxs-lookup"><span data-stu-id="590e0-166">The default value of this property is `false`.</span></span>  
  
 <span data-ttu-id="590e0-167">**表锁**</span><span class="sxs-lookup"><span data-stu-id="590e0-167">**Table lock**</span></span>  
 <span data-ttu-id="590e0-168">指定加载期间是否锁定表。</span><span class="sxs-lookup"><span data-stu-id="590e0-168">Specify whether the table is locked during the load.</span></span> <span data-ttu-id="590e0-169">此属性的默认值为 `true`。</span><span class="sxs-lookup"><span data-stu-id="590e0-169">The default value of this property is `true`.</span></span>  
  
 <span data-ttu-id="590e0-170">**检查约束**</span><span class="sxs-lookup"><span data-stu-id="590e0-170">**Check constraints**</span></span>  
 <span data-ttu-id="590e0-171">指定目标在加载数据时是否检查约束。</span><span class="sxs-lookup"><span data-stu-id="590e0-171">Specify whether the destination checks constraints when it loads data.</span></span> <span data-ttu-id="590e0-172">此属性的默认值为 `true`。</span><span class="sxs-lookup"><span data-stu-id="590e0-172">The default value of this property is `true`.</span></span>  
  
 <span data-ttu-id="590e0-173">**每批行数**</span><span class="sxs-lookup"><span data-stu-id="590e0-173">**Rows per batch**</span></span>  
 <span data-ttu-id="590e0-174">指定每批中的行数。</span><span class="sxs-lookup"><span data-stu-id="590e0-174">Specify the number of rows in a batch.</span></span> <span data-ttu-id="590e0-175">此属性的默认值为 **-1**，表示尚未分配值。</span><span class="sxs-lookup"><span data-stu-id="590e0-175">The default value of this property is **-1**, which indicates that no value has been assigned.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="590e0-176">如果在“OLE DB 目标编辑器”  中清空此文本框，则表示不希望为此属性分配自定义值。</span><span class="sxs-lookup"><span data-stu-id="590e0-176">Clear the text box in the **OLE DB Destination Editor** to indicate that you do not want to assign a custom value for this property.</span></span>  
  
 <span data-ttu-id="590e0-177">**最大插入提交大小**</span><span class="sxs-lookup"><span data-stu-id="590e0-177">**Maximum insert commit size**</span></span>  
 <span data-ttu-id="590e0-178">指定 OLE DB 目标在快速加载操作期间尝试提交的批大小。</span><span class="sxs-lookup"><span data-stu-id="590e0-178">Specify the batch size that the OLE DB destination tries to commit during fast load operations.</span></span> <span data-ttu-id="590e0-179">值为 **0** 表示在处理完所有行之后以单批方式提交所有数据。</span><span class="sxs-lookup"><span data-stu-id="590e0-179">The value of **0** indicates that all data is committed in a single batch after all rows have been processed.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="590e0-180">如果该 OLE DB 目标和其他数据流组件正在更新同一源表，则 **0** 值可能导致正在运行的包停止响应。</span><span class="sxs-lookup"><span data-stu-id="590e0-180">A value of **0** might cause the running package to stop responding if the OLE DB destination and another data flow component are updating the same source table.</span></span> <span data-ttu-id="590e0-181">若要防止包停止，请将 **“最大插入提交大小”** 选项设置为 **2147483647**。</span><span class="sxs-lookup"><span data-stu-id="590e0-181">To prevent the package from stopping, set the **Maximum insert commit size** option to **2147483647**.</span></span>  
  
 <span data-ttu-id="590e0-182">如果为此属性提供一个值，目标将分批提交行，提交的行数是 (a) “最大插入提交大小”  与 (b) 当前正在处理的缓冲区中的剩余行数中的较小者。</span><span class="sxs-lookup"><span data-stu-id="590e0-182">If you provide a value for this property, the destination commits rows in batches that are the smaller of (a) the **Maximum insert commit size**, or (b) the remaining rows in the buffer that is currently being processed.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="590e0-183">目标中任何约束失败都将导致“最大插入提交大小”  所定义的整批行失败。</span><span class="sxs-lookup"><span data-stu-id="590e0-183">Any constraint failure at the destination causes the entire batch of rows defined by **Maximum insert commit size** to fail.</span></span>  
  
### <a name="data-access-mode--table-name-or-view-name-variable"></a><span data-ttu-id="590e0-184">数据访问模式 = 表名变量或视图名变量</span><span class="sxs-lookup"><span data-stu-id="590e0-184">Data access mode = Table name or view name variable</span></span>  
 <span data-ttu-id="590e0-185">**变量名称**</span><span class="sxs-lookup"><span data-stu-id="590e0-185">**Variable name**</span></span>  
 <span data-ttu-id="590e0-186">选择包含表或视图名称的变量。</span><span class="sxs-lookup"><span data-stu-id="590e0-186">Select the variable that contains the name of the table or view.</span></span>  
  
### <a name="data-access-mode--table-name-or-view-name-variable---fast-load"></a><span data-ttu-id="590e0-187">数据访问模式 = 表名变量或视图名变量 – 快速加载）</span><span class="sxs-lookup"><span data-stu-id="590e0-187">Data Access Mode = Table name or view name variable - fast load)</span></span>  
 <span data-ttu-id="590e0-188">**变量名称**</span><span class="sxs-lookup"><span data-stu-id="590e0-188">**Variable name**</span></span>  
 <span data-ttu-id="590e0-189">选择包含表或视图名称的变量。</span><span class="sxs-lookup"><span data-stu-id="590e0-189">Select the variable that contains the name of the table or view.</span></span>  
  
 <span data-ttu-id="590e0-190">**新建**</span><span class="sxs-lookup"><span data-stu-id="590e0-190">**New**</span></span>  
 <span data-ttu-id="590e0-191">通过使用“创建表”  对话框创建一个新表。</span><span class="sxs-lookup"><span data-stu-id="590e0-191">Create a new table by using the **Create Table** dialog box.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="590e0-192">单击 **“新建”** 时， [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 将基于所连接的数据源生成一条默认的 CREATE TABLE 语句。</span><span class="sxs-lookup"><span data-stu-id="590e0-192">When you click **New**, [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] generates a default CREATE TABLE statement based on the connected data source.</span></span> <span data-ttu-id="590e0-193">即使源表包含一个已声明了 FILESTREAM 属性的列，此默认 CREATE TABLE 语句也不会包含 FILESTREAM 属性。</span><span class="sxs-lookup"><span data-stu-id="590e0-193">This default CREATE TABLE statement will not include the FILESTREAM attribute even if the source table includes a column with the FILESTREAM attribute declared.</span></span> <span data-ttu-id="590e0-194">若要运行具有 FILESTREAM 属性的 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 组件，首先要在目标数据库上实现 FILESTREAM 存储。</span><span class="sxs-lookup"><span data-stu-id="590e0-194">To run an [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] component with the FILESTREAM attribute, first implement FILESTREAM storage on the destination database.</span></span> <span data-ttu-id="590e0-195">然后在 **“创建表”** 对话框中将 FILESTREAM 属性添加到 CREATE TABLE 语句中。</span><span class="sxs-lookup"><span data-stu-id="590e0-195">Then, add the FILESTREAM attribute to the CREATE TABLE statement in the **Create Table** dialog box.</span></span> <span data-ttu-id="590e0-196">有关详细信息，请参阅[二进制大型对象 (Blob) 数据 (SQL Server)](../relational-databases/blob/binary-large-object-blob-data-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="590e0-196">For more information, see [Binary Large Object &#40;Blob&#41; Data &#40;SQL Server&#41;](../relational-databases/blob/binary-large-object-blob-data-sql-server.md).</span></span>  
  
 <span data-ttu-id="590e0-197">**保留标识**</span><span class="sxs-lookup"><span data-stu-id="590e0-197">**Keep identity**</span></span>  
 <span data-ttu-id="590e0-198">指定加载数据时是否复制标识值。</span><span class="sxs-lookup"><span data-stu-id="590e0-198">Specify whether to copy identity values when data is loaded.</span></span> <span data-ttu-id="590e0-199">仅在选择快速加载选项时，此属性才可用。</span><span class="sxs-lookup"><span data-stu-id="590e0-199">This property is available only with the fast load option.</span></span> <span data-ttu-id="590e0-200">此属性的默认值为 `false`。</span><span class="sxs-lookup"><span data-stu-id="590e0-200">The default value of this property is `false`.</span></span>  
  
 <span data-ttu-id="590e0-201">**保留 Null**</span><span class="sxs-lookup"><span data-stu-id="590e0-201">**Keep nulls**</span></span>  
 <span data-ttu-id="590e0-202">指定加载数据时是否复制 Null 值。</span><span class="sxs-lookup"><span data-stu-id="590e0-202">Specify whether to copy null values when data is loaded.</span></span> <span data-ttu-id="590e0-203">仅在选择快速加载选项时，此属性才可用。</span><span class="sxs-lookup"><span data-stu-id="590e0-203">This property is available only with the fast load option.</span></span> <span data-ttu-id="590e0-204">此属性的默认值为 `false`。</span><span class="sxs-lookup"><span data-stu-id="590e0-204">The default value of this property is `false`.</span></span>  
  
 <span data-ttu-id="590e0-205">**表锁**</span><span class="sxs-lookup"><span data-stu-id="590e0-205">**Table lock**</span></span>  
 <span data-ttu-id="590e0-206">指定加载期间是否锁定表。</span><span class="sxs-lookup"><span data-stu-id="590e0-206">Specify whether the table is locked during the load.</span></span> <span data-ttu-id="590e0-207">此属性的默认值为 `false`。</span><span class="sxs-lookup"><span data-stu-id="590e0-207">The default value of this property is `false`.</span></span>  
  
 <span data-ttu-id="590e0-208">**检查约束**</span><span class="sxs-lookup"><span data-stu-id="590e0-208">**Check constraints**</span></span>  
 <span data-ttu-id="590e0-209">指定任务是否检查约束。</span><span class="sxs-lookup"><span data-stu-id="590e0-209">Specify whether the task checks constraints.</span></span> <span data-ttu-id="590e0-210">此属性的默认值为 `false`。</span><span class="sxs-lookup"><span data-stu-id="590e0-210">The default value of this property is `false`.</span></span>  
  
 <span data-ttu-id="590e0-211">**每批行数**</span><span class="sxs-lookup"><span data-stu-id="590e0-211">**Rows per batch**</span></span>  
 <span data-ttu-id="590e0-212">指定每批中的行数。</span><span class="sxs-lookup"><span data-stu-id="590e0-212">Specify the number of rows in a batch.</span></span> <span data-ttu-id="590e0-213">此属性的默认值为 **-1**，表示尚未分配值。</span><span class="sxs-lookup"><span data-stu-id="590e0-213">The default value of this property is **-1**, which indicates that no value has been assigned.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="590e0-214">如果在“OLE DB 目标编辑器”  中清空此文本框，则表示不希望为此属性分配自定义值。</span><span class="sxs-lookup"><span data-stu-id="590e0-214">Clear the text box in the **OLE DB Destination Editor** to indicate that you do not want to assign a custom value for this property.</span></span>  
  
 <span data-ttu-id="590e0-215">**最大插入提交大小**</span><span class="sxs-lookup"><span data-stu-id="590e0-215">**Maximum insert commit size**</span></span>  
 <span data-ttu-id="590e0-216">指定 OLE DB 目标在快速加载操作期间尝试提交的批大小。</span><span class="sxs-lookup"><span data-stu-id="590e0-216">Specify the batch size that the OLE DB destination tries to commit during fast load operations.</span></span> <span data-ttu-id="590e0-217">默认值为 **2147483647** ，表示在处理完所有行之后以单批方式提交所有数据。</span><span class="sxs-lookup"><span data-stu-id="590e0-217">The default value of **2147483647** indicates that all data is committed in a single batch after all rows have been processed.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="590e0-218">如果该 OLE DB 目标和其他数据流组件正在更新同一源表，则 **0** 值可能导致正在运行的包停止响应。</span><span class="sxs-lookup"><span data-stu-id="590e0-218">A value of **0** might cause the running package to stop responding if the OLE DB destination and another data flow component are updating the same source table.</span></span> <span data-ttu-id="590e0-219">若要防止包停止，请将 **“最大插入提交大小”** 选项设置为 **2147483647**。</span><span class="sxs-lookup"><span data-stu-id="590e0-219">To prevent the package from stopping, set the **Maximum insert commit size** option to **2147483647**.</span></span>  
  
### <a name="data-access-mode--sql-command"></a><span data-ttu-id="590e0-220">数据访问模式 = SQL 命令</span><span class="sxs-lookup"><span data-stu-id="590e0-220">Data access mode = SQL command</span></span>  
 <span data-ttu-id="590e0-221">**SQL 命令文本**</span><span class="sxs-lookup"><span data-stu-id="590e0-221">**SQL command text**</span></span>  
 <span data-ttu-id="590e0-222">输入 SQL 查询的文本，通过单击“生成查询”  来生成查询，或通过单击“浏览”  定位到包含查询文本的文件。</span><span class="sxs-lookup"><span data-stu-id="590e0-222">Enter the text of a SQL query, build the query by clicking **Build Query**, or locate the file that contains the query text by clicking **Browse**.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="590e0-223">OLE DB 目标不支持参数。</span><span class="sxs-lookup"><span data-stu-id="590e0-223">The OLE DB destination does not support parameters.</span></span> <span data-ttu-id="590e0-224">如果需要执行参数化 INSERT 语句，请考虑使用 OLE DB 命令转换。</span><span class="sxs-lookup"><span data-stu-id="590e0-224">If you need to execute a parameterized INSERT statement, consider the OLE DB Command transformation.</span></span> <span data-ttu-id="590e0-225">有关详细信息，请参阅 [OLE DB Command Transformation](data-flow/transformations/ole-db-command-transformation.md)。</span><span class="sxs-lookup"><span data-stu-id="590e0-225">For more information, see [OLE DB Command Transformation](data-flow/transformations/ole-db-command-transformation.md).</span></span>  
  
 <span data-ttu-id="590e0-226">**生成查询**</span><span class="sxs-lookup"><span data-stu-id="590e0-226">**Build query**</span></span>  
 <span data-ttu-id="590e0-227">使用“查询生成器”  对话框可直观地构造 SQL 查询。</span><span class="sxs-lookup"><span data-stu-id="590e0-227">Use the **Query Builder** dialog box to construct the SQL query visually.</span></span>  
  
 <span data-ttu-id="590e0-228">**“浏览”**</span><span class="sxs-lookup"><span data-stu-id="590e0-228">**Browse**</span></span>  
 <span data-ttu-id="590e0-229">使用“打开”  对话框可定位到包含 SQL 查询文本的文件。</span><span class="sxs-lookup"><span data-stu-id="590e0-229">Use the **Open** dialog box to locate the file that contains the text of the SQL query.</span></span>  
  
 <span data-ttu-id="590e0-230">**分析查询**</span><span class="sxs-lookup"><span data-stu-id="590e0-230">**Parse query**</span></span>  
 <span data-ttu-id="590e0-231">验证查询文本的语法。</span><span class="sxs-lookup"><span data-stu-id="590e0-231">Verify the syntax of the query text.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="590e0-232">另请参阅</span><span class="sxs-lookup"><span data-stu-id="590e0-232">See Also</span></span>  
 <span data-ttu-id="590e0-233">[Integration Services 错误和消息引用](../../2014/integration-services/integration-services-error-and-message-reference.md) </span><span class="sxs-lookup"><span data-stu-id="590e0-233">[Integration Services Error and Message Reference](../../2014/integration-services/integration-services-error-and-message-reference.md) </span></span>  
 <span data-ttu-id="590e0-234">[OLE DB 目标编辑器 &#40;映射 "页&#41;](../../2014/integration-services/ole-db-destination-editor-mappings-page.md) </span><span class="sxs-lookup"><span data-stu-id="590e0-234">[OLE DB Destination Editor &#40;Mappings Page&#41;](../../2014/integration-services/ole-db-destination-editor-mappings-page.md) </span></span>  
 <span data-ttu-id="590e0-235">[OLE DB 目标编辑器 &#40;错误输出页&#41;](../../2014/integration-services/ole-db-destination-editor-error-output-page.md) </span><span class="sxs-lookup"><span data-stu-id="590e0-235">[OLE DB Destination Editor &#40;Error Output Page&#41;](../../2014/integration-services/ole-db-destination-editor-error-output-page.md) </span></span>  
 [<span data-ttu-id="590e0-236">通过使用 OLE DB 目标来加载数据</span><span class="sxs-lookup"><span data-stu-id="590e0-236">Load Data by Using the OLE DB Destination</span></span>](data-flow/load-data-by-using-the-ole-db-destination.md)  
  
  
