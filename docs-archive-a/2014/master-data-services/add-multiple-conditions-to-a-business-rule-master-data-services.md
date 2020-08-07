---
title: 向业务规则添加多个条件 (Master Data Services) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
helpviewer_keywords:
- business rules [Master Data Services], multiple conditions
ms.assetid: 5f0f6958-6cf2-444b-bdcd-05b887637a0b
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: c62b8dfa4f459958d12bd384b85aa74bef382b21
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87588593"
---
# <a name="add-multiple-conditions-to-a-business-rule-master-data-services"></a><span data-ttu-id="20218-102">向业务规则添加多个条件 (Master Data Services)</span><span class="sxs-lookup"><span data-stu-id="20218-102">Add Multiple Conditions to a Business Rule (Master Data Services)</span></span>
  <span data-ttu-id="20218-103">在 [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]中，在您想要采用更复杂的规则时，可以向业务规则添加多个 **AND** 或 **OR** 条件。</span><span class="sxs-lookup"><span data-stu-id="20218-103">In [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)], add multiple **AND** or **OR** conditions to a business rule when you want a more complex rule.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="20218-104">如果您创建使用 **OR** 运算符的业务规则，则考虑为可以独立进行计算的每个条件语句都创建单独的规则。</span><span class="sxs-lookup"><span data-stu-id="20218-104">If you create a business rule that uses the **OR** operator, consider creating a separate rule for each conditional statement that can be evaluated independently.</span></span> <span data-ttu-id="20218-105">然后，您可以根据需要排除规则，提供更高的灵活性以及更便于排除故障。</span><span class="sxs-lookup"><span data-stu-id="20218-105">You can then exclude rules as needed, providing more flexibility and easier troubleshooting.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="20218-106">必备条件</span><span class="sxs-lookup"><span data-stu-id="20218-106">Prerequisites</span></span>  
 <span data-ttu-id="20218-107">若要执行此过程：</span><span class="sxs-lookup"><span data-stu-id="20218-107">To perform this procedure:</span></span>  
  
-   <span data-ttu-id="20218-108">您必须有权访问 **“系统管理”** 功能区域。</span><span class="sxs-lookup"><span data-stu-id="20218-108">You must have permission to access the **System Administration** functional area.</span></span>  
  
-   <span data-ttu-id="20218-109">您必须是模型管理员。</span><span class="sxs-lookup"><span data-stu-id="20218-109">You must be a model administrator.</span></span> <span data-ttu-id="20218-110">有关详细信息，请参阅[管理员 &#40;Master Data Services&#41;](administrators-master-data-services.md)。</span><span class="sxs-lookup"><span data-stu-id="20218-110">For more information, see [Administrators &#40;Master Data Services&#41;](administrators-master-data-services.md).</span></span>  
  
-   <span data-ttu-id="20218-111">业务规则必须存在。</span><span class="sxs-lookup"><span data-stu-id="20218-111">A business rule must exist.</span></span> <span data-ttu-id="20218-112">有关详细信息，请参阅[创建和发布业务规则 (Master Data Services)](../../2014/master-data-services/create-and-publish-a-business-rule-master-data-services.md)。</span><span class="sxs-lookup"><span data-stu-id="20218-112">For more information, see [Create and Publish a Business Rule &#40;Master Data Services&#41;](../../2014/master-data-services/create-and-publish-a-business-rule-master-data-services.md).</span></span>  
  
### <a name="to-add-multiple-conditions-to-a-business-rule"></a><span data-ttu-id="20218-113">向业务规则添加多个条件</span><span class="sxs-lookup"><span data-stu-id="20218-113">To add multiple conditions to a business rule</span></span>  
  
1.  <span data-ttu-id="20218-114">在 [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)]中，单击 **“系统管理”**。</span><span class="sxs-lookup"><span data-stu-id="20218-114">In [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)], click **System Administration**.</span></span>  
  
2.  <span data-ttu-id="20218-115">从菜单栏中，指向 **“管理”** ，然后单击 **“业务规则”**。</span><span class="sxs-lookup"><span data-stu-id="20218-115">From the menu bar, point to **Manage** and click **Business Rules**.</span></span>  
  
3.  <span data-ttu-id="20218-116">在 **“业务规则维护”** 页上，从 **“模型”** 列表中，选择某一模型。</span><span class="sxs-lookup"><span data-stu-id="20218-116">On the **Business Rule Maintenance** page, from the **Model** list, select a model.</span></span>  
  
4.  <span data-ttu-id="20218-117">从 **“实体”** 列表中，选择某一实体。</span><span class="sxs-lookup"><span data-stu-id="20218-117">From the **Entity** list, select an entity.</span></span>  
  
5.  <span data-ttu-id="20218-118">从 "**成员类型**" 列表中，选择成员的类型。</span><span class="sxs-lookup"><span data-stu-id="20218-118">From the **Member Type** list, select a type of member.</span></span>  
  
6.  <span data-ttu-id="20218-119">从 **“属性”** 列表中，选择某一属性或保持默认值 **“全部”**。</span><span class="sxs-lookup"><span data-stu-id="20218-119">From the **Attribute** list, select an attribute or leave the default of **All**.</span></span>  
  
7.  <span data-ttu-id="20218-120">单击要编辑的业务规则所对应的行。</span><span class="sxs-lookup"><span data-stu-id="20218-120">Click the row for the business rule you want to edit.</span></span>  
  
8.  <span data-ttu-id="20218-121">单击 **“编辑所选业务规则”**。</span><span class="sxs-lookup"><span data-stu-id="20218-121">Click **Edit selected business rule**.</span></span>  
  
9. <span data-ttu-id="20218-122">在 "**组件**" 窗格中，展开 "**逻辑运算符**" 节点。</span><span class="sxs-lookup"><span data-stu-id="20218-122">In the **Components** pane, expand the **Logical Operators** node.</span></span>  
  
10. <span data-ttu-id="20218-123">单击 " **AND** " 或 " **or** "，然后将其拖到 " **IF** " 窗格**和**"标签"。</span><span class="sxs-lookup"><span data-stu-id="20218-123">Click **AND** or **OR** and drag it to the **IF** pane's **AND** label.</span></span>  
  
11. <span data-ttu-id="20218-124">在 **“组件”** 窗格中，展开 **“条件”** 节点。</span><span class="sxs-lookup"><span data-stu-id="20218-124">In the **Components** pane, expand the **Conditions** node.</span></span>  
  
12. <span data-ttu-id="20218-125">单击某个条件并将其拖到 " **IF** " 窗格，将**其添加到**步骤10中的 " **and** " 或 "标签"。</span><span class="sxs-lookup"><span data-stu-id="20218-125">Click a condition and drag it to **IF** pane, to the **AND** or **OR** label from step 10.</span></span>  
  
13. <span data-ttu-id="20218-126">在 "**属性**" 窗格中，单击某个属性，然后将其拖到 "**编辑条件**" 窗格的 "**选择属性**" 标签。</span><span class="sxs-lookup"><span data-stu-id="20218-126">In the **Attributes** pane, click an attribute and drag it to the **Edit Condition** pane's **Select attribute** label.</span></span>  
  
14. <span data-ttu-id="20218-127">在 "**编辑条件**" 窗格中，填写所有必填字段。</span><span class="sxs-lookup"><span data-stu-id="20218-127">In the **Edit Condition** pane, complete any required fields.</span></span>  
  
15. <span data-ttu-id="20218-128">在 **“编辑条件”** 窗格中，单击 **“保存项”**。</span><span class="sxs-lookup"><span data-stu-id="20218-128">In the **Edit Condition** pane, click **Save item**.</span></span>  
  
16. <span data-ttu-id="20218-129">（可选）若要添加更多条件，**请在 "** **组件**" 窗格中，将 "and"**和** **"or" 拖到 any** **and**或 or in **IF**窗格中。</span><span class="sxs-lookup"><span data-stu-id="20218-129">Optionally, to add more conditions, from the **Components** pane, drag **AND** or **OR** to any **AND** or **OR** in the **IF** pane.</span></span> <span data-ttu-id="20218-130">然后执行步骤 13-15。</span><span class="sxs-lookup"><span data-stu-id="20218-130">Then follow steps 13-15.</span></span>  
  
    > [!TIP]  
    >  <span data-ttu-id="20218-131">若要删除某个条件，请单击该条件的名称，然后在 "**编辑条件**" 窗格中，单击 "**删除项**"。</span><span class="sxs-lookup"><span data-stu-id="20218-131">To delete a condition, click the name of the condition and in the **Edit Condition** pane, click **Delete item**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="20218-132">另请参阅</span><span class="sxs-lookup"><span data-stu-id="20218-132">See Also</span></span>  
 <span data-ttu-id="20218-133">[业务规则 &#40;Master Data Services&#41;](../../2014/master-data-services/business-rules-master-data-services.md) </span><span class="sxs-lookup"><span data-stu-id="20218-133">[Business Rules &#40;Master Data Services&#41;](../../2014/master-data-services/business-rules-master-data-services.md) </span></span>  
 <span data-ttu-id="20218-134">[更改业务规则名称 &#40;Master Data Services&#41;](../../2014/master-data-services/change-a-business-rule-name-master-data-services.md) </span><span class="sxs-lookup"><span data-stu-id="20218-134">[Change a Business Rule Name &#40;Master Data Services&#41;](../../2014/master-data-services/change-a-business-rule-name-master-data-services.md) </span></span>  
 [<span data-ttu-id="20218-135">配置业务规则以发送通知 (Master Data Services)</span><span class="sxs-lookup"><span data-stu-id="20218-135">Configure Business Rules to Send Notifications &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/configure-business-rules-to-send-notifications-master-data-services.md)  
  
  
