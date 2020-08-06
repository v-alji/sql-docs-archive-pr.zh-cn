---
title: Analysis Server 属性（“服务”选项卡）| Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
ms.assetid: 8dbe4bc5-6aa9-48ee-857e-0b4ea764b9cb
author: stevestein
ms.author: sstein
ms.openlocfilehash: 91200120d87224c8e7733b0ff41ed423d3086c34
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87693593"
---
# <a name="analysis-server-properties-service-tab"></a><span data-ttu-id="3f5a6-102">分析服务器属性（“服务”选项卡）</span><span class="sxs-lookup"><span data-stu-id="3f5a6-102">Analysis Server Properties (Service Tab)</span></span>
  <span data-ttu-id="3f5a6-103">此服务是 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="3f5a6-103">This service is the [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)].</span></span> <span data-ttu-id="3f5a6-104">若要使 [!INCLUDE[ssAS](../../includes/ssas-md.md)] 正常运行，则必须运行此服务。</span><span class="sxs-lookup"><span data-stu-id="3f5a6-104">This service must be running for [!INCLUDE[ssAS](../../includes/ssas-md.md)] to work properly.</span></span> <span data-ttu-id="3f5a6-105">如果属性值呈浅灰色，则不能使用此应用程序进行更改。</span><span class="sxs-lookup"><span data-stu-id="3f5a6-105">The property values in light gray cannot be changed using this application.</span></span>  
  
## <a name="options"></a><span data-ttu-id="3f5a6-106">选项</span><span class="sxs-lookup"><span data-stu-id="3f5a6-106">Options</span></span>  
 <span data-ttu-id="3f5a6-107">**二进制路径**</span><span class="sxs-lookup"><span data-stu-id="3f5a6-107">**Binary Path**</span></span>  
 <span data-ttu-id="3f5a6-108">显示此服务所使用的程序文件的位置。</span><span class="sxs-lookup"><span data-stu-id="3f5a6-108">Displays the location of the program files used by this service.</span></span>  
  
 <span data-ttu-id="3f5a6-109">**错误控制**</span><span class="sxs-lookup"><span data-stu-id="3f5a6-109">**Error Control**</span></span>  
 <span data-ttu-id="3f5a6-110">1 指示 `SERVICE_ERROR_NORMAL`。</span><span class="sxs-lookup"><span data-stu-id="3f5a6-110">1 indicates `SERVICE_ERROR_NORMAL`.</span></span> <span data-ttu-id="3f5a6-111">如果在计算机启动过程中无法启动该服务，则启动程序会记录该错误并显示一个弹出消息框，但仍会继续执行启动操作。</span><span class="sxs-lookup"><span data-stu-id="3f5a6-111">If the service fails to start during computer start up, the startup program logs the error and displays a pop-up message box but continues the startup operation.</span></span> <span data-ttu-id="3f5a6-112">此值不能更改。</span><span class="sxs-lookup"><span data-stu-id="3f5a6-112">This value cannot be changed.</span></span>  
  
 <span data-ttu-id="3f5a6-113">**退出代码**</span><span class="sxs-lookup"><span data-stu-id="3f5a6-113">**Exit Code**</span></span>  
 <span data-ttu-id="3f5a6-114">当发生错误时，错误号显示在此信息框中。</span><span class="sxs-lookup"><span data-stu-id="3f5a6-114">When an error occurs, the error number appears in this box.</span></span> <span data-ttu-id="3f5a6-115">您可以通过在 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 知识库中搜索该号码获取相关信息来排除故障，或将该错误号提供给技术支持人员以获得帮助。</span><span class="sxs-lookup"><span data-stu-id="3f5a6-115">Use this number to troubleshoot failures by searching for the number in the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Knowledge Base or provide the number to your technical support staff.</span></span>  
  
 <span data-ttu-id="3f5a6-116">**Host Name**</span><span class="sxs-lookup"><span data-stu-id="3f5a6-116">**Host Name**</span></span>  
 <span data-ttu-id="3f5a6-117">显示运行 [!INCLUDE[ssAS](../../includes/ssas-md.md)]的计算机或群集的名称。</span><span class="sxs-lookup"><span data-stu-id="3f5a6-117">Displays the name of the computer or cluster running [!INCLUDE[ssAS](../../includes/ssas-md.md)].</span></span>  
  
 <span data-ttu-id="3f5a6-118">**名称**</span><span class="sxs-lookup"><span data-stu-id="3f5a6-118">**Name**</span></span>  
 <span data-ttu-id="3f5a6-119">指示该服务的显示名称。</span><span class="sxs-lookup"><span data-stu-id="3f5a6-119">Indicates the display name of the service.</span></span>  
  
 <span data-ttu-id="3f5a6-120">**进程 ID**</span><span class="sxs-lookup"><span data-stu-id="3f5a6-120">**Process ID**</span></span>  
 <span data-ttu-id="3f5a6-121">显示由 [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows 用来跟踪此程序进程的编号。</span><span class="sxs-lookup"><span data-stu-id="3f5a6-121">Displays the number used by [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows to keep track of this program's processes.</span></span>  
  
 <span data-ttu-id="3f5a6-122">**SQL 服务类型**</span><span class="sxs-lookup"><span data-stu-id="3f5a6-122">**SQL Service Type**</span></span>  
 <span data-ttu-id="3f5a6-123">显示用于调用进程的服务的类型。</span><span class="sxs-lookup"><span data-stu-id="3f5a6-123">Displays the type of service provided to calling processes.</span></span> [!INCLUDE[msCoName](../../includes/msconame-md.md)] <span data-ttu-id="3f5a6-124">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 安装有多种服务。</span><span class="sxs-lookup"><span data-stu-id="3f5a6-124">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] installs several services.</span></span>  
  
 <span data-ttu-id="3f5a6-125">**启动模式**</span><span class="sxs-lookup"><span data-stu-id="3f5a6-125">**Start Mode**</span></span>  
 <span data-ttu-id="3f5a6-126">对此服务设置以下选项：</span><span class="sxs-lookup"><span data-stu-id="3f5a6-126">Set this service to the following choices:</span></span>  
  
-   <span data-ttu-id="3f5a6-127">手动：计算机启动时，此服务不自动启动。</span><span class="sxs-lookup"><span data-stu-id="3f5a6-127">Manual: This service does not automatically start when the computer starts.</span></span> <span data-ttu-id="3f5a6-128">您必须使用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 配置管理器或其他工具来启动该服务。</span><span class="sxs-lookup"><span data-stu-id="3f5a6-128">You must start the service using [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Configuration Manager, or some other tool.</span></span>  
  
-   <span data-ttu-id="3f5a6-129">自动：计算机启动时，此服务将尝试启动。</span><span class="sxs-lookup"><span data-stu-id="3f5a6-129">Automatic: This service attempts to start when this computer starts.</span></span>  
  
-   <span data-ttu-id="3f5a6-130">已禁用：此服务无法启动。</span><span class="sxs-lookup"><span data-stu-id="3f5a6-130">Disabled: This service cannot be started.</span></span>  
  
 <span data-ttu-id="3f5a6-131">**State**</span><span class="sxs-lookup"><span data-stu-id="3f5a6-131">**State**</span></span>  
 <span data-ttu-id="3f5a6-132">指示此服务是正在运行、已停止还是已禁用。</span><span class="sxs-lookup"><span data-stu-id="3f5a6-132">Indicates whether this service is running, stopped, or disabled.</span></span>  
  
  
