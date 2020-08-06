---
title: 任务 1 (先决条件) ：删除 MDS 中的供应商数据 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-quality-services
ms.topic: conceptual
ms.assetid: 6f0a4287-7fd4-4f18-b7e4-a5191a9d4a3c
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: e78dc5ff04f95d42cf440e3f80b1b349e0315a69
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87589397"
---
# <a name="task-1-prerequisite-removing-supplier-data-in-mds"></a><span data-ttu-id="f8cb5-102">任务 1（先决条件）：删除 MDS 中的供应商数据</span><span class="sxs-lookup"><span data-stu-id="f8cb5-102">Task 1 (Prerequisite): Removing Supplier Data in MDS</span></span>
  <span data-ttu-id="f8cb5-103">在本任务中，您将删除在 MDS 中存储的供应商数据。</span><span class="sxs-lookup"><span data-stu-id="f8cb5-103">In this task, you remove the supplier data stored in MDS.</span></span> <span data-ttu-id="f8cb5-104">您在上一课中使用**MDS Excel 外接程序**手动上传了数据。</span><span class="sxs-lookup"><span data-stu-id="f8cb5-104">You uploaded the data manually using **MDS Excel Add-in** in the previous lesson.</span></span> <span data-ttu-id="f8cb5-105">您在本课中创建的 SSIS 包将自动为您将数据上载到 MDS。</span><span class="sxs-lookup"><span data-stu-id="f8cb5-105">The SSIS package you create in this lesson will automatically upload the data to MDS for you.</span></span> <span data-ttu-id="f8cb5-106">因此，在测试该 SSIS 包之前，您需要从 MDS 删除供应商数据，删除派生的层次结构，删除供应商和状态实体，并且创建不含数据的供应商实体。</span><span class="sxs-lookup"><span data-stu-id="f8cb5-106">Therefore, before testing the SSIS package, you need to remove the supplier data from MDS, remove the derived hierarchy, remove supplier and state entities, and create the supplier entity with no data.</span></span>  
  
1.  <span data-ttu-id="f8cb5-107">通过**Master Data Manager**导航到或在 `http://localhost/MDS` 配置 MDS 时指定的网站和应用程序来启动主数据管理器。</span><span class="sxs-lookup"><span data-stu-id="f8cb5-107">Launch **Master Data Manager** by navigating to `http://localhost/MDS` or the website and application you specified when configuring MDS.</span></span> <span data-ttu-id="f8cb5-108">如果保持**主数据管理器**打开状态，请单击顶部的 " **SQL Server 2012 Master Data Services** " 以切换到 "**主页**"。</span><span class="sxs-lookup"><span data-stu-id="f8cb5-108">If you kept the **Master Data Manager** open, click **SQL Server 2012 Master Data Services** at the top to switch to the **home page**.</span></span>  
  
2.  <span data-ttu-id="f8cb5-109">单击 "**管理任务**" 部分中的 "**系统管理**"。</span><span class="sxs-lookup"><span data-stu-id="f8cb5-109">Click **System Administration** in the **Administrative Tasks** section.</span></span>  
  
3.  <span data-ttu-id="f8cb5-110">将鼠标悬停在菜单上的 "**管理**" 上，然后单击 "**派生层次结构**"。</span><span class="sxs-lookup"><span data-stu-id="f8cb5-110">Hover the mouse over **Manage** on the menu and click **Derived Hierarchies**.</span></span> <span data-ttu-id="f8cb5-111">在删除**供应商**模型中的实体之前，需要删除派生层次结构**SuppliersInState** 。</span><span class="sxs-lookup"><span data-stu-id="f8cb5-111">You need to delete the derived hierarchy **SuppliersInState** before deleting the entities in the **Suppliers** model.</span></span>  
  
4.  <span data-ttu-id="f8cb5-112">从 "**派生层次结构**" 列表中选择 " **SuppliersInState** "，然后单击工具栏上的 " \*\*X (删除) \*\* " 按钮。</span><span class="sxs-lookup"><span data-stu-id="f8cb5-112">Select **SuppliersInState** from the **Derived Hierarchy** list and click **X (Delete)** button on the toolbar.</span></span>  
  
5.  <span data-ttu-id="f8cb5-113">单击 **"确定"** 以确认删除。</span><span class="sxs-lookup"><span data-stu-id="f8cb5-113">Click **OK** to confirm deletion.</span></span>  
  
6.  <span data-ttu-id="f8cb5-114">将鼠标悬停在菜单上的 "**管理**" 上，然后单击 "**实体**"。</span><span class="sxs-lookup"><span data-stu-id="f8cb5-114">Hover the mouse over **Manage** on the menu and click **Entities**.</span></span>  
  
7.  <span data-ttu-id="f8cb5-115">单击 "**供应商**"，然后单击工具栏上的 "\*\*删除 (X) \*\*按钮，以删除该实体。</span><span class="sxs-lookup"><span data-stu-id="f8cb5-115">Click **Supplier** and click **Delete (X)** button on toolbar to delete the entity.</span></span> <span data-ttu-id="f8cb5-116">在消息框中单击 **"确定"** 。</span><span class="sxs-lookup"><span data-stu-id="f8cb5-116">Click **OK** on message boxes.</span></span>  
  
8.  <span data-ttu-id="f8cb5-117">重复上述步骤以删除**状态**实体。</span><span class="sxs-lookup"><span data-stu-id="f8cb5-117">Repeat the previous step to delete **State** entity.</span></span>  
  
9. <span data-ttu-id="f8cb5-118">不要关闭**主数据管理器**。</span><span class="sxs-lookup"><span data-stu-id="f8cb5-118">Don't close **Master Data Manager**.</span></span>  
  
10. <span data-ttu-id="f8cb5-119">切换到包含**清理并 Suppliers.xls**文件打开的 Excel 窗口。</span><span class="sxs-lookup"><span data-stu-id="f8cb5-119">Switch to the Excel window that has **Cleansed and Matched Suppliers.xls** file open.</span></span> <span data-ttu-id="f8cb5-120">切换到底部的 " **Sheet1** " 选项卡。</span><span class="sxs-lookup"><span data-stu-id="f8cb5-120">Switch to the **Sheet1** tab at the bottom.</span></span>  
  
11. <span data-ttu-id="f8cb5-121">仅选择**带有标题的第一行**。</span><span class="sxs-lookup"><span data-stu-id="f8cb5-121">Select only the **first row with headers**.</span></span> <span data-ttu-id="f8cb5-122">不要选择任何其他行。</span><span class="sxs-lookup"><span data-stu-id="f8cb5-122">Don't select any other row.</span></span> <span data-ttu-id="f8cb5-123">您希望基于 Excel 列创建实体，但不希望上载任何数据。</span><span class="sxs-lookup"><span data-stu-id="f8cb5-123">You want to create the entities based on the Excel columns but don't want to upload any data.</span></span> <span data-ttu-id="f8cb5-124">因此，您仅选择第一行和标题。</span><span class="sxs-lookup"><span data-stu-id="f8cb5-124">Therefore you select only the first row with the headers.</span></span>  
  
12. <span data-ttu-id="f8cb5-125">单击菜单栏上的 "**主数据**"。</span><span class="sxs-lookup"><span data-stu-id="f8cb5-125">Click **Master Data** on the menu bar.</span></span>  
  
13. <span data-ttu-id="f8cb5-126">在功能区中单击 "**创建实体**"。</span><span class="sxs-lookup"><span data-stu-id="f8cb5-126">Click **Create Entity** from the ribbon.</span></span>  
  
14. <span data-ttu-id="f8cb5-127">在 "**管理连接**" 对话框中，如果在 "**现有连接**" 下看不到**本地 MDS 服务器**的连接，请执行以下操作：</span><span class="sxs-lookup"><span data-stu-id="f8cb5-127">In **Manage Connections** dialog box, if you do not see the connection to **local MDS server** under **Existing connections**, do the following:</span></span>  
  
    1.  <span data-ttu-id="f8cb5-128">选择 "**创建新连接**"，然后单击 "**新建**按钮"。</span><span class="sxs-lookup"><span data-stu-id="f8cb5-128">Select **Create a new connection**, and click **New** button.</span></span>  
  
    2.  <span data-ttu-id="f8cb5-129">在 "添加新连接" 对话框中，**为 "\*\*\*\*说明**" 键入 "**本地 MDS 服务器**" \*\*，并单击 \/ \*\* **"确定"** 以关闭对话框。</span><span class="sxs-lookup"><span data-stu-id="f8cb5-129">In the Add New Connection dialog box, type **Local MDS Server** for **Description** and **http:\//localhost/MDS** for **MDS server address**, and click **OK** to close the dialog box.</span></span>  
  
15. <span data-ttu-id="f8cb5-130">在 "**管理连接**" 对话框中，选择 "**本地 MDS Server** (`http://localhost/MDS`) ，然后单击"**测试**"以测试连接。</span><span class="sxs-lookup"><span data-stu-id="f8cb5-130">In **Manage Connections** dialog box, select **Local MDS Server** (`http://localhost/MDS`), click **Test** to test the connection.</span></span> <span data-ttu-id="f8cb5-131">在消息框中单击 **"确定"** 。</span><span class="sxs-lookup"><span data-stu-id="f8cb5-131">Click **OK** on the message box.</span></span>  
  
16. <span data-ttu-id="f8cb5-132">单击 "**连接**" 以连接到 MDS 服务器。</span><span class="sxs-lookup"><span data-stu-id="f8cb5-132">Click **Connect** to make a connection to the MDS server.</span></span>  
  
17. <span data-ttu-id="f8cb5-133">在 "**创建实体**" 对话框中，执行以下操作：</span><span class="sxs-lookup"><span data-stu-id="f8cb5-133">In the **Create Entity** dialog box, do the following:</span></span>  
  
    1.  <span data-ttu-id="f8cb5-134">确认 "**范围**" 设置为 " **$ 1： $ 1**"。</span><span class="sxs-lookup"><span data-stu-id="f8cb5-134">Confirm that **Range** is set to **$1:$1**.</span></span>  
  
    2.  <span data-ttu-id="f8cb5-135">选择**模型**的**供应商**。</span><span class="sxs-lookup"><span data-stu-id="f8cb5-135">Select **Suppliers** for **Model**.</span></span>  
  
    3.  <span data-ttu-id="f8cb5-136">为 "**版本**" 选择**VERSION_1** 。</span><span class="sxs-lookup"><span data-stu-id="f8cb5-136">Select **VERSION_1** for **Version**.</span></span>  
  
    4.  <span data-ttu-id="f8cb5-137">键入 "**供应商**" 作为**新的实体名称**。</span><span class="sxs-lookup"><span data-stu-id="f8cb5-137">Type **Supplier** for **New entity name**.</span></span>  
  
    5.  <span data-ttu-id="f8cb5-138">选择 "用于**代码**的**供应商**"。</span><span class="sxs-lookup"><span data-stu-id="f8cb5-138">Select **SupplierID** for **Code**.</span></span>  
  
    6.  <span data-ttu-id="f8cb5-139">选择 "**名称**" 的 "**供应商名称**"。</span><span class="sxs-lookup"><span data-stu-id="f8cb5-139">Select **Supplier Name** for **Name**.</span></span>  
  
    7.  <span data-ttu-id="f8cb5-140">单击 **"确定"** 以创建实体并关闭对话框。</span><span class="sxs-lookup"><span data-stu-id="f8cb5-140">Click **OK** to create the entity and close the dialog box.</span></span>  
  
18. <span data-ttu-id="f8cb5-141">关闭**Excel**且**不保存**文件。</span><span class="sxs-lookup"><span data-stu-id="f8cb5-141">Close **Excel** and **do not save** the file.</span></span>  
  
19. <span data-ttu-id="f8cb5-142">在**主数据管理器**中，刷新 internet 浏览器并确认列表中显示了 "**供应商**" 实体。</span><span class="sxs-lookup"><span data-stu-id="f8cb5-142">In **Master Data Manager**, refresh the internet browser and confirm that **Supplier** entity is displayed in the list.</span></span>  
  
20. <span data-ttu-id="f8cb5-143">单击顶部的**SQL Server 2012 Master Data Services**切换到 "**主页**"。</span><span class="sxs-lookup"><span data-stu-id="f8cb5-143">Switch to the **home page** by clicking **SQL Server 2012 Master Data Services** at the top.</span></span>  
  
21. <span data-ttu-id="f8cb5-144">确认为 "**模型**" 选择了 "**供应商**模型"，并为 "**版本**" 选择**VERSION_1** 。</span><span class="sxs-lookup"><span data-stu-id="f8cb5-144">Confirm that **Suppliers** model is selected for **Model** and **VERSION_1** is selected for **Version**.</span></span>  
  
22. <span data-ttu-id="f8cb5-145">单击 **“资源管理器”**。</span><span class="sxs-lookup"><span data-stu-id="f8cb5-145">Click **Explorer**.</span></span> <span data-ttu-id="f8cb5-146">请注意，将创建具有所有属性的 "**供应商**" 实体，并且**不包含任何值**。</span><span class="sxs-lookup"><span data-stu-id="f8cb5-146">Notice that the **Supplier** entity with all the attributes is created with **no values**.</span></span>  
  
## <a name="next-step"></a><span data-ttu-id="f8cb5-147">下一步</span><span class="sxs-lookup"><span data-stu-id="f8cb5-147">Next Step</span></span>  
 [<span data-ttu-id="f8cb5-148">任务 2 &#40;可选&#41;：使用主数据管理器创建 MDS 订阅视图</span><span class="sxs-lookup"><span data-stu-id="f8cb5-148">Task 2 &#40;Optional&#41;: Creating a MDS Subscription View using Master Data Manager</span></span>](../../2014/tutorials/task-2-optional-creating-a-mds-subscription-view-using-master-data-manager.md)  
  
  
