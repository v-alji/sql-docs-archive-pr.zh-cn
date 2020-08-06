---
title: 第 1 课：使用合并复制发布数据 | Microsoft Docs
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- replication [SQL Server], tutorials
ms.assetid: c3c6e0b6-54cd-4b7d-8efb-2cefe14fcd7f
author: rothja
ms.author: jroth
ms.openlocfilehash: ba1d8829d84c02d1436013af80de4bf0979049e4
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87691685"
---
# <a name="lesson-1-publishing-data-using-merge-replication"></a><span data-ttu-id="2282a-102">第 1 课：使用合并复制发布数据</span><span class="sxs-lookup"><span data-stu-id="2282a-102">Lesson 1: Publishing Data Using Merge Replication</span></span>
  <span data-ttu-id="2282a-103">在本课中，你将使用 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 创建合并复制以在 **示例数据库中发布**Employee **、** SalesOrderHeader **和** SalesOrderDetail [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] 表的子集。</span><span class="sxs-lookup"><span data-stu-id="2282a-103">In this lesson, you will create a merge publication using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] to publish a subset of the **Employee**, **SalesOrderHeader**, and **SalesOrderDetail** tables in the [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] sample database.</span></span> <span data-ttu-id="2282a-104">这些表用参数化行筛选器进行筛选，以便每个订阅都包含唯一的数据分区。</span><span class="sxs-lookup"><span data-stu-id="2282a-104">These tables are filtered with parameterized row filters so that each subscription contains a unique partition of the data.</span></span> <span data-ttu-id="2282a-105">你还要将合并代理使用的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 登录名添加到发布访问列表 (PAL) 中。</span><span class="sxs-lookup"><span data-stu-id="2282a-105">You will also add the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] login used by the Merge Agent to the publication access list (PAL).</span></span> <span data-ttu-id="2282a-106">本教程要求你完成上一个教程， [准备用于复制的服务器](tutorial-preparing-the-server-for-replication.md)的学习。</span><span class="sxs-lookup"><span data-stu-id="2282a-106">This tutorial requires that you have completed the previous tutorial, [Preparing the Server for Replication](tutorial-preparing-the-server-for-replication.md).</span></span>  
  
### <a name="to-create-a-publication-and-define-articles"></a><span data-ttu-id="2282a-107">创建发布和定义项目</span><span class="sxs-lookup"><span data-stu-id="2282a-107">To create a publication and define articles</span></span>  
  
1.  <span data-ttu-id="2282a-108">在 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]中连接到发布服务器，然后展开服务器节点。</span><span class="sxs-lookup"><span data-stu-id="2282a-108">Connect to the Publisher in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], and then expand the server node.</span></span>  
  
2.  <span data-ttu-id="2282a-109">展开“复制”\*\*\*\* 文件夹，右键单击“本地发布”\*\*\*\*，再单击“新建发布”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="2282a-109">Expand the **Replication** folder, right-click **Local Publications**, and click **New Publication**.</span></span>  
  
     <span data-ttu-id="2282a-110">将启动发布配置向导。</span><span class="sxs-lookup"><span data-stu-id="2282a-110">The Publication Configuration Wizard launches.</span></span>  
  
3.  <span data-ttu-id="2282a-111">在“发布数据库”页上，选择 [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)]，然后单击“下一步”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="2282a-111">On the Publication Database page, select [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)], and then click **Next**.</span></span>  
  
4.  <span data-ttu-id="2282a-112">在“发布类型”页上，选择“合并发布”\*\*\*\*，然后单击“下一步”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="2282a-112">On the Publication Type page, select **Merge publication**, and then click **Next**.</span></span>  
  
5.  <span data-ttu-id="2282a-113">在“订阅服务器类型”页上，确保仅选中了 [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] 或更高版本，然后单击“下一步”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="2282a-113">On the Subscriber Types page, ensure that only [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] or later is selected, and then click **Next**.</span></span>  
  
6.  <span data-ttu-id="2282a-114">在“项目”页上，展开“表”\*\*\*\* 节点，选择“SalesOrderHeader”\*\*\*\* 和“SalesOrderDetail”\*\*\*\*，然后展开“Employee”\*\*\*\*，选择“EmployeeID”\*\*\*\* 或“LoginID”\*\*\*\*，然后单击“下一步”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="2282a-114">On the Articles page, expand the **Tables** node, select **SalesOrderHeader** and **SalesOrderDetail**, then expand **Employee**, select **EmployeeID** or **LoginID**, and then click **Next**.</span></span>  
  
    > [!TIP]  
    >  <span data-ttu-id="2282a-115">将自动选择所需的其他列。</span><span class="sxs-lookup"><span data-stu-id="2282a-115">Additional required columns are automatically selected.</span></span> <span data-ttu-id="2282a-116">选择任一自动选择的列并查看“要发布的对象”\*\*\*\* 列表下有关解释列为必需的原因的说明。</span><span class="sxs-lookup"><span data-stu-id="2282a-116">Select any of  the automatically selected columns and view the note below the **Objects to publish** list for an explanation why the column is required.</span></span>  
  
7.  <span data-ttu-id="2282a-117">在“筛选表行”页上，单击“添加”\*\*\*\*，然后单击“添加筛选器”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="2282a-117">On the Filter Table Rows page, click **Add** and then click **Add Filter**.</span></span>  
  
8.  <span data-ttu-id="2282a-118">在“添加筛选器”\*\*\*\* 对话框的“选择要筛选的表”\*\*\*\* 中，选择“Employee (HumanResources)”\*\*\*\*，单击“LoginID”\*\*\*\* 列，再单击向右箭头以将此列添加到筛选查询的 WHERE 子句中，并将 WHERE 子句修改如下：</span><span class="sxs-lookup"><span data-stu-id="2282a-118">In the **Add Filter** dialog box, select **Employee (HumanResources)** in **Select the table to filter**, click the **LoginID** column, click the right arrow to add the column to the WHERE clause of the filter query, and modify the WHERE clause as follows:</span></span>  
  
    ```  
    WHERE [LoginID] = HOST_NAME()  
    ```  
  
9. <span data-ttu-id="2282a-119">单击“此表中的行将仅转到一个订阅”\*\*\*\*，再单击“确定”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="2282a-119">Click **A row from this table will go to only one subscription**, and click **OK**.</span></span>  
  
10. <span data-ttu-id="2282a-120">在“筛选表行”\*\*\*\* 页上，单击“Employee (Human Resources)”\*\*\*\*，单击“添加”\*\*\*\*，然后单击“添加联接以扩展所选筛选器”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="2282a-120">On the **Filter Table Rows** page, click **Employee (Human Resources)**, click **Add,** and then click **Add Join to Extend the Selected Filter**.</span></span>  
  
11. <span data-ttu-id="2282a-121">在“添加联接”\*\*\*\* 对话框的“联接的表”\*\*\*\* 下，选择“Sales.SalesOrderHeader”\*\*\*\*，然后单击“手动编写联接语句”\*\*\*\*，将联接语句完成如下：</span><span class="sxs-lookup"><span data-stu-id="2282a-121">In the **Add Join** dialog box, select **Sales.SalesOrderHeader** under **Joined table**, click **Write the join statement manually**, and complete the join statement as follows:</span></span>  
  
    ```  
    ON Employee.EmployeeID = SalesOrderHeader.SalesPersonID  
    ```  
  
12. <span data-ttu-id="2282a-122">在“指定联接选项”\*\*\*\* 中，选择“唯一键”\*\*\*\*，然后单击“确定”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="2282a-122">In **Specify join options**, select **Unique key**, and then click **OK**.</span></span>  
  
13. <span data-ttu-id="2282a-123">在“筛选表行”页上，单击“SalesOrderHeader”\*\*\*\*，再单击“添加”\*\*\*\*，然后单击“添加联接以扩展所选筛选器”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="2282a-123">On the Filter Table Rows page, click **SalesOrderHeader**, click **Add**, and then click **Add Join to Extend the Selected Filter**.</span></span>  
  
14. <span data-ttu-id="2282a-124">在“添加联接”\*\*\*\* 对话框的“联接的表”\*\*\*\* 下，选择“Sales.SalesOrderDetail”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="2282a-124">In the **Add Join** dialog box, select **Sales.SalesOrderDetail** under **Joined table**.</span></span>  
  
15. <span data-ttu-id="2282a-125">单击“手动编写联接语句”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="2282a-125">Click **Write the join statement manually**.</span></span>  
  
16. <span data-ttu-id="2282a-126">在“筛选的表列”\*\*\*\* 中，选择“BusinessEntityID”\*\*\*\*，然后单击箭头按钮将列名称复制到联接语句。</span><span class="sxs-lookup"><span data-stu-id="2282a-126">In **Filtered table columns**, select **BusinessEntityID**, then click the arrow button to copy the column name to the loin statement.</span></span>  
  
17. <span data-ttu-id="2282a-127">在“联接语句”\*\*\*\* 框中，按如下所示完成联接语句：</span><span class="sxs-lookup"><span data-stu-id="2282a-127">In the **Join statement** box, complete the join statement as follows:</span></span>  
  
    ```  
    ON Employee.BusinessEntityID = SalesOrderHeader.SalesPersonID  
    ```  
  
18. <span data-ttu-id="2282a-128">在“指定联接选项”\*\*\*\* 中，选择“唯一键”\*\*\*\*，然后单击“确定”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="2282a-128">In **Specify join options**, select **Unique key**, and then click **OK**.</span></span>  
  
19. <span data-ttu-id="2282a-129">在“筛选表行”\*\*\*\* 页上，单击“SalesOrderHeader (Sales)”\*\*\*\*，再单击“添加”\*\*\*\*，然后单击“添加联接以扩展所选筛选器”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="2282a-129">On the **Filter Table Rows** page, click **SalesOrderHeader (Sales)**, click **Add**, and then click **Add Join to Extend the Selected Filter**.</span></span>  
  
20. <span data-ttu-id="2282a-130">在“添加联接”\*\*\*\* 对话框的“联接的表”\*\*\*\* 下，选择“Sales.SalesOrderDetail”\*\*\*\*，单击“确定”\*\*\*\*，然后单击“下一步”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="2282a-130">In the **Add Join** dialog box, select **Sales.SalesOrderDetail** under **Joined table**, click **OK**, and then click **Next**.</span></span>  
  
21. <span data-ttu-id="2282a-131">选中“立即创建快照”\*\*\*\*，清除“计划在以下时间运行快照代理”\*\*\*\*，然后单击“下一步”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="2282a-131">Select **Create a snapshot immediately**, clear **Schedule the snapshot agent to run at the following times**, and click **Next**.</span></span>  
  
22. <span data-ttu-id="2282a-132">在 "代理安全性" 页上，单击 "**安全设置**"， \<_Machine_Name> 在 "**进程帐户**" 框中键入 _**\ repl_snapshot** ，为此帐户提供密码，然后单击 **"确定"**。</span><span class="sxs-lookup"><span data-stu-id="2282a-132">On the Agent Security page, click **Security Settings**, type \<_Machine_Name>_**\repl_snapshot** in the **Process account** box, supply the password for this account, and then click **OK**.</span></span> <span data-ttu-id="2282a-133">单击“完成”。</span><span class="sxs-lookup"><span data-stu-id="2282a-133">Click **Finish**.</span></span>  
  
23. <span data-ttu-id="2282a-134">在“完成该向导”页的“发布名称”\*\*\*\* 框中，输入 **AdvWorksSalesOrdersMerge**，然后单击“完成”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="2282a-134">On the Complete the Wizard page, enter **AdvWorksSalesOrdersMerge** in the **Publication name** box and click **Finish**.</span></span>  
  
24. <span data-ttu-id="2282a-135">创建发布后，单击“关闭”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="2282a-135">After the publication is created, click **Close**.</span></span>  
  
### <a name="to-view-the-status-of-snapshot-generation"></a><span data-ttu-id="2282a-136">查看快照的生成状态</span><span class="sxs-lookup"><span data-stu-id="2282a-136">To view the status of snapshot generation</span></span>  
  
1.  <span data-ttu-id="2282a-137">在 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 中连接到发布服务器，然后依次展开服务器节点和“复制”\*\*\*\* 文件夹。</span><span class="sxs-lookup"><span data-stu-id="2282a-137">Connect to the Publisher in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], expand the server node, and then expand the **Replication** folder.</span></span>  
  
2.  <span data-ttu-id="2282a-138">在“本地发布”文件夹中，右键单击 **AdvWorksSalesOrdersMerge**，再单击“查看快照代理状态”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="2282a-138">In the Local Publications folder, right-click **AdvWorksSalesOrdersMerge**, and then click **View Snapshot Agent Status**.</span></span>  
  
3.  <span data-ttu-id="2282a-139">将显示该发布的快照代理作业的当前状态。</span><span class="sxs-lookup"><span data-stu-id="2282a-139">The current status of the Snapshot Agent job for the publication is displayed.</span></span> <span data-ttu-id="2282a-140">继续下一课之前，请确保快照作业已成功完成。</span><span class="sxs-lookup"><span data-stu-id="2282a-140">Ensure that the snapshot job has succeeded before you continue to the next lesson.</span></span>  
  
### <a name="to-add-the-merge-agent-login-to-the-pal"></a><span data-ttu-id="2282a-141">将合并代理登录名添加到 PAL</span><span class="sxs-lookup"><span data-stu-id="2282a-141">To add the Merge Agent login to the PAL</span></span>  
  
1.  <span data-ttu-id="2282a-142">在 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 中连接到发布服务器，然后依次展开服务器节点和“复制”\*\*\*\* 文件夹。</span><span class="sxs-lookup"><span data-stu-id="2282a-142">Connect to the Publisher in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], expand the server node, and then expand the **Replication** folder.</span></span>  
  
2.  <span data-ttu-id="2282a-143">在“本地发布”文件夹中，右键单击 **AdvWorksSalesOrdersMerge**，再单击“属性”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="2282a-143">In the Local Publications folder, right-click **AdvWorksSalesOrdersMerge**, and then click **Properties**.</span></span>  
  
     <span data-ttu-id="2282a-144">将显示“发布属性”\*\*\*\* 对话框。</span><span class="sxs-lookup"><span data-stu-id="2282a-144">The **Publication Properties** dialog box is displayed.</span></span>  
  
3.  <span data-ttu-id="2282a-145">选择“发布访问列表”\*\*\*\* 页，单击“添加”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="2282a-145">Select the **Publication Access List** page, and click **Add**.</span></span>  
  
4.  <span data-ttu-id="2282a-146">在“添加发布访问项”对话框中，选择 Machine_Name__**\repl_merge**，然后单击“确定”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="2282a-146">In the Add Publication Access dialog box, select _<Machine_Name>_**\repl_merge** and click **OK**.</span></span> <span data-ttu-id="2282a-147">单击“确定”  。</span><span class="sxs-lookup"><span data-stu-id="2282a-147">Click **OK**.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="2282a-148">后续步骤</span><span class="sxs-lookup"><span data-stu-id="2282a-148">Next Steps</span></span>  
 <span data-ttu-id="2282a-149">您已成功创建了合并发布。</span><span class="sxs-lookup"><span data-stu-id="2282a-149">You have successfully created the merge publication.</span></span> <span data-ttu-id="2282a-150">接下来，您将订阅此发布。</span><span class="sxs-lookup"><span data-stu-id="2282a-150">Next, you will subscribe to this publication.</span></span> <span data-ttu-id="2282a-151">请参阅 [第 2 课：创建合并发布订阅](lesson-2-creating-a-subscription-to-the-merge-publication.md)。</span><span class="sxs-lookup"><span data-stu-id="2282a-151">See [Lesson 2: Creating a Subscription to the Merge Publication](lesson-2-creating-a-subscription-to-the-merge-publication.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2282a-152">另请参阅</span><span class="sxs-lookup"><span data-stu-id="2282a-152">See Also</span></span>  
 <span data-ttu-id="2282a-153">[筛选已发布数据](publish/filter-published-data.md) </span><span class="sxs-lookup"><span data-stu-id="2282a-153">[Filter Published Data](publish/filter-published-data.md) </span></span>  
 <span data-ttu-id="2282a-154">[Parameterized Row Filters](merge/parameterized-filters-parameterized-row-filters.md) </span><span class="sxs-lookup"><span data-stu-id="2282a-154">[Parameterized Row Filters](merge/parameterized-filters-parameterized-row-filters.md) </span></span>  
 [<span data-ttu-id="2282a-155">定义项目</span><span class="sxs-lookup"><span data-stu-id="2282a-155">Define an Article</span></span>](publish/define-an-article.md)  
  
  
