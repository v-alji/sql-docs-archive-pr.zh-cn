---
title: "\"分区源\" 对话框 (Analysis Services 多维数据) |Microsoft Docs"
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.partitionsourcedialog.f1
ms.assetid: c414dabe-9bad-49b7-9a3c-dfca87fef92b
author: minewiskan
ms.author: owend
ms.openlocfilehash: 6732e8f00dc0d01e0d3b708794a1d9c497ae4cf5
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87682403"
---
# <a name="partition-source-dialog-box-analysis-services---multidimensional-data"></a><span data-ttu-id="388e5-102">“分区源”对话框（Analysis Services - 多维数据）</span><span class="sxs-lookup"><span data-stu-id="388e5-102">Partition Source Dialog Box (Analysis Services - Multidimensional Data)</span></span>
  <span data-ttu-id="388e5-103">可以使用 **中的** “分区源” [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] 对话框，为分区指定事实数据表的数据源。</span><span class="sxs-lookup"><span data-stu-id="388e5-103">Use the **Partition Source** dialog box in [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] to specify the source of fact table data for a partition.</span></span> <span data-ttu-id="388e5-104">您可以通过执行以下操作之一显示 **“分区源”** 对话框：</span><span class="sxs-lookup"><span data-stu-id="388e5-104">You can display the **Partition Source** dialog box by:</span></span>  
  
-   <span data-ttu-id="388e5-105">在多维数据集设计器中 **“分区”** 选项卡上的 **“度量值组”** 窗格中，单击所选度量值组的 **“分区”** 网格中某个单元的 **...** 按钮。</span><span class="sxs-lookup"><span data-stu-id="388e5-105">Clicking the **...** button on a cell from the **Partitions** grid of a selected measure group in the **Measure Groups** pane on the **Partitions** tab in Cube Designer.</span></span>  
  
-   <span data-ttu-id="388e5-106">在 **中的** “属性” **窗口中，单击** “分区” **对象的** “源” **属性值的** ... [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]按钮。</span><span class="sxs-lookup"><span data-stu-id="388e5-106">Clicking the **...** button on the **Source** property value of a **Partition** object in the **Properties** window in [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)].</span></span>  
  
## <a name="options"></a><span data-ttu-id="388e5-107">选项</span><span class="sxs-lookup"><span data-stu-id="388e5-107">Options</span></span>  
  
|<span data-ttu-id="388e5-108">选项</span><span class="sxs-lookup"><span data-stu-id="388e5-108">Option</span></span>|<span data-ttu-id="388e5-109">定义</span><span class="sxs-lookup"><span data-stu-id="388e5-109">Definition</span></span>|  
|------------|----------------|  
|<span data-ttu-id="388e5-110">**绑定类型**</span><span class="sxs-lookup"><span data-stu-id="388e5-110">**Binding type**</span></span>|<span data-ttu-id="388e5-111">选择用于指定分区的源的绑定类型。</span><span class="sxs-lookup"><span data-stu-id="388e5-111">Select the binding type to use for the source of the specified partition.</span></span> <span data-ttu-id="388e5-112">提供了以下选项：</span><span class="sxs-lookup"><span data-stu-id="388e5-112">The following options are available:</span></span><br /><br /> <span data-ttu-id="388e5-113">**表绑定**：选择此项可显示 "**表绑定详细信息**" 窗格并指示分区绑定到数据源或数据源视图中表的内容。</span><span class="sxs-lookup"><span data-stu-id="388e5-113">**Table binding**: Select to display the **Table Binding Detail** pane and indicate that the partition is bound to the contents of a table in a data source or data source view.</span></span> <span data-ttu-id="388e5-114">有关“表绑定详细信息”\*\*\*\* 窗格的详细信息，请参阅[表绑定详细信息（“分区源”对话框）（Analysis Services - 多维数据）](table-binding-partition-source-dialog-analysis-services-multidimensional-data.md)。</span><span class="sxs-lookup"><span data-stu-id="388e5-114">For more information about the **Table Binding Detail** pane, see [Table Binding Detail &#40;Partition Source Dialog Box&#41; &#40;Analysis Services - Multidimensional Data&#41;](table-binding-partition-source-dialog-analysis-services-multidimensional-data.md).</span></span><br /><br /> <span data-ttu-id="388e5-115">**详细信息**：选择此选择可以显示 "**查询绑定详细信息**" 窗格并指示分区绑定到对数据源执行的查询的内容。</span><span class="sxs-lookup"><span data-stu-id="388e5-115">**Detail**: Select to display the **Query Binding Detail** pane and indicate that the partition is bound to the contents of a query executed on a data source.</span></span> <span data-ttu-id="388e5-116">有关“查询绑定详细信息”\*\*\*\* 窗格的详细信息，请参阅[查询绑定详细信息（“分区源”对话框）（Analysis Services - 多维数据）](query-binding-partition-source-dialog-analysis-services-multidimensional-data.md)。</span><span class="sxs-lookup"><span data-stu-id="388e5-116">For more information about the **Query Binding Detail** pane, see [Query Binding Detail &#40;Partition Source Dialog Box&#41; &#40;Analysis Services - Multidimensional Data&#41;](query-binding-partition-source-dialog-analysis-services-multidimensional-data.md).</span></span>|  
|<span data-ttu-id="388e5-117">**详细信息**</span><span class="sxs-lookup"><span data-stu-id="388e5-117">**Detail**</span></span>|<span data-ttu-id="388e5-118">根据 **“绑定类型”** 选项的值的不同，显示 **“表绑定详细信息”** 对话框，或显示 **“查询绑定详细信息”** 对话框。</span><span class="sxs-lookup"><span data-stu-id="388e5-118">Displays either the **Table Binding Detail** dialog box or the **Query Binding Detail** dialog box, depending on the value of the **Binding type** option.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="388e5-119">另请参阅</span><span class="sxs-lookup"><span data-stu-id="388e5-119">See Also</span></span>  
 <span data-ttu-id="388e5-120">[&#40;多维数据集设计器&#41; &#40;Analysis Services 多维数据的分区&#41;](partitions-cube-designer-analysis-services-multidimensional-data.md) </span><span class="sxs-lookup"><span data-stu-id="388e5-120">[Partitions &#40;Cube Designer&#41; &#40;Analysis Services - Multidimensional Data&#41;](partitions-cube-designer-analysis-services-multidimensional-data.md) </span></span>  
 [<span data-ttu-id="388e5-121">&#40;多维数据的 Analysis Services 设计器和对话框&#41;</span><span class="sxs-lookup"><span data-stu-id="388e5-121">Analysis Services Designers and Dialog Boxes &#40;Multidimensional Data&#41;</span></span>](analysis-services-designers-and-dialog-boxes-multidimensional-data.md)  
  
  
