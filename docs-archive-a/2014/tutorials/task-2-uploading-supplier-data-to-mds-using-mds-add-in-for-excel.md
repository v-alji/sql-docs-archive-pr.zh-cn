---
title: 任务2：使用 MDS Add-in for Excel 将供应商数据上载到 MDS |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-quality-services
ms.topic: conceptual
ms.assetid: 598deb57-e0cc-4e0a-aeb1-94432c094c67
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 16c5fa9db81649b30c12fae4d2e57afa8bf094e8
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87577144"
---
# <a name="task-2-uploading-supplier-data-to-mds-using-mds-add-in-for-excel"></a><span data-ttu-id="b44b5-102">任务 2：使用用于 Excel 的 MDS 外接程序将供应商数据上传到 MDS</span><span class="sxs-lookup"><span data-stu-id="b44b5-102">Task 2: Uploading Supplier Data to MDS using MDS Add-in for Excel</span></span>
  <span data-ttu-id="b44b5-103">在此任务中，将使用**MDS Add-in for Excel**将清理和供应商数据发布到**MDS** 。</span><span class="sxs-lookup"><span data-stu-id="b44b5-103">In this task, you publish the cleansed and supplier data to **MDS** using the **MDS Add-in for Excel**.</span></span> <span data-ttu-id="b44b5-104">您在上一课中创建的**供应商**模型中创建一个名为 "**供应商**" 的实体。</span><span class="sxs-lookup"><span data-stu-id="b44b5-104">You create an entity named **Supplier** in the **Suppliers** model you created in the previous lesson.</span></span> <span data-ttu-id="b44b5-105">该实体对于 Excel 文件中的每一列具有一个属性。</span><span class="sxs-lookup"><span data-stu-id="b44b5-105">The entity will have an attribute for each column in the Excel file.</span></span> <span data-ttu-id="b44b5-106">供应商实体的代码和名称属性与 Excel 中的 "**供应商**名称" 和 "**供应商名称**" 列相对应。</span><span class="sxs-lookup"><span data-stu-id="b44b5-106">The Code and Name attributes of the Supplier entity correspond to the **SupplierID** and **Supplier Name** columns in Excel.</span></span>  
  
1.  <span data-ttu-id="b44b5-107">在**Excel**中打开**清理并匹配 Suppliers.xls** 。</span><span class="sxs-lookup"><span data-stu-id="b44b5-107">Open **Cleansed and Matched Suppliers.xls** in **Excel**.</span></span>  
  
2.  <span data-ttu-id="b44b5-108">按**CTRL + A**以选择整个数据。</span><span class="sxs-lookup"><span data-stu-id="b44b5-108">Press **CTRL+A** to select entire data.</span></span> <span data-ttu-id="b44b5-109">在电子表格中选择整个数据很**重要**。</span><span class="sxs-lookup"><span data-stu-id="b44b5-109">It is **important** that you select the entire data in the spreadsheet.</span></span>  
  
3.  <span data-ttu-id="b44b5-110">单击菜单栏上的 "**主数据**"。</span><span class="sxs-lookup"><span data-stu-id="b44b5-110">Click **Master Data** on the menu bar.</span></span>  
  
4.  <span data-ttu-id="b44b5-111">单击功能区上的 "**创建实体**" 按钮。</span><span class="sxs-lookup"><span data-stu-id="b44b5-111">Click **Create Entity** button on the ribbon.</span></span>  
  
     <span data-ttu-id="b44b5-112">![Excel -“主数据”选项卡 -“创建实体”按钮](../../2014/tutorials/media/et-ulingsdtomdsusingmdsaddinforexcel-01.jpg "Excel -“主数据”选项卡 -“创建实体”按钮")</span><span class="sxs-lookup"><span data-stu-id="b44b5-112">![Excel - Master Data Tab - Create Entity Button](../../2014/tutorials/media/et-ulingsdtomdsusingmdsaddinforexcel-01.jpg "Excel - Master Data Tab - Create Entity Button")</span></span>  
  
5.  <span data-ttu-id="b44b5-113">在 "**管理连接**" 对话框中，如果在 "**现有连接**" 下看不到**本地 MDS 服务器**的连接，请执行以下操作：</span><span class="sxs-lookup"><span data-stu-id="b44b5-113">In **Manage Connections** dialog box, if you do not see the connection to **local MDS server** under **Existing connections**, do the following:</span></span>  
  
    1.  <span data-ttu-id="b44b5-114">选择 "**创建新连接**"，然后单击 "**新建**按钮"。</span><span class="sxs-lookup"><span data-stu-id="b44b5-114">Select **Create a new connection**, and click **New** button.</span></span>  
  
    2.  <span data-ttu-id="b44b5-115">在 "**添加新连接**" 对话框中，**为 "\*\*\*\*说明**" 键入 "**本地 MDS 服务器**" \*\*，并单击 \/ \*\* **"确定"** 以关闭对话框。</span><span class="sxs-lookup"><span data-stu-id="b44b5-115">In the **Add New Connection** dialog box, type **Local MDS Server** for **Description** and **http:\//localhost/MDS** for **MDS server address**, and click **OK** to close the dialog box.</span></span>  
  
6.  <span data-ttu-id="b44b5-116">在 "**管理连接**" 对话框中，选择 "**本地 MDS Server** (`http://localhost/MDS`) ，然后单击"**测试**"以测试连接。</span><span class="sxs-lookup"><span data-stu-id="b44b5-116">In **Manage Connections** dialog box, select **Local MDS Server** (`http://localhost/MDS`), click **Test** to test the connection.</span></span> <span data-ttu-id="b44b5-117">在消息框中单击 **"确定"** 。</span><span class="sxs-lookup"><span data-stu-id="b44b5-117">Click **OK** on the message box.</span></span>  
  
7.  <span data-ttu-id="b44b5-118">单击 "**连接**" 以连接到 MDS 服务器。</span><span class="sxs-lookup"><span data-stu-id="b44b5-118">Click **Connect** to connect to the MDS server.</span></span>  
  
8.  <span data-ttu-id="b44b5-119">在 "**创建实体**" 对话框中，选择**模型**的 "**供应商**"。</span><span class="sxs-lookup"><span data-stu-id="b44b5-119">In the **Create Entity** dialog box, select **Suppliers** for the **Model**.</span></span>  
  
9. <span data-ttu-id="b44b5-120">确保为 "**版本**" 选择**VERSION_1** 。</span><span class="sxs-lookup"><span data-stu-id="b44b5-120">Ensure that **VERSION_1** is selected for **Version**.</span></span>  
  
10. <span data-ttu-id="b44b5-121">为 "**新实体名称**" 输入 "**供应商**"。</span><span class="sxs-lookup"><span data-stu-id="b44b5-121">Enter **Supplier** for **New entity name**.</span></span>  
  
11. <span data-ttu-id="b44b5-122">为**包含唯一标识符**字段的列选择 "**供应商**" (您还可以) 自动生成代码。</span><span class="sxs-lookup"><span data-stu-id="b44b5-122">Select **SupplierID** for **the column that contains a unique identifier** field (you can also generate a code automatically).</span></span> <span data-ttu-id="b44b5-123">你实质上是将**Excel**中的 "**供应商**" 列映射到**供应商**实体的 "**代码**" 属性。</span><span class="sxs-lookup"><span data-stu-id="b44b5-123">You are essentially mapping the **SupplierID** column in **Excel** to the **Code** attribute of **Supplier** entity.</span></span>  
  
12. <span data-ttu-id="b44b5-124">为**包含 "名称"** 字段的列选择 "**供应商名称**"。</span><span class="sxs-lookup"><span data-stu-id="b44b5-124">Select **Supplier Name** for **the column that contains names** field.</span></span> <span data-ttu-id="b44b5-125">你实质上是将**Excel**中的 "**供应商名称**" 列映射到**供应商**实体的**name**属性。</span><span class="sxs-lookup"><span data-stu-id="b44b5-125">You are essentially mapping the **Supplier Name** column in **Excel** to the **Name** attribute of the **Supplier** entity.</span></span> <span data-ttu-id="b44b5-126">在 MDS 中，**代码**和**名称**属性是实体的必需属性。</span><span class="sxs-lookup"><span data-stu-id="b44b5-126">The **Code** and **Name** attributes are mandatory attributes for an entity in MDS.</span></span>  
  
     <span data-ttu-id="b44b5-127">![“创建实体”对话框](../../2014/tutorials/media/et-ulingsdtomdsusingmdsaddinforexcel-02.jpg "“创建实体”对话框")</span><span class="sxs-lookup"><span data-stu-id="b44b5-127">![Create Entity Dialog Box](../../2014/tutorials/media/et-ulingsdtomdsusingmdsaddinforexcel-02.jpg "Create Entity Dialog Box")</span></span>  
  
13. <span data-ttu-id="b44b5-128">单击 **"确定"** 以在 MDS 上创建实体，将主数据发布到实体，并关闭 "**创建实体**" 对话框。</span><span class="sxs-lookup"><span data-stu-id="b44b5-128">Click **OK** to create the entity on MDS, publish the master data to the entity, and close **Create Entity** dialog box.</span></span>  
  
14. <span data-ttu-id="b44b5-129">现在，你应该会看到一个名为 "**供应商**" 的新工作表，该工作表是实体的名称，添加到 Excel 电子表格，然后在工作表的顶部，你应看到该工作表已连接到 MDS 服务器。</span><span class="sxs-lookup"><span data-stu-id="b44b5-129">Now, you should see a new sheet titled **Supplier**, which is the name of the entity, added to your Excel spreadsheet and at the top of the worksheet you should see that the worksheet is connected to the MDS server.</span></span> <span data-ttu-id="b44b5-130">请注意， (标题为**Sheet1**) 的原始工作表仍然存在。</span><span class="sxs-lookup"><span data-stu-id="b44b5-130">Notice that the original worksheet (titled **Sheet1**) still exists.</span></span>  
  
     <span data-ttu-id="b44b5-131">![Excel -“供应商”和“Sheet1”选项卡](../../2014/tutorials/media/et-ulingsdtomdsusingmdsaddinforexcel-03.jpg "Excel -“供应商”和“Sheet1”选项卡")</span><span class="sxs-lookup"><span data-stu-id="b44b5-131">![Excel - Supplier and Sheet1 Tabs](../../2014/tutorials/media/et-ulingsdtomdsusingmdsaddinforexcel-03.jpg "Excel - Supplier and Sheet1 Tabs")</span></span>  
  
     <span data-ttu-id="b44b5-132">![Excel - 显示 MDS 连接详细信息](../../2014/tutorials/media/et-ulingsdtomdsusingmdsaddinforexcel-04.jpg "Excel - 显示 MDS 连接详细信息")</span><span class="sxs-lookup"><span data-stu-id="b44b5-132">![Excel - Showing MDS Connection Details](../../2014/tutorials/media/et-ulingsdtomdsusingmdsaddinforexcel-04.jpg "Excel - Showing MDS Connection Details")</span></span>  
  
15. <span data-ttu-id="b44b5-133">使**Excel**保持打开状态。</span><span class="sxs-lookup"><span data-stu-id="b44b5-133">Keep **Excel** open.</span></span>  
  
## <a name="next-task"></a><span data-ttu-id="b44b5-134">下一个任务</span><span class="sxs-lookup"><span data-stu-id="b44b5-134">Next Task</span></span>  
 [<span data-ttu-id="b44b5-135">任务 3：在主数据管理器中验证数据</span><span class="sxs-lookup"><span data-stu-id="b44b5-135">Task 3: Verifying the Data in Master Data Manager</span></span>](../../2014/tutorials/task-3-verifying-the-data-in-master-data-manager.md)  
  
  
