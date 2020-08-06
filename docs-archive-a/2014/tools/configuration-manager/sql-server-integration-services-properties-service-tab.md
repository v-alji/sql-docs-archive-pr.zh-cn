---
title: SQL Server Integration Services 属性（“服务”选项卡）| Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
ms.assetid: 37f0acd9-c96f-48fd-9b53-2ca0097af242
author: stevestein
ms.author: sstein
ms.openlocfilehash: a752bdeab3c99ac97445e3281d3165a2d8f79866
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87590455"
---
# <a name="sql-server-integration-services-properties-service-tab"></a><span data-ttu-id="118b9-102">SQL Server Integration Services 属性（“服务”选项卡）</span><span class="sxs-lookup"><span data-stu-id="118b9-102">SQL Server Integration Services Properties (Service Tab)</span></span>
  <span data-ttu-id="118b9-103">使用 **“属性”** 对话框中的“服务”选项卡可以查看或指定下列选项[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]  。</span><span class="sxs-lookup"><span data-stu-id="118b9-103">Use the **Service**tab on the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] **Properties** dialog box to view or specify the following options.</span></span>  
  
## <a name="options"></a><span data-ttu-id="118b9-104">选项</span><span class="sxs-lookup"><span data-stu-id="118b9-104">Options</span></span>  
 <span data-ttu-id="118b9-105">**二进制路径**</span><span class="sxs-lookup"><span data-stu-id="118b9-105">**Binary Path**</span></span>  
 <span data-ttu-id="118b9-106">显示此服务所使用的程序文件的位置。</span><span class="sxs-lookup"><span data-stu-id="118b9-106">Displays the location of the program files used by this service.</span></span>  
  
 <span data-ttu-id="118b9-107">**错误控制**</span><span class="sxs-lookup"><span data-stu-id="118b9-107">**Error Control**</span></span>  
 <span data-ttu-id="118b9-108">1 指示 `SERVICE_ERROR_NORMAL`。</span><span class="sxs-lookup"><span data-stu-id="118b9-108">1 indicates `SERVICE_ERROR_NORMAL`.</span></span> <span data-ttu-id="118b9-109">如果在计算机启动过程中无法启动该服务，则启动程序会记录该错误并显示一个弹出消息框，但仍会继续执行启动操作。</span><span class="sxs-lookup"><span data-stu-id="118b9-109">If the service fails to start during computer start up, the startup program logs the error and displays a pop-up message box but continues the startup operation.</span></span> <span data-ttu-id="118b9-110">此值不能更改。</span><span class="sxs-lookup"><span data-stu-id="118b9-110">This value cannot be changed.</span></span>  
  
 <span data-ttu-id="118b9-111">**退出代码**</span><span class="sxs-lookup"><span data-stu-id="118b9-111">**Exit Code**</span></span>  
 <span data-ttu-id="118b9-112">[!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows 错误代码，定义了在启动或停止服务时遇到的任何问题。</span><span class="sxs-lookup"><span data-stu-id="118b9-112">The [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows error code defining any problems encountered in starting or stopping the service.</span></span> <span data-ttu-id="118b9-113">如果错误是此类表示的服务所特有的，并且 **ServiceSpecificExitCode** 属性中包含该错误的相关信息，则此属性将设置为 **ERROR_SERVICE_SPECIFIC_ERROR** (1066)。</span><span class="sxs-lookup"><span data-stu-id="118b9-113">This property is set to **ERROR_SERVICE_SPECIFIC_ERROR** (1066) when the error is unique to the service represented by this class, and information about the error is available in the **ServiceSpecificExitCode** property.</span></span> <span data-ttu-id="118b9-114">当服务运行时，会将此值设置为 NO_ERROR (0)；而当服务正常终止时，会再次对它进行设置。</span><span class="sxs-lookup"><span data-stu-id="118b9-114">The service sets this value to NO_ERROR (0) when running, and again upon normal termination.</span></span>  
  
 <span data-ttu-id="118b9-115">**Host Name**</span><span class="sxs-lookup"><span data-stu-id="118b9-115">**Host Name**</span></span>  
 <span data-ttu-id="118b9-116">显示运行 [!INCLUDE[ssIS](../../includes/ssis-md.md)] 服务的计算机或群集的名称。</span><span class="sxs-lookup"><span data-stu-id="118b9-116">Displays the name of the computer or cluster running the [!INCLUDE[ssIS](../../includes/ssis-md.md)] service.</span></span>  
  
 <span data-ttu-id="118b9-117">**名称**</span><span class="sxs-lookup"><span data-stu-id="118b9-117">**Name**</span></span>  
 <span data-ttu-id="118b9-118">指示该服务的显示名称。</span><span class="sxs-lookup"><span data-stu-id="118b9-118">Indicates the display name of the service.</span></span>  
  
 <span data-ttu-id="118b9-119">**进程 ID**</span><span class="sxs-lookup"><span data-stu-id="118b9-119">**Process ID**</span></span>  
 <span data-ttu-id="118b9-120">显示 Windows 进程 ID。</span><span class="sxs-lookup"><span data-stu-id="118b9-120">Displays the Windows process ID.</span></span>  
  
 <span data-ttu-id="118b9-121">**SQL 服务类型**</span><span class="sxs-lookup"><span data-stu-id="118b9-121">**SQL Service Type**</span></span>  
 <span data-ttu-id="118b9-122">显示用于调用进程的服务的类型。</span><span class="sxs-lookup"><span data-stu-id="118b9-122">Displays the type of service provided to calling processes.</span></span> [!INCLUDE[msCoName](../../includes/msconame-md.md)] <span data-ttu-id="118b9-123">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 安装有多种服务。</span><span class="sxs-lookup"><span data-stu-id="118b9-123">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] installs several services.</span></span>  
  
 <span data-ttu-id="118b9-124">**启动模式**</span><span class="sxs-lookup"><span data-stu-id="118b9-124">**Start Mode**</span></span>  
 <span data-ttu-id="118b9-125">对此服务设置以下选项：</span><span class="sxs-lookup"><span data-stu-id="118b9-125">Set this service to the following choices:</span></span>  
  
-   <span data-ttu-id="118b9-126">手动：计算机启动时，此服务不自动启动。</span><span class="sxs-lookup"><span data-stu-id="118b9-126">Manual: This service does not automatically start when the computer starts.</span></span> <span data-ttu-id="118b9-127">您必须使用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 配置管理器或其他工具来启动该服务。</span><span class="sxs-lookup"><span data-stu-id="118b9-127">You must start the service using [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Configuration Manager, or some other tool.</span></span>  
  
-   <span data-ttu-id="118b9-128">自动：计算机启动时，此服务将尝试启动。</span><span class="sxs-lookup"><span data-stu-id="118b9-128">Automatic: This service attempts to start when this computer starts.</span></span>  
  
-   <span data-ttu-id="118b9-129">已禁用：此服务无法启动。</span><span class="sxs-lookup"><span data-stu-id="118b9-129">Disabled: This service cannot be started.</span></span>  
  
 <span data-ttu-id="118b9-130">**State**</span><span class="sxs-lookup"><span data-stu-id="118b9-130">**State**</span></span>  
 <span data-ttu-id="118b9-131">指示此服务是正在运行、已停止还是已禁用。</span><span class="sxs-lookup"><span data-stu-id="118b9-131">Indicates whether this service is running, stopped, or disabled.</span></span> <span data-ttu-id="118b9-132">“...  ”指明状态更改是挂起的。</span><span class="sxs-lookup"><span data-stu-id="118b9-132">"**...**" indicates a state change is pending.</span></span>  
  
  
