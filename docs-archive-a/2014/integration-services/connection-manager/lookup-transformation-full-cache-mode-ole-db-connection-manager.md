---
title: 使用 OLE DB 连接管理器在完全缓存模式下实现查找转换 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- Lookup transformation [Integration Services]
ms.assetid: c4150e1b-bdff-4f7a-af4c-3401c34def83
author: chugugrace
ms.author: chugu
ms.openlocfilehash: f77a753dd71bc487d57492371906fc48bc114357
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87589842"
---
# <a name="implement-a-lookup-transformation-in-full-cache-mode-using-the-ole-db-connection-manager"></a><span data-ttu-id="42eff-102">在完全缓存模式下使用 OLE DB 连接管理器来实现查找转换</span><span class="sxs-lookup"><span data-stu-id="42eff-102">Implement a Lookup Transformation in Full Cache Mode Using the OLE DB Connection Manager</span></span>
  <span data-ttu-id="42eff-103">可以将查找转换配置为使用完全缓存模式和 OLE DB 连接管理器。</span><span class="sxs-lookup"><span data-stu-id="42eff-103">You can configure the Lookup transformation to use full cache mode and an OLE DB connection manager.</span></span> <span data-ttu-id="42eff-104">在完全缓存模式下，在查找转换运行前，引用数据集会加载到缓存中。</span><span class="sxs-lookup"><span data-stu-id="42eff-104">In the full cache mode, the reference dataset is loaded into cache before the Lookup transformation runs.</span></span>  
  
 <span data-ttu-id="42eff-105">查找转换通过将所连接数据源输入列中的数据和引用数据集中的列进行联接来执行查找。</span><span class="sxs-lookup"><span data-stu-id="42eff-105">The Lookup transformation performs lookups by joining data in input columns from a connected data source with columns in a reference dataset.</span></span> <span data-ttu-id="42eff-106">有关详细信息，请参阅 [Lookup Transformation](../data-flow/transformations/lookup-transformation.md)。</span><span class="sxs-lookup"><span data-stu-id="42eff-106">For more information, see [Lookup Transformation](../data-flow/transformations/lookup-transformation.md).</span></span>  
  
 <span data-ttu-id="42eff-107">在配置查找转换以使用 OLE DB 连接管理器时，可以选择表、视图或 SQL 查询以生成引用数据集。</span><span class="sxs-lookup"><span data-stu-id="42eff-107">When you configure the Lookup transformation to use an OLE DB connection manager, you select a table, view, or SQL query to generate the reference dataset.</span></span>  
  
### <a name="to-implement-a-lookup-transformation-in-full-cache-mode-by-using-ole-db-connection-manager"></a><span data-ttu-id="42eff-108">在完全缓存模式下使用 OLE DB 连接管理器实现查找转换</span><span class="sxs-lookup"><span data-stu-id="42eff-108">To implement a Lookup transformation in full cache mode by using OLE DB connection manager</span></span>  
  
1.  <span data-ttu-id="42eff-109">在 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]中，打开包含所需包的 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 项目，然后在解决方案资源管理器中双击该包。</span><span class="sxs-lookup"><span data-stu-id="42eff-109">In [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], open the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] project that contains the package you want, and then double-click the package in Solution Explorer.</span></span>  
  
2.  <span data-ttu-id="42eff-110">在 **“数据流”** 选项卡上，从 **“工具箱”** 中将查找转换拖至设计图面。</span><span class="sxs-lookup"><span data-stu-id="42eff-110">On the **Data Flow** tab, from the **Toolbox**, drag the Lookup transformation to the design surface.</span></span>  
  
3.  <span data-ttu-id="42eff-111">将连接线从源或前一转换拖到查找转换，从而将查找转换连接到数据流。</span><span class="sxs-lookup"><span data-stu-id="42eff-111">Connect the Lookup transformation to the data flow by dragging a connector from a source or a previous transformation to the Lookup transformation.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="42eff-112">如果查找转换连接到包含空白日期字段的平面文件，该转换可能无效。</span><span class="sxs-lookup"><span data-stu-id="42eff-112">A Lookup transformation might not validate if that transformation connects to a flat file that contains an empty date field.</span></span> <span data-ttu-id="42eff-113">转换是否有效取决于平面文件的连接管理器是否配置为保留 Null 值。</span><span class="sxs-lookup"><span data-stu-id="42eff-113">Whether the transformation validates depends on whether the connection manager for the flat file has been configured to retain null values.</span></span> <span data-ttu-id="42eff-114">若要确保查找转换有效，请在 **“连接管理器”** 页上的 **“平面文件源编辑器”** 中选择 **“在数据流中保留源中的 Null 值”** 选项。</span><span class="sxs-lookup"><span data-stu-id="42eff-114">To ensure that the Lookup transformation validates, in the **Flat File Source Editor**, on the **Connection Manager Page**, select the **Retain null values from the source as null values in the data flow** option.</span></span>  
  
4.  <span data-ttu-id="42eff-115">双击源或前一转换以配置组件。</span><span class="sxs-lookup"><span data-stu-id="42eff-115">Double-click the source or previous transformation to configure the component.</span></span>  
  
5.  <span data-ttu-id="42eff-116">双击查找转换，在“查找转换编辑器”  的“常规”  页上，选择“完全缓存”  。</span><span class="sxs-lookup"><span data-stu-id="42eff-116">Double-click the Lookup transformation, and then in the **Lookup Transformation Editor**, on the **General** page, select **Full cache**.</span></span>  
  
6.  <span data-ttu-id="42eff-117">在 **“连接类型”** 区域，选择 **“OLE DB 连接管理器”** 。</span><span class="sxs-lookup"><span data-stu-id="42eff-117">In the **Connection type** area, select **OLE DB connection manager**.</span></span>  
  
7.  <span data-ttu-id="42eff-118">在 **“指定如何处理无匹配项的行”** 列表中，为没有匹配项的行选择一个错误处理选项。</span><span class="sxs-lookup"><span data-stu-id="42eff-118">In the **Specify how to handle rows with no matching entries** list, select an error handling option for rows without matching entries.</span></span>  
  
8.  <span data-ttu-id="42eff-119">在“连接”页上，从 **“OLE DB 连接管理器”** 列表中选择一个连接管理器，或单击 **“新建”** 创建一个新的连接管理器。</span><span class="sxs-lookup"><span data-stu-id="42eff-119">On the Connection page, select a connection manager from the **OLE DB connection manager** list or click **New** to create a new connection manager.</span></span> <span data-ttu-id="42eff-120">有关详细信息，请参阅 [OLE DB Connection Manager](ole-db-connection-manager.md)。</span><span class="sxs-lookup"><span data-stu-id="42eff-120">For more information, see [OLE DB Connection Manager](ole-db-connection-manager.md).</span></span>  
  
9. <span data-ttu-id="42eff-121">执行下列任务之一：</span><span class="sxs-lookup"><span data-stu-id="42eff-121">Do one of the following tasks:</span></span>  
  
    -   <span data-ttu-id="42eff-122">单击 **“使用表或视图”** ，然后选择一个表或视图，或单击 **“新建”** 创建表或视图。</span><span class="sxs-lookup"><span data-stu-id="42eff-122">Click **Use a table or a view**, and then either select a table or view, or click **New** to create a table or view.</span></span>  
  
         <span data-ttu-id="42eff-123">-或-</span><span class="sxs-lookup"><span data-stu-id="42eff-123">-or-</span></span>  
  
    -   <span data-ttu-id="42eff-124">单击 **“使用 SQL 查询的结果”** ，然后在 **“SQL 命令”** 窗口中生成查询，或者单击 **“生成查询”** ，使用 **查询生成器** 提供的图形工具生成查询。</span><span class="sxs-lookup"><span data-stu-id="42eff-124">Click **Use results of an SQL query**, and then build a query in the **SQL Command** window, or click **Build Query** to build a query by using the graphical tools that the **Query Builder** provides.</span></span>  
  
         <span data-ttu-id="42eff-125">-或-</span><span class="sxs-lookup"><span data-stu-id="42eff-125">-or-</span></span>  
  
    -   <span data-ttu-id="42eff-126">或者，单击 **“浏览”** ，从文件中导入 SQL 语句。</span><span class="sxs-lookup"><span data-stu-id="42eff-126">Alternatively, click **Browse** to import an SQL statement from a file.</span></span>  
  
     <span data-ttu-id="42eff-127">若要验证 SQL 查询，请单击 **“分析查询”** 。</span><span class="sxs-lookup"><span data-stu-id="42eff-127">To validate the SQL query, click **Parse Query**.</span></span>  
  
     <span data-ttu-id="42eff-128">若要查看数据的示例，请单击 **“预览”** 。</span><span class="sxs-lookup"><span data-stu-id="42eff-128">To view a sample of the data, click **Preview**.</span></span>  
  
10. <span data-ttu-id="42eff-129">单击 **“列”** 页，然后将至少一列从 **“可用输入列”** 列表中拖动到 **“可用查找列”** 列表中的列。</span><span class="sxs-lookup"><span data-stu-id="42eff-129">Click the **Columns** page, and then from the **Available Input Columns** list, drag at least one column to a column in the **Available Lookup Column** list.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="42eff-130">查找转换自动映射具有相同名称和相同数据类型的列。</span><span class="sxs-lookup"><span data-stu-id="42eff-130">The Lookup transformation automatically maps columns that have the same name and the same data type.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="42eff-131">列必须含有要映射的匹配数据类型。</span><span class="sxs-lookup"><span data-stu-id="42eff-131">Columns must have matching data types to be mapped.</span></span> <span data-ttu-id="42eff-132">有关详细信息，请参阅 [Integration Services 数据类型](../data-flow/integration-services-data-types.md)。</span><span class="sxs-lookup"><span data-stu-id="42eff-132">For more information, see [Integration Services Data Types](../data-flow/integration-services-data-types.md).</span></span>  
  
11. <span data-ttu-id="42eff-133">执行以下任务在输出中包括查找列：</span><span class="sxs-lookup"><span data-stu-id="42eff-133">Include lookup columns in the output by doing the following tasks:</span></span>  
  
    1.  <span data-ttu-id="42eff-134">在 **“可用查找列”** 列表中。</span><span class="sxs-lookup"><span data-stu-id="42eff-134">In the **Available Lookup Columns** list.</span></span> <span data-ttu-id="42eff-135">选择列。</span><span class="sxs-lookup"><span data-stu-id="42eff-135">select columns.</span></span>  
  
    2.  <span data-ttu-id="42eff-136">在 **“查找操作”** 列表中，指定查找列中的值是替换输入列中的值还是写入到新列。</span><span class="sxs-lookup"><span data-stu-id="42eff-136">In **Lookup Operation** list, specify whether the values from the lookup columns replace values in the input column or are written to a new column.</span></span>  
  
12. <span data-ttu-id="42eff-137">若要配置错误输出，请单击 **“错误输出”** 页，并设置错误处理选项。</span><span class="sxs-lookup"><span data-stu-id="42eff-137">To configure the error output, click the **Error Output** page and set the error handling options.</span></span> <span data-ttu-id="42eff-138">有关详细信息，请参阅[查找转换编辑器（“错误输出”页）](../lookup-transformation-editor-error-output-page.md)。</span><span class="sxs-lookup"><span data-stu-id="42eff-138">For more information, see [Lookup Transformation Editor &#40;Error Output Page&#41;](../lookup-transformation-editor-error-output-page.md).</span></span>  
  
13. <span data-ttu-id="42eff-139">单击 **“确定”** 以保存对查找转换的更改，然后运行包。</span><span class="sxs-lookup"><span data-stu-id="42eff-139">Click **OK** to save your changes to the Lookup transformation, and then run the package.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="42eff-140">另请参阅</span><span class="sxs-lookup"><span data-stu-id="42eff-140">See Also</span></span>  
 <span data-ttu-id="42eff-141">[在完全缓存模式下使用缓存连接管理器实现查找转换](lookup-transformation-full-cache-mode-ole-db-connection-manager.md) </span><span class="sxs-lookup"><span data-stu-id="42eff-141">[Implement a Lookup Transformation in Full Cache Mode Using the Cache Connection Manager](lookup-transformation-full-cache-mode-ole-db-connection-manager.md) </span></span>  
 <span data-ttu-id="42eff-142">[在不缓存模式或部分缓存模式下实现查找](../data-flow/transformations/implement-a-lookup-in-no-cache-or-partial-cache-mode.md) </span><span class="sxs-lookup"><span data-stu-id="42eff-142">[Implement a Lookup in No Cache or Partial Cache Mode](../data-flow/transformations/implement-a-lookup-in-no-cache-or-partial-cache-mode.md) </span></span>  
 [<span data-ttu-id="42eff-143">Integration Services 转换</span><span class="sxs-lookup"><span data-stu-id="42eff-143">Integration Services Transformations</span></span>](../data-flow/transformations/integration-services-transformations.md)  
  
  
