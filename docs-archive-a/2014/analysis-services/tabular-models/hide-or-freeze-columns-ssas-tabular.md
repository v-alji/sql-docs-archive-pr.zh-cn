---
title: " (SSAS 表格) 中隐藏或冻结列 |Microsoft Docs"
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.bidtoolset.hideunhidecolumnsdb.f1
ms.assetid: 5407aee5-6a07-4559-a2ba-2ca00a242f02
author: minewiskan
ms.author: owend
ms.openlocfilehash: 71398eecbc342b4e3f9c2445fef3023132266dac
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87687236"
---
# <a name="hide-or-freeze-columns-ssas-tabular"></a><span data-ttu-id="fffb1-102">隐藏或冻结列（SSAS 表格）</span><span class="sxs-lookup"><span data-stu-id="fffb1-102">Hide or Freeze Columns (SSAS Tabular)</span></span>
  <span data-ttu-id="fffb1-103">在模型设计器中，如果不想在表中显示某些列，则可以暂时隐藏它们。</span><span class="sxs-lookup"><span data-stu-id="fffb1-103">In the model designer, if there are columns that you don't want to display in a table, you can temporarily hide them.</span></span> <span data-ttu-id="fffb1-104">隐藏列可为您在屏幕上提供更多空间，以便添加新列或仅使用相关的数据列。</span><span class="sxs-lookup"><span data-stu-id="fffb1-104">Hiding a column gives you more room on the screen to add new columns or to work with only relevant columns of data.</span></span> <span data-ttu-id="fffb1-105">从模型设计器的“列”\*\*\*\* 菜单或者每个列标题的右键单击菜单中，可以隐藏和取消隐藏列。</span><span class="sxs-lookup"><span data-stu-id="fffb1-105">You can hide and unhide columns from the **Column** menu in the model designer, and from the right-click menu available from each column header.</span></span> <span data-ttu-id="fffb1-106">要在滚动到模型的其他区域时使模型的某一区域可见，可以通过冻结该区域的特定列来锁定它们。</span><span class="sxs-lookup"><span data-stu-id="fffb1-106">To keep an area of a model visible while you scroll to another area of the model, you can lock specific columns in one area by freezing them.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="fffb1-107">隐藏列的功能不是为了用于数据安全性，而是为了简化和缩短模型设计器或报表中可见列的列表。</span><span class="sxs-lookup"><span data-stu-id="fffb1-107">The ability to hide columns is not intended to be used for data security, only to simplify and shorten the list of columns visible in the model designer or reports.</span></span> <span data-ttu-id="fffb1-108">要保护数据，您可以定义安全角色。</span><span class="sxs-lookup"><span data-stu-id="fffb1-108">To secure data, you can define security roles.</span></span> <span data-ttu-id="fffb1-109">角色可以将可查看的元数据和数据限制为在角色中定义的那些对象。</span><span class="sxs-lookup"><span data-stu-id="fffb1-109">Roles can limit viewable metadata and data to only those objects defined in the role.</span></span> <span data-ttu-id="fffb1-110">有关详细信息，请参阅 [角色（SSAS 表格）](roles-ssas-tabular.md)中创建的表格模型项目。</span><span class="sxs-lookup"><span data-stu-id="fffb1-110">For more information, see [Roles &#40;SSAS Tabular&#41;](roles-ssas-tabular.md).</span></span>  
  
 <span data-ttu-id="fffb1-111">在隐藏某一列时，你可以选择在模型设计器或报表中工作时隐藏该列。</span><span class="sxs-lookup"><span data-stu-id="fffb1-111">When you hide a column, you have the option to hide the column while you are working in the model designer or in reports.</span></span> <span data-ttu-id="fffb1-112">如果隐藏所有列，则整个表在模型设计器中显示为空白。</span><span class="sxs-lookup"><span data-stu-id="fffb1-112">If you hide all columns, the entire table appears blank in the model designer.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="fffb1-113">如果您要隐藏的列很多，可以创建一个透视来替代隐藏列和取消隐藏列。</span><span class="sxs-lookup"><span data-stu-id="fffb1-113">If you have many columns to hide, you can create a perspective instead of hiding and unhiding columns.</span></span> <span data-ttu-id="fffb1-114">透视是自定义的数据视图，它更便于使用相关数据的子集。</span><span class="sxs-lookup"><span data-stu-id="fffb1-114">A perspective is a custom view of the data that makes it easier to work with subset of related data.</span></span> <span data-ttu-id="fffb1-115">有关详细信息，请参阅[创建和管理透视表（SSAS 表格）](perspectives-ssas-tabular.md)。</span><span class="sxs-lookup"><span data-stu-id="fffb1-115">For more information, see [Create and Manage Perspectives &#40;SSAS Tabular&#41;](perspectives-ssas-tabular.md)</span></span>  
  
### <a name="to-hide-an-individual-column"></a><span data-ttu-id="fffb1-116">隐藏单个列</span><span class="sxs-lookup"><span data-stu-id="fffb1-116">To hide an individual column</span></span>  
  
1.  <span data-ttu-id="fffb1-117">在模型设计器中，选择包含要隐藏的列的表。</span><span class="sxs-lookup"><span data-stu-id="fffb1-117">In the model designer, select the table that contains the column that you want to hide.</span></span>  
  
2.  <span data-ttu-id="fffb1-118">右键单击该列，单击“隐藏列”，然后单击“从设计器和报表”、“从报表”或“从设计器”。\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*</span><span class="sxs-lookup"><span data-stu-id="fffb1-118">Right-click the column, then click **Hide Columns**, and then click **From Designer and Reports**, **From Reports**, or **From Designer**.</span></span>  
  
### <a name="to-hide-multiple-columns"></a><span data-ttu-id="fffb1-119">隐藏多个列</span><span class="sxs-lookup"><span data-stu-id="fffb1-119">To hide multiple columns</span></span>  
  
1.  <span data-ttu-id="fffb1-120">在模型设计器中，选择包含要隐藏的列的表。</span><span class="sxs-lookup"><span data-stu-id="fffb1-120">In the model designer, select the table that contains the columns that you want to hide.</span></span>  
  
2.  <span data-ttu-id="fffb1-121">单击 **“列”** 菜单，然后单击 **“隐藏和取消隐藏”**。</span><span class="sxs-lookup"><span data-stu-id="fffb1-121">Click on the **Columns** menu, and then click **Hide and Unhide**.</span></span>  
  
3.  <span data-ttu-id="fffb1-122">在 **“隐藏和取消隐藏列”** 对话框中，找到要隐藏的每个列，然后取消选中 **“在设计器中”** 和/或 **“在报表中”**。</span><span class="sxs-lookup"><span data-stu-id="fffb1-122">In the **Hide and Unhide Columns** dialog box, locate each column that you want to hide, and then deselect one or both of **In Designer** and **In Reports**.</span></span>  
  
4.  <span data-ttu-id="fffb1-123">单击“确定”  。</span><span class="sxs-lookup"><span data-stu-id="fffb1-123">Click **OK**.</span></span>  
  
### <a name="to-freeze-columns"></a><span data-ttu-id="fffb1-124">冻结列</span><span class="sxs-lookup"><span data-stu-id="fffb1-124">To freeze columns</span></span>  
  
1.  <span data-ttu-id="fffb1-125">在模型设计器中，选择包含要冻结的列的表。</span><span class="sxs-lookup"><span data-stu-id="fffb1-125">In the model designer, select the table that contains the columns that you want to freeze.</span></span>  
  
2.  <span data-ttu-id="fffb1-126">选择一个或多个要冻结的列。</span><span class="sxs-lookup"><span data-stu-id="fffb1-126">Select one or more columns to freeze.</span></span>  
  
3.  <span data-ttu-id="fffb1-127">单击 **“列”** 菜单，然后单击 **“冻结”**。</span><span class="sxs-lookup"><span data-stu-id="fffb1-127">Click on the **Columns** menu, and then click **Freeze**..</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="fffb1-128">冻结列时，将它移到设计器中表的左侧（或前面）。</span><span class="sxs-lookup"><span data-stu-id="fffb1-128">When a column(s) is frozen, it is moved to left (or front) of the table in the designer.</span></span> <span data-ttu-id="fffb1-129">解冻该列并不将它移回原始位置。</span><span class="sxs-lookup"><span data-stu-id="fffb1-129">Unfreezing the column does not move it back to its original location.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fffb1-130">另请参阅</span><span class="sxs-lookup"><span data-stu-id="fffb1-130">See Also</span></span>  
 <span data-ttu-id="fffb1-131">[&#40;SSAS 表格&#41;的表和列](tables-and-columns-ssas-tabular.md) </span><span class="sxs-lookup"><span data-stu-id="fffb1-131">[Tables and Columns &#40;SSAS Tabular&#41;](tables-and-columns-ssas-tabular.md) </span></span>  
 <span data-ttu-id="fffb1-132">[SSAS 表格&#41;&#40;透视](perspectives-ssas-tabular.md) </span><span class="sxs-lookup"><span data-stu-id="fffb1-132">[Perspectives &#40;SSAS Tabular&#41;](perspectives-ssas-tabular.md) </span></span>  
 [<span data-ttu-id="fffb1-133">角色（SSAS 表格）</span><span class="sxs-lookup"><span data-stu-id="fffb1-133">Roles &#40;SSAS Tabular&#41;</span></span>](roles-ssas-tabular.md)  
  
  
