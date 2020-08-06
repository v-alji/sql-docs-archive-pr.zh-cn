---
title: " (Excel 数据挖掘外接程序部署和缩放挖掘模型) |Microsoft Docs"
ms.custom: ''
ms.date: 12/29/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- manage
ms.assetid: 4c617375-6b01-4a71-9680-de0cbf2cff05
author: minewiskan
ms.author: owend
ms.openlocfilehash: dd2839144d4d1667da09830aaabd1ec3f17a9c21
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87588748"
---
# <a name="deploying-and-scaling-mining-models-data-mining-add-ins-for-excel"></a><span data-ttu-id="fb85e-102">部署和缩放挖掘模型（Excel 数据挖掘外接程序）</span><span class="sxs-lookup"><span data-stu-id="fb85e-102">Deploying and Scaling Mining Models (Data Mining Add-ins for Excel)</span></span>
  <span data-ttu-id="fb85e-103">提供 "**模型使用情况**" 和 "**管理**" 组中的工具以帮助你管理和浏览现有挖掘模型。</span><span class="sxs-lookup"><span data-stu-id="fb85e-103">The tools in the **Model Usage** and **Management** group are provided to help you manage and browse existing mining models.</span></span> <span data-ttu-id="fb85e-104">您可以使用这些工具来查看在 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 实例上存储的任意模型，而不仅仅是使用外接程序创建的那些模型。</span><span class="sxs-lookup"><span data-stu-id="fb85e-104">You can use these tools to view any models that are stored on an instance of [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)], not just those created using the add-ins.</span></span>  
  
 <span data-ttu-id="fb85e-105">如果具有所需的权限，您可以在不离开 Excel 的情况下删除、修改、重命名或处理现有挖掘模型和结构。</span><span class="sxs-lookup"><span data-stu-id="fb85e-105">If you have the necessary permissions, you can delete, modify, rename, or process existing mining models and structures without leaving Excel.</span></span>  
  
## <a name="model-usage-toolbar"></a><span data-ttu-id="fb85e-106">模型用法工具栏</span><span class="sxs-lookup"><span data-stu-id="fb85e-106">Model Usage Toolbar</span></span>  
  
### <a name="browse"></a><span data-ttu-id="fb85e-107">浏览</span><span class="sxs-lookup"><span data-stu-id="fb85e-107">Browse</span></span>  
 <span data-ttu-id="fb85e-108">使用 "**浏览**" 向导选择现有的数据挖掘模型，然后在包含多个图形和工具的查看器中查看并浏览该模型。</span><span class="sxs-lookup"><span data-stu-id="fb85e-108">Use the **Browse** wizard to select an existing data mining model, and then view and explore the model in a viewer that contains multiple graphs and tools.</span></span>  
  
 <span data-ttu-id="fb85e-109">有关详细信息，请参阅[在 Excel 中浏览模型 &#40;SQL Server 数据挖掘外接程序&#41;](browsing-models-in-excel-sql-server-data-mining-add-ins.md)。</span><span class="sxs-lookup"><span data-stu-id="fb85e-109">For more information, see [Browsing Models in Excel &#40;SQL Server Data Mining Add-ins&#41;](browsing-models-in-excel-sql-server-data-mining-add-ins.md).</span></span>  
  
### <a name="document-model"></a><span data-ttu-id="fb85e-110">文档模型</span><span class="sxs-lookup"><span data-stu-id="fb85e-110">Document Model</span></span>  
 <span data-ttu-id="fb85e-111">单击 "**文档模型**" 将启动一个向导，该向导创建您已创建的挖掘结构和挖掘模型的报表。</span><span class="sxs-lookup"><span data-stu-id="fb85e-111">Click **Document Model** to start a wizard that creates a report of the mining structures and mining models that you have created.</span></span> <span data-ttu-id="fb85e-112">您可以创建基本或高级报表。</span><span class="sxs-lookup"><span data-stu-id="fb85e-112">You can create basic or advanced reports.</span></span> <span data-ttu-id="fb85e-113">这些报表包括列和模型元数据，因此对于归档您所做的工作以及跟踪模型更改很有用。</span><span class="sxs-lookup"><span data-stu-id="fb85e-113">The reports include column and model metadata, so are useful for documenting your work and tracking changes in models.</span></span>  
  
 <span data-ttu-id="fb85e-114">有关详细信息，请参阅[记录挖掘模型 &#40;Excel 数据挖掘外接程序&#41;](documenting-mining-models-data-mining-add-ins-for-excel.md)。</span><span class="sxs-lookup"><span data-stu-id="fb85e-114">For more information, see [Documenting Mining Models &#40;Data Mining Add-ins for Excel&#41;](documenting-mining-models-data-mining-add-ins-for-excel.md).</span></span>  
  
### <a name="query"></a><span data-ttu-id="fb85e-115">查询</span><span class="sxs-lookup"><span data-stu-id="fb85e-115">Query</span></span>  
 <span data-ttu-id="fb85e-116">单击 "**查询**" 以启动**查询**向导。</span><span class="sxs-lookup"><span data-stu-id="fb85e-116">Click **Query** to start the **Query** wizard.</span></span> <span data-ttu-id="fb85e-117">该向导以交互方式引导您完成根据现有数据挖掘模型创建预测查询的过程。</span><span class="sxs-lookup"><span data-stu-id="fb85e-117">The wizard interactively walks you through the process of creating a prediction query against an existing data mining model.</span></span>  
  
 <span data-ttu-id="fb85e-118">若要进一步自定义查询，或不包括在向导中的生成查询，只需单击 "**高级**" 按钮即可开始**高级编辑器的数据挖掘查询**。</span><span class="sxs-lookup"><span data-stu-id="fb85e-118">To further customize the query, or build queries not included in the wizard, just click the **Advanced** button to start the **Data Mining Query Advanced Editor**.</span></span>  
  
 <span data-ttu-id="fb85e-119">有关详细信息，请参阅[查询 &#40;SQL Server 数据挖掘外接程序&#41;](query-sql-server-data-mining-add-ins.md)。</span><span class="sxs-lookup"><span data-stu-id="fb85e-119">For more information, see [Query &#40;SQL Server Data Mining Add-ins&#41;](query-sql-server-data-mining-add-ins.md).</span></span>  
  
### <a name="data-mining-advanced-query-editor"></a><span data-ttu-id="fb85e-120">数据挖掘高级查询编辑器</span><span class="sxs-lookup"><span data-stu-id="fb85e-120">Data Mining Advanced Query Editor</span></span>  
 <span data-ttu-id="fb85e-121">在此编辑器中，您可以使用数据挖掘扩展 (DMX) 模板开始编写一个查询，然后修改输入、输出、算法和参数，以创建自定义挖掘模型、挖掘结构或预测查询。</span><span class="sxs-lookup"><span data-stu-id="fb85e-121">In this editor, you can use Data Mining Extensions (DMX) templates to jumpstart a query, and then modify the inputs, outputs, algorithms, and parameters to create a custom mining model, mining structure, or prediction query.</span></span>  
  
 <span data-ttu-id="fb85e-122">有关详细信息，请参阅[高级数据挖掘查询编辑器](advanced-data-mining-query-editor.md)。</span><span class="sxs-lookup"><span data-stu-id="fb85e-122">For more information, see [Advanced Data Mining Query Editor](advanced-data-mining-query-editor.md).</span></span>  
  
## <a name="management"></a><span data-ttu-id="fb85e-123">管理</span><span class="sxs-lookup"><span data-stu-id="fb85e-123">Management</span></span>  
 <span data-ttu-id="fb85e-124">使用 "**管理模型**" 向导可以查看当前连接上的现有模型。</span><span class="sxs-lookup"><span data-stu-id="fb85e-124">Use the **Manage Models** wizard to view existing models on the current connection.</span></span> <span data-ttu-id="fb85e-125">您还可以删除、重命名、处理或导入/导出挖掘模型和结构。</span><span class="sxs-lookup"><span data-stu-id="fb85e-125">You can also delete, rename, process, or import and export mining models and structures.</span></span>  
  
 <span data-ttu-id="fb85e-126">有关详细信息，请参阅[&#40;SQL Server 数据挖掘外接程序&#41;管理模型](manage-models-sql-server-data-mining-add-ins.md)。</span><span class="sxs-lookup"><span data-stu-id="fb85e-126">For more information, see [Manage Models &#40;SQL Server Data Mining Add-ins&#41;](manage-models-sql-server-data-mining-add-ins.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fb85e-127">另请参阅</span><span class="sxs-lookup"><span data-stu-id="fb85e-127">See Also</span></span>  
 <span data-ttu-id="fb85e-128">[创建数据挖掘模型](creating-a-data-mining-model.md) </span><span class="sxs-lookup"><span data-stu-id="fb85e-128">[Creating a Data Mining Model](creating-a-data-mining-model.md) </span></span>  
 [<span data-ttu-id="fb85e-129">验证模型和使用模型进行预测 &#40;Excel 数据挖掘外接程序&#41;</span><span class="sxs-lookup"><span data-stu-id="fb85e-129">Validating Models and Using Models for Prediction &#40;Data Mining Add-ins for Excel&#41;</span></span>](validating-models-and-using-models-for-prediction-data-mining-add-ins-for-excel.md)  
  
  
