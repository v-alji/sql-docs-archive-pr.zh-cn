---
title: OLE DB 源编辑器 ("连接管理器" 页) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.oledbsourceadapter.connection.f1
helpviewer_keywords:
- OLE DB Source Editor
ms.assetid: 53699902-8699-4547-b56b-a5b2079e98b6
author: chugugrace
ms.author: chugu
ms.openlocfilehash: e6b9d841ff902107847a9d85779af41f476315db
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87590291"
---
# <a name="ole-db-source-editor-connection-manager-page"></a><span data-ttu-id="c4269-102">OLE DB 源编辑器（“连接管理器”页）</span><span class="sxs-lookup"><span data-stu-id="c4269-102">OLE DB Source Editor (Connection Manager Page)</span></span>
  <span data-ttu-id="c4269-103">可以使用 **“OLE DB 源编辑器”** 对话框的 **“连接管理器”** 页，为源选择 OLE DB 连接管理器。</span><span class="sxs-lookup"><span data-stu-id="c4269-103">Use the **Connection Manager** page of the **OLE DB Source Editor** dialog box to select the OLE DB connection manager for the source.</span></span> <span data-ttu-id="c4269-104">使用此页还可以选择数据库中的表或视图。</span><span class="sxs-lookup"><span data-stu-id="c4269-104">This page also lets you select a table or view from the database.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="c4269-105">若要从使用 [!INCLUDE[msCoName](../includes/msconame-md.md)] Office Excel 2007 的数据源加载数据，请使用 OLE DB 源。</span><span class="sxs-lookup"><span data-stu-id="c4269-105">To load data from a data source that uses [!INCLUDE[msCoName](../includes/msconame-md.md)] Office Excel 2007, use an OLE DB source.</span></span> <span data-ttu-id="c4269-106">使用 Excel 源无法从 Excel 2007 数据源加载数据。</span><span class="sxs-lookup"><span data-stu-id="c4269-106">You cannot use an Excel source to load data from an Excel 2007 data source.</span></span> <span data-ttu-id="c4269-107">有关详细信息，请参阅 [Configure OLE DB Connection Manager](configure-ole-db-connection-manager.md)。</span><span class="sxs-lookup"><span data-stu-id="c4269-107">For more information, see [Configure OLE DB Connection Manager](configure-ole-db-connection-manager.md).</span></span>  
>   
>  <span data-ttu-id="c4269-108">若要从使用 [!INCLUDE[msCoName](../includes/msconame-md.md)] Office Excel 2003 或更低版本的数据源加载数据，请使用 Excel 源。</span><span class="sxs-lookup"><span data-stu-id="c4269-108">To load data from a data source that uses [!INCLUDE[msCoName](../includes/msconame-md.md)] Office Excel 2003 or earlier, use an Excel source.</span></span> <span data-ttu-id="c4269-109">有关详细信息，请参阅 [Excel 源编辑器（“连接管理器”页）](../../2014/integration-services/excel-source-editor-connection-manager-page.md)。</span><span class="sxs-lookup"><span data-stu-id="c4269-109">For more information, see [Excel Source Editor &#40;Connection Manager Page&#41;](../../2014/integration-services/excel-source-editor-connection-manager-page.md).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="c4269-110">`CommandTimeout`OLE DB 源的属性在**OLE DB 源编辑器**中不可用，但可以使用**高级编辑器**进行设置。</span><span class="sxs-lookup"><span data-stu-id="c4269-110">The `CommandTimeout` property of the OLE DB source is not available in the **OLE DB Source Editor**, but can be set by using the **Advanced Editor**.</span></span> <span data-ttu-id="c4269-111">有关此属性的详细信息，请参阅 [OLE DB Custom Properties](data-flow/ole-db-custom-properties.md)的“Excel 源”部分。</span><span class="sxs-lookup"><span data-stu-id="c4269-111">For more information on this property, see the Excel Source section of [OLE DB Custom Properties](data-flow/ole-db-custom-properties.md).</span></span>  
  
 <span data-ttu-id="c4269-112">若要了解有关 OLE DB 源的详细信息，请参阅 [OLE DB Source](data-flow/ole-db-source.md)。</span><span class="sxs-lookup"><span data-stu-id="c4269-112">To learn more about the OLE DB source, see [OLE DB Source](data-flow/ole-db-source.md).</span></span>  
  
## <a name="open-the-ole-db-source-editor-connection-manager-page"></a><span data-ttu-id="c4269-113">打开“OLE 源编辑器”（“连接管理器”页）</span><span class="sxs-lookup"><span data-stu-id="c4269-113">Open the OLE DB Source Editor (Connection Manager Page</span></span>  
  
1.  <span data-ttu-id="c4269-114">在 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 中，向 [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]包添加 OLE DB 源。</span><span class="sxs-lookup"><span data-stu-id="c4269-114">Add the OLE DB source to the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] package, in [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)].</span></span>  
  
2.  <span data-ttu-id="c4269-115">右键单击源组件，然后单击“编辑”。</span><span class="sxs-lookup"><span data-stu-id="c4269-115">Right-click the source component and when click **Edit**.</span></span>  
  
3.  <span data-ttu-id="c4269-116">单击 **“连接管理器”** 。</span><span class="sxs-lookup"><span data-stu-id="c4269-116">Click **Connection Manager**.</span></span>  
  
## <a name="static-options"></a><span data-ttu-id="c4269-117">静态选项</span><span class="sxs-lookup"><span data-stu-id="c4269-117">Static Options</span></span>  
 <span data-ttu-id="c4269-118">**“无缓存”**</span><span class="sxs-lookup"><span data-stu-id="c4269-118">**OLE DB connection manager**</span></span>  
 <span data-ttu-id="c4269-119">从列表中选择一个现有连接管理器，或通过单击“新建”  创建一个新连接。</span><span class="sxs-lookup"><span data-stu-id="c4269-119">Select an existing connection manager from the list, or create a new connection by clicking **New**.</span></span>  
  
 <span data-ttu-id="c4269-120">**新建**</span><span class="sxs-lookup"><span data-stu-id="c4269-120">**New**</span></span>  
 <span data-ttu-id="c4269-121">通过使用“配置 OLE DB 连接管理器”  对话框创建一个新连接管理器。</span><span class="sxs-lookup"><span data-stu-id="c4269-121">Create a new connection manager by using the **Configure OLE DB Connection Manager** dialog box.</span></span>  
  
 <span data-ttu-id="c4269-122">**数据访问模式**</span><span class="sxs-lookup"><span data-stu-id="c4269-122">**Data access mode**</span></span>  
 <span data-ttu-id="c4269-123">指定从源选择数据的方法。</span><span class="sxs-lookup"><span data-stu-id="c4269-123">Specify the method for selecting data from the source.</span></span>  
  
|<span data-ttu-id="c4269-124">选项</span><span class="sxs-lookup"><span data-stu-id="c4269-124">Option</span></span>|<span data-ttu-id="c4269-125">说明</span><span class="sxs-lookup"><span data-stu-id="c4269-125">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="c4269-126">表或视图</span><span class="sxs-lookup"><span data-stu-id="c4269-126">Table or view</span></span>|<span data-ttu-id="c4269-127">从 OLE DB 数据源中的表或视图中检索数据。</span><span class="sxs-lookup"><span data-stu-id="c4269-127">Retrieve data from a table or view in the OLE DB data source.</span></span>|  
|<span data-ttu-id="c4269-128">表名变量或视图名变量</span><span class="sxs-lookup"><span data-stu-id="c4269-128">Table name or view name variable</span></span>|<span data-ttu-id="c4269-129">在变量中指定表或视图名称。</span><span class="sxs-lookup"><span data-stu-id="c4269-129">Specify the table or view name in a variable.</span></span><br /><br /> <span data-ttu-id="c4269-130">**相关信息：** [在包中使用变量](../../2014/integration-services/use-variables-in-packages.md)</span><span class="sxs-lookup"><span data-stu-id="c4269-130">**Related information:** [Use Variables in Packages](../../2014/integration-services/use-variables-in-packages.md)</span></span>|  
|<span data-ttu-id="c4269-131">SQL 命令</span><span class="sxs-lookup"><span data-stu-id="c4269-131">SQL command</span></span>|<span data-ttu-id="c4269-132">使用 SQL 查询从 OLE DB 数据源中检索数据。</span><span class="sxs-lookup"><span data-stu-id="c4269-132">Retrieve data from the OLE DB data source by using a SQL query.</span></span>|  
|<span data-ttu-id="c4269-133">变量中的 SQL 命令</span><span class="sxs-lookup"><span data-stu-id="c4269-133">SQL command from variable</span></span>|<span data-ttu-id="c4269-134">在变量中指定 SQL 查询文本。</span><span class="sxs-lookup"><span data-stu-id="c4269-134">Specify the SQL query text in a variable.</span></span>|  
  
 <span data-ttu-id="c4269-135">**预览**</span><span class="sxs-lookup"><span data-stu-id="c4269-135">**Preview**</span></span>  
 <span data-ttu-id="c4269-136">通过使用“数据视图”  对话框预览结果。</span><span class="sxs-lookup"><span data-stu-id="c4269-136">Preview results by using the **Data View** dialog box.</span></span> <span data-ttu-id="c4269-137">**预览版** 最多可以显示 200 行。</span><span class="sxs-lookup"><span data-stu-id="c4269-137">**Preview** can display up to 200 rows.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="c4269-138">预览数据时，数据类型为 CLR 用户定义类型的列不包含数据。</span><span class="sxs-lookup"><span data-stu-id="c4269-138">When you preview data, columns with a CLR user-defined type do not contain data.</span></span> <span data-ttu-id="c4269-139">而是显示值 \<value too big to display> 或 System.Byte[]。</span><span class="sxs-lookup"><span data-stu-id="c4269-139">Instead the values \<value too big to display> or System.Byte[] display.</span></span> <span data-ttu-id="c4269-140">使用 SQL OLE DB 访问接口访问数据源时，显示前一个值；使用 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Native Client 访问接口访问数据源时，显示后一个值。</span><span class="sxs-lookup"><span data-stu-id="c4269-140">The former displays when the data source is accessed using the SQL OLE DB provider, the latter when using the [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Native Client provider.</span></span>  
  
## <a name="data-access-mode-dynamic-options"></a><span data-ttu-id="c4269-141">数据访问模式动态选项</span><span class="sxs-lookup"><span data-stu-id="c4269-141">Data Access Mode Dynamic Options</span></span>  
  
### <a name="data-access-mode--table-or-view"></a><span data-ttu-id="c4269-142">数据访问模式 = 表或视图</span><span class="sxs-lookup"><span data-stu-id="c4269-142">Data access mode = Table or view</span></span>  
 <span data-ttu-id="c4269-143">**表或视图的名称**</span><span class="sxs-lookup"><span data-stu-id="c4269-143">**Name of the table or the view**</span></span>  
 <span data-ttu-id="c4269-144">从数据源的可用表列表或视图列表中选择表或视图的名称。</span><span class="sxs-lookup"><span data-stu-id="c4269-144">Select the name of the table or view from a list of those available in the data source.</span></span>  
  
### <a name="data-access-mode--table-name-or-view-name-variable"></a><span data-ttu-id="c4269-145">数据访问模式 = 表名变量或视图名变量</span><span class="sxs-lookup"><span data-stu-id="c4269-145">Data access mode = Table name or view name variable</span></span>  
 <span data-ttu-id="c4269-146">**变量名称**</span><span class="sxs-lookup"><span data-stu-id="c4269-146">**Variable name**</span></span>  
 <span data-ttu-id="c4269-147">选择包含表或视图名称的变量。</span><span class="sxs-lookup"><span data-stu-id="c4269-147">Select the variable that contains the name of the table or view.</span></span>  
  
### <a name="data-access-mode--sql-command"></a><span data-ttu-id="c4269-148">数据访问模式 = SQL 命令</span><span class="sxs-lookup"><span data-stu-id="c4269-148">Data access mode = SQL command</span></span>  
 <span data-ttu-id="c4269-149">**SQL 命令文本**</span><span class="sxs-lookup"><span data-stu-id="c4269-149">**SQL command text**</span></span>  
 <span data-ttu-id="c4269-150">输入 SQL 查询的文本，通过单击“生成查询”  来生成查询，或通过单击“浏览”  定位到包含查询文本的文件。</span><span class="sxs-lookup"><span data-stu-id="c4269-150">Enter the text of a SQL query, build the query by clicking **Build Query**, or locate the file that contains the query text by clicking **Browse**.</span></span>  
  
 <span data-ttu-id="c4269-151">**参数**</span><span class="sxs-lookup"><span data-stu-id="c4269-151">**Parameters**</span></span>  
 <span data-ttu-id="c4269-152">如果已经在参数化查询文本中使用 ?</span><span class="sxs-lookup"><span data-stu-id="c4269-152">If you have entered a parameterized query by using ?</span></span> <span data-ttu-id="c4269-153">作为参数占位符输入了参数化查询，请使用 **“设置查询参数”** 对话框将查询输入参数映射到包变量。</span><span class="sxs-lookup"><span data-stu-id="c4269-153">as a parameter placeholder in the query text, use the **Set Query Parameters** dialog box to map query input parameters to package variables.</span></span>  
  
 <span data-ttu-id="c4269-154">**生成查询**</span><span class="sxs-lookup"><span data-stu-id="c4269-154">**Build query**</span></span>  
 <span data-ttu-id="c4269-155">使用“查询生成器”  对话框可直观地构造 SQL 查询。</span><span class="sxs-lookup"><span data-stu-id="c4269-155">Use the **Query Builder** dialog box to construct the SQL query visually.</span></span>  
  
 <span data-ttu-id="c4269-156">**“浏览”**</span><span class="sxs-lookup"><span data-stu-id="c4269-156">**Browse**</span></span>  
 <span data-ttu-id="c4269-157">使用“打开”  对话框可定位到包含 SQL 查询文本的文件。</span><span class="sxs-lookup"><span data-stu-id="c4269-157">Use the **Open** dialog box to locate the file that contains the text of the SQL query.</span></span>  
  
 <span data-ttu-id="c4269-158">**分析查询**</span><span class="sxs-lookup"><span data-stu-id="c4269-158">**Parse query**</span></span>  
 <span data-ttu-id="c4269-159">验证查询文本的语法。</span><span class="sxs-lookup"><span data-stu-id="c4269-159">Verify the syntax of the query text.</span></span>  
  
### <a name="data-access-mode--sql-command-from-variable"></a><span data-ttu-id="c4269-160">数据访问模式 = 变量中的 SQL 命令</span><span class="sxs-lookup"><span data-stu-id="c4269-160">Data access mode = SQL command from variable</span></span>  
 <span data-ttu-id="c4269-161">**变量名称**</span><span class="sxs-lookup"><span data-stu-id="c4269-161">**Variable name**</span></span>  
 <span data-ttu-id="c4269-162">选择包含 SQL 查询文本的变量。</span><span class="sxs-lookup"><span data-stu-id="c4269-162">Select the variable that contains the text of the SQL query.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c4269-163">另请参阅</span><span class="sxs-lookup"><span data-stu-id="c4269-163">See Also</span></span>  
 <span data-ttu-id="c4269-164">[Integration Services 错误和消息引用](../../2014/integration-services/integration-services-error-and-message-reference.md) </span><span class="sxs-lookup"><span data-stu-id="c4269-164">[Integration Services Error and Message Reference](../../2014/integration-services/integration-services-error-and-message-reference.md) </span></span>  
 <span data-ttu-id="c4269-165">[OLE DB 源编辑器 &#40;列 "页&#41;](../../2014/integration-services/ole-db-source-editor-columns-page.md) </span><span class="sxs-lookup"><span data-stu-id="c4269-165">[OLE DB Source Editor &#40;Columns Page&#41;](../../2014/integration-services/ole-db-source-editor-columns-page.md) </span></span>  
 <span data-ttu-id="c4269-166">[OLE DB 源编辑器 &#40;错误输出页&#41;](../../2014/integration-services/ole-db-source-editor-error-output-page.md) </span><span class="sxs-lookup"><span data-stu-id="c4269-166">[OLE DB Source Editor &#40;Error Output Page&#41;](../../2014/integration-services/ole-db-source-editor-error-output-page.md) </span></span>  
 <span data-ttu-id="c4269-167">[使用 OLE DB 源提取数据](data-flow/extract-data-by-using-the-ole-db-source.md) </span><span class="sxs-lookup"><span data-stu-id="c4269-167">[Extract Data by Using the OLE DB Source](data-flow/extract-data-by-using-the-ole-db-source.md) </span></span>  
 [<span data-ttu-id="c4269-168">OLE DB 连接管理器</span><span class="sxs-lookup"><span data-stu-id="c4269-168">OLE DB Connection Manager</span></span>](connection-manager/ole-db-connection-manager.md)  
  
  
