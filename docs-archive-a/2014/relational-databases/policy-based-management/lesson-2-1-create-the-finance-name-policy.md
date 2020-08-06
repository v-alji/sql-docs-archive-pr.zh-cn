---
title: 创建 Finance Name 策略 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
ms.assetid: 56b2c852-fd69-4cd2-9b5d-977467b94fd9
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 44ffff45f126d2ad9b73c5b8410b8f89ad2b0604
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87578155"
---
# <a name="create-the-finance-name-policy"></a><span data-ttu-id="1269d-102">创建 Finance Name 策略</span><span class="sxs-lookup"><span data-stu-id="1269d-102">Create the Finance Name Policy</span></span>
  <span data-ttu-id="1269d-103">在本任务中，将创建一个名为 Finance 的数据库，然后创建一个要求所有表以字母 **fintbl**开头的条件。</span><span class="sxs-lookup"><span data-stu-id="1269d-103">In this task, you will create a database named Finance, and then create a condition that requires all tables to start with the letters **fintbl**.</span></span> <span data-ttu-id="1269d-104">然后，将创建一个策略和策略类别，强制 Finance 数据库中的表执行某一命名标准。</span><span class="sxs-lookup"><span data-stu-id="1269d-104">Then, you will create a policy and policy category to enforce a naming standard for tables in the Finance database.</span></span>  
  
### <a name="to-create-the-finance-database"></a><span data-ttu-id="1269d-105">创建 Finance 数据库</span><span class="sxs-lookup"><span data-stu-id="1269d-105">To create the Finance database</span></span>  
  
1.  <span data-ttu-id="1269d-106">在 [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]中，打开查询窗口并执行以下语句：</span><span class="sxs-lookup"><span data-stu-id="1269d-106">In [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)], open a query window and execute the following statement:</span></span>  
  
    ```  
    CREATE DATABASE Finance ;  
    GO  
    ```  
  
2.  <span data-ttu-id="1269d-107">在对象资源管理器中，单击“数据库”\*\*\*\*，然后按 F5 键刷新数据库列表。</span><span class="sxs-lookup"><span data-stu-id="1269d-107">In Object Explorer, click **Databases**, and then press F5 to refresh the list of databases.</span></span>  
  
### <a name="to-create-the-finance-tables-condition"></a><span data-ttu-id="1269d-108">创建 Finance 表条件</span><span class="sxs-lookup"><span data-stu-id="1269d-108">To create the Finance Tables condition</span></span>  
  
1.  <span data-ttu-id="1269d-109">在对象资源管理器中，依次展开“管理”\*\*\*\* 和“策略管理”\*\*\*\*，右键单击“条件”\*\*\*\*，然后单击“新建条件”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="1269d-109">In Object Explorer, expand **Management**, expand **Policy Management**, right-click **Conditions**, and then click **New Condition**.</span></span>  
  
2.  <span data-ttu-id="1269d-110">在“创建新条件”\*\*\*\* 对话框的“名称”\*\*\*\* 框中，键入 **Finance Tables**。</span><span class="sxs-lookup"><span data-stu-id="1269d-110">In the **Create New Condition** dialog box, in the **Name** box, type **Finance Tables**.</span></span>  
  
3.  <span data-ttu-id="1269d-111">在“Facet”\*\*\*\* 列表中，选择“多部分名称”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="1269d-111">In the **Facet** list, select **Multipart Name**.</span></span>  
  
4.  <span data-ttu-id="1269d-112">在 "**表达式**" 区域中，在 "**字段**" 框中选择 " \*\* \@ 名称**"; 在 "**运算符**" 框中选择 "**与**"; 在 "**值**" 框中，键入 **"fintbl 开头%"** 以强制所有表名称以字母**fintbl 开头\*\*开头。</span><span class="sxs-lookup"><span data-stu-id="1269d-112">In the **Expression** area, in the **Field** box, select **\@Name**; in the **Operator** box, select **Like**; and in the **Value** box, type **'fintbl%'** to force all table names to start with the letters **fintbl**.</span></span>  
  
5.  <span data-ttu-id="1269d-113">在“说明”\*\*\*\* 页中，键入 **Finance table names must begin with fintbl**，然后单击“确定”\*\*\*\* 以创建条件。</span><span class="sxs-lookup"><span data-stu-id="1269d-113">On the **Description** page, type **Finance table names must begin with fintbl**, and then click **OK** to create the condition.</span></span>  
  
### <a name="to-create-the-finance-name-policy"></a><span data-ttu-id="1269d-114">创建 Finance Name 策略</span><span class="sxs-lookup"><span data-stu-id="1269d-114">To create the Finance Name policy</span></span>  
  
1.  <span data-ttu-id="1269d-115">在对象资源管理器中，右键单击“策略”\*\*\*\*，然后单击“新建策略”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="1269d-115">In Object Explorer, right-click **Policies**, and then click **New Policy**.</span></span>  
  
2.  <span data-ttu-id="1269d-116">在“新建新策略”\*\*\*\* 对话框的“名称”\*\*\*\* 框中，键入 **Finance Name**。</span><span class="sxs-lookup"><span data-stu-id="1269d-116">In the **Create New Policy** dialog box, in the **Name** box, type **Finance Name**.</span></span>  
  
3.  <span data-ttu-id="1269d-117">在“检查条件”\*\*\*\* 列表中，选择“Finance Tables”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="1269d-117">In the **Check condition** list, select **Finance Tables**.</span></span> <span data-ttu-id="1269d-118">它位于“多部分名称”\*\*\*\* 区域中。</span><span class="sxs-lookup"><span data-stu-id="1269d-118">This is in the **Multipart Name** area.</span></span>  
  
4.  <span data-ttu-id="1269d-119">在“针对”\*\*\*\* 区域中，将会看到可能应用了此策略的数据库对象的列表。</span><span class="sxs-lookup"><span data-stu-id="1269d-119">In the **Against** area you will see a list of the database objects that could apply this policy.</span></span> <span data-ttu-id="1269d-120">选中“每个表”\*\*\*\* 复选框。</span><span class="sxs-lookup"><span data-stu-id="1269d-120">Select the check box for **Every Table**.</span></span>  
  
5.  <span data-ttu-id="1269d-121">在“每个数据库”\*\*\*\* 区域中，展开“每个”\*\*\*\*，然后单击“新建条件”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="1269d-121">In the **Every Database** area, expand **Every**, and then click **New condition**.</span></span>  
  
6.  <span data-ttu-id="1269d-122">在“创建新条件”\*\*\*\* 对话框的“名称”\*\*\*\* 框中，键入 **Finance Database**。</span><span class="sxs-lookup"><span data-stu-id="1269d-122">In the **Create New Condition** dialog box, in the **Name** box, type **Finance Database**.</span></span>  
  
7.  <span data-ttu-id="1269d-123">在 "**表达式**" 框中，完成表达式以包含\*\* \@ Name = ' 财务 '\*\*，然后单击 **"确定**" 关闭条件页。</span><span class="sxs-lookup"><span data-stu-id="1269d-123">In the **Expression** box, complete the expression to include **\@Name = 'Finance'**, and then click **OK** to close the condition page.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="1269d-124">可能需要按 Tab 键移出“值”\*\*\*\* 框才能启用“确定”\*\*\*\* 按钮。</span><span class="sxs-lookup"><span data-stu-id="1269d-124">You might have to tab out of the **Value** box to enable the **OK** button.</span></span>  
  
8.  <span data-ttu-id="1269d-125">在“评估模式”\*\*\*\* 列表中，选择“更改时: 禁止”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="1269d-125">In the **Evaluation Mode** list, select **On change: prevent**.</span></span> <span data-ttu-id="1269d-126">这会对 Finance 数据库创建数据库触发器以强制实施策略。</span><span class="sxs-lookup"><span data-stu-id="1269d-126">This will enforce the policy by creating a database trigger on the Finance database.</span></span>  
  
9. <span data-ttu-id="1269d-127">选择“已启用”\*\*\*\* 列表。</span><span class="sxs-lookup"><span data-stu-id="1269d-127">Select the **Enabled** list.</span></span> <span data-ttu-id="1269d-128">（“已启用”\*\*\*\* 框不适用于“按需”\*\*\*\* 策略。）</span><span class="sxs-lookup"><span data-stu-id="1269d-128">(The **Enabled** box does not apply to **On demand** policies.)</span></span>  
  
10. <span data-ttu-id="1269d-129">在“服务器限制”\*\*\*\* 列表中，选择“无”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="1269d-129">In the **Server restriction** list, select **None**.</span></span>  
  
11. [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
### <a name="to-create-the-finance-policy-category"></a><span data-ttu-id="1269d-130">创建 Finance 策略类别</span><span class="sxs-lookup"><span data-stu-id="1269d-130">To create the Finance policy category</span></span>  
  
1.  <span data-ttu-id="1269d-131">在对象资源管理器中，展开“管理”\*\*\*\*，右键单击“策略管理”\*\*\*\*，然后单击“管理类别”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="1269d-131">In Object Explorer, expand **Management**, right-click **Policy Management**, and then click **Manage Categories**.</span></span>  
  
2.  <span data-ttu-id="1269d-132">在 "**管理策略类别**" 对话框中的 "**名称**" 下，键入 `Finance` 空白框，然后清除 "托管**数据库订阅**"。</span><span class="sxs-lookup"><span data-stu-id="1269d-132">In the **Manage Policy Categories** dialog box, under **Name**, type `Finance` in the blank box, and then clear **Mandate Database Subscriptions**.</span></span> <span data-ttu-id="1269d-133">“托管数据库订阅”\*\*\*\* 将强制实例中的每个数据库订阅属于该策略类别的策略。</span><span class="sxs-lookup"><span data-stu-id="1269d-133">**Mandate Database Subscriptions** will force every database in the instance to subscribe to the policies that belong to this policy category.</span></span> <span data-ttu-id="1269d-134">在本课中，只有 Finance 数据库应订阅 Finance Name 策略。</span><span class="sxs-lookup"><span data-stu-id="1269d-134">For this lesson, only the Finance database should subscribe to the Finance Name policy.</span></span>  
  
3.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
## <a name="next-task-in-lesson"></a><span data-ttu-id="1269d-135">课程中的下一个任务</span><span class="sxs-lookup"><span data-stu-id="1269d-135">Next Task in Lesson</span></span>  
 [<span data-ttu-id="1269d-136">订阅和检查 Finance Name 策略</span><span class="sxs-lookup"><span data-stu-id="1269d-136">Subscribe to and Check the Finance Name Policy</span></span>](lesson-2-2-subscribe-to-and-check-the-finance-name-policy.md)  
  
  
