---
title: 查找转换 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.lookuptrans.f1
helpviewer_keywords:
- Lookup transformation
- joining columns [Integration Services]
- cache [Integration Services]
- match exactly [Integration Services]
- lookups [Integration Services]
- exact matches [Integration Services]
ms.assetid: de1cc8de-e7af-4727-b5a5-a1f0a739aa09
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 567c5d95c2ee7c15ea5c541f7fe2010d46ba36f5
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87589793"
---
# <a name="lookup-transformation"></a><span data-ttu-id="57dec-102">查找转换</span><span class="sxs-lookup"><span data-stu-id="57dec-102">Lookup Transformation</span></span>
  <span data-ttu-id="57dec-103">查找转换通过联接输入列中的数据和引用数据集中的列来执行查找。</span><span class="sxs-lookup"><span data-stu-id="57dec-103">The Lookup transformation performs lookups by joining data in input columns with columns in a reference dataset.</span></span> <span data-ttu-id="57dec-104">可以使用该查找在基于通用列的值的相关表中访问其他信息。</span><span class="sxs-lookup"><span data-stu-id="57dec-104">You use the lookup to access additional information in a related table that is based on values in common columns.</span></span>  
  
 <span data-ttu-id="57dec-105">引用数据集可以是缓存文件、现有的表或视图、新表或 SQL 查询的结果。</span><span class="sxs-lookup"><span data-stu-id="57dec-105">The reference dataset can be a cache file, an existing table or view, a new table, or the result of an SQL query.</span></span> <span data-ttu-id="57dec-106">查找转换使用 OLE DB 连接管理器或缓存连接管理器来连接到引用数据集。</span><span class="sxs-lookup"><span data-stu-id="57dec-106">The Lookup transformation uses either an OLE DB connection manager or a Cache connection manager to connect to the reference dataset.</span></span> <span data-ttu-id="57dec-107">有关详细信息，请参阅 [OLE DB 连接管理器](../../connection-manager/ole-db-connection-manager.md) 和 [缓存连接管理器](../../connection-manager/cache-connection-manager.md)。</span><span class="sxs-lookup"><span data-stu-id="57dec-107">For more information, see [OLE DB Connection Manager](../../connection-manager/ole-db-connection-manager.md) and [Cache Connection Manager](../../connection-manager/cache-connection-manager.md)</span></span>  
  
 <span data-ttu-id="57dec-108">可以用以下方式来配置查找转换：</span><span class="sxs-lookup"><span data-stu-id="57dec-108">You can configure the Lookup transformation in the following ways:</span></span>  
  
-   <span data-ttu-id="57dec-109">选择要使用的连接管理器。</span><span class="sxs-lookup"><span data-stu-id="57dec-109">Select the connection manager that you want to use.</span></span> <span data-ttu-id="57dec-110">如果要连接到数据库，请选择 OLE DB 连接管理器。</span><span class="sxs-lookup"><span data-stu-id="57dec-110">If you want to connect to a database, select an OLE DB connection manager.</span></span> <span data-ttu-id="57dec-111">如果要连接到缓存文件，请选择缓存连接管理器。</span><span class="sxs-lookup"><span data-stu-id="57dec-111">If you want to connect to a cache file, select a Cache connection manager.</span></span>  
  
-   <span data-ttu-id="57dec-112">指定包含引用数据集的表或视图。</span><span class="sxs-lookup"><span data-stu-id="57dec-112">Specify the table or view that contains the reference dataset.</span></span>  
  
-   <span data-ttu-id="57dec-113">通过指定 SQL 语句来生成引用数据集。</span><span class="sxs-lookup"><span data-stu-id="57dec-113">Generate a reference dataset by specifying an SQL statement.</span></span>  
  
-   <span data-ttu-id="57dec-114">指定输入和引用数据集间的联接。</span><span class="sxs-lookup"><span data-stu-id="57dec-114">Specify joins between the input and the reference dataset.</span></span>  
  
-   <span data-ttu-id="57dec-115">将引用数据集的列添加到查找转换输出中。</span><span class="sxs-lookup"><span data-stu-id="57dec-115">Add columns from the reference dataset to the Lookup transformation output.</span></span>  
  
-   <span data-ttu-id="57dec-116">配置缓存选项。</span><span class="sxs-lookup"><span data-stu-id="57dec-116">Configure the caching options.</span></span>  
  
 <span data-ttu-id="57dec-117">查找转换支持适用于 OLE DB 连接管理器的以下数据库访问接口：</span><span class="sxs-lookup"><span data-stu-id="57dec-117">The Lookup transformation supports the following database providers for the OLE DB connection manager:</span></span>  
  
-   [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]  
  
-   <span data-ttu-id="57dec-118">Oracle</span><span class="sxs-lookup"><span data-stu-id="57dec-118">Oracle</span></span>  
  
-   <span data-ttu-id="57dec-119">DB2</span><span class="sxs-lookup"><span data-stu-id="57dec-119">DB2</span></span>  
  
 <span data-ttu-id="57dec-120">查找转换试图在转换输入的值和引用数据集的值之间执行同等联接。</span><span class="sxs-lookup"><span data-stu-id="57dec-120">The Lookup transformation tries to perform an equi-join between values in the transformation input and values in the reference dataset.</span></span> <span data-ttu-id="57dec-121">（同等联接意味着转换输入中的每一行都至少要与引用数据集中的一行匹配。）如果无法实现同等联接，则查找转换会执行下列操作之一：</span><span class="sxs-lookup"><span data-stu-id="57dec-121">(An equi-join means that each row in the transformation input must match at least one row from the reference dataset.) If an equi-join is not possible, the Lookup transformation takes one of the following actions:</span></span>  
  
-   <span data-ttu-id="57dec-122">如果引用数据集中没有匹配项，则不会发生联接。</span><span class="sxs-lookup"><span data-stu-id="57dec-122">If there is no matching entry in the reference dataset, no join occurs.</span></span> <span data-ttu-id="57dec-123">默认情况下，查找转换将没有匹配项的行视为错误。</span><span class="sxs-lookup"><span data-stu-id="57dec-123">By default, the Lookup transformation treats rows without matching entries as errors.</span></span> <span data-ttu-id="57dec-124">但是，您可以将查找转换配置为将这些行重定向到无匹配输出。</span><span class="sxs-lookup"><span data-stu-id="57dec-124">However, you can configure the Lookup transformation to redirect such rows to a no match output.</span></span> <span data-ttu-id="57dec-125">有关详细信息，请参阅[查找转换编辑器（“常规”页）](../../lookup-transformation-editor-general-page.md)和[查找转换编辑器（“错误输出”页）](../../lookup-transformation-editor-error-output-page.md)。</span><span class="sxs-lookup"><span data-stu-id="57dec-125">For more information, see [Lookup Transformation Editor &#40;General Page&#41;](../../lookup-transformation-editor-general-page.md) and [Lookup Transformation Editor &#40;Error Output Page&#41;](../../lookup-transformation-editor-error-output-page.md).</span></span>  
  
-   <span data-ttu-id="57dec-126">如果引用表中有多个匹配项，则查找转换只返回查找查询返回的第一个匹配项。</span><span class="sxs-lookup"><span data-stu-id="57dec-126">If there are multiple matches in the reference table, the Lookup transformation returns only the first match returned by the lookup query.</span></span> <span data-ttu-id="57dec-127">如果发现多个匹配项，则仅当转换被配置为将所有引用数据集加载到缓存中时查找转换才生成错误或警告。</span><span class="sxs-lookup"><span data-stu-id="57dec-127">If multiple matches are found, the Lookup transformation generates an error or warning only when the transformation has been configured to load all the reference dataset into the cache.</span></span> <span data-ttu-id="57dec-128">在这种情况下，如果查找转换在填充缓存时检测到多个匹配项，则该查找转换将生成警告。</span><span class="sxs-lookup"><span data-stu-id="57dec-128">In this case, the Lookup transformation generates a warning when the transformation detects multiple matches as the transformation fills the cache.</span></span>  
  
 <span data-ttu-id="57dec-129">联接可以是组合联接，即可以将转换输入中的多个列联接到引用数据集中的列。</span><span class="sxs-lookup"><span data-stu-id="57dec-129">The join can be a composite join, which means that you can join multiple columns in the transformation input to columns in the reference dataset.</span></span> <span data-ttu-id="57dec-130">除了 DT_R4、DT_R8、DT_TEXT、DT_NTEXT 或 DT_IMAGE 外，转换支持联接其他任何数据类型的列。</span><span class="sxs-lookup"><span data-stu-id="57dec-130">The transformation supports join columns with any data type, except for DT_R4, DT_R8, DT_TEXT, DT_NTEXT, or DT_IMAGE.</span></span> <span data-ttu-id="57dec-131">有关详细信息，请参阅 [Integration Services 数据类型](../integration-services-data-types.md)。</span><span class="sxs-lookup"><span data-stu-id="57dec-131">For more information, see [Integration Services Data Types](../integration-services-data-types.md).</span></span>  
  
 <span data-ttu-id="57dec-132">通常，将来自引用数据集的值添加到转换输出中。</span><span class="sxs-lookup"><span data-stu-id="57dec-132">Typically, values from the reference dataset are added to the transformation output.</span></span> <span data-ttu-id="57dec-133">例如，查找转换可以使用输入列的值从表中提取产品名，然后将产品名添加到转换输出中。</span><span class="sxs-lookup"><span data-stu-id="57dec-133">For example, the Lookup transformation can extract a product name from a table using a value from an input column, and then add the product name to the transformation output.</span></span> <span data-ttu-id="57dec-134">来自引用表的值可以替换列值，也可以添加到新列中。</span><span class="sxs-lookup"><span data-stu-id="57dec-134">The values from the reference table can replace column values or can be added to new columns.</span></span>  
  
 <span data-ttu-id="57dec-135">查找转换执行的查找区分大小写。</span><span class="sxs-lookup"><span data-stu-id="57dec-135">The lookups performed by the Lookup transformation are case sensitive.</span></span> <span data-ttu-id="57dec-136">因此，为了避免因数据中大小写不同而导致查找失败，首先请使用字符映射转换将数据转换为大写或小写。</span><span class="sxs-lookup"><span data-stu-id="57dec-136">To avoid lookup failures that are caused by case differences in data, first use the Character Map transformation to convert the data to uppercase or lowercase.</span></span> <span data-ttu-id="57dec-137">然后在生成引用表的 SQL 语句中包含 UPPER 或 LOWER 函数。</span><span class="sxs-lookup"><span data-stu-id="57dec-137">Then, include the UPPER or LOWER functions in the SQL statement that generates the reference table.</span></span> <span data-ttu-id="57dec-138">有关详细信息，请参阅[字符映射表转换](character-map-transformation.md)、[UPPER (Transact-SQL)](/sql/t-sql/functions/upper-transact-sql) 和 [LOWER (Transact-SQL)](/sql/t-sql/functions/lower-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="57dec-138">For more information, see [Character Map Transformation](character-map-transformation.md), [UPPER &#40;Transact-SQL&#41;](/sql/t-sql/functions/upper-transact-sql), and [LOWER &#40;Transact-SQL&#41;](/sql/t-sql/functions/lower-transact-sql).</span></span>  
  
 <span data-ttu-id="57dec-139">查找转换具有以下输入和输出：</span><span class="sxs-lookup"><span data-stu-id="57dec-139">The Lookup transformation has the following inputs and outputs:</span></span>  
  
-   <span data-ttu-id="57dec-140">输入。</span><span class="sxs-lookup"><span data-stu-id="57dec-140">Input.</span></span>  
  
-   <span data-ttu-id="57dec-141">匹配输出。</span><span class="sxs-lookup"><span data-stu-id="57dec-141">Match output.</span></span> <span data-ttu-id="57dec-142">匹配输出处理转换输入中那些在引用数据集内至少有一个匹配项的行。</span><span class="sxs-lookup"><span data-stu-id="57dec-142">The match output handles the rows in the transformation input that match at least one entry in the reference dataset.</span></span>  
  
-   <span data-ttu-id="57dec-143">无匹配输出。</span><span class="sxs-lookup"><span data-stu-id="57dec-143">No Match output.</span></span> <span data-ttu-id="57dec-144">无匹配输出处理输入中在引用数据集内没有任何匹配项的行。</span><span class="sxs-lookup"><span data-stu-id="57dec-144">The no match output handles rows in the input that do not match at least one entry in the reference dataset.</span></span> <span data-ttu-id="57dec-145">如果将查找转换配置为将无匹配项的行视为错误，则这些行会重定向到错误输出。</span><span class="sxs-lookup"><span data-stu-id="57dec-145">If you configure the Lookup transformation to treat the rows without matching entries as errors, the rows are redirected to the error output.</span></span> <span data-ttu-id="57dec-146">否则，转换会将这些行重定向到无匹配输出。</span><span class="sxs-lookup"><span data-stu-id="57dec-146">Otherwise, the transformation would redirect those rows to the no match output.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="57dec-147">在 [!INCLUDE[ssISversion2005](../../../includes/ssisversion2005-md.md)] 中，查找转换只有一个输出。</span><span class="sxs-lookup"><span data-stu-id="57dec-147">In [!INCLUDE[ssISversion2005](../../../includes/ssisversion2005-md.md)], the Lookup transformation had only one output.</span></span> <span data-ttu-id="57dec-148">有关如何运行在中创建的查找转换的详细信息 [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] ，请参阅[升级查找转换](../../../sql-server/install/upgrade-lookup-transformations.md)。</span><span class="sxs-lookup"><span data-stu-id="57dec-148">For more information about how to run a Lookup transformation that was created in [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)], see [Upgrade Lookup Transformations](../../../sql-server/install/upgrade-lookup-transformations.md).</span></span>  
  
-   <span data-ttu-id="57dec-149">错误输出。</span><span class="sxs-lookup"><span data-stu-id="57dec-149">Error output.</span></span>  
  
## <a name="caching-the-reference-dataset"></a><span data-ttu-id="57dec-150">缓存引用数据集</span><span class="sxs-lookup"><span data-stu-id="57dec-150">Caching the Reference Dataset</span></span>  
 <span data-ttu-id="57dec-151">内存缓存存储引用数据集以及为数据创建索引的哈希表。</span><span class="sxs-lookup"><span data-stu-id="57dec-151">An in-memory cache stores the reference dataset and stores a hash table that indexes the data.</span></span> <span data-ttu-id="57dec-152">缓存保留在内存中，直到包执行完成。</span><span class="sxs-lookup"><span data-stu-id="57dec-152">The cache remains in memory until the execution of the package is completed.</span></span> <span data-ttu-id="57dec-153">您可以将缓存保留到缓存文件中 (.caw)。</span><span class="sxs-lookup"><span data-stu-id="57dec-153">You can persist the cache to a cache file (.caw).</span></span>  
  
 <span data-ttu-id="57dec-154">将缓存保留到文件中时，系统加载缓存的速度会更快。</span><span class="sxs-lookup"><span data-stu-id="57dec-154">When you persist the cache to a file, the system loads the cache faster.</span></span> <span data-ttu-id="57dec-155">这可以提高查找转换和包的性能。</span><span class="sxs-lookup"><span data-stu-id="57dec-155">This improves the performance of the Lookup transformation and the package.</span></span> <span data-ttu-id="57dec-156">请注意，使用缓存文件时，您使用的数据不如数据库中的数据新。</span><span class="sxs-lookup"><span data-stu-id="57dec-156">Remember, that when you use a cache file, you are working with data that is not as current as the data in the database.</span></span>  
  
 <span data-ttu-id="57dec-157">下面是将缓存保留到文件中的其他好处：</span><span class="sxs-lookup"><span data-stu-id="57dec-157">The following are additional benefits of persisting the cache to a file:</span></span>  
  
-   <span data-ttu-id="57dec-158">***在多个包之间共享缓存文件。有关详细信息，请参阅***  [在完全缓存模式下使用缓存连接管理器实现查找转换](../../connection-manager/lookup-transformation-full-cache-mode-cache-connection-manager.md)  ***。***</span><span class="sxs-lookup"><span data-stu-id="57dec-158">***Share the cache file between multiple packages. For more information, see***  [Implement a Lookup Transformation in Full Cache Mode Using the Cache Connection Manager](../../connection-manager/lookup-transformation-full-cache-mode-cache-connection-manager.md)  ***.***</span></span>  
  
-   <span data-ttu-id="57dec-159">使用包部署缓存文件。</span><span class="sxs-lookup"><span data-stu-id="57dec-159">Deploy the cache file with a package.</span></span> <span data-ttu-id="57dec-160">***随后即可在多台计算机上使用该数据。***</span><span class="sxs-lookup"><span data-stu-id="57dec-160">***You can then use the data on multiple computers.***</span></span> <span data-ttu-id="57dec-161">有关详细信息，请参阅 [为查找转换创建和部署缓存](create-and-deploy-a-cache-for-the-lookup-transformation.md)。</span><span class="sxs-lookup"><span data-stu-id="57dec-161">For more information, see [Create and Deploy a Cache for the Lookup Transformation](create-and-deploy-a-cache-for-the-lookup-transformation.md).</span></span>  
  
-   <span data-ttu-id="57dec-162">使用原始文件源从缓存文件中读取数据。</span><span class="sxs-lookup"><span data-stu-id="57dec-162">Use the Raw File source to read data from the cache file.</span></span> <span data-ttu-id="57dec-163">随后即可使用其他数据流组件来转换或移动数据。</span><span class="sxs-lookup"><span data-stu-id="57dec-163">You can then use other data flow components to transform or move the data.</span></span> <span data-ttu-id="57dec-164">有关详细信息，请参阅 [Raw File Source](../raw-file-source.md)。</span><span class="sxs-lookup"><span data-stu-id="57dec-164">For more information, see [Raw File Source](../raw-file-source.md).</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="57dec-165">缓存连接管理器不支持使用原始文件目标创建或修改的缓存文件。</span><span class="sxs-lookup"><span data-stu-id="57dec-165">The Cache connection manager does not support cache files that are created or modified by using the Raw File destination.</span></span>  
  
-   <span data-ttu-id="57dec-166">通过使用文件系统任务对缓存文件执行操作和设置属性。</span><span class="sxs-lookup"><span data-stu-id="57dec-166">Perform operations and set attributes on the cache file by using the File System task.</span></span> <span data-ttu-id="57dec-167">有关详细信息，请参阅 [File System Task](../../control-flow/file-system-task.md)。</span><span class="sxs-lookup"><span data-stu-id="57dec-167">For more information, see and [File System Task](../../control-flow/file-system-task.md).</span></span>  
  
 <span data-ttu-id="57dec-168">下面列出了各种缓存选项：</span><span class="sxs-lookup"><span data-stu-id="57dec-168">The following are the caching options:</span></span>  
  
-   <span data-ttu-id="57dec-169">在查找转换运行之前，通过使用表、视图或 SQL 查询生成引用数据集并将该引用数据集加载到缓存中。</span><span class="sxs-lookup"><span data-stu-id="57dec-169">The reference dataset is generated by using a table, view, or SQL query and loaded into cache, before the Lookup transformation runs.</span></span> <span data-ttu-id="57dec-170">您可以使用 OLE DB 连接管理器访问该数据集。</span><span class="sxs-lookup"><span data-stu-id="57dec-170">You use the OLE DB connection manager to access the dataset.</span></span>  
  
     <span data-ttu-id="57dec-171">此缓存选项与 [!INCLUDE[ssISversion2005](../../../includes/ssisversion2005-md.md)]中查找转换的完全缓存选项兼容。</span><span class="sxs-lookup"><span data-stu-id="57dec-171">This caching option is compatible with the full caching option that is available for the Lookup transformation in [!INCLUDE[ssISversion2005](../../../includes/ssisversion2005-md.md)].</span></span>  
  
-   <span data-ttu-id="57dec-172">在查找转换运行之前，从数据流中的已连接数据源或从缓存文件生成引用数据集并将该引用数据集加载到缓存中。</span><span class="sxs-lookup"><span data-stu-id="57dec-172">The reference dataset is generated from a connected data source in the data flow or from a cache file, and is loaded into cache before the Lookup transformation runs.</span></span> <span data-ttu-id="57dec-173">您可以使用缓存连接管理器并根据需要使用缓存转换来访问该数据集。</span><span class="sxs-lookup"><span data-stu-id="57dec-173">You use the Cache connection manager, and, optionally, the Cache transformation, to access the dataset.</span></span> <span data-ttu-id="57dec-174">有关详细信息，请参阅 [缓存连接管理器](../../connection-manager/cache-connection-manager.md) 和 [缓存转换](cache-transform.md)。</span><span class="sxs-lookup"><span data-stu-id="57dec-174">For more information, see [Cache Connection Manager](../../connection-manager/cache-connection-manager.md) and [Cache Transform](cache-transform.md).</span></span>  
  
-   <span data-ttu-id="57dec-175">在执行查找转换过程中，通过使用表、视图或 SQL 查询生成引用数据集。</span><span class="sxs-lookup"><span data-stu-id="57dec-175">The reference dataset is generated by using a table, view, or SQL query during the execution of the Lookup transformation.</span></span> <span data-ttu-id="57dec-176">在引用数据集中有匹配项的行以及在该数据集中没有匹配项的行都会加载到缓存中。</span><span class="sxs-lookup"><span data-stu-id="57dec-176">The rows with matching entries in the reference dataset and the rows without matching entries in the dataset are loaded into cache.</span></span>  
  
     <span data-ttu-id="57dec-177">超出缓存的内存大小后，查找转换会自动从缓存中删除最不常使用的行。</span><span class="sxs-lookup"><span data-stu-id="57dec-177">When the memory size of the cache is exceeded, the Lookup transformation automatically removes the least frequently used rows from the cache.</span></span>  
  
     <span data-ttu-id="57dec-178">此缓存选项与适用于 [!INCLUDE[ssISversion2005](../../../includes/ssisversion2005-md.md)]中的查找转换的部分缓存选项兼容。</span><span class="sxs-lookup"><span data-stu-id="57dec-178">This caching option is compatible with the partial caching option that is available for the Lookup transformation in [!INCLUDE[ssISversion2005](../../../includes/ssisversion2005-md.md)].</span></span>  
  
-   <span data-ttu-id="57dec-179">在执行查找转换过程中，通过使用表、视图或 SQL 查询生成引用数据集。</span><span class="sxs-lookup"><span data-stu-id="57dec-179">The reference dataset is generated by using a table, view, or SQL query during the execution of the Lookup transformation.</span></span> <span data-ttu-id="57dec-180">没有缓存数据。</span><span class="sxs-lookup"><span data-stu-id="57dec-180">No data is cached.</span></span>  
  
     <span data-ttu-id="57dec-181">此缓存选项与 [!INCLUDE[ssISversion2005](../../../includes/ssisversion2005-md.md)]中查找转换的无缓存选项兼容。</span><span class="sxs-lookup"><span data-stu-id="57dec-181">This caching option is compatible with the no caching option that is available for the Lookup transformation in [!INCLUDE[ssISversion2005](../../../includes/ssisversion2005-md.md)].</span></span>  
  
 [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] <span data-ttu-id="57dec-182">和 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 在比较字符串时所用的方式不同。</span><span class="sxs-lookup"><span data-stu-id="57dec-182">and [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] differ in the way they compare strings.</span></span> <span data-ttu-id="57dec-183">如果查找转换配置为在查找转换运行之前将引用数据集加载到缓存中，则 [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] 将在缓存中执行查找比较。</span><span class="sxs-lookup"><span data-stu-id="57dec-183">If the Lookup transformation is configured to load the reference dataset into cache before the Lookup transformation runs, [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] does the lookup comparison in the cache.</span></span> <span data-ttu-id="57dec-184">否则，查找操作将使用参数化 SQL 语句并且 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 将执行查找比较。</span><span class="sxs-lookup"><span data-stu-id="57dec-184">Otherwise, the lookup operation uses a parameterized SQL statement and [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] does the lookup comparison.</span></span> <span data-ttu-id="57dec-185">这意味着，根据缓存类型的不同，查找转换可能会从同一查找表中返回不同数量的匹配项。</span><span class="sxs-lookup"><span data-stu-id="57dec-185">This means that the Lookup transformation might return a different number of matches from the same lookup table depending on the cache type.</span></span>  
  
## <a name="related-tasks"></a><span data-ttu-id="57dec-186">Related Tasks</span><span class="sxs-lookup"><span data-stu-id="57dec-186">Related Tasks</span></span>  
 <span data-ttu-id="57dec-187">可以通过 [!INCLUDE[ssIS](../../../includes/ssis-md.md)] 设计器或以编程方式来设置属性。</span><span class="sxs-lookup"><span data-stu-id="57dec-187">You can set properties through [!INCLUDE[ssIS](../../../includes/ssis-md.md)] Designer or programmatically.</span></span> <span data-ttu-id="57dec-188">有关详细信息，请参阅以下主题：</span><span class="sxs-lookup"><span data-stu-id="57dec-188">For more details, see the following topics.</span></span>  
  
-   [<span data-ttu-id="57dec-189">在不缓存模式或部分缓存模式下实现查找</span><span class="sxs-lookup"><span data-stu-id="57dec-189">Implement a Lookup in No Cache or Partial Cache Mode</span></span>](implement-a-lookup-in-no-cache-or-partial-cache-mode.md)  
  
-   [<span data-ttu-id="57dec-190">在完全缓存模式下使用缓存连接管理器实现查找转换</span><span class="sxs-lookup"><span data-stu-id="57dec-190">Implement a Lookup Transformation in Full Cache Mode Using the Cache Connection Manager</span></span>](../../connection-manager/lookup-transformation-full-cache-mode-cache-connection-manager.md)  
  
-   [<span data-ttu-id="57dec-191">在完全缓存模式下使用 OLE DB 连接管理器来实现查找转换</span><span class="sxs-lookup"><span data-stu-id="57dec-191">Implement a Lookup Transformation in Full Cache Mode Using the OLE DB Connection Manager</span></span>](../../connection-manager/lookup-transformation-full-cache-mode-ole-db-connection-manager.md)  
  
-   [<span data-ttu-id="57dec-192">设置数据流组件的属性</span><span class="sxs-lookup"><span data-stu-id="57dec-192">Set the Properties of a Data Flow Component</span></span>](../set-the-properties-of-a-data-flow-component.md)  
  
## <a name="related-content"></a><span data-ttu-id="57dec-193">相关内容</span><span class="sxs-lookup"><span data-stu-id="57dec-193">Related Content</span></span>  
  
-   <span data-ttu-id="57dec-194">msdn.microsoft.com 上的视频 [How to: Implement a Lookup Transformation in Full Cache Mode](https://go.microsoft.com/fwlink/?LinkId=131031)（如何在完全缓存模式下实现查找转换）</span><span class="sxs-lookup"><span data-stu-id="57dec-194">Video, [How to: Implement a Lookup Transformation in Full Cache Mode](https://go.microsoft.com/fwlink/?LinkId=131031), on msdn.microsoft.com</span></span>  
  
-   <span data-ttu-id="57dec-195">blogs.msdn.com 上的博客项 [Best Practices for Using the Lookup Transformation Cache Modes](https://go.microsoft.com/fwlink/?LinkId=146623)（使用查找转换缓存模式的最佳实践）</span><span class="sxs-lookup"><span data-stu-id="57dec-195">Blog entry, [Best Practices for Using the Lookup Transformation Cache Modes](https://go.microsoft.com/fwlink/?LinkId=146623), on blogs.msdn.com</span></span>  
  
-   <span data-ttu-id="57dec-196">blogs.msdn.com 上的博客项 [Lookup Pattern: Case Insensitive](https://go.microsoft.com/fwlink/?LinkId=157782)（查找模式：不区分大小写）</span><span class="sxs-lookup"><span data-stu-id="57dec-196">Blog entry, [Lookup Pattern: Case Insensitive](https://go.microsoft.com/fwlink/?LinkId=157782), on blogs.msdn.com</span></span>  
  
-   <span data-ttu-id="57dec-197">msftisprodsamples.codeplex.com 上的示例 [Lookup Transformation](https://go.microsoft.com/fwlink/?LinkId=267528)（查找转换）</span><span class="sxs-lookup"><span data-stu-id="57dec-197">Sample, [Lookup Transformation](https://go.microsoft.com/fwlink/?LinkId=267528), on msftisprodsamples.codeplex.com.</span></span>  
  
     <span data-ttu-id="57dec-198">有关安装 [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] 产品示例和示例数据库的信息，请参阅 [SQL Server Integration Services Product Samples](https://go.microsoft.com/fwlink/?LinkId=267527)（SQL Server Integration Services 产品示例）。</span><span class="sxs-lookup"><span data-stu-id="57dec-198">For information on installing [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] product samples and sample databases, see [SQL Server Integration Services Product Samples](https://go.microsoft.com/fwlink/?LinkId=267527).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="57dec-199">另请参阅</span><span class="sxs-lookup"><span data-stu-id="57dec-199">See Also</span></span>  
 <span data-ttu-id="57dec-200">[模糊查找转换](fuzzy-lookup-transformation.md) </span><span class="sxs-lookup"><span data-stu-id="57dec-200">[Fuzzy Lookup Transformation](fuzzy-lookup-transformation.md) </span></span>  
 <span data-ttu-id="57dec-201">[字词查找转换](term-lookup-transformation.md) </span><span class="sxs-lookup"><span data-stu-id="57dec-201">[Term Lookup Transformation](term-lookup-transformation.md) </span></span>  
 <span data-ttu-id="57dec-202">[数据流](../data-flow.md) </span><span class="sxs-lookup"><span data-stu-id="57dec-202">[Data Flow](../data-flow.md) </span></span>  
 [<span data-ttu-id="57dec-203">Integration Services 转换</span><span class="sxs-lookup"><span data-stu-id="57dec-203">Integration Services Transformations</span></span>](integration-services-transformations.md)  
  
  
