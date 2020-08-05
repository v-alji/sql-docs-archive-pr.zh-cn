---
title: " (数据挖掘向导) 中选择源多维数据集维度 |Microsoft Docs"
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.dm.dmwizard.selectsourcecube.f1
ms.assetid: 556e216b-5e21-4160-967d-4c57591fbab4
author: minewiskan
ms.author: owend
ms.openlocfilehash: 6295a5312b4501236e0ce8f5776fc43c0d014581
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87579081"
---
# <a name="select-the-source-cube-dimension-data-mining-wizard"></a><span data-ttu-id="fbaa6-102">选择源多维数据集维度（数据挖掘向导）</span><span class="sxs-lookup"><span data-stu-id="fbaa6-102">Select the Source Cube Dimension (Data Mining Wizard)</span></span>
  <span data-ttu-id="fbaa6-103">可以使用 **“选择源多维数据集维度”** 页，从包含要分析的事例的多维数据集中选择维度。</span><span class="sxs-lookup"><span data-stu-id="fbaa6-103">Use the **Select the Source Cube Dimension** page to select the dimension from the cube that contains the cases you want to analyze.</span></span> <span data-ttu-id="fbaa6-104">例如，如果您在生成一个依据人口统计信息对客户的购买行为进行分析的模型，您会选择 Customer 维度，该维度中通常包含每个客户的唯一记录以及表示人口统计信息（如性别、住址或收入）的各种属性。</span><span class="sxs-lookup"><span data-stu-id="fbaa6-104">For example, if you are building a model that analyzes the purchasing behavior of customers based on demographics, you would select the Customer dimension, which typically contains a unique record for each customer and various attributes that represent demographics, such as gender, location, or income.</span></span> <span data-ttu-id="fbaa6-105">在该向导的后面部分，您将可以添加一个与此事例表相关的表：例如，您可能添加一个列出该客户已购买产品的嵌套表。</span><span class="sxs-lookup"><span data-stu-id="fbaa6-105">Later in the wizard you will have the opportunity to add a table that is related to this case table: for example, you might add a nested table that shows which products the customer has purchased.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="fbaa6-106"> 只有在向导的 **“选择定义方法”** 页上选择了 **“从现有多维数据集”** 之后，才会显示此页。</span><span class="sxs-lookup"><span data-stu-id="fbaa6-106">This page will appear only if you have selected **From existing cube** on the **Select the Definition Method** page of the wizard.</span></span>  
  
## <a name="options"></a><span data-ttu-id="fbaa6-107">选项</span><span class="sxs-lookup"><span data-stu-id="fbaa6-107">Options</span></span>  
 <span data-ttu-id="fbaa6-108">**选择源多维数据集维度**</span><span class="sxs-lookup"><span data-stu-id="fbaa6-108">**Select a Source Cube Dimension**</span></span>  
 <span data-ttu-id="fbaa6-109">选择将为挖掘结构提供源数据的多维数据集的维度。</span><span class="sxs-lookup"><span data-stu-id="fbaa6-109">Select the dimension of the cube that will provide the source data for your mining structure.</span></span>  
  
## <a name="choosing-a-dimension"></a><span data-ttu-id="fbaa6-110">选择维度</span><span class="sxs-lookup"><span data-stu-id="fbaa6-110">Choosing a Dimension</span></span>  
 <span data-ttu-id="fbaa6-111">因为只能选择一个维度在模型中使用，因此请务必了解多维数据集结构并选择可为您的模型提供最佳信息的维度。</span><span class="sxs-lookup"><span data-stu-id="fbaa6-111">Because you can select only one dimension for use in your model, it is important that you understand the cube structure and select the dimension that provides the best information for your model.</span></span> <span data-ttu-id="fbaa6-112">如果无法确定要使用的维度，使用维度设计器浏览多维数据集并查看其中的字段和数据可能会很有用。</span><span class="sxs-lookup"><span data-stu-id="fbaa6-112">If you are not sure which dimension to use, it might be helpful to browse the cube and review the fields and the data in them by using Dimension Designer.</span></span> <span data-ttu-id="fbaa6-113">有关详细信息，请参阅[在维度设计器中浏览维度数据](multidimensional-models/database-dimensions-browse-dimension-data-in-dimension-designer.md)。</span><span class="sxs-lookup"><span data-stu-id="fbaa6-113">For more information, see [Browse Dimension Data in Dimension Designer](multidimensional-models/database-dimensions-browse-dimension-data-in-dimension-designer.md).</span></span>  
  
 <span data-ttu-id="fbaa6-114">如果你不熟悉维度，请参阅[维度简介（Analysis Services - 多维数据）](multidimensional-models-olap-logical-dimension-objects/dimensions-analysis-services-multidimensional-data.md)。</span><span class="sxs-lookup"><span data-stu-id="fbaa6-114">If you are unfamiliar with dimensions in general, see [Introduction to Dimensions &#40;Analysis Services - Multidimensional Data&#41;](multidimensional-models-olap-logical-dimension-objects/dimensions-analysis-services-multidimensional-data.md).</span></span>  
  
 <span data-ttu-id="fbaa6-115">有关单个维度中通常包含的信息类型（包括可能对数据挖掘有用的属性和度量值）的详细信息，请参阅 [Dimension Relationships](multidimensional-models-olap-logical-cube-objects/dimension-relationships.md)。</span><span class="sxs-lookup"><span data-stu-id="fbaa6-115">For more information about the type of information that is typically contained in a single dimension, including attributes and measures that might be useful for data mining, see [Dimension Relationships](multidimensional-models-olap-logical-cube-objects/dimension-relationships.md).</span></span>  
  
 <span data-ttu-id="fbaa6-116">如果选择的维度未包含生成数据挖掘模型所需的所有相关属性，则可能需要修改该维度。</span><span class="sxs-lookup"><span data-stu-id="fbaa6-116">If the dimension that you choose does not contain all of the related attributes that you need to build the data mining model, you might need to modify the dimension.</span></span> <span data-ttu-id="fbaa6-117">有关详细信息，请参阅 [定义数据库维度](multidimensional-models/define-database-dimensions.md)。</span><span class="sxs-lookup"><span data-stu-id="fbaa6-117">For more information, see [Define Database Dimensions](multidimensional-models/define-database-dimensions.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fbaa6-118">另请参阅</span><span class="sxs-lookup"><span data-stu-id="fbaa6-118">See Also</span></span>  
 <span data-ttu-id="fbaa6-119">[数据挖掘向导 F1 帮助 &#40;Analysis Services 数据挖掘&#41;](data-mining-wizard-f1-help-analysis-services-data-mining.md) </span><span class="sxs-lookup"><span data-stu-id="fbaa6-119">[Data Mining Wizard F1 Help &#40;Analysis Services - Data Mining&#41;](data-mining-wizard-f1-help-analysis-services-data-mining.md) </span></span>  
 <span data-ttu-id="fbaa6-120">[&#40;数据挖掘向导创建数据挖掘结构&#41;](create-the-data-mining-structure-data-mining-wizard.md) </span><span class="sxs-lookup"><span data-stu-id="fbaa6-120">[Create the Data Mining Structure &#40;Data Mining Wizard&#41;](create-the-data-mining-structure-data-mining-wizard.md) </span></span>  
 [<span data-ttu-id="fbaa6-121">在数据挖掘向导 &#40;选择事例密钥&#41;</span><span class="sxs-lookup"><span data-stu-id="fbaa6-121">Select the Case Key &#40;Data Mining Wizard&#41;</span></span>](select-the-case-key-data-mining-wizard.md)  
  
  
