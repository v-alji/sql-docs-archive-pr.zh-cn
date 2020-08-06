---
title: 将查询参数与报表参数相关联（报表生成器和 SSRS）| Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- queries [Reporting Services], parameters
- parameters [Reporting Services], queries
ms.assetid: 6d297e1a-ff71-472a-addc-349e863092b5
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: f65aa36e8910378d68963c8c9990518b661025ab
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87688616"
---
# <a name="associate-a-query-parameter-with-a-report-parameter-report-builder-and-ssrs"></a><span data-ttu-id="a0bc0-102">将查询参数与报表参数相关联（报表生成器和 SSRS）</span><span class="sxs-lookup"><span data-stu-id="a0bc0-102">Associate a Query Parameter with a Report Parameter (Report Builder and SSRS)</span></span>
  <span data-ttu-id="a0bc0-103">在您定义包含查询变量的数据集查询时，将对查询命令进行分析。</span><span class="sxs-lookup"><span data-stu-id="a0bc0-103">When you define a dataset query that contains a query variable, the query command is parsed.</span></span> <span data-ttu-id="a0bc0-104">对于每个查询变量，都会创建相应的数据集参数和报表参数。</span><span class="sxs-lookup"><span data-stu-id="a0bc0-104">For each query variable, a corresponding dataset parameter and report parameter are created.</span></span> <span data-ttu-id="a0bc0-105">数据集参数将指向报表参数。</span><span class="sxs-lookup"><span data-stu-id="a0bc0-105">The dataset parameter points to the report parameter.</span></span> <span data-ttu-id="a0bc0-106">这样可以使用户输入一个直接传递给查询的值。</span><span class="sxs-lookup"><span data-stu-id="a0bc0-106">This enables a user to enter a value that passes directly to the query.</span></span> <span data-ttu-id="a0bc0-107">每次您编辑查询命令时，都会发生相同的过程。</span><span class="sxs-lookup"><span data-stu-id="a0bc0-107">Each time you edit the query command, the same process takes place.</span></span>  
  
 <span data-ttu-id="a0bc0-108">如果重命名绑定到查询参数的报表参数，则需要使用本主题中的过程手动将查询参数链接到重命名的报表参数。</span><span class="sxs-lookup"><span data-stu-id="a0bc0-108">If you rename a report parameter that is bound to a query parameter, you need to manually link the query parameters to the renamed report parameter by using the procedure in this topic.</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
### <a name="to-associate-a-query-parameter-with-a-report-parameter"></a><span data-ttu-id="a0bc0-109">将查询参数与报表参数相关联</span><span class="sxs-lookup"><span data-stu-id="a0bc0-109">To associate a query parameter with a report parameter</span></span>  
  
1.  <span data-ttu-id="a0bc0-110">在“报表数据”窗格中，右键单击数据集，再单击“数据集属性”\*\*\*\*，然后单击“参数”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="a0bc0-110">In the Report Data pane, right-click the dataset, click **Dataset Properties**, and then click **Parameters**.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="a0bc0-111"> 如果“报表数据”窗格不可见，请单击 **“视图”** 菜单上的 **“报表数据”** 。</span><span class="sxs-lookup"><span data-stu-id="a0bc0-111">If the Report Data pane is not visible, click **Report Data** on the **View** menu.</span></span>  
  
2.  <span data-ttu-id="a0bc0-112">在 **“参数名称”** 列中，查找查询参数的名称。</span><span class="sxs-lookup"><span data-stu-id="a0bc0-112">In the column **Parameter Name**, find the name of the query parameter.</span></span> <span data-ttu-id="a0bc0-113">将基于查询自动填充参数名称。</span><span class="sxs-lookup"><span data-stu-id="a0bc0-113">Parameter names are automatically populated based on the query.</span></span> <span data-ttu-id="a0bc0-114">每次更改查询时，都会检查查询是否有新的查询参数。</span><span class="sxs-lookup"><span data-stu-id="a0bc0-114">Every time you change the query, the query is checked for new query parameters.</span></span> <span data-ttu-id="a0bc0-115">手动创建的查询参数不会随着查询的更改而变化。</span><span class="sxs-lookup"><span data-stu-id="a0bc0-115">Query parameters that you create manually are not changed when the query changes.</span></span>  
  
    -   <span data-ttu-id="a0bc0-116">在 **“参数名称”** 中，查找查询中存在的查询参数名称。</span><span class="sxs-lookup"><span data-stu-id="a0bc0-116">In **Parameter Name**, find the query parameter name as it exists in the query.</span></span> <span data-ttu-id="a0bc0-117">还可以手动添加新的查询参数，并输入名称。</span><span class="sxs-lookup"><span data-stu-id="a0bc0-117">You can also manually add a new query parameter and enter a name.</span></span>  
  
    -   <span data-ttu-id="a0bc0-118">在 **“参数值”** 中，键入或选择计算结果为要传递给查询参数的值的表达式。</span><span class="sxs-lookup"><span data-stu-id="a0bc0-118">In **Parameter Value**, type or select an expression that evaluates to the value to pass to the query parameter.</span></span> <span data-ttu-id="a0bc0-119">这通常为报表参数的名称。</span><span class="sxs-lookup"><span data-stu-id="a0bc0-119">This is typically the name of the report parameter.</span></span>  
  
        > [!NOTE]  
        >  <span data-ttu-id="a0bc0-120">您不仅可以将报表参数作为查询参数的值。</span><span class="sxs-lookup"><span data-stu-id="a0bc0-120">You are not limited to report parameters as values for a query parameter.</span></span> <span data-ttu-id="a0bc0-121">也可以使用任何表达式来计算参数值。</span><span class="sxs-lookup"><span data-stu-id="a0bc0-121">You can use any expression that evaluates to a value for the parameter value.</span></span>  
  
3.  <span data-ttu-id="a0bc0-122">对于其他查询参数，重复执行步骤 2。</span><span class="sxs-lookup"><span data-stu-id="a0bc0-122">Repeat step 2 for additional query parameters.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a0bc0-123">另请参阅</span><span class="sxs-lookup"><span data-stu-id="a0bc0-123">See Also</span></span>  
 <span data-ttu-id="a0bc0-124">[报表嵌入数据集和共享数据集 &#40;报表生成器和 SSRS&#41;](report-embedded-datasets-and-shared-datasets-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="a0bc0-124">[Report Embedded Datasets and Shared Datasets &#40;Report Builder and SSRS&#41;](report-embedded-datasets-and-shared-datasets-report-builder-and-ssrs.md) </span></span>  
 [<span data-ttu-id="a0bc0-125">报表参数概念 &#40;报表生成器和 SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="a0bc0-125">Report Parameters Concept &#40;Report Builder and SSRS&#41;</span></span>](../report-design/report-parameters-concepts-report-builder-and-ssrs.md)  
  
  
