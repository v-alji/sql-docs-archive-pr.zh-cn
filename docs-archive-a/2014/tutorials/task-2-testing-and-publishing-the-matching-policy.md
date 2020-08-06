---
title: 任务2：测试和发布匹配策略 |Microsoft Docs
ms.custom: ''
ms.date: 03/09/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-quality-services
ms.topic: conceptual
ms.assetid: e1ffb6d7-fbc5-4695-b538-cc2302d1a17d
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 88bed2e91ca1fee3eab6136fb94df0d13328dc80
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87589396"
---
# <a name="task-2-testing-and-publishing-the-matching-policy"></a><span data-ttu-id="91af9-102">任务 2：测试和发布匹配策略</span><span class="sxs-lookup"><span data-stu-id="91af9-102">Task 2: Testing and Publishing the Matching Policy</span></span>
  <span data-ttu-id="91af9-103">在此任务中，您将测试并发布**删除重复的供应商**匹配策略。</span><span class="sxs-lookup"><span data-stu-id="91af9-103">In this task, you test and publish the **Remove Duplicate Suppliers** matching policy.</span></span>  
  
1.  <span data-ttu-id="91af9-104">在 "**匹配结果**" 页上，单击 "**启动**" 以测试整个策略。</span><span class="sxs-lookup"><span data-stu-id="91af9-104">In the **Matching Results** page, click **Start** to test the entire policy.</span></span> <span data-ttu-id="91af9-105">对于您，此策略中只有唯一的一条规则，因此，测试此规则和策略的结果应该相同。</span><span class="sxs-lookup"><span data-stu-id="91af9-105">In your case, you have only rule in the policy, so the results from testing the rule and the policy should be the same.</span></span>  
  
2.  <span data-ttu-id="91af9-106">在列表框中查看所有匹配的记录及其匹配分数。</span><span class="sxs-lookup"><span data-stu-id="91af9-106">Review all the matched records and their matching score in the list box.</span></span> <span data-ttu-id="91af9-107">具有与之关联的**绿色**图标的记录是其前面的透视记录的副本。</span><span class="sxs-lookup"><span data-stu-id="91af9-107">A record that has a **Green** icon associated with it is a duplicate of the pivot record that precedes it.</span></span> <span data-ttu-id="91af9-108">示例如下：</span><span class="sxs-lookup"><span data-stu-id="91af9-108">Here are couple of examples:</span></span>  
  
    1.  <span data-ttu-id="91af9-109">记录 ID 为**1000005**的记录与**记录 id： 1000004**的记录匹配，**分数为： 100%** ，因为这两条记录对于**供应商 (先决条件) **、**供应商名称**和**ContactEmailAddress 列**都具有相同的值。</span><span class="sxs-lookup"><span data-stu-id="91af9-109">The record with **Record ID: 1000005** is a match of the record with **Record Id: 1000004** with **Score: 100%** because both the records have the same values for **SupplierID (prerequisite)**, **Supplier Name**, and **ContactEmailAddress columns**.</span></span> <span data-ttu-id="91af9-110">DQS 随机选择一条记录作为群集的透视记录。</span><span class="sxs-lookup"><span data-stu-id="91af9-110">DQS randomly picks a record as the pivot record for a cluster.</span></span>  
  
    2.  <span data-ttu-id="91af9-111">记录**1000023**与匹配分数为的记录**1000022**匹配：93%，因为这两条记录对于**供应商 (先决条件) **和**供应商名称**列都具有相同的值，但**ContactEmailAddress**列的值不同。</span><span class="sxs-lookup"><span data-stu-id="91af9-111">The record **1000023** is a match of the record **1000022** with the matching score: 93% because the two records have the same values for **SupplierID (prerequisite)** and **Supplier Name** columns, but different values for the **ContactEmailAddress** column.</span></span>  
  
    3.  <span data-ttu-id="91af9-112">滚动到列表底部，查看记录 Id 为**1000051**和**1000052**的两个记录。</span><span class="sxs-lookup"><span data-stu-id="91af9-112">Scroll to the bottom of the list to see two records with records IDs: **1000051** and **1000052**.</span></span> <span data-ttu-id="91af9-113">记录**1000052**被视为匹配分数为**91%** 的匹配，因为这两条记录对供应**商**和**ContactEmailAddress**列具有相同的值，但**供应商名称**列的值不同。</span><span class="sxs-lookup"><span data-stu-id="91af9-113">Record **1000052** is considered a match with matching score **91%** because the two records have the same values for the **SupplierID** and **ContactEmailAddress** columns, but different values for the **Supplier Name** column.</span></span>  
  
     <span data-ttu-id="91af9-114">![策略定义 - 策略结果](../../2014/tutorials/media/et-testingandpublishingthematchingpolicy-01.jpg "策略定义 - 策略结果")</span><span class="sxs-lookup"><span data-stu-id="91af9-114">![Policy Definition - Policy Results](../../2014/tutorials/media/et-testingandpublishingthematchingpolicy-01.jpg "Policy Definition - Policy Results")</span></span>  
  
3.  <span data-ttu-id="91af9-115">右键单击任何匹配的记录 (带有绿色图标) ，然后单击 "**查看详细信息**" 以查看有关匹配项的详细信息，例如每个字段分数对总体匹配分数的贡献。</span><span class="sxs-lookup"><span data-stu-id="91af9-115">Right-click on any matched record (with green icon) and click **View Details** to see more details about the matching such as contribution of each field score to the overall matching score.</span></span>  
  
     <span data-ttu-id="91af9-116">![“匹配分数详细信息”对话框](../../2014/tutorials/media/et-testingandpublishingthematchingpolicy-02.jpg "“匹配分数详细信息”对话框")</span><span class="sxs-lookup"><span data-stu-id="91af9-116">![Matching Score Details Dialog Box](../../2014/tutorials/media/et-testingandpublishingthematchingpolicy-02.jpg "Matching Score Details Dialog Box")</span></span>  
  
4.  <span data-ttu-id="91af9-117">单击 "**关闭**" 以关闭 "**匹配分数详细信息**" 对话框。</span><span class="sxs-lookup"><span data-stu-id="91af9-117">Click **Close** to close the **Matching Score Details** dialog box.</span></span>  
  
5.  <span data-ttu-id="91af9-118">单击页面底部的 "**匹配结果**" 选项卡。</span><span class="sxs-lookup"><span data-stu-id="91af9-118">Click **Matching Results** tab at the bottom of the page.</span></span> <span data-ttu-id="91af9-119">此选项卡向您提供了详细信息，例如匹配的记录数、不匹配的记录数、具有匹配记录的群集数、平均群集大小、最小群集大小和最大群集大小。</span><span class="sxs-lookup"><span data-stu-id="91af9-119">This tab gives you detail such as number of matched records, number of unmatched records, number of clusters with matched records, the average cluster size, minimum cluster size, and maximum cluster size.</span></span> <span data-ttu-id="91af9-120">有关更多详细信息，请参阅[创建匹配策略](https://msdn.microsoft.com/library/hh270290.aspx)。</span><span class="sxs-lookup"><span data-stu-id="91af9-120">See [Create a Matching Policy](https://msdn.microsoft.com/library/hh270290.aspx) for more details.</span></span> <span data-ttu-id="91af9-121">您无法从此活动中导出结果。</span><span class="sxs-lookup"><span data-stu-id="91af9-121">You cannot export results from this activity.</span></span> <span data-ttu-id="91af9-122">您刚刚使用示例数据定义了一个匹配策略，以对照示例数据测试规则和策略。</span><span class="sxs-lookup"><span data-stu-id="91af9-122">You are just defining a matching policy by using the sample data to test rules and the policy against the sample data.</span></span>  
  
     <span data-ttu-id="91af9-123">![“匹配结果”选项卡](../../2014/tutorials/media/et-testingandpublishingthematchingpolicy-03.jpg "“匹配结果”选项卡")</span><span class="sxs-lookup"><span data-stu-id="91af9-123">![Matching Results Tab](../../2014/tutorials/media/et-testingandpublishingthematchingpolicy-03.jpg "Matching Results Tab")</span></span>  
  
6.  <span data-ttu-id="91af9-124">单击 "**完成**" 以完成创建匹配策略。</span><span class="sxs-lookup"><span data-stu-id="91af9-124">Click **Finish** to finish creating the matching policy.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="91af9-125">您已在此定义了匹配策略；因此，您无法将结果导出到输出文件。</span><span class="sxs-lookup"><span data-stu-id="91af9-125">You have defined the matching policy here; therefore you cannot export results to an output file.</span></span> <span data-ttu-id="91af9-126">大致说来，您使用了示例输入文件，创建了规则，并且为了定义策略而对照示例数据测试了规则和策略。</span><span class="sxs-lookup"><span data-stu-id="91af9-126">You basically used a sample input file, created rules, and tested the rules and policy against the sample data with the goal of defining the policy.</span></span>  
  
7.  <span data-ttu-id="91af9-127">在 "SQL Server Data Quality Services" 对话框中，单击 "**发布**"，然后在消息框中单击 **"确定"** 。</span><span class="sxs-lookup"><span data-stu-id="91af9-127">In the SQL Server Data Quality Services dialog box, click **Publish** and click **OK** on the message box.</span></span> <span data-ttu-id="91af9-128">现在，您定义的匹配策略发布到**供应商**知识库中。</span><span class="sxs-lookup"><span data-stu-id="91af9-128">Now, the matching policy you defined is published into the **Suppliers** Knowledge Base.</span></span> <span data-ttu-id="91af9-129">您可以使用此知识库来针对输入文件运行匹配过程，以确定和解决重复项。</span><span class="sxs-lookup"><span data-stu-id="91af9-129">You can use the knowledge base to run the matching process against an input file to identify and remove duplicates.</span></span>  
  
## <a name="next-step"></a><span data-ttu-id="91af9-130">下一步</span><span class="sxs-lookup"><span data-stu-id="91af9-130">Next Step</span></span>  
 [<span data-ttu-id="91af9-131">任务 3：创建并运行数据质量项目以进行匹配</span><span class="sxs-lookup"><span data-stu-id="91af9-131">Task 3: Creating and Running a Data Quality Project for Matching</span></span>](../../2014/tutorials/task-3-creating-and-running-a-data-quality-project-for-matching.md)  
  
  
