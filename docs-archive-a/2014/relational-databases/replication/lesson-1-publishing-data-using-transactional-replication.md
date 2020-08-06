---
title: 第 1 课：使用事务复制发布数据 | Microsoft Docs
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- replication [SQL Server], tutorials
ms.assetid: 9c55aa3c-4664-41fc-943f-e817c31aad5e
author: rothja
ms.author: jroth
ms.openlocfilehash: ce20f4ed8863ede34c8709d2b77bf032e7d14a97
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87687755"
---
# <a name="lesson-1-publishing-data-using-transactional-replication"></a><span data-ttu-id="73c00-102">第 1 课：使用事务复制发布数据</span><span class="sxs-lookup"><span data-stu-id="73c00-102">Lesson 1: Publishing Data Using Transactional Replication</span></span>
  <span data-ttu-id="73c00-103">在本课中，使用 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 创建一个事务发布，以便在 [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] 示例数据库中发布“Product”表的筛选子集\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="73c00-103">In this lesson, you will create a transactional publication using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] to publish a filtered subset of the **Product** table in the [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] sample database.</span></span> <span data-ttu-id="73c00-104">您还要将分发代理使用的 SQL Server 登录名添加到发布访问列表 (PAL)。</span><span class="sxs-lookup"><span data-stu-id="73c00-104">You will also add the SQL Server login used by the Distribution Agent to the publication access list (PAL).</span></span> <span data-ttu-id="73c00-105">开始本教程之前，应已完成上一个教程 [准备用于复制的服务器](tutorial-preparing-the-server-for-replication.md)。</span><span class="sxs-lookup"><span data-stu-id="73c00-105">Before starting this tutorial, you should have completed the previous tutorial, [Preparing the Server for Replication](tutorial-preparing-the-server-for-replication.md).</span></span>  
  
### <a name="to-create-a-publication-and-define-articles"></a><span data-ttu-id="73c00-106">创建发布和定义项目</span><span class="sxs-lookup"><span data-stu-id="73c00-106">To create a publication and define articles</span></span>  
  
1.  <span data-ttu-id="73c00-107">在 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]中连接到发布服务器，然后展开服务器节点。</span><span class="sxs-lookup"><span data-stu-id="73c00-107">Connect to the Publisher in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], and then expand the server node.</span></span>  
  
2.  <span data-ttu-id="73c00-108">展开“复制”文件夹，右键单击“本地发布”文件夹，再单击“新建发布”。\*\*\*\*\*\*\*\*\*\*\*\*</span><span class="sxs-lookup"><span data-stu-id="73c00-108">Expand the **Replication** folder, right-click the **Local Publications** folder, and click **New Publication**.</span></span>  
  
     <span data-ttu-id="73c00-109">将启动发布配置向导。</span><span class="sxs-lookup"><span data-stu-id="73c00-109">The Publication Configuration Wizard launches.</span></span>  
  
3.  <span data-ttu-id="73c00-110">在“发布数据库”页上，选择 [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)]，然后单击“下一步”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="73c00-110">On the Publication Database page, select [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)], and then click **Next**.</span></span>  
  
4.  <span data-ttu-id="73c00-111">在“发布类型”页上，选择“事务发布”\*\*\*\*，然后单击“下一步”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="73c00-111">On the Publication Type page, select **Transactional publication**, and then click **Next**.</span></span>  
  
5.  <span data-ttu-id="73c00-112">在“项目”页上，展开“表”\*\*\*\* 节点，选中“Product”\*\*\*\* 复选框，然后展开“Product”\*\*\*\* 并取消选中“ListPrice”\*\*\*\* 和“StandardCost”\*\*\*\* 复选框。</span><span class="sxs-lookup"><span data-stu-id="73c00-112">On the Articles page, expand the **Tables** node, select the **Product** check box, then expand **Product** and clear the **ListPrice** and **StandardCost** check boxes.</span></span> <span data-ttu-id="73c00-113">单击“下一步”。</span><span class="sxs-lookup"><span data-stu-id="73c00-113">Click **Next**.</span></span>  
  
6.  <span data-ttu-id="73c00-114">在“筛选表行”页上，单击“添加”。\*\*\*\*</span><span class="sxs-lookup"><span data-stu-id="73c00-114">On the Filter Table Rows page, click **Add**.</span></span>  
  
7.  <span data-ttu-id="73c00-115">在“添加筛选器”\*\*\*\* 对话框中，单击 **SafetyStockLevel** 列，再单击向右箭头以将此列添加到筛选查询的筛选语句的 WHERE 子句，并修改 WHERE 子句，如下所示：</span><span class="sxs-lookup"><span data-stu-id="73c00-115">In the **Add Filter** dialog box, click the **SafetyStockLevel** column, click the right arrow to add the column to the Filter statement WHERE clause of the filter query, and modify the WHERE clause as follows:</span></span>  
  
    ```  
    WHERE [SafetyStockLevel] < 500  
    ```  
  
8.  <span data-ttu-id="73c00-116">单击 **“确定”**，然后单击 **“下一步”**。</span><span class="sxs-lookup"><span data-stu-id="73c00-116">Click **OK**, and then click **Next**.</span></span>  
  
9. <span data-ttu-id="73c00-117">选中“立即创建快照并使快照保持可用状态，以初始化订阅”\*\*\*\* 复选框，单击“下一步”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="73c00-117">Select the **Create a snapshot immediately and keep the snapshot available to initialize subscriptions** check box, and click **Next**.</span></span>  
  
10. <span data-ttu-id="73c00-118">在“代理安全性”页上，清除“使用快照代理的安全设置”\*\*\*\* 复选框。</span><span class="sxs-lookup"><span data-stu-id="73c00-118">On the Agent Security page, clear **Use the security settings from the Snapshot Agent** check box.</span></span>  
  
11. <span data-ttu-id="73c00-119">单击 "快照代理的"**安全设置**"， \<_Machine_Name> 在"**进程帐户**"框中输入 _**\ repl_snapshot** ，为此帐户提供密码，然后单击 **" 确定 "**。</span><span class="sxs-lookup"><span data-stu-id="73c00-119">Click **Security Settings** for the Snapshot Agent, enter \<_Machine_Name>_**\repl_snapshot** in the **Process account** box, supply the password for this account, and then click **OK**.</span></span>  
  
12. <span data-ttu-id="73c00-120">重复上一步，将 repl_logreader 设置为日志读取器代理的进程帐户，然后单击“完成”。\*\*\*\*</span><span class="sxs-lookup"><span data-stu-id="73c00-120">Repeat the previous step to set repl_logreader as the process account for the Log Reader Agent, and then click **Finish**.</span></span>  
  
13. <span data-ttu-id="73c00-121">在“完成向导”页的“发布名称”\*\*\*\* 框中，键入 **AdvWorksProductTrans**，然后单击“完成”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="73c00-121">On the Complete the Wizard page, type **AdvWorksProductTrans** in the **Publication name** box, and click **Finish**.</span></span>  
  
14. <span data-ttu-id="73c00-122">创建发布后，单击“关闭”\*\*\*\* 完成该向导。</span><span class="sxs-lookup"><span data-stu-id="73c00-122">After the publication is created, click **Close** to complete the wizard.</span></span>  
  
### <a name="to-view-the-status-of-snapshot-generation"></a><span data-ttu-id="73c00-123">查看快照的生成状态</span><span class="sxs-lookup"><span data-stu-id="73c00-123">To view the status of snapshot generation</span></span>  
  
1.  <span data-ttu-id="73c00-124">在 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 中连接到发布服务器，然后依次展开服务器节点和“复制”\*\*\*\* 文件夹。</span><span class="sxs-lookup"><span data-stu-id="73c00-124">Connect to the Publisher in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], expand the server node, and then expand the **Replication** folder.</span></span>  
  
2.  <span data-ttu-id="73c00-125">在“本地发布”\*\*\*\* 文件夹中，右键单击 **AdvWorksProductTrans**，再单击“查看快照代理状态”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="73c00-125">In the **Local Publications** folder, right-click **AdvWorksProductTrans**, and then click **View Snapshot Agent Status**.</span></span>  
  
3.  <span data-ttu-id="73c00-126">将显示该发布的快照代理作业的当前状态。</span><span class="sxs-lookup"><span data-stu-id="73c00-126">The current status of the Snapshot Agent job for the publication is displayed.</span></span> <span data-ttu-id="73c00-127">继续下一课之前，请确保快照作业已成功完成。</span><span class="sxs-lookup"><span data-stu-id="73c00-127">Verify that the snapshot job has succeeded before you continue to the next lesson.</span></span>  
  
### <a name="to-add-the-distribution-agent-login-to-the-pal"></a><span data-ttu-id="73c00-128">将分发代理登录名添加到 PAL</span><span class="sxs-lookup"><span data-stu-id="73c00-128">To add the Distribution Agent login to the PAL</span></span>  
  
1.  <span data-ttu-id="73c00-129">在 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 中连接到发布服务器，然后依次展开服务器节点和“复制”\*\*\*\* 文件夹。</span><span class="sxs-lookup"><span data-stu-id="73c00-129">Connect to the Publisher in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], expand the server node, and then expand the **Replication** folder.</span></span>  
  
2.  <span data-ttu-id="73c00-130">在“本地发布”\*\*\*\* 文件夹中，右键单击 **AdvWorksProductTrans**，再单击“属性”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="73c00-130">In the **Local Publications** folder, right-click **AdvWorksProductTrans**, and then click **Properties**.</span></span>  
  
     <span data-ttu-id="73c00-131">将显示“发布属性”\*\*\*\* 对话框。</span><span class="sxs-lookup"><span data-stu-id="73c00-131">The **Publication Properties** dialog box is displayed.</span></span>  
  
3.  <span data-ttu-id="73c00-132">选择“发布访问列表”\*\*\*\* 页，单击“添加”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="73c00-132">Select the **Publication Access List** page, and click **Add**.</span></span>  
  
4.  <span data-ttu-id="73c00-133">\在“添加发布访问项”\*\*\*\* 对话框中，选择 _<Machine_Name>_**\repl_distribution**，再单击“确定”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="73c00-133">\In the **Add Publication Access** dialog box, select _<Machine_Name>_**\repl_distribution** and click **OK**.</span></span> <span data-ttu-id="73c00-134">单击“确定”  。</span><span class="sxs-lookup"><span data-stu-id="73c00-134">Click **OK**.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="73c00-135">后续步骤</span><span class="sxs-lookup"><span data-stu-id="73c00-135">Next Steps</span></span>  
 <span data-ttu-id="73c00-136">您已成功创建了事务发布。</span><span class="sxs-lookup"><span data-stu-id="73c00-136">You have successfully created the transactional publication.</span></span> <span data-ttu-id="73c00-137">接下来，您将订阅此发布。</span><span class="sxs-lookup"><span data-stu-id="73c00-137">Next, you will subscribe to this publication.</span></span> <span data-ttu-id="73c00-138">请参阅 [第 2 课：创建事务发布的订阅](lesson-2-creating-a-subscription-to-the-transactional-publication.md)。</span><span class="sxs-lookup"><span data-stu-id="73c00-138">See [Lesson 2: Creating a Subscription to the Transactional Publication](lesson-2-creating-a-subscription-to-the-transactional-publication.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="73c00-139">另请参阅</span><span class="sxs-lookup"><span data-stu-id="73c00-139">See Also</span></span>  
 <span data-ttu-id="73c00-140">[筛选已发布数据](publish/filter-published-data.md) </span><span class="sxs-lookup"><span data-stu-id="73c00-140">[Filter Published Data](publish/filter-published-data.md) </span></span>  
 <span data-ttu-id="73c00-141">[Define an Article](publish/define-an-article.md) </span><span class="sxs-lookup"><span data-stu-id="73c00-141">[Define an Article](publish/define-an-article.md) </span></span>  
 [<span data-ttu-id="73c00-142">创建并应用快照</span><span class="sxs-lookup"><span data-stu-id="73c00-142">Create and Apply the Snapshot</span></span>](create-and-apply-the-snapshot.md)  
  
  
