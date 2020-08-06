---
title: 查询 (SQL Server 数据挖掘外接程序) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- queries [data mining]
- Data Mining Query Advanced Editor
- query builder [data mining]
- DMX
ms.assetid: 16af4a6f-18d4-496a-a304-7a13aa32ee76
author: minewiskan
ms.author: owend
ms.openlocfilehash: 90794aae8a3d664d47ab251ffdd954f22d48f992
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87692586"
---
# <a name="query-sql-server-data-mining-add-ins"></a><span data-ttu-id="ae6fb-102">查询（SQL Server 数据挖掘外接程序）</span><span class="sxs-lookup"><span data-stu-id="ae6fb-102">Query (SQL Server Data Mining Add-ins)</span></span>
  <span data-ttu-id="ae6fb-103">![“数据挖掘”功能区中的“查询模型”按钮](media/dmc-query.gif "“数据挖掘”功能区中的“查询模型”按钮")</span><span class="sxs-lookup"><span data-stu-id="ae6fb-103">![Query Model button, Data Mining ribbon](media/dmc-query.gif "Query Model button, Data Mining ribbon")</span></span>  
  
 <span data-ttu-id="ae6fb-104">**查询**向导可帮助您与现有挖掘模型进行交互，以根据 excel 表、excel 区域或其他数据源中的数据进行预测。</span><span class="sxs-lookup"><span data-stu-id="ae6fb-104">The **Query** wizard helps you interact with existing mining models to make predictions based on data in an Excel table, an Excel range, or another data source.</span></span> <span data-ttu-id="ae6fb-105">将新数据应用于现有模型以预测趋势的过程称为*预测查询*。</span><span class="sxs-lookup"><span data-stu-id="ae6fb-105">The process of applying new data to an existing model to predict trends is called a *prediction query*.</span></span>  
  
 <span data-ttu-id="ae6fb-106">**查询**向导还提供了一个高级编辑器，用于创建或修改数据挖掘模型、生成自定义查询或使用其他工具（如嵌套数据集）不支持的结构。</span><span class="sxs-lookup"><span data-stu-id="ae6fb-106">The **Query** wizard also provides an advanced editor for creating or modifying data mining models, for generating custom queries, or for working with structures not supported in the other tools, such as nested datasets.</span></span>  
  
-   <span data-ttu-id="ae6fb-107">使用文本编辑器在数据挖掘扩展插件中键入或粘贴 (DMX) 语句。</span><span class="sxs-lookup"><span data-stu-id="ae6fb-107">Use the text editor to type or paste in the Data Mining Extensions (DMX) statements you've created elsewhere.</span></span>  
  
-   <span data-ttu-id="ae6fb-108">使用交互式查询生成器可在模版和对话框的帮助下编写自定义 DMX 语句。</span><span class="sxs-lookup"><span data-stu-id="ae6fb-108">Use the interactive Query Builder to compose a custom DMX statement with the help of templates and dialog boxes.</span></span>  
  
-   <span data-ttu-id="ae6fb-109">创建 DMX 语句来管理或备份挖掘模型和结构。</span><span class="sxs-lookup"><span data-stu-id="ae6fb-109">Create DMX statements to manage or back up mining models and structures.</span></span>  
  
## <a name="using-the-query-wizard"></a><span data-ttu-id="ae6fb-110">使用查询向导</span><span class="sxs-lookup"><span data-stu-id="ae6fb-110">Using the Query Wizard</span></span>  
  
1.  <span data-ttu-id="ae6fb-111">首先，必须指定要用作输入的数据的源。</span><span class="sxs-lookup"><span data-stu-id="ae6fb-111">First, you must specify a source for the data to use as input.</span></span> <span data-ttu-id="ae6fb-112">您可以使用现有 Excel 表或区域中的数据，也可以指定一个 SQL 语句来检索数据。</span><span class="sxs-lookup"><span data-stu-id="ae6fb-112">You can use data in an existing Excel table or range, or you can specify a SQL statement to retrieve the data.</span></span>  
  
2.  <span data-ttu-id="ae6fb-113">然后，该向导提供一组要连接到的服务器上的数据挖掘模型。</span><span class="sxs-lookup"><span data-stu-id="ae6fb-113">Next, the wizard presents a list of data mining models on the server to which you are connected.</span></span> <span data-ttu-id="ae6fb-114">如果知道所需的模型，并且熟悉数据挖掘，则还可以单击 "**高级**" 打开**数据挖掘高级查询编辑器**。</span><span class="sxs-lookup"><span data-stu-id="ae6fb-114">If you know the model you want and are familiar with data mining, you can also click **Advanced** to open the **Data Mining Advanced Query Editor**.</span></span>  
  
3.  <span data-ttu-id="ae6fb-115">根据选择的模型类型，您必须指定包含要计算的数据的列，并且定义输入数据列与模型列之间的映射。</span><span class="sxs-lookup"><span data-stu-id="ae6fb-115">Depending on the type of model that you choose, you must specify the column that contains the data to be evaluated, and define mappings between the input data columns and the model columns.</span></span> <span data-ttu-id="ae6fb-116">根据选择的算法，您可以设置模型的其他属性。</span><span class="sxs-lookup"><span data-stu-id="ae6fb-116">Depending on the algorithm you choose, you can set other properties on the model.</span></span>  
  
4.  <span data-ttu-id="ae6fb-117">最后，还可以通过该向导选择一个或多个预测，并且指定存储结果的目标。</span><span class="sxs-lookup"><span data-stu-id="ae6fb-117">Finally, the wizard also gives you the ability to choose one or more predictions, and specify a destination in which to store the results.</span></span>  
  
 <span data-ttu-id="ae6fb-118">你随时都可以单击 "**高级**" 以切换到 "**数据挖掘高级查询编辑器**"，这使你可以更好地控制 DMX 语句的每个部分。</span><span class="sxs-lookup"><span data-stu-id="ae6fb-118">At any time, you can click **Advanced** to switch to the **Data Mining Advanced Query Editor**, which gives you more control over each part of the DMX statement.</span></span> <span data-ttu-id="ae6fb-119">有关如何使用高级查询编辑工具的详细信息，请参阅[高级数据挖掘查询编辑器](advanced-data-mining-query-editor.md)。</span><span class="sxs-lookup"><span data-stu-id="ae6fb-119">For more information about how to use the advanced query editing tools, see [Advanced Data Mining Query Editor](advanced-data-mining-query-editor.md).</span></span>  
  
### <a name="requirements"></a><span data-ttu-id="ae6fb-120">要求</span><span class="sxs-lookup"><span data-stu-id="ae6fb-120">Requirements</span></span>  
 <span data-ttu-id="ae6fb-121">若要使用**查询**向导，您必须连接到的实例 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="ae6fb-121">To use the **Query** wizard, you must be connected to an instance of [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)].</span></span> <span data-ttu-id="ae6fb-122">此外，服务器必须至少包含一个具有适当类型的数据挖掘模型。</span><span class="sxs-lookup"><span data-stu-id="ae6fb-122">Moreover, the server must contain at least one data mining model of an appropriate type.</span></span> <span data-ttu-id="ae6fb-123">如果没有可用的挖掘模型，您可以使用 Excel 数据挖掘客户端中提供的向导创建一个。</span><span class="sxs-lookup"><span data-stu-id="ae6fb-123">If no mining models are available, you can create one by using the wizards provided in the Data Mining Client for Excel.</span></span> <span data-ttu-id="ae6fb-124">有关如何使用向导创建新挖掘模式的信息，请参阅[创建数据挖掘模型](creating-a-data-mining-model.md)。</span><span class="sxs-lookup"><span data-stu-id="ae6fb-124">For information about how to create a new mining mode by using a wizard, see [Creating a Data Mining Model](creating-a-data-mining-model.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ae6fb-125">另请参阅</span><span class="sxs-lookup"><span data-stu-id="ae6fb-125">See Also</span></span>  
 <span data-ttu-id="ae6fb-126">[&#40;Excel 数据挖掘外接程序部署和缩放挖掘模型&#41;](deploying-and-scaling-mining-models-data-mining-add-ins-for-excel.md) </span><span class="sxs-lookup"><span data-stu-id="ae6fb-126">[Deploying and Scaling Mining Models &#40;Data Mining Add-ins for Excel&#41;](deploying-and-scaling-mining-models-data-mining-add-ins-for-excel.md) </span></span>  
 [<span data-ttu-id="ae6fb-127">Excel 数据挖掘客户端 &#40;SQL Server 数据挖掘外接程序&#41;</span><span class="sxs-lookup"><span data-stu-id="ae6fb-127">Data Mining Client for Excel &#40;SQL Server Data Mining Add-ins&#41;</span></span>](data-mining-client-for-excel-sql-server-data-mining-add-ins.md)  
  
  
