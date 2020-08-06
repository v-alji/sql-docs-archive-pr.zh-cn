---
title: 设置多维数据库 (Analysis Services) 的兼容级别 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 978279e6-a581-4184-af9d-8701b9826a89
author: minewiskan
ms.author: owend
ms.openlocfilehash: eea3d522abc5133e759cf476f3b169fd570b196f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87691986"
---
# <a name="set-the-compatibility-level-of-a-multidimensional-database-analysis-services"></a><span data-ttu-id="a2c7a-102">设置多维数据库的兼容级别 (Analysis Services)</span><span class="sxs-lookup"><span data-stu-id="a2c7a-102">Set the Compatibility Level of a Multidimensional Database (Analysis Services)</span></span>
  <span data-ttu-id="a2c7a-103">在 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]中，数据库兼容级别属性确定数据库的功能级别。</span><span class="sxs-lookup"><span data-stu-id="a2c7a-103">In [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], the database compatibility level property determines the functional level of a database.</span></span> <span data-ttu-id="a2c7a-104">兼容级别对于每个模型类型都是唯一的。</span><span class="sxs-lookup"><span data-stu-id="a2c7a-104">Compatibility levels are unique to each model type.</span></span> <span data-ttu-id="a2c7a-105">例如，兼容级别 `1100` 具有不同的含义，具体取决于该数据库是多维数据库还是表格数据库。</span><span class="sxs-lookup"><span data-stu-id="a2c7a-105">For example, a compatibility level of `1100` has a different meaning depending on whether the database is multidimensional or tabular.</span></span>  
  
 <span data-ttu-id="a2c7a-106">本主题仅描述多维数据库的兼容级别。</span><span class="sxs-lookup"><span data-stu-id="a2c7a-106">This topic describes compatibility level for multidimensional databases only.</span></span> <span data-ttu-id="a2c7a-107">有关表格解决方案的详细信息，请参阅[&#40;SSAS 表格 SP1&#41;兼容级别](../tabular-models/compatibility-level-for-tabular-models-in-analysis-services.md)。</span><span class="sxs-lookup"><span data-stu-id="a2c7a-107">For more information about tabular solutions, see [Compatibility Level &#40;SSAS Tabular SP1&#41;](../tabular-models/compatibility-level-for-tabular-models-in-analysis-services.md).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="a2c7a-108">表格模型具有其他一些不适用于多维模型的数据库兼容级别。</span><span class="sxs-lookup"><span data-stu-id="a2c7a-108">Tabular models have additional database compatibility levels that are not applicable to multidimensional models.</span></span> <span data-ttu-id="a2c7a-109">多维模型不具有兼容级别 `1103`。</span><span class="sxs-lookup"><span data-stu-id="a2c7a-109">Compatibility level `1103` does not exist for multidimensional models.</span></span> <span data-ttu-id="a2c7a-110">有关表格解决方案的详细信息，请参阅[SQL Server 2012 SP1 和兼容性级别中表格模型的新增功能](https://go.microsoft.com/fwlink/?LinkId=301727) `1103` 。</span><span class="sxs-lookup"><span data-stu-id="a2c7a-110">See [What is new for the Tabular model in SQL Server 2012 SP1 and compatibility level](https://go.microsoft.com/fwlink/?LinkId=301727) for more information about `1103` for tabular solutions.</span></span>  
  
 <span data-ttu-id="a2c7a-111">**多维数据库的兼容级别**</span><span class="sxs-lookup"><span data-stu-id="a2c7a-111">**Compatibility Levels for multidimensional databases**</span></span>  
  
 <span data-ttu-id="a2c7a-112">目前，唯一因功能级别而异的多维数据库行为是字符串存储体系结构。</span><span class="sxs-lookup"><span data-stu-id="a2c7a-112">Currently, the only multidimensional database behavior that varies by functional level is string storage architecture.</span></span> <span data-ttu-id="a2c7a-113">通过提高数据库兼容级别，可以覆盖度量值和维度的最大 4 GB 字符串存储限制。</span><span class="sxs-lookup"><span data-stu-id="a2c7a-113">By raising the database compatibility level, you can override the 4 gigabyte maximum limit for string storage of measures and dimensions.</span></span>  
  
 <span data-ttu-id="a2c7a-114">对于多维数据库，`CompatibilityLevel` 属性的有效值包括以下：</span><span class="sxs-lookup"><span data-stu-id="a2c7a-114">For a multidimensional database, valid values for the `CompatibilityLevel` property include the following:</span></span>  
  
|<span data-ttu-id="a2c7a-115">设置</span><span class="sxs-lookup"><span data-stu-id="a2c7a-115">Setting</span></span>|<span data-ttu-id="a2c7a-116">说明</span><span class="sxs-lookup"><span data-stu-id="a2c7a-116">Description</span></span>|  
|-------------|-----------------|  
|`1050`|<span data-ttu-id="a2c7a-117">此值在脚本或工具中不可见，但它对应于 [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]、 [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]或 [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)]中创建的数据库。</span><span class="sxs-lookup"><span data-stu-id="a2c7a-117">This value is not visible in script or tools, but it corresponds to databases created in [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)], [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)], or [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)].</span></span> <span data-ttu-id="a2c7a-118">对于任何没有显式设置 `CompatibilityLevel` 的数据库，都将在 `1050` 级别隐式运行。</span><span class="sxs-lookup"><span data-stu-id="a2c7a-118">Any database that does not have `CompatibilityLevel` explicitly set is implicitly running at the `1050` level.</span></span>|  
|`1100`|<span data-ttu-id="a2c7a-119">这是在 [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] 或 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]中创建的新数据库的默认值。</span><span class="sxs-lookup"><span data-stu-id="a2c7a-119">This is the default value for new databases that you create in [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] or [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].</span></span> <span data-ttu-id="a2c7a-120">您还可以为在 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 的早期版本中创建的数据库指定该值，以便使用仅在此兼容级别支持的功能（也就是说，增大了用于包含字符串数据的维度属性或非重复计数度量值的字符串存储空间）。</span><span class="sxs-lookup"><span data-stu-id="a2c7a-120">You can also specify it for databases created in earlier versions of [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] to enable the use of features that are supported only at this compatibility level (namely, increased string storage for dimension attributes or distinct count measures that contain string data).</span></span><br /><br /> <span data-ttu-id="a2c7a-121">`CompatibilityLevel`如果数据库设置为 `1100` 获取附加属性， `StringStoresCompatibilityLevel` 则可以为分区和维度选择其他字符串存储。</span><span class="sxs-lookup"><span data-stu-id="a2c7a-121">Databases that have a `CompatibilityLevel` set to `1100` get an additional property, `StringStoresCompatibilityLevel`, that lets you choose alternative string storage for partitions and dimensions.</span></span>|  
  
> [!WARNING]  
>  <span data-ttu-id="a2c7a-122">将数据库兼容级别设置为更高级别是不可逆的。</span><span class="sxs-lookup"><span data-stu-id="a2c7a-122">Setting the database compatibility to a higher level is irreversible.</span></span> <span data-ttu-id="a2c7a-123">将兼容级别提高到后 `1100` ，必须继续在更高版本的服务器上运行数据库。</span><span class="sxs-lookup"><span data-stu-id="a2c7a-123">After you increase the compatibility level to `1100`, you must continue to run the database on newer servers.</span></span> <span data-ttu-id="a2c7a-124">不能回滚到 `1050` 。</span><span class="sxs-lookup"><span data-stu-id="a2c7a-124">You cannot rollback to `1050`.</span></span> <span data-ttu-id="a2c7a-125">不能 `1100` 在早于或的服务器版本上附加或还原数据库 [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="a2c7a-125">You cannot attach or restore an `1100` database on a server version that is earlier than [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] or [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="a2c7a-126">先决条件</span><span class="sxs-lookup"><span data-stu-id="a2c7a-126">Prerequisites</span></span>  
 <span data-ttu-id="a2c7a-127">在 [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]中引入数据库兼容级别。</span><span class="sxs-lookup"><span data-stu-id="a2c7a-127">Database compatibility levels are introduced in [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)].</span></span> <span data-ttu-id="a2c7a-128">你必须具有 [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)][!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 或更高版本才能查看或设置数据库兼容级别。</span><span class="sxs-lookup"><span data-stu-id="a2c7a-128">You must have [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)][!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] or higher to view or set the database compatibility level.</span></span>  
  
 <span data-ttu-id="a2c7a-129">数据库不能为本地多维数据集。</span><span class="sxs-lookup"><span data-stu-id="a2c7a-129">The database cannot be a local cube.</span></span> <span data-ttu-id="a2c7a-130">本地多维数据集不支持 `CompatibilityLevel` 属性。</span><span class="sxs-lookup"><span data-stu-id="a2c7a-130">Local cubes do not support the `CompatibilityLevel` property.</span></span>  
  
 <span data-ttu-id="a2c7a-131">该数据库必须已在以前的版本（SQL Server 2008 R2 或更早版本）中创建，然后附加或还原到 [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)][!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 或更高版本的服务器。</span><span class="sxs-lookup"><span data-stu-id="a2c7a-131">The database must have been created in a previous release (SQL Server 2008 R2 or earlier) and then attached or restored to a [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)][!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] or higher server.</span></span> <span data-ttu-id="a2c7a-132">部署到 SQL Server 2012 的数据库已在 `1100` 级别，无法降级到更低级别。</span><span class="sxs-lookup"><span data-stu-id="a2c7a-132">Databases deployed to SQL Server 2012 are already at `1100` and cannot be downgraded to run at a lower level.</span></span>  
  
## <a name="determine-the-existing-database-compatibility-level-for-a-multidimensional-database"></a><span data-ttu-id="a2c7a-133">确定多维数据库的现有数据库兼容级别</span><span class="sxs-lookup"><span data-stu-id="a2c7a-133">Determine the existing database compatibility level for a multidimensional database</span></span>  
 <span data-ttu-id="a2c7a-134">查看或修改数据库兼容级别的唯一方法就是通过 XMLA。</span><span class="sxs-lookup"><span data-stu-id="a2c7a-134">The only way to view or modify the database compatibility level is through XMLA.</span></span> <span data-ttu-id="a2c7a-135">您可以在 SQL Server Management Studio 中查看或修改指定您的数据库的 XMLA 脚本。</span><span class="sxs-lookup"><span data-stu-id="a2c7a-135">You can view or modify the XMLA script that specifies your database in SQL Server Management Studio.</span></span>  
  
 <span data-ttu-id="a2c7a-136">如果在数据库的 XMLA 定义中搜索属性 `CompatibilityLevel`，没有任何结果，则该数据库很可能已位于 `1050` 级别。</span><span class="sxs-lookup"><span data-stu-id="a2c7a-136">If you search the XMLA definition of a database for the property `CompatibilityLevel` and it does not exist, you most likely have a database at the `1050` level.</span></span>  
  
 <span data-ttu-id="a2c7a-137">下一节中提供了有关查看和修改 XMLA 脚本的说明。</span><span class="sxs-lookup"><span data-stu-id="a2c7a-137">Instructions for viewing and modifying the XMLA script are provided in the next section.</span></span>  
  
## <a name="set-the-database-compatibility-level-in-sql-server-management-studio"></a><span data-ttu-id="a2c7a-138">在 SQL Server Management Studio 中设置数据库兼容级别</span><span class="sxs-lookup"><span data-stu-id="a2c7a-138">Set the database compatibility level in SQL Server Management Studio</span></span>  
  
1.  <span data-ttu-id="a2c7a-139">在提高兼容级别之前，请备份该数据库，以备稍后您要撤消更改。</span><span class="sxs-lookup"><span data-stu-id="a2c7a-139">Before raising the compatibility level, backup the database in case you want to reverse your changes later.</span></span>  
  
2.  <span data-ttu-id="a2c7a-140">使用 SQL Server Management Studio，连接到承载数据库的 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)][!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 服务器。</span><span class="sxs-lookup"><span data-stu-id="a2c7a-140">Using SQL Server Management Studio, connect to the [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)][!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] server that hosts the database.</span></span>  
  
3.  <span data-ttu-id="a2c7a-141">右键单击数据库名称，指向“编写数据库脚本为”\*\*\*\*，指向“ALTER to”\*\*\*\*，然后选择“新查询编辑器窗口”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="a2c7a-141">Right-click the database name, point to **Script Database as**, point to **ALTER to**, and then select **New Query Editor Window**.</span></span> <span data-ttu-id="a2c7a-142">数据库的 XMLA 表示形式将在新窗口中打开。</span><span class="sxs-lookup"><span data-stu-id="a2c7a-142">An XMLA representation of the database will open in a new window.</span></span>  
  
4.  <span data-ttu-id="a2c7a-143">复制以下 XML 元素：</span><span class="sxs-lookup"><span data-stu-id="a2c7a-143">Copy the following XML element:</span></span>  
  
    ```  
    <ddl200:CompatibilityLevel>1100</ddl200:CompatibilityLevel>  
    ```  
  
5.  <span data-ttu-id="a2c7a-144">将其粘贴到 `</Annotations>` 结尾元素之后、 `<Language>` 元素之前。</span><span class="sxs-lookup"><span data-stu-id="a2c7a-144">Paste it after the `</Annotations>` closing element and before the `<Language>` element.</span></span> <span data-ttu-id="a2c7a-145">XML 应类似以下示例：</span><span class="sxs-lookup"><span data-stu-id="a2c7a-145">The XML should look similar to the following example:</span></span>  
  
    ```  
    </Annotations>  
    <ddl200:CompatibilityLevel>1100</ddl200:CompatibilityLevel>  
    <Language>1033</Language>  
    ```  
  
6.  <span data-ttu-id="a2c7a-146">保存文件。</span><span class="sxs-lookup"><span data-stu-id="a2c7a-146">Save the file.</span></span>  
  
7.  <span data-ttu-id="a2c7a-147">若要运行脚本，请在“查询”菜单上单击 **“执行”** ，或按 F5。</span><span class="sxs-lookup"><span data-stu-id="a2c7a-147">To run the script, click **Execute** on the Query menu or press F5.</span></span>  
  
## <a name="supported-operations-that-require-the-same-compatibility-level"></a><span data-ttu-id="a2c7a-148">要求相同兼容级别的支持的操作</span><span class="sxs-lookup"><span data-stu-id="a2c7a-148">Supported Operations that Require the Same Compatibility Level</span></span>  
 <span data-ttu-id="a2c7a-149">以下操作要求源数据库共享相同的兼容级别。</span><span class="sxs-lookup"><span data-stu-id="a2c7a-149">The following operations require that the source databases share the same compatibility level.</span></span>  
  
1.  <span data-ttu-id="a2c7a-150">只有在两个不同的数据库共享相同的兼容级别时，才支持从这两个不同的数据库合并分区。</span><span class="sxs-lookup"><span data-stu-id="a2c7a-150">Merging partitions from different databases is supported only if both databases share the same compatibility level.</span></span>  
  
2.  <span data-ttu-id="a2c7a-151">使用来自其他数据库的链接维度要求相同的兼容级别。</span><span class="sxs-lookup"><span data-stu-id="a2c7a-151">Using linked dimensions from another database requires the same compatibility level.</span></span> <span data-ttu-id="a2c7a-152">例如，如果要使用数据库中的数据库的链接维度 [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] ，则必须将 [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] 数据库移植到 [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] 服务器，并将兼容级别设置为 `1100` 。</span><span class="sxs-lookup"><span data-stu-id="a2c7a-152">For example, if you want to use a linked dimension from a [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] database in a [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] database, you must port the [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] database to a [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] server and set the compatibility level to `1100`.</span></span>  
  
3.  <span data-ttu-id="a2c7a-153">仅对于共享相同版本和数据库兼容级别的服务器，才支持同步服务器。</span><span class="sxs-lookup"><span data-stu-id="a2c7a-153">Synchronizing servers is only supported for servers that share the same version and database compatibility level.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="a2c7a-154">后续步骤</span><span class="sxs-lookup"><span data-stu-id="a2c7a-154">Next Steps</span></span>  
 <span data-ttu-id="a2c7a-155">在增加了数据库兼容级别之后，可以在 [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)] 中设置 `StringStoresCompatibilityLevel` 属性。</span><span class="sxs-lookup"><span data-stu-id="a2c7a-155">After you increase the database compatibility level, you can set the `StringStoresCompatibilityLevel` property in [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)].</span></span> <span data-ttu-id="a2c7a-156">这样将增大度量值和维度的字符串存储空间。</span><span class="sxs-lookup"><span data-stu-id="a2c7a-156">This increases string storage for measures and dimensions.</span></span> <span data-ttu-id="a2c7a-157">有关此功能的详细信息，请参阅 [配置维度和分区的字符串存储](configure-string-storage-for-dimensions-and-partitions.md)。</span><span class="sxs-lookup"><span data-stu-id="a2c7a-157">For more information about this feature, see [Configure String Storage for Dimensions and Partitions](configure-string-storage-for-dimensions-and-partitions.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a2c7a-158">另请参阅</span><span class="sxs-lookup"><span data-stu-id="a2c7a-158">See Also</span></span>  
 [<span data-ttu-id="a2c7a-159">备份、还原和同步数据库 (XMLA)</span><span class="sxs-lookup"><span data-stu-id="a2c7a-159">Backing Up, Restoring, and Synchronizing Databases &#40;XMLA&#41;</span></span>](../multidimensional-models-scripting-language-assl-xmla/backing-up-restoring-and-synchronizing-databases-xmla.md)  
  
  
