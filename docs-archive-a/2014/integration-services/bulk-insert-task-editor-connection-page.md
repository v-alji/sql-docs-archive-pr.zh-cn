---
title: 大容量插入任务编辑器 (连接页) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.bulkinserttask.connection.f1
helpviewer_keywords:
- Bulk Insert Task Editor
ms.assetid: 51252c20-8865-4ede-a3fd-bd73a968f47d
author: chugugrace
ms.author: chugu
ms.openlocfilehash: b2cd722fd8520ff011c0d57040a55d624178e15e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87692498"
---
# <a name="bulk-insert-task-editor-connection-page"></a><span data-ttu-id="76e18-102">大容量插入任务编辑器（“连接”页）</span><span class="sxs-lookup"><span data-stu-id="76e18-102">Bulk Insert Task Editor (Connection Page)</span></span>
  <span data-ttu-id="76e18-103">可以使用 **“大容量插入任务编辑器”** 对话框的 **“连接”** 页，指定大容量插入操作的源和目标以及使用的格式。</span><span class="sxs-lookup"><span data-stu-id="76e18-103">Use the **Connection** page of the **Bulk Insert Task Editor** dialog box to specify the source and destination of the bulk insert operation and the format to use.</span></span>  
  
 <span data-ttu-id="76e18-104">若要了解大容量插入，请参阅[大容量插入任务](control-flow/bulk-insert-task.md)和[用来导入或导出数据的格式化文件 (SQL Server)](../relational-databases/import-export/format-files-for-importing-or-exporting-data-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="76e18-104">To learn about working with bulk inserts, see [Bulk Insert Task](control-flow/bulk-insert-task.md) and [Format Files for Importing or Exporting Data &#40;SQL Server&#41;](../relational-databases/import-export/format-files-for-importing-or-exporting-data-sql-server.md).</span></span>  
  
## <a name="options"></a><span data-ttu-id="76e18-105">选项</span><span class="sxs-lookup"><span data-stu-id="76e18-105">Options</span></span>  
 <span data-ttu-id="76e18-106">**Connection**</span><span class="sxs-lookup"><span data-stu-id="76e18-106">**Connection**</span></span>  
 <span data-ttu-id="76e18-107">从列表中选择一个 OLE DB 连接管理器，或单击“\<**New connection...**>创建新的连接。</span><span class="sxs-lookup"><span data-stu-id="76e18-107">Select an OLE DB connection manager in the list, or click \<**New connection...**> to create a new connection.</span></span>  
  
 <span data-ttu-id="76e18-108">**相关主题：** [OLE DB 连接管理器](connection-manager/ole-db-connection-manager.md)、[配置 OLE DB 连接管理器](../../2014/integration-services/configure-ole-db-connection-manager.md)</span><span class="sxs-lookup"><span data-stu-id="76e18-108">**Related Topics:** [OLE DB Connection Manager](connection-manager/ole-db-connection-manager.md), [Configure OLE DB Connection Manager](../../2014/integration-services/configure-ole-db-connection-manager.md)</span></span>  
  
 <span data-ttu-id="76e18-109">**DestinationTable**</span><span class="sxs-lookup"><span data-stu-id="76e18-109">**DestinationTable**</span></span>  
 <span data-ttu-id="76e18-110">键入目标表或视图的名称，或在列表中选择表或视图。</span><span class="sxs-lookup"><span data-stu-id="76e18-110">Type the name of the destination table or view or select a table or view in the list.</span></span>  
  
 <span data-ttu-id="76e18-111">**格式**</span><span class="sxs-lookup"><span data-stu-id="76e18-111">**Format**</span></span>  
 <span data-ttu-id="76e18-112">选择大容量插入任务的格式源。</span><span class="sxs-lookup"><span data-stu-id="76e18-112">Select the source of the format for the bulk insert.</span></span> <span data-ttu-id="76e18-113">此属性具有下表所列的选项。</span><span class="sxs-lookup"><span data-stu-id="76e18-113">This property has the options listed in the following table.</span></span>  
  
|<span data-ttu-id="76e18-114">值</span><span class="sxs-lookup"><span data-stu-id="76e18-114">Value</span></span>|<span data-ttu-id="76e18-115">说明</span><span class="sxs-lookup"><span data-stu-id="76e18-115">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="76e18-116">**使用文件**</span><span class="sxs-lookup"><span data-stu-id="76e18-116">**Use File**</span></span>|<span data-ttu-id="76e18-117">选择包含格式规范的文件。</span><span class="sxs-lookup"><span data-stu-id="76e18-117">Select a file containing the format specification.</span></span> <span data-ttu-id="76e18-118">选择此选项将显示动态选项 **FormatFile**。</span><span class="sxs-lookup"><span data-stu-id="76e18-118">Selecting this option displays the dynamic option, **FormatFile**.</span></span>|  
|<span data-ttu-id="76e18-119">**指定**</span><span class="sxs-lookup"><span data-stu-id="76e18-119">**Specify**</span></span>|<span data-ttu-id="76e18-120">指定格式。</span><span class="sxs-lookup"><span data-stu-id="76e18-120">Specify the format.</span></span> <span data-ttu-id="76e18-121">选择此选项将显示动态选项 `RowDelimiter` 和 `ColumnDelimiter` 。</span><span class="sxs-lookup"><span data-stu-id="76e18-121">Selecting this option displays the dynamic options, `RowDelimiter` and `ColumnDelimiter`.</span></span>|  
  
 <span data-ttu-id="76e18-122">**File**</span><span class="sxs-lookup"><span data-stu-id="76e18-122">**File**</span></span>  
 <span data-ttu-id="76e18-123">在列表中选择一个“文件连接管理器”或“平面文件连接管理器”，或单击“\<**New connection...**>”创建新的连接。</span><span class="sxs-lookup"><span data-stu-id="76e18-123">Select a File or Flat File connection manager in the list, or click \<**New connection...**> to create a new connection.</span></span>  
  
 <span data-ttu-id="76e18-124">文件位置与在此任务的连接管理器中指定的 SQL Server 数据库引擎有关。</span><span class="sxs-lookup"><span data-stu-id="76e18-124">The file location is relative to the SQL Server Database Engine specified in the connection manager for this task.</span></span> <span data-ttu-id="76e18-125">该文本文件必须可被服务器本地硬盘上的 SQL Server 数据库引擎访问，或可通过 SQL Server 的共享驱动器或映射的驱动器访问。</span><span class="sxs-lookup"><span data-stu-id="76e18-125">The text file must be accessible by the SQL Server Database Engine either on a local hard drive on the server, or via a share or mapped drive to the SQL Server.</span></span> <span data-ttu-id="76e18-126">SSIS 运行时不访问该文件。</span><span class="sxs-lookup"><span data-stu-id="76e18-126">The file is not accessed by the SSIS Runtime.</span></span>  
  
 <span data-ttu-id="76e18-127">如果通过使用平面文件连接管理器来访问源文件，则大容量插入任务不会使用在平面文件连接管理器中指定的格式。</span><span class="sxs-lookup"><span data-stu-id="76e18-127">If you access the source file by using a Flat File connection manager, the Bulk Insert task does not use the format specified in the Flat File connection manager.</span></span> <span data-ttu-id="76e18-128">相反，大容量插入任务将使用在格式化文件中指定的格式，或者使用该任务的 RowDelimite 和 ColumnDelimiter 属性的值。</span><span class="sxs-lookup"><span data-stu-id="76e18-128">Instead, the Bulk Insert task uses either the format specified in a format file or the values of the RowDelimiter and ColumnDelimiter properties of the task.</span></span>  
  
 <span data-ttu-id="76e18-129">**相关主题：** [文件连接管理器](connection-manager/file-connection-manager.md)、[文件连接管理器编辑器](../../2014/integration-services/file-connection-manager-editor.md)、[平面文件连接管理器](connection-manager/flat-file-connection-manager.md)、[平面文件连接管理器编辑器（“常规”页）](general-page-of-integration-services-designers-options.md)、[平面文件连接管理器编辑器（“列”页）](../../2014/integration-services/flat-file-connection-manager-editor-columns-page.md)、[平面文件连接管理器编辑器（“高级”页）](../../2014/integration-services/flat-file-connection-manager-editor-advanced-page.md)</span><span class="sxs-lookup"><span data-stu-id="76e18-129">**Related Topics:** [File Connection Manager](connection-manager/file-connection-manager.md), [File Connection Manager Editor](../../2014/integration-services/file-connection-manager-editor.md), [Flat File Connection Manager](connection-manager/flat-file-connection-manager.md), [Flat File Connection Manager Editor &#40;General Page&#41;](general-page-of-integration-services-designers-options.md), [Flat File Connection Manager Editor &#40;Columns Page&#41;](../../2014/integration-services/flat-file-connection-manager-editor-columns-page.md), [Flat File Connection Manager Editor &#40;Advanced Page&#41;](../../2014/integration-services/flat-file-connection-manager-editor-advanced-page.md)</span></span>  
  
 <span data-ttu-id="76e18-130">**刷新表**</span><span class="sxs-lookup"><span data-stu-id="76e18-130">**Refresh Tables**</span></span>  
 <span data-ttu-id="76e18-131">刷新表和视图的列表。</span><span class="sxs-lookup"><span data-stu-id="76e18-131">Refresh the list of tables and views.</span></span>  
  
## <a name="format-dynamic-options"></a><span data-ttu-id="76e18-132">Format 动态选项</span><span class="sxs-lookup"><span data-stu-id="76e18-132">Format Dynamic Options</span></span>  
  
### <a name="format--use-file"></a><span data-ttu-id="76e18-133">Format = 使用文件</span><span class="sxs-lookup"><span data-stu-id="76e18-133">Format = Use File</span></span>  
 <span data-ttu-id="76e18-134">**FormatFile**</span><span class="sxs-lookup"><span data-stu-id="76e18-134">**FormatFile**</span></span>  
 <span data-ttu-id="76e18-135">键入格式化文件的路径，或单击省略号按钮“(…)”定位到该格式化文件  。</span><span class="sxs-lookup"><span data-stu-id="76e18-135">Type the path of the format file or click the ellipsis button **(...)** to locate the format file.</span></span>  
  
### <a name="format--specify"></a><span data-ttu-id="76e18-136">Format = 指定</span><span class="sxs-lookup"><span data-stu-id="76e18-136">Format = Specify</span></span>  
 `RowDelimiter`  
 <span data-ttu-id="76e18-137">指定源文件中的行分隔符。</span><span class="sxs-lookup"><span data-stu-id="76e18-137">Specify the row delimiter in the source file.</span></span> <span data-ttu-id="76e18-138">默认值为 **{CR}{LF}** 。</span><span class="sxs-lookup"><span data-stu-id="76e18-138">The default value is **{CR}{LF}**.</span></span>  
  
 `ColumnDelimiter`  
 <span data-ttu-id="76e18-139">指定源文件中的列分隔符。</span><span class="sxs-lookup"><span data-stu-id="76e18-139">Specify the column delimiter in the source file.</span></span> <span data-ttu-id="76e18-140">默认值为 **“制表符”** 。</span><span class="sxs-lookup"><span data-stu-id="76e18-140">The default is **Tab**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="76e18-141">另请参阅</span><span class="sxs-lookup"><span data-stu-id="76e18-141">See Also</span></span>  
 <span data-ttu-id="76e18-142">[Integration Services 错误和消息引用](../../2014/integration-services/integration-services-error-and-message-reference.md) </span><span class="sxs-lookup"><span data-stu-id="76e18-142">[Integration Services Error and Message Reference](../../2014/integration-services/integration-services-error-and-message-reference.md) </span></span>  
 <span data-ttu-id="76e18-143">[大容量插入任务编辑器 &#40;常规页&#41;](../../2014/integration-services/bulk-insert-task-editor-general-page.md) </span><span class="sxs-lookup"><span data-stu-id="76e18-143">[Bulk Insert Task Editor &#40;General Page&#41;](../../2014/integration-services/bulk-insert-task-editor-general-page.md) </span></span>  
 <span data-ttu-id="76e18-144">[大容量插入任务编辑器 &#40;选项 "页面&#41;](../../2014/integration-services/bulk-insert-task-editor-options-page.md) </span><span class="sxs-lookup"><span data-stu-id="76e18-144">[Bulk Insert Task Editor &#40;Options Page&#41;](../../2014/integration-services/bulk-insert-task-editor-options-page.md) </span></span>  
 <span data-ttu-id="76e18-145">[“表达式”页](expressions/expressions-page.md) </span><span class="sxs-lookup"><span data-stu-id="76e18-145">[Expressions Page](expressions/expressions-page.md) </span></span>  
 <span data-ttu-id="76e18-146">[BULK INSERT (Transact-SQL)](/sql/t-sql/statements/bulk-insert-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="76e18-146">[BULK INSERT &#40;Transact-SQL&#41;](/sql/t-sql/statements/bulk-insert-transact-sql) </span></span>  
 [<span data-ttu-id="76e18-147">控制流</span><span class="sxs-lookup"><span data-stu-id="76e18-147">Control Flow</span></span>](control-flow/control-flow.md)  
  
  
