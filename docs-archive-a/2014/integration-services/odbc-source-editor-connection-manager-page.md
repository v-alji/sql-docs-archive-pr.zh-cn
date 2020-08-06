---
title: ODBC 源编辑器 (连接管理器页) |Microsoft Docs
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.ssis.designer.odbcsource.connection.f1
ms.assetid: e2c8dc83-6394-4d6c-9232-97e94be72431
author: chugugrace
ms.author: chugu
ms.openlocfilehash: c8b54ce4a1c1b3fea0afb51f1cbf7447971ccab4
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87690750"
---
# <a name="odbc-source-editor-connection-manager-page"></a><span data-ttu-id="86181-102">ODBC 源编辑器（“连接管理器”页）</span><span class="sxs-lookup"><span data-stu-id="86181-102">ODBC Source Editor (Connection Manager Page)</span></span>
  <span data-ttu-id="86181-103">可以使用 **“ODBC 源编辑器”** 对话框的 **“连接管理器”** 页，为源选择 ODBC 连接管理器。</span><span class="sxs-lookup"><span data-stu-id="86181-103">Use the **Connection Manager** page of the **ODBC Source Editor** dialog box to select the ODBC connection manager for the source.</span></span> <span data-ttu-id="86181-104">使用此页还可以选择数据库中的表或视图。</span><span class="sxs-lookup"><span data-stu-id="86181-104">This page also lets you select a table or view from the database.</span></span>  
  
 <span data-ttu-id="86181-105">有关 ODBC 源的详细信息，请参阅 [ODBC Source](data-flow/odbc-source.md)。</span><span class="sxs-lookup"><span data-stu-id="86181-105">For more information about the ODBC source, see [ODBC Source](data-flow/odbc-source.md).</span></span>  
  
## <a name="task-list"></a><span data-ttu-id="86181-106">任务列表</span><span class="sxs-lookup"><span data-stu-id="86181-106">Task List</span></span>  
 <span data-ttu-id="86181-107">**打开“ODBC 源编辑器”的“连接管理器”页**</span><span class="sxs-lookup"><span data-stu-id="86181-107">**To open the ODBC Source Editor Connection Manager Page**</span></span>  
  
-   <span data-ttu-id="86181-108">在 [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)]中，打开具有 ODBC 源的 [!INCLUDE[ssISCurrent](../includes/ssiscurrent-md.md)] 包。</span><span class="sxs-lookup"><span data-stu-id="86181-108">In [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)], open the [!INCLUDE[ssISCurrent](../includes/ssiscurrent-md.md)] package that has the ODBC source.</span></span>  
  
-   <span data-ttu-id="86181-109">在“数据流”\*\*\*\* 选项卡上，双击 ODBC 源。</span><span class="sxs-lookup"><span data-stu-id="86181-109">On the **Data Flow** tab, double-click the ODBC source.</span></span>  
  
## <a name="options"></a><span data-ttu-id="86181-110">选项</span><span class="sxs-lookup"><span data-stu-id="86181-110">Options</span></span>  
  
### <a name="connection-manager"></a><span data-ttu-id="86181-111">“ODBC 源编辑器”</span><span class="sxs-lookup"><span data-stu-id="86181-111">Connection manager</span></span>  
 <span data-ttu-id="86181-112">从列表中选择现有 ODBC 连接管理器，或单击 "**新建**" 创建新连接。</span><span class="sxs-lookup"><span data-stu-id="86181-112">Select an existing ODBC connection manager from the list, or click **New** to create a new connection.</span></span> <span data-ttu-id="86181-113">该连接可以指向支持 ODBC 的任何数据库。</span><span class="sxs-lookup"><span data-stu-id="86181-113">The connection can be to any ODBC-supported database.</span></span>  
  
### <a name="new"></a><span data-ttu-id="86181-114">新建</span><span class="sxs-lookup"><span data-stu-id="86181-114">New</span></span>  
 <span data-ttu-id="86181-115">单击 **“新建”** 。</span><span class="sxs-lookup"><span data-stu-id="86181-115">Click **New**.</span></span> <span data-ttu-id="86181-116">**“配置 ODBC 连接管理器编辑器”** 对话框随即打开，供您在其中创建新的 ODBC 连接管理器。</span><span class="sxs-lookup"><span data-stu-id="86181-116">The **Configure ODBC Connection Manager Editor** dialog box opens where you can create a new ODBC connection manager.</span></span>  
  
### <a name="data-access-mode"></a><span data-ttu-id="86181-117">数据访问模式</span><span class="sxs-lookup"><span data-stu-id="86181-117">Data Access Mode</span></span>  
 <span data-ttu-id="86181-118">选择从源选择数据的方法。</span><span class="sxs-lookup"><span data-stu-id="86181-118">Select the method for selecting data from the source.</span></span> <span data-ttu-id="86181-119">选项显示在下表中：</span><span class="sxs-lookup"><span data-stu-id="86181-119">The options are shown in the following table:</span></span>  
  
|<span data-ttu-id="86181-120">选项</span><span class="sxs-lookup"><span data-stu-id="86181-120">Option</span></span>|<span data-ttu-id="86181-121">说明</span><span class="sxs-lookup"><span data-stu-id="86181-121">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="86181-122">表名称</span><span class="sxs-lookup"><span data-stu-id="86181-122">Table Name</span></span>|<span data-ttu-id="86181-123">从 ODBC 数据源中的表或视图检索数据。</span><span class="sxs-lookup"><span data-stu-id="86181-123">Retrieve data from a table or view in the ODBC data source.</span></span> <span data-ttu-id="86181-124">选择此选项后，请从列表中为以下选项选择一个值：</span><span class="sxs-lookup"><span data-stu-id="86181-124">When you select this option, select a value from the list for the following:</span></span>|  
||<span data-ttu-id="86181-125">**表或视图的名称**：从列表中选择一个可用表或视图，或键入正则表达式以标识该表。</span><span class="sxs-lookup"><span data-stu-id="86181-125">**Name of the table or the view**: Select an available table or view from the list or type a regular expression to identify the table.</span></span>|  
||<span data-ttu-id="86181-126">该列表仅包含前 1000 个表。</span><span class="sxs-lookup"><span data-stu-id="86181-126">This list contains the first 1000 tables only.</span></span> <span data-ttu-id="86181-127">如果您的数据库包含超过 1000 个表，则可以键入表名的开头，或者使用 (\*) 通配符输入名称的任何部分以便显示要使用的表。</span><span class="sxs-lookup"><span data-stu-id="86181-127">If your database contains more than 1000 tables, you can type the beginning of a table name or use the (\*) wild card to enter any part of the name to display the table or tables you want to use.</span></span>|  
|<span data-ttu-id="86181-128">SQL 命令</span><span class="sxs-lookup"><span data-stu-id="86181-128">SQL command</span></span>|<span data-ttu-id="86181-129">使用 SQL 查询从 ODBC 数据源中检索数据。</span><span class="sxs-lookup"><span data-stu-id="86181-129">Retrieve data from the ODBC data source by using an SQL query.</span></span> <span data-ttu-id="86181-130">您应该采用正在使用的源数据库的语法编写查询。</span><span class="sxs-lookup"><span data-stu-id="86181-130">You should write the query in the syntax of the source database you are working with.</span></span> <span data-ttu-id="86181-131">选择此选项后，请采用以下方法之一输入查询：</span><span class="sxs-lookup"><span data-stu-id="86181-131">When you select this option, enter a query in one of the following ways:</span></span>|  
||<span data-ttu-id="86181-132">在 **“SQL 命令文本”** 字段中，输入 SQL 查询的文本。</span><span class="sxs-lookup"><span data-stu-id="86181-132">Enter the text of the SQL query in the **SQL command text** field.</span></span>|  
||<span data-ttu-id="86181-133">单击 **“浏览”** 从文本文件加载 SQL 查询。</span><span class="sxs-lookup"><span data-stu-id="86181-133">Click **Browse** to load the SQL query from a text file.</span></span>|  
||<span data-ttu-id="86181-134">单击 **“分析查询”** 验证查询文本的语法。</span><span class="sxs-lookup"><span data-stu-id="86181-134">Click **Parse query** to verify the syntax of the query text.</span></span>|  
  
### <a name="preview"></a><span data-ttu-id="86181-135">预览</span><span class="sxs-lookup"><span data-stu-id="86181-135">Preview</span></span>  
 <span data-ttu-id="86181-136">单击 **“预览”** ，查看从选定的表或视图中提取的最多前 200 行数据。</span><span class="sxs-lookup"><span data-stu-id="86181-136">Click **Preview** to view up to the first 200 rows of the data extracted from the table or view you selected.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="86181-137">另请参阅</span><span class="sxs-lookup"><span data-stu-id="86181-137">See Also</span></span>  
 <span data-ttu-id="86181-138">[ODBC 源自定义属性](data-flow/odbc-source-custom-properties.md) </span><span class="sxs-lookup"><span data-stu-id="86181-138">[ODBC Source Custom Properties](data-flow/odbc-source-custom-properties.md) </span></span>  
 <span data-ttu-id="86181-139">[ODBC 源编辑器 &#40;列 "页&#41;](../../2014/integration-services/odbc-source-editor-columns-page.md) </span><span class="sxs-lookup"><span data-stu-id="86181-139">[ODBC Source Editor &#40;Columns Page&#41;](../../2014/integration-services/odbc-source-editor-columns-page.md) </span></span>  
 [<span data-ttu-id="86181-140">ODBC 源编辑器（“错误输出”页）</span><span class="sxs-lookup"><span data-stu-id="86181-140">ODBC Source Editor &#40;Error Output Page&#41;</span></span>](../../2014/integration-services/odbc-source-editor-error-output-page.md)  
  
  
