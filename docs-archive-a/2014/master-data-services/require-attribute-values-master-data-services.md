---
title: 要求属性值 (Master Data Services) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
helpviewer_keywords:
- business rules [Master Data Services], requiring attribute values
- attributes [Master Data Services], requiring values
ms.assetid: a360ef13-0c34-43b8-a87e-2f5d8732d30e
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 42b412fc42138c5e186c6c7ad42373f20e35f3cb
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87579614"
---
# <a name="require-attribute-values-master-data-services"></a><span data-ttu-id="78225-102">要求属性值 (Master Data Services)</span><span class="sxs-lookup"><span data-stu-id="78225-102">Require Attribute Values (Master Data Services)</span></span>
  <span data-ttu-id="78225-103">在 [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]中，在您想要确保主数据完整时要求属性值。</span><span class="sxs-lookup"><span data-stu-id="78225-103">In [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)], require attribute values when you want to ensure your master data is complete.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="78225-104">缺少基于域的属性值的成员不显示在基于那些关系的派生层次结构中。</span><span class="sxs-lookup"><span data-stu-id="78225-104">Members that are missing domain-based attribute values are not displayed in derived hierarchies that are based on those relationships.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="78225-105">先决条件</span><span class="sxs-lookup"><span data-stu-id="78225-105">Prerequisites</span></span>  
 <span data-ttu-id="78225-106">若要执行此过程：</span><span class="sxs-lookup"><span data-stu-id="78225-106">To perform this procedure:</span></span>  
  
-   <span data-ttu-id="78225-107">您必须有权访问 **“系统管理”** 功能区域。</span><span class="sxs-lookup"><span data-stu-id="78225-107">You must have permission to access the **System Administration** functional area.</span></span>  
  
-   <span data-ttu-id="78225-108">您必须是模型管理员。</span><span class="sxs-lookup"><span data-stu-id="78225-108">You must be a model administrator.</span></span> <span data-ttu-id="78225-109">有关详细信息，请参阅[管理员 &#40;Master Data Services&#41;](administrators-master-data-services.md)。</span><span class="sxs-lookup"><span data-stu-id="78225-109">For more information, see [Administrators &#40;Master Data Services&#41;](administrators-master-data-services.md).</span></span>  
  
### <a name="to-require-attribute-values"></a><span data-ttu-id="78225-110">要求属性值</span><span class="sxs-lookup"><span data-stu-id="78225-110">To require attribute values</span></span>  
  
1.  <span data-ttu-id="78225-111">在 [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)]中，单击 **“系统管理”**。</span><span class="sxs-lookup"><span data-stu-id="78225-111">In [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)], click **System Administration**.</span></span>  
  
2.  <span data-ttu-id="78225-112">从菜单栏中，指向 **“管理”** ，然后单击 **“业务规则”**。</span><span class="sxs-lookup"><span data-stu-id="78225-112">From the menu bar, point to **Manage** and click **Business Rules**.</span></span>  
  
3.  <span data-ttu-id="78225-113">在 **“业务规则维护”** 页上，从 **“模型”** 列表中，选择某一模型。</span><span class="sxs-lookup"><span data-stu-id="78225-113">On the **Business Rule Maintenance** page, from the **Model** list, select a model.</span></span>  
  
4.  <span data-ttu-id="78225-114">从 **“实体”** 列表中，选择某一实体。</span><span class="sxs-lookup"><span data-stu-id="78225-114">From the **Entity** list, select an entity.</span></span>  
  
5.  <span data-ttu-id="78225-115">从 **“成员类型”** 列表中，为要应用于的业务规则选择成员类型。</span><span class="sxs-lookup"><span data-stu-id="78225-115">From the **Member Type** list, select a type of member for the business rule to apply to.</span></span>  
  
6.  <span data-ttu-id="78225-116">从 **“属性”** 列表中，选择某一属性或保持默认值 **“全部”**。</span><span class="sxs-lookup"><span data-stu-id="78225-116">From the **Attribute** list, select an attribute or leave the default of **All**.</span></span>  
  
7.  <span data-ttu-id="78225-117">单击 **“添加业务规则”**。</span><span class="sxs-lookup"><span data-stu-id="78225-117">Click **Add business rule**.</span></span>  
  
8.  <span data-ttu-id="78225-118">单击 **“编辑所选业务规则”**。</span><span class="sxs-lookup"><span data-stu-id="78225-118">Click **Edit selected business rule**.</span></span>  
  
9. <span data-ttu-id="78225-119">在 **“组件”** 窗格中，展开 **“操作”** 节点。</span><span class="sxs-lookup"><span data-stu-id="78225-119">In the **Components** pane, expand the **Actions** node.</span></span>  
  
10. <span data-ttu-id="78225-120">单击 "**是必需**的，然后将其拖到" **THEN** "窗格的"**操作**"标签。</span><span class="sxs-lookup"><span data-stu-id="78225-120">Click **is required** and drag it to the **THEN** pane's **Action** label.</span></span>  
  
11. <span data-ttu-id="78225-121">在 **“属性”** 窗格中，单击某一属性并且将其拖到 **“编辑操作”** 窗格的 **“选择属性”** 标签。</span><span class="sxs-lookup"><span data-stu-id="78225-121">In the **Attributes** pane, click an attribute and drag it to the **Edit Action** pane's **Select attribute** label.</span></span>  
  
12. <span data-ttu-id="78225-122">在 **“编辑操作”** 窗格中，单击 **“保存项”**。</span><span class="sxs-lookup"><span data-stu-id="78225-122">In the **Edit Action** pane, click **Save item**.</span></span>  
  
13. <span data-ttu-id="78225-123">单击 **“上一步”**。</span><span class="sxs-lookup"><span data-stu-id="78225-123">Click **Back**.</span></span>  
  
14. <span data-ttu-id="78225-124">或者，在“业务规则维护”\*\*\*\* 页上，对于包含业务规则的行，双击“名称”\*\*\*\*、“说明”\*\*\*\* 或“通知”\*\*\*\* 列中的单元以便更新值。</span><span class="sxs-lookup"><span data-stu-id="78225-124">Optionally, on the **Business Rules Maintenance** page, for the row that contains your business rule, double-click a cell in the **Name**, **Description**, or **Notification** column to update the value.</span></span>  
  
15. <span data-ttu-id="78225-125">单击 **“发布业务规则”**。</span><span class="sxs-lookup"><span data-stu-id="78225-125">Click **Publish business rules**.</span></span>  
  
16. <span data-ttu-id="78225-126">在确认对话框中，单击 **“确定”**。</span><span class="sxs-lookup"><span data-stu-id="78225-126">On the confirmation dialog box, click **OK**.</span></span> <span data-ttu-id="78225-127">规则的状态将更改为 **“活动”**。</span><span class="sxs-lookup"><span data-stu-id="78225-127">The rule's status changes to **Active**.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="78225-128">后续步骤</span><span class="sxs-lookup"><span data-stu-id="78225-128">Next Steps</span></span>  
  
-   <span data-ttu-id="78225-129">通过以下过程之一将业务规则应用到数据：</span><span class="sxs-lookup"><span data-stu-id="78225-129">Apply business rules to data by following one of these procedures:</span></span>  
  
    -   [<span data-ttu-id="78225-130">针对业务规则验证特定成员 (Master Data Services)</span><span class="sxs-lookup"><span data-stu-id="78225-130">Validate Specific Members against Business Rules &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/validate-specific-members-against-business-rules-master-data-services.md)  
  
    -   [<span data-ttu-id="78225-131">针对业务规则验证版本 (Master Data Services)</span><span class="sxs-lookup"><span data-stu-id="78225-131">Validate a Version against Business Rules &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/validate-a-version-against-business-rules-master-data-services.md)  
  
## <a name="see-also"></a><span data-ttu-id="78225-132">另请参阅</span><span class="sxs-lookup"><span data-stu-id="78225-132">See Also</span></span>  
 <span data-ttu-id="78225-133">[业务规则 &#40;Master Data Services&#41;](../../2014/master-data-services/business-rules-master-data-services.md) </span><span class="sxs-lookup"><span data-stu-id="78225-133">[Business Rules &#40;Master Data Services&#41;](../../2014/master-data-services/business-rules-master-data-services.md) </span></span>  
 [<span data-ttu-id="78225-134">派生层次结构 (Master Data Services)</span><span class="sxs-lookup"><span data-stu-id="78225-134">Derived Hierarchies &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/derived-hierarchies-master-data-services.md)  
  
  
