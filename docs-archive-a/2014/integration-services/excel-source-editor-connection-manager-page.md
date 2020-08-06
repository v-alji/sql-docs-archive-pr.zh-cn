---
title: Excel 源编辑器 (连接管理器页) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.excelsourceadapter.connection.f1
helpviewer_keywords:
- Excel Source Editor
ms.assetid: 428e04e0-ad98-45d0-8345-12ec1b67b2eb
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 3285b5c8b14016b91005af79542e3e2f9b6559b6
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87587494"
---
# <a name="excel-source-editor-connection-manager-page"></a><span data-ttu-id="f2c36-102">Excel 源编辑器（“连接管理器”页）</span><span class="sxs-lookup"><span data-stu-id="f2c36-102">Excel Source Editor (Connection Manager Page)</span></span>
  <span data-ttu-id="f2c36-103">使用 **“Excel 源编辑器”** 对话框的 **“连接管理器”** 节点可以为源选择要使用的 [!INCLUDE[ofprexcel](../includes/ofprexcel-md.md)] 工作簿。</span><span class="sxs-lookup"><span data-stu-id="f2c36-103">Use the **Connection Manager** node of the **Excel Source Editor** dialog box to select the [!INCLUDE[ofprexcel](../includes/ofprexcel-md.md)] workbook for the source to use.</span></span> <span data-ttu-id="f2c36-104">Excel 源从现有工作簿中的工作表或指定范围中读取数据。</span><span class="sxs-lookup"><span data-stu-id="f2c36-104">The Excel source reads data from a worksheet or named range in an existing workbook.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="f2c36-105">`CommandTimeout`Excel 源的属性在**Excel 源编辑器**中不可用，但可以使用**高级编辑器**进行设置。</span><span class="sxs-lookup"><span data-stu-id="f2c36-105">The `CommandTimeout` property of the Excel source is not available in the **Excel Source Editor**, but can be set by using the **Advanced Editor**.</span></span> <span data-ttu-id="f2c36-106">有关此属性的详细信息，请参阅 [Excel Custom Properties](data-flow/excel-custom-properties.md)的“Excel 源”部分。</span><span class="sxs-lookup"><span data-stu-id="f2c36-106">For more information on this property, see the Excel Source section of [Excel Custom Properties](data-flow/excel-custom-properties.md).</span></span>  
  
 <span data-ttu-id="f2c36-107">若要了解有关 Excel 源的详细信息，请参阅 [Excel Source](data-flow/excel-source.md)。</span><span class="sxs-lookup"><span data-stu-id="f2c36-107">To learn more about the Excel source, see [Excel Source](data-flow/excel-source.md).</span></span>  
  
## <a name="static-options"></a><span data-ttu-id="f2c36-108">静态选项</span><span class="sxs-lookup"><span data-stu-id="f2c36-108">Static Options</span></span>  
 <span data-ttu-id="f2c36-109">**“无缓存”**</span><span class="sxs-lookup"><span data-stu-id="f2c36-109">**OLE DB connection manager**</span></span>  
 <span data-ttu-id="f2c36-110">从列表中选择现有的 Excel 连接管理器，或单击“新建”\*\*\*\* 创建新连接。</span><span class="sxs-lookup"><span data-stu-id="f2c36-110">Select an existing Excel connection manager from the list, or create a new connection by clicking **New**.</span></span>  
  
 <span data-ttu-id="f2c36-111">**新建**</span><span class="sxs-lookup"><span data-stu-id="f2c36-111">**New**</span></span>  
 <span data-ttu-id="f2c36-112">使用“Excel 连接管理器”\*\*\*\* 对话框创建一个新连接管理器。</span><span class="sxs-lookup"><span data-stu-id="f2c36-112">Create a new connection manager by using the **Excel Connection Manager** dialog box.</span></span>  
  
 <span data-ttu-id="f2c36-113">**数据访问模式**</span><span class="sxs-lookup"><span data-stu-id="f2c36-113">**Data access mode**</span></span>  
 <span data-ttu-id="f2c36-114">指定从源选择数据的方法。</span><span class="sxs-lookup"><span data-stu-id="f2c36-114">Specify the method for selecting data from the source.</span></span>  
  
|<span data-ttu-id="f2c36-115">值</span><span class="sxs-lookup"><span data-stu-id="f2c36-115">Value</span></span>|<span data-ttu-id="f2c36-116">说明</span><span class="sxs-lookup"><span data-stu-id="f2c36-116">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="f2c36-117">表或视图</span><span class="sxs-lookup"><span data-stu-id="f2c36-117">Table or view</span></span>|<span data-ttu-id="f2c36-118">从 Excel 文件的工作表或指定范围中检索数据。</span><span class="sxs-lookup"><span data-stu-id="f2c36-118">Retrieve data from a worksheet or named range in the Excel file.</span></span>|  
|<span data-ttu-id="f2c36-119">表名变量或视图名变量</span><span class="sxs-lookup"><span data-stu-id="f2c36-119">Table name or view name variable</span></span>|<span data-ttu-id="f2c36-120">在变量中指定工作表名称或范围名称。</span><span class="sxs-lookup"><span data-stu-id="f2c36-120">Specify the worksheet or range name in a variable.</span></span><br /><br /> <span data-ttu-id="f2c36-121">**相关信息：** [在包中使用变量](../../2014/integration-services/use-variables-in-packages.md)</span><span class="sxs-lookup"><span data-stu-id="f2c36-121">**Related information:** [Use Variables in Packages](../../2014/integration-services/use-variables-in-packages.md)</span></span>|  
|<span data-ttu-id="f2c36-122">SQL 命令</span><span class="sxs-lookup"><span data-stu-id="f2c36-122">SQL command</span></span>|<span data-ttu-id="f2c36-123">使用 SQL 查询从 Excel 文件中检索数据。</span><span class="sxs-lookup"><span data-stu-id="f2c36-123">Retrieve data from the Excel file by using a SQL query.</span></span> <span data-ttu-id="f2c36-124">有关查询语法的详细信息，请参阅 [Excel Source](data-flow/excel-source.md)。</span><span class="sxs-lookup"><span data-stu-id="f2c36-124">For information about query syntax, see [Excel Source](data-flow/excel-source.md).</span></span>|  
|<span data-ttu-id="f2c36-125">变量中的 SQL 命令</span><span class="sxs-lookup"><span data-stu-id="f2c36-125">SQL command from variable</span></span>|<span data-ttu-id="f2c36-126">在变量中指定 SQL 查询文本。</span><span class="sxs-lookup"><span data-stu-id="f2c36-126">Specify the SQL query text in a variable.</span></span>|  
  
 <span data-ttu-id="f2c36-127">**预览**</span><span class="sxs-lookup"><span data-stu-id="f2c36-127">**Preview**</span></span>  
 <span data-ttu-id="f2c36-128">通过使用“数据视图”  对话框预览结果。</span><span class="sxs-lookup"><span data-stu-id="f2c36-128">Preview results by using the **Data View** dialog box.</span></span> <span data-ttu-id="f2c36-129">预览最多可以显示 200 行。</span><span class="sxs-lookup"><span data-stu-id="f2c36-129">Preview can display up to 200 rows.</span></span>  
  
## <a name="data-access-mode-dynamic-options"></a><span data-ttu-id="f2c36-130">数据访问模式动态选项</span><span class="sxs-lookup"><span data-stu-id="f2c36-130">Data Access Mode Dynamic Options</span></span>  
  
### <a name="data-access-mode--table-or-view"></a><span data-ttu-id="f2c36-131">数据访问模式 = 表或视图</span><span class="sxs-lookup"><span data-stu-id="f2c36-131">Data access mode = Table or view</span></span>  
 <span data-ttu-id="f2c36-132">**Excel 表的名称**</span><span class="sxs-lookup"><span data-stu-id="f2c36-132">**Name of the Excel sheet**</span></span>  
 <span data-ttu-id="f2c36-133">从 Excel 工作簿可用的工作表或指定范围中选择工作表或指定范围的名称。</span><span class="sxs-lookup"><span data-stu-id="f2c36-133">Select the name of the worksheet or named range from a list of those available in the Excel workbook.</span></span>  
  
### <a name="data-access-mode--table-name-or-view-name-variable"></a><span data-ttu-id="f2c36-134">数据访问模式 = 表名变量或视图名变量</span><span class="sxs-lookup"><span data-stu-id="f2c36-134">Data access mode = Table name or view name variable</span></span>  
 <span data-ttu-id="f2c36-135">**变量名称**</span><span class="sxs-lookup"><span data-stu-id="f2c36-135">**Variable name**</span></span>  
 <span data-ttu-id="f2c36-136">选择包含工作表名称或指定范围名称的变量。</span><span class="sxs-lookup"><span data-stu-id="f2c36-136">Select the variable that contains the name of the worksheet or named range.</span></span>  
  
### <a name="data-access-mode--sql-command"></a><span data-ttu-id="f2c36-137">数据访问模式 = SQL 命令</span><span class="sxs-lookup"><span data-stu-id="f2c36-137">Data access mode = SQL command</span></span>  
 <span data-ttu-id="f2c36-138">**SQL 命令文本**</span><span class="sxs-lookup"><span data-stu-id="f2c36-138">**SQL command text**</span></span>  
 <span data-ttu-id="f2c36-139">输入 SQL 查询的文本，通过单击“生成查询”\*\*\*\* 来生成查询，或通过单击“浏览”\*\*\*\* 浏览至包含查询文本的文件。</span><span class="sxs-lookup"><span data-stu-id="f2c36-139">Enter the text of a SQL query, build the query by clicking **Build Query**, or browse to the file that contains the query text by clicking **Browse**.</span></span>  
  
 <span data-ttu-id="f2c36-140">**参数**</span><span class="sxs-lookup"><span data-stu-id="f2c36-140">**Parameters**</span></span>  
 <span data-ttu-id="f2c36-141">如果已经在参数化查询文本中使用 ?</span><span class="sxs-lookup"><span data-stu-id="f2c36-141">If you have entered a parameterized query by using ?</span></span> <span data-ttu-id="f2c36-142">作为参数占位符输入了参数化查询，请使用 **“设置查询参数”** 对话框将查询输入参数映射到包变量。</span><span class="sxs-lookup"><span data-stu-id="f2c36-142">as a parameter placeholder in the query text, use the **Set Query Parameters** dialog box to map query input parameters to package variables.</span></span>  
  
 <span data-ttu-id="f2c36-143">**生成查询**</span><span class="sxs-lookup"><span data-stu-id="f2c36-143">**Build query**</span></span>  
 <span data-ttu-id="f2c36-144">使用“查询生成器”  对话框可直观地构造 SQL 查询。</span><span class="sxs-lookup"><span data-stu-id="f2c36-144">Use the **Query Builder** dialog box to construct the SQL query visually.</span></span>  
  
 <span data-ttu-id="f2c36-145">**“浏览”**</span><span class="sxs-lookup"><span data-stu-id="f2c36-145">**Browse**</span></span>  
 <span data-ttu-id="f2c36-146">使用“打开”  对话框可定位到包含 SQL 查询文本的文件。</span><span class="sxs-lookup"><span data-stu-id="f2c36-146">Use the **Open** dialog box to locate the file that contains the text of the SQL query.</span></span>  
  
 <span data-ttu-id="f2c36-147">**分析查询**</span><span class="sxs-lookup"><span data-stu-id="f2c36-147">**Parse query**</span></span>  
 <span data-ttu-id="f2c36-148">验证查询文本的语法。</span><span class="sxs-lookup"><span data-stu-id="f2c36-148">Verify the syntax of the query text.</span></span>  
  
### <a name="data-access-mode--sql-command-from-variable"></a><span data-ttu-id="f2c36-149">数据访问模式 = 变量中的 SQL 命令</span><span class="sxs-lookup"><span data-stu-id="f2c36-149">Data access mode = SQL command from variable</span></span>  
 <span data-ttu-id="f2c36-150">**变量名称**</span><span class="sxs-lookup"><span data-stu-id="f2c36-150">**Variable name**</span></span>  
 <span data-ttu-id="f2c36-151">选择包含 SQL 查询文本的变量。</span><span class="sxs-lookup"><span data-stu-id="f2c36-151">Select the variable that contains the text of the SQL query.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f2c36-152">另请参阅</span><span class="sxs-lookup"><span data-stu-id="f2c36-152">See Also</span></span>  
 <span data-ttu-id="f2c36-153">[Integration Services 错误和消息引用](../../2014/integration-services/integration-services-error-and-message-reference.md) </span><span class="sxs-lookup"><span data-stu-id="f2c36-153">[Integration Services Error and Message Reference](../../2014/integration-services/integration-services-error-and-message-reference.md) </span></span>  
 <span data-ttu-id="f2c36-154">[Excel 源编辑器 &#40;列 "页&#41;](../../2014/integration-services/excel-source-editor-columns-page.md) </span><span class="sxs-lookup"><span data-stu-id="f2c36-154">[Excel Source Editor &#40;Columns Page&#41;](../../2014/integration-services/excel-source-editor-columns-page.md) </span></span>  
 <span data-ttu-id="f2c36-155">[Excel 源编辑器 &#40;错误输出页&#41;](../../2014/integration-services/excel-source-editor-error-output-page.md) </span><span class="sxs-lookup"><span data-stu-id="f2c36-155">[Excel Source Editor &#40;Error Output Page&#41;](../../2014/integration-services/excel-source-editor-error-output-page.md) </span></span>  
 <span data-ttu-id="f2c36-156">[Excel 连接管理器](connection-manager/excel-connection-manager.md) </span><span class="sxs-lookup"><span data-stu-id="f2c36-156">[Excel Connection Manager](connection-manager/excel-connection-manager.md) </span></span>  
 [<span data-ttu-id="f2c36-157">使用 Foreach 循环容器循环遍历 Excel 文件和表</span><span class="sxs-lookup"><span data-stu-id="f2c36-157">Loop through Excel Files and Tables by Using a Foreach Loop Container</span></span>](control-flow/foreach-loop-container.md)  
  
  
