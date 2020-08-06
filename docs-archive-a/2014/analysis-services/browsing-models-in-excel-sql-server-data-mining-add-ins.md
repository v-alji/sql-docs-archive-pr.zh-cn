---
title: 在 Excel 中浏览模型 (SQL Server 数据挖掘外接程序) |Microsoft Docs
ms.custom: ''
ms.date: 12/29/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- mining models, browsing
- browse models
- mining models, viewing
ms.assetid: a8cca1d7-602a-449a-875c-99da564965bc
author: minewiskan
ms.author: owend
ms.openlocfilehash: c992f1f61112478a85276b6596da0137ccd5c9be
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87579289"
---
# <a name="browsing-models-in-excel-sql-server-data-mining-add-ins"></a><span data-ttu-id="d2085-102">在 Excel 中浏览模型（SQL Server 数据挖掘外接程序）</span><span class="sxs-lookup"><span data-stu-id="d2085-102">Browsing Models in Excel (SQL Server Data Mining Add-ins)</span></span>
  <span data-ttu-id="d2085-103">![“数据挖掘”功能区中的“浏览模型”按钮](media/dmc-browse.gif "“数据挖掘”功能区中的“浏览模型”按钮")</span><span class="sxs-lookup"><span data-stu-id="d2085-103">![Browse Model button in Data Mining ribbon](media/dmc-browse.gif "Browse Model button in Data Mining ribbon")</span></span>  
  
 <span data-ttu-id="d2085-104">直观探索模型通常是了解通过分析发现的规则与关系的最快和最方便的方法。</span><span class="sxs-lookup"><span data-stu-id="d2085-104">Visually exploring the model is usually the fastest and easiest way to get an understanding of the rules and relationships discovered by analysis.</span></span> <span data-ttu-id="d2085-105">通过使用 Excel 数据挖掘客户端，您可以浏览在当前 Excel 会话期间创建的临时模型以及存储在 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 实例中的模型。</span><span class="sxs-lookup"><span data-stu-id="d2085-105">By using the Data Mining Client for Excel, you can browse both temporary models created during the current Excel session, and models stored in an instance of [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)].</span></span>  
  
 <span data-ttu-id="d2085-106">若要浏览模型，请从可用模型列表中选择模型及其关联结构，外接程序会自动选取适用于该数据挖掘算法的查看器。</span><span class="sxs-lookup"><span data-stu-id="d2085-106">To browse a model, you select a model and its associated structure from a list of available models, and the add-in automatically picks the viewer that is appropriate for that data mining algorithm.</span></span> <span data-ttu-id="d2085-107">您可以深入钻取最令人感兴趣的趋势，筛选已完成的数据挖掘模型，将图形和数据复制到 Excel 或 Visio。</span><span class="sxs-lookup"><span data-stu-id="d2085-107">You can drill into the most interesting trends, filter the completed data mining model, and copy graphs and data to Excel or to Visio.</span></span>  
  
## <a name="using-the-browse-model-wizard"></a><span data-ttu-id="d2085-108">使用浏览模型向导</span><span class="sxs-lookup"><span data-stu-id="d2085-108">Using the Browse Model Wizard</span></span>  
  
1.  <span data-ttu-id="d2085-109">单击 "**数据挖掘**" 选项卡。</span><span class="sxs-lookup"><span data-stu-id="d2085-109">Click the **Data Mining** tab.</span></span>  
  
2.  <span data-ttu-id="d2085-110">在 "**模型用法**" 组中，单击 "**浏览**"。</span><span class="sxs-lookup"><span data-stu-id="d2085-110">In the **Model Usage** group, click **Browse**.</span></span>  
  
3.  <span data-ttu-id="d2085-111">在 "**选择模型**" 对话框中，从列表中选择一个挖掘模型，然后单击 "**下一步**"。</span><span class="sxs-lookup"><span data-stu-id="d2085-111">In the **Select Model** dialog box, choose a mining model from the list, and click **Next**.</span></span>  
  
4.  <span data-ttu-id="d2085-112">向导将打开一个适用于所选模型类型的**浏览**窗口。</span><span class="sxs-lookup"><span data-stu-id="d2085-112">The wizard opens a **Browse** window that is appropriate for the type of model that you selected.</span></span>  
  
## <a name="list-of-data-mining-viewers"></a><span data-ttu-id="d2085-113">数据挖掘查看器列表</span><span class="sxs-lookup"><span data-stu-id="d2085-113">List of Data Mining Viewers</span></span>  
 <span data-ttu-id="d2085-114">根据创建模型时使用的数据挖掘算法，**浏览**窗口看起来会有所不同。</span><span class="sxs-lookup"><span data-stu-id="d2085-114">Depending on the data mining algorithm that you used when you created the model, the **Browse** window will look a bit different.</span></span> <span data-ttu-id="d2085-115">该窗口可能包含用于帮助解释结果的图形、包含其他详细信息的图例以及与数据进行交互的控件。</span><span class="sxs-lookup"><span data-stu-id="d2085-115">It can include graphs to help interpret the results, legends that contain additional detail, and controls for interacting with the data.</span></span>  
  
 <span data-ttu-id="d2085-116">以下主题提供如何使用每个查看器（包括解释复杂图形的提示）以及如何更改、复制或使用结果的指南。</span><span class="sxs-lookup"><span data-stu-id="d2085-116">The following topics provide guidance in how to use each of the viewers, including tips on interpreting the complex graphs, and how to change, copy, or work with the results.</span></span>  
  
 [<span data-ttu-id="d2085-117">浏览关联规则模型</span><span class="sxs-lookup"><span data-stu-id="d2085-117">Browsing an Association Rules Model</span></span>](browsing-an-association-rules-model.md)  
  
 [<span data-ttu-id="d2085-118">浏览聚类分析模型</span><span class="sxs-lookup"><span data-stu-id="d2085-118">Browsing a Clustering Model</span></span>](browsing-a-clustering-model.md)  
  
 [<span data-ttu-id="d2085-119">浏览决策树模型</span><span class="sxs-lookup"><span data-stu-id="d2085-119">Browsing a Decision Trees Model</span></span>](browsing-a-decision-trees-model.md)  
  
 [<span data-ttu-id="d2085-120">浏览预测模型</span><span class="sxs-lookup"><span data-stu-id="d2085-120">Browsing a Forecasting Model</span></span>](browsing-a-forecasting-model.md)  
  
 [<span data-ttu-id="d2085-121">浏览 Naive Bayes 模型</span><span class="sxs-lookup"><span data-stu-id="d2085-121">Browsing a Naive Bayes Model</span></span>](browsing-a-naive-bayes-model.md)  
  
 [<span data-ttu-id="d2085-122">浏览神经网络模型</span><span class="sxs-lookup"><span data-stu-id="d2085-122">Browsing a Neural Network Model</span></span>](browsing-a-neural-network-model.md)  
  
## <a name="see-also"></a><span data-ttu-id="d2085-123">另请参阅</span><span class="sxs-lookup"><span data-stu-id="d2085-123">See Also</span></span>  
 <span data-ttu-id="d2085-124">[查看 Visio &#40;数据挖掘外接程序中的数据挖掘模型&#41;](viewing-data-mining-models-in-visio-data-mining-add-ins.md) </span><span class="sxs-lookup"><span data-stu-id="d2085-124">[Viewing Data Mining Models in Visio &#40;Data Mining Add-ins&#41;](viewing-data-mining-models-in-visio-data-mining-add-ins.md) </span></span>  
 [<span data-ttu-id="d2085-125">管理 &#40;SQL Server 数据挖掘外接程序的模型&#41;</span><span class="sxs-lookup"><span data-stu-id="d2085-125">Manage Models &#40;SQL Server Data Mining Add-ins&#41;</span></span>](manage-models-sql-server-data-mining-add-ins.md)  
  
  
