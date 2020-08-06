---
title: 添加和删除扩展部署的加密密钥 (SSRS Configuration Manager) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- encryption keys [Reporting Services]
- deleting encryption keys
- removing encryption keys
- adding encryption keys
- rskeymgmt utility
- scale-out deployments [Reporting Services]
ms.assetid: 2da86fb3-4b4d-407f-9825-74dcc42486f5
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 3926e57c1ad3bb884af8debf7f831092b223a3cb
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87694323"
---
# <a name="add-and-remove-encryption-keys-for-scale-out-deployment-ssrs-configuration-manager"></a><span data-ttu-id="6ff6a-102">添加和删除扩展部署的加密密钥（SSRS 配置管理器）</span><span class="sxs-lookup"><span data-stu-id="6ff6a-102">Add and Remove Encryption Keys for Scale-Out Deployment (SSRS Configuration Manager)</span></span>
  <span data-ttu-id="6ff6a-103">通过将多个报表服务器配置为使用一个共享的报表服务器数据库，可以在扩展部署模型中运行 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="6ff6a-103">You can run [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] in a scale-out deployment model by configuring multiple report servers to use a shared report server database.</span></span> <span data-ttu-id="6ff6a-104">扩展部署中的成员身份是基于报表服务器是否将加密密钥存储在报表服务器数据库中。</span><span class="sxs-lookup"><span data-stu-id="6ff6a-104">Membership in a scale-out deployment is based on whether the report server stores an encryption key in the report server database.</span></span> <span data-ttu-id="6ff6a-105">通过为特定的报表服务器实例添加和删除加密密钥，可以控制扩展部署成员身份。</span><span class="sxs-lookup"><span data-stu-id="6ff6a-105">You can control scale-out deployment membership by adding and removing encryption keys for specific report server instances.</span></span> <span data-ttu-id="6ff6a-106">如果要从部署中删除节点，则可以按任意顺序进行删除。</span><span class="sxs-lookup"><span data-stu-id="6ff6a-106">If you are removing nodes from the deployment, you can remove them in any order.</span></span> <span data-ttu-id="6ff6a-107">如果要向部署中添加节点，则必须联接已作为部署的一部分的报表服务器中的所有新实例。</span><span class="sxs-lookup"><span data-stu-id="6ff6a-107">If you are adding nodes to a deployment, you must join any new instances from a report server that is already part of the deployment.</span></span>  
  
## <a name="using-the-reporting-services-configuration-tool-to-configure-scale-out-deployment"></a><span data-ttu-id="6ff6a-108">使用 Reporting Services 配置工具配置扩展部署</span><span class="sxs-lookup"><span data-stu-id="6ff6a-108">Using the Reporting Services Configuration Tool to Configure Scale-Out Deployment</span></span>  
 <span data-ttu-id="6ff6a-109">配置扩展部署的最简单方法是使用 Reporting Services 配置工具。</span><span class="sxs-lookup"><span data-stu-id="6ff6a-109">The easiest way to configure a scale-out deployment is to use the Reporting Services Configuration tool.</span></span> <span data-ttu-id="6ff6a-110">有关详细信息以及分步说明，请参阅[配置本机模式报表服务器扩展部署（SSRS 配置管理器）](configure-a-native-mode-report-server-scale-out-deployment.md)。</span><span class="sxs-lookup"><span data-stu-id="6ff6a-110">For more information and step-by-step instructions, see [Configure a Native Mode Report Server Scale-Out Deployment &#40;SSRS Configuration Manager&#41;](configure-a-native-mode-report-server-scale-out-deployment.md).</span></span>  
  
## <a name="using-rskeymgmt-to-configure-scale-out-deployment"></a><span data-ttu-id="6ff6a-111">使用 Rskeymgmt 配置扩展部署</span><span class="sxs-lookup"><span data-stu-id="6ff6a-111">Using Rskeymgmt to Configure Scale-Out Deployment</span></span>  
 <span data-ttu-id="6ff6a-112">使用 **rskeymgmt** 实用工具，可以将报表服务器实例初始化为使用共享的报表服务器数据库。</span><span class="sxs-lookup"><span data-stu-id="6ff6a-112">Use the **rskeymgmt** utility to initialize a report server instance to use a shared report server database.</span></span> <span data-ttu-id="6ff6a-113">要向扩展部署中添加报表服务器，需要初始化报表服务器。</span><span class="sxs-lookup"><span data-stu-id="6ff6a-113">Adding a report server to a scale-out deployment requires that you initialize the report server.</span></span> <span data-ttu-id="6ff6a-114">要进行初始化，需要有管理员权限。</span><span class="sxs-lookup"><span data-stu-id="6ff6a-114">Initialization requires administrator permissions.</span></span> <span data-ttu-id="6ff6a-115">对于承载要加入部署的报表服务器的远程计算机，您必须拥有管理员凭据。</span><span class="sxs-lookup"><span data-stu-id="6ff6a-115">You must have administrator credentials for the remote computer that hosts the report server you are joining to the deployment.</span></span>  
  
#### <a name="how-to-join-a-report-server-to-a-scale-out-deployment-rskeymgmt"></a><span data-ttu-id="6ff6a-116">如何将报表服务器加入扩展部署 (rskeymgmt)</span><span class="sxs-lookup"><span data-stu-id="6ff6a-116">How to join a report server to a scale-out deployment (rskeymgmt)</span></span>  
  
1.  <span data-ttu-id="6ff6a-117">在特定计算机的本地运行 **rskeymgmt.exe** ，该计算机承载已经是报表服务器扩展部署成员的报表服务器。</span><span class="sxs-lookup"><span data-stu-id="6ff6a-117">Run **rskeymgmt.exe** locally on the computer that hosts a report server that is already a member of the report server scale-out deployment.</span></span>  
  
2.  <span data-ttu-id="6ff6a-118">使用 `-j` 参数将报表服务器加入报表服务器数据库。</span><span class="sxs-lookup"><span data-stu-id="6ff6a-118">Use the `-j` argument to join a report server to the report server database.</span></span> <span data-ttu-id="6ff6a-119">使用 `-m` 和 `-n` 参数指定要添加到部署中的远程报表服务器实例。</span><span class="sxs-lookup"><span data-stu-id="6ff6a-119">Use the `-m` and `-n` arguments to specify the remote report server instance you want to add to the deployment.</span></span> <span data-ttu-id="6ff6a-120">使用 `-u` 和 `-v` 参数指定远程计算机上的管理员帐户。</span><span class="sxs-lookup"><span data-stu-id="6ff6a-120">Use the `-u` and `-v` arguments to specify an administrator account on the remote computer.</span></span> <span data-ttu-id="6ff6a-121">如果要使用同一台计算机中的多个报表服务器实例创建扩展部署，则使用的语法会稍有不同。</span><span class="sxs-lookup"><span data-stu-id="6ff6a-121">If you are creating a scale-out deployment using multiple report server instances on the same computer, the syntax to use is slightly different.</span></span> <span data-ttu-id="6ff6a-122">有关应使用的语法的详细信息，请参阅 [rskeymgmt 实用工具 (SSRS)](../tools/rskeymgmt-utility-ssrs.md)。</span><span class="sxs-lookup"><span data-stu-id="6ff6a-122">For more information about the syntax you should use, see [rskeymgmt Utility &#40;SSRS&#41;](../tools/rskeymgmt-utility-ssrs.md).</span></span>  
  
     <span data-ttu-id="6ff6a-123">下面的示例说明了将远程报表服务器加入扩展部署时必须指定的参数（如果您对远程计算机拥有管理员权限，则可以忽略凭据）：</span><span class="sxs-lookup"><span data-stu-id="6ff6a-123">The following example illustrates the arguments you must specify if you are joining a remote report server to a scale-out deployment (you can omit credentials if you have administrator permissions on the remote computer):</span></span>  
  
    ```  
    rskeymgmt -j -m <remotecomputer> -n <namedreportserverinstance> -u <administratoraccount> -v <administratorpassword>  
    ```  
  
#### <a name="how-to-remove-a-report-server-from-a-scale-out-deployment-rskeymgmt"></a><span data-ttu-id="6ff6a-124">如何从扩展部署 (rskeymgmt) 中删除报表服务器</span><span class="sxs-lookup"><span data-stu-id="6ff6a-124">How to remove a report server from a scale-out deployment (rskeymgmt)</span></span>  
  
1.  <span data-ttu-id="6ff6a-125">打开要删除的报表服务器的 rsreportserver.config 文件，找到安装 ID。</span><span class="sxs-lookup"><span data-stu-id="6ff6a-125">Open the rsreportserver.config file of the report server you want to remove and find the installation ID.</span></span> <span data-ttu-id="6ff6a-126">默认情况下，此文件位于 Program Files\Microsoft SQL Server\MSSQL.*n*\Reporting Services\ReportServer)。</span><span class="sxs-lookup"><span data-stu-id="6ff6a-126">By default, this file is located at Program Files\Microsoft SQL Server\MSSQL.*n*\Reporting Services\ReportServer).</span></span>  
  
     <span data-ttu-id="6ff6a-127">如果安装了单个实例，则计算机中只有一个 rsreportserver.config 文件。</span><span class="sxs-lookup"><span data-stu-id="6ff6a-127">If you installed a single instance, there will only be one rsreportserver.config file on the computer.</span></span> <span data-ttu-id="6ff6a-128">如果安装了多个 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 实例，则请使用 Reporting Services 配置工具中的“服务器状态”页来查找要删除的报表服务器的实例标识符（例如，MSSQL.2）。</span><span class="sxs-lookup"><span data-stu-id="6ff6a-128">If multiple instances of [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] are installed, use the Server Status page in the Reporting Services Configuration tool to find the instance identifier (for example, MSSQL.2) for the report server that you want to remove.</span></span> <span data-ttu-id="6ff6a-129">为报表服务器实例存储程序文件的文件夹名称将基于实例标识符来命名（例如，Program Files\Microsoft SQL Server\MSSQL.2）。</span><span class="sxs-lookup"><span data-stu-id="6ff6a-129">The name of the folder that stores the program files for the report server instance will be based on the instance identifier (for example, Program Files\Microsoft SQL Server\MSSQL.2).</span></span>  
  
2.  <span data-ttu-id="6ff6a-130">运行 **rskeymgmt.exe**。</span><span class="sxs-lookup"><span data-stu-id="6ff6a-130">Run **rskeymgmt.exe**.</span></span> <span data-ttu-id="6ff6a-131">可以在属于报表服务器扩展部署一部分的任何报表服务器上运行该文件。</span><span class="sxs-lookup"><span data-stu-id="6ff6a-131">You can run it on any report server that is part of the report server scale-out deployment.</span></span>  
  
3.  <span data-ttu-id="6ff6a-132">使用 `-r` 参数从扩展部署中释放该报表服务器实例。</span><span class="sxs-lookup"><span data-stu-id="6ff6a-132">Use the `-r` argument to release the report server instance from the scale-out deployment.</span></span> <span data-ttu-id="6ff6a-133">下面的示例演示必须指定的参数：</span><span class="sxs-lookup"><span data-stu-id="6ff6a-133">The following example illustrates the arguments you must specify:</span></span>  
  
    ```  
    rskeymgmt -r <installation ID>  
    ```  
  
 <span data-ttu-id="6ff6a-134">这些步骤从扩展部署中删除报表服务器，但不会卸载报表服务器上的 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 实例。</span><span class="sxs-lookup"><span data-stu-id="6ff6a-134">These steps remove the report server from a scale-out deployment, but they do not uninstall the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] instance on the report server.</span></span> <span data-ttu-id="6ff6a-135">从扩展部署中删除报表服务器之后，如果不再需要服务器上的 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] ，则可以卸载该服务器上的 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="6ff6a-135">After you remove the report server from the scale-out deployment, you can uninstall [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] from the server if you no longer need [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] on that server.</span></span> <span data-ttu-id="6ff6a-136">有关信息，请参阅 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 联机丛书中的[卸载现有 SQL Server 实例（安装程序）](../../sql-server/install/uninstall-an-existing-instance-of-sql-server-setup.md)。</span><span class="sxs-lookup"><span data-stu-id="6ff6a-136">For information, see [Uninstall an Existing Instance of SQL Server &#40;Setup&#41;](../../sql-server/install/uninstall-an-existing-instance-of-sql-server-setup.md) in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Books Online.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6ff6a-137">另请参阅</span><span class="sxs-lookup"><span data-stu-id="6ff6a-137">See Also</span></span>  
 <span data-ttu-id="6ff6a-138">[&#40;SSRS Configuration Manager 中配置和管理加密密钥&#41;](ssrs-encryption-keys-manage-encryption-keys.md) </span><span class="sxs-lookup"><span data-stu-id="6ff6a-138">[Configure and Manage Encryption Keys &#40;SSRS Configuration Manager&#41;](ssrs-encryption-keys-manage-encryption-keys.md) </span></span>  
 [<span data-ttu-id="6ff6a-139">初始化 Report Server（SSRS 配置管理器）</span><span class="sxs-lookup"><span data-stu-id="6ff6a-139">Initialize a Report Server &#40;SSRS Configuration Manager&#41;</span></span>](ssrs-encryption-keys-initialize-a-report-server.md)  
  
  
