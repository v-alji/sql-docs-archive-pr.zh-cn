---
title: 检查正在使用的文件 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
ms.assetid: ccd65867-d4c0-43b2-8361-7fd41c6f79ac
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: 51505b0dece146b7f6fcdf982e6f88a5715357e1
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87586211"
---
# <a name="check-files-in-use"></a><span data-ttu-id="32a53-102">检查正在使用的文件</span><span class="sxs-lookup"><span data-stu-id="32a53-102">Check Files In Use</span></span>
  <span data-ttu-id="32a53-103">若要避免在安装 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 更新后重新启动 Windows，请使用“检查正在使用的文件”页来识别锁定 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 更新安装程序所需文件的进程。</span><span class="sxs-lookup"><span data-stu-id="32a53-103">To avoid restarting Windows after you install [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] updates, use the Check Files in Use page to identify processes that are locking files required by the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] update Setup program.</span></span>  
  
 <span data-ttu-id="32a53-104">停止与正在更新的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 实例连接的所有应用程序和服务。</span><span class="sxs-lookup"><span data-stu-id="32a53-104">Stop all applications and services that make connections to the instances of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] that are being updated.</span></span> <span data-ttu-id="32a53-105">包括停止 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 和 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="32a53-105">This includes stopping [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] and [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)].</span></span>  
  
 <span data-ttu-id="32a53-106">如果安装程序确定在安装过程中文件已被锁定，那么，您在安装完成后可能必须重新启动计算机。</span><span class="sxs-lookup"><span data-stu-id="32a53-106">If Setup determines that files are locked during installation, you might have to restart your computer after installation is completed.</span></span> <span data-ttu-id="32a53-107">如有必要，安装程序会提示您重新启动计算机。</span><span class="sxs-lookup"><span data-stu-id="32a53-107">If necessary, Setup prompts you to restart your computer.</span></span> <span data-ttu-id="32a53-108">如果安装程序必须在安装过程中停止某个服务，则在安装完成后将重新启动这个服务。</span><span class="sxs-lookup"><span data-stu-id="32a53-108">If the Setup program must stop a service during installation, it will restart the service after installation is completed.</span></span>  
  
 <span data-ttu-id="32a53-109">为了使安装后无需重新启动计算机，安装程序将显示正在锁定文件的进程的列表。</span><span class="sxs-lookup"><span data-stu-id="32a53-109">To eliminate the requirement to restart your computer after installation, Setup displays a list of processes that are locking files.</span></span> <span data-ttu-id="32a53-110">停止或结束列表中的进程和应用程序。</span><span class="sxs-lookup"><span data-stu-id="32a53-110">Stop or end the processes and applications in the list.</span></span> <span data-ttu-id="32a53-111">然后，单击 **“刷新检查”** 重新运行相应检查。</span><span class="sxs-lookup"><span data-stu-id="32a53-111">Then click **Refresh check** to rerun the check.</span></span> <span data-ttu-id="32a53-112">单击 **“停职检查”** 结束正在运行的检查。</span><span class="sxs-lookup"><span data-stu-id="32a53-112">Click **Stop check** to end a check that is running.</span></span> <span data-ttu-id="32a53-113">如果找不到锁定的文件，则该表为空。</span><span class="sxs-lookup"><span data-stu-id="32a53-113">If locked files are not found, the table is empty.</span></span> <span data-ttu-id="32a53-114">关闭或停止所有锁定的进程以后，单击 **“下一步”** 继续。</span><span class="sxs-lookup"><span data-stu-id="32a53-114">When all locked processes have been closed or stopped, click **Next** to continue.</span></span>  
  
 <span data-ttu-id="32a53-115">安装程序将信息记录在日志文件中。</span><span class="sxs-lookup"><span data-stu-id="32a53-115">Setup logs the information in the log files.</span></span> <span data-ttu-id="32a53-116">有关如何查看日志文件的详细信息，请参阅 [查看和读取 SQL Server 安装日志文件](../../database-engine/install-windows/view-and-read-sql-server-setup-log-files.md) 和 [如何读取 SQL Server 安装日志文件](https://go.microsoft.com/fwlink/?LinkID=134490)。</span><span class="sxs-lookup"><span data-stu-id="32a53-116">For more information about how to view the log files, see [View and Read SQL Server Setup Log Files](../../database-engine/install-windows/view-and-read-sql-server-setup-log-files.md) and [How to: Read a SQL Server Setup Log File](https://go.microsoft.com/fwlink/?LinkID=134490).</span></span>  
  
 <span data-ttu-id="32a53-117">日志文件中包括下列信息：</span><span class="sxs-lookup"><span data-stu-id="32a53-117">The following information is included in the log file:</span></span>  
  
-   <span data-ttu-id="32a53-118">进程的名称</span><span class="sxs-lookup"><span data-stu-id="32a53-118">Name of the process</span></span>  
  
-   <span data-ttu-id="32a53-119">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 功能的名称</span><span class="sxs-lookup"><span data-stu-id="32a53-119">Name of the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] feature</span></span>  
  
-   <span data-ttu-id="32a53-120">进程类型</span><span class="sxs-lookup"><span data-stu-id="32a53-120">Process type</span></span>  
  
-   <span data-ttu-id="32a53-121">运行进程的帐户</span><span class="sxs-lookup"><span data-stu-id="32a53-121">Account under which the process is running</span></span>  
  
-   <span data-ttu-id="32a53-122">进程 ID</span><span class="sxs-lookup"><span data-stu-id="32a53-122">Process ID</span></span>  
  
-   <span data-ttu-id="32a53-123">锁定的文件的名称</span><span class="sxs-lookup"><span data-stu-id="32a53-123">Name of the file that is locked</span></span>  
  
## <a name="ui-element-list"></a><span data-ttu-id="32a53-124">UI 元素列表</span><span class="sxs-lookup"><span data-stu-id="32a53-124">UI element list</span></span>  
  
|<span data-ttu-id="32a53-125">名称</span><span class="sxs-lookup"><span data-stu-id="32a53-125">Name</span></span>|<span data-ttu-id="32a53-126">说明</span><span class="sxs-lookup"><span data-stu-id="32a53-126">Description</span></span>|  
|----------|-----------------|  
|<span data-ttu-id="32a53-127">过程</span><span class="sxs-lookup"><span data-stu-id="32a53-127">Process</span></span>|<span data-ttu-id="32a53-128">显示以下进程的全名，该进程正在使用要更新的文件。</span><span class="sxs-lookup"><span data-stu-id="32a53-128">Displays the full name of the process that is using the files to be updated.</span></span>|  
|<span data-ttu-id="32a53-129">类型</span><span class="sxs-lookup"><span data-stu-id="32a53-129">Type</span></span>|<span data-ttu-id="32a53-130">显示进程的类型。</span><span class="sxs-lookup"><span data-stu-id="32a53-130">Displays the type of process.</span></span>|  
|<span data-ttu-id="32a53-131">帐户</span><span class="sxs-lookup"><span data-stu-id="32a53-131">Account</span></span>|<span data-ttu-id="32a53-132">显示运行进程的帐户。</span><span class="sxs-lookup"><span data-stu-id="32a53-132">Displays the account under which the process is running.</span></span>|  
|<span data-ttu-id="32a53-133">进程 ID</span><span class="sxs-lookup"><span data-stu-id="32a53-133">Process ID</span></span>|<span data-ttu-id="32a53-134">显示进程 ID。</span><span class="sxs-lookup"><span data-stu-id="32a53-134">Displays the process ID.</span></span>|  
  
  
