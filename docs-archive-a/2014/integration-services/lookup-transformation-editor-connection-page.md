---
title: 查找转换编辑器 (连接页) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.lookuptransformation.referencetable.f1
helpviewer_keywords:
- Lookup Transformation Editor
ms.assetid: e90d6b69-5a26-43c5-8433-5c3c9588e08c
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 381378ac1aca85c6bca825033bc439ebc39fb063
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87586802"
---
# <a name="lookup-transformation-editor-connection-page"></a><span data-ttu-id="e7a02-102">查找转换编辑器（“连接”页）</span><span class="sxs-lookup"><span data-stu-id="e7a02-102">Lookup Transformation Editor (Connection Page)</span></span>
  <span data-ttu-id="e7a02-103">可以使用 **“查找转换编辑器”** 对话框的 **“连接”** 页选择连接管理器。</span><span class="sxs-lookup"><span data-stu-id="e7a02-103">Use the **Connection** page of the **Lookup Transformation Editor** dialog box to select a connection manager.</span></span> <span data-ttu-id="e7a02-104">在选择 OLE DB 连接管理器时，会同时选择用来生成引用数据集的查询、表或视图。</span><span class="sxs-lookup"><span data-stu-id="e7a02-104">If you select an OLE DB connection manager, you also select a query, table, or view to generate the reference dataset.</span></span>  
  
 <span data-ttu-id="e7a02-105">若要了解有关查找转换的详细信息，请参阅 [Lookup Transformation](data-flow/transformations/lookup-transformation.md)。</span><span class="sxs-lookup"><span data-stu-id="e7a02-105">To learn more about the Lookup transformation, see [Lookup Transformation](data-flow/transformations/lookup-transformation.md).</span></span>  
  
## <a name="options"></a><span data-ttu-id="e7a02-106">选项</span><span class="sxs-lookup"><span data-stu-id="e7a02-106">Options</span></span>  
 <span data-ttu-id="e7a02-107">在 **“查找转换编辑器”** 对话框的“常规”页上选择 **“完全缓存”** 和 **“缓存连接管理器”** 时，下列选项可用：</span><span class="sxs-lookup"><span data-stu-id="e7a02-107">The following options are available when you select **Full cache** and **Cache connection manager** on the General page of the **Lookup Transformation Editor** dialog box.</span></span>  
  
 <span data-ttu-id="e7a02-108">**缓存连接管理器**</span><span class="sxs-lookup"><span data-stu-id="e7a02-108">**Cache connection manager**</span></span>  
 <span data-ttu-id="e7a02-109">从列表中选择现有的缓存连接管理器，或单击“新建”\*\*\*\* 创建一个新连接。</span><span class="sxs-lookup"><span data-stu-id="e7a02-109">Select an existing Cache connection manager from the list, or create a new connection by clicking **New**.</span></span>  
  
 <span data-ttu-id="e7a02-110">**新建**</span><span class="sxs-lookup"><span data-stu-id="e7a02-110">**New**</span></span>  
 <span data-ttu-id="e7a02-111">使用“缓存连接管理器编辑器”\*\*\*\* 对话框创建新的连接。</span><span class="sxs-lookup"><span data-stu-id="e7a02-111">Create a new connection by using the **Cache Connection Manager Editor** dialog box.</span></span>  
  
 <span data-ttu-id="e7a02-112">在 **“查找转换编辑器”** 对话框的“常规”页上选择 **“完全缓存”**、 **“部分缓存”** 或 **“无缓存”** 以及 **“OLE DB 连接管理器”** 时，下列选项可用：</span><span class="sxs-lookup"><span data-stu-id="e7a02-112">The following options are available when you select **Full cache**, **Partial cache**, or **No cache**, and **OLE DB connection manager**, on the General page of the **Lookup Transformation Editor** dialog box.</span></span>  
  
 <span data-ttu-id="e7a02-113">**“无缓存”**</span><span class="sxs-lookup"><span data-stu-id="e7a02-113">**OLE DB connection manager**</span></span>  
 <span data-ttu-id="e7a02-114">从列表中选择现有的 OLE DB 连接管理器，或通过单击“新建”\*\*\*\* 创建一个新连接。</span><span class="sxs-lookup"><span data-stu-id="e7a02-114">Select an existing OLE DB connection manager from the list, or create a new connection by clicking **New**.</span></span>  
  
 <span data-ttu-id="e7a02-115">**新建**</span><span class="sxs-lookup"><span data-stu-id="e7a02-115">**New**</span></span>  
 <span data-ttu-id="e7a02-116">通过使用“配置 OLE DB 连接管理器”  对话框创建新的连接。</span><span class="sxs-lookup"><span data-stu-id="e7a02-116">Create a new connection by using the **Configure OLE DB Connection Manager** dialog box.</span></span>  
  
 <span data-ttu-id="e7a02-117">**使用表或视图**</span><span class="sxs-lookup"><span data-stu-id="e7a02-117">**Use a table or view**</span></span>  
 <span data-ttu-id="e7a02-118">从列表中选择现有表或视图，或单击 "**新建**" 创建新表。</span><span class="sxs-lookup"><span data-stu-id="e7a02-118">Select an existing table or view from the list, or create a new table by clicking **New**.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="e7a02-119">在此处选择的表名将由在 **“查找转换编辑器”** 的 **“高级”** 页上指定的 SQL 语句覆盖和替换。</span><span class="sxs-lookup"><span data-stu-id="e7a02-119">If you specify a SQL statement on the **Advanced** page of the **Lookup Transformation Editor**, that SQL statement overrides and replaces the table name selected here.</span></span> <span data-ttu-id="e7a02-120">有关详细信息，请参阅 [查找转换编辑器（“高级”页）](../../2014/integration-services/lookup-transformation-editor-advanced-page.md)。</span><span class="sxs-lookup"><span data-stu-id="e7a02-120">For more information, see [Lookup Transformation Editor &#40;Advanced Page&#41;](../../2014/integration-services/lookup-transformation-editor-advanced-page.md).</span></span>  
  
 <span data-ttu-id="e7a02-121">**新建**</span><span class="sxs-lookup"><span data-stu-id="e7a02-121">**New**</span></span>  
 <span data-ttu-id="e7a02-122">通过使用“创建表”  对话框创建一个新表。</span><span class="sxs-lookup"><span data-stu-id="e7a02-122">Create a new table by using the **Create Table** dialog box.</span></span>  
  
 <span data-ttu-id="e7a02-123">**使用 SQL 查询的结果**</span><span class="sxs-lookup"><span data-stu-id="e7a02-123">**Use results of an SQL query**</span></span>  
 <span data-ttu-id="e7a02-124">选择该选项后，可以通过浏览找到预先存在的查询、生成一个新查询、检查查询语法，然后预览查询结果。</span><span class="sxs-lookup"><span data-stu-id="e7a02-124">Choose this option to browse to a preexisting query, build a new query, check query syntax, and preview query results.</span></span>  
  
 <span data-ttu-id="e7a02-125">**生成查询**</span><span class="sxs-lookup"><span data-stu-id="e7a02-125">**Build query**</span></span>  
 <span data-ttu-id="e7a02-126">通过使用“查询生成器”\*\*\*\* 可以创建要运行的 Transact-SQL 语句，查询生成器是一个用于通过浏览数据来创建查询的图形工具。</span><span class="sxs-lookup"><span data-stu-id="e7a02-126">Create the Transact-SQL statement to run by using **Query Builder**, a graphical tool that is used to create queries by browsing through data.</span></span>  
  
 <span data-ttu-id="e7a02-127">**“浏览”**</span><span class="sxs-lookup"><span data-stu-id="e7a02-127">**Browse**</span></span>  
 <span data-ttu-id="e7a02-128">使用此选项可以找到保存为文件的预先存在的查询。</span><span class="sxs-lookup"><span data-stu-id="e7a02-128">Use this option to browse to a preexisting query saved as a file.</span></span>  
  
 <span data-ttu-id="e7a02-129">**分析查询**</span><span class="sxs-lookup"><span data-stu-id="e7a02-129">**Parse Query**</span></span>  
 <span data-ttu-id="e7a02-130">检查查询的语法。</span><span class="sxs-lookup"><span data-stu-id="e7a02-130">Check the syntax of the query.</span></span>  
  
 <span data-ttu-id="e7a02-131">**预览**</span><span class="sxs-lookup"><span data-stu-id="e7a02-131">**Preview**</span></span>  
 <span data-ttu-id="e7a02-132">使用“预览查询结果”  对话框预览结果。</span><span class="sxs-lookup"><span data-stu-id="e7a02-132">Preview results by using the **Preview Query Results** dialog box.</span></span> <span data-ttu-id="e7a02-133">此选项最多可以显示 200 行。</span><span class="sxs-lookup"><span data-stu-id="e7a02-133">This option displays up to 200 rows.</span></span>  
  
## <a name="external-resources"></a><span data-ttu-id="e7a02-134">外部资源</span><span class="sxs-lookup"><span data-stu-id="e7a02-134">External Resources</span></span>  
 <span data-ttu-id="e7a02-135">blogs.msdn.com 上的博客文章： [查找缓存模式](https://go.microsoft.com/fwlink/?LinkId=219518)</span><span class="sxs-lookup"><span data-stu-id="e7a02-135">Blog entry, [Lookup cache modes](https://go.microsoft.com/fwlink/?LinkId=219518) on blogs.msdn.com</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e7a02-136">另请参阅</span><span class="sxs-lookup"><span data-stu-id="e7a02-136">See Also</span></span>  
 <span data-ttu-id="e7a02-137">[查找转换编辑器 &#40;常规页&#41;](general-page-of-integration-services-designers-options.md) </span><span class="sxs-lookup"><span data-stu-id="e7a02-137">[Lookup Transformation Editor &#40;General Page&#41;](general-page-of-integration-services-designers-options.md) </span></span>  
 <span data-ttu-id="e7a02-138">[查找转换编辑器 &#40;列 "页&#41;](../../2014/integration-services/lookup-transformation-editor-columns-page.md) </span><span class="sxs-lookup"><span data-stu-id="e7a02-138">[Lookup Transformation Editor &#40;Columns Page&#41;](../../2014/integration-services/lookup-transformation-editor-columns-page.md) </span></span>  
 <span data-ttu-id="e7a02-139">[查找转换编辑器 &#40;高级页面&#41;](../../2014/integration-services/lookup-transformation-editor-advanced-page.md) </span><span class="sxs-lookup"><span data-stu-id="e7a02-139">[Lookup Transformation Editor &#40;Advanced Page&#41;](../../2014/integration-services/lookup-transformation-editor-advanced-page.md) </span></span>  
 <span data-ttu-id="e7a02-140">[查找转换编辑器 &#40;错误输出页&#41;](../../2014/integration-services/lookup-transformation-editor-error-output-page.md) </span><span class="sxs-lookup"><span data-stu-id="e7a02-140">[Lookup Transformation Editor &#40;Error Output Page&#41;](../../2014/integration-services/lookup-transformation-editor-error-output-page.md) </span></span>  
 [<span data-ttu-id="e7a02-141">模糊查找转换</span><span class="sxs-lookup"><span data-stu-id="e7a02-141">Fuzzy Lookup Transformation</span></span>](data-flow/transformations/fuzzy-lookup-transformation.md)  
  
  
