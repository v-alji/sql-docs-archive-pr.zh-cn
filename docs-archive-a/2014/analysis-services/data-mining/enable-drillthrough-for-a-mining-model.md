---
title: 为挖掘模型启用钻取 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- data mining [Analysis Services], how-to topics
- drillthrough [Analysis Services]
ms.assetid: 4fa44f60-ef9a-4b59-98c0-c0baf1195c8e
author: minewiskan
ms.author: owend
ms.openlocfilehash: 0a6adfc389776f91132e527130f50f61c9783d9f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87577911"
---
# <a name="enable-drillthrough-for-a-mining-model"></a><span data-ttu-id="2da57-102">对挖掘模型启用钻取</span><span class="sxs-lookup"><span data-stu-id="2da57-102">Enable Drillthrough for a Mining Model</span></span>
  <span data-ttu-id="2da57-103">如果为挖掘模型启用了钻取，则可以在浏览模型时检索用于创建模型的事例的详细信息。</span><span class="sxs-lookup"><span data-stu-id="2da57-103">If you have enabled drillthrough for a mining model, when you browse the model you can retrieve detailed information about the cases that were used to create the model.</span></span> <span data-ttu-id="2da57-104">若要查看这些信息，则您必须拥有必要的权限，且挖掘结构已经过处理。</span><span class="sxs-lookup"><span data-stu-id="2da57-104">To view this information, you must have the necessary permissions, and the structure must have already been processed.</span></span>  
  
 <span data-ttu-id="2da57-105">**权限** 如果用户要钻取模型数据或结构数据，则该用户必须是具有挖掘模型或挖掘结构的 [AllowDrillThrough](https://docs.microsoft.com/bi-reference/assl/properties/allowdrillthrough-element-assl) 权限的角色成员。</span><span class="sxs-lookup"><span data-stu-id="2da57-105">**Permissions** For a user to drill through to either model data or structure data, the user must be a member of a role that has [AllowDrillThrough](https://docs.microsoft.com/bi-reference/assl/properties/allowdrillthrough-element-assl) permissions on the mining model or mining structure.</span></span> <span data-ttu-id="2da57-106">挖掘结构和挖掘模型的钻取权限是分开设置的。</span><span class="sxs-lookup"><span data-stu-id="2da57-106">Drillthrough permissions are set separately on the structure and model.</span></span>  
  
-   <span data-ttu-id="2da57-107">即使不具有结构的钻取权限，模型的钻取权限也允许您从模型进行钻取。</span><span class="sxs-lookup"><span data-stu-id="2da57-107">Drillthrough permissions on the model enable you to drill through from the model, even if you do not have permissions on the structure.</span></span>  
  
-   <span data-ttu-id="2da57-108">如果拥有结构的钻取权限，则可通过使用 [StructureColumn (DMX)](/sql/dmx/structurecolumn-dmx) 函数，将结构列包含到模型钻取查询中。</span><span class="sxs-lookup"><span data-stu-id="2da57-108">Drillthrough permissions on the structure provide the additional ability to include structure columns in drillthrough queries from the model, by using the [StructureColumn &#40;DMX&#41;](/sql/dmx/structurecolumn-dmx) function.</span></span> <span data-ttu-id="2da57-109">您还可以使用 "选择 ..." 来查询结构中的定型和测试用例。FROM \<structure> 。Case 语法。</span><span class="sxs-lookup"><span data-stu-id="2da57-109">You can also query the training and test cases in the structure by using the SELECT... FROM \<structure>.CASES syntax.</span></span>  
  
 <span data-ttu-id="2da57-110">**缓存定型事例** 钻取就是检索挖掘结构中的定型事例的相关信息。</span><span class="sxs-lookup"><span data-stu-id="2da57-110">**Caching of training cases** Drillthrough works by retrieving information about the training cases in the mining structure.</span></span> <span data-ttu-id="2da57-111">这些信息是在处理结构时缓存的。</span><span class="sxs-lookup"><span data-stu-id="2da57-111">This information is cached when the structure is processed.</span></span> <span data-ttu-id="2da57-112">因此，如果通过将 <xref:Microsoft.AnalysisServices.MiningStructureCacheMode> 属性更改为 `ClearAfterProcessing`，选择清除了缓存的所有数据，则钻取功能将无法正常工作。</span><span class="sxs-lookup"><span data-stu-id="2da57-112">Therefore, if you choose to clear all cached data by changing the <xref:Microsoft.AnalysisServices.MiningStructureCacheMode> property to `ClearAfterProcessing`, drillthrough will not work.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="2da57-113">如果没有缓存定型事例，则必须将 <xref:Microsoft.AnalysisServices.MiningStructureCacheMode> 属性更改为 **KeepTrainingCases** ，并重新处理模型，然后才能查看事例数据。</span><span class="sxs-lookup"><span data-stu-id="2da57-113">If the training cases have not been cached, you must change the <xref:Microsoft.AnalysisServices.MiningStructureCacheMode> property to **KeepTrainingCases** and then reprocess the model before you can view the case data.</span></span>  
  
 <span data-ttu-id="2da57-114">有关详细信息，请参阅 [钻取查询（数据挖掘）](drillthrough-queries-data-mining.md)。</span><span class="sxs-lookup"><span data-stu-id="2da57-114">For more information, see [Drillthrough Queries &#40;Data Mining&#41;](drillthrough-queries-data-mining.md).</span></span>  
  
### <a name="to-enable-drillthrough-on-a-mining-model"></a><span data-ttu-id="2da57-115">对挖掘模型启用钻取</span><span class="sxs-lookup"><span data-stu-id="2da57-115">To enable drillthrough on a mining model</span></span>  
  
1.  <span data-ttu-id="2da57-116">在 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] 中数据挖掘设计器的“挖掘模型”\*\*\*\* 选项卡上，右键单击要针对其启用钻取的挖掘模型名称，再选择“属性”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="2da57-116">In [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], on the **Mining Models** tab of Data Mining Designer, right-click the name of the mining model on which you want to enable drillthrough, and select **Properties**.</span></span>  
  
2.  <span data-ttu-id="2da57-117">在 "**属性**" 窗口中，单击 " **AllowDrillthrough**"，然后选择 " **True**"。</span><span class="sxs-lookup"><span data-stu-id="2da57-117">In the **Properties** windows, click **AllowDrillthrough**, and select **True**.</span></span>  
  
3.  <span data-ttu-id="2da57-118">在“挖掘模型”选项卡中，右键单击所需的模型，再选择“处理模型”\*\*\*\*\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="2da57-118">In the **Mining Models** tab, right-click the model, and select **Process Model**.</span></span>  
  
### <a name="to-enable-caching-for-a-mining-structure"></a><span data-ttu-id="2da57-119">启用挖掘结构的缓存功能</span><span class="sxs-lookup"><span data-stu-id="2da57-119">To enable caching for a mining structure</span></span>  
  
1.  <span data-ttu-id="2da57-120">在 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] 中的数据挖掘设计器的“挖掘结构”\*\*\*\* 选项卡上，右键单击挖掘结构的名称。</span><span class="sxs-lookup"><span data-stu-id="2da57-120">In [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], on the **Mining Structure** tab of Data Mining Designer, right-click the name of the mining structure.</span></span>  
  
2.  <span data-ttu-id="2da57-121">打开 **“属性”** 窗口。</span><span class="sxs-lookup"><span data-stu-id="2da57-121">Open the **Properties** window.</span></span>  
  
3.  <span data-ttu-id="2da57-122">在 **“属性”** 窗口中，找到 **CacheMode** 属性，然后从列表中选择 **KeepTrainingCases** 。</span><span class="sxs-lookup"><span data-stu-id="2da57-122">In the **Properties** window, locate the **CacheMode** property, and select **KeepTrainingCases** from the list.</span></span>  
  
4.  <span data-ttu-id="2da57-123">在 **“数据集”** 菜单上，选择 **“处理”**。</span><span class="sxs-lookup"><span data-stu-id="2da57-123">On the **Database** menu, select **Process**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2da57-124">另请参阅</span><span class="sxs-lookup"><span data-stu-id="2da57-124">See Also</span></span>  
 [<span data-ttu-id="2da57-125">钻取查询（数据挖掘）</span><span class="sxs-lookup"><span data-stu-id="2da57-125">Drillthrough Queries &#40;Data Mining&#41;</span></span>](drillthrough-queries-data-mining.md)  
  
  
