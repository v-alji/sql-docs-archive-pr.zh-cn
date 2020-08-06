---
title: 第 2 课：创建事务发布的订阅 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- replication [SQL Server], tutorials
ms.assetid: 5995b7d2-7c06-46f5-b96c-2bee879bcda2
author: rothja
ms.author: jroth
ms.openlocfilehash: dbf40fa259302dffdd6c0b8e8717b7c35b0cf92d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87578059"
---
# <a name="lesson-2-creating-a-subscription-to-the-transactional-publication"></a><span data-ttu-id="8d5b8-102">第 2 课：创建事务发布的订阅</span><span class="sxs-lookup"><span data-stu-id="8d5b8-102">Lesson 2: Creating a Subscription to the Transactional Publication</span></span>
  <span data-ttu-id="8d5b8-103">在本课程中，将使用 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]创建一个订阅。</span><span class="sxs-lookup"><span data-stu-id="8d5b8-103">In this lesson, you will create a subscription using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].</span></span> <span data-ttu-id="8d5b8-104">本课程要求已完成上一课， [第 1 课：使用事务复制发布数据](lesson-1-publishing-data-using-transactional-replication.md)。</span><span class="sxs-lookup"><span data-stu-id="8d5b8-104">This lesson requires that you have completed the previous lesson, [Lesson 1: Publishing Data Using Transactional Replication](lesson-1-publishing-data-using-transactional-replication.md).</span></span>  
  
### <a name="to-create-the-subscription"></a><span data-ttu-id="8d5b8-105">创建订阅</span><span class="sxs-lookup"><span data-stu-id="8d5b8-105">To create the subscription</span></span>  
  
1.  <span data-ttu-id="8d5b8-106">在 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 中连接到发布服务器，然后依次展开服务器节点和“复制”\*\*\*\* 文件夹。</span><span class="sxs-lookup"><span data-stu-id="8d5b8-106">Connect to the Publisher in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], expand the server node, and then expand the **Replication** folder.</span></span>  
  
2.  <span data-ttu-id="8d5b8-107">在“本地发布”\*\*\*\* 文件夹中，右键单击“AdvWorksProductTrans”\*\*\*\* 发布，然后单击“新建订阅”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="8d5b8-107">In the **Local Publications** folder, right-click the **AdvWorksProductTrans** publication, and then click **New Subscriptions**.</span></span>  
  
     <span data-ttu-id="8d5b8-108">新建订阅向导将启动。</span><span class="sxs-lookup"><span data-stu-id="8d5b8-108">The New Subscription Wizard launches.</span></span>  
  
3.  <span data-ttu-id="8d5b8-109">在“发布”页上，选择“AdvWorksProductTrans”\*\*\*\*，然后单击“下一步”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="8d5b8-109">On the Publication page, select **AdvWorksProductTrans**, and then click **Next**.</span></span>  
  
4.  <span data-ttu-id="8d5b8-110">在“分发代理位置”页上，选择“在分发服务器上运行所有代理”\*\*\*\*，然后单击“下一步”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="8d5b8-110">On the Distribution Agent Location page, select **Run all agents at the Distributor**, and then click **Next**.</span></span>  
  
5.  <span data-ttu-id="8d5b8-111">在“订阅服务器”页上，如果未显示订阅服务器实例名称，请单击“添加订阅服务器”\*\*\*\*，然后单击“添加 SQL Server 订阅服务器”\*\*\*\*，在“连接到服务器”\*\*\*\* 对话框中输入订阅服务器实例名称，然后单击“连接”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="8d5b8-111">On the Subscribers page, if the name of the Subscriber instance is not displayed, click **Add Subscriber**, click **Add SQL Server Subscriber**, enter the Subscriber instance name in the **Connect to Server** dialog box, and then click **Connect**.</span></span>  
  
6.  <span data-ttu-id="8d5b8-112">在 "订阅服务器" 页上，选择订阅服务器的实例名称，然后 **\<New Database>** 在 "**订阅数据库**" 下选择。</span><span class="sxs-lookup"><span data-stu-id="8d5b8-112">On the Subscribers page, select the instance name of the Subscriber server, and select **\<New Database>** under **Subscription Database**.</span></span>  
  
7.  <span data-ttu-id="8d5b8-113">在“新建数据库”\*\*\*\* 对话框的“数据库名称”\*\*\*\* 框中输入“ProductReplica”\*\*\*\*，然后依次单击“确定”\*\*\*\* 和“下一步”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="8d5b8-113">On the **New Database** dialog box, enter **ProductReplica** in the **Database name** box, click **OK**, and then click **Next**.</span></span>  
  
8.  <span data-ttu-id="8d5b8-114">在 "**分发代理安全性**" 对话框中，单击省略号 (**...** ") 按钮， \<_Machine_Name> 在"**进程帐户**"框中输入 _**\ repl_distribution** ，输入此帐户的密码，单击 **" 确定**"，然后单击"**下一步**"。</span><span class="sxs-lookup"><span data-stu-id="8d5b8-114">In the **Distribution Agent Security** dialog box, click the ellipsis (**...**) button, enter \<_Machine_Name>_**\repl_distribution** in the **Process account** box, enter the password for this account, click **OK**, and then click **Next**.</span></span>  
  
9. <span data-ttu-id="8d5b8-115">单击“完成”\*\*\*\* 以接受其余页中的默认值并完成向导。</span><span class="sxs-lookup"><span data-stu-id="8d5b8-115">Click **Finish** to accept the default values on the remaining pages and complete the wizard.</span></span>  
  
### <a name="setting-database-permissions-at-the-subscriber"></a><span data-ttu-id="8d5b8-116">在订阅服务器上设置数据库权限</span><span class="sxs-lookup"><span data-stu-id="8d5b8-116">Setting database permissions at the Subscriber</span></span>  
  
1.  <span data-ttu-id="8d5b8-117">连接到 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 中的订阅服务器，依次展开“数据库”\*\*\*\*、“ProductReplica”\*\*\*\* 和“安全性”\*\*\*\*，右键单击“用户”\*\*\*\*，然后选择“新建用户”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="8d5b8-117">Connect to the Subscriber in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], expand **Databases**, **ProductReplica**, and **Security**, right-click **Users**, and then select **New User**.</span></span>  
  
2.  <span data-ttu-id="8d5b8-118">在“常规”\*\*\*\* 页的“用户类型”\*\*\*\* 列表中选择“Windows 用户”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="8d5b8-118">On the **General** page, in the **User type** list, select **Windows user**.</span></span>  
  
3.  <span data-ttu-id="8d5b8-119">选择 "**用户名**" 框，然后单击省略号 ( ... ) "按钮，在"**输入要选择的对象名称 "** 框中键入 <Machine_Name **>\ Repl_distribution**中，单击"**检查名称**"，然后单击 **" 确定 "**。</span><span class="sxs-lookup"><span data-stu-id="8d5b8-119">Select the **User name** box and click the ellipsis (...) button, in the **Enter the object name to select** box type <Machine_Name>**\repl_distribution**, click **Check Names**, and then click **OK**.</span></span>  
  
4.  <span data-ttu-id="8d5b8-120">在“成员资格”\*\*\*\* 页的“数据库角色成员资格”\*\*\*\* 区域中，选择“db_owner”\*\*\*\*，然后单击“确定”\*\*\*\* 以创建用户。</span><span class="sxs-lookup"><span data-stu-id="8d5b8-120">On the **Membership** page, in **Database role membership** area, select **db_owner**, and then click **OK** to create the user.</span></span>  
  
### <a name="to-view-the-synchronization-status-of-the-subscription"></a><span data-ttu-id="8d5b8-121">查看订阅的同步状态</span><span class="sxs-lookup"><span data-stu-id="8d5b8-121">To view the synchronization status of the subscription</span></span>  
  
1.  <span data-ttu-id="8d5b8-122">在 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 中连接到发布服务器，然后依次展开服务器节点和“复制”\*\*\*\* 文件夹。</span><span class="sxs-lookup"><span data-stu-id="8d5b8-122">Connect to the Publisher in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], expand the server node, and then expand the **Replication** folder.</span></span>  
  
2.  <span data-ttu-id="8d5b8-123">在“本地发布”\*\*\*\* 文件夹中，展开“AdvWorksProductTrans”\*\*\*\* 发布，右键单击“ProductReplica”\*\*\*\* 数据库中的订阅，然后单击“查看同步状态”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="8d5b8-123">In the **Local Publications** folder, expand the **AdvWorksProductTrans** publication, right-click the subscription in the **ProductReplica** database, and then click **View Synchronization Status**.</span></span>  
  
     <span data-ttu-id="8d5b8-124">系统将显示订阅的当前同步状态。</span><span class="sxs-lookup"><span data-stu-id="8d5b8-124">The current synchronization status of the subscription is displayed.</span></span>  
  
3.  <span data-ttu-id="8d5b8-125">如果订阅未在“AdvWorksProductTrans”\*\*\*\* 下出现，请按 F5 刷新列表。</span><span class="sxs-lookup"><span data-stu-id="8d5b8-125">If the subscription is not visible under **AdvWorksProductTrans**, press F5 to refresh the list.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="8d5b8-126">后续步骤</span><span class="sxs-lookup"><span data-stu-id="8d5b8-126">Next Steps</span></span>  
 <span data-ttu-id="8d5b8-127">您已经成功创建了对事务发布的订阅。</span><span class="sxs-lookup"><span data-stu-id="8d5b8-127">You have successfully created a subscription to the transactional publication.</span></span> <span data-ttu-id="8d5b8-128">因为此订阅的分发代理持续运行，所以订阅一经创建就进行了初始化。</span><span class="sxs-lookup"><span data-stu-id="8d5b8-128">Because the Distribution Agent for this subscription runs continuously, the subscription is initialized when it is created.</span></span> <span data-ttu-id="8d5b8-129">接下来，您将用跟踪令牌来验证更改是否已复制到订阅服务器并确定滞后时间。</span><span class="sxs-lookup"><span data-stu-id="8d5b8-129">Next, you will use tracer tokens to verify that changes are being replicated to the Subscriber and to determine latency.</span></span> <span data-ttu-id="8d5b8-130">请参阅 [第 3 课：验证订阅和测量滞后时间](lesson-3-validating-the-subscription-and-measuring-latency.md)。</span><span class="sxs-lookup"><span data-stu-id="8d5b8-130">See [Lesson 3: Validating the Subscription and Measuring Latency](lesson-3-validating-the-subscription-and-measuring-latency.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8d5b8-131">另请参阅</span><span class="sxs-lookup"><span data-stu-id="8d5b8-131">See Also</span></span>  
 <span data-ttu-id="8d5b8-132">[使用快照初始化订阅](initialize-a-subscription-with-a-snapshot.md) </span><span class="sxs-lookup"><span data-stu-id="8d5b8-132">[Initialize a Subscription with a Snapshot](initialize-a-subscription-with-a-snapshot.md) </span></span>  
 <span data-ttu-id="8d5b8-133">[ssSDSFull](create-a-push-subscription.md) </span><span class="sxs-lookup"><span data-stu-id="8d5b8-133">[Create a Push Subscription](create-a-push-subscription.md) </span></span>  
 [<span data-ttu-id="8d5b8-134">订阅发布</span><span class="sxs-lookup"><span data-stu-id="8d5b8-134">Subscribe to Publications</span></span>](subscribe-to-publications.md)  
  
  
