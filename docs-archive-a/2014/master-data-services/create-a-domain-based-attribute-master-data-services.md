---
title: 创建基于域的属性 (Master Data Services) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
helpviewer_keywords:
- domain-based attributes [Master Data Services], creating
- creating domain-based attributes [Master Data Services]
- attributes [Master Data Services], creating domain-based attributes
ms.assetid: 11c31c9f-e6cc-47b7-b76a-d691f84c93c6
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 51c0f44bb76ae2ad4c25987ed5e5ee144a18c739
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87578927"
---
# <a name="create-a-domain-based-attribute-master-data-services"></a><span data-ttu-id="43398-102">创建基于域的属性 (Master Data Services)</span><span class="sxs-lookup"><span data-stu-id="43398-102">Create a Domain-Based Attribute (Master Data Services)</span></span>
  <span data-ttu-id="43398-103">在 [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]中，创建基于域的属性以便使用来自某一实体的成员填充属性值。</span><span class="sxs-lookup"><span data-stu-id="43398-103">In [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)], create a domain-based attribute to populate an attribute's values with members from an entity.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="43398-104">先决条件</span><span class="sxs-lookup"><span data-stu-id="43398-104">Prerequisites</span></span>  
 <span data-ttu-id="43398-105">若要执行此过程：</span><span class="sxs-lookup"><span data-stu-id="43398-105">To perform this procedure:</span></span>  
  
-   <span data-ttu-id="43398-106">您必须有权访问 **“系统管理”** 功能区域。</span><span class="sxs-lookup"><span data-stu-id="43398-106">You must have permission to access the **System Administration** functional area.</span></span>  
  
-   <span data-ttu-id="43398-107">您必须是模型管理员。</span><span class="sxs-lookup"><span data-stu-id="43398-107">You must be a model administrator.</span></span> <span data-ttu-id="43398-108">有关详细信息，请参阅[管理员 &#40;Master Data Services&#41;](administrators-master-data-services.md)。</span><span class="sxs-lookup"><span data-stu-id="43398-108">For more information, see [Administrators &#40;Master Data Services&#41;](administrators-master-data-services.md).</span></span>  
  
-   <span data-ttu-id="43398-109">要用作属性值的源的实体必须存在。</span><span class="sxs-lookup"><span data-stu-id="43398-109">An entity must exist to use as the source of the attribute values.</span></span> <span data-ttu-id="43398-110">例如，若要基于 Color 实体创建基于域的属性，您必须首先创建 Color 实体。</span><span class="sxs-lookup"><span data-stu-id="43398-110">For example, to create a domain-based attribute based on the Color entity, you must first create the Color entity.</span></span> <span data-ttu-id="43398-111">有关详细信息，请参阅[创建实体 (Master Data Services)](../../2014/master-data-services/create-an-entity-master-data-services.md)。</span><span class="sxs-lookup"><span data-stu-id="43398-111">For more information, see [Create an Entity &#40;Master Data Services&#41;](../../2014/master-data-services/create-an-entity-master-data-services.md).</span></span>  
  
-   <span data-ttu-id="43398-112">要为其创建属性的实体必须存在。</span><span class="sxs-lookup"><span data-stu-id="43398-112">An entity must exist to create the attribute for.</span></span> <span data-ttu-id="43398-113">有关详细信息，请参阅[创建实体 (Master Data Services)](../../2014/master-data-services/create-an-entity-master-data-services.md)。</span><span class="sxs-lookup"><span data-stu-id="43398-113">For more information, see [Create an Entity &#40;Master Data Services&#41;](../../2014/master-data-services/create-an-entity-master-data-services.md).</span></span>  
  
### <a name="to-create-a-domain-based-attribute"></a><span data-ttu-id="43398-114">创建基于域的属性</span><span class="sxs-lookup"><span data-stu-id="43398-114">To create a domain-based attribute</span></span>  
  
1.  <span data-ttu-id="43398-115">在 [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)]中，单击 **“系统管理”**。</span><span class="sxs-lookup"><span data-stu-id="43398-115">In [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)], click **System Administration**.</span></span>  
  
2.  <span data-ttu-id="43398-116">在 **“模型视图”** 页上，从菜单栏中，指向 **“管理”** ，然后单击 **“实体”**。</span><span class="sxs-lookup"><span data-stu-id="43398-116">On the **Model View** page, from the menu bar, point to **Manage** and click **Entities**.</span></span>  
  
3.  <span data-ttu-id="43398-117">在 **“实体维护”** 页上，从 **“模型”** 列表中，选择某一模型。</span><span class="sxs-lookup"><span data-stu-id="43398-117">On the **Entity Maintenance** page, from the **Model** list, select a model.</span></span>  
  
4.  <span data-ttu-id="43398-118">为您要为其创建属性的实体选择行。</span><span class="sxs-lookup"><span data-stu-id="43398-118">Select the row for the entity that you want to create an attribute for.</span></span>  
  
5.  <span data-ttu-id="43398-119">单击 **“编辑所选实体”**。</span><span class="sxs-lookup"><span data-stu-id="43398-119">Click **Edit selected entity**.</span></span>  
  
6.  <span data-ttu-id="43398-120">在 **“编辑实体”** 页上：</span><span class="sxs-lookup"><span data-stu-id="43398-120">On the **Edit Entity** page:</span></span>  
  
    -   <span data-ttu-id="43398-121">如果属性是针对叶成员的，则在 **“叶成员属性”** 窗格中，单击 **“添加叶属性”**。</span><span class="sxs-lookup"><span data-stu-id="43398-121">If the attribute is for leaf members, in the **Leaf member attributes** pane, click **Add leaf attribute**.</span></span>  
  
    -   <span data-ttu-id="43398-122">如果属性是针对合并成员的，则在 **“合并成员属性”** 窗格中，单击 **“添加合并属性”**。</span><span class="sxs-lookup"><span data-stu-id="43398-122">If the attribute is for consolidated members, in the **Consolidated member attributes** pane, click **Add consolidated attribute**.</span></span>  
  
    -   <span data-ttu-id="43398-123">如果属性是针对集合的，则在 **“集合属性”** 窗格中，单击 **“添加集合属性”**。</span><span class="sxs-lookup"><span data-stu-id="43398-123">If the attribute is for collections, in the **Collection attributes** pane, click **Add collection attribute**.</span></span>  
  
7.  <span data-ttu-id="43398-124">在 "**添加属性**" 页上，选择 "**基于域**" 选项。</span><span class="sxs-lookup"><span data-stu-id="43398-124">On the **Add Attribute** page, select the **Domain-based** option.</span></span>  
  
8.  <span data-ttu-id="43398-125">在 **“名称”** 框中，键入属性的名称。</span><span class="sxs-lookup"><span data-stu-id="43398-125">In the **Name** box, type a name for the attribute.</span></span> <span data-ttu-id="43398-126">该名称不必与您用于属性值的源的实体名称相同。</span><span class="sxs-lookup"><span data-stu-id="43398-126">It does not have to be the same name as the entity that you use for the source of the attribute values.</span></span>  
  
9. <span data-ttu-id="43398-127">在 **“显示像素宽度”** 框中，键入要在 **“资源管理器”** 网格中显示的属性列的宽度。</span><span class="sxs-lookup"><span data-stu-id="43398-127">In the **Display pixel width** box, type the width of the attribute column to be displayed in the **Explorer** grid.</span></span>  
  
10. <span data-ttu-id="43398-128">从 "**实体**" 列表中，选择要用于填充属性值的实体。</span><span class="sxs-lookup"><span data-stu-id="43398-128">From the **Entity** list, choose the entity to be used to populate the attribute values.</span></span>  
  
11. <span data-ttu-id="43398-129">可选。</span><span class="sxs-lookup"><span data-stu-id="43398-129">Optional.</span></span> <span data-ttu-id="43398-130">选择 **Enable change tracking** 可以跟踪对属性值的更改。</span><span class="sxs-lookup"><span data-stu-id="43398-130">Select **Enable change tracking** to track changes to groups of attributes.</span></span> <span data-ttu-id="43398-131">有关详细信息，请参阅[向更改跟踪组添加属性 (Master Data Services)](../../2014/master-data-services/add-attributes-to-a-change-tracking-group-master-data-services.md)。</span><span class="sxs-lookup"><span data-stu-id="43398-131">For more information, see [Add Attributes to a Change Tracking Group &#40;Master Data Services&#41;](../../2014/master-data-services/add-attributes-to-a-change-tracking-group-master-data-services.md).</span></span>  
  
12. <span data-ttu-id="43398-132">单击 **“保存属性”**。</span><span class="sxs-lookup"><span data-stu-id="43398-132">Click **Save attribute**.</span></span>  
  
13. <span data-ttu-id="43398-133">在 **“实体维护”** 页上，单击 **“保存实体”**。</span><span class="sxs-lookup"><span data-stu-id="43398-133">On the **Entity Maintenance** page, click **Save entity**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="43398-134">另请参阅</span><span class="sxs-lookup"><span data-stu-id="43398-134">See Also</span></span>  
 <span data-ttu-id="43398-135">[基于域的属性 &#40;Master Data Services&#41;](../../2014/master-data-services/domain-based-attributes-master-data-services.md) </span><span class="sxs-lookup"><span data-stu-id="43398-135">[Domain-Based Attributes &#40;Master Data Services&#41;](../../2014/master-data-services/domain-based-attributes-master-data-services.md) </span></span>  
 <span data-ttu-id="43398-136">[创建派生层次结构 &#40;Master Data Services&#41;](../../2014/master-data-services/create-a-derived-hierarchy-master-data-services.md) </span><span class="sxs-lookup"><span data-stu-id="43398-136">[Create a Derived Hierarchy &#40;Master Data Services&#41;](../../2014/master-data-services/create-a-derived-hierarchy-master-data-services.md) </span></span>  
 <span data-ttu-id="43398-137">[更改属性名称 &#40;Master Data Services&#41;](change-an-attribute-name-and-data-type-master-data-services.md) </span><span class="sxs-lookup"><span data-stu-id="43398-137">[Change an Attribute Name &#40;Master Data Services&#41;](change-an-attribute-name-and-data-type-master-data-services.md) </span></span>  
 [<span data-ttu-id="43398-138">删除属性 &#40;Master Data Services&#41;</span><span class="sxs-lookup"><span data-stu-id="43398-138">Delete an Attribute &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/delete-an-attribute-master-data-services.md)  
  
  
