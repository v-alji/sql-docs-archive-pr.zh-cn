---
title: 编写复制脚本 | Microsoft Docs
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- scripts [SQL Server replication], replication objects
- merge replication scripting [SQL Server replication]
- replication [SQL Server], scripting
- snapshot replication [SQL Server], scripting
- scripts [SQL Server replication]
- transactional replication, scripting
ms.assetid: e50fac44-54c0-470c-a4ea-9c111fa4322b
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 2e865e2664a399bca4738c1fc157bef176f35e96
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87577508"
---
# <a name="scripting-replication"></a><span data-ttu-id="a5e80-102">编写复制脚本</span><span class="sxs-lookup"><span data-stu-id="a5e80-102">Scripting Replication</span></span>
  <span data-ttu-id="a5e80-103">制订灾难恢复计划时，应要求对拓扑中的所有复制组件编写脚本，另外，脚本还可以用来自动处理重复性的任务。</span><span class="sxs-lookup"><span data-stu-id="a5e80-103">All replication components in a topology should be scripted as part of a disaster recovery plan, and scripts can also be used to automate repetitive tasks.</span></span> <span data-ttu-id="a5e80-104">脚本包含为实现要为其编写脚本的复制组件所需的 Transact-SQL 系统存储过程，如发布或订阅。</span><span class="sxs-lookup"><span data-stu-id="a5e80-104">A script contains the Transact-SQL system stored procedures necessary to implement the replication component(s) scripted, such as a publication or subscription.</span></span> <span data-ttu-id="a5e80-105">创建完组件后，可以在向导（如新建发布向导）或 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 中创建脚本。</span><span class="sxs-lookup"><span data-stu-id="a5e80-105">Scripts can be created in a wizard (such as the New Publication Wizard) or in [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] after you create a component.</span></span> <span data-ttu-id="a5e80-106">您可以使用 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 或 **sqlcmd**查看、修改和运行脚本。</span><span class="sxs-lookup"><span data-stu-id="a5e80-106">You can view, modify, and run the script using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or **sqlcmd**.</span></span> <span data-ttu-id="a5e80-107">脚本可以与备份文件存储在一起，以便在必须重新配置复制拓扑时使用。</span><span class="sxs-lookup"><span data-stu-id="a5e80-107">Scripts can be stored with backup files to be used in case a replication topology must be reconfigured.</span></span>  
  
 <span data-ttu-id="a5e80-108">如果更改了属性，便需要为组件重新编写脚本。</span><span class="sxs-lookup"><span data-stu-id="a5e80-108">A component should be re-scripted if any property changes are made.</span></span> <span data-ttu-id="a5e80-109">如果对事务复制使用自定义存储过程，则应与脚本一起存储每个过程的副本。如果过程发生更改，应更新相应的副本（通常会由于架构更改或应用程序要求的更改而更新过程）。</span><span class="sxs-lookup"><span data-stu-id="a5e80-109">If you use custom stored procedures with transactional replication, a copy of each procedure should be stored with the scripts; the copy should be updated if the procedure changes (procedures are typically updated due to schema changes or changing application requirements).</span></span> <span data-ttu-id="a5e80-110">有关自定义过程的详细信息，请参阅[指定如何传播事务项目的更改](transactional/transactional-articles-specify-how-changes-are-propagated.md)。</span><span class="sxs-lookup"><span data-stu-id="a5e80-110">For more information about custom procedures, see [Specify How Changes Are Propagated for Transactional Articles](transactional/transactional-articles-specify-how-changes-are-propagated.md).</span></span>  
  
 <span data-ttu-id="a5e80-111">对于使用参数化筛选器的合并发布而言，发布脚本中包含了对创建数据分区的存储过程的调用。</span><span class="sxs-lookup"><span data-stu-id="a5e80-111">For merge publications that use parameterized filters, publication scripts contain the stored procedure calls to create data partitions.</span></span> <span data-ttu-id="a5e80-112">该脚本提供了对所创建的分区的引用和一种在必要时重建分区的途径。</span><span class="sxs-lookup"><span data-stu-id="a5e80-112">The script provides a reference for the partitions created and a way in which to re-create one or more partitions if necessary.</span></span>  
  
## <a name="example-of-automating-a-task-with-scripts"></a><span data-ttu-id="a5e80-113">用脚本使任务自动化的示例</span><span class="sxs-lookup"><span data-stu-id="a5e80-113">Example of Automating a Task with Scripts</span></span>  
 <span data-ttu-id="a5e80-114">请考虑 [!INCLUDE[ssSampleDBCoFull](../../includes/sssampledbcofull-md.md)]，它为把数据分发给远程销售部门而实现合并复制。</span><span class="sxs-lookup"><span data-stu-id="a5e80-114">Consider [!INCLUDE[ssSampleDBCoFull](../../includes/sssampledbcofull-md.md)], which implements merge replication to distribute data to its remote sales force.</span></span> <span data-ttu-id="a5e80-115">销售代表可以用请求订阅下载所有他所负责的区域客户的相关数据。</span><span class="sxs-lookup"><span data-stu-id="a5e80-115">A sales representative downloads all the data that pertains to the customers in her territory using pull subscriptions.</span></span> <span data-ttu-id="a5e80-116">脱机工作时，销售代表可以更新数据并输入新的客户和订单。</span><span class="sxs-lookup"><span data-stu-id="a5e80-116">When working offline, the sales representative updates data and enters new customers and orders.</span></span> <span data-ttu-id="a5e80-117">由于 [!INCLUDE[ssSampleDBCoFull](../../includes/sssampledbcofull-md.md)] 在不同地区拥有 50 多个销售代表，所以，用新建订阅向导在每个订阅服务器上创建不同订阅需要耗费大量时间。</span><span class="sxs-lookup"><span data-stu-id="a5e80-117">Because [!INCLUDE[ssSampleDBCoFull](../../includes/sssampledbcofull-md.md)] has more than fifty sales representatives in different territories, it would be time-consuming to create the different subscriptions at each Subscriber with the New Subscription Wizard.</span></span> <span data-ttu-id="a5e80-118">而复制管理员可以执行下列步骤：</span><span class="sxs-lookup"><span data-stu-id="a5e80-118">Instead, the replication administrator can follow these steps:</span></span>  
  
1.  <span data-ttu-id="a5e80-119">建立必要的根据销售代表或其所在区域进行分区的合并发布。</span><span class="sxs-lookup"><span data-stu-id="a5e80-119">Set up the necessary merge publications with partitions based on the sales representative or their territory.</span></span>  
  
2.  <span data-ttu-id="a5e80-120">为一个订阅服务器创建请求订阅。</span><span class="sxs-lookup"><span data-stu-id="a5e80-120">Create a pull subscription for one Subscriber.</span></span>  
  
3.  <span data-ttu-id="a5e80-121">根据该请求订阅生成脚本。</span><span class="sxs-lookup"><span data-stu-id="a5e80-121">Generate a script based on that pull subscription.</span></span>  
  
4.  <span data-ttu-id="a5e80-122">修改脚本，将这些值更改为订阅服务器的名称。</span><span class="sxs-lookup"><span data-stu-id="a5e80-122">Modify the script, changing such values as the name of the Subscriber.</span></span>  
  
5.  <span data-ttu-id="a5e80-123">在多个订阅服务器上运行脚本，以生成所需的请求订阅。</span><span class="sxs-lookup"><span data-stu-id="a5e80-123">Run the script at multiple Subscribers to generate the required pull subscriptions.</span></span>  
  
## <a name="script-replication-objects"></a><span data-ttu-id="a5e80-124">脚本复制对象</span><span class="sxs-lookup"><span data-stu-id="a5e80-124">Script Replication Objects</span></span>  
 <span data-ttu-id="a5e80-125">复制向导或 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 中“复制”文件夹中的脚本复制对象。</span><span class="sxs-lookup"><span data-stu-id="a5e80-125">Script replication objects from the replication wizards or from the **Replication** folder in [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].</span></span> <span data-ttu-id="a5e80-126">如果从向导编写脚本，则可以选择创建对象并为其编写脚本，也可以选择仅编写脚本。</span><span class="sxs-lookup"><span data-stu-id="a5e80-126">If you script from the wizards, you can choose to create objects and script them, or you can choose only to script them.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="a5e80-127">所有密码的脚本被编写为 NULL。</span><span class="sxs-lookup"><span data-stu-id="a5e80-127">All passwords are scripted as NULL.</span></span> <span data-ttu-id="a5e80-128">如果可能，请在运行时提示用户输入安全凭据。</span><span class="sxs-lookup"><span data-stu-id="a5e80-128">When possible, prompt users to enter security credentials at runtime.</span></span> <span data-ttu-id="a5e80-129">如果将凭据存储在脚本文件中，则必须确保文件的安全以防受到未经授权的访问。</span><span class="sxs-lookup"><span data-stu-id="a5e80-129">If you store credentials in a script file, you must secure the file to prevent unauthorized access.</span></span>  
  
 <span data-ttu-id="a5e80-130">有关使用复制向导的详细信息，请参阅：</span><span class="sxs-lookup"><span data-stu-id="a5e80-130">For more information about using the replication wizards, see:</span></span>  
  
-   [<span data-ttu-id="a5e80-131">配置发布和分发</span><span class="sxs-lookup"><span data-stu-id="a5e80-131">Configure Publishing and Distribution</span></span>](configure-publishing-and-distribution.md)  
  
-   [<span data-ttu-id="a5e80-132">创建发布</span><span class="sxs-lookup"><span data-stu-id="a5e80-132">Create a Publication</span></span>](publish/create-a-publication.md)  
  
-   [<span data-ttu-id="a5e80-133">创建推送订阅</span><span class="sxs-lookup"><span data-stu-id="a5e80-133">Create a Push Subscription</span></span>](create-a-push-subscription.md)  
  
-   [<span data-ttu-id="a5e80-134">创建请求订阅</span><span class="sxs-lookup"><span data-stu-id="a5e80-134">Create a Pull Subscription</span></span>](create-a-pull-subscription.md)  
  
#### <a name="to-script-an-object-from-a-replication-wizard"></a><span data-ttu-id="a5e80-135">从复制向导编写对象脚本</span><span class="sxs-lookup"><span data-stu-id="a5e80-135">To script an object from a replication wizard</span></span>  
  
1.  <span data-ttu-id="a5e80-136">在向导的 **“向导操作”** 页上，选中适合该向导的复选框：</span><span class="sxs-lookup"><span data-stu-id="a5e80-136">On the **Wizard Actions** page of a wizard, select the check box appropriate for the wizard:</span></span>  
  
    -   <span data-ttu-id="a5e80-137">**生成包含创建发布的步骤的脚本文件**</span><span class="sxs-lookup"><span data-stu-id="a5e80-137">**Generate a script file with steps to create a publication**</span></span>  
  
    -   <span data-ttu-id="a5e80-138">**生成包含创建订阅的步骤的脚本文件**</span><span class="sxs-lookup"><span data-stu-id="a5e80-138">**Generate a script file with steps to create the subscription(s)**</span></span>  
  
    -   <span data-ttu-id="a5e80-139">**生成包含配置分发的步骤的脚本文件**</span><span class="sxs-lookup"><span data-stu-id="a5e80-139">**Generate a script file with steps to configure distribution**</span></span>  
  
2.  <span data-ttu-id="a5e80-140">在 **“脚本文件属性”** 页上指定选项。</span><span class="sxs-lookup"><span data-stu-id="a5e80-140">Specify options on the **Script File Properties** page.</span></span>  
  
3.  <span data-ttu-id="a5e80-141">完成向导。</span><span class="sxs-lookup"><span data-stu-id="a5e80-141">Complete the wizard.</span></span>  
  
#### <a name="to-script-an-object-from-management-studio"></a><span data-ttu-id="a5e80-142">从 Management Studio 编写对象脚本</span><span class="sxs-lookup"><span data-stu-id="a5e80-142">To script an object from Management Studio</span></span>  
  
1.  <span data-ttu-id="a5e80-143">在 [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]中，连接到分发服务器、发布服务器或订阅服务器，然后展开服务器节点。</span><span class="sxs-lookup"><span data-stu-id="a5e80-143">Connect to the Distributor, Publisher, or Subscriber in [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)], and then expand the server node.</span></span>  
  
2.  <span data-ttu-id="a5e80-144">展开 **“复制”** 文件夹，再展开 **“本地发布”** 文件夹或 **“本地订阅”** 文件夹。</span><span class="sxs-lookup"><span data-stu-id="a5e80-144">Expand the **Replication** folder, and then expand the **Local Publications** folder or the **Local Subscriptions** folder.</span></span>  
  
3.  <span data-ttu-id="a5e80-145">右键单击某个发布或订阅，然后单击 **“生成脚本”** 。</span><span class="sxs-lookup"><span data-stu-id="a5e80-145">Right-click a publication or subscription, and then click **Generate Scripts**.</span></span>  
  
4.  <span data-ttu-id="a5e80-146">在“生成 SQL 脚本 - \<ReplicationObject>”对话框中指定选项。</span><span class="sxs-lookup"><span data-stu-id="a5e80-146">Specify options in the **Generate SQL Script - \<ReplicationObject>** dialog box.</span></span>  
  
5.  <span data-ttu-id="a5e80-147">单击 **“将脚本保存到文件”** 。</span><span class="sxs-lookup"><span data-stu-id="a5e80-147">Click **Script to File**.</span></span>  
  
6.  <span data-ttu-id="a5e80-148">在 **“脚本文件位置”** 对话框中输入文件名，然后单击 **“保存”** 。</span><span class="sxs-lookup"><span data-stu-id="a5e80-148">Enter a file name in the **Script File Location** dialog box, and then click **Save**.</span></span> <span data-ttu-id="a5e80-149">将显示状态消息。</span><span class="sxs-lookup"><span data-stu-id="a5e80-149">A status message is displayed.</span></span>  
  
7.  <span data-ttu-id="a5e80-150">单击 **“确定”** ，再单击 **“关闭”** 。</span><span class="sxs-lookup"><span data-stu-id="a5e80-150">Click **OK**, and then click **Close**.</span></span>  
  
#### <a name="to-script-multiple-objects-from-management-studio"></a><span data-ttu-id="a5e80-151">从 Management Studio 编写多个对象的脚本</span><span class="sxs-lookup"><span data-stu-id="a5e80-151">To script multiple objects from Management Studio</span></span>  
  
1.  <span data-ttu-id="a5e80-152">在 [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]中，连接到分发服务器、发布服务器或订阅服务器，然后展开服务器节点。</span><span class="sxs-lookup"><span data-stu-id="a5e80-152">Connect to the Distributor, Publisher, or Subscriber in [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)], and then expand the server node.</span></span>  
  
2.  <span data-ttu-id="a5e80-153">右键单击 **“复制”** 文件夹，然后单击 **“生成脚本”** 。</span><span class="sxs-lookup"><span data-stu-id="a5e80-153">Right-click the **Replication** folder, and then click **Generate Scripts**.</span></span>  
  
3.  <span data-ttu-id="a5e80-154">在 **“生成 SQL 脚本”** 对话框中指定选项。</span><span class="sxs-lookup"><span data-stu-id="a5e80-154">Specify options in the **Generate SQL Script** dialog box.</span></span>  
  
4.  <span data-ttu-id="a5e80-155">单击 **“将脚本保存到文件”** 。</span><span class="sxs-lookup"><span data-stu-id="a5e80-155">Click **Script to File**.</span></span>  
  
5.  <span data-ttu-id="a5e80-156">在 **“脚本文件位置”** 对话框中输入文件名，然后单击 **“保存”** 。</span><span class="sxs-lookup"><span data-stu-id="a5e80-156">Enter a file name in the **Script File Location** dialog box, and then click **Save**.</span></span> <span data-ttu-id="a5e80-157">将显示状态消息。</span><span class="sxs-lookup"><span data-stu-id="a5e80-157">A status message is displayed.</span></span>  
  
6.  <span data-ttu-id="a5e80-158">单击 **“确定”** ，再单击 **“关闭”** 。</span><span class="sxs-lookup"><span data-stu-id="a5e80-158">Click **OK, and then** click **Close**.</span></span>  
  
  
