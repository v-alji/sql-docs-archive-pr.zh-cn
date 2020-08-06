---
title: Excel 目标编辑器 (连接管理器页) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.exceldestadapter.connection.f1
helpviewer_keywords:
- Excel Destination Editor
ms.assetid: fc13f725-963c-488e-91e2-20627133e842
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 1556bf713c49aac31f1cc1cd624336f10dbf832f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87587510"
---
# <a name="excel-destination-editor-connection-manager-page"></a><span data-ttu-id="fe866-102">Excel 目标编辑器（“连接管理器”页）</span><span class="sxs-lookup"><span data-stu-id="fe866-102">Excel Destination Editor (Connection Manager Page)</span></span>
  <span data-ttu-id="fe866-103">使用 **“Excel 目标编辑器”** 对话框的 **“连接管理器”** 页可以指定数据源信息和预览结果。</span><span class="sxs-lookup"><span data-stu-id="fe866-103">Use the **Connection Manager** page of the **Excel Destination Editor** dialog box to specify data source information, and to preview the results.</span></span> <span data-ttu-id="fe866-104">Excel 目标将数据加载到 [!INCLUDE[ofprexcel](../includes/ofprexcel-md.md)] 工作簿中的工作表或指定范围。</span><span class="sxs-lookup"><span data-stu-id="fe866-104">The Excel destination loads data into a worksheet or a named range in a [!INCLUDE[ofprexcel](../includes/ofprexcel-md.md)] workbook.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="fe866-105">`CommandTimeout`Excel 目标的属性在**Excel 目标编辑器**中不可用，但可以使用**高级编辑器**进行设置。</span><span class="sxs-lookup"><span data-stu-id="fe866-105">The `CommandTimeout` property of the Excel destination is not available in the **Excel Destination Editor**, but can be set by using the **Advanced Editor**.</span></span> <span data-ttu-id="fe866-106">此外，某些快速加载选项仅在**高级编辑器**中可用。</span><span class="sxs-lookup"><span data-stu-id="fe866-106">In addition, certain Fast Load options are available only in the **Advanced Editor**.</span></span> <span data-ttu-id="fe866-107">有关这些属性的详细信息，请参阅 [Excel Custom Properties](data-flow/excel-custom-properties.md)的“Excel 目标”部分。</span><span class="sxs-lookup"><span data-stu-id="fe866-107">For more information on these properties, see the Excel Destination section of [Excel Custom Properties](data-flow/excel-custom-properties.md).</span></span>  
  
 <span data-ttu-id="fe866-108">若要了解有关 Excel 目标的详细信息，请参阅 [Excel Destination](data-flow/excel-destination.md)。</span><span class="sxs-lookup"><span data-stu-id="fe866-108">To learn more about the Excel destination, see [Excel Destination](data-flow/excel-destination.md).</span></span>  
  
## <a name="static-options"></a><span data-ttu-id="fe866-109">静态选项</span><span class="sxs-lookup"><span data-stu-id="fe866-109">Static Options</span></span>  
 <span data-ttu-id="fe866-110">**Excel 连接管理器**</span><span class="sxs-lookup"><span data-stu-id="fe866-110">**Excel connection manager**</span></span>  
 <span data-ttu-id="fe866-111">从列表中选择现有的 Excel 连接管理器，或单击“新建”\*\*\*\* 创建新连接。</span><span class="sxs-lookup"><span data-stu-id="fe866-111">Select an existing Excel connection manager from the list, or create a new connection by clicking **New**.</span></span>  
  
 <span data-ttu-id="fe866-112">**新建**</span><span class="sxs-lookup"><span data-stu-id="fe866-112">**New**</span></span>  
 <span data-ttu-id="fe866-113">使用“Excel 连接管理器”\*\*\*\* 对话框创建一个新连接管理器。</span><span class="sxs-lookup"><span data-stu-id="fe866-113">Create a new connection manager by using the **Excel Connection Manager** dialog box.</span></span>  
  
 <span data-ttu-id="fe866-114">**数据访问模式**</span><span class="sxs-lookup"><span data-stu-id="fe866-114">**Data access mode**</span></span>  
 <span data-ttu-id="fe866-115">指定从源选择数据的方法。</span><span class="sxs-lookup"><span data-stu-id="fe866-115">Specify the method for selecting data from the source.</span></span>  
  
|<span data-ttu-id="fe866-116">选项</span><span class="sxs-lookup"><span data-stu-id="fe866-116">Option</span></span>|<span data-ttu-id="fe866-117">说明</span><span class="sxs-lookup"><span data-stu-id="fe866-117">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="fe866-118">表或视图</span><span class="sxs-lookup"><span data-stu-id="fe866-118">Table or view</span></span>|<span data-ttu-id="fe866-119">将数据加载到 Excel 数据源中的工作表或指定范围。</span><span class="sxs-lookup"><span data-stu-id="fe866-119">Loads data into a worksheet or named range in the Excel data source.</span></span>|  
|<span data-ttu-id="fe866-120">表名变量或视图名变量</span><span class="sxs-lookup"><span data-stu-id="fe866-120">Table name or view name variable</span></span>|<span data-ttu-id="fe866-121">在变量中指定工作表名称或范围名称。</span><span class="sxs-lookup"><span data-stu-id="fe866-121">Specify the worksheet or range name in a variable.</span></span><br /><br /> <span data-ttu-id="fe866-122">**相关信息**：[在包中使用变量](../../2014/integration-services/use-variables-in-packages.md)</span><span class="sxs-lookup"><span data-stu-id="fe866-122">**Related information**: [Use Variables in Packages](../../2014/integration-services/use-variables-in-packages.md)</span></span>|  
|<span data-ttu-id="fe866-123">SQL 命令</span><span class="sxs-lookup"><span data-stu-id="fe866-123">SQL command</span></span>|<span data-ttu-id="fe866-124">使用 SQL 查询将数据加载到 Excel 目标中。</span><span class="sxs-lookup"><span data-stu-id="fe866-124">Load data into the Excel destination by using an SQL query.</span></span>|  
  
 <span data-ttu-id="fe866-125">**Excel 表的名称**</span><span class="sxs-lookup"><span data-stu-id="fe866-125">**Name of the Excel sheet**</span></span>  
 <span data-ttu-id="fe866-126">从下拉列表中选择 Excel 目标。</span><span class="sxs-lookup"><span data-stu-id="fe866-126">Select the excel destination from the drop-down list.</span></span> <span data-ttu-id="fe866-127">如果此列表为空，请单击 **“新建”**。</span><span class="sxs-lookup"><span data-stu-id="fe866-127">If the list is empty, click **New**.</span></span>  
  
 <span data-ttu-id="fe866-128">**新建**</span><span class="sxs-lookup"><span data-stu-id="fe866-128">**New**</span></span>  
 <span data-ttu-id="fe866-129">单击“新建”将启动“创建表”对话框。\*\*\*\*\*\*\*\*</span><span class="sxs-lookup"><span data-stu-id="fe866-129">Click **New** to launch the **Create Table** dialog box.</span></span> <span data-ttu-id="fe866-130">当您单击 **“确定”** 时，此对话框将创建 **“Excel 连接管理器”** 指向的 Excel 文件。</span><span class="sxs-lookup"><span data-stu-id="fe866-130">When you click **OK**, the dialog box creates the excel file that the **Excel Connection Manager** points to.</span></span>  
  
 <span data-ttu-id="fe866-131">**查看现有数据**</span><span class="sxs-lookup"><span data-stu-id="fe866-131">**View Existing Data**</span></span>  
 <span data-ttu-id="fe866-132">使用“预览查询结果”  对话框预览结果。</span><span class="sxs-lookup"><span data-stu-id="fe866-132">Preview results by using the **Preview Query Results** dialog box.</span></span> <span data-ttu-id="fe866-133">预览最多可以显示 200 行。</span><span class="sxs-lookup"><span data-stu-id="fe866-133">Preview can display up to 200 rows.</span></span>  
  
> [!WARNING]  
>  <span data-ttu-id="fe866-134">如果你选择的“Excel 连接管理器”指向的 Excel 文件不存在，则单击此按钮时你将看到一条错误消息。\*\*\*\*</span><span class="sxs-lookup"><span data-stu-id="fe866-134">If the **Excel connection manager** you selected points to an excel file that does not exist, you will see an error message when you click this button.</span></span>  
  
## <a name="data-access-mode-dynamic-options"></a><span data-ttu-id="fe866-135">数据访问模式动态选项</span><span class="sxs-lookup"><span data-stu-id="fe866-135">Data Access Mode Dynamic Options</span></span>  
  
### <a name="data-access-mode--table-or-view"></a><span data-ttu-id="fe866-136">数据访问模式 = 表或视图</span><span class="sxs-lookup"><span data-stu-id="fe866-136">Data access mode = Table or view</span></span>  
 <span data-ttu-id="fe866-137">**Excel 表的名称**</span><span class="sxs-lookup"><span data-stu-id="fe866-137">**Name of the Excel sheet**</span></span>  
 <span data-ttu-id="fe866-138">从数据源中可用的工作表或指定范围列表中选择工作表或指定范围的名称。</span><span class="sxs-lookup"><span data-stu-id="fe866-138">Select the name of the worksheet or named range from a list of those available in the data source.</span></span>  
  
### <a name="data-access-mode--table-name-or-view-name-variable"></a><span data-ttu-id="fe866-139">数据访问模式 = 表名变量或视图名变量</span><span class="sxs-lookup"><span data-stu-id="fe866-139">Data access mode = Table name or view name variable</span></span>  
 <span data-ttu-id="fe866-140">**变量名称**</span><span class="sxs-lookup"><span data-stu-id="fe866-140">**Variable name**</span></span>  
 <span data-ttu-id="fe866-141">选择包含工作表名称或指定范围名称的变量。</span><span class="sxs-lookup"><span data-stu-id="fe866-141">Select the variable that contains the name of the worksheet or named range.</span></span>  
  
### <a name="data-access-mode--sql-command"></a><span data-ttu-id="fe866-142">数据访问模式 = SQL 命令</span><span class="sxs-lookup"><span data-stu-id="fe866-142">Data access mode = SQL command</span></span>  
 <span data-ttu-id="fe866-143">**SQL 命令文本**</span><span class="sxs-lookup"><span data-stu-id="fe866-143">**SQL command text**</span></span>  
 <span data-ttu-id="fe866-144">输入 SQL 查询的文本，通过单击“生成查询”来生成查询，或通过单击“浏览”定位到包含查询文本的文件。\*\*\*\*\*\*\*\*</span><span class="sxs-lookup"><span data-stu-id="fe866-144">Enter the text of an SQL query, build the query by clicking **Build Query**, or locate the file that contains the query text by clicking **Browse**.</span></span>  
  
 <span data-ttu-id="fe866-145">**生成查询**</span><span class="sxs-lookup"><span data-stu-id="fe866-145">**Build Query**</span></span>  
 <span data-ttu-id="fe866-146">使用“查询生成器”  对话框可直观地构造 SQL 查询。</span><span class="sxs-lookup"><span data-stu-id="fe866-146">Use the **Query Builder** dialog box to construct the SQL query visually.</span></span>  
  
 <span data-ttu-id="fe866-147">**“浏览”**</span><span class="sxs-lookup"><span data-stu-id="fe866-147">**Browse**</span></span>  
 <span data-ttu-id="fe866-148">使用“打开”  对话框可定位到包含 SQL 查询文本的文件。</span><span class="sxs-lookup"><span data-stu-id="fe866-148">Use the **Open** dialog box to locate the file that contains the text of the SQL query.</span></span>  
  
 <span data-ttu-id="fe866-149">**分析查询**</span><span class="sxs-lookup"><span data-stu-id="fe866-149">**Parse Query**</span></span>  
 <span data-ttu-id="fe866-150">验证查询文本的语法。</span><span class="sxs-lookup"><span data-stu-id="fe866-150">Verify the syntax of the query text.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fe866-151">另请参阅</span><span class="sxs-lookup"><span data-stu-id="fe866-151">See Also</span></span>  
 <span data-ttu-id="fe866-152">[Integration Services 错误和消息引用](../../2014/integration-services/integration-services-error-and-message-reference.md) </span><span class="sxs-lookup"><span data-stu-id="fe866-152">[Integration Services Error and Message Reference](../../2014/integration-services/integration-services-error-and-message-reference.md) </span></span>  
 <span data-ttu-id="fe866-153">[Excel 目标编辑器 &#40;映射 "页面&#41;](../../2014/integration-services/excel-destination-editor-mappings-page.md) </span><span class="sxs-lookup"><span data-stu-id="fe866-153">[Excel Destination Editor &#40;Mappings Page&#41;](../../2014/integration-services/excel-destination-editor-mappings-page.md) </span></span>  
 <span data-ttu-id="fe866-154">[Excel 目标编辑器 &#40;错误输出页&#41;](../../2014/integration-services/excel-destination-editor-error-output-page.md) </span><span class="sxs-lookup"><span data-stu-id="fe866-154">[Excel Destination Editor &#40;Error Output Page&#41;](../../2014/integration-services/excel-destination-editor-error-output-page.md) </span></span>  
 [<span data-ttu-id="fe866-155">使用 Foreach 循环容器循环遍历 Excel 文件和表</span><span class="sxs-lookup"><span data-stu-id="fe866-155">Loop through Excel Files and Tables by Using a Foreach Loop Container</span></span>](control-flow/foreach-loop-container.md)  
  
  
