---
title: "\"查找表\" 对话框 (Analysis Services 多维数据) |Microsoft Docs"
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.cubeeditor.findtabledialog.f1
helpviewer_keywords:
- Find Table dialog box
ms.assetid: 133d28e8-55eb-4783-bb8b-d3776a95ebda
author: minewiskan
ms.author: owend
ms.openlocfilehash: ee22c912a3121841a7827e31d53f7b8baba72174
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87579178"
---
# <a name="find-table-dialog-box-analysis-services---multidimensional-data"></a><span data-ttu-id="d0c94-102">“查找表”对话框（Analysis Services - 多维数据）</span><span class="sxs-lookup"><span data-stu-id="d0c94-102">Find Table Dialog Box (Analysis Services - Multidimensional Data)</span></span>
  <span data-ttu-id="d0c94-103">使用 **中的** “查找表” [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] 对话框，可以在与维度、多维数据集或挖掘结构关联的数据源视图中查找表。</span><span class="sxs-lookup"><span data-stu-id="d0c94-103">Use the **Find Table** dialog box in [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] to locate a table in the data source view associated with a dimension, cube, or mining structure.</span></span> <span data-ttu-id="d0c94-104">通过执行以下操作可以在 [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)] 中显示此对话框：</span><span class="sxs-lookup"><span data-stu-id="d0c94-104">You can display this dialog box in [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)] by:</span></span>  
  
-   <span data-ttu-id="d0c94-105">在 **“维度设计器”** 的 **“维度结构”** 页上，单击 **“工具栏”** 窗格中的 **“查找表”**。</span><span class="sxs-lookup"><span data-stu-id="d0c94-105">Clicking **Find Table** from the **Toolbar** pane on the **Dimension Structure** page of the **Dimension Designer**.</span></span>  
  
-   <span data-ttu-id="d0c94-106">右键单击“维度设计器”\*\*\*\* 的“维度结构”\*\*\*\* 页上的“数据源视图”\*\*\*\* 窗格的背景，选择“查找表”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="d0c94-106">Right-clicking the background of the **Data Source View** pane on the **Dimension Structure** page of the **Dimension Designer** and selecting **Find Table**.</span></span>  
  
-   <span data-ttu-id="d0c94-107">在 **多维数据集设计器** 的 **“多维数据集结构”** 页，单击 **“工具栏”** 窗格中的 **“查找表”**。</span><span class="sxs-lookup"><span data-stu-id="d0c94-107">Clicking **Find Table** from the **Toolbar** pane on the **Cube Structure** page of the **Cube Designer**.</span></span>  
  
-   <span data-ttu-id="d0c94-108">右键单击“多维数据集设计器”的“多维数据集结构”页上的“数据源视图”窗格的背景，选择“查找表”\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="d0c94-108">Right-clicking the background of the **Data Source View** pane on the **Cube Structure** page of the **Cube Designer** and selecting **Find Table**.</span></span>  
  
-   <span data-ttu-id="d0c94-109">右键单击“数据挖掘模型设计器”的“挖掘结构”页上的“数据源视图”窗格的背景，选择“查找表”\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="d0c94-109">Right-clicking the background of the **Data Source View** pane on the **Mining Structure** page of the **Data Mining Model Designer** and selecting **Find Table**.</span></span>  
  
## <a name="options"></a><span data-ttu-id="d0c94-110">选项</span><span class="sxs-lookup"><span data-stu-id="d0c94-110">Options</span></span>  
 <span data-ttu-id="d0c94-111">**从数据源视图中选择表**</span><span class="sxs-lookup"><span data-stu-id="d0c94-111">**Select a table from data source view**</span></span>  
 <span data-ttu-id="d0c94-112">选择要在“数据源视图”\*\*\*\* 窗格中查找的表。</span><span class="sxs-lookup"><span data-stu-id="d0c94-112">Select the table to find in the **Data Source View** pane.</span></span> <span data-ttu-id="d0c94-113">使用此选项可显示一个包含可用对象及其类型的网格，这些对象及其类型与“筛选器”\*\*\*\* 中设置的筛选器匹配（如果未设置“筛选器”\*\*\*\*，则为所有表），但尚未显示在当前关系图中。</span><span class="sxs-lookup"><span data-stu-id="d0c94-113">This option displays a grid of available objects and their types that match the filter set in **Filter** (or all tables if **Filter** is not set) and have not yet been shown in the current diagram.</span></span>  
  
 <span data-ttu-id="d0c94-114">**Filter**</span><span class="sxs-lookup"><span data-stu-id="d0c94-114">**Filter**</span></span>  
 <span data-ttu-id="d0c94-115">键入用于限制所列对象的筛选条件，然后单击该按钮以筛选“从数据源视图中选择一个表”\*\*\*\* 中所列的表。</span><span class="sxs-lookup"><span data-stu-id="d0c94-115">Type the filter used to restrict the objects listed, and then click the button to filter the tables listed in **Select a table from data source view**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d0c94-116">另请参阅</span><span class="sxs-lookup"><span data-stu-id="d0c94-116">See Also</span></span>  
 <span data-ttu-id="d0c94-117">["程序集属性" 对话框 &#40;Analysis Services 多维数据&#41;](assembly-properties-dialog-box-analysis-services-multidimensional-data.md) </span><span class="sxs-lookup"><span data-stu-id="d0c94-117">[Assembly Properties Dialog Box &#40;Analysis Services - Multidimensional Data&#41;](assembly-properties-dialog-box-analysis-services-multidimensional-data.md) </span></span>  
 <span data-ttu-id="d0c94-118">[数据源视图 &#40;维度结构 "选项卡，维度设计器&#41; &#40;Analysis Services 多维数据&#41;](datasource-view-dimension-designer-analysis-services-multidimensional-data.md) </span><span class="sxs-lookup"><span data-stu-id="d0c94-118">[Data Source View &#40;Dimension Structure Tab, Dimension Designer&#41; &#40;Analysis Services - Multidimensional Data&#41;](datasource-view-dimension-designer-analysis-services-multidimensional-data.md) </span></span>  
 [<span data-ttu-id="d0c94-119">数据源视图 &#40;多维数据集结构 "选项卡、多维数据集设计器&#41; &#40;Analysis Services 多维数据&#41;</span><span class="sxs-lookup"><span data-stu-id="d0c94-119">Data Source View &#40;Cube Structure Tab, Cube Designer&#41; &#40;Analysis Services - Multidimensional Data&#41;</span></span>](data-source-view-cube-designer-analysis-services-multidimensional-data.md)  
  
  
