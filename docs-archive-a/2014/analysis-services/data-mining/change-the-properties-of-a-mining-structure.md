---
title: 更改挖掘结构的属性 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- mining structures [Analysis Services], properties
ms.assetid: 03b16897-2e36-42b8-9f7d-db1b9b898401
author: minewiskan
ms.author: owend
ms.openlocfilehash: 2c1e63ad5fada770394e2fc283e0e592319281b2
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87682451"
---
# <a name="change-the-properties-of-a-mining-structure"></a><span data-ttu-id="19e8e-102">更改挖掘结构的属性</span><span class="sxs-lookup"><span data-stu-id="19e8e-102">Change the Properties of a Mining Structure</span></span>
  <span data-ttu-id="19e8e-103">有两种针对挖掘结构的属性，这两种属性均可以修改：</span><span class="sxs-lookup"><span data-stu-id="19e8e-103">There are two kinds of properties on a mining structure, both of which can be modified:</span></span>  
  
-   <span data-ttu-id="19e8e-104">影响整个结构的挖掘结构属性</span><span class="sxs-lookup"><span data-stu-id="19e8e-104">Properties of the mining structure that affect the entire structure</span></span>  
  
-   <span data-ttu-id="19e8e-105">针对结构中的单个列的属性</span><span class="sxs-lookup"><span data-stu-id="19e8e-105">Properties on individual columns in the structure</span></span>  
  
 <span data-ttu-id="19e8e-106">请注意，有些属性依赖于其他属性设置。</span><span class="sxs-lookup"><span data-stu-id="19e8e-106">Note that some properties are dependent on other property settings.</span></span> <span data-ttu-id="19e8e-107">例如，在您将列的数据类型设置为 `Discretized` 之前，不能设置控制绑定行为的属性（例如 <xref:Microsoft.AnalysisServices.ScalarMiningStructureColumn.DiscretizationMethod%2A> 或 <xref:Microsoft.AnalysisServices.ScalarMiningStructureColumn.DiscretizationBucketCount%2A>）。</span><span class="sxs-lookup"><span data-stu-id="19e8e-107">For example, you cannot set properties that control binning behavior (such as <xref:Microsoft.AnalysisServices.ScalarMiningStructureColumn.DiscretizationMethod%2A> or <xref:Microsoft.AnalysisServices.ScalarMiningStructureColumn.DiscretizationBucketCount%2A>) until you have set the data type of the column to `Discretized`.</span></span>  
  
 <span data-ttu-id="19e8e-108">有关挖掘结构属性的详细信息，请参阅 [挖掘结构列](mining-structure-columns.md)。</span><span class="sxs-lookup"><span data-stu-id="19e8e-108">For more information about mining structure properties, see [Mining Structure Columns](mining-structure-columns.md).</span></span>  
  
### <a name="to-change-the-properties-of-a-mining-structure"></a><span data-ttu-id="19e8e-109">更改挖掘结构的属性</span><span class="sxs-lookup"><span data-stu-id="19e8e-109">To change the properties of a mining structure</span></span>  
  
1.  <span data-ttu-id="19e8e-110">在数据挖掘设计器中的“挖掘结构”\*\*\*\* 选项卡上，右键单击挖掘结构或挖掘结构中的一列，然后选择“属性”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="19e8e-110">On the **Mining Structure** tab in Data Mining Designer, right-click either the mining structure or a column in the mining structure, and then select **Properties**.</span></span>  
  
     <span data-ttu-id="19e8e-111">此时将在屏幕右侧打开 **“属性”** 窗口（如果该窗口尚未可见）。</span><span class="sxs-lookup"><span data-stu-id="19e8e-111">The **Properties** window opens on the right side of the screen, if it was not already visible.</span></span>  
  
2.  <span data-ttu-id="19e8e-112">在 **“属性”** 窗口中，选择与要更改属性相对应的值，然后输入新的值。</span><span class="sxs-lookup"><span data-stu-id="19e8e-112">In the **Properties** window, select the value that corresponds to the property that you want to change, and then enter the new value.</span></span>  
  
     <span data-ttu-id="19e8e-113">在设计器中选择一个不同的元素后，新值即生效。</span><span class="sxs-lookup"><span data-stu-id="19e8e-113">The new value will take effect when you select a different element in the designer.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="19e8e-114">另请参阅</span><span class="sxs-lookup"><span data-stu-id="19e8e-114">See Also</span></span>  
 [<span data-ttu-id="19e8e-115">挖掘结构任务和操作指南</span><span class="sxs-lookup"><span data-stu-id="19e8e-115">Mining Structure Tasks and How-tos</span></span>](mining-structure-tasks-and-how-tos.md)  
  
  
