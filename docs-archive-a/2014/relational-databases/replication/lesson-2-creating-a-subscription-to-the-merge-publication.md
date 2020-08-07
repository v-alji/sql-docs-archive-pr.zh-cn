---
title: 第 2 课：创建合并发布订阅 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- replication [SQL Server], tutorials
ms.assetid: 06722baa-9065-443e-b1d5-99036cf89074
author: rothja
ms.author: jroth
ms.openlocfilehash: 2ca4f9cdf9c40d80b428d65b4201be61c2ea3eae
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87587770"
---
# <a name="lesson-2-creating-a-subscription-to-the-merge-publication"></a><span data-ttu-id="5b56c-102">第 2 课：创建合并发布订阅</span><span class="sxs-lookup"><span data-stu-id="5b56c-102">Lesson 2: Creating a Subscription to the Merge Publication</span></span>
  <span data-ttu-id="5b56c-103">在本课中，将使用 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]创建订阅。</span><span class="sxs-lookup"><span data-stu-id="5b56c-103">In this lesson, you will create the subscription using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].</span></span> <span data-ttu-id="5b56c-104">然后，为订阅数据库设置权限，并手动生成新订阅的筛选数据快照。</span><span class="sxs-lookup"><span data-stu-id="5b56c-104">You will then set permissions on the subscription database and manually generate the filtered data snapshot for the new subscription.</span></span> <span data-ttu-id="5b56c-105">本课程要求已完成上一课， [第 1 课：使用合并复制发布数据](lesson-1-publishing-data-using-merge-replication.md)。</span><span class="sxs-lookup"><span data-stu-id="5b56c-105">This lesson requires that you have completed the previous lesson, [Lesson 1: Publishing Data Using Merge Replication](lesson-1-publishing-data-using-merge-replication.md).</span></span>  
  
### <a name="to-create-the-subscription"></a><span data-ttu-id="5b56c-106">创建订阅</span><span class="sxs-lookup"><span data-stu-id="5b56c-106">To create the subscription</span></span>  
  
1.  <span data-ttu-id="5b56c-107">连接到 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 中的订阅服务器，依次展开服务器节点和“复制”\*\*\*\* 文件夹，右键单击“本地订阅”\*\*\*\* 文件夹，然后单击“新建订阅”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="5b56c-107">Connect to the Subscriber in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], expand the server node, expand the **Replication** folder, right-click the **Local Subscriptions** folder, and then click **New Subscriptions**.</span></span>  
  
     <span data-ttu-id="5b56c-108">新建订阅向导将启动。</span><span class="sxs-lookup"><span data-stu-id="5b56c-108">The New Subscription Wizard launches.</span></span>  
  
2.  <span data-ttu-id="5b56c-109">在“发布”\*\*\*\* 页上，单击“发布服务器”\*\*\*\* 列表中的“查找 SQL Server 发布服务器”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="5b56c-109">On the **Publication** page, click **Find SQL Server Publisher** in the **Publisher** list.</span></span>  
  
3.  <span data-ttu-id="5b56c-110">在“连接到服务器”\*\*\*\* 对话框的“服务器名称”\*\*\*\* 框中，输入发布服务器实例的名称，然后单击“连接”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="5b56c-110">In the **Connect to Server** dialog box, enter the name of the Publisher instance in the **Server name** box, and click **Connect**.</span></span>  
  
4.  <span data-ttu-id="5b56c-111">单击“AdvWorksSalesOrdersMerge”\*\*\*\*，然后单击“下一步”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="5b56c-111">Click **AdvWorksSalesOrdersMerge**, and click **Next**.</span></span>  
  
5.  <span data-ttu-id="5b56c-112">在“合并代理位置”页上，单击“在其订阅服务器上运行每个代理”\*\*\*\*，然后单击“下一步”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="5b56c-112">On the Merge Agent Location page, click **Run each agent at its Subscriber**, and then click **Next**.</span></span>  
  
6.  <span data-ttu-id="5b56c-113">在“订阅服务器”页上，选择订阅服务器的实例名称，然后在“订阅数据库”\*\*\*\* 下，从列表中选择“\<New Database>”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="5b56c-113">On the Subscribers page, select the instance name of the Subscriber server, and under **Subscription Database**, select **\<New Database>** from the list.</span></span>  
  
7.  <span data-ttu-id="5b56c-114">在“新建数据库”\*\*\*\* 对话框的“数据库名称”\*\*\*\* 框中输入 **SalesOrdersReplica**，然后依次单击“确定”\*\*\*\* 和“下一步”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="5b56c-114">In the **New Database** dialog box, enter **SalesOrdersReplica** in the **Database name** box, click **OK**, and then click **Next**.</span></span>  
  
8.  <span data-ttu-id="5b56c-115">在 "合并代理安全" 页上，单击省略号 (**...** ") 按钮， \<_Machine_Name> 在"**进程帐户**"框中输入 _**\ repl_merge** ，为此帐户提供密码，单击 **" 确定**"，单击"**下一**步 "，然后再次单击"**下一步**"。</span><span class="sxs-lookup"><span data-stu-id="5b56c-115">On the Merge Agent Security page, click the ellipsis (**...**) button, enter \<_Machine_Name>_**\repl_merge** in the **Process account** box, supply the password for this account, click **OK**, click **Next**, and then click **Next** again.</span></span>  
  
9. <span data-ttu-id="5b56c-116">在“初始化订阅”页上，从“初始化时间”\*\*\*\* 列表中选择“首次同步时”\*\*\*\*，单击“下一步”\*\*\*\*，然后再次单击“下一步”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="5b56c-116">On the Initialize Subscriptions page, select **At first synchronization** from the **Initialize When** list, click **Next**, and then click **Next** again.</span></span>  
  
10. <span data-ttu-id="5b56c-117">在 "HOST_NAME 值" 页上， `adventure-works\pamela0` 在 " **HOST_NAME 值**" 框中输入值，然后单击 "**完成**"。</span><span class="sxs-lookup"><span data-stu-id="5b56c-117">On the HOST_NAME Values page, enter a value of `adventure-works\pamela0` in the **HOST_NAME Value** box, and then click **Finish**.</span></span>  
  
11. <span data-ttu-id="5b56c-118">再次单击“完成”\*\*\*\*，创建订阅后，单击“关闭”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="5b56c-118">Click **Finish** again, and after the subscription is created, click **Close**.</span></span>  
  
### <a name="setting-database-permissions-at-the-subscriber"></a><span data-ttu-id="5b56c-119">在订阅服务器上设置数据库权限</span><span class="sxs-lookup"><span data-stu-id="5b56c-119">Setting database permissions at the Subscriber</span></span>  
  
1.  <span data-ttu-id="5b56c-120">连接到 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 中的订阅服务器，依次展开“数据库”\*\*\*\*、“SalesOrdersReplica”\*\*\*\* 和“安全性”\*\*\*\*，右键单击“用户”\*\*\*\*，然后选择“新建用户”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="5b56c-120">Connect to the Subscriber in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], expand **Databases**, **SalesOrdersReplica**, and **Security**, right-click **Users**, and then select **New User**.</span></span>  
  
2.  <span data-ttu-id="5b56c-121">在 "**常规**" 页上 \<_Machine_Name> _的 "**用户名**" 框中，输入**\ repl_merge** ，单击省略号 (**...**) "按钮，单击"**浏览**" \<_Machine_Name> ，选择_ **\ repl_merge**，单击 **" 确定**"，再单击"**检查名称**"，然后单击 **" 确定 "**。</span><span class="sxs-lookup"><span data-stu-id="5b56c-121">On the **General** page, enter \<_Machine_Name>_**\repl_merge** in the **User name** box, click the ellipsis (**...**) button, click **Browse**, select \<_Machine_Name>_**\repl_merge**, click **OK**, click **Check Names**, and then click **OK**.</span></span>  
  
3.  <span data-ttu-id="5b56c-122">在“数据库角色成员资格”\*\*\*\* 中，选择“db_owner”\*\*\*\*，然后单击“确定”\*\*\*\* 以创建用户。</span><span class="sxs-lookup"><span data-stu-id="5b56c-122">In **Database role membership**, select **db_owner**, and then click **OK** to create the user.</span></span>  
  
### <a name="to-create-the-filtered-data-snapshot-for-the-subscription"></a><span data-ttu-id="5b56c-123">创建订阅的筛选数据快照</span><span class="sxs-lookup"><span data-stu-id="5b56c-123">To create the filtered data snapshot for the subscription</span></span>  
  
1.  <span data-ttu-id="5b56c-124">在 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 中连接到发布服务器，然后依次展开服务器节点和“复制”\*\*\*\* 文件夹。</span><span class="sxs-lookup"><span data-stu-id="5b56c-124">Connect to the Publisher in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], expand the server node, and then expand the **Replication** folder.</span></span>  
  
2.  <span data-ttu-id="5b56c-125">在“本地发布”\*\*\*\* 文件夹中，右键单击“AdvWorksSalesOrdersMerge”\*\*\*\* 发布，然后单击“属性”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="5b56c-125">In the **Local Publications** folder, right-click the **AdvWorksSalesOrdersMerge** publication, and then click **Properties**.</span></span>  
  
     <span data-ttu-id="5b56c-126">将显示“发布属性”\*\*\*\* 对话框。</span><span class="sxs-lookup"><span data-stu-id="5b56c-126">The **Publication Properties** dialog box is displayed.</span></span>  
  
3.  <span data-ttu-id="5b56c-127">选择“数据分区”\*\*\*\* 页，然后单击“添加”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="5b56c-127">Select the **Data Partitions** page, and click **Add**.</span></span>  
  
4.  <span data-ttu-id="5b56c-128">在 "**添加数据分区**" 对话框中，在 `adventure-works\pamela0` " **HOST_NAME 值**" 框中键入，然后单击 **"确定"**。</span><span class="sxs-lookup"><span data-stu-id="5b56c-128">In the **Add Data Partition** dialog box, type `adventure-works\pamela0` in the **HOST_NAME Value** box, and then click **OK**.</span></span>  
  
5.  <span data-ttu-id="5b56c-129">选择新添加的分区，单击“立即生成所选快照”\*\*\*\*，然后单击“确定”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="5b56c-129">Select the newly added partition, click **Generate the selected snapshots now**, and then click **OK**.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="5b56c-130">后续步骤</span><span class="sxs-lookup"><span data-stu-id="5b56c-130">Next Steps</span></span>  
 <span data-ttu-id="5b56c-131">您已经成功地对合并发布创建了一个订阅，并且为该新订阅的数据分区生成了筛选快照，因此初始化订阅后即可使用此筛选快照。</span><span class="sxs-lookup"><span data-stu-id="5b56c-131">You have successfully created a subscription to the merge publication and generated the filtered snapshot for the new subscription's data partition so that it will be available when the subscription is initialized.</span></span> <span data-ttu-id="5b56c-132">接下来，您将对订阅数据库的合并代理授予权限，并且运行合并代理来启动订阅的同步和初始化操作。</span><span class="sxs-lookup"><span data-stu-id="5b56c-132">Next, you will grant rights to the Merge Agent on the subscription database and run the Merge Agent to start synchronization and initialize the subscription.</span></span> <span data-ttu-id="5b56c-133">请参阅 [第 3 课：使订阅与合并发布同步](lesson-3-synchronizing-the-subscription-to-the-merge-publication.md)。</span><span class="sxs-lookup"><span data-stu-id="5b56c-133">See [Lesson 3: Synchronizing the Subscription to the Merge Publication](lesson-3-synchronizing-the-subscription-to-the-merge-publication.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5b56c-134">另请参阅</span><span class="sxs-lookup"><span data-stu-id="5b56c-134">See Also</span></span>  
 <span data-ttu-id="5b56c-135">[Subscribe to Publications](subscribe-to-publications.md) </span><span class="sxs-lookup"><span data-stu-id="5b56c-135">[Subscribe to Publications](subscribe-to-publications.md) </span></span>  
 <span data-ttu-id="5b56c-136">[Create a Pull Subscription](create-a-pull-subscription.md) </span><span class="sxs-lookup"><span data-stu-id="5b56c-136">[Create a Pull Subscription](create-a-pull-subscription.md) </span></span>  
 [<span data-ttu-id="5b56c-137">Snapshots for Merge Publications with Parameterized Filters</span><span class="sxs-lookup"><span data-stu-id="5b56c-137">Snapshots for Merge Publications with Parameterized Filters</span></span>](snapshots-for-merge-publications-with-parameterized-filters.md)  
  
  
