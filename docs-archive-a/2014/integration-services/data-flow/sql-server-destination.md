---
title: SQL Server 目标 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.sqlserverdest.f1
helpviewer_keywords:
- SQL Server destination
- loading data
- destinations [Integration Services], SQL Server
- inserting data
- bulk load [Integration Services]
ms.assetid: a0227cd8-6944-4547-87e8-7b2507e26442
author: chugugrace
ms.author: chugu
ms.openlocfilehash: fcd65007e1e6af36386cb2ceba1f7242305b81a5
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87688075"
---
# <a name="sql-server-destination"></a><span data-ttu-id="ee204-102">SQL Server 目标</span><span class="sxs-lookup"><span data-stu-id="ee204-102">SQL Server Destination</span></span>
  <span data-ttu-id="ee204-103">SQL Server 目标连接到本地 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 数据库，并将数据大容量加载到 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 表和视图中。</span><span class="sxs-lookup"><span data-stu-id="ee204-103">The SQL Server destination connects to a local [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] database and bulk loads data into [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] tables and views.</span></span> <span data-ttu-id="ee204-104">如果包访问远程服务器上的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 数据库，则不能在包中使用 SQL Server 目标。</span><span class="sxs-lookup"><span data-stu-id="ee204-104">You cannot use the SQL Server destination in packages that access a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] database on a remote server.</span></span> <span data-ttu-id="ee204-105">相反，包应使用 OLE DB 目标。</span><span class="sxs-lookup"><span data-stu-id="ee204-105">Instead, the packages should use the OLE DB destination.</span></span> <span data-ttu-id="ee204-106">有关详细信息，请参阅 [OLE DB Destination](ole-db-destination.md)。</span><span class="sxs-lookup"><span data-stu-id="ee204-106">For more information, see [OLE DB Destination](ole-db-destination.md).</span></span>  
  
## <a name="permissions"></a><span data-ttu-id="ee204-107">权限</span><span class="sxs-lookup"><span data-stu-id="ee204-107">Permissions</span></span>  
 <span data-ttu-id="ee204-108">如果用户所执行的包中包括 SQL Server 目标，则用户需要“创建全局对象”权限。</span><span class="sxs-lookup"><span data-stu-id="ee204-108">Users who execute packages that include the SQL Server destination require the "Create global objects" permission.</span></span> <span data-ttu-id="ee204-109">通过使用从 **“管理工具”** 菜单打开的本地安全策略工具，可以将此权限授予用户。</span><span class="sxs-lookup"><span data-stu-id="ee204-109">You can grant this permission to users by using the Local Security Policy tool opened from the **Administrative Tools** menu.</span></span> <span data-ttu-id="ee204-110">如果在执行使用 SQL Server 目标的包时收到错误消息，请确保运行包的帐户拥有“创建全局对象”权限。</span><span class="sxs-lookup"><span data-stu-id="ee204-110">If you receive an error message when executing a package that uses the SQL Server destination, make sure that the account running the package has the "Create global objects" permission.</span></span>  
  
## <a name="bulk-inserts"></a><span data-ttu-id="ee204-111">大容量插入</span><span class="sxs-lookup"><span data-stu-id="ee204-111">Bulk Inserts</span></span>  
 <span data-ttu-id="ee204-112">如果尝试使用 SQL Server 目标向远程 SQL Server 数据库中大容量加载数据，可能会看到如下错误消息：“已获得 OLE DB 记录。</span><span class="sxs-lookup"><span data-stu-id="ee204-112">If you attempt to use the SQL Server destination to bulk load data into a remote SQL Server database, you may see an error message similar to the following: "An OLE DB record is available.</span></span> <span data-ttu-id="ee204-113">源：“Microsoft [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client”结果:0x80040E14 说明:“由于无法打开 SSIS 文件映射对象‘Global\DTSQLIMPORT’，无法进行大容量加载。</span><span class="sxs-lookup"><span data-stu-id="ee204-113">Source: "Microsoft [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client" Hresult: 0x80040E14 Description: "Could not bulk load because SSIS file mapping object 'Global\DTSQLIMPORT ' could not be opened.</span></span> <span data-ttu-id="ee204-114">操作系统错误代码为 2 （系统找不到指定的文件。）。</span><span class="sxs-lookup"><span data-stu-id="ee204-114">Operating system error code 2 (The system cannot find the file specified.).</span></span> <span data-ttu-id="ee204-115">请确保您是通过 Windows 安全性访问本地服务器的。”</span><span class="sxs-lookup"><span data-stu-id="ee204-115">Make sure you are accessing a local server via Windows security.""</span></span>  
  
 <span data-ttu-id="ee204-116">此 SQL Server 目标将数据插入到 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 中的速度与使用“大容量插入”任务时一样快；但使用 SQL Server 目标可以在数据加载到 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 中之前，对列数据应用转换。</span><span class="sxs-lookup"><span data-stu-id="ee204-116">The SQL Server destination offers the same high-speed insertion of data into [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] that the Bulk Insert task provides; however, by using the SQL Server destination, a package can apply transformations to column data before the data is loaded into [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
 <span data-ttu-id="ee204-117">为了将数据加载到 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]中，应考虑使用 SQL Server 目标而不是 OLE DB 目标。</span><span class="sxs-lookup"><span data-stu-id="ee204-117">For loading data into [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], you should consider using the SQL Server destination instead of the OLE DB destination.</span></span>  
  
### <a name="bulk-insert-options"></a><span data-ttu-id="ee204-118">大容量插入选项</span><span class="sxs-lookup"><span data-stu-id="ee204-118">Bulk Insert Options</span></span>  
 <span data-ttu-id="ee204-119">如果 SQL Server 目标使用快速加载数据访问模式，则可以指定下列快速加载选项：</span><span class="sxs-lookup"><span data-stu-id="ee204-119">If the SQL Server destination uses a fast-load data access mode, you can specify the following fast load options:</span></span>  
  
-   <span data-ttu-id="ee204-120">保留导入数据文件的标识值，或使用由 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]分配的唯一值。</span><span class="sxs-lookup"><span data-stu-id="ee204-120">Retain identity values from the imported data file, or use unique values assigned by [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
-   <span data-ttu-id="ee204-121">在大容量加载操作过程中保留空值。</span><span class="sxs-lookup"><span data-stu-id="ee204-121">Retain null values during the bulk load operation.</span></span>  
  
-   <span data-ttu-id="ee204-122">在大容量导入操作过程中，验证目标表或视图上的约束。</span><span class="sxs-lookup"><span data-stu-id="ee204-122">Verify constraints on the target table or view during the bulk import operation.</span></span>  
  
-   <span data-ttu-id="ee204-123">在大容量加载操作期间获取表级锁。</span><span class="sxs-lookup"><span data-stu-id="ee204-123">Acquire a table-level lock for the duration of the bulk load operation.</span></span>  
  
-   <span data-ttu-id="ee204-124">在大容量加载操作过程中，执行对目标表定义的插入触发器。</span><span class="sxs-lookup"><span data-stu-id="ee204-124">Execute insert triggers defined on the destination table during the bulk load operation.</span></span>  
  
-   <span data-ttu-id="ee204-125">在大容量插入操作过程中，指定要加载的输入中第一行的行号。</span><span class="sxs-lookup"><span data-stu-id="ee204-125">Specify the number of the first row in the input to load during the bulk insert operation.</span></span>  
  
-   <span data-ttu-id="ee204-126">在大容量插入操作过程中，指定要加载的输入中最后一行的行号。</span><span class="sxs-lookup"><span data-stu-id="ee204-126">Specify the number of the last row in the input to load during the bulk insert operation.</span></span>  
  
-   <span data-ttu-id="ee204-127">指定在大容量加载操作取消之前允许的最大错误数。</span><span class="sxs-lookup"><span data-stu-id="ee204-127">Specify the maximum number of errors allowed before the bulk load operation is canceled.</span></span> <span data-ttu-id="ee204-128">无法导入的每一行将被计为一个错误。</span><span class="sxs-lookup"><span data-stu-id="ee204-128">Each row that cannot be imported is counted as one error.</span></span>  
  
-   <span data-ttu-id="ee204-129">指定输入中包含已排序数据的列。</span><span class="sxs-lookup"><span data-stu-id="ee204-129">Specify the columns in the input that contain sorted data.</span></span>  
  
 <span data-ttu-id="ee204-130">有关大容量加载选项的详细信息，请参阅 [BULK INSERT (Transact-SQL)](/sql/t-sql/statements/bulk-insert-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="ee204-130">For more information about bulk load options, see [BULK INSERT &#40;Transact-SQL&#41;](/sql/t-sql/statements/bulk-insert-transact-sql).</span></span>  
  
#### <a name="performance-improvements"></a><span data-ttu-id="ee204-131">性能改进</span><span class="sxs-lookup"><span data-stu-id="ee204-131">Performance Improvements</span></span>  
 <span data-ttu-id="ee204-132">若要改善大容量插入的性能和在大容量插入操作过程中对表数据的访问，应对默认选项作如下更改：</span><span class="sxs-lookup"><span data-stu-id="ee204-132">To improve the performance of a bulk insert and the access to table data during the bulk insert operation, you should change the default options as follows:</span></span>  
  
-   <span data-ttu-id="ee204-133">在大容量导入操作过程中，不要验证目标表或视图上的约束。</span><span class="sxs-lookup"><span data-stu-id="ee204-133">Do not verify constraints on the target table or view during the bulk import operation.</span></span>  
  
-   <span data-ttu-id="ee204-134">在大容量加载操作过程中，不要执行在目标表上定义的插入触发器。</span><span class="sxs-lookup"><span data-stu-id="ee204-134">Do not execute insert triggers defined on the destination table during the bulk load operation.</span></span>  
  
-   <span data-ttu-id="ee204-135">不要对表应用锁。</span><span class="sxs-lookup"><span data-stu-id="ee204-135">Do not apply a lock to the table.</span></span> <span data-ttu-id="ee204-136">这样，其他用户和应用程序在大容量插入操作过程中将可以一直使用该表。</span><span class="sxs-lookup"><span data-stu-id="ee204-136">That way, the table remains available to other users and applications during the bulk insert operation.</span></span>  
  
## <a name="configuration-of-the-sql-server-destination"></a><span data-ttu-id="ee204-137">SQL Server 目标的配置</span><span class="sxs-lookup"><span data-stu-id="ee204-137">Configuration of the SQL Server Destination</span></span>  
 <span data-ttu-id="ee204-138">可以使用下列方式配置 SQL Server 目标：</span><span class="sxs-lookup"><span data-stu-id="ee204-138">You can configure the SQL Server destination in the following ways:</span></span>  
  
-   <span data-ttu-id="ee204-139">指定要向其大容量加载数据的表或视图。</span><span class="sxs-lookup"><span data-stu-id="ee204-139">Specify the table or view into which to bulk load the data.</span></span>  
  
-   <span data-ttu-id="ee204-140">通过指定如是否检查约束之类的选项，自定义大容量加载操作。</span><span class="sxs-lookup"><span data-stu-id="ee204-140">Customize the bulk load operation by specifying options such as whether to check constraints.</span></span>  
  
-   <span data-ttu-id="ee204-141">指定是否在一批中提交所有行，或设置在一批中提交的最大行数。</span><span class="sxs-lookup"><span data-stu-id="ee204-141">Specify whether all rows commit in one batch or set the maximum number of rows to commit as a batch.</span></span>  
  
-   <span data-ttu-id="ee204-142">指定大容量加载操作的超时值。</span><span class="sxs-lookup"><span data-stu-id="ee204-142">Specify a time-out for the bulk load operation.</span></span>  
  
 <span data-ttu-id="ee204-143">此目标使用 OLE DB 连接管理器连接到数据源，该连接管理器指定要使用的 OLE DB 访问接口。</span><span class="sxs-lookup"><span data-stu-id="ee204-143">This destination uses an OLE DB connection manager to connect to a data source, and the connection manager specifies the OLE DB provider to use.</span></span> <span data-ttu-id="ee204-144">有关详细信息，请参阅 [OLE DB Connection Manager](../connection-manager/ole-db-connection-manager.md)。</span><span class="sxs-lookup"><span data-stu-id="ee204-144">For more information, see [OLE DB Connection Manager](../connection-manager/ole-db-connection-manager.md).</span></span>  
  
 <span data-ttu-id="ee204-145">[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 项目还提供了创建 OLE DB 连接管理器所用的数据源对象。</span><span class="sxs-lookup"><span data-stu-id="ee204-145">An [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] project also provides the data source object from which you can create an OLE DB connection manager.</span></span> <span data-ttu-id="ee204-146">这样，SQL Server 目标便可以使用数据源和数据源视图。</span><span class="sxs-lookup"><span data-stu-id="ee204-146">This makes data sources and data source views available to the SQL Server destination.</span></span>  
  
 <span data-ttu-id="ee204-147">SQL Server 目标具有一个输入。</span><span class="sxs-lookup"><span data-stu-id="ee204-147">The SQL Server destination has one input.</span></span> <span data-ttu-id="ee204-148">它不支持错误输出。</span><span class="sxs-lookup"><span data-stu-id="ee204-148">It does not support an error output.</span></span>  
  
 <span data-ttu-id="ee204-149">可以通过 [!INCLUDE[ssIS](../../includes/ssis-md.md)] 设计器或以编程方式来设置属性。</span><span class="sxs-lookup"><span data-stu-id="ee204-149">You can set properties through [!INCLUDE[ssIS](../../includes/ssis-md.md)] Designer or programmatically.</span></span>  
  
 <span data-ttu-id="ee204-150">有关在 **“SQL Server 目标编辑器”** 对话框中可以设置的属性的详细信息，请单击下列主题之一：</span><span class="sxs-lookup"><span data-stu-id="ee204-150">For more information about the properties that you can set in the **SQL Server Destination Editor** dialog box, click one of the following topics:</span></span>  
  
-   [<span data-ttu-id="ee204-151">SQL 目标编辑器（“连接管理器”页）</span><span class="sxs-lookup"><span data-stu-id="ee204-151">SQL Destination Editor &#40;Connection Manager Page&#41;</span></span>](../sql-destination-editor-connection-manager-page.md)  
  
-   [<span data-ttu-id="ee204-152">SQL 目标编辑器（“映射”页）</span><span class="sxs-lookup"><span data-stu-id="ee204-152">SQL Destination Editor &#40;Mappings Page&#41;</span></span>](../sql-destination-editor-mappings-page.md)  
  
-   [<span data-ttu-id="ee204-153">SQL 目标编辑器（“高级”页）</span><span class="sxs-lookup"><span data-stu-id="ee204-153">SQL Destination Editor &#40;Advanced Page&#41;</span></span>](../sql-destination-editor-advanced-page.md)  
  
 <span data-ttu-id="ee204-154">**“高级编辑器”** 对话框反映了可以通过编程方式进行设置的属性。</span><span class="sxs-lookup"><span data-stu-id="ee204-154">The **Advanced Editor** dialog box reflects the properties that can be set programmatically.</span></span> <span data-ttu-id="ee204-155">有关可以在 **“高级编辑器”** 对话框中或以编程方式设置的属性的详细信息，请单击下列主题之一：</span><span class="sxs-lookup"><span data-stu-id="ee204-155">For more information about the properties that you can set in the **Advanced Editor** dialog box or programmatically, click one of the following topics:</span></span>  
  
-   [<span data-ttu-id="ee204-156">Common Properties</span><span class="sxs-lookup"><span data-stu-id="ee204-156">Common Properties</span></span>](../common-properties.md)  
  
-   [<span data-ttu-id="ee204-157">SQL Server 目标自定义属性</span><span class="sxs-lookup"><span data-stu-id="ee204-157">SQL Server Destination Custom Properties</span></span>](sql-server-destination-custom-properties.md)  
  
 <span data-ttu-id="ee204-158">有关如何设置属性的详细信息，请单击下列主题之一：</span><span class="sxs-lookup"><span data-stu-id="ee204-158">For more information about how to set properties, click one of the following topics:</span></span>  
  
-   [<span data-ttu-id="ee204-159">使用 SQL Server 目标大容量加载数据</span><span class="sxs-lookup"><span data-stu-id="ee204-159">Bulk Load Data by Using the SQL Server Destination</span></span>](sql-server-destination.md)  
  
-   [<span data-ttu-id="ee204-160">设置数据流组件的属性</span><span class="sxs-lookup"><span data-stu-id="ee204-160">Set the Properties of a Data Flow Component</span></span>](set-the-properties-of-a-data-flow-component.md)  
  
## <a name="related-tasks"></a><span data-ttu-id="ee204-161">Related Tasks</span><span class="sxs-lookup"><span data-stu-id="ee204-161">Related Tasks</span></span>  
  
-   [<span data-ttu-id="ee204-162">使用 SQL Server 目标大容量加载数据</span><span class="sxs-lookup"><span data-stu-id="ee204-162">Bulk Load Data by Using the SQL Server Destination</span></span>](sql-server-destination.md)  
  
-   [<span data-ttu-id="ee204-163">设置数据流组件的属性</span><span class="sxs-lookup"><span data-stu-id="ee204-163">Set the Properties of a Data Flow Component</span></span>](set-the-properties-of-a-data-flow-component.md)  
  
## <a name="related-content"></a><span data-ttu-id="ee204-164">相关内容</span><span class="sxs-lookup"><span data-stu-id="ee204-164">Related Content</span></span>  
  
-   <span data-ttu-id="ee204-165">support.microsoft.com 上的技术文章 [您可能会在支持 UAC 的系统上看到“无法准备 SSIS 大容量插入以插入数据”错误](https://go.microsoft.com/fwlink/?LinkId=199482)。</span><span class="sxs-lookup"><span data-stu-id="ee204-165">Technical article, [You may get "Unable to prepare the SSIS bulk insert for data insertion" error on UAC enabled systems](https://go.microsoft.com/fwlink/?LinkId=199482), on support.microsoft.com.</span></span>  
  
-   <span data-ttu-id="ee204-166">msdn.microsoft.com 上的技术文章 [数据加载性能指南](https://go.microsoft.com/fwlink/?LinkId=233700)。</span><span class="sxs-lookup"><span data-stu-id="ee204-166">Technical article, [The Data Loading Performance Guide](https://go.microsoft.com/fwlink/?LinkId=233700), on msdn.microsoft.com.</span></span>  
  
-   <span data-ttu-id="ee204-167">simple-talk.com 上的技术文章 [使用 SQL Server Integration Services 大容量加载数据](https://go.microsoft.com/fwlink/?LinkId=233701)。</span><span class="sxs-lookup"><span data-stu-id="ee204-167">Technical article, [Using SQL Server Integration Services to Bulk Load Data](https://go.microsoft.com/fwlink/?LinkId=233701), on simple-talk.com.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ee204-168">另请参阅</span><span class="sxs-lookup"><span data-stu-id="ee204-168">See Also</span></span>  
 [<span data-ttu-id="ee204-169">数据流</span><span class="sxs-lookup"><span data-stu-id="ee204-169">Data Flow</span></span>](data-flow.md)  
  
  
