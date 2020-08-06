---
title: "\"显示表\" 对话框 (Analysis Services 多维数据) |Microsoft Docs"
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.cubeeditor.cubebuilder.showtabledialog.f1
helpviewer_keywords:
- Show Table dialog box
ms.assetid: 4c0bf4fa-5685-4269-bf7d-f0e9802ab4bf
author: minewiskan
ms.author: owend
ms.openlocfilehash: 15d90ccc5773663baf9c780a920d80e4adc38927
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87691900"
---
# <a name="show-table-dialog-box-analysis-services---multidimensional-data"></a><span data-ttu-id="c85c5-102">“显示表”对话框（Analysis Services - 多维数据）</span><span class="sxs-lookup"><span data-stu-id="c85c5-102">Show Table Dialog Box (Analysis Services - Multidimensional Data)</span></span>
  <span data-ttu-id="c85c5-103">使用 **中的** “显示表” [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] 对话框，可以包括与维度、多维数据集或挖掘结构相关联的数据源视图中的表。</span><span class="sxs-lookup"><span data-stu-id="c85c5-103">Use the **Show Table** dialog box in [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] to include tables from the data source view associated with a dimension, cube, or mining structure.</span></span> <span data-ttu-id="c85c5-104">通过执行以下操作可以在 [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] 中显示此对话框：</span><span class="sxs-lookup"><span data-stu-id="c85c5-104">You can display this dialog box in [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] by:</span></span>  
  
-   <span data-ttu-id="c85c5-105">在 **维度设计器** 的 **“维度结构”** 页上，在 **“工具栏”** 窗格中单击 **“显示表”**。</span><span class="sxs-lookup"><span data-stu-id="c85c5-105">Clicking **Show Tables** from the **Toolbar** pane on the **Dimension Structure** page of **Dimension Designer**.</span></span>  
  
-   <span data-ttu-id="c85c5-106">在**维度设计器**的“维度结构”页上，右键单击“数据源视图”窗格的背景，然后选择“显示表”\*\*\*\*\*\*\*\*\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="c85c5-106">Right-clicking the background of the **Data Source View** pane on the **Dimension Structure** page of **Dimension Designer** and selecting **Show Tables**.</span></span>  
  
-   <span data-ttu-id="c85c5-107">在 **多维数据集设计器** 的 **“多维数据集结构”** 页上，在 **“工具栏”** 窗格中单击 **“显示表”**。</span><span class="sxs-lookup"><span data-stu-id="c85c5-107">Clicking **Show Tables** from the **Toolbar** pane on the **Cube Structure** page of **Cube Designer**.</span></span>  
  
-   <span data-ttu-id="c85c5-108">在**多维数据集设计器**的“多维数据集结构”页上，右键单击“数据源视图”窗格的背景，然后选择“显示表”\*\*\*\*\*\*\*\*\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="c85c5-108">Right-clicking the background of the **Data Source View** pane on the **Cube Structure** page of **Cube Designer** and selecting **Show Tables**.</span></span>  
  
-   <span data-ttu-id="c85c5-109">在**数据挖掘模型设计器**的“挖掘结构”页上，右键单击“数据源视图”窗格的背景，然后选择“显示表”\*\*\*\*\*\*\*\*\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="c85c5-109">Right-clicking the background of the **Data Source View** pane on the **Mining Structure** page of **Data Mining Model Designer** and selecting **Show Tables**.</span></span>  
  
## <a name="options"></a><span data-ttu-id="c85c5-110">选项</span><span class="sxs-lookup"><span data-stu-id="c85c5-110">Options</span></span>  
 <span data-ttu-id="c85c5-111">**选择要显示的其他表**</span><span class="sxs-lookup"><span data-stu-id="c85c5-111">**Select additional tables to be shown**</span></span>  
 <span data-ttu-id="c85c5-112">选择要添加到“数据源视图”窗格中的表\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="c85c5-112">Select the tables to add to the **Data Source View** pane.</span></span> <span data-ttu-id="c85c5-113">使用此选项可显示一个包含可用对象及其类型的网格，这些对象及其类型与“筛选器”\*\*\*\* 中设置的筛选器匹配（如果未设置“筛选器”\*\*\*\*，则为所有表），但尚未显示在当前关系图中。</span><span class="sxs-lookup"><span data-stu-id="c85c5-113">This option displays a grid of available objects and their types that match the filter set in **Filter** (or all tables if **Filter** is not set) and have not yet been shown in the current diagram.</span></span>  
  
 <span data-ttu-id="c85c5-114">**Filter**</span><span class="sxs-lookup"><span data-stu-id="c85c5-114">**Filter**</span></span>  
 <span data-ttu-id="c85c5-115">键入用来限制所列对象的筛选器，再单击该按钮，即可对“选择要显示的其他表”\*\*\*\* 中列出的表进行筛选。</span><span class="sxs-lookup"><span data-stu-id="c85c5-115">Type the filter used to restrict the objects listed, and then click the button to filter the tables listed in **Select additional tables to be shown**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c85c5-116">另请参阅</span><span class="sxs-lookup"><span data-stu-id="c85c5-116">See Also</span></span>  
 <span data-ttu-id="c85c5-117">[&#40;多维数据的 Analysis Services 设计器和对话框&#41;](analysis-services-designers-and-dialog-boxes-multidimensional-data.md) </span><span class="sxs-lookup"><span data-stu-id="c85c5-117">[Analysis Services Designers and Dialog Boxes &#40;Multidimensional Data&#41;](analysis-services-designers-and-dialog-boxes-multidimensional-data.md) </span></span>  
 <span data-ttu-id="c85c5-118">[数据源视图 &#40;维度结构 "选项卡，维度设计器&#41; &#40;Analysis Services 多维数据&#41;](datasource-view-dimension-designer-analysis-services-multidimensional-data.md) </span><span class="sxs-lookup"><span data-stu-id="c85c5-118">[Data Source View &#40;Dimension Structure Tab, Dimension Designer&#41; &#40;Analysis Services - Multidimensional Data&#41;](datasource-view-dimension-designer-analysis-services-multidimensional-data.md) </span></span>  
 [<span data-ttu-id="c85c5-119">数据源视图 &#40;多维数据集结构 "选项卡、多维数据集设计器&#41; &#40;Analysis Services 多维数据&#41;</span><span class="sxs-lookup"><span data-stu-id="c85c5-119">Data Source View &#40;Cube Structure Tab, Cube Designer&#41; &#40;Analysis Services - Multidimensional Data&#41;</span></span>](data-source-view-cube-designer-analysis-services-multidimensional-data.md)  
  
  
