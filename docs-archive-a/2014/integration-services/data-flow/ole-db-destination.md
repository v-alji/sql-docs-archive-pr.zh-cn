---
title: OLE DB 目标 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.oledbdest.f1
helpviewer_keywords:
- fast-load data access mode [Integration Services]
- OLE DB destination [Integration Services]
- fast load options [Integration Services]
- fast-load options [Integration Services]
- destinations [Integration Services], OLE DB
- fast load data access mode [Integration Services]
- inserting data
ms.assetid: 873a2fa0-2a02-41fc-a80a-ec9767f36a8a
author: chugugrace
ms.author: chugu
ms.openlocfilehash: a5227175e80db3a8f31a8b8db8c3d6bee3061bae
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87579674"
---
# <a name="ole-db-destination"></a><span data-ttu-id="c64ba-102">OLE DB 目标</span><span class="sxs-lookup"><span data-stu-id="c64ba-102">OLE DB Destination</span></span>
  <span data-ttu-id="c64ba-103">OLE DB 目标用数据库表或视图或者用 SQL 命令，将数据加载到各种符合 OLE DB 的数据库中。</span><span class="sxs-lookup"><span data-stu-id="c64ba-103">The OLE DB destination loads data into a variety of OLE DB-compliant databases using a database table or view or an SQL command.</span></span> <span data-ttu-id="c64ba-104">例如，OLE DB 源可以将数据加载到 [!INCLUDE[msCoName](../../includes/msconame-md.md)] Office Access 和 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 数据库的表中。</span><span class="sxs-lookup"><span data-stu-id="c64ba-104">For example, the OLE DB source can load data into tables in [!INCLUDE[msCoName](../../includes/msconame-md.md)] Office Access and [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] databases.</span></span>  
  
 <span data-ttu-id="c64ba-105">OLE DB 目标为数据加载提供了五种数据访问模式：</span><span class="sxs-lookup"><span data-stu-id="c64ba-105">The OLE DB destination provides five different data access modes for loading data:</span></span>  
  
-   <span data-ttu-id="c64ba-106">表或视图。</span><span class="sxs-lookup"><span data-stu-id="c64ba-106">A table or view.</span></span> <span data-ttu-id="c64ba-107">可以指定现有的表或视图，也可以创建新表。</span><span class="sxs-lookup"><span data-stu-id="c64ba-107">You can specify an existing table or view, or you create a new table.</span></span>  
  
-   <span data-ttu-id="c64ba-108">使用快速加载选项的表或视图。</span><span class="sxs-lookup"><span data-stu-id="c64ba-108">A table or view using fast-load options.</span></span> <span data-ttu-id="c64ba-109">可以指定现有的表或者创建新表。</span><span class="sxs-lookup"><span data-stu-id="c64ba-109">You can specify an existing table or create a new table.</span></span>  
  
-   <span data-ttu-id="c64ba-110">变量中指定的表或视图。</span><span class="sxs-lookup"><span data-stu-id="c64ba-110">A table or view specified in a variable.</span></span>  
  
-   <span data-ttu-id="c64ba-111">使用快速加载选项在变量中指定的表或视图。</span><span class="sxs-lookup"><span data-stu-id="c64ba-111">A table or view specified in a variable using fast-load options.</span></span>  
  
-   <span data-ttu-id="c64ba-112">SQL 语句的运行结果。</span><span class="sxs-lookup"><span data-stu-id="c64ba-112">The results of an SQL statement.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="c64ba-113">OLE DB 目标不支持参数。</span><span class="sxs-lookup"><span data-stu-id="c64ba-113">The OLE DB destination does not support parameters.</span></span> <span data-ttu-id="c64ba-114">如果需要执行参数化 INSERT 语句，请考虑使用 OLE DB 命令转换。</span><span class="sxs-lookup"><span data-stu-id="c64ba-114">If you need to execute a parameterized INSERT statement, consider the OLE DB Command transformation.</span></span> <span data-ttu-id="c64ba-115">有关详细信息，请参阅 [OLE DB Command Transformation](transformations/ole-db-command-transformation.md)。</span><span class="sxs-lookup"><span data-stu-id="c64ba-115">For more information, see [OLE DB Command Transformation](transformations/ole-db-command-transformation.md).</span></span>  
  
 <span data-ttu-id="c64ba-116">当 OLE DB 目标加载使用双字节字符集 (DBCS) 的数据时，如果没有使用快速加载选项的数据访问模式，并且 OLE DB 连接管理器使用 [!INCLUDE[msCoName](../../includes/msconame-md.md)] OLE DB Provider for [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (SQLOLEDB)，则该数据可能会被损坏。</span><span class="sxs-lookup"><span data-stu-id="c64ba-116">When the OLE DB destination loads data that uses a double-byte character set (DBCS), the data may be corrupted if the data access mode does not use the fast load option and if the OLE DB connection manager uses the [!INCLUDE[msCoName](../../includes/msconame-md.md)] OLE DB Provider for [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (SQLOLEDB).</span></span> <span data-ttu-id="c64ba-117">为了确保 DBCS 数据的完整性，应将 OLE DB 连接管理器配置为使用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client 或使用以下任一快速加载访问模式：“表或视图 - 快速加载”  或“表名称或视图名称变量 - 快速加载”  。</span><span class="sxs-lookup"><span data-stu-id="c64ba-117">To ensure the integrity of DBCS data you should configure the OLE DB connection manager to use the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client, or use one of the fast-load access modes: **Table or view - fast load** or **Table name or view name variable - fast load**.</span></span> <span data-ttu-id="c64ba-118">这两个选项都可以在 **“OLE DB 目标编辑器”** 对话框中使用。</span><span class="sxs-lookup"><span data-stu-id="c64ba-118">Both options are available from the **OLE DB Destination Editor** dialog box.</span></span> <span data-ttu-id="c64ba-119">在对对象模型进行编程时 [!INCLUDE[ssIS](../../includes/ssis-md.md)] ，应将 AccessMode 属性设置为 `OpenRowset Using FastLoad` 、或 `OpenRowset Using FastLoad From Variable` 。</span><span class="sxs-lookup"><span data-stu-id="c64ba-119">When programming the [!INCLUDE[ssIS](../../includes/ssis-md.md)] object model, you should set the AccessMode property to `OpenRowset Using FastLoad`, or `OpenRowset Using FastLoad From Variable`.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="c64ba-120">如果用 **设计器中的** “OLE DB 目标编辑器” [!INCLUDE[ssIS](../../includes/ssis-md.md)] 对话框创建 OLE DB 目标要向其插入数据的目标表，可能需要手动选择新创建的表。</span><span class="sxs-lookup"><span data-stu-id="c64ba-120">If you use the **OLE DB Destination Editor** dialog box in [!INCLUDE[ssIS](../../includes/ssis-md.md)] Designer to create the destination table into which the OLE DB destination inserts data, you may have to select the newly created table manually.</span></span> <span data-ttu-id="c64ba-121">当 OLE DB 访问接口（如 OLE DB Provider for DB2）自动将架构标识符添加到表名称时，需要进行手动选择。</span><span class="sxs-lookup"><span data-stu-id="c64ba-121">The need for manual selection occurs when an OLE DB provider, such as the OLE DB provider for DB2, automatically adds schema identifiers to the table name.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="c64ba-122">**“OLE DB 目标编辑器”** 对话框生成的 CREATE TABLE 语句可能需要修改，具体取决于目标类型。</span><span class="sxs-lookup"><span data-stu-id="c64ba-122">The CREATE TABLE statement that the **OLE DB Destination Editor** dialog box generates may require modification depending on the destination type.</span></span> <span data-ttu-id="c64ba-123">例如，某些目标不支持 CREATE TABLE 语句所使用的数据类型。</span><span class="sxs-lookup"><span data-stu-id="c64ba-123">For example, some destinations do not support the data types that the CREATE TABLE statement uses.</span></span>  
  
 <span data-ttu-id="c64ba-124">此目标使用 OLE DB 连接管理器连接数据源，该连接管理器指定要使用的 OLE DB 访问接口。</span><span class="sxs-lookup"><span data-stu-id="c64ba-124">This destination uses an OLE DB connection manager to connect to a data source and the connection manager specifies the OLE DB provider to use.</span></span> <span data-ttu-id="c64ba-125">有关详细信息，请参阅 [OLE DB Connection Manager](../connection-manager/ole-db-connection-manager.md)。</span><span class="sxs-lookup"><span data-stu-id="c64ba-125">For more information, see [OLE DB Connection Manager](../connection-manager/ole-db-connection-manager.md).</span></span>  
  
 <span data-ttu-id="c64ba-126">[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 项目还提供了可从中创建 OLE DB 连接管理器的数据源对象，使数据源和数据源视图可用于 OLE DB 目标。</span><span class="sxs-lookup"><span data-stu-id="c64ba-126">An [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] project also provides the data source object from which you can create an OLE DB connection manager, to make data sources and data source views available to the OLE DB destination.</span></span>  
  
 <span data-ttu-id="c64ba-127">OLE DB 目标包括输入列和目标数据源中的列之间的映射。</span><span class="sxs-lookup"><span data-stu-id="c64ba-127">An OLE DB destination includes mappings between input columns and columns in the destination data source.</span></span> <span data-ttu-id="c64ba-128">您不必将输入列映射到所有目标列，但有时如果没有将输入列映射到目标列可能会出错，具体取决于目标列的属性。</span><span class="sxs-lookup"><span data-stu-id="c64ba-128">You do not have to map input columns to all destination columns, but depending on the properties of the destination columns, errors can occur if no input columns are mapped to the destination columns.</span></span> <span data-ttu-id="c64ba-129">例如，如果目标列不允许出现 Null 值，则必须将输入列映射到该列。</span><span class="sxs-lookup"><span data-stu-id="c64ba-129">For example, if a destination column does not allow null values, an input column must be mapped to that column.</span></span> <span data-ttu-id="c64ba-130">另外，映射的列的数据类型必须是兼容的。</span><span class="sxs-lookup"><span data-stu-id="c64ba-130">In addition, the data types of mapped columns must be compatible.</span></span> <span data-ttu-id="c64ba-131">例如，不能将数据类型为字符串的输入列映射到数据类型为数值的目标列。</span><span class="sxs-lookup"><span data-stu-id="c64ba-131">For example, you cannot map an input column with a string data type to a destination column with a numeric data type.</span></span>  
  
 <span data-ttu-id="c64ba-132">OLE DB 目标具有一个常规输入和一个错误输出。</span><span class="sxs-lookup"><span data-stu-id="c64ba-132">The OLE DB destination has one regular input and one error output.</span></span>  
  
 <span data-ttu-id="c64ba-133">有关数据类型的详细信息，请参阅 [Integration Services Data Types](integration-services-data-types.md)。</span><span class="sxs-lookup"><span data-stu-id="c64ba-133">For more information about data types, see [Integration Services Data Types](integration-services-data-types.md).</span></span>  
  
## <a name="fast-load-options"></a><span data-ttu-id="c64ba-134">快速加载选项</span><span class="sxs-lookup"><span data-stu-id="c64ba-134">Fast Load Options</span></span>  
 <span data-ttu-id="c64ba-135">如果 OLE DB 目标使用快速加载数据访问模式，则可以在用户界面“OLE DB 目标编辑器”  中为目标指定以下快速加载选项：</span><span class="sxs-lookup"><span data-stu-id="c64ba-135">If the OLE DB destination uses a fast-load data access mode, you can specify the following fast load options in the user interface, **OLE DB Destination Editor**, for the destination:</span></span>  
  
-   <span data-ttu-id="c64ba-136">保持导入数据文件的标识值或使用由 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]分配的唯一值。</span><span class="sxs-lookup"><span data-stu-id="c64ba-136">Keep identity values from the imported data file or use unique values assigned by [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
-   <span data-ttu-id="c64ba-137">在大容量加载操作过程中保留 Null 值。</span><span class="sxs-lookup"><span data-stu-id="c64ba-137">Retain a null value during the bulk load operation.</span></span>  
  
-   <span data-ttu-id="c64ba-138">在大容量导入操作过程中检查目标表或视图的约束。</span><span class="sxs-lookup"><span data-stu-id="c64ba-138">Check constraints on the target table or view during the bulk import operation.</span></span>  
  
-   <span data-ttu-id="c64ba-139">在大容量加载操作期间获取表级锁。</span><span class="sxs-lookup"><span data-stu-id="c64ba-139">Acquire a table-level lock for the duration of the bulk load operation.</span></span>  
  
-   <span data-ttu-id="c64ba-140">指定批中的行数和提交大小。</span><span class="sxs-lookup"><span data-stu-id="c64ba-140">Specify the number of rows in the batch and the commit size.</span></span>  
  
 <span data-ttu-id="c64ba-141">某些快速加载选项存储在 OLE DB 目标的特定属性中。</span><span class="sxs-lookup"><span data-stu-id="c64ba-141">Some fast load options are stored in specific properties of the OLE DB destination.</span></span> <span data-ttu-id="c64ba-142">例如，FastLoadKeepIdentity 指定是否保持标识值，FastLoadKeepNulls 指定是否保持 Null 值，而 FastLoadMaxInsertCommitSize 则指定作为批提交的行数。</span><span class="sxs-lookup"><span data-stu-id="c64ba-142">For example, FastLoadKeepIdentity specifies whether to keep identify values, FastLoadKeepNulls specifies whether to keep null values, and FastLoadMaxInsertCommitSize specifies the number of rows to commit as a batch.</span></span> <span data-ttu-id="c64ba-143">其他快速加载选项则存储在 FastLoadOptions 属性内的以逗号分隔的列表中。</span><span class="sxs-lookup"><span data-stu-id="c64ba-143">Other fast load options are stored in a comma-separated list in the FastLoadOptions property.</span></span> <span data-ttu-id="c64ba-144">如果 OLE DB 目标使用存储在 FastLoadOptions 中并在 " **OLE DB 目标编辑器**" 对话框中列出的所有快速加载选项，则该属性的值将设置为 `TABLOCK, CHECK_CONSTRAINTS, ROWS_PER_BATCH=1000` 。</span><span class="sxs-lookup"><span data-stu-id="c64ba-144">If the OLE DB destination uses all the fast load options that are stored in FastLoadOptions and listed in the **OLE DB Destination Editor** dialog box, the value of the property is set to `TABLOCK, CHECK_CONSTRAINTS, ROWS_PER_BATCH=1000`.</span></span> <span data-ttu-id="c64ba-145">值 1000 指示已将目标配置为使用 1000 行组成的批。</span><span class="sxs-lookup"><span data-stu-id="c64ba-145">The value 1000 indicates that the destination is configured to use batches of 1000 rows.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="c64ba-146">目标中任何约束失败都将导致 FastLoadMaxInsertCommitSize 所定义的整批行失败。</span><span class="sxs-lookup"><span data-stu-id="c64ba-146">Any constraint failure at the destination causes the entire batch of rows defined by FastLoadMaxInsertCommitSize to fail.</span></span>  
  
 <span data-ttu-id="c64ba-147">除了在“OLE DB 目标编辑器”  对话框中公开的快速加载选项以外，还可以通过在“高级编辑器”  对话框的 FastLoadOptions 属性中键入选项，将 OLE DB 目标配置为使用以下大容量加载选项。</span><span class="sxs-lookup"><span data-stu-id="c64ba-147">In addition to the fast load options exposed in the **OLE DB Destination Editor** dialog box,you can configure the OLE DB destination to use the following bulk load options by typing the options in FastLoadOptions property in the **Advanced Editor** dialog box.</span></span>  
  
|<span data-ttu-id="c64ba-148">快速加载选项</span><span class="sxs-lookup"><span data-stu-id="c64ba-148">Fast load option</span></span>|<span data-ttu-id="c64ba-149">说明</span><span class="sxs-lookup"><span data-stu-id="c64ba-149">Description</span></span>|  
|----------------------|-----------------|  
|<span data-ttu-id="c64ba-150">KILOBYTES_PER_BATCH</span><span class="sxs-lookup"><span data-stu-id="c64ba-150">KILOBYTES_PER_BATCH</span></span>|<span data-ttu-id="c64ba-151">指定要插入的大小 (KB)。</span><span class="sxs-lookup"><span data-stu-id="c64ba-151">Specifies the size in kilobytes to insert.</span></span> <span data-ttu-id="c64ba-152">选项的格式为 `KILOBYTES_PER_BATCH`  =  \<positive integer value**> \* \*。</span><span class="sxs-lookup"><span data-stu-id="c64ba-152">The option has the form `KILOBYTES_PER_BATCH` = \<positive integer value**>\*\*.</span></span>|  
|<span data-ttu-id="c64ba-153">FIRE_TRIGGERS</span><span class="sxs-lookup"><span data-stu-id="c64ba-153">FIRE_TRIGGERS</span></span>|<span data-ttu-id="c64ba-154">指定是否在插入表上激发触发器。</span><span class="sxs-lookup"><span data-stu-id="c64ba-154">Specifies whether triggers fire on the insert table.</span></span> <span data-ttu-id="c64ba-155">选项的格式为 **FIRE_TRIGGERS**。</span><span class="sxs-lookup"><span data-stu-id="c64ba-155">The option has the form **FIRE_TRIGGERS**.</span></span> <span data-ttu-id="c64ba-156">出现该选项说明要激发触发器。</span><span class="sxs-lookup"><span data-stu-id="c64ba-156">The presence of the option indicates that triggers fire.</span></span>|  
|<span data-ttu-id="c64ba-157">ORDER</span><span class="sxs-lookup"><span data-stu-id="c64ba-157">ORDER</span></span>|<span data-ttu-id="c64ba-158">指定输入数据如何排序。</span><span class="sxs-lookup"><span data-stu-id="c64ba-158">Specifies how the input data is sorted.</span></span> <span data-ttu-id="c64ba-159">选项格式为 ORDER \<column name> ASC&#124;DESC。</span><span class="sxs-lookup"><span data-stu-id="c64ba-159">The option has the form ORDER \<column name> ASC&#124;DESC.</span></span> <span data-ttu-id="c64ba-160">可以列出任何列数，是否包括排序顺序是可选的。</span><span class="sxs-lookup"><span data-stu-id="c64ba-160">Any number of columns may be listed and it is optional to include the sort order.</span></span> <span data-ttu-id="c64ba-161">如果省略排序顺序，则插入操作假定数据不排序。</span><span class="sxs-lookup"><span data-stu-id="c64ba-161">If sort order is omitted, the insert operation assumes the data is unsorted.</span></span><br /><br /> <span data-ttu-id="c64ba-162">注意：如果使用 ORDER 选项根据表中的聚集索引对输入数据进行排序，可以提升性能。</span><span class="sxs-lookup"><span data-stu-id="c64ba-162">Note: Performance can be improved if you use the ORDER option to sort the input data according to the clustered index on the table.</span></span>|  
  
 <span data-ttu-id="c64ba-163">[!INCLUDE[tsql](../../includes/tsql-md.md)] 关键字传统上采用大写字母键入，但并不区分大小写。</span><span class="sxs-lookup"><span data-stu-id="c64ba-163">The [!INCLUDE[tsql](../../includes/tsql-md.md)] keywords are traditionally typed using uppercase letters, but the keywords are not case sensitive.</span></span>  
  
 <span data-ttu-id="c64ba-164">若要了解快速加载选项的详细信息，请参阅[BULK INSERT (Transact-SQL)](/sql/t-sql/statements/bulk-insert-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="c64ba-164">To learn more about fast load options, see [BULK INSERT &#40;Transact-SQL&#41;](/sql/t-sql/statements/bulk-insert-transact-sql).</span></span>  
  
## <a name="troubleshooting-the-ole-db-destination"></a><span data-ttu-id="c64ba-165">OLE DB 目标故障排除</span><span class="sxs-lookup"><span data-stu-id="c64ba-165">Troubleshooting the OLE DB Destination</span></span>  
 <span data-ttu-id="c64ba-166">可以记录 OLE DB 目标对外部数据访问接口所做的调用。</span><span class="sxs-lookup"><span data-stu-id="c64ba-166">You can log the calls that the OLE DB destination makes to external data providers.</span></span> <span data-ttu-id="c64ba-167">利用此日志记录功能，可以对 OLE DB 目标在执行将数据保存到外部数据源的操作进行故障排除。</span><span class="sxs-lookup"><span data-stu-id="c64ba-167">You can use this logging capability to troubleshoot the saving of data to external data sources that the OLE DB destination performs.</span></span> <span data-ttu-id="c64ba-168">若要记录 OLE DB 目标对外部数据访问接口所做的调用，请在包级别启用包日志记录并选择 **“诊断”** 事件。</span><span class="sxs-lookup"><span data-stu-id="c64ba-168">To log the calls that the OLE DB destination makes to external data providers, enable package logging and select the **Diagnostic** event at the package level.</span></span> <span data-ttu-id="c64ba-169">有关详细信息，请参阅 [包执行的疑难解答工具](../troubleshooting/troubleshooting-tools-for-package-execution.md)。</span><span class="sxs-lookup"><span data-stu-id="c64ba-169">For more information, see [Troubleshooting Tools for Package Execution](../troubleshooting/troubleshooting-tools-for-package-execution.md).</span></span>  
  
## <a name="configuring-the-ole-db-destination"></a><span data-ttu-id="c64ba-170">配置 OLE DB 目标</span><span class="sxs-lookup"><span data-stu-id="c64ba-170">Configuring the OLE DB Destination</span></span>  
 <span data-ttu-id="c64ba-171">可以通过 [!INCLUDE[ssIS](../../includes/ssis-md.md)] 设计器或以编程方式来设置属性。</span><span class="sxs-lookup"><span data-stu-id="c64ba-171">You can set properties through [!INCLUDE[ssIS](../../includes/ssis-md.md)] Designer or programmatically.</span></span>  
  
 <span data-ttu-id="c64ba-172">有关可在 **“OLE DB 目标编辑器”** 对话框中设置的属性的详细信息，请单击下列主题之一：</span><span class="sxs-lookup"><span data-stu-id="c64ba-172">For more information about the properties that you can set in the **OLE DB Destination Editor** dialog box, click one of the following topics:</span></span>  
  
-   [<span data-ttu-id="c64ba-173">OLE DB 目标编辑器（“连接管理器”页）</span><span class="sxs-lookup"><span data-stu-id="c64ba-173">OLE DB Destination Editor &#40;Connection Manager Page&#41;</span></span>](../ole-db-destination-editor-connection-manager-page.md)  
  
-   [<span data-ttu-id="c64ba-174">OLE DB 目标编辑器（“映射”页）</span><span class="sxs-lookup"><span data-stu-id="c64ba-174">OLE DB Destination Editor &#40;Mappings Page&#41;</span></span>](../ole-db-destination-editor-mappings-page.md)  
  
-   [<span data-ttu-id="c64ba-175">OLE DB 目标编辑器（“错误输出”页）</span><span class="sxs-lookup"><span data-stu-id="c64ba-175">OLE DB Destination Editor &#40;Error Output Page&#41;</span></span>](../ole-db-destination-editor-error-output-page.md)  
  
 <span data-ttu-id="c64ba-176">**“高级编辑器”** 对话框反映了可以通过编程方式进行设置的属性。</span><span class="sxs-lookup"><span data-stu-id="c64ba-176">The **Advanced Editor** dialog box reflects the properties that can be set programmatically.</span></span> <span data-ttu-id="c64ba-177">有关可以在 **“高级编辑器”** 对话框中或以编程方式设置的属性的详细信息，请单击下列主题之一：</span><span class="sxs-lookup"><span data-stu-id="c64ba-177">For more information about the properties that you can set in the **Advanced Editor** dialog box or programmatically, click one of the following topics:</span></span>  
  
-   [<span data-ttu-id="c64ba-178">Common Properties</span><span class="sxs-lookup"><span data-stu-id="c64ba-178">Common Properties</span></span>](../common-properties.md)  
  
-   [<span data-ttu-id="c64ba-179">OLE DB 自定义属性</span><span class="sxs-lookup"><span data-stu-id="c64ba-179">OLE DB Custom Properties</span></span>](ole-db-custom-properties.md)  
  
 <span data-ttu-id="c64ba-180">有关如何设置属性的详细信息，请单击下列主题之一：</span><span class="sxs-lookup"><span data-stu-id="c64ba-180">For more information about how to set properties, click one of the following topics:</span></span>  
  
-   [<span data-ttu-id="c64ba-181">通过使用 OLE DB 目标来加载数据</span><span class="sxs-lookup"><span data-stu-id="c64ba-181">Load Data by Using the OLE DB Destination</span></span>](ole-db-destination.md)  
  
-   [<span data-ttu-id="c64ba-182">设置数据流组件的属性</span><span class="sxs-lookup"><span data-stu-id="c64ba-182">Set the Properties of a Data Flow Component</span></span>](set-the-properties-of-a-data-flow-component.md)  
  
## <a name="related-content"></a><span data-ttu-id="c64ba-183">相关内容</span><span class="sxs-lookup"><span data-stu-id="c64ba-183">Related Content</span></span>  
 [<span data-ttu-id="c64ba-184">OLE DB 源</span><span class="sxs-lookup"><span data-stu-id="c64ba-184">OLE DB Source</span></span>](ole-db-source.md)  
  
 [<span data-ttu-id="c64ba-185">Integration Services (SSIS) 变量</span><span class="sxs-lookup"><span data-stu-id="c64ba-185">Integration Services &#40;SSIS&#41; Variables</span></span>](../integration-services-ssis-variables.md)  
  
 [<span data-ttu-id="c64ba-186">数据流</span><span class="sxs-lookup"><span data-stu-id="c64ba-186">Data Flow</span></span>](data-flow.md)  
  
  
