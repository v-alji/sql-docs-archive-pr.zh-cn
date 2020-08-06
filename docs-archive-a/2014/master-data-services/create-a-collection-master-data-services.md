---
title: 创建集合 (Master Data Services) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
helpviewer_keywords:
- creating collections [Master Data Services]
- collections [Master Data Services], creating
ms.assetid: 3d4f152c-863c-4385-bca9-a9fcd0402e1f
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: f76171b4fd9b07f751d4f919011a443253fbe31b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87690683"
---
# <a name="create-a-collection-master-data-services"></a><span data-ttu-id="0c6d4-102">创建集合 (Master Data Services)</span><span class="sxs-lookup"><span data-stu-id="0c6d4-102">Create a Collection (Master Data Services)</span></span>
  <span data-ttu-id="0c6d4-103">在 [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]中，当您想要创建叶成员和合并成员的平面列表时，可以创建集合。</span><span class="sxs-lookup"><span data-stu-id="0c6d4-103">In [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)], create a collection when you want to create flat lists of leaf and consolidated members.</span></span> <span data-ttu-id="0c6d4-104">集合无需包括来自实体的所有成员。</span><span class="sxs-lookup"><span data-stu-id="0c6d4-104">Collections do not need to include all members from the entity.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="0c6d4-105">先决条件</span><span class="sxs-lookup"><span data-stu-id="0c6d4-105">Prerequisites</span></span>  
 <span data-ttu-id="0c6d4-106">若要执行此过程：</span><span class="sxs-lookup"><span data-stu-id="0c6d4-106">To perform this procedure:</span></span>  
  
-   <span data-ttu-id="0c6d4-107">\*\*\*\* 您必须有权访问“资源管理器”功能区域。</span><span class="sxs-lookup"><span data-stu-id="0c6d4-107">You must have permission to access the **Explorer** functional area.</span></span>  
  
-   <span data-ttu-id="0c6d4-108">对于实体的集合模型对象，您必须至少具有 **“更新”** 权限。</span><span class="sxs-lookup"><span data-stu-id="0c6d4-108">You must have a minimum of **Update** permission to the collection model object for the entity.</span></span>  
  
-   <span data-ttu-id="0c6d4-109">必须为显式层次结构和集合启用了实体。</span><span class="sxs-lookup"><span data-stu-id="0c6d4-109">The entity must be enabled for explicit hierarchies and collections.</span></span> <span data-ttu-id="0c6d4-110">有关详细信息，请参阅为[显式层次结构和集合启用实体 &#40;Master Data Services&#41;](enable-an-entity-for-explicit-hierarchies-and-collections-master-data-services.md)。</span><span class="sxs-lookup"><span data-stu-id="0c6d4-110">For more information, see [Enable an Entity for Explicit Hierarchies and Collections &#40;Master Data Services&#41;](enable-an-entity-for-explicit-hierarchies-and-collections-master-data-services.md).</span></span>  
  
### <a name="to-create-a-collection"></a><span data-ttu-id="0c6d4-111">创建集合</span><span class="sxs-lookup"><span data-stu-id="0c6d4-111">To create a collection</span></span>  
  
1.  <span data-ttu-id="0c6d4-112">[!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] 在 \*\*\*\* 主页上，从“模型”列表中，选择模型。</span><span class="sxs-lookup"><span data-stu-id="0c6d4-112">On the [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] home page, from the **Model** list, select a model.</span></span>  
  
2.  <span data-ttu-id="0c6d4-113">\*\*\*\* 从“版本”列表中，选择某一版本。</span><span class="sxs-lookup"><span data-stu-id="0c6d4-113">From the **Version** list, select a version.</span></span>  
  
3.  <span data-ttu-id="0c6d4-114">单击 **“资源管理器”**。</span><span class="sxs-lookup"><span data-stu-id="0c6d4-114">Click **Explorer**.</span></span>  
  
4.  <span data-ttu-id="0c6d4-115">从菜单栏中，指向“集合”\*\*\*\*，然后单击“entity_name”\*\*。</span><span class="sxs-lookup"><span data-stu-id="0c6d4-115">From the menu bar, point to **Collections** and click *entity_name*.</span></span>  
  
5.  <span data-ttu-id="0c6d4-116">单击 **“添加集合”**。</span><span class="sxs-lookup"><span data-stu-id="0c6d4-116">Click **Add collection**.</span></span>  
  
6.  <span data-ttu-id="0c6d4-117">在 **“详细信息”** 选项卡上的 **“名称”** 框中，键入集合的名称。</span><span class="sxs-lookup"><span data-stu-id="0c6d4-117">On the **Details** tab, in the **Name** box, type a name for the collection.</span></span>  
  
7.  <span data-ttu-id="0c6d4-118">在 **“代码”** 框中，键入集合的唯一代码。</span><span class="sxs-lookup"><span data-stu-id="0c6d4-118">In the **Code** box, type a unique code for the collection.</span></span>  
  
8.  <span data-ttu-id="0c6d4-119">还可以在 **“说明”** 框中键入对集合的说明。</span><span class="sxs-lookup"><span data-stu-id="0c6d4-119">Optionally, in the **Description** box, type a description for the collection.</span></span>  
  
9. <span data-ttu-id="0c6d4-120">单击“确定”  。</span><span class="sxs-lookup"><span data-stu-id="0c6d4-120">Click **OK**.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="0c6d4-121">后续步骤</span><span class="sxs-lookup"><span data-stu-id="0c6d4-121">Next Steps</span></span>  
  
-   [<span data-ttu-id="0c6d4-122">将成员添加到集合 (Master Data Services)</span><span class="sxs-lookup"><span data-stu-id="0c6d4-122">Add Members to a Collection &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/add-members-to-a-collection-master-data-services.md)  
  
## <a name="see-also"></a><span data-ttu-id="0c6d4-123">另请参阅</span><span class="sxs-lookup"><span data-stu-id="0c6d4-123">See Also</span></span>  
 <span data-ttu-id="0c6d4-124">[集合 &#40;Master Data Services&#41;](../../2014/master-data-services/collections-master-data-services.md) </span><span class="sxs-lookup"><span data-stu-id="0c6d4-124">[Collections &#40;Master Data Services&#41;](../../2014/master-data-services/collections-master-data-services.md) </span></span>  
 <span data-ttu-id="0c6d4-125">[&#40;Master Data Services 中删除成员或集合&#41;](../../2014/master-data-services/delete-a-member-or-collection-master-data-services.md) </span><span class="sxs-lookup"><span data-stu-id="0c6d4-125">[Delete a Member or Collection &#40;Master Data Services&#41;](../../2014/master-data-services/delete-a-member-or-collection-master-data-services.md) </span></span>  
 [<span data-ttu-id="0c6d4-126">创建显式层次结构 (Master Data Services)</span><span class="sxs-lookup"><span data-stu-id="0c6d4-126">Create an Explicit Hierarchy &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/create-an-explicit-hierarchy-master-data-services.md)  
  
  
