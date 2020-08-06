---
title: 创建数字属性 (Master Data Services) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
helpviewer_keywords:
- attributes [Master Data Services], creating number attributes
- creating number attributes [Master Data Services]
ms.assetid: c0dbb6d8-ba78-485a-a40d-6d5cb7e75d0a
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: bb9302c0b585c21410a6a764dc2e6dac845c6299
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87576871"
---
# <a name="create-a-numeric-attribute-master-data-services"></a><span data-ttu-id="57e6a-102">创建数字属性 (Master Data Services)</span><span class="sxs-lookup"><span data-stu-id="57e6a-102">Create a Numeric Attribute (Master Data Services)</span></span>
  <span data-ttu-id="57e6a-103">在 [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]中，在您希望用户输入数字作为属性值时创建数字属性。</span><span class="sxs-lookup"><span data-stu-id="57e6a-103">In [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)], create a numeric attribute when you want users to enter a number as an attribute value.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="57e6a-104">数字属性存在一些限制。</span><span class="sxs-lookup"><span data-stu-id="57e6a-104">Numeric attributes have limitations.</span></span> <span data-ttu-id="57e6a-105">有关详细信息，请参阅 [属性 (Master Data Services)](attributes-master-data-services.md)。</span><span class="sxs-lookup"><span data-stu-id="57e6a-105">For more information, see [Attributes &#40;Master Data Services&#41;](attributes-master-data-services.md).</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="57e6a-106">先决条件</span><span class="sxs-lookup"><span data-stu-id="57e6a-106">Prerequisites</span></span>  
 <span data-ttu-id="57e6a-107">若要执行此过程：</span><span class="sxs-lookup"><span data-stu-id="57e6a-107">To perform this procedure:</span></span>  
  
-   <span data-ttu-id="57e6a-108">您必须有权访问 **“系统管理”** 功能区域。</span><span class="sxs-lookup"><span data-stu-id="57e6a-108">You must have permission to access the **System Administration** functional area.</span></span>  
  
-   <span data-ttu-id="57e6a-109">您必须是模型管理员。</span><span class="sxs-lookup"><span data-stu-id="57e6a-109">You must be a model administrator.</span></span> <span data-ttu-id="57e6a-110">有关详细信息，请参阅[管理员 &#40;Master Data Services&#41;](../../2014/master-data-services/administrators-master-data-services.md)。</span><span class="sxs-lookup"><span data-stu-id="57e6a-110">For more information, see [Administrators &#40;Master Data Services&#41;](../../2014/master-data-services/administrators-master-data-services.md).</span></span>  
  
-   <span data-ttu-id="57e6a-111">要为其创建属性的实体必须存在。</span><span class="sxs-lookup"><span data-stu-id="57e6a-111">An entity must exist to create the attribute for.</span></span> <span data-ttu-id="57e6a-112">有关详细信息，请参阅[创建实体 (Master Data Services)](../../2014/master-data-services/create-an-entity-master-data-services.md)。</span><span class="sxs-lookup"><span data-stu-id="57e6a-112">For more information, see [Create an Entity &#40;Master Data Services&#41;](../../2014/master-data-services/create-an-entity-master-data-services.md).</span></span>  
  
### <a name="to-create-a-numeric-attribute"></a><span data-ttu-id="57e6a-113">创建数字属性</span><span class="sxs-lookup"><span data-stu-id="57e6a-113">To create a numeric attribute</span></span>  
  
1.  <span data-ttu-id="57e6a-114">在 [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)]中，单击 **“系统管理”**。</span><span class="sxs-lookup"><span data-stu-id="57e6a-114">In [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)], click **System Administration**.</span></span>  
  
2.  <span data-ttu-id="57e6a-115">在 **“模型视图”** 页上，从菜单栏中，指向 **“管理”** ，然后单击 **“实体”**。</span><span class="sxs-lookup"><span data-stu-id="57e6a-115">On the **Model View** page, from the menu bar, point to **Manage** and click **Entities**.</span></span>  
  
3.  <span data-ttu-id="57e6a-116">在 **“实体维护”** 页上，从 **“模型”** 列表中，选择某一模型。</span><span class="sxs-lookup"><span data-stu-id="57e6a-116">On the **Entity Maintenance** page, from the **Model** list, select a model.</span></span>  
  
4.  <span data-ttu-id="57e6a-117">为您要为其创建属性的实体选择行。</span><span class="sxs-lookup"><span data-stu-id="57e6a-117">Select the row for the entity that you want to create an attribute for.</span></span>  
  
5.  <span data-ttu-id="57e6a-118">单击 **“编辑所选实体”**。</span><span class="sxs-lookup"><span data-stu-id="57e6a-118">Click **Edit selected entity**.</span></span>  
  
6.  <span data-ttu-id="57e6a-119">在 **“编辑实体”** 页上：</span><span class="sxs-lookup"><span data-stu-id="57e6a-119">On the **Edit Entity** page:</span></span>  
  
    -   <span data-ttu-id="57e6a-120">如果属性是针对叶成员的，则在 **“叶成员属性”** 窗格中，单击 **“添加叶属性”**。</span><span class="sxs-lookup"><span data-stu-id="57e6a-120">If the attribute is for leaf members, in the **Leaf member attributes** pane, click **Add leaf attribute**.</span></span>  
  
    -   <span data-ttu-id="57e6a-121">如果属性是针对合并成员的，则在 **“合并成员属性”** 窗格中，单击 **“添加合并属性”**。</span><span class="sxs-lookup"><span data-stu-id="57e6a-121">If the attribute is for consolidated members, in the **Consolidated member attributes** pane, click **Add consolidated attribute**.</span></span>  
  
    -   <span data-ttu-id="57e6a-122">如果属性是针对集合的，则在 **“集合属性”** 窗格中，单击 **“添加集合属性”**。</span><span class="sxs-lookup"><span data-stu-id="57e6a-122">If the attribute is for collections, in the **Collection attributes** pane, click **Add collection attribute**.</span></span>  
  
7.  <span data-ttu-id="57e6a-123">在 **“添加属性”** 页上，选择 **“自由格式”** 选项。</span><span class="sxs-lookup"><span data-stu-id="57e6a-123">On the **Add Attribute** page, select the **Free-form** option.</span></span>  
  
8.  <span data-ttu-id="57e6a-124">在 **“名称”** 框中，键入属性的名称。</span><span class="sxs-lookup"><span data-stu-id="57e6a-124">In the **Name** box, type a name for the attribute.</span></span> <span data-ttu-id="57e6a-125">有关不可用作属性名称的单词列表，请参阅[保留字 (Master Data Services)](../../2014/master-data-services/reserved-words-master-data-services.md)。</span><span class="sxs-lookup"><span data-stu-id="57e6a-125">For a list of words that should not be used as attribute names, see [Reserved Words &#40;Master Data Services&#41;](../../2014/master-data-services/reserved-words-master-data-services.md).</span></span>  
  
9. <span data-ttu-id="57e6a-126">在 **“显示像素宽度”** 框中，键入要在 **“资源管理器”** 网格中显示的属性列的宽度。</span><span class="sxs-lookup"><span data-stu-id="57e6a-126">In the **Display pixel width** box, type the width of the attribute column to be displayed in the **Explorer** grid.</span></span>  
  
10. <span data-ttu-id="57e6a-127">从 **“数据类型”** 列表中，选择 **“数字”**。</span><span class="sxs-lookup"><span data-stu-id="57e6a-127">From the **Data type** list, select **Number**.</span></span>  
  
11. <span data-ttu-id="57e6a-128">在 **“小数位数”** 框中，键入小数点后可以输入的位数。</span><span class="sxs-lookup"><span data-stu-id="57e6a-128">In the **Decimals** box, type the number of numbers that can be entered after a decimal.</span></span>  
  
12. <span data-ttu-id="57e6a-129">从 "**输入掩码**" 列表中，选择负数的格式。</span><span class="sxs-lookup"><span data-stu-id="57e6a-129">From the **Input mask** list, select a format for negative numbers.</span></span>  
  
13. <span data-ttu-id="57e6a-130">根据需要，选择 **“启用更改跟踪”** 可以跟踪对属性组的更改。</span><span class="sxs-lookup"><span data-stu-id="57e6a-130">Optionally, select **Enable change tracking** to track changes to groups of attributes.</span></span> <span data-ttu-id="57e6a-131">有关详细信息，请参阅 [向更改跟踪组添加属性 (Master Data Services)](../../2014/master-data-services/add-attributes-to-a-change-tracking-group-master-data-services.md) 。</span><span class="sxs-lookup"><span data-stu-id="57e6a-131">See [Add Attributes to a Change Tracking Group &#40;Master Data Services&#41;](../../2014/master-data-services/add-attributes-to-a-change-tracking-group-master-data-services.md) for more information.</span></span>  
  
14. <span data-ttu-id="57e6a-132">单击 **“保存属性”**。</span><span class="sxs-lookup"><span data-stu-id="57e6a-132">Click **Save attribute**.</span></span>  
  
15. <span data-ttu-id="57e6a-133">在 **“实体维护”** 页上，单击 **“保存实体”**。</span><span class="sxs-lookup"><span data-stu-id="57e6a-133">On the **Entity Maintenance** page, click **Save entity**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="57e6a-134">另请参阅</span><span class="sxs-lookup"><span data-stu-id="57e6a-134">See Also</span></span>  
 <span data-ttu-id="57e6a-135">[属性 &#40;Master Data Services&#41;](attributes-master-data-services.md) </span><span class="sxs-lookup"><span data-stu-id="57e6a-135">[Attributes &#40;Master Data Services&#41;](attributes-master-data-services.md) </span></span>  
 <span data-ttu-id="57e6a-136">[更改属性名称 &#40;Master Data Services&#41;](change-an-attribute-name-and-data-type-master-data-services.md) </span><span class="sxs-lookup"><span data-stu-id="57e6a-136">[Change an Attribute Name &#40;Master Data Services&#41;](change-an-attribute-name-and-data-type-master-data-services.md) </span></span>  
 <span data-ttu-id="57e6a-137">[创建基于域的属性 &#40;Master Data Services&#41;](../../2014/master-data-services/create-a-domain-based-attribute-master-data-services.md) </span><span class="sxs-lookup"><span data-stu-id="57e6a-137">[Create a Domain-Based Attribute &#40;Master Data Services&#41;](../../2014/master-data-services/create-a-domain-based-attribute-master-data-services.md) </span></span>  
 [<span data-ttu-id="57e6a-138">创建文件属性 (Master Data Services)</span><span class="sxs-lookup"><span data-stu-id="57e6a-138">Create a File Attribute &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/create-a-file-attribute-master-data-services.md)  
  
  
