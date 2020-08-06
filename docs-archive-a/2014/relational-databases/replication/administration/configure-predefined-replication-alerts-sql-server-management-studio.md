---
title: 配置预定义的复制警报 (SQL Server Management Studio) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- alerts [SQL Server replication]
- predefined replication alerts [SQL Server replication]
ms.assetid: c0414147-7ffe-4f9a-908c-71c1b5201584
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: aa78a08757cc7bbe809c5e3a1808c9632b76763a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87693786"
---
# <a name="configure-predefined-replication-alerts-sql-server-management-studio"></a><span data-ttu-id="89f29-102">配置预定义的复制警报 (SQL Server Management Studio)</span><span class="sxs-lookup"><span data-stu-id="89f29-102">Configure Predefined Replication Alerts (SQL Server Management Studio)</span></span>
  <span data-ttu-id="89f29-103">复制提供了下列预定义警报，可以配置这些警报以响应复制事件：</span><span class="sxs-lookup"><span data-stu-id="89f29-103">Replication offers the following predefined alerts, which can be configured to respond to replication events:</span></span>  
  
-   <span data-ttu-id="89f29-104">**复制: 代理成功**</span><span class="sxs-lookup"><span data-stu-id="89f29-104">**Replication: agent success**</span></span>    
-   <span data-ttu-id="89f29-105">**复制: 代理失败**</span><span class="sxs-lookup"><span data-stu-id="89f29-105">**Replication: agent failure**</span></span>    
-   <span data-ttu-id="89f29-106">**复制：代理重试**</span><span class="sxs-lookup"><span data-stu-id="89f29-106">**Replication: agent retry**</span></span>    
-   <span data-ttu-id="89f29-107">**复制：已删除过期的订阅**</span><span class="sxs-lookup"><span data-stu-id="89f29-107">**Replication: expired subscription dropped**</span></span>    
-   <span data-ttu-id="89f29-108">复制：验证失败后重新初始化了订阅</span><span class="sxs-lookup"><span data-stu-id="89f29-108">**Replication: Subscription reinitialized after validation failure**</span></span>    
-   <span data-ttu-id="89f29-109">复制：订阅服务器未通过数据验证</span><span class="sxs-lookup"><span data-stu-id="89f29-109">**Replication: Subscriber has failed data validation**</span></span>    
-   <span data-ttu-id="89f29-110">复制：订阅服务器已通过数据验证</span><span class="sxs-lookup"><span data-stu-id="89f29-110">**Replication: Subscriber has passed data validation**</span></span>    
-   <span data-ttu-id="89f29-111">复制：代理自定义关闭</span><span class="sxs-lookup"><span data-stu-id="89f29-111">**Replication: agent custom shutdown**</span></span>  
  
 <span data-ttu-id="89f29-112">在 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] 中的“警报”文件夹或复制监视器的“警告”选项卡中配置这些警报 。</span><span class="sxs-lookup"><span data-stu-id="89f29-112">Configure these alerts from the **Alerts** folder in [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] or the **Warnings** tab in Replication Monitor.</span></span> <span data-ttu-id="89f29-113">有关访问此选项卡的详细信息，请参阅[使用复制监视器查看信息和执行任务](../monitor/view-information-and-perform-tasks-replication-monitor.md)。</span><span class="sxs-lookup"><span data-stu-id="89f29-113">For more information about accessing this tab, see [View Information and Perform Tasks using Replication Monitor](../monitor/view-information-and-perform-tasks-replication-monitor.md).</span></span>  
  
 <span data-ttu-id="89f29-114">除这些警报之外，复制监视器还提供了一组与状态和性能相关的警告和警报。</span><span class="sxs-lookup"><span data-stu-id="89f29-114">In addition to these alerts, Replication Monitor provides a set of warnings and alerts related to status and performance.</span></span> <span data-ttu-id="89f29-115">有关详细信息，请参阅[在复制监视器警报基础结构中设置阈值和警告](../monitor/set-thresholds-and-warnings-in-replication-monitor.md)。</span><span class="sxs-lookup"><span data-stu-id="89f29-115">For more information, see [Set Thresholds and Warnings in Replication Monitor](../monitor/set-thresholds-and-warnings-in-replication-monitor.md) alerts infrastructure.</span></span> <span data-ttu-id="89f29-116">有关详细信息，请参阅[创建用户定义事件](../../../ssms/agent/create-a-user-defined-event.md)。</span><span class="sxs-lookup"><span data-stu-id="89f29-116">For more information, see [Create a User-Defined Event](../../../ssms/agent/create-a-user-defined-event.md).</span></span>  
  
### <a name="to-configure-a-predefined-replication-alert-in-management-studio"></a><span data-ttu-id="89f29-117">在 Management Studio 中配置预定义复制警报</span><span class="sxs-lookup"><span data-stu-id="89f29-117">To configure a predefined replication alert in Management Studio</span></span>  
  
1.  <span data-ttu-id="89f29-118">在 [!INCLUDE[ssManStudio](../../../includes/ssmanstudio-md.md)]中连接到分发服务器，然后展开服务器节点。</span><span class="sxs-lookup"><span data-stu-id="89f29-118">Connect to the Distributor in [!INCLUDE[ssManStudio](../../../includes/ssmanstudio-md.md)], and then expand the server node.</span></span>    
2.  <span data-ttu-id="89f29-119">展开 “SQL Server 代理” 文件夹，然后展开 “警报” 文件夹。</span><span class="sxs-lookup"><span data-stu-id="89f29-119">Expand the **SQL Server Agent** folder, and then expand the **Alerts** folder.</span></span>    
3.  <span data-ttu-id="89f29-120">右键单击一个复制警报，然后单击 “属性”。</span><span class="sxs-lookup"><span data-stu-id="89f29-120">Right-click a replication alert, and then click **Properties**.</span></span>    
4.  <span data-ttu-id="89f29-121">在“\<AlertName> 警报属性”对话框中设置选项：</span><span class="sxs-lookup"><span data-stu-id="89f29-121">Set options in the **\<AlertName> alert properties** dialog box:</span></span>    
    -   <span data-ttu-id="89f29-122">在 **“常规”** 页上，单击 **“启用”** ，指定应用此警报的数据库。</span><span class="sxs-lookup"><span data-stu-id="89f29-122">On the **General** page, click **Enable**; specify which database the alert should apply to.</span></span>    
    -   <span data-ttu-id="89f29-123">在 **“响应”** 页上，指定是否应发送电子邮件和/或是否应执行作业。</span><span class="sxs-lookup"><span data-stu-id="89f29-123">On the **Response** page, specify whether an e-mail should be sent and/or a job should be executed.</span></span>  
  
         <span data-ttu-id="89f29-124">如果警报是“复制：订阅服务器未通过数据验证”，可以指定复制为此警报提供的响应作业：选择“执行作业”，再单击浏览按钮（“...”）。 在 **“定位作业”** 对话框中，单击 **“浏览”** 。</span><span class="sxs-lookup"><span data-stu-id="89f29-124">If the alert is **Replication: Subscriber has failed data validation**, you can specify the response job that replication provides for this alert: Select **Execute job**, and then click the browse button (**...**). In the **Locate Job** dialog box, click **Browse**.</span></span> <span data-ttu-id="89f29-125">在 **“查找对象”** 对话框中，选择 **“重新初始化未通过数据验证的订阅”** 。</span><span class="sxs-lookup"><span data-stu-id="89f29-125">In the **Browse for Objects** dialog box, select **Reinitialize subscriptions having data validation failures**.</span></span> <span data-ttu-id="89f29-126">在两个打开的对话框中，单击 **“确定”** 。</span><span class="sxs-lookup"><span data-stu-id="89f29-126">Click **OK** in both open dialog boxes.</span></span> <span data-ttu-id="89f29-127">作业执行时，它将把远程过程调用 (RPC) 用于重新初始化订阅的存储过程。</span><span class="sxs-lookup"><span data-stu-id="89f29-127">When the job executes, it uses a remote procedure call (RPC) to a stored procedure that reinitializes the subscription.</span></span> <span data-ttu-id="89f29-128">如果发布服务器使用远程分发服务器，您必须在发布服务器上定义远程服务器登录名，以便可以从分发服务器到发布服务器进行 RPC。</span><span class="sxs-lookup"><span data-stu-id="89f29-128">If the Publisher uses a remote Distributor, you must define a remote server login at the Publisher, so that the RPC from the Distributor to the Publisher can be made.</span></span>   
    -   <span data-ttu-id="89f29-129">在 **“选项”** 页上，自定义响应文本。</span><span class="sxs-lookup"><span data-stu-id="89f29-129">On the **Options** page, customize the text of the response.</span></span>    
5.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
### <a name="to-configure-an-alert-for-a-threshold-in-replication-monitor"></a><span data-ttu-id="89f29-130">在复制监视器中配置阈值的警报</span><span class="sxs-lookup"><span data-stu-id="89f29-130">To configure an alert for a threshold in Replication Monitor</span></span>  
  
1.  <span data-ttu-id="89f29-131">在 **“警告”** 选项卡上，单击 **“配置警报”** 。</span><span class="sxs-lookup"><span data-stu-id="89f29-131">On the **Warnings** tab click **Configure Alerts**.</span></span>    
2.  <span data-ttu-id="89f29-132">在 **“配置复制警报”** 对话框中，选择一个警报，然后单击 **“配置”** 。</span><span class="sxs-lookup"><span data-stu-id="89f29-132">In the **Configure Replication Alerts** dialog box, select an alert, and then click **Configure**.</span></span>    
3.  <span data-ttu-id="89f29-133">在“\<AlertName> 警报属性”对话框中设置选项：</span><span class="sxs-lookup"><span data-stu-id="89f29-133">Set options in the **\<AlertName> alert properties** dialog box:</span></span>    
    -   <span data-ttu-id="89f29-134">在 **“常规”** 页上，单击 **“启用”** ，指定应用此警报的数据库。</span><span class="sxs-lookup"><span data-stu-id="89f29-134">On the **General** page, click **Enable**; specify which database the alert should apply to.</span></span>    
    -   <span data-ttu-id="89f29-135">在 **“响应”** 页上，指定是否应发送电子邮件和/或是否应执行作业。</span><span class="sxs-lookup"><span data-stu-id="89f29-135">On the **Response** page, specify whether an e-mail should be sent and/or a job should be executed.</span></span>    
         <span data-ttu-id="89f29-136">如果警报是“复制：订阅服务器未通过数据验证”，可以指定复制为此警报提供的响应作业：选择“执行作业”，再单击浏览按钮（“...”）。 在 **“定位作业”** 对话框中，单击 **“浏览”** 。</span><span class="sxs-lookup"><span data-stu-id="89f29-136">If the alert is **Replication: Subscriber has failed data validation**, you can specify the response job that replication provides for this alert: Select **Execute job**, and then click the browse button (**...**). In the **Locate Job** dialog box, click **Browse**.</span></span> <span data-ttu-id="89f29-137">在 **“查找对象”** 对话框中，选择 **“重新初始化未通过数据验证的订阅”** 。</span><span class="sxs-lookup"><span data-stu-id="89f29-137">In the **Browse for Objects** dialog box, select **Reinitialize subscriptions having data validation failures**.</span></span> <span data-ttu-id="89f29-138">在两个打开的对话框中，单击 **“确定”** 。</span><span class="sxs-lookup"><span data-stu-id="89f29-138">Click **OK** in both open dialog boxes.</span></span> <span data-ttu-id="89f29-139">作业执行时，它将把远程过程调用 (RPC) 用于重新初始化订阅的存储过程。</span><span class="sxs-lookup"><span data-stu-id="89f29-139">When the job executes, it uses a remote procedure call (RPC) to a stored procedure that reinitializes the subscription.</span></span> <span data-ttu-id="89f29-140">如果发布服务器使用远程分发服务器，您必须在发布服务器上定义远程服务器登录名，以便可以从分发服务器到发布服务器进行 RPC。</span><span class="sxs-lookup"><span data-stu-id="89f29-140">If the Publisher uses a remote Distributor, you must define a remote server login at the Publisher, so that the RPC from the Distributor to the Publisher can be made.</span></span>   
    -   <span data-ttu-id="89f29-141">在 **“选项”** 页上，自定义响应文本。</span><span class="sxs-lookup"><span data-stu-id="89f29-141">On the **Options** page, customize the text of the response.</span></span>    
4.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]    
5.  <span data-ttu-id="89f29-142">单击“关闭”。</span><span class="sxs-lookup"><span data-stu-id="89f29-142">Click **Close**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="89f29-143">另请参阅</span><span class="sxs-lookup"><span data-stu-id="89f29-143">See Also</span></span>  
 [<span data-ttu-id="89f29-144">对复制代理事件使用警报</span><span class="sxs-lookup"><span data-stu-id="89f29-144">Use Alerts for Replication Agent Events</span></span>](../agents/use-alerts-for-replication-agent-events.md)  
  
  
