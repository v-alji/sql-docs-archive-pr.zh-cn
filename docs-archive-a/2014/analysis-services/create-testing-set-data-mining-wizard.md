---
title: " (数据挖掘向导) 创建测试集 |Microsoft Docs"
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.dm.dmwizard.holdout.f1
ms.assetid: d0a44b59-ffbd-45fc-baa8-6b8046b1a2f5
author: minewiskan
ms.author: owend
ms.openlocfilehash: ab22597224f5c6c6006a02af81fa6583886d93b1
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87587106"
---
# <a name="create-testing-set-data-mining-wizard"></a><span data-ttu-id="951bd-102">创建测试集（数据挖掘向导）</span><span class="sxs-lookup"><span data-stu-id="951bd-102">Create Testing Set (Data Mining Wizard)</span></span>
  <span data-ttu-id="951bd-103">可以使用 **“创建测试集”** 页指定用于定型的数据量，以及为用作测试集而保留的数据量。</span><span class="sxs-lookup"><span data-stu-id="951bd-103">Use the **Create Testing Set** page to specify how much of the data is to be used for training, and how much is to be reserved for use as a test set.</span></span> <span data-ttu-id="951bd-104">在创建挖掘结构时将数据分成定型集和测试集，可以更方便地评估以后创建的挖掘模型的准确性。</span><span class="sxs-lookup"><span data-stu-id="951bd-104">Separating data into a training and testing set when you create a mining structure makes it much easier to assess the accuracy of mining models that you create later.</span></span>  
  
 <span data-ttu-id="951bd-105">您可以将测试数据量指定为百分比，也可以指定一个数字来限定用于测试的事例的数量。</span><span class="sxs-lookup"><span data-stu-id="951bd-105">You can specify the amount of testing data as a percentage, or you can specify a number to limit the number of cases used for testing.</span></span> <span data-ttu-id="951bd-106">如果同时指定百分比和用于测试的事例的最大数量，则将同时使用这两个设置，测试数据集将包含较少的事例数。</span><span class="sxs-lookup"><span data-stu-id="951bd-106">If you specify both a percentage and a maximum number of cases to use for testing, both settings are used, and the testing data set contains the smaller number of cases.</span></span> <span data-ttu-id="951bd-107">默认情况下，30 % 的数据用于测试，70 % 的数据用于定型，没有最大测试事例数。</span><span class="sxs-lookup"><span data-stu-id="951bd-107">By default, 30 percent of data is used for testing, 70 percent for training, and there is no maximum number of test cases.</span></span>  
  
 <span data-ttu-id="951bd-108">默认情况下， [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 生成用于启动分区的数值种子。</span><span class="sxs-lookup"><span data-stu-id="951bd-108">By default, [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] generates a numeric seed that is used to start partitioning.</span></span> <span data-ttu-id="951bd-109">此种子基于挖掘结构的名称。</span><span class="sxs-lookup"><span data-stu-id="951bd-109">This seed is based on the name of the mining structure.</span></span> <span data-ttu-id="951bd-110">如果希望即使在挖掘结构名称更改的情况下分区仍保持不变，则可以设置挖掘结构的 HoldoutSeed 属性，为种子指定一个值。</span><span class="sxs-lookup"><span data-stu-id="951bd-110">If you want to ensure that the partition stays the same even if the name of the mining structure is changed, you can specify a value for the seed, by setting the HoldoutSeed property of the mining structure.</span></span> <span data-ttu-id="951bd-111">如果更改维持种子，则必须重新处理该结构。</span><span class="sxs-lookup"><span data-stu-id="951bd-111">If you change the holdout seed, you must reprocess the structure.</span></span>  
  
 <span data-ttu-id="951bd-112">如果以后要更改测试数据量或定型数据量，则可以 `HoldoutMaxCases` `HoldoutMaxPercent` 使用 "**属性**" 窗口修改数据挖掘结构的和属性。</span><span class="sxs-lookup"><span data-stu-id="951bd-112">If you later want to change the amount of testing or training data, you can modify the `HoldoutMaxCases` and `HoldoutMaxPercent` properties on the data mining structure by using the **Properties** window.</span></span> <span data-ttu-id="951bd-113">不过，进行更改后，必须重新处理挖掘结构及所有关联挖掘模型。</span><span class="sxs-lookup"><span data-stu-id="951bd-113">However, after you make the change you must reprocess the mining structure and all associated mining models.</span></span> <span data-ttu-id="951bd-114">还存在下列限制：</span><span class="sxs-lookup"><span data-stu-id="951bd-114">The following limitations also apply:</span></span>  
  
-   <span data-ttu-id="951bd-115">仅当数据挖掘结构存储在 [!INCLUDE[ssKatmai](../includes/sskatmai-md.md)]中时，才支持数据挖掘结构的分区。</span><span class="sxs-lookup"><span data-stu-id="951bd-115">Partitioning of a data mining structure is supported only when the data mining structure is stored in [!INCLUDE[ssKatmai](../includes/sskatmai-md.md)].</span></span> <span data-ttu-id="951bd-116">的早期版本 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 不支持缓存挖掘结构的分区信息。</span><span class="sxs-lookup"><span data-stu-id="951bd-116">Earlier versions of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] do not support caching of partition information for mining structures.</span></span>  
  
-   <span data-ttu-id="951bd-117">如果挖掘结构包含 Key Time 列（这是时序挖掘模型所必需的），则无法对挖掘结构进行分区。</span><span class="sxs-lookup"><span data-stu-id="951bd-117">You cannot partition a mining structure if the mining structure contains a Key Time column, which is required for time series mining models.</span></span>  
  
-   <span data-ttu-id="951bd-118">如果尝试预测的值存储在嵌套表中，则无法对数据进行分区。</span><span class="sxs-lookup"><span data-stu-id="951bd-118">You cannot partition data if you are trying to predict a value that is stored in a nested table.</span></span>  
  
 <span data-ttu-id="951bd-119">**有关详细信息，请参阅** [测试和验证（数据挖掘）](data-mining/testing-and-validation-data-mining.md)、[创建关系挖掘结构](data-mining/create-a-relational-mining-structure.md)、[数据挖掘基础教程](../../2014/tutorials/basic-data-mining-tutorial.md)</span><span class="sxs-lookup"><span data-stu-id="951bd-119">**For More Information:** [Testing and Validation &#40;Data Mining&#41;](data-mining/testing-and-validation-data-mining.md), [Create a Relational Mining Structure](data-mining/create-a-relational-mining-structure.md), [Basic Data Mining Tutorial](../../2014/tutorials/basic-data-mining-tutorial.md)</span></span>  
  
## <a name="options"></a><span data-ttu-id="951bd-120">选项</span><span class="sxs-lookup"><span data-stu-id="951bd-120">Options</span></span>  
 <span data-ttu-id="951bd-121">**测试数据百分比**</span><span class="sxs-lookup"><span data-stu-id="951bd-121">**Percentage of data for testing**</span></span>  
 <span data-ttu-id="951bd-122">单击向上箭头和向下箭头可以增大或减小用作测试数据的数据百分比，也可以在文本框中键入介于 0 到 100 之间的值。</span><span class="sxs-lookup"><span data-stu-id="951bd-122">Click the up and down arrows to increase or decrease the percentage of data to use as a training set, or type a value between 0 and 100 in the text box.</span></span>  
  
 <span data-ttu-id="951bd-123">**测试数据集中的最大事例数**</span><span class="sxs-lookup"><span data-stu-id="951bd-123">**Maximum number of cases in testing data set**</span></span>  
 <span data-ttu-id="951bd-124">键入一个数字，以限制可用于测试的事例数。</span><span class="sxs-lookup"><span data-stu-id="951bd-124">Type a number to limit the number of cases that can be used for testing.</span></span>  
  
 <span data-ttu-id="951bd-125">如果指定的数字大于数据中的实际事例数，则将使用所有事例。</span><span class="sxs-lookup"><span data-stu-id="951bd-125">If you specify a number that is larger than the number of actual cases in the data, all the cases will be used.</span></span>  
  
 <span data-ttu-id="951bd-126">默认值为 NULL。</span><span class="sxs-lookup"><span data-stu-id="951bd-126">The default is NULL.</span></span> <span data-ttu-id="951bd-127">这表示没有限制。</span><span class="sxs-lookup"><span data-stu-id="951bd-127">This means there is no limit.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="951bd-128">另请参阅</span><span class="sxs-lookup"><span data-stu-id="951bd-128">See Also</span></span>  
 <span data-ttu-id="951bd-129">[数据挖掘向导 F1 帮助 &#40;Analysis Services 数据挖掘&#41;](data-mining-wizard-f1-help-analysis-services-data-mining.md) </span><span class="sxs-lookup"><span data-stu-id="951bd-129">[Data Mining Wizard F1 Help &#40;Analysis Services - Data Mining&#41;](data-mining-wizard-f1-help-analysis-services-data-mining.md) </span></span>  
 <span data-ttu-id="951bd-130">[在数据挖掘向导 &#40;建议相关列&#41;](suggest-related-columns-data-mining-wizard.md) </span><span class="sxs-lookup"><span data-stu-id="951bd-130">[Suggest Related Columns &#40;Data Mining Wizard&#41;](suggest-related-columns-data-mining-wizard.md) </span></span>  
 <span data-ttu-id="951bd-131">[在数据挖掘向导 &#40;指定表类型&#41;](specify-table-types-data-mining-wizard.md) </span><span class="sxs-lookup"><span data-stu-id="951bd-131">[Specify Table Types &#40;Data Mining Wizard&#41;](specify-table-types-data-mining-wizard.md) </span></span>  
 [<span data-ttu-id="951bd-132">指定数据挖掘向导 &#40;列的内容和数据类型&#41;</span><span class="sxs-lookup"><span data-stu-id="951bd-132">Specify the Column's Content and Data Type &#40;Data Mining Wizard&#41;</span></span>](specify-the-column-s-content-and-data-type-data-mining-wizard.md)  
  
  
