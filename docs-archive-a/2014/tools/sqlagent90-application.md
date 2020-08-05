---
title: sqlagent90 应用程序 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: tools-other
ms.topic: conceptual
helpviewer_keywords:
- starting SQL Server Agent
- sqlagent90 application
- SQL Server Agent, starting
- command prompt utilities [SQL Server], sqlagent90
ms.assetid: e8b80e8d-d0c9-4500-a868-0ce08233da08
author: stevestein
ms.author: sstein
ms.openlocfilehash: 290cb69f39aa3b08bb290c210b2d37977614a1ae
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87579918"
---
# <a name="sqlagent90-application"></a><span data-ttu-id="6d2c4-102">sqlagent90 应用程序</span><span class="sxs-lookup"><span data-stu-id="6d2c4-102">sqlagent90 Application</span></span>
  <span data-ttu-id="6d2c4-103">**sqlagent90** 应用程序从命令提示符处启动 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 代理。</span><span class="sxs-lookup"><span data-stu-id="6d2c4-103">The **sqlagent90** application starts [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Agent from the command prompt.</span></span> <span data-ttu-id="6d2c4-104">通常，应从 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 或在应用程序中使用 SQL-SMO 方法来运行 [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] 代理。</span><span class="sxs-lookup"><span data-stu-id="6d2c4-104">Usually, [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Agent should be run from [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] or by using SQL-SMO methods in an application.</span></span> <span data-ttu-id="6d2c4-105">只有在诊断 **代理时或主要支持提供商指示你使用命令提示符时，才可以从命令提示符处运行** sqlagent90 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="6d2c4-105">Only run **sqlagent90** from the command prompt when you are diagnosing [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Agent, or when you are directed to it by your primary support provider.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6d2c4-106">语法</span><span class="sxs-lookup"><span data-stu-id="6d2c4-106">Syntax</span></span>  
  
```  
  
sqlagent90  
-c [-v] [-iinstance_name]  
```  
  
## <a name="arguments"></a><span data-ttu-id="6d2c4-107">参数</span><span class="sxs-lookup"><span data-stu-id="6d2c4-107">Arguments</span></span>  
 <span data-ttu-id="6d2c4-108">**-c**</span><span class="sxs-lookup"><span data-stu-id="6d2c4-108">**-c**</span></span>  
 <span data-ttu-id="6d2c4-109">指示 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 代理从命令提示符运行，并且独立于 Microsoft Windows 服务控制管理器。</span><span class="sxs-lookup"><span data-stu-id="6d2c4-109">Indicates that [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Agent is running from the command prompt and is independent of the Microsoft Windows Services Control Manager.</span></span> <span data-ttu-id="6d2c4-110">使用 **-c** 时，无法从“管理工具”的“服务”应用程序或从 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 配置管理器控制 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 代理。</span><span class="sxs-lookup"><span data-stu-id="6d2c4-110">When **-c** is used, [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Agent cannot be controlled from either the Services application in Administrative Tools or [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Configuration Manager.</span></span> <span data-ttu-id="6d2c4-111">此参数是必需的。</span><span class="sxs-lookup"><span data-stu-id="6d2c4-111">This argument is mandatory.</span></span>  
  
 <span data-ttu-id="6d2c4-112">**-v**</span><span class="sxs-lookup"><span data-stu-id="6d2c4-112">**-v**</span></span>  
 <span data-ttu-id="6d2c4-113">指示 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 代理以详细模式运行并向命令提示符窗口写入诊断信息。</span><span class="sxs-lookup"><span data-stu-id="6d2c4-113">Indicates that [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Agent runs in verbose mode and writes diagnostic information to the command-prompt window.</span></span> <span data-ttu-id="6d2c4-114">该诊断信息与写入 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 代理错误日志中的信息相同。</span><span class="sxs-lookup"><span data-stu-id="6d2c4-114">The diagnostic information is the same as the information written to the [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Agent error log.</span></span>  
  
 <span data-ttu-id="6d2c4-115">**-i** *instance_name*</span><span class="sxs-lookup"><span data-stu-id="6d2c4-115">**-i** *instance_name*</span></span>  
 <span data-ttu-id="6d2c4-116">指示 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 代理连接到由 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] instance_name *所指定的*命名实例。</span><span class="sxs-lookup"><span data-stu-id="6d2c4-116">Indicates that [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Agent connects to the named [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] instance specified by *instance_name*.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="6d2c4-117">备注</span><span class="sxs-lookup"><span data-stu-id="6d2c4-117">Remarks</span></span>  
 <span data-ttu-id="6d2c4-118">在显示版权消息后，只有在指定了 **-v** 开关时， **sqlagent90** 才会在命令提示符窗口中显示输出。</span><span class="sxs-lookup"><span data-stu-id="6d2c4-118">After displaying a copyright message, **sqlagent90** displays output in the command prompt window only when the **-v** switch is specified.</span></span> <span data-ttu-id="6d2c4-119">若要停止 **sqlagent90**，请在命令提示符处按 CTRL+C。</span><span class="sxs-lookup"><span data-stu-id="6d2c4-119">To stop **sqlagent90**, press CTRL+C at the command prompt.</span></span> <span data-ttu-id="6d2c4-120">在停止 **sqlagent90**之前，请不要关闭命令提示符窗口。</span><span class="sxs-lookup"><span data-stu-id="6d2c4-120">Do not close the command-prompt window before stopping **sqlagent90**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6d2c4-121">另请参阅</span><span class="sxs-lookup"><span data-stu-id="6d2c4-121">See Also</span></span>  
 [<span data-ttu-id="6d2c4-122">自动执行管理任务（SQL Server 代理）</span><span class="sxs-lookup"><span data-stu-id="6d2c4-122">Automated Administration Tasks &#40;SQL Server Agent&#41;</span></span>](../ssms/agent/automated-administration-tasks-sql-server-agent.md)  
  
  
