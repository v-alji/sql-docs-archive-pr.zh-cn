---
title: "\"添加多维数据集维度\" 对话框 (Analysis Services 多维数据) |Microsoft Docs"
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.cubeeditor.addcubedimensiondialog.f1
helpviewer_keywords:
- Add Cube Dimension dialog box
ms.assetid: 625a3b1f-183b-445f-9bb7-96945c324767
author: minewiskan
ms.author: owend
ms.openlocfilehash: d0de75c02c39b0690184f35f2b0b6a07d7ed9a4f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87578537"
---
# <a name="add-cube-dimension-dialog-box-analysis-services---multidimensional-data"></a><span data-ttu-id="fa9e4-102">“添加多维数据集维度”对话框（Analysis Services - 多维数据）</span><span class="sxs-lookup"><span data-stu-id="fa9e4-102">Add Cube Dimension Dialog Box (Analysis Services - Multidimensional Data)</span></span>
  <span data-ttu-id="fa9e4-103">可以使用 **中的** “添加多维数据集维度” [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] 对话框，在多维数据集中添加对数据库维度的引用。</span><span class="sxs-lookup"><span data-stu-id="fa9e4-103">Use the **Add Cube Dimension** dialog box in [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] to add a reference to a database dimension to a cube.</span></span> <span data-ttu-id="fa9e4-104">通过执行下列操作之一，可以显示 **“添加多维数据集维度”** 对话框：</span><span class="sxs-lookup"><span data-stu-id="fa9e4-104">You can display the **Add Cube Dimension** dialog box by doing one of the following:</span></span>  
  
-   <span data-ttu-id="fa9e4-105">在多维数据集设计器中的 **“多维数据集结构”** 或 **“维度用法”** 选项卡上，单击 **“工具栏”** 窗格中的 **“添加多维数据集维度”** 。</span><span class="sxs-lookup"><span data-stu-id="fa9e4-105">Click **Add Cube Dimension** in the **Toolbar** pane on the **Cube Structure** or **Dimension Usage** tab in Cube Designer.</span></span>  
  
-   <span data-ttu-id="fa9e4-106">在多维数据集设计器中的“多维数据集结构”选项卡上，右键单击“维度”窗格，再从上下文菜单中选择“添加多维数据集维度”。\*\*\*\*\*\*\*\*\*\*\*\*</span><span class="sxs-lookup"><span data-stu-id="fa9e4-106">Right-click the **Dimensions** pane on the **Cube Structure** tab in Cube Designer and select **Add Cube Dimension** from the context menu.</span></span>  
  
-   <span data-ttu-id="fa9e4-107">在多维数据集设计器中的“维度用法”选项卡上，右键单击“网格”窗格，再从上下文菜单中选择“添加多维数据集维度”。\*\*\*\*\*\*\*\*\*\*\*\*</span><span class="sxs-lookup"><span data-stu-id="fa9e4-107">Right-click the **Grid** pane on the **Dimension Usage** tab in Cube Designer and select **Add Cube Dimension** from the context menu.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="fa9e4-108">每个多维数据集维度与度量值组之间只能有一个关系。</span><span class="sxs-lookup"><span data-stu-id="fa9e4-108">Each cube dimension can have only one relationship to a measure group.</span></span> <span data-ttu-id="fa9e4-109">不过，如果多维数据集维度所基于的数据库维度通过数据源视图中的多个关系与度量值组相关，则可以创建多个多维数据集维度并将其添加到多维数据集。</span><span class="sxs-lookup"><span data-stu-id="fa9e4-109">However, you can create more than one cube dimension and add it to the cube, if the database dimension on which the cube dimension is based is related to measure groups through more than one relationship in the data source view.</span></span> <span data-ttu-id="fa9e4-110">此类维度称为角色共享维度，通常与时间维度一起使用。</span><span class="sxs-lookup"><span data-stu-id="fa9e4-110">Such dimensions are referred to as role-playing dimensions and commonly occur with time dimensions.</span></span>  
  
## <a name="options"></a><span data-ttu-id="fa9e4-111">选项</span><span class="sxs-lookup"><span data-stu-id="fa9e4-111">Options</span></span>  
 <span data-ttu-id="fa9e4-112">**选择维度**</span><span class="sxs-lookup"><span data-stu-id="fa9e4-112">**Select dimension**</span></span>  
 <span data-ttu-id="fa9e4-113">选择现有数据库维度，将基于该数据库维度的多维数据集维度添加到所选多维数据集。</span><span class="sxs-lookup"><span data-stu-id="fa9e4-113">Select an existing database dimension to add a cube dimension based on it to the selected cube.</span></span> <span data-ttu-id="fa9e4-114">基于同一个数据库维度可以定义多个多维数据集维度。</span><span class="sxs-lookup"><span data-stu-id="fa9e4-114">Multiple cube dimensions can be defined from the same database dimension.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="fa9e4-115">如果将基于同一个数据库维度的多个多维数据集维度添加到多维数据集，额外添加的多维数据集维度则称为角色共享维度。</span><span class="sxs-lookup"><span data-stu-id="fa9e4-115">If more than one cube dimension based on the same database dimension is added to a cube, the additional cube dimensions are called role-playing dimensions.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fa9e4-116">另请参阅</span><span class="sxs-lookup"><span data-stu-id="fa9e4-116">See Also</span></span>  
 [<span data-ttu-id="fa9e4-117">&#40;多维数据的 Analysis Services 设计器和对话框&#41;</span><span class="sxs-lookup"><span data-stu-id="fa9e4-117">Analysis Services Designers and Dialog Boxes &#40;Multidimensional Data&#41;</span></span>](analysis-services-designers-and-dialog-boxes-multidimensional-data.md)  
  
  
