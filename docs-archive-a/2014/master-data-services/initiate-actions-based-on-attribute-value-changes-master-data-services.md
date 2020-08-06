---
title: 基于属性值更改启动操作 (Master Data Services) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
helpviewer_keywords:
- business rules [Master Data Services], tracking attribute changes
- change tracking groups [Master Data Services], initiating actions
ms.assetid: 5e4402ce-31db-4774-a2a1-552335f87693
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 50931b9f9c4bd5d08596d485ba695143b9c6594e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87687955"
---
# <a name="initiate-actions-based-on-attribute-value-changes-master-data-services"></a><span data-ttu-id="1c376-102">基于属性值更改启动操作 (Master Data Services)</span><span class="sxs-lookup"><span data-stu-id="1c376-102">Initiate Actions Based on Attribute Value Changes (Master Data Services)</span></span>
  <span data-ttu-id="1c376-103">在 [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]中，创建业务规则以便基于对属性值的更改启动操作。</span><span class="sxs-lookup"><span data-stu-id="1c376-103">In [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)], create a business rule to initiate actions based on changes to attribute values.</span></span> <span data-ttu-id="1c376-104">例如，在某个特定的属性值发生更改时，您可能需要更改值、发送通知或启动外部工作流。</span><span class="sxs-lookup"><span data-stu-id="1c376-104">For example, when a specific attribute value changes, you may want to change a value, send a notification, or start an external workflow.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="1c376-105">先决条件</span><span class="sxs-lookup"><span data-stu-id="1c376-105">Prerequisites</span></span>  
 <span data-ttu-id="1c376-106">若要执行此过程：</span><span class="sxs-lookup"><span data-stu-id="1c376-106">To perform this procedure:</span></span>  
  
-   <span data-ttu-id="1c376-107">您必须有权访问 **“系统管理”** 功能区域。</span><span class="sxs-lookup"><span data-stu-id="1c376-107">You must have permission to access the **System Administration** functional area.</span></span>  
  
-   <span data-ttu-id="1c376-108">您必须是模型管理员。</span><span class="sxs-lookup"><span data-stu-id="1c376-108">You must be a model administrator.</span></span> <span data-ttu-id="1c376-109">有关详细信息，请参阅[管理员 &#40;Master Data Services&#41;](administrators-master-data-services.md)。</span><span class="sxs-lookup"><span data-stu-id="1c376-109">For more information, see [Administrators &#40;Master Data Services&#41;](administrators-master-data-services.md).</span></span>  
  
-   <span data-ttu-id="1c376-110">您的属性必须处于更改跟踪组中。</span><span class="sxs-lookup"><span data-stu-id="1c376-110">Your attributes must be in a change tracking group.</span></span> <span data-ttu-id="1c376-111">有关详细信息，请参阅 [向更改跟踪组添加属性 (Master Data Services)](../../2014/master-data-services/add-attributes-to-a-change-tracking-group-master-data-services.md) 。</span><span class="sxs-lookup"><span data-stu-id="1c376-111">See [Add Attributes to a Change Tracking Group &#40;Master Data Services&#41;](../../2014/master-data-services/add-attributes-to-a-change-tracking-group-master-data-services.md) for more information.</span></span>  
  
### <a name="to-create-a-business-rule-to-initiate-actions-based-on-attribute-value-changes"></a><span data-ttu-id="1c376-112">创建业务规则以便基于属性值更改启动操作</span><span class="sxs-lookup"><span data-stu-id="1c376-112">To create a business rule to initiate actions based on attribute value changes</span></span>  
  
1.  <span data-ttu-id="1c376-113">在 [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)]中，单击 **“系统管理”**。</span><span class="sxs-lookup"><span data-stu-id="1c376-113">In [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)], click **System Administration**.</span></span>  
  
2.  <span data-ttu-id="1c376-114">从菜单栏中，指向 **“管理”** ，然后单击 **“业务规则”**。</span><span class="sxs-lookup"><span data-stu-id="1c376-114">From the menu bar, point to **Manage** and click **Business Rules**.</span></span>  
  
3.  <span data-ttu-id="1c376-115">在 **“业务规则维护”** 页上，从 **“模型”** 列表中，选择某一模型。</span><span class="sxs-lookup"><span data-stu-id="1c376-115">On the **Business Rule Maintenance** page, from the **Model** list, select a model.</span></span>  
  
4.  <span data-ttu-id="1c376-116">从 **“实体”** 列表中，选择某一实体。</span><span class="sxs-lookup"><span data-stu-id="1c376-116">From the **Entity** list, select an entity.</span></span>  
  
5.  <span data-ttu-id="1c376-117">从 **“成员类型”** 列表中，为要应用于的业务规则选择成员类型。</span><span class="sxs-lookup"><span data-stu-id="1c376-117">From the **Member Type** list, select a type of member for the business rule to apply to.</span></span>  
  
6.  <span data-ttu-id="1c376-118">从 **“属性”** 列表中，选择某一属性或保持默认值 **“全部”**。</span><span class="sxs-lookup"><span data-stu-id="1c376-118">From the **Attribute** list, select an attribute or leave the default of **All**.</span></span>  
  
7.  <span data-ttu-id="1c376-119">单击 **“添加业务规则”**。</span><span class="sxs-lookup"><span data-stu-id="1c376-119">Click **Add business rule**.</span></span>  
  
8.  <span data-ttu-id="1c376-120">单击 **“编辑所选业务规则”**。</span><span class="sxs-lookup"><span data-stu-id="1c376-120">Click **Edit selected business rule**.</span></span>  
  
9. <span data-ttu-id="1c376-121">在 **“组件”** 窗格中，展开 **“条件”** 节点。</span><span class="sxs-lookup"><span data-stu-id="1c376-121">In the **Components** pane, expand the **Conditions** node.</span></span>  
  
10. <span data-ttu-id="1c376-122">在 **“值比较”** 节点下，将 **“已更改”** 拖到 **IF** 窗格的 **“条件”** 标签。</span><span class="sxs-lookup"><span data-stu-id="1c376-122">Under the **Value comparison** node, drag **has changed** to the **IF** pane's **Conditions** label.</span></span>  
  
11. <span data-ttu-id="1c376-123">在 "**属性**" 窗格中，单击某个属性，然后将其拖到 "**编辑条件**" 窗格的 "**选择属性**" 标签。</span><span class="sxs-lookup"><span data-stu-id="1c376-123">In the **Attributes** pane, click an attribute and drag it to the **Edit Condition** pane's **Select attribute** label.</span></span> <span data-ttu-id="1c376-124">此属性对规则没有影响，因此，可选择任何可用属性。</span><span class="sxs-lookup"><span data-stu-id="1c376-124">This attribute has no effect on the rule, so select any available attribute.</span></span>  
  
12. <span data-ttu-id="1c376-125">在 **“编辑条件”** 窗格的 **“更改跟踪组”** 框中，键入您作为必备组件的一部分分配的更改跟踪组的编号。</span><span class="sxs-lookup"><span data-stu-id="1c376-125">In the **Edit Condition** pane, in the **Change tracking group** box, type the number of the change tracking group that you assigned as part of the prerequisites.</span></span>  
  
13. <span data-ttu-id="1c376-126">在 **“编辑条件”** 窗格中，单击 **“保存项”**。</span><span class="sxs-lookup"><span data-stu-id="1c376-126">In the **Edit Condition** pane, click **Save item**.</span></span>  
  
14. <span data-ttu-id="1c376-127">在 **“组件”** 窗格中，展开 **“操作”** 节点。</span><span class="sxs-lookup"><span data-stu-id="1c376-127">In the **Components** pane, expand the **Actions** node.</span></span>  
  
15. <span data-ttu-id="1c376-128">单击某一操作，然后将其拖到 **THEN** 窗格的 **“操作”** 标签。</span><span class="sxs-lookup"><span data-stu-id="1c376-128">Click an action and drag it to the **THEN** pane's **Action** label.</span></span>  
  
16. <span data-ttu-id="1c376-129">在 **“属性”** 窗格中，单击某一属性并且将其拖到 **“编辑操作”** 窗格的 **“选择属性”** 标签。</span><span class="sxs-lookup"><span data-stu-id="1c376-129">In the **Attributes** pane, click an attribute and drag it to the **Edit Action** pane's **Select attribute** label.</span></span>  
  
17. <span data-ttu-id="1c376-130">在 **“编辑操作”** 窗格中，完成必填字段。</span><span class="sxs-lookup"><span data-stu-id="1c376-130">In the **Edit Action** pane, complete any required fields.</span></span>  
  
18. <span data-ttu-id="1c376-131">在 **“编辑操作”** 窗格中，单击 **“保存项”**。</span><span class="sxs-lookup"><span data-stu-id="1c376-131">In the **Edit Action** pane, click **Save item**.</span></span>  
  
19. <span data-ttu-id="1c376-132">单击 **“上一步”**。</span><span class="sxs-lookup"><span data-stu-id="1c376-132">Click **Back**.</span></span>  
  
20. <span data-ttu-id="1c376-133">或者，在“业务规则维护”\*\*\*\* 页上，对于包含业务规则的行，双击“名称”\*\*\*\*、“说明”\*\*\*\* 或“通知”\*\*\*\* 列中的单元以便更新值。</span><span class="sxs-lookup"><span data-stu-id="1c376-133">Optionally, on the **Business Rules Maintenance** page, for the row that contains your business rule, double-click a cell in the **Name**, **Description**, or **Notification** column to update the value.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="1c376-134">仅针对包括验证操作的规则发送通知。</span><span class="sxs-lookup"><span data-stu-id="1c376-134">Notifications are sent only for rules that include a validation action.</span></span>  
  
21. <span data-ttu-id="1c376-135">单击 **“发布业务规则”**。</span><span class="sxs-lookup"><span data-stu-id="1c376-135">Click **Publish business rules**.</span></span>  
  
22. <span data-ttu-id="1c376-136">在确认对话框中，单击 **“确定”**。</span><span class="sxs-lookup"><span data-stu-id="1c376-136">On the confirmation dialog box, click **OK**.</span></span> <span data-ttu-id="1c376-137">规则的状态将更改为 **“活动”**。</span><span class="sxs-lookup"><span data-stu-id="1c376-137">The rule's status changes to **Active**.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="1c376-138">后续步骤</span><span class="sxs-lookup"><span data-stu-id="1c376-138">Next Steps</span></span>  
  
-   <span data-ttu-id="1c376-139">通过以下过程之一将业务规则应用到数据：</span><span class="sxs-lookup"><span data-stu-id="1c376-139">Apply business rules to data by following one of these procedures:</span></span>  
  
    -   [<span data-ttu-id="1c376-140">针对业务规则验证特定成员 (Master Data Services)</span><span class="sxs-lookup"><span data-stu-id="1c376-140">Validate Specific Members against Business Rules &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/validate-specific-members-against-business-rules-master-data-services.md)  
  
    -   [<span data-ttu-id="1c376-141">针对业务规则验证版本 (Master Data Services)</span><span class="sxs-lookup"><span data-stu-id="1c376-141">Validate a Version against Business Rules &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/validate-a-version-against-business-rules-master-data-services.md)  
  
## <a name="see-also"></a><span data-ttu-id="1c376-142">另请参阅</span><span class="sxs-lookup"><span data-stu-id="1c376-142">See Also</span></span>  
 <span data-ttu-id="1c376-143">[将属性添加到更改跟踪组 &#40;Master Data Services&#41;](../../2014/master-data-services/add-attributes-to-a-change-tracking-group-master-data-services.md) </span><span class="sxs-lookup"><span data-stu-id="1c376-143">[Add Attributes to a Change Tracking Group &#40;Master Data Services&#41;](../../2014/master-data-services/add-attributes-to-a-change-tracking-group-master-data-services.md) </span></span>  
 [<span data-ttu-id="1c376-144">业务规则 (Master Data Services)</span><span class="sxs-lookup"><span data-stu-id="1c376-144">Business Rules &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/business-rules-master-data-services.md)  
  
  
