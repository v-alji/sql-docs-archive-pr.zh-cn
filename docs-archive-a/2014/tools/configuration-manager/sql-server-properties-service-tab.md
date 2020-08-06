---
title: SQL Server 属性（“服务”选项卡）| Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
ms.assetid: e4ae0c6b-6fd8-4325-b54e-1758fc659958
author: stevestein
ms.author: sstein
ms.openlocfilehash: 5822a02d5631e0d0e9318b20a1dcee87b8a4ded1
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87693156"
---
# <a name="sql-server-properties-service-tab"></a><span data-ttu-id="606a3-102">SQL Server 属性（“服务”选项卡）</span><span class="sxs-lookup"><span data-stu-id="606a3-102">SQL Server Properties (Service Tab)</span></span>
  <span data-ttu-id="606a3-103">使用“MSSQLSERVER 属性”对话框上的“服务”选项卡查看或指定下列选项。</span><span class="sxs-lookup"><span data-stu-id="606a3-103">Use the **Service**tab on the **MSSQLSERVER Properties** dialog box to view or specify the following options.</span></span>  
  
## <a name="options"></a><span data-ttu-id="606a3-104">选项</span><span class="sxs-lookup"><span data-stu-id="606a3-104">Options</span></span>  
 <span data-ttu-id="606a3-105">**二进制路径**</span><span class="sxs-lookup"><span data-stu-id="606a3-105">**Binary Path**</span></span>  
 <span data-ttu-id="606a3-106">列出此服务所使用的程序文件的位置。</span><span class="sxs-lookup"><span data-stu-id="606a3-106">Lists the location of the program files used by this service.</span></span>  
  
 <span data-ttu-id="606a3-107">**错误控制**</span><span class="sxs-lookup"><span data-stu-id="606a3-107">**Error Control**</span></span>  
 <span data-ttu-id="606a3-108">1 指示 `SERVICE_ERROR_NORMAL`。</span><span class="sxs-lookup"><span data-stu-id="606a3-108">1 indicates `SERVICE_ERROR_NORMAL`.</span></span> <span data-ttu-id="606a3-109">如果在计算机启动过程中无法启动该服务，则启动程序会记录该错误并显示一个弹出消息框，但仍会继续执行启动操作。</span><span class="sxs-lookup"><span data-stu-id="606a3-109">If the service fails to start during computer start up, the startup program logs the error and displays a pop-up message box but continues the startup operation.</span></span> <span data-ttu-id="606a3-110">此值不能更改。</span><span class="sxs-lookup"><span data-stu-id="606a3-110">This value cannot be changed.</span></span>  
  
 <span data-ttu-id="606a3-111">**退出代码**</span><span class="sxs-lookup"><span data-stu-id="606a3-111">**Exit Code**</span></span>  
 <span data-ttu-id="606a3-112">当发生错误时，错误号显示在此信息框中。</span><span class="sxs-lookup"><span data-stu-id="606a3-112">When an error occurs, the error number appears in this box.</span></span> <span data-ttu-id="606a3-113">您可以通过在 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 知识库中搜索该号码获取相关信息来排除故障，或将该错误号提供给技术支持人员以获得帮助。</span><span class="sxs-lookup"><span data-stu-id="606a3-113">Use this number to troubleshoot failures by searching for the number in the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Knowledge Base or provide the number to your technical support staff.</span></span>  
  
 <span data-ttu-id="606a3-114">**Host Name**</span><span class="sxs-lookup"><span data-stu-id="606a3-114">**Host Name**</span></span>  
 <span data-ttu-id="606a3-115">显示运行 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 服务的计算机或群集的名称。</span><span class="sxs-lookup"><span data-stu-id="606a3-115">Displays the name of the computer or cluster running the [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] service.</span></span>  
  
 <span data-ttu-id="606a3-116">**名称**</span><span class="sxs-lookup"><span data-stu-id="606a3-116">**Name**</span></span>  
 <span data-ttu-id="606a3-117">指示该服务的显示名称。</span><span class="sxs-lookup"><span data-stu-id="606a3-117">Indicates the display name of the service.</span></span>  
  
 <span data-ttu-id="606a3-118">**进程 ID**</span><span class="sxs-lookup"><span data-stu-id="606a3-118">**Process ID**</span></span>  
 <span data-ttu-id="606a3-119">显示 Windows 进程 ID。</span><span class="sxs-lookup"><span data-stu-id="606a3-119">Displays the Windows process ID.</span></span>  
  
 <span data-ttu-id="606a3-120">**服务类型**</span><span class="sxs-lookup"><span data-stu-id="606a3-120">**Service Type**</span></span>  
 <span data-ttu-id="606a3-121">显示用于调用进程的服务的类型。</span><span class="sxs-lookup"><span data-stu-id="606a3-121">Displays the type of service provided to calling processes.</span></span> [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="606a3-122">安装有多种服务。</span><span class="sxs-lookup"><span data-stu-id="606a3-122">installs several services.</span></span>  
  
 <span data-ttu-id="606a3-123">**启动模式**</span><span class="sxs-lookup"><span data-stu-id="606a3-123">**Start Mode**</span></span>  
 <span data-ttu-id="606a3-124">对此服务设置以下选项：</span><span class="sxs-lookup"><span data-stu-id="606a3-124">Set this service to the following choices:</span></span>  
  
-   <span data-ttu-id="606a3-125">手动：计算机启动时，此服务不自动启动。</span><span class="sxs-lookup"><span data-stu-id="606a3-125">Manual: This service does not automatically start when the computer starts.</span></span> <span data-ttu-id="606a3-126">您必须使用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 配置管理器或其他工具来启动该服务。</span><span class="sxs-lookup"><span data-stu-id="606a3-126">You must start the service using [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Configuration Manager, or some other tool.</span></span>  
  
-   <span data-ttu-id="606a3-127">自动：计算机启动时，此服务将尝试启动。</span><span class="sxs-lookup"><span data-stu-id="606a3-127">Automatic: This service attempts to start when this computer starts.</span></span>  
  
-   <span data-ttu-id="606a3-128">已禁用：此服务无法启动。</span><span class="sxs-lookup"><span data-stu-id="606a3-128">Disabled: This service cannot be started.</span></span>  
  
 <span data-ttu-id="606a3-129">**State**</span><span class="sxs-lookup"><span data-stu-id="606a3-129">**State**</span></span>  
 <span data-ttu-id="606a3-130">指示此服务是正在运行、已停止还是已禁用。</span><span class="sxs-lookup"><span data-stu-id="606a3-130">Indicates whether this service is running, stopped, or disabled.</span></span> <span data-ttu-id="606a3-131">“...  ”指明状态更改是挂起的。</span><span class="sxs-lookup"><span data-stu-id="606a3-131">"**...**" indicates a state change is pending.</span></span>  
  
  
