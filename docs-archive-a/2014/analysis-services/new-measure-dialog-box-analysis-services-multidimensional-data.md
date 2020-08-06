---
title: "\"新建度量值\" 对话框 (Analysis Services 多维数据) |Microsoft Docs"
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.cubeeditor.newmeasuredialog.f1
helpviewer_keywords:
- New Measure dialog box
ms.assetid: 86dc9146-cc6d-4cef-b178-9a6b4cf616e8
author: minewiskan
ms.author: owend
ms.openlocfilehash: 1fb60bd598257d2de1f60900aafa43b085000fd8
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87694604"
---
# <a name="new-measure-dialog-box-analysis-services---multidimensional-data"></a><span data-ttu-id="19311-102">“新建度量值”对话框（Analysis Services - 多维数据）</span><span class="sxs-lookup"><span data-stu-id="19311-102">New Measure Dialog Box (Analysis Services - Multidimensional Data)</span></span>
  <span data-ttu-id="19311-103">可以使用 **中的** “新建度量值” [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] 对话框，在多维数据集设计器的度量值组中添加新度量值。</span><span class="sxs-lookup"><span data-stu-id="19311-103">Use the **New Measure** dialog box in [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] to add a new measure to a measure group in Cube Designer.</span></span> <span data-ttu-id="19311-104">通过执行以下操作之一，可以显示 **“新建度量值”** 对话框：</span><span class="sxs-lookup"><span data-stu-id="19311-104">You can display the **New Measure** dialog box by:</span></span>  
  
-   <span data-ttu-id="19311-105">在多维数据集设计器中的 **“多维数据集结构”** 选项卡上，单击 **“工具栏”** 窗格中的 **“新建度量值”** 。</span><span class="sxs-lookup"><span data-stu-id="19311-105">Clicking **New Measure** in the **Toolbar** pane on the **Cube Structure** tab in Cube Designer.</span></span>  
  
-   <span data-ttu-id="19311-106">在多维数据集设计器中的“多维数据集结构”\*\*\*\* 选项卡上，右键单击“度量值”\*\*\*\* 窗格中的度量值组或度量值，再从上下文菜单中选择“新建度量值”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="19311-106">Right-clicking a measure group or measure in the **Measures** pane on the **Cube Structure** tab in Cube Designer and selecting **New Measure** from the context menu.</span></span>  
  
## <a name="options"></a><span data-ttu-id="19311-107">选项</span><span class="sxs-lookup"><span data-stu-id="19311-107">Options</span></span>  
 <span data-ttu-id="19311-108">**使用情况**</span><span class="sxs-lookup"><span data-stu-id="19311-108">**Usage**</span></span>  
 <span data-ttu-id="19311-109">选择新度量值要使用的聚合函数。</span><span class="sxs-lookup"><span data-stu-id="19311-109">Select the aggregation function to be used by the new measure.</span></span>  
  
 <span data-ttu-id="19311-110">**源表**</span><span class="sxs-lookup"><span data-stu-id="19311-110">**Source table**</span></span>  
 <span data-ttu-id="19311-111">选择要从中创建新度量值的表。</span><span class="sxs-lookup"><span data-stu-id="19311-111">Select the table from which the new measure is to be created.</span></span>  
  
 <span data-ttu-id="19311-112">**源列**</span><span class="sxs-lookup"><span data-stu-id="19311-112">**Source column**</span></span>  
 <span data-ttu-id="19311-113">从“源表”\*\*\*\* 中所选择的表中选择新度量值所基于的列。</span><span class="sxs-lookup"><span data-stu-id="19311-113">Select the column in the table selected in **Source table** on which the new measure is to be based.</span></span>  
  
 <span data-ttu-id="19311-114">**显示所有列**</span><span class="sxs-lookup"><span data-stu-id="19311-114">**Show all columns**</span></span>  
 <span data-ttu-id="19311-115">对于创建新度量值所在的度量值组的事实数据表，选择此选项将显示其中的所有列。</span><span class="sxs-lookup"><span data-stu-id="19311-115">Select to display all columns in the fact table for the measure group in which the new measure is to be created.</span></span> <span data-ttu-id="19311-116">如果未选择此项， **“源列”** 将仅显示未用作逻辑主键的数字列或关系所涉及的数字列。</span><span class="sxs-lookup"><span data-stu-id="19311-116">If not selected, **Source column** only displays numeric columns that are not used as logical primary keys or involved in relationships.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="19311-117">另请参阅</span><span class="sxs-lookup"><span data-stu-id="19311-117">See Also</span></span>  
 <span data-ttu-id="19311-118">[多维数据集设计器的多维数据集结构 &#40;&#41; &#40;Analysis Services 多维数据&#41;](cube-structure-cube-designer-analysis-services-multidimensional-data.md) </span><span class="sxs-lookup"><span data-stu-id="19311-118">[Cube Structure &#40;Cube Designer&#41; &#40;Analysis Services - Multidimensional Data&#41;](cube-structure-cube-designer-analysis-services-multidimensional-data.md) </span></span>  
 [<span data-ttu-id="19311-119">&#40;多维数据的 Analysis Services 设计器和对话框&#41;</span><span class="sxs-lookup"><span data-stu-id="19311-119">Analysis Services Designers and Dialog Boxes &#40;Multidimensional Data&#41;</span></span>](analysis-services-designers-and-dialog-boxes-multidimensional-data.md)  
  
  
