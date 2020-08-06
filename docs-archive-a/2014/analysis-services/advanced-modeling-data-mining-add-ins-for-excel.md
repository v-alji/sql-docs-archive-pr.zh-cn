---
title: " (Excel) 的数据挖掘外接程序的高级建模 |Microsoft Docs"
ms.custom: ''
ms.date: 12/29/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- mining structures, creating
ms.assetid: 042270a3-6ec7-4b52-b2ba-2adb6c4740d5
author: minewiskan
ms.author: owend
ms.openlocfilehash: 771eb6111765b558995ee3b0eb98196c63951567
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87579431"
---
# <a name="advanced-modeling-data-mining-add-ins-for-excel"></a><span data-ttu-id="cdd05-102">高级建模（Excel 数据挖掘外接程序）</span><span class="sxs-lookup"><span data-stu-id="cdd05-102">Advanced Modeling (Data Mining Add-ins for Excel)</span></span>
  <span data-ttu-id="cdd05-103">您可以使用**高级**数据建模选项来创建自定义数据挖掘结构和模型，其中的参数不同于向导创建的参数。</span><span class="sxs-lookup"><span data-stu-id="cdd05-103">You can use the **Advanced** data modeling options to create custom data mining structures and models with parameters different from those created by the wizards.</span></span> <span data-ttu-id="cdd05-104">本节中介绍的两个向导可以帮助您创建全新的数据挖掘结构，以及可应用于现有数据挖掘结构的新挖掘模型。</span><span class="sxs-lookup"><span data-stu-id="cdd05-104">The two wizards described in this section help you create a completely new data mining structure, and a new mining model to apply to an existing data mining structure.</span></span>  
  
## <a name="create-mining-structure"></a><span data-ttu-id="cdd05-105">创建挖掘结构</span><span class="sxs-lookup"><span data-stu-id="cdd05-105">Create Mining Structure</span></span>  
 <span data-ttu-id="cdd05-106">![“数据挖掘”功能区中的“创建挖掘结构”按钮](media/dmc-createstruct.gif "“数据挖掘”功能区中的“创建挖掘结构”按钮")</span><span class="sxs-lookup"><span data-stu-id="cdd05-106">![Create Mining Structure button, Data Mining ribbon](media/dmc-createstruct.gif "Create Mining Structure button, Data Mining ribbon")</span></span>  
  
 <span data-ttu-id="cdd05-107">**创建挖掘结构向导**可帮助您生成新的数据挖掘结构。</span><span class="sxs-lookup"><span data-stu-id="cdd05-107">The **Create Mining Structure Wizard** helps you build a new data mining structure.</span></span> <span data-ttu-id="cdd05-108">结构是从指定数据源提取的数据集合。</span><span class="sxs-lookup"><span data-stu-id="cdd05-108">A structure is a collection of data extracted from a specified data source.</span></span>  <span data-ttu-id="cdd05-109">挖掘结构可以使用源中的新数据更新，但您在创建挖掘结构时需要定义数据类型和名称，以规定如何在分析中使用数据。</span><span class="sxs-lookup"><span data-stu-id="cdd05-109">A mining structure can be updated with new data at the source, but when you create the mining structure, you define data types and names that define how the data is used for analysis.</span></span>  
  
 <span data-ttu-id="cdd05-110">可以使用以下数据源生成结构：Excel 表、Excel 区域或已定义为 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 数据源视图的外部数据源中的任何数据。</span><span class="sxs-lookup"><span data-stu-id="cdd05-110">You can use the following data sources to build your structure: an Excel table, an Excel range, or any data in an external data source that has already been defined as an [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] data source view.</span></span>  
  
 <span data-ttu-id="cdd05-111">对于每种结构，您都可以选择留出一些数据来用于测试和验证。</span><span class="sxs-lookup"><span data-stu-id="cdd05-111">For each structure, you have the option of setting aside some of the data to use for testing and validation.</span></span> <span data-ttu-id="cdd05-112">通过在设置数据源时创建此*维持数据集*，可以确保所有基于该结构的模型都能够使用一致的数据集进行测试。</span><span class="sxs-lookup"><span data-stu-id="cdd05-112">By creating this *holdout data set* when you set up your data sources, you can ensure that all models that are based on the structure are able to use a consistent data set for testing.</span></span>  
  
 <span data-ttu-id="cdd05-113">创建挖掘结构之后，可以添加多个挖掘模型来应用不同的分析方法。</span><span class="sxs-lookup"><span data-stu-id="cdd05-113">After you have created a mining structure, you can add multiple models to apply different methods of analysis.</span></span>  
  
 <span data-ttu-id="cdd05-114">有关如何使用**创建挖掘结构向导**的详细信息，请参阅[创建挖掘结构 &#40;SQL Server 数据挖掘外接程序&#41;](create-mining-structure-sql-server-data-mining-add-ins.md)。</span><span class="sxs-lookup"><span data-stu-id="cdd05-114">For more information about how to use the **Create Mining Structure Wizard**, see [Create Mining Structure &#40;SQL Server Data Mining Add-ins&#41;](create-mining-structure-sql-server-data-mining-add-ins.md).</span></span>  
  
## <a name="add-model-to-structure"></a><span data-ttu-id="cdd05-115">将模型添加到结构</span><span class="sxs-lookup"><span data-stu-id="cdd05-115">Add Model to Structure</span></span>  
 <span data-ttu-id="cdd05-116">![“将模型添加到结构”按钮](media/dmc-addmodel.gif "“将模型添加到结构”按钮")</span><span class="sxs-lookup"><span data-stu-id="cdd05-116">![Add Model to Structure button](media/dmc-addmodel.gif "Add Model to Structure button")</span></span>  
  
 <span data-ttu-id="cdd05-117">在向结构中添加新的模型时，可以通过使用不同的算法或者不同的参数对数据进行分析。</span><span class="sxs-lookup"><span data-stu-id="cdd05-117">When you add a new model to a structure, you analyze the data by using a different algorithm, or with different parameters.</span></span> <span data-ttu-id="cdd05-118">如果要使用“数据挖掘客户端”工具中未公开的某种算法创建模型，此选项尤其有用。</span><span class="sxs-lookup"><span data-stu-id="cdd05-118">This option is particularly useful if you want to create a model using one of the algorithms not exposed in the Data Mining Client tools.</span></span>  
  
 <span data-ttu-id="cdd05-119">您可以使用 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 支持的任意算法，例如：</span><span class="sxs-lookup"><span data-stu-id="cdd05-119">For example, you can use any of the algorithms supported by [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)], such as:</span></span>  
  
-   <span data-ttu-id="cdd05-120">线性回归</span><span class="sxs-lookup"><span data-stu-id="cdd05-120">Linear regression</span></span>  
  
-   <span data-ttu-id="cdd05-121">顺序分析和聚类分析</span><span class="sxs-lookup"><span data-stu-id="cdd05-121">Sequence clustering</span></span>  
  
-   <span data-ttu-id="cdd05-122">嵌套数据集的关联分析</span><span class="sxs-lookup"><span data-stu-id="cdd05-122">Association analysis on nested data sets</span></span>  
  
 <span data-ttu-id="cdd05-123">若要查看可用的挖掘结构类型，可以 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 通过单击 "**管理模型**" 或 "**浏览**" 来浏览中存储的模型和结构。</span><span class="sxs-lookup"><span data-stu-id="cdd05-123">To see what kind of mining structures are available, you can browse the models and structures stored in [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] by clicking either **Manage Models** or **Browse**.</span></span>  
  
 <span data-ttu-id="cdd05-124">您只能看到当前会话过程中创建的数据挖掘结构或保存到 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 实例的挖掘结构。</span><span class="sxs-lookup"><span data-stu-id="cdd05-124">You are limited to data mining structures that were created during the current session, or mining structures that were saved to an instance of [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)].</span></span>  
  
 <span data-ttu-id="cdd05-125">有关详细信息，请参阅[将模型添加到 &#40;用于 Excel 的数据挖掘外接程序&#41;](add-model-to-structure-data-mining-add-ins-for-excel.md)。</span><span class="sxs-lookup"><span data-stu-id="cdd05-125">For more information, see [Add Model to Structure &#40;Data Mining Add-ins for Excel&#41;](add-model-to-structure-data-mining-add-ins-for-excel.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cdd05-126">另请参阅</span><span class="sxs-lookup"><span data-stu-id="cdd05-126">See Also</span></span>  
 <span data-ttu-id="cdd05-127">[管理 &#40;SQL Server 数据挖掘外接程序的模型&#41;](manage-models-sql-server-data-mining-add-ins.md) </span><span class="sxs-lookup"><span data-stu-id="cdd05-127">[Manage Models &#40;SQL Server Data Mining Add-ins&#41;](manage-models-sql-server-data-mining-add-ins.md) </span></span>  
 [<span data-ttu-id="cdd05-128">在 Excel 中浏览模型 &#40;SQL Server 数据挖掘外接程序&#41;</span><span class="sxs-lookup"><span data-stu-id="cdd05-128">Browsing Models in Excel &#40;SQL Server Data Mining Add-ins&#41;</span></span>](browsing-models-in-excel-sql-server-data-mining-add-ins.md)  
  
  
