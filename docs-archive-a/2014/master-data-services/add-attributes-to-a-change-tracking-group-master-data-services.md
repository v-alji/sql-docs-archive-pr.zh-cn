---
title: 向更改跟踪组添加属性 (Master Data Services) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
helpviewer_keywords:
- change tracking groups [Master Data Services]
- attributes [Master Data Services], change tracking groups
- change tracking groups [Master Data Services], adding attributes
ms.assetid: e153eb5f-70ca-4c6f-89d8-1f937ed3917d
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: c8a13dad3ca886668c96c1886f8cd238d9adad9f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87590895"
---
# <a name="add-attributes-to-a-change-tracking-group-master-data-services"></a><span data-ttu-id="7eda7-102">向更改跟踪组添加属性 (Master Data Services)</span><span class="sxs-lookup"><span data-stu-id="7eda7-102">Add Attributes to a Change Tracking Group (Master Data Services)</span></span>
  <span data-ttu-id="7eda7-103">在 [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]中，在您想要跟踪对属性值的更改时向更改跟踪组添加属性。</span><span class="sxs-lookup"><span data-stu-id="7eda7-103">In [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)], add attributes to a change tracking group when you want to track changes to the attribute's values.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="7eda7-104">在您向更改跟踪组添加属性后，在属性值发生更改时，该属性在 [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] 数据库中将标记为“已更改”。</span><span class="sxs-lookup"><span data-stu-id="7eda7-104">After you add an attribute to a change tracking group, when values for the attribute change, the attribute is flagged as changed in the [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] database.</span></span> <span data-ttu-id="7eda7-105">创建业务规则以便基于更改执行操作。</span><span class="sxs-lookup"><span data-stu-id="7eda7-105">Create a business rule to take action based on the change.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="7eda7-106">先决条件</span><span class="sxs-lookup"><span data-stu-id="7eda7-106">Prerequisites</span></span>  
 <span data-ttu-id="7eda7-107">若要执行此过程：</span><span class="sxs-lookup"><span data-stu-id="7eda7-107">To perform this procedure:</span></span>  
  
-   <span data-ttu-id="7eda7-108">您必须有权访问 **“系统管理”** 功能区域。</span><span class="sxs-lookup"><span data-stu-id="7eda7-108">You must have permission to access the **System Administration** functional area.</span></span>  
  
-   <span data-ttu-id="7eda7-109">您必须是模型管理员。</span><span class="sxs-lookup"><span data-stu-id="7eda7-109">You must be a model administrator.</span></span> <span data-ttu-id="7eda7-110">有关详细信息，请参阅[管理员 &#40;Master Data Services&#41;](administrators-master-data-services.md)。</span><span class="sxs-lookup"><span data-stu-id="7eda7-110">For more information, see [Administrators &#40;Master Data Services&#41;](administrators-master-data-services.md).</span></span>  
  
-   <span data-ttu-id="7eda7-111">要添加到更改跟踪组的属性必须存在。</span><span class="sxs-lookup"><span data-stu-id="7eda7-111">Attributes must exist to add to the change tracking group.</span></span> <span data-ttu-id="7eda7-112">有关详细信息，请参阅 [创建文本属性 (Master Data Services)](../../2014/master-data-services/create-a-text-attribute-master-data-services.md)。</span><span class="sxs-lookup"><span data-stu-id="7eda7-112">For more information, see [Create a Text Attribute &#40;Master Data Services&#41;](../../2014/master-data-services/create-a-text-attribute-master-data-services.md).</span></span>  
  
### <a name="to-add-attributes-to-a-change-tracking-group"></a><span data-ttu-id="7eda7-113">向更改跟踪组添加属性</span><span class="sxs-lookup"><span data-stu-id="7eda7-113">To add attributes to a change tracking group</span></span>  
  
1.  <span data-ttu-id="7eda7-114">在 [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)]中，单击 **“系统管理”**。</span><span class="sxs-lookup"><span data-stu-id="7eda7-114">In [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)], click **System Administration**.</span></span>  
  
2.  <span data-ttu-id="7eda7-115">在 "**模型资源管理器**" 页上，从菜单栏中指向 "**管理**"，然后单击 "**实体**"。</span><span class="sxs-lookup"><span data-stu-id="7eda7-115">On the **Model Explorer** page, from the menu bar, point to **Manage** and click **Entities**.</span></span>  
  
3.  <span data-ttu-id="7eda7-116">在 **“实体维护”** 页上，从 **“模型”** 列表中，选择某一模型。</span><span class="sxs-lookup"><span data-stu-id="7eda7-116">On the **Entity Maintenance** page, from the **Model** list, select a model.</span></span>  
  
4.  <span data-ttu-id="7eda7-117">为您要跟踪其属性值的实体选择行。</span><span class="sxs-lookup"><span data-stu-id="7eda7-117">Select the row for the entity that you want to track attribute values for.</span></span>  
  
5.  <span data-ttu-id="7eda7-118">单击 **“编辑所选实体”**。</span><span class="sxs-lookup"><span data-stu-id="7eda7-118">Click **Edit selected entity**.</span></span>  
  
6.  <span data-ttu-id="7eda7-119">在 **“编辑实体”** 页上：</span><span class="sxs-lookup"><span data-stu-id="7eda7-119">On the **Edit Entity** page:</span></span>  
  
    -   <span data-ttu-id="7eda7-120">如果该属性是针对叶成员的，则在 "**叶属性**" 窗格中，选择该属性，然后单击 "**编辑叶属性**"。</span><span class="sxs-lookup"><span data-stu-id="7eda7-120">If the attribute is for leaf members, in the **Leaf attributes** pane, select the attribute and click **Edit leaf attribute**.</span></span>  
  
    -   <span data-ttu-id="7eda7-121">如果属性是针对合并成员的，则在 "**合并属性**" 窗格中选择该属性，然后单击 "**编辑合并属性**"。</span><span class="sxs-lookup"><span data-stu-id="7eda7-121">If the attribute is for consolidated members, in the **Consolidated attributes** pane, select the attribute and click **Edit consolidated attribute**.</span></span>  
  
    -   <span data-ttu-id="7eda7-122">如果该属性是针对集合的，则在 "**集合属性**" 窗格中选择该属性，然后单击 "**编辑集合属性**"。</span><span class="sxs-lookup"><span data-stu-id="7eda7-122">If the attribute is for collections, in the **Collection attributes** pane, select the attribute and click **Edit collection attribute**.</span></span>  
  
7.  <span data-ttu-id="7eda7-123">选中 **“启用更改跟踪”** 复选框。</span><span class="sxs-lookup"><span data-stu-id="7eda7-123">Select the **Enable change tracking** check box.</span></span>  
  
8.  <span data-ttu-id="7eda7-124">在 **“更改跟踪组”** 框中，键入该组的编号。</span><span class="sxs-lookup"><span data-stu-id="7eda7-124">In the **Change tracking group** box, type a number for the group.</span></span>  
  
9. <span data-ttu-id="7eda7-125">单击 **“保存属性”**。</span><span class="sxs-lookup"><span data-stu-id="7eda7-125">Click **Save attribute**.</span></span>  
  
10. <span data-ttu-id="7eda7-126">在 **“实体维护”** 页上，单击 **“保存实体”**。</span><span class="sxs-lookup"><span data-stu-id="7eda7-126">On the **Entity Maintenance** page, click **Save entity**.</span></span>  
  
11. <span data-ttu-id="7eda7-127">对于您要在组中包括的所有属性重复此过程。</span><span class="sxs-lookup"><span data-stu-id="7eda7-127">Repeat this procedure for all attributes you want to include in the group.</span></span> <span data-ttu-id="7eda7-128">对于该组中的每个属性，使用相同的更改跟踪组编号。</span><span class="sxs-lookup"><span data-stu-id="7eda7-128">Use the same change tracking group number for each attribute in the group.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="7eda7-129">后续步骤</span><span class="sxs-lookup"><span data-stu-id="7eda7-129">Next Steps</span></span>  
  
-   [<span data-ttu-id="7eda7-130">基于属性值更改启动操作 (Master Data Services)</span><span class="sxs-lookup"><span data-stu-id="7eda7-130">Initiate Actions Based on Attribute Value Changes &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/initiate-actions-based-on-attribute-value-changes-master-data-services.md)  
  
## <a name="see-also"></a><span data-ttu-id="7eda7-131">另请参阅</span><span class="sxs-lookup"><span data-stu-id="7eda7-131">See Also</span></span>  
 <span data-ttu-id="7eda7-132">[Master Data Services 创建文本属性 &#40;&#41;](../../2014/master-data-services/create-a-text-attribute-master-data-services.md) </span><span class="sxs-lookup"><span data-stu-id="7eda7-132">[Create a Text Attribute &#40;Master Data Services&#41;](../../2014/master-data-services/create-a-text-attribute-master-data-services.md) </span></span>  
 [<span data-ttu-id="7eda7-133">创建基于域的属性 (Master Data Services)</span><span class="sxs-lookup"><span data-stu-id="7eda7-133">Create a Domain-Based Attribute &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/create-a-domain-based-attribute-master-data-services.md)  
  
  
