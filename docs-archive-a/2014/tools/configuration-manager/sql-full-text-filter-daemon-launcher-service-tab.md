---
title: SQL 全文筛选器守护程序启动器（“服务”选项卡）| Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
ms.assetid: 6aad7ebe-c4be-4d37-8536-61502f51faa2
author: stevestein
ms.author: sstein
ms.openlocfilehash: 8f0d9c76d7d92947dd17fe2ed6e912e3d6baa6bd
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87590460"
---
# <a name="sql-full-text-filter-daemon-launcher-service-tab"></a><span data-ttu-id="da4ee-102">SQL 全文筛选器后台程序启动器（“服务”选项卡）</span><span class="sxs-lookup"><span data-stu-id="da4ee-102">SQL Full-text Filter Daemon Launcher (Service Tab)</span></span>
  <span data-ttu-id="da4ee-103">从 [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]开始， [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 全文将使用 SQL 全文筛选器后台程序启动器 (FDHOST Launcher) 服务。</span><span class="sxs-lookup"><span data-stu-id="da4ee-103">Beginning in [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)], the SQL Full-text Filter Daemon Launcher (FDHOST Launcher) service is used by [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] full-text.</span></span> <span data-ttu-id="da4ee-104">如果使用全文搜索，则必须运行此服务。</span><span class="sxs-lookup"><span data-stu-id="da4ee-104">This service must be running if you use full-text search.</span></span> <span data-ttu-id="da4ee-105">有关筛选器后台程序主机进程的信息，请参阅 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 联机丛书中的“全文搜索体系结构”。</span><span class="sxs-lookup"><span data-stu-id="da4ee-105">For information about the filter daemon host processes, see "Full-Text Search Architecture" in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Books Online.</span></span>  
  
 <span data-ttu-id="da4ee-106">使用“SQL 全文筛选器后台程序启动器属性”的“属性”对话框上的“服务”选项卡，可以查看或指定以下选项。</span><span class="sxs-lookup"><span data-stu-id="da4ee-106">Use the **Service**tab on the **SQL Full-text Filter Daemon LauncherProperties** dialog box to view or specify the following options.</span></span>  
  
## <a name="options"></a><span data-ttu-id="da4ee-107">选项</span><span class="sxs-lookup"><span data-stu-id="da4ee-107">Options</span></span>  
 <span data-ttu-id="da4ee-108">**二进制路径**</span><span class="sxs-lookup"><span data-stu-id="da4ee-108">**Binary Path**</span></span>  
 <span data-ttu-id="da4ee-109">列出此服务所使用的程序文件的位置。</span><span class="sxs-lookup"><span data-stu-id="da4ee-109">Lists the location of the program files used by this service.</span></span>  
  
 <span data-ttu-id="da4ee-110">**错误控制**</span><span class="sxs-lookup"><span data-stu-id="da4ee-110">**Error Control**</span></span>  
 <span data-ttu-id="da4ee-111">1 指示 `SERVICE_ERROR_NORMAL`。</span><span class="sxs-lookup"><span data-stu-id="da4ee-111">1 indicates `SERVICE_ERROR_NORMAL`.</span></span> <span data-ttu-id="da4ee-112">如果在计算机启动过程中无法启动该服务，则启动程序会记录该错误并显示一个弹出消息框，但仍会继续执行启动操作。</span><span class="sxs-lookup"><span data-stu-id="da4ee-112">If the service fails to start during computer start up, the startup program logs the error and displays a pop-up message box but continues the startup operation.</span></span> <span data-ttu-id="da4ee-113">此值不能更改。</span><span class="sxs-lookup"><span data-stu-id="da4ee-113">This value cannot be changed.</span></span>  
  
 <span data-ttu-id="da4ee-114">**退出代码**</span><span class="sxs-lookup"><span data-stu-id="da4ee-114">**Exit Code**</span></span>  
 <span data-ttu-id="da4ee-115">当发生错误时，错误号显示在此信息框中。</span><span class="sxs-lookup"><span data-stu-id="da4ee-115">When an error occurs, the error number appears in this box.</span></span> <span data-ttu-id="da4ee-116">您可以通过在 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 知识库中搜索该号码获取相关信息来排除故障，或将该错误号提供给技术支持人员以获得帮助。</span><span class="sxs-lookup"><span data-stu-id="da4ee-116">Use this number to troubleshoot failures by searching for the number in the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Knowledge Base or provide the number to your technical support staff.</span></span>  
  
 <span data-ttu-id="da4ee-117">**Host Name**</span><span class="sxs-lookup"><span data-stu-id="da4ee-117">**Host Name**</span></span>  
 <span data-ttu-id="da4ee-118">显示运行 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 服务的计算机或群集的名称。</span><span class="sxs-lookup"><span data-stu-id="da4ee-118">Displays the name of the computer or cluster running the [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] service.</span></span>  
  
 <span data-ttu-id="da4ee-119">**名称**</span><span class="sxs-lookup"><span data-stu-id="da4ee-119">**Name**</span></span>  
 <span data-ttu-id="da4ee-120">指示该服务的显示名称。</span><span class="sxs-lookup"><span data-stu-id="da4ee-120">Indicates the display name of the service.</span></span>  
  
 <span data-ttu-id="da4ee-121">**进程 ID**</span><span class="sxs-lookup"><span data-stu-id="da4ee-121">**Process ID**</span></span>  
 <span data-ttu-id="da4ee-122">显示 Windows 进程 ID。</span><span class="sxs-lookup"><span data-stu-id="da4ee-122">Displays the Windows process ID.</span></span>  
  
 <span data-ttu-id="da4ee-123">**SQL 服务类型**</span><span class="sxs-lookup"><span data-stu-id="da4ee-123">**SQL Service Type**</span></span>  
 <span data-ttu-id="da4ee-124">显示用于调用进程的服务的类型。</span><span class="sxs-lookup"><span data-stu-id="da4ee-124">Displays the type of service provided to calling processes.</span></span> [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="da4ee-125">安装有多种服务。</span><span class="sxs-lookup"><span data-stu-id="da4ee-125">installs several services.</span></span>  
  
 <span data-ttu-id="da4ee-126">**启动模式**</span><span class="sxs-lookup"><span data-stu-id="da4ee-126">**Start Mode**</span></span>  
 <span data-ttu-id="da4ee-127">对此服务设置以下选项：</span><span class="sxs-lookup"><span data-stu-id="da4ee-127">Set this service to the following choices:</span></span>  
  
-   <span data-ttu-id="da4ee-128">手动：计算机启动时，此服务不自动启动。</span><span class="sxs-lookup"><span data-stu-id="da4ee-128">Manual: This service does not automatically start when the computer starts.</span></span> <span data-ttu-id="da4ee-129">您必须使用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 配置管理器或其他工具来启动该服务。</span><span class="sxs-lookup"><span data-stu-id="da4ee-129">You must start the service using [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Configuration Manager, or some other tool.</span></span>  
  
-   <span data-ttu-id="da4ee-130">自动：计算机启动时，此服务将尝试启动。</span><span class="sxs-lookup"><span data-stu-id="da4ee-130">Automatic: This service attempts to start when this computer starts.</span></span>  
  
-   <span data-ttu-id="da4ee-131">已禁用：此服务无法启动。</span><span class="sxs-lookup"><span data-stu-id="da4ee-131">Disabled: This service cannot be started.</span></span>  
  
 <span data-ttu-id="da4ee-132">**State**</span><span class="sxs-lookup"><span data-stu-id="da4ee-132">**State**</span></span>  
 <span data-ttu-id="da4ee-133">指示此服务是正在运行、已停止还是已禁用。</span><span class="sxs-lookup"><span data-stu-id="da4ee-133">Indicates whether this service is running, stopped, or disabled.</span></span> <span data-ttu-id="da4ee-134">“...  ”指明状态更改是挂起的。</span><span class="sxs-lookup"><span data-stu-id="da4ee-134">"**...**" indicates a state change is pending.</span></span>  
  
  
