---
title: 使用缓存连接管理器在完全缓存模式下实现查找转换 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- Lookup transformation [Integration Services]
ms.assetid: 58bc7611-5fb5-4113-9742-10959e06b94c
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 8b8c77f7ecfbe79db00acce09f706468ec0a0055
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87589843"
---
# <a name="implement-a-lookup-transformation-in-full-cache-mode-using-the-cache-connection-manager"></a><span data-ttu-id="d73b1-102">在完全缓存模式下使用缓存连接管理器实现查找转换</span><span class="sxs-lookup"><span data-stu-id="d73b1-102">Implement a Lookup Transformation in Full Cache Mode Using the Cache Connection Manager</span></span>
  <span data-ttu-id="d73b1-103">可以将查找转换配置为使用完全缓存模式和缓存连接管理器。</span><span class="sxs-lookup"><span data-stu-id="d73b1-103">You can configure the Lookup transformation to use full cache mode and a Cache connection manager.</span></span> <span data-ttu-id="d73b1-104">在完全缓存模式下，在查找转换运行前，引用数据集会加载到缓存中。</span><span class="sxs-lookup"><span data-stu-id="d73b1-104">In full cache mode, the reference dataset is loaded into cache before the Lookup transformation runs.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="d73b1-105">缓存连接管理器不支持二进制大型对象 (BLOB) 数据类型 DT_TEXT、DT_NTEXT 和 DT_IMAGE。</span><span class="sxs-lookup"><span data-stu-id="d73b1-105">The Cache connection manager does not support the Binary Large Object (BLOB) data types DT_TEXT, DT_NTEXT, and DT_IMAGE.</span></span> <span data-ttu-id="d73b1-106">如果引用数据集包含 BLOB 数据类型，则运行包时该组件将失败。</span><span class="sxs-lookup"><span data-stu-id="d73b1-106">If the reference dataset contains a BLOB data type, the component will fail when you run the package.</span></span> <span data-ttu-id="d73b1-107">可以使用 **“缓存连接管理器编辑器”** 修改列数据类型。</span><span class="sxs-lookup"><span data-stu-id="d73b1-107">You can use the **Cache Connection Manager Editor** to modify column data types.</span></span> <span data-ttu-id="d73b1-108">有关详细信息，请参阅 [Cache Connection Manager Editor](../cache-connection-manager-editor.md)。</span><span class="sxs-lookup"><span data-stu-id="d73b1-108">For more information, see [Cache Connection Manager Editor](../cache-connection-manager-editor.md).</span></span>  
  
 <span data-ttu-id="d73b1-109">查找转换通过将所连接数据源输入列中的数据和引用数据集中的列进行联接来执行查找。</span><span class="sxs-lookup"><span data-stu-id="d73b1-109">The Lookup transformation performs lookups by joining data in input columns from a connected data source with columns in a reference dataset.</span></span> <span data-ttu-id="d73b1-110">有关详细信息，请参阅 [Lookup Transformation](../data-flow/transformations/lookup-transformation.md)。</span><span class="sxs-lookup"><span data-stu-id="d73b1-110">For more information, see [Lookup Transformation](../data-flow/transformations/lookup-transformation.md).</span></span>  
  
 <span data-ttu-id="d73b1-111">使用下列项之一来生成引用数据集：</span><span class="sxs-lookup"><span data-stu-id="d73b1-111">You use one of the following to generate a reference dataset:</span></span>  
  
-   <span data-ttu-id="d73b1-112">缓存文件 (.caw)</span><span class="sxs-lookup"><span data-stu-id="d73b1-112">Cache file (.caw)</span></span>  
  
     <span data-ttu-id="d73b1-113">配置缓存连接管理器以便从现有缓存文件读取数据。</span><span class="sxs-lookup"><span data-stu-id="d73b1-113">You configure the Cache connection manager to read data from an existing cache file.</span></span>  
  
-   <span data-ttu-id="d73b1-114">数据流中的已连接数据源</span><span class="sxs-lookup"><span data-stu-id="d73b1-114">Connected data source in the data flow</span></span>  
  
     <span data-ttu-id="d73b1-115">使用“缓存转换”转换将数据流中已连接数据源的数据写入到缓存连接管理器。</span><span class="sxs-lookup"><span data-stu-id="d73b1-115">You use a Cache Transform transformation to write data from a connected data source in the data flow to a Cache connection manager.</span></span> <span data-ttu-id="d73b1-116">这些数据始终存储在内存中。</span><span class="sxs-lookup"><span data-stu-id="d73b1-116">The data is always stored in memory.</span></span>  
  
     <span data-ttu-id="d73b1-117">必须将查找转换添加到一个单独的数据流中。</span><span class="sxs-lookup"><span data-stu-id="d73b1-117">You must add the Lookup transformation to a separate data flow.</span></span> <span data-ttu-id="d73b1-118">这样，在执行查找转换前，缓存转换会填充缓存连接管理器。</span><span class="sxs-lookup"><span data-stu-id="d73b1-118">This enables the Cache Transform to populate the Cache connection manager before the Lookup transformation is executed.</span></span> <span data-ttu-id="d73b1-119">数据流可以位于同一个包中，也可以位于两个单独的包中。</span><span class="sxs-lookup"><span data-stu-id="d73b1-119">The data flows can be in the same package or in two separate packages.</span></span>  
  
     <span data-ttu-id="d73b1-120">如果数据流位于同一个包中，请使用优先约束来连接数据流。</span><span class="sxs-lookup"><span data-stu-id="d73b1-120">If the data flows are in the same package, use a precedence constraint to connect the data flows.</span></span> <span data-ttu-id="d73b1-121">这样，缓存转换就会在查找转换运行之前运行。</span><span class="sxs-lookup"><span data-stu-id="d73b1-121">This enables the Cache Transform to run before the Lookup transformation runs.</span></span>  
  
     <span data-ttu-id="d73b1-122">如果数据流位于单独的包中，则可使用执行包任务从父包调用子包。</span><span class="sxs-lookup"><span data-stu-id="d73b1-122">If the data flows are in separate packages, you can use the Execute Package task to call the child package from the parent package.</span></span> <span data-ttu-id="d73b1-123">在父包中的序列容器任务中添加多个执行包任务，可调用多个子包。</span><span class="sxs-lookup"><span data-stu-id="d73b1-123">You can call multiple child packages by adding multiple Execute Package tasks to a Sequence Container task in the parent package.</span></span>  
  
 <span data-ttu-id="d73b1-124">通过下面的任一方法，可在多个查找转换之间共享缓存中存储的引用数据集：</span><span class="sxs-lookup"><span data-stu-id="d73b1-124">You can share the reference dataset stored in cache, between multiple Lookup transformations by using one of the following methods:</span></span>  
  
-   <span data-ttu-id="d73b1-125">在单个包中将查找转换配置为使用同一缓存连接管理器。</span><span class="sxs-lookup"><span data-stu-id="d73b1-125">Configure the Lookup transformations in a single package to use the same Cache connection manager.</span></span>  
  
-   <span data-ttu-id="d73b1-126">在不同的包中将缓存连接管理器配置为使用同一缓存文件。</span><span class="sxs-lookup"><span data-stu-id="d73b1-126">Configure the Cache connection managers in different packages to use the same cache file.</span></span>  
  
 <span data-ttu-id="d73b1-127">有关详情，请参阅以下主题：</span><span class="sxs-lookup"><span data-stu-id="d73b1-127">For more information, see the following topics:</span></span>  
  
-   [<span data-ttu-id="d73b1-128">缓存转换</span><span class="sxs-lookup"><span data-stu-id="d73b1-128">Cache Transform</span></span>](../data-flow/transformations/cache-transform.md)  
  
-   [<span data-ttu-id="d73b1-129">缓存连接管理器</span><span class="sxs-lookup"><span data-stu-id="d73b1-129">Cache Connection Manager</span></span>](cache-connection-manager.md)  
  
-   [<span data-ttu-id="d73b1-130">优先约束</span><span class="sxs-lookup"><span data-stu-id="d73b1-130">Precedence Constraints</span></span>](../control-flow/precedence-constraints.md)  
  
-   [<span data-ttu-id="d73b1-131">执行包任务</span><span class="sxs-lookup"><span data-stu-id="d73b1-131">Execute Package Task</span></span>](../control-flow/execute-package-task.md)  
  
-   [<span data-ttu-id="d73b1-132">序列容器</span><span class="sxs-lookup"><span data-stu-id="d73b1-132">Sequence Container</span></span>](../control-flow/sequence-container.md)  
  
 <span data-ttu-id="d73b1-133">有关演示如何使用缓存连接管理器在完全缓存模式下实现查找转换的视频，请参阅 [如何在完全缓存模式下实现查找转换（SQL Server 视频）](https://go.microsoft.com/fwlink/?LinkId=131031)。</span><span class="sxs-lookup"><span data-stu-id="d73b1-133">For a video that demonstrates how to implement a Lookup transformation in Full Cache mode using the Cache connection manager, see [How to: Implement a Lookup Transformation in Full Cache Mode (SQL Server Video)](https://go.microsoft.com/fwlink/?LinkId=131031).</span></span>  
  
### <a name="to-implement-a-lookup-transformation-in-full-cache-mode-in-one-package-by-using-cache-connection-manager-and-a-data-source-in-the-data-flow"></a><span data-ttu-id="d73b1-134">在完全缓存模式下使用缓存连接管理器和数据流中的数据源在单个包中实现查找转换</span><span class="sxs-lookup"><span data-stu-id="d73b1-134">To implement a Lookup transformation in full cache mode in one package by using Cache connection manager and a data source in the data flow</span></span>  
  
1.  <span data-ttu-id="d73b1-135">在 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]中，打开一个 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 项目，再打开一个包。</span><span class="sxs-lookup"><span data-stu-id="d73b1-135">In [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], open a [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] project, and then open a package.</span></span>  
  
2.  <span data-ttu-id="d73b1-136">在 **“控制流”** 选项卡上，添加两个数据流任务，然后使用绿色连接线来连接任务：</span><span class="sxs-lookup"><span data-stu-id="d73b1-136">On the **Control Flow** tab, add two Data Flow tasks, and then connect the tasks by using a green connector:</span></span>  
  
3.  <span data-ttu-id="d73b1-137">在第一个数据流中，添加“缓存转换”转换，然后将该转换连接到数据源。</span><span class="sxs-lookup"><span data-stu-id="d73b1-137">In the first data flow, add a Cache Transform transformation, and then connect the transformation to a data source.</span></span>  
  
     <span data-ttu-id="d73b1-138">根据需要配置数据源。</span><span class="sxs-lookup"><span data-stu-id="d73b1-138">Configure the data source as needed.</span></span>  
  
4.  <span data-ttu-id="d73b1-139">双击缓存转换，在“缓存转换编辑器”  中的“连接管理器”  页上单击“新建”  ，创建一个新的缓存连接管理器。</span><span class="sxs-lookup"><span data-stu-id="d73b1-139">Double-click the Cache Transform, and then in the **Cache Transformation Editor**, on the **Connection Manager** page, click **New** to create a new Cache connection manager.</span></span>  
  
5.  <span data-ttu-id="d73b1-140">单击 **“缓存连接管理器编辑器”** 对话框的 **“列”** 选项卡，使用 **“索引位置”** 选项指定哪些列是索引列。</span><span class="sxs-lookup"><span data-stu-id="d73b1-140">Click the **Columns** tab of the **Cache Connection Manager Editor** dialog box, and then specify which columns are the index columns by using the **Index Position** option.</span></span>  
  
     <span data-ttu-id="d73b1-141">对于非索引列，索引位置是 0。</span><span class="sxs-lookup"><span data-stu-id="d73b1-141">For non-index columns, the index position is 0.</span></span> <span data-ttu-id="d73b1-142">对于索引列，索引位置是连续的正数。</span><span class="sxs-lookup"><span data-stu-id="d73b1-142">For index columns, the index position is a sequential, positive number.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="d73b1-143">当将查找转换配置为使用缓存连接管理器时，则仅引用数据集中的索引列能够映射到输入列。</span><span class="sxs-lookup"><span data-stu-id="d73b1-143">When the Lookup transformation is configured to use a Cache connection manager, only index columns in the reference dataset can be mapped to input columns.</span></span> <span data-ttu-id="d73b1-144">此外，还必须对所有索引列进行映射。</span><span class="sxs-lookup"><span data-stu-id="d73b1-144">Also, all index columns must be mapped.</span></span> <span data-ttu-id="d73b1-145">有关详细信息，请参阅 [Cache Connection Manager Editor](../cache-connection-manager-editor.md)。</span><span class="sxs-lookup"><span data-stu-id="d73b1-145">For more information, see [Cache Connection Manager Editor](../cache-connection-manager-editor.md).</span></span>  
  
6.  <span data-ttu-id="d73b1-146">若要将缓存保存到文件，请在 **“缓存连接管理器编辑器”** 中的 **“常规”** 选项卡上，设置以下选项来配置缓存连接管理器：</span><span class="sxs-lookup"><span data-stu-id="d73b1-146">To save the cache to a file, in the **Cache Connection Manager Editor**, on the **General** tab, configure the Cache connection manager by setting the following options:</span></span>  
  
    -   <span data-ttu-id="d73b1-147">选择 **“使用文件缓存”** 。</span><span class="sxs-lookup"><span data-stu-id="d73b1-147">Select **Use file cache**.</span></span>  
  
    -   <span data-ttu-id="d73b1-148">对于 **“文件名”** ，请键入文件路径，或者单击 **“浏览”** 选择文件。</span><span class="sxs-lookup"><span data-stu-id="d73b1-148">For **File name**, either type the file path or click **Browse** to select the file.</span></span>  
  
         <span data-ttu-id="d73b1-149">如果为其键入路径的文件不存在，则运行包时系统会创建该文件。</span><span class="sxs-lookup"><span data-stu-id="d73b1-149">If you type a path for a file that does not exist, the system creates the file when you run the package.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="d73b1-150">包的保护级别不适用于缓存文件。</span><span class="sxs-lookup"><span data-stu-id="d73b1-150">The protection level of the package does not apply to the cache file.</span></span> <span data-ttu-id="d73b1-151">如果缓存文件包含敏感信息，可使用访问控制列表 (ACL) 来限制对存储该文件的位置或文件夹的访问。</span><span class="sxs-lookup"><span data-stu-id="d73b1-151">If the cache file contains sensitive information, use an access control list (ACL) to restrict access to the location or folder in which you store the file.</span></span> <span data-ttu-id="d73b1-152">应只允许访问某些帐户。</span><span class="sxs-lookup"><span data-stu-id="d73b1-152">You should enable access only to certain accounts.</span></span> <span data-ttu-id="d73b1-153">有关详细信息，请参阅 [访问包使用的文件](../access-to-files-used-by-packages.md)。</span><span class="sxs-lookup"><span data-stu-id="d73b1-153">For more information, see [Access to Files Used by Packages](../access-to-files-used-by-packages.md).</span></span>  
  
7.  <span data-ttu-id="d73b1-154">根据需要配置缓存转换。</span><span class="sxs-lookup"><span data-stu-id="d73b1-154">Configure the Cache Transform as needed.</span></span> <span data-ttu-id="d73b1-155">有关详细信息，请参阅[缓存转换编辑器（“连接管理器”页）](../cache-transformation-editor-connection-manager-page.md)和[缓存转换编辑器（“映射”页）](../cache-transformation-editor-mappings-page.md)。</span><span class="sxs-lookup"><span data-stu-id="d73b1-155">For more information, see [Cache Transformation Editor &#40;Connection Manager Page&#41;](../cache-transformation-editor-connection-manager-page.md) and [Cache Transformation Editor &#40;Mappings Page&#41;](../cache-transformation-editor-mappings-page.md).</span></span>  
  
8.  <span data-ttu-id="d73b1-156">在第二个数据流中，添加一个查找转换，然后执行以下任务来配置转换：</span><span class="sxs-lookup"><span data-stu-id="d73b1-156">In the second data flow, add a Lookup transformation, and then configure the transformation by doing the following tasks:</span></span>  
  
    1.  <span data-ttu-id="d73b1-157">将连接线从源或前一转换拖到查找转换，从而将查找转换连接到数据流。</span><span class="sxs-lookup"><span data-stu-id="d73b1-157">Connect the Lookup transformation to the data flow by dragging a connector from a source or a previous transformation to the Lookup transformation.</span></span>  
  
        > [!NOTE]  
        >  <span data-ttu-id="d73b1-158">如果查找转换连接到包含空白日期字段的平面文件，该转换可能无效。</span><span class="sxs-lookup"><span data-stu-id="d73b1-158">A Lookup transformation might not validate if that transformation connects to a flat file that contains an empty date field.</span></span> <span data-ttu-id="d73b1-159">转换是否有效取决于平面文件的连接管理器是否配置为保留 Null 值。</span><span class="sxs-lookup"><span data-stu-id="d73b1-159">Whether the transformation validates depends on whether the connection manager for the flat file has been configured to retain null values.</span></span> <span data-ttu-id="d73b1-160">若要确保查找转换有效，请在 **“连接管理器”** 页上的 **“平面文件源编辑器”** 中选择 **“在数据流中保留源中的 Null 值”** 选项。</span><span class="sxs-lookup"><span data-stu-id="d73b1-160">To ensure that the Lookup transformation validates, in the **Flat File Source Editor**, on the **Connection Manager Page**, select the **Retain null values from the source as null values in the data flow** option.</span></span>  
  
    2.  <span data-ttu-id="d73b1-161">双击源或前一转换以配置组件。</span><span class="sxs-lookup"><span data-stu-id="d73b1-161">Double-click the source or previous transformation to configure the component.</span></span>  
  
    3.  <span data-ttu-id="d73b1-162">双击查找转换，在“查找转换编辑器”  的“常规”  页上，选择“完全缓存”  。</span><span class="sxs-lookup"><span data-stu-id="d73b1-162">Double-click the Lookup transformation, and then in the **Lookup Transformation Editor**, on the **General** page, select **Full cache**.</span></span>  
  
    4.  <span data-ttu-id="d73b1-163">在 **“连接类型”** 区域，选择 **“缓存连接管理器”** 。</span><span class="sxs-lookup"><span data-stu-id="d73b1-163">In the **Connection type** area, select **Cache connection manager**.</span></span>  
  
    5.  <span data-ttu-id="d73b1-164">在 **“指定如何处理没有匹配项的行”** 列表中，选择一个错误处理选项。</span><span class="sxs-lookup"><span data-stu-id="d73b1-164">From the **Specify how to handle rows with no matching entries** list, select an error handling option.</span></span>  
  
    6.  <span data-ttu-id="d73b1-165">在 **“连接”** 页的 **“缓存连接管理器”** 列表中，选择缓存连接管理器。</span><span class="sxs-lookup"><span data-stu-id="d73b1-165">On the **Connection** page, from the **Cache connection manager** list, select a Cache connection manager.</span></span>  
  
    7.  <span data-ttu-id="d73b1-166">单击 **“列”** 页，然后将至少一列从 **“可用输入列”** 列表中拖动到 **“可用查找列”** 列表中的列。</span><span class="sxs-lookup"><span data-stu-id="d73b1-166">Click the **Columns** page, and then drag at least one column from the **Available Input Columns** list to a column in the **Available Lookup Column** list.</span></span>  
  
        > [!NOTE]  
        >  <span data-ttu-id="d73b1-167">查找转换自动映射具有相同名称和相同数据类型的列。</span><span class="sxs-lookup"><span data-stu-id="d73b1-167">The Lookup transformation automatically maps columns that have the same name and the same data type.</span></span>  
  
        > [!NOTE]  
        >  <span data-ttu-id="d73b1-168">列必须含有要映射的匹配数据类型。</span><span class="sxs-lookup"><span data-stu-id="d73b1-168">Columns must have matching data types to be mapped.</span></span> <span data-ttu-id="d73b1-169">有关详细信息，请参阅 [Integration Services 数据类型](../data-flow/integration-services-data-types.md)。</span><span class="sxs-lookup"><span data-stu-id="d73b1-169">For more information, see [Integration Services Data Types](../data-flow/integration-services-data-types.md).</span></span>  
  
    8.  <span data-ttu-id="d73b1-170">在 **“可用查找列”** 列表中，选择列。</span><span class="sxs-lookup"><span data-stu-id="d73b1-170">In the **Available Lookup Columns** list, select columns.</span></span> <span data-ttu-id="d73b1-171">在 **“查找操作”** 列表中，指定查找列中的值是替换输入列中的值还是写入到新列。</span><span class="sxs-lookup"><span data-stu-id="d73b1-171">Then in the **Lookup Operation** list, specify whether the values from the lookup columns replace values in the input column or are written to a new column.</span></span>  
  
    9. <span data-ttu-id="d73b1-172">若要配置错误输出，请单击 **“错误输出”** 页，并设置错误处理选项。</span><span class="sxs-lookup"><span data-stu-id="d73b1-172">To configure the error output, click the **Error Output** page and set the error handling options.</span></span> <span data-ttu-id="d73b1-173">有关详细信息，请参阅[查找转换编辑器（“错误输出”页）](../lookup-transformation-editor-error-output-page.md)。</span><span class="sxs-lookup"><span data-stu-id="d73b1-173">For more information, see [Lookup Transformation Editor &#40;Error Output Page&#41;](../lookup-transformation-editor-error-output-page.md).</span></span>  
  
    10. <span data-ttu-id="d73b1-174">单击 **“确定”** 保存对查找转换的更改。</span><span class="sxs-lookup"><span data-stu-id="d73b1-174">Click **OK** to save your changes to the Lookup transformation.</span></span>  
  
9. <span data-ttu-id="d73b1-175">运行包。</span><span class="sxs-lookup"><span data-stu-id="d73b1-175">Run the package.</span></span>  
  
### <a name="to-implement-a-lookup-transformation-in-full-cache-mode-in-two-packages-by-using-cache-connection-manager-and-a-data-source-in-the-data-flow"></a><span data-ttu-id="d73b1-176">在完全缓存模式下使用缓存连接管理器和数据流中的数据源在两个包中实现查找转换</span><span class="sxs-lookup"><span data-stu-id="d73b1-176">To implement a Lookup transformation in full cache mode in two packages by using Cache connection manager and a data source in the data flow</span></span>  
  
1.  <span data-ttu-id="d73b1-177">在 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]中，打开一个 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 项目，再打开两个包。</span><span class="sxs-lookup"><span data-stu-id="d73b1-177">In [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], open a [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] project, and then open two packages.</span></span>  
  
2.  <span data-ttu-id="d73b1-178">在每个包中的“控制流”选项卡上，添加数据流任务。</span><span class="sxs-lookup"><span data-stu-id="d73b1-178">On the Control Flow tab in each package, add a Data Flow task.</span></span>  
  
3.  <span data-ttu-id="d73b1-179">在父包中，向数据流添加“缓存转换”转换，然后将该转换连接到数据源。</span><span class="sxs-lookup"><span data-stu-id="d73b1-179">In the parent package, add a Cache Transform transformation to the data flow, and then connect the transformation to a data source.</span></span>  
  
     <span data-ttu-id="d73b1-180">根据需要配置数据源。</span><span class="sxs-lookup"><span data-stu-id="d73b1-180">Configure the data source as needed.</span></span>  
  
4.  <span data-ttu-id="d73b1-181">双击缓存转换，在“缓存转换编辑器”  中的“连接管理器”  页上单击“新建”  ，创建一个新的缓存连接管理器。</span><span class="sxs-lookup"><span data-stu-id="d73b1-181">Double-click the Cache Transform, and then in the **Cache Transformation Editor**, on the **Connection Manager** page, click **New** to create a new Cache connection manager.</span></span>  
  
5.  <span data-ttu-id="d73b1-182">在 **“缓存连接管理器编辑器”** 中的 **“常规”** 选项卡上，设置以下选项来配置缓存连接管理器：</span><span class="sxs-lookup"><span data-stu-id="d73b1-182">In the **Cache Connection Manager Editor**, on the **General** tab, configure the Cache connection manager by setting the following options:</span></span>  
  
    -   <span data-ttu-id="d73b1-183">选择 **“使用文件缓存”** 。</span><span class="sxs-lookup"><span data-stu-id="d73b1-183">Select **Use file cache**.</span></span>  
  
    -   <span data-ttu-id="d73b1-184">对于 **“文件名”** ，请键入文件路径，或者单击 **“浏览”** 选择文件。</span><span class="sxs-lookup"><span data-stu-id="d73b1-184">For **File name**, either type the file path or click **Browse** to select the file.</span></span>  
  
         <span data-ttu-id="d73b1-185">如果为其键入路径的文件不存在，则运行包时系统会创建该文件。</span><span class="sxs-lookup"><span data-stu-id="d73b1-185">If you type a path for a file that does not exist, the system creates the file when you run the package.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="d73b1-186">包的保护级别不适用于缓存文件。</span><span class="sxs-lookup"><span data-stu-id="d73b1-186">The protection level of the package does not apply to the cache file.</span></span> <span data-ttu-id="d73b1-187">如果缓存文件包含敏感信息，可使用访问控制列表 (ACL) 来限制对存储该文件的位置或文件夹的访问。</span><span class="sxs-lookup"><span data-stu-id="d73b1-187">If the cache file contains sensitive information, use an access control list (ACL) to restrict access to the location or folder in which you store the file.</span></span> <span data-ttu-id="d73b1-188">应只允许访问某些帐户。</span><span class="sxs-lookup"><span data-stu-id="d73b1-188">You should enable access only to certain accounts.</span></span> <span data-ttu-id="d73b1-189">有关详细信息，请参阅 [访问包使用的文件](../access-to-files-used-by-packages.md)。</span><span class="sxs-lookup"><span data-stu-id="d73b1-189">For more information, see [Access to Files Used by Packages](../access-to-files-used-by-packages.md).</span></span>  
  
6.  <span data-ttu-id="d73b1-190">单击 **“列”** 选项卡，然后使用 **“索引位置”** 选项来指定哪些列是索引列。</span><span class="sxs-lookup"><span data-stu-id="d73b1-190">Click the **Columns** tab, and then specify which columns are the index columns by using the **Index Position** option.</span></span>  
  
     <span data-ttu-id="d73b1-191">对于非索引列，索引位置是 0。</span><span class="sxs-lookup"><span data-stu-id="d73b1-191">For non-index columns, the index position is 0.</span></span> <span data-ttu-id="d73b1-192">对于索引列，索引位置是连续的正数。</span><span class="sxs-lookup"><span data-stu-id="d73b1-192">For index columns, the index position is a sequential, positive number.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="d73b1-193">当将查找转换配置为使用缓存连接管理器时，则仅引用数据集中的索引列能够映射到输入列。</span><span class="sxs-lookup"><span data-stu-id="d73b1-193">When the Lookup transformation is configured to use a Cache connection manager, only index columns in the reference dataset can be mapped to input columns.</span></span> <span data-ttu-id="d73b1-194">此外，还必须对所有索引列进行映射。</span><span class="sxs-lookup"><span data-stu-id="d73b1-194">Also, all index columns must be mapped.</span></span> <span data-ttu-id="d73b1-195">有关详细信息，请参阅 [Cache Connection Manager Editor](../cache-connection-manager-editor.md)。</span><span class="sxs-lookup"><span data-stu-id="d73b1-195">For more information, see [Cache Connection Manager Editor](../cache-connection-manager-editor.md).</span></span>  
  
7.  <span data-ttu-id="d73b1-196">根据需要配置缓存转换。</span><span class="sxs-lookup"><span data-stu-id="d73b1-196">Configure the Cache Transform as needed.</span></span> <span data-ttu-id="d73b1-197">有关详细信息，请参阅[缓存转换编辑器（“连接管理器”页）](../cache-transformation-editor-connection-manager-page.md)和[缓存转换编辑器（“映射”页）](../cache-transformation-editor-mappings-page.md)。</span><span class="sxs-lookup"><span data-stu-id="d73b1-197">For more information, see [Cache Transformation Editor &#40;Connection Manager Page&#41;](../cache-transformation-editor-connection-manager-page.md) and [Cache Transformation Editor &#40;Mappings Page&#41;](../cache-transformation-editor-mappings-page.md).</span></span>  
  
8.  <span data-ttu-id="d73b1-198">执行下列操作之一以填充第二个包中使用的缓存连接管理器：</span><span class="sxs-lookup"><span data-stu-id="d73b1-198">Do one of the following to populate the Cache connection manager that is used in the second package:</span></span>  
  
    -   <span data-ttu-id="d73b1-199">运行父包。</span><span class="sxs-lookup"><span data-stu-id="d73b1-199">Run the parent package.</span></span>  
  
    -   <span data-ttu-id="d73b1-200">双击在步骤 4 中创建的缓存连接管理器，单击“列”  ，选择行，然后按 Ctrl+C 复制列元数据。</span><span class="sxs-lookup"><span data-stu-id="d73b1-200">Double-click the Cache connection manager you created in step 4, click **Columns**, select the rows, and then press CTRL+C to copy the column metadata.</span></span>  
  
9. <span data-ttu-id="d73b1-201">在子包中，右键单击“连接管理器”区域，单击“新建连接”，在“添加 SSIS 连接管理器”对话框中选择“缓存”，单击“添加”，即可创建缓存连接管理器。</span><span class="sxs-lookup"><span data-stu-id="d73b1-201">In the child package, create a Cache connection manager by right-clicking in the **Connection Managers** area, clicking **New Connection**, selecting **CACHE** in the **Add SSIS Connection Manager** dialog box, and then clicking **Add**.</span></span>  
  
     <span data-ttu-id="d73b1-202">**“连接管理器”** 区域显示在 **设计器的**“控制流” **、** “数据流” **和** “事件处理程序” [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 选项卡的底部。</span><span class="sxs-lookup"><span data-stu-id="d73b1-202">The **Connection Managers** area appears on the bottom of the **Control Flow**, **Data Flow**, and **Event Handlers** tabs of [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] Designer.</span></span>  
  
10. <span data-ttu-id="d73b1-203">在 **“缓存连接管理器编辑器”** 中的 **“常规”** 选项卡上，设置以下选项对缓存连接管理器进行配置，以便从所选的缓存文件中读取数据：</span><span class="sxs-lookup"><span data-stu-id="d73b1-203">In the **Cache Connection Manager Editor**, on the **General** tab, configure the Cache connection manager to read the data from the cache file that you selected by setting the following options:</span></span>  
  
    -   <span data-ttu-id="d73b1-204">选择 **“使用文件缓存”** 。</span><span class="sxs-lookup"><span data-stu-id="d73b1-204">Select **Use file cache**.</span></span>  
  
    -   <span data-ttu-id="d73b1-205">对于 **“文件名”** ，请键入文件路径，或者单击 **“浏览”** 选择文件。</span><span class="sxs-lookup"><span data-stu-id="d73b1-205">For **File name**, either type the file path or click **Browse** to select the file.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="d73b1-206">包的保护级别不适用于缓存文件。</span><span class="sxs-lookup"><span data-stu-id="d73b1-206">The protection level of the package does not apply to the cache file.</span></span> <span data-ttu-id="d73b1-207">如果缓存文件包含敏感信息，可使用访问控制列表 (ACL) 来限制对存储该文件的位置或文件夹的访问。</span><span class="sxs-lookup"><span data-stu-id="d73b1-207">If the cache file contains sensitive information, use an access control list (ACL) to restrict access to the location or folder in which you store the file.</span></span> <span data-ttu-id="d73b1-208">应只允许访问某些帐户。</span><span class="sxs-lookup"><span data-stu-id="d73b1-208">You should enable access only to certain accounts.</span></span> <span data-ttu-id="d73b1-209">有关详细信息，请参阅 [访问包使用的文件](../access-to-files-used-by-packages.md)。</span><span class="sxs-lookup"><span data-stu-id="d73b1-209">For more information, see [Access to Files Used by Packages](../access-to-files-used-by-packages.md).</span></span>  
  
11. <span data-ttu-id="d73b1-210">如果在步骤 8 中复制了列元数据，请单击“列”  ，选择空行，然后按 Ctrl+V 粘贴列元数据。</span><span class="sxs-lookup"><span data-stu-id="d73b1-210">If you copied the column metadata in step 8, click **Columns**, select the empty row, and then press CTRL+V to paste the column metadata.</span></span>  
  
12. <span data-ttu-id="d73b1-211">添加查找转换，然后执行以下操作来配置转换：</span><span class="sxs-lookup"><span data-stu-id="d73b1-211">Add a Lookup transformation, and then configure the transformation by doing the following:</span></span>  
  
    1.  <span data-ttu-id="d73b1-212">将连接线从源或前一转换拖到查找转换，从而将查找转换连接到数据流。</span><span class="sxs-lookup"><span data-stu-id="d73b1-212">Connect the Lookup transformation to the data flow by dragging a connector from a source or a previous transformation to the Lookup transformation.</span></span>  
  
        > [!NOTE]  
        >  <span data-ttu-id="d73b1-213">如果查找转换连接到包含空白日期字段的平面文件，该转换可能无效。</span><span class="sxs-lookup"><span data-stu-id="d73b1-213">A Lookup transformation might not validate if that transformation connects to a flat file that contains an empty date field.</span></span> <span data-ttu-id="d73b1-214">转换是否有效取决于平面文件的连接管理器是否配置为保留 Null 值。</span><span class="sxs-lookup"><span data-stu-id="d73b1-214">Whether the transformation validates depends on whether the connection manager for the flat file has been configured to retain null values.</span></span> <span data-ttu-id="d73b1-215">若要确保查找转换有效，请在 **“连接管理器”** 页上的 **“平面文件源编辑器”** 中选择 **“在数据流中保留源中的 Null 值”** 选项。</span><span class="sxs-lookup"><span data-stu-id="d73b1-215">To ensure that the Lookup transformation validates, in the **Flat File Source Editor**, on the **Connection Manager Page**, select the **Retain null values from the source as null values in the data flow** option.</span></span>  
  
    2.  <span data-ttu-id="d73b1-216">双击源或前一转换以配置组件。</span><span class="sxs-lookup"><span data-stu-id="d73b1-216">Double-click the source or previous transformation to configure the component.</span></span>  
  
    3.  <span data-ttu-id="d73b1-217">双击查找转换，在“查找转换编辑器”的“常规”页上选择“完全缓存”。</span><span class="sxs-lookup"><span data-stu-id="d73b1-217">Double-click the Lookup transformation, and then select **Full cache** on the **General** page of the **Lookup Transformation Editor**.</span></span>  
  
    4.  <span data-ttu-id="d73b1-218">在 **“连接类型”** 区域，选择 **“缓存连接管理器”** 。</span><span class="sxs-lookup"><span data-stu-id="d73b1-218">Select **Cache connection manager** in the **Connection type** area.</span></span>  
  
    5.  <span data-ttu-id="d73b1-219">在 **“指定如何处理没有匹配项的行”** 列表中，为没有匹配项的行选择一个错误处理选项。</span><span class="sxs-lookup"><span data-stu-id="d73b1-219">Select an error handling option for rows without matching entries from the **Specify how to handle rows with no matching entries** list.</span></span>  
  
    6.  <span data-ttu-id="d73b1-220">在 **“连接”** 页的 **“缓存连接管理器”** 列表中，选择您添加的缓存连接管理器。</span><span class="sxs-lookup"><span data-stu-id="d73b1-220">On the **Connection** page, from the **Cache connection manager** list, select the Cache connection manager that you added.</span></span>  
  
    7.  <span data-ttu-id="d73b1-221">单击 **“列”** 页，然后将至少一列从 **“可用输入列”** 列表中拖动到 **“可用查找列”** 列表中的列。</span><span class="sxs-lookup"><span data-stu-id="d73b1-221">Click the **Columns** page, and then drag at least one column from the **Available Input Columns** list to a column in the **Available Lookup Column** list.</span></span>  
  
        > [!NOTE]  
        >  <span data-ttu-id="d73b1-222">查找转换自动映射具有相同名称和相同数据类型的列。</span><span class="sxs-lookup"><span data-stu-id="d73b1-222">The Lookup transformation automatically maps columns that have the same name and the same data type.</span></span>  
  
        > [!NOTE]  
        >  <span data-ttu-id="d73b1-223">列必须含有要映射的匹配数据类型。</span><span class="sxs-lookup"><span data-stu-id="d73b1-223">Columns must have matching data types to be mapped.</span></span> <span data-ttu-id="d73b1-224">有关详细信息，请参阅 [Integration Services 数据类型](../data-flow/integration-services-data-types.md)。</span><span class="sxs-lookup"><span data-stu-id="d73b1-224">For more information, see [Integration Services Data Types](../data-flow/integration-services-data-types.md).</span></span>  
  
    8.  <span data-ttu-id="d73b1-225">在 **“可用查找列”** 列表中，选择列。</span><span class="sxs-lookup"><span data-stu-id="d73b1-225">In the **Available Lookup Columns** list, select columns.</span></span> <span data-ttu-id="d73b1-226">在 **“查找操作”** 列表中，指定查找列中的值是替换输入列中的值还是写入到新列。</span><span class="sxs-lookup"><span data-stu-id="d73b1-226">Then in the **Lookup Operation** list, specify whether the values from the lookup columns replace values in the input column or are written to a new column.</span></span>  
  
    9. <span data-ttu-id="d73b1-227">若要配置错误输出，请单击 **“错误输出”** 页，并设置错误处理选项。</span><span class="sxs-lookup"><span data-stu-id="d73b1-227">To configure the error output, click the **Error Output** page and set the error handling options.</span></span> <span data-ttu-id="d73b1-228">有关详细信息，请参阅[查找转换编辑器（“错误输出”页）](../lookup-transformation-editor-error-output-page.md)。</span><span class="sxs-lookup"><span data-stu-id="d73b1-228">For more information, see [Lookup Transformation Editor &#40;Error Output Page&#41;](../lookup-transformation-editor-error-output-page.md).</span></span>  
  
    10. <span data-ttu-id="d73b1-229">单击 **“确定”** 保存对查找转换的更改。</span><span class="sxs-lookup"><span data-stu-id="d73b1-229">Click **OK** to save your changes to the Lookup transformation.</span></span>  
  
13. <span data-ttu-id="d73b1-230">打开父包，向控制流添加一个执行包任务，然后配置任务以调用子包。</span><span class="sxs-lookup"><span data-stu-id="d73b1-230">Open the parent package, add an Execute Package task to the control flow, and then configure the task to call the child package.</span></span> <span data-ttu-id="d73b1-231">有关详细信息，请参阅 [Execute Package Task](../control-flow/execute-package-task.md)。</span><span class="sxs-lookup"><span data-stu-id="d73b1-231">For more information, see [Execute Package Task](../control-flow/execute-package-task.md).</span></span>  
  
14. <span data-ttu-id="d73b1-232">运行包。</span><span class="sxs-lookup"><span data-stu-id="d73b1-232">Run the packages.</span></span>  
  
### <a name="to-implement-a-lookup-transformation-in-full-cache-mode-by-using-cache-connection-manager-and-an-existing-cache-file"></a><span data-ttu-id="d73b1-233">在完全缓存模式下使用缓存连接管理器和现有缓存文件实现查找转换</span><span class="sxs-lookup"><span data-stu-id="d73b1-233">To implement a Lookup transformation in full cache mode by using Cache connection manager and an existing cache file</span></span>  
  
1.  <span data-ttu-id="d73b1-234">在 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]中，打开一个 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 项目，再打开一个包。</span><span class="sxs-lookup"><span data-stu-id="d73b1-234">In [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], open a [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] project, and then open a package.</span></span>  
  
2.  <span data-ttu-id="d73b1-235">右键单击“连接管理器”  区域，然后单击“新建连接”  。</span><span class="sxs-lookup"><span data-stu-id="d73b1-235">Right-click in the **Connection Managers** area, and then click **New Connection**.</span></span>  
  
     <span data-ttu-id="d73b1-236">**“连接管理器”** 区域显示在 **设计器的**“控制流” **、** “数据流” **和** “事件处理程序” [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 选项卡的底部。</span><span class="sxs-lookup"><span data-stu-id="d73b1-236">The **Connection Managers** area appears on the bottom of the **Control Flow**, **Data Flow**, and **Event Handlers** tabs of [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] Designer.</span></span>  
  
3.  <span data-ttu-id="d73b1-237">在 **“添加 SSIS 连接管理器”** 对话框中，选择 **CACHE**，单击 **“添加”** 添加一个缓存连接管理器。</span><span class="sxs-lookup"><span data-stu-id="d73b1-237">In the **Add SSIS Connection Manager** dialog box, select **CACHE**, and then click **Add** to add a Cache connection manager.</span></span>  
  
4.  <span data-ttu-id="d73b1-238">双击缓存连接管理器以打开“缓存连接管理器编辑器”  。</span><span class="sxs-lookup"><span data-stu-id="d73b1-238">Double-click the Cache connection manager to open the **Cache Connection Manager Editor**.</span></span>  
  
5.  <span data-ttu-id="d73b1-239">在 **“缓存连接管理器编辑器”** 中的 **“常规”** 选项卡上，设置以下选项来配置缓存连接管理器：</span><span class="sxs-lookup"><span data-stu-id="d73b1-239">In the **Cache Connection Manager Editor**, on the **General** tab, configure the Cache connection manager by setting the following options:</span></span>  
  
    -   <span data-ttu-id="d73b1-240">选择 **“使用文件缓存”** 。</span><span class="sxs-lookup"><span data-stu-id="d73b1-240">Select **Use file cache**.</span></span>  
  
    -   <span data-ttu-id="d73b1-241">对于 **“文件名”** ，请键入文件路径，或者单击 **“浏览”** 选择文件。</span><span class="sxs-lookup"><span data-stu-id="d73b1-241">For **File name**, either type the file path or click **Browse** to select the file.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="d73b1-242">包的保护级别不适用于缓存文件。</span><span class="sxs-lookup"><span data-stu-id="d73b1-242">The protection level of the package does not apply to the cache file.</span></span> <span data-ttu-id="d73b1-243">如果缓存文件包含敏感信息，可使用访问控制列表 (ACL) 来限制对存储该文件的位置或文件夹的访问。</span><span class="sxs-lookup"><span data-stu-id="d73b1-243">If the cache file contains sensitive information, use an access control list (ACL) to restrict access to the location or folder in which you store the file.</span></span> <span data-ttu-id="d73b1-244">应只允许访问某些帐户。</span><span class="sxs-lookup"><span data-stu-id="d73b1-244">You should enable access only to certain accounts.</span></span> <span data-ttu-id="d73b1-245">有关详细信息，请参阅 [访问包使用的文件](../access-to-files-used-by-packages.md)。</span><span class="sxs-lookup"><span data-stu-id="d73b1-245">For more information, see [Access to Files Used by Packages](../access-to-files-used-by-packages.md).</span></span>  
  
6.  <span data-ttu-id="d73b1-246">单击 **“列”** 选项卡，然后使用 **“索引位置”** 选项来指定哪些列是索引列。</span><span class="sxs-lookup"><span data-stu-id="d73b1-246">Click the **Columns** tab, and then specify which columns are the index columns by using the **Index Position** option.</span></span>  
  
     <span data-ttu-id="d73b1-247">对于非索引列，索引位置是 0。</span><span class="sxs-lookup"><span data-stu-id="d73b1-247">For non-index columns, the index position is 0.</span></span> <span data-ttu-id="d73b1-248">对于索引列，索引位置是连续的正数。</span><span class="sxs-lookup"><span data-stu-id="d73b1-248">For index columns, the index position is a sequential, positive number.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="d73b1-249">当将查找转换配置为使用缓存连接管理器时，则仅引用数据集中的索引列能够映射到输入列。</span><span class="sxs-lookup"><span data-stu-id="d73b1-249">When the Lookup transformation is configured to use a Cache connection manager, only index columns in the reference dataset can be mapped to input columns.</span></span> <span data-ttu-id="d73b1-250">此外，还必须对所有索引列进行映射。</span><span class="sxs-lookup"><span data-stu-id="d73b1-250">Also, all index columns must be mapped.</span></span> <span data-ttu-id="d73b1-251">有关详细信息，请参阅 [Cache Connection Manager Editor](../cache-connection-manager-editor.md)。</span><span class="sxs-lookup"><span data-stu-id="d73b1-251">For more information, see [Cache Connection Manager Editor](../cache-connection-manager-editor.md).</span></span>  
  
7.  <span data-ttu-id="d73b1-252">在 **“控制流”** 选项卡上，向包添加一个数据流任务，然后向数据流添加一个查找转换。</span><span class="sxs-lookup"><span data-stu-id="d73b1-252">On the **Control Flow** tab, add a Data Flow task to the package, and then add a Lookup transformation to the data flow.</span></span>  
  
8.  <span data-ttu-id="d73b1-253">执行以下操作来配置查找转换：</span><span class="sxs-lookup"><span data-stu-id="d73b1-253">Configure the Lookup transformation by doing the following:</span></span>  
  
    1.  <span data-ttu-id="d73b1-254">将连接线从源或前一转换拖到查找转换，从而将查找转换连接到数据流。</span><span class="sxs-lookup"><span data-stu-id="d73b1-254">Connect the Lookup transformation to the data flow by dragging a connector from a source or a previous transformation to the Lookup transformation.</span></span>  
  
        > [!NOTE]  
        >  <span data-ttu-id="d73b1-255">如果查找转换连接到包含空白日期字段的平面文件，该转换可能无效。</span><span class="sxs-lookup"><span data-stu-id="d73b1-255">A Lookup transformation might not validate if that transformation connects to a flat file that contains an empty date field.</span></span> <span data-ttu-id="d73b1-256">转换是否有效取决于平面文件的连接管理器是否配置为保留 Null 值。</span><span class="sxs-lookup"><span data-stu-id="d73b1-256">Whether the transformation validates depends on whether the connection manager for the flat file has been configured to retain null values.</span></span> <span data-ttu-id="d73b1-257">若要确保查找转换有效，请在 **“连接管理器”** 页上的 **“平面文件源编辑器”** 中选择 **“在数据流中保留源中的 Null 值”** 选项。</span><span class="sxs-lookup"><span data-stu-id="d73b1-257">To ensure that the Lookup transformation validates, in the **Flat File Source Editor**, on the **Connection Manager Page**, select the **Retain null values from the source as null values in the data flow** option.</span></span>  
  
    2.  <span data-ttu-id="d73b1-258">双击源或前一转换以配置组件。</span><span class="sxs-lookup"><span data-stu-id="d73b1-258">Double-click the source or previous transformation to configure the component.</span></span>  
  
    3.  <span data-ttu-id="d73b1-259">双击查找转换，在“查找转换编辑器”  的“常规”  页上，选择“完全缓存”  。</span><span class="sxs-lookup"><span data-stu-id="d73b1-259">Double-click the Lookup transformation, and then in the **Lookup Transformation Editor**, on the **General** page, select **Full cache**.</span></span>  
  
    4.  <span data-ttu-id="d73b1-260">在 **“连接类型”** 区域，选择 **“缓存连接管理器”** 。</span><span class="sxs-lookup"><span data-stu-id="d73b1-260">Select **Cache connection manager** in the **Connection type** area.</span></span>  
  
    5.  <span data-ttu-id="d73b1-261">在 **“指定如何处理没有匹配项的行”** 列表中，为没有匹配项的行选择一个错误处理选项。</span><span class="sxs-lookup"><span data-stu-id="d73b1-261">Select an error handling option for rows without matching entries from the **Specify how to handle rows with no matching entries** list.</span></span>  
  
    6.  <span data-ttu-id="d73b1-262">在 **“连接”** 页的 **“缓存连接管理器”** 列表中，选择您添加的缓存连接管理器。</span><span class="sxs-lookup"><span data-stu-id="d73b1-262">On the **Connection** page, from the **Cache connection manager** list, select the Cache connection manager that you added.</span></span>  
  
    7.  <span data-ttu-id="d73b1-263">单击 **“列”** 页，然后将至少一列从 **“可用输入列”** 列表中拖动到 **“可用查找列”** 列表中的列。</span><span class="sxs-lookup"><span data-stu-id="d73b1-263">Click the **Columns** page, and then drag at least one column from the **Available Input Columns** list to a column in the **Available Lookup Column** list.</span></span>  
  
        > [!NOTE]  
        >  <span data-ttu-id="d73b1-264">查找转换自动映射具有相同名称和相同数据类型的列。</span><span class="sxs-lookup"><span data-stu-id="d73b1-264">The Lookup transformation automatically maps columns that have the same name and the same data type.</span></span>  
  
        > [!NOTE]  
        >  <span data-ttu-id="d73b1-265">列必须含有要映射的匹配数据类型。</span><span class="sxs-lookup"><span data-stu-id="d73b1-265">Columns must have matching data types to be mapped.</span></span> <span data-ttu-id="d73b1-266">有关详细信息，请参阅 [Integration Services 数据类型](../data-flow/integration-services-data-types.md)。</span><span class="sxs-lookup"><span data-stu-id="d73b1-266">For more information, see [Integration Services Data Types](../data-flow/integration-services-data-types.md).</span></span>  
  
    8.  <span data-ttu-id="d73b1-267">在 **“可用查找列”** 列表中，选择列。</span><span class="sxs-lookup"><span data-stu-id="d73b1-267">In the **Available Lookup Columns** list, select columns.</span></span> <span data-ttu-id="d73b1-268">在 **“查找操作”** 列表中，指定查找列中的值是替换输入列中的值还是写入到新列。</span><span class="sxs-lookup"><span data-stu-id="d73b1-268">Then in the **Lookup Operation** list, specify whether the values from the lookup columns replace values in the input column or are written to a new column.</span></span>  
  
    9. <span data-ttu-id="d73b1-269">若要配置错误输出，请单击 **“错误输出”** 页，并设置错误处理选项。</span><span class="sxs-lookup"><span data-stu-id="d73b1-269">To configure the error output, click the **Error Output** page and set the error handling options.</span></span> <span data-ttu-id="d73b1-270">有关详细信息，请参阅[查找转换编辑器（“错误输出”页）](../lookup-transformation-editor-error-output-page.md)。</span><span class="sxs-lookup"><span data-stu-id="d73b1-270">For more information, see [Lookup Transformation Editor &#40;Error Output Page&#41;](../lookup-transformation-editor-error-output-page.md).</span></span>  
  
    10. <span data-ttu-id="d73b1-271">单击 **“确定”** 保存对查找转换的更改。</span><span class="sxs-lookup"><span data-stu-id="d73b1-271">Click **OK** to save your changes to the Lookup transformation.</span></span>  
  
9. <span data-ttu-id="d73b1-272">运行包。</span><span class="sxs-lookup"><span data-stu-id="d73b1-272">Run the package.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d73b1-273">另请参阅</span><span class="sxs-lookup"><span data-stu-id="d73b1-273">See Also</span></span>  
 <span data-ttu-id="d73b1-274">[在完全缓存模式下使用 OLE DB 连接管理器实现查找转换](lookup-transformation-full-cache-mode-ole-db-connection-manager.md) </span><span class="sxs-lookup"><span data-stu-id="d73b1-274">[Implement a Lookup Transformation in Full Cache Mode Using the OLE DB Connection Manager](lookup-transformation-full-cache-mode-ole-db-connection-manager.md) </span></span>  
 <span data-ttu-id="d73b1-275">[在不缓存模式或部分缓存模式下实现查找](../data-flow/transformations/implement-a-lookup-in-no-cache-or-partial-cache-mode.md) </span><span class="sxs-lookup"><span data-stu-id="d73b1-275">[Implement a Lookup in No Cache or Partial Cache Mode](../data-flow/transformations/implement-a-lookup-in-no-cache-or-partial-cache-mode.md) </span></span>  
 [<span data-ttu-id="d73b1-276">Integration Services 转换</span><span class="sxs-lookup"><span data-stu-id="d73b1-276">Integration Services Transformations</span></span>](../data-flow/transformations/integration-services-transformations.md)  
  
  
