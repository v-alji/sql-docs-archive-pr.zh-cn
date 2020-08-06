---
title: 任务12：发现知识 (知识发现) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-quality-services
ms.topic: conceptual
ms.assetid: dd80a8e6-1e41-4c49-9898-02b1d2505a10
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 2dee66f94f1df609701f92d591f2c31863702465
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87689177"
---
# <a name="task-12-discovering-knowledge-knowledge-discovery"></a><span data-ttu-id="dd9f6-102">任务 12：发现知识（知识发现）</span><span class="sxs-lookup"><span data-stu-id="dd9f6-102">Task 12: Discovering Knowledge (Knowledge Discovery)</span></span>
  <span data-ttu-id="dd9f6-103">在此任务中，您将对**供应商 ID**和**供应商名称**域执行**知识发现**活动。</span><span class="sxs-lookup"><span data-stu-id="dd9f6-103">In this task, you perform the **Knowledge Discovery** activity on **Supplier ID** and **Supplier Name** domains.</span></span> <span data-ttu-id="dd9f6-104">在此方案中，知识发现过程主要导入这两个域的值。</span><span class="sxs-lookup"><span data-stu-id="dd9f6-104">In this scenario, the knowledge discovery process mainly imports values for these two domains.</span></span>  
  
 <span data-ttu-id="dd9f6-105">在本教程中，您是从头开始构建知识库的。</span><span class="sxs-lookup"><span data-stu-id="dd9f6-105">In this tutorial, you started building knowledge base from scratch.</span></span> <span data-ttu-id="dd9f6-106">还可以通过执行知识发现活动来创建知识库。</span><span class="sxs-lookup"><span data-stu-id="dd9f6-106">You can also start creating a knowledge base by performing a knowledge discovery activity.</span></span> <span data-ttu-id="dd9f6-107">单击主页中的 "**创建知识库**" 时，DQS 客户端会将您转到一个页面，其中包含为活动选择的**域管理**活动。</span><span class="sxs-lookup"><span data-stu-id="dd9f6-107">When you click **Create a Knowledge Base** in the main page, DQS client takes you to a page with **Domain Management** activity selected for the activity.</span></span> <span data-ttu-id="dd9f6-108">您可以将**活动**更改为**知识发现**，然后在下一页中，您可以在知识发现过程中创建域。</span><span class="sxs-lookup"><span data-stu-id="dd9f6-108">You can change the **activity** to **Knowledge Discovery** and then in the next page you can create domains as part of the knowledge discovery process.</span></span> <span data-ttu-id="dd9f6-109">有关更多详细信息，请参阅[执行知识发现](https://msdn.microsoft.com/library/hh510398.aspx)。</span><span class="sxs-lookup"><span data-stu-id="dd9f6-109">See [Perform Knowledge Discovery](https://msdn.microsoft.com/library/hh510398.aspx) for more details.</span></span>  
  
1.  <span data-ttu-id="dd9f6-110">在 DQS 客户端的主页中，在 "**最近的知识库**" 部分中，单击 "**供应商**" 知识库旁边的**向右箭头**，然后单击 "**知识发现**"。</span><span class="sxs-lookup"><span data-stu-id="dd9f6-110">In the main page of DQS Client, in the **Recent Knowledge Base** section, click **right-arrow** next to the **Suppliers** knowledge base and click **Knowledge Discovery**.</span></span> <span data-ttu-id="dd9f6-111">或者，您可以单击 "**打开知识库**"，选择**知识库列表中的**"**供应商**"，选择 "**知识发现**" 作为**活动**，然后单击 "**下一步**"。</span><span class="sxs-lookup"><span data-stu-id="dd9f6-111">Alternatively, you can click **Open Knowledge Base**, select **Suppliers** from the **list of knowledge bases**, select **Knowledge Discovery** as **activity** and click **Next**.</span></span>  
  
     <span data-ttu-id="dd9f6-112">![主页上的“知识发现”菜单](../../2014/tutorials/media/et-discoveringknowledge-01.jpg "主页上的“知识发现”菜单")</span><span class="sxs-lookup"><span data-stu-id="dd9f6-112">![Knowledge Discovery Menu on Main Page](../../2014/tutorials/media/et-discoveringknowledge-01.jpg "Knowledge Discovery Menu on Main Page")</span></span>  
  
2.  <span data-ttu-id="dd9f6-113">为 "**数据源**" 选择 " **Excel 文件**"。</span><span class="sxs-lookup"><span data-stu-id="dd9f6-113">Select **Excel File** for **Data Source**.</span></span>  
  
3.  <span data-ttu-id="dd9f6-114">单击 "**浏览**"，导航并选择 " **Suppliers.xls**"，然后单击 "**打开**"。</span><span class="sxs-lookup"><span data-stu-id="dd9f6-114">Click **Browse**, navigate and select **Suppliers.xls**, and click **Open**.</span></span>  
  
4.  <span data-ttu-id="dd9f6-115">选择**工作表\*\*\*\*的发现的供应商**。</span><span class="sxs-lookup"><span data-stu-id="dd9f6-115">Select **Suppliers for Discovery** for **Worksheet**.</span></span>  
  
5.  <span data-ttu-id="dd9f6-116">在 "**映射**" 部分中，使用**下拉列表**将 "供应商**ID** " 列从**Excel** **文件映射到**供应**商名称 "** 域和**供应商名称**" 列。</span><span class="sxs-lookup"><span data-stu-id="dd9f6-116">In the **Mappings** section, map **SupplierID** column from the **Excel** file to the **Supplier ID** domain and **Supplier Name** column to the **Supplier Name** domain by using **drop-down lists**.</span></span> <span data-ttu-id="dd9f6-117">该 Excel 文件包含**供应商 ID**和**供应商名称**域的示例数据。</span><span class="sxs-lookup"><span data-stu-id="dd9f6-117">The Excel file has sample data for the **Supplier ID** and **Supplier Name** domains.</span></span> <span data-ttu-id="dd9f6-118">在发现过程中，您可以选择要为其发现值的域。</span><span class="sxs-lookup"><span data-stu-id="dd9f6-118">In the discovery process, you can select the domains for which you want to discover the values.</span></span> <span data-ttu-id="dd9f6-119">您可以在此页上创建域，然后将源列映射到这些域。</span><span class="sxs-lookup"><span data-stu-id="dd9f6-119">You can create domains on this page and then map the source columns to those domains.</span></span> <span data-ttu-id="dd9f6-120">在知识发现活动中创建域的情况并不少见，而不是在域管理活动期间创建域。</span><span class="sxs-lookup"><span data-stu-id="dd9f6-120">It is not uncommon to create domains during knowledge discovery activity instead of creating domains during domain management activity.</span></span>  
  
     <span data-ttu-id="dd9f6-121">![发现过程的“映射”页](../../2014/tutorials/media/et-discoveringknowledge-02.jpg "发现过程的“映射”页")</span><span class="sxs-lookup"><span data-stu-id="dd9f6-121">![Map Page of Discovery Process](../../2014/tutorials/media/et-discoveringknowledge-02.jpg "Map Page of Discovery Process")</span></span>  
  
6.  <span data-ttu-id="dd9f6-122">单击 "**下一步**" 切换到 "**发现**" 页。</span><span class="sxs-lookup"><span data-stu-id="dd9f6-122">Click **Next** to switch to the **Discover** page.</span></span>  
  
7.  <span data-ttu-id="dd9f6-123">在 "**发现**" 页上，单击 "**启动**" 以启动发现进程。</span><span class="sxs-lookup"><span data-stu-id="dd9f6-123">On the **Discover** page, click **Start** to start the discovery process.</span></span> <span data-ttu-id="dd9f6-124">将对**Suppliers.xls**文件中的**供应商**和**供应商名称**的列执行发现。</span><span class="sxs-lookup"><span data-stu-id="dd9f6-124">Discovery is performed on the columns **SupplierID** and **Supplier Name** in the **Suppliers.xls** file.</span></span> <span data-ttu-id="dd9f6-125">**供应商 ID**和**供应商名称**域应填充从发现中提取的知识。</span><span class="sxs-lookup"><span data-stu-id="dd9f6-125">The **Supplier ID** and **Supplier Name** domains should be populated with the knowledge drawn from the discovery.</span></span>  
  
     <span data-ttu-id="dd9f6-126">![发现过程的“发现”页](../../2014/tutorials/media/et-discoveringknowledge-03.jpg "发现过程的“发现”页")</span><span class="sxs-lookup"><span data-stu-id="dd9f6-126">![Discover Page of Discovery Process](../../2014/tutorials/media/et-discoveringknowledge-03.jpg "Discover Page of Discovery Process")</span></span>  
  
8.  <span data-ttu-id="dd9f6-127">分析完成后，在页面底部的 "**探查器" 选项卡**中查看 "**源统计信息**"。</span><span class="sxs-lookup"><span data-stu-id="dd9f6-127">After the analysis has completed, review the **Source Statistics** in the **Profiler tab** at the bottom of the page.</span></span> <span data-ttu-id="dd9f6-128">请注意，有10个新记录，其中包含20个值，其中包含从**Excel 工作表**)  (**供应商\*\*\*\*名称**值。</span><span class="sxs-lookup"><span data-stu-id="dd9f6-128">Notice that 10 new records with total 20 values (**SupplierID** and **Supplier Name** values from the **Excel worksheet**) were discovered.</span></span> <span data-ttu-id="dd9f6-129">我们还看到多少个值是新的、唯一的、新并且是唯一的以及有效的。</span><span class="sxs-lookup"><span data-stu-id="dd9f6-129">You will also see how many of the values are new, unique, new and unique, and valid.</span></span> <span data-ttu-id="dd9f6-130">在右侧的列表框中，您可以看到发现过程中涉及的每个域的详细信息。</span><span class="sxs-lookup"><span data-stu-id="dd9f6-130">In the list box to the right, you can see more details for each domain involved in the discovery process.</span></span> <span data-ttu-id="dd9f6-131">如果您将鼠标悬停在“完整性”列的状态栏上，您可以看到源列中是否有任何缺失值。</span><span class="sxs-lookup"><span data-stu-id="dd9f6-131">If you hover the mouse over the status bar in the Completeness column, you can see if there are any missing values in the columns in the source.</span></span>  
  
     <span data-ttu-id="dd9f6-132">![知识发现结果](../../2014/tutorials/media/et-discoveringknowledge-04.jpg "知识发现结果")</span><span class="sxs-lookup"><span data-stu-id="dd9f6-132">![Knowledge Discovery Results](../../2014/tutorials/media/et-discoveringknowledge-04.jpg "Knowledge Discovery Results")</span></span>  
  
9. <span data-ttu-id="dd9f6-133">单击 "**下一步**" 切换到 "**管理域值**" 页。</span><span class="sxs-lookup"><span data-stu-id="dd9f6-133">Click **Next** to switch to the **Manage Domain Values** page.</span></span>  
  
10. <span data-ttu-id="dd9f6-134">在 "**管理域值**" 页中，单击域列表中的 "**供应商名称**域"。</span><span class="sxs-lookup"><span data-stu-id="dd9f6-134">In the **Manage Domain Values** page, click **Supplier Name** domain from the list of domains.</span></span>  
  
11. <span data-ttu-id="dd9f6-135">在右侧窗格中，右键单击 "**懒惰国家/地区 Storex** (通知" x "，并选择"**懒惰国家商店**) "。</span><span class="sxs-lookup"><span data-stu-id="dd9f6-135">In the right pane, right-click **Lazy Country Storex** (notice 'x' at the end), and select **Lazy Country Store**.</span></span> <span data-ttu-id="dd9f6-136">DQS 建议在对域运行拼写检查程序后进行此更改。</span><span class="sxs-lookup"><span data-stu-id="dd9f6-136">DQS suggests this change after running the spell checker on the domain.</span></span> <span data-ttu-id="dd9f6-137">默认情况下，在您创建的域上启用拼写检查程序。</span><span class="sxs-lookup"><span data-stu-id="dd9f6-137">By default, speller is enabled on the domains you create.</span></span>  
  
     <span data-ttu-id="dd9f6-138">![正确供应商名称 - 惰性国家/地区商店](../../2014/tutorials/media/et-discoveringknowledge-05.jpg "正确供应商名称 - 惰性国家/地区商店")</span><span class="sxs-lookup"><span data-stu-id="dd9f6-138">![Correct Supplier Name - Lazy Country Store](../../2014/tutorials/media/et-discoveringknowledge-05.jpg "Correct Supplier Name - Lazy Country Store")</span></span>  
  
12. <span data-ttu-id="dd9f6-139">在 "域值" 列表中，确认 "**懒惰国家/地区 Storex** " 值设置为错误 (红色**X**标记) 使用 "**懒惰国家商店**" 作为更正，还会将 "**惰性国家/地区" 存储**添加为有效值。</span><span class="sxs-lookup"><span data-stu-id="dd9f6-139">In the domain values list, confirm that the value **Lazy Country Storex** is set as an error (red **X** mark) with **Lazy Country Store** as the correction and also the **Lazy Country Store** is also added as a valid value.</span></span>  
  
     <span data-ttu-id="dd9f6-140">![域值和更正为值](../../2014/tutorials/media/et-discoveringknowledge-06.jpg "域值和更正为值")</span><span class="sxs-lookup"><span data-stu-id="dd9f6-140">![Domain Value and Correct To Value](../../2014/tutorials/media/et-discoveringknowledge-06.jpg "Domain Value and Correct To Value")</span></span>  
  
13. <span data-ttu-id="dd9f6-141">单击“完成”。</span><span class="sxs-lookup"><span data-stu-id="dd9f6-141">Click **Finish**.</span></span>  
  
14. <span data-ttu-id="dd9f6-142">在**SQL Server Data Quality Services** "对话框中，单击"**发布**"。</span><span class="sxs-lookup"><span data-stu-id="dd9f6-142">On **SQL Server Data Quality Services** dialog box, click **Publish**.</span></span>  
  
15. <span data-ttu-id="dd9f6-143">在 "成功" 消息框中单击 **"确定"** 。</span><span class="sxs-lookup"><span data-stu-id="dd9f6-143">Click **OK** on the success message box.</span></span>  
  
     <span data-ttu-id="dd9f6-144">您已经完成本教程的第一个课程。</span><span class="sxs-lookup"><span data-stu-id="dd9f6-144">You have completed the first lesson of the tutorial.</span></span>  
  
## <a name="next-step"></a><span data-ttu-id="dd9f6-145">下一步</span><span class="sxs-lookup"><span data-stu-id="dd9f6-145">Next Step</span></span>  
 [<span data-ttu-id="dd9f6-146">第 2 课：使用 Suppliers 知识库清理供应商数据</span><span class="sxs-lookup"><span data-stu-id="dd9f6-146">Lesson 2: Cleansing Supplier Data using the Suppliers Knowledge Base</span></span>](../../2014/tutorials/lesson-2-cleansing-supplier-data-using-the-suppliers-knowledge-base.md)  
  
  
