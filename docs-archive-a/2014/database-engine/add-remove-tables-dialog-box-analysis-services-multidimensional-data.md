---
title: "\"添加/删除表\" 对话框 (Analysis Services 多维数据) |Microsoft Docs"
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.dsvdesigner.addremoveobjects.f1
helpviewer_keywords:
- Add/Remove Tables dialog box
ms.assetid: b2760517-b0cb-4268-905d-bb1e1f9d902a
author: minewiskan
ms.author: owend
ms.openlocfilehash: 3bf1606ab7a0d43cbc0fa08bd921808792b6c85f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87689031"
---
# <a name="add-remove-tables-dialog-box-analysis-services---multidimensional-data"></a><span data-ttu-id="f2eec-102">"添加/删除表" 对话框 (Analysis Services 多维数据) </span><span class="sxs-lookup"><span data-stu-id="f2eec-102">Add-Remove Tables Dialog Box (Analysis Services - Multidimensional Data)</span></span>
  <span data-ttu-id="f2eec-103">可以使用 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] 中的“添加/删除表”\*\*\*\* 对话框，在数据源视图中添加或删除数据源中的表。</span><span class="sxs-lookup"><span data-stu-id="f2eec-103">Use the **Add/Remove Tables** dialog box in [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] to add or remove tables in a data source to or from a data source view.</span></span> <span data-ttu-id="f2eec-104">可以通过执行以下操作之一显示“添加/删除表”\*\*\*\* 对话框：</span><span class="sxs-lookup"><span data-stu-id="f2eec-104">You can display the **Add/Remove Tables** dialog box by:</span></span>  
  
-   <span data-ttu-id="f2eec-105">在“数据源视图设计器”\*\*\*\* 的“工具栏”\*\*\*\* 窗格中，单击“添加/删除对象”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="f2eec-105">Clicking **Add/Remove Objects** in the **Toolbar** pane of **Data Source View Designer**.</span></span>  
  
-   <span data-ttu-id="f2eec-106">右键单击“数据源视图设计器”\*\*\*\* 的“关系图”\*\*\*\* 窗格，再选择“添加/删除表”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="f2eec-106">Right-clicking the **Diagram** pane of **Data Source View Designer** and selecting **Add/Remove Tables**.</span></span>  
  
## <a name="options"></a><span data-ttu-id="f2eec-107">选项</span><span class="sxs-lookup"><span data-stu-id="f2eec-107">Options</span></span>  
 <span data-ttu-id="f2eec-108">**数据源**</span><span class="sxs-lookup"><span data-stu-id="f2eec-108">**Data source**</span></span>  
 <span data-ttu-id="f2eec-109">Select the data source to add or remove tables.</span><span class="sxs-lookup"><span data-stu-id="f2eec-109">Select the data source to add or remove tables.</span></span>  
  
 <span data-ttu-id="f2eec-110">**Available objects**</span><span class="sxs-lookup"><span data-stu-id="f2eec-110">**Available objects**</span></span>  
 <span data-ttu-id="f2eec-111">Displays the objects and their types in the data source that are not already included in the data source view.</span><span class="sxs-lookup"><span data-stu-id="f2eec-111">Displays the objects and their types in the data source that are not already included in the data source view.</span></span>  
  
 <span data-ttu-id="f2eec-112">单击 **>>** 以将 "**可用对象**" 中列出的所有对象传输到 "**包含的对象**"，或选择一个或多个对象，然后单击 **>** "将所选对象传输到**包含的对象**"。</span><span class="sxs-lookup"><span data-stu-id="f2eec-112">Click **>>** to transfer all objects listed in **Available objects** to **Included objects**, or select one or more objects and click **>** to transfer the selected objects to **Included objects**.</span></span>  
  
 <span data-ttu-id="f2eec-113">**Filter**</span><span class="sxs-lookup"><span data-stu-id="f2eec-113">**Filter**</span></span>  
 <span data-ttu-id="f2eec-114">键入用于限制“可用对象”\*\*\*\* 中所列对象的筛选器，然后单击此按钮筛选列出的对象。</span><span class="sxs-lookup"><span data-stu-id="f2eec-114">Type the filter used to restrict the objects listed in **Available objects**, and then click the button to filter the listed objects.</span></span>  
  
 <span data-ttu-id="f2eec-115">**Show system objects**</span><span class="sxs-lookup"><span data-stu-id="f2eec-115">**Show system objects**</span></span>  
 <span data-ttu-id="f2eec-116">选择此项将在“可用对象”\*\*\*\* 中显示数据源的系统对象。</span><span class="sxs-lookup"><span data-stu-id="f2eec-116">Select to display system objects for the data source in **Available objects**.</span></span>  
  
 <span data-ttu-id="f2eec-117">**Included objects**</span><span class="sxs-lookup"><span data-stu-id="f2eec-117">**Included objects**</span></span>  
 <span data-ttu-id="f2eec-118">Displays the objects and their types that have already been added to the data source view.</span><span class="sxs-lookup"><span data-stu-id="f2eec-118">Displays the objects and their types that have already been added to the data source view.</span></span>  
  
 <span data-ttu-id="f2eec-119">单击 **<<** 以将 "**包含的对象**" 中列出的所有对象传输到 "**可用对象**"，或选择一个或多个对象，然后单击 **<** 将所选对象传输到**可用对象**。</span><span class="sxs-lookup"><span data-stu-id="f2eec-119">Click **<<** to transfer all objects listed in **Included objects** to **Available objects**, or select one or more objects and click **<** to transfer the selected objects to **Available objects**.</span></span>  
  
 <span data-ttu-id="f2eec-120">**Add related tables**</span><span class="sxs-lookup"><span data-stu-id="f2eec-120">**Add related tables**</span></span>  
 <span data-ttu-id="f2eec-121">单击此项将添加所有与“包含的对象”\*\*\*\* 中所选表相关的表。</span><span class="sxs-lookup"><span data-stu-id="f2eec-121">Click to add all tables that are related to the selected tables in **Included objects**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f2eec-122">另请参阅</span><span class="sxs-lookup"><span data-stu-id="f2eec-122">See Also</span></span>  
 <span data-ttu-id="f2eec-123">[&#40;多维数据的 Analysis Services 设计器和对话框&#41;](../analysis-services/analysis-services-designers-and-dialog-boxes-multidimensional-data.md) </span><span class="sxs-lookup"><span data-stu-id="f2eec-123">[Analysis Services Designers and Dialog Boxes &#40;Multidimensional Data&#41;](../analysis-services/analysis-services-designers-and-dialog-boxes-multidimensional-data.md) </span></span>  
 [<span data-ttu-id="f2eec-124">数据源视图设计器（Analysis Services - 多维数据）</span><span class="sxs-lookup"><span data-stu-id="f2eec-124">Data Source View Designer &#40;Analysis Services - Multidimensional Data&#41;</span></span>](../analysis-services/data-source-view-designer-analysis-services-multidimensional-data.md)  
  
  
