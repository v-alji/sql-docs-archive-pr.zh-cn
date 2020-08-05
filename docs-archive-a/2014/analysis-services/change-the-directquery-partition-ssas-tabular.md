---
title: " (SSAS 表格) 更改 DirectQuery 分区 |Microsoft Docs"
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: f9df1e66-dd23-41b4-95eb-af110d10eda4
author: minewiskan
ms.author: owend
ms.openlocfilehash: 43d14785f72d9bfe6406e2b81d3f1b97e9b7cc2e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87579901"
---
# <a name="change-the-directquery-partition-ssas-tabular"></a><span data-ttu-id="af4e2-102">更改 DirectQuery 分区（SSAS 表格）</span><span class="sxs-lookup"><span data-stu-id="af4e2-102">Change the DirectQuery Partition (SSAS Tabular)</span></span>
  <span data-ttu-id="af4e2-103">因为在一个表中只能有一个分区可以指定为 DirectQuery 分区，所以，默认情况下，Analysis Services 使用在该表中创建的第一个分区。</span><span class="sxs-lookup"><span data-stu-id="af4e2-103">Because only one partition in a table can be designated as the DirectQuery partition, by default, Analysis Services uses the first partition that was created in the table.</span></span> <span data-ttu-id="af4e2-104">在模型项目创作过程中，您可以通过使用 [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]中的“分区管理器”对话框来更改 DirectQuery 分区。</span><span class="sxs-lookup"><span data-stu-id="af4e2-104">During model project authoring, you can change the DirectQuery partition by using the Partition Manager dialog box in [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)].</span></span> <span data-ttu-id="af4e2-105">对于部署的模型，您可以通过使用 [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)]来更改 DirectQuery 分区。</span><span class="sxs-lookup"><span data-stu-id="af4e2-105">For deployed models, you can change the DirectQuery partition by using [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)].</span></span>  
  
### <a name="change-the-directquery-partition-for-a-tabular-model-project"></a><span data-ttu-id="af4e2-106">更改表格模型项目的 DirectQuery 分区</span><span class="sxs-lookup"><span data-stu-id="af4e2-106">Change the DirectQuery partition for a tabular model project</span></span>  
  
1.  <span data-ttu-id="af4e2-107">在 [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)]的模型设计器中，单击包含已分区表的表（选项卡）。</span><span class="sxs-lookup"><span data-stu-id="af4e2-107">In [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)], in the model designer, click on the table (tab) that contains the partitioned table.</span></span>  
  
2.  <span data-ttu-id="af4e2-108">单击 **“表”** 菜单，然后单击 **“分区”**。</span><span class="sxs-lookup"><span data-stu-id="af4e2-108">Click on the **Table** menu, and then click **Partitions**.</span></span>  
  
3.  <span data-ttu-id="af4e2-109">在“分区管理器”中，作为当前直接查询分区的分区由分区名称上的前缀 **(DirectQuery)** 指示。\*\*\*\*</span><span class="sxs-lookup"><span data-stu-id="af4e2-109">In **Partition Manager**, the partition that is the current Direct Query partition in indicated by the prefix **(DirectQuery)** on the partition name.</span></span>  
  
     <span data-ttu-id="af4e2-110">从 **“分区”** 列表中选择一个不同的分区，然后单击 **“设置为 DirectQuery”**。</span><span class="sxs-lookup"><span data-stu-id="af4e2-110">Select a different partition from the **Partitions** list, and then click **Set as DirectQuery**.</span></span> <span data-ttu-id="af4e2-111">在选择当前 DirectQuery 分区时 **“设置为 DirectQuery”** 按钮未启用，并且在尚未为直接查询模式启用模型时不可见。</span><span class="sxs-lookup"><span data-stu-id="af4e2-111">The **Set as DirectQuery** button is not enabled when the current DirectQuery partition is selected, and is not visible if the model has not been enabled for Direct Query mode.</span></span>  
  
4.  <span data-ttu-id="af4e2-112">如果需要，请更改处理选项，然后单击 **“确定”**。</span><span class="sxs-lookup"><span data-stu-id="af4e2-112">If necessary, change the processing options, and then click **OK**.</span></span>  
  
### <a name="change-the-directquery-partition-for-a-deployed-tabular-model"></a><span data-ttu-id="af4e2-113">更改已部署表格模型的 DirectQuery 分区</span><span class="sxs-lookup"><span data-stu-id="af4e2-113">Change the DirectQuery partition for a deployed tabular model</span></span>  
  
1.  <span data-ttu-id="af4e2-114">在 [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)]的对象资源管理器中，打开模型数据库。</span><span class="sxs-lookup"><span data-stu-id="af4e2-114">In [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)], open the model database in Object Explorer.</span></span>  
  
2.  <span data-ttu-id="af4e2-115">展开“表”节点，右键单击已分区表，然后选择“分区”。\*\*\*\*\*\*\*\*</span><span class="sxs-lookup"><span data-stu-id="af4e2-115">Expand the **Tables** node, then right-click the partitioned table, and then select **Partitions**.</span></span>  
  
     <span data-ttu-id="af4e2-116">为用于 DirectQuery 模式而指定的分区在分区名称上具有前缀 (DirectQuery)。</span><span class="sxs-lookup"><span data-stu-id="af4e2-116">The partition that is designated for use with DirectQuery mode has the prefix (DirectQuery) on the partition name.</span></span>  
  
3.  <span data-ttu-id="af4e2-117">若要更改为其他分区，请单击 **“直接查询”** 工具栏图标以便打开 **“设置 DirectQuery 分区”** 对话框。</span><span class="sxs-lookup"><span data-stu-id="af4e2-117">To change to a different partition, click the **Direct Query** toolbar icon to open the **Set DirectQuery Partition** dialog box.</span></span> <span data-ttu-id="af4e2-118">在尚未为直接查询启用的模型上，DirectQuery 工具栏图标不可用。</span><span class="sxs-lookup"><span data-stu-id="af4e2-118">The DirectQuery toolbar icon is not available on models that have not been enabled for Direct Query.</span></span>  
  
4.  <span data-ttu-id="af4e2-119">从 **“分区名称”** 下拉列表中选择一个不同的分区，然后根据需要更改该分区上的处理选项。</span><span class="sxs-lookup"><span data-stu-id="af4e2-119">Choose a different partition from the **Partition Name** dropdown list, and then change processing options on the partition if necessary.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="af4e2-120">另请参阅</span><span class="sxs-lookup"><span data-stu-id="af4e2-120">See Also</span></span>  
 [<span data-ttu-id="af4e2-121">分区（SSAS 表格）</span><span class="sxs-lookup"><span data-stu-id="af4e2-121">Partitions &#40;SSAS Tabular&#41;</span></span>](tabular-models/partitions-ssas-tabular.md)  
  
  
