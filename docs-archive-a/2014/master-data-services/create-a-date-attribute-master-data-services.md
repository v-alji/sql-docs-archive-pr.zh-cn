---
title: 创建日期属性 (Master Data Services) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
helpviewer_keywords:
- creating date attributes [Master Data Services]
- attributes [Master Data Services], creating date attributes
ms.assetid: 22a8f1a3-b4f2-4cfa-8495-7daad5ce9d12
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 93797b90ff03c6a2b60ce8e015897a46a7448aad
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87576874"
---
# <a name="create-a-date-attribute-master-data-services"></a><span data-ttu-id="19050-102">创建日期属性 (Master Data Services)</span><span class="sxs-lookup"><span data-stu-id="19050-102">Create a Date Attribute (Master Data Services)</span></span>
  <span data-ttu-id="19050-103">在 [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]中，在您希望用户输入日期作为属性值时创建日期属性。</span><span class="sxs-lookup"><span data-stu-id="19050-103">In [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)], create a date attribute when you want users to enter a date as an attribute value.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="19050-104">该属性称为 DateTime，但不支持时间值。</span><span class="sxs-lookup"><span data-stu-id="19050-104">The attribute is called DateTime, but time values are not supported.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="19050-105">先决条件</span><span class="sxs-lookup"><span data-stu-id="19050-105">Prerequisites</span></span>  
 <span data-ttu-id="19050-106">若要执行此过程：</span><span class="sxs-lookup"><span data-stu-id="19050-106">To perform this procedure:</span></span>  
  
-   <span data-ttu-id="19050-107">您必须有权访问 **“系统管理”** 功能区域。</span><span class="sxs-lookup"><span data-stu-id="19050-107">You must have permission to access the **System Administration** functional area.</span></span>  
  
-   <span data-ttu-id="19050-108">您必须是模型管理员。</span><span class="sxs-lookup"><span data-stu-id="19050-108">You must be a model administrator.</span></span> <span data-ttu-id="19050-109">有关详细信息，请参阅[管理员 &#40;Master Data Services&#41;](administrators-master-data-services.md)。</span><span class="sxs-lookup"><span data-stu-id="19050-109">For more information, see [Administrators &#40;Master Data Services&#41;](administrators-master-data-services.md).</span></span>  
  
-   <span data-ttu-id="19050-110">您必须具有要为其创建属性的实体。</span><span class="sxs-lookup"><span data-stu-id="19050-110">You must have an entity to create the attribute for.</span></span> <span data-ttu-id="19050-111">有关详细信息，请参阅[创建实体 (Master Data Services)](../../2014/master-data-services/create-an-entity-master-data-services.md)。</span><span class="sxs-lookup"><span data-stu-id="19050-111">For more information, see [Create an Entity &#40;Master Data Services&#41;](../../2014/master-data-services/create-an-entity-master-data-services.md).</span></span>  
  
### <a name="to-create-a-date-attribute"></a><span data-ttu-id="19050-112">创建日期属性</span><span class="sxs-lookup"><span data-stu-id="19050-112">To create a date attribute</span></span>  
  
1.  <span data-ttu-id="19050-113">在 [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)]中，单击 **“系统管理”**。</span><span class="sxs-lookup"><span data-stu-id="19050-113">In [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)], click **System Administration**.</span></span>  
  
2.  <span data-ttu-id="19050-114">在 **“模型视图”** 页上，从菜单栏中，指向 **“管理”** ，然后单击 **“实体”**。</span><span class="sxs-lookup"><span data-stu-id="19050-114">On the **Model View** page, from the menu bar, point to **Manage** and click **Entities**.</span></span>  
  
3.  <span data-ttu-id="19050-115">在 **“实体维护”** 页上，从 **“模型”** 列表中，选择某一模型。</span><span class="sxs-lookup"><span data-stu-id="19050-115">On the **Entity Maintenance** page, from the **Model** list, select a model.</span></span>  
  
4.  <span data-ttu-id="19050-116">为您要为其创建属性的实体选择行。</span><span class="sxs-lookup"><span data-stu-id="19050-116">Select the row for the entity that you want to create an attribute for.</span></span>  
  
5.  <span data-ttu-id="19050-117">单击 **“编辑所选实体”**。</span><span class="sxs-lookup"><span data-stu-id="19050-117">Click **Edit selected entity**.</span></span>  
  
6.  <span data-ttu-id="19050-118">在 **“编辑实体”** 页上：</span><span class="sxs-lookup"><span data-stu-id="19050-118">On the **Edit Entity** page:</span></span>  
  
    -   <span data-ttu-id="19050-119">如果属性是针对叶成员的，则在 **“叶成员属性”** 窗格中，单击 **“添加叶属性”**。</span><span class="sxs-lookup"><span data-stu-id="19050-119">If the attribute is for leaf members, in the **Leaf member attributes** pane, click **Add leaf attribute**.</span></span>  
  
    -   <span data-ttu-id="19050-120">如果属性是针对合并成员的，则在 **“合并成员属性”** 窗格中，单击 **“添加合并属性”**。</span><span class="sxs-lookup"><span data-stu-id="19050-120">If the attribute is for consolidated members, in the **Consolidated member attributes** pane, click **Add consolidated attribute**.</span></span>  
  
    -   <span data-ttu-id="19050-121">如果属性是针对集合的，则在 **“集合属性”** 窗格中，单击 **“添加集合属性”**。</span><span class="sxs-lookup"><span data-stu-id="19050-121">If the attribute is for collections, in the **Collection attributes** pane, click **Add collection attribute**.</span></span>  
  
7.  <span data-ttu-id="19050-122">在 **“添加属性”** 页上，选择 **“自由格式”** 选项。</span><span class="sxs-lookup"><span data-stu-id="19050-122">On the **Add Attribute** page, select the **Free-form** option.</span></span>  
  
8.  <span data-ttu-id="19050-123">在 **“名称”** 框中，键入属性的名称。</span><span class="sxs-lookup"><span data-stu-id="19050-123">In the **Name** box, type a name for the attribute.</span></span> <span data-ttu-id="19050-124">有关不可用作属性名称的单词列表，请参阅[保留字 (Master Data Services)](../../2014/master-data-services/reserved-words-master-data-services.md)。</span><span class="sxs-lookup"><span data-stu-id="19050-124">For a list of words that should not be used as attribute names, see [Reserved Words &#40;Master Data Services&#41;](../../2014/master-data-services/reserved-words-master-data-services.md).</span></span>  
  
9. <span data-ttu-id="19050-125">在 **“显示像素宽度”** 框中，键入要在 **“资源管理器”** 网格中显示的属性列的宽度。</span><span class="sxs-lookup"><span data-stu-id="19050-125">In the **Display pixel width** box, type the width of the attribute column to be displayed in the **Explorer** grid.</span></span>  
  
10. <span data-ttu-id="19050-126">从 **“数据类型”** 列表中，选择 **“DateTime”**。</span><span class="sxs-lookup"><span data-stu-id="19050-126">From the **Data type** list, select **DateTime**.</span></span>  
  
11. <span data-ttu-id="19050-127">从 **“输入掩码”** 列表中，选择用于日期的格式。</span><span class="sxs-lookup"><span data-stu-id="19050-127">From the **Input mask** list, select a format for dates.</span></span>  
  
12. <span data-ttu-id="19050-128">根据需要，选择 **“启用更改跟踪”** 可以跟踪对属性组的更改。</span><span class="sxs-lookup"><span data-stu-id="19050-128">Optionally, select **Enable change tracking** to track changes to groups of attributes.</span></span> <span data-ttu-id="19050-129">有关详细信息，请参阅[向更改跟踪组添加属性 (Master Data Services)](../../2014/master-data-services/add-attributes-to-a-change-tracking-group-master-data-services.md)。</span><span class="sxs-lookup"><span data-stu-id="19050-129">For more information, see [Add Attributes to a Change Tracking Group &#40;Master Data Services&#41;](../../2014/master-data-services/add-attributes-to-a-change-tracking-group-master-data-services.md).</span></span>  
  
13. <span data-ttu-id="19050-130">单击 **“保存属性”**。</span><span class="sxs-lookup"><span data-stu-id="19050-130">Click **Save attribute**.</span></span>  
  
14. <span data-ttu-id="19050-131">在 **“实体维护”** 页上，单击 **“保存实体”**。</span><span class="sxs-lookup"><span data-stu-id="19050-131">On the **Entity Maintenance** page, click **Save entity**.</span></span>  
  
## <a name="to-display-the-time-portion-of-a-datetime-value"></a><span data-ttu-id="19050-132">显示日期时间值的时间部分</span><span class="sxs-lookup"><span data-stu-id="19050-132">To display the time portion of a datetime value</span></span>  
 <span data-ttu-id="19050-133">若要使用户界面显示日期时间值的时间部分，您必须为该属性选择一个适当的输入掩码。</span><span class="sxs-lookup"><span data-stu-id="19050-133">To have the user interface display the time portion of a datetime value, you must select an appropriate input mask for the attribute.</span></span> <span data-ttu-id="19050-134">对于日期时间属性没有内置的此类掩码，但您可以添加一个新掩码以便显示时间。</span><span class="sxs-lookup"><span data-stu-id="19050-134">None of the built-in masks for Datetime attributes do this, but you can add a new mask that will allow you to display time.</span></span> <span data-ttu-id="19050-135">为此，在存储内置掩码的 MDS 数据库的 mdm.tblList 表中添加一行。</span><span class="sxs-lookup"><span data-stu-id="19050-135">To do so, add a row in the mdm.tblList table of the MDS database, where the built-in masks are stored.</span></span> <span data-ttu-id="19050-136">此行应具有以下各值：</span><span class="sxs-lookup"><span data-stu-id="19050-136">The row should have the following values:</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="19050-137">ListCode</span><span class="sxs-lookup"><span data-stu-id="19050-137">ListCode</span></span>|<span data-ttu-id="19050-138">lstInputMask</span><span class="sxs-lookup"><span data-stu-id="19050-138">lstInputMask</span></span>|  
|<span data-ttu-id="19050-139">ListName</span><span class="sxs-lookup"><span data-stu-id="19050-139">ListName</span></span>|<span data-ttu-id="19050-140">“输入掩码”</span><span class="sxs-lookup"><span data-stu-id="19050-140">Input Mask</span></span>|  
|<span data-ttu-id="19050-141">Seq</span><span class="sxs-lookup"><span data-stu-id="19050-141">Seq</span></span>|<span data-ttu-id="19050-142">19</span><span class="sxs-lookup"><span data-stu-id="19050-142">19</span></span>|  
|<span data-ttu-id="19050-143">List Option</span><span class="sxs-lookup"><span data-stu-id="19050-143">List Option</span></span>|<span data-ttu-id="19050-144">dd/MM/yyyy hh:mm:ss tt</span><span class="sxs-lookup"><span data-stu-id="19050-144">dd/MM/yyyy hh:mm:ss tt</span></span>|  
|<span data-ttu-id="19050-145">Option ID</span><span class="sxs-lookup"><span data-stu-id="19050-145">Option ID</span></span>|<span data-ttu-id="19050-146">19</span><span class="sxs-lookup"><span data-stu-id="19050-146">19</span></span>|  
|<span data-ttu-id="19050-147">IsVisible</span><span class="sxs-lookup"><span data-stu-id="19050-147">IsVisible</span></span>|<span data-ttu-id="19050-148">1</span><span class="sxs-lookup"><span data-stu-id="19050-148">1</span></span>|  
|<span data-ttu-id="19050-149">Group_ID</span><span class="sxs-lookup"><span data-stu-id="19050-149">Group_ID</span></span>|<span data-ttu-id="19050-150">3</span><span class="sxs-lookup"><span data-stu-id="19050-150">3</span></span>|  
  
 <span data-ttu-id="19050-151">在 mdm.tblList 表中输入具有上述值的行后，在“输入掩码”列表框中会提供“dd/MM/yyyy hh:mm:ss tt”掩码。</span><span class="sxs-lookup"><span data-stu-id="19050-151">After you enter a row with the above values in the mdm.tblList table, the "dd/MM/yyyy hh:mm:ss tt" mask will be available in the Input mask list box.</span></span> <span data-ttu-id="19050-152">然后，您可以选择该掩码，以便在 MDS 资源管理器中某实体的日期时间属性列中显示日期和时间。</span><span class="sxs-lookup"><span data-stu-id="19050-152">You can then select that mask to display the date and time in a datetime attribute column of an entity in the MDS Explorer.</span></span>  
  
 <span data-ttu-id="19050-153">输入掩码是一个自定义 .NET DateTime 格式字符串。</span><span class="sxs-lookup"><span data-stu-id="19050-153">The Input Mask is a custom .NET DateTime format string.</span></span> <span data-ttu-id="19050-154">有关详细信息，请参阅 [自定义日期和时间格式字符串](https://msdn.microsoft.com/library/8kb3ddd4\(v=vs.110\).aspx)</span><span class="sxs-lookup"><span data-stu-id="19050-154">For more information, see [Custom Date and Time Format Strings](https://msdn.microsoft.com/library/8kb3ddd4\(v=vs.110\).aspx)</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="19050-155">另请参阅</span><span class="sxs-lookup"><span data-stu-id="19050-155">See Also</span></span>  
 <span data-ttu-id="19050-156">[属性 &#40;Master Data Services&#41;](../../2014/master-data-services/attributes-master-data-services.md) </span><span class="sxs-lookup"><span data-stu-id="19050-156">[Attributes &#40;Master Data Services&#41;](../../2014/master-data-services/attributes-master-data-services.md) </span></span>  
 <span data-ttu-id="19050-157">[更改属性名称 &#40;Master Data Services&#41;](change-an-attribute-name-and-data-type-master-data-services.md) </span><span class="sxs-lookup"><span data-stu-id="19050-157">[Change an Attribute Name &#40;Master Data Services&#41;](change-an-attribute-name-and-data-type-master-data-services.md) </span></span>  
 <span data-ttu-id="19050-158">[创建基于域的属性 &#40;Master Data Services&#41;](../../2014/master-data-services/create-a-domain-based-attribute-master-data-services.md) </span><span class="sxs-lookup"><span data-stu-id="19050-158">[Create a Domain-Based Attribute &#40;Master Data Services&#41;](../../2014/master-data-services/create-a-domain-based-attribute-master-data-services.md) </span></span>  
 [<span data-ttu-id="19050-159">创建文件属性 (Master Data Services)</span><span class="sxs-lookup"><span data-stu-id="19050-159">Create a File Attribute &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/create-a-file-attribute-master-data-services.md)  
  
  
