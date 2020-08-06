---
title: 任务 4 (可选) ：合并、匹配和发布新的数据集 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-quality-services
ms.topic: conceptual
ms.assetid: 13a13f03-b307-4555-8e33-6d98c459d994
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 9ddcec19fa8b957bf77b6ea5269b4d033779bdf1
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87577938"
---
# <a name="task-4-optional-combining-matching-and-publishing-new-set-of-data"></a><span data-ttu-id="b6a4e-102">任务 4（可选）：组合、匹配和发布新数据集</span><span class="sxs-lookup"><span data-stu-id="b6a4e-102">Task 4 (Optional): Combining, Matching, and Publishing New Set of Data</span></span>
  <span data-ttu-id="b6a4e-103">随着时间的推移，您将会想要向 MDS 存储库中添加更多的数据。</span><span class="sxs-lookup"><span data-stu-id="b6a4e-103">Over time, you will want to add more data to the MDS repository.</span></span> <span data-ttu-id="b6a4e-104">在添加数据前，将新数据与已在 MDS 中进行管理的数据进行比较可能会很有用，以确保不会添加重复数据或不准确的数据。</span><span class="sxs-lookup"><span data-stu-id="b6a4e-104">Before adding data, it can be useful to compare the new data to the data that's already managed in MDS, to ensure that you are not adding duplicate or inaccurate data.</span></span> <span data-ttu-id="b6a4e-105">在用于 Excel 的 Master Data Services 外接程序中，您可以合并两个工作表的数据并比较数据以在将数据发布到 MDS 前识别并删除重复项。</span><span class="sxs-lookup"><span data-stu-id="b6a4e-105">In the Master Data Services Add-in for Excel, you can combine data from two worksheets and the compare the data to identify and remove duplicates before publishing the data to MDS.</span></span> <span data-ttu-id="b6a4e-106">MDS Excel 外接程序的匹配功能使用 DQS 匹配功能来识别数据中的匹配项。</span><span class="sxs-lookup"><span data-stu-id="b6a4e-106">The matching feature of MDS Excel Add-in uses the DQS matching functionality to identify matches in the data.</span></span> <span data-ttu-id="b6a4e-107">在本任务中，您将两个工作表中的数据合并到一个工作表中，然后执行匹配活动以在发布到 MDS 前识别并删除重复项。</span><span class="sxs-lookup"><span data-stu-id="b6a4e-107">In this task, you will combine data from a two worksheets into one and then perform the matching activity to identify and remove duplicates before publishing to MDS.</span></span> <span data-ttu-id="b6a4e-108">有关更多详细信息，请参阅[MDS Add-in for Excel 中的数据质量匹配](https://msdn.microsoft.com/library/hh548681.aspx)和[组合数据](https://msdn.microsoft.com/library/hh548680.aspx)主题。</span><span class="sxs-lookup"><span data-stu-id="b6a4e-108">See [Data Quality Matching in the MDS Add-in for Excel](https://msdn.microsoft.com/library/hh548681.aspx) and [Combine Data](https://msdn.microsoft.com/library/hh548680.aspx) topics for more details.</span></span>  
  
1.  <span data-ttu-id="b6a4e-109">启动**Excel**的新实例。</span><span class="sxs-lookup"><span data-stu-id="b6a4e-109">Launch new instance of **Excel**.</span></span> <span data-ttu-id="b6a4e-110">单击 "**开始**"，指向 "**运行**"，键入**Excel**，然后单击 **"确定"**。</span><span class="sxs-lookup"><span data-stu-id="b6a4e-110">Click **Start**, point to **Run**, type **Excel**, and click **OK**.</span></span>  
  
2.  <span data-ttu-id="b6a4e-111">通过单击菜单栏上的 "**主数据**" 切换到 "**主数据**" 选项卡。</span><span class="sxs-lookup"><span data-stu-id="b6a4e-111">Switch to the **Master Data** tab by clicking **Master Data** on the menu bar.</span></span>  
  
3.  <span data-ttu-id="b6a4e-112">单击**连接和加载**组中的功能区上的 "**连接**" 以连接到**MDS 服务器**。</span><span class="sxs-lookup"><span data-stu-id="b6a4e-112">Click **Connect** on the ribbon in the **Connect and Load** group to connect to the **MDS server**.</span></span> <span data-ttu-id="b6a4e-113">您在本课前面已配置了此连接。</span><span class="sxs-lookup"><span data-stu-id="b6a4e-113">You have configured this connection earlier in this lesson.</span></span>  
  
     <span data-ttu-id="b6a4e-114">![Excel - 在“主数据”选项卡上显示“资源管理器”按钮](../../2014/tutorials/media/et-combinematchandpublishnewsod-01.jpg "Excel - 在“主数据”选项卡上显示“资源管理器”按钮")</span><span class="sxs-lookup"><span data-stu-id="b6a4e-114">![Excel - Show Explorer Button on Master Data Tabl](../../2014/tutorials/media/et-combinematchandpublishnewsod-01.jpg "Excel - Show Explorer Button on Master Data Tabl")</span></span>  
  
4.  <span data-ttu-id="b6a4e-115">你应看到右侧的 "**主数据资源管理器**" 窗格。</span><span class="sxs-lookup"><span data-stu-id="b6a4e-115">You should see the **Master Data Explorer** pane to the right.</span></span> <span data-ttu-id="b6a4e-116">如果看不到主数据资源管理器，请单击功能区上的 "**显示资源管理器**" 按钮。</span><span class="sxs-lookup"><span data-stu-id="b6a4e-116">If you do not see the Master Data Explorer, click **Show Explorer** button on the ribbon.</span></span>  
  
5.  <span data-ttu-id="b6a4e-117">在 "**主数据资源管理器**" 窗口中，选择**模型**下拉列表中的 "**供应商**"。</span><span class="sxs-lookup"><span data-stu-id="b6a4e-117">In the **Master Data Explorer** Window, select **Suppliers** in the drop-down list for the **Model**.</span></span> <span data-ttu-id="b6a4e-118">应会看到该模型具有一个实体：**供应商**。</span><span class="sxs-lookup"><span data-stu-id="b6a4e-118">You should see that the model has one entity: **Supplier**.</span></span>  
  
     <span data-ttu-id="b6a4e-119">![Excel -“主数据资源管理器”窗口](../../2014/tutorials/media/et-combinematchandpublishnewsod-02.jpg "Excel -“主数据资源管理器”窗口")</span><span class="sxs-lookup"><span data-stu-id="b6a4e-119">![Excel - Master Data Explorer Window](../../2014/tutorials/media/et-combinematchandpublishnewsod-02.jpg "Excel - Master Data Explorer Window")</span></span>  
  
6.  <span data-ttu-id="b6a4e-120">双击实体列表中的 "**供应商**"，将实体成员加载到 Excel 工作表中。</span><span class="sxs-lookup"><span data-stu-id="b6a4e-120">Double-click **Supplier** in the entity list to load the entity members into the Excel worksheet.</span></span>  
  
7.  <span data-ttu-id="b6a4e-121">单击底部的 " **Sheet2** " 切换到 " **sheet2** " 选项卡。如果看不到**Sheet2**，请添加一个新的工作表。</span><span class="sxs-lookup"><span data-stu-id="b6a4e-121">Click **Sheet2** at the bottom to switch to the **Sheet2** tab. If you do not see **Sheet2**, add a new worksheet.</span></span>  
  
8.  <span data-ttu-id="b6a4e-122">打开**Suppliers.xls**文件 (包含在教程文件中的原始输入文件) 并将**CombineAndCleanse**工作表中的所有 (三个) 行复制到**Sheet2**。</span><span class="sxs-lookup"><span data-stu-id="b6a4e-122">Open **Suppliers.xls** file (the original input file that is included in the tutorial files) and copy all (three) rows from the **CombineAndCleanse** worksheet to **Sheet2**.</span></span>  
  
9. <span data-ttu-id="b6a4e-123">切换回书籍1中的**供应商**工作表 **-Microsoft Excel** (不是连接到**MDS**的**清理和匹配的供应商列表**Excel) 。</span><span class="sxs-lookup"><span data-stu-id="b6a4e-123">Switch back to the **Supplier** sheet in the **Book 1 - Microsoft Excel** (not the **Cleansed and Matched Supplier List** Excel) that is connected to **MDS**.</span></span>  
  
10. <span data-ttu-id="b6a4e-124">单击菜单栏上的 "**主数据**"。</span><span class="sxs-lookup"><span data-stu-id="b6a4e-124">Click **Master Data** on the menu bar.</span></span>  
  
11. <span data-ttu-id="b6a4e-125">在功能区上单击 "**合并数据**"。</span><span class="sxs-lookup"><span data-stu-id="b6a4e-125">Click **Combine Data** on the ribbon.</span></span> <span data-ttu-id="b6a4e-126">您将看到 "**合并数据**" 对话框。</span><span class="sxs-lookup"><span data-stu-id="b6a4e-126">You will see the **Combine Data** dialog box.</span></span>  
  
12. <span data-ttu-id="b6a4e-127">在 "**合并数据**" 对话框中，单击 "**要与 MDS 数据组合的范围**" 文本框旁的按钮，如下图所示。</span><span class="sxs-lookup"><span data-stu-id="b6a4e-127">In the **Combine Data** dialog box, click the button next to **Range to combine with MDS data** text box as shown in the following image.</span></span>  
  
     <span data-ttu-id="b6a4e-128">![Excel -“合并数据”对话框](../../2014/tutorials/media/et-combinematchandpublishnewsod-03.jpg "Excel -“合并数据”对话框")</span><span class="sxs-lookup"><span data-stu-id="b6a4e-128">![Excel - Combine Data Dialog Box](../../2014/tutorials/media/et-combinematchandpublishnewsod-03.jpg "Excel - Combine Data Dialog Box")</span></span>  
  
13. <span data-ttu-id="b6a4e-129">您现在应看到收缩的对话框。</span><span class="sxs-lookup"><span data-stu-id="b6a4e-129">You should see the shrunken dialog box now.</span></span> <span data-ttu-id="b6a4e-130">现在，单击 " **sheet2** " 切换到 " **sheet2** " 选项卡，该选项卡具有具有4行 (的新供应商数据，其中包含一个标题行) 。</span><span class="sxs-lookup"><span data-stu-id="b6a4e-130">Now, click **Sheet2** to switch to the **Sheet2** tab that has the new supplier data with 4 rows (including one header row).</span></span>  
  
14. <span data-ttu-id="b6a4e-131">在**Sheet2**中，选择**包括标题行 (的所有行**，即使它们看起来已经处于选中状态) 。</span><span class="sxs-lookup"><span data-stu-id="b6a4e-131">In the **Sheet2**, select **all rows including the header row** (even if they seem to be already selected).</span></span> <span data-ttu-id="b6a4e-132">应会看到**要与 MDS 数据组合的范围**自动更新。</span><span class="sxs-lookup"><span data-stu-id="b6a4e-132">You should see the **Range to combine with MDS data** is automatically updated.</span></span>  
  
     <span data-ttu-id="b6a4e-133">![Excel -“合并数据”对话框 - 最小化](../../2014/tutorials/media/et-combinematchandpublishnewsod-04.jpg "Excel -“合并数据”对话框 - 最小化")</span><span class="sxs-lookup"><span data-stu-id="b6a4e-133">![Excel - Combine Data Dialog Box - Minimized](../../2014/tutorials/media/et-combinematchandpublishnewsod-04.jpg "Excel - Combine Data Dialog Box - Minimized")</span></span>  
  
15. <span data-ttu-id="b6a4e-134">切换回 "**供应商**" 选项卡，而不关闭 "**合并数据**" 对话框。</span><span class="sxs-lookup"><span data-stu-id="b6a4e-134">Switch back to the **Suppliers** tab without closing the **Combine Data** dialog box.</span></span>  
  
16. <span data-ttu-id="b6a4e-135">单击**文本框**旁边的**按钮**。</span><span class="sxs-lookup"><span data-stu-id="b6a4e-135">Click the **button** next to the **text box**.</span></span> <span data-ttu-id="b6a4e-136">您现在应看到对话框已展开。</span><span class="sxs-lookup"><span data-stu-id="b6a4e-136">You should see that the dialog box is expanded now.</span></span> <span data-ttu-id="b6a4e-137">应会看到**供应商**MDS**实体**列与**Excel**列之间的所有映射都将自动填充。</span><span class="sxs-lookup"><span data-stu-id="b6a4e-137">You should see all the mappings between columns of the **Supplier** MDS **entity** to **Excel** columns are automatically populated.</span></span>  
  
     <span data-ttu-id="b6a4e-138">![Excel -使用数据填充的“合并数据”对话框](../../2014/tutorials/media/et-combinematchandpublishnewsod-05.jpg "Excel -使用数据填充的“合并数据”对话框")</span><span class="sxs-lookup"><span data-stu-id="b6a4e-138">![Excel - Combine Data Dialog Box Filled with Data](../../2014/tutorials/media/et-combinematchandpublishnewsod-05.jpg "Excel - Combine Data Dialog Box Filled with Data")</span></span>  
  
17. <span data-ttu-id="b6a4e-139">确保将**代码**实体列映射到工作表中的 "**供应商**" 列，并将 "**邮政编码**" 实体列映射到工作表中的**邮政编码**列。</span><span class="sxs-lookup"><span data-stu-id="b6a4e-139">Ensure that **Code** entity column is mapped to the **SupplierID** column in the worksheet and **Zip Code** entity column is mapped to the **Zip Code** column in the worksheet.</span></span>  
  
18. <span data-ttu-id="b6a4e-140">在 "**合并数据**" 对话框中，单击 "**合并**"。</span><span class="sxs-lookup"><span data-stu-id="b6a4e-140">On the **Combine Data** dialog box, click **Combine**.</span></span>  
  
19. <span data-ttu-id="b6a4e-141">确认将三个数据行添加到了工作表的底部且它们应用颜色标记出来。</span><span class="sxs-lookup"><span data-stu-id="b6a4e-141">Confirm that three data rows are added to the bottom of the worksheet and they should be color coded.</span></span>  
  
     <span data-ttu-id="b6a4e-142">![Excel - 合并后的新元素](../../2014/tutorials/media/et-combinematchandpublishnewsod-06.jpg "Excel - 合并后的新元素")</span><span class="sxs-lookup"><span data-stu-id="b6a4e-142">![Excel - New Elements after Combining](../../2014/tutorials/media/et-combinematchandpublishnewsod-06.jpg "Excel - New Elements after Combining")</span></span>  
  
20. <span data-ttu-id="b6a4e-143">单击功能区上的 "**数学数据**" 以标识重复项。</span><span class="sxs-lookup"><span data-stu-id="b6a4e-143">Click **Math Data** on the ribbon to identify duplicates.</span></span> <span data-ttu-id="b6a4e-144">此功能使用 DQS 的匹配功能。</span><span class="sxs-lookup"><span data-stu-id="b6a4e-144">This feature uses the matching functionality of DQS.</span></span>  
  
21. <span data-ttu-id="b6a4e-145">在 "**匹配数据**" 对话框中，选择 " **DQS 知识库**" 的 "**供应商**"。</span><span class="sxs-lookup"><span data-stu-id="b6a4e-145">In the **Match Data** dialog box, select **Suppliers** for **DQS Knowledge Base**.</span></span>  
  
     <span data-ttu-id="b6a4e-146">![Excel -“匹配数据”对话框](../../2014/tutorials/media/et-combinematchandpublishnewsod-07.jpg "Excel -“匹配数据”对话框")</span><span class="sxs-lookup"><span data-stu-id="b6a4e-146">![Excel - Match Data Dialog Box](../../2014/tutorials/media/et-combinematchandpublishnewsod-07.jpg "Excel - Match Data Dialog Box")</span></span>  
  
22. <span data-ttu-id="b6a4e-147">将工作表列映射到域，如下表中所示。</span><span class="sxs-lookup"><span data-stu-id="b6a4e-147">Map worksheet columns to domains as shown in the following table.</span></span>  
  
    |<span data-ttu-id="b6a4e-148">工作表列</span><span class="sxs-lookup"><span data-stu-id="b6a4e-148">Worksheet Column</span></span>|<span data-ttu-id="b6a4e-149">域</span><span class="sxs-lookup"><span data-stu-id="b6a4e-149">Domain</span></span>|  
    |----------------------|------------|  
    |<span data-ttu-id="b6a4e-150">Code（您上载了 Supplier ID 作为 MDS 中 Supplier 实体的代码）</span><span class="sxs-lookup"><span data-stu-id="b6a4e-150">Code (you uploaded Supplier ID as the Code for the Supplier entity in MDS)</span></span>|<span data-ttu-id="b6a4e-151">Supplier ID</span><span class="sxs-lookup"><span data-stu-id="b6a4e-151">Supplier ID</span></span>|  
    |<span data-ttu-id="b6a4e-152">Name（您上载了 Supplier Name 作为 MDS 中 Supplier 实体的名称）</span><span class="sxs-lookup"><span data-stu-id="b6a4e-152">Name (you uploaded Supplier Name as the Name for the Supplier entity to MDS)</span></span>|<span data-ttu-id="b6a4e-153">Supplier Name</span><span class="sxs-lookup"><span data-stu-id="b6a4e-153">Supplier Name</span></span>|  
    |<span data-ttu-id="b6a4e-154">ContactEmailAddress</span><span class="sxs-lookup"><span data-stu-id="b6a4e-154">ContactEmailAddress</span></span>|<span data-ttu-id="b6a4e-155">ContactEmail</span><span class="sxs-lookup"><span data-stu-id="b6a4e-155">ContactEmail</span></span>|  
  
23. <span data-ttu-id="b6a4e-156">选择 "**代码**列映射的**先决条件**"。</span><span class="sxs-lookup"><span data-stu-id="b6a4e-156">Select **Prerequisite** for the **Code** column mapping.</span></span>  
  
24. <span data-ttu-id="b6a4e-157">输入**70%** 作为**供应商名称**的**权重**，输入**30%** 作为**联系电子邮件\*\*\*\*的权重**，如图所示。</span><span class="sxs-lookup"><span data-stu-id="b6a4e-157">Enter **70%** as the **weight** for **Supplier Name** and **30%** as the **weight** for **Contact Email** as shown in the image.</span></span>  
  
25. <span data-ttu-id="b6a4e-158">单击“确定”  。</span><span class="sxs-lookup"><span data-stu-id="b6a4e-158">Click **OK**.</span></span>  
  
26. <span data-ttu-id="b6a4e-159">匹配过程应为供应商标识一个重复项，**代码为： S1**。</span><span class="sxs-lookup"><span data-stu-id="b6a4e-159">The matching process should identify one duplicate for the supplier with **Code: S1**.</span></span>  
  
     <span data-ttu-id="b6a4e-160">![Excel - 匹配结果](../../2014/tutorials/media/et-combinematchandpublishnewsod-08.jpg "Excel - 匹配结果")</span><span class="sxs-lookup"><span data-stu-id="b6a4e-160">![Excel - Matching Results](../../2014/tutorials/media/et-combinematchandpublishnewsod-08.jpg "Excel - Matching Results")</span></span>  
  
27. <span data-ttu-id="b6a4e-161">选择**重复行 (橙色) **，右键单击，然后单击 "**删除**" 以删除该行。</span><span class="sxs-lookup"><span data-stu-id="b6a4e-161">Select the **duplicate row (orange)**, right-click, and click **Delete** to delete the row.</span></span>  
  
28. <span data-ttu-id="b6a4e-162">删除**CLUSTER_ID**列，因为不再需要它。</span><span class="sxs-lookup"><span data-stu-id="b6a4e-162">Delete the **CLUSTER_ID** column since you don't need it anymore.</span></span>  
  
29. <span data-ttu-id="b6a4e-163">单击 "**发布**"，将具有**代码 S66**和**S57**的其他两个新记录发布到 MDS。</span><span class="sxs-lookup"><span data-stu-id="b6a4e-163">Click **Publish** to publish the other two new records with **Codes S66** and **S57** to MDS.</span></span>  
  
30. <span data-ttu-id="b6a4e-164">在 "**发布并**添加批注" 对话框中，添加一个**批注**，然后单击 "**发布**"。</span><span class="sxs-lookup"><span data-stu-id="b6a4e-164">In the **Publish and Annotate** dialog box, add an **annotation**, and click **Publish**.</span></span>  
  
31. <span data-ttu-id="b6a4e-165">切换到**主数据管理器 Web 应用程序**。</span><span class="sxs-lookup"><span data-stu-id="b6a4e-165">Switch to the **Master Data Manager Web application**.</span></span>  
  
32. <span data-ttu-id="b6a4e-166">在主页上，确保已为**模型**选择 "**供应商**"，然后单击 "**资源管理器**"。</span><span class="sxs-lookup"><span data-stu-id="b6a4e-166">On the home page, ensure that **Suppliers** is selected for the **Model**, and click **Explorer**.</span></span> <span data-ttu-id="b6a4e-167">如果已打开**资源管理器**，请刷新 internet 浏览器。</span><span class="sxs-lookup"><span data-stu-id="b6a4e-167">If you already have the **Explorer** open, refresh the internet browser.</span></span>  
  
33. <span data-ttu-id="b6a4e-168">按**代码\*\*\*\*对列表进行排序**，并使用**S57**和**S66**作为代码查找记录。</span><span class="sxs-lookup"><span data-stu-id="b6a4e-168">**Sort** the list by **Code** and look for records with **S57** and **S66** as codes.</span></span> <span data-ttu-id="b6a4e-169">您也可以使用工具栏上的 "**筛选器**" 按钮在列表中搜索特定记录。</span><span class="sxs-lookup"><span data-stu-id="b6a4e-169">You can also use the **Filter** button on the toolbar to search for a specific record in the list.</span></span>  
  
34. <span data-ttu-id="b6a4e-170">现在，关闭**Book1-Microsoft Excel**窗口而不保存该文件。</span><span class="sxs-lookup"><span data-stu-id="b6a4e-170">Now, close **Book1 - Microsoft Excel** window without saving the file.</span></span>  
  
## <a name="next-step"></a><span data-ttu-id="b6a4e-171">下一步</span><span class="sxs-lookup"><span data-stu-id="b6a4e-171">Next Step</span></span>  
 [<span data-ttu-id="b6a4e-172">任务 5：从 Excel 中创建基于域的属性</span><span class="sxs-lookup"><span data-stu-id="b6a4e-172">Task 5: Creating a Domain-Based Attribute from Excel</span></span>](../../2014/tutorials/task-5-creating-a-domain-based-attribute-from-excel.md)  
  
  
