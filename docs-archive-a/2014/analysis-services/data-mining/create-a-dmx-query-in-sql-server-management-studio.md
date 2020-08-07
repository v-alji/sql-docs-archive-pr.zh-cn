---
title: 在 SQL Server Management Studio 中创建 DMX 查询 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- templates [Analysis Services], queries
- SQL Server Management Studio [Analysis Services], DMX queries
- predictions [Analysis Services], DMX prediction queries
- predictions [DMX]
- prediction queries [DMX]
- queries [DMX], prediction queries
- mining models [Analysis Services], DMX
ms.assetid: 568ce40a-1f53-47eb-8c79-14347cdfde83
author: minewiskan
ms.author: owend
ms.openlocfilehash: d20fc7a618f4977058203d8f35d235b543609dd9
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87588156"
---
# <a name="create-a-dmx-query-in-sql-server-management-studio"></a><span data-ttu-id="357d7-102">在 SQL Server Management Studio 中创建一个 DMX 查询</span><span class="sxs-lookup"><span data-stu-id="357d7-102">Create a DMX Query in SQL Server Management Studio</span></span>
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="357d7-103">提供了一组功能，可帮助您创建针对挖掘模型和挖掘结构的预测查询、内容查询和数据定义查询。</span><span class="sxs-lookup"><span data-stu-id="357d7-103">provides a set of features to help you create prediction queries, content queries, and data definition queries against mining models and mining structures.</span></span>  
  
-   <span data-ttu-id="357d7-104">[!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] 和 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]中都提供了图形预测查询生成器，旨在简化编写预测查询并将数据集映射到模型的过程。</span><span class="sxs-lookup"><span data-stu-id="357d7-104">The graphical Prediction Query Builder is available in both [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] and [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], to simplify the process of writing prediction queries and mapping data sets to a model.</span></span>  
  
-   <span data-ttu-id="357d7-105">模板资源管理器中提供的查询模板可快速创建多种类型的 DMX 查询（包括许多类型的预测查询）。</span><span class="sxs-lookup"><span data-stu-id="357d7-105">The query templates provided in the Template Explorer jump-start the creation of many kinds of DMX queries, including many types of prediction queries.</span></span> <span data-ttu-id="357d7-106">提供了针对内容查询、使用嵌套数据集的查询、从挖掘结构返回事例的查询以及数据定义查询的模板。</span><span class="sxs-lookup"><span data-stu-id="357d7-106">Templates are provided for content queries, queries used nested data sets, queries that return cases from the mining structure, and even data definition queries.</span></span>  
  
-   <span data-ttu-id="357d7-107">MDX 和 DMX 查询窗格中的元数据资源管理器提供了可用模型和结构（可将其拖放到查询生成器中）的列表以及 DMX 函数的列表。</span><span class="sxs-lookup"><span data-stu-id="357d7-107">The Metadata Explorer in the MDX and DMX query panes provides a list of available models and structures that you can drag and drop into the query builder, as well as a list of DMX functions.</span></span> <span data-ttu-id="357d7-108">可利用此功能轻松地获取正确的对象名，而无需键入。</span><span class="sxs-lookup"><span data-stu-id="357d7-108">This feature makes it easy to get object names right, without typing.</span></span>  
  
 <span data-ttu-id="357d7-109">本主题介绍如何通过使用元数据资源管理器和 DMX 查询编辑器来生成 DMX 查询。</span><span class="sxs-lookup"><span data-stu-id="357d7-109">This topic describes how to build a DMX query by using the Metadata Explorer and the DMX query editor.</span></span>  
  
##  <a name="dmx-query-templates"></a><a name="BKMK_Templates"></a> <span data-ttu-id="357d7-110">DMX 查询模板</span><span class="sxs-lookup"><span data-stu-id="357d7-110">DMX Query Templates</span></span>  
 <span data-ttu-id="357d7-111">模板资源管理器中有创建 DMX 基本查询的模板。</span><span class="sxs-lookup"><span data-stu-id="357d7-111">Templates for creating basic DMX queries are available in Template Explorer.</span></span> <span data-ttu-id="357d7-112">**DMX** 文件夹包含数据挖掘模板，这些模板划分为以下类别：</span><span class="sxs-lookup"><span data-stu-id="357d7-112">The **DMX** folder contains data mining templates, which are divided into these categories:</span></span>  
  
-   <span data-ttu-id="357d7-113">**模型内容**</span><span class="sxs-lookup"><span data-stu-id="357d7-113">**Model Content**</span></span>  
  
-   <span data-ttu-id="357d7-114">**模型管理**</span><span class="sxs-lookup"><span data-stu-id="357d7-114">**Model Management**</span></span>  
  
-   <span data-ttu-id="357d7-115">**预测查询**</span><span class="sxs-lookup"><span data-stu-id="357d7-115">**Prediction Queries**</span></span>  
  
-   <span data-ttu-id="357d7-116">**结构内容**</span><span class="sxs-lookup"><span data-stu-id="357d7-116">**Structure Content**</span></span>  
  
 <span data-ttu-id="357d7-117">还可以为经常运行的查询或命令创建自定义模板。</span><span class="sxs-lookup"><span data-stu-id="357d7-117">You can also create custom templates, for queries or commands that you run frequently.</span></span>  
  
## <a name="xmla-query-templates"></a><span data-ttu-id="357d7-118">XMLA 查询模板</span><span class="sxs-lookup"><span data-stu-id="357d7-118">XMLA Query Templates</span></span>  
 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] <span data-ttu-id="357d7-119">还提供了 XMLA 查询模板。</span><span class="sxs-lookup"><span data-stu-id="357d7-119">also provides templates for XMLA queries.</span></span>  
  
 <span data-ttu-id="357d7-120">可使用 XMLA 和 DMX 执行的查询类型之间存在某种重叠。</span><span class="sxs-lookup"><span data-stu-id="357d7-120">There is some overlap between the types of queries that you can perform by using XMLA and DMX.</span></span> <span data-ttu-id="357d7-121">例如，可通过使用 DMX 或数据挖掘架构行集创建一些模型内容查询，但是架构行集有时包含不在 DMX 内容查询显示的信息。</span><span class="sxs-lookup"><span data-stu-id="357d7-121">For example, you can create some model content queries by using either DMX or the data mining schema rowsets, but the schema rowsets sometimes contain information that is not exposed in DMX content queries.</span></span>  
  
 <span data-ttu-id="357d7-122">DMX 和 XMLA 中处理操作的方式之间也存在一些关键差异。</span><span class="sxs-lookup"><span data-stu-id="357d7-122">There are also some key differences in the way that operations are handled in DMX and in XMLA.</span></span> <span data-ttu-id="357d7-123">例如，可使用 XMLA 执行管理操作（例如，备份整个 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 数据库），但如果需要备份单个挖掘模型，则 DMX 会提供一个简单命令 [EXPORT (DMX)](/sql/dmx/export-dmx)，使用该命令执行此操作更佳。</span><span class="sxs-lookup"><span data-stu-id="357d7-123">For example, you can use XMLA to perform administrative operations such as backup of an entire [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] database, but if you want to back up a single mining model, DMX provides a simple command, [EXPORT &#40;DMX&#41;](/sql/dmx/export-dmx), that is better suited to that purpose.</span></span>  
  
##  <a name="build-and-run-a-dmx-query"></a><a name="BKMK_Building_Queries"></a> <span data-ttu-id="357d7-124">生成和运行 DMX 查询</span><span class="sxs-lookup"><span data-stu-id="357d7-124">Build and Run a DMX Query</span></span>  
  
#### <a name="open-a-new-dmx-query-window"></a><span data-ttu-id="357d7-125">打开新的 DMX 查询窗口</span><span class="sxs-lookup"><span data-stu-id="357d7-125">Open a new DMX Query window</span></span>  
  
1.  <span data-ttu-id="357d7-126">在 **中单击** “新建查询” [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]，再选择 **“新建 Analysis Server DMX 查询”**。</span><span class="sxs-lookup"><span data-stu-id="357d7-126">Click **New Query** in [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)], and then select **New Analysis Server DMX Query**.</span></span>  
  
2.  <span data-ttu-id="357d7-127">出现 **“连接到服务器”** 对话框后，选择包含要使用的挖掘模型的 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 实例。</span><span class="sxs-lookup"><span data-stu-id="357d7-127">When the **Connect to Server** dialog box appears, select the instance of [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] that contains the mining models you want to work with.</span></span>  
  
#### <a name="open-template-explorer"></a><span data-ttu-id="357d7-128">打开模板资源管理器</span><span class="sxs-lookup"><span data-stu-id="357d7-128">Open Template Explorer</span></span>  
  
1.  <span data-ttu-id="357d7-129">在 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]中，在 **“视图”** 菜单上选择 **“模板资源管理器”**。</span><span class="sxs-lookup"><span data-stu-id="357d7-129">In [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], on the **View** menu, select **Template Explorer**.</span></span>  
  
2.  <span data-ttu-id="357d7-130">单击 **Analysis Server** 可以查看应用于 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]的模板的树视图。</span><span class="sxs-lookup"><span data-stu-id="357d7-130">Click **Analysis Server** to see a tree view of the templates that apply to [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)].</span></span>  
  
#### <a name="apply-a-template-to-build-a-query"></a><span data-ttu-id="357d7-131">应用模板以生成查询</span><span class="sxs-lookup"><span data-stu-id="357d7-131">Apply a template to build a query</span></span>  
  
-   <span data-ttu-id="357d7-132">右键单击适当的查询类型，然后选择“打开”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="357d7-132">Right-click the appropriate query type and select **Open**.</span></span>  
  
-   <span data-ttu-id="357d7-133">或者，将模板拖入查询编辑器中。</span><span class="sxs-lookup"><span data-stu-id="357d7-133">Or, drag the template into the query editor.</span></span>  
  
-   <span data-ttu-id="357d7-134">也可以使用 **“查询”** 菜单中的 **“指定参数的值”** 选项来填写查询的参数。</span><span class="sxs-lookup"><span data-stu-id="357d7-134">You can also fill in the parameters for the query by using the option, **Specify Values for Parameters**, from the **Query** menu.</span></span>  
  
 <span data-ttu-id="357d7-135">有关如何从模板创建特定类型的查询的示例，请参阅下列主题：</span><span class="sxs-lookup"><span data-stu-id="357d7-135">For examples of how to create specific types of queries from templates, see the following topics:</span></span>  
  
 [<span data-ttu-id="357d7-136">通过模板创建单独预测查询</span><span class="sxs-lookup"><span data-stu-id="357d7-136">Create a Singleton Prediction Query from a Template</span></span>](create-a-singleton-prediction-query-from-a-template.md)  
  
 [<span data-ttu-id="357d7-137">针对挖掘模型创建内容查询</span><span class="sxs-lookup"><span data-stu-id="357d7-137">Create a Content Query on a Mining Model</span></span>](create-a-content-query-on-a-mining-model.md)  
  
## <a name="see-also"></a><span data-ttu-id="357d7-138">另请参阅</span><span class="sxs-lookup"><span data-stu-id="357d7-138">See Also</span></span>  
 <span data-ttu-id="357d7-139">[数据挖掘查询接口](data-mining-query-tools.md) </span><span class="sxs-lookup"><span data-stu-id="357d7-139">[Data Mining Query Interfaces](data-mining-query-tools.md) </span></span>  
 [<span data-ttu-id="357d7-140">数据挖掘扩展插件 (DMX) 参考</span><span class="sxs-lookup"><span data-stu-id="357d7-140">Data Mining Extensions &#40;DMX&#41; Reference</span></span>](/sql/dmx/data-mining-extensions-dmx-reference)  
  
  
