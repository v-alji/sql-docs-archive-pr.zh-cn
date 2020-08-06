---
title: " (SSAS 表格) 中删除关系 |Microsoft Docs"
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: d40e3f05-54e8-4c4b-807a-0b06f446079b
author: minewiskan
ms.author: owend
ms.openlocfilehash: 3c63324918eb6919ce0abd65b5ee0765f9d7243b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87687247"
---
# <a name="delete-relationships-ssas-tabular"></a><span data-ttu-id="4bd55-102">删除关系（SSAS 表格）</span><span class="sxs-lookup"><span data-stu-id="4bd55-102">Delete Relationships (SSAS Tabular)</span></span>
  <span data-ttu-id="4bd55-103">您可以使用模型设计器中的“关系图视图”或使用“管理关系”对话框来删除现有关系。</span><span class="sxs-lookup"><span data-stu-id="4bd55-103">You can delete existing relationships by using the model designer in Diagram View or by using the Manage Relationships dialog box.</span></span> <span data-ttu-id="4bd55-104">有关如何在表格模型中使用关系的详细信息，请参阅 [关系（SSAS 表格）](relationships-ssas-tabular.md)。</span><span class="sxs-lookup"><span data-stu-id="4bd55-104">For information about how relationships are used in tabular models, see [Relationships &#40;SSAS Tabular&#41;](relationships-ssas-tabular.md).</span></span>  
  
## <a name="considerations-for-deleting-relationships"></a><span data-ttu-id="4bd55-105">删除关系时的注意事项</span><span class="sxs-lookup"><span data-stu-id="4bd55-105">Considerations for Deleting Relationships</span></span>  
 <span data-ttu-id="4bd55-106">决定是否删除关系时要注意下列问题：</span><span class="sxs-lookup"><span data-stu-id="4bd55-106">Keep the following issues in mind when deciding whether to delete a relationship:</span></span>  
  
-   <span data-ttu-id="4bd55-107">无法撤消删除关系。</span><span class="sxs-lookup"><span data-stu-id="4bd55-107">There is no way to undo the deletion of a relationship.</span></span> <span data-ttu-id="4bd55-108">您可以重新创建关系，但此操作要求完全重新计算模型中的公式。</span><span class="sxs-lookup"><span data-stu-id="4bd55-108">You can re-create the relationship, but this action requires a complete recalculation of formulas in the model.</span></span> <span data-ttu-id="4bd55-109">因此，在删除在公式中使用的关系前，应始终首先进行检查。</span><span class="sxs-lookup"><span data-stu-id="4bd55-109">Therefore, always check first before deleting a relationship that is used in formulas.</span></span>  
  
-   <span data-ttu-id="4bd55-110">删除两个表之间的关系会导致引用这些表的公式中出现错误。</span><span class="sxs-lookup"><span data-stu-id="4bd55-110">Deleting a relationship between two tables can cause errors in formulas that reference these tables.</span></span>  
  
-   <span data-ttu-id="4bd55-111">数据分析表达式 (DAX) RELATED 函数使用表之间的关系查找其他表中的相关值。</span><span class="sxs-lookup"><span data-stu-id="4bd55-111">The Data Analysis Expression (DAX) RELATED function uses the relationships between tables to look up related values in another table.</span></span> <span data-ttu-id="4bd55-112">关系删除之后，该函数将返回不同的结果。</span><span class="sxs-lookup"><span data-stu-id="4bd55-112">It will return different results after the relationship is deleted.</span></span> <span data-ttu-id="4bd55-113">有关详细信息，请参阅 RELATED 函数 (DAX)。</span><span class="sxs-lookup"><span data-stu-id="4bd55-113">For more information, see the RELATED Function (DAX).</span></span>  
  
-   <span data-ttu-id="4bd55-114">除了更改数据透视表和公式的结果以外，创建和删除关系还将导致重新计算工作簿，这可能需要一些时间。</span><span class="sxs-lookup"><span data-stu-id="4bd55-114">In addition to changing PivotTable and formula results, both the creation and deletion of relationships will cause the workbook to be recalculated, which can take some time.</span></span>  
  
## <a name="delete-relationships"></a><span data-ttu-id="4bd55-115">删除关系</span><span class="sxs-lookup"><span data-stu-id="4bd55-115">Delete Relationships</span></span>  
  
#### <a name="to-delete-a-relationship-by-using-diagram-view"></a><span data-ttu-id="4bd55-116">使用“关系图视图”删除关系</span><span class="sxs-lookup"><span data-stu-id="4bd55-116">To delete a relationship by using Diagram View</span></span>  
  
1.  <span data-ttu-id="4bd55-117">在 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]中，单击 **“模型”** 菜单，然后指向 **“模型视图”**，再单击 **“关系图视图”**。</span><span class="sxs-lookup"><span data-stu-id="4bd55-117">In [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], click the **Model** menu, then point to **Model View**, and then click **Diagram View**.</span></span>  
  
2.  <span data-ttu-id="4bd55-118">右键单击两个表之间的关系线，然后单击“删除”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="4bd55-118">Right-click a relationship line between two tables, and then click **Delete**.</span></span>  
  
#### <a name="to-delete-a-relationship-by-using-the-manage-relationships-dialog-box"></a><span data-ttu-id="4bd55-119">使用“管理关系”对话框删除关系</span><span class="sxs-lookup"><span data-stu-id="4bd55-119">To delete a relationship by using the Manage Relationships dialog box</span></span>  
  
1.  <span data-ttu-id="4bd55-120">在 [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)]中，单击 **“表”** 菜单，然后单击 **“管理关系”**。</span><span class="sxs-lookup"><span data-stu-id="4bd55-120">In [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)], click the **Table** menu, and then click **Manage Relationships**.</span></span>  
  
2.  <span data-ttu-id="4bd55-121">在 **“管理关系”** 对话框中，从列表中选择一个或多个关系。</span><span class="sxs-lookup"><span data-stu-id="4bd55-121">In the **Manage Relationships** dialog box, select one or more relationships from the list.</span></span>  
  
     <span data-ttu-id="4bd55-122">若要选择多个关系，请按住 Ctrl 键，同时单击各个关系。</span><span class="sxs-lookup"><span data-stu-id="4bd55-122">To select multiple relationships, hold down CTRL while you click each relationship.</span></span>  
  
3.  <span data-ttu-id="4bd55-123">单击 **“删除关系”**。</span><span class="sxs-lookup"><span data-stu-id="4bd55-123">Click **Delete Relationship**.</span></span>  
  
4.  <span data-ttu-id="4bd55-124">在 **“管理关系”** 对话框中，单击 **“关闭”**。</span><span class="sxs-lookup"><span data-stu-id="4bd55-124">In the **Manage Relationships** dialog box, click **Close**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4bd55-125">另请参阅</span><span class="sxs-lookup"><span data-stu-id="4bd55-125">See Also</span></span>  
 <span data-ttu-id="4bd55-126">[SSAS 表格&#41;&#40;关系](relationships-ssas-tabular.md) </span><span class="sxs-lookup"><span data-stu-id="4bd55-126">[Relationships &#40;SSAS Tabular&#41;](relationships-ssas-tabular.md) </span></span>  
 [<span data-ttu-id="4bd55-127">创建两个表之间的关系（SSAS 表格）</span><span class="sxs-lookup"><span data-stu-id="4bd55-127">Create a Relationship Between Two Tables &#40;SSAS Tabular&#41;</span></span>](create-a-relationship-between-two-tables-ssas-tabular.md)  
  
  
