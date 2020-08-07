---
title: ODBC 目标编辑器 (连接管理器页) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.ssis.designer.odbcdest.connection.f1
ms.assetid: f6d9c6c2-e4c4-468b-9e0d-af7b9609614d
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 6e4fc1073bb187c0864d2991459a358a7f81d066
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87690756"
---
# <a name="odbc-destination-editor-connection-manager-page"></a><span data-ttu-id="0cb84-102">ODBC 目标编辑器（“连接管理器”页）</span><span class="sxs-lookup"><span data-stu-id="0cb84-102">ODBC Destination Editor (Connection Manager Page)</span></span>
  <span data-ttu-id="0cb84-103">可以使用 **“ODBC 目标编辑器”** 对话框的 **“连接管理器”** 页，为目标选择 ODBC 连接管理器。</span><span class="sxs-lookup"><span data-stu-id="0cb84-103">Use the **Connection Manager** page of the **ODBC Destination Editor** dialog box to select the ODBC connection manager for the destination.</span></span> <span data-ttu-id="0cb84-104">使用此页还可以选择数据库中的表或视图。</span><span class="sxs-lookup"><span data-stu-id="0cb84-104">This page also lets you select a table or view from the database</span></span>  
  
 <span data-ttu-id="0cb84-105">有关 ODBC 目标的详细信息，请参阅 [ODBC Destination](data-flow/odbc-destination.md)。</span><span class="sxs-lookup"><span data-stu-id="0cb84-105">For more information about the ODBC destination, see [ODBC Destination](data-flow/odbc-destination.md).</span></span>  
  
 <span data-ttu-id="0cb84-106">**打开“ODBC 目标编辑器”的“连接管理器”页**</span><span class="sxs-lookup"><span data-stu-id="0cb84-106">**To open the ODBC Destination Editor Connection Manager Page**</span></span>  
  
## <a name="task-list"></a><span data-ttu-id="0cb84-107">任务列表</span><span class="sxs-lookup"><span data-stu-id="0cb84-107">Task List</span></span>  
  
-   <span data-ttu-id="0cb84-108">在 [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)]中，打开包含 ODBC 目标的 [!INCLUDE[ssISCurrent](../includes/ssiscurrent-md.md)] 包。</span><span class="sxs-lookup"><span data-stu-id="0cb84-108">In [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)], open the [!INCLUDE[ssISCurrent](../includes/ssiscurrent-md.md)] package that has the ODBC destination.</span></span>  
  
-   <span data-ttu-id="0cb84-109">在“数据流”  选项卡上，双击 ODBC 目标。</span><span class="sxs-lookup"><span data-stu-id="0cb84-109">On the **Data Flow** tab, double-click the ODBC destination.</span></span>  
  
-   <span data-ttu-id="0cb84-110">在 **“ODBC 目标编辑器”** 中，单击 **“连接管理器”** 。</span><span class="sxs-lookup"><span data-stu-id="0cb84-110">In the **ODBC Destination Editor**, click **Connection Manager**.</span></span>  
  
## <a name="options"></a><span data-ttu-id="0cb84-111">选项</span><span class="sxs-lookup"><span data-stu-id="0cb84-111">Options</span></span>  
  
### <a name="connection-manager"></a><span data-ttu-id="0cb84-112">“ODBC 源编辑器”</span><span class="sxs-lookup"><span data-stu-id="0cb84-112">Connection manager</span></span>  
 <span data-ttu-id="0cb84-113">从列表中选择现有 ODBC 连接管理器，或单击“新建”创建新的连接。</span><span class="sxs-lookup"><span data-stu-id="0cb84-113">Select an existing ODBC connection manager from the list, or click New to create a new connection.</span></span> <span data-ttu-id="0cb84-114">该连接可以指向支持 ODBC 的任何数据库。</span><span class="sxs-lookup"><span data-stu-id="0cb84-114">The connection can be to any ODBC-supported database.</span></span>  
  
### <a name="new"></a><span data-ttu-id="0cb84-115">新建</span><span class="sxs-lookup"><span data-stu-id="0cb84-115">New</span></span>  
 <span data-ttu-id="0cb84-116">单击 **“新建”** 。</span><span class="sxs-lookup"><span data-stu-id="0cb84-116">Click **New**.</span></span> <span data-ttu-id="0cb84-117">**“配置 ODBC 连接管理器编辑器”** 对话框随即打开，供您在其中创建新的连接管理器。</span><span class="sxs-lookup"><span data-stu-id="0cb84-117">The **Configure ODBC Connection Manager Editor** dialog box opens where you can create a new connection manager.</span></span>  
  
### <a name="data-access-mode"></a><span data-ttu-id="0cb84-118">数据访问模式</span><span class="sxs-lookup"><span data-stu-id="0cb84-118">Data Access Mode</span></span>  
 <span data-ttu-id="0cb84-119">选择将数据加载到目标的方法。</span><span class="sxs-lookup"><span data-stu-id="0cb84-119">Select the method for loading data to the destination.</span></span> <span data-ttu-id="0cb84-120">选项显示在下表中：</span><span class="sxs-lookup"><span data-stu-id="0cb84-120">The options are shown in the following table:</span></span>  
  
|<span data-ttu-id="0cb84-121">选项</span><span class="sxs-lookup"><span data-stu-id="0cb84-121">Option</span></span>|<span data-ttu-id="0cb84-122">说明</span><span class="sxs-lookup"><span data-stu-id="0cb84-122">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="0cb84-123">表名 - 批处理</span><span class="sxs-lookup"><span data-stu-id="0cb84-123">Table Name - Batch</span></span>|<span data-ttu-id="0cb84-124">选择此选项可将 ODBC 目标配置为在批处理模式下工作。</span><span class="sxs-lookup"><span data-stu-id="0cb84-124">Select this option to configure the ODBC destination to work in batch mode.</span></span> <span data-ttu-id="0cb84-125">选择此选项后，以下选项可用：</span><span class="sxs-lookup"><span data-stu-id="0cb84-125">When you select this option the following options are available:</span></span>|  
||<span data-ttu-id="0cb84-126">**表或视图的名称**：从列表中选择可用的表或视图。</span><span class="sxs-lookup"><span data-stu-id="0cb84-126">**Name of the table or the view**: Select an available table or view from the list.</span></span><br /><br /> <span data-ttu-id="0cb84-127">该列表仅包含前 1000 个表。</span><span class="sxs-lookup"><span data-stu-id="0cb84-127">This list contains the first 1000 tables only.</span></span> <span data-ttu-id="0cb84-128">如果你的数据库包含超过 1000 个表，则可以键入表名的开头，或者使用 (\*) 通配符输入名称的任何部分以便显示要使用的表。</span><span class="sxs-lookup"><span data-stu-id="0cb84-128">If your database contains more than 1000 tables, you can type the beginning of a table name or use the (\*) wild card to enter any part of the name to display the table or tables you want to use.</span></span><br /><br /> <span data-ttu-id="0cb84-129">**批大小**：键入用于大容量加载的批处理的大小。</span><span class="sxs-lookup"><span data-stu-id="0cb84-129">**Batch size**: Type the size of the batch for bulk loading.</span></span> <span data-ttu-id="0cb84-130">这是作为一批加载的行数。</span><span class="sxs-lookup"><span data-stu-id="0cb84-130">This is the number of rows loaded as a batch</span></span>|  
|<span data-ttu-id="0cb84-131">表名 - 逐行</span><span class="sxs-lookup"><span data-stu-id="0cb84-131">Table Name - Row by Row</span></span>|<span data-ttu-id="0cb84-132">选择此选项可以将 ODBC 目标配置为一次一行将各行插入目标表中。</span><span class="sxs-lookup"><span data-stu-id="0cb84-132">Select this option to configure the ODBC destination to insert each of the rows into the destination table one at a time.</span></span> <span data-ttu-id="0cb84-133">选择此选项后，以下选项可用：</span><span class="sxs-lookup"><span data-stu-id="0cb84-133">When you select this option the following option is available:</span></span>|  
||<span data-ttu-id="0cb84-134">**表或视图的名称**：从列表中选择数据库中的可用表或视图。</span><span class="sxs-lookup"><span data-stu-id="0cb84-134">**Name of the table or the view**: Select an available table or view from the database from the list.</span></span><br /><br /> <span data-ttu-id="0cb84-135">该列表仅包含前 1000 个表。</span><span class="sxs-lookup"><span data-stu-id="0cb84-135">This list contains the first 1000 tables only.</span></span> <span data-ttu-id="0cb84-136">如果您的数据库包含超过 1000 个表，则可以键入表名的开头，或者使用 (\*) 通配符输入名称的任何部分以便显示要使用的表。</span><span class="sxs-lookup"><span data-stu-id="0cb84-136">If your database contains more than 1000 tables, you can type the beginning of a table name or use the (\*) wild card to enter any part of the name to display the table or tables you want to use.</span></span>|  
  
### <a name="preview"></a><span data-ttu-id="0cb84-137">预览</span><span class="sxs-lookup"><span data-stu-id="0cb84-137">Preview</span></span>  
 <span data-ttu-id="0cb84-138">单击 **“预览”** 可以查看所选表的最多 200 行数据。</span><span class="sxs-lookup"><span data-stu-id="0cb84-138">Click **Preview** to view up to 200 rows of data for the table that you selected.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0cb84-139">另请参阅</span><span class="sxs-lookup"><span data-stu-id="0cb84-139">See Also</span></span>  
 <span data-ttu-id="0cb84-140">[ODBC 目标自定义属性](data-flow/odbc-destination-custom-properties.md) </span><span class="sxs-lookup"><span data-stu-id="0cb84-140">[ODBC Destination Custom Properties](data-flow/odbc-destination-custom-properties.md) </span></span>  
 <span data-ttu-id="0cb84-141">[ODBC 目标编辑器 &#40;映射 "页面&#41;](../../2014/integration-services/odbc-destination-editor-mappings-page.md) </span><span class="sxs-lookup"><span data-stu-id="0cb84-141">[ODBC Destination Editor &#40;Mappings Page&#41;](../../2014/integration-services/odbc-destination-editor-mappings-page.md) </span></span>  
 [<span data-ttu-id="0cb84-142">ODBC 目标编辑器（“错误输出”页）</span><span class="sxs-lookup"><span data-stu-id="0cb84-142">ODBC Destination Editor &#40;Error Output Page&#41;</span></span>](../../2014/integration-services/odbc-destination-editor-error-output-page.md)  
  
  
