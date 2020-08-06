---
title: 创建属性组 (Master Data Services) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
helpviewer_keywords:
- attribute groups [Master Data Services], creating
- creating attribute groups [Master Data Services]
ms.assetid: 798c325e-e8d8-412a-b02e-118f2741d1c7
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: fbd95869082ea0a73f3abea092163c4705e4da5c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87691769"
---
# <a name="create-an-attribute-group-master-data-services"></a><span data-ttu-id="79349-102">创建属性组 (Master Data Services)</span><span class="sxs-lookup"><span data-stu-id="79349-102">Create an Attribute Group (Master Data Services)</span></span>
  <span data-ttu-id="79349-103">在 [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]中，当您想要在 **“资源管理器”** 网格中的单独选项卡上显示属性时，创建属性组。</span><span class="sxs-lookup"><span data-stu-id="79349-103">In [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)], create attribute groups when you want to display attributes on individual tabs in the **Explorer** grid.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="79349-104">创建属性组时，对除创建者之外的所有用户自动隐藏它。</span><span class="sxs-lookup"><span data-stu-id="79349-104">When you create an attribute group, it is automatically hidden from all users except the one who created it.</span></span> <span data-ttu-id="79349-105">有关使组可见的详细信息，请参阅 [使属性组对用户可见 (Master Data Services)](make-an-attribute-group-visible-to-users-master-data-services.md)选项卡上。</span><span class="sxs-lookup"><span data-stu-id="79349-105">For more information about making the group visible, see [Make an Attribute Group Visible to Users &#40;Master Data Services&#41;](make-an-attribute-group-visible-to-users-master-data-services.md).</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="79349-106">先决条件</span><span class="sxs-lookup"><span data-stu-id="79349-106">Prerequisites</span></span>  
 <span data-ttu-id="79349-107">若要执行此过程：</span><span class="sxs-lookup"><span data-stu-id="79349-107">To perform this procedure:</span></span>  
  
-   <span data-ttu-id="79349-108">您必须有权访问 **“系统管理”** 功能区域。</span><span class="sxs-lookup"><span data-stu-id="79349-108">You must have permission to access the **System Administration** functional area.</span></span>  
  
-   <span data-ttu-id="79349-109">您必须是模型管理员。</span><span class="sxs-lookup"><span data-stu-id="79349-109">You must be a model administrator.</span></span> <span data-ttu-id="79349-110">有关详细信息，请参阅[管理员 &#40;Master Data Services&#41;](../../2014/master-data-services/administrators-master-data-services.md)。</span><span class="sxs-lookup"><span data-stu-id="79349-110">For more information, see [Administrators &#40;Master Data Services&#41;](../../2014/master-data-services/administrators-master-data-services.md).</span></span>  
  
-   <span data-ttu-id="79349-111">必须至少存在一个属性。</span><span class="sxs-lookup"><span data-stu-id="79349-111">At least one attribute must exist.</span></span> <span data-ttu-id="79349-112">有关详细信息，请参阅 [创建文本属性 (Master Data Services)](../../2014/master-data-services/create-a-text-attribute-master-data-services.md)。</span><span class="sxs-lookup"><span data-stu-id="79349-112">For more information, see [Create a Text Attribute &#40;Master Data Services&#41;](../../2014/master-data-services/create-a-text-attribute-master-data-services.md).</span></span>  
  
### <a name="to-create-an-attribute-group"></a><span data-ttu-id="79349-113">创建属性组</span><span class="sxs-lookup"><span data-stu-id="79349-113">To create an attribute group</span></span>  
  
1.  <span data-ttu-id="79349-114">在 [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)]中，单击 **“系统管理”**。</span><span class="sxs-lookup"><span data-stu-id="79349-114">In [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)], click **System Administration**.</span></span>  
  
2.  <span data-ttu-id="79349-115">在 "**模型视图**" 页上，从菜单栏中指向 "**管理**"，然后单击 "**属性组**"。</span><span class="sxs-lookup"><span data-stu-id="79349-115">On the **Model View** page, from the menu bar, point to **Manage** and click **Attribute Groups**.</span></span>  
  
3.  <span data-ttu-id="79349-116">从 **“模型”** 列表中，选择某一模型。</span><span class="sxs-lookup"><span data-stu-id="79349-116">From the **Model** list, select a model.</span></span>  
  
4.  <span data-ttu-id="79349-117">从 **“实体”** 列表中，选择某一实体。</span><span class="sxs-lookup"><span data-stu-id="79349-117">From the **Entity** list, select an entity.</span></span>  
  
5.  <span data-ttu-id="79349-118">单击 **“叶组”**、 **“合并组”** 或 **“集合组”** ，以便为叶成员、合并成员或集合相应创建属性组。</span><span class="sxs-lookup"><span data-stu-id="79349-118">Click **Leaf Groups**, **Consolidated Groups**, or **Collection Groups** to create an attribute group of leaf members, consolidated members, or collections respectively.</span></span>  
  
6.  <span data-ttu-id="79349-119">单击 "**添加属性组**"。</span><span class="sxs-lookup"><span data-stu-id="79349-119">Click **Add attribute group**.</span></span>  
  
7.  <span data-ttu-id="79349-120">在 "**叶组名称**" 框中，键入组的名称。</span><span class="sxs-lookup"><span data-stu-id="79349-120">In the **Leaf group name** box, type a name for the group.</span></span> <span data-ttu-id="79349-121">这是在 "**资源管理器**" 中的选项卡上显示的名称。</span><span class="sxs-lookup"><span data-stu-id="79349-121">This is the name displayed on the tab in **Explorer**.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="79349-122">如果在步骤5中选择了 "**合并组**" 或 "**集合组**"，则此框将分别为 "**合并组名称**" 或 "**集合组名称**"。</span><span class="sxs-lookup"><span data-stu-id="79349-122">If you selected **Consolidated Groups** or **Collection Groups** in step 5, this box is **Consolidated group name** or **Collection group name**, respectively.</span></span>  
  
8.  <span data-ttu-id="79349-123">单击 **“保存组”**。</span><span class="sxs-lookup"><span data-stu-id="79349-123">Click **Save group**.</span></span>  
  
9. <span data-ttu-id="79349-124">展开该组的文件夹。</span><span class="sxs-lookup"><span data-stu-id="79349-124">Expand the folder for the group.</span></span>  
  
10. <span data-ttu-id="79349-125">单击 **“属性”**。</span><span class="sxs-lookup"><span data-stu-id="79349-125">Click **Attributes**.</span></span>  
  
11. <span data-ttu-id="79349-126">单击 "**编辑所选项**"。</span><span class="sxs-lookup"><span data-stu-id="79349-126">Click **Edit selected item**.</span></span>  
  
12. <span data-ttu-id="79349-127">单击 "**可用**" 框中的 "属性"，然后单击 "**添加**" 箭头。</span><span class="sxs-lookup"><span data-stu-id="79349-127">Click attributes in the **Available** box and click the **Add** arrow.</span></span> <span data-ttu-id="79349-128">若要全部添加，请单击 **“全部添加”** 箭头。</span><span class="sxs-lookup"><span data-stu-id="79349-128">To add all, click the **Add All** arrow.</span></span>  
  
13. <span data-ttu-id="79349-129">或者，单击 "**向上**" 和 "**向下**" 箭头可以更改属性的从左到右顺序。</span><span class="sxs-lookup"><span data-stu-id="79349-129">Optionally, click the **Up** and **Down** arrows to change the left-to-right order of the attributes.</span></span>  
  
14. <span data-ttu-id="79349-130">单击“ **保存**”。</span><span class="sxs-lookup"><span data-stu-id="79349-130">Click **Save**.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="79349-131">后续步骤</span><span class="sxs-lookup"><span data-stu-id="79349-131">Next Steps</span></span>  
  
-   [<span data-ttu-id="79349-132">使属性组对用户可见 (Master Data Services)</span><span class="sxs-lookup"><span data-stu-id="79349-132">Make an Attribute Group Visible to Users &#40;Master Data Services&#41;</span></span>](make-an-attribute-group-visible-to-users-master-data-services.md)  
  
## <a name="see-also"></a><span data-ttu-id="79349-133">另请参阅</span><span class="sxs-lookup"><span data-stu-id="79349-133">See Also</span></span>  
 <span data-ttu-id="79349-134">[属性组 &#40;Master Data Services&#41;](../../2014/master-data-services/attribute-groups-master-data-services.md) </span><span class="sxs-lookup"><span data-stu-id="79349-134">[Attribute Groups &#40;Master Data Services&#41;](../../2014/master-data-services/attribute-groups-master-data-services.md) </span></span>  
 <span data-ttu-id="79349-135">[属性 &#40;Master Data Services&#41;](../../2014/master-data-services/attributes-master-data-services.md) </span><span class="sxs-lookup"><span data-stu-id="79349-135">[Attributes &#40;Master Data Services&#41;](../../2014/master-data-services/attributes-master-data-services.md) </span></span>  
 <span data-ttu-id="79349-136">[更改属性组名称 &#40;Master Data Services&#41;](../../2014/master-data-services/change-an-attribute-group-name-master-data-services.md) </span><span class="sxs-lookup"><span data-stu-id="79349-136">[Change an Attribute Group Name &#40;Master Data Services&#41;](../../2014/master-data-services/change-an-attribute-group-name-master-data-services.md) </span></span>  
 <span data-ttu-id="79349-137">[删除 &#40;Master Data Services 的属性组&#41;](../../2014/master-data-services/delete-an-attribute-group-master-data-services.md) </span><span class="sxs-lookup"><span data-stu-id="79349-137">[Delete an Attribute Group &#40;Master Data Services&#41;](../../2014/master-data-services/delete-an-attribute-group-master-data-services.md) </span></span>  
 <span data-ttu-id="79349-138">[叶权限 &#40;Master Data Services&#41;](../../2014/master-data-services/leaf-permissions-master-data-services.md) </span><span class="sxs-lookup"><span data-stu-id="79349-138">[Leaf Permissions &#40;Master Data Services&#41;](../../2014/master-data-services/leaf-permissions-master-data-services.md) </span></span>  
 [<span data-ttu-id="79349-139">&#40;Master Data Services 的合并权限&#41;</span><span class="sxs-lookup"><span data-stu-id="79349-139">Consolidated Permissions &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/consolidated-permissions-master-data-services.md)  
  
  
