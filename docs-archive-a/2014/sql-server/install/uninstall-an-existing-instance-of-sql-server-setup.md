---
title: 卸载现有 SQL Server 实例（安装程序）| Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: install
ms.topic: conceptual
helpviewer_keywords:
- removing instances of SQL Server
- uninstalling instances of SQL Server
- removing SQL Server
- instances of SQL Server, uninstalling
- uninstalling SQL Server
ms.assetid: 3c64b29d-61d7-4b86-961c-0de62261c6a1
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 51d426a12a2f7f1b7bedbfb7770c4d9cb369f12b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87586138"
---
# <a name="uninstall-an-existing-instance-of-sql-server-setup"></a><span data-ttu-id="52c3b-102">卸载现有 SQL Server 实例（安装程序）</span><span class="sxs-lookup"><span data-stu-id="52c3b-102">Uninstall an Existing Instance of SQL Server (Setup)</span></span>
  <span data-ttu-id="52c3b-103">本文介绍如何卸载 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]的独立实例。</span><span class="sxs-lookup"><span data-stu-id="52c3b-103">This article describes how to uninstall a stand-alone instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="52c3b-104">使用本主题中提供的步骤，您还可以准备系统以便重新安装 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="52c3b-104">By following the steps in this topic, you also prepare the system so that you can reinstall [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="52c3b-105">若要卸载 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]实例，您必须是拥有“作为服务登录”权限的本地管理员。</span><span class="sxs-lookup"><span data-stu-id="52c3b-105">To uninstall an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], you must be a local administrator with permission to log on as a service.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="52c3b-106">若要卸载 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 故障转移群集，请使用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 安装程序提供的删除节点功能分别删除每个节点。</span><span class="sxs-lookup"><span data-stu-id="52c3b-106">To uninstall a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] failover cluster, use the Remove Node functionality provided by [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Setup to remove each node individually.</span></span> <span data-ttu-id="52c3b-107">有关详细信息，请参阅[在 SQL Server 故障转移群集中添加或删除节点（安装程序）](../failover-clusters/install/add-or-remove-nodes-in-a-sql-server-failover-cluster-setup.md)</span><span class="sxs-lookup"><span data-stu-id="52c3b-107">For more information, see [Add or Remove Nodes in a SQL Server Failover Cluster &#40;Setup&#41;](../failover-clusters/install/add-or-remove-nodes-in-a-sql-server-failover-cluster-setup.md)</span></span>  
  
 <span data-ttu-id="52c3b-108">卸载 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 之前，请注意以下重要信息：</span><span class="sxs-lookup"><span data-stu-id="52c3b-108">Consider the following important information before you uninstall [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]:</span></span>  
  
-   <span data-ttu-id="52c3b-109">从内存大小为最小必需物理内存量的计算机中删除 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 组件前，请确保有足够大小的页文件。</span><span class="sxs-lookup"><span data-stu-id="52c3b-109">Before you remove [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] components from a computer that has the minimum required amount of physical memory, make sure that the page file size is sufficient.</span></span> <span data-ttu-id="52c3b-110">页文件大小必须等于物理内存量的两倍。</span><span class="sxs-lookup"><span data-stu-id="52c3b-110">The page file size must be equal to two times the amount of physical memory.</span></span> <span data-ttu-id="52c3b-111">虚拟内存不足会导致无法完全删除 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="52c3b-111">Insufficient virtual memory can cause an incomplete removal of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
-   <span data-ttu-id="52c3b-112">如果有多个 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]实例，则 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Browser 将在删除 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 的最后一个实例后自动卸载。</span><span class="sxs-lookup"><span data-stu-id="52c3b-112">If you have multiple instances of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Browser uninstalls automatically when the last instance of [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] is uninstalled.</span></span>  
  
     <span data-ttu-id="52c3b-113">如果您要卸载 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]的所有组件，则必须从 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] “控制面板” **中的** “程序和功能” **手动卸载**Browser 组件。</span><span class="sxs-lookup"><span data-stu-id="52c3b-113">If you want to uninstall all components of [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)], you must uninstall the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Browser component manually from **Programs and Features** in **Control Panel**.</span></span>  
  
### <a name="before-you-uninstall"></a><span data-ttu-id="52c3b-114">卸载之前</span><span class="sxs-lookup"><span data-stu-id="52c3b-114">Before You Uninstall</span></span>  
  
1.  <span data-ttu-id="52c3b-115">**备份数据。**</span><span class="sxs-lookup"><span data-stu-id="52c3b-115">**Back up your data.**</span></span> <span data-ttu-id="52c3b-116">尽管这不是必需的步骤，但您可能希望按照当前的状态保存数据库。</span><span class="sxs-lookup"><span data-stu-id="52c3b-116">Although this is not a required step, you might have databases that you want to save in their present state.</span></span> <span data-ttu-id="52c3b-117">可能还希望保存对系统数据库所做的更改。</span><span class="sxs-lookup"><span data-stu-id="52c3b-117">You might also want to save changes that were made to the system databases.</span></span> <span data-ttu-id="52c3b-118">无论哪种情况，请确保先备份数据，再卸载 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="52c3b-118">If either situation is true, make sure that back up the data before you uninstall [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="52c3b-119">或者，将所有数据和日志文件的副本保存在 MSSQL 文件夹以外的文件夹中。</span><span class="sxs-lookup"><span data-stu-id="52c3b-119">Alternatively, save a copy of all the data and log files in a folder other than the MSSQL folder.</span></span> <span data-ttu-id="52c3b-120">卸载期间 MSSQL 文件夹将被删除。</span><span class="sxs-lookup"><span data-stu-id="52c3b-120">The MSSQL folder is deleted during uninstallation.</span></span>  
  
     <span data-ttu-id="52c3b-121">必须保存的文件包括以下数据库文件：</span><span class="sxs-lookup"><span data-stu-id="52c3b-121">The files that you must save include the following database files:</span></span>  
  
    -   <span data-ttu-id="52c3b-122">Master.mdf</span><span class="sxs-lookup"><span data-stu-id="52c3b-122">Master.mdf</span></span>  
  
    -   <span data-ttu-id="52c3b-123">Mastlog.ldf</span><span class="sxs-lookup"><span data-stu-id="52c3b-123">Mastlog.ldf</span></span>  
  
    -   <span data-ttu-id="52c3b-124">Model.mdf</span><span class="sxs-lookup"><span data-stu-id="52c3b-124">Model.mdf</span></span>  
  
    -   <span data-ttu-id="52c3b-125">Modellog.ldf</span><span class="sxs-lookup"><span data-stu-id="52c3b-125">Modellog.ldf</span></span>  
  
    -   <span data-ttu-id="52c3b-126">Msdbdata.mdf</span><span class="sxs-lookup"><span data-stu-id="52c3b-126">Msdbdata.mdf</span></span>  
  
    -   <span data-ttu-id="52c3b-127">Msdblog.ldf</span><span class="sxs-lookup"><span data-stu-id="52c3b-127">Msdblog.ldf</span></span>  
  
    -   <span data-ttu-id="52c3b-128">Mssqlsystemresource.mdf</span><span class="sxs-lookup"><span data-stu-id="52c3b-128">Mssqlsystemresource.mdf</span></span>  
  
    -   <span data-ttu-id="52c3b-129">Mssqlsustemresource.ldf</span><span class="sxs-lookup"><span data-stu-id="52c3b-129">Mssqlsustemresource.ldf</span></span>  
  
    -   <span data-ttu-id="52c3b-130">Tempdb.mdf</span><span class="sxs-lookup"><span data-stu-id="52c3b-130">Tempdb.mdf</span></span>  
  
    -   <span data-ttu-id="52c3b-131">Templog.ldf</span><span class="sxs-lookup"><span data-stu-id="52c3b-131">Templog.ldf</span></span>  
  
    -   <span data-ttu-id="52c3b-132">`ReportServer[$InstanceName]` (Thisis [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 默认数据库。 ) </span><span class="sxs-lookup"><span data-stu-id="52c3b-132">`ReportServer[$InstanceName]` (Thisis the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] default database.)</span></span>  
  
    -   <span data-ttu-id="52c3b-133">ReportServer[$InstanceName]TempDB（这是 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 的默认临时数据库。）</span><span class="sxs-lookup"><span data-stu-id="52c3b-133">ReportServer[$InstanceName]TempDB (This is the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] default temporary database.)</span></span>  
  
2.  <span data-ttu-id="52c3b-134">**删除本地安全组。**</span><span class="sxs-lookup"><span data-stu-id="52c3b-134">**Delete the local security groups.**</span></span> <span data-ttu-id="52c3b-135">卸载 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]之前，应先删除用于 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 组件的本地安全组。</span><span class="sxs-lookup"><span data-stu-id="52c3b-135">Before you uninstall [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], delete the local security groups for [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] components.</span></span>  
  
3.  <span data-ttu-id="52c3b-136">停止所有\*\* 服务\*\*  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] \*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="52c3b-136">**Stop all**  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] **services.**</span></span> <span data-ttu-id="52c3b-137">建议先停止所有 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 服务，然后再卸载 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 组件的本地安全组。</span><span class="sxs-lookup"><span data-stu-id="52c3b-137">We recommend that you stop all [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] services before you uninstall [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] components.</span></span> <span data-ttu-id="52c3b-138">活动的连接可能会使卸载过程无法成功完成。</span><span class="sxs-lookup"><span data-stu-id="52c3b-138">Active connections can prevent successful uninstallation.</span></span>  
  
4.  <span data-ttu-id="52c3b-139">**使用具有适当权限的帐户。**</span><span class="sxs-lookup"><span data-stu-id="52c3b-139">**Use an account that has the appropriate permissions.**</span></span> <span data-ttu-id="52c3b-140">使用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 服务帐户或具有同等权限的帐户登录到服务器。</span><span class="sxs-lookup"><span data-stu-id="52c3b-140">Log on to the server by using the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] service account or by using an account that has equivalent permissions.</span></span> <span data-ttu-id="52c3b-141">例如，可以使用本地 Administrators 组的成员帐户登录到服务器。</span><span class="sxs-lookup"><span data-stu-id="52c3b-141">For example, you can log on to the server by using an account that is a member of the local Administrators group.</span></span>  
  
### <a name="to-uninstall-an-instance-of-ssnoversion"></a><span data-ttu-id="52c3b-142">To Uninstall an Instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]</span><span class="sxs-lookup"><span data-stu-id="52c3b-142">To Uninstall an Instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]</span></span>  
  
1.  <span data-ttu-id="52c3b-143">若要开始卸载过程，请转到 **“控制面板”** ，然后选择 **“程序和功能”**。</span><span class="sxs-lookup"><span data-stu-id="52c3b-143">To begin the uninstall process, go to **Control Panel** and then **Programs and Features**.</span></span>  
  
2.  <span data-ttu-id="52c3b-144">右键单击 **[!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssSQL14](../../includes/sssql14-md.md)]** 并选择 "**卸载**"。</span><span class="sxs-lookup"><span data-stu-id="52c3b-144">Right click **[!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssSQL14](../../includes/sssql14-md.md)]** and select **Uninstall**.</span></span> <span data-ttu-id="52c3b-145">然后单击 **“删除”**。</span><span class="sxs-lookup"><span data-stu-id="52c3b-145">Then click **Remove**.</span></span> <span data-ttu-id="52c3b-146">此时将启动 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 安装向导。</span><span class="sxs-lookup"><span data-stu-id="52c3b-146">This starts the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Installation Wizard.</span></span>  
  
     <span data-ttu-id="52c3b-147">将运行安装程序支持规则以验证您的计算机配置。</span><span class="sxs-lookup"><span data-stu-id="52c3b-147">Setup Support Rules runs to verify your computer configuration.</span></span> <span data-ttu-id="52c3b-148">若要继续，请单击 **“下一步”** 。</span><span class="sxs-lookup"><span data-stu-id="52c3b-148">To continue, click **Next**.</span></span>  
  
3.  <span data-ttu-id="52c3b-149">在“选择实例”页上，使用下拉框指定要删除的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 实例，或者指定与仅删除 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 共享功能和管理工具相对应的选项。</span><span class="sxs-lookup"><span data-stu-id="52c3b-149">On the Select Instance page, use the drop-down box to specify an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] to remove, or specify the option to remove only the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] shared features and management tools.</span></span> <span data-ttu-id="52c3b-150">若要继续，请单击 **“下一步”** 。</span><span class="sxs-lookup"><span data-stu-id="52c3b-150">To continue, click **Next**.</span></span>  
  
4.  <span data-ttu-id="52c3b-151">在“选择功能”页上指定要从指定的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]实例中删除的功能。</span><span class="sxs-lookup"><span data-stu-id="52c3b-151">On the Select Features page, specify the features to remove from the specified instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
     <span data-ttu-id="52c3b-152">将运行删除规则以验证是否可以成功完成删除操作。</span><span class="sxs-lookup"><span data-stu-id="52c3b-152">Removal rules runs to verify that the operation can complete successfully.</span></span>  
  
5.  <span data-ttu-id="52c3b-153">在 **“准备删除”** 页上查看要卸载的组件和功能的列表。</span><span class="sxs-lookup"><span data-stu-id="52c3b-153">On the **Ready to Remove** page, review the list of components and features that will be uninstalled.</span></span> <span data-ttu-id="52c3b-154">单击 **“删除”** 开始卸载</span><span class="sxs-lookup"><span data-stu-id="52c3b-154">Click **Remove** to begin uninstalling</span></span>  
  
6.  <span data-ttu-id="52c3b-155">在卸载最后一个 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 实例后，与 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 关联的其他程序仍显示在 **“程序和功能”** 的程序列表中。</span><span class="sxs-lookup"><span data-stu-id="52c3b-155">Immediately after you uninstall the last [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instance, the other programs associated with [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] will still be visible in the list of programs in **Programs and Features**.</span></span> <span data-ttu-id="52c3b-156">但是，如果关闭 **“程序和功能”**，则下次打开 **“程序和功能”** 时，将会刷新程序列表以仅显示仍实际安装的程序。</span><span class="sxs-lookup"><span data-stu-id="52c3b-156">However, if you close **Programs and Features**, the next time you open **Programs and Features**, it will refresh the list of programs, to show only the ones that are actually still installed.</span></span>  
  
### <a name="if-the-uninstallation-fails"></a><span data-ttu-id="52c3b-157">如果卸载失败</span><span class="sxs-lookup"><span data-stu-id="52c3b-157">If the Uninstallation Fails</span></span>  
  
1.  <span data-ttu-id="52c3b-158">如果卸载过程没有成功完成，请尝试修复造成卸载失败的问题。</span><span class="sxs-lookup"><span data-stu-id="52c3b-158">If the uninstallation process does not complete successfully, attempt to fix the problem that caused the uninstallation to fail.</span></span> <span data-ttu-id="52c3b-159">以下文章可帮助您了解卸载失败的原因：</span><span class="sxs-lookup"><span data-stu-id="52c3b-159">The following articles can help you understand the cause of the failed uninstallation:</span></span>  
  
    -   [<span data-ttu-id="52c3b-160">如何在安装日志文件中识别 SQL Server 2008 安装问题</span><span class="sxs-lookup"><span data-stu-id="52c3b-160">How to identify SQL Server 2008 setup issues in the setup log files</span></span>](https://support.microsoft.com/kb/955396/en-us)  
  
    -   [<span data-ttu-id="52c3b-161">查看和读取 SQL Server 安装程序日志文件</span><span class="sxs-lookup"><span data-stu-id="52c3b-161">View and Read SQL Server Setup Log Files</span></span>](../../database-engine/install-windows/view-and-read-sql-server-setup-log-files.md)  
  
2.  <span data-ttu-id="52c3b-162">如果无法修复卸载失败的原因，可与 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 支持部门联系。</span><span class="sxs-lookup"><span data-stu-id="52c3b-162">If you are unable to fix the cause of the uninstallation failure, you can contact [!INCLUDE[msCoName](../../includes/msconame-md.md)] Support.</span></span> <span data-ttu-id="52c3b-163">在某些情况下（如无意间删除了重要文件），则在计算机上重新安装 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 之前，可能需要重新安装操作系统。</span><span class="sxs-lookup"><span data-stu-id="52c3b-163">In some cases, such as unintentional deletion of important files, reinstalling the operating system may be required before reinstalling [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] on the computer.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="52c3b-164">另请参阅</span><span class="sxs-lookup"><span data-stu-id="52c3b-164">See Also</span></span>  
 [<span data-ttu-id="52c3b-165">查看和读取 SQL Server 安装程序日志文件</span><span class="sxs-lookup"><span data-stu-id="52c3b-165">View and Read SQL Server Setup Log Files</span></span>](../../database-engine/install-windows/view-and-read-sql-server-setup-log-files.md)  
  
  
