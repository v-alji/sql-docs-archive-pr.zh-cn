---
title: 隐藏或删除派生层次结构中的级别 (Master Data Services) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
helpviewer_keywords:
- derived hierarchies, hiding levels
- derived hierarchies, deleting levels
ms.assetid: e00582b9-9415-4b66-b4a7-9f590d83875f
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 039b05633bcd1fdc69d226e565b3dc5211e9734f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87587882"
---
# <a name="hide-or-delete-levels-in-a-derived-hierarchy-master-data-services"></a><span data-ttu-id="d4f0a-102">隐藏或删除派生层次结构中的级别 (Master Data Services)</span><span class="sxs-lookup"><span data-stu-id="d4f0a-102">Hide or Delete Levels in a Derived Hierarchy (Master Data Services)</span></span>
  <span data-ttu-id="d4f0a-103">在 [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]中，当您在派生层次结构中需要级别进行分组，但不需要显示级别时，可以隐藏级别。</span><span class="sxs-lookup"><span data-stu-id="d4f0a-103">In [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)], hide a level in a derived hierarchy when you require the level for grouping but you do not need to show the level.</span></span> <span data-ttu-id="d4f0a-104">当您不希望将级别用于分组时，可以删除它。</span><span class="sxs-lookup"><span data-stu-id="d4f0a-104">Delete a level when you do not want to use it for grouping.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="d4f0a-105">必备条件</span><span class="sxs-lookup"><span data-stu-id="d4f0a-105">Prerequisites</span></span>  
 <span data-ttu-id="d4f0a-106">若要执行此过程：</span><span class="sxs-lookup"><span data-stu-id="d4f0a-106">To perform this procedure:</span></span>  
  
-   <span data-ttu-id="d4f0a-107">您必须有权访问 **“系统管理”** 功能区域。</span><span class="sxs-lookup"><span data-stu-id="d4f0a-107">You must have permission to access the **System Administration** functional area.</span></span>  
  
-   <span data-ttu-id="d4f0a-108">您必须是模型管理员。</span><span class="sxs-lookup"><span data-stu-id="d4f0a-108">You must be a model administrator.</span></span> <span data-ttu-id="d4f0a-109">有关详细信息，请参阅[管理员 &#40;Master Data Services&#41;](administrators-master-data-services.md)。</span><span class="sxs-lookup"><span data-stu-id="d4f0a-109">For more information, see [Administrators &#40;Master Data Services&#41;](administrators-master-data-services.md).</span></span>  
  
### <a name="to-hide-or-delete-levels-in-a-derived-hierarchy"></a><span data-ttu-id="d4f0a-110">隐藏或删除派生层次结构中的级别</span><span class="sxs-lookup"><span data-stu-id="d4f0a-110">To hide or delete levels in a derived hierarchy</span></span>  
  
1.  <span data-ttu-id="d4f0a-111">在 [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)]中，单击 **“系统管理”**。</span><span class="sxs-lookup"><span data-stu-id="d4f0a-111">In [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)], click **System Administration**.</span></span>  
  
2.  <span data-ttu-id="d4f0a-112">在 "**模型视图**" 页上，从菜单栏中指向 "**管理**"，然后单击 "**派生层次结构**"。</span><span class="sxs-lookup"><span data-stu-id="d4f0a-112">On the **Model View** page, from the menu bar, point to **Manage** and click **Derived Hierarchies**.</span></span>  
  
3.  <span data-ttu-id="d4f0a-113">在 **“派生层次结构维护”** 页上，从 **“模型”** 列表中，选择某一模型。</span><span class="sxs-lookup"><span data-stu-id="d4f0a-113">On the **Derived Hierarchy Maintenance** page, from the **Model** list, select a model.</span></span>  
  
4.  <span data-ttu-id="d4f0a-114">为您要编辑的派生层次结构选择行。</span><span class="sxs-lookup"><span data-stu-id="d4f0a-114">Select the row for the derived hierarchy you want to edit.</span></span>  
  
5.  <span data-ttu-id="d4f0a-115">单击 "**编辑所选派生层次结构**"。</span><span class="sxs-lookup"><span data-stu-id="d4f0a-115">Click **Edit selected derived hierarchy**.</span></span>  
  
6.  <span data-ttu-id="d4f0a-116">在 **“当前级别”** 窗格中：</span><span class="sxs-lookup"><span data-stu-id="d4f0a-116">In the **Current Levels** pane:</span></span>  
  
    -   <span data-ttu-id="d4f0a-117">若要隐藏级别，请单击除顶部或底部之外的级别。</span><span class="sxs-lookup"><span data-stu-id="d4f0a-117">To hide a level, click a level other than the top or bottom.</span></span> <span data-ttu-id="d4f0a-118">从 **“可见”** 列表中，选择 **“否”**。</span><span class="sxs-lookup"><span data-stu-id="d4f0a-118">From the **Visible** list, select **No**.</span></span> <span data-ttu-id="d4f0a-119">然后，单击 **“保存所选层次结构项”**。</span><span class="sxs-lookup"><span data-stu-id="d4f0a-119">Then click **Save selected hierarchy item**.</span></span>  
  
    -   <span data-ttu-id="d4f0a-120">若要删除顶部级别，请单击 **“删除所选层次结构项”**。</span><span class="sxs-lookup"><span data-stu-id="d4f0a-120">To delete the top level, click **Delete selected hierarchy item**.</span></span> <span data-ttu-id="d4f0a-121">在确认对话框中，单击 **“确定”**。</span><span class="sxs-lookup"><span data-stu-id="d4f0a-121">In the confirmation dialog box, click **OK**.</span></span> <span data-ttu-id="d4f0a-122">只能删除顶部级别。</span><span class="sxs-lookup"><span data-stu-id="d4f0a-122">You can delete the top level only.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d4f0a-123">另请参阅</span><span class="sxs-lookup"><span data-stu-id="d4f0a-123">See Also</span></span>  
 <span data-ttu-id="d4f0a-124">[在层次结构中移动 &#40;Master Data Services 的成员&#41;](../../2014/master-data-services/move-members-within-a-hierarchy-master-data-services.md) </span><span class="sxs-lookup"><span data-stu-id="d4f0a-124">[Move Members within a Hierarchy &#40;Master Data Services&#41;](../../2014/master-data-services/move-members-within-a-hierarchy-master-data-services.md) </span></span>  
 [<span data-ttu-id="d4f0a-125">派生层次结构 (Master Data Services)</span><span class="sxs-lookup"><span data-stu-id="d4f0a-125">Derived Hierarchies &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/derived-hierarchies-master-data-services.md)  
  
  
