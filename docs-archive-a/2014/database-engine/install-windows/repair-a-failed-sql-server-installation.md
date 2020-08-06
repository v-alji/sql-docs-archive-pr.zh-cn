---
title: 修复 SQL Server 2014 安装 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: install
ms.topic: conceptual
ms.assetid: 90c11b28-892b-44d6-978e-0eee48c75b7d
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: f3e382137a971b3f8b23cf1d814bff9908f04150
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87690025"
---
# <a name="drop-a-sql-server-2014-installation"></a><span data-ttu-id="8bf55-102">删除 SQL Server 2014 安装</span><span class="sxs-lookup"><span data-stu-id="8bf55-102">Drop a SQL Server 2014 Installation</span></span>
  <span data-ttu-id="8bf55-103">可以在以下情况下使用修复操作：</span><span class="sxs-lookup"><span data-stu-id="8bf55-103">Repair operation can be used in the following scenarios:</span></span>  
  
-   <span data-ttu-id="8bf55-104">修复在成功安装后损坏的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 实例。</span><span class="sxs-lookup"><span data-stu-id="8bf55-104">Repair an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] that is corrupted after it was successfully installed.</span></span>  
  
-   <span data-ttu-id="8bf55-105">如果在将实例名称映射到新升级的实例后取消了升级操作或升级操作失败，修复 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 实例。</span><span class="sxs-lookup"><span data-stu-id="8bf55-105">Repair an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] if the upgrade operation is cancelled or fails after the instance name is mapped to the newly-upgraded instance.</span></span>  
  
    -   <span data-ttu-id="8bf55-106">如果在摘要日志中看到以下消息，则可以修复失败的升级实例：</span><span class="sxs-lookup"><span data-stu-id="8bf55-106">If you see the following message in the summary log, you can repair the failed upgrade instance:</span></span>  
  
         <span data-ttu-id="8bf55-107">“[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 升级失败。</span><span class="sxs-lookup"><span data-stu-id="8bf55-107">"[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] upgrade failed.</span></span> <span data-ttu-id="8bf55-108">若要继续操作，请调查失败的原因，更正问题，然后修复您的安装。”</span><span class="sxs-lookup"><span data-stu-id="8bf55-108">To continue, investigate the reason for the failure, correct the problem, and then repair your installation."</span></span>  
  
    -   <span data-ttu-id="8bf55-109">如果在摘要日志中看到以下消息，则需要先卸载再重新安装 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="8bf55-109">If you see the following message in the summary log, you need to uninstall and reinstall [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="8bf55-110">不能修复 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 实例。</span><span class="sxs-lookup"><span data-stu-id="8bf55-110">You cannot repair the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instance.</span></span>  
  
         <span data-ttu-id="8bf55-111">“[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 升级失败。</span><span class="sxs-lookup"><span data-stu-id="8bf55-111">"[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] upgrade failed.</span></span> <span data-ttu-id="8bf55-112">若要继续操作，请调查失败的原因，更正问题。”</span><span class="sxs-lookup"><span data-stu-id="8bf55-112">To continue, investigate the reason for the failure, correct the problem."</span></span>  
  
 <span data-ttu-id="8bf55-113">在修复 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]的实例时：</span><span class="sxs-lookup"><span data-stu-id="8bf55-113">When you repair an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]:</span></span>  
  
-   <span data-ttu-id="8bf55-114">将替换所有缺失或损坏的文件。</span><span class="sxs-lookup"><span data-stu-id="8bf55-114">All missing or corrupt files are replaced.</span></span>  
  
-   <span data-ttu-id="8bf55-115">将替换所有缺失或损坏的注册表项。</span><span class="sxs-lookup"><span data-stu-id="8bf55-115">All missing or corrupt registry keys are replaced.</span></span>  
  
-   <span data-ttu-id="8bf55-116">所有缺失或无效的配置值将设置为默认值。</span><span class="sxs-lookup"><span data-stu-id="8bf55-116">All missing or invalid configuration values are set to default values.</span></span>  
  
 <span data-ttu-id="8bf55-117">继续之前，请查阅有关 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 故障转移群集的以下重要信息：</span><span class="sxs-lookup"><span data-stu-id="8bf55-117">Before you continue, for [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] failover clusters, review the following important information:</span></span>  
  
-   <span data-ttu-id="8bf55-118">必须在单个群集节点上运行修复。</span><span class="sxs-lookup"><span data-stu-id="8bf55-118">Repair must be run on individual cluster nodes.</span></span>  
  
-   <span data-ttu-id="8bf55-119">若要在“准备”操作失败之后修复故障转移群集节点，请使用 **“删除节点”** ，然后再次执行“准备”步骤。</span><span class="sxs-lookup"><span data-stu-id="8bf55-119">To repair a failover cluster node after a failed Prepare operation, use **Remove node** and then perform the Prepare step again.</span></span> <span data-ttu-id="8bf55-120">有关详细信息，请参阅[在 SQL Server 故障转移群集中添加或删除节点（安装程序）](../../sql-server/failover-clusters/install/add-or-remove-nodes-in-a-sql-server-failover-cluster-setup.md)。</span><span class="sxs-lookup"><span data-stu-id="8bf55-120">For more information, see [Add or Remove Nodes in a SQL Server Failover Cluster &#40;Setup&#41;](../../sql-server/failover-clusters/install/add-or-remove-nodes-in-a-sql-server-failover-cluster-setup.md).</span></span>  
  
### <a name="to-repair-a-failed-installation-of-ssnoversion-from-the-installation-center"></a><span data-ttu-id="8bf55-121">从安装中心修复失败的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 安装</span><span class="sxs-lookup"><span data-stu-id="8bf55-121">To repair a failed installation of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] from the Installation Center</span></span>  
  
1.  <span data-ttu-id="8bf55-122">从 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 安装介质中启动 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 安装程序 (setup.exe)。</span><span class="sxs-lookup"><span data-stu-id="8bf55-122">Launch the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Setup program (setup.exe) from [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] installation media.</span></span>  
  
2.  <span data-ttu-id="8bf55-123">安装必备组件并进行系统验证之后，安装程序会显示“[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 安装中心”页。</span><span class="sxs-lookup"><span data-stu-id="8bf55-123">After prerequisites and system verification, the Setup program will display the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Installation Center page.</span></span>  
  
3.  <span data-ttu-id="8bf55-124">单击左侧导航区域中的“维护”  ，然后单击“修复”  启动修复操作。</span><span class="sxs-lookup"><span data-stu-id="8bf55-124">Click **Maintenance** in the left-hand navigation area, and then click **Repair** to start the repair operation.</span></span>  
  
    > [!TIP]  
    >  <span data-ttu-id="8bf55-125">如果使用“开始”菜单启动了安装中心，您将需要在此时提供安装介质的位置。</span><span class="sxs-lookup"><span data-stu-id="8bf55-125">If the Installation Center was launched using the start menu, you will need to provide the location of the installation media at this time.</span></span>  
  
4.  <span data-ttu-id="8bf55-126">将运行安装程序支持规则和文件例程，以确保您的系统上安装了必备组件，并且计算机能够通过安装程序验证规则。</span><span class="sxs-lookup"><span data-stu-id="8bf55-126">Setup support rule and file routines will run to ensure that your system has prerequisites installed and that the computer passes Setup validation rules.</span></span> <span data-ttu-id="8bf55-127">单击 **“确定”** 或 **“安装”** 以继续操作。</span><span class="sxs-lookup"><span data-stu-id="8bf55-127">Click **OK** or **Install** to continue.</span></span>  
  
5.  <span data-ttu-id="8bf55-128">在“选择实例”页上选择要修复的实例，然后单击 **“下一步”** 继续操作。</span><span class="sxs-lookup"><span data-stu-id="8bf55-128">On the Select Instance page, select the instance to repair, and then click **Next** to continue.</span></span>  
  
6.  <span data-ttu-id="8bf55-129">将运行修复规则以验证修复操作。</span><span class="sxs-lookup"><span data-stu-id="8bf55-129">The repair rules will run to validate the operation.</span></span> <span data-ttu-id="8bf55-130">若要继续，请单击 **“下一步”** 。</span><span class="sxs-lookup"><span data-stu-id="8bf55-130">To continue, click **Next**.</span></span>  
  
7.  <span data-ttu-id="8bf55-131">“准备修复”页指示修复操作已准备就绪，可以继续。</span><span class="sxs-lookup"><span data-stu-id="8bf55-131">The Ready to Repair page indicates that the operation is ready to proceed.</span></span> <span data-ttu-id="8bf55-132">若要继续，请单击 **“修复”** 。</span><span class="sxs-lookup"><span data-stu-id="8bf55-132">To continue, click **Repair**.</span></span>  
  
8.  <span data-ttu-id="8bf55-133">“修复进度”页显示修复操作的状态。</span><span class="sxs-lookup"><span data-stu-id="8bf55-133">The Repair Progress page shows the status of the repair operation.</span></span> <span data-ttu-id="8bf55-134">“完成”页指示修复操作已完成。</span><span class="sxs-lookup"><span data-stu-id="8bf55-134">The Complete page indicates that the operation is finished.</span></span>  
  
### <a name="to-repair-a-failed-installation-of-ssnoversion-using-command-prompt"></a><span data-ttu-id="8bf55-135">使用命令提示符修复失败的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 安装</span><span class="sxs-lookup"><span data-stu-id="8bf55-135">To repair a failed installation of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] using Command Prompt</span></span>  
  
1.  <span data-ttu-id="8bf55-136">在命令提示符下运行以下命令：</span><span class="sxs-lookup"><span data-stu-id="8bf55-136">Run the following command at a command prompt:</span></span>  
  
    ```  
    Setup.exe /q /ACTION=Repair /INSTANCENAME=instancename  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="8bf55-137">另请参阅</span><span class="sxs-lookup"><span data-stu-id="8bf55-137">See Also</span></span>  
 <span data-ttu-id="8bf55-138">[查看和读取 SQL Server 安装程序日志文件](view-and-read-sql-server-setup-log-files.md) </span><span class="sxs-lookup"><span data-stu-id="8bf55-138">[View and Read SQL Server Setup Log Files](view-and-read-sql-server-setup-log-files.md) </span></span>  
 [<span data-ttu-id="8bf55-139">安装操作指南主题</span><span class="sxs-lookup"><span data-stu-id="8bf55-139">Installation How-to Topics</span></span>](../../sql-server/install/installation-how-to-topics.md)  
  
  
