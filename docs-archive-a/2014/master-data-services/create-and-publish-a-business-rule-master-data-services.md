---
title: 创建和发布业务规则 (Master Data Services) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
helpviewer_keywords:
- business rules [Master Data Services], creating
- creating business rules [Master Data Services]
ms.assetid: 6961d636-4d69-468e-81f7-8d0be6a4a039
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 4dfca5613a1f328e02b3fd2c7337885a23889207
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87589739"
---
# <a name="create-and-publish-a-business-rule-master-data-services"></a><span data-ttu-id="0cabb-102">创建和发布业务规则 (Master Data Services)</span><span class="sxs-lookup"><span data-stu-id="0cabb-102">Create and Publish a Business Rule (Master Data Services)</span></span>
  <span data-ttu-id="0cabb-103">在 [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]中，创建业务规则以便确保您的主数据的精确性。</span><span class="sxs-lookup"><span data-stu-id="0cabb-103">In [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)], create a business rule to ensure the accuracy of your master data.</span></span> <span data-ttu-id="0cabb-104">创建规则后，必须首先发布它，然后才能将该规则应用于数据。</span><span class="sxs-lookup"><span data-stu-id="0cabb-104">After you create a rule, you must publish it before you can apply it to data.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="0cabb-105">先决条件</span><span class="sxs-lookup"><span data-stu-id="0cabb-105">Prerequisites</span></span>  
 <span data-ttu-id="0cabb-106">若要执行此过程：</span><span class="sxs-lookup"><span data-stu-id="0cabb-106">To perform this procedure:</span></span>  
  
-   <span data-ttu-id="0cabb-107">您必须有权访问 **“系统管理”** 功能区域。</span><span class="sxs-lookup"><span data-stu-id="0cabb-107">You must have permission to access the **System Administration** functional area.</span></span>  
  
-   <span data-ttu-id="0cabb-108">您必须是模型管理员。</span><span class="sxs-lookup"><span data-stu-id="0cabb-108">You must be a model administrator.</span></span> <span data-ttu-id="0cabb-109">有关详细信息，请参阅[管理员 &#40;Master Data Services&#41;](administrators-master-data-services.md)。</span><span class="sxs-lookup"><span data-stu-id="0cabb-109">For more information, see [Administrators &#40;Master Data Services&#41;](administrators-master-data-services.md).</span></span>  
  
### <a name="to-create-and-publish-a-business-rule"></a><span data-ttu-id="0cabb-110">创建和发布业务规则</span><span class="sxs-lookup"><span data-stu-id="0cabb-110">To create and publish a business rule</span></span>  
  
1.  <span data-ttu-id="0cabb-111">在 [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)]中，单击 **“系统管理”**。</span><span class="sxs-lookup"><span data-stu-id="0cabb-111">In [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)], click **System Administration**.</span></span>  
  
2.  <span data-ttu-id="0cabb-112">从菜单栏中，指向 **“管理”** ，然后单击 **“业务规则”**。</span><span class="sxs-lookup"><span data-stu-id="0cabb-112">From the menu bar, point to **Manage** and click **Business Rules**.</span></span>  
  
3.  <span data-ttu-id="0cabb-113">在 **“业务规则维护”** 页上，从 **“模型”** 列表中，选择某一模型。</span><span class="sxs-lookup"><span data-stu-id="0cabb-113">On the **Business Rule Maintenance** page, from the **Model** list, select a model.</span></span>  
  
4.  <span data-ttu-id="0cabb-114">从 **“实体”** 列表中，选择某一实体。</span><span class="sxs-lookup"><span data-stu-id="0cabb-114">From the **Entity** list, select an entity.</span></span>  
  
5.  <span data-ttu-id="0cabb-115">从 **“成员类型”** 列表中，为要应用于的业务规则选择成员类型。</span><span class="sxs-lookup"><span data-stu-id="0cabb-115">From the **Member Type** list, select a type of member for the business rule to apply to.</span></span>  
  
6.  <span data-ttu-id="0cabb-116">从 **“属性”** 列表中，选择某一属性或保持默认值 **“全部”**。</span><span class="sxs-lookup"><span data-stu-id="0cabb-116">From the **Attribute** list, select an attribute or leave the default of **All**.</span></span>  
  
7.  <span data-ttu-id="0cabb-117">单击 **“添加业务规则”**。</span><span class="sxs-lookup"><span data-stu-id="0cabb-117">Click **Add business rule**.</span></span>  
  
8.  <span data-ttu-id="0cabb-118">单击 **“编辑所选业务规则”**。</span><span class="sxs-lookup"><span data-stu-id="0cabb-118">Click **Edit selected business rule**.</span></span>  
  
9. <span data-ttu-id="0cabb-119">在 **“组件”** 窗格中，展开 **“条件”** 节点。</span><span class="sxs-lookup"><span data-stu-id="0cabb-119">In the **Components** pane, expand the **Conditions** node.</span></span>  
  
10. <span data-ttu-id="0cabb-120">单击某个条件并将其拖到**IF**窗格的 "**条件**" 标签。</span><span class="sxs-lookup"><span data-stu-id="0cabb-120">Click a condition and drag it to the **IF** pane's **Conditions** label.</span></span>  
  
    > [!TIP]  
    >  <span data-ttu-id="0cabb-121">您可以通过右键单击并选择 "**删除**" 来删除业务规则中的项。</span><span class="sxs-lookup"><span data-stu-id="0cabb-121">You can delete items from your business rule by right-clicking and choosing **Delete**.</span></span>  
  
11. <span data-ttu-id="0cabb-122">在 "**属性**" 窗格中，单击某个属性，然后将其拖到 "**编辑条件**" 窗格的 "**选择属性**" 标签。</span><span class="sxs-lookup"><span data-stu-id="0cabb-122">In the **Attributes** pane, click an attribute and drag it to the **Edit Condition** pane's **Select attribute** label.</span></span>  
  
12. <span data-ttu-id="0cabb-123">在 "**编辑条件**" 窗格中，填写所有必填字段。</span><span class="sxs-lookup"><span data-stu-id="0cabb-123">In the **Edit Condition** pane, complete any required fields.</span></span>  
  
13. <span data-ttu-id="0cabb-124">在 **“编辑条件”** 窗格中，单击 **“保存项”**。</span><span class="sxs-lookup"><span data-stu-id="0cabb-124">In the **Edit Condition** pane, click **Save item**.</span></span>  
  
14. <span data-ttu-id="0cabb-125">在 **“组件”** 窗格中，展开 **“操作”** 节点。</span><span class="sxs-lookup"><span data-stu-id="0cabb-125">In the **Components** pane, expand the **Actions** node.</span></span>  
  
15. <span data-ttu-id="0cabb-126">单击某一操作，然后将其拖到 **THEN** 窗格的 **“操作”** 标签。</span><span class="sxs-lookup"><span data-stu-id="0cabb-126">Click an action and drag it to the **THEN** pane's **Action** label.</span></span>  
  
16. <span data-ttu-id="0cabb-127">在 **“属性”** 窗格中，单击某一属性并且将其拖到 **“编辑操作”** 窗格的 **“选择属性”** 标签。</span><span class="sxs-lookup"><span data-stu-id="0cabb-127">In the **Attributes** pane, click an attribute and drag it to the **Edit Action** pane's **Select attribute** label.</span></span>  
  
17. <span data-ttu-id="0cabb-128">在 **“编辑操作”** 窗格中，完成必填字段。</span><span class="sxs-lookup"><span data-stu-id="0cabb-128">In the **Edit Action** pane, complete any required fields.</span></span>  
  
18. <span data-ttu-id="0cabb-129">在 **“编辑操作”** 窗格中，单击 **“保存项”**。</span><span class="sxs-lookup"><span data-stu-id="0cabb-129">In the **Edit Action** pane, click **Save item**.</span></span>  
  
19. <span data-ttu-id="0cabb-130">也可以向规则添加多个条件。</span><span class="sxs-lookup"><span data-stu-id="0cabb-130">Optionally, add multiple conditions to the rule.</span></span> <span data-ttu-id="0cabb-131">有关详细信息，请参阅 [向业务规则添加多个条件 (Master Data Services)](../../2014/master-data-services/add-multiple-conditions-to-a-business-rule-master-data-services.md)。</span><span class="sxs-lookup"><span data-stu-id="0cabb-131">For more information, see [Add Multiple Conditions to a Business Rule &#40;Master Data Services&#41;](../../2014/master-data-services/add-multiple-conditions-to-a-business-rule-master-data-services.md).</span></span>  
  
20. <span data-ttu-id="0cabb-132">单击 **“上一步”**。</span><span class="sxs-lookup"><span data-stu-id="0cabb-132">Click **Back**.</span></span>  
  
21. <span data-ttu-id="0cabb-133">或者，在“业务规则维护”\*\*\*\* 页上，对于包含业务规则的行，双击“名称”\*\*\*\*、“说明”\*\*\*\* 或“通知”\*\*\*\* 列中的单元以便更新值。</span><span class="sxs-lookup"><span data-stu-id="0cabb-133">Optionally, on the **Business Rules Maintenance** page, for the row that contains your business rule, double-click a cell in the **Name**, **Description**, or **Notification** column to update the value.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="0cabb-134">仅针对包括验证操作的规则发送通知。</span><span class="sxs-lookup"><span data-stu-id="0cabb-134">Notifications are sent only for rules that include a validation action.</span></span>  
  
22. <span data-ttu-id="0cabb-135">单击 **“发布业务规则”**。</span><span class="sxs-lookup"><span data-stu-id="0cabb-135">Click **Publish business rules**.</span></span>  
  
23. <span data-ttu-id="0cabb-136">在确认对话框中，单击 **“确定”**。</span><span class="sxs-lookup"><span data-stu-id="0cabb-136">On the confirmation dialog box, click **OK**.</span></span> <span data-ttu-id="0cabb-137">规则的状态将更改为 **“活动”**。</span><span class="sxs-lookup"><span data-stu-id="0cabb-137">The rule's status changes to **Active**.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="0cabb-138">后续步骤</span><span class="sxs-lookup"><span data-stu-id="0cabb-138">Next Steps</span></span>  
  
-   <span data-ttu-id="0cabb-139">通过以下过程之一将业务规则应用到数据：</span><span class="sxs-lookup"><span data-stu-id="0cabb-139">Apply business rules to data by following one of these procedures:</span></span>  
  
    -   [<span data-ttu-id="0cabb-140">针对业务规则验证特定成员 (Master Data Services)</span><span class="sxs-lookup"><span data-stu-id="0cabb-140">Validate Specific Members against Business Rules &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/validate-specific-members-against-business-rules-master-data-services.md)  
  
    -   [<span data-ttu-id="0cabb-141">针对业务规则验证版本 (Master Data Services)</span><span class="sxs-lookup"><span data-stu-id="0cabb-141">Validate a Version against Business Rules &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/validate-a-version-against-business-rules-master-data-services.md)  
  
## <a name="see-also"></a><span data-ttu-id="0cabb-142">另请参阅</span><span class="sxs-lookup"><span data-stu-id="0cabb-142">See Also</span></span>  
 <span data-ttu-id="0cabb-143">[配置业务规则以发送通知 &#40;Master Data Services&#41;](../../2014/master-data-services/configure-business-rules-to-send-notifications-master-data-services.md) </span><span class="sxs-lookup"><span data-stu-id="0cabb-143">[Configure Business Rules to Send Notifications &#40;Master Data Services&#41;](../../2014/master-data-services/configure-business-rules-to-send-notifications-master-data-services.md) </span></span>  
 <span data-ttu-id="0cabb-144">[更改业务规则名称 &#40;Master Data Services&#41;](../../2014/master-data-services/change-a-business-rule-name-master-data-services.md) </span><span class="sxs-lookup"><span data-stu-id="0cabb-144">[Change a Business Rule Name &#40;Master Data Services&#41;](../../2014/master-data-services/change-a-business-rule-name-master-data-services.md) </span></span>  
 [<span data-ttu-id="0cabb-145">向业务规则添加多个条件 &#40;Master Data Services&#41;</span><span class="sxs-lookup"><span data-stu-id="0cabb-145">Add Multiple Conditions to a Business Rule &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/add-multiple-conditions-to-a-business-rule-master-data-services.md)  
  
  
