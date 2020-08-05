---
title: " (SSAS 表格) 创建和管理层次结构 |Microsoft Docs"
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 8dd30cd0-a831-4d25-b577-648d7f3c7fa6
author: minewiskan
ms.author: owend
ms.openlocfilehash: 0bab3e09aadb4e0c857b9c1da3111e03e90f777e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87580406"
---
# <a name="create-and-manage-hierarchies-ssas-tabular"></a><span data-ttu-id="977b2-102">创建和管理层次结构（SSAS 表格）</span><span class="sxs-lookup"><span data-stu-id="977b2-102">Create and Manage Hierarchies (SSAS Tabular)</span></span>
  <span data-ttu-id="977b2-103">可以在模型设计器的关系图视图中创建和管理层次结构。</span><span class="sxs-lookup"><span data-stu-id="977b2-103">Hierarchies can be created and managed in the model designer, in Diagram View.</span></span> <span data-ttu-id="977b2-104">若要在关系图视图中查看模型设计器，请在 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]中单击 **“模型”** 菜单，然后指向 **“模型视图”**，再单击 **“关系图视图”**。</span><span class="sxs-lookup"><span data-stu-id="977b2-104">To view the model designer in Diagram View, in [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], click the **Model** menu, then point to **Model View**, and then click **Diagram View**.</span></span>  
  
 <span data-ttu-id="977b2-105">本主题包括以下任务：</span><span class="sxs-lookup"><span data-stu-id="977b2-105">This topic includes the following tasks:</span></span>  
  
-   [<span data-ttu-id="977b2-106">创建层次结构</span><span class="sxs-lookup"><span data-stu-id="977b2-106">Create a Hierarchy</span></span>](#bkmk_create)  
  
-   [<span data-ttu-id="977b2-107">编辑层次结构</span><span class="sxs-lookup"><span data-stu-id="977b2-107">Edit a Hierarchy</span></span>](#bkmk_edit)  
  
-   [<span data-ttu-id="977b2-108">删除层次结构</span><span class="sxs-lookup"><span data-stu-id="977b2-108">Delete a Hierarchy</span></span>](#bkmk_delete)  
  
##  <a name="create-a-hierarchy"></a><a name="bkmk_create"></a> <span data-ttu-id="977b2-109">创建层次结构</span><span class="sxs-lookup"><span data-stu-id="977b2-109">Create a Hierarchy</span></span>  
 <span data-ttu-id="977b2-110">您可以通过使用列和表上下文菜单，创建层次结构。</span><span class="sxs-lookup"><span data-stu-id="977b2-110">You can create a hierarchy by using the columns and table context menu.</span></span> <span data-ttu-id="977b2-111">创建层次结构时，一个新的父级别将与您作为子级别选择的列一起出现。</span><span class="sxs-lookup"><span data-stu-id="977b2-111">When you create a hierarchy, a new parent level displays with selected columns as child levels.</span></span>  
  
#### <a name="to-create-a-hierarchy-from-the-context-menu"></a><span data-ttu-id="977b2-112">从上下文菜单创建层次结构</span><span class="sxs-lookup"><span data-stu-id="977b2-112">To create a hierarchy from the context menu</span></span>  
  
1.  <span data-ttu-id="977b2-113">在模型设计器（关系图视图）的表窗口中，右键单击某一列，然后单击“创建层次结构”。\*\*\*\*</span><span class="sxs-lookup"><span data-stu-id="977b2-113">In the model designer (Diagram View), in a table window, right-click on a column, and then click **Create Hierarchy**.</span></span>  
  
     <span data-ttu-id="977b2-114">若要选择多列，请单击每一列，右键单击以便打开上下文菜单，然后单击“创建层次结构”。\*\*\*\*</span><span class="sxs-lookup"><span data-stu-id="977b2-114">To select multiple columns, click each column, then right-click to open the context menu, and then click **Create Hierarchy**.</span></span>  
  
     <span data-ttu-id="977b2-115">一个父层次结构级别将在表窗口的底部创建，并且所选列将作为子级别复制到该层次结构的下方。</span><span class="sxs-lookup"><span data-stu-id="977b2-115">A parent hierarchy level is created at the bottom of the table window and the selected columns are copied under the hierarchy as child levels.</span></span>  
  
2.  <span data-ttu-id="977b2-116">键入层次结构的名称。</span><span class="sxs-lookup"><span data-stu-id="977b2-116">Type a name for the hierarchy.</span></span>  
  
 <span data-ttu-id="977b2-117">您可以将其他列拖到层次结构的父级别中，这将复制这些列。</span><span class="sxs-lookup"><span data-stu-id="977b2-117">You can drag additional columns into your hierarchy's parent level, which copies the columns.</span></span> <span data-ttu-id="977b2-118">将子级别放到层次结构中您希望其出现的位置。</span><span class="sxs-lookup"><span data-stu-id="977b2-118">Drop the child level to place it where you want it to appear in the hierarchy.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="977b2-119">如果您多选度量值以及一个或多个列，或者如果您从多个表中选择列，则在上下文菜单中将禁用“创建层次结构”命令。</span><span class="sxs-lookup"><span data-stu-id="977b2-119">The Create Hierarchy command is disabled in the context menu if you multi-select a measure along with one or more columns or you select columns from multiple tables.</span></span>  
  
##  <a name="edit-a-hierarchy"></a><a name="bkmk_edit"></a><span data-ttu-id="977b2-120">编辑层次结构</span><span class="sxs-lookup"><span data-stu-id="977b2-120">Edit a Hierarchy</span></span>  
 <span data-ttu-id="977b2-121">您可以重命名层次结构，重命名子级别，更改子级别的顺序，添加附加列作为子级别，从层次结构中删除子级别，显示子级别的源名称（列名），以及在子级别与层次结构父级别同名的情况下隐藏子级别。</span><span class="sxs-lookup"><span data-stu-id="977b2-121">You can rename a hierarchy, rename a child level, change the order of the child levels, add additional columns as child levels, remove a child level from a hierarchy, show the source name of a child level (the column name), and hide a child level if it has the same name as the hierarchy parent level.</span></span>  
  
#### <a name="to-change-the-name-of-a-hierarchy-or-child-level"></a><span data-ttu-id="977b2-122">更改层次结构或子级别的名称</span><span class="sxs-lookup"><span data-stu-id="977b2-122">To change the name of a hierarchy or child level</span></span>  
  
1.  <span data-ttu-id="977b2-123">右键单击层次结构父级别或子级别，然后单击“重命名”。\*\*\*\*</span><span class="sxs-lookup"><span data-stu-id="977b2-123">Right-click the hierarchy parent level or a child level, and the click **Rename**.</span></span>  
  
2.  <span data-ttu-id="977b2-124">键入新名称或者编辑现有名称。</span><span class="sxs-lookup"><span data-stu-id="977b2-124">Type a new name or edit the existing name.</span></span>  
  
#### <a name="to-change-the-order-of-a-child-level-in-a-hierarchy"></a><span data-ttu-id="977b2-125">更改层次结构中子级别的顺序</span><span class="sxs-lookup"><span data-stu-id="977b2-125">To change the order of a child level in a hierarchy</span></span>  
  
-   <span data-ttu-id="977b2-126">单击并将子级别拖入到层次结构上的新位置中。</span><span class="sxs-lookup"><span data-stu-id="977b2-126">Click and drag a child level into a new position in the hierarchy.</span></span>  
  
-   <span data-ttu-id="977b2-127">或者，右键单击层次结构的某一子级别，然后单击“上移”以便在列表中上移该级别，或单击“下移”以便在列表中下移该级别。</span><span class="sxs-lookup"><span data-stu-id="977b2-127">Or, right-click a child level of the hierarchy, and then click Move Up to move the level up in the list, or click Move Down to move the level down in the list.</span></span>  
  
-   <span data-ttu-id="977b2-128">或者，右键单击某一子级别以便选择它，然后按下 Alt + 向上箭头以便上移该级别，或按下 Alt + 向上箭头以便在列表中下移该级别。</span><span class="sxs-lookup"><span data-stu-id="977b2-128">Or, click a child level to select it, and then press Alt + Up Arrow to move the level up, or press Alt+Down Arrow to move the level down in the list.</span></span>  
  
#### <a name="to-add-another-child-level-to-a-hierarchy"></a><span data-ttu-id="977b2-129">向层次结构添加其他子级别</span><span class="sxs-lookup"><span data-stu-id="977b2-129">To add another child level to a hierarchy</span></span>  
  
-   <span data-ttu-id="977b2-130">单击并将列拖到父级别或者层次结构的特定位置。</span><span class="sxs-lookup"><span data-stu-id="977b2-130">Click and drag a column onto the parent level or into a specific location of the hierarchy.</span></span> <span data-ttu-id="977b2-131">该列将作为层次结构中的子级别复制。</span><span class="sxs-lookup"><span data-stu-id="977b2-131">The column is copied as a child level of the hierarchy.</span></span>  
  
-   <span data-ttu-id="977b2-132">或者，右键单击某一列，指向“添加到层次结构”，然后单击该层次结构。\*\*\*\*</span><span class="sxs-lookup"><span data-stu-id="977b2-132">Or, right-click a column, point to **Add to Hierarchy**, and then click the hierarchy.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="977b2-133">您可以将隐藏的列（从报表中隐藏的列）作为子级别添加到层次结构。</span><span class="sxs-lookup"><span data-stu-id="977b2-133">You can add a hidden column (a column that is hidden from reports) as a child level to the hierarchy.</span></span> <span data-ttu-id="977b2-134">该子级别并不隐藏。</span><span class="sxs-lookup"><span data-stu-id="977b2-134">The child level is not hidden.</span></span>  
  
#### <a name="to-remove-a-child-level-from-a-hierarchy"></a><span data-ttu-id="977b2-135">从层次结构中删除子级别</span><span class="sxs-lookup"><span data-stu-id="977b2-135">To remove a child level from a hierarchy</span></span>  
  
-   <span data-ttu-id="977b2-136">右键单击子级别，然后单击“从层次结构中删除”。\*\*\*\*</span><span class="sxs-lookup"><span data-stu-id="977b2-136">Right-click a child level, and then click **Remove from Hierarchy**.</span></span>  
  
-   <span data-ttu-id="977b2-137">或者，单击某一子级别，然后按下 **Delete**键。</span><span class="sxs-lookup"><span data-stu-id="977b2-137">Or, click a child level, and then press **Delete**.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="977b2-138">如果您重命名某一层次结构子级别，则该子级别将不再与从其复制的列共享相同名称。</span><span class="sxs-lookup"><span data-stu-id="977b2-138">If you rename a hierarchy child level, it no longer shares the same name as the column that it is copied from.</span></span> <span data-ttu-id="977b2-139">使用 **“显示源名称”** 命令可以看到子级别从其复制的列。</span><span class="sxs-lookup"><span data-stu-id="977b2-139">Use the **Show Source Name** command to see which column it was copied from.</span></span>  
  
#### <a name="to-show-a-source-name"></a><span data-ttu-id="977b2-140">显示源名称</span><span class="sxs-lookup"><span data-stu-id="977b2-140">To show a source name</span></span>  
  
-   <span data-ttu-id="977b2-141">右键单击某一层次结构子级别，然后单击“显示源名称”。\*\*\*\*</span><span class="sxs-lookup"><span data-stu-id="977b2-141">Right-click a hierarchy child level, and then click **Show Source Name**.</span></span> <span data-ttu-id="977b2-142">此时将显示该子级别从其复制的列的名称。</span><span class="sxs-lookup"><span data-stu-id="977b2-142">The name of the column that it was copied from appears.</span></span>  
  
##  <a name="delete-a-hierarchy"></a><a name="bkmk_delete"></a> <span data-ttu-id="977b2-143">删除层次结构</span><span class="sxs-lookup"><span data-stu-id="977b2-143">Delete a Hierarchy</span></span>  
  
#### <a name="to-delete-a-hierarchy-and-remove-its-child-levels"></a><span data-ttu-id="977b2-144">删除层次结构及其子级别</span><span class="sxs-lookup"><span data-stu-id="977b2-144">To delete a hierarchy and remove its child levels</span></span>  
  
-   <span data-ttu-id="977b2-145">右键单击父层次结构级别，然后单击“删除层次结构”。</span><span class="sxs-lookup"><span data-stu-id="977b2-145">Right-click the parent hierarchy level, and then click Delete Hierarchy.</span></span>  
  
-   <span data-ttu-id="977b2-146">或者，单击父层次结构级别，然后按 Delete 键。</span><span class="sxs-lookup"><span data-stu-id="977b2-146">Or, click the parent hierarchy level, and then press Delete.</span></span> <span data-ttu-id="977b2-147">这也会删除其所有子级别。</span><span class="sxs-lookup"><span data-stu-id="977b2-147">This also removes all the child levels.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="977b2-148">另请参阅</span><span class="sxs-lookup"><span data-stu-id="977b2-148">See Also</span></span>  
 <span data-ttu-id="977b2-149">[&#40;SSAS 表格&#41;的表格模型设计器](../tabular-model-designer-ssas-tabular.md) </span><span class="sxs-lookup"><span data-stu-id="977b2-149">[Tabular Model Designer &#40;SSAS Tabular&#41;](../tabular-model-designer-ssas-tabular.md) </span></span>  
 <span data-ttu-id="977b2-150">[SSAS 表格&#41;&#40;层次结构](hierarchies-ssas-tabular.md) </span><span class="sxs-lookup"><span data-stu-id="977b2-150">[Hierarchies &#40;SSAS Tabular&#41;](hierarchies-ssas-tabular.md) </span></span>  
 [<span data-ttu-id="977b2-151">度量值（SSAS 表格）</span><span class="sxs-lookup"><span data-stu-id="977b2-151">Measures &#40;SSAS Tabular&#41;</span></span>](measures-ssas-tabular.md)  
  
  
