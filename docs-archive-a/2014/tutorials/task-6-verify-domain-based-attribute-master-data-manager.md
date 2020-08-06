---
title: 任务6：使用主数据管理器来验证是否创建了基于域的属性 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-quality-services
ms.topic: conceptual
ms.assetid: 6e90517a-910c-4c33-8f11-92ac3cff4fdc
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: ea26202ca9e607058b1e385957be3ea3d04038b3
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87577127"
---
# <a name="task-6-verify-that-the-domain-based-attribute-is-created-using-master-data-manager"></a><span data-ttu-id="fa454-102">任务 6：验证基于域的属性是否使用主数据管理器进行创建</span><span class="sxs-lookup"><span data-stu-id="fa454-102">Task 6: Verify that the Domain-Based Attribute is Created using Master Data Manager</span></span>
  <span data-ttu-id="fa454-103">在本任务中，将使用“主数据管理器”\*\*\*\* 验证在 **MDS** 中创建了 **State** 实体并且 **Supplier** 实体的 **State** 属性是依赖 **State** 实体的基于域的属性。</span><span class="sxs-lookup"><span data-stu-id="fa454-103">In this task, you verify that the **State** entity is created in **MDS** and the **State** attribute of the **Supplier** entity is a domain-based attribute that depends on the **State** entity by using **Master Data Manager**.</span></span>

1.  <span data-ttu-id="fa454-104">切换到“主数据管理器”\*\*\*\* Web 应用程序。</span><span class="sxs-lookup"><span data-stu-id="fa454-104">Switch to the **Master Data Manger** web application.</span></span>

2.  <span data-ttu-id="fa454-105">单击顶部的“SQL Server 2012 Master Data Services”\*\*\*\* 以进入主页。</span><span class="sxs-lookup"><span data-stu-id="fa454-105">Click **SQL Server 2012 Master Data Services** at the top to get to the home page.</span></span>

3.  <span data-ttu-id="fa454-106">确保选择了 **Suppliers** 模型，然后单击“资源管理器”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="fa454-106">Ensure that **Suppliers** model is selected and click **Explorer**.</span></span> <span data-ttu-id="fa454-107">如果已打开“资源管理器”\*\*\*\*，则可以刷新该页。</span><span class="sxs-lookup"><span data-stu-id="fa454-107">You could refresh the page if you already had **Explorer** open.</span></span>

4.  <span data-ttu-id="fa454-108">将鼠标悬浮在菜单栏的“实体”\*\*\*\* 上，请注意现在有两个实体：**Supplier** 和 **State**。</span><span class="sxs-lookup"><span data-stu-id="fa454-108">Hover your mouse over **Entities** on the menu bar and notice that now there are two entities: **Supplier** and **State**.</span></span>

     <span data-ttu-id="fa454-109">![包含州/省和供应商的“实体”菜单](../../2014/tutorials/media/et-verifythatthedbaiscreatedusingmdm-01.jpg "包含州/省和供应商的“实体”菜单")</span><span class="sxs-lookup"><span data-stu-id="fa454-109">![Entities Menu with State and Supplier](../../2014/tutorials/media/et-verifythatthedbaiscreatedusingmdm-01.jpg "Entities Menu with State and Supplier")</span></span>

5.  <span data-ttu-id="fa454-110">如果 **State** 实体未打开，则单击该实体。</span><span class="sxs-lookup"><span data-stu-id="fa454-110">Click **State** if the entity is not open already.</span></span>

6.  <span data-ttu-id="fa454-111">从列表中选择“GA”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="fa454-111">Select **GA** from the list.</span></span>

7.  <span data-ttu-id="fa454-112">在右侧的“详细信息”\*\*\*\* 窗格\*\*\*\* 中，将右窗格中的“名称”\*\*\*\* 更改为“Georgia”\*\*\*\*，然后单击“确定”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="fa454-112">In the **Details** pane to the right, change the **Name** to **Georgia** in the **right pane**, and click **OK**.</span></span>

8.  <span data-ttu-id="fa454-113">对其他州重复前面的步骤。</span><span class="sxs-lookup"><span data-stu-id="fa454-113">Repeat the previous steps for other states.</span></span>

    |<span data-ttu-id="fa454-114">代码</span><span class="sxs-lookup"><span data-stu-id="fa454-114">Code</span></span>|<span data-ttu-id="fa454-115">名称</span><span class="sxs-lookup"><span data-stu-id="fa454-115">Name</span></span>|
    |----------|----------|
    |<span data-ttu-id="fa454-116">CA</span><span class="sxs-lookup"><span data-stu-id="fa454-116">CA</span></span>|<span data-ttu-id="fa454-117">California</span><span class="sxs-lookup"><span data-stu-id="fa454-117">California</span></span>|
    |<span data-ttu-id="fa454-118">CO</span><span class="sxs-lookup"><span data-stu-id="fa454-118">CO</span></span>|<span data-ttu-id="fa454-119">Colorado</span><span class="sxs-lookup"><span data-stu-id="fa454-119">Colorado</span></span>|
    |<span data-ttu-id="fa454-120">IL</span><span class="sxs-lookup"><span data-stu-id="fa454-120">IL</span></span>|<span data-ttu-id="fa454-121">伊利诺斯州</span><span class="sxs-lookup"><span data-stu-id="fa454-121">Illinois</span></span>|
    |<span data-ttu-id="fa454-122">DC</span><span class="sxs-lookup"><span data-stu-id="fa454-122">DC</span></span>|<span data-ttu-id="fa454-123">District of Columbia</span><span class="sxs-lookup"><span data-stu-id="fa454-123">District of Columbia</span></span>|
    |<span data-ttu-id="fa454-124">FL</span><span class="sxs-lookup"><span data-stu-id="fa454-124">FL</span></span>|<span data-ttu-id="fa454-125">Florida</span><span class="sxs-lookup"><span data-stu-id="fa454-125">Florida</span></span>|
    |<span data-ttu-id="fa454-126">AL</span><span class="sxs-lookup"><span data-stu-id="fa454-126">AL</span></span>|<span data-ttu-id="fa454-127">Alabama</span><span class="sxs-lookup"><span data-stu-id="fa454-127">Alabama</span></span>|
    |<span data-ttu-id="fa454-128">KY</span><span class="sxs-lookup"><span data-stu-id="fa454-128">KY</span></span>|<span data-ttu-id="fa454-129">Kentucky</span><span class="sxs-lookup"><span data-stu-id="fa454-129">Kentucky</span></span>|
    |<span data-ttu-id="fa454-130">MA</span><span class="sxs-lookup"><span data-stu-id="fa454-130">MA</span></span>|<span data-ttu-id="fa454-131">Massachusetts</span><span class="sxs-lookup"><span data-stu-id="fa454-131">Massachusetts</span></span>|
    |<span data-ttu-id="fa454-132">AZ</span><span class="sxs-lookup"><span data-stu-id="fa454-132">AZ</span></span>|<span data-ttu-id="fa454-133">Arizona</span><span class="sxs-lookup"><span data-stu-id="fa454-133">Arizona</span></span>|
    |<span data-ttu-id="fa454-134">MI</span><span class="sxs-lookup"><span data-stu-id="fa454-134">MI</span></span>|<span data-ttu-id="fa454-135">Michigan</span><span class="sxs-lookup"><span data-stu-id="fa454-135">Michigan</span></span>|
    |<span data-ttu-id="fa454-136">MN</span><span class="sxs-lookup"><span data-stu-id="fa454-136">MN</span></span>|<span data-ttu-id="fa454-137">Minnesota</span><span class="sxs-lookup"><span data-stu-id="fa454-137">Minnesota</span></span>|
    |<span data-ttu-id="fa454-138">NJ</span><span class="sxs-lookup"><span data-stu-id="fa454-138">NJ</span></span>|<span data-ttu-id="fa454-139">New Jersey</span><span class="sxs-lookup"><span data-stu-id="fa454-139">New Jersey</span></span>|
    |<span data-ttu-id="fa454-140">NV</span><span class="sxs-lookup"><span data-stu-id="fa454-140">NV</span></span>|<span data-ttu-id="fa454-141">Nevada</span><span class="sxs-lookup"><span data-stu-id="fa454-141">Nevada</span></span>|
    |<span data-ttu-id="fa454-142">NY</span><span class="sxs-lookup"><span data-stu-id="fa454-142">NY</span></span>|<span data-ttu-id="fa454-143">纽约</span><span class="sxs-lookup"><span data-stu-id="fa454-143">New York</span></span>|
    |<span data-ttu-id="fa454-144">OH</span><span class="sxs-lookup"><span data-stu-id="fa454-144">OH</span></span>|<span data-ttu-id="fa454-145">Ohio</span><span class="sxs-lookup"><span data-stu-id="fa454-145">Ohio</span></span>|
    |<span data-ttu-id="fa454-146">确定</span><span class="sxs-lookup"><span data-stu-id="fa454-146">OK</span></span>|<span data-ttu-id="fa454-147">Oklahoma</span><span class="sxs-lookup"><span data-stu-id="fa454-147">Oklahoma</span></span>|
    |<span data-ttu-id="fa454-148">或者</span><span class="sxs-lookup"><span data-stu-id="fa454-148">OR</span></span>|<span data-ttu-id="fa454-149">Oregon</span><span class="sxs-lookup"><span data-stu-id="fa454-149">Oregon</span></span>|
    |<span data-ttu-id="fa454-150">PA</span><span class="sxs-lookup"><span data-stu-id="fa454-150">PA</span></span>|<span data-ttu-id="fa454-151">Pennsylvania</span><span class="sxs-lookup"><span data-stu-id="fa454-151">Pennsylvania</span></span>|
    |<span data-ttu-id="fa454-152">SC</span><span class="sxs-lookup"><span data-stu-id="fa454-152">SC</span></span>|<span data-ttu-id="fa454-153">South Carolina</span><span class="sxs-lookup"><span data-stu-id="fa454-153">South Carolina</span></span>|
    |<span data-ttu-id="fa454-154">KS</span><span class="sxs-lookup"><span data-stu-id="fa454-154">KS</span></span>|<span data-ttu-id="fa454-155">Kansas</span><span class="sxs-lookup"><span data-stu-id="fa454-155">Kansas</span></span>|
    |<span data-ttu-id="fa454-156">TN</span><span class="sxs-lookup"><span data-stu-id="fa454-156">TN</span></span>|<span data-ttu-id="fa454-157">Tennessee</span><span class="sxs-lookup"><span data-stu-id="fa454-157">Tennessee</span></span>|
    |<span data-ttu-id="fa454-158">TX</span><span class="sxs-lookup"><span data-stu-id="fa454-158">TX</span></span>|<span data-ttu-id="fa454-159">Texas</span><span class="sxs-lookup"><span data-stu-id="fa454-159">Texas</span></span>|
    |<span data-ttu-id="fa454-160">UT</span><span class="sxs-lookup"><span data-stu-id="fa454-160">UT</span></span>|<span data-ttu-id="fa454-161">Utah</span><span class="sxs-lookup"><span data-stu-id="fa454-161">Utah</span></span>|
    |<span data-ttu-id="fa454-162">VA</span><span class="sxs-lookup"><span data-stu-id="fa454-162">VA</span></span>|<span data-ttu-id="fa454-163">弗吉尼亚州</span><span class="sxs-lookup"><span data-stu-id="fa454-163">Virginia</span></span>|
    |<span data-ttu-id="fa454-164">WA</span><span class="sxs-lookup"><span data-stu-id="fa454-164">WA</span></span>|<span data-ttu-id="fa454-165">Washington</span><span class="sxs-lookup"><span data-stu-id="fa454-165">Washington</span></span>|
    |<span data-ttu-id="fa454-166">WI</span><span class="sxs-lookup"><span data-stu-id="fa454-166">WI</span></span>|<span data-ttu-id="fa454-167">Wisconsin</span><span class="sxs-lookup"><span data-stu-id="fa454-167">Wisconsin</span></span>|
    |<span data-ttu-id="fa454-168">HI</span><span class="sxs-lookup"><span data-stu-id="fa454-168">HI</span></span>|<span data-ttu-id="fa454-169">Hawaii</span><span class="sxs-lookup"><span data-stu-id="fa454-169">Hawaii</span></span>|
    |<span data-ttu-id="fa454-170">MD</span><span class="sxs-lookup"><span data-stu-id="fa454-170">MD</span></span>|<span data-ttu-id="fa454-171">Maryland</span><span class="sxs-lookup"><span data-stu-id="fa454-171">Maryland</span></span>|
    |<span data-ttu-id="fa454-172">CT</span><span class="sxs-lookup"><span data-stu-id="fa454-172">CT</span></span>|<span data-ttu-id="fa454-173">Connecticut</span><span class="sxs-lookup"><span data-stu-id="fa454-173">Connecticut</span></span>|

9. <span data-ttu-id="fa454-174">选择任意州条目，然后从工具栏单击“查看事务”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="fa454-174">Select any of the state entries and click **View Transactions** from the Toolbar.</span></span> <span data-ttu-id="fa454-175">您应在事务列表中看到与刚刚进行的更新对应的事务。</span><span class="sxs-lookup"><span data-stu-id="fa454-175">You should see the transaction for the update you just made is in the list of transactions.</span></span>

10. <span data-ttu-id="fa454-176">将鼠标悬浮在“实体”\*\*\*\* 菜单上，然后单击“Supplier”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="fa454-176">Hover the mouse over **Entities** menu and click **Supplier**.</span></span>

11. <span data-ttu-id="fa454-177">现在，请注意可以使用下拉列表在“详细信息”\*\*\*\* 窗格中更改 **State** 字段的值。</span><span class="sxs-lookup"><span data-stu-id="fa454-177">Now, notice that a value for the **State** field can be changed in the **Details** pane by using the drop-down list.</span></span> <span data-ttu-id="fa454-178">还可以看到，在左侧的列表中和“详细信息”\*\*\*\* 窗格中的下拉列表中，首先显示代码，然后显示用大括号括起来的名称。</span><span class="sxs-lookup"><span data-stu-id="fa454-178">You can also see that, in the list to the left and in the drop-down list in the **Details** pane, code is displayed first and then the name in curly braces.</span></span> <span data-ttu-id="fa454-179">还可以在“详细信息”\*\*\*\* 窗格中更改任何其他值。</span><span class="sxs-lookup"><span data-stu-id="fa454-179">You can also change any other value in the **Details** pane.</span></span>

     <span data-ttu-id="fa454-180">![包含更新的代码和名称的州/省属性](../../2014/tutorials/media/et-verifythatthedbaiscreatedusingmdm-02.jpg "包含更新的代码和名称的州/省属性")</span><span class="sxs-lookup"><span data-stu-id="fa454-180">![State Attribute with Updated Code and Names](../../2014/tutorials/media/et-verifythatthedbaiscreatedusingmdm-02.jpg "State Attribute with Updated Code and Names")</span></span>

## <a name="next-step"></a><span data-ttu-id="fa454-181">下一步</span><span class="sxs-lookup"><span data-stu-id="fa454-181">Next Step</span></span>
 [<span data-ttu-id="fa454-182">任务 7：在 Excel 中查看你使用“主数据管理器”所做的更新</span><span class="sxs-lookup"><span data-stu-id="fa454-182">Task 7: Viewing Updates Made using Master Data Manager in Excel</span></span>](../../2014/tutorials/task-7-viewing-updates-made-using-master-data-manager-in-excel.md)


