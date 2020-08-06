---
title: 在 SQL Server 故障转移群集上安装客户端工具 | Microsoft Docs
ms.custom: ''
ms.date: 03/09/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: install
ms.topic: conceptual
ms.assetid: 3c82d510-9798-46be-bebb-cac9bef56936
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: b9cd0b426c01ebdb6f61d164302963ac3c7ff8aa
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87586291"
---
# <a name="install-client-tools-on-a-sql-server-failover-cluster"></a><span data-ttu-id="cffea-102">在 SQL Server 故障转移群集上安装客户端工具</span><span class="sxs-lookup"><span data-stu-id="cffea-102">Install Client Tools on a SQL Server Failover Cluster</span></span>
  <span data-ttu-id="cffea-103">诸如 [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] 的客户端工具是在同一台计算机上的所有实例间公用的共享功能。</span><span class="sxs-lookup"><span data-stu-id="cffea-103">Client tools such as [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] are shared features common across all instances on the same machine.</span></span> <span data-ttu-id="cffea-104">它们与支持的、可并行安装的 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 版本兼容。</span><span class="sxs-lookup"><span data-stu-id="cffea-104">They are backward compatible, with supported [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] versions that can be installed side by side.</span></span> <span data-ttu-id="cffea-105">在某一时刻，节点上只能存在客户端工具的一个版本。</span><span class="sxs-lookup"><span data-stu-id="cffea-105">Only one version of the client tool exists on a node at a time.</span></span>  
  
 <span data-ttu-id="cffea-106">如果在 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 群集的第一个节点上进行安装时安装了 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 客户端工具，它们将自动添加到稍后可能使用“添加节点”功能添加到 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 的实例的任何节点。</span><span class="sxs-lookup"><span data-stu-id="cffea-106">If the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] client tools are installed during setup on first node of the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] cluster, they are automatically added to any nodes that may be added later to the instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] using Add Node.</span></span>  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] <span data-ttu-id="cffea-107">联机丛书不会自动添加到使用“添加节点”功能添加到 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 群集的其他节点。</span><span class="sxs-lookup"><span data-stu-id="cffea-107">Books Online is not automatically added to the additional nodes added to the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] cluster using Add Node.</span></span> [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] <span data-ttu-id="cffea-108">联机丛书手动安装到您希望具有 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 联机丛书的本地副本的节点上。</span><span class="sxs-lookup"><span data-stu-id="cffea-108">Books Online can be installed manually on the nodes that you wish to have a local copy of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Books Online.</span></span>  
  
 <span data-ttu-id="cffea-109">如果在 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 群集的初始安装过程中没有安装 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 客户端工具，稍后可按下面的过程中所述进行安装。</span><span class="sxs-lookup"><span data-stu-id="cffea-109">If you do not install the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] client tools during the initial installation of the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] cluster, you can install it later as described in the procedures below.</span></span>  
  
## <a name="installation-procedures"></a><span data-ttu-id="cffea-110">安装过程</span><span class="sxs-lookup"><span data-stu-id="cffea-110">Installation procedures</span></span>  
  
#### <a name="installing-ssnoversion-client-tools-using-the-setup-user-interface"></a><span data-ttu-id="cffea-111">使用安装程序用户界面安装 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 客户端工具</span><span class="sxs-lookup"><span data-stu-id="cffea-111">Installing [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Client Tools Using the Setup User Interface</span></span>  
  
1.  <span data-ttu-id="cffea-112">插入 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 安装介质，</span><span class="sxs-lookup"><span data-stu-id="cffea-112">Insert the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] installation media.</span></span> <span data-ttu-id="cffea-113">然后双击根安装文件夹中的 Setup.exe。</span><span class="sxs-lookup"><span data-stu-id="cffea-113">From the root installation folder, double click Setup.exe.</span></span> <span data-ttu-id="cffea-114">若要从网络共享进行安装，请找到共享中的根文件夹，然后双击 Setup.exe。</span><span class="sxs-lookup"><span data-stu-id="cffea-114">To install from the network share, locate the root folder on the share, and then double-click Setup.exe.</span></span>  
  
2.  <span data-ttu-id="cffea-115">在“安装”  页上，单击“全新” **[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]独立安装或向现有安装添加功能**。</span><span class="sxs-lookup"><span data-stu-id="cffea-115">On the **Installation** page, click **New [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] stand-alone installation or add Features to an existing installation**.</span></span> <span data-ttu-id="cffea-116">请勿单击“新建” **[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]故障转移群集安装**。</span><span class="sxs-lookup"><span data-stu-id="cffea-116">Do not click **New [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] failover cluster installation**.</span></span>  
  
3.  <span data-ttu-id="cffea-117">系统配置检查器将验证计算机的系统状态，然后安装程序继续运行。</span><span class="sxs-lookup"><span data-stu-id="cffea-117">The system configuration checker verifies the system state of your computer before Setup will continue.</span></span>  
  
4.  <span data-ttu-id="cffea-118">在“安装类型”  页上，单击“执行全新安装” **[!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)]** 。</span><span class="sxs-lookup"><span data-stu-id="cffea-118">On the **Installation Type** page, click **Perform a new installation of [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)]**.</span></span>  
  
5.  <span data-ttu-id="cffea-119">在 **“功能选择”** 页上，选择需要安装的工具，然后按照安装过程的剩余步骤操作。</span><span class="sxs-lookup"><span data-stu-id="cffea-119">On the **Feature Selection** page, select the tools that you want to install and follow through the rest of the steps of the Setup process.</span></span>  
  
#### <a name="installing-ssnoversion-client-tools-at-the-command-prompt"></a><span data-ttu-id="cffea-120">在命令提示符处安装 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 客户端工具</span><span class="sxs-lookup"><span data-stu-id="cffea-120">Installing [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] client tools at the command prompt</span></span>  
  
1.  <span data-ttu-id="cffea-121">若要安装 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 客户端工具和 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 联机丛书，请运行以下命令：Setup.exe/q/Action=Install /Features=Tools</span><span class="sxs-lookup"><span data-stu-id="cffea-121">To install [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] client tools and [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Books Online, run the following command: Setup.exe/q/Action=Install /Features=Tools</span></span>  
  
2.  <span data-ttu-id="cffea-122">若要只安装基本 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 管理工具，请运行以下命令：Setup.exe/q/Action=Install Features=SSMS。</span><span class="sxs-lookup"><span data-stu-id="cffea-122">To install only the basic [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Management tools run the following command: Setup.exe/q/Action=Install Features=SSMS.</span></span> <span data-ttu-id="cffea-123">这将为 [!INCLUDE[ssManStudio](../../../includes/ssmanstudio-md.md)] 、 [!INCLUDE[ssDEnoversion](../../../includes/ssdenoversion-md.md)]、sqlcmd 实用工具以及 [!INCLUDE[ssExpress](../../../includes/ssexpress-md.md)]Powershell 提供程序安装 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 支持。</span><span class="sxs-lookup"><span data-stu-id="cffea-123">This will install [!INCLUDE[ssManStudio](../../../includes/ssmanstudio-md.md)] support for [!INCLUDE[ssDEnoversion](../../../includes/ssdenoversion-md.md)], [!INCLUDE[ssExpress](../../../includes/ssexpress-md.md)], sqlcmd utility, and the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Powershell provider.</span></span>  
  
3.  <span data-ttu-id="cffea-124">若要安装完整的 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 管理工具，请运行以下命令：Setup.exe/q/Action=Install /Features=ADV_SSMS。</span><span class="sxs-lookup"><span data-stu-id="cffea-124">To install the complete [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Management tools, run the following command: Setup.exe/q/Action=Install /Features=ADV_SSMS.</span></span> <span data-ttu-id="cffea-125">有关功能的参数值的详细信息，请参阅[从命令提示符安装 SQL Server 2014](../../../database-engine/install-windows/install-sql-server-from-the-command-prompt.md)。</span><span class="sxs-lookup"><span data-stu-id="cffea-125">For more information about parameter values for the features, see [Install SQL Server 2014 from the Command Prompt](../../../database-engine/install-windows/install-sql-server-from-the-command-prompt.md).</span></span>  
  
### <a name="uninstalling-ssnoversion-client-tools"></a><span data-ttu-id="cffea-126">卸载 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 客户端工具</span><span class="sxs-lookup"><span data-stu-id="cffea-126">Uninstalling [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Client Tools</span></span>  
 <span data-ttu-id="cffea-127">它们在“控制面板”的“添加或删除程序”中显示为 **[!INCLUDE[msCoName](../../../includes/msconame-md.md)][!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)]** ，可从此处将其删除。</span><span class="sxs-lookup"><span data-stu-id="cffea-127">They appear in Add or Remove programs in Control Panel as **[!INCLUDE[msCoName](../../../includes/msconame-md.md)][!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)]**, and can be removed from there.</span></span> <span data-ttu-id="cffea-128">当使用“删除节点”从故障转移群集中卸载 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 的实例时，并不同时卸载这些客户端组件。</span><span class="sxs-lookup"><span data-stu-id="cffea-128">When you use Remove Node to uninstall an instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] from the failover cluster, the client components are not uninstalled at the same time.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cffea-129">另请参阅</span><span class="sxs-lookup"><span data-stu-id="cffea-129">See Also</span></span>  
 [<span data-ttu-id="cffea-130">查看和读取 SQL Server 安装程序日志文件</span><span class="sxs-lookup"><span data-stu-id="cffea-130">View and Read SQL Server Setup Log Files</span></span>](../../../database-engine/install-windows/view-and-read-sql-server-setup-log-files.md)  
  
  
