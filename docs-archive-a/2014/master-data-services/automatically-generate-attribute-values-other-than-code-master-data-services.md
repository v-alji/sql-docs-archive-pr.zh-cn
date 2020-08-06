---
title: 自动生成 Code 之外的属性值 (Master Data Services) | Microsoft Docs
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
ms.assetid: b82f6f81-6e9c-4918-9ea9-4ab5f5d11b15
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 8db6c89bdce2a11a5a54ed3a763a7bc41bd7f1be
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87589747"
---
# <a name="automatically-generate-attribute-values-other-than-code-master-data-services"></a><span data-ttu-id="5ae6f-102">自动生成 Code 之外的属性值 (Master Data Services)</span><span class="sxs-lookup"><span data-stu-id="5ae6f-102">Automatically Generate Attribute Values Other Than Code (Master Data Services)</span></span>
  <span data-ttu-id="5ae6f-103">在 [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]中，当希望在每次应用业务规则时自动分配一个整数作为值时，自动为实体的属性值生成值。</span><span class="sxs-lookup"><span data-stu-id="5ae6f-103">In [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)], automatically generate values for an entity's attribute values when you want an integer to be automatically assigned as the value each time business rules are applied.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="5ae6f-104">先决条件</span><span class="sxs-lookup"><span data-stu-id="5ae6f-104">Prerequisites</span></span>  
 <span data-ttu-id="5ae6f-105">若要执行此过程：</span><span class="sxs-lookup"><span data-stu-id="5ae6f-105">To perform this procedure:</span></span>  
  
-   <span data-ttu-id="5ae6f-106">您必须有权访问 **“系统管理”** 功能区域。</span><span class="sxs-lookup"><span data-stu-id="5ae6f-106">You must have permission to access the **System Administration** functional area.</span></span>  
  
-   <span data-ttu-id="5ae6f-107">您必须是模型管理员。</span><span class="sxs-lookup"><span data-stu-id="5ae6f-107">You must be a model administrator.</span></span> <span data-ttu-id="5ae6f-108">有关详细信息，请参阅[管理员 &#40;Master Data Services&#41;](administrators-master-data-services.md)。</span><span class="sxs-lookup"><span data-stu-id="5ae6f-108">For more information, see [Administrators &#40;Master Data Services&#41;](administrators-master-data-services.md).</span></span>  
  
-   <span data-ttu-id="5ae6f-109">数值属性必须存在。</span><span class="sxs-lookup"><span data-stu-id="5ae6f-109">A numeric attribute must exist.</span></span> <span data-ttu-id="5ae6f-110">有关详细信息，请参阅[创建数字属性 (Master Data Services)](../../2014/master-data-services/create-a-numeric-attribute-master-data-services.md)。</span><span class="sxs-lookup"><span data-stu-id="5ae6f-110">For more information, see [Create a Numeric Attribute &#40;Master Data Services&#41;](../../2014/master-data-services/create-a-numeric-attribute-master-data-services.md).</span></span>  
  
### <a name="to-automatically-generate-an-attribute-value"></a><span data-ttu-id="5ae6f-111">自动生成属性值</span><span class="sxs-lookup"><span data-stu-id="5ae6f-111">To automatically generate an attribute value</span></span>  
  
1.  <span data-ttu-id="5ae6f-112">在 [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)]中，单击 **“系统管理”**。</span><span class="sxs-lookup"><span data-stu-id="5ae6f-112">In [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)], click **System Administration**.</span></span>  
  
2.  <span data-ttu-id="5ae6f-113">从菜单栏中，指向 **“管理”** ，然后单击 **“业务规则”**。</span><span class="sxs-lookup"><span data-stu-id="5ae6f-113">From the menu bar, point to **Manage** and click **Business Rules**.</span></span>  
  
3.  <span data-ttu-id="5ae6f-114">在 **“业务规则维护”** 页上，从 **“模型”** 列表中，选择某一模型。</span><span class="sxs-lookup"><span data-stu-id="5ae6f-114">On the **Business Rule Maintenance** page, from the **Model** list, select a model.</span></span>  
  
4.  <span data-ttu-id="5ae6f-115">从 **“实体”** 列表中，选择某一实体。</span><span class="sxs-lookup"><span data-stu-id="5ae6f-115">From the **Entity** list, select an entity.</span></span>  
  
5.  <span data-ttu-id="5ae6f-116">从 **“成员类型”** 列表中，为要应用于的业务规则选择成员类型。</span><span class="sxs-lookup"><span data-stu-id="5ae6f-116">From the **Member Type** list, select a type of member for the business rule to apply to.</span></span>  
  
6.  <span data-ttu-id="5ae6f-117">从 **“属性”** 列表中，保留默认值 **“全部”**。</span><span class="sxs-lookup"><span data-stu-id="5ae6f-117">From the **Attribute** list, leave the default of **All**.</span></span>  
  
7.  <span data-ttu-id="5ae6f-118">单击 **“添加业务规则”**。</span><span class="sxs-lookup"><span data-stu-id="5ae6f-118">Click **Add business rule**.</span></span>  
  
8.  <span data-ttu-id="5ae6f-119">单击 **“编辑所选业务规则”**。</span><span class="sxs-lookup"><span data-stu-id="5ae6f-119">Click **Edit selected business rule**.</span></span>  
  
9. <span data-ttu-id="5ae6f-120">在 **“组件”** 窗格中，展开 **“操作”** 节点。</span><span class="sxs-lookup"><span data-stu-id="5ae6f-120">In the **Components** pane, expand the **Actions** node.</span></span>  
  
10. <span data-ttu-id="5ae6f-121">在“默认值”节点中，单击“默认为生成的值”并将其拖到“THEN”窗格的“操作”标签\*\*\*\*\*\*\*\*\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="5ae6f-121">In the Default Value node, click **defaults to a generated value** and drag it to the **THEN** pane's **Actions** label.</span></span>  
  
11. <span data-ttu-id="5ae6f-122">在 **“属性”** 窗格中，单击要生成其值的属性并将其拖到 **“编辑操作”** 窗格的 **“选择属性”** 标签。</span><span class="sxs-lookup"><span data-stu-id="5ae6f-122">In the **Attributes** pane, click the attribute with the value you want to generated and drag it to the **Edit Action** pane's **Select attribute** label.</span></span>  
  
12. <span data-ttu-id="5ae6f-123">在 **“起始”** 和 **“增量”** 框中键入值。</span><span class="sxs-lookup"><span data-stu-id="5ae6f-123">Type a value in the **Start with** and **Increment by** boxes.</span></span> <span data-ttu-id="5ae6f-124">如果成员已存在，则将基于最大的现有值设置值。</span><span class="sxs-lookup"><span data-stu-id="5ae6f-124">If members already exist, the value will be set based on the highest existing value.</span></span> <span data-ttu-id="5ae6f-125">例如，如果最大的现有值为 299 并且将“增量”设置为“1”，则下一个成员的值将设置为 300\*\*\*\*\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="5ae6f-125">For example, if the highest existing value is 299 and you set **Increment by** to **1**, the next member's value will be set to 300.</span></span>  
  
13. <span data-ttu-id="5ae6f-126">在 **“编辑操作”** 窗格中，单击 **“保存项”**。</span><span class="sxs-lookup"><span data-stu-id="5ae6f-126">In the **Edit Action** pane, click **Save item**.</span></span>  
  
14. <span data-ttu-id="5ae6f-127">单击 **“上一步”**。</span><span class="sxs-lookup"><span data-stu-id="5ae6f-127">Click **Back**.</span></span>  
  
15. <span data-ttu-id="5ae6f-128">或者，在“业务规则维护”\*\*\*\* 页上，对于包含业务规则的行，双击“名称”\*\*\*\*、“说明”\*\*\*\* 或“通知”\*\*\*\* 列中的单元以便更新值。</span><span class="sxs-lookup"><span data-stu-id="5ae6f-128">Optionally, on the **Business Rules Maintenance** page, for the row that contains your business rule, double-click a cell in the **Name**, **Description**, or **Notification** column to update the value.</span></span>  
  
16. <span data-ttu-id="5ae6f-129">单击 **“发布业务规则”**。</span><span class="sxs-lookup"><span data-stu-id="5ae6f-129">Click **Publish business rules**.</span></span>  
  
17. <span data-ttu-id="5ae6f-130">在确认对话框中，单击 **“确定”**。</span><span class="sxs-lookup"><span data-stu-id="5ae6f-130">On the confirmation dialog box, click **OK**.</span></span> <span data-ttu-id="5ae6f-131">规则的状态将更改为 **“活动”**。</span><span class="sxs-lookup"><span data-stu-id="5ae6f-131">The rule's status changes to **Active**.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="5ae6f-132">后续步骤</span><span class="sxs-lookup"><span data-stu-id="5ae6f-132">Next Steps</span></span>  
  
-   [<span data-ttu-id="5ae6f-133">针对业务规则验证特定成员 (Master Data Services)</span><span class="sxs-lookup"><span data-stu-id="5ae6f-133">Validate Specific Members against Business Rules &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/validate-specific-members-against-business-rules-master-data-services.md)  
  
-   [<span data-ttu-id="5ae6f-134">针对业务规则验证版本 (Master Data Services)</span><span class="sxs-lookup"><span data-stu-id="5ae6f-134">Validate a Version against Business Rules &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/validate-a-version-against-business-rules-master-data-services.md)  
  
## <a name="see-also"></a><span data-ttu-id="5ae6f-135">另请参阅</span><span class="sxs-lookup"><span data-stu-id="5ae6f-135">See Also</span></span>  
 <span data-ttu-id="5ae6f-136">[自动创建代码 &#40;Master Data Services&#41;](../../2014/master-data-services/automatic-code-creation-master-data-services.md) </span><span class="sxs-lookup"><span data-stu-id="5ae6f-136">[Automatic Code Creation &#40;Master Data Services&#41;](../../2014/master-data-services/automatic-code-creation-master-data-services.md) </span></span>  
 <span data-ttu-id="5ae6f-137">[业务规则 &#40;Master Data Services&#41;](../../2014/master-data-services/business-rules-master-data-services.md) </span><span class="sxs-lookup"><span data-stu-id="5ae6f-137">[Business Rules &#40;Master Data Services&#41;](../../2014/master-data-services/business-rules-master-data-services.md) </span></span>  
 [<span data-ttu-id="5ae6f-138">验证 (Master Data Services)</span><span class="sxs-lookup"><span data-stu-id="5ae6f-138">Validation &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/validation-master-data-services.md)  
  
  
