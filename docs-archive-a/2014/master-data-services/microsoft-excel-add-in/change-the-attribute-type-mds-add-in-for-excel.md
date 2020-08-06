---
title: 更改属性类型 (MDS Add-in for Excel) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
ms.assetid: 9d3001d9-8d0f-4e4a-8e04-4f666bf0df69
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: a55ca53fcf6923957e2196840aea2fb5914e1746
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87688974"
---
# <a name="change-the-attribute-type-mds-add-in-for-excel"></a><span data-ttu-id="d184e-102">更改属性类型（用于 Excel 的 MDS 外接程序）</span><span class="sxs-lookup"><span data-stu-id="d184e-102">Change the Attribute Type (MDS Add-in for Excel)</span></span>
  <span data-ttu-id="d184e-103">在 [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)][!INCLUDE[ssMDSXLS](../../includes/ssmdsxls-md.md)]中，数据类型或允许的字符数不正确时，管理员可以更改属性类型。</span><span class="sxs-lookup"><span data-stu-id="d184e-103">In the [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)][!INCLUDE[ssMDSXLS](../../includes/ssmdsxls-md.md)], administrators can change the attribute type when the data type or number of allowed characters is incorrect.</span></span>  
  
 <span data-ttu-id="d184e-104">如果要更改属性类型以创建受限制列表（基于域的属性），请参阅[创建基于域的属性（用于 Excel 的 MDS 外接程序）](create-a-domain-based-attribute-mds-add-in-for-excel.md)。</span><span class="sxs-lookup"><span data-stu-id="d184e-104">If you want to change the attribute type to create a constrained list (domain-based attribute), see [Create a Domain-based Attribute &#40;MDS Add-in for Excel&#41;](create-a-domain-based-attribute-mds-add-in-for-excel.md).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="d184e-105">不能更新“名称”\*\*\*\* 或“代码”\*\*\*\* 列的类型或长度。</span><span class="sxs-lookup"><span data-stu-id="d184e-105">You cannot update the type or length of the **Name** or **Code** columns.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="d184e-106">先决条件</span><span class="sxs-lookup"><span data-stu-id="d184e-106">Prerequisites</span></span>  
 <span data-ttu-id="d184e-107">若要执行此过程：</span><span class="sxs-lookup"><span data-stu-id="d184e-107">To perform this procedure:</span></span>  
  
-   <span data-ttu-id="d184e-108">您必须有权访问 **“系统管理”** 功能区域和 **“资源管理器”** 功能区域。</span><span class="sxs-lookup"><span data-stu-id="d184e-108">You must have permission to access the **System Administration** and **Explorer** functional areas.</span></span>  
  
-   <span data-ttu-id="d184e-109">您必须是模型管理员。</span><span class="sxs-lookup"><span data-stu-id="d184e-109">You must be a model administrator.</span></span> <span data-ttu-id="d184e-110">有关详细信息，请参阅[管理员 &#40;Master Data Services&#41;](../administrators-master-data-services.md)。</span><span class="sxs-lookup"><span data-stu-id="d184e-110">For more information, see [Administrators &#40;Master Data Services&#41;](../administrators-master-data-services.md).</span></span>  
  
-   <span data-ttu-id="d184e-111">必须存在现有的模型、实体和属性。</span><span class="sxs-lookup"><span data-stu-id="d184e-111">There must be an existing model, entity, and attribute.</span></span>  
  
### <a name="to-change-the-attribute-type"></a><span data-ttu-id="d184e-112">更改属性类型</span><span class="sxs-lookup"><span data-stu-id="d184e-112">To change the attribute type</span></span>  
  
1.  <span data-ttu-id="d184e-113">在 Excel 中，加载包含要更改的列（属性）的实体。</span><span class="sxs-lookup"><span data-stu-id="d184e-113">In Excel, load the entity that contains the column (attribute) you want to change.</span></span> <span data-ttu-id="d184e-114">有关详细信息，请参阅将[数据从 MDS 加载到 Excel](export-data-to-excel-from-master-data-services.md)中。</span><span class="sxs-lookup"><span data-stu-id="d184e-114">For more information, see [Load Data from MDS into Excel](export-data-to-excel-from-master-data-services.md).</span></span>  
  
2.  <span data-ttu-id="d184e-115">单击要更改的列中的任意单元。</span><span class="sxs-lookup"><span data-stu-id="d184e-115">Click any cell in the column you want to change.</span></span>  
  
3.  <span data-ttu-id="d184e-116">在 **“生成模型”** 组中，单击 **“特性属性”**。</span><span class="sxs-lookup"><span data-stu-id="d184e-116">In the **Build Model** group, click **Attribute Properties**.</span></span>  
  
4.  <span data-ttu-id="d184e-117">在 **“特性属性”** 对话框中，根据需要更新设置。</span><span class="sxs-lookup"><span data-stu-id="d184e-117">In the **Attribute Properties** dialog box, update settings as needed.</span></span>  
  
5.  <span data-ttu-id="d184e-118">单击“确定”  。</span><span class="sxs-lookup"><span data-stu-id="d184e-118">Click **OK**.</span></span>  
  
## <a name="what-happens-when-you-change-the-attribute-type"></a><span data-ttu-id="d184e-119">在更改属性类型时会发生什么情况？</span><span class="sxs-lookup"><span data-stu-id="d184e-119">What happens when you change the attribute type?</span></span>  
 <span data-ttu-id="d184e-120">如果属性有任何依赖项，例如属性由任何 MDS 业务规则引用或属性包含在订阅视图中，则您更改属性的数据类型时，MDS 将：</span><span class="sxs-lookup"><span data-stu-id="d184e-120">If there is any dependency on the attribute, such as the attribute is referenced by any MDS business rule or the attribute is included in a subscription view, and you change the data type of an attribute, MDS will:</span></span>  
  
-   <span data-ttu-id="d184e-121">更改属性的数据类型。</span><span class="sxs-lookup"><span data-stu-id="d184e-121">Change the data type of the attribute.</span></span>  
  
-   <span data-ttu-id="d184e-122">使用不包含任何值的后缀 "_old" 生成属性的副本。</span><span class="sxs-lookup"><span data-stu-id="d184e-122">Generate a copy of the attribute with the suffix "_old" that does not contain any value.</span></span> <span data-ttu-id="d184e-123">这称为不**推荐使用**的属性。</span><span class="sxs-lookup"><span data-stu-id="d184e-123">This is called a **deprecated** attribute.</span></span>  
  
 <span data-ttu-id="d184e-124">但是，原始属性的所有现有依赖项将指向此不推荐使用的属性，而非指向已更改的属性。</span><span class="sxs-lookup"><span data-stu-id="d184e-124">However, all the existing dependencies on the original attribute will point to the deprecated attribute, and not to the changed one.</span></span>  
  
 <span data-ttu-id="d184e-125">这表示：</span><span class="sxs-lookup"><span data-stu-id="d184e-125">This implies that:</span></span>  
  
-   <span data-ttu-id="d184e-126">您必须刷新业务规则才能指向已更改的属性，因为考虑到属性的新数据类型，逻辑可能会不一样。</span><span class="sxs-lookup"><span data-stu-id="d184e-126">You must refresh the business rules to point to the changed attribute because the logic may not be the same given the new data type of the attribute.</span></span> <span data-ttu-id="d184e-127">您将必须编辑每个受影响的规则，然后重新处理说明删除不推荐使用的属性 (_old) 中的引用的表达式，以指向已更新的属性。</span><span class="sxs-lookup"><span data-stu-id="d184e-127">You will have to edit each affected rule, and then rework the expressions to point to remove references from the deprecated attribute (_old) to point to the updated attribute.</span></span>  
  
-   <span data-ttu-id="d184e-128">你必须在 "集成管理" 选项下打开任何订阅视图，选择 "查看" 行，通过单击铅笔图标打开它进行编辑，然后单击 "**保存磁盘**" 图标以刷新视图定义。</span><span class="sxs-lookup"><span data-stu-id="d184e-128">You must open any subscription views under the Integration Management selection, select the view row, open it for editing by clicking the pencil icon, and then click the **Save disk** icon to refresh the view definition.</span></span> <span data-ttu-id="d184e-129">重新生成视图语法不需要其他更改。</span><span class="sxs-lookup"><span data-stu-id="d184e-129">No other change is needed to regenerate the view syntax.</span></span>  
  
-   <span data-ttu-id="d184e-130">包括该属性的临时表将向这些表添加一个不推荐使用的属性列，这意味着您的临时代码将受到影响。</span><span class="sxs-lookup"><span data-stu-id="d184e-130">Staging tables that include the attribute will have a deprecated attribute column added to them, which means that your staging code will be affected.</span></span> <span data-ttu-id="d184e-131">要删除此不推荐使用的属性，您可以在更新业务规则和订阅视图后进行删除。</span><span class="sxs-lookup"><span data-stu-id="d184e-131">To get rid of the deprecated attribute, you can delete it after you have updated the business rules and subscription views.</span></span>  
  
 <span data-ttu-id="d184e-132">**删除不推荐使用的属性**</span><span class="sxs-lookup"><span data-stu-id="d184e-132">**Deleting the deprecated attribute**</span></span>  
  
 <span data-ttu-id="d184e-133">在删除任何不推荐使用的属性前，您必须删除对该属性的所有引用，例如修复业务规则和重新生成订阅视图（如前所述）。</span><span class="sxs-lookup"><span data-stu-id="d184e-133">Before you delete any deprecated attribute, you must remove any references to the attribute such as fixing the business rules and regenerating subscription views as described earlier.</span></span> <span data-ttu-id="d184e-134">否则，当您尝试删除不推荐使用的属性时，将在“系统管理”网页中收到错误，指示该属性因被某对象引用而无法删除。</span><span class="sxs-lookup"><span data-stu-id="d184e-134">Otherwise, you will get an error in the System Administration web page when you attempt to delete the deprecated attribute stating that the attribute cannot be deleted because it is referenced by an object.</span></span>  
  
 <span data-ttu-id="d184e-135">若要删除属性，请参阅[删除属性 &#40;Master Data Services&#41;](../delete-an-attribute-master-data-services.md)</span><span class="sxs-lookup"><span data-stu-id="d184e-135">To delete an attribute, see [Delete an Attribute &#40;Master Data Services&#41;](../delete-an-attribute-master-data-services.md)</span></span>  
  
> [!TIP]  
>  <span data-ttu-id="d184e-136">更改具有现有数据及相关实体的 MDS 属性的数据类型会很麻烦，特别是当存在依赖于实体的已声明的业务规则或订阅视图时。</span><span class="sxs-lookup"><span data-stu-id="d184e-136">It is cumbersome to change data types for MDS attributes that have existing data and related entities, especially if there is a business rule or subscription view declared which depends on the entity.</span></span> <span data-ttu-id="d184e-137">最佳做法是从足够灵活可包含所需值的数据类型开始。</span><span class="sxs-lookup"><span data-stu-id="d184e-137">The best practice is to start with a data type that is flexible enough to hold the necessary values.</span></span> <span data-ttu-id="d184e-138">例如，字符串开始时可能会比较小，但是可能随着时间的推移需要延长，因此请考虑最坏的情况。</span><span class="sxs-lookup"><span data-stu-id="d184e-138">For example, strings may start small, but may need to be lengthened over time, so consider the worst case scenarios.</span></span> <span data-ttu-id="d184e-139">额外的文本字符串长度可能会成为负担（例如，宽 GUI 文本框很难适应屏幕），因此，请避免过长的字符串长度。</span><span class="sxs-lookup"><span data-stu-id="d184e-139">Extra text string length can be burdensome (for example, wide GUI text boxes are hard to fit on the screen), so avoid too long string length.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d184e-140">另请参阅</span><span class="sxs-lookup"><span data-stu-id="d184e-140">See Also</span></span>  
 <span data-ttu-id="d184e-141">[属性 &#40;Master Data Services&#41;](../attributes-master-data-services.md) </span><span class="sxs-lookup"><span data-stu-id="d184e-141">[Attributes &#40;Master Data Services&#41;](../attributes-master-data-services.md) </span></span>  
 [<span data-ttu-id="d184e-142">生成模型（用于 Excel 的 MDS 外接程序）</span><span class="sxs-lookup"><span data-stu-id="d184e-142">Building a Model &#40;MDS Add-in for Excel&#41;</span></span>](building-a-model-mds-add-in-for-excel.md)  
  
  
