---
title: SQL Server Office 数据挖掘外接程序 |Microsoft Docs
ms.custom: ''
ms.date: 12/29/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: c9021a19-2c19-4f0a-a293-5f7e0ac2524c
author: minewiskan
ms.author: owend
ms.openlocfilehash: b64d0c8728e4752d0d5831562d43646e29f7d723
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87577075"
---
# <a name="sql-server-data-mining-add-ins-for-office"></a><span data-ttu-id="ebcc1-102">SQL Server Office 数据挖掘外接程序</span><span class="sxs-lookup"><span data-stu-id="ebcc1-102">SQL Server Data Mining Add-Ins for Office</span></span>
  [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] <span data-ttu-id="ebcc1-103">Office 数据挖掘外接程序是用于预测分析的一组轻型工具，允许您使用 Excel 中的数据生成分析模型来用于预测、建议或浏览。</span><span class="sxs-lookup"><span data-stu-id="ebcc1-103">Data Mining Add-ins for Office is a lightweight set of tools for predictive analytics that lets you use data in Excel to build analytical models for prediction, recommendation, or exploration.</span></span>  
  
 <span data-ttu-id="ebcc1-104">该外接程序中的向导和数据管理工具为以下这些常用的数据挖掘任务提供了分步说明：</span><span class="sxs-lookup"><span data-stu-id="ebcc1-104">The wizards and data management tools in the add-ins provide step-by-step instruction for these common data mining tasks:</span></span>  
  
-   <span data-ttu-id="ebcc1-105">**建模前组织和清理你的数据。**</span><span class="sxs-lookup"><span data-stu-id="ebcc1-105">**Organize and clean your data prior to modeling.**</span></span> <span data-ttu-id="ebcc1-106">使用在 Excel 或任何 Excel 数据源中存储的数据。</span><span class="sxs-lookup"><span data-stu-id="ebcc1-106">Use data stored in Excel or any Excel data source.</span></span> <span data-ttu-id="ebcc1-107">可创建并保存连接以重用数据源、重复进行试验或将模型重新定型。</span><span class="sxs-lookup"><span data-stu-id="ebcc1-107">You can create and save connections to re-use data sources, repeat experiments, or re-train models.</span></span>  
  
-   <span data-ttu-id="ebcc1-108">**探查、抽样和准备。**</span><span class="sxs-lookup"><span data-stu-id="ebcc1-108">**Profile, sample, and prepare.**</span></span> <span data-ttu-id="ebcc1-109">许多经验丰富的数据挖掘人员都说，一个数据挖掘项目中有百分之 70-90 的时间用在数据准备上。</span><span class="sxs-lookup"><span data-stu-id="ebcc1-109">Many experienced data miners say that as much as 70-90 percent of a data mining project is spent on data preparation.</span></span> <span data-ttu-id="ebcc1-110">该外接程序通过在 Excel 中提供可视化效果和帮助您完成以下这些常用任务的向导，可使此任务更快完成：</span><span class="sxs-lookup"><span data-stu-id="ebcc1-110">The add-ins can make this task go faster, by providing visualizations in Excel and wizards that help you with these common tasks:</span></span>  
  
    -   <span data-ttu-id="ebcc1-111">探查数据并了解其分布和特征。</span><span class="sxs-lookup"><span data-stu-id="ebcc1-111">Profile data and understand its distribution and characteristics.</span></span>  
  
    -   <span data-ttu-id="ebcc1-112">通过随机抽样或过度抽样创建定型集和测试集。</span><span class="sxs-lookup"><span data-stu-id="ebcc1-112">Create training and testing sets through random sampling or oversampling.</span></span>  
  
    -   <span data-ttu-id="ebcc1-113">找到离散值并删除或替换它们。</span><span class="sxs-lookup"><span data-stu-id="ebcc1-113">Find outliers and remove or replace them.</span></span>  
  
    -   <span data-ttu-id="ebcc1-114">重新标记数据以提高分析质量。</span><span class="sxs-lookup"><span data-stu-id="ebcc1-114">Re-label data to improve the quality of analysis.</span></span>  
  
-   <span data-ttu-id="ebcc1-115">**通过监督的学习或无人监督的学习分析模式。**</span><span class="sxs-lookup"><span data-stu-id="ebcc1-115">**Analyze patterns through supervised or unsupervised learning.**</span></span> <span data-ttu-id="ebcc1-116">单击用户友好的向导以便执行某些最常见数据挖掘任务，包括聚类分析、市场篮分析和预测。</span><span class="sxs-lookup"><span data-stu-id="ebcc1-116">Click through friendly wizards to perform some of the most popular data mining tasks, including clustering analysis, market basket analysis, and forecasting.</span></span>  
  
     <span data-ttu-id="ebcc1-117">该外接程序中包括的众所周知的计算机学习算法为 Naïve Bayes、逻辑回归、聚类分析、时序和神经网络。</span><span class="sxs-lookup"><span data-stu-id="ebcc1-117">Among the well-known machine learning algorithms included in the add-ins are Naïve Bayes, logistic regression, clustering, time series, and neural networks.</span></span>  
  
     <span data-ttu-id="ebcc1-118">如果您不熟悉数据挖掘，则可以使用 **“查询”** 向导帮助生成预测查询。</span><span class="sxs-lookup"><span data-stu-id="ebcc1-118">If you are new to data mining, get help building prediction queries from the **Query** wizard.</span></span>  
  
     <span data-ttu-id="ebcc1-119">高级用户可通过拖放“高级查询编辑器”生成自定义 DMX 查询，或使用 Excel VBA 自动进行预测。\*\*\*\*</span><span class="sxs-lookup"><span data-stu-id="ebcc1-119">Advanced users can build custom DMX queries with the drag-and-drop **Advanced Query Editor**, or automate predictions using Excel VBA.</span></span>  
  
-   <span data-ttu-id="ebcc1-120">**记载和管理。**</span><span class="sxs-lookup"><span data-stu-id="ebcc1-120">**Document and manage.**</span></span> <span data-ttu-id="ebcc1-121">创建了数据集并生成了一些模型后，通过生成数据和模型参数的统计摘要来记录您的工作和见解。</span><span class="sxs-lookup"><span data-stu-id="ebcc1-121">After you've created a data set and built some models, document your work and your insights by generating a statistical summary of the data and model parameters.</span></span>  
  
-   <span data-ttu-id="ebcc1-122">**浏览和展现。**</span><span class="sxs-lookup"><span data-stu-id="ebcc1-122">**Explore and visualize.**</span></span> <span data-ttu-id="ebcc1-123">数据挖掘不是可完全自动进行的活动-需要探索并理解结果才能采取有意义的操作。</span><span class="sxs-lookup"><span data-stu-id="ebcc1-123">Data mining is not an activity that can be fully automated - you need to explore and understand your results to take meaningful action.</span></span> <span data-ttu-id="ebcc1-124">该外接程序帮助您探索各种内容，其中在 Excel、Visio 模板中提供交互式查看器，使您可自定义模型关系图，还可将图表和表导出到 Excel 供进一步筛选或修改。</span><span class="sxs-lookup"><span data-stu-id="ebcc1-124">The add-ins help you with exploration by providing interactive viewers in Excel, Visio templates that let you customize model diagrams, and the ability to export charts and tables to Excel for additional filtering or modification.</span></span>  
  
-   <span data-ttu-id="ebcc1-125">**部署和集成。**</span><span class="sxs-lookup"><span data-stu-id="ebcc1-125">**Deploy and integrate.**</span></span> <span data-ttu-id="ebcc1-126">创建有用的模型后，通过使用管理工具将模型从试验服务器导出到另一个实例，使模型进入生产环境中 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="ebcc1-126">When you've created a useful model, put your model into production, by using the management tools to export the model from your experimental server to another instance of [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)].</span></span>  
  
     <span data-ttu-id="ebcc1-127">您还可以将模型保留在服务器上创建它时的位置，但使用 Integration Services 或 DMX 脚本刷新定型数据并运行预测。</span><span class="sxs-lookup"><span data-stu-id="ebcc1-127">You can also leave the model on the server where you created it, but refresh the training data and run predictions using Integration Services or DMX scripts.</span></span>  
  
     <span data-ttu-id="ebcc1-128">高级用户一定会感激 **“跟踪”** 功能，通过该功能，可看到发送到服务器的 XMLA 和 DMX 语句。</span><span class="sxs-lookup"><span data-stu-id="ebcc1-128">Power users will appreciate the **Trace** functionality, that lets you see the XMLA and DMX statements sent to the server.</span></span>  
  
## <a name="getting-started"></a><span data-ttu-id="ebcc1-129">入门</span><span class="sxs-lookup"><span data-stu-id="ebcc1-129">Getting Started</span></span>  
 <span data-ttu-id="ebcc1-130">若要了解这些工具和进行设置，请参阅以下这些主题：</span><span class="sxs-lookup"><span data-stu-id="ebcc1-130">See these topics to learn about the tools and to get set up:</span></span>  
  
-   [<span data-ttu-id="ebcc1-131">Excel 数据挖掘客户端 &#40;SQL Server 数据挖掘外接程序&#41;</span><span class="sxs-lookup"><span data-stu-id="ebcc1-131">Data Mining Client for Excel &#40;SQL Server Data Mining Add-ins&#41;</span></span>](../data-mining-client-for-excel-sql-server-data-mining-add-ins.md)  
  
-   [<span data-ttu-id="ebcc1-132">Excel 表分析工具</span><span class="sxs-lookup"><span data-stu-id="ebcc1-132">Table Analysis Tools for Excel</span></span>](../table-analysis-tools-for-excel.md)  
  
-   [<span data-ttu-id="ebcc1-133">Visio 数据挖掘形状</span><span class="sxs-lookup"><span data-stu-id="ebcc1-133">Data Mining Shapes for Visio</span></span>](../data-mining-shapes-for-visio.md)  
  
-   [<span data-ttu-id="ebcc1-134">连接到数据挖掘服务器</span><span class="sxs-lookup"><span data-stu-id="ebcc1-134">Connect to a Data Mining Server</span></span>](../connect-to-a-data-mining-server.md)  
  
## <a name="support-and-requirements"></a><span data-ttu-id="ebcc1-135">支持和要求</span><span class="sxs-lookup"><span data-stu-id="ebcc1-135">Support and Requirements</span></span>  
 <span data-ttu-id="ebcc1-136">可免费下载 SQL Server Office 数据挖掘外接程序。</span><span class="sxs-lookup"><span data-stu-id="ebcc1-136">The SQL Server Data Mining Add-Ins for Office is a free download.</span></span> <span data-ttu-id="ebcc1-137">必须已安装以下某个 Office 版本才能使用这些工具：</span><span class="sxs-lookup"><span data-stu-id="ebcc1-137">You must have one of the following versions of Office already installed to use these tools:</span></span>  
  
-   <span data-ttu-id="ebcc1-138">Office 2010（32 位或 64 位版）</span><span class="sxs-lookup"><span data-stu-id="ebcc1-138">Office 2010, 32-bit or 64-bit version</span></span>  
  
-   <span data-ttu-id="ebcc1-139">Office 2013（32 位或 64 位版）</span><span class="sxs-lookup"><span data-stu-id="ebcc1-139">Office 2013, 32-bit or 64-bit version</span></span>  
  
> [!WARNING]  
>  <span data-ttu-id="ebcc1-140">请确保下载与您的 Excel 版本匹配的外接程序版本。</span><span class="sxs-lookup"><span data-stu-id="ebcc1-140">Be sure to download the version of the add-ins that matches your version of Excel.</span></span>  
  
 <span data-ttu-id="ebcc1-141">数据挖掘外接程序要求与以下 SQL Server Analysis Services 版本之一的连接：</span><span class="sxs-lookup"><span data-stu-id="ebcc1-141">The Data Mining Add-ins requires a connection to one of the following editions of SQL Server Analysis Services:</span></span>  
  
-   <span data-ttu-id="ebcc1-142">Enterprise</span><span class="sxs-lookup"><span data-stu-id="ebcc1-142">Enterprise</span></span>  
  
-   <span data-ttu-id="ebcc1-143">商业智能</span><span class="sxs-lookup"><span data-stu-id="ebcc1-143">Business Intelligence</span></span>  
  
-   <span data-ttu-id="ebcc1-144">Standard</span><span class="sxs-lookup"><span data-stu-id="ebcc1-144">Standard</span></span>  
  
 <span data-ttu-id="ebcc1-145">根据所连接的 SQL Server Analysis Services 版本，某些高级算法可能不可用。</span><span class="sxs-lookup"><span data-stu-id="ebcc1-145">Depending on the edition of SQL Server Analysis Services that you connect to, some of the advanced algorithms might not be available.</span></span> <span data-ttu-id="ebcc1-146">有关信息，请参阅[SQL Server 2014 的各个版本支持的功能](https://msdn.microsoft.com/library/cc645993.aspx)。</span><span class="sxs-lookup"><span data-stu-id="ebcc1-146">For information, see [Features Supported by the Editions of SQL Server 2014](https://msdn.microsoft.com/library/cc645993.aspx).</span></span>  
  
 <span data-ttu-id="ebcc1-147">有关安装的其他帮助，请参阅下载中心上的此页：[https://www.microsoft.com/download/details.aspx?id=29061](https://www.microsoft.com/download/details.aspx?id=29061)</span><span class="sxs-lookup"><span data-stu-id="ebcc1-147">For additional help with installation, see this page on the Download Center: [https://www.microsoft.com/download/details.aspx?id=29061](https://www.microsoft.com/download/details.aspx?id=29061)</span></span>  
  
  
