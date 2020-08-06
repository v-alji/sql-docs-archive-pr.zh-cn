---
title: DMX 模板 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 2a577e52-821d-4bd3-ba35-075a6be285c9
author: minewiskan
ms.author: owend
ms.openlocfilehash: 79c8615933baf4fa3d80974daae91b4d1c7fa101
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87589951"
---
# <a name="dmx-templates"></a><span data-ttu-id="88115-102">DMX 模板</span><span class="sxs-lookup"><span data-stu-id="88115-102">DMX Templates</span></span>
  <span data-ttu-id="88115-103">数据挖掘模板可帮助您快速生成复杂的查询。</span><span class="sxs-lookup"><span data-stu-id="88115-103">The data mining templates help you quickly build sophisticated queries.</span></span> <span data-ttu-id="88115-104">虽然 DMX 查询的常规语法具有详细说明，但借助于这些模板，可通过单击并且指向参数和数据源，更轻松地生成查询。</span><span class="sxs-lookup"><span data-stu-id="88115-104">Although the general syntax for DMX queries is well documented, using the templates makes it easier to build queries by clicking and pointing to arguments and data sources.</span></span>  
  
## <a name="using-the-templates"></a><span data-ttu-id="88115-105">使用模板</span><span class="sxs-lookup"><span data-stu-id="88115-105">Using the Templates</span></span>  
  
1.  <span data-ttu-id="88115-106">在 Excel 数据挖掘客户端中，单击 "**查询**"。</span><span class="sxs-lookup"><span data-stu-id="88115-106">In the Data Mining Client for Excel, click **Query**.</span></span>  
  
2.  <span data-ttu-id="88115-107">在向导的 "**开始**" 页上，单击 "**下一步**"。</span><span class="sxs-lookup"><span data-stu-id="88115-107">On the wizard **Start** page, click **Next**.</span></span>  
  
3.  <span data-ttu-id="88115-108">在该页上，**选择 "模型**"，然后单击 "**高级**"。</span><span class="sxs-lookup"><span data-stu-id="88115-108">On the page, **Select Model**, click **Advanced**.</span></span>  
  
     <span data-ttu-id="88115-109">**提示：** 如果要在模型中创建预测查询，则可以先选择该模型，然后单击 "**高级**"，使用模型名称预填充模板。</span><span class="sxs-lookup"><span data-stu-id="88115-109">**Tip:** If you are going to create a prediction query on a model, you can select the model first, and then click **Advanced**, to prepopulate the template with the model name.</span></span>  
  
4.  <span data-ttu-id="88115-110">在 "**数据挖掘高级查询编辑器**" 中，单击 " **DMX 模板**"，然后选择一个模板。</span><span class="sxs-lookup"><span data-stu-id="88115-110">In the **Data Mining Advanced Query Editor**, click **DMX Templates**, and select a template.</span></span>  
  
5.  <span data-ttu-id="88115-111">按 Enter 将模板加载到“DMX 查询”窗格中。</span><span class="sxs-lookup"><span data-stu-id="88115-111">Press ENTER to load the template into the DMX Query pane.</span></span>  
  
6.  <span data-ttu-id="88115-112">继续单击模板中的链接，在对话框出现后，选择相应的输出、模型或参数。</span><span class="sxs-lookup"><span data-stu-id="88115-112">Continue clicking the links in the template, and as the dialog box appears, select an appropriate output, model, or parameter.</span></span>  
  
     <span data-ttu-id="88115-113">对于预测查询，请首先选择输入数据集，然后映射列。</span><span class="sxs-lookup"><span data-stu-id="88115-113">For prediction queries, choose the input dataset first, and then map the columns.</span></span>  
  
7.  <span data-ttu-id="88115-114">单击 "**编辑查询**" 以切换到文本编辑器视图，并手动更改查询。</span><span class="sxs-lookup"><span data-stu-id="88115-114">Click **Edit Query** to switch to text editor view and manually change the query.</span></span>  
  
     <span data-ttu-id="88115-115">但要注意，如果在使用查询编辑器时切换视图，则上一视图中的所有信息都将被清除。</span><span class="sxs-lookup"><span data-stu-id="88115-115">Be aware, however, that if you switch views when working in the query editor, any information that you had in the previous view will be cleared.</span></span> <span data-ttu-id="88115-116">更改视图前，请将 DMX 语句复制并粘贴到一个单独的文件中，保存好您的工作结果。</span><span class="sxs-lookup"><span data-stu-id="88115-116">Before changing views, save your work by copying and pasting the DMX statements to a separate file.</span></span>  
  
8.  <span data-ttu-id="88115-117">单击“完成”。</span><span class="sxs-lookup"><span data-stu-id="88115-117">Click **Finish**.</span></span> <span data-ttu-id="88115-118">在 "**选择目标**" 对话框中，指定要将结果保存到的位置。</span><span class="sxs-lookup"><span data-stu-id="88115-118">In the **Choose Destination** dialog  box, specify where you want the result saved.</span></span> [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
> [!NOTE]  
>  <span data-ttu-id="88115-119">如果成功执行语句，则发送到服务器的 DMX 语句也将记录在**跟踪**窗口中。</span><span class="sxs-lookup"><span data-stu-id="88115-119">If you executed a statement successfully, the DMX statement that you sent to the server is also recorded in the **Trace** window.</span></span> <span data-ttu-id="88115-120">有关如何使用跟踪功能的详细信息，请参阅[trace &#40;Excel 数据挖掘客户端&#41;](trace-data-mining-client-for-excel.md)。</span><span class="sxs-lookup"><span data-stu-id="88115-120">For more information about how to use the Trace feature, see [Trace &#40;Data Mining Client for Excel&#41;](trace-data-mining-client-for-excel.md).</span></span>  
  
 <span data-ttu-id="88115-121">有关如何使用 "数据挖掘高级查询编辑器" 的详细信息，请参阅[查询 &#40;SQL Server 数据挖掘外接程序 "&#41;](query-sql-server-data-mining-add-ins.md)和[高级数据挖掘查询编辑器](advanced-data-mining-query-editor.md)。</span><span class="sxs-lookup"><span data-stu-id="88115-121">For more information about how to use the Data Mining Advanced Query Editor, see [Query &#40;SQL Server Data Mining Add-ins&#41;](query-sql-server-data-mining-add-ins.md) and [Advanced Data Mining Query Editor](advanced-data-mining-query-editor.md).</span></span>  
  
## <a name="list-of-dmx-templates"></a><span data-ttu-id="88115-122">DMX 模板的列表</span><span class="sxs-lookup"><span data-stu-id="88115-122">List of DMX Templates</span></span>  
 <span data-ttu-id="88115-123">以下 DMX 模板包含在 Excel 数据挖掘客户端中。</span><span class="sxs-lookup"><span data-stu-id="88115-123">The following DMX templates are included in the Data Mining Client for Excel.</span></span>  
  
 <span data-ttu-id="88115-124">**预测**</span><span class="sxs-lookup"><span data-stu-id="88115-124">**Prediction**</span></span>  
  
 <span data-ttu-id="88115-125">使用这些模板可创建高级预测查询，包括外接程序中向导不支持的查询，例如使用嵌套表或外部数据源的查询。</span><span class="sxs-lookup"><span data-stu-id="88115-125">Use these templates to create advanced prediction queries, including queries not supported by the wizards in the add-ins, such as queries that use nested tables or external data sources.</span></span>  
  
-   <span data-ttu-id="88115-126">筛选的预测</span><span class="sxs-lookup"><span data-stu-id="88115-126">Filtered predictions</span></span>  
  
-   <span data-ttu-id="88115-127">筛选的嵌套预测</span><span class="sxs-lookup"><span data-stu-id="88115-127">Filtered nested predictions</span></span>  
  
-   <span data-ttu-id="88115-128">嵌套的预测</span><span class="sxs-lookup"><span data-stu-id="88115-128">Nested predictions</span></span>  
  
-   <span data-ttu-id="88115-129">单独预测</span><span class="sxs-lookup"><span data-stu-id="88115-129">Singleton predictions</span></span>  
  
-   <span data-ttu-id="88115-130">标准预测</span><span class="sxs-lookup"><span data-stu-id="88115-130">Standard predictions</span></span>  
  
-   <span data-ttu-id="88115-131">时序预测</span><span class="sxs-lookup"><span data-stu-id="88115-131">Time series predictions</span></span>  
  
-   <span data-ttu-id="88115-132">TOP 预测查询</span><span class="sxs-lookup"><span data-stu-id="88115-132">TOP prediction query</span></span>  
  
-   <span data-ttu-id="88115-133">嵌套表的 TOP 预测查询</span><span class="sxs-lookup"><span data-stu-id="88115-133">TOP prediction query on nested table</span></span>  
  
 <span data-ttu-id="88115-134">**创建**</span><span class="sxs-lookup"><span data-stu-id="88115-134">**Create**</span></span>  
  
 <span data-ttu-id="88115-135">使用这些模板可生成自定义模型或数据结构。</span><span class="sxs-lookup"><span data-stu-id="88115-135">Use these templates to build custom models or data structures.</span></span> <span data-ttu-id="88115-136">您不仅限于向导支持的模型，您可以使用您连接到的实例所支持的任何数据挖掘算法 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] ，包括插件算法。</span><span class="sxs-lookup"><span data-stu-id="88115-136">You are not limited to the models supported by the wizards - you can use any data mining algorithm supported by the instance of [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] that you are connected to, including plug-in algorithms.</span></span>  
  
-   <span data-ttu-id="88115-137">挖掘模型</span><span class="sxs-lookup"><span data-stu-id="88115-137">Mining model</span></span>  
  
-   <span data-ttu-id="88115-138">挖掘结构</span><span class="sxs-lookup"><span data-stu-id="88115-138">Mining structure</span></span>  
  
-   <span data-ttu-id="88115-139">具有维持的挖掘结构</span><span class="sxs-lookup"><span data-stu-id="88115-139">Mining structure with holdout</span></span>  
  
-   <span data-ttu-id="88115-140">临时模型</span><span class="sxs-lookup"><span data-stu-id="88115-140">Temporary model</span></span>  
  
-   <span data-ttu-id="88115-141">临时结构</span><span class="sxs-lookup"><span data-stu-id="88115-141">Temporary structure</span></span>  
  
 <span data-ttu-id="88115-142">**模型属性**</span><span class="sxs-lookup"><span data-stu-id="88115-142">**Model Properties**</span></span>  
  
 <span data-ttu-id="88115-143">使用这些模板可创建获取有关模型和定型集的元数据的查询。</span><span class="sxs-lookup"><span data-stu-id="88115-143">Use these templates to create queries that get metadata about the model and the training set.</span></span> <span data-ttu-id="88115-144">还可以从模型内容中检索详细信息，或者获取定型数据的统计配置文件。</span><span class="sxs-lookup"><span data-stu-id="88115-144">You can also retrieve details from the model content, or get a statistical profile of the training data.</span></span>  
  
-   <span data-ttu-id="88115-145">挖掘模型内容</span><span class="sxs-lookup"><span data-stu-id="88115-145">Mining model content</span></span>  
  
-   <span data-ttu-id="88115-146">最小和最大列值</span><span class="sxs-lookup"><span data-stu-id="88115-146">Minimum and maximum column values</span></span>  
  
-   <span data-ttu-id="88115-147">挖掘结构测试/定型事例</span><span class="sxs-lookup"><span data-stu-id="88115-147">Mining structure test/training cases</span></span>  
  
-   <span data-ttu-id="88115-148">离散列值</span><span class="sxs-lookup"><span data-stu-id="88115-148">Discrete column values</span></span>  
  
 <span data-ttu-id="88115-149">**Management**</span><span class="sxs-lookup"><span data-stu-id="88115-149">**Management**</span></span>  
  
 <span data-ttu-id="88115-150">使用这些模板可执行 DMX 支持的任何管理任务，包括导入和导出模型、删除模型以及清除模型或数据结构。</span><span class="sxs-lookup"><span data-stu-id="88115-150">Use these templates to perform any management task supported by DMX, which includes importing and exporting models, deleting models, and clearing models or data structures.</span></span>  
  
-   <span data-ttu-id="88115-151">清除挖掘模型</span><span class="sxs-lookup"><span data-stu-id="88115-151">Clear mining model</span></span>  
  
-   <span data-ttu-id="88115-152">清除结构和模型</span><span class="sxs-lookup"><span data-stu-id="88115-152">Clear structure and models</span></span>  
  
-   <span data-ttu-id="88115-153">清除挖掘结构</span><span class="sxs-lookup"><span data-stu-id="88115-153">Clear mining structure</span></span>  
  
-   <span data-ttu-id="88115-154">删除挖掘模型</span><span class="sxs-lookup"><span data-stu-id="88115-154">Delete mining model</span></span>  
  
-   <span data-ttu-id="88115-155">删除挖掘结构</span><span class="sxs-lookup"><span data-stu-id="88115-155">Delete mining structure</span></span>  
  
-   <span data-ttu-id="88115-156">重命名挖掘模型</span><span class="sxs-lookup"><span data-stu-id="88115-156">Rename mining model</span></span>  
  
-   <span data-ttu-id="88115-157">重命名挖掘结构</span><span class="sxs-lookup"><span data-stu-id="88115-157">Rename mining structure</span></span>  
  
-   <span data-ttu-id="88115-158">为挖掘模型定型</span><span class="sxs-lookup"><span data-stu-id="88115-158">Train mining model</span></span>  
  
-   <span data-ttu-id="88115-159">为嵌套挖掘结构定型</span><span class="sxs-lookup"><span data-stu-id="88115-159">Train nested mining structure</span></span>  
  
-   <span data-ttu-id="88115-160">为挖掘结构定型</span><span class="sxs-lookup"><span data-stu-id="88115-160">Train mining structure</span></span>  
  
### <a name="requirements"></a><span data-ttu-id="88115-161">要求</span><span class="sxs-lookup"><span data-stu-id="88115-161">Requirements</span></span>  
 <span data-ttu-id="88115-162">根据使用的模板，您可能需要具有管理权限才能访问 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 服务器和执行查询。</span><span class="sxs-lookup"><span data-stu-id="88115-162">Depending on which template you are using, you might need administrative permissions to access the [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] server and execute the query.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="88115-163">另请参阅</span><span class="sxs-lookup"><span data-stu-id="88115-163">See Also</span></span>  
 [<span data-ttu-id="88115-164">创建数据挖掘模型</span><span class="sxs-lookup"><span data-stu-id="88115-164">Creating a Data Mining Model</span></span>](creating-a-data-mining-model.md)  
  
  
