---
title: ADO NET 源编辑器 (连接管理器页) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.adonetsource.connection.f1
ms.assetid: 7de3f438-bdd6-49b5-937a-47369e754943
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 19dd9c256f15bc9022f7267cb38b6f91bd4d8a5c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87691840"
---
# <a name="ado-net-source-editor-connection-manager-page"></a><span data-ttu-id="3ecc8-102">ADO NET 源编辑器（“连接管理器”页）</span><span class="sxs-lookup"><span data-stu-id="3ecc8-102">ADO NET Source Editor (Connection Manager Page)</span></span>
  <span data-ttu-id="3ecc8-103">可以使用 **“ADO NET 源编辑器”** 对话框的 **“连接管理器”** 页，为源选择 [!INCLUDE[vstecado](../includes/vstecado-md.md)] 连接管理器。</span><span class="sxs-lookup"><span data-stu-id="3ecc8-103">Use the **Connection Manager** page of the **ADO NET Source Editor** dialog box to select the [!INCLUDE[vstecado](../includes/vstecado-md.md)] connection manager for the source.</span></span> <span data-ttu-id="3ecc8-104">使用此页还可以选择数据库中的表或视图。</span><span class="sxs-lookup"><span data-stu-id="3ecc8-104">This page also lets you select a table or view from the database.</span></span>  
  
 <span data-ttu-id="3ecc8-105">若要了解有关 ADO NET 源的详细信息，请参阅 [ADO NET Source](data-flow/ado-net-source.md)。</span><span class="sxs-lookup"><span data-stu-id="3ecc8-105">To learn more about the ADO NET source, see [ADO NET Source](data-flow/ado-net-source.md).</span></span>  
  
 <span data-ttu-id="3ecc8-106">**打开“连接管理器”页**</span><span class="sxs-lookup"><span data-stu-id="3ecc8-106">**To open the Connection Manager page**</span></span>  
  
1.  <span data-ttu-id="3ecc8-107">在 [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]中，打开具有 ADO NET 源的 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 包。</span><span class="sxs-lookup"><span data-stu-id="3ecc8-107">In [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)], open the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] package that has the ADO NET source.</span></span>  
  
2.  <span data-ttu-id="3ecc8-108">在“数据流”  选项卡上，双击 ADO NET 源。</span><span class="sxs-lookup"><span data-stu-id="3ecc8-108">On the **Data Flow** tab, double-click the ADO NET source.</span></span>  
  
3.  <span data-ttu-id="3ecc8-109">在 **“ADO NET 源编辑器”** 中，单击 **“连接管理器”** 。</span><span class="sxs-lookup"><span data-stu-id="3ecc8-109">In the **ADO NET Source Editor**, click **Connection Manager**.</span></span>  
  
## <a name="static-options"></a><span data-ttu-id="3ecc8-110">静态选项</span><span class="sxs-lookup"><span data-stu-id="3ecc8-110">Static Options</span></span>  
 <span data-ttu-id="3ecc8-111">**ADO.NET 连接管理器**</span><span class="sxs-lookup"><span data-stu-id="3ecc8-111">**ADO.NET connection manager**</span></span>  
 <span data-ttu-id="3ecc8-112">从列表中选择一个现有连接管理器，或通过单击“新建”  创建一个新连接。</span><span class="sxs-lookup"><span data-stu-id="3ecc8-112">Select an existing connection manager from the list, or create a new connection by clicking **New**.</span></span>  
  
 <span data-ttu-id="3ecc8-113">**新建**</span><span class="sxs-lookup"><span data-stu-id="3ecc8-113">**New**</span></span>  
 <span data-ttu-id="3ecc8-114">使用“配置 ADO.NET 连接管理器”  对话框创建新的连接管理器。</span><span class="sxs-lookup"><span data-stu-id="3ecc8-114">Create a new connection manager by using the **Configure ADO.NET Connection Manager** dialog box.</span></span>  
  
 <span data-ttu-id="3ecc8-115">**数据访问模式**</span><span class="sxs-lookup"><span data-stu-id="3ecc8-115">**Data access mode**</span></span>  
 <span data-ttu-id="3ecc8-116">指定从源选择数据的方法。</span><span class="sxs-lookup"><span data-stu-id="3ecc8-116">Specify the method for selecting data from the source.</span></span>  
  
|<span data-ttu-id="3ecc8-117">选项</span><span class="sxs-lookup"><span data-stu-id="3ecc8-117">Option</span></span>|<span data-ttu-id="3ecc8-118">说明</span><span class="sxs-lookup"><span data-stu-id="3ecc8-118">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="3ecc8-119">表或视图</span><span class="sxs-lookup"><span data-stu-id="3ecc8-119">Table or view</span></span>|<span data-ttu-id="3ecc8-120">从 [!INCLUDE[vstecado](../includes/vstecado-md.md)] 数据源中的表或视图中检索数据。</span><span class="sxs-lookup"><span data-stu-id="3ecc8-120">Retrieve data from a table or view in the [!INCLUDE[vstecado](../includes/vstecado-md.md)] data source.</span></span>|  
|<span data-ttu-id="3ecc8-121">SQL 命令</span><span class="sxs-lookup"><span data-stu-id="3ecc8-121">SQL command</span></span>|<span data-ttu-id="3ecc8-122">使用 SQL 查询从 [!INCLUDE[vstecado](../includes/vstecado-md.md)] 数据源中检索数据。</span><span class="sxs-lookup"><span data-stu-id="3ecc8-122">Retrieve data from the [!INCLUDE[vstecado](../includes/vstecado-md.md)] data source by using a SQL query.</span></span>|  
  
 <span data-ttu-id="3ecc8-123">**预览**</span><span class="sxs-lookup"><span data-stu-id="3ecc8-123">**Preview**</span></span>  
 <span data-ttu-id="3ecc8-124">通过使用“数据视图”  对话框预览结果。</span><span class="sxs-lookup"><span data-stu-id="3ecc8-124">Preview results by using the **Data View** dialog box.</span></span> <span data-ttu-id="3ecc8-125">**预览版** 最多可以显示 200 行。</span><span class="sxs-lookup"><span data-stu-id="3ecc8-125">**Preview** can display up to 200 rows.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="3ecc8-126">预览数据时，数据类型为 CLR 用户定义类型的列不包含数据。</span><span class="sxs-lookup"><span data-stu-id="3ecc8-126">When you preview data, columns with a CLR user-defined type do not contain data.</span></span> <span data-ttu-id="3ecc8-127">而是显示值 \<value too big to display> 或 System.Byte[]。</span><span class="sxs-lookup"><span data-stu-id="3ecc8-127">Instead the values \<value too big to display> or System.Byte[] display.</span></span> <span data-ttu-id="3ecc8-128">使用 [!INCLUDE[vstecado](../includes/vstecado-md.md)] 访问接口访问数据源时，显示前一个值；使用 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Native Client 访问接口访问数据源时，显示后一个值。</span><span class="sxs-lookup"><span data-stu-id="3ecc8-128">The former displays when the data source is accessed by using the [!INCLUDE[vstecado](../includes/vstecado-md.md)] provider, the latter when using the [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Native Client provider.</span></span>  
  
## <a name="data-access-mode-dynamic-options"></a><span data-ttu-id="3ecc8-129">数据访问模式动态选项</span><span class="sxs-lookup"><span data-stu-id="3ecc8-129">Data Access Mode Dynamic Options</span></span>  
  
### <a name="data-access-mode--table-or-view"></a><span data-ttu-id="3ecc8-130">数据访问模式 = 表或视图</span><span class="sxs-lookup"><span data-stu-id="3ecc8-130">Data access mode = Table or view</span></span>  
 <span data-ttu-id="3ecc8-131">**表或视图的名称**</span><span class="sxs-lookup"><span data-stu-id="3ecc8-131">**Name of the table or the view**</span></span>  
 <span data-ttu-id="3ecc8-132">从数据源的可用表列表或视图列表中选择表或视图的名称。</span><span class="sxs-lookup"><span data-stu-id="3ecc8-132">Select the name of the table or view from a list of those available in the data source.</span></span>  
  
### <a name="data-access-mode--sql-command"></a><span data-ttu-id="3ecc8-133">数据访问模式 = SQL 命令</span><span class="sxs-lookup"><span data-stu-id="3ecc8-133">Data access mode = SQL command</span></span>  
 <span data-ttu-id="3ecc8-134">**SQL 命令文本**</span><span class="sxs-lookup"><span data-stu-id="3ecc8-134">**SQL command text**</span></span>  
 <span data-ttu-id="3ecc8-135">输入 SQL 查询的文本，通过单击“生成查询”  来生成查询，或通过单击“浏览”  定位到包含查询文本的文件。</span><span class="sxs-lookup"><span data-stu-id="3ecc8-135">Enter the text of a SQL query, build the query by clicking **Build Query**, or locate the file that contains the query text by clicking **Browse**.</span></span>  
  
 <span data-ttu-id="3ecc8-136">**生成查询**</span><span class="sxs-lookup"><span data-stu-id="3ecc8-136">**Build query**</span></span>  
 <span data-ttu-id="3ecc8-137">使用“查询生成器”  对话框可直观地构造 SQL 查询。</span><span class="sxs-lookup"><span data-stu-id="3ecc8-137">Use the **Query Builder** dialog box to construct the SQL query visually.</span></span>  
  
 <span data-ttu-id="3ecc8-138">**“浏览”**</span><span class="sxs-lookup"><span data-stu-id="3ecc8-138">**Browse**</span></span>  
 <span data-ttu-id="3ecc8-139">使用“打开”  对话框可定位到包含 SQL 查询文本的文件。</span><span class="sxs-lookup"><span data-stu-id="3ecc8-139">Use the **Open** dialog box to locate the file that contains the text of the SQL query.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3ecc8-140">另请参阅</span><span class="sxs-lookup"><span data-stu-id="3ecc8-140">See Also</span></span>  
 <span data-ttu-id="3ecc8-141">[ADO NET 源编辑器 &#40;列 "页&#41;](../../2014/integration-services/ado-net-source-editor-columns-page.md) </span><span class="sxs-lookup"><span data-stu-id="3ecc8-141">[ADO NET Source Editor &#40;Columns Page&#41;](../../2014/integration-services/ado-net-source-editor-columns-page.md) </span></span>  
 <span data-ttu-id="3ecc8-142">[ADO NET 源编辑器 &#40;错误输出页&#41;](../../2014/integration-services/ado-net-source-editor-error-output-page.md) </span><span class="sxs-lookup"><span data-stu-id="3ecc8-142">[ADO NET Source Editor &#40;Error Output Page&#41;](../../2014/integration-services/ado-net-source-editor-error-output-page.md) </span></span>  
 [<span data-ttu-id="3ecc8-143">ADO.NET 连接管理器</span><span class="sxs-lookup"><span data-stu-id="3ecc8-143">ADO.NET Connection Manager</span></span>](connection-manager/ado-net-connection-manager.md)  
  
  
