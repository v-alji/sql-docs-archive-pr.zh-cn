---
title: “执行 T-SQL 语句”任务（维护计划）| Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
f1_keywords:
- sql12.swb.maint.tsql.f1
helpviewer_keywords:
- Execute T-SQL Statement Task dialog box
ms.assetid: fef3e259-0c47-4f6e-ade0-aee95e3d6c1a
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 63738758ce228a51ab6c75eb11a681eec3b27352
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87589054"
---
# <a name="execute-t-sql-statement-task-maintenance-plan"></a><span data-ttu-id="33217-102">“执行 T-SQL 语句”任务（维护计划）</span><span class="sxs-lookup"><span data-stu-id="33217-102">Execute T-SQL Statement Task (Maintenance Plan)</span></span>
  <span data-ttu-id="33217-103">使用“执行 T-SQL 语句任务”  对话框，可以通过向此维护计划添加所选择的 [!INCLUDE[tsql](../../includes/tsql-md.md)] 语句来自定义维护计划。</span><span class="sxs-lookup"><span data-stu-id="33217-103">Use the **Execute T-SQL Statement Task** dialog to customize your maintenance plan by adding [!INCLUDE[tsql](../../includes/tsql-md.md)] statements of your choice to this maintenance plan.</span></span>  
  
## <a name="options"></a><span data-ttu-id="33217-104">选项</span><span class="sxs-lookup"><span data-stu-id="33217-104">Options</span></span>  
 <span data-ttu-id="33217-105">**Connection**</span><span class="sxs-lookup"><span data-stu-id="33217-105">**Connection**</span></span>  
 <span data-ttu-id="33217-106">选择执行此任务时使用的服务器连接。</span><span class="sxs-lookup"><span data-stu-id="33217-106">Select the server connection to use when performing this task.</span></span>  
  
 <span data-ttu-id="33217-107">**新建**</span><span class="sxs-lookup"><span data-stu-id="33217-107">**New**</span></span>  
 <span data-ttu-id="33217-108">创建一个新的服务器连接，在执行此任务时使用。</span><span class="sxs-lookup"><span data-stu-id="33217-108">Create a new server connection to use when performing this task.</span></span> <span data-ttu-id="33217-109">下面对 **“新建连接”** 对话框进行了介绍。</span><span class="sxs-lookup"><span data-stu-id="33217-109">The **New Connection** dialog box is described below.</span></span>  
  
 <span data-ttu-id="33217-110">**执行超时值**</span><span class="sxs-lookup"><span data-stu-id="33217-110">**Execution time out**</span></span>  
 <span data-ttu-id="33217-111">超时（终止任务）前等待任务完成的时间（秒）。</span><span class="sxs-lookup"><span data-stu-id="33217-111">Time (seconds) to wait for task completion before timing out (terminating task).</span></span>  
  
 <span data-ttu-id="33217-112">**T-SQL 语句**</span><span class="sxs-lookup"><span data-stu-id="33217-112">**T-SQL statement**</span></span>  
 [!INCLUDE[tsql](../../includes/tsql-md.md)] <span data-ttu-id="33217-113">要执行的语句。</span><span class="sxs-lookup"><span data-stu-id="33217-113">statements to execute.</span></span>  
  
 <span data-ttu-id="33217-114">**查看 T-SQL**</span><span class="sxs-lookup"><span data-stu-id="33217-114">**View T-SQL**</span></span>  
 <span data-ttu-id="33217-115">根据所选选项，查看针对此任务的服务器执行的 [!INCLUDE[tsql](../../includes/tsql-md.md)] 语句。</span><span class="sxs-lookup"><span data-stu-id="33217-115">View the [!INCLUDE[tsql](../../includes/tsql-md.md)] statements performed against the server for this task, based on the selected options.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="33217-116">当受影响的对象很多时，可能需要相当长的时间才可显示。</span><span class="sxs-lookup"><span data-stu-id="33217-116">When the number of objects affected is large, this display can take a considerable amount of time.</span></span>  
  
## <a name="new-connection-dialog-box"></a><span data-ttu-id="33217-117">“新建连接”对话框</span><span class="sxs-lookup"><span data-stu-id="33217-117">New Connection Dialog Box</span></span>  
 <span data-ttu-id="33217-118">**连接名称**</span><span class="sxs-lookup"><span data-stu-id="33217-118">**Connection name**</span></span>  
 <span data-ttu-id="33217-119">输入新连接的名称。</span><span class="sxs-lookup"><span data-stu-id="33217-119">Enter a name for the new connection.</span></span>  
  
 <span data-ttu-id="33217-120">**选择或输入服务器名称**</span><span class="sxs-lookup"><span data-stu-id="33217-120">**Select or enter a server name**</span></span>  
 <span data-ttu-id="33217-121">选择执行此任务时所要连接的服务器。</span><span class="sxs-lookup"><span data-stu-id="33217-121">Select a server to connect to when performing this task.</span></span>  
  
 <span data-ttu-id="33217-122">**“刷新”**</span><span class="sxs-lookup"><span data-stu-id="33217-122">**Refresh**</span></span>  
 <span data-ttu-id="33217-123">刷新可用服务器的列表。</span><span class="sxs-lookup"><span data-stu-id="33217-123">Refresh the list of available servers.</span></span>  
  
 <span data-ttu-id="33217-124">**输入登录服务器所需的信息**</span><span class="sxs-lookup"><span data-stu-id="33217-124">**Enter information to log on to the server**</span></span>  
 <span data-ttu-id="33217-125">指定如何对服务器进行身份验证。</span><span class="sxs-lookup"><span data-stu-id="33217-125">Specify how to authenticate against the server.</span></span>  
  
 <span data-ttu-id="33217-126">**使用 Windows 集成安全性**</span><span class="sxs-lookup"><span data-stu-id="33217-126">**Use Windows integrated security**</span></span>  
 <span data-ttu-id="33217-127">使用 [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows 身份验证连接到 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] [!INCLUDE[msCoName](../../includes/msconame-md.md)] 实例。</span><span class="sxs-lookup"><span data-stu-id="33217-127">Connect to an instance of the [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] with [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows Authentication.</span></span>  
  
 <span data-ttu-id="33217-128">**使用特定用户名和密码**</span><span class="sxs-lookup"><span data-stu-id="33217-128">**Use a specific user name and password**</span></span>  
 <span data-ttu-id="33217-129">使用 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] 身份验证连接到 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 的实例。</span><span class="sxs-lookup"><span data-stu-id="33217-129">Connect to an instance of the [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] using [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Authentication.</span></span> <span data-ttu-id="33217-130">此选项不可用。</span><span class="sxs-lookup"><span data-stu-id="33217-130">This option is not available.</span></span>  
  
 <span data-ttu-id="33217-131">**用户名**</span><span class="sxs-lookup"><span data-stu-id="33217-131">**User name**</span></span>  
 <span data-ttu-id="33217-132">提供一个在进行身份验证时要使用的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 登录名。</span><span class="sxs-lookup"><span data-stu-id="33217-132">Provide a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] login to use when authenticating.</span></span> <span data-ttu-id="33217-133">此选项不可用。</span><span class="sxs-lookup"><span data-stu-id="33217-133">This option is not available.</span></span>  
  
 <span data-ttu-id="33217-134">**密码**</span><span class="sxs-lookup"><span data-stu-id="33217-134">**Password**</span></span>  
 <span data-ttu-id="33217-135">提供一个在进行身份验证时要使用的密码。</span><span class="sxs-lookup"><span data-stu-id="33217-135">Provide a password to use when authenticating.</span></span> <span data-ttu-id="33217-136">此选项不可用。</span><span class="sxs-lookup"><span data-stu-id="33217-136">This option is not available.</span></span>  
  
  
