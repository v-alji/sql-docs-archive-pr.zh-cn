---
title: 在层次结构中移动成员 (Master Data Services) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
helpviewer_keywords:
- hierarchies [Master Data Services], moving members
- explicit hierarchies, moving members
- derived hierarchies, moving members
- members [Master Data Services], moving
ms.assetid: 049c9a15-89c1-478c-8438-028fffc9e187
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 37167f76b965197dbf8e37e365778395ec640d38
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87580783"
---
# <a name="move-members-within-a-hierarchy-master-data-services"></a><span data-ttu-id="aeccf-102">在层次结构中移动成员 (Master Data Services)</span><span class="sxs-lookup"><span data-stu-id="aeccf-102">Move Members within a Hierarchy (Master Data Services)</span></span>
  <span data-ttu-id="aeccf-103">在[!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)]中，在层次结构中移动成员可以更改其位置或父分配。</span><span class="sxs-lookup"><span data-stu-id="aeccf-103">In [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)], move members within a hierarchy to change their location or parent assignment.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="aeccf-104">先决条件</span><span class="sxs-lookup"><span data-stu-id="aeccf-104">Prerequisites</span></span>  
 <span data-ttu-id="aeccf-105">若要执行此过程：</span><span class="sxs-lookup"><span data-stu-id="aeccf-105">To perform this procedure:</span></span>  
  
-   <span data-ttu-id="aeccf-106">\*\*\*\* 您必须有权访问“资源管理器”功能区域。</span><span class="sxs-lookup"><span data-stu-id="aeccf-106">You must have permission to access the **Explorer** functional area.</span></span>  
  
-   <span data-ttu-id="aeccf-107">对于显式层次结构，你必须对该实体至少具有 "**更新**" 权限。</span><span class="sxs-lookup"><span data-stu-id="aeccf-107">For explicit hierarchies, you must have a minimum of **Update** permission to the entity.</span></span>  
  
-   <span data-ttu-id="aeccf-108">对于派生层次结构，您必须对模型以及在层次结构中使用的任何基于域的属性进行最低**更新**。</span><span class="sxs-lookup"><span data-stu-id="aeccf-108">For derived hierarchies, you must have a minimum of **Update** to the model and to any domain-based attributes used in the hierarchy.</span></span>  
  
### <a name="to-move-members-within-a-hierarchy"></a><span data-ttu-id="aeccf-109">在层次结构中移动成员</span><span class="sxs-lookup"><span data-stu-id="aeccf-109">To move members within a hierarchy</span></span>  
  
1.  <span data-ttu-id="aeccf-110">[!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] 在 \*\*\*\* 主页上，从“模型”列表中，选择模型。</span><span class="sxs-lookup"><span data-stu-id="aeccf-110">On the [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] home page, from the **Model** list, select a model.</span></span>  
  
2.  <span data-ttu-id="aeccf-111">\*\*\*\* 从“版本”列表中，选择某一版本。</span><span class="sxs-lookup"><span data-stu-id="aeccf-111">From the **Version** list, select a version.</span></span>  
  
3.  <span data-ttu-id="aeccf-112">单击 **“资源管理器”**。</span><span class="sxs-lookup"><span data-stu-id="aeccf-112">Click **Explorer**.</span></span>  
  
4.  <span data-ttu-id="aeccf-113">从菜单栏中，指向 "**层次结构**"，然后单击 " *hierarchy_name*"。</span><span class="sxs-lookup"><span data-stu-id="aeccf-113">From the menu bar, point to **Hierarchies** and click *hierarchy_name*.</span></span>  
  
5.  <span data-ttu-id="aeccf-114">在层次**结构窗格中**，层次结构显示为树结构，单击要移动的每个成员所对应的复选框。</span><span class="sxs-lookup"><span data-stu-id="aeccf-114">In the **Hierarchy** pane, where the hierarchy is displayed in a tree structure, click the check box for each member you want to move.</span></span>  
  
6.  <span data-ttu-id="aeccf-115">在**层次结构**窗格的顶部，单击 "**剪切**"。</span><span class="sxs-lookup"><span data-stu-id="aeccf-115">At the top of the **Hierarchy** pane, click **Cut**.</span></span>  
  
7.  <span data-ttu-id="aeccf-116">在 "**层次结构**" 窗格中，单击要将成员移动到的成员的复选框。</span><span class="sxs-lookup"><span data-stu-id="aeccf-116">In the **Hierarchy** pane, click the check box for the member you want to move the members to.</span></span>  
  
8.  <span data-ttu-id="aeccf-117">单击 "**粘贴**"。</span><span class="sxs-lookup"><span data-stu-id="aeccf-117">Click **Paste**.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="aeccf-118">在派生层次结构中，您只能将成员移到同一个级别。</span><span class="sxs-lookup"><span data-stu-id="aeccf-118">In derived hierarchies, you can move members to the same level only.</span></span> <span data-ttu-id="aeccf-119">此外，不能更改成员的排序顺序。</span><span class="sxs-lookup"><span data-stu-id="aeccf-119">Also, you cannot change the sort order of members.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="aeccf-120">另请参阅</span><span class="sxs-lookup"><span data-stu-id="aeccf-120">See Also</span></span>  
 <span data-ttu-id="aeccf-121">[使用 &#40;Master Data Services 的临时过程移动显式层次结构成员&#41;](add-update-and-delete-data-master-data-services.md) </span><span class="sxs-lookup"><span data-stu-id="aeccf-121">[Move Explicit Hierarchy Members by Using the Staging Process &#40;Master Data Services&#41;](add-update-and-delete-data-master-data-services.md) </span></span>  
 <span data-ttu-id="aeccf-122">[派生层次结构 &#40;Master Data Services&#41;](../../2014/master-data-services/derived-hierarchies-master-data-services.md) </span><span class="sxs-lookup"><span data-stu-id="aeccf-122">[Derived Hierarchies &#40;Master Data Services&#41;](../../2014/master-data-services/derived-hierarchies-master-data-services.md) </span></span>  
 [<span data-ttu-id="aeccf-123">显式层次结构 (Master Data Services)</span><span class="sxs-lookup"><span data-stu-id="aeccf-123">Explicit Hierarchies &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/explicit-hierarchies-master-data-services.md)  
  
  
