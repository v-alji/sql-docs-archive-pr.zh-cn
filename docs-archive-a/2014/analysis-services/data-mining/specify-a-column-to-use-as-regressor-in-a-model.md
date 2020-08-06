---
title: 在模型中指定用作回归量的列 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: d8e0cb8e-302a-4166-9ed0-e2d9e2919b0a
author: minewiskan
ms.author: owend
ms.openlocfilehash: 86899d3793985b5e3c07618360d7b6a540935a54
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87577078"
---
# <a name="specify-a-column-to-use-as-regressor-in-a-model"></a><span data-ttu-id="74caa-102">在模型中指定用作回归量的列</span><span class="sxs-lookup"><span data-stu-id="74caa-102">Specify a Column to Use as Regressor in a Model</span></span>
  <span data-ttu-id="74caa-103">线性回归模型将可预测属性的值表示为结合了各种输入的公式的结果，这样，数据将尽可能接近地适合于估计的回归线。</span><span class="sxs-lookup"><span data-stu-id="74caa-103">A linear regression model represents the value of the predictable attribute as the result of a formula that combines the inputs in such a way that the data is fitted as a closely as possible to an estimated regression line.</span></span> <span data-ttu-id="74caa-104">该算法只接受数值作为输入，并且自动检测提供最佳调整的输入。</span><span class="sxs-lookup"><span data-stu-id="74caa-104">The algorithm accepts only numeric values as inputs, and automatically detects the inputs that provide the best fit.</span></span>  
  
 <span data-ttu-id="74caa-105">不过，您可以通过将 FORCE_REGRESSOR 参数添加到该模型并指定要使用的回归量，指定要作为回归量包括的列。</span><span class="sxs-lookup"><span data-stu-id="74caa-105">However, you can specify that a column be included as a regressor by adding the FORCE_REGRESSOR parameter to the model and specifying the regressors to use.</span></span> <span data-ttu-id="74caa-106">您最好在属性有意义的情况下（甚至在结果太小以致模型无法检测到时）或者您要确保属性包括在公式中时执行此操作。</span><span class="sxs-lookup"><span data-stu-id="74caa-106">You might want to do this in cases where the attribute has meaning even if the effect is too small to be detected by the model, or when you want to ensure that the attribute is included in the formula.</span></span>  
  
 <span data-ttu-id="74caa-107">下面的过程介绍的是如何使用 [神经网络教程](../../tutorials/lesson-5-build-models-intermediate-data-mining-tutorial.md)使用的示例数据创建简单线形回归模型。</span><span class="sxs-lookup"><span data-stu-id="74caa-107">The following procedure describes how to create a simple linear regression model, using the same sample data that is used for the [neural networks tutorial](../../tutorials/lesson-5-build-models-intermediate-data-mining-tutorial.md).</span></span> <span data-ttu-id="74caa-108">该模型不一定强健，但演示了如何使用数据挖掘设计器自定义线性回归模型。</span><span class="sxs-lookup"><span data-stu-id="74caa-108">The model is not necessarily robust, but demonstrates how to use the Data Mining Designer to customize a linear regression model.</span></span>  
  
### <a name="how-to-create-a-simple-linear-regression-model"></a><span data-ttu-id="74caa-109">如何创建简单线性回归模型</span><span class="sxs-lookup"><span data-stu-id="74caa-109">How to create a simple linear regression model</span></span>  
  
1.  <span data-ttu-id="74caa-110">在 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]的 **解决方案资源管理器**中，展开 **“挖掘结构”**。</span><span class="sxs-lookup"><span data-stu-id="74caa-110">In [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], in **Solution Explorer**, expand **Mining Structures**.</span></span>  
  
2.  <span data-ttu-id="74caa-111">双击 Call Center.dmm 以在设计器中将其打开。</span><span class="sxs-lookup"><span data-stu-id="74caa-111">Double-click Call Center.dmm to open it in the designer.</span></span>  
  
3.  <span data-ttu-id="74caa-112">从 **“挖掘模型”** 菜单中，选择 **“新建挖掘模型”**。</span><span class="sxs-lookup"><span data-stu-id="74caa-112">From the **Mining Model** menu, select **New Mining Model**.</span></span>  
  
4.  <span data-ttu-id="74caa-113">对于算法，选择 **“Microsoft 线性回归”**。</span><span class="sxs-lookup"><span data-stu-id="74caa-113">For the algorithm, select **Microsoft Linear Regression**.</span></span> <span data-ttu-id="74caa-114">对于名称，键入“呼叫中心回归”。 \*\*\*\*</span><span class="sxs-lookup"><span data-stu-id="74caa-114">For the name, type **Call Center Regression**.</span></span>  
  
5.  <span data-ttu-id="74caa-115">在 **“挖掘模型”** 选项卡中，按如下所示更改列用法。</span><span class="sxs-lookup"><span data-stu-id="74caa-115">In the **Mining Models** tab, change the column usage as follows.</span></span> <span data-ttu-id="74caa-116">不在以下列表中的所有列都应设置为 **“忽略”**（如果尚未设置它们）。</span><span class="sxs-lookup"><span data-stu-id="74caa-116">All columns not in the following list should be set to **Ignore**, if they are not already.</span></span>  
  
     <span data-ttu-id="74caa-117">FactCallCenterID**键**</span><span class="sxs-lookup"><span data-stu-id="74caa-117">FactCallCenterID**Key**</span></span>  
  
     <span data-ttu-id="74caa-118">ServiceGrade**仅预测**</span><span class="sxs-lookup"><span data-stu-id="74caa-118">ServiceGrade**PredictOnly**</span></span>  
  
     <span data-ttu-id="74caa-119">Total Operators**输入**</span><span class="sxs-lookup"><span data-stu-id="74caa-119">Total Operators**Input**</span></span>  
  
     <span data-ttu-id="74caa-120">AverageTimePerIssue**输入**</span><span class="sxs-lookup"><span data-stu-id="74caa-120">AverageTimePerIssue**Input**</span></span>  
  
6.  <span data-ttu-id="74caa-121">从 **“挖掘模型”** 菜单上，选择 **“设置模型参数”**。</span><span class="sxs-lookup"><span data-stu-id="74caa-121">From the **Mining Model** menu, select **Set Model Parameters**.</span></span>  
  
7.  <span data-ttu-id="74caa-122">对于参数 FORCE_REGRESSOR，在“值”列中，键入用方括号括起来的列名称，各名称之间用逗号分隔，如下所示：\*\*\*\*</span><span class="sxs-lookup"><span data-stu-id="74caa-122">For the parameter, FORCE_REGRESSOR, in the **Value** column, type the column names enclosed in brackets and separated by a comma, as follows:</span></span>  
  
    ```  
    [Average Time Per Issue],[Total Operators]  
    ```  
  
    > [!NOTE]  
    >  <span data-ttu-id="74caa-123">算法将自动检测哪些列是最佳回归量。</span><span class="sxs-lookup"><span data-stu-id="74caa-123">The algorithm will automatically detect which columns are the best regressors.</span></span> <span data-ttu-id="74caa-124">在您想要确保某一列包括在最终的公式中时，只需强制回归量。</span><span class="sxs-lookup"><span data-stu-id="74caa-124">You only need to force regressors when you want to ensure that a column is included in the final formula.</span></span>  
  
8.  <span data-ttu-id="74caa-125">从 **“挖掘模型”** 菜单中，选择 **“处理模型”**。</span><span class="sxs-lookup"><span data-stu-id="74caa-125">From the **Mining Model** menu, select **Process Model**.</span></span>  
  
     <span data-ttu-id="74caa-126">在查看器中，该模型将表示为包含递归公式的单个节点。</span><span class="sxs-lookup"><span data-stu-id="74caa-126">In the viewer, the model is represented a single node containing the regression formula.</span></span> <span data-ttu-id="74caa-127">您可以在 **“挖掘图例”** 中查看该公式，或者可以通过使用查询提取公式的系数。</span><span class="sxs-lookup"><span data-stu-id="74caa-127">You can view the formula in the **Mining Legend**, or you can extract the coefficients for the formula by using queries.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="74caa-128">另请参阅</span><span class="sxs-lookup"><span data-stu-id="74caa-128">See Also</span></span>  
 <span data-ttu-id="74caa-129">[Microsoft 线性回归算法](microsoft-linear-regression-algorithm.md) </span><span class="sxs-lookup"><span data-stu-id="74caa-129">[Microsoft Linear Regression Algorithm](microsoft-linear-regression-algorithm.md) </span></span>  
 <span data-ttu-id="74caa-130">[数据挖掘查询](data-mining-queries.md) </span><span class="sxs-lookup"><span data-stu-id="74caa-130">[Data Mining Queries](data-mining-queries.md) </span></span>  
 <span data-ttu-id="74caa-131">[Microsoft 线性回归算法技术参考](microsoft-linear-regression-algorithm-technical-reference.md) </span><span class="sxs-lookup"><span data-stu-id="74caa-131">[Microsoft Linear Regression Algorithm Technical Reference](microsoft-linear-regression-algorithm-technical-reference.md) </span></span>  
 [<span data-ttu-id="74caa-132">线性回归模型的挖掘模型内容（Analysis Services - 数据挖掘）</span><span class="sxs-lookup"><span data-stu-id="74caa-132">Mining Model Content for Linear Regression Models &#40;Analysis Services - Data Mining&#41;</span></span>](mining-model-content-for-linear-regression-models-analysis-services-data-mining.md)  
  
  
