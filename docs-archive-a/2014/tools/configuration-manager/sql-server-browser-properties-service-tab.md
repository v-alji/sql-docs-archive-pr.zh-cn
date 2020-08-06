---
title: SQL Server Browser 属性（“服务”选项卡）| Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
ms.assetid: 98ace9b0-72d5-4b72-9b7b-11fbc490981a
author: stevestein
ms.author: sstein
ms.openlocfilehash: 200e45648b94e26c5e808e9a817cfe01866e6a65
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87577989"
---
# <a name="sql-server-browser-properties-service-tab"></a><span data-ttu-id="321a6-102">SQL Server 浏览器属性（“服务”选项卡）</span><span class="sxs-lookup"><span data-stu-id="321a6-102">SQL Server Browser Properties (Service Tab)</span></span>
  <span data-ttu-id="321a6-103">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 浏览器程序以服务的形式在服务器上运行。</span><span class="sxs-lookup"><span data-stu-id="321a6-103">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Browser program runs as a service on the server.</span></span> [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="321a6-104">浏览器侦听对 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 资源的传入请求，并提供计算机上安装的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 实例的相关信息。</span><span class="sxs-lookup"><span data-stu-id="321a6-104">Browser listens for incoming requests for [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] resources and provides information about [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instances installed on the computer.</span></span>  
  
 <span data-ttu-id="321a6-105">使用 **“SQL Server 浏览器属性”** 对话框中的 **“服务”** 选项卡可以查看下列选项。</span><span class="sxs-lookup"><span data-stu-id="321a6-105">Use the **Service** tab on the **SQL Server Browser Properties** dialog box to view the following options.</span></span> <span data-ttu-id="321a6-106">除了 **“启动模式”** 以外，其他所有属性都是只读的。</span><span class="sxs-lookup"><span data-stu-id="321a6-106">All properties except **Start Mode** are read-only.</span></span>  
  
## <a name="options"></a><span data-ttu-id="321a6-107">选项</span><span class="sxs-lookup"><span data-stu-id="321a6-107">Options</span></span>  
 <span data-ttu-id="321a6-108">**二进制路径**</span><span class="sxs-lookup"><span data-stu-id="321a6-108">**Binary Path**</span></span>  
 <span data-ttu-id="321a6-109">显示此服务所使用的程序文件的位置。</span><span class="sxs-lookup"><span data-stu-id="321a6-109">Displays the location of the program files used by this service.</span></span>  
  
 <span data-ttu-id="321a6-110">**错误控制**</span><span class="sxs-lookup"><span data-stu-id="321a6-110">**Error Control**</span></span>  
 <span data-ttu-id="321a6-111">1 指示 `SERVICE_ERROR_NORMAL`。</span><span class="sxs-lookup"><span data-stu-id="321a6-111">1 indicates `SERVICE_ERROR_NORMAL`.</span></span> <span data-ttu-id="321a6-112">如果在计算机启动过程中无法启动该服务，则启动程序会记录该错误并显示一个弹出消息框，但仍会继续执行启动操作。</span><span class="sxs-lookup"><span data-stu-id="321a6-112">If the service fails to start during computer start up, the startup program logs the error and displays a pop-up message box but continues the startup operation.</span></span> <span data-ttu-id="321a6-113">此值不能更改。</span><span class="sxs-lookup"><span data-stu-id="321a6-113">This value cannot be changed.</span></span>  
  
 <span data-ttu-id="321a6-114">**退出代码**</span><span class="sxs-lookup"><span data-stu-id="321a6-114">**Exit Code**</span></span>  
 <span data-ttu-id="321a6-115">当发生错误时，错误号显示在此信息框中。</span><span class="sxs-lookup"><span data-stu-id="321a6-115">When an error occurs, the error number appears in this box.</span></span> <span data-ttu-id="321a6-116">您可以通过在 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 知识库中搜索该号码获取相关信息来排除故障，或将该错误号提供给技术支持人员以获得帮助。</span><span class="sxs-lookup"><span data-stu-id="321a6-116">Use this number to troubleshoot failures by searching for the number in the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Knowledge Base or provide the number to your technical support staff.</span></span>  
  
 <span data-ttu-id="321a6-117">**Host Name**</span><span class="sxs-lookup"><span data-stu-id="321a6-117">**Host Name**</span></span>  
 <span data-ttu-id="321a6-118">显示运行 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Browser 服务的计算机或群集的名称。</span><span class="sxs-lookup"><span data-stu-id="321a6-118">Displays the name of the computer or cluster running the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Browser service.</span></span>  
  
 <span data-ttu-id="321a6-119">**名称**</span><span class="sxs-lookup"><span data-stu-id="321a6-119">**Name**</span></span>  
 <span data-ttu-id="321a6-120">指示该服务的显示名称。</span><span class="sxs-lookup"><span data-stu-id="321a6-120">Indicates the display name of the service.</span></span>  
  
 <span data-ttu-id="321a6-121">**进程 ID**</span><span class="sxs-lookup"><span data-stu-id="321a6-121">**Process ID**</span></span>  
 <span data-ttu-id="321a6-122">显示 Windows 进程 ID。</span><span class="sxs-lookup"><span data-stu-id="321a6-122">Displays the Windows process ID.</span></span>  
  
 <span data-ttu-id="321a6-123">**服务类型**</span><span class="sxs-lookup"><span data-stu-id="321a6-123">**Service Type**</span></span>  
 <span data-ttu-id="321a6-124">显示用于调用进程的服务的类型。</span><span class="sxs-lookup"><span data-stu-id="321a6-124">Displays the type of service provided to calling processes.</span></span> [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="321a6-125">安装有多种服务。</span><span class="sxs-lookup"><span data-stu-id="321a6-125">installs several services.</span></span>  
  
 <span data-ttu-id="321a6-126">**启动模式**</span><span class="sxs-lookup"><span data-stu-id="321a6-126">**Start Mode**</span></span>  
 <span data-ttu-id="321a6-127">对此服务设置以下选项：</span><span class="sxs-lookup"><span data-stu-id="321a6-127">Set this service to the following choices:</span></span>  
  
-   <span data-ttu-id="321a6-128">手动：计算机启动时，此服务不自动启动。</span><span class="sxs-lookup"><span data-stu-id="321a6-128">Manual: This service does not automatically start when the computer starts.</span></span> <span data-ttu-id="321a6-129">您必须使用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 配置管理器或其他工具来启动该服务。</span><span class="sxs-lookup"><span data-stu-id="321a6-129">You must start the service using [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Configuration Manager, or some other tool.</span></span>  
  
-   <span data-ttu-id="321a6-130">自动：计算机启动时，此服务将尝试启动。</span><span class="sxs-lookup"><span data-stu-id="321a6-130">Automatic: This service attempts to start when this computer starts.</span></span>  
  
-   <span data-ttu-id="321a6-131">已禁用：此服务无法启动。</span><span class="sxs-lookup"><span data-stu-id="321a6-131">Disabled: This service cannot be started.</span></span>  
  
 <span data-ttu-id="321a6-132">**State**</span><span class="sxs-lookup"><span data-stu-id="321a6-132">**State**</span></span>  
 <span data-ttu-id="321a6-133">指示此服务是正在运行、已停止还是已禁用。</span><span class="sxs-lookup"><span data-stu-id="321a6-133">Indicates whether this service is running, stopped, or disabled.</span></span> <span data-ttu-id="321a6-134">“...  ”指明状态更改是挂起的。</span><span class="sxs-lookup"><span data-stu-id="321a6-134">"**...**" indicates a state change is pending.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="321a6-135">另请参阅</span><span class="sxs-lookup"><span data-stu-id="321a6-135">See Also</span></span>  
 [<span data-ttu-id="321a6-136">SQL Server Browser 服务</span><span class="sxs-lookup"><span data-stu-id="321a6-136">SQL Server Browser Service</span></span>](../../../2014/tools/configuration-manager/sql-server-browser-service.md)  
  
  
