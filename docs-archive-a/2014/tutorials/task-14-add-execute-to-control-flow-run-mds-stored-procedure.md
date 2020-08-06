---
title: 任务14：将执行 SQL 任务添加到控制流以运行 MDS 的存储过程 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-quality-services
ms.topic: conceptual
ms.assetid: 9a5d1b52-d505-4e6f-8a89-569329c094e2
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: da8e80b25706c40e749fc364baeb578681e76b42
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87689154"
---
# <a name="task-14-adding-execute-sql-task-to-control-flow-to-run-the-stored-procedure-for-mds"></a><span data-ttu-id="a0a74-102">任务 14：将执行 SQL 任务添加到控制流以运行 MDS 的存储过程</span><span class="sxs-lookup"><span data-stu-id="a0a74-102">Task 14: Adding Execute SQL Task to Control Flow to Run the Stored Procedure for MDS</span></span>
  <span data-ttu-id="a0a74-103">在将数据加载到 MDS 的临时表后，您运行与该表相关联的存储过程以便将数据从临时表加载到 MDS 数据库的相应表中。</span><span class="sxs-lookup"><span data-stu-id="a0a74-103">After loading data into the staging tables of MDS, you run a stored procedure associated with that table to load the data from staging into the appropriate tables in the MDS database.</span></span> <span data-ttu-id="a0a74-104">此存储过程有两个需要传递的必需参数：LogFlag 和 VersionName。</span><span class="sxs-lookup"><span data-stu-id="a0a74-104">This stored procedure has two required parameters that you need to pass: LogFlag and VersionName.</span></span> <span data-ttu-id="a0a74-105">LogFlag 指定在临时过程中是否将事务记入日志，而 VersionName 表示模型版本。</span><span class="sxs-lookup"><span data-stu-id="a0a74-105">LogFlag specifies whether transactions are logged during the staging process and VersionName represents the version of the model.</span></span> <span data-ttu-id="a0a74-106">有关更多详细信息，请参阅[分步存储过程](https://msdn.microsoft.com/library/hh231028.aspx)主题。</span><span class="sxs-lookup"><span data-stu-id="a0a74-106">See [Staged Stored Procedure](https://msdn.microsoft.com/library/hh231028.aspx) topic for more details.</span></span>

 <span data-ttu-id="a0a74-107">在本任务中，您将执行 SQL 任务添加到控制流中，以便调用该存储过程来将临时数据加载到相应 MDS 表中。</span><span class="sxs-lookup"><span data-stu-id="a0a74-107">In this task, you add the Execute SQL Task to the control flow to invoke the stored procedure to load the staged data into appropriate MDS tables.</span></span>

1.  <span data-ttu-id="a0a74-108">现在，切换到 "**控制流**" 选项卡。</span><span class="sxs-lookup"><span data-stu-id="a0a74-108">Now, switch to the **Control Flow** tab.</span></span>

2.  <span data-ttu-id="a0a74-109">将 "**执行 SQL 任务**" 从 " **SSIS 工具箱**" 拖放到 "**控制流**" 选项卡。</span><span class="sxs-lookup"><span data-stu-id="a0a74-109">Drag-drop **Execute SQL Task** from the **SSIS Toolbox** to the **Control Flow** tab.</span></span>

3.  <span data-ttu-id="a0a74-110">右键单击 "**控制流**" 选项卡中的 "**执行 SQL 任务**"，然后单击 "**重命名**"。</span><span class="sxs-lookup"><span data-stu-id="a0a74-110">Right-click **Execute SQL Task** in the **Control Flow** tab, and click **Rename**.</span></span> <span data-ttu-id="a0a74-111">键入 "**触发器存储过程" 将数据加载到 MDS 中**，然后按**enter**。</span><span class="sxs-lookup"><span data-stu-id="a0a74-111">Type **Trigger Stored Procedure to Load Data into MDS** and press **ENTER**.</span></span>

4.  <span data-ttu-id="a0a74-112">使用绿色连接器将**接收、清理、匹配和组织供应商数据**连接到**触发器存储过程以加载数据**。</span><span class="sxs-lookup"><span data-stu-id="a0a74-112">Connect **Receive, Cleanse, Match, and Curate Supplier Data** to **Trigger Stored Procedure to Load Data** using the green connector.</span></span>

     <span data-ttu-id="a0a74-113">![连接以执行 SQL 任务](../../2014/tutorials/media/et-addingesqltasktocftorunthespformds-01.jpg "连接以执行 SQL 任务")</span><span class="sxs-lookup"><span data-stu-id="a0a74-113">![Connect to Execute SQL Task](../../2014/tutorials/media/et-addingesqltasktocftorunthespformds-01.jpg "Connect to Execute SQL Task")</span></span>

5.  <span data-ttu-id="a0a74-114">使用 "**变量**" 窗口，添加两个具有以下设置的新变量。</span><span class="sxs-lookup"><span data-stu-id="a0a74-114">Using the **Variables** window, add two new variables with the following settings.</span></span> <span data-ttu-id="a0a74-115">如果看不到 "**变量**" 窗口，请单击菜单栏上的 " **SSIS** " 并单击 "**变量**"。</span><span class="sxs-lookup"><span data-stu-id="a0a74-115">If you do not see the **Variables** window, click **SSIS** on the menu bar and click **Variables**.</span></span>

    |<span data-ttu-id="a0a74-116">名称</span><span class="sxs-lookup"><span data-stu-id="a0a74-116">Name</span></span>|<span data-ttu-id="a0a74-117">数据类型</span><span class="sxs-lookup"><span data-stu-id="a0a74-117">Data Type</span></span>|<span data-ttu-id="a0a74-118">值</span><span class="sxs-lookup"><span data-stu-id="a0a74-118">Value</span></span>|
    |----------|---------------|-----------|
    |<span data-ttu-id="a0a74-119">LogFlag</span><span class="sxs-lookup"><span data-stu-id="a0a74-119">LogFlag</span></span>|<span data-ttu-id="a0a74-120">Int32</span><span class="sxs-lookup"><span data-stu-id="a0a74-120">Int32</span></span>|<span data-ttu-id="a0a74-121">1</span><span class="sxs-lookup"><span data-stu-id="a0a74-121">1</span></span>|
    |<span data-ttu-id="a0a74-122">VersionName</span><span class="sxs-lookup"><span data-stu-id="a0a74-122">VersionName</span></span>|<span data-ttu-id="a0a74-123">String</span><span class="sxs-lookup"><span data-stu-id="a0a74-123">String</span></span>|<span data-ttu-id="a0a74-124">VERSION_1</span><span class="sxs-lookup"><span data-stu-id="a0a74-124">VERSION_1</span></span>|

     <span data-ttu-id="a0a74-125">![SSIS 变量窗口](../../2014/tutorials/media/et-addingesqltasktocftorunthespformds-02.jpg "SSIS 变量窗口")</span><span class="sxs-lookup"><span data-stu-id="a0a74-125">![SSIS Variables Window](../../2014/tutorials/media/et-addingesqltasktocftorunthespformds-02.jpg "SSIS Variables Window")</span></span>

6.  <span data-ttu-id="a0a74-126">双击 "**触发器存储过程" 将数据加载到 MDS 中**。</span><span class="sxs-lookup"><span data-stu-id="a0a74-126">Double-click **Trigger Stored Procedure to Load Data into MDS**.</span></span>

7.  <span data-ttu-id="a0a74-127">在 "**执行 SQL 任务编辑器**" 对话框中，选择 " \*\* (本地) \*\* " (或 " **localhost"。MDS**) 用于**连接**。</span><span class="sxs-lookup"><span data-stu-id="a0a74-127">In the **Execute SQL Task Editor** dialog box, select **(local).MDS** (or **localhost.MDS**) for **Connection**.</span></span>

8.  <span data-ttu-id="a0a74-128">键入**EXEC [stg.<name]. [udp_Supplier_Leaf]?,?,?**</span><span class="sxs-lookup"><span data-stu-id="a0a74-128">Type **EXEC [stg].[udp_Supplier_Leaf] ?, ?, ?**</span></span> <span data-ttu-id="a0a74-129">用于**SQL 语句**。</span><span class="sxs-lookup"><span data-stu-id="a0a74-129">for **SQL Statement**.</span></span> <span data-ttu-id="a0a74-130">您可以使用 SQL Server Management Studio 确认该名称。</span><span class="sxs-lookup"><span data-stu-id="a0a74-130">You can verify the name by using SQL Server Management Studio.</span></span>

     <span data-ttu-id="a0a74-131">![“执行 SQL 编辑器”对话框 - 常规设置](../../2014/tutorials/media/et-addingesqltasktocftorunthespformds-03.jpg "“执行 SQL 编辑器”对话框 - 常规设置")</span><span class="sxs-lookup"><span data-stu-id="a0a74-131">![Execute SQL Editor Dialog Box - General Settings](../../2014/tutorials/media/et-addingesqltasktocftorunthespformds-03.jpg "Execute SQL Editor Dialog Box - General Settings")</span></span>

9. <span data-ttu-id="a0a74-132">单击左侧菜单中的 "**参数映射**"。</span><span class="sxs-lookup"><span data-stu-id="a0a74-132">Click **Parameter Mapping** from the menu on left.</span></span>

10. <span data-ttu-id="a0a74-133">在 "**参数映射**" 页中，单击 "**添加**" 以添加映射。</span><span class="sxs-lookup"><span data-stu-id="a0a74-133">In the **Parameter Mapping** page, click **Add** to add a mapping.</span></span> <span data-ttu-id="a0a74-134">最大化该窗口并且调整列大小，以便您可以正确在下拉列表中看到值。</span><span class="sxs-lookup"><span data-stu-id="a0a74-134">Maximize the window and resize columns so that you can see values in drop-down lists properly.</span></span>

11. <span data-ttu-id="a0a74-135">从 "**变量名称**" 的下拉列表中选择 " **User：： VersionName** "。</span><span class="sxs-lookup"><span data-stu-id="a0a74-135">Select **User::VersionName** from the drop-down list for the **Variable Name**.</span></span>

12. <span data-ttu-id="a0a74-136">为 "**数据类型**" 选择 " **NVARCHAR** "。</span><span class="sxs-lookup"><span data-stu-id="a0a74-136">Select **NVARCHAR** for **Data Type**.</span></span>

13. <span data-ttu-id="a0a74-137">键入**0** (零) 作为**参数名称**。</span><span class="sxs-lookup"><span data-stu-id="a0a74-137">Type **0** (zero) for **Parameter Name**.</span></span>

14. <span data-ttu-id="a0a74-138">重复执行前四个步骤以便再添加两个变量。</span><span class="sxs-lookup"><span data-stu-id="a0a74-138">Repeat the previous four steps to add two more variables.</span></span>

    |<span data-ttu-id="a0a74-139">变量名</span><span class="sxs-lookup"><span data-stu-id="a0a74-139">Variable Name</span></span>|<span data-ttu-id="a0a74-140">数据类型（重要）</span><span class="sxs-lookup"><span data-stu-id="a0a74-140">Data Type (important)</span></span>|<span data-ttu-id="a0a74-141">参数名称</span><span class="sxs-lookup"><span data-stu-id="a0a74-141">Parameter Name</span></span>|
    |-------------------|-----------------------------|--------------------|
    |<span data-ttu-id="a0a74-142">User::LogFlag</span><span class="sxs-lookup"><span data-stu-id="a0a74-142">User::LogFlag</span></span>|<span data-ttu-id="a0a74-143">LONG</span><span class="sxs-lookup"><span data-stu-id="a0a74-143">LONG</span></span>|<span data-ttu-id="a0a74-144">1</span><span class="sxs-lookup"><span data-stu-id="a0a74-144">1</span></span>|
    |<span data-ttu-id="a0a74-145">User::BatchTag</span><span class="sxs-lookup"><span data-stu-id="a0a74-145">User::BatchTag</span></span>|<span data-ttu-id="a0a74-146">NVARCHAR</span><span class="sxs-lookup"><span data-stu-id="a0a74-146">NVARCHAR</span></span>|<span data-ttu-id="a0a74-147">2</span><span class="sxs-lookup"><span data-stu-id="a0a74-147">2</span></span>|

     <span data-ttu-id="a0a74-148">![执行 SQL 任务编辑器 - 参数映射](../../2014/tutorials/media/et-addingesqltasktocftorunthespformds-04.jpg "执行 SQL 任务编辑器 - 参数映射")</span><span class="sxs-lookup"><span data-stu-id="a0a74-148">![Execute SQL Task Editor - Parameter Mapping](../../2014/tutorials/media/et-addingesqltasktocftorunthespformds-04.jpg "Execute SQL Task Editor - Parameter Mapping")</span></span>

15. <span data-ttu-id="a0a74-149">单击 **"确定"** 以关闭 "**执行 SQL 编辑器**" 对话框。</span><span class="sxs-lookup"><span data-stu-id="a0a74-149">Click **OK** to close the **Execute SQL Editor** dialog box.</span></span>

## <a name="next-step"></a><span data-ttu-id="a0a74-150">下一步</span><span class="sxs-lookup"><span data-stu-id="a0a74-150">Next Step</span></span>
 [<span data-ttu-id="a0a74-151">任务 15：生成和运行 SSIS 项目</span><span class="sxs-lookup"><span data-stu-id="a0a74-151">Task 15: Building and Running the SSIS Project</span></span>](../../2014/tutorials/task-15-building-and-running-the-ssis-project.md)


