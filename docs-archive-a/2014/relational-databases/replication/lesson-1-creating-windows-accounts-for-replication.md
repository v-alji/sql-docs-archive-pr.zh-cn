---
title: 第 1 课：为复制创建 Windows 帐户 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- replication [SQL Server], tutorials
- replication [SQL Server], administering
ms.assetid: 65c3816b-47f0-448c-a4a4-ebd3e2a58820
author: rothja
ms.author: jroth
ms.openlocfilehash: 29f1008338b3ba728066ed611108477586a4c899
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87578060"
---
# <a name="lesson-1-creating-windows-accounts-for-replication"></a><span data-ttu-id="c69ac-102">第 1 课：为复制创建 Windows 帐户</span><span class="sxs-lookup"><span data-stu-id="c69ac-102">Lesson 1: Creating Windows Accounts for Replication</span></span>
  <span data-ttu-id="c69ac-103">在本课中，将创建 Windows 帐户以运行复制代理。</span><span class="sxs-lookup"><span data-stu-id="c69ac-103">In this lesson, you will create Windows accounts to run replication agents.</span></span> <span data-ttu-id="c69ac-104">您将在本地服务器上为以下代理创建一个单独的 Windows 帐户：</span><span class="sxs-lookup"><span data-stu-id="c69ac-104">You will create a separate Windows account on the local server for the following agents:</span></span>  
  
|<span data-ttu-id="c69ac-105">代理</span><span class="sxs-lookup"><span data-stu-id="c69ac-105">Agent</span></span>|<span data-ttu-id="c69ac-106">位置</span><span class="sxs-lookup"><span data-stu-id="c69ac-106">Location</span></span>|<span data-ttu-id="c69ac-107">帐户名</span><span class="sxs-lookup"><span data-stu-id="c69ac-107">Account name</span></span>|  
|-----------|--------------|------------------|  
|<span data-ttu-id="c69ac-108">快照代理</span><span class="sxs-lookup"><span data-stu-id="c69ac-108">Snapshot Agent</span></span>|<span data-ttu-id="c69ac-109">Publisher</span><span class="sxs-lookup"><span data-stu-id="c69ac-109">Publisher</span></span>|<span data-ttu-id="c69ac-110">\<*machine_name*>\ repl_snapshot</span><span class="sxs-lookup"><span data-stu-id="c69ac-110">\<*machine_name*>\repl_snapshot</span></span>|  
|<span data-ttu-id="c69ac-111">日志读取器代理</span><span class="sxs-lookup"><span data-stu-id="c69ac-111">Log Reader Agent</span></span>|<span data-ttu-id="c69ac-112">Publisher</span><span class="sxs-lookup"><span data-stu-id="c69ac-112">Publisher</span></span>|<span data-ttu-id="c69ac-113">\<*machine_name*>\ repl_logreader</span><span class="sxs-lookup"><span data-stu-id="c69ac-113">\<*machine_name*>\repl_logreader</span></span>|  
|<span data-ttu-id="c69ac-114">分发代理</span><span class="sxs-lookup"><span data-stu-id="c69ac-114">Distribution Agent</span></span>|<span data-ttu-id="c69ac-115">发布服务器和订阅服务器</span><span class="sxs-lookup"><span data-stu-id="c69ac-115">Publisher and Subscriber</span></span>|<span data-ttu-id="c69ac-116">\<*machine_name*>\ repl_distribution</span><span class="sxs-lookup"><span data-stu-id="c69ac-116">\<*machine_name*>\repl_distribution</span></span>|  
|<span data-ttu-id="c69ac-117">合并代理</span><span class="sxs-lookup"><span data-stu-id="c69ac-117">Merge Agent</span></span>|<span data-ttu-id="c69ac-118">发布服务器和订阅服务器</span><span class="sxs-lookup"><span data-stu-id="c69ac-118">Publisher and Subscriber</span></span>|<span data-ttu-id="c69ac-119">\<*machine_name*>\ repl_merge</span><span class="sxs-lookup"><span data-stu-id="c69ac-119">\<*machine_name*>\repl_merge</span></span>|  
  
> [!NOTE]  
>  <span data-ttu-id="c69ac-120">在复制教程中，发布服务器和分发服务器共享同一 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]实例。</span><span class="sxs-lookup"><span data-stu-id="c69ac-120">In the replication tutorials, the Publisher and Distributor share the same instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="c69ac-121">发布服务器和订阅服务器可以共享同一 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]实例，但这不是必须的。</span><span class="sxs-lookup"><span data-stu-id="c69ac-121">The Publisher and Subscriber may share the same instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], but it is not a requirement.</span></span> <span data-ttu-id="c69ac-122">如果发布服务器和订阅服务器共享同一实例，则在订阅服务器上用于创建帐户的步骤不是必须的。</span><span class="sxs-lookup"><span data-stu-id="c69ac-122">If the Publisher and Subscriber share the same instance, the steps that are used to create accounts at the Subscriber are not required.</span></span>  
  
### <a name="to-create-local-windows-accounts-for-replication-agents-at-the-publisher"></a><span data-ttu-id="c69ac-123">在发布服务器上为复制代理创建本地 Windows 帐户</span><span class="sxs-lookup"><span data-stu-id="c69ac-123">To create local Windows accounts for replication agents at the Publisher</span></span>  
  
1.  <span data-ttu-id="c69ac-124">在发布服务器上，从 "控制面板" 的 "**管理工具**" 中打开 "**计算机管理**"。</span><span class="sxs-lookup"><span data-stu-id="c69ac-124">At the Publisher, open **Computer Management** from **Administrative Tools** in Control Panel.</span></span>  
  
2.  <span data-ttu-id="c69ac-125">在“系统工具”\*\*\*\* 中，展开“本地用户和组”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="c69ac-125">In **System Tools**, expand **Local Users and Groups**.</span></span>  
  
3.  <span data-ttu-id="c69ac-126">右键单击 "**用户**"，然后单击 "**新建用户**"。</span><span class="sxs-lookup"><span data-stu-id="c69ac-126">Right-click **Users** and then click **New User**.</span></span>  
  
4.  <span data-ttu-id="c69ac-127">`repl_snapshot`在 "**用户名**" 框中输入，提供密码和其他相关信息，然后单击 "**创建**" 创建 repl_snapshot 帐户。</span><span class="sxs-lookup"><span data-stu-id="c69ac-127">Enter `repl_snapshot` in the **User name** box, provide the password and other relevant information, and then click **Create** to create the repl_snapshot account.</span></span>  
  
5.  <span data-ttu-id="c69ac-128">重复上述步骤创建 repl_logreader、repl_distribution 和 repl_merge 帐户。</span><span class="sxs-lookup"><span data-stu-id="c69ac-128">Repeat the previous step to create the repl_logreader, repl_distribution, and repl_merge accounts.</span></span>  
  
6.  <span data-ttu-id="c69ac-129">单击 **“关闭”** 。</span><span class="sxs-lookup"><span data-stu-id="c69ac-129">Click **Close**.</span></span>  
  
### <a name="to-create-local-windows-accounts-for-replication-agents-at-the-subscriber"></a><span data-ttu-id="c69ac-130">在订阅服务器上为复制代理创建本地 Windows 帐户</span><span class="sxs-lookup"><span data-stu-id="c69ac-130">To create local Windows accounts for replication agents at the Subscriber</span></span>  
  
1.  <span data-ttu-id="c69ac-131">在订阅服务器上，从 "控制面板" 的 "**管理工具**" 中打开 "**计算机管理**"。</span><span class="sxs-lookup"><span data-stu-id="c69ac-131">At the Subscriber, open **Computer Management** from **Administrative Tools** in Control Panel.</span></span>  
  
2.  <span data-ttu-id="c69ac-132">在“系统工具”\*\*\*\* 中，展开“本地用户和组”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="c69ac-132">In **System Tools**, expand **Local Users and Groups**.</span></span>  
  
3.  <span data-ttu-id="c69ac-133">右键单击 "**用户**"，然后单击 "**新建用户**"。</span><span class="sxs-lookup"><span data-stu-id="c69ac-133">Right-click **Users** and then click **New User**.</span></span>  
  
4.  <span data-ttu-id="c69ac-134">`repl_distribution`在 "**用户名**" 框中输入，提供密码和其他相关信息，然后单击 "**创建**" 创建 repl_distribution 帐户。</span><span class="sxs-lookup"><span data-stu-id="c69ac-134">Enter `repl_distribution` in the **User name** box, provide the password and other relevant information, and then click **Create** to create the repl_distribution account.</span></span>  
  
5.  <span data-ttu-id="c69ac-135">重复上述步骤创建 repl_merge 帐户。</span><span class="sxs-lookup"><span data-stu-id="c69ac-135">Repeat the previous step to create the repl_merge account.</span></span>  
  
6.  <span data-ttu-id="c69ac-136">单击 **“关闭”** 。</span><span class="sxs-lookup"><span data-stu-id="c69ac-136">Click **Close**.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="c69ac-137">后续步骤</span><span class="sxs-lookup"><span data-stu-id="c69ac-137">Next Steps</span></span>  
 <span data-ttu-id="c69ac-138">您已经成功地为复制代理创建了 Windows 帐户。</span><span class="sxs-lookup"><span data-stu-id="c69ac-138">You have successfully created Windows accounts for replication agents.</span></span> <span data-ttu-id="c69ac-139">接下来，您将配置快照文件夹。</span><span class="sxs-lookup"><span data-stu-id="c69ac-139">Next, you will configure the snapshot folder.</span></span> <span data-ttu-id="c69ac-140">请参阅 [第 2 课：准备快照文件夹](lesson-2-preparing-the-snapshot-folder.md)。</span><span class="sxs-lookup"><span data-stu-id="c69ac-140">See [Lesson 2: Preparing the Snapshot Folder](lesson-2-preparing-the-snapshot-folder.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c69ac-141">另请参阅</span><span class="sxs-lookup"><span data-stu-id="c69ac-141">See Also</span></span>  
 [<span data-ttu-id="c69ac-142">复制代理概述</span><span class="sxs-lookup"><span data-stu-id="c69ac-142">Replication Agents Overview</span></span>](agents/replication-agents-overview.md)  
  
  
