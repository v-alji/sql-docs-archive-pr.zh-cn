---
title: Report Server 属性（“服务”选项卡）| Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
ms.assetid: 2a2e1dbf-02b9-4893-aaf0-c0e4a2c9b4f9
author: stevestein
ms.author: sstein
ms.openlocfilehash: a8d223234e5f53eb087650d0634eb09b520cd21e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87588165"
---
# <a name="report-server-properties-service-tab"></a><span data-ttu-id="c7402-102">报表服务器属性（“服务”选项卡）</span><span class="sxs-lookup"><span data-stu-id="c7402-102">Report Server Properties (Service Tab)</span></span>
  <span data-ttu-id="c7402-103">此服务为 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 报表服务器服务。</span><span class="sxs-lookup"><span data-stu-id="c7402-103">This service is the [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Report Server service.</span></span> <span data-ttu-id="c7402-104">如果属性值呈浅灰色，则不能使用此应用程序更改。</span><span class="sxs-lookup"><span data-stu-id="c7402-104">The property values in light gray cannot be changed by using this application.</span></span>  
  
## <a name="options"></a><span data-ttu-id="c7402-105">选项</span><span class="sxs-lookup"><span data-stu-id="c7402-105">Options</span></span>  
 <span data-ttu-id="c7402-106">**二进制路径**</span><span class="sxs-lookup"><span data-stu-id="c7402-106">**Binary Path**</span></span>  
 <span data-ttu-id="c7402-107">显示此服务所使用的程序文件的位置。</span><span class="sxs-lookup"><span data-stu-id="c7402-107">Displays the location of the program files used by this service.</span></span>  
  
 <span data-ttu-id="c7402-108">**错误控制**</span><span class="sxs-lookup"><span data-stu-id="c7402-108">**Error Control**</span></span>  
 <span data-ttu-id="c7402-109">1 指示“SERVICE_ERROR_NORMAL”。</span><span class="sxs-lookup"><span data-stu-id="c7402-109">1 indicates "SERVICE_ERROR_NORMAL".</span></span> <span data-ttu-id="c7402-110">如果在计算机启动过程中无法启动该服务，则启动程序会记录该错误并显示一个弹出消息框，但仍会继续执行启动操作。</span><span class="sxs-lookup"><span data-stu-id="c7402-110">If the service fails to start during computer start up, the startup program logs the error and displays a pop-up message box but continues the startup operation.</span></span> <span data-ttu-id="c7402-111">此值不能更改。</span><span class="sxs-lookup"><span data-stu-id="c7402-111">This value cannot be changed.</span></span>  
  
 <span data-ttu-id="c7402-112">**退出代码**</span><span class="sxs-lookup"><span data-stu-id="c7402-112">**Exit Code**</span></span>  
 <span data-ttu-id="c7402-113">当发生错误时，错误号显示在此信息框中。</span><span class="sxs-lookup"><span data-stu-id="c7402-113">When an error occurs, the error number appears in this box.</span></span> <span data-ttu-id="c7402-114">您可以通过在 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 知识库中搜索该号码获取相关信息来排除故障，或将该错误号提供给技术支持人员以获得帮助。</span><span class="sxs-lookup"><span data-stu-id="c7402-114">Use this number to troubleshoot failures by searching for the number in the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Knowledge Base or provide the number to your technical support staff.</span></span>  
  
 <span data-ttu-id="c7402-115">**Host Name**</span><span class="sxs-lookup"><span data-stu-id="c7402-115">**Host Name**</span></span>  
 <span data-ttu-id="c7402-116">显示运行全文搜索的计算机或群集的名称。</span><span class="sxs-lookup"><span data-stu-id="c7402-116">Displays the name of the computer or cluster running the full text search.</span></span>  
  
 <span data-ttu-id="c7402-117">**名称**</span><span class="sxs-lookup"><span data-stu-id="c7402-117">**Name**</span></span>  
 <span data-ttu-id="c7402-118">指示该服务的显示名称。</span><span class="sxs-lookup"><span data-stu-id="c7402-118">Indicates the display name of the service.</span></span>  
  
 <span data-ttu-id="c7402-119">**进程 ID**</span><span class="sxs-lookup"><span data-stu-id="c7402-119">**Process ID**</span></span>  
 <span data-ttu-id="c7402-120">显示 [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows 进程 ID。</span><span class="sxs-lookup"><span data-stu-id="c7402-120">Displays the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows process ID.</span></span>  
  
 <span data-ttu-id="c7402-121">**SQL 服务类型**</span><span class="sxs-lookup"><span data-stu-id="c7402-121">**SQL Service Type**</span></span>  
 <span data-ttu-id="c7402-122">用于调用进程的服务的类型。</span><span class="sxs-lookup"><span data-stu-id="c7402-122">Type of service provided to calling processes.</span></span> [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="c7402-123">安装有多种服务。</span><span class="sxs-lookup"><span data-stu-id="c7402-123">installs several services.</span></span>  
  
 <span data-ttu-id="c7402-124">**启动模式**</span><span class="sxs-lookup"><span data-stu-id="c7402-124">**Start Mode**</span></span>  
 <span data-ttu-id="c7402-125">对此服务设置以下选项：</span><span class="sxs-lookup"><span data-stu-id="c7402-125">Set this service to the following choices:</span></span>  
  
-   <span data-ttu-id="c7402-126">手动：计算机启动时，此服务不自动启动。</span><span class="sxs-lookup"><span data-stu-id="c7402-126">Manual: This service does not automatically start when the computer starts.</span></span> <span data-ttu-id="c7402-127">您必须使用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 配置管理器或其他工具来启动该服务。</span><span class="sxs-lookup"><span data-stu-id="c7402-127">You must start the service using [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Configuration Manager, or some other tool.</span></span>  
  
-   <span data-ttu-id="c7402-128">自动：计算机启动时，此服务将尝试启动。</span><span class="sxs-lookup"><span data-stu-id="c7402-128">Automatic: This service attempts to start when this computer starts.</span></span>  
  
-   <span data-ttu-id="c7402-129">已禁用：此服务无法启动。</span><span class="sxs-lookup"><span data-stu-id="c7402-129">Disabled: This service cannot be started.</span></span>  
  
 <span data-ttu-id="c7402-130">**State**</span><span class="sxs-lookup"><span data-stu-id="c7402-130">**State**</span></span>  
 <span data-ttu-id="c7402-131">指示此服务是正在运行、已停止还是已禁用。</span><span class="sxs-lookup"><span data-stu-id="c7402-131">Indicates whether this service is running, stopped, or disabled.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c7402-132">另请参阅</span><span class="sxs-lookup"><span data-stu-id="c7402-132">See Also</span></span>  
 [<span data-ttu-id="c7402-133">SQL Server 服务</span><span class="sxs-lookup"><span data-stu-id="c7402-133">SQL Server Services</span></span>](../../../2014/tools/configuration-manager/sql-server-services.md)  
  
  
