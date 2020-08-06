---
title: 删除显式层次结构 (Master Data Services) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
helpviewer_keywords:
- explicit hierarchies, deleting
- deleting explicit hierarchies [Master Data Services]
ms.assetid: 4ce177b0-9884-47a2-9cea-212e845dd762
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 744f96a2705a3abbc2318ecd3c9b0c7fffb7605e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87591932"
---
# <a name="delete-an-explicit-hierarchy-master-data-services"></a><span data-ttu-id="341b0-102">删除显式层次结构 (Master Data Services)</span><span class="sxs-lookup"><span data-stu-id="341b0-102">Delete an Explicit Hierarchy (Master Data Services)</span></span>
  <span data-ttu-id="341b0-103">在 [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]中，当不再需要显式层次结构时可将其删除。</span><span class="sxs-lookup"><span data-stu-id="341b0-103">In [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)], delete an explicit hierarchy when you no longer need it.</span></span>  
  
> [!WARNING]  
>  <span data-ttu-id="341b0-104">当删除显式层次结构时，还将删除该层次结构中的所有合并成员。</span><span class="sxs-lookup"><span data-stu-id="341b0-104">When you delete an explicit hierarchy, all consolidated members in the hierarchy are deleted also.</span></span> <span data-ttu-id="341b0-105">如果您删除某一实体的所有显式层次结构，则还将删除此实体的所有集合，并且不再为显式层次结构和集合启用此实体。</span><span class="sxs-lookup"><span data-stu-id="341b0-105">If you delete all explicit hierarchies for an entity, all collections for the entity are also deleted and the entity is no longer enabled for explicit hierarchies and collections.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="341b0-106">先决条件</span><span class="sxs-lookup"><span data-stu-id="341b0-106">Prerequisites</span></span>  
 <span data-ttu-id="341b0-107">若要执行此过程：</span><span class="sxs-lookup"><span data-stu-id="341b0-107">To perform this procedure:</span></span>  
  
-   <span data-ttu-id="341b0-108">您必须有权访问 **“系统管理”** 功能区域。</span><span class="sxs-lookup"><span data-stu-id="341b0-108">You must have permission to access the **System Administration** functional area.</span></span>  
  
-   <span data-ttu-id="341b0-109">您必须是模型管理员。</span><span class="sxs-lookup"><span data-stu-id="341b0-109">You must be a model administrator.</span></span> <span data-ttu-id="341b0-110">有关详细信息，请参阅[管理员 &#40;Master Data Services&#41;](administrators-master-data-services.md)。</span><span class="sxs-lookup"><span data-stu-id="341b0-110">For more information, see [Administrators &#40;Master Data Services&#41;](administrators-master-data-services.md).</span></span>  
  
### <a name="to-delete-an-explicit-hierarchy"></a><span data-ttu-id="341b0-111">删除显式层次结构</span><span class="sxs-lookup"><span data-stu-id="341b0-111">To delete an explicit hierarchy</span></span>  
  
1.  <span data-ttu-id="341b0-112">在 [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)]中，单击 **“系统管理”**。</span><span class="sxs-lookup"><span data-stu-id="341b0-112">In [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)], click **System Administration**.</span></span>  
  
2.  <span data-ttu-id="341b0-113">在 **“模型视图”** 页上，从菜单栏中，指向 **“管理”** ，然后单击 **“实体”**。</span><span class="sxs-lookup"><span data-stu-id="341b0-113">On the **Model View** page, from the menu bar, point to **Manage** and click **Entities**.</span></span>  
  
3.  <span data-ttu-id="341b0-114">在 **“实体维护”** 页上，从 **“模型”** 列表中，选择某一模型。</span><span class="sxs-lookup"><span data-stu-id="341b0-114">On the **Entity Maintenance** page, from the **Model** list, select a model.</span></span>  
  
4.  <span data-ttu-id="341b0-115">为包含您要删除的显式层次结构的实体选择行。</span><span class="sxs-lookup"><span data-stu-id="341b0-115">Select the row for the entity that contains the explicit hierarchy you want to delete.</span></span>  
  
5.  <span data-ttu-id="341b0-116">单击 **“编辑所选实体”**。</span><span class="sxs-lookup"><span data-stu-id="341b0-116">Click **Edit selected entity**.</span></span>  
  
6.  <span data-ttu-id="341b0-117">在 "**编辑实体**" 页上的 "**显式层次结构**" 窗格中，单击要删除的显式层次结构。</span><span class="sxs-lookup"><span data-stu-id="341b0-117">On the **Edit Entity** page, in the **Explicit Hierarchies** pane, click the explicit hierarchy you want to delete.</span></span>  
  
7.  <span data-ttu-id="341b0-118">单击 "**删除所选层次结构**"。</span><span class="sxs-lookup"><span data-stu-id="341b0-118">Click **Delete selected hierarchy**.</span></span>  
  
8.  <span data-ttu-id="341b0-119">在确认对话框中，单击 **“确定”**。</span><span class="sxs-lookup"><span data-stu-id="341b0-119">In the confirmation dialog box, click **OK**.</span></span>  
  
9. <span data-ttu-id="341b0-120">在附加确认对话框中，单击 **“确定”**。</span><span class="sxs-lookup"><span data-stu-id="341b0-120">In the additional confirmation dialog box, click **OK**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="341b0-121">另请参阅</span><span class="sxs-lookup"><span data-stu-id="341b0-121">See Also</span></span>  
 <span data-ttu-id="341b0-122">[创建显式层次结构 &#40;Master Data Services&#41;](../../2014/master-data-services/create-an-explicit-hierarchy-master-data-services.md) </span><span class="sxs-lookup"><span data-stu-id="341b0-122">[Create an Explicit Hierarchy &#40;Master Data Services&#41;](../../2014/master-data-services/create-an-explicit-hierarchy-master-data-services.md) </span></span>  
 [<span data-ttu-id="341b0-123">显式层次结构 (Master Data Services)</span><span class="sxs-lookup"><span data-stu-id="341b0-123">Explicit Hierarchies &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/explicit-hierarchies-master-data-services.md)  
  
  
