---
title: 创建链接属性 (Master Data Services) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
helpviewer_keywords:
- attributes [Master Data Services], creating link attributes
- creating link attributes [Master Data Services]
ms.assetid: e6658e9c-5b08-4b8d-b556-17ec2dd041d2
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 4770d7904371c10dc6720e8d3d7f28ca797d9b80
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87591455"
---
# <a name="create-a-link-attribute-master-data-services"></a><span data-ttu-id="859d8-102">创建链接属性 (Master Data Services)</span><span class="sxs-lookup"><span data-stu-id="859d8-102">Create a Link Attribute (Master Data Services)</span></span>
  <span data-ttu-id="859d8-103">在 [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] 中，在希望用户输入超链接作为属性值（例如 `http://www.contoso.com`）时创建链接属性。</span><span class="sxs-lookup"><span data-stu-id="859d8-103">In [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)], create a link attribute when you want users to enter a hyperlink as an attribute value, such as `http://www.contoso.com`.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="859d8-104">当用户为链接属性输入值时，该字符串必须以 **http://** 开头，否则将显示错误。</span><span class="sxs-lookup"><span data-stu-id="859d8-104">When users enter a value for a link attribute, the string must begin with **http://** or an error will be displayed.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="859d8-105">先决条件</span><span class="sxs-lookup"><span data-stu-id="859d8-105">Prerequisites</span></span>  
 <span data-ttu-id="859d8-106">若要执行此过程：</span><span class="sxs-lookup"><span data-stu-id="859d8-106">To perform this procedure:</span></span>  
  
-   <span data-ttu-id="859d8-107">您必须有权访问 **“系统管理”** 功能区域。</span><span class="sxs-lookup"><span data-stu-id="859d8-107">You must have permission to access the **System Administration** functional area.</span></span>  
  
-   <span data-ttu-id="859d8-108">您必须是模型管理员。</span><span class="sxs-lookup"><span data-stu-id="859d8-108">You must be a model administrator.</span></span> <span data-ttu-id="859d8-109">有关详细信息，请参阅[管理员 &#40;Master Data Services&#41;](administrators-master-data-services.md)。</span><span class="sxs-lookup"><span data-stu-id="859d8-109">For more information, see [Administrators &#40;Master Data Services&#41;](administrators-master-data-services.md).</span></span>  
  
-   <span data-ttu-id="859d8-110">要为其创建属性的实体必须存在。</span><span class="sxs-lookup"><span data-stu-id="859d8-110">An entity must exist to create the attribute for.</span></span> <span data-ttu-id="859d8-111">有关详细信息，请参阅[创建实体 (Master Data Services)](../../2014/master-data-services/create-an-entity-master-data-services.md)。</span><span class="sxs-lookup"><span data-stu-id="859d8-111">For more information, see [Create an Entity &#40;Master Data Services&#41;](../../2014/master-data-services/create-an-entity-master-data-services.md).</span></span>  
  
### <a name="to-create-a-link-attribute"></a><span data-ttu-id="859d8-112">创建链接属性</span><span class="sxs-lookup"><span data-stu-id="859d8-112">To create a link attribute</span></span>  
  
1.  <span data-ttu-id="859d8-113">在 [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)]中，单击 **“系统管理”**。</span><span class="sxs-lookup"><span data-stu-id="859d8-113">In [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)], click **System Administration**.</span></span>  
  
2.  <span data-ttu-id="859d8-114">在 **“模型视图”** 页上，从菜单栏中，指向 **“管理”** ，然后单击 **“实体”**。</span><span class="sxs-lookup"><span data-stu-id="859d8-114">On the **Model View** page, from the menu bar, point to **Manage** and click **Entities**.</span></span>  
  
3.  <span data-ttu-id="859d8-115">在 **“实体维护”** 页上，从 **“模型”** 列表中，选择某一模型。</span><span class="sxs-lookup"><span data-stu-id="859d8-115">On the **Entity Maintenance** page, from the **Model** list, select a model.</span></span>  
  
4.  <span data-ttu-id="859d8-116">为您要为其创建属性的实体选择行。</span><span class="sxs-lookup"><span data-stu-id="859d8-116">Select the row for the entity that you want to create an attribute for.</span></span>  
  
5.  <span data-ttu-id="859d8-117">单击 **“编辑所选实体”**。</span><span class="sxs-lookup"><span data-stu-id="859d8-117">Click **Edit selected entity**.</span></span>  
  
6.  <span data-ttu-id="859d8-118">在 **“编辑实体”** 页上：</span><span class="sxs-lookup"><span data-stu-id="859d8-118">On the **Edit Entity** page:</span></span>  
  
    -   <span data-ttu-id="859d8-119">如果属性是针对叶成员的，则在 **“叶成员属性”** 窗格中，单击 **“添加叶属性”**。</span><span class="sxs-lookup"><span data-stu-id="859d8-119">If the attribute is for leaf members, in the **Leaf member attributes** pane, click **Add leaf attribute**.</span></span>  
  
    -   <span data-ttu-id="859d8-120">如果属性是针对合并成员的，则在 **“合并成员属性”** 窗格中，单击 **“添加合并属性”**。</span><span class="sxs-lookup"><span data-stu-id="859d8-120">If the attribute is for consolidated members, in the **Consolidated member attributes** pane, click **Add consolidated attribute**.</span></span>  
  
    -   <span data-ttu-id="859d8-121">如果属性是针对集合的，则在 **“集合属性”** 窗格中，单击 **“添加集合属性”**。</span><span class="sxs-lookup"><span data-stu-id="859d8-121">If the attribute is for collections, in the **Collection attributes** pane, click **Add collection attribute**.</span></span>  
  
7.  <span data-ttu-id="859d8-122">在 **“添加属性”** 页上，选择 **“自由格式”** 选项。</span><span class="sxs-lookup"><span data-stu-id="859d8-122">On the **Add Attribute** page, select the **Free-form** option.</span></span>  
  
8.  <span data-ttu-id="859d8-123">在 **“名称”** 框中，键入属性的名称。</span><span class="sxs-lookup"><span data-stu-id="859d8-123">In the **Name** box, type a name for the attribute.</span></span> <span data-ttu-id="859d8-124">有关不可用作属性名称的单词列表，请参阅[保留字 (Master Data Services)](../../2014/master-data-services/reserved-words-master-data-services.md)。</span><span class="sxs-lookup"><span data-stu-id="859d8-124">For a list of words that should not be used as attribute names, see [Reserved Words &#40;Master Data Services&#41;](../../2014/master-data-services/reserved-words-master-data-services.md).</span></span>  
  
9. <span data-ttu-id="859d8-125">在 **“显示像素宽度”** 框中，键入要在 **“资源管理器”** 网格中显示的属性列的宽度。</span><span class="sxs-lookup"><span data-stu-id="859d8-125">In the **Display pixel width** box, type the width of the attribute column to be displayed in the **Explorer** grid.</span></span>  
  
10. <span data-ttu-id="859d8-126">从 **“数据类型”** 列表中，选择 **“链接”**。</span><span class="sxs-lookup"><span data-stu-id="859d8-126">From the **Data type** list, select **Link**.</span></span>  
  
11. <span data-ttu-id="859d8-127">在 **“长度”** 框中，键入允许的最大字符数。</span><span class="sxs-lookup"><span data-stu-id="859d8-127">In the **Length** box, type the maximum number of characters allowed.</span></span>  
  
12. <span data-ttu-id="859d8-128">根据需要，选择 **“启用更改跟踪”** 可以跟踪对属性组的更改。</span><span class="sxs-lookup"><span data-stu-id="859d8-128">Optionally, select **Enable change tracking** to track changes to groups of attributes.</span></span> <span data-ttu-id="859d8-129">有关详细信息，请参阅[向更改跟踪组添加属性 (Master Data Services)](../../2014/master-data-services/add-attributes-to-a-change-tracking-group-master-data-services.md)。</span><span class="sxs-lookup"><span data-stu-id="859d8-129">For more information, see [Add Attributes to a Change Tracking Group &#40;Master Data Services&#41;](../../2014/master-data-services/add-attributes-to-a-change-tracking-group-master-data-services.md).</span></span>  
  
13. <span data-ttu-id="859d8-130">单击 **“保存属性”**。</span><span class="sxs-lookup"><span data-stu-id="859d8-130">Click **Save attribute**.</span></span>  
  
14. <span data-ttu-id="859d8-131">在 **“实体维护”** 页上，单击 **“保存实体”**。</span><span class="sxs-lookup"><span data-stu-id="859d8-131">On the **Entity Maintenance** page, click **Save entity**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="859d8-132">另请参阅</span><span class="sxs-lookup"><span data-stu-id="859d8-132">See Also</span></span>  
 <span data-ttu-id="859d8-133">[属性 &#40;Master Data Services&#41;](../../2014/master-data-services/attributes-master-data-services.md) </span><span class="sxs-lookup"><span data-stu-id="859d8-133">[Attributes &#40;Master Data Services&#41;](../../2014/master-data-services/attributes-master-data-services.md) </span></span>  
 <span data-ttu-id="859d8-134">[更改属性名称 &#40;Master Data Services&#41;](change-an-attribute-name-and-data-type-master-data-services.md) </span><span class="sxs-lookup"><span data-stu-id="859d8-134">[Change an Attribute Name &#40;Master Data Services&#41;](change-an-attribute-name-and-data-type-master-data-services.md) </span></span>  
 <span data-ttu-id="859d8-135">[创建基于域的属性 &#40;Master Data Services&#41;](../../2014/master-data-services/create-a-domain-based-attribute-master-data-services.md) </span><span class="sxs-lookup"><span data-stu-id="859d8-135">[Create a Domain-Based Attribute &#40;Master Data Services&#41;](../../2014/master-data-services/create-a-domain-based-attribute-master-data-services.md) </span></span>  
 [<span data-ttu-id="859d8-136">创建文件属性 (Master Data Services)</span><span class="sxs-lookup"><span data-stu-id="859d8-136">Create a File Attribute &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/create-a-file-attribute-master-data-services.md)  
  
  
