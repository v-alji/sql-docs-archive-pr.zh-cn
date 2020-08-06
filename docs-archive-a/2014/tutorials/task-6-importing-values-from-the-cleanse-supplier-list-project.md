---
title: 任务6：从 "清理供应商列表" 项目导入值 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-quality-services
ms.topic: conceptual
ms.assetid: fec0deef-a729-4ff1-b709-72d2b3f407ac
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: b674cfb42ddf31c3b903a465d1be1b04e9a355ab
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87578577"
---
# <a name="task-6-importing-values-from-the-cleanse-supplier-list-project"></a><span data-ttu-id="eee89-102">任务 6：从 Cleanse Supplier List 项目导入值</span><span class="sxs-lookup"><span data-stu-id="eee89-102">Task 6: Importing Values from the Cleanse Supplier List Project</span></span>
  <span data-ttu-id="eee89-103">在该任务中，您将导入在清理过程中收集的数据质量知识。</span><span class="sxs-lookup"><span data-stu-id="eee89-103">In this task, you import the data quality knowledge gathered during the cleansing process.</span></span> <span data-ttu-id="eee89-104">有关更多详细信息，请参阅[将清理项目值导入到域](https://msdn.microsoft.com/library/hh479581.aspx)主题。</span><span class="sxs-lookup"><span data-stu-id="eee89-104">See [Importing Cleansing Project Values into a Domain](https://msdn.microsoft.com/library/hh479581.aspx) topic for more details.</span></span> <span data-ttu-id="eee89-105">您还可以在发布更新的**供应商**知识库之前，将知识库导出到 DQS 文件中。</span><span class="sxs-lookup"><span data-stu-id="eee89-105">You also export the knowledge base into a DQS file before publishing the updated **Suppliers** knowledge base.</span></span>  
  
1.  <span data-ttu-id="eee89-106">在**DQS 客户端**的主页中，单击 "**最近的知识库**" 下的 "**供应商**" 旁边的**向右箭头**，然后单击 "**域管理**"。</span><span class="sxs-lookup"><span data-stu-id="eee89-106">In the main page of **DQS Client**, click **right-arrow** next to **Suppliers** under **Recent Knowledge Bases** and click **Domain Management**.</span></span>  
  
2.  <span data-ttu-id="eee89-107">单击域列表中的 "**联系人电子邮件**"，并切换到右窗格中的 "**域值**" 选项卡。</span><span class="sxs-lookup"><span data-stu-id="eee89-107">Click **Contact Email** in the list of domains, and switch to the **Domain Values** tab in the right pane.</span></span>  
  
3.  <span data-ttu-id="eee89-108">单击工具栏上的 "**导入值**" 图标旁边的**向下箭头**，然后单击 "**导入项目值**"。</span><span class="sxs-lookup"><span data-stu-id="eee89-108">Click **down arrow** next to the **Import Values** icon on the toolbar and click **Import Project Values**.</span></span>  
  
     <span data-ttu-id="eee89-109">![“导入项目值”工具栏按钮](../../2014/tutorials/media/et-importingvaluesfromthecslistproject-01.jpg "“导入项目值”工具栏按钮")</span><span class="sxs-lookup"><span data-stu-id="eee89-109">![Import Project Values Toolbar Button](../../2014/tutorials/media/et-importingvaluesfromthecslistproject-01.jpg "Import Project Values Toolbar Button")</span></span>  
  
4.  <span data-ttu-id="eee89-110">在 "**导入项目值**" 对话框中，选择 "**清理供应商列表**" 项目，然后单击 **"确定"**。</span><span class="sxs-lookup"><span data-stu-id="eee89-110">In the **Import Project Values** dialog box, select the **Cleanse Supplier List** project, and click **OK**.</span></span>  
  
5.  <span data-ttu-id="eee89-111">注意，此时将导入所有电子邮件以及您在交互式清理过程中所做的两处更正内容。</span><span class="sxs-lookup"><span data-stu-id="eee89-111">Notice that all the emails are imported along with the two corrections you did during interactive cleansing.</span></span> <span data-ttu-id="eee89-112">滚动以查看这两处更正内容。</span><span class="sxs-lookup"><span data-stu-id="eee89-112">Scroll to see the two corrections.</span></span>  
  
    |<span data-ttu-id="eee89-113">值</span><span class="sxs-lookup"><span data-stu-id="eee89-113">Value</span></span>|<span data-ttu-id="eee89-114">更正为</span><span class="sxs-lookup"><span data-stu-id="eee89-114">Correct To</span></span>|  
    |-----------|----------------|  
    |bobby0@adventure-work.com|bobby0@adventure-works.com|  
    |tad0@adventure-work.com|tad0@adventure-works.com|  
  
6.  <span data-ttu-id="eee89-115">重复前面的步骤，为**Country**域导入项目值，请注意，添加了一个新条目来更正**美国\*\*\*\*美国** (使用 ") "。</span><span class="sxs-lookup"><span data-stu-id="eee89-115">Repeat the previous step of importing project values for the **Country** domain and notice that a new entry is added for correcting **United State** to **United States** (with 's').</span></span>  
  
    |<span data-ttu-id="eee89-116">值</span><span class="sxs-lookup"><span data-stu-id="eee89-116">Value</span></span>|<span data-ttu-id="eee89-117">更正为</span><span class="sxs-lookup"><span data-stu-id="eee89-117">Correct To</span></span>|  
    |-----------|----------------|  
    |<span data-ttu-id="eee89-118">United State</span><span class="sxs-lookup"><span data-stu-id="eee89-118">United State</span></span>|<span data-ttu-id="eee89-119">美国</span><span class="sxs-lookup"><span data-stu-id="eee89-119">United States</span></span>|  
  
7.  <span data-ttu-id="eee89-120">若要查看旧的域值，请清除 "**仅显示新**的" 复选框。</span><span class="sxs-lookup"><span data-stu-id="eee89-120">To see the old domain values, clear **Show Only New** checkbox.</span></span>  
  
8.  <span data-ttu-id="eee89-121">为**供应商名称**域重复导入项目值的上一步。</span><span class="sxs-lookup"><span data-stu-id="eee89-121">Repeat the previous step of importing project values for the **Supplier Name** domain.</span></span> <span data-ttu-id="eee89-122">默认情况下，在导入后，您将只看到新值。</span><span class="sxs-lookup"><span data-stu-id="eee89-122">By default, after importing, you will only see the new values.</span></span> <span data-ttu-id="eee89-123">若要查看所有值，请清除 "**仅显示新**的" 复选框。</span><span class="sxs-lookup"><span data-stu-id="eee89-123">To see all the values, clear **Show Only New** check box.</span></span> <span data-ttu-id="eee89-124">您已经使用了 "清理" 活动中的内容来丰富了**供应商**知识库。</span><span class="sxs-lookup"><span data-stu-id="eee89-124">You have enriched the **Suppliers** knowledge base with what you learned from the cleansing activity.</span></span> <span data-ttu-id="eee89-125">知识库越强，清理结果就越好。</span><span class="sxs-lookup"><span data-stu-id="eee89-125">The stronger the knowledge base is, the better the cleansing results are.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="eee89-126">无法导入复合域的值。</span><span class="sxs-lookup"><span data-stu-id="eee89-126">It is not possible import values for a composite domain.</span></span>  
  
9. <span data-ttu-id="eee89-127">单击工具栏上的 "**导出知识库**" 图标，然后单击 "**导出知识库**"。</span><span class="sxs-lookup"><span data-stu-id="eee89-127">Click **Export Knowledge Base** icon on the toolbar and then click **Export Knowledge Base**.</span></span>  
  
     <span data-ttu-id="eee89-128">![“导出知识库”菜单](../../2014/tutorials/media/et-importingvaluesfromthecslistproject-02.jpg "“导出知识库”菜单")</span><span class="sxs-lookup"><span data-stu-id="eee89-128">![Export Knowledge Base Menu](../../2014/tutorials/media/et-importingvaluesfromthecslistproject-02.jpg "Export Knowledge Base Menu")</span></span>  
  
10. <span data-ttu-id="eee89-129">导航到教程文件夹，键入 "提供**商**" 作为**文件名**，然后单击 "**保存**"。</span><span class="sxs-lookup"><span data-stu-id="eee89-129">Navigate to the Tutorial folder, type **Suppliers.dqs** for the **file name**, and click **Save**.</span></span> <span data-ttu-id="eee89-130">您可以使用此 DQS 文件创建基于此文件的新知识库。</span><span class="sxs-lookup"><span data-stu-id="eee89-130">You can use this DQS file to create a new knowledge base based on it.</span></span>  
  
11. <span data-ttu-id="eee89-131">单击 **"确定"** 关闭 "**导出知识库-供应商**" 消息框。</span><span class="sxs-lookup"><span data-stu-id="eee89-131">Click **OK** to close the **Export Knowledge Base - Suppliers** message box.</span></span>  
  
12. <span data-ttu-id="eee89-132">单击 "**完成**" 完成活动。</span><span class="sxs-lookup"><span data-stu-id="eee89-132">Click **Finish** to finish the activity.</span></span>  
  
13. <span data-ttu-id="eee89-133">单击“发布”。</span><span class="sxs-lookup"><span data-stu-id="eee89-133">Click **Publish**.</span></span>  
  
14. <span data-ttu-id="eee89-134">在消息框中单击 **"确定"** 。</span><span class="sxs-lookup"><span data-stu-id="eee89-134">Click **OK** on the message box.</span></span>  
  
## <a name="next-step"></a><span data-ttu-id="eee89-135">下一步</span><span class="sxs-lookup"><span data-stu-id="eee89-135">Next Step</span></span>  
 [<span data-ttu-id="eee89-136">第 3 课：匹配数据以便从供应商列表中删除重复项</span><span class="sxs-lookup"><span data-stu-id="eee89-136">Lesson 3: Matching Data to Remove Duplicates from Supplier List</span></span>](../../2014/tutorials/lesson-3-matching-data-to-remove-duplicates-from-supplier-list.md)  
  
  
